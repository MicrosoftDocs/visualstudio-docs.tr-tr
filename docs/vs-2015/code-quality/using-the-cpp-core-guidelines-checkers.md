---
title: C++ temel yönergeleri denetleyicilerini kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1153f7a32c26946fafb1230699c4afcae976cd9e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799567"
---
# <a name="using-the-c-core-guidelines-checkers"></a>C++ temel yönergeleri denetleyicilerini kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C++ temel yönergeleri yönergeleri, kuralları ve C++ uzmanlar ve tasarımcılar tarafından oluşturulan c++ kodlama hakkında en iyi taşınabilir bir kümesidir.  Visual Studio artık ek kuralları için kod çözümleme araçları, C++ temel yönergeleri ile uyumluluk için kodunuzu denetlemek ve geliştirmeleri önermek için oluşturduğunuz eklenti paketlerinin destekler.  
  
## <a name="the-c-core-guidelines-project"></a>C++ temel yönergeleri proje  
 Bjarne Stroustrup ve başkaları tarafından oluşturulan, C++ temel yönergeleri güvenle ve etkili bir şekilde modern C++'ı kullanarak bir kılavuz olan. Statik tür güvenliği ve kaynak güvenliği yönergeleri vurgulayın. Bunlar, kaldırın veya dil en hataya bölümlerini en aza indirmek için yollarını tanımlar ve kodunuzu daha basit hale getirme ve daha fazla yüksek performanslı, güvenilir bir biçimde önerin. Bu yönergeleri, standart C++ Foundation tarafından korunur. Daha fazla bilgi edinmek için belgelere bakın [C++ temel yönergeleri](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)ve C++ temel yönergeleri belge proje dosyaları üzerinde erişim [GitHub](https://github.com/isocpp/CppCoreGuidelines).  
  
 Microsoft, bir Nuget paketi kullanarak projelerinize ekleyebilirsiniz Kod Analizi kural kümesi, C++ temel denetimi sağlayarak, C++ temel yönergeleri çaba destekler. Paket Microsoft.CppCoreCheck olarak adlandırılır ve adresten edinilebilir [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Bu paket, yüklü en az Visual Studio 2015 güncelleştirme 1 ile olması gerekir.  
  
 Paket, başka bir paket bağımlılık olarak, bir yalnızca üstbilgi yönerge desteği kitaplığı (GSL) de yükler. GSL GitHub üzerinde de kullanılabilir [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>C++ temel denetimi yönergeleri kod analizini etkinleştir  
 C++ temel denetimi kod çözümleme araçları etkinleştirmek için Visual Studio içinden kontrol etmek istediğiniz her C++ projesi içine Microsoft.CppCoreCheck NuGet paketini yükleyin.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Microsoft.CppCoreCheck paketi projenize eklemek için  
  
1. İçinde **Çözüm Gezgini**, pakete eklemek istediğiniz çözümü projenizin bağlam menüsünü açmak için sağ tıklayın. Seçin **NuGet paketlerini Yönet** açmak için **NuGet Paket Yöneticisi**.  
  
2. İçinde **NuGet Paket Yöneticisi** penceresinde, Microsoft.CppCoreCheck arayın.  
  
    ![Nuget Paket Yöneticisi penceresi gösterir CppCoreCheck paket](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Microsoft.CppCoreCheck paketi seçin ve ardından **yükleme** düğmesini kuralları projenize ekleyin.  
  
   NuGet paketini projenize projeniz üzerinde kod analizini etkinleştirdiğinizde, çağrılan bir ek MSBuild .targets dosyasını ekler. Bu .targets dosyasında, Visual Studio kod analizi aracı için ek uzantı olarak C++ temel denetimi kuralları ekler.  
  
   Seçerek projeniz üzerinde kod analizi etkinleştirebilirsiniz **derlemede kod analizini etkinleştir** onay kutusu **Kod Analizi** bölümünü **özellik sayfaları** için iletişim kutusu projenizi.  
  
   ![Kod Analizi genel ayarları için özellik sayfası](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   C++ temel denetimi kuralları, Kod Analizi etkinleştirildiğinde çalıştırılan varsayılan kural kümesi bir parçası haline gelir. C++ temel denetimi kuralları geliştirilmekte olduğundan, bazı kurallar tüm kod üzerinde kullanılmaya hazır olmayabilir ancak geliştirme sırasında bilgilendirici olabilir. Bu kurallar, Deneysel olarak kullanıma sunulur. Projeniz için özellikleri yayınlanan veya Deneysel kuralı çalıştırılıp çalıştırılmayacağını seçebilirsiniz.  
  
   ![Kod Analizi uzantıları ayarları için özellik sayfası](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   Etkinleştirmek veya devre dışı C++ temel denetimi kural kümesi için açık **özellik sayfaları** projeniz için iletişim. Altında **yapılandırma özellikleri**, genişletme **Kod Analizi**, **uzantıları**. Denetim yanındaki açılır menüde **etkinleştirme C++ temel denetimi (serbest bırakıldı)** veya **etkinleştirme C++ temel denetimi (Deneysel)**, seçin **Evet** veya **Hayır**. Seçin **Tamam** veya **Uygula** yaptığınız değişiklikleri kaydedin.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Türleri, sınırları ve yaşam süresi yok  
 C++ temel denetimi şu anda denetleyicileri için pakette [tür güvenliği](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), [sınırların güvenliği](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds), ve [ömrü güvenliği](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) profilleri.  
  
 C++ temel denetimi kuralları bulabilirsiniz sorunları türüne bir örnek aşağıda verilmiştir:  
  
```cpp  
// CoreCheckExample.cpp  
// Add CppCoreCheck package and enable code analysis in build for warnings.  
  
int main()  
{  
    int arr[10];           // warning C26494  
    int* p = arr;          // warning C26485  
  
    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1  
    {  
        int* q = p + 1;    // warning C26481 (suppressed)  
        p = q++;           // warning C26481 (suppressed)  
    }  
  
    return 0;  
}  
```  
  
 Bu örnek, C++ temel denetimi kuralları bulabilirsiniz uyarıları birkaçını göstermektedir:  
  
- C26494 olan kural Type.5: bir nesneyi her zaman başlatın.  
  
- C26485 olan kural Bounds.3: hiçbir dizi işaretçiye azalma gerçekleştirmeyin.  
  
- C26481 olan kural Bounds.1: işaretçi aritmetiği kullanmayın. Bunun yerine `span` kullanın.  
  
  C++ temel denetimi Kod Analizi rulesets yüklediyseniz ve bu kodu derlerken etkin ilk iki uyarıları çıktısı alınır, ancak üçüncü bastırılır. Örnek kod derleme çıktısı şöyledir:  
  
  **1 >---derleme başladı: Proje: CoreCheckExample, yapılandırma: hata ayıklama Win32--**  
**----**  
**1 > CoreCheckExample.cpp**  
**1 > CoreCheckExample.vcxproj C:\Users\username\documents\visual studio 2015\P ->**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1 > CoreCheckExample.vcxproj C:\Users\username\documents\visual studio 2015\P ->**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (tam PDB)**  
**c:\users\username\documents\visual studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(6): C26494 Uyarı: 'arr' değişkendir uninitializ**  
**Ed. her zaman bir nesneyi başlatır. (type.5: http://go.microsoft.com/fwlink/p/?Link**  
**KİMLİĞİ 620421 =)**  
**c:\users\username\documents\visual studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(7): C26485 Uyarı: 'arr' ifadesi: diziden**  
 **işaretçiye bozunma gerçekleştirmeyin. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)**  
**=== Yapı: 1 başarılı, 0, 0 güncel, başarısız oldu 0 atladı ===** C++ temel yönergeleri bulunduğundan daha iyi ve daha güvenli kod yazmanıza yardımcı olacak. Ancak, bir kuralı ya da profili burada uygulanan olmamalıdır örneği varsa, doğrudan kodunda gizlemek kolaydır. Kullanabileceğiniz `gsl::suppress` C++ temel denetimi algılama ve bir kural aşağıdaki kod bloğu, herhangi bir ihlali raporlama tutmak için özniteliği. Belirli kurallar bastırmak için ayrı deyimler işaretleyebilirsiniz. Yazarak bile tüm sınırların profil gizleyebilirsiniz `[[gsl::suppress(bounds)]]` bir özel kural numarası dahil olmak üzere olmadan.  
  
## <a name="use-the-guideline-support-library"></a>Kılavuzu destek kitaplığını kullanma  
 Microsoft.CppCoreCheck NuGet paketini de Microsoft'un uygulamasına yönerge desteği kitaplığı (GSL) içeren bir paketi yükler. GSL tek başına form içinde de kullanılabilir [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). Bu kitaplık, temel yönergeleri takip etmek istiyorsanız yararlıdır. GSL hataya yapıları ile daha güvenli alternatifler değiştirmenizi sağlayan tanımlarını içerir. Örneğin, değiştirebileceğiniz bir `T*, length` parametrelerle çiftinin `span<T>` türü. GSL olan açık kaynaklı, göz atın istiyorsanız, kitaplık kaynaklarını açıklama satırı yapın veya katkıda bulunan, bu nedenle proje adresinde bulunabilir [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).



