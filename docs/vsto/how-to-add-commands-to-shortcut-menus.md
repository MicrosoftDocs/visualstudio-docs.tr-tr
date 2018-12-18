---
title: 'Nasıl yapılır: kısayol menülerine komut ekleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9accca69c5d56461f07d21d25821c0f4181c8fbd
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677134"
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Nasıl yapılır: kısayol menülerine komut ekleme
  Bu konu, komutları kısayol menüsüne bir Office uygulamasında VSTO eklentisi kullanılarak nasıl ekleneceğini gösterir.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Kısayol menüleri Office komutları eklemek için  
  
1.  Ekle bir **Ribbon XML** belge düzeyi veya proje VSTO eklentisi öğesi. Daha fazla bilgi için [nasıl yapılır: Şerit özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md). İçindeki  
  
2.  **Çözüm Gezgini**seçin **ThisAddIn.cs** veya **ThisAddIn.vb**.  
  
3.  Menü çubuğunda, **görünümü** > **kod**.  
  
     **ThisAddIn** sınıf dosyası Kod Düzenleyicisi'nde açılır.  
  
4.  Aşağıdaki kodu ekleyin **ThisAddIn** sınıfı. Bu kodu geçersiz kılmalar `CreateRibbonExtensibilityObject` Office uygulamasına sınıf yöntemi ve Şerit XML döndürür.  
  
     [!code-csharp[Trin_WordAddIn_Menus#1](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#1)]  
  
5.  İçinde **Çözüm Gezgini**, Şerit XML dosyasını seçin. Varsayılan olarak, Ribbon XML dosyasındaki adlı *Ribbon1.xml*.  
  
6.  Menü çubuğunda, **görünümü** > **kod**.  
  
     Şerit xml dosyası Kod Düzenleyicisi'nde açılır.  
  
7.  Kod Düzenleyicisi'nde kısayol menüsünü ve kısayol menüsüne eklemek istediğiniz denetime açıklayan XML ekleyin.  
  
     Aşağıdaki örnek, bir düğme, menü ve galeri denetimi bir word belgesi için kısayol menüsünü ekler. Bu kısayol menüsünün denetim ContextMenuText kimliğidir. Office 2010 kısayol denetimi tam listesi için kimlikleri bkz [Office 2010 Yardım dosyaları: Office fluent kullanıcı arabirimi denetimi tanımlayıcıları](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>  
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui">  
      <contextMenus>  
        <contextMenu idMso="ContextMenuText">  
          <button id="MyButton" label="My Button" insertBeforeMso="HyperlinkInsert" onAction="GetButtonID" />  
          <menu id="MySubMenu" label="My Submenu" >  
            <button id="MyButton2" label="Button on submenu" />  
          </menu>  
          <gallery id="galleryOne" label="My Gallery">  
            <item id="item1" imageMso="HappyFace" />  
            <item id="item2" imageMso="HappyFace" />  
            <item id="item3" imageMso="HappyFace" />  
            <item id="item4" imageMso="HappyFace" />  
          </gallery>  
        </contextMenu>  
      </contextMenus>  
    </customUI>  
    ```  
  
8.  İçinde **Çözüm Gezgini**, seçin **MyRibbon.cs** veya **MyRibbon.vb**.  
  
9. Bir geri çağırma yöntemine ekleyin `Ribbon1` kullanmak istediğiniz her denetim için sınıf.  
  
     Aşağıdaki geri çağırma yöntemi tutamaçları **Düğmem** düğmesi. Bu kod, işaretçi, geçerli konumundaki etkin belge için bir dize ekler.  
  
     [!code-vb[Trin_WordAddIn_Menus#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb#2)]
     [!code-csharp[Trin_WordAddIn_Menus#2](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office kullanıcı arabirimini özelleştirme](../vsto/office-ui-customization.md)   
 [İzlenecek yol: Yer işaretleri için kısayol menüleri oluşturma](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)   
 [Office 2010'daki bağlam menüleri özelleştirme](http://go.microsoft.com/fwlink/?LinkId=182186)  
  