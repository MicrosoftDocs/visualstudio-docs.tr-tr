---
title: Mac için Visual Studio'yu genişletme
description: Mac özellikleri ve işlevleri için Visual Studio uzantı paketleri adlı modülleriyle genişletilebilir. Bu kılavuzun ilk bölümü, bir basit bir belgeye tarih ve saat için Visual Studio'yu Mac uzantı paketi oluşturur. İkinci bölümü, bu kılavuzun uzantı paketi sistemi temelleri ve bazı çekirdek temelini Mac için Visual Studio'nun API'leri sunar.
author: conceptdev
ms.author: crdun
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: D5245AB0-8404-426B-B538-F49125E672B2
ms.openlocfilehash: 8212039cd4f83cd9ea2b53a1050f32ed5dbad367
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295143"
---
# <a name="extending-visual-studio-for-mac"></a>Mac için Visual Studio'yu genişletme

Mac için Visual Studio modülleri adlı bir dizi oluşur *uzantı paketleri*. Uzantı paketleri gibi ek bir dil veya yeni bir proje şablonu için destek, Mac için Visual Studio için yeni işlevleri tanıtmak için kullanabilirsiniz.

Uzantı paketleri yapı gelen *uzantısı* diğer uzantı paketleri noktaları. Uzantı, bağlı bir menü veya IDE komutların listesini gibi Genişletilebilir alanlarını yer tutucular noktalarıdır. Uzantı paketi, bir düğüm olarak adlandırılan yeni bir menü öğesi ya da yeni bir komut gibi bir uzantı yapılandırılmış verilerin kaydederek bir uzantı noktası oluşturabilirsiniz. Her uzantı noktası uzantıları, belirli bir türdeki gibi kabul bir *komut*, *paneli*, veya *FileTemplate*. Uzantı noktaları içeren bir modül olarak adlandırılan bir *eklentisi konak*gibi diğer uzantı paketleri tarafından genişletilebilir.

Mac için Visual Studio özelleştirmek için yapıları bir uzantı paketi, Mac için Visual Studio'da önceden mevcut olan kitaplıkları içindeki eklenti ana bulunan uzantı noktaları tarafından Aşağıdaki diyagramda gösterildiği gibi oluşturabilirsiniz:

![Eklenti mimarisi](media/extending-visual-studio-mac-addin1.png)

Mac için Visual Studio'dan oluşturmak bir uzantı paketi için sırada Visual Studio'da genişletme noktaları Mac IDE için önceden varolan yapı uzantıları olması gerekir. Uzantı paketinin bir eklenti konak tanımlanmış bir uzantı noktası kullanır, olması bildirilir bir _bağımlılık_ üzerinde bu uzantı paketi.

Bu modüler bir tasarım avantajdır Mac için Visual Studio Genişletilebilir--bağlı özel uzantı paketleri ile oluşturulabilir birçok uzantı noktaları vardır. Geçerli uzantı paketleri örnekler için destek C# ve F#, hata ayıklayıcı, Araçlar ve proje şablonları.

