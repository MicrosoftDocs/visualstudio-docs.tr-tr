---
title: Profil oluşturma araçları | Microsoft Docs
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
- vs.diagnosticshub.overview
ms.assetid: 0fb6cd5d-e16a-4526-84a5-19e63c625bc5
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 380e98a8cd52fe77486dae245eee910a65a41057
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782108"
---
# <a name="profiling-tools"></a>Profil Araçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profil oluşturma ve tanılama araçları bellek ve CPU kullanımı ve diğer uygulama düzeyi sorunları tanılamanıza yardımcı olur. Bu araçları ile hata ayıklayıcıda uygulamanızı çalıştırdığınız zaman içinde verileri (örneğin, değişken değerleri, işlev çağrıları ve olayları) birikebilir. Kodunuzun yürütülmesi sırasında farklı noktalarda, uygulamanızın durumunu görüntüleyebilirsiniz.  
  
 Özet, proje türü için hangi araçları kullanılabildiğini görmek için alt kısımdaki göz atın (örneğin, masaüstü, UWP, ASP.NET).  
  
 Profil oluşturma araçlarını kullanarak erişebileceğiniz **hata ayıklama / Windows / tanılama araçlarını Göster** araçlarını kullanarak veya hata ayıklama oturumunuz sırasında kullanmak için **hata ayıklama / performans Profiler...**  odaklanmış performans analizi yapmak için.  Bkz: [çalıştıran profil oluşturma araçları ile veya olmadan, hata ayıklayıcı](../profiling/running-profiling-tools-with-or-without-the-debugger.md) farklı yaklaşımlar hakkında daha fazla bilgi için.  
  
 ![DebugDiagnosticsToolsMenu](../profiling/media/debugdiagnosticstoolsmenu.png "DebugDiagnosticsToolsMenu")  
  
 Bkz: [profil oluşturma araçlarındaki yenilikler](../profiling/what-s-new-in-profiling-tools.md) bu sürüm için yeni özellikleri hakkında bilgi edinin.  
  
 Aşağıdaki bölümlerde, Visual Studio'da farklı performans araçları açıklanmaktadır.  
  
