---
title: 'DA0021: Yüksek oranda Gen 1 çöp koleksiyonları | Microsoft Docs'
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
- vs.performance.21
- vs.performance.DA0021
- vs.performance.rules.DA0021
ms.assetid: ebf5d9b3-a1ac-4688-8f0f-39a85f4dd15f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77bcfd877bb0e5a8bf20caa629c226c4f304fafa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765852"
---
# <a name="da0021-high-rate-of-gen-1-garbage-collections"></a>DA0021: Yüksek oranda Gen 1 çöp koleksiyonları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural Kimliği | DA0021 |  
| Kategori |. NET Framework kullanım |  
| Profil oluşturma yöntemlerini | Tüm |  
| İleti | Oldukça yüksek oranda Gen 1 çöp koleksiyonları gerçekleşen yoktur. Tasarım gereği, programınızın veri yapılarının çoğu ayrılan ve uzun bir süredir kalıcı ise, bu genellikle bir sorun değildir. Ancak, bu istenmeyen bir davranıştır, uygulamanız nesneleri sabitleme. Emin değilseniz, uygulamanızın kullandığı bellek ayırma desenini anlamak için .NET bellek ayırma verileri ve nesne yaşam süresi bilgilerini toplayabilirsiniz. |  
| Kural türü | Bilgi |  
  
 Örnekleme, .NET bellek ve kaynak çekişmesi yöntemleri kullanılarak profili, bu kural tetiklemek için en az 10 örnekleri toplamanız gerekir.  
  
## <a name="cause"></a>Sebep  
 Bellek for.NET Framework nesneleri önemli bir kısmı, 1. nesil çöp toplama için nesil 0 veri toplama karşılaştırıldığında iadesi profil oluşturma sırasında toplanan sistem performans verilerini gösterir.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Microsoft .NET ortak dil çalışma zamanı (CLR) nesnelerden artık uygulamanın kullandığı belleği geri kazanmak için atık Toplayıcıya kullanan bir otomatik bellek yönetimi mekanizması sağlar. Atık toplayıcı nesil odaklı birçok ayırmaları ömürlüdür varsayımına dayanır. Örneğin, yerel değişkenler, kısa süreli olmalıdır. Yeni oluşturulan nesneleri nesil 0 (gen 0) başlatın ve bunların uygulama yine de bunları kullanıyorsa, ne zaman, bir çöp toplama çalıştırın ve son olarak 2. nesil geçiş varlığını sürdürmesini nesil 1 ilerleme durumu.  
  
 Nesil 0'daki nesneleri, sık ve genellikle çok verimli bir şekilde toplanır. 1. nesil nesneler, daha az sıklıkta ve daha az verimli bir şekilde toplanır. Son olarak, uzun süreli nesneler nesil 2 içinde bile daha az sık toplanması. Tam çöp toplama çalıştırmak olan 2. nesil koleksiyonu da en pahalı bir işlemdir.  
  
 Bu kural ne zaman orantılı olarak çok fazla kuşak 1 çöp koleksiyonları oluşmuş tetikler. Çok fazla oldukça kısa süreli nesneleri nesil 0 toplamadan ancak ardından 1. kuşak koleksiyonunda toplanır olanağına sahip olursunuz, bellek yönetimi maliyetini aşırı hale gelebilir. Daha fazla bilgi için [Orta yaşam kriz](http://go.microsoft.com/fwlink/?LinkId=177835) Rico Mariani'nın performans ipuçları MSDN Web sitesinde gönderin.  
  
## <a name="how-to-investigate-a-warning"></a>Bir uyarı araştırma  
 Hata Listesi penceresindeki iletiyi gitmek için çift tıklatın [işaret görünümü](../profiling/marks-view.md) profil oluşturma verilerinin. Bulma **.NET CLR bellek\\Gen 0 toplamaları sayısı** ve **.NET CLR bellek\\Gen 1 toplamaları sayısı** sütunları. Varsa belirli program yürütme aşamaları çöp toplamanın daha sık nerede oluştuğunu belirler. Bu değerleri karşılaştırmak **% gc'de zaman** desenini yönetilen bellek ayırmaları, aşırı bellek yönetim yükünü neden olup olmadığını görmek için sütun.  
  
 Uygulamanın düzeni yönetilen bellek kullanımını anlamak için yeniden dotfuscato bellek ayırma profili ve istek nesne yaşam süresi ölçülerini çalışmasını profil.  
  
 Çöp toplama performansını artırma hakkında daha fazla bilgi için bkz. [çöp toplayıcı temelleri ve performans ipuçları](http://go.microsoft.com/fwlink/?LinkId=148226) Microsoft Web sitesinde. Otomatik çöp toplama yükü hakkında daha fazla bilgi için bkz. [büyük nesne yığını Kapatılmamışa](http://go.microsoft.com/fwlink/?LinkId=177836).



