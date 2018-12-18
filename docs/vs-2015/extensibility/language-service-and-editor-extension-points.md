---
title: Dil hizmeti ve düzenleyici uzantı noktaları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extension points
ms.assetid: 91a6417e-a6fe-4bc2-9d9f-5173c634a99b
caps.latest.revision: 34
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0bcbef5094bd12392b7ea79865e1d28e2934a11e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743578"
---
# <a name="language-service-and-editor-extension-points"></a>Dil Hizmeti ve Düzenleyici Uzantı Noktaları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Düzenleyici, çoğu dil hizmeti özellikleri dahil olmak üzere Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşen parçalarına genişletebilirsiniz uzantı noktaları sağlar. Ana uzantı noktası kategorileri şunlardır:  
  
-   İçerik türleri  
  
-   Sınıflandırma türleri ve sınıflandırma biçimleri  
  
-   Kenar boşlukları ve kaydırma çubukları  
  
-   Etiketler  
  
-   Kenarlıklar  
  
-   Fare işlemcileri  
  
-   Bırakma işleyicileri  
  
-   Seçenekler  
  
-   IntelliSense  
  
## <a name="extending-content-types"></a>İçerik türlerini genişletme  
 Örneğin düzenleyici tarafından işlenen metin, "metin", "code" veya "CSharp" tür tanımlarını içerik türleridir. Yeni bir içerik türü türünün bir değişkeni bildirerek tanımladığınız <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> ve yeni içerik türü benzersiz bir ad verir. İçerik türü Düzenleyicisi ile kaydetmek için aşağıdaki öznitelikleri ile birlikte dışarı aktarın:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute> içerik türü adıdır.  
  
- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute> Bu içerik türü türetildiği içerik türü adıdır. Bir içerik türü diğer içerik birden çok türlerinden devraldığına.  
  
  Çünkü <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> sınıfı Mühürlü, hiçbir tür parametresi ile dışarı aktarabilirsiniz.  
  
  Aşağıdaki örnek, bir içerik türü tanımı üzerinde dışarı aktarma öznitelikleri gösterir.  
  
```  
[Export]  
[Name("test")]  
[BaseDefinition("code")]  
[BaseDefinition("projection")]  
internal static ContentTypeDefinition TestContentTypeDefinition;  
```  
  
 İçerik türleri sıfır veya daha fazla önceden var olan içerik türlerine göre uygulanabilir. Yerleşik türleri şunlardır:  
  
- Tüm: temel içerik türü. Tüm diğer içerik türlerine üst.  
  
- Metin: projeksiyon olmayan içerik için temel türü. "Tümü" devralır.  
  
- Düz metin: kod dışı metni. "Metin" devralır.  
  
- Kod: kod her tür için. "Metin" devralır.  
  
- Simge: metin işleme her türden dışlar. Bu içerik türü metin hiçbir zaman uygulanmış herhangi bir uzantısına sahip olmayacak.  
  
- Projeksiyon: projeksiyon arabellek için içerik. "Tümü" devralır.  
  
- IntelliSense: içeriğini IntelliSense için. "Metin" devralır.  
  
- Sighelp: İmza Yardımı. "IntelliSense" devralır.  
  
- Sighelp-doc: İmza Yardım belgeleri. "IntelliSense" devralır.  
  
  Bazı Visual Studio tarafından tanımlanan içerik türleri ve Visual Studio'da barındırılan dilleri bazıları şunlardır:  
  
- Temel  
  
- C/C++  
  
- ConsoleOutput  
  
- CSharp  
  
- CSS  
  
- ENC  
  
- FindResults  
  
- F#  
  
- HTML  
  
- JScript  
  
- XAML  
  
- XML  
  
  Kullanılabilir içerik türleri listesini bulmak için içeri aktarma <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>, içerik türleri Koleksiyonu Düzenleyicisi tutar. Aşağıdaki kod bu hizmet bir özellik olarak içeri aktarır.  
  
```  
[Import]  
internal IContentTypeRegistryService ContentTypeRegistryService { get; set; }  
```  
  
 Dosya adı uzantısına sahip bir içerik türüyle ilişkilendirmek için kullanmak <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition>.  
  
