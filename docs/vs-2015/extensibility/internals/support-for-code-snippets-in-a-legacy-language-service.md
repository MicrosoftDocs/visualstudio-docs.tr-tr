---
title: Eski dil hizmetinde kod parçacıkları için destek | Microsoft Docs
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
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bf26d48c541806a1dd65a0ffb4a8e3e974b11db4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795771"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Kod Parçacıkları için Destek
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kod parçacığı bir kaynak dosyasına eklenen kod parçasıdır. Kod parçacığının kendisi bir XML tabanlı bir alan kümesi ile şablonudur. Kod parçacığı eklenir ve, kod parçacığının eklenmiş olduğu bağlama bağlı olarak farklı değerlere sahip olabilir, bu alanlar vurgulanır. Hemen kod parçacığı eklendikten sonra kod parçacığı dil hizmeti biçimlendirebilirsiniz.  
  
 Kod parçacığı, SEKME tuşunu kullanarak geçtiğiniz için kod parçacığı alanlarını izin veren bir özel düzenleme modunda eklenir. IntelliSense stili açılan menüler alanlarını destekler. Kullanıcı ENTER veya ESC tuşuna yazarak, kaynak dosyaya kod parçacığını kaydeder. Kod parçacıkları hakkında daha fazla bilgi için bkz. [kod parçacıkları](../../ide/code-snippets.md).  
  
 Eski dil Hizmetleri bir VSPackage'ı bir parçası olarak uygulanır, ancak dil hizmeti özellikleri uygulamak için daha yeni MEF uzantıları kullanmaktır. Daha fazla bilgi için bkz. [izlenecek yol: kod parçacıkları uygulama](../../extensibility/walkthrough-implementing-code-snippets.md).  
  
> [!NOTE]
>  Yeni bir düzenleyici API hemen kullanmaya başlamak öneririz. Bu dil hizmetinizin performansını ve yeni düzenleyici özellikleri yararlanmanıza olanak tanır.  
  
## <a name="managed-package-framework-support-for-code-snippets"></a>Yönetilen kod parçacıkları için paket Framework desteği  
 Kod parçacığını eklemek için şablonu okuma gelen çoğu kod parçacığı işlevleri (MPF) yönetilen paket çerçevesini destekler ve özel etkinleştirme düzenleme modunda. Destek aracılığıyla yönetilir <xref:Microsoft.VisualStudio.Package.ExpansionProvider> sınıfı.  
  
 Zaman <xref:Microsoft.VisualStudio.Package.Source> sınıf örneği, <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> yönteminde <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı almak için çağırılır bir <xref:Microsoft.VisualStudio.Package.ExpansionProvider> nesne (unutmayın temel <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı her zaman döndüren yeni bir <xref:Microsoft.VisualStudio.Package.ExpansionProvider> her nesne <xref:Microsoft.VisualStudio.Package.Source> Nesne).  
  
 MPF genişletme işlevleri desteklemiyor. Bir genişletme işlevi bir kod parçacığı şablonunda katıştırılır ve bir alanın yerleştirileceği bir veya daha fazla değer döndüren bir adlandırılmış bir işlevdir. Dil tarafından döndürülen değerlerin hizmetinin kendisi aracılığıyla bir <xref:Microsoft.VisualStudio.Package.ExpansionFunction> nesne. <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Nesne genişletme işlevleri desteklemek için dil hizmeti tarafından uygulanan gerekir.  
  
## <a name="providing-support-for-code-snippets"></a>Kod parçacıkları için desteği sağlama  
 Kod parçacıkları desteğini etkinleştirmek için sağlayın veya kod parçacıkları yükleyin ve bu kod parçacığı eklemek kullanıcı araçlarını sağlamanız gerekir. Kod parçacıkları desteğini etkinleştirmek için üç adım vardır:  
  
1.  Kod parçacığı dosyalar yükleniyor.  
  
2.  Dil hizmeti için kod parçacıkları etkinleştiriliyor.  
  
3.  Çağırma <xref:Microsoft.VisualStudio.Package.ExpansionProvider> nesne.  
  
