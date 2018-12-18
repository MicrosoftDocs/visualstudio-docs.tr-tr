---
title: XAML uygulamalarında kaynak tüketimini analiz etme
ms.custom: seodec18
ms.date: 11/01/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: df7d854b-0a28-45a9-8a64-c015a4327701
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 32368b280faf7b87aa128865cf169c7675a58c95
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059184"
---
# <a name="analyze-resource-consumption-and-ui-thread-activity-xaml"></a>Kaynak tüketimi ve kullanıcı Arabirimi iş parçacığı etkinliği (XAML) analiz edin

Kullanım **uygulama zaman çizelgesi** ilgili XAML uygulamalarında performans sorunlarını bulup düzeltme uygulama etkileşimi profil oluşturucu. Bu araç, uygulamanın kaynak tüketimi ayrıntılı bir görünümünü göstererek XAML uygulama performansını artırmak yardımcı olur. (Düzen ve işleme), UI çerçevelerinin hazırlanması, ağ ve disk isteklerine hizmet uygulamanız tarafından ve uygulama başlatma, sayfa yükleme gibi senaryolar için harcanan süre çözümleyebilir ve Windows yeniden boyutlandırın.

**Uygulama zaman çizelgesi** ile başlayabilir araçları biri **hata ayıklama** > **performans Profiler** komutu.

Bu aracının yerini alır **XAML UI yanıtlama hızı** tanılama araç takımı Visual Studio 2013'ün bir parçası olan aracı.

Aşağıdaki platformlarda bu aracı kullanabilirsiniz:

- Evrensel Windows uygulamaları (üzerinde Windows 10)
- Windows 8.1
- Windows Presentation Foundation (.Net 4.0 ve üzeri)
- Windows 7

> [!NOTE]
> Toplama ve CPU kullanım verileri ve enerji tüketimi verilerini ile birlikte analiz **ApplicationTimeline** veri. Bkz: [profil oluşturma araçları ile veya hata ayıklayıcı olmadan çalıştırın](../profiling/running-profiling-tools-with-or-without-the-debugger.md).
  
## <a name="collect-application-timeline-data"></a>Uygulama zaman çizelgesi verilerini topla

