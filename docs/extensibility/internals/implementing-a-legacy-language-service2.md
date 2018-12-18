---
title: Bir eski dil hizmeti Uygulama2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dccbac140aefb952eed97006cbcae6a61f94ac92
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855423"
---
# <a name="implementing-a-legacy-language-service"></a>Eski dil hizmetinde uygulama
Yönetilen paket çerçevesini (MPF) kullanarak bir dil hizmeti uygulamak için öğesinden bir sınıf türetin <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı ve aşağıdaki soyut yöntemler ve özellikler uygular:  
  
- <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> Yöntemi  
  
- <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> Yöntemi  
  
- <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Yöntemi  
  
- <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> Özelliği  
  
  Uygulamaya bu yöntemleri ve özellikleri için aşağıdaki uygun bölümlere bakın.  
  
  Ek özellikleri destekleyecek şekilde dili hizmetinizi MPF dil hizmeti sınıflarının birinden bir sınıf türetin gerekebilir; Örneğin, ek menü komutları desteklemek için bir sınıftan türetilmelidir <xref:Microsoft.VisualStudio.Package.ViewFilter> sınıfı ve birkaç komut işleme yöntemi geçersiz kılın (bkz <xref:Microsoft.VisualStudio.Package.ViewFilter> Ayrıntılar için). <xref:Microsoft.VisualStudio.Package.LanguageService> , Sınıfının bir örneğini sağlamak üzere uygun oluşturma yöntemini geçersiz kılma ve sınıfı bir dizi yeni çeşitli sınıfların örneklerini oluşturmak için çağrılan yöntem sağlar. Örneğin, geçersiz kılmak ihtiyacınız <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> yönteminde <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfının örneğini, kendi dönüş <xref:Microsoft.VisualStudio.Package.ViewFilter> sınıfı. Daha fazla ayrıntı için "Özel sınıflar örnekleme" bölümüne bakın.  
  
  Dil hizmetiniz aynı zamanda pek çok yerde kullanılan kendi simgeleri sağlayabilir. Örneğin, bir IntelliSense tamamlanma listesi gösterildiğinde, listedeki her öğeye simge öğesi, bir yöntem, sınıf, ad alanı, özelliği işaretleme ilişkili olabilir veya dilinizi ne olursa olsun gereklidir. Bu simgeler kullanılan tüm IntelliSense listelerinde **gezinti çubuğu**hem de **hata listesi** görev penceresi. Ayrıntılar için aşağıdaki "Dil hizmeti görüntüleri" bölümüne bakın.  
  
## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences yöntemi  
 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> Yöntemi her zaman aynı örneğini döndüren bir <xref:Microsoft.VisualStudio.Package.LanguagePreferences> sınıfı. Temel kullanabileceğiniz <xref:Microsoft.VisualStudio.Package.LanguagePreferences> dil hizmetiniz için ek tercihlere gerekmiyorsa sınıfı. Varlığı en az MPF dil hizmeti sınıfları varsayar temel <xref:Microsoft.VisualStudio.Package.LanguagePreferences> sınıfı.  
  
