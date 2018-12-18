---
title: 'Nasıl yapılır: etki alanına özgü bir dilde standart menü komutunu değiştirme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
ms.assetid: 9b9d8314-d0d8-421a-acb9-d7e91e69825c
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3d29a501ef6f55c835efd68e474bc39a847f745d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837576"
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Nasıl yapılır: Etki Alanına Özgü bir Dilde Standart Menü Komutunu Değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL'nizi içinde otomatik olarak tanımlanan standart komutlardan bazıları davranışını değiştirebilirsiniz. Örneğin, değiştirebilir **Kes** böylece hassas bilgileri içermez. Bunu yapmak için bir komut kümesi sınıftaki yöntemleri geçersiz kılın. Bu sınıfların DslPackage projesinde CommandSet.cs dosyasında tanımlanır ve türetilmiş <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.  
  
 Özetle, komutu değiştirmek için şunu yazın:  
  
1. [Hangi değiştirebilirsiniz komutları bulma](#what).  
  
2. [Uygun komut kümesi sınıfının bir kısmi bildirimi oluşturma](#extend).  
  
3. [Geçersiz kılma ProcessOnStatus ve ProcessOnMenu yöntemleri](#override) komutu.  
  
   Bu konu, bu yordamı açıklar.  
  
> [!NOTE]
>  Menü komutlarınızı oluşturmak istiyorsanız, bkz. [nasıl yapılır: kısayol menüsüne komut ekleme](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
##  <a name="what"></a> Hangi komutların, değişiklik yapabilirsiniz?  
  
#### <a name="to-discover-what-commands-you-can-modify"></a>Bulmak için hangi komutları değiştirebilir  
  
1.  İçinde `DslPackage` projesini açarsanız `GeneratedCode\CommandSet.cs`. Bu C# dosyası Çözüm Gezgini'nde bir yan kuruluşu olan bulunabilir `CommandSet.tt`.  
  
2.  Sınıf adları ile biten içinde bu dosyayı bulup "`CommandSet`", örneğin `Language1CommandSet` ve `Language1ClipboardCommandSet`.  
  
3.  Her komut kümesi sınıfı türü "`override`" ardından bir boşluk. IntelliSense, geçersiz kılabilirsiniz yöntemlerin listesini gösterir. Her komut, adları başlamak yöntemleri bir çift olan "`ProcessOnStatus`"ve"`ProcessOnMenu`".  
  
4.  Sınıfı, komutunun başarısını Not değiştirmek istediğiniz komutu içerir.  
  
5.  Dosyayı, yaptığınız düzenlemeleri kaydetmeden kapatın.  
  
    > [!NOTE]
    >  Genellikle, oluşturulan dosyaları düzenleme yapmamanız gerekir. Tüm düzenlemeleri dosyalar oluşturulur bir sonraki açışınızda kaybolur.  
  
##  <a name="extend"></a> Uygun komut kümesi sınıfını genişletir  
 Komut kümesi sınıfının bir kısmi bildirimi içeren yeni bir dosya oluşturun.  
  
#### <a name="to-extend-the-command-set-class"></a>Set sınıfı komutu genişletmek için  
  
1.  DslPackage projesindeki Çözüm Gezgini'nde GeneratedCode klasörü açın ve konum altında CommandSet.tt CommandSet.cs oluşturulan dosyasını açabilir. Ad alanı ve orada tanımladığınız ilk sınıf adını not edin. Örneğin, aşağıdaki görebilirsiniz:  
  
     `namespace Company.Language1`  
  
     `{ ...  internal partial class Language1CommandSet : ...`  
  
2.  İçinde **DslPackage**, adlı bir klasör oluşturun **özel kod**. Adlı yeni bir sınıf dosyası bu klasörde, oluşturma `CommandSet.cs`.  
  
3.  Yeni dosyanın, aynı ad alanı ve üretilen kısmi sınıf ada sahip bir kısmi bildirimi yazın. Örneğin:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Design;  
    namespace Company.Language1 /* Make sure this is correct */  
    { internal partial class Language1CommandSet { ...  
    ```  
  
     **Not** yeni dosyayı oluşturmak için sınıf dosyası şablonu kullandıysanız, hem ad alanı ve sınıf adını düzeltmeniz gerekir.  
  
##  <a name="override"></a> Komut yöntemleri geçersiz kılın  
 Çoğu komutlarının ilişkili iki yöntem vardır: yöntem bir adla ister `ProcessOnStatus`... komutu görünür ve etkin olup olmayacağını belirler. Kullanıcı diyagramda sağ tıkladığı zaman çağrılır hızlı bir şekilde yürütün ve herhangi bir değişiklik yapın. `ProcessOnMenu`... kullanıcı komutu tıkladığında ve komutun işlevi gerçekleştirmeniz gereken çağrılır. Bir ya da bu yöntemlerin ikisi de geçersiz kılmak isteyebilirsiniz.  
  
### <a name="to-change-when-the-command-appears-on-a-menu"></a>Komut bir menü görüntülendiğinde değiştirmek için  
 Geçersiz kılma ProcessOnStatus... yöntemi. Bu yöntem, Visible ayarlamanız gerekir ve özelliklerini, parametresinin MenuCommand etkin. Genellikle komut şu anda arar. Komut seçilen öğeleri için geçerlidir ve komut geçerli durumlarını uygulanabilir olup olmadığını belirlemek için özelliklerini, görünebilir olup olmadığını belirlemek için CurrentSelection.  
  
 Genel bir kılavuz olarak Visible özelliği tarafından hangi öğelerin seçilen belirlenmesi. Komut siyah veya gri menüde görüntülenip görüntülenmeyeceğini belirler, Enabled özelliğini seçimin geçerli durumuna bağlı olmalıdır.  
  
 Aşağıdaki örnek kullanıcının birden fazla şekil seçildiğinde Sil menü öğesi devre dışı bırakır.  
  
> [!NOTE]
>  Bu yöntem, komutu bir tuş vuruşu kullanılabilir olup olmadığını etkilemez. Örneğin, Sil menü öğesi devre dışı bırakma komutu Delete tuşuna çağrılan engellemez.  
  
```  
/// <summary>  
/// Called when user right-clicks on the diagram or clicks the Edit menu.  
/// </summary>  
/// <param name="command">Set Visible and Enabled properties.</param>  
protected override void ProcessOnStatusDeleteCommand (MenuCommand command)  
{  
  // Default settings from the base method.  
  base.ProcessOnStatusDeleteCommand(command);  
  if (this.CurrentSelection.Count > 1)  
  {  
    // If user has selected more than one item, Delete is greyed out.  
    command.Enabled = false;  
  }  
}  
```  
  
 İyi taban yöntemi çağırın, tüm durumları ve ayarları ile ilgili olmayan bir uygulamadır.  
  
 ProcessOnStatus yöntemi oluşturma, silme veya gerekir Store öğeleri güncelleştirme.  
  
### <a name="to-change-the-behavior-of-the-command"></a>Komutun davranışını değiştirmek için  
 Geçersiz kılma ProcessOnMenu... yöntemi. Aşağıdaki örnek, kullanıcının bile Delete tuşunu kullanarak bir kerede birden fazla öğe silmesi engeller.  
  
```  
/// <summary>  
/// Called when user presses Delete key   
/// or clicks the Delete command on a menu.  
/// </summary>  
protected override void ProcessOnMenuDeleteCommand()  
{  
  // Allow users to delete only one thing at a time.  
  if (this.CurrentSelection.Count <= 1)  
  {  
    base.ProcessOnMenuDeleteCommand();  
  }  
}  
```  
  
 Kodunuzu oluşturma, silme veya öğeleri veya bağlantıları güncelleştirme gibi Store için değişiklik yaparsa bir işlem içinde bunu yapmanız gerekir. Daha fazla bilgi için [model öğelerini oluşturmak veya güncelleştirmek için nasıl](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
### <a name="writing-the-code-of-the-methods"></a>Yöntemlerin kodunu yazma  
 Aşağıdaki parça bu yöntemleri içinde sık kullanışlıdır:  
  
- `this.CurrentSelection`. Kullanıcının sağ şekli şekiller ve bağlayıcılar bu listede her zaman dahil edilir. Diyagram kullanıcı diyagramın boş bir kısmına tıklarsa, listeyi yalnızca üyesidir.  
  
- `this.IsDiagramSelected()` - `true` Kullanıcı diyagramın boş bir kısmına tıkladıysanız.  
  
- `this.IsCurrentDiagramEmpty()`  
  
- `this.IsSingleSelection()` -Kullanıcı birden çok şekil seçmediniz  
  
- `this.SingleSelection` -Şekil veya kullanıcı sağ diyagramı  
  
- `shape.ModelElement as MyLanguageElement` -bir şekil tarafından temsil edilen model öğesi.  
  
  Nesneler ve bağlantılar oluşturma ve gezinme öğesi başka bir öğe hakkında daha fazla bilgi için bkz: [gezinme ve güncelleştirme Program kodundaki modeli](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ComponentModel.Design.MenuCommand>   
 [Bir etki alanına özgü dili özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Nasıl yapılır: kısayol menüsüne komut ekleme](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)   
 [İzlenecek yol: Seçilen bir bağlantıdan bilgi alma](../misc/walkthrough-getting-information-from-a-selected-link.md)   
 [VSPackage kullanıcı arabirimi öğelerini nasıl eklenir](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML Şeması Başvurusu](../extensibility/vsct-xml-schema-reference.md)   
 [VMSDK – devre diyagramları örnek. Kapsamlı DSL özelleştirme](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)   
 [Örnek kod: bağlantı hattı diyagramları](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)



