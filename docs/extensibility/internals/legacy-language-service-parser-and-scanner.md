---
title: Eski dil hizmeti ayrıştırıcısı ve tarayıcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d4ca98b5e4f991e795af95e479fa57a38ca2b57a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912052"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Eski Dil Hizmeti Ayrıştırıcısı ve Tarayıcısı
Ayrıştırıcının dil hizmeti kalbidir. Yönetilen paket Framework (MPF) dil sınıflar görüntülenen kodu hakkında bilgi seçmek için bir dil ayrıştırıcı gerektirir. Bir ayrıştırıcı, metin sözcük belirteçlere ayırır ve ardından bu belirteçleri türü ve işlevleri belirler.  
  
## <a name="discussion"></a>Tartışma  
 Bir C# yöntemi verilmiştir.  
  
```csharp  
namespace MyNamespace  
{  
    class MyClass  
    {  
        public void MyFunction(int arg1)  
        {  
            int var1 = arg1;  
        }  
    }  
}  
```  
  
 Bu örnekte, noktalama işaretleri ve sözcükler belirteçleridir. Tür belirteçleri aşağıdaki gibidir.  
  
|Belirteç adı|Belirteç türü|  
|----------------|----------------|  
|ad alanı, sınıf, public void, int|Anahtar sözcüğü|  
|=|operator|  
|{ } ( ) ;|Sınırlayıcı|  
|MyNamespace MyClass, MyFunction arg1, var1|tanımlayıcı|  
|MyNamespace|ad alanı|  
|MyClass|sınıf|  
|MyFunction|yöntemi|  
|arg1|parametre|  
|var1|yerel değişken|  
  
 Ayrıştırıcının rolünü belirteçleri belirlemektir. Bazı belirteçler birden fazla tür var. Ayrıştırıcının belirteçleri belirlediği sonra dil hizmeti bilgileri söz dizimi vurgulama gibi yararlı özellikleri, ayraç eşleştirme sağlamak ve IntelliSense işlemlerini kullanabilirsiniz.  
  
## <a name="types-of-parsers"></a>Çözümleyicileri türleri  
 Dil hizmeti ayrıştırıcısı bir derleyici bir parçası olarak kullanılan bir ayrıştırıcı ile aynı değil. Ancak, bu tür bir ayrıştırıcı bir tarayıcı hem bir ayrıştırıcı derleyici ayrıştırıcı olarak aynı şekilde kullanılmalıdır.  
  
- Bir tarayıcı, belirteç türleri tanımlamak için kullanılır. Bu bilgiler, sözdizimi vurgulama ve Ayraç eşleştirme diğer işlemler, örneğin, tetikleyebilirsiniz belirteç türleri hızlı bir şekilde tanımlamak için kullanılır. Bu tarayıcı tarafından temsil edilen <xref:Microsoft.VisualStudio.Package.IScanner> arabirimi.  
  
- Bir Ayrıştırıcı işlevler ve belirteçlerin kapsamı tanımlamak için kullanılır. Bu bilgiler, yöntemleri, değişkenleri, parametreleri ve bildirimler gibi Dil öğelerini tanımlamak ve üye ve yöntem imzalarına bağlamına dayalı bir listesini sağlamak üzere IntelliSense işlemlerinde kullanılır. Bu Çözümleyici, küme ayraçları ve parantezler gibi eşleşen dil öğesi çiftlerini bulmak için de kullanılır. Bu ayrıştırıcısı, aracılığıyla erişilir <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yönteminde <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı.  
  
  Tarayıcı ve ayrıştırıcı dil hizmetiniz için nasıl uygulayacağınıza size bağlıdır. Çeşitli kaynaklar kullanılabilir Çözümleyicileri nasıl çalıştığı ve nasıl kendi ayrıştırıcı yazılacağını açıklar. Ayrıca, bazı ücretsiz ve ticari ürünleri kullanılabilir Yardım bir ayrıştırıcı oluşturma.  
  
### <a name="the-parsesource-parser"></a>ParseSource ayrıştırıcı  
 (Burada belirteçleri yürütülebilir kod bazı biçimine dönüştürülür) bir derleyici bir parçası olarak kullanılan bir ayrıştırıcı, bir dil hizmeti ayrıştırıcısı birçok farklı nedenlerle ve birçok farklı bağlamlardaki volat pouze jednou. Bu yaklaşımda nasıl uygulayacağınıza <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yönteminde <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı, size kalmıştır. Bunu göz önünde bulundurmanız önemlidir, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi bir arka plan iş parçacığında çağrıldı.  
  