> [!NOTE]
> **Not**: eklenti Oluşturucu önce 1.2 oluşturulmuş bir oluşturucu eklenti projesine sahip olmak, projenizi adımlarda belirtildiği gibi geçiş geçmeniz [burada](https://mhut.ch/addinmaker/1.2).

<!---The [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) topic explains how to build an extension package that uses a *Command* to insert the date and time into an open text document.--->

Bu bölümde, eklenti Oluşturucu tarafından üretilen farklı dosyalar bakar ve komut uzantısı verileri gerektirir.

## <a name="attribute-files"></a>Öznitelik dosyaları

Uzantı paketleri C# özniteliklerinde kullanıcının adını, sürüm, bağımlılıklar ve diğer bilgileri hakkındaki meta verileri depolar. Eklenti Oluşturucu iki dosya oluşturur `AddinInfo.cs` ve `AssemblyInfo.cs` depolamak ve bu bilgileri düzenlemek için. Uzantı paketleri benzersiz bir kimliği olması gerekir ve içinde belirtilen namespace kendi *eklentisi özniteliği*:

```csharp
[assembly:Addin (
   "DateInserter",
   Namespace = "DateInserter",
   Version = "1.0"
)]
```

Uzantı paketleri ayrıca bunlar takın uzantı noktaları kendi uzantı paketleri bağımlılıklarını bildirmeniz gerekir. Bunlar, oluşturma zamanında otomatik olarak başvurulur.

Ayrıca, ek başvurular proje çözüm panelinde eklenti referans düğümün aracılığıyla tarafından aşağıdaki görüntüde gösterildiği şekilde eklenebilir:

![Tarih ekran görüntüsü Ekle](media/extending-visual-studio-mac-addin13.png)

Bunlara karşılık gelen aynı zamanda sahiptirler `assembly:AddinDependency` başında eklenen öznitelikleri derleme zamanı. Meta veriler ve bağımlılık bildirimlerini yerinde olduktan sonra uzantı paketinin temel yapı taşlarını üzerinde odaklanabilirsiniz.

## <a name="extensions-and-extension-points"></a>Uzantılar ve uzantı noktaları

(Bir tür), bir veri yapısını tanımlayan yer tutucu bir uzantı noktasıdır istediğiniz uzantıyı noktasınca belirtilen bir yapıya uyan veriler uzantı tanımlar. Ne tür uzantısı kendi bildiriminde kabul edebilir, uzantı noktaları belirtin. Uzantılar, tür adları veya uzantı yolları kullanarak bildirilir. Bkz: [uzantı noktası başvuru](https://github.com/mono/mono-addins/wiki/Extension-Points) ihtiyacınız uzantı noktası oluşturma hakkında daha ayrıntılı bir açıklama için.

Uzantı/uzantı noktası mimarisi, hızlı ve modüler bir Mac için Visual Studio geliştirme tutar.

<!--Since there are a large number of extension types, this article focuses on the ones used in the extension package that was built in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md).-->

### <a name="command-extensions"></a>Komut uzantıları

<!--[Walkthrough](~/extending-visual-studio-mac-walkthrough.md) uses a Command Extension - an extension that points to methods that are called every time it is executed. -->

Komut uzantıları her zaman yürütülür çağrılan yöntemlere işaret eden uzantılarıdır.

Komut uzantıları girdileri ekleme tarafından tanımlanan `/MonoDevelop/Ide/Commands` uzantı noktası. Bizim uzantısında tanımladığımız `Manifest.addin.xml` aşağıdaki kod ile:

 ```xml
<Extension path="/MonoDevelop/Ide/Commands/Edit">
  <command id="DateInserter.DateInserterCommands.InsertDate"
            _label="Insert Date"
            _description="Insert the current date"
            defaulthandler="DateInserter.InsertDateHandler" />
</Extension>
```

Uzantı düğüm, bu durumda takarak genişletme noktası belirtir bir path özniteliği içeren `/MonoDevelop/Ide/Commands/Edit`. Ayrıca, komutu bir üst düğüme görür. Komut düğümü aşağıdaki özniteliklere sahiptir:

*   **Kimliği** -bu komut için bir tanımlayıcı belirtir. Komut tanımlayıcıları numaralandırma üyeleri bildirilmesi gerekir ve komutları için Commandıtems'lara bağlanmak için kullanılır.
*   **_etiketi** -menülerde gösterilecek metin.
*   **açı_klama** -araç çubuğu düğmeleri araç ipucu olarak gösterilecek metin.
*   **defaultHandler** -belirtir `CommandHandler` komutu güç katan sınıfı

<!--To invoke the command from the Edit Menu, the walkthrough creates a CommandItem extension that plugs into the `/MonoDevelop/Ide/MainMenu/Edit` extension point:-->

İçine takılan CommandItem uzantısı `/MonoDevelop/Ide/MainMenu/Edit` uzantı noktası, aşağıdaki kod parçacığında gösterilmiştir:

```xml
<Extension path="/MonoDevelop/Ide/MainMenu/Edit">
  <commanditem id="DateInserter.DateInserterCommands.InsertDate" />
</Extension>
```

Bir menüye alt kimliği özniteliğinde belirtilen bir komutu bir CommandItem yerleştirir. Bu CommandItem genişletme `/MonoDevelop/Ide/MainMenu/Edit` komut etiket görünür kılan uzantı noktası **Düzen menüsünün**. Unutmayın **kimliği** CommandItem içinde komut düğümünün kimliğine karşılık gelen `InsertDate`. CommandItem kaldırmak için olsaydı **tarih Ekle** seçeneği Düzenle Menüsü'nden kaybolması.

### <a name="command-handlers"></a>Komut işleyicileri

`InsertDateHandler` Uzantısıdır `CommandHandler` sınıfı. İki yöntem, onu geçersiz kılar `Update` ve `Run`. `Update` Yöntemi sorgulanan her bir komut bir menüde görüntülenen veya tuş bağlamaları yürütülür. Bilgisi nesnesi değiştirerek, komutunu devre dışı bırakmak veya görünmez yapma, dizi komutları ve daha fazlasını doldurun. Bu `Update` yöntemi devre dışı bırakır komut etkin bir bulamazsanız *belge* ile bir *TextEditor* metnine eklemek için:

```csharp
protected override void Update (CommandInfo info)
{
    info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
}
```

Geçersiz kılmak yeterlidir `Update` etkinleştirme veya komut gizleme için özel bir mantık varsa yöntemi. `Run` Yöntemini yürütür her bir kullanıcı Düzenle Menüsü'nden bir kullanıcı komutu seçtiğinde oluşan bu durumda bir komutu yürütür. Bu yöntem, metin düzenleyici giriş işaretini tarihi ve saati ekler:

```csharp
protected override void Run ()
{
  var editor = IdeApp.Workbench.ActiveDocument.Editor;
  var date = DateTime.Now.ToString ();
  editor.InsertAtCaret (date);
}
```

Komut türü içinde bir sabit listesi üye olarak bildirmek `DateInserterCommands`:

```csharp
public enum DateInserterCommands
{
  InsertDate,
}
```

Bu komut ve CommandItem bağdaştırabilir - CommandItem seçildiğinde CommandItem komutu çağıran **Düzen menüsünün**.

## <a name="ide-apis"></a>IDE API'leri

<!--The extension package detailed in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) deals with the Text Editor in Visual Studio for Mac, but this is only one of many possible areas for customization. -->

