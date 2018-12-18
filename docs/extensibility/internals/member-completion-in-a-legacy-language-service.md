---
title: Eski dil hizmeti üye tamamlanmasında | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f618c9500b79ec5e1ef0db8c2c6b8b130c6c75b
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057277"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Üye Tamamlama

IntelliSense üye tamamlama sınıf, yapı, numaralandırma veya ad alanı gibi belirli bir kapsam olası üyelerinin listesini görüntüleyen bir araç ipucu olur. Kullanıcı "Bu" ardından bir noktayla türleri, örneğin, C# ' ta sınıf veya yapı geçerli kapsamdaki tüm üyelerin listesi Kullanıcı seçebileceği bir liste sunulur.

Yönetilen paket framework (MPF) araç ipucu ve araç ipucu listesinde yönetmek için destek sağlar; gereken tek şey iş Birliği dan listesinde görüntülenen verileri sağlamak için ayrıştırıcı.

Eski dil hizmetler bir VSPackage bir parçası olarak uygulanır, ancak dil hizmet özellikleri uygulamak için daha yeni MEF uzantıları kullanmak için bir yoludur. Daha fazla bilgi bulmak için bkz: [Düzenleyicisi ve dil Hizmetleri genişletme](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Yeni Düzenleyicisi API mümkün olan en kısa sürede kullanmaya başlamanızı öneriyoruz. Bu dil hizmetinizin performansını ve yeni Düzenleyicisi özelliklerden yararlanmak sağlar.

## <a name="how-it-works"></a>Nasıl çalışır?

MPF sınıfları kullanma üye listesini gösterilen iki yolla verilmiştir:

- Tanımlayıcı veya bir üye tamamlama karakterinden sonraki şapka konumlandırma ve seçerek **listesi üyeleri** gelen **IntelliSense** menüsü.

- <xref:Microsoft.VisualStudio.Package.IScanner> Tarayıcı bir üye tamamlama karakter algılar ve bir belirteç tetikleyicisi ayarlar [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) bu karakteri.

Üye tamamlama karakteri izlemek için bir sınıf, yapı veya numaralandırma üyesi olduğunu gösterir. Örneğin, C# veya Visual Basic üye tamamlama karakterdir bir `.`, c++'ta karakter ya da olsa da bir `.` veya `->`. Üye seçim karakter tarandığında tetikleyici değer ayarlanır.

### <a name="the-intellisense-member-list-command"></a>IntelliSense üye Listele komutu

<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Komut yapılan bir çağrı başlatır <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> yöntemi <xref:Microsoft.VisualStudio.Package.Source> sınıfı ve <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> yöntemini de çağırır <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi ayrıştırıcı ayrıştırma nedeni ile [ParseReason.DisplayMemberList ](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>).

Ayrıştırıcı bağlamı altında veya geçerli konumu hemen önce belirteci yanı sıra geçerli konumunu belirler. Belirteçte bağlı olarak, bildirimler listesi sunulur. Örneğin, C# ' de bir sınıf üyesi ve seçim şapka getirin varsa, **listesi üyeleri**, sınıfın tüm üyelerin listesini alın. Bir nesne değişkeni izleyen bir süre sonra şapka getirin, temsil nesne tüm üyeleri sınıfın listesini alın. Üye listesi gösterildiğinde üyede düzeltme işareti konumlandırılır, üye listeden seçerek düzeltme işareti listeden birini ile açıktır üye değiştirir.

### <a name="the-token-trigger"></a>Belirteç tetikleyici

[TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) tetikleyici için bir çağrı başlatır <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> yöntemi <xref:Microsoft.VisualStudio.Package.Source> sınıfı ve <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> yöntemi, sırayla ayrıştırıcının ayrıştırma nedeni ile çağırır [ ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>). Belirteç tetikleyici de dahil edilmişse [TokenTriggers.MatchBraces](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) bayrağı, ayrıştırma nedeni [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>), üye seçimi ve küme parantezi vurgulama birleştirir .

Geçerli bağlam ayrıştırıcı belirler üye seçmeden önce karakter neler yazıldığını yanı sıra, konum. Bu bilgilerden, istenen kapsamının tüm üyelerin listesi ayrıştırıcı oluşturur. Bu bildirimler listesi depolanan <xref:Microsoft.VisualStudio.Package.AuthoringScope> sunucudan döndürülen nesne <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi. Tüm bildirimler döndürülürse, üye tamamlama araç ipucu görüntülenir. Araç İpucu örneği tarafından yönetilen <xref:Microsoft.VisualStudio.Package.CompletionSet> sınıfı.

## <a name="enable-support-for-member-completion"></a>Üye tamamlama desteğini etkinleştirme

Bilmeniz gereken `CodeSense` kayıt defteri girdisini herhangi IntelliSense işlemi desteklemek için 1 olarak ayarlayın. Bu kayıt defteri girdisi geçirilen adlandırılmış bir parametre ile ayarlayabilirsiniz <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> dil paket ile ilişkili kullanıcı özniteliği. Bu kayıt defteri girdisinden değerini dil hizmet sınıfları okuma <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> özellikte <xref:Microsoft.VisualStudio.Package.LanguagePreferences> sınıfı.

Tarayıcınız belirteci tetikleyicisi döndürürse [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)ve ayrıştırıcısı sürümünüzü bildirimleri listesini döndürür ve ardından üye tamamlanma listesi görüntülenir.

## <a name="support-member-completion-in-the-scanner"></a>Tarayıcı desteği üye tamamlama

Tarayıcı bir üye tamamlama karakter algılamak ve belirteç tetikleyicisi ayarlamak [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) bu karakteri zaman ayrıştırılır.

### <a name="scanner-example"></a>Tarayıcı Örnek

İşte üye tamamlama karakter algılama ve uygun ayar basitleştirilmiş bir örnek <xref:Microsoft.VisualStudio.Package.TokenTriggers> bayrağı. Bu örnek yalnızca tanım amaçlıdır. Tarayıcınız bir yöntem içerdiğini varsayar `GetNextToken` tanımlar ve bir metin satırından belirteçleri verir. Karakter sağ türü görür her kod örneği yalnızca tetikleyici ayarlar.

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

## <a name="support-member-completion-in-the-parser"></a>Üye tamamlama ayrıştırıcısını desteği

Üye tamamlanması için <xref:Microsoft.VisualStudio.Package.Source> sınıfı çağrıları <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> yöntemi. Türetilmiş bir sınıf listesi uygulamalıdır <xref:Microsoft.VisualStudio.Package.Declarations> sınıfı. Bkz: <xref:Microsoft.VisualStudio.Package.Declarations> sınıfını uygulaması gerekiyor yöntemleri hakkında ayrıntılar için.

Ayrıştırıcının çağrılır [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) veya [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) zaman bir üye seçin karakter yazdınız. Verilen konumu <xref:Microsoft.VisualStudio.Package.ParseRequest> nesnesidir hemen üye seçtikten sonra karakter. Ayrıştırıcının kaynak kodundaki belirli o noktada üye listede görünebilir tüm üyelerinin adlarını toplamanız gerekir. Ardından ayrıştırıcı kullanıcının üye seçin karakteri ile ilişkili istediği kapsamını belirlemek için geçerli satır ayrıştırma gerekir.

Üye seçmeden önce karakter bu kapsamı tanımlayıcının türüne dayalıdır. Örneğin, verilen C# ' ta üye değişkeni `languageService` bir tür olan `LanguageService`yazarak **languageService.** tüm üyelerini listesini üreten `LanguageService` sınıfı. Ayrıca C# ' ta yazarak **bu.** Geçerli kapsamdaki sınıfın tüm üyelerin listesi oluşturur.

### <a name="parser-example"></a>Ayrıştırıcı örneği

Aşağıdaki örnek, doldurmak için bir yol gösterir. bir <xref:Microsoft.VisualStudio.Package.Declarations> listesi. Bu kod ayrıştırıcı bir bildirimi oluşturur ve çağırarak listeye ekler varsayar bir `AddDeclaration` yöntemi `TestAuthoringScope` sınıfı.

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