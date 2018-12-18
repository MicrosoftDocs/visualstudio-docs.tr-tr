---
title: İş Parçacıkları görünümü'nde eşzamanlılık görselleştiricisi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce7cf5cf0534a0e989b65d6e67451fe2a7c496ab
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388911"
---
# <a name="threads-view-in-the-concurrency-visualizer"></a>Eşzamanlılık görselleştiricisi'ndeki iş parçacıkları görünümü

**İş parçacığı** en ayrıntılı ve zengin eşzamanlılık görselleştiricisi görünümünde bir görünümdür. İçinde **iş parçacıkları** görünümü, hangi iş parçacığı bir yürütme kesimi sırasında kodu yürüten tanımlayabilir ve yürütme ya da eşitleme, g/ç veya diğer nedenlerle nedeniyle engelleyen iş parçacığı analiz edin. **İş parçacığı** raporlar da profil çağrı yığını ağacı yürütme ve iş parçacıklarının engellemesinin kaldırılması görünümü.

İş parçacıkları çalıştırılıyorken, Concurrency Visualizer örnekleri toplar. Bir iş parçacığının yürütülmesi durdurulduğunda, iş parçacığı için tüm işletim sistemi bağlam anahtar olayları Görselleştirici inceler. Bağlam anahtarları nedeniyle oluşabilir:  
  
- Bir iş parçacığı eşitleme temel nesne üzerinde engellenir.  
- İş parçacığı kuantum süresi dolar.  
- Bir iş parçacığı, engelleyici bir g/ç isteği yapar.  

Eşzamanlılık görselleştiricisi iş parçacığı ve bağlam anahtar olayları kategorilere ayırır ve iyi bilinen engelleme API'leri için iş parçacığı çağrı yığınlarını arar. Alt sol konumunda etkin Göstergedeki iş parçacığı kategorileri görüntüler **iş parçacıkları** görünümü. Çoğu durumda, içerik anahtarı olayları için karşılık gelen çağrı yığınlarını inceleyerek engelleyen bir olayı kök nedenini tanımlayabilirsiniz.

Çağrı yığını eşleşme yoksa, Concurrency Visualizer tarafından sağlanan bekleme nedeni kullanan [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]. Ancak, [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] kategorisi üzerinde bir uygulama ayrıntısı temel olabilir ve kullanıcının amacını yansıtmayabilir. Örneğin, [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] g/ç eşitleme yerine olarak yerel ince Okuyucu-Yazıcı kilit engellemek için bekleme nedeni bildirir.  
  
**İş parçacığı** görünümü ayrıca iş parçacıkları arasındaki bağımlılıkları gösterir. Örneğin, bir eşitleme nesnesi üzerinde engellenen bir iş parçacığı olduğunu belirlerseniz, onu engeli kaldırılmış iş parçacığı bulabilirsiniz. Diğer tek engellemesini zaman noktasında engellemeyi kaldırma iş parçacığı için çağrı yığınını inceleyebilirsiniz.  

Kullanabileceğiniz **iş parçacıkları** görüntüleyin:  

- Kullanıcı Arabirimi (UI) bir uygulamanın belirli yürütme aşamaları sırasında yanıt vermiyor nedeniyle belirleyin.  
- Eşitleme, g/ç, sayfa hataları ve diğer olayları engelleme harcadığı süre miktarını belirleyin.  
- Sistemde yürütülen diğer işlemleri girişime derecesini keşfedin.  
- Paralel yürütme için Yük Dengeleme sorunları belirleyin.  
- Yetersiz ya da yok ölçeklenebilirlik nedenlerle bulun. Daha fazla mantıksal çekirdek hazır olduğunda, neden paralel bir uygulaması performansını iyileştirmez.  
- Uygulamasındaki paralelleştirme, yardımcı olmak için eşzamanlılık derecesini anlayın.  
- Çalışan iş parçacıkları ve kritik yürütme yollarına arasında bağımlılıklar tanımlayın.  
  
## <a name="use-threads-view"></a>İş Parçacıkları görünümü kullanın 

Eşzamanlılık görselleştiricisi'ni başlatmak için **Çözümle** > **eşzamanlılık görselleştiricisi**ve ardından bir seçenek, aşağıdaki gibi seçin **yeni bir işlem başlatma**. 

