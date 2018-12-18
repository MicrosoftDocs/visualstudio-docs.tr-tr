---
title: Komut satırından performans verileri toplamak için profil oluşturma yöntemlerini kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d853322762942e874528b35164dc3f04a6c22b0a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722767"
---
# <a name="using-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Komut Satırından Performans Verileri Toplamak için Profil Oluşturma Yöntemlerini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tercih ettiğiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profil Araçları komut satırı araçlarını ve seçeneklerini etkenlere bağlıdır uygulama türü gibi profil olduğunu, kullanmak istediğiniz ve olup hedef uygulamanın yazıldığı yerel ya da Profiloluşturmayöntemine[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]kod.  
  
 Bu konu başlığı altında komut satırı yordam konuları seçtiğiniz profil oluşturma yöntemine göre düzenler.  
  
## <a name="in-this-topic"></a>Bu konuda  
 [Performans istatistikleri toplamak için örnekleme metodu kullanılarak](#BKMK_Using_the_sampling_method_to_collect_performance_statistics)  
  
 [Ayrıntılı zamanlama verileri toplamak için izleme metodunu kullanarak](#BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data)  
  
 [Bellek ayırma ve nesne yaşam verisi toplamak için .NET bellek yöntemlerini kullanma](#BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data)  
  
 [Kaynak çakışması ve iş parçacığı etkinlik verilerini toplamak için eşzamanlılık metodu kullanarak](#BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data)  
  
 [Bir profil oluşturma yürütmesine katman etkileşim verileri ekleme](#BKMK_Adding_tier_interaction_data_to_a_profiling_run)  
  
##  <a name="BKMK_Using_the_sampling_method_to_collect_performance_statistics"></a> Performans istatistikleri toplamak için örnekleme metodu kullanılarak  
 Profil oluşturma araçları örnekleme profil oluşturma çalıştırmada belirtilen aralıklarla performans verilerini toplar. Veri örnekleme CPU bağımlı performans sorunlarıyla ilgili Öngörüler sağlayabilir ve bir uygulamanın performansını keşfetmeye başlamak için en iyi yolu olabilir.  
  
 Profil Oluşturucu uygulamaya çalışan bir örneğini ekleme veya profil oluşturucuyu ve aynı zamanda uygulamayı başlatabilirsiniz.  
  
|Görev|Hedef uygulama türü|  
|----------|-----------------------------|  
|**Bir uygulama başlatın**|-   [Tek başına uygulamalar](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Çalışan bir işleme**|-   [.NET framework bağımsız uygulamalar](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Yerel bir tek başına uygulamalar](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [ASP.NET Web uygulamaları](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [.NET Hizmetleri](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Yerel Hizmetleri](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data"></a> Ayrıntılı zamanlama verileri toplamak için izleme metodunu kullanarak  
 Profil oluşturma araçları izleme metodunu yazılım araştırmalardaki kayıt performans bilgilerini içeren bir uygulama ikili dosyalarını kopyalarını performans verilerini toplar. Ölçümlü izleme verilerini, başlangıç ve bitiş izleme eklenmiş her işlevin ve diğer işlevlere her çağrı izleme eklenmiş işlevden toplanır. Araçlar yöntemini, disk kullanımı gibi g/ç sorunlarını ile performans sorunlarını bulmak için yararlıdır.  
  
 İzleme eklenmiş ikili ile oluşturduğunuz [VInstr.exe](../profiling/vsinstr.md) aracı. Profil oluşturucuyu başlatmayı sonra hedef uygulamayı çalıştırdığınızda veri izleme eklenmiş ikili dosyaları otomatik olarak toplanır.  
  
 **Hedef uygulama türü**  
  
-   [.NET framework bağımsız bileşenler](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Yerel bağımsız bileşenler](../profiling/how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Statik olarak derlenmiş ASP.NET Web uygulamaları](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
-   [Dinamik olarak derlenmiş bir ASP.NET Web uygulamaları](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
-   [.NET Hizmetleri](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
-   [Yerel Hizmetleri](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
##  <a name="BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data"></a> Bellek ayırma ve nesne yaşam verisi toplamak için .NET bellek yöntemlerini kullanma  
 Profil oluşturma araçlar .NET bellek yöntemi toplamanızı sağlayan [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] bellek ayırma verilerinin ve nesne yaşam süresi hakkında bilgi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
 Hedef uygulamadaki profil oluşturucuyu kullanarak başlayabilirsiniz; Profil Oluşturucu uygulamaya çalışan bir örneğini ekleyebilirsiniz; İzleme eklenmiş sürümleri ile birlikte ayrıntılı zamanlama bilgileri toplamak için bir uygulama oluşturabilirsiniz [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] bellek verileri.  
  
|Görev|Hedef uygulama türü|  
|----------|-----------------------------|  
|**Bir uygulama başlatın**|-   [Bağımsız bir .NET Framework uygulamaları](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line.md)|  
|**Çalışan bir işleme**|-   [.NET framework bağımsız uygulamalar](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [ASP.NET Web uygulamaları](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [.NET Hizmetleri](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**Gereç modülleri**|-   [.NET framework bağımsız bileşenler](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line.md)<br />-   [Statik olarak derlenmiş ASP.NET Web uygulamaları](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Dinamik olarak derlenmiş bir ASP.NET Web uygulamaları](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [.NET Hizmetleri](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
##  <a name="BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data"></a> Kaynak çakışması ve iş parçacığı etkinlik verilerini toplamak için eşzamanlılık metodu kullanarak  
 Profil oluşturma araçları eşzamanlılık yöntemi, kaynak çekişmesini ve iş parçacığı ve işlem etkinlik verileri birden çok iş parçacıklı uygulamalardan toplamanıza olanak tanır.  
  
 Profil oluşturucuyu kullanarak uygulamayı başlatabilirsiniz veya profil oluşturucuyu çalışan bir uygulama örneği için ekleyebilirsiniz.  
  
|Görev|Hedef uygulama türü|  
|----------|-----------------------------|  
|**Bir uygulama başlatın**|-   [Bağımsız bir .NET Framework uygulaması](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Tek başına yerel uygulama](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Çalışan bir işleme**|-   [.NET framework bağımsız uygulamasına](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Yerel bir tek başına uygulama](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line.md)<br />-   [ASP.NET Web uygulaması](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [.NET hizmeti](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Yerel hizmeti](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Adding_tier_interaction_data_to_a_profiling_run"></a> Bir profil oluşturma yürütmesine katman etkileşim verileri ekleme  
 Bir profil oluşturma yürütmesine katman etkileşim verileri ekleme, komut satırı profil araçlarıyla özel yordamlar gerektirir. Bkz: [katman etkileşim verileri toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağımsız uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarında profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)