### <a name="example"></a>Örnek  
 Bu örnek, tipik bir uygulaması gösterir <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> yöntemi. Bu örnekte temel <xref:Microsoft.VisualStudio.Package.LanguagePreferences> sınıfı.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private LanguagePreferences m_preferences;  
  
        public override LanguagePreferences GetLanguagePreferences()  
        {  
            if (m_preferences == null)  
            {  
                m_preferences = new LanguagePreferences(this.Site,  
                                                        typeof(TestLanguageService).GUID,  
                                                        this.Name );  
                m_preferences.Init();  
            }  
            return m_preferences;  
        }  
    }  
}  
```  
  
## <a name="getscanner-method"></a>GetScanner yöntemi  
 Bu yöntem bir örneğini döndürür. bir <xref:Microsoft.VisualStudio.Package.IScanner> satır yönelimli ayrıştırıcı veya belirteçleri ve türleri ve Tetikleyicileri almak için kullanılan tarayıcı uygulayan nesne. Bu tarayıcı kullanılan <xref:Microsoft.VisualStudio.Package.Colorizer> tarayıcı bir tanıtımlar daha karmaşık bir ayrıştırma işlemi olarak belirteç türleri ve Tetikleyicileri almak için de kullanılabilir olsa da renklendirme için sınıf. Uygulayan sınıfa sağlamalısınız <xref:Microsoft.VisualStudio.Package.IScanner> arabirimi ve uygulanmalı tüm yöntemleri üzerinde <xref:Microsoft.VisualStudio.Package.IScanner> arabirimi.  
  
### <a name="example"></a>Örnek  
 Bu örnek, tipik bir uygulaması gösterir <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> yöntemi. `TestScanner` Sınıfının Implements <xref:Microsoft.VisualStudio.Package.IScanner> arabirimi (gösterilmemiştir).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private TestScanner m_scanner;  
  
        public override IScanner GetScanner(IVsTextLines buffer)  
        {  
            if (m_scanner == null)  
            {  
                m_scanner = new TestScanner(buffer);  
            }  
            return m_scanner;  
        }  
    }  
}  
    internal class TestScanner : IScanner  
    {  
        private IVsTextBuffer m_buffer;  
        string m_source;  
  
        public TestScanner(IVsTextBuffer buffer)  
        {  
            m_buffer = buffer;  
        }  
  
        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)  
        {  
            tokenInfo.Type = TokenType.Unknown;  
            tokenInfo.Color = TokenColor.Text;  
            return true;  
        }  
  
        void IScanner.SetSource(string source, int offset)  
        {  
            m_source = source.Substring(offset);  
        }  
    }  
  
```  
  
## <a name="parsesource-method"></a>ParseSource yöntemi  
 Farklı nedenlerden sayısına göre kaynak dosyasını ayrıştırır. Bu yöntem verilen bir <xref:Microsoft.VisualStudio.Package.ParseRequest> açıklayan belirli bir ayrıştırma işlemi beklenen değer nesnesi. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Belirteci işlevselliğini ve kapsamını belirleyen daha karmaşık bir ayrıştırıcı yöntemini çağırır. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> IntelliSense işlemlerini yanı sıra Ayraç eşleştirme yöntemi desteği kullanılır. Gibi gelişmiş işlemler desteklemiyor olsa bile, hala geçerli bir döndürmelidir <xref:Microsoft.VisualStudio.Package.AuthoringScope> nesne ve, uygulayan bir sınıf oluşturmak gerektirir <xref:Microsoft.VisualStudio.Package.AuthoringScope> arabirimi ve tüm yöntemler, bu arabirimdeki uygulayın. Tüm yöntemlerden null değerleri döndürebilir ancak <xref:Microsoft.VisualStudio.Package.AuthoringScope> nesnesinin kendisi bir null değer olmamalıdır.  
  
### <a name="example"></a>Örnek  
 Bu örnekte en az bir uygulamasını gösterir <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi ve <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıfı, derlemek ve gerçekten daha gelişmiş özelliklerinden herhangi birini destekleyen olmadan işlev dil hizmeti izin vermek için yeterli.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            return new TestAuthoringScope();  
        }  
    }  
  
    internal class TestAuthoringScope : AuthoringScope  
    {  
        public override string GetDataTipText(int line, int col, out TextSpan span)  
        {  
            span = new TextSpan();  
            return null;  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return null;  
        }  
  
        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)  
        {  
            span = new TextSpan();  
            return null;  
        }  
  
        public override Methods GetMethods(int line, int col, string name)  
        {  
            return null;  
        }  
}  
```  
  
## <a name="name-property"></a>Name özelliği  
 Bu özellik, dil hizmeti adını döndürür. Bu dil hizmeti kaydettiğinizde verilen aynı adı olmalıdır. Bu ad, en yaygın olan bir dizi yerde içinde kullanılır <xref:Microsoft.VisualStudio.Package.LanguagePreferences> sınıfı burada adı kayıt defterine erişim için kullanılır. Kayıt defteri girişini ve anahtar adları için kayıt defterinde kullanılan bu özellik tarafından döndürülen adı yerelleştirilmiş olmalıdır değil.  
  
### <a name="example"></a>Örnek  
 Bu örnekte, olası bir uygulaması gösterilmektedir <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> özelliği. Burada adı, sabit kodlanmış olduğunu unutmayın: bir dil hizmeti kaydedilirken kullanılabilmesi için bir kaynak dosyasından gerçek adı elde edilmelidir (bkz [eski dil hizmetinde kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override string Name  
        {  
            get { return "Test Language"; }  
        }  
    }  
}  
```  
  