Eşzamanlılık görselleştiricisi uygulama başlar ve siz seçene kadar bir izleme toplar **toplamasını Durdur**. Görselleştirici izlemeyi analiz eder ve izleme rapor sayfasında sonuçları görüntüler. 

Seçin **iş parçacıkları** sol üst köşesinde raporu açmak için sekmesinde **iş parçacıkları** görünümü. 

![İş Parçacıkları görünümü](../profiling/media/threadsviewnarrowing.png "iş parçacıkları görünümü")  
  
Zaman aralıkları ve Performans Analizi başlatmak için iş parçacığı seçin.  
  
## <a name="timeline-analysis"></a>Zaman Çizelgesi analizi  

Üst kısmında **iş parçacıkları** bir zaman çizelgesi görünümüdür. Zaman çizelgesi işlemi ve ana bilgisayarda tüm fiziksel disk cihazlarının tüm iş parçacıklarının etkinliğini gösterir. Ayrıca GPU etkinliği ve işaret olayları görüntüler.  

Zaman çizelgesi üzerinde süresi x ekseni ve y ekseninde olan çeşitli kanallar:  
  
- Sistem, bir kanalı için okuma ve yazma işlemleri için bir tane her disk için iki g/ç kanal.  
- İşlemdeki her iş parçacığı için bir kanal.  
- İzlemede işaret olayları olup olmadığına işaret kanalları. İşaret kanalları, başlangıçta bu olayları oluşturan iş parçacığı kanalları altında görünür.  
- GPU kanalları.  
  
Başlangıçta, ana uygulama iş parçacığı ilk olarak, bu nedenle iş parçacığı, oluşturuldukları sıraya göre sıralanır. Başka bir seçeneğini **sıralama ölçütü** açılan sıralamak için başka bir ölçüte göre gibi iş parçacıkları **yürütme**. 

Zaman Çizelgesi renkleri, belirli bir zamanda bir iş parçacığı durumunu gösterir. Yeşil segmentleri yürütme, kırmızı segmentleri eşitlemede engellendi, sarı segmentleri etkisiz ve mor segmentleri cihaz g/ç katılan. 

Daha fazla ayrıntı görüntülemek için yakınlaştırın veya uzun bir zaman aralığı görmek için uzaklaştırmanız. Parçaları ve kategorileri hakkında ayrıntılı bilgi edinmek için gecikmeler kez başlatın ve çağrı yığını durumları grafiğine noktalarında seçin.  

Paralel bir döngüden veya eş zamanlı görevleri katılan iş parçacıkları arasında iş Bakiye incelemek için zaman çizelgesi kullanın. Bir iş parçacığı diğerlerine göre daha uzun zaman alıyorsa, iş dengesiz olabilir. İş parçacıkları arasında daha eşit dağıtarak uygulamanızın performansını iyileştirebilir.  
  
Yalnızca tek bir iş parçacığı bir noktada sürede yürütüyor, uygulama tam anlamıyla eşzamanlılık sistemde sürüyor değil. İş parçacığı engelleme arasındaki geçici ilişkiyi arasındaki bağımlılıkları incelemek için zaman çizelgesi grafiği kullanabilirsiniz ve engellenen iş parçacıkları. İş parçacığı yeniden düzenlemek için bir iş parçacığı seçin ve yukarı veya aşağı araç çubuğundaki simgeye. 

İş yaptığı değil ya da kendi istatistikleri ilgisi olmayan ve raporları clog çünkü tamamen, engellenen iş parçacıkları gizleyebilirsiniz. İş parçacığı adlarını ve ardından seçerek Gizle **Seçili iş parçacıklarını Gizle** veya **hariç Seçili iş parçacıklarını Gizle** araç çubuğundaki simgeler. İş parçacıklarını Gizle tanımlamak için seçin **başına iş parçacığı özeti** bağlantı sol konumunda. Hiçbir etkinlik olmayan iş parçacıkları gizleyebilirsiniz **başına iş parçacığı özeti** grafiği. 

### <a name="thread-execution-details"></a>İş parçacığı yürütme ayrıntıları  
Bir yürütme segment hakkında daha ayrıntılı bilgi almak için zaman çizelgesi yeşil bir Segmentte bir noktası seçin. Eşzamanlılık görselleştiricisi seçili belirli noktaya yukarıda siyah şapka işareti görüntüler ve çağrı yığınını gösteren **geçerli** alt bölme sekmesi. Birden çok yürütme kesim noktalarını seçebilirsiniz.  
  
