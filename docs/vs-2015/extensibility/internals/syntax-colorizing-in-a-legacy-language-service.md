---
title: Eski dil hizmetinde söz dizimi renklendirme | Microsoft Docs
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
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20655534439fa187488087e1ae819a7ffca4c27a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730281"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Söz Dizimi Renklendirmesi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Söz dizimi renklendirme, farklı bir kaynak dosyada farklı renkler ve stil görüntülenecek bir programlama dili öğelerinin neden olan bir özelliktir. Bu özelliği desteklemek için bir ayrıştırıcı veya sözcük temelli öğeler veya belirteçleri dosya türlerini tanımlamak tarayıcı sağlamanız gerekir. Birçok dil anahtar sözcükleri, sınırlayıcılar (örneğin, ayraçlar veya küme ayraçları) ve açıklamaları farklı şekillerde renklendirme tarafından ayırt.  
  
 Eski dil Hizmetleri bir VSPackage'ı bir parçası olarak uygulanır, ancak dil hizmeti özellikleri uygulamak için daha yeni MEF uzantıları kullanmaktır. Daha fazla bilgi için bkz. [düzenleyiciyi ve dil hizmetlerini genişletme](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Yeni bir düzenleyici API hemen kullanmaya başlamak öneririz. Bu dil hizmetinizin performansını ve yeni düzenleyici özellikleri yararlanmanıza olanak tanır.  
  
