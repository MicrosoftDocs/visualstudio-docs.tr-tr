---
title: Uygulamanızı modeller aracılığıyla oluşturma ve yapılandırma
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 78dc0907fa717f61b6cf883994a3ac2fd6072ba1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872804"
---
# <a name="generate-and-configure-your-app-from-models"></a>Uygulamanızı modeller aracılığıyla oluşturma ve yapılandırma
Oluşturma veya modelden uygulamanızın parçalarını yapılandırın.

 Modeli, kodun daha doğrudan gereksinimleri temsil eder. Modelden doğrudan uygulamanın davranışını türetme tarafından değiştirilen gereksinimlerine çok daha hızlı ve göre daha güvenilir bir şekilde güncelleştirme yanıtlayabilir kodu. Bazı ilk iş türetmeyi'kurmak için gerekli olmasa da, ayırdığı bu gereksinimleri değişiklikleri bekliyorsanız ya da birkaç ürün çeşidini yapmayı planlıyorsanız döndürülür.

## <a name="generating-the-code-of-your-application-from-a-model"></a>Bir modelde uygulamanızın kod oluşturma
 Kod oluşturmanın en kolay yolu, metin şablonları kullanmaktır. Kod modeli tuttuğunuz aynı Visual Studio çözümü içinde oluşturabilirsiniz. Daha fazla bilgi için bkz.:

- [T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

- [Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)

  Bu yöntem, artımlı olarak uygulamak kolay bir işlemdir. Yalnızca özel durumunuz için çalışan bir uygulama ile başlayın ve birkaç parçalarını modelden değiştirmek için istediğiniz zaman seçin. Kaynak dosyaları bu parçaların haline gelmeden metin şablonu (.tt) dosyalarını yeniden adlandırın. Bu noktada, önceden yaptığınız gibi uygulamanın çalışması için kaynak .cs dosyaları otomatik olarak şablon dosyalarından oluşturulur.

  Daha sonra kodun bir parçası olması ve model okur ve kaynak dosyasının bu bölümü oluşturan bir metin şablonu ifadesi ile değiştirin. Modelin en az bir değer uygulamayı tekrar çalıştırabilirsiniz ve önceki gibi çalışır, özgün kaynak oluşturmanız gerekir. Farklı bir model değerleri test ettikten sonra siz başka bir kod parçası şablon ifadeleri eklemek geçebilirsiniz.

  Bu artımlı bir yöntem, kod oluşturma genellikle düşük riskli bir yaklaşım olduğunu gösterir. Elde edilen uygulamalar genellikle el ile yazılmış bir sürümünün yanı sıra hemen gerçekleştirin.

  Ancak, varolan bir uygulama ile başlatırsanız, çok sayıda yeniden düzenleme modeli tarafından yönetilir ve böylece bağımsız olarak değiştirilebilir farklı davranışları ayırmak için gerekli olduğunu fark edebilirsiniz. Projenizin maliyet tahmini yaparken uygulamanın bu en boy değerlendirmek öneririz.

## <a name="configuring-your-application-from-a-model"></a>Model aracılığıyla uygulamanızı yapılandırma
 Çalışma zamanında uygulamanızın davranışını değiştirmek istiyorsanız, uygulama derlenmeden önce kaynak kodunu üretir ve kod oluşturma kullanamazsınız. Bunun yerine, modeli okumak ve buna göre davranışını değiştirmek için uygulamanızı tasarlayabilirsiniz. Daha fazla bilgi için bkz.:

- [Nasıl yapılır: Program Kodunda Dosyadan Model Açma](../modeling/how-to-open-a-model-from-file-in-program-code.md)

  Bu yöntem aynı zamanda artımlı olarak uygulanabilir, ancak daha fazla iş başında yoktur. Modeli okumak ve değişken parçaları için erişilebilir olmasını değerleri olanak tanıyan bir altyapı ayarlamak kod yazmanız gerekir. Değişken parçaları genel yapma, kod oluşturmaktan daha pahalıdır.

  Genel bir uygulama genellikle kendi belirli ortaklarınıza daha az iyi gerçekleştirir. Proje planınızı, performans önemliyse, bu risk değerlendirmesini içermesi gerekir.

## <a name="developing-a-derived-application"></a>Türetilen bir uygulama geliştirme
 Aşağıdaki genel yönergeleri yararlı bulabilirsiniz.

-   **Belirli başlayın, daha sonra genelleştirin.** İlk uygulamanızı belirli bir sürümünü yazın. Bu sürüm, koşulları bir dizi çalışması gerekir. Memnun kaldığınızda BT'nin düzgün çalıştığından, bir modelinden türetilen bazıları da yapabilirsiniz. Türetilmiş bölümlerini kademeli olarak genişletin.

     Örneğin, bir modelde tanımlanan sayfaları sunan web uygulaması tasarlamadan önce web sayfaları belirli bir dizi olan bir Web sitesi tasarlayın.

-   **Değişken görünüşlerini modelleyin.** Ya da bir dağıtım ve başka arasında farklılık veya gereksinimleri zamanla değiştirme yönleri tanımlar. Bir modelden türetilmesi gereken yönleri şunlardır.

     Örneğin, web sayfaları ve arası bağlantılar, bunları değiştirir ancak stil ve biçim sayfaların her zaman aynı olduğu model bağlantıları açıklamalıdır ancak sayfaları biçimini açıklamak zorunda değildir.

-   **Sorunları ayırın.** Değişken yönleri bağımsız alanlarına ayrılabilir, ayrı modelleri her alan için kullanın. ModelBus kullanarak modelleri hem aralarında kısıtlamaları etkileyen işlemleri tanımlayabilirsiniz.

     Örneğin, web sayfalarını ve sayfa düzeni tanımlamak için farklı bir model arasında gezinmeyi tanımlamak için bir model kullanın.

-   **Gereksinim, çözüm modeli.** Model kullanıcı gereksinimleri açıklanır şekilde tasarlayın. Bunun aksine, değişken yönleri göre gösterimini uygulamasının tasarlamayın.

     Örneğin, web gezinti modeli, web sayfaları ve bunlar arasında köprü temsil etmelidir. Web gezinti modeli HTML veya uygulamanızdaki sınıfları parçalarını temsil etmiyor.

-   **Oluşturma veya yorumlama?** Belirli bir dağıtım için gereksinimleri nadiren değişiklik, program kodu modeli oluşturur. Gereksinimleri, sık sık değişebilir veya aynı dağıtımda birden fazla değişken içinde birlikte var, böylece okumak ve yorumlamak bir model uygulaması yazma.

     Bir dizi farklı ve ayrı olarak yüklenmiş bir Web sitesi geliştirmek için Web sitesi model kullanıyorsanız, örneğin, daha sonra site kodunu modelden oluşturmanız gerekir. Ancak, yazma modeli okuyan ve buna göre site sunan bir web sunucusu daha iyi ise her gün bir site denetlemek için modelinizi kullanın.

-   **UML veya DSL?** UML genişletmek için stereotipleri kullanarak, modelleme gösterimi oluşturmayı düşünün. Amaca uygun hiçbir UML diyagram ise bir DSL tanımlayın. Ancak, UML Standart semantiği bozmayı önlemek.

     Örneğin, bir UML sınıf diyagramı kutuları ve oklar oluşan bir koleksiyondur; Bu gösterim teorik olarak herhangi bir şey tanımlayabilirsiniz. Ancak burada aslında bir dizi türleri tanımlamakta olduğunuz dışında sınıf diyagramı kullanmanızı önermiyoruz. Örneğin, web sayfalarının farklı türlerini tanımlamak için sınıf diyagramları uyarlayabilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.

- [Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)
- [Nasıl yapılır: Program Kodunda Dosyadan Model Açma](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)