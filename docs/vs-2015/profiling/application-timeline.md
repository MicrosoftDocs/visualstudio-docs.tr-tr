---
title: Uygulama zaman çizelgesi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: df7d854b-0a28-45a9-8a64-c015a4327701
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d3a8edb0a2bf7809fc125812b5d541ba008547a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751433"
---
# <a name="application-timeline"></a>Uygulama zaman çizelgesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanım **uygulama zaman çizelgesi** ilgili XAML uygulamalarında performans sorunlarını bulup düzeltme uygulama etkileşimi profil oluşturucu. Bu araç, uygulamanın kaynak tüketimi ayrıntılı bir görünümünü sağlayarak XAML uygulamaları performansını yardımcı olur. Uygulamanızı (Düzen ve işleme), UI çerçevelerinin hazırlanması, ağ ve disk isteklerine hizmet ve uygulama başlatma ve sayfa yükleme Windows yeniden boyutlandırma gibi senaryolarda harcanan süre çözümleyebilirsiniz.  
  
 **Uygulama zaman çizelgesi** ile başlayabilir araçları biri **hata ayıklama / performans Profiler...**  komutu.  
  
 Bu aracının yerini alır **XAML UI yanıtlama hızı** tanılama araç takımı Visual Studio 2013'ün bir parçası olan aracı.  
  
 Aşağıdaki platformlarda bu aracı kullanabilirsiniz:  
  
1.  Evrensel Windows uygulamaları (üzerinde Windows 10)  
  
2.  Windows Store 8.1  
  
3.  Windows Phone 8.1 (ortak XAML Platform)  
  
4.  Windows Presentation Foundation (.Net 4.0 ve üzeri)  
  
5.  Windows 7  
  
