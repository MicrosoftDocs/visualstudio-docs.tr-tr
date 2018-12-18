---
title: 'DA0018: 32 bit uygulama çalışan yönetilen bellek sınırlarında | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.18
- vs.performance.DA0018
- vs.performance.rules.DA0018
ms.assetid: 98eb2d96-f92f-42f9-915c-e5ac2330ffbf
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aeca49e13a2d7181d74f48522786185f4be9ed58
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722254"
---
# <a name="da0018-32-bit-application-running-at-process-managed-memory-limits"></a>DA0018: 32 bitlik Uygulama işlem tarafından yönetilen bellek sınırlarında çalışıyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural Kimliği | DA0018 |  
| Kategori | Profil oluşturma araçları kullanım |  
| Profil oluşturma yöntemi | Örnekleme |  
| İleti | Bellek ayırmaları 32 bitlik bir işlem için varsayılan sınırına yaklaşılıyor yönetilen. Uygulamanız bellek-sınırlı olabilir. |  
| Kural türü | Uyarı |  
  
 Örnekleme, .NET bellek ve kaynak çekişmesi yöntemleri kullanılarak profili, bu kural tetiklemek için en az 10 örnekleri toplamanız gerekir.  
  
## <a name="cause"></a>Sebep  
 Profil oluşturma çalışması sırasında toplanan sistem verilerini, .NET Framework bellek 32-bit işlem içinde yönetilen yığınlar ulaşan en büyük boyutu yığınlardaki yaklaşıldığında gösterir. Bu maksimum boyutu varsayılan değerdir. Özel baytlar için ayrılan işlem adres alanının toplam miktarını temel alır. Profilli işlemin etkinken yığınlar değerini gözlemlenen en yüksek değer bildirdi. Uygulama tarafından yönetilen kaynaklarının kullanımını en iyi duruma getirme ve .NET bellek profil oluşturma yöntemini kullanarak yeniden profil oluşturmayı göz önünde bulundurun.  
  
 Varsayılan sınır boyutu yönetilen yığınlar yaklaşımı, otomatik çöp toplama işlemi daha sık çağrılması gerekebilir. Bu, bellek yönetimi yükü artırır.  
  
 Kural, yalnızca 32 bit makinelerde çalıştırılan 32-bit uygulamalar için tetikler.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Microsoft .NET ortak dil çalışma zamanı (CLR) nesnelerden artık uygulamanın kullandığı belleği geri kazanmak için atık Toplayıcıya kullanan bir otomatik bellek yönetimi mekanizması sağlar. Atık toplayıcı nesil odaklı birçok ayırmaları ömürlüdür varsayımına dayanır. Örneğin, yerel değişkenler, kısa süreli olmalıdır. Yeni oluşturulan nesneleri nesil 0 (gen 0) başlatın ve bunların uygulama yine de bunları kullanıyorsa, ne zaman, bir çöp toplama çalıştırın ve son olarak 2. nesil geçiş varlığını sürdürmesini nesil 1 ilerleme durumu.  
  
 85 KB'den büyük olan yönetilen nesneleri, daha az sıklıkta atık toplama ve daha küçük nesneleri sıkıştırılmasını tabi olan büyük nesne yığını üzerindeki ayrılır. Bunlar daha kalıcı ve kalıcı ve büyük karıştırma çünkü nesneleri sık ayrılmış küçük nesnelerle yığının en kötü atama parçalanma üretebilir varsayıldığından büyük nesnelerin ayrı olarak yönetilir.  
  
 Toplam boyutu yönetilen yığınlar yaklaşımını varsayılan sınır, bellek yönetimi yükü genellikle, uygulamanın ölçeklenebilirlik ve yanıt hızını etkileyebilir başlayabileceğiniz noktasına artar.  
  
## <a name="how-to-investigate-a-warning"></a>Bir uyarı araştırma  
 Hata Listesi penceresindeki iletiyi gitmek için çift tıklatın [işaretleri](../profiling/marks-view.md) görünümü. Bulma **.NET CLR bellek\\# tüm yığınlardaki bayt** ve **# toplam kaydedilmiş bayt** sütunları. Varsa belirli program yürütme aşamaları yönetilen bellek ayırma diğer aşamaları ağır olduğu belirleyin. Değerleri Karşılaştır **# tüm yığınlardaki bayt** sütun çöp toplama hızı için bildirilen içinde **.NET CLR bellek\\Gen 0 toplamaları sayısı**, **.NET CLR bellek\\Gen 1 toplamaları sayısı**, ve **.NET CLR bellek\\Gen 2 toplamaları sayısı** yönetilen bellek ayırmaları desenini çöp oranını etkileyen varsa belirlemek için sütunları koleksiyonu.  
  
 Bir .NET Framework uygulamasında ortak dil çalışma zamanı yönetilen yığınlar biraz daha az için toplam boyutunu sınırlayan bir işlemin adres alanı özel alanı kısmı en büyük boyutunu yarısı daha. Bir 32-bit makine üzerinde çalışan 32 bitlik işlemler için işlem adres alanı özel bölümünü sayısı üst sınırı 2 GB temsil eder. Yönetilen yığınlar toplam boyutu varsayılan sınırına yaklaşım başladığında, bellek yönetme ek yükünü artırabilir ve uygulama performansını düşürebilir.  
  
 Aşırı yönetilen bellek yükü bir sorun varsa, bu seçeneklerden birini göz önünde bulundurun:  
  
- uygulamanın yönetilen bellek kaynaklarının kullanımını en iyi duruma getirme  
  
   veya  
  
- sanal bellek 32 bitlik bir işlem için en büyük boyutunu mimari kısıtlamalar hafifletmek için gerekli adımların atılmasından  
  
  Yönetilen bellek kaynaklarının uygulama kullanımını iyileştirmek için bir .NET bellek ayırma profil oluşturma, yönetilen bellek ayırma verisini toplayın. Gözden geçirme [.NET bellek verisi görünümleri](../profiling/dotnet-memory-data-views.md) bellek ayırma uygulama desenini anlamak için raporlar.  
  
  Kullanım [nesne ömrü görünümü](../profiling/object-lifetime-view.md) hangi programın veri oluşturma ve ardından buradan iadesi nesneleri geri kalan belirleme.  
  
  Kullanım [ayırma görünümü](../profiling/dotnet-memory-allocations-view.md) bu ayırma sonuçlanan yürütme yolunu belirlemek için.  
  
  Çöp toplama performansını artırma hakkında daha fazla bilgi için .NET Framework teknik makaleye bakın [çöp toplayıcı temelleri ve performans ipuçları](http://go.microsoft.com/fwlink/?LinkId=177946) MSDN Web sitesinde.  
  
  Mimari Tahliye boyutu sanal bellek kısıtlamalardan işlemi adres alanı özel kısmının kazanmak için bu 32 bit işlemin 64-bit bir makineye çalıştığı deneyin.  Bir 64-bit makinedeki 32 bitlik bir işlem en fazla 4 GB özel sanal bellek elde edebilirsiniz.  
  
  Bir 64 bit makine üzerinde çalışan 64 bitlik bir işlem 8 TB'a kadar sanal belleğin elde edebilirsiniz. Yerel bir 64 bit uygulama olarak yürütmek için uygulamayı yeniden derlemeyi düşünün. Bu kural yalnızca bilgi amaçlıdır ve düzeltici eylem gerekli değil.



