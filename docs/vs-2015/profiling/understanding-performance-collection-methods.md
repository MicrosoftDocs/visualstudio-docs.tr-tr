---
title: Performans toplama metotlarını anlama | Microsoft Docs
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
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling Tools, profiling methods
ms.assetid: ea4881fd-bd04-4875-9b7b-28490d6706f9
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a941b3c9dff3a80adea61026c6176dcf4c44361
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809058"
---
# <a name="understanding-performance-collection-methods"></a>Performans toplama metotlarını anlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Profil Araçları performans verilerini toplamak için kullanabileceğiniz beş yöntemler sağlar. Bu konu, farklı yöntemleri açıklar ve bazı senaryolarda belirli bir yöntem ile veri toplama uygun olabilir önerir.  
  
> [!NOTE]
>  Windows 8 ve Windows Server 2012'deki Gelişmiş güvenlik özellikleri Visual Studio profil oluşturucu bu platformlarda veri toplayan bir şekilde önemli değişiklikler gerekmiştir. Windows Store apps ayrıca yeni toplama teknikleri gerektirir. Bkz: [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Örnekleme](#sampling)|Bir uygulama tarafından gerçekleştirilen işin hakkında istatistiksel veriler toplar.|  
|[İzleme](#instrumentation)|Her işlev çağrısının hakkında ayrıntılı zamanlama bilgi toplar.|  
|[Eşzamanlılık](#concurrency)|Çok iş parçacıklı uygulamalar hakkında ayrıntılı bilgi toplar.|  
|[.NET bellek](#net_memory)|Ayrıntılı .NET bellek ayırma ve atık toplama hakkında bilgi toplar.|  
|[Katman etkileşimi](#tier_interaction)|Zaman uyumlu bir SQL Server veritabanına ADO.NET işlev çağrıları hakkında bilgi toplar.<br /><br /> Katman etkileşim profili oluşturma toplanacak kullanarak [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], veya [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Ancak, katman etkileşimli profil oluşturma veri yalnızca görüntülenebilir [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] veya [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].|  
  
 Bazı profil oluşturma yöntemlerini kullanarak, yazılım ve donanım performans sayaçları gibi ek verileri toplayabilirsiniz. Daha fazla bilgi için [ek performans verileri toplama](../profiling/collecting-additional-performance-data.md).  
  
##  <a name="sampling"></a> Örnekleme  
 Örnekleme profili oluşturma yöntemi, bir profil oluşturma çalışması sırasında bir uygulama tarafından gerçekleştirilen iş hakkında istatistiksel veriler toplar. Örnekleme yöntemi basit ve uygulama yöntemlerini yürütülmesi çok az etkisi.  
  
 Örnekleme profil oluşturma Visual Studio Araçları'nın varsayılan yöntemdir. Aşağıdakiler için kullanışlıdır:  
  
- Uygulamanızın performansını ilk araştırmaları.  
  
- İşlemci (CPU) kullanımına ilgili performans sorunlarını araştırmanıza.  
  
  Örnekleme profili oluşturma yöntemi, belirlenen aralıklarla Bilgisayar işlemcisi keser ve işlev çağrı yığını toplar. Dışlamalı örnek sayımları yürüten işlevi artırılır ve tüm çağrı yığınında çağırma işlevlerini içeren sayılar işlevin artırılır. Profili oluşturulan modülü, işlev, kaynak kod satırı ve yönerge için bu sayıları toplamı örnekleme raporlar sunar.  
  
  Varsayılan olarak, profil oluşturucu örnekleme aralığı için CPU döngülerini ayarlar. Aralık türü için başka bir CPU performans sayacı değiştirebilir ve aralığını sayacı olay sayısını ayarlayabilirsiniz. ADO.NET ile bir SQL server veritabanına yapılan sorguları hakkında bilgi sağlayan katman etkileşim profiling(TIP) verileri de toplayabilirsiniz.  
  
  [Örnekleme Kullanarak Performans İstatistikleri Toplama](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
  [Örnekleme Veri Değerlerini Anlama](../profiling/understanding-sampling-data-values.md)  
  
  [Örnekleme Yöntemi Veri Görünümleri](../profiling/profiler-sampling-method-data-views.md)  
  
##  <a name="instrumentation"></a> İzleme  
 İzleme profili oluşturma metodu profili oluşturulmuş bir uygulamada işlev çağrıları için ayrıntılı zamanlama toplar. İzleme profil aşağıdakiler için yararlıdır:  
  
- Disk g/ç gibi giriş/çıkış performans sorunlarını araştırma.  
  
- Belirli bir modülün incelenmesi veya işlevler kümesi kapatın.  
  
  Araçlar yöntemini kod izleme eklenmiş dosyanın her işlevde ve bu işlevler tarafından yapılan her işlev çağrısı için zamanlama bilgilerini yakalayan bir ikili dosyaya ekler. Bir dosyaya yazmak gibi işlemler için işletim içine bir işlevi çağırdığında, araçları da tanımlar. İzleme raporları, bir işlev veya kaynak kodu satır için harcanan toplam zamanı temsil eden dört değerleri kullanın:  
  
- Geçen Inclusive - işlevi veya kaynak satırı yürütmek için harcanan toplam süre.  
  
- Uygulama Inclusive - işlevi veya kaynak satırı yürütülürken, ancak işletim sistemi çağrılarında harcanan süre hariç geçen süre.  
  
- Geçen dışlamalı - işlevi veya kaynak kod satırı gövdesinde kod yürütürken harcanan süre. İşlev veya kaynak satırı tarafından çağrılan işlevleri yürütmek için harcanan süre dahil değildir.  
  
- Uygulama özel - işlevi veya kaynak kod satırı gövdesinde kod yürütürken harcanan süre. İşletim sistemi ve işlev veya kaynak satırı tarafından çağrılan işlevleri yürütmek için harcanan süre çağrıları yürütmek için harcanan süre dahil değildir.  
  
  Araçlar yöntemini kullanarak, hem CPU hem de yazılım performans sayaçları de toplayabilir.  
  
  [İzleme Veri Değerlerini Anlama](../profiling/understanding-instrumentation-data-values.md)  
  
  [İzleme Kullanarak Ayrıntılı Zamanlama Verileri Toplama](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)  
  
  [İzleme Metodu Veri Görünümleri](../profiling/instrumentation-method-data-views.md)  
  
##  <a name="concurrency"></a> Eşzamanlılık  
 Eşzamanlılık profil oluşturması, çok iş parçacıklı uygulamalar hakkında bilgi toplar. Paylaşılan bir kaynağa erişim için beklenecek toplar profil oluşturma kaynak çekişmesini, rakip iş parçacıkları her zaman ayrıntılı çağrı yığını bilgileri zorla. Eşzamanlılık görselleştirmesi ayrıca kendisi, donanım, işletim sistemi ve diğer işlemleri ana bilgisayarda birden çok iş parçacıklı uygulamanızın nasıl etkileşim hakkında daha fazla genel bilgi toplar:  
  
- Kaynak Çekişme raporları Çekişme ve modüller, İşlevler, kaynak kod satırlarına ve yönergeleri bekleniyor gerçekleştiği için bir kaynak beklerken geçen toplam süre toplam sayısını görüntüler. Bunlar oluştuğundan zaman çizelgesi grafikleri de çakışmaları gösterir.  
  
- Eşzamanlılık görselleştiricisi performans sorunları, CPU Tıkanıklığı, iş parçacığı Çekişme, iş parçacığı geçişi, eşitleme gecikmeleri, çakışan I/O alanları ve diğer bilgileri bulmak için kullanabileceğiniz grafik bilgilerini görüntüler. Mümkün olduğunda, yığın ve kaynak çağırmak üzere grafik çıktı bağlantıları veri kod. Eşzamanlılık görselleştirme verileri yalnızca komut satırı ve Windows uygulamaları için toplanabilir.  
  
  [Kaynak Çakışması Veri Değerlerini Anlama](../profiling/understanding-resource-contention-data-values.md)  
  
  [İş Parçacığı ve İşlem Eşzamanlılık Verileri Toplama](../profiling/collecting-thread-and-process-concurrency-data.md)  
  
  [Kaynak Çakışması Veri Görünümleri](../profiling/resource-contention-data-views.md)  
  
  [Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md)  
  
##  <a name="net_memory"></a> .NET bellek  
 .NET bellek ayırma profil oluşturma yöntemi, bilgisayar işlemci, profili oluşturulmuş bir uygulama .NET Framework nesnesinin her ayırma kesintiye uğratır. Nesne yaşam verisi ayrıca toplandığında, profil oluşturucu işlemci her .NET Framework çöp toplamanın ardından kesintiye uğratır.  
  
 Profil Oluşturucu türü, boyut ve sayısının bir ayırmayı oluşturulan ya da bir çöp toplama tahrip edilmiş nesne hakkında bilgi toplar.  
  
- Profil Oluşturucu, bir ayırma olayını ortaya çıktığında, işlev çağrı yığını hakkında daha fazla bilgi toplar. Dışlamalı ayırma sayıları şu anda yürütülmekte olan işlevi artırılır ve çağrı yığınında çağıran tüm işlevler için içeren sayılar işlevin artırılır. Profili oluşturulan türler, modüller, İşlevler, kaynak kod satırlarına ve yönergeler için bu sayıları toplamı .NET raporlar sunar.  
  
- Bir çöp toplama ortaya çıktığında, Profil Oluşturucu veri tahrip edilmiş nesneler hakkında ve her çöp toplama nesil nesneler hakkında bilgi toplar. Profil oluşturma çalışması sonunda, profil oluşturucu değil açıkça tahrip edilmiş nesneleri hakkında daha fazla veri kaydeder. Nesne ömrü rapor toplamları ayrılmış her türü için profil oluşturma çalıştırmasını görüntüler.  
  
  .NET bellek profili oluşturma, örnekleme veya izleme modunda kullanılabilir. Seçtiğiniz moda ayırma etkilemez ve nesne yaşam süresi benzersiz to.NET bellek profili oluşturma, raporları:  
  
- .NET bellek çalıştırdığınızda örnekleme modu profil oluşturma profiler.NET bellek ayırma olayları ve aralık olarak kullanır ve raporlarında dahil ve hariç değerler olarak ayrılan nesneler ve ayrılan toplam bayt sayısını görüntüler.  
  
- .NET bellek profili oluşturma araçları modda çalıştırdığınızda, birlikte dahil ve hariç ayırma değerleri ayrıntılı zamanlama bilgileri toplanır.  
  
  [Bellek Ayırma ve Nesne Yaşam Verisi Değerlerini Anlama](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)  
  
  [.NET Bellek Ayırma ve Yaşam Süresi Verilerini Toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)  
  
  [.NET Bellek Verisi Görünümleri](../profiling/dotnet-memory-data-views.md)  
  
##  <a name="tier_interaction"></a> Katman etkileşimi  
 Katman etkileşimli profil oluşturma ekler bilgi hakkında zaman uyumlu bir profil oluşturma veri dosyasını [!INCLUDE[vstecado](../includes/vstecado-md.md)] arasında çağıran bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] sayfa veya diğer uygulama ve [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] veritabanı. Veri sayısı ve zaman çağrıları ve maksimum ve minimum içerir. Örnekleme, izleme, .NET bellek veya eşzamanlılık yöntemi ile toplanan verileri profil oluşturma için katman etkileşim verileri eklenebilir.  
  
 ![Katman etkileşimi profil oluşturma verilerini](../profiling/media/tierinteraction-profilingtools.png "TierInteraction_ProfilingTools")  
Profil oluşturma araçları tarafından toplanan katman etkileşim verileri  
  
 [Katman etkileşim verileri toplama](../profiling/collecting-tier-interaction-data.md)  
  
 [Katman Etkileşimi Görünümleri](../profiling/tier-interaction-views.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: bir Web sitesi için performans verileri toplama](../profiling/how-to-collect-performance-data-for-a-web-site.md)   
 [Performans Profili Oluşturma Başlangıç Kılavuzu](../profiling/beginners-guide-to-performance-profiling.md)