## <a name="instantiating-custom-classes"></a>Özel bir sınıf oluşturma  
 Belirtilen sınıfları aşağıdaki yöntemlere kendi sürümleri her sınıfın bir örneğini sağlamak için geçersiz kılınabilir.  
  
### <a name="in-the-languageservice-class"></a>LanguageService sınıfı  
  
|Yöntem|Döndürülen sınıfı|Açıklama|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Özel metin görünümünü eklemeler desteklemek için.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Özel belge özellikleri desteklemek için.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Desteklemek için **gezinti çubuğu**.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Kod parçacığı şablonlarında işlevleri desteklemek için.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Kod parçacıkları (Bu yöntem genellikle değil geçersiz kılınır) desteklemek için.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Özelleştirmeyi desteklemek için <xref:Microsoft.VisualStudio.Package.ParseRequest> yapısı (Bu yöntemi geçersiz genellikle değil kılınmıştır).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Açıklama karakterleri belirtme ve yöntem imzaları özelleştirme biçimlendirme kaynak kodu desteklemek için.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Ek menü komutları desteklemek için.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|(Bu yöntem genellikle değil geçersiz kılınır) söz dizimi vurgulama desteklemek için.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Dil Tercihleri erişimi desteklemek için. Bu yöntemin uygulanması gereken ancak temel sınıfının bir örneğini döndürebilirsiniz.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Bir satırda belirteç türleri tanımlamak için kullanılan bir ayrıştırıcı sağlamak için. Bu yöntemin uygulanması gerekir ve <xref:Microsoft.VisualStudio.Package.IScanner> nesnesinden türetilmesi gerekir.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|İşlevsellik ve tüm kaynak dosyasına kapsamdadır tanımlamak için kullanılan bir ayrıştırıcı sağlamak için. Bu yöntemin uygulanması gereken ve sürümünüzü örneği döndürmelidir <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıfı. Tüm desteklemek isterseniz olan söz dizimi vurgulama (gerektiren <xref:Microsoft.VisualStudio.Package.IScanner> döndürüldüğü ayrıştırıcı <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> yöntemi), bir sürümü Bu yöntemde return dışında bir şey yapabilirsiniz <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıfı yöntemleri tüm null değerler döndürür.|  
  
### <a name="in-the-source-class"></a>Kaynak sınıfı  
  
|Yöntem|Döndürülen sınıfı|Açıklama|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|(Bu yöntem genellikle değil geçersiz kılınır) IntelliSense tamamlanma listelerinde görüntüsünü özelleştirmek için.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|İşaretçileri hata listesinde desteklemek için görev listesi; Özellikle, dosyayı açmayı ve hataya neden olan satır atlama ötesinde özellikleri için destek.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|IntelliSense parametresi bilgi araç ipuçlarını görüntüsünü özelleştirmek için.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Koda açıklama desteklemek için.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Ayrıştırma işlemi sırasında bilgi toplamak için.|  
  
### <a name="in-the-authoringscope-class"></a>AuthoringScope sınıfı  
  
|Yöntem|Döndürülen sınıfı|Açıklama|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Üyeleri veya türleri gibi bildirimlerin listesini sağlar. Bu yöntemin uygulanması gereken ancak bir null değer döndürebilir. Bu yöntem, geçerli bir nesne döndürürse, nesne örneği sürümünüz olmalıdır <xref:Microsoft.VisualStudio.Package.Declarations> sınıfı.|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Yöntem imzaları listesi için belirli bir bağlam sağlar. Bu yöntemin uygulanması gereken ancak bir null değer döndürebilir. Bu yöntem, geçerli bir nesne döndürürse, nesne örneği sürümünüz olmalıdır <xref:Microsoft.VisualStudio.Package.Methods> sınıfı.|  
  
