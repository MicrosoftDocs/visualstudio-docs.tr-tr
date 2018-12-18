---
title: Kullanıcı gereksinimlerini modelleme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- requirements
- stories
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4791566d3c37517c3c93e62e371bf4cbc9fc6604
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966563"
---
# <a name="model-user-requirements"></a>Kullanıcı gereksinimlerini modelleme

Etkinlikler ve bölümü hakkında diyagramlar çizerek kullanıcılarınızın ihtiyaçlarını anlamanıza, tartışın ve visual Studio yardımcı sisteminizi hedeflerine elde etmelerine yardımcı oynadığı. Her biri farklı bir açısını Kullanıcıların ihtiyaçlarını üzerinde odaklanır. Bu diyagramları kümesi gereksinimleri modelidir. Video gösterimi için bkz: [iş etki alanı modelleme](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain).

Visual Studio'nun hangi sürümlerinin her model türünü desteklemek için bkz [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Gereksinimler modeli, yardımcı olur:

- İç tasarımından ayrı olarak sistemin dış özelliklerine odaklanır.

- Kullanıcıların ve hissedarların ile doğal dilde daha az belirsizlik gerekiyor.

- Tutarlı bir kullanıcı, geliştiriciler ve testçiler tarafından kullanılan terimler sözlüğü tanımlayın.

- Boşluk ve tutarsızlıkları azaltın.

- Gereksinim değişikliklerine yanıt vermek için gereken iş miktarını azaltmaya.

- Özellikleri geliştirileceğini sırasını planlayın.

- Modelleri, testler ve gereksinimler arasında NET bir ilişki yapma, sistem testleri için temel olarak kullanın. Gereksinimleri değiştiğinde, bu ilişki, testler doğru bir şekilde güncelleştirmenize yardımcı olur. Bu, sistemin yeni gereksinimlerini karşıladığından emin olur.

Kullanıcıları veya temsilciler ile tartışmalara odaklanmak için kullanın ve bunu her yineleme başlangıcında yeniden ziyaret gereksinimler modelini en büyük avantajı sağlar. Ayrıntılı olarak kod yazmadan önce tamamlamanız gerekmez. Kısmen çalışan bir uygulama, çok Basitleştirilmiş bile genellikle kullanıcıların gereksinimleriyle irdelemesi en cazip temelini oluşturur. Model, bu tartışmaların sonuçları özetlemek için etkili bir yoludur. Daha fazla bilgi için [geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md).

> [!NOTE]
> Bu konular boyunca sistem ya da geliştirmekte olduğunuz uygulamanın "Sistem" anlamına gelir. Birçok yazılım ve donanım bileşenleri büyük koleksiyonu olabilir; ya da tek bir uygulama; veya daha büyük bir sistemde içinde bir yazılım bileşeni. Her durumda, bir kullanıcı arabirimi ya da API aracılığıyla sistemin dışından görülemediğinden, davranışı gereksinimler modelini açıklar.

## <a name="common-tasks"></a>Ortak görevler

Kullanıcı gereksinimlerini birkaç farklı görünümler oluşturabilirsiniz.  Her görünüm, belirli türde bilgi sağlar.  Bu görünümler oluşturduğunuzda, sık birinden diğerine taşımak idealdir. Herhangi bir görüntüden yeniden başlatabilirsiniz.

|Diyagram veya belge|Bu gereksinimler modelinde açıklar|Bölüm|
|-|-|-|
|Kavramsal bir sınıf diyagramı|Gereksinimlerini tanımlamak için kullanılan türler sözlüğü; görünen türler sistemin arabirimi.||
|Ek belgelerin veya iş öğeleri|Performans, güvenlik, kullanılabilirlik ve güvenilirlik ölçütleri.|[Hizmet gereksinimlerinin kalitesini açıklayan](#QoSRequirements)|
|Ek belgelerin veya iş öğeleri|Kullanım kısıtlamaları ve belirli bir özel olmayan kuralları|[İş kurallarını gösterme](#BusinessRules)|

Diyagram türlerin çoğu başka bir amaçla kullanılabilir dikkat edin. Diyagram türleri genel bakış için bkz. [uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md).

##  <a name="BusinessRules"></a> İş kurallarını gösterme

Bir iş kuralı, belirli kullanım örneği ile ilişkili değil ve sistem genelinde gözlenmelidir bir gereksinimdir.

Birçok iş kuralları kavramsal sınıflar arasındaki ilişkileri kısıtlamalar şunlardır. Bu yazma *statik iş kuralları* kavramsal sınıf diyagramında ilgili sınıflar ile ilgili açıklamalar olarak. Örneğin:

![Açıklama kuralında sırasını sınıfa iliştirilen.](../modeling/media/uml_reqmcd2.png)

*Dinamik iş kuralları* kısıtlamak izin verilen olaylar dizisi. Örneğin, bir kullanıcı, sisteminizdeki diğer işlemleri gerçekleştirmeden önce oturum açması gerektiğini göstermek için bir sıralı veya etkinlik diyagramı kullanın.

Ancak, çok sayıda dinamik kurallar daha etkili bir şekilde ve genel statik kuralları ile değiştirerek belirtilebilir. Örneğin, bir sınıfa sınıf kavramsal modeldeki 'Farklı oturum' bir Boolean özniteliği ekleyebilirsiniz. Günlük kullanım örneğindeki Sonkoşul olarak oturum ekleyin ve diğer kullanım örnekleri çoğunu önkoşulu olarak ekleyin. Bu yaklaşım, tüm olası eşleştirme birleşimlerini olaylar dizisini tanımlamamaya özen gösterin sağlar. Yeni kullanım durumlarını modele eklemek, ihtiyacınız olduğunda, ayrıca daha esnektir.

Seçimi buraya gereksinimleri nasıl tanımlayacağınız hakkında olduğunu ve bunun nasıl gereksinimleri program kodu içinde uygulamanız bağımsız olduğuna dikkat edin.

Aşağıdaki konular, daha fazla bilgi sağlar:

|Hakkında bilgi edinmek için|Oku|
|-|-|
|İş kurallarının aynılarını kod geliştirme|[Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)|

##  <a name="QoSRequirements"></a> Hizmet gereksinimlerinin kalitesini açıklayan

Hizmet gereksinimi kalitesi birkaç işlem kategorisi vardır. Bunlar aşağıdakileri içerir:

-   Performans

-   Güvenlik

-   Kullanılabilirlik

-   Güvenilirlik

-   Sağlamlık

Bu gereksinimlerin bazıları belirli kullanım durumları açıklamasında içerebilir. Diğer gereksinimler kullanım örneklerine özgü olmayan ve ayrı bir belgede en etkili bir şekilde yazılır. Mümkün olduğunda, gereksinimler modeli tarafından tanımlanan sözlük izliyor kullanışlıdır. Aşağıdaki örnekte, özel olarak gereksinimini kullanılan ana sözcüklerin aktörleri kullanım örnekleri ve önceki çizimlerde sınıfları başlıklarını olduğuna dikkat edin:

Bir müşteri, Yemek Sipariş sırada bir restoran, bir menü öğesini siler. Bu menü öğesine başvuran bir sipariş öğesi kırmızı renkte görüntülenir.

Bkz: [uygulama Mimarinizi modelleme](../modeling/model-your-app-s-architecture.md) Hizmet gereksinimlerinin kalitesini için uyar kod geliştirme hakkında bilgi edinmek için.

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)
- [Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)
