---
title: İş Parçacıkları görünümü (paralel performans) | Microsoft Docs
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
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39457684ba19ecbb0ad2ef82caa349e67cdaf8a7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756334"
---
# <a name="threads-view-parallel-performance"></a>İş Parçacıkları Görünümü (Paralel Performans)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İş Parçacıkları görünümü eşzamanlılık görselleştiricisi en ayrıntılı ve zengin özellikli Görünüm ' dir. Bu görünümü kullanarak, iş parçacığı yürütme veya eşitleme, g/ç veya diğer herhangi bir nedenden dolayı engelleme olup olmadığını belirleyebilirsiniz.  
  
 Profil analiz sırasında tüm işletim sistemi bağlam anahtar olayları için her bir uygulama iş parçacığı eşzamanlılık görselleştiricisi inceler. Bağlam anahtarları, bunlar gibi birçok nedenden dolayı ortaya çıkabilir:  
  
- Bir iş parçacığı eşitleme temel nesne üzerinde engellenir.  
  
- İş parçacığı kuantum süresi dolar.  
  
- Bir iş parçacığı, engelleyici bir g/ç isteği yapar.  
  
  Bir iş parçacığı yürütme durdurulduğunda iş parçacıkları görünümü her içerik anahtarı için bir kategoriye atar. Kategorileri gösterge görünümü sol alt kısmında gösterilir. Eşzamanlılık görselleştiricisi, iş parçacığı çağrı yığınını iyi bilinen engelleme API'leri için arama yaparak içerik değiştirme olayları kategorilere ayırır. Çağrı yığını eşleşme, tarafından sağlanan bekleme nedeni yoksa [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] kullanılır. Ancak, [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] kategorisi üzerinde bir uygulama ayrıntısı temel olabilir ve kullanıcı amacı yansıtmayabilir. Örneğin, [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] yerel ince Okuyucu-Yazıcı kilit g/ç olarak eşitleme yerine engellemek için bekleme nedeni bildirir. Çoğu durumda, içerik anahtarı olayları için karşılık gelen çağrı yığınlarını inceleyerek engelleyen bir olayı kök nedenini tanımlayabilirsiniz.  
  
  İş Parçacıkları görünümü ayrıca iş parçacıkları arasındaki bağımlılıkları gösterir. Örneğin, bir eşitleme nesnesi üzerinde engellenen bir iş parçacığı olduğunu belirlerseniz, onu engeli kaldırılmış iş parçacığı için bakabilirsiniz ve diğerinde engellemesini zaman noktasında iş parçacığı için çağrı yığınında etkinlik inceleyebilirsiniz.  
  
  İş parçacığı çalıştırırken, Concurrency Visualizer örnekleri toplar. İş Parçacıkları görünümü'nde, hangi kod tarafından bir veya daha fazla iş parçacığı bir yürütme kesimi sırasında yürütülür analiz edebilirsiniz. Ayrıca, raporlar ve engelleme çağrı yığını ağacı yürütme profil raporları da inceleyebilirsiniz.  
  
## <a name="usage"></a>Kullanım  
 İş Parçacıkları görünümü kullanabileceğiniz bazı yollar şunlardır:  
  
-   Kullanıcı Arabirimi (UI) bir uygulamanın belirli yürütme aşamaları sırasında yanıt vermiyor neden nedeniyle belirleyin.  
  
-   Eşitleme, g/ç, sayfa hataları ve diğer olayları engelleme harcadığı süre miktarını belirleyin.  
  
-   Sistemde yürütülen diğer işlemleri girişime derecesini tanımlayın.  
  
-   Paralel yürütme için Yük Dengeleme sorunları belirleyin.  
  
-   (Daha mantıksal çekirdekler kullanılabilir olduğunda, paralel bir uygulaması performansını iyileştirmez nedeni) yetersiz ya da yok ölçeklenebilirlik nedenlerini belirleyin.  
  
-   Uygulamasındaki paralelleştirme, yardımcı olmak için eşzamanlılık derecesini anlayın.  
  
-   Çalışan iş parçacıkları ve kritik yürütme yollarına arasında bağımlılıklar anlayın.  
  
## <a name="examining-specific-time-intervals-and-threads"></a>Belirli zaman aralıkları ve iş parçacığı İnceleme  
 İş Parçacıkları görünümü zaman çizelgesi gösterir. Yakınlaştırma ve kaydırma belirli aralıklarla ve uygulamanızın iş parçacıklarını incelemek için zaman çizelgesi içinde. X ekseninde zaman ve y ekseninde çeşitli kanallar:  
  
