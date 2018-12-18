---
title: Grafik çerçevesi analizi | Microsoft Docs
ms.custom: ''
ms.date: 02/09/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.frameanalysis
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0ae541830adab222b07d1f16ce99e4957e380e5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49838107"
---
# <a name="graphics-frame-analysis"></a>Grafik Çerçeve Çözümlemesi
Grafik çerçevesi analizi, çözümlemek ve Direct3D oyunlarda veya uygulamalarda işleme performansını iyileştirmek için Visual Studio grafik Çözümleyicisi'nde kullanın.  

## <a name="frame-analysis"></a>Çerçeve analizi  
 Çerçeve analizi tanılama amacıyla bir grafik günlük dosyasında yakalanır ama bunun yerine işleme performansını özetlemek için kullandığı aynı olan bilgileri kullanır. Performans bilgilerini yakalama sırasında günlüğe kayıtlı değil; Çerçeve kayıttan gibi bunun yerine performans bilgileri daha sonra çerçeve analizi sırasında zamanlama olayları ve toplama istatistiklerini tarafından oluşturulur. Bu yaklaşım, yakalama sırasında performans bilgilerini kaydetme üzerinde çeşitli avantajları vardır:  
  
- Çerçeve analizi sonuçları Özet performans istatistiksel olarak ses olduğundan emin olmak için aynı çerçevenin birden çok her oynatma ortalama.  
  
- Çerçeve analizi, donanım yapılandırmaları ve bilgilerin yakalandığı farklı cihazlar için performans bilgilerini oluşturabilir.  
  
- Çerçeve analizi daha önce yakalanan bilgilerinden yeni performans özetlerini oluşturun — Örneğin, ne zaman GPU sürücüleri iyileştirilmiştir veya ek hata ayıklama özellikleri kullanıma sunar.  
  
  Bu avantajlara ek olarak, çerçeve analizi aynı zamanda bir uygulamanın işleme performansını bu değişiklikleri nasıl etkileyebileceğini hakkında bilgi sunabilir, çerçeve kayıttan yürütme sırasında işlenme için değişiklik yapabilirsiniz. Tümünü uygulayın ve ardından yakalamak ve tüm sonuçlarını karşılaştırın gerek kalmadan olası en iyi duruma getirme stratejileri arasında karar vermek için bu bilgileri kullanabilirsiniz.  
  
  Çerçeve analizi öncelikle işleme daha hızlı performans elde etmenize yardımcı olmak amacıyla hazırlanmıştır olsa da, eşit olarak belirli performans hedefi için daha iyi görsel kaliteyi elde etmek veya GPU güç tüketimini azaltmak yardımcı olur.  
  
  Çerçeve analizi uygulamanız için neler yapabileceğinizi bir örnek görmek için izleyebilirsiniz [Visual Studio grafik çerçevesi analizi](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) Channel 9 video.  
  
## <a name="using-frame-analysis"></a>Çerçeve analizi kullanma  
 Çerçeve analizi kullanabilmeniz için önce çalıştığı bir grafik Çözümleyicisi araçlardan birini kullanırken yaptığınız gibi uygulamanızdan grafik bilgilerini yakalama gerekir. Ardından, grafik günlüğü (.vsglog) belge penceresinde **çerçeve analizi** sekmesi.  
  
 ![Çerçeve analizi sekmesini](media/pix_frame_analysis_select_tab.png "pix_frame_analysis_select_tab")  
  
 Analiz tamamlandıktan sonra sonuçlar görüntülenir. Çerçeve analizi sekmesine üst kısmında Özet Tablo ve zaman çizelgesi görüntüler. Pencerenin en altında ayrıntıları tabloları görüntüler. Kayıttan yürütme sırasında oluşturulan hatalar veya uyarılar, bunlar zaman çizelgesi özetlenmiştir; Buradan, hataları ve Uyarıları hakkında daha fazla bilgi için bağlantıları takip edebilirsiniz.  
  
