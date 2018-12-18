---
title: Eski dil hizmetinde üye tamamlama | Microsoft Docs
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
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b8b5940e473c639600c30e66e7dc0c732359322d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790999"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Üye Tamamlama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

IntelliSense üye tamamlama sınıf, yapı, sabit listesi veya ad alanı gibi belirli bir kapsam olası üyelerinin bir listesini görüntüleyen bir araç ipucu ' dir. Kullanıcı "this" bir nokta türleri, örneğin, C# ' ta sınıfın veya yapının geçerli kapsamda tüm üyelerin listesi kullanıcının seçim yapabileceği bir listede sunulur.  
  
 Yönetilen paket çerçevesini (MPF), araç ipucu ve araç ipucu listesinde yönetmek için destek sağlar; gereken şey işbirliği gelen listesinde görüntülenen veri sağlamak için.  
  
 Eski dil Hizmetleri bir VSPackage'ı bir parçası olarak uygulanır, ancak dil hizmeti özellikleri uygulamak için daha yeni MEF uzantıları kullanmaktır. Daha fazla bilgi için bkz. [düzenleyiciyi ve dil hizmetlerini genişletme](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Yeni bir düzenleyici API hemen kullanmaya başlamak öneririz. Bu dil hizmetinizin performansını ve yeni düzenleyici özellikleri yararlanmanıza olanak tanır.  
  
## <a name="how-it-works"></a>Nasıl çalışır?  
 MPF sınıflarını kullanarak bir üye listesi gösterilen iki yollar şunlardır:  
  
- Giriş işaretini bir tanımlayıcı veya bir üye tamamlama karakterinden sonraki konumlandırma ve seçerek **üyeleri Listele** gelen **IntelliSense** menüsü.  
  
- <xref:Microsoft.VisualStudio.Package.IScanner> Tarayıcı üye tamamlama karakter algılar ve bir belirteç tetikleyicisi ayarlar <xref:Microsoft.VisualStudio.Package.TokenTriggers> bu karakteri.  
  
  Bir üye tamamlama karakter, bir sınıf, yapı ya da numaralandırma üyesi izlemek için olduğunu gösterir. Örneğin, C# veya Visual Basic'te üye tamamlama karakter olan bir `.`, c++'ta karakter ya da olsa bir `.` veya `->`. Üye seçme karakter tarandığında tetikleyici değeri ayarlanır.  
  
### <a name="the-intellisense-member-list-command"></a>IntelliSense üye Listele komutu  
 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Komut başlatan bir çağrı <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodunda <xref:Microsoft.VisualStudio.Package.Source> sınıfı ve <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> sırayla yöntemini çağırır <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi ayrıştırıcı ayrıştırma nedeni ile <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
 Ayrıştırıcının bağlam belirteci altında ya da geçerli konum hemen önce yanı sıra geçerli konumunu belirler. Bu belirteci temel alınarak, bildirimleri listesi sunulur. Örneğin, C# ' de giriş işaretini bir sınıf üyesi ve seçim konum değilse, **üyeleri Listele**, sınıfın tüm üyeleri bir listesini alın. Giriş işaretini bir nesne değişkeninin izleyen bir süre sonra getirin, sınıf nesnesini temsil tüm üyelerinin listesini alın. Üye listesi gösterildiğinde giriş işaretini bir üyede konumlandırılmış, listeden bir üye seçme giriş işaretini bir listedeki açıktır üye değiştirir.  
  