> [!NOTE]
>  Visual Studio'da dosya adı uzantılarını kullanarak kayıtlı <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute> dil hizmeti paketi üzerinde. <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> MEF içerik türü, bu şekilde kayıtlı bir dosya adı uzantısı ile ilişkilendirir.  
  
 Dosya adı uzantısı içerik türü tanımını dışarı aktarmak için öznitelikleri şunlardır:  
  
- <xref:Microsoft.VisualStudio.Utilities.FileExtensionAttribute>: dosya adı uzantısını belirtir.  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: içerik türünü belirtir.  
  
  Çünkü <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> sınıfı Mühürlü, hiçbir tür parametresi ile dışarı aktarabilirsiniz.  
  
  Aşağıdaki örnek, bir dosya adı uzantısı için bir içerik türü tanımı üzerinde dışarı aktarma öznitelikleri gösterir.  
  
```  
[Export]  
[FileExtension(".test")]  
[ContentType("test")]  
internal static FileExtensionToContentTypeDefinition TestFileExtensionDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService> Dosya adı uzantılarının ve içerik türleri arasındaki ilişkilendirmeleri yönetir.  
  
## <a name="extending-classification-types-and-classification-formats"></a>Sınıflandırma türleri ve sınıflandırma genişletme biçimleri  
 Sınıflandırma türleri (örneğin, "anahtar sözcüğü" metni mavi ve "Açıklama" metni yeşil renklendirme) farklı işleme sağlamak istediğiniz metin türleri tanımlamak için kullanabilirsiniz. Yeni bir sınıflandırma türü türünün bir değişkeni bildirerek tanımlamak <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> ve benzersiz bir ad verin.  
  
 Düzenleyiciyle sınıflandırma türünü kaydetmek için aşağıdaki öznitelikleri ile birlikte dışarı aktarın:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: sınıflandırma türünün adı.  
  
- <xref:Microsoft.VisualStudio.Utilities.BaseDefinitionAttribute>: Bu sınıflandırma türünü devraldığı sınıflandırma türünün adı. Tüm sınıflandırma türleri "metin" devralır ve bir sınıflandırma türü diğer birden çok sınıflandırması türlerinden devraldığına.  
  
  Çünkü <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeDefinition> sınıfı Mühürlü, hiçbir tür parametresi ile dışarı aktarabilirsiniz.  
  
  Aşağıdaki örnek, bir sınıflandırma türü tanımı üzerinde dışarı aktarma öznitelikleri gösterir.  
  
```  
[Export]  
[Name("csharp.test")]  
[BaseDefinition("test")]  
internal static ClassificationTypeDefinition CSharpTestDefinition;  
```  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService> Standart sınıflandırmaları erişim sağlar. Bu yerleşik sınıflandırma türleri şunlardır:  
  
- "metin"  
  
- "doğal dil" ("metin" türetilir)  
  
- "biçimsel dili (türetilen"metni")"  
  
- "dize" ("sabit" türetilir)  
  
- "character" ("sabit" türetilir)  
  
- "sayısal" ("sabit" türetilir)  
  
  Farklı hata türleri kümesi devralmanız <xref:Microsoft.VisualStudio.Text.Adornments.ErrorTypeDefinition>. Bunlar, aşağıdaki hata türleri şunlardır:  
  
- "söz dizimi hatası"  
  
- "derleyici hatası"  
  
- "hata"  
  
- "uyarı"  
  
  Kullanılabilir sınıflandırma türleri listesini bulmak için içeri aktarma <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>, sınıflandırma türleri Koleksiyonu Düzenleyicisi tutar. Aşağıdaki kod bu hizmet bir özellik olarak içeri aktarır.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationTypeRegistryService { get; set; }  
```  
  
 Yeni sınıflandırma türünüz için bir sınıflandırma biçim tanımını tanımlayabilirsiniz. Öğesinden bir sınıf türetin <xref:Microsoft.VisualStudio.Text.Classification.ClassificationFormatDefinition> ve türü ile dışarı aktarın <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>aşağıdaki özniteliklerle birlikte:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: biçim adı.  
  
- <xref:Microsoft.VisualStudio.Utilities.DisplayNameAttribute>: biçimi görünen adı.  
  
- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: biçimi görünür olup olmadığını belirtir **yazı tipleri ve renkler** sayfasının **seçenekleri** iletişim kutusu.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: öncelik biçimi. Geçerli değerler: gelen <xref:Microsoft.VisualStudio.Text.Classification.Priority>.  
  