Yerel makinenize, bağlı cihaz, Visual Studio simulatorunda veya öykünücüleri veya uzak cihaz üzerinde uygulamanızın yanıt verme hızı profilini oluşturabilirsiniz. Bkz: [profil oluşturma araçları ile veya hata ayıklayıcı olmadan çalıştırın](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

> [!TIP]
> Mümkünse, uygulamayı doğrudan cihazda çalıştırın. Uygulama performansı gözlenen veya bir Uzak Masaüstü Bağlantısı cihazdaki gerçek performansın aynı olmayabilir. Öte yandan, Visual Studio uzak Araçlar'ı kullanarak veri toplama, performans verileri etkilemez.  

Temel adımlar şunlardır:  

1. XAML uygulamanızı açın.

2. Tıklayın **hata ayıklama / performans Profiler**. Profil oluşturma araçları .diagsession penceresinde listesini görmeniz gerekir.

3. Seçin **uygulama zaman çizelgesi** ve ardından **Başlat** pencerenin alt kısmındaki.

   > [!NOTE]
   > Çalıştırmak için izninizi isteyen bir kullanıcı hesabı denetimi penceresinde görebilirsiniz *Vsetwcollector.exe'yi*. **Evet**'i tıklayın.

4. Uygulamanızda performans verilerini toplamak için profil oluşturma ilgilendiğiniz senaryonun çalıştırın.

5. Profil oluşturmayı durdurmak için .diagsession penceresine geçin ve **Durdur** pencerenin üst kısmındaki.

   Visual Studio toplanan verileri analiz eder ve sonuçları görüntüler.

   ![Zaman Çizelgesi profil oluşturucu rapor](../profiling/media/timeline_base.png "TIMELINE_Base")

## <a name="analyze-timeline-profiling-data"></a>Zaman Çizelgesi profil oluşturma verilerini analiz edin

Profil oluşturma verilerini topladıktan sonra analizinizi başlatmak için aşağıdaki adımları kullanabilirsiniz:  
  
1. İlgili bilgileri görüntülemek **UI iş parçacığı kullanımı** ve **görsel üretilen iş (FPS)** grafikler ve zaman çizelgesi gezinti çubuklarını çözümlemek istediğiniz bir zaman aralığını seçmek için kullanın.  
  
2. Bilgileri kullanarak **UI iş parçacığı kullanımı** veya **görsel üretilen iş (FPS)** grafikler, ayrıntıları inceleyin **zaman çizelgesi ayrıntıları** olası bulmak için neden için yanıt verme hızını seeming herhangi eksiği.
  
### <a name="BKMK_Report_scenarios_categories_and_events"></a> Rapor senaryoları, kategoriler ve olaylar  

**Uygulama zaman çizelgesi** araç senaryoları, kategoriler ve XAML performansıyla ilgili olayları için zamanlama verileri görüntüler.  

### <a name="BKMK_Diagnostic_session_timeline"></a> Tanılama oturumu zaman çizelgesi  

![Performans ve tanılama zaman çizelgesi](../profiling/media/diaghub_timelinewithusermarks.png "DIAGHUB_TimelineWithUserMarks")  

Sayfanın üst cetvel profili oluşturulan bilgiler için zaman çizelgesini gösterir. Bu zaman çizelgesi hem de geçerli **UI iş parçacığı kullanımı** grafiği ve **görsel üretilen iş** grafiği. Zaman çizelgesinin bir bölümü seçmek için, zaman çizelgesindeki gezinti çubuklarını sürükleyerek raporun kapsamını daraltabilirsiniz.  

Zaman Çizelgesi Ayrıca, eklediğiniz kullanıcı işaretlerini ve uygulamanın etkinleştirme yaşam döngüsü olaylarını da görüntüler.  

### <a name="BKMK_UI_thread_utilization_graph"></a> UI iş parçacığı kullanım grafiği

![CPU kullanım grafiği](../profiling/media/timeline_cpuutilization.png "TIMELINE_CpuUtilization")  

**UI iş parçacığı kullanımı (%)** grafiğidir göreli harcanan süreyi bir kategori için bir koleksiyon aralığı sırasında görüntüleyen bir çubuk grafiği.  

### <a name="BKMK_Visual_throughput_FPS_graph"></a> Görsel üretilen iş (FPS) grafiği  

![Görsel üretilen iş grafiklerini](../profiling/media/timeline_visualthroughput.png "TIMELINE_VisualThroughput")  

**Görsel üretilen iş (FPS)** çizgi grafiği, uygulama için kullanıcı Arabirimi ve kompozisyon iş parçacığında saniyedeki kare sayısını (FPS) gösterir.  

### <a name="BKMK_Timeline_details_"></a> Zaman Çizelgesi ayrıntıları  

Ayrıntılar görünümü, çözümleme rapor zamanınızın çoğunu burada harcadığınız ' dir. UI çerçevesi alt sistemi veya CPU kullanılan sistem bileşeni tarafından kategorilere uygulamanız tarafından CPU kullanımını gösterir.

Aşağıdakiler desteklenir:  

|||  
|-|-|  
|**Ayrıştırma**|XAML dosyaları ayrıştırma ve oluşturma nesneleri için harcanan süre.<br /><br /> Genişleyen bir **ayrıştırma** düğümünde **zaman çizelgesi ayrıntıları** kök olay nedeniyle ayrıştırıldı tüm XAML dosyaları bağımlılık zincirini görüntüler. Bu ipucu, gereksiz dosya ayrıştırma ve nesne oluşturma performans duyarlı senaryolarda tanımlamak ve bunları en iyi duruma olanak tanır.|  
|**Düzen**|Büyük uygulamalar, öğeleri binlerce aynı anda ekranda gösterilebilir. Bu görüntü, düşük kullanıcı Arabirimi kare hızı ve gelenlere kötü uygulama yanıt hızını neden olabilir. Düzen olayı doğru şekilde her bir öğe yerleştirme maliyetini belirler (diğer bir deyişle, harcanan süre düzenleyin, ölçü, ApplyTemplate, ArrangeOverride ve MeasureOverride). Ayrıca, bölüm düzeni pass sürdü visual ağaçları oluşturur. Bu görselleştirme hangi mantıksal ağaçları Ayıkla veya diğer erteleme mekanizmaları, Düzen geçişi en iyi duruma getirmek için değerlendirilecek belirlemek için kullanabilirsiniz.|  
|**İşleme**|Ekranda çizim XAML öğeleri için geçen süre.|  
|**BEN / 0**|Harcanan süre yerel diskten veya erişilir ağ kaynaklarına veri alma [Microsoft Windows Internet (WinINet) API](/windows/desktop/WinInet/portal).|  
|**Uygulama kodu**|Ayrıştırma veya Düzenle ilişkili olmayan (kullanıcı) uygulama kodu yürütürken harcanan süre.|  
|**XAML diğer**|XAML çalışma zamanı kodu yürütürken harcanan süre.|  
  
> [!TIP]
> Seçin **CPU kullanımı** ile birlikte aracı **uygulama zaman çizelgesi** aracı, UI iş parçacığında yürütülen görünümü uygulama yöntemler için profil oluşturmayı başlat. Uzun süre çalışan uygulama kodu taşımak için bir arka plan iş parçacığı UI yanıtlama hızını artırabilir.  
  
#### <a name="BKMK_Customizing_Timeline_details_"></a> Zaman Çizelgesi ayrıntıları özelleştirme  

Kullanım **zaman çizelgesi ayrıntıları** sıralama, filtreleme ve açıklamalarını belirtmek için araç **zaman çizelgesi ayrıntıları** girişleri görüntüleyin.  
  
|||  
|-|-|  
|**Sıralama ölçütü**|Başlangıç zamanı veya olayları uzunluğunu göre sıralayın.|  
|![Çerçeve tarafından olayları grup](../profiling/media/timeline_groupbyframes.png "TIMELINE_GroupByFrames")|Ekler veya bir üst düzey kaldırır **çerçeve** olayları çerçeve tarafından gruplandırır kategorisi.|  
|![Filtre zaman çizelgesi ayrıntıları listesi](../profiling/media/timeline_filter.png "TIMELINE_Filter")|Listeyi seçili kategorilerdeki ve olayları uzunluğunu göre filtreler.|  
|![Zaman Çizelgesi ayrıntıları bilgilerini özelleştirin](../profiling/media/timeline_viewsettings.png "TIMELINE_ViewSettings")|Ek açıklamalar olayları belirtmenize olanak sağlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF ekibi blogu: WPF uygulamaları için yeni kullanıcı Arabirimi performans çözümleme aracı](https://blogs.msdn.microsoft.com/wpf/2015/01/16/new-ui-performance-analysis-tool-for-wpf-applications/)  
- [C++, C# ve Visual Basic kullanarak UWP uygulamaları için en iyi performans](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [WPF uygulama performansını iyileştirin](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)  
- [Visual Studio profil oluşturma](../profiling/index.md)  
- [Araçlar profil oluşturmaya ilk bakış](../profiling/profiling-feature-tour.md)
