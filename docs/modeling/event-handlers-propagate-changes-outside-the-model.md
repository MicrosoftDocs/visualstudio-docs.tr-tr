---
title: Değişiklikleri Modelin Dışına Yayan Olay İşleyicileri
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 02cf41daa9bea74e62ceb96f7c6227982bfcad84
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967356"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Değişiklikleri Modelin Dışına Yayan Olay İşleyicileri

Görselleştirme ve modelleme SDK'sı, mağaza içi değişkenler, dosyalar, diğer depoları ve diğer Visual Studio uzantıları modeller gibi mağazası dışındaki kaynaklar değişiklikleri yaymak için depolama olay işleyicileri tanımlayabilirsiniz. Tetikleyici olayın gerçekleştiği işlem sonunda Store olay işleyicisi yürütülür. Bunlar ayrıca bir geri alma veya yineleme işlemi içinde yürütülür. Bu nedenle, depolama kurallarından farklı olarak, deposu olayları deponun dışında olan değerleri güncelleştirmek için ekseriyetle faydalıdır. .NET olaylarının tersine, bir sınıfa dinlemek için depolama olay işleyicileri kaydedilir: her örneği için ayrı bir işleyici kaydetmek zorunda değildir. Değişiklikleri işlemek için farklı yöntemler arasında seçim yapma hakkında daha fazla bilgi için bkz. [yanıt verme ve değişiklikleri yayma](../modeling/responding-to-and-propagating-changes.md).

Grafik yüzeyine ve diğer kullanıcı arabirimi denetimleri deposu olayları tarafından işlenebilen dış kaynaklara örnekleridir.

### <a name="to-define-a-store-event"></a>Bir depolama olayı tanımlamak için

1.  İzlemek istediğiniz olay türünü seçin. Tam bir listesi için özelliklerine bakmak <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>. Her bir özellik bir olay türüne karşılık gelir. En sık olay türleri kullanılır:

    -   `ElementAdded` -bir model öğesini tetiklenir, ilişki bağlantısı, Şekil veya bağlayıcının oluşturulur.

    -   Tetiklenen ElementPropertyChanged - değerini bir `Normal` etki alanı özelliği. Yalnızca eski ve yeni değerler eşit değilse, olay tetiklenir. Olay, hesaplanan ve özel depolama özellikleri için uygulanamaz.

         İlişki bağlantılarını karşılık gelen rol özellikleri için uygulanamaz. Bunun yerine, `ElementAdded` etki alanı ilişkisi izlemek için.

    -   `ElementDeleted` -bir model öğesini sonra tetiklenen, ilişki, Şekil veya bağlayıcının silindi. Öğesinin özellik değerlerini erişmeye devam edebilirsiniz, ancak hiçbir ilişki diğer öğelere sahip olacaktır.

2.  İçin bir parçalı sınıf tanımı ekleyin _YourDsl_**DocData** ayrı bir kod dosyasında **DslPackage** proje.

3.  Aşağıdaki örnekte olduğu gibi bir yöntem olarak olayın kodu yazın. Bu olabilir `static`erişmek istediğiniz sürece `DocData`.

4.  Geçersiz kılma `OnDocumentLoaded()` işleyicisini kaydetmek için. Birden fazla işleyici varsa, bunların tümü aynı yerde kaydedebilirsiniz.

Kayıt kodu konumunu kritik değildir. `DocView.LoadView()` Alternatif bir konumdur.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.MusicLib
{
  partial class MusicLibDocData
  {
    // Register store events here or in DocView.LoadView().
    protected override void OnDocumentLoaded()
    {
      base.OnDocumentLoaded(); // Don't forget this.

      #region Store event handler registration.
      Store store = this.Store;
      EventManagerDirectory emd = store.EventManagerDirectory;
      DomainRelationshipInfo linkInfo = store.DomainDataDirectory
          .FindDomainRelationship(typeof(ArtistAppearsInAlbum));
      emd.ElementAdded.Add(linkInfo,
          new EventHandler<ElementAddedEventArgs>(AddLink));
      emd.ElementDeleted.Add(linkInfo,
          new EventHandler<ElementDeletedEventArgs>(RemoveLink));

      #endregion Store event handlers.
    }

    private void AddLink(object sender, ElementAddedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Add(link.Artist.Name, link.Album.Title);
    }
    private void RemoveLink(object sender, ElementDeletedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Delete(link.Artist.Name, link.Album.Title);
    }
  }
}
```

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>Store içinde geri alınamaz ayarlamalar yapmak için olayları kullanma

İşlem, sonra olay işleyicisi yürütüldüğünden Store olayları normalde mağazasındaki değişiklikleri yayma için kullanılmaz. Bunun yerine, bir depo kural kullanmanız gerekir. Daha fazla bilgi için [kuralları yaymak değişiklikleri içinde modeli](../modeling/rules-propagate-changes-within-the-model.md).

Ancak, ek güncelleştirmeler özgün olayı ayrı ayrı geri alabilmek kullanıcıya istiyorsanız deposuna ek güncelleştirmeler yapmak için bir olay işleyicisi kullanabilirsiniz. Örneğin, küçük harf karakterler albüm başlıkları için normal kuralı olduğunu varsayalım. Kullanıcının büyük harfle yazdığını sonra küçük harf başlık düzeltir depolama olay işleyicisini yazabilirsiniz. Ancak, kullanıcı büyük harf karakterler geri yükleme, düzeltme, iptal etmek için geri alma komutunu kullanabilirsiniz. İkinci bir geri alma kullanıcının değişiklik kaldırabilirsiniz.

Aynı şeyi yapmak için bir depolama kural yazdıysanız, böylece kullanıcı ayarlama özgün değişiklik kaybetmeden geri alamadı aksine, kullanıcının değişiklik ve düzeltmenizi aynı işlemde olacaktır.

```csharp
partial class MusicLibDocView
{
    // Register store events here or in DocData.OnDocumentLoaded().
    protected override void LoadView()
    {
      /* Register store event handler for Album Title property. */
      // Get reflection data for property:
      DomainPropertyInfo propertyInfo =
        this.DocData.Store.DomainDataDirectory
        .FindDomainProperty(Album.TitleDomainPropertyId);
      // Add to property handler list:
      this.DocData.Store.EventManagerDirectory
        .ElementPropertyChanged.Add(propertyInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));