- <xref:Microsoft.VisualStudio.Text.Classification.ClassificationTypeAttribute>: sınıflandırma adı Bu biçim eşlenmiş.  
  
  Aşağıdaki örnek, bir sınıflandırma biçim tanımını dışarı aktarma öznitelikleri gösterir.  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[ClassificationType(ClassificationTypeNames = "test")]  
[Name("test")]  
[DisplayName("Test")]  
[UserVisible(true)]  
[Order(After = Priority.Default, Before = Priority.High)]  
internal sealed class TestFormat : ClassificationFormatDefinition  
```  
  
 Kullanılabilir biçimler listesini bulmak için içeri aktarma <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>, biçimleri Koleksiyonu Düzenleyicisi tutar. Aşağıdaki kod bu hizmet bir özellik olarak içeri aktarır.  
  
```  
[Import]  
internal IEditorFormatMapService FormatMapService { get; set; }  
```  
  
## <a name="extending-margins-and-scrollbars"></a>Genişletme kenar boşlukları ve kaydırma çubukları  
 Kenar boşlukları ve kaydırma çubukları ana görünüm düzenleyici metin görünümünü yanı sıra öğeleridir. Kenar boşlukları metin görünümünü görünen standart kenar boşluklarını yanı sıra herhangi bir sayıda sağlayabilir.  
  
 Uygulama bir <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMargin> kenar boşluğu tanımlamak için arabirim. Ayrıca uygulamalıdır <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> kenar oluşturmak için arabirim.  
  
 Düzenleyiciyle kenar boşluğu sağlayıcıyı kaydetmek için aşağıdaki öznitelikleri ile birlikte sağlayıcısı dışarı aktarmanız gerekir:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: kenar adı.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kenar göründüğü, diğer kenar boşluklarını göre sırası.  
  
   Yerleşik kenar şunlardır:  
  
  - "Wpf yatay kaydırma çubuğu"  
  
  - "Wpf dikey kaydırma çubuğu"  
  
  - "Wpf satır numarası kenar boşluğu"  
  
    Bir sipariş özniteliği yatay kenar boşlukları `After="Wpf Horizontal Scrollbar"` yerleşik kenar boşluğu ve bir sipariş özniteliği yatay kenar boşlukları görüntülenen `Before ="Wpf Horizontal Scrollbar"` yerleşik kenar görüntülenir. Bir sipariş özniteliği Dikey Kenar boşluklarını sağ `After="Wpf Vertical Scrollbar"` kaydırma çubuğunun sağında görüntülenir. Bir sipariş özniteliği Dikey Kenar boşluklarını sol `After="Wpf Line Number Margin"` (görünüyorsa) satır numarası kenar boşluğu solunda görünür.  
  
- <xref:Microsoft.VisualStudio.Text.Editor.MarginContainerAttribute>: kenar boşluğu (sol, sağ, üst veya alt) türü.  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>:, kenar boşluğu olduğu geçerli tür içerik (örneğin, "metin" veya "code").  
  
  Aşağıdaki örnek, bir kenar boşluğu sağlayıcısında satır numarası kenar boşluğu sağında görünen kenar boşlukları için dışarı aktarma öznitelikleri gösterir.  
  
```  
[Export(typeof(IWpfTextViewMarginProvider))]  
[Name("TestMargin")]  
[Order(Before = "Wpf Line Number Margin")]  
[MarginContainer(PredefinedMarginNames.Left)]  
[ContentType("text")]   
```  
  
## <a name="extending-tags"></a>Etiketleri genişletme  
 Etiketler, veri metni farklı türleri ile ilişkilendirme bir yoludur. Çoğu durumda, ilişkili veriler bir görsel efekt görüntülenir, ancak bir görsel sunumunu tüm etiketlere sahip. Kendi tür bir etiket uygulayarak tanımlayabileceğiniz <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Ayrıca uygulamalıdır <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> etiketler belirli bir metin alanı kümesi için sağlamak ve bir <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> etiketlerde sağlamak için. Etiketlerde sağlayıcısı aşağıdaki öznitelikleri ile birlikte dışarı aktarmanız gerekir:  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: Etiket alanınızda olduğu geçerli tür içerik (örneğin, "metin" veya "code").  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: Etiket türü.  
  
  Aşağıdaki örnek, etiketlerde sağlayıcısında dışarı aktarma öznitelikleri gösterir.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TagType(typeof(TestTag))]  
internal class TestTaggerProvider : ITaggerProvider  
```  
  
 Yerleşik etiket aşağıdaki türleri şunlardır:  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.ClassificationTag>: ile ilişkili bir <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>: hata türleri ile ilişkili.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>: bir kenarlığı ile ilişkili.  
  
  > [!NOTE]
  >  Bir örneği bir <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, HighlightWordTag tanımında bkz [izlenecek yol: metni vurgulama](../extensibility/walkthrough-highlighting-text.md).  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>: genişletilmiş veya daraltılmış anahat içinde bölge ile ilişkilendirilmiş.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>: bir metin görünümünde bir kenarlığı kapladığı tanımlar. Kenarlıklar alanı anlaşması hakkında daha fazla bilgi için aşağıdaki bölüme bakın.  
  