> [!CAUTION]
>  <xref:Microsoft.VisualStudio.Package.ParseRequest> Yapısı bir başvuru içermektedir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nesne. Bu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nesne arka plan iş parçacığında kullanılamaz. Aslında, çoğu temel MPF sınıflarının arka plan iş parçacığında kullanılamaz. Bunlar <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> sınıfları ve doğrudan veya dolaylı olarak görünümü ile iletişim kurduğu herhangi bir sınıf.  
  
 Bu çözümleyici genellikle adlandırılır veya ne zaman ayrıştırma neden değerini tüm kaynak dosyası birinci zaman ayrıştırır <xref:Microsoft.VisualStudio.Package.ParseReason> verilir. Yapılan sonraki çağrılar <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi ayrıştırılmış kodu küçük bir bölümünü işlemek ve çok daha hızlı bir şekilde önceki tam ayrıştırma işleminin sonuçlarını kullanarak yürütülebilir. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Yöntemi ayrıştırma işleminin sonuçlarını iletişim kuran <xref:Microsoft.VisualStudio.Package.AuthoringSink> ve <xref:Microsoft.VisualStudio.Package.AuthoringScope> nesneleri. <xref:Microsoft.VisualStudio.Package.AuthoringSink> Nesnesi bilgilerini belirli ayrıştırma için bir neden, küme ayraçları veya parametre listeleri olan yöntem imzaları eşleşen örneğin yayılma hakkında bilgi toplamak için kullanılır. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Bildirimleri ve yöntem imzaları ve ayrıca destek koleksiyonları gitmek için Gelişmiş Düzenleme seçeneği sağlar (**Tanıma Git**, **bildirimine gidin**, **gidin Başvuru**).  
  
### <a name="the-iscanner-scanner"></a>IScanner tarayıcı  
 Ayrıca uygulayan bir tarayıcı uygulamalıdır <xref:Microsoft.VisualStudio.Package.IScanner>. Ancak, bu tarayıcı satır satır temelinde çalıştığından <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfı, bunu uygulamak genellikle daha kolay. Her satırın başında MPF verir <xref:Microsoft.VisualStudio.Package.Colorizer> tarayıcıya geçirilen bir durum değişkeninin olarak kullanılacak bir değer sınıfı. Her satırın sonunda, tarayıcı güncelleştirilen durumu değişkeni döndürür. Tarayıcı kaynak dosyasının başından itibaren başlatmak zorunda kalmadan herhangi bir satır ayrıştırma başlayabilmesi MPF her satır için bu durum bilgilerini önbelleğe alır. Bu hızlı tek bir satırı taraması kullanıcıya hızlı geri bildirim sağlamak için Düzenleyicisi sağlar.  
  
## <a name="parsing-for-matching-braces"></a>Ayraç eşleştirme için ayrıştırma  
 Bu örnek, kullanıcının girdiği bir kapanış ayracı eşleşen denetim akışını gösterir. Bu işlemde renklendirme için kullanılan tarayıcı belirtecini ve Ayraç eşleştirme işlemi belirteci olup olmadığını tetikleyebilirsiniz türünü belirlemek için de kullanılır. Tetikleyici bulunursa <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi eşleşen Ayraca bulmak için çağrılır. Son olarak, iki küme ayraçları vurgulanır.  
  
 Küme ayraçları Tetikleyicileri adlarında kullanılır ve nedenleri ayrıştırma olsa bile, bu işlem için gerçek bir küme ayraçları sınırlı değil. Eşleşen bir çift olarak belirtilen herhangi bir çifti karakterleri desteklenir. Örnekler (ve) \< ve >, ve [ve].  
  
 Dil hizmeti eşleşen küme ayraçlarını desteklediği varsayılır.  
  
1.  Kullanıcı, bir kapatma küme ayracından (}) yazar.  
  
2.  İmleç bir Gelişmiş ve küme ayracı kaynak dosyadaki imlecin eklenir.  
  
3.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Yönteminde <xref:Microsoft.VisualStudio.Package.Source> sınıfı ile yazılan kapanış ayracı çağrılır.  
  
4.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Yöntem çağrılarını <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> yönteminde <xref:Microsoft.VisualStudio.Package.Source> geçerli imleç konumu hemen önce bir konumda belirteci almak için sınıf. Bu belirteç için belirlenmiş bir kapanış ayracı karşılık gelir).  
  
    1.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Yöntem çağrılarını <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metodunda <xref:Microsoft.VisualStudio.Package.Colorizer> geçerli satırdaki tüm belirteçleri elde etmek için nesne.  
  
    2.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Yöntem çağrılarını <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> metodunda <xref:Microsoft.VisualStudio.Package.IScanner> nesneyi geçerli satırın metinle.  
  
    3.  <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Yöntemini tekrar tekrar çağırır <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metodunda <xref:Microsoft.VisualStudio.Package.IScanner> geçerli satırından tüm belirteçlerin toplamak için nesne.  
  
    4.  <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Yöntemi çağrıları özel bir yöntem <xref:Microsoft.VisualStudio.Package.Source> istenilen içeren belirteci almak için sınıf ve belirteçler listesinde geçişlerinde öğesinden alınan <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> yöntemi.  
  