## <a name="memory-usage"></a>Bellek kullanımı  
 ![DiagMemorySmall](../profiling/media/diagmemorysmall.png "DiagMemorySmall")  
  
 Bellek sızıntılarını ve verimsiz bellek ile hata ayıklarken Bul **bellek kullanımı** aracı. Aracı yönetilen ve yerel bellek yığın anlık görüntüsünü sağlar. Masaüstü uygulamaları, Windows Evrensel uygulamaları ve ASP.NET uygulamaları ile bu aracı kullanabilirsiniz. **Bellek kullanımı** araç çalıştırılabilir **tanılama araçları** ayıklarken penceresi (**hata ayıklama / Windows / tanılama araçlarını Göster**) veya hata ayıklayıcı (dışında**Hata ayıklama / performans Profiler...**). Bkz: [bellek kullanımı](../profiling/memory-usage.md) ve [bellek kullanımını hata ayıklama olmadan](http://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0) daha fazla bilgi için.  
  
## <a name="cpu-usage"></a>CPU kullanımı  
 ![DiagCPUSmall](../profiling/media/diagcpusmall.png "DiagCPUSmall")  
  
 **CPU kullanımı** aracı gösterir, CPU zamanı yürütülen C++, C# burada harcama / VB ve JavaScript kodu.  Hem Masaüstü ve Windows Evrensel uygulamaları, hem de ile Azure App Services uygulamaları bu aracı kullanabilirsiniz. **CPU kullanımı** araç çalıştırılabilir **tanılama araçları** ayıklarken penceresi (**hata ayıklama / Windows / tanılama araçlarını Göster**) veya hata ayıklayıcı (dışında**Hata ayıklama / performans Profiler...**). Bkz: [CPU kullanımı](../profiling/cpu-usage.md) daha fazla bilgi için.  
  
## <a name="performance-explorer"></a>Performans Gezgini  
 ![PerfTools](../profiling/media/perftools.png "PerfTools")  
  
 **Performans Gezgini** (**hata ayıklama / Profiler / performans Gezgini**) birçok farklı araçları kullanmanıza olanak tanır dahil olmak üzere **CPU örnekleme**,  **İzleme**, **.NET bellek ayırma**, ve **kaynak çekişmesini**. Masaüstü uygulamaları ve ASP.NET uygulamaları, ancak Windows Evrensel uygulamaları performans Gezgini araçlarını kullanabilirsiniz. Daha fazla bilgi için [performans Gezgini](../profiling/performance-explorer.md).  
  
## <a name="gpu-usage"></a>GPU Kullanımı  
 ![DiagGPUUsage](../profiling/media/diaggpuusage.png "DiagGPUUsage")  
  
 Kullanım [GPU kullanımı](../debugger/gpu-usage.md) Direct3D uygulamanızı üst düzey donanım kullanımını daha iyi anlamak için aracı. Bu araç, hem Masaüstü ve Windows Evrensel uygulamaları, ancak ASP.NET uygulamaları ile kullanabilirsiniz. **GPU kullanımı** araç çalıştırılabilir **tanılama araçları** ayıklarken penceresi (**Göster / hata ayıklama tanılama araçları**) veya hata ayıklayıcı dışında (**Hata ayıklama / performans Profiler...**).  
  
## <a name="application-timeline"></a>Uygulama zaman çizelgesi  
 ![DiagAppTimeline](../profiling/media/diagapptimeline.png "DiagAppTimeline")  
  
 [Uygulama zaman çizelgesi](../profiling/application-timeline.md) aracı kaynak tüketimi için ayrıntılı bir görünümünü sağlayarak XAML uygulamaları performansını yardımcı olur. Kullanabileceğiniz **uygulama zaman çizelgesi** Masaüstü ve Windows Evrensel uygulamaları, ancak ASP.NET uygulamaları. **Uygulama zaman çizelgesi** araç çalıştırılabilir **tanılama araçları** penceresi (**hata ayıklama / performans Profiler...** ).  
  
## <a name="perftips"></a>PerfTips  
 ![DiagPerfTips](../profiling/media/diagperftips.png "DiagPerfTips")  
  
 Hata ayıklayıcı bir kesme noktası veya atlama işlemi yürütmeyi sona erdiğinde, kesme ve önceki kesme noktası arasında geçen süre düzenleyici penceresinde bir ipucu olarak görüntülenir. Bunlar [PerfTips](../profiling/perftips.md) izleme ve hata ayıklarken uygulamanızın performansını analiz yardımcı olur. Gördüğünüz **PerfTips** Masaüstü, Windows evrensel ve ASP.NET uygulamaları.  
  
## <a name="javascript-memory"></a>JavaScript bellek  
 ![DiagJSMemory](../profiling/media/diagjsmemory.png "DiagJSMemory")  
  
 [JavaScript belleği](../profiling/javascript-memory.md) aracı, ölçün, değerlendirin ve giriş ve çıkış uygulamanızdaki her işlevin zamanlama bilgileri toplayarak performans ile ilgili sorunlar kodunuzda hedef sağlar. Windows Evrensel HTML uygulamaları ile bu aracı kullanabilirsiniz. **JavaScript işlev zamanlaması** araç çalıştırılabilir **tanılama araçları** penceresi (**hata ayıklama / performans Profiler...** ).  
  
## <a name="html-ui-responsiveness"></a>HTML kullanıcı Arabirimi yanıt hızı  
 ![DiagHTMLResp](../profiling/media/diaghtmlresp.png "DiagHTMLResp")  
  
 [HTML UI yanıtlama hızı](../profiling/html-ui-responsiveness.md) aracı yanıt süresi, yükleme süresi, yavaş olmaması dahil olmak üzere uygulamalarınızın performans sorunları ayırmanıza yardımcı olur ve daha az olan görsel güncelleştirmeleri, beklenenden daha sık. Windows Evrensel HTML uygulamaları ile bu aracı kullanabilirsiniz. **HTML UI yanıtlama hızı** araç çalıştırılabilir **tanılama araçları** penceresi (**hata ayıklama / performans Profiler...** ).  
  
## <a name="intellitrace"></a>IntelliTrace  
 ![DiagIntelliTrace](../profiling/media/diagintellitrace.png "DiagIntelliTrace")  
  
 [IntelliTrace](../debugger/intellitrace.md) kayıt belirli olayları, verileri incelemek sayesinde **Yereller** penceresi sırasında hata ayıklayıcı olayları ve işlev çağrıları ve yeniden oluşturulması zor olan hata ayıklama hataları.  IntelliTrace, hata ayıklama aracı öncelikle olmakla birlikte, performans verileri araştırmak için kullanılan bilgileri de sağlar. Visual Studio Enterprise bu aracın yalnızca, masaüstü, Windows evrensel ve ASP.NET C# uygulamaları ile kullanabilirsiniz. IntelliTrace içinde bulabilirsiniz **tanılama araçları** ayıklarken penceresi (**hata ayıklama / Windows / tanılama araçlarını Göster**).  
  
## <a name="profiling-in-production"></a>Üretim ortamında profil oluşturma  
 Üretim ortamında profil oluşturma için önerilen profilinden yaklaşımdır [vsperf.exe kullanarak komut satırı](../profiling/using-the-profiling-tools-from-the-command-line.md) CPU profili toplanacak. Azure App Service'te uzaktan profil oluşturma desteği için aracılığıyla profilini oluşturabilirsiniz [Sunucu Gezgini veya Kudu portalı](https://azure.microsoft.com/en-us/blog/remote-profiling-support-in-azure-app-service/).  
  
## <a name="which-tool-should-i-use"></a>Hangi aracı kullanmalıyım?  
 Farklı araçlar sunan Visual Studio listeleyen bir tablo işte ve farklı proje türleri ile kullanabilirsiniz:  
  
|Performans aracı|Windows Masaüstü|Windows Evrensel/Store|ASP.NET|  
|----------------------|---------------------|------------------------------|-------------|  
|[Bellek Kullanımı](../profiling/memory-usage.md)|Evet|Evet|Yok|  
|[CPU Kullanımı](../profiling/cpu-usage.md)|Evet|Evet|Yalnızca Azure uygulama hizmeti|  
|[GPU Kullanımı](../debugger/gpu-usage.md)|Evet|Evet|Yok|  
|[Uygulama Zaman Çizelgesi](../profiling/application-timeline.md)|Evet|Evet|Yok|  
|[PerfTips](../profiling/perftips.md)|Evet|XAML, HTML için Hayır için Evet|Yok|  
|[Performans Gezgini](../profiling/performance-explorer.md)|Evet|Yok|Evet|  
|[IntelliTrace](../debugger/intellitrace.md)|Yalnızca .NET Enterprise|Yalnızca .NET Enterprise|Yalnızca .NET Enterprise|  
|[HTML kullanıcı arabirimi yanıt hızı](../profiling/html-ui-responsiveness.md)|Yok|Evet, HTML için XAML için Hayır|Yok|  
|[JavaScript Belleği](../profiling/javascript-memory.md)|Yok|Evet, HTML için XAML için Hayır|Yok|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio IDE](../ide/visual-studio-ide.md)



