---
title: İşlev Ayrıntıları görünümünde | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.functiondetails
helpviewer_keywords:
- Function Details view
- Profiling Tools, Function Details view
ms.assetid: 8806954f-cf28-48d5-81b2-d722ceaf7d27
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7bfc700f0757d99686e28942ff796cf117b1456f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951229"
---
# <a name="function-details-view"></a>İşlev Ayrıntıları Görünümü
**İşlev Ayrıntıları görünümü** penceresinde aşağıdaki bilgileri görüntüler:  
  
- **Maliyet dağılımı** çubuk grafik, seçtiğiniz bir işlev ve seçili işlev çağıran işlevler arasında ve seçili işlev tarafından çağrılan işlevler arasındaki ilişkileri temsil eder .  
  
- **İşlevi performans ayrıntıları** belirttiğiniz işlevi için Özet profil oluşturma verilerini gösteren tablo.  
  
- **İşlev kod görünümü** kod kullanılabilir olduğunda, işlev kodunu gösteren bir pencere.  
  
  **İşlev kod görünümü** ayrı bir bölme bir penceredir. Varsayılan olarak, yatay, iki bölme bölme ve **işlev kod görünümü** penceresi çerçevenin en altında konumlandırılmış.  
  
- İki bölmeyi dikey olarak Böl için tıklatın **ekranı dikey olarak bölünmüş** araç.  
  
- Bölmelerin göreli boyutlarını değiştirmek için gölgeli kenarlık kareleri arasında tıklayın ve kenarlığı farklı bir konuma sürükleyin.  
  
## <a name="cost-distribution-bar-chart"></a>Maliyet dağıtımı çubuk grafik  
  
### <a name="performance-metrics"></a>Performans ölçümleri  
 İçinde **performans ölçümü** aşağı açılan listesinde, hangi değerlerin görüntülenir belirtebilirsiniz. Kullanılabilir değerler, profil oluşturma veri dosyasında kullanılan profil oluşturma yöntemine bağlıdır. Adlar parantez içinde: satır adları **işlevi performans ayrıntıları** tablo.  
  
### <a name="bar-chart"></a>Çubuk Grafiği  
 **İşlevleri çağırma**  
  
 **Çağıran fonksiyonları** çubuğu seçili işlev çağıran işlevler gösterir. Çağıran işlevin içeren bloğun performans ölçümü seçilen işlevin toplam değerini çağırma işlevine katkısını derlemekten boyutudur.  
  
 Görünümünde seçili işlev yapmak için bir çağıran işlevin adını tıklayabilirsiniz.  
  
- Listelemek için çok fazla arama işlevleri varsa, en küçük katkılar işlevleriyle toplanır bir **diğer** blok. Tıklayın **diğer** seçilen işlevin çağrılmasından ve çağrılan işlevlerinden görüntülenecek **arayan/Aranan görünümü** penceresi. Daha fazla bilgi için [arayan/Aranan görünümü](../profiling/caller-callee-view.md).  
  
- Çağıran işlev yok yoksa veya işlev bir iş parçacığı veya işlem girişi işlevi ise bir **üst, yığın** bloğu görünür.  
  
  **Seçili işlevi**  
  
  Seçili işleve çubuğu, seçilen işlevin toplam performans ölçüm seçili işlev çağrılan işlevlerin ve kod Katkıları gösterir. Proportion için çağrılan bir işlevin veya işlev gövdesinin içeren blok boyutu olduğundan seçilen işlevin performans ölçüm, toplam değere katkıyı.  
  
  Görünümünde seçili işlev yapmak için çağrılan bir işlevin adını tıklayabilirsiniz.  
  
- **Toplam** performans ölçümü seçilen işlevin bir değerdir.  
  
- **İşlev gövdesi** blok doğrudan işlevinin gövdesindeki kod yürütülmesi gerçekleşen performans ölçümü toplam değerini miktarını temsil eder.  
  
- Seçili işlev tarafından çağrılmış işlevler bloklar halinde listelenmiştir. Seçilen işlevlerin blok boyutu içinde çağrılan işlev oluştu seçilen işlevin toplam performans ölçümü miktarını temsil eder.  
  