5.  <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Yöntemi için bir belirteç tetikleyici bayrak görünür <xref:Microsoft.VisualStudio.Package.TokenTriggers> öğesinden döndürülen belirtecine <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> yöntemi; diğer bir deyişle, kapatma küme ayracından temsil eden bir belirteci).  
  
6.  Tetikleyici, bayrak varsa <xref:Microsoft.VisualStudio.Package.TokenTriggers> bulunursa <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> yönteminde <xref:Microsoft.VisualStudio.Package.Source> sınıfı çağrılır.  
  
7.  <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> Yöntemi ayrıştırma neden değeri ile bir ayrıştırma işlemi başlatır <xref:Microsoft.VisualStudio.Package.ParseReason>. Bu işlem sonunda çağırır <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodunda <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı. Zaman uyumsuz ayrıştırma etkinse, bu çağrı <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi bir arka plan iş parçacığında oluşur.  
  
8.  Ayrıştırma işlemi tamamlandığında, adlı bir iç tamamlama işleyicisi (geri çağırma yöntemi olarak da bilinir) `HandleMatchBracesResponse` çağrılma yeri <xref:Microsoft.VisualStudio.Package.Source> sınıfı. Bu çağrı tarafından otomatik olarak yapılır <xref:Microsoft.VisualStudio.Package.LanguageService> temel sınıf ayrıştırıcı tarafından değil.  
  
9. `HandleMatchBracesResponse` Yöntemi yayılma listesini alır <xref:Microsoft.VisualStudio.Package.AuthoringSink> depolanan nesne <xref:Microsoft.VisualStudio.Package.ParseRequest> nesne. (Bir aralığı bir <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> kaynak dosyada bir dizi satır ve karakter belirten yapısı.) Yayılma oluşan bu liste, genellikle her biri açılış ve kapanış küme ayraçları için iki yayılma içerir.  
  
10. `HandleBracesResponse` Yöntem çağrılarını <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> metodunda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> depolanan nesne <xref:Microsoft.VisualStudio.Package.ParseRequest> nesne. Bu, verilen yayılma vurgular.  
  
11. Varsa <xref:Microsoft.VisualStudio.Package.LanguagePreferences> özelliği <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> etkinleştirildiğinde `HandleBracesResponse` yöntemi tarafından eşleşen aralık çevrelenmiş ve durum çubuğunda bu aralığı ilk 80 karakterlerini görüntüleyen metni alır. Bu, en iyi şekilde çalışır <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntem, eşleşen bir çift eşlik eden dil öğesi içerir. Daha fazla bilgi için <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> özelliği.  
  
12. Bitti.  
  
