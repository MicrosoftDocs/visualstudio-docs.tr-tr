---
title: 'DA0023: Yüksek GC CPU süresi | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0023
- vs.performance.23
- vs.performance.rules.DA0023
ms.assetid: aba875fe-9cbc-418d-a2c4-6eb47519a5bb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7d13f1c0bc2a024d35611d81f4aba3694f3bc39e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836274"
---
# <a name="da0023-high-gc-cpu-time"></a>DA0023: Yüksek GC CPU süresi

|||  
|-|-|  
|Kural Kimliği|DA0023|  
|Kategori|.NET framework kullanımı|  
|Profil oluşturma yöntemi|Tümü|  
|İleti|Gc'de zaman oldukça yüksektir. Bu çöp toplama taşması aşırı miktarda göstergesi uygulamanızın yanıt hızını etkiliyor. Uygulamanızı daha iyi kullanabileceği bellek ayırması desenini anlamak için .NET bellek ayırma verileri ve nesne yaşam süresi bilgilerini toplayabilirsiniz.|  
|Kural türü|Bilgi|  

 Örnekleme, .NET bellek ve kaynak çekişmesi yöntemleri kullanılarak profili, bu kural tetiklemek için en az 10 örnekleri toplamanız gerekir.  

## <a name="cause"></a>Sebep  
 Profil oluşturma sırasında toplanan sistem performansı verilerini toplam uygulama işleme süresi ile karşılaştırıldığında, çöp toplamaya harcanan süreyi önemli olduğunu gösterir.  

## <a name="rule-description"></a>Kural açıklaması  
 Microsoft .NET ortak dil çalışma zamanı (CLR) nesnelerden artık uygulamanın kullandığı belleği geri kazanmak için atık Toplayıcıya kullanan bir otomatik bellek yönetimi mekanizması sağlar. Atık toplayıcı nesil odaklı birçok ayırmaları ömürlüdür varsayımına dayanır. Örneğin, yerel değişkenler, kısa süreli olmalıdır. Yeni oluşturulan nesneleri nesil 0 (gen 0) başlatın ve bunların uygulama yine de bunları kullanıyorsa, ne zaman, bir çöp toplama çalıştırın ve son olarak 2. nesil geçiş varlığını sürdürmesini nesil 1 ilerleme durumu.  

 Nesil 0'daki nesneleri, sık ve verimli bir şekilde toplanır. 1. nesil nesneler, daha az sıklıkta ve daha az verimli bir şekilde toplanır. Son olarak, uzun süreli nesneler nesil 2 içinde bile daha az sık toplanması. Tam çöp toplama çalıştırmak olan 2. nesil koleksiyonu da en pahalı bir işlemdir.  

 Bu kural, çöp toplamaya harcanan süreyi toplam uygulama işleme süresi ile karşılaştırıldığında önemli olduğunda tetikler.  

> [!NOTE]
>  Toplam uygulama işleme süresi ile karşılaştırıldığında oranı çöp toplamaya harcanan süresinin aşırı olduğunda [DA0024: aşırı GC CPU zamanı](../profiling/da0024-excessive-gc-cpu-time.md) yerine bu kural uyarı ateşlenir.  

## <a name="how-to-investigate-a-warning"></a>Bir uyarı araştırma  
 Hata Listesi penceresindeki iletiyi gitmek için çift tıklatın [işaret görünümü](../profiling/marks-view.md) profil oluşturma verilerinin. Bulma **.NET CLR bellek\\% gc'de zaman** sütun. Varsa belirli program yürütme aşamaları çöp toplamanın yönetilen bellek yükü diğer aşamaları ağır olduğu belirleyin. Gc'de zaman % değerlerini değer çöp toplama oranını karşılaştırma bildirilen içinde **Gen 0 toplamaları sayısı**, **Gen 1 toplamaları sayısı**, **Gen 2 toplamaları sayısı** değerleri .  

 Bir uygulama işleme toplam tutarı orantılı gerçekleştirme çöp toplama için harcadığı süreyi bildirmek % GC değerindeki zamanı çalışır. Bazı durumlarda yüksek bir değer % GC değerindeki zamanı bildirebilirsiniz, ancak nedeniyle aşırı çöp toplama değil unutmayın. % GC değerindeki zamanı hesaplanır biçimi hakkında daha fazla bilgi için bkz. [fark arasındaki performans verileri tarafından bildirilen farklı araçları - 4](http://go.microsoft.com/fwlink/?LinkId=177863) girişi **Maoni'nın blog** MSDN'de. Sayfa hataları ortaya çıkan veya uygulama tarafından diğer daha yüksek öncelikli iş makinede çöp toplama sırasında geçersiz kılınırsa, GC sayacı zaman % bu ek gecikmelere ücreti yansıtılır.