- <xref:Microsoft.VisualStudio.Text.Editor.IntraTextAdornmentTag>: Otomatik aralık ve boyutlandırma kenarlığı için sağlar.  
  
  Bul ve arabellekleri ve görünümler için etiketleri kullanmak için içeri aktarma <xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService> veya <xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>, hangi size bir <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> istenen türde. Aşağıdaki kod bu hizmet bir özellik olarak içeri aktarır.  
  
```  
[Import]  
internal IViewTagAggregatorFactoryService ViewTagAggregatorFactoryService { get; set; }  
```  
  
#### <a name="tags-and-markerformatdefinitions"></a>Etiketleri ve MarkerFormatDefinitions  
 Genişletebileceğiniz <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> etiket görünümünü tanımlamak için sınıf. Sınıfınıza dışarı aktarmanız gerekir (olarak bir <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition>) aşağıdaki özelliklere sahip:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Bu biçim başvurmak için kullanılan ad  
  
- <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: Bu biçim kullanıcı Arabiriminde görüntülenecek neden olur  
  
  Oluşturucu içinde görünen adı ve etiketi görünümünü tanımlayın. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.BackgroundColor%2A> Dolgu rengi tanımlar ve <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.ForegroundColor%2A> kenarlık rengini tanımlar. <xref:Microsoft.VisualStudio.Text.Classification.EditorFormatDefinition.DisplayName%2A> Biçimlendirme tanımında yerelleştirilebilir adıdır.  
  
  Biçimlendirme tanımında örneği verilmiştir:  
  
```  
[Export(typeof(EditorFormatDefinition))]  
[Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
[UserVisible(true)]  
internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
{  
    public HighlightWordFormatDefinition()  
    {  
        this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";   
        this.ZOrder = 5;  
    }  
}  
  
```  
  
 Bu biçim tanımı için bir etiket uygulamak için ayarladığınız (görünen adı değil) sınıfın ad özniteliği adı başvuru.  
  
> [!NOTE]
>  Bir örneği bir <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>, HighlightWordFormatDefinition bkz [izlenecek yol: metni vurgulama](../extensibility/walkthrough-highlighting-text.md).  
  
## <a name="extending-adornments"></a>Kenarlıklar genişletme  
 Kenarlıklar ya da bir metin görünümünde görüntülenen metin eklenebilir veya metnin kendisini görüntülemek görsel efektler tanımlayın. Her tür kendi kenarlığı tanımlayabilirsiniz <xref:System.Windows.UIElement>.  
  
 Kenarlığı sınıfınızda bildirmelisiniz bir <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>. Kenarlığı katmanınızdaki kaydetmek için aşağıdaki öznitelikleri ile birlikte dışarı aktarın:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: kenarlığı adı.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kenarlığı diğer kenarlığı katmanları göre sıralama. Sınıf <xref:Microsoft.VisualStudio.Text.Editor.PredefinedAdornmentLayers> dört varsayılan Katmanlar tanımlar: seçimi, anahat oluşturma, giriş işaretini ve metin.  
  
  Aşağıdaki örnek, bir kenarlığı katman tanımı üzerinde dışarı aktarma öznitelikleri gösterir.  
  