### <a name="summary"></a>Özet  
 Eşleşen küme ayraçlarını işlemi, genellikle basit dil öğe çiftlerine sınırlıdır. Üçlü eşleştirme gibi daha karmaşık öğeleri ("`if(...)`","`{`"ve"`}`", veya "`else`","`{`"ve"`}`"), bir sözcük tamamlama işleminin bir parçası vurgulanabilir. Örneğin, "else" sözcüğü tamamlandığında eşleşen "`if`" deyimi vurgulanır. Bir dizi varsa `if` / `else if` deyimleri, bunların tümünün vurgulanmış Ayraç eşleştirme olarak aynı mekanizmayı kullanarak. <xref:Microsoft.VisualStudio.Package.Source> Temel sınıf zaten destekler, şu şekilde: tarayıcı belirteci tetikleyici değer döndürmelidir <xref:Microsoft.VisualStudio.Package.TokenTriggers> tetikleyici değeri ile birlikte <xref:Microsoft.VisualStudio.Package.TokenTriggers> önce imleç konumu belirteci.  
  
 Daha fazla bilgi için [eski dil hizmetinde Ayraç eşleştirme](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-colorization"></a>Ayrıştırma için renklendirme  
 Kaynak kod renklendirme basittir, yalnızca renk belirteç ve dönüş türü hakkında bilgileri türünü tanımlayın. <xref:Microsoft.VisualStudio.Package.Colorizer> Sınıfı renk her belirteç bilgilerini sağlamak için düzenleyici ve tarayıcı arasında aracı görevi görür. <xref:Microsoft.VisualStudio.Package.Colorizer> Sınıfının kullandığı <xref:Microsoft.VisualStudio.Package.IScanner> bir satır renklendirme Yardım ve kaynak dosyasındaki tüm satırlar için durum bilgilerini toplamak için bir nesne. MPF dil hizmeti sınıflardaki <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfı tarayıcıyla kurduğundan geçersiz kılınacak sahip değil yalnızca aracılığıyla <xref:Microsoft.VisualStudio.Package.IScanner> arabirimi. Uygulayan nesne sağladığınız <xref:Microsoft.VisualStudio.Package.IScanner> kılarak arabirimi <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodunda <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı.  
  
 <xref:Microsoft.VisualStudio.Package.IScanner> Tarayıcı kaynak kod satırı verilen <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> yöntemi. Çağrılar <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> yöntemi satır belirteçlerin ulaşana kadar satırda sonraki belirteç edinme yineleniyor. Renklendirme için MPF tüm kaynak kodu bir dizi satır değerlendirir. Bu nedenle, tarayıcı satırlar halinde ulaştığı kaynağıyla başa mümkün olması gerekir. Ayrıca, herhangi bir zamanda herhangi bir satır tarayıcıya geçirilebilir ve tarayıcı yaklaşık taranacak satırından önce satırından durumu değişkeni alan yalnızca bir garanti sağlar.  
  
 <xref:Microsoft.VisualStudio.Package.Colorizer> Sınıfı belirteci Tetikleyicileri tanımlamak için de kullanılır. Bu tetikleyiciler, belirli bir belirteç Sözcük tamamlama gibi daha karmaşık bir işlemi başlatabilirsiniz MPF bildirin veya eşleşen küme ayraçları. Böyle Tetikleyicileri tanımlayan hızlı olması ve herhangi bir konumda olmalıdır çünkü tarayıcı bu görev için idealdir.  
  
 Daha fazla bilgi için [eski dil hizmetinde söz dizimi renklendirme](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-functionality-and-scope"></a>İşlevsellik ve kapsam için ayrıştırma  
 İşlevsellik ve kapsam için ayrıştırma yalnızca karşılaşılan belirteçleri türlerini tanımlayan değerinden daha fazla çaba gerektirir. Ayrıştırıcının yalnızca Belirtecin türü, aynı zamanda belirteci kullanıldığı işlevselliği tanımlamak vardır. Örneğin, yalnızca bir adı bir tanımlayıcıdır, ancak sizin dilinizde tanımlayıcı bir sınıf, ad alanı, yöntemi veya bağlama bağlı olarak bir değişken adı olabilir. Belirtecin genel bir tür tanımlayıcı olabilir, ancak tanımlayıcısı de bağlı olarak ne olduğunu ve tanımlandığı gibi diğer anlamlara sahip. Ayrıştırıcının Ayrıştırılmakta olan dili hakkında daha kapsamlı bilgi için bu kimliği gerektirir. Burada <xref:Microsoft.VisualStudio.Package.AuthoringSink> sınıfı halinde sunulur. <xref:Microsoft.VisualStudio.Package.AuthoringSink> Sınıf tanımlayıcıları, yöntemler, eşleşen dil çiftleri (örneğin, küme ayraçları ve parantezler) ve dil Üçlü hakkında bilgi toplar (dil çiftleri için benzer ancak bu üç bölümü, örneğin, "`foreach()`" "`{`"ve"`}`"). Ayrıca, geçersiz kılabilirsiniz <xref:Microsoft.VisualStudio.Package.AuthoringSink> erken kesme noktalarını doğrulamada kullanılan ve böylece hata ayıklayıcı, yüklü olması gerekmez. kod kimliği desteklemek için sınıf ve **Otolar** gösteren yerel hata ayıklama penceresi değişkenleri ve parametreleri otomatik olarak ne zaman bir programı hata ayıklama yapılıyor ve uygun yerel değişkenleri ve parametreleri ek olarak, hata ayıklayıcı sunan tanımlamak için ayrıştırıcı gerektirir.  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink> Nesne için ayrıştırıcı bir parçası olarak geçirilir <xref:Microsoft.VisualStudio.Package.ParseRequest> nesne ve yeni bir <xref:Microsoft.VisualStudio.Package.AuthoringSink> nesnesi, her zaman oluşturulan bir yeni <xref:Microsoft.VisualStudio.Package.ParseRequest> nesnesi oluşturulur. Ayrıca, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yöntemi döndürmelidir bir <xref:Microsoft.VisualStudio.Package.AuthoringScope> çeşitli IntelliSense işlemlerini işlemek için kullanılan nesne. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Nesne tutar bildirimleri için bir listesi ve bir liste yöntemleri için ya da hangi, ayrıştırma nedeni bağlı olarak doldurulur. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Sınıfı uygulanmış.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski dil hizmetinde uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Eski dil hizmetine genel bakış](../../extensibility/internals/legacy-language-service-overview.md)   
 [Eski dil hizmetinde söz dizimi renklendirme](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [Eski Dil Hizmetinde Ayraç Eşleştirme](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)