## <a name="language-service-images"></a>Dil hizmeti görüntüleri  
 Dil hizmeti genelinde kullanılan simge listesi sağlamak için geçersiz kılma <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> yönteminde <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı ve dönüş bir <xref:System.Windows.Forms.ImageList> simgeleri içeren. Temel <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfın varsayılan bir simge kümesi yükler. Tam görüntü dizini simgeler gereken bu yerde belirtin, nasıl, kendi görüntü listesi düzenleme tamamen size bağlıdır olduğu.  
  
### <a name="images-used-in-intellisense-completion-lists"></a>IntelliSense tamamlanma listelerinde kullanılan görüntüler  
 IntelliSense tamamlanma listeleri için resim dizinini her öğe için belirtilen <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> yöntemi <xref:Microsoft.VisualStudio.Package.Declarations> sınıfı bir görüntü dizini sağlamak istiyorsanız, geçersiz kılmanız gerekir. Döndürülen değer <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> yöntemdir sağlanan görüntü listesi bir dizine <xref:Microsoft.VisualStudio.Package.CompletionSet> sağlayıcıdan döndürülen sınıf oluşturucusu ve diğer bir deyişle aynı görüntü listesi <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> yönteminde <xref:Microsoft.VisualStudio.Package.LanguageService> (değiştirebilirsiniz hangi resim listesi için sınıf kullanılmaya <xref:Microsoft.VisualStudio.Package.CompletionSet> kılarsanız <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> yönteminde <xref:Microsoft.VisualStudio.Package.Source> farklı görüntü listesini sağlamak üzere sınıfı).  
  