- Sistem, bir kanalı için okuma ve yazma işlemleri için bir tane her disk için iki g/ç kanal.  
  
- İşlemdeki her iş parçacığı için bir kanal.  
  
- İzlemede işaret olayları olup olmadığına işaret kanalları. İşaret kanalları, başlangıçta bu olayları oluşturan iş parçacığı kanalları altında görünür.  
  
- GPU kanalları.  
  
  İş Parçacıkları görünümü bir gösterimi aşağıda verilmiştir:  
  
  ![İş Parçacıkları görünümü](../profiling/media/threadsviewnarrowing.png "ThreadsViewNarrowing")  
  İş Parçacıkları Görünümü  
  
  Başlangıçta, böylece ana uygulama iş parçacığının ilk iş parçacıkları, oluşturuldukları sıraya göre sıralanır. İş parçacıkları (örneğin, çoğu yürütme çalışma tarafından) başka bir ölçüte göre sıralamak için görünümünün sol üst köşedeki sıralama seçeneği kullanabilirsiniz.  
  
  Sol sütun adlarını seçme ve ardından çalışma yapmadığınız bir iş parçacığı gizleyebilirsiniz **Seçili iş parçacıklarını Gizle** araç çubuğunda. Kendi istatistikleri ilgisi olmayan ve raporları clog çünkü tamamen engellenen iş parçacıklarının Gizle öneririz.  
  
  Ek iş parçacıklarının, etkin göstergede Gizle tanımlamak için kullanılacak **başına iş parçacığı özeti** rapor **Profil raporu** sekmesi. Bu, seçili zaman aralığı için iş parçacığı durumunu gösteren yürütülme dökümünü grafiği görüntüler. Bazı yakınlaştırma düzeylerinde bazı iş parçacıkları görüntülenmeyebilir. Böyle bir durumda elipsler sağ tarafta görüntülenir.  
  
  Zamanı ve bazı iş parçacıkları bir aralık içinde seçtikten sonra Performans Analizi başlayabilirsiniz.  
  
## <a name="analysis-tools"></a>Analiz Araçları  
 Bu bölümde, raporlar ve diğer analiz araçları açıklanmaktadır.  
  
### <a name="thread-blocking-details"></a>İş parçacığı engelleme ayrıntıları  
 Bir iş parçacığı üzerinde belirli bir bölgede engelleyen bir olayı hakkında bilgi almak için bir araç ipucunu görüntülemek için bu bölge işaretçisini. Varsa bu kategori, bölge başlangıç zamanı, engelleme süresi ve engelleme API gibi bilgileri içerir. Engelleme Bölgesi'ni seçin, yığın zaman içinde o noktadaki araç ipucunda görüntülenen bilgilerin birlikte alt bölmesinde görüntülenir. Çağrı yığını inceleyerek, iş parçacığı engelleme olayı temel nedeni belirleyebilirsiniz. Segment seçme ve geçerli sekme İnceleme ek işlem ve iş parçacığı bilgisi bulabilirsiniz.  
  
 Birden çok engelleme olayı yürütme yolu olabilir. Sorunlu alanları daha hızlı bulabilmeniz için bunlar engelleyen kategoriye göre inceleyebilirsiniz. Yalnızca engelleme kategorilerden birini Göstergeyi Solda seçin.  
  
### <a name="dependencies-between-threads"></a>İş parçacıkları arasındaki bağımlılıkları  
 Engellenen bir iş parçacığı yapmak ve öğrenmek edebiliyordum belirleyebilirsiniz eşzamanlılık görselleştiricisi işleminizi iş parçacıkları arasındaki bağımlılıkları gösterebilirsiniz hangi başka bir iş parçacığında yürütmek etkinleştirilmiş. Hangi iş parçacığının başka bir iş parçacığını engellemesini belirlemek için ilgili engelleme segmentini seçin. Eşzamanlılık görselleştiricisi engellemeyi kaldırma iş parçacığı belirlerseniz engelleme segmentini izleyen yürütülen kesim engellemeyi kaldırma iş parçacığı arasında bir çizgi çizer. Ayrıca, **Unblocking yığın** sekmesi ilgili çağrı yığınını gösterir.  
  
### <a name="thread-execution-details"></a>İş parçacığı yürütme ayrıntıları  
 İş parçacığı zaman çizelgesi grafikte, kodun ne zaman yürütülmekte olan yeşil segmentlerini gösterir. Yürütme bölütü hakkında daha ayrıntılı bilgi edinebilirsiniz.  
  
 Bir yürütme Segmentte bir nokta seçtiğinizde, eşzamanlılık görselleştiricisi ilgili çağrı yığınında saat için o noktadan arar ve ardından seçili belirli noktaya yukarıda siyah şapka işareti yürütme kesimdeki görüntüler ve çağrı yığınını görüntüler  **Geçerli yığın** sekmesi. Birden çok yürütme kesim noktalarını seçebilirsiniz.  
  
