---
title: Eski dil hizmetinde söz dizimi renklendirme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1d82a85958fd979a3d9d44375656b08356ef09d9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135954"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Eski dil hizmetinde söz dizimi renklendirme
Söz dizimi renklendirme farklı renkler ve stiller kaynak dosyasında görüntülenecek bir programlama dili farklı öğeleri neden olan bir özelliktir. Bu özelliği desteklemek için bir ayrıştırıcı veya sözcük öğeleri veya dosya belirteçleri türlerini tanımlamak tarayıcı sağlamanız gerekir. Anahtar sözcükler, (örneğin, parantez veya küme ayraçları) sınırlayıcıları ve açıklamaları farklı şekillerde renklendirme tarafından birçok dilde ayırt etmek.  
  
 Eski dil hizmetler bir VSPackage bir parçası olarak uygulanır, ancak dil hizmet özellikleri uygulamak için daha yeni MEF uzantıları kullanmak için bir yoludur. Daha fazla bilgi bulmak için bkz: [Düzenleyicisi ve dil Hizmetleri genişletme](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Yeni Düzenleyicisi API mümkün olan en kısa sürede kullanmaya başlamanızı öneriyoruz. Bu dil hizmetinizin performansını ve yeni Düzenleyicisi özelliklerden yararlanmak sağlar.  
  
## <a name="implementation"></a>Uygulama  
 Renklendirme desteklemek için yönetilen paket framework (MPF) içeren <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfı, hangi uygulayan <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> arabirimi. Bu sınıf ile etkileşime giren bir <xref:Microsoft.VisualStudio.Package.IScanner> belirteci ve renkleri belirlemek için. Tarayıcılar hakkında daha fazla bilgi için bkz: [eski dil hizmeti Ayrıştırıcı ve tarayıcı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). <xref:Microsoft.VisualStudio.Package.Colorizer> Sınıfı sonra her bir karakteri renk bilgilerini belirteciyle işaretler ve kaynak dosyayı görüntüleme Düzenleyicisi bu bilgileri döndürür.  
  
 Düzenleyici döndürülen renk colorable öğelerin listesini bir dizine bilgilerdir. Bir renk değeri ve yazı tipi özniteliklerini kümesi gibi kalın her colorable öğesi belirtir veya üstü çizili. Düzenleyici dil hizmetinizi kullanabileceğiniz varsayılan colorable öğeleri kümesi sağlar. Yapmanız gereken tek şey her bir belirteç türü için uygun renk dizini belirtin. Ancak, özel colorable öğeler ve sağladığınız dizinlerini kümesi için belirteçleri sağlar ve kendi varsayılan liste yerine colorable öğeleri listesi başvurun. De ayarlamalısınız `RequestStockColors` kayıt defteri girdisi için 0 (veya belirtmeyin `RequestStockColors` hiç giriş) özel renkler desteklemek için. Bu kayıt defteri girişini adlandırılmış bir parametre ile ayarlayabilirsiniz <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> kullanıcı tanımlı öznitelik. Dil hizmeti kaydetme ve onun seçeneklerini ayarlama hakkında daha fazla bilgi için bkz: [eski dil hizmeti kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## <a name="custom-colorable-items"></a>Özel Colorable öğeler  
 Kendi özel colorable öğeler sağlamak için geçersiz kılmanız gerekir <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> ve <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> yöntemi <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı. İlk yöntem dil hizmetinizin desteklediği özel colorable öğe sayısını döndürür ve ikinci dizini tarafından özel colorable öğesi alır. Özel colorable öğeleri varsayılan listesi oluşturun. Dil hizmetinizi oluşturucuda tüm yapmanız gereken olduğu tedarik colorable her öğe bir ada sahip. Visual Studio, burada colorable öğeleri farklı bir dizi kullanıcının seçtiği durumunu otomatik olarak işler. Bu adın ne görünür olduğundan **yazı tiplerini ve renkleri** özellik sayfasında **seçenekleri** iletişim kutusu (Visual Studio'da kullanılabilir **Araçları** menüsü) ve bu adı belirler bir kullanıcı geçersiz kılınmış rengi. Kullanıcının seçimlerini kayıt önbellekte depolanır ve renk adı tarafından erişilen. **Yazı tiplerini ve renkleri** özellik sayfası listeler, tüm alfabetik sırada renk adları, her dil adınızı; renk adıyla koyarak özel renkler gruplandırabilirsiniz şekilde Örneğin, "**TestLanguage - açıklama**"ve"**TestLanguage - anahtar sözcüğü**". Veya colorable öğelerinizi türüne göre gruplandırabilirsiniz "**Açıklama (TestLanguage)**"ve"**anahtar sözcüğü (TestLanguage)**". Dil adı gruplandırarak tercih edilir.  
  
> [!CAUTION]
>  Varolan colorable öğe adları ile çakışmaları önlemek için colorable öğe adı dil adı dahil önerilir.  
  
> [!NOTE]
>  Geliştirme sırasında renkleri birinin adını değiştirirseniz, Visual Studio renkleri erişilen ilk kez oluşturulan önbellek sıfırlamanız gerekir. Çalıştırarak bunu yapabilirsiniz **Deneysel Hive sıfırlama** Visual Studio SDK program menüsünden komutu.  
  
 Listesindeki ilk öğeyi colorable öğelerin hiçbir zaman başvurulan unutmayın. Visual Studio her zaman varsayılan metin rengini ve bu öğe için öznitelikler sağlar. Kolay bu postalarla bir yer tutucu colorable öğesi ilk öğe olarak sağlamak için yoludur.  
  
### <a name="high-color-colorable-items"></a>Yüksek renk Colorable öğeleri  
 Colorable öğeleri de 24 bit ya da yüksek renk değerlerini destekleyen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> arabirimi. MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> sınıf destekler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> arabirimi ve 24 bit renkleri normal renkler birlikte oluşturucuda belirtilir. Bkz: <xref:Microsoft.VisualStudio.Package.ColorableItem> daha fazla ayrıntı için sınıf. Aşağıdaki örnek, anahtar sözcükleri ve açıklamalar için 24 bit renkleri Ayarla gösterilmektedir. Kullanıcının masaüstünde 24 bit renk desteklendiğinde 24 bit renkleri kullanılır; Aksi takdirde, normal metin renkleri kullanılır.  
  
 , Dil için varsayılan renkleri bunlar unutmayın; Kullanıcı bu renkleri ne olursa olsun istedikleri değiştirebilirsiniz.  
  
### <a name="example"></a>Örnek  
 Bu örnek bildirme ve bir dizi özel colorable öğelerini kullanarak doldurmak için bir yol gösterir <xref:Microsoft.VisualStudio.Package.ColorableItem> sınıfı. Bu örnekte, 24 bit renkleri kullanarak anahtar sözcüğü ve yorum renklerini ayarlar.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private ColorableItem[] m_colorableItems;  
  
        TestLanguageService() : base()  
        {  
            m_colorableItems = new ColorableItem[] {  
                new ColorableItem("TestLanguage - Text",  
                                  "Text",  
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.Empty,  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT),  
                new ColorableItem("TestLanguage - Keyword",  
                                  "Keyword",  
                                  COLORINDEX.CI_MAROON,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.FromArgb(192,32,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_BOLD),  
                new ColorableItem("TestLanguage - Comment",  
                                  "Comment",  
                                  COLORINDEX.CI_DARKGREEN,  
                                  COLORINDEX.CI_LIGHTGRAY,  
                                  System.Drawing.Color.FromArgb(32,128,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT)  
                // ...  
                // Add as many colorable items as you want to support.  
            };  
        }  
    }  
}  
```  
  
## <a name="the-colorizer-class-and-the-scanner"></a>Renklendirici sınıfı ve tarayıcı  
 Temel <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfına sahip bir <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> yöntemi bu instantiantes <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfı. Sunucudan döndürülen tarayıcı <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> yöntemi iletilir <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfı oluşturucusu.  
  
 Uygulamanız gereken <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> yöntemi kendi sürümünde <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı. <xref:Microsoft.VisualStudio.Package.Colorizer> Sınıfı, tüm belirteç renk bilgilerini elde etmek için tarayıcıyı kullanır.  
  
 Tarayıcı doldurmak gereken bir <xref:Microsoft.VisualStudio.Package.TokenInfo> isteğe bağlı olarak için her bir belirteç bulur yapılandırın. Bu yapı kullanmak için renk dizini aralık belirteci kapladığı gibi bilgileri içerir belirteci ve belirteç Tetikleyicileri hangi türüdür (bkz: <xref:Microsoft.VisualStudio.Package.TokenTriggers>). Yalnızca aralık ve renk dizin renklendirme tarafından gerekli <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfı.  
  
 Renk dizini depolanan <xref:Microsoft.VisualStudio.Package.TokenInfo> yapısıdır genellikle arasında bir değer <xref:Microsoft.VisualStudio.Package.TokenColor> adlandırılmış dizinlerini anahtar sözcükleri ve işleçler gibi çeşitli dil öğelerine karşılık gelen bir dizi sağlar numaralandırması. Özel colorable öğelerinizi eşleşmeleri listelerseniz öğeleri içinde sunulan <xref:Microsoft.VisualStudio.Package.TokenColor> numaralandırma olduktan sonra yalnızca kullanabilir numaralandırması renkte için her belirteci. Ancak, ek colorable öğeler veya var olan değerleri o sırada kullanmak istemediğiniz varsa, gereksinimlerinize ve uygun dizin o listesine geri dönmek için özel colorable öğeler listenizi düzenleyebilirsiniz. Yalnızca dizine cast mutlaka bir <xref:Microsoft.VisualStudio.Package.TokenColor> içinde depolarken <xref:Microsoft.VisualStudio.Package.TokenInfo> yapısı; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] yalnızca dizini görür.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, tarayıcı üç belirteç türleri nasıl tanımlayabilir gösterir: sayı, noktalama ve tanımlayıcıları (herhangi bir sayı veya noktalama değil). Bu örnek yalnızca tanım amaçlıdır ve kapsamlı bir ayrıştırıcı ve tarayıcı uygulaması temsil etmiyor. Olduğunu varsayar bir `Lexer` ile sınıf bir `GetNextToken()` yöntemi bir dize döndürür.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    private Lexer lex;  
  
    public class TestScanner : IScanner  
    {  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false;  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                char firstChar = token[0];  
                if (Char.IsPunctuation(firstChar))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                }  
                else if (Char.IsNumber(firstChar))  
                {  
                    tokenInfo.Type = TokenType.Literal;  
                    tokenInfo.Color = TokenColor.Number;  
                }  
                else  
                {  
                    tokenInfo.Type = TokenType.Identifier;  
                    tokenInfo.Color = TokenColor.Identifier;  
                }  
            }  
            return foundToken;  
        }  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski dil hizmeti özellikleri](../../extensibility/internals/legacy-language-service-features1.md)   
 [Eski dil hizmeti Ayrıştırıcı ve tarayıcı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [Eski dil hizmeti kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)