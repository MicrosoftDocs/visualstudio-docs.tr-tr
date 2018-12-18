---
title: Gelişmiş Ayarlar iletişim kutusu (eşzamanlılık görselleştiricisi) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.settings
ms.assetid: bb3d90aa-5f08-4953-9be0-be6cea11633d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 60f4a038056d326cfb184cc3bb6876c411263ca1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884010"
---
# <a name="advanced-settings-dialog-box-concurrency-visualizer"></a>Gelişmiş Ayarlar iletişim kutusu (eşzamanlılık görselleştiricisi)
Kullanarak **Gelişmiş ayarlar** iletişim kutusu eşzamanlılık görselleştiricisi içinde nasıl izlemeleri toplanır denetleyebilirsiniz.  İletişim kutusu, semboller, yalnızca kendi kodum, arabelleğe alma, filtreleme, CLR olayları, işaretçileri, sağlayıcıları ve dosyalar için sekme bulunur.  
  
## <a name="symbols"></a>Simgeleri  
 Eşzamanlılık görselleştiricisi Visual Studio hata ayıklayıcı sembol ayarlarının aynısını kullanır. Eşzamanlılık görselleştiricisi, performans verileri ile ilişkili olan çağrı yığınlarını çözümlemek için ayarları kullanır.  İzlemeleri işlediğinde, Concurrency Visualizer Ayarları sayfasında belirtilen sembol sunucuları erişir.  Bu verileri ağ üzerinden erişildiğinde izleme işleme yavaşlar.  Sembolleri çözümlemek için gereken süreyi azaltmak için semboller yerel olarak önbelleğe alabilir. Semboller karşıdan yüklediyseniz, Visual Studio bunları yerel önbellekten yüklenir.  
  
## <a name="just-my-code"></a>Yalnızca Kendi Kodum  
 Varsayılan olarak, yalnızca kendi kodum kümesidir. *exe* ve. *dll* geçerli çözümde Visual Studio ile ilişkili olan dosyaları. Çağrı yığınlarını filtrelemek için yalnızca kendi kodum özelliğini kullandığınızda bu dosya kümesini eşzamanlılık görselleştiricisi değerlendirir. Yalnızca kendi kodum sekmesinde içeren dizinleri ekleyebilirsiniz. *exe* ve. *dll* dosyaları konumlara eşzamanlılık görselleştiricisi için sadece benim kodumu kullanır.  
  
 Yolları. *exe* ve. *dll* dosyaları izleme toplandığında izleme dosyasında saklanır.  Bu ayarı değiştirmeden önce toplanan tüm izlemeleri etkilemez.  
  