      /*
      // Alternatively, you can set one handler for
      // all properties of a class.
      // Your handler has to determine which property changed.
      DomainClassInfo classInfo = this.Store.DomainDataDirectory
           .FindDomainClass(typeof(Album));
      this.Store.EventManagerDirectory
          .ElementPropertyChanged.Add(classInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));
       */
      return base.LoadView();
    }

// Undoable adjustment after a property is changed.
// Method can be static since no local access.
private static void AlbumTitleAdjuster(object sender,
         ElementPropertyChangedEventArgs e)
{
  Album album = e.ModelElement as Album;
  Store store = album.Store;

  // We mustn't update the store in an Undo:
  if (store.InUndoRedoOrRollback
      || store.InSerializationTransaction)
      return;

  if (e.DomainProperty.Id == Album.TitleDomainPropertyId)
  {
    string newValue = (string)e.NewValue;
    string lowerCase = newValue.ToLowerInvariant();
    if (!newValue.Equals(lowerCase))
    {
      using (Transaction t = store.TransactionManager
            .BeginTransaction("adjust album title"))
      {
        album.Title = lowerCase;
        t.Commit();
      } // Beware! This could trigger the event again.
    }
  }
  // else other properties of this class.
}
```

Bir olay yazarsanız, deponun güncelleştirir:

-   Kullanım `store.InUndoRedoOrRollback` geri model öğelerini değişiklik yapmasını önlemek için. İşlem Yöneticisi, özgün durumuna geri deposundaki her şeyi ayarlanır.

-   Kullanım `store.InSerializationTransaction` model dosyasından yüklenirken değişiklik yapmasını önlemek için.

-   Değişikliklerinizi başka tetiklenmesi olayları neden olur. Sonsuz bir döngüye önlemek emin olun.

## <a name="store-event-types"></a>Store olay türleri

Her olay türüne bir koleksiyon Store.EventManagerDirectory karşılık gelir. Ekleyip olay işleyicileri dilediğiniz zaman kaldırabilirsiniz, ancak belge yüklendiğinde bunları eklemek için normal.

|`EventManagerDirectory` Özellik adı|Yürütülmesi|
|-|-|
|ElementAdded|Etki alanı sınıfı, etki alanı ilişkisi, şekil, bağlayıcı veya diyagramı örneği oluşturulur.|
|ElementDeleted|Bir model öğesini mağazanın öğesi dizinden kaldırılıp artık kaynak veya herhangi bir ilişki hedefi değil. Öğe gerçekten bellekten silinmez, ancak gelecekteki bir geri alma durumunda korunur.|
|ElementEventsBegun|Bir dış işlem sonunda çağrılır.|
|ElementEventsEnded|Diğer tüm olayları işlendiğinde çağrılır.|
|ElementMoved|Bir model öğesi bir depo bölümünden diğerine taşındı.<br /><br /> Bu diyagramdaki bir şeklin konumuna ilişkili değil.|
|ElementPropertyChanged|Bir etki alanı özelliğinin değerini değiştirdi. Yalnızca eski ve yeni değerler eşit değilse yürütülür.|
|RolePlayerChanged|Bir ilişkinin iki rollerinden (sonu), yeni bir öğeye başvuruyor.|
|RolePlayerOrderChanged|1'den büyük çokluktaki rolünde bağlantıları sırası değişti.|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>Ayrıca Bkz.

- [Değişikliklere Yanıt Verme ve Değişiklikleri Yayma](../modeling/responding-to-and-propagating-changes.md)
- [Örnek kod: bağlantı hattı diyagramları](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]