---
title: Şerit nesne modeline genel bakış
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 25e34dcb38685a885ae0730740c25e1cb502e15c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910595"
---
# <a name="ribbon-object-model-overview"></a>Şerit nesne modeline genel bakış
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Almak ve çalışma zamanında Şerit denetimlerinin özelliklerini ayarlamak için kullanabileceğiniz sağlam biçimde yazılmış nesne modeli sunar. Örneğin, dinamik olarak menü denetimlerini doldurmak veya gösterebilir ve bağlamsal denetimlerini gizle. Şerit, ancak yalnızca Şerit tarafından Office uygulamasına yüklenmeden önce sekmeler, gruplar ve denetimler de ekleyebilirsiniz. Bilgi için [salt okunur özelliklerini ayarlama](#SettingReadOnlyProperties).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Şerit nesne modeli çoğunlukla oluşan [Şerit sınıfı](#RibbonClass), [Şerit olaylarını](#RibbonEvents), ve [Şerit denetim sınıfları](#RibbonControlClasses).  
  
##  <a name="RibbonClass"></a> Şerit sınıfı  
 Yeni bir eklediğinizde **Şerit (Görsel Tasarımcı)** öğesi için bir proje, Visual Studio ekler bir **Şerit** projenize sınıfı. **Şerit** sınıfının devraldığı <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> sınıfı.  
  
 Bu sınıf, Şerit kod dosyasını ve Şerit Tasarımcısı kod dosyası arasında bölünür kısmi bir sınıf olarak görünür.  
  
##  <a name="RibbonEvents"></a> Şerit olayları  
 **Şerit** sınıfı, aşağıdaki üç olaylar içerir:  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Office uygulamasının Şerit Özelleştirmelerini yüklediğinde oluşur. <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> Olay işleyicisi Şerit kod dosyasına otomatik olarak eklenir. Bu olay işleyicisi, Şerit yüklediğinde, özel kod çalıştırmak için kullanın.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Şerit yüklediğinde, Şerit Özelleştirmelerini önbellek görüntüleri sağlar. Bu olay işleyicisi Şerit görüntüleri önbelleğe almak için kod yazma, küçük bir performans kazancı elde edebilirsiniz. Daha fazla bilgi için bkz. <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Şerit örneği kapandığında ortaya çıkar.|  
  
##  <a name="RibbonControlClasses"></a> Şerit denetimleri  
 <xref:Microsoft.Office.Tools.Ribbon> Ad alanı içeren bir tür gördüğünüz her denetim için **Office Şerit denetimleri** grubunu **araç kutusu**.  
  
 Türü her biri için aşağıdaki tabloda gösterilir `Ribbon` denetimi. Her denetim açıklaması için bkz: [Şerite Genel Bakış](../vsto/ribbon-overview.md).  
  
|Denetim adı|Sınıf adı|  
|------------------|----------------|  
|**Kutusu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**Düğme**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|  
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|  
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|  
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|  
|**Açılan**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|  
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Galeri**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**Grup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Etiket**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|  
|**Menü**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Ayıraç**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**sekmesi**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
  
 <xref:Microsoft.Office.Tools.Ribbon> Ad alanı adları ile denetim sınıflarda oluşan bir ad çakışması önlemek için bu tür için "Şeridinde" önekini kullanır <xref:System.Windows.Forms> ad alanı.  
  
 Şerit Tasarımcısı Şerit Tasarımcısına denetim eklediğinizde, denetimin sınıfı Şerit Tasarımcısı kod dosyasında bir alan olarak bildirir.  
  
### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Şerit denetimlerinin özelliklerini kullanarak ortak görevleri  
 Her `Ribbon` denetimi içeren bir denetim için etiket atama veya gizleme ve gösterme gibi çeşitli görevleri gerçekleştirmek için kullanabileceğiniz özellikler.  
  
 Bazı durumlarda, özellikleri Şerit yükledikten sonra veya bir denetimi dinamik bir menüye eklendikten sonra salt okunur hale gelir. Daha fazla bilgi için [salt okunur özelliklerini ayarlama](#SettingReadOnlyProperties).  
  
 Aşağıdaki tablo kullanarak gerçekleştirebileceğiniz görevlerden bazılarını açıklar `Ribbon` denetim özellikleri.  
  
|Bu görev için:|Bunu yapın:|  
|--------------------|--------------|  
|Gizleme veya bir denetimi gösterir.|Visible özelliği kullanın.|  
|Etkinleştirmek veya devre dışı bırakmak.|Enabled özelliğini kullanın.|  
|Bir denetimin boyutunu ayarlayın.|ControlSize özelliğini kullanın.|  
|Bir denetimde görünen resmi alın.|Görüntü özelliğini kullanın.|  
|Bir denetimin etiketi değiştirin.|Etiket özelliğini kullanın.|  
|Kullanıcı tanımlı veri denetimi ekleyin.|Tag özelliği kullanın.|  
|Öğeleri al bir <xref:Microsoft.Office.Tools.Ribbon.RibbonBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>, veya<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> denetimi.|Items özelliğini kullanın.|  
|Öğe ekleme bir <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, veya <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> denetimi.|Items özelliğini kullanın.|  
|Denetimlere ekleme bir <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>.|Items özelliğini kullanın.<br /><br /> Denetimler eklemek için <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> Şerit Office uygulamasına yüklendikten sonra ayarlamalısınız <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> özelliğini **true** Şerit Office uygulamasına yüklenmeden önce. Bilgi için [salt okunur özelliklerini ayarlama](#SettingReadOnlyProperties).|  
|Seçilen öğenin almak bir <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, veya <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|SelectedItem özelliği kullanın. İçin bir <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, kullanın <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> özelliği.|  
|Grupları Al bir <xref:Microsoft.Office.Tools.Ribbon.RibbonTab>.|Kullanım <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A> özelliği.|  
|Satırları ve sütunları görünen sayısını bir <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Kullanım <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> ve <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> özellikleri.|  
  
##  <a name="SettingReadOnlyProperties"></a> Salt okunur özelliklerini ayarlama  
 Bazı özellikler, yalnızca Şerit yüklenmeden önce ayarlanabilir. Bu özellikleri ayarlamak için üç yer vardır:  
  
- Visual Studio **özellikleri** penceresi.  
  
- Oluşturucusunun içinde **Şerit** sınıfı.  
  
- İçinde `CreateRibbonExtensibilityObject` yöntemi `ThisAddin`, `ThisWorkbook`, veya `ThisDocument` projenizin sınıfı.  
  
  Dinamik menüler, bazı özel durumlar sağlar. Yeni denetimler oluşturun, özelliklerini ayarlamayı ve bile menüyü içeren Şerit yüklendikten sonra daha sonra bunları çalışma zamanında, bir dinamik menüyü ekleyin.  
  
  Herhangi bir zamanda bir Dinamik menü eklediğiniz denetimin özelliklerini ayarlayabilirsiniz.  
  
  Daha fazla bilgi için [salt okunur özellikler](#ReadOnlyProperties).  
  
### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>Şerit oluşturucuda özelliklerini ayarlama  
 Özelliklerini ayarlayabileceğiniz bir `Ribbon` oluşturucusunun denetiminde **Şerit** sınıfı. Bu kod çağrısından sonra görünmelidir `InitializeComponent` yöntemi. Aşağıdaki örnekte geçerli saat 17:00 ise yeni bir düğme bir gruba ekler. Pasifik Saati (UTC-8) veya üzeri.  
  
 Aşağıdaki kodu ekleyin.  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]  
  
 Görselde C# Visual Studio 2008'den yükseltilmiş projeleri Oluşturucusu Şerit kod dosyasında görünür.  
  
 Görselde veya Visual Basic projelerinde C# oluşturduğunuz projeleri [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], oluşturucu Şerit Tasarımcısı kod dosyasında görünür. Bu dosya adlı *ŞeritÖğeniz*. Designer.cs veya *ŞeritÖğeniz*. Designer.vb olarak adlandırılır. Bu dosyayı Visual Basic projelerinde görmek için önce tıklatmalısınız **tüm dosyaları göster** Çözüm Gezgini'nde düğmesi.  
  
### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>Yöntemini kümesi özellikleri  
 Özelliklerini ayarlayabileceğiniz bir `Ribbon` ne zaman geçersiz kılmanız denetim `CreateRibbonExtensibilityObject` yöntemi `ThisAddin`, `ThisWorkbook`, veya `ThisDocument` projenizin sınıfı. Hakkında daha fazla bilgi için `CreateRibbonExtensibilityObject` yöntemi bkz [Şerite Genel Bakış](../vsto/ribbon-overview.md).  
  
 Aşağıdaki örnek Şerit özellikleri ayarlar `CreateRibbonExtensibilityObject` yöntemi `ThisWorkbook` bir Excel çalışma kitabı projesi sınıfı.  
  
 Aşağıdaki kodu ekleyin.  
  
 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]  
  
###  <a name="ReadOnlyProperties"></a> Salt okunur özellikler  
 Aşağıdaki tabloda, Şerit yüklemeden önce yalnızca ayarlanabilir özelliklerini gösterir.  
  
> [!NOTE]  
>  Herhangi bir zamanda Dinamik menüdeki denetimlerin özelliklerini ayarlayabilirsiniz. Bu tabloda bu durumda geçerli değildir.  
  
|Özellik|Şerit denetimi sınıfı|  
|--------------|--------------------------|  
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**columnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**Zadejte vlastnosti ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Dinamik**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Genel**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Grupları**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**Görüntü adı**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**maxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Ad**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|  
|**Konumu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Satır sayısı**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Sekmeleri**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Başlık**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
  
### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Outlook denetçilerinin içinde görünür şeritler özelliklerini ayarlama  
 Şeritteki yeni bir örneğini bir kullanıcı bir denetçi Şerit göründüğü her açtığında oluşturulur. Ancak, yalnızca Şerit ilk örneği oluşturulmadan önce yukarıdaki tabloda listelenen özellikleri ayarlayabilirsiniz. Sonra ilk örneği oluşturulduğunda, bu özellikleri ilk örnek XML dosyasının şeridi yüklemek için Outlook kullanan tanımladığından salt okunur hale gelir.  
  
 Şerit diğer örnekleri oluşturulduğunda, bu özelliklerden herhangi birini farklı bir değer ayarlar, koşullu mantık varsa, bu kodu herhangi bir etkisi gerekir.  
  
> [!NOTE]  
>  Emin **adı** Outlook Şeridine eklediğiniz her denetimin özelliğini ayarlayın. Outlook Şeridine çalışma zamanında denetim ekleme, kodunuzda bu özelliği ayarlayın gerekir. Outlook Şeridine tasarım zamanında denetim ekleme, Name özelliği otomatik olarak ayarlanır.  
  
## <a name="ribbon-control-events"></a>Şerit denetim olayları  
 Her denetim sınıfı bir veya daha fazla etkinlik içermiyor. Aşağıdaki tabloda, bu olayları açıklar.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|Şuna tıklayın|Bir denetim tıklandığında gerçekleşir.|  
|TextChanged|Metin düzenleme kutusu veya açılan kutusu değiştirildiğinde gerçekleşir.|  
|ItemsLoading|Denetim öğeleri koleksiyonu Office tarafından istendiğinde oluşur. Office önbelleğe öğe koleksiyonunun kodunuzu denetimin özelliklerini değiştirir veya çağırmanızı kadar <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> yöntemi.|  
|ButtonClick|Bir düğme bir <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> veya <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> tıklandığında.|  
|SelectionChanged|Gerçekleşir, seçimdeki bir <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> veya <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> değişiklikler.|  
|DialogLauncherClick|Bir grubun sağ alt köşedeki iletişim kutusu başlatıcısı simgesine tıklandığında gerçekleşir.|  
  
 Bu olayları için olay işleyicileri aşağıdaki iki parametreye sahip.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|*Gönderen*|Bir <xref:System.Object> olayı denetimi temsil eder.|  
|*e*|A <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> içeren bir <xref:Microsoft.Office.Core.IRibbonControl>. Şerit nesne modeli tarafından sağlanan mevcut değil herhangi bir özelliğe erişmek için bu denetimi kullanın [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Şerit, çalışma zamanında erişme](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Şerite Genel Bakış](../vsto/ribbon-overview.md)   
 [Nasıl yapılır: Şerit özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Şerit Tasarımcısı](../vsto/ribbon-designer.md)   
 [İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [İzlenecek yol: çalışma zamanında Şerit denetimlerini güncelleştirme](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Outlook için Şerit özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Nasıl yapılır: yerleşik bir sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md)   
 [Nasıl yapılır: Backstage görünümüne denetimler ekleme](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Nasıl yapılır: Şerit Şerit Tasarımcısından Şerit XML'ine verebilir.](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Nasıl yapılır: kullanıcı arayüzü hatalarını gösterme eklentisi](../vsto/how-to-show-add-in-user-interface-errors.md)  
 