> [!NOTE]
>  Eşzamanlılık görselleştiricisi yürütme segmentine bir seçim çözmek mümkün olmayabilir. Genellikle, kesim süresi kısa bir milisaniyeden kısa olduğunda bu gerçekleşir.  
  
 Tüm Seçili zaman aralığında (görünür) iş parçacığı etkinleştirilmiş bir yürütme profili almak için seçtiğiniz **yürütme** düğmesi etkin göstergesi.  
  
### <a name="timeline-graph"></a>Zaman Çizelgesi grafiği  
 Zaman Çizelgesi grafiği işlemini ve tüm fiziksel disk cihazlarının ana bilgisayarda tüm iş parçacıklarının etkinliğini gösterir. Ayrıca GPU etkinliği ve işaret olayları görüntüler.  Daha fazla ayrıntı görüntülemek ya da daha uzun bir zaman aralığını görüntülemek için çıkış için yakınlaştırabilirsiniz. Kategoriler, başlangıç saati, süreleri ve çağrı yığını durumları hakkında bilgi almak için grafikteki noktaları belirleyebilirsiniz.  
  
 Zaman Çizelgesi grafikte bir renk belirli bir anda bir iş parçacığı durumunu gösterir. Örneğin, yeşil segmentleri yürütme kırmızı segmentleri eşitlemede engellendi sarı segmentleri etkisiz ve mor segmentleri cihaz g/ç bağlı. Bu görünüm, paralel bir döngüden veya eş zamanlı görevleri katılan iş parçacıkları arasında iş bakiyesini incelemek için kullanabilirsiniz. Bir iş parçacığı diğerlerine göre daha uzun zaman alıyorsa, iş dengesiz olabilir. İş parçacıkları arasında daha eşit dağıtarak programınızın performansını artırmak için bu bilgileri kullanabilirsiniz.  
  
 Yalnızca tek bir iş parçacığı yeşil (zamanda bir noktada Yürütülüyor), uygulama tam anlamıyla eşzamanlılık sistemde sürüyor değil. Zaman Çizelgesi grafiği engelleme arasındaki geçici ilişkiyi iş parçacıkları arasındaki bağımlılıkları incelemek için kullanabileceğiniz ve engellenen iş parçacıkları. İş parçacığı yeniden düzenlemek için bir iş parçacığı seçin ve araç çubuğunda yukarı veya aşağı. İş parçacıkları gizlemek için bunları seçin ve ardından **iş parçacıklarını Gizle** düğmesi.  
  
### <a name="profile-reports"></a>Profil raporları  
 Zaman Çizelgesi bir zaman çizelgesi profili ve çeşitli raporlar için Sekmeler içeren bir bölme grafiğidir. Raporları, iş parçacıkları görünümü değiştikçe otomatik olarak güncelleştirilir. Güncelleştirmeleri hesaplanırken raporları bölmesi büyük izlemeler için kullanılamayabilir. Her raporda iki filtre ayarlamalar vardır: gürültü azaltma ve yalnızca kendi kodum. Çağrı ağacı girişleri nerede biraz zaman harcandığını filtrelemek için gürültü azaltma kullanın. Varsayılan filtre değeri 2 yüzde olmakla birlikte yüzde 0 ' 99 yüzde olarak ayarlayabilirsiniz. Yalnızca çağrı ağacı, kodunuzda görüntülemek için seçin **yalnızca kendi kodum** onay kutusu. Tüm çağrı ağaçları görüntülemek için onay kutusunu temizleyin.  
  
#### <a name="profile-report"></a>Profil raporu  
 Bu sekme, etkin göstergesi girişlere karşılık gelen raporlar gösterir. Bir raporu görüntülemek için girişlerden birini seçin.  
  
#### <a name="current-stack"></a>Geçerli yığın  
 Bu sekme, bir iş parçacığı segmentine zaman çizelgesi grafikteki seçili noktası için çağrı yığınını gösterir. Çağrı yığınlarını, programınız için ilgili etkinlik göstermek için atılır.  
  
#### <a name="unblocking-stack"></a>Yığın Engellemesini Kaldırma  
 Hangi iş parçacığının Seçili iş parçacığını engellemesini bakın ve hangi kod satırında **Unblocking yığın** sekmesi.  
  