Geliştirme için kullanılabilir alanları kapsamı hakkında daha fazla bilgi için bkz: [uzantı ağaç başvurusu](http://monodevelop.com/Developers/Articles/Extension_Tree_Reference) ve [API'sine genel bakış](http://monodevelop.com/Developers/Articles/API_Overview). Ayrıca başvurmak Gelişmiş uzantı paketleri oluştururken [Geliştirici makaleleri](http://monodevelop.com/Developers/Articles). Özelleştirme için alanları kısmi bir listesi aşağıdadır:

*   Bölmeleri
*   Tuş bağlama şemalarını
*   İlkeler
*   Kod biçimlendiricileri
*   Proje dosya biçimleri
*   Tercihler panelleri
*   Seçenekleri panelleri
*   Hata ayıklayıcı protokolleri
*   Hata ayıklama görselleştiricileri
*   Çalışma alanı düzeni
*   Çözüm paneli ağaç düğümleri
*   Kaynak Düzenleyicisi kenar boşlukları
*   Birim test altyapıları
*   Kod oluşturucuları
*   Kod parçacıkları
*   Hedef Çerçeve
*   Hedef çalışma zamanı
*   VC arka uçları
*   Yeniden Düzenle
*   Yürütme işleyicileri
*   Söz dizimi vurgulama

## <a name="additional-information"></a>Ek Bilgiler

> [!NOTE]
> Şu anda Mac için Visual Studio genişletilebilirlik senaryoları geliştirmeye çalışıyoruz Uzantıları oluşturma ve Ek Yardım veya bilgi gereksinim veya geri bildirim sağlamak isterseniz, lütfen doldurun [Mac uzantısı geliştirme için Visual Studio](https://aka.ms/vsmac-extensions-survey) formu.

## <a name="see-also"></a>Ayrıca bkz.

- [(Windows üzerinde) Visual Studio uzantıları geliştirme](/visualstudio/extensibility/starting-to-develop-visual-studio-extensions)