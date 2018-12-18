---
title: 'DA0022: Yüksek oranda Gen 2 çöp koleksiyonları | Microsoft Docs'
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
- vs.performance.DA0022
- vs.performance.rules.DA0022
- vs.performance.22
ms.assetid: f871a547-0e6f-4b11-b2d7-174d30fc2ed8
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8da44ab48ae468c5b71bcd08d106548f40d04aa8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757061"
---
# <a name="da0022-high-rate-of-gen-2-garbage-collections"></a>DA0022: Yüksek oranda Gen 2 çöp koleksiyonları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural Kimliği | DA0022 |  
| Kategori |. NET Framework kullanım |  
| Profil oluşturma yöntemi | Tüm |  
| İleti | Oldukça yüksek oranda Gen 2 çöp koleksiyonları gerçekleşen yoktur. Tasarım gereği, programınızın veri yapılarının çoğu ayrılan ve uzun bir süredir kalıcı ise, bu genellikle bir sorun değildir. Ancak, bu istenmeyen bir davranıştır, uygulamanız nesneleri sabitleme. Emin değilseniz, uygulamanızın kullandığı bellek ayırma desenini anlamak için .NET bellek ayırma verileri ve nesne yaşam süresi bilgilerini toplayabilirsiniz. |  
| Kural türü | Uyarı |  
  
 Örnekleme, .NET bellek ve kaynak çekişmesi yöntemleri kullanılarak profili, bu kural tetiklemek için en az 10 örnekleri toplamanız gerekir.  
  
## <a name="cause"></a>Sebep  
 Bellek for.NET Framework nesneleri önemli bir kısmı karşılaştırıldığında nesil 0 çöp toplama ve kuşak 1 çöp koleksiyonları 2. iadesi profil oluşturma sırasında toplanan sistem performans verilerini gösterir.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Microsoft .NET ortak dil çalışma zamanı (CLR) nesnelerden artık uygulamanın kullandığı belleği geri kazanmak için atık Toplayıcıya kullanan bir otomatik bellek yönetimi mekanizması sağlar. Atık toplayıcı nesil odaklı birçok ayırmaları ömürlüdür varsayımına dayanır. Örneğin, yerel değişkenler, kısa süreli olmalıdır. Yeni oluşturulan nesneleri nesil 0 (gen 0) başlatın ve bunların uygulama yine de bunları kullanıyorsa, ne zaman, bir çöp toplama çalıştırın ve son olarak 2. nesil geçiş varlığını sürdürmesini nesil 1 ilerleme durumu.  
  
 Nesil 0'daki nesneleri, sık ve genellikle çok verimli bir şekilde toplanır. 1. nesil nesneler, daha az sıklıkta ve daha az verimli bir şekilde toplanır. Son olarak, uzun süreli nesneler nesil 2 içinde bile daha az sık toplanması. Tam çöp toplama çalıştırmak olan 2. nesil koleksiyonu da en pahalı bir işlemdir.  
  
 Bu kural ne zaman orantılı olarak çok fazla nesil 2 çöp koleksiyonları gerçekleşen tetikler. Uyum gösteren .NET Framework uygulamaları 2. nesil koleksiyonlar birden 5 kez olarak birçok kuşak 1 çöp koleksiyonları olacaktır. (10 x faktör, büyük olasılıkla en uygun yöntemdir.)  
  
## <a name="how-to-investigate-a-warning"></a>Bir uyarı araştırma  
 Hata Listesi penceresindeki iletiyi gitmek için çift tıklatın [işaret görünümü](../profiling/marks-view.md) profil oluşturma verilerinin. Bulma **.NET CLR bellek\\Gen 0 toplamaları sayısı** ve **.NET CLR bellek\\Gen 1 toplamaları sayısı** sütunları. Varsa belirli program yürütme aşamaları çöp toplamanın daha sık nerede oluştuğunu belirler. Bu değerleri karşılaştırmak **% gc'de zaman** desenini yönetilen bellek ayırmaları, aşırı bellek yönetim yükünü neden olup olmadığını görmek için sütun.  
  
 Bir yüksek oranda 2. nesil çöp koleksiyonları her zaman bir sorun değildir. Tasarım gereği olabilir. Bu kural, yürütme sırasında uzun süreler için etkin kalması gereken büyük veri yapıları ayıran bir uygulama tetikleyebilir. Bu tür bir uygulama bellek baskısı altında olduğunda, sık sık çöp toplama işlemi gerçekleştirmek için zorlanabilir. Daha ucuz nesil 0 ve 1. nesil atık toplama yalnızca küçük bir miktar yönetilen belleği geri, daha sık nesil 2 çöp koleksiyonları zamanlanacak.  
  
 Çöp toplama sorunlarını belirlemenize yardımcı olabilecek işaretler görünümünde ek .NET CLR bellek sütunlar vardır. **% Gc'de zaman** sütun ne kadar bellek yönetim yükünü oluştuğunu anlamanıza yardımcı olur. Uygulamanız oldukça az sayıda büyük ancak kalıcı nesneler genellikle kullanıyorsa, sık sık 2. nesil koleksiyonlar aşırı miktarda CPU süresi kullanmalıdır değil. Daha fazla fiziksel bellek (RAM) değerlendirmek gerekli, ilgili kuralları olduğundan uygulamanın bellek baskısı altında olduğu durumlarda **Bellek\Sayfa/sn** sütun değerleri de yangın.  
  
 Uygulamanın düzeni yönetilen bellek kullanımını anlamak için profil dotfuscato bellek ayırma profili tekrar çalışır ve nesne ömür seçeneği seçin.  
  
 Çöp toplama performansını artırma hakkında daha fazla bilgi için bkz. [çöp toplayıcı temelleri ve performans ipuçları](http://go.microsoft.com/fwlink/?LinkId=148226) Microsoft Web sitesinde. Otomatik çöp toplama yükü hakkında daha fazla bilgi için bkz. [büyük nesne yığını Kapatılmamışa](http://go.microsoft.com/fwlink/?LinkId=177836).



