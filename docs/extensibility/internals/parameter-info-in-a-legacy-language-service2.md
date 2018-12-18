---
title: Eski dil Service2 parametre bilgilerini | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b562f5dd2c7e4f3851f6ed16e0f0007ef65e14cb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863262"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Eski dil hizmetinde parametre bilgisi
IntelliSense parametre bilgisi, kullanıcı, parametre listesi yazdığında, yöntemin imzası görüntüleyen bir araç ipucu başlangıç karakteri (genellikle bir açık parantez) için bir yöntem parametresi listesinden ' dir. Her parametre girilmesi ve parametre ayırıcı (genellikle bir virgül) yazılı olarak araç ipucu bir sonraki parametreyi kalın olarak göstermek için güncelleştirilir.  
  
 Yönetilen paket framework (MPF) sınıfları, parametre bilgisi araç ipucu yönetmek için destek sağlar. Ayrıştırıcının parametresi Başlat, parametre ardından, ve parametresi bitiş karakterlerini ve yöntem imzaları ve bunların ilişkili parametrelerin bir listesi sağlamalısınız algılaması gerekir.  
  
 Eski dil Hizmetleri bir VSPackage'ı bir parçası olarak uygulanır, ancak dil hizmeti özellikleri uygulamak için daha yeni MEF uzantıları kullanmaktır. Daha fazla bilgi için bkz. [düzenleyiciyi ve dil hizmetlerini genişletme](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Yeni bir düzenleyici API hemen kullanmaya başlamak öneririz. Bu dil hizmetinizin performansını ve yeni düzenleyici özellikleri yararlanmanıza olanak tanır.  
  
## <a name="implementation"></a>Uygulama  
 Ayrıştırıcının tetikleyici değer ayarlamalısınız <xref:Microsoft.VisualStudio.Package.TokenTriggers> bir parametre listesi başlangıç karakteri (genellikle bir açık parantez) bulduğunda ayarlanır. Ayarlamanız gerekir bir <xref:Microsoft.VisualStudio.Package.TokenTriggers> parametre ayırıcı (genellikle bir virgül) bulduğunda tetikleyin. Bu, güncelleştirilmesi ve bir sonraki parametreyi kalın olarak göstermek bir parametre bilgisi araç ipucu neden olur. Ayrıştırıcının tetikleyici değer ayarlamalısınız <xref:Microsoft.VisualStudio.Package.TokenTriggers> olduğunda, parametre listesi son karakter (genellikle bir kapatma ayracı) bulur.  
  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers> Tetikleyicisi değeri başlatan bir çağrı <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> sırayla çağıran yöntem <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi ayrıştırıcı bir ayrıştırma nedeni ile <xref:Microsoft.VisualStudio.Package.ParseReason>. Ayrıştırıcının parametre listesi'ı başlatmadan önce karakter tanımlayıcı tanınan bir yöntem adı olduğunu belirlerse, yöntem imzalarının eşleştirilmesi listesini döndürür. <xref:Microsoft.VisualStudio.Package.AuthoringScope> nesne. Herhangi bir yöntem imzaları bulunmazsa, parametre bilgisi araç ipucu listedeki ilk imzayla görüntülenir. Bu araç ipucu sonra daha fazla imzası yazıldığında güncelleştirilir. Parametre listesi son karakter yazıldığında, parametre bilgisi araç ipucu görünümünden kaldırılır.  
  
> [!NOTE]
>  Parametre bilgisi araç ipucu düzgün biçimlendirildiğinden, özellikleri geçersiz kılmalısınız emin olmak için <xref:Microsoft.VisualStudio.Package.Methods> uygun karaktere sağlamak için sınıf. Temel <xref:Microsoft.VisualStudio.Package.Methods> sınıfı varsayar C#-style metodu imzası. Bkz: <xref:Microsoft.VisualStudio.Package.Methods> sınıfı bu nasıl yapılabilir ilişkin ayrıntılar için.  
  
## <a name="enabling-support-for-the-parameter-info"></a>Parametre bilgisi desteğini etkinleştirme  
 Parametre bilgisi araç ipuçları desteklemek için ayarlamalısınız `ShowCompletion` parametresinin adlı <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> için `true`. Dil hizmeti bu kayıt defteri girdisinden değerini okur <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> özelliği.  
  
 Ayrıca, <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> özelliği ayarlanmalıdır `true` gösterilecek parametre bilgisi araç ipucu için.  
  