### <a name="installing-the-snippet-files"></a>Kod parçacığı dosyaları yükleme  
 Tüm parçaları bir dil için varsayılan olarak, genellikle bir parçacık şablonu dosya başına XML dosyaları, şablon olarak depolanır. Kod parçacığı şablonları için kullanılan XML şeması hakkında daha fazla bilgi için bkz: [kod parçacıkları şema başvurusu](../../ide/code-snippets-schema-reference.md). Her parçacık şablonu dil kimliği ile tanımlanır. Bu dil kimliği kayıt defterinde belirtilen ve içine yerleştirin `Language` özniteliği \<kod > şablondaki etiketi.  
  
 Parçacık şablonu dosyalarının depolandığı iki konum vardır: 1) burada dilinizi yüklendi ve (2) kullanıcının klasöründe. Bu konumlar kayıt defterine bu nedenle, eklenen Visual Studio **kod parçacıkları Yöneticisi** parçacıkları bulabilirsiniz. Kullanıcının kullanıcı tarafından oluşturulan kod parçacıkları depolandığı bir klasördür.  
  
 Yüklü bir kod parçacığı şablon dosyaları için tipik klasör düzeni şöyle görünür: *[InstallRoot]*\\ *[TestLanguage]* \Snippets\\ *[LCID]* \Snippets.  
  
 *[InstallRoot]*  dilinizi yüklenmiş olduğu klasördür.  
  
 *[TestLanguage]*  diliniz bir klasör adı olarak adıdır.  
  
 *[LCID]*  yerel ayar kimliğidir. Bu, kod parçacıkları nasıl yerelleştirilmiş sürümlerini, depolanır. Örneğin, İngilizce yerel ayar Kimliğini 1033, bu nedenle ' *[LCID]* 1033 tarafından değiştirilir.  
  
 Bir ek dosyası sağlanmalıdır ve genellikle SnippetsIndex.xml veya ExpansionsIndex.xml (.xml biten geçerli bir dosya kullanabilirsiniz) adlı bir dizin dosyası. Bu dosya genellikle depolanan *[InstallRoot]*\\ *[TestLanguage]* klasör kod parçacıklarının klasör yanı sıra dil kimliği tam konumu ve dil GUID belirtir kod kullanan hizmet. Dizin dosyasının tam yolu, daha sonra "yükleme kayıt defteri girdileri içinde" açıklandığı gibi kayıt defterine konur. SnippetsIndex.xml dosyası örneği aşağıdadır:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<SnippetCollection>  
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">  
        <SnippetDir>  
            <OnOff>On</OnOff>  
            <Installed>true</Installed>  
            <Locale>1033</Locale>  
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>  
            <LocalizedName>Snippets</LocalizedName>  
        </SnippetDir>  
    </Language>  
