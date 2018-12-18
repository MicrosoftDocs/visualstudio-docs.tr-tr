---
title: İçerik denetimleri
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.DropDownListContentControl
- VST.Toolbox.RichTextContentControl
- VST.Toolbox.PlainTextContentControl
- VST.Toolbox.ComboBoxContentControl
- VST.Toolbox.CCBuildingBlockGalleryContentControl
- VST.Toolbox.DatePickerContentControl
- VST.Toolbox.PictureContentControl
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document building blocks [Office development in Visual Studio]
- restricted permissions [Office development in Visual Studio]
- ComboBoxContentControl class
- PictureContentControl class
- PlainTextContentControl class
- Office documents [Office development in Visual Studio], restricted permissions
- RichTextContentControl class
- content controls [Office development in Visual Studio]
- building block gallery [Office development in Visual Studio]
- controls [Office development in Visual Studio], content controls
- GroupContentControl class
- documents [Office development in Visual Studio], restricted permissions
- DropDownListContentControl class
- DatePickerContentControl class
- data binding [Office development in Visual Studio], content controls
- content controls [Office development in Visual Studio], about content controls
- custom XML parts, content controls
- templates [Office development in Visual Studio], content controls
- BuildingBlockGalleryContentControl class
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 924f31ac38219453ae96fd573d968b18ce19c913
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672905"
---
# <a name="content-controls"></a>İçerik denetimleri
  İçerik denetimleri tasarım belgeleri ve bu özelliklere sahip şablonları sağlamak sizin için bir yol:  
  
- Girdileri form gibi uygulanmayacaksa bir kullanıcı arabirimi (UI).  
  