### <a name="example"></a>Örnek  
 Parametre listesi karakterleri algılamak ve uygun Tetikleyiciler ayarı basitleştirilmiş bir örnek aşağıda verilmiştir. Bu örnek yalnızca tanım amaçlıdır. Tarayıcınız bir yöntem içerdiğini varsayar `GetNextToken` tanımlar ve bir metin satırından belirteçleri döndürür. Karakter doğru tür gördüğünde her kod örneği yalnızca Tetikleyiciler ayarlar.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char parameterListStartChar = '(';  
        private const char parameterListEndChar   = ')';  
        private const char parameterNextChar      = ',';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (Char.IsPunctuation(c))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                    tokenInfo.EndIndex = index;  
  
                    if (c == parameterListStartChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;  
                    }  
                    else if (c == parameterListNextChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;  
                    else if (c == parameterListEndChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;  
                    }  
                }  
            return foundToken;  
        }  
    }  
}  
```  
  
## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Parametre bilgisi araç ipucu ayrıştırıcısını destekleme  
 <xref:Microsoft.VisualStudio.Package.Source> Sınıfı içeriğini ilgili bazı varsayımlarda <xref:Microsoft.VisualStudio.Package.AuthoringScope> ve <xref:Microsoft.VisualStudio.Package.AuthoringSink> parametre bilgisi araç ipucu görüntülenir ve sınıfları.  
  
- Ayrıştırıcının verilen <xref:Microsoft.VisualStudio.Package.ParseReason> parametre listesi başlangıç karakteri türü olduğunda.  
  
- Verilen konuma <xref:Microsoft.VisualStudio.Package.ParseRequest> nesnedir parametre listesinde hemen sonra karakter. Ayrıştırıcının getirin ve bunları sürümünüz listesinde depolayan kullanılabilir tüm yöntem bildirimleri imzalarını toplamak gerekir <xref:Microsoft.VisualStudio.Package.AuthoringScope> nesne. Bu liste, yöntem adı içerir yöntemi türü (veya dönüş türü) ve olası parametrelerin bir listesi. Bu liste, daha sonra yöntem imzası veya parametre bilgisi İpucunda görüntülenecek imzaları aranır.  
  
  Ayrıştırıcı tarafından belirtilen satırın ardından ayrıştırma gerekir <xref:Microsoft.VisualStudio.Package.ParseRequest> Girilmekte olan yöntemin yanı sıra kullanıcının ne kadar boyunca adı toplamak için nesnedir parametreleri metin. Bu yöntemin adını geçirerek gerçekleştirilir <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> metodunda <xref:Microsoft.VisualStudio.Package.AuthoringSink> nesnesi ve ardından arama <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> parametre listesi karakter başlattığınızda yöntemi ayrıştırılır, çağırma <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> yöntemi, parametre listesi sonraki karakteri, ayrıştırılmış ve son olarak çağıran <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> parametre listesi son karakter ayrıştırıldığında yöntemi. Bu yöntem çağrılarının sonuçlarını tarafından kullanılan <xref:Microsoft.VisualStudio.Package.Source> sınıfı parametre bilgisi araç ipucu uygun şekilde güncelleştirilecek.  
  
### <a name="example"></a>Örnek  
 Kullanıcı girebilir metin satırı aşağıda verilmiştir. Çizginin altındaki sayılar, hangi adımın (ayrıştırma taşır soldan sağa varsayılarak) satırı o konumda ayrıştırıcı tarafından gerçekleştirilen gösterir. Buradaki varsayım satırından önce her şeyi zaten "testfunc" yöntem imzası dahil olmak üzere, yöntem imzaları için ayrıştırıldıktan emin olur.  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 Ayrıştırıcının gereken adımlar aşağıda ana hatlarıyla özetlenen:  
  
1.  Ayrıştırıcı çağrıları <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> "testfunc" metni ile.  
  
2.  Ayrıştırıcı çağrıları <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.  
  
3.  Ayrıştırıcı çağrıları <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.  
  
4.  Ayrıştırıcı çağrıları <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.