- Listelemek için çok fazla arama işlevleri varsa, en küçük katkılar işlevleriyle toplanır bir **diğer** blok. Tıklayın **diğer** seçilen işlevin çağrılmasından ve çağrılan işlevlerinden görüntülenecek **arayan/Aranan görünümü** penceresi. Daha fazla bilgi için [arayan/Aranan görünümü](../profiling/caller-callee-view.md).  
  
- Çağrılan işlev yok, ise bir **alt, yığın** bloğu görünür.  
  
## <a name="function-performance-details"></a>İşlev performans ayrıntıları  
 İşlev performans Ayrıntıları tablosu özet verilerini seçili işlev için performans ölçümlerini sağlar. Hem değer hem de yüzde görünür. Belirtme ve grafik ayrıntıları görünen profil oluşturma verileri tablo olarak belirttiğiniz **performans ölçümü** listesi.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Özel**|-İşlev gövdesi yürütme gerçekleşen performans ölçümü miktarı.|  
|**Çağrıları**|-Seçili işlev çağıran işlevler içinde gerçekleşen performans ölçümü miktarı.|  
|**Kapsamlı toplam**|-Toplam **özel** ve **içinde çağrıları** değerleri.|  
  
## <a name="function-code-view"></a>İşlev kod görünümü  
 **İşlev kod görünümü** penceresi, kullanılabilir olduğunda kaynak kodunu bir listesini görüntüler. Diğer işlevlerini kaynak kod satırlarına yanındaki gölgeli bir sütun çağrılan işlev için performans ölçüm değerleri içerir. Kaynak kodu düzenlemek için kaynak kodu dosyasının bağlantısını tıklayın.  
  
## <a name="cost-distribution-bar-chart-values"></a>Maliyet dağıtımı çubuk grafik değerleri  
  
### <a name="sampling"></a>Örnekleme  
 Performans ölçümü liste için örnekleme metodu kullanılarak toplanmış olduğu profil oluşturma veri değerleri aşağıdaki tabloda açıklanmaktadır.  
  
|||  
|-|-|  
|**Kapsamlı örnekler (toplanan örnekler)**|-Bir arama işlevi için seçili işlev tarafından çağıran bu işlev çağrıldığında, toplanan örnek sayısı.<br />-İşlev gövdesi için seçili işlev kendi kod yürütülürken toplanan örnek sayısı.<br />-Çağrılan işlev için seçili işlev çağrısından nedeniyle çağrılan işlev yürütülürken toplanan örnek sayısı.|  
  
### <a name="instrumentation"></a>İzleme  
 Araçlar yöntemini kullanarak toplanan profil oluşturma verisi için performans ölçümü listesindeki değerlerin aşağıdaki tabloda açıklanmaktadır.  
  
|||  
|-|-|  
|**Geçen kapsamlı süre (geçen süre)**|Geçen süre bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrılarında harcanan süreyi içerir.<br /><br /> -İçin bir **işlevi çağırma**, işlev tarafından çağrılan örneklerini seçili işlev yürütülürken harcanan süre miktarı. Seçili işlev tarafından çağırılan işlevlerde geçen süre dahildir.<br />-İçin **işlev gövdesi**, geçen süre toplam harcanan seçili işlev kodunu yürütülüyor. Çağrılan işlevlerde geçen süre dahil değildir.<br />-İçin çağrılan bir işlev, seçili işlev tarafından çağrılan işlev örneklerini yürütülürken harcanan süre tutar. Toplam harcanan zaman işlevi olarak adlandırılan işlevler içerir. Seçili işlev tarafından çağırılan işlevlerde geçen süre dahildir.|  
|**Kapsamlı uygulama süresi (uygulama zamanı)**|Uygulama süresi bağlam anahtarları ve giriş/çıkış işlemleri gibi işletim sistemi çağrılarında harcanan süreyi içermez.<br /><br /> -İçin bir **işlevi çağırma**, işlev tarafından çağrılan örneklerini seçili işlev yürütülürken harcanan süreyi uygulama. Seçili işlev tarafından çağırılan işlevlerde geçen süre dahildir.<br />-İçin **işlev gövdesi**, toplam uygulama süreyi harcanan seçili işlev kodunu yürütülüyor. Çağrılan işlevlerde geçen süre dahil değildir.<br />-İçin çağrılan bir işlev, seçili işlev tarafından çağrılan işlev örneklerini yürütülürken harcanan tutar uygulama süre. Toplam harcanan zaman işlevi olarak adlandırılan işlevler içerir.|  
  