### <a name="images-used-in-the-navigation-bar"></a>Gezinti çubuğunda kullanılan görüntüler  
 **Gezinti çubuğu** kullanılır ve türlerin ve üyelerin listelerini görüntüler için hızlı bir gezinti simgeler gösterebilirsiniz. Bu simgeler elde edilen <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> yönteminde <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı ve özel olarak geçersiz kılınamaz **gezinti çubuğu**. Birleşik giriş kutuları her öğe için kullanılan dizinleri temsil eden birleşik giriş kutuları listelerini dolu olduğunda belirtilen <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> yönteminde <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> sınıfı (bkz [eski dil hizmetindeGezintiçubuğudesteği](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Bu görüntü dizinler şekilde genellikle sürümünüz aracılığıyla ayrıştırıcının öğesinden elde edilir <xref:Microsoft.VisualStudio.Package.Declarations> sınıfı. Dizinleri nasıl elde edilen tamamen size bağlıdır.  
  
### <a name="images-used-in-the-error-list-task-window"></a>Hata listesi görev penceresinde kullanılan görüntüler  
 Her <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi ayrıştırıcı (bkz [eski dil hizmeti ayrıştırıcısı ve tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) bir hatayla karşılaşırsa ve bu hata durumuna geçirir <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> yönteminde <xref:Microsoft.VisualStudio.Package.AuthoringSink> sınıfı içindebildirilenhata **Hata listesi** görev penceresi. Bir simge görev penceresinde görüntülenen her bir öğesi ile ilişkili olabilir ve bu simge, döndürülen aynı görüntü listesi geldiği <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> yönteminde <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı. Varsayılan davranışı MPF sınıfların hata iletisiyle bir görüntü gösterme sağlamaktır. Ancak, bir sınıftan türetme tarafından bu davranışı geçersiz kılabilirsiniz <xref:Microsoft.VisualStudio.Package.Source> sınıf ve geçersiz kılma <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> yöntemi. Bu yöntemde, yeni oluşturduğunuz <xref:Microsoft.VisualStudio.Package.DocumentTask> nesne. Bu nesne döndürmeden önce kullanabilirsiniz <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> özelliği <xref:Microsoft.VisualStudio.Package.DocumentTask> nesne resim dizinini ayarlayın. Bu sorun aşağıdaki örnekte olduğu gibi görünür. Unutmayın `TestIconImageIndex` tüm simgeleri listeler ve bu örnek için belirli bir sabit listesidir. Dil hizmetinizdeki simgeleri tanımlamak için farklı bir yol olabilir.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestSource : Source  
    {  
        public override DocumentTask CreateErrorTaskItem(  
            TextSpan          span,  
            string            filename,  
            string            message,  
            TaskPriority      priority,  
            TaskCategory      category,  
            MARKERTYPE        markerType,  
            TaskErrorCategory errorCategory)  
        {  
            DocumentTask taskItem = base.CreateErrorTaskItem(  
                                           span,  
                                           filename,  
                                           message,  
                                           priority,  
                                           category,  
                                           markerType,  
                                           errorCategory);  
            if (errorCategory == TaskErrorCategory.Error)  
            {  
                taskItem.ImageIndex = TestIconImageIndex.Error;  
            }  
            return taskItem;  
        }  
    }  
}  
```  
  
## <a name="the-default-image-list-for-a-language-service"></a>Varsayılan görüntü listesi için bir dil hizmeti  
 Temel MPF dil hizmeti sınıfları ile sağlanan varsayılan görüntü listesi daha yaygın dil öğelerle ilişkili simgeler içerir. Bu simgeler, toplu, genel, iç ve korumalı, özel, arkadaş kısayol erişim kavramlarını için karşılık gelen altı çeşitleri kümeleri düzenlenir. Örneğin, genel, korumalı veya özel olmasına bağlı olarak bir yöntem için farklı simgeler olabilir.  
  
 Aşağıdaki sabit her simge kümesi için tipik adları ve ilişkili dizini belirtir. Örneğin, sabit listesi üzerinde bağlı olarak, korumalı bir yöntem için resim dizini belirtebilirsiniz `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`. Bu sabit listesi istediğiniz şekilde adları değiştirebilirsiniz.  
  
```csharp  
public enum IconImageIndex  
        {  
            // access types  
            AccessPublic = 0,  
            AccessInternal = 1,  
            AccessFriend = 2,  
            AccessProtected = 3,  
            AccessPrivate = 4,  
            AccessShortcut = 5,  
  
            Base = 6,  
            // Each of the following icon type has 6 versions,  
            //corresponding to the access types  
            Class = Base + 0,  
            Constant = Base + 1,  
            Delegate = Base + 2,  
            Enumeration = Base + 3,  
            EnumMember = Base + 4,  
            Event = Base + 5,  
            Exception = Base + 6,  
            Field = Base + 7,  
            Interface = Base + 8,  
            Macro = Base + 9,  
            Map = Base + 10,  
            MapItem = Base + 11,  
            Method = Base + 12,  
            OverloadedMethod = Base + 13,  
            Module = Base + 14,  
            Namespace = Base + 15,  
            Operator = Base + 16,  
            Property = Base + 17,  
            Struct = Base + 18,  
            Template = Base + 19,  
            Typedef = Base + 20,  
            Type = Base + 21,  
            Union = Base + 22,  
            Variable = Base + 23,  
            ValueType = Base + 24,  
            Intrinsic = Base + 25,  
            JavaMethod = Base + 26,  
            JavaField = Base + 27,  
            JavaClass = Base + 28,  
            JavaNamespace = Base + 29,  
            JavaInterface = Base + 30,  
            // Miscellaneous icons with one icon for each type.  
            Error = 187,  
            GreyedClass = 188,  
            GreyedPrivateMethod = 189,  
            GreyedProtectedMethod = 190,  
            GreyedPublicMethod = 191,  
            BrowseResourceFile = 192,  
            Reference = 193,  
            Library = 194,  
            VBProject = 195,  
            VBWebProject = 196,  
            CSProject = 197,  
            CSWebProject = 198,  
            VB6Project = 199,  
            CPlusProject = 200,  
            Form = 201,  
            OpenFolder = 202,  
            ClosedFolder = 203,  
            Arrow = 204,  
            CSClass = 205,  
            Snippet = 206,  
            Keyword = 207,  
            Info = 208,  
            CallBrowserCall = 209,  
            CallBrowserCallRecursive = 210,  
            XMLEditor = 211,  
            VJProject = 212,  
            VJClass = 213,  
            ForwardedType = 214,  
            CallsTo = 215,  
            CallsFrom = 216,  
            Warning = 217,  
        }  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski dil hizmetinde uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Eski dil hizmetine genel bakış](../../extensibility/internals/legacy-language-service-overview.md)   
 [Eski dil hizmeti kaydediliyor](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Eski Dil Hizmeti Ayrıştırıcısı ve Tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)