## <a name="implementation"></a>Uygulama  
 Renklendirme desteklemek için yönetilen paket çerçevesini (MPF) içeren <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfını <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> arabirimi. Bu sınıf ile etkileşime giren bir <xref:Microsoft.VisualStudio.Package.IScanner> renkleri ve belirteç belirlemek için. Tarayıcılar hakkında daha fazla bilgi için bkz. [eski dil hizmeti ayrıştırıcısı ve tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). <xref:Microsoft.VisualStudio.Package.Colorizer> Sınıfı sonra her karakteri renk bilgilerini belirteciyle işaretler ve kaynak dosyasını görüntülemeden Düzenleyicisi için bu bilgileri döndürür.  
  
 Düzenleyici döndürülen renk renklendirilebilir öğeleri listesini bir dizine bilgilerdir. Bir renk değeri ve yazı tipi öznitelikleri kümesi gibi kalın renklendirilebilir her öğeyi belirtir ya da üstü çizili. Düzenleyici, dil hizmeti kullanabileceğiniz varsayılan renklendirilebilir öğeleri kümesi sağlar. Tek yapmak için ihtiyacınız olan her bir belirteç türü için uygun renk dizini belirtin. Ancak, belirteçleri için bir dizi özel renklendirilebilir öğeler ve sağladığınız dizinleri sağlar ve kendi varsayılan liste yerine renklendirilebilir öğeleri listesi başvuru. Ayrıca ayarlamanız gerekir `RequestStockColors` kayıt defteri girdisi için 0 (veya belirtmeyin `RequestStockColors` hiç giriş) özel renkler desteklemek için. Bu kayıt defteri girdisi için adlandırılmış bir parametre ile ayarlayabileceğiniz <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> kullanıcı tanımlı öznitelik. Dil hizmeti kaydetme ve onun seçeneklerini ayarlama hakkında daha fazla bilgi için bkz. [eski dil hizmetinde kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## <a name="custom-colorable-items"></a>Özel Renklendirilebilir Öğeler  
 Kendi özel renklendirilebilir öğeler sağlamak için geçersiz kılmanız gerekir <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> ve <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> metodunda <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı. İlk yöntem, dil hizmeti destekleyen özel renklendirilebilir öğeler verir ve ikinci özel renklendirilebilir öğesi dizine göre alır. Size özel renklendirilebilir öğeler varsayılan liste oluşturur. Oluşturucu, dil hizmetinin tek yapmanız gereken olan tedarik renklendirilebilir her öğe bir ada sahip. Visual Studio, kullanıcının renklendirilebilir öğeleri farklı bir dizi seçebileceği durumu otomatik olarak işler. Bu ad görünür ne olduğunu **yazı tipleri ve renkler** özellik sayfasında **seçenekleri** iletişim kutusu (Visual Studio'dan kullanılabilir **Araçları** menüsü) ve bu ad belirler bir kullanıcı geçersiz kılınmış rengi. Kullanıcının seçenekleri kayıt defteri önbellekte depolanır ve renk adı tarafından erişilebilir. **Yazı tipleri ve renkler** özellik sayfası listeler, tüm alfabetik sırayla rengi adları, her renk adı; dil adınızla koyarak, özel renkler gruplayabilirsiniz, böylece Örneğin, "**TestLanguage - açıklama**"ve"**TestLanguage - anahtar sözcüğü**". Veya, renklendirilebilir öğeleri türüne göre gruplandırabilirsiniz "**yorum (TestLanguage)**"ve"**anahtar sözcüğü (TestLanguage)**". Dil adı gruplandırarak tercih edilir.  
  
> [!CAUTION]
>  Mevcut renklendirilebilir öğesi adları ile çarpışmalardan kaçınmak için renklendirilebilir öğe adı dil adı dahil önemle tavsiye edilir.  
  
> [!NOTE]
>  Geliştirme sırasında renkleri birinin adını değiştirirseniz, Visual Studio renkleri erişildiğini ilk kez oluşturulan önbellek sıfırlamanız gerekir. Çalıştırarak bunu **Deneysel Hive sıfırlama** Visual Studio SDK program menüsünden komutu.  
  
 Listesindeki ilk öğe renklendirilebilir öğeleri hiçbir zaman başvurulan unutmayın. Visual Studio, her zaman varsayılan metin rengini ve bu öğenin öznitelikleri sağlar. İlk öğe olarak bir yer tutucu renklendirilebilir öğesi sağlamak için bu uğraşmanızı en kolay yolu olan.  
  
### <a name="high-color-colorable-items"></a>Yüksek renk renklendirilebilir öğeler  
 Renklendirilebilir öğeleri da 24-bit ya da yüksek renk değerleri aracılığıyla destek <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> arabirimi. MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> sınıfı destekler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> arabirimi ve 24 bit renk normal renkleri birlikte oluşturucu içinde belirtilir. Bkz: <xref:Microsoft.VisualStudio.Package.ColorableItem> daha fazla ayrıntı için sınıf. Aşağıdaki örnekte, 24 bit renkleri için anahtar sözcükleri ve açıklamaları gösterilmektedir. Kullanıcının masaüstünde 24 bit renk desteklendiğinde 24 bit renk kullanılır; Aksi takdirde, normal metin renkleri kullanılır.  
  
 Varsayılan dil renklerdir unutmayın; Kullanıcı, her şeyi istedikleri bu renklerini değiştirebilirsiniz.  
  
### <a name="example"></a>Örnek  
 Bu örnekte bildirme ve bir dizi kullanarak özel renklendirilebilir öğeleri doldurmak için yollarından biri gösterilmektedir <xref:Microsoft.VisualStudio.Package.ColorableItem> sınıfı. Bu örnekte, 24 bit renk kullanarak anahtar sözcüğü ve yorum renkleri ayarlar.  
  
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
                new ColorableItem("TestLanguage – Text",  
                                  "Text",  
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.Empty,  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT),  
                new ColorableItem("TestLanguage – Keyword",  
                                  "Keyword",  
                                  COLORINDEX.CI_MAROON,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.FromArgb(192,32,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_BOLD),  
                new ColorableItem("TestLanguage – Comment",  
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
 Temel <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfında bir <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> yöntemi bu instantiantes <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfı. Öğesinden döndürülen tarayıcı <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> yöntemi geçirilir <xref:Microsoft.VisualStudio.Package.Colorizer> sınıf oluşturucusu.  
  
 Uygulamanız gereken <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> yöntemi kendi sürümünde <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı. <xref:Microsoft.VisualStudio.Package.Colorizer> Sınıfı, tüm belirteç renk bilgilerini almak için tarayıcıyı kullanır.  
  
 Tarayıcı doldurmak gereken bir <xref:Microsoft.VisualStudio.Package.TokenInfo> isteğe bağlı olarak için her bir belirteç bulur yapılandırın. Kullanmak için renk dizini aralık belirteci kapladığı gibi bu yapı bilgilerini içerir. ne tür belirteç ve belirteç Tetikleyiciler olduğundan (bkz <xref:Microsoft.VisualStudio.Package.TokenTriggers>). Yalnızca aralık ve renk dizin tarafından renklendirme gereklidir <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfı.  
  
 Renk dizini depolanan <xref:Microsoft.VisualStudio.Package.TokenInfo> yapısı, genellikle bir değerden <xref:Microsoft.VisualStudio.Package.TokenColor> sabit listesi anahtar sözcükleri ve işleçler gibi çeşitli dil öğelerini karşılık gelen adlandırılmış dizinlerini sayısını sağlar. Eşleşme, özel renklendirilebilir öğeler listesi öğeleri içinde sunulan <xref:Microsoft.VisualStudio.Package.TokenColor> numaralandırma ve ardından yalnızca kullanabilir numaralandırma renkte için her bir belirteç. Ancak, ek renklendirilebilir öğeler varsa veya bu sırayla mevcut değerleri kullanmak istemediğiniz gereksinimlerinize ve uygun dizin bu listeye döndürmek için özel renklendirilebilir öğeler listenize düzenleyebilirsiniz. Yalnızca dizine cast mutlaka bir <xref:Microsoft.VisualStudio.Package.TokenColor> içinde depolarken <xref:Microsoft.VisualStudio.Package.TokenInfo> yapısı; [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] yalnızca dizini görür.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekte, tarayıcı üç belirteç türleri nasıl tanımlayabileceğiniz gösterilmektedir: sayılar ve noktalama işaretleri tanımlayıcıları (herhangi bir sayı veya noktalama değil). Bu örnek yalnızca tanım amaçlıdır ve kapsamlı bir ayrıştırıcısı ve tarayıcısı uygulaması temsil etmiyor. Olduğunu varsayar bir `Lexer` sınıfıyla birlikte bir `GetNextToken()` yönteminin bir dize döndürür.  
  
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
 [Eski dil hizmeti ayrıştırıcısı ve tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [Eski Dil Hizmeti Kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)