### <a name="the-token-trigger"></a>Tetikleyici belirteç  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers> Tetikleyici başlatan bir çağrı <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodunda <xref:Microsoft.VisualStudio.Package.Source> sınıfı ve <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> yöntemini çağırır, ayrıştırıcının ayrıştırma nedeni ile <xref:Microsoft.VisualStudio.Package.ParseReason> (belirteç tetikleyici da içeriyorsa <xref:Microsoft.VisualStudio.Package.TokenTriggers> bayrak Ayrıştırma nedeni <xref:Microsoft.VisualStudio.Package.ParseReason> üye seçimi ve küme ayracı vurgulayarak birleştirir).  
  
 Ayrıştırıcının geçerli bağlam belirler konumlandırma üyeyi seçin önce karakter neler yazıldığını yanı sıra. Bu bilgilerden, ayrıştırıcının istenen kapsam tüm üyelerinin bir listesini oluşturur. Bu bildirimler listesi depolanan <xref:Microsoft.VisualStudio.Package.AuthoringScope> öğesinden döndürülen nesne <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi. Tüm bildirimleri döndürülürse, üye tamamlama araç ipucu görüntülenir. Araç İpucu örneği tarafından yönetilen <xref:Microsoft.VisualStudio.Package.CompletionSet> sınıfı.  
  
## <a name="enabling-support-for-member-completion"></a>Üye tamamlama desteğini etkinleştirme  
 Olmalıdır `CodeSense` kayıt defteri girişi, herhangi bir IntelliSense işlemi desteklemek için 1 olarak ayarlayın. Bu kayıt defteri girişi, geçirilen bir adlandırılmış parametre kullanılarak ayarlanabilir. <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> dil paket ile ilişkili kullanıcı özniteliği. Dil hizmeti sınıfları bu kayıt defteri girdisinden değerini okumak <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> özelliği <xref:Microsoft.VisualStudio.Package.LanguagePreferences> sınıfı.  
  
 Tarayıcınız belirteci tetikleyicisi döndürürse <xref:Microsoft.VisualStudio.Package.TokenTriggers>ve, ayrıştırıcı bildirimleri listesini döndürür ve ardından üye tamamlanma listesi görüntülenir.  
  
## <a name="supporting-member-completion-in-the-scanner"></a>Tarayıcı destekleyen üye tamamlama  
 Tarayıcı bir üye tamamlama karakter algılamak ve belirteç tetikleyicisi ayarlayın <xref:Microsoft.VisualStudio.Package.TokenTriggers> bu karakteri zaman ayrıştırılır.  
  