### <a name="interpreting-results"></a>Sonuçları yorumlayarak destek sağlama  
 Her değişken sonuçları yorumlayarak destek sağlama uygulamanız hakkında yararlı bilgiler performansı ve davranışıyla işleme çıkarabilir. İşleme türevleri hakkında daha fazla bilgi için bkz. [çeşitleri](#Variants) bu makalenin ilerleyen bölümlerinde.  
  
 Bazı sonuçları doğrudan değişken işleme performansını nasıl etkilediğini gösterir:  
  
- Doku çift doğrusal filtreleme değişken performans kazancı elde edildi ise, uygulamanızda filtreleme çeşitleri doku'ı kullanarak benzer performans artışı gösterilir.  
  
- 1 x 1 Görünüm penceresi değişken performans kazancı elde edildi ise, ardından uygulamanıza işleme hedefleri boyutunu küçültmeyi işleme performansını geliştirir.  
  
- BC doku sıkıştırma çeşidi performans kazancı elde edildi ise, sonra da uygulamanızda BC doku sıkıştırma kullanarak benzer performans artışı gösterilir.  
  
- 2xMSAA değişken neredeyse aynı performans 0xMSAA değişken varsa, uygulamanızda performans maliyeti olmadan işleme kalitesini artırmak için 2xMSAA etkinleştirebilirsiniz.  
  
  Diğer sonuçlar, uygulamanızın performansına daha derin, daha hafif etkileri önerebilir:  
  
- 1 x 1 Görünüm penceresi değişken çok yüksek performans artışları gösteriyorsa, uygulamanızın büyük olasılıkla bulunandan daha fazla fillrate tüketiyor. Bu değişken bir performans kazancı elde edildi gösteriyorsa, uygulamanın büyük olasılıkla çok fazla köşe işliyor.  
  
- 16bpp işleme hedef biçim çeşidi önemli ölçüde performans kazanımı gösteriyorsa, uygulamanızın büyük olasılıkla çok fazla bellek bant genişliği tüketiyor.  
  
- Önemli ölçüde performans kazanımı Half/Quarter doku boyutları çeşidi gösterir, dokular, büyük olasılıkla çok fazla bellek kaplayabilir, çok fazla bant genişliği tüketebilir veya doku önbelleğinin kullanamayabilir. Bu değişken performans içinde değişiklik gösteriyorsa, büyük olasılıkla bir performans maliyeti ödeme yapmadan daha büyük, daha ayrıntılı dokular kullanabilirsiniz.  
  
  Donanım sayaçları kullanılabilir olduğunda, uygulamanızın işleme performansını neden yaşıyorsa hakkında çok ayrıntılı bilgi toplamak için kullanabilirsiniz. Tüm özellik düzeyinde 9.2 ve üzeri cihazlar derinliği kapatma sorgularını destekler (**occluded piksel** sayacı) ve zaman damgası. Diğer donanım sayaçları GPU üreticisi ve donanım sayaçları uygulanan bunları sürücüsünü kullanıma bağlı olarak mevcut olabilir. Bu sayaçlar özet tabloda gösterilen sonuçları kesin nedenini onaylamak için kullanabileceğiniz — Örneğin, belirleyebilirsiniz olup overdraw tarafından derinlik testinde occluded piksel yüzdesi inceleyerek bir faktördür.  
  
### <a name="timeline-and-summary-table"></a>Zaman Çizelgesi ve Özet Tablosu  
 Varsayılan olarak, Özet Tablo ve zaman çizelgesi görüntülenir ve diğer bölümleri daraltılır.  
  
#### <a name="timeline"></a>Zaman Çizelgesi  
 Çizim çağrısı zamanlamalara göre başka bir genel bakış zaman çizelgesi gösterir. Daha büyük çubukları için daha uzun çizim süreleri karşılık geldiğinden en pahalı çekme çağrılarını çerçevede hızlıca bulmak için kullanabilirsiniz. Yakalanan çerçeve, çok sayıda çizim çağrıları içerdiğinde, bu toplam uzunluğu çubuğu biridir birden çok çizim çağrıları birleştirilir çağrıları çizin.  
  
 ![Çizim zaman çizelgesini gösterir&#45;maliyetleri çağırın. ](media/pix_frame_analysis_timeline.png "pix_frame_analysis_timeline")  
  
 İşaretçi çubuk karşılık gelen çizim çağrısı olayı görmek için çubuğundaki yaslayabilirsiniz. Çubuğu seçerek, o olaya eşitlemek olay listesi neden olur.  
  
#### <a name="table"></a>Tablo  
 Zaman Çizelgesi altındaki sayılar tablosunun her işleme değişken için her bir çizim çağrısı, uygulamanızın varsayılan işleme göre performanslarını gösterir. Farklı işleme değişken her sütunda görüntülenir ve her satırın en soldaki sütunda tanımlanan bir farklı çizim çağrısını temsil eder; Buradan, bir bağlantı grafik olay Listesi penceresinde olay takip edebilirsiniz.  
  
 ![Özet tablosunu farklı çeşitleri gösterir. ](media/pix_frame_analysis_summary.png "pix_frame_analysis_summary")  
  
 Uygulamanızın temel işleme süresi Özet Tablonun ikinci en soldaki sütuna görüntüler — diğer bir deyişle, bu çizim çağrısı tamamlamak, uygulamanızın varsayılan işleme için geçen süre. Böylece performans geliştirildi olup olmadığını görmek daha kolay olur ve kalan sütunların her işleme değişken göreli performans taban çizgisi yüzdesi olarak gösterir. % 100'den daha büyük yüzde temel uzun sürdü — diğer bir deyişle, performansı düştü — ve yüzde 100'e daha az zaman aldı. daha küçük yüzdeleri — performans oluştu.  
  
 Birden fazla çalıştırma, aslında ortalama ortalamalar değerler hem temel mutlak zamanlamasını hem de işleme çeşitler göreli zamanlamasını — varsayılan olarak 5. Bu ortalama zamanlama verileri güvenilir ve tutarlı olduğundan emin olun yardımcı olur. En düşük incelemek için tablodaki her hücre işaretçiyi tuttuğunuzda, maksimum, ortalama ve sonuçlar için arama ve işleme değişken çizdiğinizde, gözlemlenmedi ORTANCA zamanlama değerlerini oluşturulan. Temel zamanlama de görüntülenir.  
  
#### <a name="hot-draw-calls"></a>"Sıcak" Çizim çağrıları  
 Büyük bir kısmı tüketen çağrıları çizmek için dikkat getirmek için genel işleme süresini veya, önlenmiş, nedenlerden dolayı bu içeren satırı çok yavaş olabilir "Sık erişimli" bir çizim çağrıları olduğunda gölgeli kırmızı kendi temel zamanlama birden fazla Standart sapma ortalama temel zamanlama çerçevesindeki tüm çizim çağrıları daha uzun.  
  
 ![Bu DrawIndexed çağrı sıcak ve soğuk çeşitlemesi vardır. ](media/pix_frame_analysis_hot_calls.png "pix_frame_analysis_hot_calls")  
  
#### <a name="statistical-significance"></a>İstatistiksel önemi  
 Yüksek uygunluğa sahip çeşitlemeleri işleme için dikkat getirmek için çerçeve analizi istatistiksel önemi, her işleme değişken belirler ve önemli olanları kalın olarak görüntüler. Yeşil olarak performansı olanları ve kırmızı olarak performansı düşürebilir olanları gösterir. Bu, normal türü olarak istatistiksel olmayan sonuçlar görüntüler.  
  
 ![Çizim çağrısı değişkeni istatistiksel relevence](media/pix_frame_analysis_summary_stats.png "pix_frame_analysis_summary_stats")  
  
 Çerçeve analizi istatistiksel uygunluğu belirlemek için kullandığı [öğrencinin t-test](http://www.wikipedia.org/wiki/Student%27s_t-test).  
  
### <a name="details-table"></a>Ayrıntıları tablosu  
 Tablo varsayılan olarak daraltılmış olan ayrıntı tablosunda özetidir. Ayrıntı tablosunda içeriğini kayıttan yürütme makinesi donanım platformunda bağlıdır. Desteklenen donanım platformları hakkında daha fazla bilgi için bkz. [donanım desteği](#HardwareSupport).  
  
#### <a name="platforms-that-do-not-support-hardware-counters"></a>Donanım sayaçları desteklemeyen platformları  
 Çoğu platformda donanım GPU sayaçları tam olarak desteklemeyen — bunlar, şu anda Intel, AMD ve NVIDIA tarafından sunulan tüm GPU içerir. Toplamak için donanım sayaç olduğunda, yalnızca bir Ayrıntıları tablosu görüntülenir ve tüm çeşitleri ortalama mutlak zamanlamasını içerir.  
  
 ![Ayrıntı tablosunda ve bazı kayıttan yürütme çeşitleri. ](media/pix_frame_analysis_details.png "pix_frame_analysis_details")  
  
#### <a name="platforms-that-support-hardware-counters"></a>Donanım sayaçları destekleyen platformlar  
 Donanım GPU sayaçları destekleyen platformlar için — örneğin, NVIDIA T40 SOC ve tüm Qualcomm SOC — çeşitli ayrıntıları tabloları görüntülenir, her değişken için bir tane. Her bir kullanılabilir donanım sayaç her işleme değişken için toplanır ve kendi ayrıntıları tabloda görüntülenir.  
  
 ![Donanım sayaçları desteklendiği durumlarda görüntülenir. ](media/pix_frame.png "pix_frame")  
  
 Donanım sayaç bilgileri, performans sorunlarına neden çok kesin olarak belirlemenize yardımcı olabilecek her çizim çağrısı için belirli donanım platformlar davranışı çok ayrıntılı bir görünümünü sağlar.  
  
> [!NOTE]
>  Farklı donanım platformları farklı sayaçları desteği: Standart yoktur. Sayaçlar ve neyi gösterdikleri yalnızca her GPU üreticisi tarafından belirlenir.  
  
### <a name="marker-regions-and-events"></a>İşaret bölgeler ve olaylar  
 Çerçeve analizi, kullanıcı tanımlı olay işaretçileri ve olay gruplarını destekler. Bunlar, Özet tablosunu ve ayrıntı tabloları görüntülenir.  
  
 ID3DUserDefinedAnnotation API'leri ya da eski API'ler D3DPERF_ ailesi işaretçileri ve grupları oluşturmak için kullanabilirsiniz. Çerçeve analizi olay işaretçisi veya olay grubu başlamak/bitiş işaretleri ve bunların içeriğini içeren satırları renkli bir bant görüntüler bir renk D3DPERF_ API ailesi kullandığınızda, her bir işaret ve grup atayabilirsiniz. Bu özellik, önemli işleme olay veya olay gruplarını hızlıca tanımlamanıza yardımcı olabilir.  
  
### <a name="warnings-and-errors"></a>Uyarıları ve hatalar  
 Çerçeve analizi uyarıları veya zaman çizelgesi özetlenen ve çerçeve analizi sekmesine alt kısmında ayrıntılı hatalar, bazen tamamlar.  
  
 Genellikle, uyarılar ve hatalar yalnızca bilgilendirme amaçlıdır ve herhangi bir müdahalesi gerektirmez.  
  
 Uyarılar donanım desteği bulunmaması, ancak geçici bir çözüm kullanarak çalışılabilmesi, donanım sayaçları olamaz toplanacak veya bazı performans verileri güvenilir olmayabilir, genellikle belirtin — örneğin, ne zaman geçici bir çözüm olumsuz etkiler.  
  
 Hataları genellikle çerçeve analizi uygulaması hataya sahip olduğunu, bir sürücü hataya sahip olduğunu, donanım desteği bulunmaması ve geçici olarak çalışan olamaz veya uygulamanın kayıttan yürütme tarafından desteklenmiyor bir şey çalışır olduğunu gösterir.  
  
### <a name="retries"></a>Yeniden deneme sayısı  
 Çerçeve analizi sırasında güç durumu geçiş GPU uğradığında, GPU clockspeed değiştirilmiş ve dolayısıyla göreli zamanlama sonuçları geçersiz olduğundan etkilenen çözümleme geçişi yeniden denenmelidir.  
  
 Çerçeve analizi 10 yeniden deneme sayısını sınırlar. Platformunuza agresif güç yönetimi veya saat geçişi varsa, başarısız ve yeniden deneme sınırı aştığından bir hata rapor çerçeve analizi neden olabilir. Güç Yönetimi, platformun sıfırlayarak bu sorunu gidermek ve platform etkinleştirirse daha az agresiftir olmasını hızı azaltma saat mümkün olabilir.  
  
##  <a name="HardwareSupport"></a> Donanım desteği  
  
### <a name="timestamps-and-occlusion-queries"></a>Zaman damgaları ve kapatma sorguları  
 Zaman damgaları çerçeve analizi destekleyen tüm platformlarda desteklenir. Derinlik kapatma sorguları — piksel Occluded sayaç gerekli —, özellik düzeyi 9.2 veya üzeri destekleyen platformlarında desteklenir.  
  
> [!NOTE]
>  Zaman damgaları çerçeve analizi destekleyen tüm platformlarda desteklenir ancak doğruluğunu ve zaman damgaları tutarlılık platformdan platforma değişir.  
  
### <a name="gpu-counters"></a>GPU sayaçları  
 GPU donanım sayaçları desteği donanım bağlıdır.  
  
 Hiçbir bilgisayar şu anda Intel, AMD veya NVIDIA tarafından sunulan GPU GPU donanım sayaçları güvenilir bir şekilde desteklediğinden, çerçeve analizi bunları sayaçlarını toplamaz. Ancak, çerçeve analizi güvenilir bir şekilde destekleyen aşağıdaki GPU donanım sayaçları toplamak:  
  
- NVIDIA T40 (Tegra4)
  
  Çerçeve analizi destekleyen herhangi bir platform GPU donanım sayaçlarını toplar.  
  
> [!NOTE]
>  GPU donanım sayaçları donanım kaynaklar olduğundan, uygulamanın her işleme değişken için donanım sayaçları kümesinin tamamını toplamak için birden çok geçiş sürebilir. Sonuç olarak, hangi GPU'yu sayaçlar toplanır belirtilmeyen sırasıdır.  
  
## <a name="unsupported-scenarios"></a>Desteklenmeyen senaryolar  
 Çerçeve analizi kullanarak belirli yollar desteklenmeyen ya da kötü bir fikir.  
  
### <a name="playback-of-high-feature-level-captures-on-down-level-devices"></a>Yüksek düzeyli özellik yürütülmesi alt düzey cihazlarda yakalar.  
 Kayıttan yürütme makinesi desteklediğinden daha yüksek bir özellik düzeyi kullanan bir grafik günlük dosyasını kayıttan yürütürken grafik Çözümleyicisi'nde, otomatik olarak geri için WARP döner. Çerçeve analizi, açıkça için WARP dönmesi değil ve bir hata oluşturur — WARP, Direct3D uygulamanızı doğruluğunu İnceleme için ancak performansı inceleniyor değil için kullanışlıdır.  
  
> [!NOTE]
>  Özellik düzeyinde sorunları akılda tutulması gereken önemli olsa da, yakalama ve günlük dosyaları farklı donanım yapılandırmaları ve cihazlarda grafikleri kayıttan yürütme. Grafik günlüğü, günlük dosyası değil veya API'leri içeren kayıttan yürütme makinesinde desteklenmeyen özellik düzeylerini kullanın geri sürece çalınabilir.  
  
### <a name="direct3d-10-and-lower"></a>Direct3D 10 ve daha düşük  
 Uygulamanızı Direct3D 10 API'sini çağırıyorsa, çerçeve analizi tanı veya tanınır ve diğer grafik Çözümleyicisi araçları tarafından kullanılan olsa da bunları profil olmaz.
  
> [!NOTE]
>  Bu, kullanmakta olduğunuz yalnızca Direct3D API çağrıları özellik düzeylerini geçerlidir.

### <a name="warp"></a>EĞRİLTME  
 Çerçeve analizi, profil ve gerçek donanıma işleme performansını geliştirmek için kullanılmak üzere tasarlanmıştır. Çerçeve analizi WARP cihaz üzerinde çalışan engellenmez, ancak genellikle faydalı takip WARP yüksek kaliteli bir CPU üzerinde çalışan daha az özellikli modern Gpu'lar yavaş olduğundan ve WARP performans belirli CPU bağlı olarak büyük ölçüde farklılık gösterebileceğinden değil üzerinde çalıştığı.  
  
##  <a name="Variants"></a> Çeşitleri  
 Çerçeve analizi bir kare, oynatma sırasında işlenir şekilde yaptığı her değişiklik olarak bilinen bir *değişken*. Çerçeve analizi inceler çeşitleri için uygulamanızın görsel kaliteyi ve işleme performansını iyileştirmek için yapabileceğiniz ortak, görece kolay değişiklikler karşılık gelen — örneğin, dokular boyutunu küçültme, doku sıkıştırma kullanmayı veya etkinleştirme Düzgünleştirme farklı türde. Çeşitleri normal işleme bağlamını ve uygulama parametreleri geçersiz. Bir özeti aşağıda verilmiştir:  
  
|Değişken|Açıklama|  
|-------------|-----------------|  
|**1 x 1 Görünüm penceresi boyutu**|Tüm işleme hedeflerde Görünüm penceresi boyutları 1 x 1 piksel azaltır.<br /><br /> Daha fazla bilgi için [1 x 1 Görünüm penceresi boyut çeşidi](1x1-viewport-size-variant.md)|  
|**0x MSAA**|Birden çok örnek düzgünleştirme (MSAA) tüm işleme hedefler üzerinde devre dışı bırakır.<br /><br /> Daha fazla bilgi için [0 x / 2 x / 4 x MSAA çeşitleri](0x-2x-4x-msaa-variants.md)|  
|**2 x MSAA**|Birden çok örnek düzgünleştirme (MSAA) tüm işleme hedeflerde x 2 sağlar.<br /><br /> Daha fazla bilgi için [0 x / 2 x / 4 x MSAA çeşitleri](0x-2x-4x-msaa-variants.md)|  
|**4 x MSAA**|Birden çok örnek düzgünleştirme (MSAA) tüm işleme hedeflerde x 4 sağlar.<br /><br /> Daha fazla bilgi için [0 x / 2 x / 4 x MSAA çeşitleri](0x-2x-4x-msaa-variants.md)|  
|**Noktası doku filtreleme**|Filtre modu ayarlar `DXD11_FILTER_MIN_MAG_MIP_POINT` (doku filtreleme noktası) için tüm uygun dokuyu örnekler.<br /><br /> Daha fazla bilgi için [noktası, ikili Trilinear ve Anizotropik doku filtreleme çeşitleri](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Çeşitleri doku filtreleme**|Filtre modu ayarlar `DXD11_FILTER_MIN_MAG_LINEAR_MIP_POINT` (filtreleme çeşitleri doku) için tüm uygun dokuyu örnekler.<br /><br /> Daha fazla bilgi için [noktası, ikili Trilinear ve Anizotropik doku filtreleme çeşitleri](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Üçlü doku filtreleme**|Filtre modu ayarlar `DXD11_FILTER_MIN_MAG_MIP_LINEAR` (üçlü doku filtreleme) için tüm uygun dokuyu örnekler.<br /><br /> Daha fazla bilgi için [noktası, ikili Trilinear ve Anizotropik doku filtreleme çeşitleri](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Doku anizotropik filtreleme**|Filtre modu ayarlar `DXD11_FILTER_ANISOTROPIC` ve `MaxAnisotropy` için `16` (doku anizotropik filtreleme x 16) için tüm uygun dokuyu örnekler.<br /><br /> Daha fazla bilgi için [noktası, ikili Trilinear ve Anizotropik doku filtreleme çeşitleri](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**16bpp işleme hedef biçim**|Piksel biçimini ayarlar `DXGI_FORMAT_B5G6R5_UNORM` (16bpp 565 biçimi) tüm hedefler ve backbuffers işlemek için.<br /><br /> Daha fazla bilgi için [16bpp işleme hedef biçim değişken](16bpp-render-target-format-variant.md)|  
|**Mip-map oluşturma**|Mip eşlemeleri hedefleri işlenmeyebilir tüm dokular üzerinde sağlar.<br /><br /> Daha fazla bilgi için [Mip-map oluşturma değişken](mip-map-generation-variant.md).|  
|**Yarı doku boyutları**|Doku boyutları işleme hedeflerini kullanıcıların özgün boyutu her boyutundaki yarısını olmayan tüm dokular üzerinde azaltır. Örneğin, 256 x 128 doku için 128 x 64 texel'in azaltılır.<br /><br /> Daha fazla bilgi için [Half/Quarter doku boyutları değişken](half-quarter-texture-dimensions-variant.md).|  
|**Çeyrek doku boyutları**|Doku boyutlarını kullanıcıların özgün boyutu her boyutundaki çeyreği hedeflerini işlenmeyebilir tüm dokular üzerinde azaltır. Örneğin, 256 x 128 doku için 64 x 32 texel'in azaltılır.<br /><br /> Daha fazla bilgi için [Half/Quarter doku boyutları değişken](half-quarter-texture-dimensions-variant.md).|  
|**BC doku sıkıştırma**|Etkinleştirir sıkıştırma B8G8R8X8, B8G8R8A8 veya R8G8B8A8 piksel biçimi değişken tüm dokular hakkında engelleyin. B8G8R8X8 biçimi çeşitleri BC1 kullanarak sıkıştırılır; B8G8R8A8 ve R8G8B8A8 biçimi çeşitleri BC3 kullanarak sıkıştırılır.<br /><br /> Daha fazla bilgi için [BC doku sıkıştırma değişken](bc-texture-compression-variant.md).|  
  
 Çoğu çeşitleri için öngörücü sonucudur: "azalan doku boyutuna göre yarı daha hızlı yüzde 25" veya "Etkinleştirme 2 x MSAA yalnızca 2 yüzde daha yavaş". Daha fazla yorumu diğer çeşitleri gerektirebilir; 1 x 1 Görünüm penceresi boyutları değişiklikleri değişken büyük performans kazancı gösterir, örneğin, işleme göre düşük doldurma oranı; performansı düşürdüğünü gösterir olmadığını olduğunu gösterebilir Alternatif olarak, performansı önemli bir değişiklik varsa, işleme göre köşe işleme performansı düşürdüğünü gösterir emin olduğunu gösterebilir.