</SnippetCollection>  
```  
  
 \<Dil > etiketi, dil kimliği belirtir ( `Lang` özniteliği) ve dil hizmeti GUID.  
  
 Bu örnekte, Visual Studio yükleme klasöründe, dil hizmetinin yüklü olduğu varsayılır. Kullanıcının geçerli yerel ayar kimliği ile değiştirildiği LCID % Birden çok \<SnippetDir > etiketleri eklenebilir, her farklı bir dizin ve yerel ayar için bir tane. Ayrıca, bir kod parçacığı klasörüne alt klasörlerdeki her biri ile dizin dosyasında tanımlanır içerebilir \<SnippetSubDir > etiketi katıştırılmış bir \<SnippetDir > etiketi.  
  
 Kullanıcılar kendi diliniz için de oluşturabilirsiniz. Bu genellikle kullanıcının ayarlarını, örneğin klasöründeki *[TestDocs]* \Code parçacıkları\\ *[TestLanguage]* \Test kod parçacıkları, burada *[TestDocs]* Visual Studio kullanıcı ayarları klasörün konumu.  
  
 Aşağıdaki değişim öğeleri depolanmış bir yolda yerleştirilebilir \<DirPath > etiketinde dizin dosyası.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|LCID %|Yerel ayar kimliği.|  
|InstallRoot %|Visual Studio, örneğin, C:\Program Files\Microsoft Visual Studio 8 yükleme klasörünü kök.|  
|ProjDir %|Geçerli projeyi içeren klasörü.|  
|ProjItem %|Geçerli proje öğesi içeren klasör.|  
|TestDocs %|Klasöründe kullanıcının ayarlarını, örneğin, C:\Documents ve ayarları\\ *[username]* \My Documents\Visual Studio\8.|  
  
### <a name="enabling-code-snippets-for-your-language-service"></a>Kod parçacıkları, dil hizmeti için etkinleştirme  
 Ekleyerek dil hizmetiniz için kod parçacıkları etkinleştirebilirsiniz <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> özniteliği, Vspackage'e (bkz [eski dil hizmetinde kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md) Ayrıntılar için). <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> Ve <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> parametreler isteğe bağlıdır, ancak içermesi gerekir `SearchPaths` haber vermek için parametre adlı **kod parçacıkları Yöneticisi** , kod parçacıkları konumunu.  
  
 Bu öznitelik kullanmaya ilişkin bir örnek verilmiştir:  
  
```  
[ProvideLanguageCodeExpansion(  
         typeof(TestSnippetLanguageService),  
         "Test Snippet Language",          // Name of language used as registry key  
         0,                               // Resource ID of localized name of language service  
         "Test Snippet Language",        // Name of Language attribute in snippet template  
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index  
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets  
```  
  
### <a name="calling-the-expansion-provider"></a>Genişletme sağlayıcıya çağrı  
 Dil hizmeti ekleme çağrılan yöntem yanı sıra, herhangi bir kod parçacığı eklenmesini denetler.  
  
## <a name="calling-the-expansion-provider-for-code-snippets"></a>Genişletme sağlayıcısını çağırmak için kod parçacıkları  
 Genişletme sağlayıcısını çağırmak için iki yolu vardır: bir menü komutunu kullanarak veya bir tamamlama listesinden bir kısayolunu kullanarak.  
  
### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Bir menü komutu kullanılarak bir kod parçacığı ekleme  
 Kod parçacığı tarayıcıda görüntülemek için bir menü komutu kullanmak için bir menü komutu eklemek ve sonra çağrı <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> yönteminde <xref:Microsoft.VisualStudio.Package.ExpansionProvider> arabirimi yanıt olarak bu menü komutu.  
  
1.  Bir komut ve bir düğmeyi .vsct dosyanıza ekleyin. Bu nedenle de yapmak için yönergeler bulabilirsiniz [izlenecek yol: bir menü komutu kullanarak Visual Studio Paketi şablonu oluşturma](http://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
2.  Öğesinden bir sınıf türetin <xref:Microsoft.VisualStudio.Package.ViewFilter> sınıf ve geçersiz kılma <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> desteği için yeni menü komutu belirtmek için yöntemi. Bu örnekte, her zaman menü komutunu sağlar.  
  
    ```csharp  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)  
                : base(mgr, view)  
            {  
            }  
  
            protected override int QueryCommandStatus(ref Guid guidCmdGroup,  
                                                      uint nCmdId)  
            {  
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);  
                // If the base class did not recognize the command then  
                // see if we can handle the command.  
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)  
                {  
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                    {  
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                        {  
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);  
                        }  
                    }  
                }  
                return hr;  
            }  
        }  
    }  
    ```  
  
3.  Geçersiz kılma <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> yönteminde <xref:Microsoft.VisualStudio.Package.ViewFilter> almak için sınıf <xref:Microsoft.VisualStudio.Package.ExpansionProvider> nesne ve çağrı <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> o nesne üzerindeki yöntemi.  
  
    ```csharp  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public override bool HandlePreExec(ref Guid guidCmdGroup,  
                                               uint nCmdId,  
                                               uint nCmdexecopt,  
                                               IntPtr pvaIn,  
                                               IntPtr pvaOut)  
            {  
                if (base.HandlePreExec(ref guidCmdGroup,  
                                       nCmdId,  
                                       nCmdexecopt,  
                                       pvaIn,  
                                       pvaOut))  
                {  
                    // Base class handled the command.  Do nothing more here.  
                    return true;  
                }  
  
                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                {  
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                    {  
                        ExpansionProvider ep = this.GetExpansionProvider();  
                        if (this.TextView != null && ep != null)  
                        {  
                            bool bDisplayed = ep.DisplayExpansionBrowser(  
                                this.TextView,  
                                "TestLanguagePackage Snippet:",  
                                null,  
                                false,  
                                null,  
                                false);  
                        }  
                        return true;   // Handled the command.  
                    }  
                }  
                return false;   // Did not handle the command.  
            }  
        }  
    }  
  
    ```  
  
     Aşağıdaki yöntemleri <xref:Microsoft.VisualStudio.Package.ExpansionProvider> sınıfı çağrılır Visual Studio tarafından verilen sırasına göre kod parçacığı ekleme işlemi sırasında:  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     Sonra <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> yöntemi çağrıldığında, kod parçacığının eklenmiş ve <xref:Microsoft.VisualStudio.Package.ExpansionProvider> nesnedir yalnızca eklenmiş bir kod parçacığını değiştirmek için kullanılan bir özel düzenleme modunda.  
  
### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Bir kısayol kullanarak bir kod parçacığı ekleme  
 Tamamlama listesinden bir kısayol menü komutunu uygulama daha çok daha karmaşık uygulamasıdır. Kod parçacığı kısayollarında önce IntelliSense Sözcük tamamlama listesine eklemeniz gerekir. Ardından kod parçacığı kısayol adı tamamlama sonucunda eklendiğinde algılamalıdır. Son olarak, kod parçacığı başlık ve kısayol adı kullanarak yolu almalı ve bu bilgileri geçirmek <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> metodunda <xref:Microsoft.VisualStudio.Package.ExpansionProvider> yöntemi.  
  
 Kod parçacığı kısayollarında Sözcük tamamlama listesine eklemek için bunlara ekleyin <xref:Microsoft.VisualStudio.Package.Declarations> nesnesine, <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıfı. Bir kod parçacığı ad kısaca tanımlayabilirsiniz emin olmanız gerekir. Bir örnek için bkz. [izlenecek yol: bir liste, yüklü kod parçacıkları (eski uygulama) alma](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
 Kod parçacığı kısayolun ekleme algılayabilir <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> yöntemi <xref:Microsoft.VisualStudio.Package.Declarations> sınıfı. Kaynak dosyaya kod parçacığı adı zaten eklenmiş olduğundan, genişletme eklendiğinde kaldırılmalıdır. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> Yöntemi için kod parçacığı ekleme noktasını tanımlayan bir yayılma alır; aralık kaynak dosyadaki tüm kod parçacığı adı içeriyorsa, söz konusu ad kod parçacığı tarafından değiştirilir.  
  
 Bir hali aşağıdadır bir <xref:Microsoft.VisualStudio.Package.Declarations> parçacığı ekleme kısayol adı verilen işleme sınıfı. Diğer yöntemlerle <xref:Microsoft.VisualStudio.Package.Declarations> sınıfı, açıklık için atlanmış. Bu sınıfın Oluşturucusu alır Not bir <xref:Microsoft.VisualStudio.Package.LanguageService> nesne. Bu, sürümünden geçirilebilir <xref:Microsoft.VisualStudio.Package.AuthoringScope> nesne (örneğin, uygulamanız <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıfı alabilir <xref:Microsoft.VisualStudio.Package.LanguageService> nesne oluşturucusunda ve bu nesne için geçirin, `TestDeclarations` sınıf oluşturucu).  
  
```  
[C#]  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList       declarations;  
        private LanguageService languageService;  
        private TextSpan        commitSpan;  
  
        public TestDeclarations(LanguageService langService)  
            : base()  
        {  
            languageService = langService;  
            declarations = new ArrayList();  
        }  
  
        // This method is used to add declarations to the internal list.  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        // This method is called to get the string to commit to the source buffer.  
        // Note that the initial extent is only what the user has typed so far.  
        public override string OnCommit(IVsTextView textView,  
                                        string textSoFar,  
                                        char commitCharacter,  
                                        int index,  
                                        ref TextSpan initialExtent)  
        {  
            // We intercept this call only to get the initial extent  
            // of what was committed to the source buffer.  
            commitSpan = initialExtent;  
  
            return base.OnCommit(textView,  
                                 textSoFar,  
                                 commitCharacter,  
                                 index,  
                                 ref initialExtent);  
        }  
  
        // This method is called after the string has been committed to the source buffer.  
        public override char OnAutoComplete(IVsTextView textView,  
                                            string committedText,  
                                            char commitCharacter,  
                                            int index)  
        {  
            TestDeclaration item = declarations[index] as TestDeclaration;  
            if (item != null)  
            {  
                // In this example, TestDeclaration identifies types with a string.  
                // You can choose a different approach.  
                if (item.Type == "snippet")  
                {  
                    Source src = languageService.GetSource(textView);  
                    if (src != null)  
                    {  
                        ExpansionProvider ep = src.GetExpansionProvider();  
                        if (ep != null)  
                        {  
                            string title;  
                            string path;  
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;  
                            if (commitLength < committedText.Length)  
                            {  
                                // Replace everything that was inserted  
                                // so calculate the span of the full  
                                // insertion, taking into account what  
                                // was inserted when the commitSpan  
                                // was obtained in the first place.  
                                commitSpan.iEndIndex += (committedText.Length - commitLength);  
                            }  
  
                            if (ep.FindExpansionByShortcut(textView,  
                                                           committedText,  
                                                           commitSpan,  
                                                           true,  
                                                           out title,  
                                                           out path))  
                            {  
                                ep.InsertNamedExpansion(textView,  
                                                        title,  
                                                        path,  
                                                        commitSpan,  
                                                        false);  
                            }  
                        }  
                    }  
                }  
            }  
            return '\0';  
        }  
    }  
}  
```  
  
 Dil hizmeti kısayol adı girdiğinde, çağrı <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> dosya adı ve kod parçacığı başlığı elde etmek için yöntemi. Daha sonra dil hizmeti çağırır <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> yönteminde <xref:Microsoft.VisualStudio.Package.ExpansionProvider> kod parçacığını eklemek için sınıfı. Aşağıdaki yöntemlerden Visual Studio tarafından verilen sırayla çağrılır <xref:Microsoft.VisualStudio.Package.ExpansionProvider> kod parçacığını ekleme işlemi sırasında sınıfı:  
  
1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
   Dil hizmetiniz için yüklü kod parçacıklarının listesini alma hakkında daha fazla bilgi için bkz. [izlenecek yol: bir liste, yüklü kod parçacıkları (eski uygulama) alma](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
## <a name="implementing-the-expansionfunction-class"></a>ExpansionFunction sınıfı  
 Bir genişletme işlevi bir kod parçacığı şablonunda katıştırılır ve bir alanın yerleştirileceği bir veya daha fazla değer döndüren bir adlandırılmış bir işlevdir. Dil hizmetinizde genişletme işlevleri desteklemek için öğesinden bir sınıf türetin <xref:Microsoft.VisualStudio.Package.ExpansionFunction> sınıfı ve uygulama <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> yöntemi. Ardından geçersiz kılmanız gerekir <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> yönteminde <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfının yeni bir örneğini oluşturmada sürümünüzün döndürülecek <xref:Microsoft.VisualStudio.Package.ExpansionFunction> desteklediğiniz her genişletme işlevi için sınıf. Bir genişletme işlevden olası değerlerin bir listesini destekliyorsa, geçersiz kılmalısınız <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> yönteminde <xref:Microsoft.VisualStudio.Package.ExpansionFunction> bu değerlerin bir listesini döndürmek için sınıf.  
  
 Bağımsız değişken almaz veya diğer alanlarına erişmek gereken bir genişletme işlevi, genişletme sağlayıcısını genişletme işlev çağrıldığı zaman tarafından tam olarak atanamaz düzenlenebilir bir alanı ile ilişkilendirilmemelidir. Sonuç olarak, genişletme işlevi bağımsız değişkenlerinden veya diğer herhangi bir alan değeri elde etmek mümkün değil.  
  
### <a name="example"></a>Örnek  
 Aşağıda, bir örnek nasıl bir basit genişletme işlevini çağırdı `GetName` uygulanabilir. Bu genişletme işlevi birkaç temel sınıf adına genişletme işlev örneği her zaman ekler (ilişkili kod parçacığı her zaman için karşılık gelen eklenir).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private int classNameCounter = 0;  
  
        public override ExpansionFunction CreateExpansionFunction(  
            ExpansionProvider provider,  
            string functionName)  
        {  
            ExpansionFunction function = null;  
            if (functionName == "GetName")  
            {  
                ++classNameCounter;  
                function = new TestGetNameExpansionFunction(provider, classNameCounter);  
            }  
            return function;  
        }  
    }  
  
    internal class TestGetNameExpansionFunction : ExpansionFunction  
    {  
        private int nameCount;  
  
        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)  
            : base(provider)  
        {  
            nameCount = counter;  
        }  
  
        public override string GetCurrentValue()  
        {  
            string name = "TestClass";  
            name += nameCount.ToString();  
            return name;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski dil hizmeti özellikleri](../../extensibility/internals/legacy-language-service-features1.md)   
 [Eski dil hizmeti kaydediliyor](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Kod parçacıkları](../../ide/code-snippets.md)   
 [İzlenecek Yol: Yüklü Kod Parçacıklarının Listesini Alma (Eski Uygulama)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