### <a name="example"></a>Örnek  
 Üye tamamlama karakter algılama ve uygun ayar basitleştirilmiş bir örnek aşağıda verilmiştir <xref:Microsoft.VisualStudio.Package.TokenTriggers> bayrağı. Bu örnek yalnızca tanım amaçlıdır. Tarayıcınız bir yöntem içerdiğini varsayar `GetNextToken` tanımlar ve bir metin satırından belirteçleri döndürür. Karakter doğru tür gördüğünde her kod örneği yalnızca tetikleyici ayarlar.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char memberSelectChar = '.';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (c == memberSelectChar)  
                {  
                        tokenInfo.Trigger |= TokenTriggers.MemberSelect;  
                }  
            }  
            return foundToken;  
        }  
    }  
}  
```  
  
## <a name="supporting-member-completion-in-the-parser"></a>Ayrıştırıcının destekleyen üye tamamlama  
 Üye tamamlama için <xref:Microsoft.VisualStudio.Package.Source> sınıf çağrıları <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> yöntemi. Türetilen bir sınıfta listenin uygulamalıdır <xref:Microsoft.VisualStudio.Package.Declarations> sınıfı. Bkz: <xref:Microsoft.VisualStudio.Package.Declarations> uygulanmalı yöntemleri hakkında daha fazla ayrıntı için sınıf.  
  
 Ayrıştırıcının çağrılır <xref:Microsoft.VisualStudio.Package.ParseReason> veya <xref:Microsoft.VisualStudio.Package.ParseReason> ne zaman bir üye seçin karakter türü. Verilen konuma <xref:Microsoft.VisualStudio.Package.ParseRequest> nesnedir hemen üyeyi seçin sonra karakter. Ayrıştırıcının, kaynak kodunda, belirli bir noktada bir üye listesinde görünen tüm üyelerinin adları toplamanız gerekir. Ardından ayrıştırıcı, kullanıcının üye seçme karakteri ile ilişkili istediği kapsamını belirlemek için geçerli satırı ayrıştırma gerekir.  
  
 Üye karakter seçebilmeniz bu kapsam tanıtıcı türüne bağlıdır. Örneğin, verilen C# ' ta bir üye değişkeni `languageService` türü olan `LanguageService`yazarak **languageService.** tüm üyelerinin bir listesini oluşturur `LanguageService` sınıfı. Ayrıca, C# ' ta, yazmaya **bu.** Geçerli kapsam içinde bir sınıfın tüm üyeleri listesi oluşturur.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek doldurmak için bir yol gösterir. bir <xref:Microsoft.VisualStudio.Package.Declarations> listesi. Bu kod ayrıştırıcı bir bildirim oluşturur ve çağırarak listeye ekler varsayar bir `AddDeclaration` metodunda `TestAuthoringScope` sınıfı.  
  
```csharp  
using System.Collections;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclaration  
    {  
        public string Name;            // Name of declaration  
        public int     TypeImageIndex; // Glyph index  
        public string Description;     // Description of declaration  
  
        public TestDeclaration(string name, int typeImageIndex, string description)  
        {  
            this.Name = name;  
            this.TypeImageIndex = typeImageIndex;  
            this.Description = description;  
        }  
    }  
  
    //===================================================  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList declarations;  
  
        public TestDeclarations()  
            : base()  
        {  
            declarations = new ArrayList();  
        }  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        //////////////////////////////////////////////////////////////////////  
        // Declarations of class methods that must be implemented.  
        public override int GetCount()  
        {  
            // Return the number of declarations to show.  
            return declarations.Count;  
        }  
  
        public override string GetDescription(int index)  
        {  
            // Return the description of the specified item.  
            string description = "";  
            if (index >= 0 && index < declarations.Count)  
            {  
                description = ((TestDeclaration)declarations[index]).Description;  
            }  
            return description;  
        }  
  
        public override string GetDisplayText(int index)  
        {  
            // Determine what is displayed in the tool tip list.  
            string text = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                text = ((TestDeclaration)declarations[index]).Name;  
            }  
            return text;  
        }  
  
        public override int GetGlyph(int index)  
        {  
            // Return index of image to display next to the display text.  
            int imageIndex = -1;  
            if (index >= 0 && index < declarations.Count)  
            {  
                imageIndex = ((TestDeclaration)declarations[index]).TypeImageIndex;  
            }  
            return imageIndex;  
        }  
  
        public override string GetName(int index)  
        {  
            string name = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                name = ((TestDeclaration)declarations[index]).Name;  
            }  
            return name;  
        }  
    }  
  
    //===================================================  
    public class TestAuthoringScope : AuthoringScope  
    {  
        private TestDeclarations declarationsList;  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            if (declaration != null)  
            {  
                if (declarationsList == null)  
                {  
                    declarationsList = new TestDeclarations();  
                }  
                declarationsList.AddDeclaration(declaration);  
            }  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return declarationsList;  
        }  
  
        /////////////////////////////////////////////////  
        // Remainder of AuthoringScope methods not shown.  
        /////////////////////////////////////////////////  
    }  
  
    //===================================================  
    class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            TestAuthoringScope scope = new TestAuthoringScope();  
            if (req.Reason == ParseReason.MemberSelect ||  
                req.Reason == ParseReason.MemberSelectAndHighlightBraces)  
            {  
                // Gather list of declarations based on what the user  
                // has typed so far. In this example, this list is an array of  
                // MemberDeclaration objects (a helper class you might implement  
                // to hold member declarations).  
                // How this list is gathered is dependent on the parser  
                // and is not shown here.  
                MemberDeclarations memberDeclarations;  
                memberDeclarations = GetDeclarationsForScope();  
  
                // Now populate the Declarations list in the authoring scope.  
                // GetImageIndexBasedOnType() is a helper method you  
                // might implement to convert a member type to an index into  
                // the image list returned from the language service.  
                foreach (MemberDeclaration dec in memberDeclarations)  
                {  
                    scope.AddDeclaration(new TestDeclaration(  
                                             dec.Name,  
                                             GetImageIndexBasedOnType(dec.Type),  
                                             dec.Description));  
                }  
            }  
            return scope;  
        }  
    }  
}  
```