#### <a name="execution"></a>Yürütme  
 Yürütme rapor yürütme uygulama harcanan sürenin dökümünü gösterir.  
  
 Yürütme saati harcanır kod satırının bulmak için çağrı ağacı genişletin ve ardından çağrı ağacında giriş için kısayol menüsünden seçin **kaynağı görüntüle** veya **çağrı siteleri görünümünü**. **Kaynak görüntüleme** yürütülen kod satırını bulur. **Çağrı sitelerini görüntüle** yürütülen kod satırının çağıran kod satırı bulur. Yalnızca bir çağrı sitesi varsa, kendi kod satırı vurgulanır. Birden çok çağrı siteleri varsa, görünür ve sonra iletişim kutusunda istediğiniz seçebileceğiniz **kaynağa Git** çağrı site kodu vurgulamak için düğme. Genellikle en iyi örnek, en çok zaman veya her ikisi de çağrı sitedeki bulunacak en kullanışlı. Daha fazla bilgi için [yürütme Profil raporu](../profiling/execution-profile-report.md).  
  
#### <a name="synchronization"></a>Eşitleme  
 Eşitleme rapor eşitleme blokları, her bir çağrı yığını sürelerinin engelleme toplama sorumlu olan çağrılarını gösterir. Daha fazla bilgi için [eşitleme zamanı](../profiling/synchronization-time.md).  
  
#### <a name="io"></a>G/Ç  
 G/ç rapor g/ç blokları, her bir çağrı yığını sürelerinin engelleme toplama sorumlu olan çağrılarını gösterir. Daha fazla bilgi için [g/ç zamanı (iş parçacıkları görünümü)](../profiling/i-o-time-threads-view.md).  
  
#### <a name="sleep"></a>Uyku  
 Uyku rapor uyku blokları, her bir çağrı yığını sürelerinin engelleme toplama sorumlu olan çağrılarını gösterir. Daha fazla bilgi için [uyku zaman](../profiling/sleep-time.md).  
  
#### <a name="memory-management"></a>Bellek Yönetimi  
 Bellek yönetimi raporu, bellek yönetimi blokları, her bir çağrı yığını sürelerinin engelleme toplama birlikte oluştuğu çağrıları gösterir. Aşırı disk belleği veya çöp toplama sorunlarını olan alanları belirlemek için bu bilgileri kullanabilirsiniz.  Daha fazla bilgi için [bellek yönetimi zamanı](../profiling/memory-management-time.md).  
  
#### <a name="preemption"></a>Önalım  
 Önalım raporu, işlemler sistem üzerindeki geçerli işlem ve geçerli işlemdeki iş parçacıkları yerine tek tek iş parçacığı burada etkisiz örnekleri gösterir. Önalım için en sorumlu olan iş parçacıkları ve işlemler tanımlamak için bu bilgileri kullanabilirsiniz. Daha fazla bilgi için [Önalım zamanı](../profiling/preemption-time.md).  
  
#### <a name="ui-processing"></a>UI işleme  
 UI işleme rapor blokları, her bir çağrı yığını sürelerinin engelleme toplama birlikte işleme için kullanıcı Arabirimi sorumlu olan çağrılarını gösterir. Daha fazla bilgi için [UI işleme zamanı](../profiling/ui-processing-time.md).  
  
#### <a name="per-thread-summary"></a>Her iş parçacığı özeti  
 Bu sekme bir renk kodlu sütun görünümü toplam süreyi her iş parçacığı çalıştırmasında harcanan, g/ç ve diğer Devletler engellenen gösterir. Sütunları altındaki etiketlenir. Bu sekme, zaman çizelgesi graftaki yakınlaştırma düzeyi ayarla, otomatik olarak güncelleştirilir. Bazı yakınlaştırma düzeylerinde bazı iş parçacıkları görüntülenmeyebilir. Böyle bir durumda elipsler sağ tarafta görüntülenir. İstediğiniz iş parçacığı görünmüyorsa, diğer iş parçacıklarını gizleyebilirsiniz. Daha fazla bilgi için [başına iş parçacığı özet raporu](../profiling/per-thread-summary-report.md).  
  
#### <a name="disk-operations"></a>Disk işlemleri  
 Bu sekme, hangi işlemlerin gösterir ve iş parçacıkları disk g/ç bunlar (örneğin, yüklenen DLL'ler) dokunulan, hangi dosyaların kaç bayt okundu, geçerli işlem ve diğer bilgileri adına söz konusu. Özellikle işleminizi g/ç gibi görünüyor, dosyaları yürütme sırasında erişirken geçen zamanın değerlendirmek için bu raporu kullanabilirsiniz. Daha fazla bilgi için [Disk işlemleri raporu](../profiling/disk-operations-report-threads-view.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md)



