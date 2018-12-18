---
title: 'İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], controlling from Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon Designer [Office development in Visual Studio]
- customizing the Ribbon, tabs
- custom Ribbon, tabs
- Custom tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a0089880e143c3db8f260141d9936058bf35b1ce
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808878"
---
# <a name="walkthrough-create-a-custom-tab-by-using-the-ribbon-designer"></a>İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma
  Şerit Tasarımcısını kullanarak, özel bir sekme oluşturabilir ve ardından ekleyin ve üzerinde denetimleri konumlandırma.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
-   [Eylemler bölmesi oluşturmak](#BKMK_CreateActionsPanes).  
  
-   [Özel sekme oluşturma](#BKMK_CreateCustomTab).  
  
-   [Özel sekme üzerindeki düğmeleri kullanarak Eylemler bölmelerini gösterme ve gizleme](#BKMK_HideShowActionsPane).  
  
> [!NOTE]  
>  Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="create-an-excel-workbook-project"></a>Bir Excel çalışma kitabı projesi oluşturma  
 Şerit Tasarımcısını kullanma adımları bütün Office uygulamaları için neredeyse aynıdır. Bu örnekte, bir Excel çalışma kitabı kullanılmıştır.  
  
### <a name="to-create-an-excel-workbook-project"></a>Bir Excel çalışma kitabı projesi oluşturmak için  
  
-   Adlı bir Excel çalışma kitabı projesi oluşturun **MyExcelRibbon**. Daha fazla bilgi için [nasıl yapılır: Visual Studio'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio tasarımcıda yeni çalışma kitabını açar ve ekler **MyExcelRibbon** için proje **Çözüm Gezgini**.  
  
##  <a name="BKMK_CreateActionsPanes"></a> Eylemler bölmesi oluşturma  
 Projeye iki özel eylem bölmesi ekleyin. Daha sonra gösteren ve özel sekmeye bu eylemler bölmelerini gizleme düğmeler ekleyeceksiniz.  
  
### <a name="to-create-actions-panes"></a>Eylemler bölmesi oluşturmak için  
  
1.  Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **ActionsPaneControl**ve ardından **Ekle**.  
  
     **ActionsPaneControl1.cs** veya **ActionsPaneControl1.vb** dosyası tasarımcıda açılır.  
  
3.  Gelen **ortak denetimleri** sekmesinde **araç kutusu**, Tasarımcı yüzeyine bir etiket ekleyin.  
  
4.  İçinde **özellikleri** penceresinde **metin** label1'in özelliği **Actions Pane 1**.  
  
5.  İkinci eylemler bölmesi ve etiketi oluşturmak için 1 ile 5 adımlarını tekrarlayın. Ayarlama **metin** özelliği İkinci etiketin **Actions Pane 2**.  
  
##  <a name="BKMK_CreateCustomTab"></a> Özel sekme oluşturma  
 Office uygulaması tasarım yönergelerinden biri olduğundan, kullanıcıların Office uygulaması UI denetimini her zaman olmalıdır. Bu özelliği Eylemler bölmelerine uygulamak eklemek için Göster ve her bir özel Şerit sekmesinde Eylemler bölmesinde gizleyen düğmeler ekleyebilirsiniz. Özel sekme oluşturmak için bir **Şerit (Görsel Tasarımcı)** projeye öğe. Tasarımcı eklemenize ve yerleştirmenize, denetim özelliklerini ayarlamanıza ve denetim olaylarını yardımcı olur.  
  
### <a name="to-create-a-custom-tab"></a>Özel sekme oluşturma  
  
1.  Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.  
  
2.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **Şerit (Görsel Tasarımcı)**.  
  
3.  Yeni Şeridin adını değiştirmek **MyRibbon**ve **Ekle**.  
  
     **MyRibbon.cs** veya **MyRibbon.vb** dosyası Şerit Tasarımcısı'nda açılır ve varsayılan bir sekme ve grup görüntüler.  
  
4.  Şerit Tasarımcısı'nda varsayılan sekmesini seçin.  
  
5.  İçinde **özellikleri** penceresini genişletin **ControlId** özelliği ve ardından **ControlIdType** özelliğini **özel**.  
  
6.  Ayarlama **etiket** özelliğini **bana özel sekme**.  
  
7.  Şerit Tasarımcısı'nda **group1**.  
  
8.  İçinde **özellikleri** penceresinde **etiket** için **Actions Pane Manager**.  
  
9. Gelen **Office Şerit denetimleri** sekmesinde **araç kutusu**, bir düğme sürükleyin **group1**.  
  
10. Seçin **button1**.  
  
11. İçinde **özellikleri** penceresinde **etiket** için **Show Actions Pane 1**.  
  
12. İkinci bir düğme ekleyin **group1**, ayarlayıp **etiket** özelliğini **Show Actions Pane 2**.  
  
13. Gelen **Office Şerit denetimleri** sekmesinde **araç kutusu**, sürükleyin bir **ToggleButton** denetimi **group1**.  
  
14. Ayarlama **etiket** özelliğini **Eylemler Bölmesini Gizle**.  
  
##  <a name="BKMK_HideShowActionsPane"></a> Özel sekme üzerindeki düğmeleri kullanarak Eylemler bölmelerini gösterme ve gizleme  
 Son adım kullanıcıya yanıt veren kodu eklemektir. Olay işleyicileri ekleme <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> iki düğmenin olayları ve <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> iki durumlu düğmenin olay. Olay işleyicilere Eylemler bölmelerini gösterme ve gizleme etkinleştirmek için kod ekleyin.  
  
### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>Kullanarak özel sekmedeki düğmeleri kullanarak Eylemler bölmelerini göstermek ve gizlemek için  
  
1.  İçinde **Çözüm Gezgini**, kısayol menüsünü açın *MyRibbon.cs* veya *MyRibbon.vb*ve ardından **Kodu Görüntüle**.  
  
2.  Üstüne aşağıdaki kodu ekleyin `MyRibbon` sınıfı. Bu kod, iki Eylemler bölmesi nesnesi oluşturur.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#1)]  
  
3.  Değiştirin `MyRibbon_Load` yöntemini aşağıdaki kod ile. Bu kod Eylemler bölmesi nesnelerini ekler <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> toplama ve nesneleri görünümden gizler. Visual C# kodu, ayrıca birçok Şerit denetim olaylarına temsilciler ekler.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#2)]  
  
4.  Aşağıdaki üç olay işleyicisi yöntemini ekleyin `MyRibbon` sınıfı. Bu yöntemleri işleyen <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> iki düğmenin olayları ve <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> iki durumlu düğmenin olay. Button1 ve button2 için olay işleyiciler alternatif Eylemler bölmelerini görüntüler. ToggleButton1 için olay işleyicisi etkin eylemler bölmesini gizler ve gösterir.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#3)]  
  
## <a name="test-the-custom-tab"></a>Özel sekmeyi test etme  
 Programını çalıştırdığınızda proje, Excel başlatır ve **bana özel sekme** sekmesi, Şerit üzerinde görünür. Düğmeleri seçin **bana özel sekme** gösterip Eylemler bölmelerini gizleme.  
  
### <a name="to-test-the-custom-tab"></a>Özel sekmeyi test etmek için  
  
1.  Tuşuna **F5** projeyi çalıştırın.  
  
2.  Seçin **bana özel sekme** sekmesi.  
  
3.  İçinde **özel eylem bölmesi Yöneticisi** Grup öğesini **Show Actions Pane 1**.  
  
     Eylemler bölmesi görünür ve etiket görüntüler **Actions Pane 1**.  
  
4.  Seçin **Göster Eylemler bölmesi 2**.  
  
     Eylemler bölmesi görünür ve etiket görüntüler **Actions Pane 2**.  
  
5.  Seçin **Eylemler Bölmesini Gizle**.  
  
     Eylemler bölmesi artık görünür değildir.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Aşağıdaki konulardan Office UI özelleştirme hakkında daha fazla bilgi edinebilirsiniz:  
  
-   Tüm belge düzeyi özelleştirmesine Bağlam tabanlı UI ekleyin. Daha fazla bilgi için [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md).  
  
-   Bir standart veya özel Microsoft Office Outlook biçimini genişletin. Daha fazla bilgi için [izlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Şerit, çalışma zamanında erişme](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Şerite Genel Bakış](../vsto/ribbon-overview.md)   
 [Şerit Tasarımcısı](../vsto/ribbon-designer.md)   
 [Outlook için Şerit özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Nasıl yapılır: Şerit özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Nasıl yapılır: Şeritteki sekmenin konumunu değiştirme](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Nasıl yapılır: yerleşik bir sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md)   
 [Nasıl yapılır: backstage görünümüne denetimler ekleme](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Şerit nesne modeline genel bakış](../vsto/ribbon-object-model-overview.md)  
  
  