```  
[Export]  
[Name("TestEmbeddedAdornment")]  
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testLayerDefinition;  
```  
  
 Uygulayan bir ikinci sınıf oluşturmalısınız <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> ve işleme, <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> kenarlığı örnekleme tarafından olay. Bu sınıf aşağıdaki öznitelikleri ile birlikte dışarı aktarmanız gerekir:  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: kenarlığı olduğu geçerli tür içerik (örneğin, "metin" veya "code").  
  
- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: Bu kenarlığı olduğu geçerli metin görünümünü türü. Sınıf <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> tanımlanmış metin görünümü roller kümesi vardır. Örneğin, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> öncelikle dosyalarının metin görünümler için kullanılır. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> Kullanıcı düzenleme veya fare ve klavye kullanarak gezinme metin görünümler için kullanılır. Örnekleri <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> görünümleridir düzenleyici metin görünümünü ve **çıkış** penceresi.  
  
  Aşağıdaki örnek, dışarı aktarma öznitelik kenarlığı sağlayıcısında gösterir.  
  
```  
[Export(typeof(IWpfTextViewCreationListener))]  
[ContentType("csharp")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
internal sealed class TestAdornmentProvider : IWpfTextViewCreationListener  
```  
  
 Bir alanı anlaşması kenarlığı metin ile aynı düzeyde yer kaplar biridir. Bu tür bir kenarlığı oluşturmak için devralınan bir etiket sınıfı tanımlayın <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, kenarlığı kapladığı alanı tanımlar.  
  
 Gibi tüm kenarlıklar ile kenarlığı katman tanımını dışarı aktarmanız gerekir.  
  
```  
[Export]  
[Name("TestAdornment")]  
[Order(After = DefaultAdornmentLayers.Text)]  
internal AdornmentLayerDefinition testAdornmentLayer;  
```  
  
 Alanı anlaşması kenarlığı örneklemek için uygulayan bir sınıf oluşturmanız gerekir <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, uygulayan sınıf yanı sıra <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> (kenarlıklar diğer türlerde olduğu gibi).  
  
 Etiketlerde sağlayıcıyı kaydetmek için aşağıdaki öznitelikleri ile birlikte dışarı aktarmanız gerekir:  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: uygulamanızın kenarlığı olduğu geçerli tür içerik (örneğin, "metin" veya "code").  
  
- <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>: Bu metin görünümünü türü etiketi veya kenarlığı geçerlidir. Sınıf <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles> tanımlanmış metin görünümü roller kümesi vardır. Örneğin, <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> öncelikle dosyalarının metin görünümler için kullanılır. <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> Kullanıcı düzenleme veya fare ve klavye kullanarak gezinme metin görünümler için kullanılır. Örnekleri <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Interactive> görünümleridir düzenleyici metin görünümünü ve **çıkış** penceresi.  
  
- <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute>: etiketi veya sizin tanımladığınız kenarlığı türü. İkinci eklemelisiniz <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> için <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>.  
  
  Aşağıdaki örnek, alan anlaşması kenarlığı etiket etiketlerde sağlayıcısı dışarı aktarma öznitelikleri gösterir.  
  
```  
[Export(typeof(ITaggerProvider))]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Document)]  
[TagType(typeof(SpaceNegotiatingAdornmentTag))]  
[TagType(typeof(TestSpaceNegotiatingTag))]  
internal sealed class TestTaggerProvider : ITaggerProvider  
```  
  
## <a name="extending-mouse-processors"></a>Fare işlemci genişletme  
 Fare girişi için özel işleme ekleyebilirsiniz. Devralınan bir sınıf oluşturmanız <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> ve fare olayları işlemek istediğiniz girişi için geçersiz kılın. Ayrıca uygulamalıdır <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> ikinci sınıfında ve birlikte dışarı aktarın <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> fare işleyicinizi olduğu geçerli içerik (örneğin, "metin" veya "code") türünü belirtir.  
  
 Aşağıdaki örnek, bir fare işlemci sağlayıcısında dışarı aktarma öznitelikleri gösterir.  
  
```  
[Export(typeof(IMouseProcessorProvider))]  
[Name("test mouse processor")]  
[ContentType("text")]  
[TextViewRole(PredefinedTextViewRoles.Interactive)]   
internal sealed class TestMouseProcessorProvider : IMouseProcessorProvider  
```  
  