> [!NOTE]
>  Toplama ve CPU kullanım verileri ve enerji tüketimi verilerini ile birlikte analiz **ApplicationTimeline** veri. Bkz: [hata ayıklama olmadan profil oluşturma araçları çalıştırma](http://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)  
  
##  <a name="BKMK_Collect_Timeline_data_for_your_app"></a> Uygulama zaman çizelgesi verileri toplama  
 Yerel makinenize, bağlı cihaz, Visual Studio simulatorunda veya öykünücüleri veya uzak cihaz üzerinde uygulamanızın yanıt verme hızı profilini oluşturabilirsiniz. Bkz: [hata ayıklama olmadan profil oluşturma araçları çalıştırma](http://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01).  
  
> [!TIP]
>  Mümkünse, uygulamayı doğrudan cihazda çalıştırın. Uygulama performansı gözlenen veya bir Uzak Masaüstü Bağlantısı cihazdaki gerçek performansın aynı olmayabilir. Öte yandan, Visual Studio uzak Araçlar'ı kullanarak veri toplama performans verileri etkilemez.  
  
 Temel adımlar şunlardır:  
  
1.  XAML uygulamanızı açın.  
  
2.  Tıklayın **hata ayıklama / performans Profiler...** . Profil oluşturma araçları .diagsession penceresinde listesini görmeniz gerekir.  
  
3.  Seçin **uygulama zaman çizelgesi** ve ardından **Başlat** pencerenin alt kısmındaki.  
  
    > [!NOTE]
    >  Vsetwcollector.exe'yi çalıştırmak için izninizi isteyen bir kullanıcı hesabı denetimi penceresinde görebilirsiniz. **Evet**'i tıklayın.  
  
4.  Uygulamanızda performans verilerini toplamak için profil oluşturma ilgilendiğiniz senaryonun çalıştırın.  
  
5.  Profil oluşturmayı durdurmak için .diagsession penceresine geçin ve **Durdur** pencerenin üst kısmındaki.  
  
     Visual Studio toplanan verileri analiz eder ve sonuçları görüntüler.  
  
     ![Zaman Çizelgesi profil oluşturucu rapor](../profiling/media/timeline-base.png "TIMELINE_Base")  
  
##  <a name="BKMK_Analyze_Timeline_profiling_data"></a> Zaman Çizelgesi profil oluşturma verilerini analiz edin  
 Profil oluşturma verilerini topladıktan sonra analizinizi başlatmak için aşağıdaki adımları kullanabilirsiniz:  
  
1.  Bilgileri inceleyin **UI iş parçacığı kullanımı** ve **görsel üretilen iş (FPS)** grafikler ve zaman çizelgesi gezinti çubuklarını çözümlemek istediğiniz bir zaman aralığını seçmek için kullanın.  
  
2.  Bilgileri kullanarak **UI iş parçacığı kullanımı** veya **görsel üretilen iş (FPS)** grafikler, ayrıntıları inceleyin **zaman çizelgesi ayrıntıları** olası nedenlerini keşfetmek için görünümü herhangi bir görünen kaçağın yanıt süresi için.  
  
###  <a name="BKMK_Report_scenarios_categories_and_events"></a> Rapor senaryoları, kategoriler ve olaylar  
 **Uygulama zaman çizelgesi** araç senaryoları, kategoriler ve XAML performansıyla ilgili olayları için zamanlama verileri görüntüler.  
  
###  <a name="BKMK_Diagnostic_session_timeline"></a> Tanılama oturumu zaman çizelgesi  
 ![Performans ve tanılama zaman çizelgesi](../profiling/media/diaghub-timelinewithusermarks.png "DIAGHUB_TimelineWithUserMarks")  
  
 Sayfanın üst cetvel profili oluşturulan bilgiler için zaman çizelgesini gösterir. Bu zaman çizelgesi hem de geçerli **UI iş parçacığı kullanımı** grafiği ve **görsel üretilen iş** grafiği. Zaman çizelgesinin bir bölümü seçmek için, zaman çizelgesindeki gezinti çubuklarını sürükleyerek raporun kapsamını daraltabilirsiniz.  
  
 Zaman çizelgesi ayrıca, eklediğiniz kullanıcı işaretlerini ve uygulamanın etkinleştirme yaşam döngüsü olaylarını da görüntüler.  
  
###  <a name="BKMK_UI_thread_utilization_graph"></a> UI iş parçacığı kullanım grafiği  
 ![CPU kullanım grafiği](../profiling/media/timeline-cpuutilization.png "TIMELINE_CpuUtilization")  
  
 **UI iş parçacığı kullanımı (%)** grafiğidir göreli harcanan süreyi bir kategori için bir koleksiyon aralığı sırasında görüntüleyen bir çubuk grafiği.  
  
###  <a name="BKMK_Visual_throughput_FPS_graph"></a> Görsel üretilen iş (FPS) grafiği  
 ![Görsel üretilen iş grafiklerini](../profiling/media/timeline-visualthroughput.png "TIMELINE_VisualThroughput")  
  
 **Görsel üretilen iş (FPS)** çizgi grafiği, uygulama için kullanıcı Arabirimi ve kompozisyon iş parçacığında saniyedeki kare sayısını (FPS) gösterir.  
  
###  <a name="BKMK_Timeline_details_"></a> Zaman Çizelgesi ayrıntıları  
 Ayrıntılar görünümü, burada çözümleme rapor zamanınızın çoğunu harcama ' dir. Bu, UI çerçevesi alt sistemi veya CPU kullanılan sistem bileşeni tarafından kategorilere uygulamanızın CPU kullanımını ayrıntılı bir görünümünü gösterir.  
  
 Aşağıdakiler desteklenir:  
  
|||  
|-|-|  
|**Ayrıştırma**|XAML dosyaları ayrıştırma ve oluşturma nesneleri için harcanan süre.<br /><br /> Genişleyen bir **ayrıştırma** düğümünde **zaman çizelgesi ayrıntıları** kök olay sonucu olarak ayrıştırıldı tüm XAML dosyaları bağımlılık zincirini görüntüler. Bu, gereksiz dosya ayrıştırma ve nesne oluşturma performans duyarlı senaryolarda tanımlamak ve bunları en iyi duruma getirmek sağlayacaktır.|  
|**Düzen**|Büyük uygulamalar, öğeleri binlerce aynı anda ekranda gösterilebilir. Bu, düşük kullanıcı Arabirimi kare hızı ve gelenlere kötü uygulama yanıt hızını neden olabilir. Düzen olayı doğru bir şekilde her öğe (Düzenle, ölçü, ApplyTemplate, ArrangeOverride ve ArrangeOverride harcanan zaman) düzenlemeyi maliyetini belirler ve bölüm düzeni pass sürdü visual ağaçları oluşturur. Bu görselleştirme hangi mantıksal uygulamanızın ağaçları ayıklama gerektiğini veya diğer erteleme mekanizmaları, Düzen geçişi en iyi duruma getirme değerlendirmek için kullanabilirsiniz.|  
|**İşleme**|Ekranda çizim XAML öğeleri için geçen süre.|  
|**BEN / 0**|Harcanan süre yerel diskten veya erişilir ağ kaynaklarına veri alma [Microsoft Windows Internet (WinINet) API](https://msdn.microsoft.com/library/windows/desktop/aa385331.aspx).|  
|**Uygulama kodu**|Ayrıştırma veya Düzenle ilişkili olmayan (kullanıcı) uygulama kodu yürütürken harcanan süre.|  
|**XAML diğer**|XAML çalışma zamanı kodu yürütürken harcanan süre.|  
  
> [!TIP]
>  Seçin **CPU kullanımı** ile birlikte aracı **uygulama zaman çizelgesi** aracı, UI iş parçacığında yürütülen görünümü uygulama yöntemler için profil oluşturmayı başlat. Uzun süre çalışan uygulama kodu taşımak için bir arka plan iş parçacığı UI yanıtlama hızını artırabilir.  
  
####  <a name="BKMK_Customizing_Timeline_details_"></a> Zaman Çizelgesi ayrıntıları özelleştirme  
 Kullanım **zaman çizelgesi ayrıntıları** sıralama, filtreleme ve açıklamalarını belirtmek için araç **zaman çizelgesi ayrıntıları** girişleri görüntüleyin.  
  
|||  
|-|-|  
|**Sıralama ölçütü**|Başlangıç zamanı veya olayları uzunluğunu göre sıralayın.|  
|![Çerçeve tarafından olayları grup](../profiling/media/timeline-groupbyframes.png "TIMELINE_GroupByFrames")|Ekler veya bir üst düzey kaldırır **çerçeve** olayları çerçeve tarafından gruplandırır kategorisi.|  
|![Filtre zaman çizelgesi ayrıntıları listesi](../profiling/media/timeline-filter.png "TIMELINE_Filter")|Listeyi seçili kategorilerdeki ve olayları uzunluğunu göre filtreler.|  
|![Zaman Çizelgesi ayrıntıları bilgilerini özelleştirin](../profiling/media/timeline-viewsettings.png "TIMELINE_ViewSettings")|Ek açıklamalar olayları belirtmenize olanak sağlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF ekibi blogu: Yeni kullanıcı Arabirimi Performans Analizi aracını WPF uygulamaları için](http://blogs.msdn.com/b/wpf/archive/2015/01/16/new-ui-performance-analysis-tool-for-wpf-applications.aspx)   
 [C++, C# ve Visual Basic kullanan Windows Store uygulamaları için en iyi performans](http://msdn.microsoft.com/en-us/567bcefa-5da5-4e42-a4b8-1358c71adfa2)   
 [WPF Uygulama Performansını İyileştirme](http://msdn.microsoft.com/library/ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf)