### <a name="net-memory"></a>.NET bellek  
 .NET bellek profil oluşturma yöntemini kullanarak toplanan profil oluşturma verisi için performans ölçümü listesindeki değerlerin aşağıdaki tabloda açıklanmaktadır.  
  
|||  
|-|-|  
|**Kapsamlı ayırmalar (ayırmalar)**|-İçin bir **işlevi çağırma**, çağrılan işlev seçili işlev örneği tarafından ayrılan nesne sayısı. Seçili işlev çağıran işlevler tarafından ayrılan nesneler içerir.<br />-İçin **işlev gövdesi**, tarafından ayrılan nesnelerin sayısını kendi kod yürütülürken seçili işleve göre. Seçili işlev tarafından çağırılan işlevlerdeki ayrılan nesneler dahil edilmez.<br />-Çağrılan işlev için seçili işlev tarafından çağrılan işlev örnekleri tarafından ayrılan nesne sayısı. İşlev çağıran işlevler tarafından ayrılan nesneler içerir.|  
|**Kapsamlı bayt (bayt)**|-İçin bir **işlevi çağırma**, çağrılan işlev seçili işlev örneği tarafından ayrılan bayt sayısı. Seçili işlev çağıran işlevler tarafından ayrılan bayt sayısını içerir.<br />-İçin **işlev gövdesi**, kendi kod yürütülürken seçili işlev tarafından ayrılan bayt sayısı. Seçili işlev tarafından çağırılan işlevlerdeki ayrılan bayt sayısı dahil edilmez.<br />-Çağrılan işlev için seçili işlev tarafından çağrılan işlev örnekleri tarafından ayrılan bayt sayısı. İşlev çağıran işlevler tarafından ayrılan bayt sayısını içerir.|  
  
### <a name="concurrency"></a>Eşzamanlılık  
 Eşzamanlılık metodu kullanarak toplanan profil oluşturma verisi için performans ölçümü listesindeki değerlerin aşağıdaki tabloda açıklanmaktadır.  
  
|||  
|-|-|  
|**Kapsamlı Çekişmeler (Çekişme)**|-İçin bir **işlevi çağırma**, çağrılan işlev seçili işlev durumlarda oluşan kaynak Çekişme olayları sayısı. Çekişme olayları seçili işlev çağıran işlevler içerir.<br />-İçin **işlev gövdesi**, işlev, kendi kod yürütülürken oluşan Çekişme olaylarının toplam sayısı. Seçili işlev tarafından çağrılan işlevler gerçekleşen Çekişme dahil edilmez.<br />-Çağrılan işlev için seçili işlev tarafından çağrılan işlev örneklerinde oluştu Çekişme olayları sayısı. Çekişme olayları işlevi çağıran işlevler içerir.|  
|**Kapsamlı engellenen zaman (engellenme süresi)**|-Bir arama işlevi için kaynak harcanan süreyi olayların seçili örnekleri için işlev Çekişme işlevi çağrılır. Saat çağrılan işlev seçili işlevlerde engellenme süresi içeriyor.<br />-İçin **işlev gövdesi**, işlev, kendi kod yürütülürken oluşan Çekişme olayları harcanan toplam süre. Seçili işlev çağıran işlevler içinde oluşan çakışmaları dahil edilmez.<br />-Çağrılan işlev için kaynak Çekişme olayları seçili işlevi çağıran işleve örnekleri için harcanan süre. Saat işlevi çağıran işlevler oluştu engellenme süresi içeriyor.|