## <a name="buffering"></a>arabelleğe alma  
 Eşzamanlılık görselleştiricisi izlemesi topladığı olay izleme için Windows (ETW) kullanır.  ETW olaylarını depolayan çeşitli arabellekler kullanır.  Varsayılan ETW arabellek ayarlarını tüm durumlarda ve bazı durumlarda uygun olmayabilir, kayıp olayları gibi sorunlara neden olabilir.  Arabelleği sekmesi, ETW arabellek ayarlarını yapılandırmak için kullanabilirsiniz. Daha fazla bilgi için [olay izleme](http://go.microsoft.com/fwlink/?LinkId=234579) ve [EVENT_TRACE_PROPERTIES yapısı](http://go.microsoft.com/fwlink/?LinkId=234580).  
  
## <a name="filter"></a>Filtrele  
 Filtre sekmesinde eşzamanlılık görselleştiricisi toplayan olay kümesini seçebilirsiniz. Olayların bir alt seçme raporlarında görüntülenir, her izleme boyutunu azaltır ve izlemeler işlemek için gereken süreyi kısaltır veri türlerini kısıtlar.  
  
### <a name="clr-events"></a>CLR olayları  
 Ortak dil çalışma zamanı (CLR) tarafından oluşturulan olayları yönetilen çağrı yığınları çözmek eşzamanlılık görselleştiricisi etkinleştirin.  CLR olayları toplamayı devre dışı bırakırsanız, izleme boyutu sınırlı, ancak bazı çağrı yığınlarını çözmeyecek.  Sonuç olarak, bazı CPU iş parçacığı etkinliği yanlış kategorilere.  
  
### <a name="collect-for-native-processes"></a>Yerel işlemler için TOPLA  
 Yönetilen bir işlem yalnızca profili yerel işlemler için normal gereksiz olduğundan, varsayılan olarak, CLR olayları toplanır.  Bazı durumlarda (örneğin, yerel bir işlem, CLR barındırma) için yerel işlem CLR olayları toplamak gerekebilir.  Bu durumda, seçin **yerel işlemler için TOPLA** onay kutusu.  
  
### <a name="disable-rundown-events"></a>Azaltma olaylarını devre dışı bırak  
 CLR olayları iki sağlayıcılarını oluşturur: çalışma zamanı ve özeti.  İsterseniz CLR çalışma zamanı olayları toplamak için ancak azaltma olaylarını toplama engellemek istiyorsanız, seçin **devre dışı Özet olayları** onay kutusu.  Bu toplama işlemi tarafından oluşturulan izleme dosyasının boyutunu azaltır, ancak bazı yığınları çözümlenmiyor. Daha fazla bilgi için [CLR ETW sağlayıcılar](/dotnet/framework/performance/clr-etw-providers)  
  
### <a name="sample-events"></a>Örnek olaylar  
 Örnek olaylar, iş parçacığı yürütme ile ilişkili olan çağrı yığınlarını Topla için kullanabilirsiniz. Bu olaylar, yaklaşık bir kez geçerli işlemde çalışan iş parçacıkları için milisaniye başına toplanır. Örnek olaylar koleksiyonunu devre dışı bırakırsanız, toplanan izlemenin boyutunu azalır, ancak iş parçacığı yürütme ile ilişkili olan herhangi bir çağrı yığınlarını görüntüleyemezsiniz.  
  
### <a name="gpu-events"></a>GPU olayları  
 GPU, DirectX tarafından oluşturulan olayları olaylardır. GPU olayları toplamayı devre dışı bırakırsanız, toplanan izlemenin boyutunu azalır, ancak herhangi bir GPU etkinliği kullanım görünümü ya da DirectX altyapısı etkinliği iş parçacıkları Görünümü'nde görüntüleyemezsiniz.  
  
### <a name="file-io-events"></a>Dosya g/ç olayları  
 Dosya g/ç olayları diske geçerli işlem adına erişim temsil eder.  Dosya g/ç olayları devre dışı bırakırsanız, izleme boyutunu azalır, ancak iş parçacıkları görünümü disk kanalları ya da Disk işlemleri bilgileri bildirmez.  
  
## <a name="markers"></a>İşaretçileri  
 Üzerinde **işaretçileri** sekmesi, Concurrency Visualizer işaretleyici olarak gösterilen ETW sağlayıcıları kümesini yapılandırabilirsiniz.  Ayrıca, işaret koleksiyonu önem düzeyini ve ETW kategoriye göre filtreleyebilirsiniz.  Kullanıyorsanız [eşzamanlılık görselleştiricisi SDK'si](../profiling/concurrency-visualizer-sdk.md) ve böylece iş parçacıkları Görünümü'nde göründüğü kendi işaretleyici Sağlayıcısı'nı kullanarak, burada kaydedebilirsiniz.  
  
### <a name="add-a-new-provider"></a>Yeni Sağlayıcı Ekle  
 Kodunuzu kullanıyorsa [eşzamanlılık görselleştiricisi SDK'si](../profiling/concurrency-visualizer-sdk.md) veya izleyen ETW olaylarını oluşturur <xref:System.Diagnostics.Tracing.EventSource> kural, görüntüleyebilirsiniz bu olayları eşzamanlılık görselleştiricisi içinde bu iletişim kutusunda kaydederek.  
  
 İçinde **adı** sağlayıcı tarafından oluşturulan olayları türlerini tanımlayan bir ad girin.  İçinde **GUID** bu sağlayıcıyla ilişkili GUID girin. (Bir GUID her ETW sağlayıcısı ile ilişkilidir.)  
  
 İsteğe bağlı olarak, kategori veya önem düzeyini temel alan, bu sağlayıcı olayları filtrelemek belirtebilirsiniz.  Kategori kullanabileceğiniz tabanlı eşzamanlılık görselleştiricisi SDK'si kategorilerine göre filtrelemek için alan.  Bunu yapmak için kategoriler virgülle ayrılmış bir dize veya kategoriden aralıklarını girin.  Bu olayların kategorilerini göstermek için geçerli sağlayıcıyı belirtir.  Ekliyorsanız bir <xref:System.Diagnostics.Tracing.EventSource> sağlayıcısı ETW anahtar sözcüğe göre filtrelemek için alan kullanabilirsiniz.  Anahtar sözcüğü bir bit maskesi olduğundan, hangi bit maskesi kümesini belirlemek için virgülle ayrılmış bir tamsayılar dizisi kullanabilirsiniz. Örneğin, "1,2" birinci ve ikinci bitlerini ayarlar ve bu 6 ondalık dönüşür.  
  
 Önem düzeyi listenin bir önem veya belirtilen değer'dan küçük ETW düzeyine sahip olayları filtrelemek için kullanabilirsiniz.  
  
### <a name="configure-an-existing-provider"></a>Mevcut bir sağlayıcı yapılandırın  
 Mevcut bir sağlayıcı ile ilişkili ayarları düzenlemek için listeden seçin ve ardından **düzenleme sağlayıcısı** düğmesi.  Ad, GUID ve filtreleme ayarlarını değiştirebilirsiniz.  
  
### <a name="filter-marker-data-out-of-concurrency-visualizer-reports"></a>Eşzamanlılık görselleştiricisi raporları dışında işaret verileri filtreleme  
 Belirli bir sağlayıcı, gelecekte izlemeleri görünmesi için veri istemiyorsanız, kaldırmak istediğiniz sağlayıcıyı yanındaki onay kutusunu temizleyin.  
  
## <a name="files"></a>Dosyalar  
 Üzerinde **dosyaları** sekmesinde, bir izleme depolanan her seferinde hangi izleme dosyalar dizine toplanır belirtebilirsiniz.  Eşzamanlılık görselleştiricisi topladığı her izleme için dört dosya üretir:  
  
- Bir çekirdek modu olay izleme günlüğü (ETL) dosyası (<em>.</em> Kernel.etl*)  
  
- Bir kullanıcı modu olay izleme günlüğü dosyası (<em>.</em> User.etl*)  
  
- Eşzamanlılık görselleştiricisi verisi dosyası (<em>.</em> CVData*)  
  
- Eşzamanlılık görselleştiricisi izlemesi dosyası (<em>.</em> CVTrace*)  
  
  İki ETL Ham izleme verileri depolamak ve iki eşzamanlılık görselleştiricisi dosyaları işlenen verileri depolayın.  Bir izleme işlendikten sonra ham ETL dosyaları genellikle kullanılmaz.  Seçme **Sil olay izleme günlüğü (ETL) dosyalarını çözümleme sonrasında** onay kutusunu, diskte depolanan izleme veri miktarını azaltır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Yalnızca kendi kodum](../profiling/just-my-code-threads-view.md)   
 [Eşzamanlılık görselleştiricisi işaretleyicileri](../profiling/concurrency-visualizer-markers.md)