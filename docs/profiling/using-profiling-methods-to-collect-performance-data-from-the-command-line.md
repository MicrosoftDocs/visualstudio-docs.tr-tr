---
title: Komut satırından performans verileri toplamak için profil oluşturma yöntemlerini kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e8dbaf62043897292afbb2805879e0447f3048a
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276708"
---
# <a name="use-profiling-methods-to-collect-performance-data-from-the-command-line"></a>Komut satırından performans verileri toplamak için profil oluşturma metotlarını kullanma
Tercih ettiğiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Araçları komut satırı araçlarını ve seçeneklerini etkenlere bağlıdır uygulama türü gibi profil olduğunu, kullanmak istediğiniz ve olup hedef uygulamanın yazıldığı yerel ya da Profiloluşturmayöntemine[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]kod.  
  
 Bu konu başlığı altında komut satırı yordam konuları seçtiğiniz profil oluşturma yöntemine göre düzenler.  
  
## <a name="use-the-sampling-method-to-collect-performance-statistics"></a>Örnekleme yöntemi performans istatistikleri toplamak için kullanın  
 Profil oluşturma araçları örnekleme profil oluşturma çalıştırmada belirtilen aralıklarla performans verilerini toplar. Veri örnekleme CPU bağımlı performans sorunlarıyla ilgili Öngörüler sağlayabilir ve bir uygulamanın performansını keşfetmeye başlamak için en iyi yolu olabilir.  
  
 Profil Oluşturucu uygulamaya çalışan bir örneğini ekleme veya profil oluşturucuyu ve aynı zamanda uygulamayı başlatabilirsiniz.  
  
|Görev|Hedef uygulama türü|  
|----------|-----------------------------|  
|**Bir uygulama başlatın**|-   [Tek başına uygulamalar](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|  
|**Çalışan bir işleme**|-   [.NET framework bağımsız uygulamalar](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)<br />-   [Yerel bir tek başına uygulamalar](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)<br />-   [ASP.NET web uygulamaları](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [.NET Hizmetleri](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Yerel Hizmetleri](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="use-the-instrumentation-method-to-collect-detailed-timing-data"></a>Ayrıntılı zamanlama verileri toplamak için izleme metodunu kullanın.  
 Profil oluşturma araçları izleme metodunu yazılım araştırmalardaki kayıt performans bilgilerini içeren bir uygulama ikili dosyalarını kopyalarını performans verilerini toplar. Ölçümlü izleme verilerini, başlangıç ve bitiş izleme eklenmiş her işlevin ve diğer işlevlere her çağrı izleme eklenmiş işlevden toplanır. Araçlar yöntemini, disk kullanımı gibi g/ç sorunlarını ile performans sorunlarını bulmak için yararlıdır.  
  
 İzleme eklenmiş ikili ile oluşturduğunuz [VInstr.exe](../profiling/vsinstr.md) aracı. Profil oluşturucuyu başlatmayı sonra hedef uygulamayı çalıştırdığınızda veri izleme eklenmiş ikili dosyaları otomatik olarak toplanır.  
  
 **Hedef uygulama türü**  
  
-   [.NET framework bağımsız bileşenler](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-timing-data.md)  
  
-   [Yerel bağımsız bileşenler](../profiling/how-to-instrument-a-native-component-and-collect-timing-data.md)  
  
-   [Statik olarak derlenmiş ASP.NET web uygulamaları](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)  
  
-   [Dinamik olarak derlenmiş ASP.NET web uygulamaları](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)  
  
-   [.NET Hizmetleri](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
-   [Yerel Hizmetleri](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
## <a name="use-net-memory-methods-to-collect-memory-allocation-and-object-lifetime-data"></a>Bellek ayırma ve nesne yaşam verisi toplamak için .NET bellek yöntemleri kullanın.  
 Profil oluşturma araçlar .NET bellek yöntemi toplamanızı sağlayan [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] bellek ayırma verilerinin ve nesne yaşam süresi hakkında bilgi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Hedef uygulamadaki profil oluşturucuyu kullanarak başlayabilirsiniz; Profil Oluşturucu uygulamaya çalışan bir örneğini ekleyebilirsiniz; İzleme eklenmiş sürümleri ile birlikte ayrıntılı zamanlama bilgileri toplamak için bir uygulama oluşturabilirsiniz [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] bellek verileri.  
  
|Görev|Hedef uygulama türü|  
|----------|-----------------------------|  
|**Bir uygulama başlatın**|-   [Tek başına bir .NET Framework uygulamaları](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-memory-data.md)|  
|**Çalışan bir işleme**|-   [.NET framework bağımsız uygulamalar](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-app-to-collect-memory-data.md)<br />-   [ASP.NET web uygulamaları](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [.NET Hizmetleri](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**Gereç modülleri**|-   [.NET framework bağımsız bileşenler](../profiling/how-to-instrument-a-dotnet-framework-component-and-collect-memory-data.md)<br />-   [Statik olarak derlenmiş ASP.NET web uygulamaları](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)<br />-   [Dinamik olarak derlenmiş ASP.NET web uygulamaları](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)<br />-   [.NET Hizmetleri](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## <a name="use-the-concurrency-method-to-collect-resource-contention-and-thread-activity-data"></a>Kaynak çakışması ve iş parçacığı etkinlik verilerini toplamak için eşzamanlılık yöntemi kullanın.  
 Profil oluşturma araçları eşzamanlılık yöntemi, kaynak çekişmesini ve iş parçacığı ve işlem etkinlik verileri birden çok iş parçacıklı uygulamalardan toplamanıza olanak tanır.  
  
 Profil oluşturucuyu kullanarak uygulamayı başlatabilirsiniz veya profil oluşturucuyu çalışan bir uygulama örneği için ekleyebilirsiniz.  
  
|Görev|Hedef uygulama türü|  
|----------|-----------------------------|  
|**Bir uygulama başlatın**|-   [Tek başına bir .NET Framework uygulaması](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)<br />-   [Tek başına yerel uygulama](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|  
|**Çalışan bir işleme**|-   [.NET framework bağımsız uygulamasına](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)<br />-   [Yerel bir tek başına uygulama](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)<br />-   [ASP.NET web uygulaması](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [.NET hizmeti](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Yerel hizmeti](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="add-tier-interaction-data-to-a-profiling-run"></a>Bir profil oluşturma yürütmesine katman etkileşim verileri ekleme  
 Bir profil oluşturma yürütmesine katman etkileşim verileri ekleme, komut satırı profil araçlarıyla özel yordamlar gerektirir. Bkz: [katman etkileşim verileri toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Bağımsız uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profil ASP.NET web uygulamaları](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil hizmetler](../profiling/command-line-profiling-of-services.md)