## <a name="extending-drop-handlers"></a>Bırakma işleyicileri genişletme  
 Uygulayan bir sınıf oluşturarak, belirli türde metin için bırakma işleyiciler davranışını özelleştirebilirsiniz <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandler> ve uygulayan bir ikinci sınıf <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.IDropHandlerProvider> bırak işleyicisi oluşturmak için. Bırak işleyicisi aşağıdaki öznitelikleri ile birlikte dışarı aktarmanız gerekir:  
  
- <xref:Microsoft.VisualStudio.Text.Editor.DragDrop.DropFormatAttribute>: Bu bırak işleyicisi olduğu geçerli metin biçimi. Şu biçimlerden yüksekten en düşüğe öncelik sırasına ele alınmıştır:  
  
  1.  Herhangi bir özel biçim  
  
  2.  FileDrop  
  
  3.  EnhancedMetafile  
  
  4.  WaveAudio  
  
  5.  RIFF  
  
  6.  DIF  
  
  7.  Yerel Ayar  
  
  8.  Palet  
  
  9. PenData  
  
  10. Seri hale getirilebilir  
  
  11. SymbolicLink  
  
  12. XAML  
  
  13. XamlPackage  
  
  14. TIFF  
  
  15. Bit eşlem  
  
  16. DIB  
  
  17. MetafilePicture  
  
  18. CSV  
  
  19. System.String  
  
  20. HTML biçiminde  
  
  21. UnicodeText  
  
  22. OEMText  
  
  23. Metin  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: bırak işleyicisi adı.  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: önce veya sonra varsayılan bırak işleyicisi bırak işleyicisi sıralama. Visual Studio için varsayılan bırakma işleyicisini "DefaultFileDropHandler" olarak adlandırılır.  
  
  Aşağıdaki örnek, bir bırakma işleyici sağlayıcısında dışarı aktarma öznitelikleri gösterir.  
  
```  
[Export(typeof(IDropHandlerProvider))]  
[DropFormat("Text")]   
[Name("TestDropHandler")]  
[Order(Before="DefaultFileDropHandler")]   
internal class TestDropHandlerProvider : IDropHandlerProvider  
```  
  
## <a name="extending-editor-options"></a>Düzenleyici seçeneklerini genişletme  
 Bir metin görünümünde yalnızca belirli bir kapsama, örneğin, geçerli olması için seçenekleri tanımlayabilirsiniz. Bu önceden tanımlanmış seçenekleri kümesi Düzenleyicisi sağlar: Düzenleyici seçeneklerini görüntüleme seçenekleri ve Windows Presentation Foundation (WPF) görüntüleme seçenekleri. Bu seçenekler bulunabilir <xref:Microsoft.VisualStudio.Text.Editor.DefaultOptions>, <xref:Microsoft.VisualStudio.Text.Editor.DefaultTextViewOptions>, ve <xref:Microsoft.VisualStudio.Text.Editor.DefaultWpfViewOptions>.  
  
 Yeni bir seçenek eklemek için bu seçenek tanımı sınıflarının birinden bir sınıf türetin:  
  
- <xref:Microsoft.VisualStudio.Text.Editor.EditorOptionDefinition%601>  
  
- <xref:Microsoft.VisualStudio.Text.Editor.ViewOptionDefinition%601>  
  
- <xref:Microsoft.VisualStudio.Text.Editor.WpfViewOptionDefinition%601>  
  
  Aşağıdaki örnek, bir Boolean değerine sahip bir seçenek tanımı dışa aktarmayı gösterir.  
  
```  
[Export(typeof(EditorOptionDefinition))]  
internal sealed class TestOption : EditorOptionDefinition<bool>  
```  
  
## <a name="extending-intellisense"></a>IntelliSense genişletme  
 IntelliSense, yapılandırılmış metin hakkında bilgi sağlayan bir grup için genel bir terim ve deyim tamamlama, için ' dir. Bu özellikler, deyim tamamlama, imza Yardımı, hızlı bilgi ve ampuller içerir. Deyim tamamlama, kullanıcıların bir dil anahtar sözcüğü ya da üye adını doğru şekilde yazın yardımcı olur. İmza Yardımı, imza veya kullanıcının yalnızca yazdığını yöntem imzaları görüntüler. Fareyi üzerine getirildiğinde bir tür veya üye adı için tam imza hızlı bilgi görüntüler. Ampul belirli bağlamlarda, örneğin, belirli tanımlayıcıları için ek eylemler bir oluşum yeniden adlandırıldı sonra bir değişkenin tüm örnekleri yeniden adlandırma sağlar.  
  
 Bir IntelliSense özelliğini tasarımını kadar tüm durumlarda aynıdır:  
  
