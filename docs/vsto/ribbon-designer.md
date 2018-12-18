---
title: Şerit Tasarımcısı
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, about Ribbon Designer
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- customizing the Ribbon, about Ribbon Designer
- Ribbon [Office development in Visual Studio], visual designer
- customizing the Ribbon
- custom Ribbon
- designers [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon [Office development in Visual Studio], common tasks
- Ribbon Designer [Office development in Visual Studio]
- read-only properties
- Ribbon [Office development in Visual Studio], shortcut keys
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b85347b6bda0d42f7350d145baf2c824aa92a71c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820634"
---
# <a name="ribbon-designer"></a>Şerit Tasarımcısı
  Şerit Tasarımcısı bir görsel tasarım tuvalidir. Bir Microsoft Office uygulamasının Şeritine özel sekmeler, gruplar ve denetimler eklemek için Şerit Tasarımcısını kullanın.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Şerit Tasarımcısını açmak için ekleme bir **Şerit (Görsel Tasarımcı)** projenize öğesi. Ardından, tasarım araçlarını aşağıdaki görevler için kullanabilirsiniz:  
  
-   [Şerit düzeninin tasarlama](#DesigningRibbonLayout)  
  
-   [Olayları işleme ve denetim özelliklerini ayarlama](#HandleEventsSetProperties)  
  
-   [Backstage görünümüne denetimler ekleme](#CustomizingMicrosoftOfficeButton)  
  
> [!NOTE]  
>  Şerit Tasarımcısını kullanarak yapamayacağınız bazı görevler vardır. Bu görevler ve bunları nasıl yapabileceğinizle ilgili daha fazla bilgi için bkz. [Şerite Genel Bakış](../vsto/ribbon-overview.md).  
  
 ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz. [şeridi Outlook'ta özelleştirmek için Şerit Tasarımcısını bunu nasıl yaparım kullanın?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>Projeye bir Şerit (Görsel Tasarımcı) öğesi ekleme  
 Şerit Tasarımcısını kullanmak için yeni bir ekleme **Şerit (Görsel Tasarımcı)** projenize öğesi. Daha fazla bilgi için [nasıl yapılır: Şerit özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
 Yeni bir eklediğinizde **Şerit (Görsel Tasarımcı)** öğesi, Visual Studio otomatik olarak aşağıdaki dosyaları projenize ekler:  
  
- Bir Şerit kod dosyası. Bu dosya için belirttiğiniz ada sahip **Şerit (Görsel Tasarımcı)** öğesi **Yeni Öğe Ekle** iletişim kutusu. Bu dosya için Şerit olaylarını işlemek için kod ekleyin.  
  
- Şerit Tasarımcısı kod dosyası. Bu dosya Şerit Tasarımcısı tarafından yaratılan kodu içerir ve be doğrudan düzenlenemez.  
  
- Bir kaynak dosyası. Bu dosya Şeritteki her denetimin özellik değerlerini içerir.  
  
  Zaten bir **Şerit (Görsel Tasarımcı)** öğesi başka bir projeden, geçerli projenizde kullanarak yeniden kullanabileceğiniz **varolan öğeyi Ekle** iletişim kutusu.  
  
##  <a name="DesigningRibbonLayout"></a> Şeriti Tasarlama  
 Şerit Tasarımcısını açmanın üç yolu vardır:  
  
- İçinde **Çözüm Gezgini**, Şerit kod dosyasına çift tıklayın.  
  
- İçinde **Çözüm Gezgini**Şerit kod dosyasını sağ tıklayın ve ardından **Görünüm Tasarımcısı**.  
  
- İçinde **Çözüm Gezgini**Şerit kod dosyasını seçin ve ardından **Tasarımcısı** üzerinde **görünümü** menüsü.  
  
  Şerit Tasarımcısı varsayılan bir sekme ve grup içerir. Varsayılan sekme ve grubu Şerit Tasarımcısından kaldırabilirsiniz. Varsayılan grubu kaldırmak için sağ **Group1**ve ardından **Sil**. Varsayılan sekmeyi kaldırmak için tasarım yüzeyinde boş bir alana sağ tıklayın ve ardından **Şerit Sekmesi Kaldır**.  
  
  Şerit Tasarımcısına özel sekmeler, gruplar ve denetimler de ekleyebilirsiniz. Bu denetimlerin bulabilirsiniz **araç kutusu**, **Office Şerit denetimleri** grubu. Denetim eklemenin üç yolu vardır **Office Şerit denetimleri** Şerit Tasarımcısına Grup:  
  
- Bir denetimi Şerit Tasarımcısı üzerinde uygun bir alana sürükleyin.  
  
- Denetim ve ardından Şerit Tasarımcısında uygun bir alana tıklayın.  
  
- Tasarımcıda uygun bir alan seçin ve sonra denetimi çift **araç kutusu**.  
  
### <a name="ribbon-design-workflow"></a>Şerit tasarımı iş akışı  
 Şerit düzenini tasarlamak için aşağıdaki temel adımları izleyin:  
  
1. [Şerite özel sekme Ekle](#AddTabToRibbon).  
  
2. [Sekmeye gruplar ekleyin](#AddGroupsToTab).  
  
3. [Gruplara denetim ekleyin](#AddControlsToGroups).  
  
   Denetimler sadece gruplar üzerine bırakılabilir; bir denetimi doğrudan bir sekmeye ya da Şerite sürükleyemezsiniz. Gruplar sadece sekmeler üzerine bırakılabilir; bir grubu doğrudan Şerite sürükleyemezsiniz.  
  
   Denetimleri gereken yerlere sürükleyerek düzenleyin. Bir denetimin özelliklerini kullanarak ayarlayabilirsiniz **özellikleri** penceresi.  
  
   Denetimleri bir sekmeden diğerine Şerit üzerinde sürükleyemezsiniz. Başka bir sekmeye bir denetimi taşımak istiyorsanız, kullanmalısınız **Kes** komut denetimi sekmeden kaldırmak ve denetimi başka bir sekmeye yapıştırmalısınız. Denetimi kesip yapıştırırsanız, olay işleyicisi çalışmaz hâle gelir. Olay işleyicisi bağlanabilirsiniz **özellikleri** penceresi. Daha fazla bilgi için [Özellikler penceresi](/visualstudio/ide/reference/properties-window).  
  
###  <a name="AddTabToRibbon"></a> Şeride özel sekmeler ekleme  
 Şerite özel sekme eklemenin üç yolu vardır:  
  
- Bir sekmesinden ekleyin **araç kutusu**.  
  
- Şerit Tasarımcısını sağ tıklayın ve ardından **Şerit sekmesi Ekle**.  
  
- Açık **Sekme Derlemi Düzenleyicisi**ve ardından **Ekle**.  
  
   Açmak için **Sekme Derlemi Düzenleyicisi**, **özellikleri** penceresinde **sekmeleri** özelliği ve ardından üç nokta düğmesine ![ASP.NET Mobil Tasarımcı elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcısı elips").  
  
  Bir sekme ekledikten sonra denetimleri içermesi için gruplar ekleyebilirsiniz.  
  
#### <a name="remove-custom-tabs-from-the-ribbon"></a>Şeritten özel sekmeleri kaldırma  
 Şeritten özel sekme kaldırmanın üç yolu vardır:  
  
-   Tasarımcıyı sağ tıklatın ve ardından **Şerit Sekmesi Kaldır**.  
  
-   İçinde **komutları** bölmesinde **özellikleri** penceresinde tıklayın **Şerit Sekmesi Kaldır**.  
  
-   Açık **Sekme Derlemi Düzenleyicisi**sekmesini seçin ve ardından **Kaldır**.  
  
#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>Şeritteki sekmenin konumunu değiştirme  
 Bir Şeritteki özel sekmelerin sırasını değiştirebilirsiniz. Ayrıca, önce veya sonra Şeritteki yerleşik bir sekmeyi özel sekmeler konumlandırabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Şeritteki sekmenin konumunu değiştirme](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).  
  
#### <a name="customize-built-in-tabs-on-the-ribbon"></a>Şeritteki yerleşik sekmeleri özelleştirme  
 Yerleşik bir sekmeyi bir Microsoft Office uygulamasının Şerit üzerinde zaten var olan bir sekmedir. Örneğin, **veri** Excel yerleşik bir sekmede sekmesidir.  
  
 Yerleşik bir sekmeye grup ve denetim ekleyebilirsiniz. Öncesinde veya sonrasında herhangi bir yerleşik grubun sekmesinde yerini değiştirebilirsiniz ancak varsayılan olarak, özel bir grup yerleşik bir sekmede son grup olarak görünür.  
  
 Varsayılan grupları silemezsiniz.  
  
 Yerleşik sekmelerin nasıl özelleştirildiği hakkında daha fazla ayrıntı için bkz: [nasıl yapılır: yerleşik bir sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md).  
  
###  <a name="AddGroupsToTab"></a> Bir sekmeye grup ekleme  
 Gruplar Şerit üzerindeki denetimleri mantıksal olarak düzenlemek. Sekmelere gruplar ekleyin. Diğer bütün denetimleri grubuna ekleyin.  
  
###  <a name="AddControlsToGroups"></a> Gruplara denetim ekleme  
 Bir gruba bir veya daha fazla denetim ekleyin. Aşağıdaki tabloda, her denetimi açıklanmaktadır.  
  
|Denetim|Açıklama|  
|-------------|-----------------|  
|**Kutusu**|Gruptaki denetimleri düzenleyen bir kapsayıcı. Kutuya ayırıcı, Grup ve sekme haricinde, herhangi bir denetim ekleyebilirsiniz. Bir kutu, yatay veya dikey olabilir.|  
|**Düğme**|Eylem başlatan bir düğme. Bir grup, düğme grubuna, açılır listede, bir galeri, bir menü veya Bölünmüş düğme, bir düğme ekleyebilirsiniz.|  
|**ButtonGroup**|Bir veya daha fazla düğme, iki durumlu düğmeler, menüler, Bölünmüş düğme ve galerilerini içeren grup. Düğme grubunu bir gruba veya menüye ekleyebilirsiniz.|  
|**CheckBox**|Seçilen veya bir seçeneği açıp kapatması için işaretli bir kutu.|  
|**ComboBox**|Liste kutusu ekli bir düzenleme kutusu. Kullanıcılar yazın veya seçerler. Geçerli seçim kutusunu görüntüler. Kullanım <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> özelliğini ekleyip öğelerinin çalışma zamanında önce veya Şerit Office uygulamasına yüklendikten sonra kaldırabilirsiniz.|  
|**Açılan**|Kullanıcının seçebileceği öğelerin listesi. Kullanıcı aşağı açılan listesinde yeni öğe türü.<br /><br /> Kullanım <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> listeye öğe eklemek için özellik. Ekleme ve çalışma zamanında öğeleri kaldırın.<br /><br /> Kullanım <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> listeye düğme eklemek için özellik. Ancak, ekleyin ve düğmeleri, Şerit Office uygulamasına yüklendikten sonra çalışma zamanında kaldırın.|  
|**EditBox**|Kullanıcının metin yazabileceği bir kutu.|  
|**Galeri**|Bir menü, bir dizi ya da kullanıcıların seçebileceği görsel seçimler kılavuzunun sunar. Menüdeki seçimlerin düzenini denetleyebilirsiniz. Kullanım <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> ve <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> satır ve öğeleri görüntüler sütun sayısı ve galerinin düğmeleri belirtmek için özellikleri.|  
|**Etiket**|Şerit üzerindeki denetimleri tanımlamak için kullanabileceğiniz metin.|  
|**Menü**|Aşağıdaki denetimleri içerebilen bir açılan liste:<br /><br /> -Düğme<br />-Onay kutusu<br />-Galerisi<br />-Menü<br />-Bölünmüş düğme<br />-İki durumlu düğme<br />-Ayırıcı<br /><br /> Şerit tasarımcısındaki bir menüye denetim eklemek için menü tasarım yüzeyini göstertmek amacıyla menünün aşağı oka tıklayın. Sonra Şerit denetimlerini sürükleyebilirsiniz **araç kutusu** menüye. Denetimleri düzenlemek amacıyla istediğiniz yere sürükleyin.<br /><br /> Denetimler eklemek için <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> Şerit Office uygulamasına yüklendikten sonra ayarlamalısınız <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> özelliğini **true** Şerit yüklenmeden önce. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [Şerit nesne modeline genel bakış](../vsto/ribbon-object-model-overview.md).|  
|**Ayıraç**|Bir listedeki öğeleri ayırmak için kullanılan ince bir çubuk. Bir gruba eklendiğinde çubuk dikey olur. Bir menüye eklendiğinde çubuk yatay olur.|  
|**SplitButton**|Menü iliştirilmiş bir düğme. Bölünmüş düğme aşağıdaki denetimleri içerebilir:<br /><br /> -Düğme<br />-Onay kutusu<br />-Galerisi<br />-Menü<br />-Bölünmüş düğme<br />-İki durumlu düğme<br />-Ayırıcı<br /><br /> Menü gibi Bölünmüş düğme, kendi tasarım yüzeyi vardır. Şerit Office uygulamasına yüklenmeden önce ancak, menüye benzemeyen, yalnızca Bölünmüş düğmedeki öğeleri güncelleştirebilirsiniz. Bölünmüş düğmedeki öğeleri güncelleştirme hakkında daha fazla bilgi için bkz: [Şerit nesne modeline genel bakış](../vsto/ribbon-object-model-overview.md).|  
|**ToggleButton**|Basılı ya da basılmamış görünen bir düğme.|  
  
##  <a name="HandleEventsSetProperties"></a> Olayları ve özelliklerini ayarlama  
 Şerit Tasarımcısını kullanarak tasarım zamanında denetim özelliklerini ayarlamanıza olanak tanır **özellikleri** penceresi. Ayrıca, Şerit almak ve çalışma zamanında Şerit denetimlerinin özelliklerini ayarlamak için kullanabileceğiniz bir türü kesin belirlenmiş nesne modeli sağlar.  
  
 Denetimin varsayılan olayı için olay işleyicisi açmak için tasarımcıda herhangi bir denetime çift tıklayabilirsiniz. Diğer bütün denetim olayları için olay işleyicileri kullanarak oluşturabileceğiniz **özellikleri** penceresi.  
  
 Şerit olayları ve özellikleri yerleştirilir <xref:Microsoft.Office.Tools.Ribbon> ad alanı. **Şerit (Görsel Tasarımcı)** öğesine otomatik olarak projedeki bu derlemeye bir başvuru ekler ve uygun ekler **kullanarak** veya **içeri aktarmalar** üst deyimi Şerit kod dosyasını.  
  
 Şerit olaylarını işleme ve Şerit denetimlerini çalışma zamanında ayarlama hakkında daha fazla bilgi için bkz: [Şerit nesne modeline genel bakış](../vsto/ribbon-object-model-overview.md).  
  
##  <a name="CustomizingMicrosoftOfficeButton"></a> Backstage görünümünü özelleştirme  
 Şerit Tasarımcısı tıkladığınızda açılan menüye denetimler eklemek için kullanabileceğiniz **dosya** sekmesi. Bu menü, Backstage görünümü olarak adlandırılır.  
  
 Şerit Tasarımcısını kullanarak, önce veya sonra yerleşik denetimlerin denetimler yerleştiremezsiniz. Yerleşik denetim, Backstage görünümünde önceden görüntülenen bir denetimdir. Önce veya sonra yerleşik denetimlerin yerleştirmenize istiyorsanız Şerit XML kullanmalısınız. Hakkında daha fazla bilgi için **Ribbon (XML)**, bkz: [Ribbon XML](../vsto/ribbon-xml.md). Backstage görünümünü özelleştirme hakkında daha fazla bilgi için bkz. [geliştiriciler için Office 2010 Backstage görünümüne giriş](http://go.microsoft.com/fwlink/?LinkId=182189) ve [geliştiriciler için Office 2010 Backstage görünümünü özelleştirme](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]  
  
 Backstage görünümüne denetimler ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Backstage görünümüne denetimler ekleme](../vsto/how-to-add-controls-to-the-backstage-view.md).  
  
##  <a name="Accessibility"></a> Şerit Tasarımcısında erişilebilirlik  
 Şerit Tasarımcısında denetimleri taşımak için klavye kısayollarını kullanabilirsiniz. Bazı klavye kısayolları tüm denetimlere ve bazı menüsü olan denetimlere uygulanır.  
  
 Aşağıdaki tabloda bütün denetimlere uygulanan klavye kısayolları gösterilmektedir.  
  
|Eylem|Klavye kısayolu|  
|------------|-----------------------|  
|Listeden bir denetimi önceki denetimin önüne taşıma.|**CTRL**+**ayarlama**<br /><br /> **CTRL**+**sol**|  
|Bir denetimi, listedeki sonraki denetimin arkasına taşıma.|**CTRL**+**aşağı**<br /><br /> **CTRL**+**sağ**|  
|Seçimi bir denetimden aynı gruptaki başka bir taşıma. Açılır panel için üst denetim ve açılır panel denetimleri arasında taşıyın.|**Ayarlama**<br /><br /> **Aşağı**|  
|Tüm denetim boyunca ileri doğru yineleme.|**sekmesi**|  
|Tüm denetim boyunca geriye doğru yineleme.|**Shift**+**sekmesi**|  
|Seçili denetimi veya denetim kümesini silin.|**Delete**|  
|Seçili denetimleri kopyalayın.|**CTRL**+**C**|  
|Seçili denetimleri kesin.|**CTRL**+**X**|  
|Panodaki denetimi yapıştırma.|**CTRL**+**V**|  
|Seçin **araç kutusu**.|**CTRL**+**Alt**+**X**|  
|Üst bileşeni seçin.|**ESC**|  
  
 Yalnızca Microsoft Office Menu, uygulanan klavye kısayolları <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>, ve <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> aşağıdaki tabloda gösterilmiştir.  
  
|Eylem|Klavye kısayolu|  
|------------|-----------------------|  
|Açılır panel açık ve bir denetim seçiliyken açılır paneli üzerinde olduğundan üst denetimi seçin.|**Sol**|  
|Açılır panel açık ve üst denetim seçiliyken açılır paneli kapatma.|**Sol**|  
|Açılır paneli açma.|**sağ**|  
|Açılır panel açıkken birinci açılır panel denetimi seçin.|**sağ**|  
|Açılır paneli kapatma.|**ESC**|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Şerite Genel Bakış](../vsto/ribbon-overview.md)   
 [Şerit XML](../vsto/ribbon-xml.md)   
 [İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Nasıl yapılır: Şerit Şerit Tasarımcısından Şerit XML'ine verebilir.](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Nasıl yapılır: Şerit özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Şerit, çalışma zamanında erişme](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  