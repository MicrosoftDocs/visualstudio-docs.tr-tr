---
title: GPU kullanımı | Microsoft Docs
ms.custom: ''
ms.date: 11/01/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8265ae81b5ea1c6395af352f8f981f41f77cea8
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220950"
---
# <a name="gpu-usage"></a>GPU kullanımı

Visual Studio performans ve tanılama hub'ında GPU kullanımı aracı daha iyi Direct3D uygulamanızın üst düzey donanım kullanımını anlayın. Uygulamanızın performansını nasıl platformun donanım daha etkili bir şekilde kullanabileceğinizi bağlanmış CPU veya GPU bağlı ve kazanç Öngörüler olup olmadığını görmenize yardımcı olur. GPU kullanımı Direct3D 12, Direct3D 11 ve Direct3D 10 kullanan uygulamaları destekler. Bunu diğer grafik API'lerinin Direct2D veya OpenGL gibi desteklemiyor.

Bu ekran görüntüsünde gösterilmiştir **GPU kullanım raporu** penceresi:

![GPU kullanımı raporu CPU ve GPU zaman çizelgeleri](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

## <a name="requirements"></a>Gereksinimler

GPU kullanımı aracı kullanmak için aşağıdaki gereksinimleri için grafik tanılama gereksinimleri ekleyin.

- Bir GPU ve sürücü gerekli zamanlama araçları desteği.

  > [!NOTE]
  > Desteklenen donanım ve sürücüler hakkında daha fazla bilgi için bkz. [donanım ve sürücü desteği](#hwsupport) bu belgenin sonunda.

  Grafik tanılama gereksinimleri hakkında daha fazla bilgi için bkz. [Başlarken](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md).

## <a name="using-the-gpu-usage-tool"></a>GPU kullanımı Aracı'nı kullanma

 GPU kullanımı aracı altında uygulamanızı çalıştırdığınızda, Visual Studio gerçek zamanlı olarak bu grafikleri üst düzey bilgileri, uygulamanızın işleme performansını ve GPU kullanımı hakkında tanılama oturumu oluşturur.

**GPU kullanımı aracı başlatmak için:**

1. Ana menüde seçin **hata ayıklama**, ardından **performans ve tanılama** (klavye: Alt + F2 tuşuna basın).

2. Performans ve tanılama hub yanındaki kutuyu işaretleyin **GPU kullanımı**. İsteğe bağlı olarak, ilgilendiğiniz diğer Araçlar'ın yanındaki kutuları işaretleyin. Eşzamanlı olarak uygulamanızın performansını daha kapsamlı bir resmini almak için birkaç performans ve tanılama araçları çalıştırabilirsiniz.

    ![Kullanmak istediğiniz Tanılama Araçları'nı seçin. ](media/gfx_diag_diagsession_tools.png "gfx_diag_diagsession_tools")

   > [!NOTE]
   > Tüm performans ve tanılama araçları, aynı anda kullanılabilir.

3. Mavi seçin **Başlat** seçtiğiniz Araçları altındaki uygulamanızı çalıştırmak için performans ve tanılama hub'ın altındaki düğmesi.

   Çerçeve zamanlama, kare hızı ve GPU kullanımı gerçek zamanlı olarak gösterilen üst düzey bilgileri içerir. Bu bilgilerin her bağımsız olarak grafiği çizilecek, ancak ortak saat ölçek kullanabilir, böylece bunlar arasında kolayca ilişkilendirebilirsiniz.

   **Çerçeve süresi (ms)** ve **kare / saniye (FPS)** grafikleri sahip iki kırmızı, yatay satırları göster performans hedefleyen 60 ve 30 kare / saniye. İçinde **çerçeve süresi** grafik, uygulamanız hedefin performans grafiğin altına satır ve grafik üzerine satır olduğunda hedef isabetsiz okumaları olduğunda. İkinci grafik, grafik üstündeki satırın olduğunda ve grafiğin altına satır olduğunda hedef isabetsiz okumaları tersi--uygulamanıza performans hedef aşıyor başına çerçeveler için. Öncelikle, bu grafiklere uygulamanızın performansı hakkında üst düzey bir fikir edinmek ve GPU kullanımı bir ani değişiklik ya da bir kare hızı ani düşme gibi araştırmak isteyebileceğiniz slow-downs tanımlamak için kullanılır.

   Tanılama oturumu, ayrıca uygulamanızı GPU kullanımı aracı altında çalışırken, GPU üzerinde yürütülen grafik olaylarını hakkında ayrıntılı bilgi toplar. Bu bilgileri, uygulamanızın donanım nasıl kullanacağını daha ayrıntılı bir rapor oluşturmak için kullanılır. Bu rapor toplanan bilgileri oluşturmak için biraz zaman alır çünkü Tanılama oturumu bilgi toplama tamamlandıktan sonra yalnızca kullanılabilir.

   Ne zaman bir performans aramak istediğiniz veya kullanımı daha yakından sorun, raporu oluşturulan performans bilgilerini toplama durdurun.

**GPU kullanımı raporu görüntülemek ve oluşturmak için:**

1. Tanılama oturumu pencerenin alt kısmında seçin **toplamasını Durdur** tuşuna basın veya bağlantı **Durdur** sol üst köşesinde.

   ![GPU ve CPU zamanlama bilgilerini toplayın. ](media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")

2. Raporun üst kısmında, araştırmak istediğiniz sorunu gösteren grafikler birinden bir bölüm seçin. Seçiminizi 3 saniyeye kadar uzun olabilir. daha uzun bölüm başına doğrultusunda kesilir.

   ![POST&#45;koleksiyonu, ayrıntıları görüntülemek için bir aralık seçin](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")

3. Raporun alt kısmında seçin **ayrıntıları görüntüle** bağlantısını **.. Bu aralıktaki GPU kullanım ayrıntılarını görüntülemek için burayı** seçiminizi ayrıntılı bir zaman çizelgesi görüntülenecek ileti.

   ![POST&#45;koleksiyonuyla seçilen aralık](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")

   Bu seçim, raporu içeren yeni bir sekmeli belge açılır. GPU kullanımı raporu, CPU üzerinde bir grafik olay başlatıldığında, GPU ulaştığında ve onu yürütmek için ne kadar GPU geçen görmenize yardımcı olur. Bu bilgiler performans sorunlarını ve kodunuzu artan paralellikteki fırsatları belirlemenize yardımcı olabilir.

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>GPUView ya da Windows Performans Çözümleyicisi dışarı aktarma

Visual Studio 2017'den itibaren bu verilerle açabilirsiniz [GPUView](/windows-hardware/drivers/display/using-gpuview) ve [Windows Performans Çözümleyicisi](/windows-hardware/test/wpt/windows-performance-analyzer). Yalnızca select **Gpuview'da Aç** veya **WPA'da Aç** Tanılama oturumu alt sağ tarafta bulunan bağlantılar.

![Şurada Aç...](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="using-the-gpu-usage-report"></a>GPU kullanımı raporu kullanma

GPU kullanımı raporu üst kısmını zaman çizelgeleri CPU işleme etkinlik, GPU işleme etkinliği ve GPU kopyalama etkinliği için görüntüler. Bu zaman çizelgeleri görüntünün vsync belirtmek açık gri, dikey çubuklar ayrılır. Yenileme hızı görüntüler birinin çubukları sıklığını eşleşir (kullanarak seçili **görünen** açılır), GPU kullanımı verileri toplandığı. Görüntü, uygulamanızın performans hedef değerinden daha yüksek bir yenileme hızı olabileceğinden vsync elde etmek için uygulamanızı istediğiniz kare hızı arasında bir 1-1 ilişkisi olmayabilir. Performans hedefine ulaşmak için bir uygulama gerekir tüm işlemleri tamamlamak, işleme yapmak ve hedeflenen kare hızı Present() çağrı yapmak. Bir kareyi Present() sonra ancak sonraki vsync'e kadar görüntülenmez.

Alt bölümünde, raporun dönem boyunca gerçekleşen grafik olaylarını bir listesini görüntüler.

İşte **GPU kullanım raporu** penceresi:

![GPU kullanımı raporu CPU ve GPU zaman çizelgeleri](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

Raporun alt kısmında bir olay seçtiğinizde, ilgili zaman çizelgesi içinde karşılık gelen olayları bir işaret görünür. Genellikle, başka bir olay GPU zaman çizelgeleri birinde GPU görev tamamlandığında gösterirken CPU iş parçacığı üzerinde bir olay API çağrısı gösterir. Benzer şekilde, bir zaman çizelgesinde bir olay seçtiğinizde, rapor, raporun alt kısmında karşılık gelen olay vurgular. Üst bölümünde rapor zaman çizelgelerini dışında uzaklaştırılacağını, yalnızca en uzun süren olayları görülebilir. Daha kısa bir süre olan olayları görmek için Ctrl + tekerleği, bir işaretleme cihazı veya üst sol alt köşesinde ölçeklendirme denetimi kullanarak zaman çizelgesi yakınlaştırın. Ayrıca, kayıtlı olayları taşımak için zaman çizelgesi bölmenin içeriği sürükleyebilirsiniz.

Aradığınız ne bulmak için işlem adları, iş parçacığı kimlikleri ve olay adı filtresi GPU kullanım raporu temel. Ayrıca, hangi görüntü yenileme hızı vysnc satırları belirler seçebilirsiniz. Uygulamanız kullanıyorsa hiyerarşik olarak olayları sıralamak [ID3DUserDefinedAnnotation](/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) Grup işleme komutları için arabirim.

 Daha fazla ayrıntı aşağıdadır:

|Filtre denetimi|Açıklama|
|--------------------|-----------------|
|**İşlem**|İlgilendiğiniz işlemin adı. Bu açılır menüde GPU Tanılama oturumu sırasında kullanılan tüm işlemler dahildir. Bu açılan işlemi ile ilişkili rengi aşağıdaki zaman çizelgeleri iş parçacığının etkinlik renktir.|
|**iş parçacığı**|İlgilendiğiniz iş parçacığı kimliği. Çok iş parçacıklı bir uygulamada, bu bilgileri, ilgilendiğiniz iş akışına ait belirli bir iş parçacığı ayırmanıza yardımcı olabilir. Seçili iş parçacığıyla ilişkilendirilmiş olayları, her zaman çizelgesinde vurgulanır.|
|**Görüntüleme**|Yenileme hızı görüntülenir görüntüleme sayısını **Not:** bazı sürücüler tek ve büyük sanal bir görüntü birden çok fiziksel görüntüler sunmak için yapılandırılabilir. Makine bağlı birden çok ekran olsa bile, listelenen, yalnızca bir görüntü görebilirsiniz.|
|**Filtre**|İlgilendiğiniz anahtar sözcükler. Raporun alt kısmında olaylar, yalnızca tam veya kısmi bir anahtar sözcükle eşleşen vm'lere yer alır. Birden çok anahtar sözcüklerini noktalı virgülle (;) ayırarak belirtebilirsiniz.|
|**Hiyerarşi sıralama**|Kullanıcı işaretleri--tanımlanan olay hiyerarşilerde--korunur veya göz ardı olduğunu gösteren bir onay kutusu.|

 GPU kullanım raporun alt kısmında olayların listesini her bir olay ayrıntılarını görüntüler.

|Sütun|Açıklama|
|------------|-----------------|
|**Olay adı**|Grafik olay adı. Bir olay, genellikle bir olaya bir zaman çizelgesindeki CPU iş parçacığı ve GPU zaman çizelgesi etkinliğine'karşılık gelir.<br /><br /> GPU kullanımı bir olayın adını belirleyemedi olay adları 'unattributed' olabilir. Daha fazla bilgi için bu tablonun altındaki nota bakın.|
|**CPU başlangıcı (ns)**|Olay CPU üzerinde Direct3D API'sini çağırarak başlatıldığı zaman. Uygulama başlatıldığında göreli zaman nanosaniye cinsinden ölçülür.|
|**GPU başlangıcı (ns)**|Olay GPU üzerinde başlatıldığı zaman. Uygulama başlatıldığında göreli zaman nanosaniye cinsinden ölçülür.|
|**GPU süresi (ns)**|Olay nanosaniye cinsinden GPU üzerinde tamamlanması için geçen süre.|
|**İşlem adı**|Olay içinden gelen uygulamasının adı.|
|**İş parçacığı kimliği**|Olay içinden gelen iş parçacığı kimliği.|

> [!IMPORTANT]
> GPU veya sürücü gereken İzleme özelliklerini desteklemiyorsa, tüm olaylar 'unattributed' görünür. GPU sürücünüzü güncelleştirin ve bu sorunla karşılaşırsanız, yeniden denemek emin olun. Daha fazla bilgi için [donanım ve sürücü desteği](#hwsupport) aşağıda.

## <a name="gpu-usage-settings"></a>GPU kullanım ayarları

GPU kullanımı aracı, uygulama başladıktan hemen sonra bilgi toplamak başlangıç yerine bilgi profil oluşturma koleksiyonu ertelemek için yapılandırabilirsiniz. Profil bilgilerini boyutunu önemli olabileceğinden, bu eylem, uygulamanızın performans yavaşlamalara sonraya görünmez bildiğinizde yararlıdır.

**Uygulama başlangıcından profil oluşturma ertelemek için:**

1. Ana menüde seçin **hata ayıklama**, ardından **performans ve tanılama** (klavye: Alt + F2 tuşuna basın).

2. Performans ve tanılama hub'ı izleyin **ayarları** yanındaki bağlantı **GPU kullanımı**.

3. Altında **GPU profili oluşturma Yapılandırması**, **genel** özellik sayfası, NET **uygulama başlangıcında profil oluşturma başlamak** profil oluşturma ertelemek için onay kutusu.

   ![GPU kullanım verisi toplama başladığında, yapılandırma](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")

> [!IMPORTANT]
> Profil oluşturma erteleme Direct3D 12 uygulamalar için şu anda desteklenmemektedir.

Çalıştırmadan sonra uygulamanızı altında GPU kullanımı aracı, ek bir bağlantı GPU kullanımı aracı penceresinin alt bölümünde kullanılabilir hale gelir. Profil bilgilerini toplamaya başlamak için seçin **Başlat** bağlantısını **başlangıç ek toplama ayrıntılı GPU kullanım verilerini** ileti.

## <a name="hwsupport"></a> Donanım ve sürücü desteği

Aşağıdaki GPU donanım ve sürücüler desteklenir:

|Satıcı|GPU açıklaması|Gerekli sürücü sürümü|
|------------|---------------------|-----------------------------|
|Intel®|4. nesil Intel® Çekirdek işlemcileri ('Haswell')<br /><br /> -Intel® HD grafikleri (GT1)<br />-Intel® HD grafik 4200 (GT2)<br />-Intel® HD grafik 4400 (GT2)<br />-Intel® HD grafik 4600 (GT2)<br />-Intel® HD grafik P4600 (GT2)<br />-Intel® HD grafik P4700 (GT2)<br />-Intel® HD grafik 5000 (GT3)<br />-Intel® Iris™ grafik 5100 (GT3)<br />-Intel® Iris™ Pro grafik 5200 (GT3e)|--(en son sürücüleri kullanan)|
|AMD®|Çoğu beri AMD Radeon™ HD 7000-Serisi (AMD Radeon™ HD 7350 7670 hariç)<br /><br /> AMD Radeon™ GPU, AMD FirePro™ GPU'ları ve AMD FirePro GPU Hızlandırıcısı özelliklerine sahip grafik çekirdek sonraki (GCN) mimarisi.<br /><br /> AMD® E serisi ve AMD A serisi hızlandırılmış işleme grafik çekirdek sonraki (GCN) mimarisi ('Kaveri', 'Kabini', 'Temash', 'Beema', 'Mullins') içeren birim (APUs)|14.7 RC3 veya üzeri|
|NVIDIA®|Çoğu NVIDIA® GeForce 400 serisi itibaren.<br /><br /> NVIDIA® GeForce® GPU'ları, NVIDIA Quadro® GPU'ları ve NVIDIA® Tesla™ GPU Hızlandırıcısı Fermi™, Kepler™ veya Maxwell™ mimarisi özelliklerine sahip.|343.37 veya üzeri|

 Birden çok GPU yapılandırmaları NVIDIA® SLI™ ve AMD Crossfire™ gibi şu anda desteklenmiyor. Karma grafikler Kurulum NVIDIA® Optimus™ ve AMD Enduro™ gibi desteklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Zor olan grafik çözmekte, oyun kullanarak DirectX Araçları (video)](https://channel9.msdn.com/Events/GDC/GDC-2015/Solve-the-Tough-Graphics-Problems-with-your-Game-Using-DirectX-Tools)
- [GPU kullanımı aracı Visual Studio (video)](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/715)
- [GPU kullanımı Aracı'nda Visual Studio 2013 güncelleştirme 4 CTP1 (blog)](https://blogs.msdn.microsoft.com/vcblog/2014/09/04/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1/)
- [(Blog) Visual Studio'da DirectX GPU kullanımı](https://blogs.msdn.microsoft.com/ianhu/2014/12/16/gpu-usage-for-directx-in-visual-studio/)
- [GPUView](/windows-hardware/drivers/display/using-gpuview)
- [Windows Performans Çözümleyicisi](/windows-hardware/test/wpt/windows-performance-analyzer)