- Bir IntelliSense *Aracısı* için genel işlem sorumludur.  
  
- Bir IntelliSense *oturumu* sunan ve committal veya seçimini iptal etme işlemini tetikleme arasında olaylar dizisini temsil eder. Oturum, genellikle bazı kullanıcı hareketi tarafından tetiklenir.  
  
- Bir IntelliSense *denetleyicisi* oturumu zaman başlatmak ve biteceğini karar verirken sorumludur. Ayrıca, bilgileri yürütülmesi gereken ve oturum zaman iptal karar verir.  
  
- Bir IntelliSense *kaynak* içerik sağlar ve en iyi eşleşmeyi karar verir.  
  
- Bir IntelliSense *sunan* içeriği görüntülemek için sorumludur.  
  
  Çoğu durumda, en az bir kaynağı ile bir denetleyici sağlamanız önerilir. Sunucu görüntüsünü özelleştirmek istiyorsanız de sağlayabilirsiniz.  
  
### <a name="implementing-an-intellisense-source"></a>Bir IntelliSense kaynağı uygulama  
 Bir kaynak özelleştirmek için aşağıdaki kaynak arabirimlerinden birini (veya daha fazla) uygulamanız gerekir:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSource> sunulmasıyla kullanım dışı <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
 Ayrıca, aynı türden bir sağlayıcı uygulamanız gerekir:  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>  
  
-   <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>  
  
> [!IMPORTANT]
>  <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagSourceProvider> sunulmasıyla kullanım dışı <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.  
  
 Sağlayıcı aşağıdaki öznitelikleri ile birlikte dışarı aktarmanız gerekir:  
  
-   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: kaynağının adı.  
  
-   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: kaynak uygulandığı türde içerik (örneğin, "metin" veya "code").  
  
-   <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: kaynak (göre diğer kaynakları) görünmelidir sırası.  
  
-   Aşağıdaki örnek, bir tamamlama kaynak sağlayıcısına dışarı aktarma öznitelikleri gösterir.  
  
```  
Export(typeof(ICompletionSourceProvider))]  
[Name(" Test Statement Completion Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestCompletionSourceProvider : ICompletionSourceProvider  
```  
  
 IntelliSense kaynakları uygulama hakkında daha fazla bilgi için aşağıdaki izlenecek yollara bakın:  
  
 [İzlenecek Yol: HızlıBilgi Araç İpuçlarını Görüntüleme](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [İzlenecek Yol: İmza Yardımını Görüntüleme](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [İzlenecek Yol: Deyim Tamamlamayı Görüntüleme](../extensibility/walkthrough-displaying-statement-completion.md)  
  
### <a name="implementing-an-intellisense-controller"></a>Bir IntelliSense denetleyicisi uygulama  
 Bir denetleyici özelleştirmek için uygulamanız gereken <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> arabirimi. Ayrıca, aşağıdaki öznitelikleri ile birlikte bir denetleyici sağlayıcısı uygulamanız gerekir:  
  
- <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: denetleyicinin adı.  
  
- <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>: Denetleyici uygulandığı türde içerik (örneğin, "metin" veya "code").  
  
- <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>: siparişin denetleyici (göre diğer denetleyicileri) görüntülenmelidir.  
  
  Aşağıdaki örnek, bir tamamlama denetleyicisi sağlayıcısında dışarı aktarma öznitelikleri gösterir.  
  
```  
Export(typeof(IIntellisenseControllerProvider))]  
[Name(" Test Controller Provider")]  
[Order(Before = "default")]  
[ContentType("text")]  
internal class TestIntellisenseControllerProvider : IIntellisenseControllerProvider  
```  
  
 IntelliSense denetleyicileri kullanma hakkında daha fazla bilgi için aşağıdaki izlenecek yollara bakın:  
  
 [İzlenecek Yol: HızlıBilgi Araç İpuçlarını Görüntüleme](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