>[!NOTE]
>Eşzamanlılık görselleştiricisi kesim süresi kısa bir milisaniyeden kısa ise bir yürütme segmentine bir seçim çözmek mümkün olmayabilir.  
  
Seçili zaman aralığındaki tüm görünür iş parçacıkları için bir yürütme profili ulaşmak için **yürütme** Göstergedeki sol konumunda.  
  
### <a name="thread-blocking-details"></a>İş parçacığı engelleme ayrıntıları  
Bir iş parçacığı üzerinde belirli bir bölge hakkında bilgi almak için bir araç ipucunu görüntülemek için zaman çizelgesinde o bölgenin üzerine gelin. Araç ipucu, kategori, başlangıç saati ve gecikme gibi bilgileri içerir. Zaman içinde o noktadaki çağrı yığınını görüntülemek için bir bölge seçin **geçerli** alt bölme sekmesi. Bölmesinde kategori, ayrıca gösterir, varsa API engelleme ve varsa, iş parçacığı engellemesinin kaldırılması gecikme. Çağrı yığını inceleyerek, iş parçacığı engelleme olayları temel nedenleri belirleyebilirsiniz.  
  
Bir yürütme yolu birkaç engelleyen olay olabilir. Bu engelleme kategoriye göre inceleyin ve sorun alanlarını daha hızlı bulmak için sol taraftaki Göstergedeki engelleyici bir kategori seçin.  
  
### <a name="dependencies-between-threads"></a>İş parçacıkları arasındaki bağımlılıkları  
Eşzamanlılık görselleştiricisi engellenen bir iş parçacığı yapmak çalışıyordu ve başka bir iş parçacığında hangi yürütmek etkinleştirilmiş belirlemek için iş parçacıkları arasındaki bağımlılıkları gösterir. 

Hangi iş parçacığının başka bir iş parçacığını engellemesini belirlemek için zaman çizelgesi üzerinde engelleme segmentini seçin. Eşzamanlılık görselleştiricisi engellemeyi kaldırma iş parçacığı belirlerseniz engelleme segmentini izleyen yürütülen kesim engellemeyi kaldırma iş parçacığı arasında bir çizgi çizer. Seçin **engellemeyi kaldırma yığını** alt bölmesinde ilgili çağrı yığınını görmek için sekmesinde.  
  
## <a name="profile-reports"></a>Profil raporları 
Zaman çizelgesini içeren bölme grafiğidir **Profil raporu**, **geçerli**, ve **engellemeyi kaldırma yığını** rapor sekmeler. Zaman Çizelgesi ve iş parçacıkları seçimleri değiştirerek raporları otomatik olarak güncelleştirin. Güncelleştirmeleri hesaplanırken büyük izlemeler için raporlar bölmesinde geçici olarak kullanılamıyor olabilir. 

### <a name="profile-report-tab"></a>Profil rapor sekmesi 

**Profil raporu** iki filtreleri:

- Bir filtre değeri 0 ile yüzde 99'arasında çok az zamanın nerede harcandığına çağrı ağacı girişleri filtrelemek için yazın **gürültü azaltma:** alan. 2 yüzde varsayılan değerdir. 
- Yalnızca kodunuzun çağrı ağaçları görüntülemek için seçin **yalnızca kendi kodum** onay kutusu. Tüm çağrı ağaçları görüntülemek için onay kutusunu temizleyin.  

**Profil raporu** sekmesi göstergede raporları kategorileri ve bağlantıları gösterir. Bir raporu görüntülemek için sol taraftaki girişlerden birini seçin:  

- **Yürütme**  
  **Yürütme** rapor yürütme uygulama harcanan sürenin dökümünü gösterir.  
  
  Yürütme saati harcanır kod satırının bulmak için çağrı ağacı genişletin ve çağrı ağacı girdisi için kısayol menüsünden seçin **kaynağı görüntüle** veya **çağrı siteleri görünümünü**. **Kaynak görüntüleme** yürütülen kod satırını bulur. **Çağrı sitelerini görüntüle** yürütülen satırı çağıran kod satırı bulur. Yalnızca bir çağrı sitesini satır varsa, onun kodu vurgulanır. Siteleri birkaç çağırırsanız, mevcut, iletişim kutusunda, istediğiniz ve ardından seçmek **kaynağa Git**. Genellikle en iyi örnek, en çok zaman veya her ikisi de çağrı sitedeki bulunacak en kullanışlı. Daha fazla bilgi için [yürütme Profil raporu](../profiling/execution-profile-report.md).  
  
