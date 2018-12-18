---
title: 'DA0038: Yüksek oranda kilit çakışmaları | Microsoft Docs'
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
- vs.performance.38
- vs.performance.rules.DA0038
- vs.performance.DA0038
ms.assetid: ae0c8b2f-17b2-4f3d-a834-aa2f6371753b
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c160ff4a61e8a0e2879cc0cacc59aae9e951361b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761143"
---
# <a name="da0038-high-rate-of-lock-contentions"></a>DA0038: Yüksek Oranda Kilit çakışmaları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 ile ilgili en son belgeler için bkz. [DA0038: yüksek oranda kilit çakışmaları](https://docs.microsoft.com/visualstudio/profiling/da0038-high-rate-of-lock-contentions) docs.microsoft.com'da.  
  
|||  
|-|-|  
|Kural Kimliği|DA0038|  
|Kategori|.NET framework kullanımı|  
|Profil oluşturma yöntemi|Örnekleme<br /><br /> İzleme<br /><br /> .NET bellek|  
|İleti|Bir yüksek oranda .NET kilit çakışması gerçekleşiyor. Lütfen eşzamanlılık profilini çalıştırarak bu kilit çakışmasının nedenini araştırın.|  
|Kural türü|Bilgiler|  
  
 Örnekleme, .NET bellek ve kaynak çekişmesi yöntemleri kullanılarak profili, bu kural tetiklemek için en az 25 örnekleri toplamanız gerekir.  
  