- Kullanıcıların belgenin veya şablonun korunan bölümlerini düzenlemesini önlemek kısıtlamaları. Daha fazla bilgi için [içerik denetimlerini kullanarak belge bölümlerini koruma](#Protection).  
  
- Bir veri kaynağına veri bağlama. Daha fazla bilgi için [içerik denetimlerine veri bağlama](#DataBinding).  
  
  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
  ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz. [Word 2007 için veri bağlama denetimleri Office sistemi (3.0) için Visual Studio araçları kullanarak içerik](http://go.microsoft.com/fwlink/?LinkId=136785).  
  
## <a name="overview-of-content-controls"></a>İçerik denetimlerine genel bakış  
 İçerik denetimleri, her iki kullanıcı için giriş ve yazdırma için iyileştirilmiş bir kullanıcı Arabirimi sağlar. Belge bir içerik denetimi eklediğinizde, denetimin kenarlık, bir başlık ve kullanıcıya yönergeler sağlayan geçici metin tarafından tanımlanır. Kenarlık ve denetimi başlığı belge yazdırılan sürümlerde görünmez.  
  
 Örneğin, bir tarih belgenizin bir bölümde girmesini istiyorsanız, belgeye bir tarih seçici içerik denetimi ekleyebilirsiniz. Kullanıcı denetime tıkladığınızda, standart tarih seçici kullanıcı Arabirimi görüntülenir. Görüntülenen bölgesel bir takvim ve tarih biçimi belirtmek için denetimin özellikleri de ayarlayabilirsiniz. Kullanıcının bir tarih seçtikten sonra kullanıcı Arabirimi denetimi gizlenir ve kullanıcı belgeyi yazdırır yalnızca tarih görüntülenir.  
  
 İçerik, ayrıca Yardım aşağıdakileri denetler:  
  
- Kullanıcının düzenleme veya belge parçalarını silmesini engeller. Bu, bir belge veya kullanıcıların okuma, ancak düzenleyemez şablon bilgileri varsa veya kullanıcıların içerik denetimleri Düzen ancak silme istiyorsanız kullanışlıdır.  
  
- Bir belge veya şablon bölümleri verilere bağlayın. İçerik denetimleri veritabanı alanları, yönetilen nesneleri adlarınıza bağlayabileceğiniz [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)], belge ve diğer veri kaynakları depolanan XML öğeleri.  
  
  Belge düzeyinde projelerde belgenize tasarım zamanında veya çalışma zamanında içerik denetimlerine ekleyebilirsiniz. VSTO eklenti projesinde herhangi bir açık belgeye çalışma zamanında içerik denetimlerine ekleyebilirsiniz. Daha fazla bilgi için [nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
> [!NOTE]  
>  Open XML biçiminde kaydedilen belgelerde içerik denetimleri kullanabilirsiniz. Word 97-2003 belgesi kaydedilen belgelerde içerik denetimlerini kullanamazsınız (*.doc*) biçimi.  
  
## <a name="types-of-content-controls"></a>İçerik denetimi türleri  
 Dokuz farklı belgelere ekleyebileceğiniz içerik denetimi türleri vardır. İçerik denetimleri çoğunu olmayan karşılık gelen türü <xref:Microsoft.Office.Tools.Word> ad alanı. Genel kullanabilirsiniz <xref:Microsoft.Office.Tools.Word.ContentControl>, hangi temsil edebilir kullanılabilir içerik denetimleri. Her kullanılabilir içerik denetimlerini nasıl kullanılacağını gösteren bir kılavuz için bkz. [izlenecek yol: içerik denetimlerini kullanarak şablon oluşturma](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).  
  
### <a name="build-block-gallery"></a>Yapı Taşı Galerisi  
 Kullanıcılar bir listesinden seçmek bir Yapı Taşı Galerisi sağlar *belge yapı taşları* belgeye eklenecek. Bir belge yapı taşı, yaygın bir kapak sayfası, biçimlendirilmiş bir tablo veya bir üst bilgisi gibi birden çok kez kullanılmak üzere oluşturulan içerik parçasıdır. Daha fazla bilgi için <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> türü. Yapı taşları hakkında daha fazla bilgi için bkz. [Word 2007'de geliştiricilerine yönelik yenilikler](/previous-versions/office/developer/office-2007/bb266218(v=office.12)).  
  
### <a name="check-box"></a>Onay kutusu  
 Bir onay kutusu ikili durumunu temsil eden bir kullanıcı Arabirimi sağlar: seçilen veya temizlenen.  
  
 İçerik denetimleri, diğer türlerinin aksine [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] onay kutusu içerik denetimi temsil eden belirli bir tür sağlamaz. Diğer bir deyişle, var olan hiçbir `CheckBoxContentControl` türü. Ancak hala bir onay kutusu içerik denetimi genel ekleyerek oluşturabilirsiniz <xref:Microsoft.Office.Tools.Word.ContentControl> belgeye programlı olarak. Daha fazla bilgi için [onay kutusu içerik denetimi Word projelerinde](#checkbox).  
  
### <a name="combo-box"></a>Birleşik giriş kutusu  
 Birleşik giriş kutusu kullanıcıların seçebileceği öğe listesini görüntüler. Aşağı açılan listesinde, birleşik giriş kutusu kendi öğelerini eklemesine olanak sağlar. Daha fazla bilgi için <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> türü.  
  
### <a name="date-picker"></a>Tarih Seçici  
 Bir tarih seçmek için Takvim kullanıcı Arabirimi tarih seçici sağlar. Takvim, son kullanıcı denetiminde açılan liste okunu tıkladığında görüntülenir. Bölgesel takvimler ve farklı tarih biçimleri kullanabilirsiniz. Daha fazla bilgi için <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> türü.  
  
### <a name="drop-down-list"></a>Aşağı açılan listesi  
 Açılır listede, kullanıcıların seçebileceği öğelerin bir listesini görüntüler. Birleşik giriş kutusu, aşağı açılan liste öğeleri ekleyin veya düzenleyin, kullanıcıların izin vermez. Daha fazla bilgi için <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> türü.  
  
### <a name="group"></a>Grup  
 Grup denetim kullanıcılar düzenleyemeyeceğiniz veya silemeyeceğiniz bir belgenin korumalı bir bölgeyi tanımlar. Grup denetim, metin, tablolar, grafik ve diğer içerik denetimleri gibi herhangi bir belge öğesi içerebilir. Daha fazla bilgi için <xref:Microsoft.Office.Tools.Word.GroupContentControl> türü.  
  
### <a name="picture"></a>Resim  
 Bir resim denetimi, bir resim görüntüler. Tasarım zamanında resmi belirtin veya çalışma zamanı ya da bu denetim, belgede eklemek için görüntü seçmek için tıklatabileceği. Daha fazla bilgi için <xref:Microsoft.Office.Tools.Word.PictureContentControl> türü.  
  
### <a name="rich-text"></a>Zengin metin  
 Zengin metin denetimi, metin veya tabloları, resimleri veya diğer içerik denetimleri gibi diğer öğeleri içerir. Daha fazla bilgi için <xref:Microsoft.Office.Tools.Word.RichTextContentControl> türü.  
  
### <a name="plain-text"></a>Düz metin  
 Metin düz metin denetimi içerir. Düz metin denetimi, tablo, resimleri veya diğer içerik denetimleri gibi diğer öğeler içeremez. Ayrıca, tüm düz metin denetimdeki metin sahiptir ve aynı biçimlendirme. Örneğin, bir sözcüğün bir düz metin denetimi bir cümle italik, denetimin içindeki tüm metni italik. Daha fazla bilgi için <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> türü.  
  
### <a name="generic-content-control"></a>Genel içerik denetimi  
 Genel bir içerik denetimi bir <xref:Microsoft.Office.Tools.Word.ContentControl> içerik denetimleri kullanılabilir türlerinden herhangi birini temsil eden nesne. Değiştirebileceğiniz bir <xref:Microsoft.Office.Tools.Word.ContentControl> kullanarak farklı türde bir içerik denetimi gibi davranmaya nesne <xref:Microsoft.Office.Tools.Word.ContentControl.Type%2A> özelliği. Örneğin, oluşturduğunuz bir <xref:Microsoft.Office.Tools.Word.ContentControl> nesnesini temsil eder bir düz metin denetimini, birleşik giriş kutusu gibi davranması çalışma zamanında değiştirebilirsiniz.  
  
 Oluşturabileceğiniz <xref:Microsoft.Office.Tools.Word.ContentControl> nesneleri yalnızca çalışma zamanında, tasarım zamanında. Daha fazla bilgi için [nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
## <a name="common-features-of-content-controls"></a>İçerik denetimleri genel özellikleri  
 Çoğu içerik denetimleri ortak görevleri gerçekleştirmek için kullanabileceğiniz üyelerin kümesini paylaşır. Aşağıdaki tabloda, bu üyeler kullanarak gerçekleştirebileceğiniz görevlerden bazıları açıklanmaktadır.  
  
|Bu görev için:|Bunu yapın:|  
|--------------------|--------------|  
|Alma veya denetimde görüntülenen metni ayarlama.|Kullanım **metin** özelliği. **Not:** <xref:Microsoft.Office.Tools.Word.PictureContentControl> ve <xref:Microsoft.Office.Tools.Word.ContentControl> türleri bu özelliğe sahip değildir.|  
|Alın veya bir kullanıcı denetimi Düzenleyene, denetim bir veri kaynağı ile doldurulur veya denetimin içeriği silinene kadar denetimde görüntülenen metnin geçici ayarlayın.|Kullanım **PlaceholderText** özelliği. **Not:** <xref:Microsoft.Office.Tools.Word.PictureContentControl> türü, bu özelliğe sahip değildir.|  
|GET veya kullanıcı tıkladığında içerik denetiminin kenarlık görüntülenen başlığı ayarlayın.|Kullanım **başlık** özelliği.|  
|Kullanıcı denetimi Düzenleyene sonra Denetim belgeden otomatik olarak kaldırın. (Metin denetiminde belgede kalır.)|Kullanım **geçici** özelliği.|  
|Kullanıcı içerik denetimine tıkladığında veya imleci içerik denetimine programlı olarak taşındığında kodu çalıştırın.|Tanıtıcı <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> Olay denetimi.|  
|İçerik denetimi dışında kullanıcı tıkladığında veya imleci programlı bir şekilde içerik denetimi dışında hareket ettiğinde kodu çalıştırın.|Tanıtıcı <xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting> Olay denetimi.|  
|İçerik denetimi, yineleme bir belgeye eklendikten sonra kodu çalıştırmak veya geri alma işlemi.|Tanıtıcı <xref:Microsoft.Office.Tools.Word.ContentControlBase.Added> Olay denetimi.|  
|Belge içerik denetimi yalnızca silinmeden önce kodu çalıştırın.|Tanıtıcı <xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting> Olay denetimi.|  
  
##  <a name="Protection"></a> İçerik denetimlerini kullanarak belge bölümlerini koruma  
 Belgenin bir bölümünü koruduğunuzda, kullanıcıların belgenin bu bölümü içeriğini silme veya değiştirme engeller. İçerik denetimlerini kullanarak belge bölümlerini koruyabilmeniz için birkaç yol vardır.  
  
 Bir içerik denetimi içinde korumak istediğiniz alan ise kullanıcıların düzenleme veya silmesini önlemek için içerik denetimi özelliklerini kullanabilirsiniz:  
  
- **LockContents** özelliği kullanıcılar içeriği düzenlemesini engeller.  
  
- **LockContentControl** özelliği kullanıcılar silmesini engeller.  
  
  Korumak istediğiniz alanı içinde bir içerik denetimi değilse veya içerik denetimleri ve diğer içerik türlerini içeren bir alan korumak istiyorsanız, size tüm alanı koyabilirsiniz bir <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Diğer içerik denetimleri farklı bir <xref:Microsoft.Office.Tools.Word.GroupContentControl> kullanıcıya görünür olan kullanıcı Arabirimi sağlar. Tek amacı, kullanıcıların düzenleyemeyeceği bir bölge tanımlamaktır.  
  
> [!NOTE]  
>  Oluşturursanız, bir <xref:Microsoft.Office.Tools.Word.GroupContentControl> katıştırılmış içerik denetimleri içeren, katıştırılmış içerik denetimleri otomatik olarak korunmaz. Kullanmalısınız **LockContents** her özellik katıştırılmış kullanıcıların içeriklerini düzenlemesini önlemek için denetimi.  
  
 İçerik denetimleri belge bölümlerini koruma için nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: içerik denetimlerini kullanarak belge bölümlerini koruma](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
##  <a name="DataBinding"></a> İçerik denetimlerine veri bağlama  
 Bir içerik denetimi veri kaynağına bağlayarak veri belgeleri görüntüleyebilirsiniz. Veri kaynağı güncelleştirildiğinde, içerik denetimi değişiklikleri yansıtır. Ayrıca, değişiklikleri veri kaynağına kaydedebilirsiniz.  
  
 İçerik denetimleri, veri bağlama seçenekler aşağıda belirtilmiştir:  
  
- İçerik denetimleri, Windows Forms aynı veri bağlama modelini kullanarak veritabanı alanları veya yönetilen nesnelere bağlayabilirsiniz.  
  
- İçerik denetimleri, XML parçalarının öğelere bağlayabilirsiniz (olarak da adlandırılan *özel XML bölümleri*) belge içinde gömülü.  
  
  Konak denetimleri Office çözümlerinde veri bağlama genel bakış için bkz: [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
### <a name="use-the-windows-forms-data-binding-model"></a>Windows Forms veri bağlama modelini kullanın  
 Çoğu içerik denetimleri, Windows Forms kullanan basit veri bağlama modelini destekler. Basit veri bağlama, bir denetim bir veri tablosunun bir sütunu bir değer gibi bir tek veri öğesine bağlı olduğu anlamına gelir. Daha fazla bilgi için [veri bağlama ve Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
 Belge düzeyinde projelerde verileri içerik denetimlerini kullanarak bağlayabilirsiniz **veri kaynakları** penceresinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Belgeler için içerik verilere bağlı denetimler ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: belgeleri veritabanı verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md) ve [nasıl yapılır: belgeleri nesne verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md).  
  
 Aşağıdaki tabloda her bir veri türü adlarınıza bağlayabileceğiniz içerik denetimleri listeler **veri kaynakları** penceresi.  
  
|Veri türü|Varsayılan içerik denetimi|Bu veri türüne bağlı diğer içerik denetimleri|  
|---------------|-----------------------------|----------------------------------------------------------------|  
|<xref:System.Boolean><br /><br /> <xref:System.Byte><br /><br /> <xref:System.Char><br /><br /> <xref:System.Double><br /><br /> <xref:System.Enum><br /><br /> <xref:System.Guid><br /><br /> <xref:System.Int16><br /><br /> <xref:System.Int32><br /><br /> <xref:System.Int64><br /><br /> <xref:System.SByte><br /><br /> <xref:System.Single><br /><br /> <xref:System.String><br /><br /> <xref:System.TimeSpan><br /><br /> <xref:System.UInt16><br /><br /> <xref:System.UInt32><br /><br /> <xref:System.UInt64>|<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|  
|<xref:System.DateTime>|<xref:Microsoft.Office.Tools.Word.DatePickerContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|  
|<xref:System.Drawing.Image><br /><br /> <xref:System.Byte> Dizi|<xref:Microsoft.Office.Tools.Word.PictureContentControl>|Yok.|  
  
 Belge düzeyi ve VSTO eklentisi projeleri, bir içerik denetimi veri kaynağına program aracılığıyla kullanarak bağlayabilirsiniz <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> yöntemi <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> denetiminin özelliği. Bunu yaparsanız bir dizeyi geçirmek **metin** için *propertyName* parametresinin <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> yöntemi. **Metin** içerik denetimleri için varsayılan veri bağlama özelliği bir özelliktir.  
  
 İçerik denetimleri de denetiminde değişiklikleri veri kaynağına güncelleştirilir, iki yönlü veri bağlamayı destekler. Daha fazla bilgi için [nasıl yapılır: konak kontrolü verileriyle veri kaynağını güncelleme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
> [!NOTE]  
>  İçerik denetimleri, karmaşık veri bağlamayı desteklemez. Bağlarsanız bir <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> veya <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> denetimi tıkladıklarında bir veri kaynağına Windows Forms veri modelini kullanarak, kullanıcılar yalnızca tek bir değer görürsünüz. Bu denetimler, kullanıcıların seçebileceği veri değerlerini bir dizi bağlamak istiyorsanız, özel bir XML parçasına öğeleri bu denetimler bağlayabilirsiniz.  
  
### <a name="bind-content-controls-to-custom-xml-parts"></a>İçerik denetimlerini özel XML bölümlerine bağlama  
 Bazı içerik denetimleri, belgeye gömülü özel XML bölümleri öğelerine bağlayabilirsiniz. Özel XML bölümleri hakkında daha fazla bilgi için bkz. [özel XML bölümlerine genel bakış](../vsto/custom-xml-parts-overview.md).  
  
 Özel bir XML parçasına içindeki bir öğenin içerik denetimine bağlamak için kullanın **XMLMapping** denetiminin özelliği. Aşağıdaki kod örneğinde nasıl bağlanacağını gösterir. bir <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> için `Price` öğesi altında `Product` belgeye zaten eklenmiş olan özel bir XML parçasına düğümü.  
  
```vb  
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price")  
```  
  
```csharp  
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price", String.Empty, null);  
```  
  
 İçerik denetimlerini özel XML bölümlerine daha ayrıntılı bir şekilde bağlamak nasıl erişileceğini gösteren bir kılavuz için bkz. [izlenecek yol: içerik denetimlerini özel XML bölümlerine bağlama](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
 Bir içerik denetimi için özel bir XML parçasına bağlama, çift yönlü veri bağlama otomatik olarak etkinleştirilir. Bir kullanıcı denetiminde metin düzenlerse, karşılık gelen XML öğelerine otomatik olarak güncelleştirilir. Benzer şekilde, XML öğelerine bağlanan içerik denetimlerini özel XML bölümleri içindeki öğe değerlerini değiştirdiyseniz, yeni veriler görüntülenir.  
  
 Aşağıdaki türde içerik denetimlerini özel XML bölümlerine bağlayabilirsiniz:  
  
-   <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.PictureContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>  
  
### <a name="data-bind-events-for-content-controls"></a>İçerik denetimleri için olaylar veri bağlama  
 Tüm içerik denetimlerini bir veri kaynağı güncelleştirilmeden önce bir denetimdeki metin belirli kriterlere uyan doğrulama gibi verilerle ilgili görevleri gerçekleştirmek için işleyebilen bir etkinlik kümesi sağlar. Aşağıdaki tablo, veri bağlama ile ilgili içerik denetimi olayları listeler.  
  
|Görev|Olay|  
|----------|-----------|  
|Otomatik olarak özel bir XML parçasına ilişkili içerik bir denetimdeki metin yalnızca Word güncellenmeden önce kodu çalıştırın.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|  
|Kodu çalıştırın, yalnızca Word bağlı özel bir XML parçasına verileri otomatik olarak güncelleştirir önce bir içerik (diğer bir deyişle, içerik denetimi metinde değiştikten sonra) denetler.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|  
|Özel ölçütlere göre denetimin içeriğini doğrulamak için kendi kodunuzu çalıştırın.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validating>|  
|Denetimin içeriğini başarıyla doğrulandıktan sonra kodu çalıştırmak.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validated>|  
  
## <a name="limitations-of-content-controls"></a>İçerik denetimleri sınırlamaları  
 İçerik denetimleri, Office projelerinde kullandığınızda, aşağıdaki sınırlamaları unutmayın.  
  
### <a name="behavior-differences-between-design-time-and-runtime"></a>Tasarım zamanı ve çalışma zamanı arasındaki davranış farklılıkları  
 Microsoft Office Word içerik denetimleri, çalışma zamanında uygular sınırlamaları birçoğu, tasarım zamanında zorlanmaz. Belge düzeyi çözümde UI tasarlarken [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], içerik denetimlerini çalışma zamanında desteklenen yolla değiştirdiğinizden emin olun.  
  
 Tasarım zamanında çalışma zamanında denetim desteği olmayan bir şekilde içerik denetimi değiştirirseniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tasarımcısı uyarı vermemesi desteklenmeyen değişiklikleri. Ancak, hata ayıklama veya proje çalıştırdığınızda ya da kaydedin ve ardından projeyi yeniden Word belge onarmak için bir hata iletisi ve istek izni görüntüler. Belge onarma işlemini Word desteklenmeyen içerik ve biçimlendirme denetimden kaldırır.  
  
 Örneğin, Word, tabloya eklemesini engellemez bir <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> tasarım zamanında. Ancak, çünkü <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> nesneler, çalışma zamanında tabloları içeremez, Word belge açıldığında bir hata iletisi görüntüler.  
  
 Ayrıca içerik denetimlerini davranışını tanımlayan birçok özellikleri tasarım zamanında etkisi gerektiğini unutmayın. Örneğin, ayarlarsanız **LockContents** özelliği içerik denetiminin **True** tasarım zamanında metin denetiminde yine de düzenleyebilirsiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tasarımcısı. Bu özellik, kullanıcıların yalnızca çalışma zamanında denetim düzenlemesini engeller.  
  
### <a name="event-limitations"></a>Olay sınırlamaları  
 İçerik denetimleri, kullanıcı, metin veya diğer öğeleri denetiminde değiştiğinde bir olay sağlamaz. Örneğin, bir kullanıcı farklı bir öğe seçtiğinde hiçbir olay yok bir <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> veya <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>.  
  
 Kullanıcının ne zaman bir içerik denetimi içeriğini düzenlediğini belirlemek için denetimini özel bir XML parçasına bağlama ve ardından işleme <xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating> olay. Kullanıcı özel bir XML parçasına bağlı bir denetimin içeriğini değiştirdiğinde bu olay tetiklenir. Bir içerik denetimi için özel bir XML parçasına bağlama yapmayı gösteren bir anlatım için bkz: [izlenecek yol: içerik denetimlerini özel XML bölümlerine bağlama](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
###  <a name="checkbox"></a> Word projelerinde onay kutusu içerik denetimi  
 Word 2010 temsil eden bir onay kutusu içerik denetimi yeni türü kullanıma sunuldu. Ancak, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Office projelerinde kullanabilmeniz için karşılık gelen CheckBoxContentControl türü sağlamaz. Bir onay kutusu içerik denetimi oluşturmak için bir [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya Word 2010 projesinde kullanmak <xref:Microsoft.Office.Tools.Word.ControlCollection.AddContentControl%2A> yöntemi oluşturmak için bir <xref:Microsoft.Office.Tools.Word.ContentControl> nesne ve geçmesi <xref:Microsoft.Office.Interop.Word.WdContentControlType.wdContentControlCheckBox> onay kutusu içerik denetimi belirtmek için yöntemi için değer. Aşağıdaki kod örneği, bunun nasıl yapılacağı gösterilmektedir.  
  
 [!code-vb[Trin_ContentControlReference#800](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/checkbox.vb#800)]
 [!code-csharp[Trin_ContentControlReference#800](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/checkbox.cs#800)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Genişletilmiş nesneleri kullanarak Word'ü otomatikleştirirken](../vsto/automating-word-by-using-extended-objects.md)   
 [Nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [İzlenecek yol: içerik denetimlerini kullanarak şablon oluşturma](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [Office çözümlerindeki veriler](../vsto/data-in-office-solutions.md)   
 [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Konak denetimlerinin ve konak öğelerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