- **Eşitleme**  
  **Eşitleme** rapor her çağrı yığınının kez engelleme toplam birlikte eşitleme blokları sorumlu olan çağrılarını gösterir. Daha fazla bilgi için [eşitleme zamanı](../profiling/synchronization-time.md).  
  
- **G/Ç**  
  **G/ç** rapor birlikte her çağrı yığınının kez engelleme toplam g/ç blokları sorumlu olan çağrılarını gösterir. Daha fazla bilgi için [g/ç zamanı (iş parçacıkları görünümü)](../profiling/i-o-time-threads-view.md).  
  
- **Uyku**  
  **Uyku** rapor her çağrı yığınının kez engelleme toplam birlikte uyku blokları sorumlu olan çağrılarını gösterir. Daha fazla bilgi için [uyku zaman](../profiling/sleep-time.md).  
  
- **Bellek Yönetimi**  
  **Bellek yönetimi** rapor bellek yönetimi blokları, her bir çağrı yığını sürelerinin engelleme toplam birlikte oluştuğu çağrıları gösterir. Aşırı disk belleği veya çöp toplama sorunlarını olan alanları belirlemek için bu bilgileri kullanın.  Daha fazla bilgi için [bellek yönetimi zamanı](../profiling/memory-management-time.md).  
  
- **Önalım**  
  **Önalım** burada süreçleri sistem üzerindeki geçerli işlem etkisiz ve tek tek iş parçacıkları rapor gösterir, geçerli işlemdeki iş parçacıkları değiştirildi. Önalım için en sorumlu olan iş parçacıkları ve işlemler tanımlamak için bu bilgileri kullanabilirsiniz. Daha fazla bilgi için [Önalım zamanı](../profiling/preemption-time.md).  
  
- **UI işleme**  
  **UI işleme** rapor UI işleme blokları, her bir çağrı yığını sürelerinin engelleme toplam sorumlu olan çağrılarını gösterir. Daha fazla bilgi için [UI işleme zamanı](../profiling/ui-processing-time.md).  
  
- **Her iş parçacığı özeti**  
  Seçin **başına iş parçacığı özeti** seçili zaman aralığı için iş parçacıklarının durumu gösteren bir grafiği görüntülemek için. Renk kodlu sütunları göster toplam zaman harcanan her bir iş parçacığı çalıştırın, engellenmiş, g/ç ve diğer durumlar. İş parçacıkları altındaki etiketlenir. Bu grafik, zaman çizelgesi graftaki yakınlaştırma düzeyi ayarla, otomatik olarak güncelleştirir. 
  
  Bazı yakınlaştırma düzeylerinde bazı iş parçacıkları grafikte göstermeyebilir. Bu durumda, üç nokta simgesini (**...** ) sağ tarafta görüntülenir. İstediğiniz iş parçacığı görünmüyorsa, diğer iş parçacıklarını gizleyebilirsiniz. Daha fazla bilgi için [başına iş parçacığı özet raporu](../profiling/per-thread-summary-report.md).  
  
- **Disk işlemleri**  
  Seçin **Disk işlemleri** süreçleri ve iş parçacıkları için geçerli işlem disk g/ç katılan göstermek için dosyaları bunlar (örneğin, bunlar yüklenen DLL'ler) dokunulan, kaç bayt okurlar ve diğer bilgiler. Özellikle işleminizi miyim/O-bağlı görünüyor zaman harcadığı sürenin erişen dosyaları yürütme sırasında değerlendirmek için bu raporu kullanabilirsiniz. Daha fazla bilgi için [Disk işlemleri raporu](../profiling/disk-operations-report-threads-view.md).  
  
### <a name="current-tab"></a>Geçerli sekme  
Bu sekme, bir iş parçacığı segmentine zaman çizelgesi grafikteki seçili noktası için çağrı yığınını gösterir. Çağrı yığınlarını, uygulamanızla ilgili etkinlik göstermek için atılır.  
  
### <a name="unblocking-stack-tab"></a>Engellemeyi kaldırma yığını sekmesi 
Bu sekme, hangi iş parçacığının, seçilen iş parçacığı ve engellemeyi kaldırma çağrı yığını Engellemesi gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md)