## <a name="cause"></a>Sebep  
 Toplanan sistem performansı verilerini profil oluşturma verileriyle birlikte önemli ölçüde yüksek oranda kilit çakışması uygulama yürütme sırasında oluştuğunu gösterir. Çekişme nedenini bulmak için eşzamanlılık profili oluşturma yöntemi kullanarak yeniden profil oluşturmayı göz önünde bulundurun.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Kilit, çok iş parçacıklı bir uygulamada bir anda bir iş parçacığı tarafından seri olarak yürütülmelidir kodun önemli bölümleri korumak için kullanılır. Microsoft .NET ortak dil çalışma zamanı (CLR), eşitleme ve temelleri kilitleme tam bir dizi sağlar. Örneğin, C# dili lock deyimi (Visual Basic'te SyncLock) destekler. Yönetilen bir uygulamayı almak ve doğrudan kilidi System.Threading ad alanında Monitor.Enter ve Monitor.Exit yöntemleri çağırabilir. .NET Framework, ek eşitleme ve temelleri Mutex'leri ReaderWriterLocks ve semaforları destekleyen sınıflar da dahil olmak üzere, kilitleme destekler. Daha fazla bilgi için [eşitleme temellerine genel bakış](http://go.microsoft.com/fwlink/?LinkId=177867) MSDN Web sitesinde .NET Framework Geliştirici Kılavuzu'nda. .NET Framework kendilerini Windows işletim sisteminde yerleşik daha düşük düzeyli Eşitleme Hizmetleri üzerinde katmanlı sınıflardır. Bunlar, kritik bölüm nesneleri ve birçok farklı bekleyin ve işlevleri sinyal olay içerir. Daha fazla bilgi için [eşitleme](http://go.microsoft.com/fwlink/?LinkId=177869) Win32 ve COM Geliştirme MSDN Kitaplığı'nda bölümü  
  
 .NET Framework sınıfları ve eşitleme için kullanılan yerel Windows nesneler temel ve kilitleme birbirine kenetlenmiş işlemler kullanarak değiştirmesi gereken paylaşılan bellek konumlardır. Paylaşılan bellek konumlarına atomik işlemler kullanarak kendi durumunu değiştirmek için çalışan işlemleri kullanın donanıma özgü yönergeleri birbirine geçmiş. Atomik işlemler, makinedeki tüm işlemciler arasında tutarlı olması garanti edilir. Kilitler ve WaitHandle ayarlamak veya sıfırlamak, otomatik olarak birbirine kenetlenmiş işlemler kullanan .NET nesneleridir. Olabilir diğer paylaşılan bellek veri yapılarını uygulamanızda da bir iş parçacığı açısından güvenli şekilde güncelleştirilmesi için birbirine kenetlenmiş işlemler kullanmanızı gerektirir. Daha fazla bilgi için [birbirine geçmiş Operations](http://go.microsoft.com/fwlink/?LinkId=177870) MSND kitaplığının .NET Framework bölümdeki  
  
 Eşitleme ve kilitleme çoklu iş parçacığı uygulamaları doğru yürütme sağlamak için kullanılan mekanizmasıdır. Çok iş parçacıklı bir uygulamanın her bir iş parçacığı işletim sistemi tarafından bağımsız olarak zamanlanır bağımsız yürütme birimidir. Başka bir iş parçacığı, kilidi tutan çünkü bir kilit almaya çalışırken bir iş parçacığı ertelendi her bir kilit çakışması gerçekleşir.  
  
 Kilitleri sık iç içe geçirilmiştir. İç içe geçme, önemli bir bölümü yürütme iş parçacığı başka bir kilit ardından gerektiren bir işlevi gerçekleştiren oluşur. Bazı kilit iç içe geçme kaçınılmaz miktarıdır. Kritik Bölümü kilitler iş parçacığı açısından güvenli olduğundan emin olmak için bağımlı bir .NET Framework yöntemi çağırabilir. Ayrıca farklı kilit işleci kullanılarak kilitler bir Framework yöntemi uygulamanıza bazı kritik bölümünden bir çağrı yerleştirmek kilit neden olur. İç içe geçmiş kilitleme koşullar aydınlatmak ve düzeltmek öğesinin zor olan performans sorunlarına yol açabilir.  
  
 Bu kural, bir profil oluşturma çalışması süresince alınan ölçümlere aşırı yüksek miktarda bir kilit çakışması var. belirttiğinizde tetikler. Kilit çakışması kilit için bekleyen iş parçacıklarının yürütülmesini geciktirmek. Kilit çakışması birim testlerini veya daha düşük bir son donanım üzerinde çalışan yük testlerini bile oldukça küçük miktarlarda araştırılmalıdır.  
  
> [!NOTE]
>  Profil oluşturma verilerinin bildirilen kilit çakışması oranını aşırı yüksek olduğunda [DA0039: çok yüksek oranda kilit çakışmaları](../profiling/da0039-very-high-rate-of-lock-contentions.md) uyarı iletisi bu bilgi iletisi yerine tetiklenir.  
  
## <a name="how-to-investigate-a-warning"></a>Bir uyarı araştırma  
 İletiyi gitmek için çift tıklatın [işaretleri](../profiling/marks-view.md) profil oluşturma verilerinin görünümü.  Bulma **.NET CLR LocksAndThreads\Contention hızı / sn** sütun. Varsa belirli program yürütme aşamaları kilit çakışması diğer aşamaları ağır olduğu belirleyin.  
  
 Bu kural yalnızca eşzamanlılık profili oluşturma yöntemi kullanmıyorsanız tetikler. Eşzamanlılık profili oluşturma yöntemi, uygulamanızdaki kilit çakışması ilgili performans sorunlarını tanılamak için en iyi bir araçtır. Eşzamanlılık profili oluşturma, uygulamanızın kilitlenme davranışını anlamak için verileri toplar. İş parçacığı yürütme süresi çekişmeli kilitler ve hangi belirli bir kod implicated bekleniyor ne kadar süreyle geciktirileceğini, bu hangi kilitleri yoğun contended anlama içerir. Eşzamanlılık profilleri topladığı verileri tüm kilit çakışmaları, yerel Windows özellikleri, .NET Framework sınıfları ve diğer üçüncü taraf kitaplıklar kilitlenme davranışını dahil olmak üzere uygulamanızı başvuruları. Öğesinden eşzamanlılık profil oluşturması hakkında bilgi için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE bkz [toplama iş parçacığı ve işlem eşzamanlılık verileri](../profiling/collecting-thread-and-process-concurrency-data.md). Komut satırından profil oluşturma eşzamanlılık hakkındaki bilgilere bağlantılar için bkz: **kaynak çekişmesini toplamak ve iş parçacığı etkinliği verileri için eşzamanlılık metodu kullanarak** bölümünü [kullanarak profil oluşturma yöntemleri gelen Komut satırı](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).

