---
title: Animasyonlar
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b74a283a4142cea7753db6e04d922517ae32afe9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052099"
---
# <a name="animations-for-visual-studio"></a>Visual Studio için animasyonları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="animation-fundamentals"></a>Animasyonu ile ilgili temel bilgiler

### <a name="animation-best-practices-in-visual-studio"></a>Visual Studio'da animasyon en iyi uygulamalar
 Visual Studio IDE arasında tutarlı ve kullanımı kolay animasyon stilleri emin olmak için bu kuralları izleyin.

-   **Seçici olun.** Belirli bir amaca hizmet eder bu animasyonları sınırlayın.

-   **Zamanlama ve hızını önemli** geçişleri hızlı ve doğal düşünüyorsanız emin olmak için:

    -   Animasyonlu geçişler yarım saniye (500 milisaniye cinsinden) içinde tamamlayın.

    -   Sık oluşacak animasyonları kullanıcının iş akışı kesintiye yoksa yeterince hızlı olması gerekir.

    -   Bu nedenle hızlı veya jarring anlaşılması zor ancak değil çok yavaş bir geçişi tamamlamak için sabırsız kolaylaştırır, olduğunu animasyonları olmamalıdır.

    -   Değişken zamanlama önem vurgulamak için kullanın. Örneğin, bir sınıf diyagramında öğelerinin bir dizisini aracılığıyla gittiğinizde, öğeleri arasında geçişler hızlandırmak sonra önemli öğeye odaklanmayı yavaşlayabilir.

-   **Aşamalı doğrusal olmayan hızlandırma kullanın** diğerine bir durumdan diğerine taşıma sakin ve doğal bir fikir veren

-   Mümkün olduğunda, **üzerine gelindiğinde zarif bir animasyon kullanın** fare altında etkileşimli öğeleri göstermek için.

-   Yoğun animasyonları, özellikleri ardından güveniyorsanız **kapatmak için bir yol sağlar** yerel olarak (için tüm özelliklerinizi) bir seçenek olarak **Araçlar > Seçenekler** iletişim.

-   **Yalnızca bir animasyon teker teker gerçekleşmesi** ve iletmek yalnızca bir bilgi parçasıdır.

-   **Subtlety büyük/küçük harf önemlidir.** Çoğu durumda, amaca hizmet için isteğe bağlı kullanıcı dikkat animasyon sahip değil. Zamanlama, sıralama ve davranışı hafif değişiklikler perception önemli ölçüde etkileyebilir ve maliyetli ve verimsiz bir animasyon arasındaki fark yaratabilir.

-   Animasyon bir şey, dikkat çekmek için kullanırken **kullanıcı kesintiye değer olduğundan emin olun**'s düşünce eğitin.

-   **İlerleme veya durum gösterilirken** animasyon aracılığıyla:

    -   Temel alınan işlem değil ilerletmektedir olduğunda ilerleme taşıma gösteren durdurun.

    -   Belirsiz işlemleri kararlı işlemlerden ayırmak.

    -   Bir animasyon tanımlanabilen tamamlama ve hata durumları olduğundan emin olun.

    -   Durumu göster ve gerçek kullanımı için ek bilgi sağlayarak gerçek değeri olduğundan emin olun etkisi animasyonları kullanımını en aza indirin. Örnekler arasında geçici durum değişikliklerini ve acil durumlar bulunur

#### <a name="do-not"></a>Yapma:

- Küçük hareketleri (küçük ayak izine hareket) kullanın, belgelemeyi ve belirerek nesneleri taşınmadan değiştirir.

- Büyük bir alanı ekran gerçek boyutunuzu gerçekleşmesi animasyonları kullanın. Boyutundan bağımsız olarak, bu stil animasyonun dikkat kullanıcıya dağıtıyor.

- Kullanıcı şu anda odaklanmıştır nesne veya ile etkileşim kurma ile ilgili olmayan animasyon kullanın.

- Yanıp Durdur sağlamak için bir yanıp sönen bildirime yanıt vermek için kullanıcı zorlama gibi durumunu sıfırlamak için kullanıcı etkileşimi gerektiren animasyonları kullanın. Herhangi bir yolla normalde bunları kapatmak yeterli olmalıdır.

  Bu en iyi uygulamalar hakkında daha fazla bilgi için bkz. [animasyon desenleri](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Animasyon ölçümleri

-   Sistem görünüşte 10 milisaniyeden kısa kullanıcı hareketleri tepki.

-   Animasyonlu Geçişi tamamlamak için 500 milisaniyeden uzun sürmesi gerekir.

-   Daha uzun süreleri gerektiren geçişleri için telafi yollarından biri, iki bölüme ayırın sağlamaktır; Örneğin, bir animasyon ilk bölümü tarafından içerik Soluklaşan kapsayıcıya (en fazla 500 milisaniye cinsinden) ardından boş içerik kapsayıcı (en fazla 500 milisaniye cinsinden) olabilir.

-   Hesaplanabilir yükleme süreleri için determinant İlerleme göstergesi (ilerleme yüzdesi bitti göstergesi) tercih edilir.

-   İmleç veya katıştırılmış dönen animasyon (yükleme veya çalışma göstergesi) gibi bir meşgul göstergesi hesaplanamaz yükleme süreleri için uygundur.

### <a name="animation-as-communicator"></a>Animasyon communicator olarak
 Visual Studio kullanıcı Arabiriminde animasyon yalnızca bir iletişim aracı çalışır.  Kullanıcı arabiriminde yapısal değişiklikler gibi bilgileri çeşitli iletişim kurmak için kullanılır; Örneğin, ne zaman bir menü açar veya kapatır. Animasyon, yükleme ilerleme durumunu görselleştirme gibi karmaşık sistemleri zamana bağımlı davranışını görselleştirmenize yardımcı olabilir veya uyarılar ve bildirimler ile dikkat çekmek için kullanılabilir.

 UI animasyonları, genellikle dört şekilde işlev: görselleştirin, dikkat çekmek, benzetimini gerçekleştirmek ve yanıt belirtmek kez/ilerleme durumu.

#### <a name="visualize"></a>Görselleştirin
 Animasyon, üç boyutlu nesneler yapısını vurgulamak ve kullanıcıların, uzamsal yapılarını görselleştirmek kolaylaştırır. Bunu başarmak için animasyon dolu bir daire nesneyi döndürme için yavaş geri ve İleri etkinleştirmek veya nesne yakın getirin ve biraz geçişi veya odağı vurgulamak için boyutunu artırın.

 Üç boyutlu nesneler kullanıcı denetimi ile Tasarımcı önceden (program aracılığıyla veya el ile) belirlemelisiniz taşınmış olabilir ancak nasıl en iyi nesneyi en iyi bir anlayış sağlayan bir taşıma animasyon ekleme. Bu, animasyon can programlanmış sonra kullanıcı, nesneyi işlemek nasıl anlamak kullanıcı tarafından denetlenen hareketleri gerektirdiğinde kullanıcı tarafından nesnenin üzerine imleci yerleştirerek etkinleştirilmesi. Tek bir eksen ya da aynı anda yönünü taşıma sınırı; ya da ölçeklendirin, döndürme, veya Çevir, ancak aynı anda birden fazla desteklemez.

 Veri ilişkileri, durumu, yönlerini Görselleştir kategorisi içerir yapısı, dizisi ve saat.

##### <a name="data"></a>Veri
 Karmaşık ve değişken bilgilerini göstermektedir:

-   Grafikler gibi görselleştirmelerin bilgi üstünden geçme

-   Bir dizi Adımlama, Kılavuzlu Tur ve disk belleği

-   Ayrıntılarını çağırma işaret eden ve belirli bilgileri vurgulama

-   Ayrıntılar ve ek bilgiler üzerine odaklanan öğeyi planlamanızda

-   Bir yapısal ya da kuruluş gösterimden diğerine morfingu prvku.

-   Değişiklikleri temsil eden saat kaydırıcılar, koşu shuttle tekerlekleri ve Aktarım denetimleri (Yürüt, durdurma ve duraklatma) kullanarak zaman içinde.

##### <a name="relationships"></a>İlişkiler

-   Öğeleri birbirleriyle nasıl ilişki kuracağını veya belirli bir öğe için hangi öğeleri arasında ilişki gösterilmektedir.

-   Hiyerarşileri ve üst-alt veya eşdüzey ilişkilerini Göster

-   Başka bir öğe olarak çoğaltılır

-   Bir öğe başka bir öğeye en aza indirir.

-   Bir öğe diğerine tethered tamamen

##### <a name="state"></a>Durum

-   İçerik güncelleştirmeleri.

-   Kullanıcı odak ve seçimi

-   İlerleme durumu

-   Hatalar

##### <a name="structure"></a>Yapı

-   Bir düğümde yapısı özetleme

-   Reorienting

-   En aza indirmek ve en üst düzeye çıkarmak, veya genişletme ve daraltma

##### <a name="sequence"></a>Dizisi

-   Slayt gösterisi dizisi

-   Resimleri çevirme

##### <a name="time"></a>Zaman

-   Zaman zaman lapse ve yayını değişimini Göster

-   Çöp, Geri Al ve Yinele Taşı

-   Geçmiş durumuna

#### <a name="attract-attention"></a>Dikkatini
 Hedef birkaç dışında tek bir öğe için kullanıcının dikkat çekmek veya güncelleştirilmiş bilgileri için kullanıcıyı uyarmak için ise, bir animasyon uygun olabilir. Örneğin, uygulama başlangıç sayfanızı Başlarken Sayfa yüklendikten sonra yere slaytları bir düğme kullanmak istemiyorsunuz.

 Bir kural olarak, son taşınan öğeyi ekranda kullanıcının dikkatini çektiğini.  Animasyonlu öğelerin sıralı, kullanıcının dikkatini son hareket eden nesnenin izler.

##### <a name="alert"></a>Uyarı

-   Kullanıcıyı uyarmak, dikkatini, ilerleme durumunu gösterir

-   Bir şey doğru veya yanlış yapıldığını gösterir veya ilerleme durumunu veya ilerlemesini değişiklikleri göster

-   Çevrimiçi daha fazla bilgi bulmak veya geçerli görevle ilgili öğrenme gibi bir görev sırasında kullanıcılara sor

##### <a name="notifications"></a>Bildirimler

-   Kullanıcı bir hata durumu hakkında uyar

-   Bunlar başka bir şeye katılmayı isteyip istemediğinizi görmek için kullanıcının kesme

-   Bir işlem tamamlanmış veya değiştirilen, bir yükleme tamamlandığında gibi kullanıcı yavaşça bildirin.

#### <a name="simulate"></a>Benzetimi
 Bu kategori, physicality ve işlenemez kapsar.

-   Nesnelerin nereden geldiğini veya bunlar için nereye gösterilmektedir.

-   Genişlet ve Daralt veya açın ve Kapat

-   Yatay kaydırma ve sayfası açar

-   Yığın ve z-sıralamasıyla

-   Döngüsü ve accordion

-   Çevirme ve döndürme kullanıcı Arabirimi

#### <a name="response-and-progress-indicators"></a>Yanıt ve ilerleme göstergeleri
 İlerleme göstergesi, birkaç önemli avantajları vardır:

-   Her iki kararlı ve belirsiz ilerleme göstergeleri sistem değil kilitlendi ve bu sorun üzerinde çalıştığı kullanıcı reassure.

-   Kararlı göstergeleri bir güvenliymiş bitiş tarihine yakın almanın yanı sıra bir fikir ne kadar eylem boyunca İlerliyor kullanıcıya sağlayın.

##  <a name="BKMK_AnimationPatterns"></a> Animasyon desenleri

### <a name="overview"></a>Genel Bakış
 Visual Studio içinde animasyon belirli bir işlev sunmak ve kullanıcı üretkenliğini azaltabilir değil yöneliktir. Eklenecek uyması genel animasyon özellikleri:

- Küçük ve örtük

- Doğal ve gerçekçi

- İnce ve subdued

- Hızlı ve verimli

- Esnek, hurried değil

  Aşağıdaki çizim Visual Studio'da kullanmak için önerilen animasyon stilleri gösterir. Gibi hiçbir animasyon ve ince animasyon belirerek / silinme en sık kullanılan. Animasyonları gibi genişletin ve sözleşme hareketin sınırlı bir uygulama, değiştirme ve Döndürme X ve Y konumu.

  ![Visual Studio için önerilen animasyon stiller](../../extensibility/ux-guidelines/media/1202-a-vsanimstyles.png "1202 a_VSAnimStyles")

  **Visual Studio için önerilen animasyon stilleri**

#### <a name="appear-and-disappear"></a>Görünür ve kaybolur
 Bu düzen ile bir öğe görülemediğinden görünüme giden ve geri geçiş animasyon olmadan geçer:

 ![Görünür&#47;Visual Studio'daki animasyon kayboluyor](../../extensibility/ux-guidelines/media/1202-b-appearanddisappear.png "1202 b_AppearAndDisappear")

##### <a name="correct-usage"></a>Doğru kullanımı
 Yeni kullanıcı Arabirimi öğeleri, böylece kullanıcı dikkatinizin obstructed ne kaybolur veya anında görünür gerekir. Ayrıca, yavaş hareketli animasyonların görünmesi ve görünmez olur stiliyle gerçekleşmeyeceğini bir performans Sürükle olarak algılanabilir.

##### <a name="incorrect-usage"></a>Yanlış kullanımı
 Çalışmalarını ne kadar aniden hiçbir fikriniz kullanıcının kullanıcı Arabirimi görüntülenir ve bir animasyon ekleme ile bağlamsal anlamak yardımcı olur.

##### <a name="animation-properties"></a>Animasyon özellikleri
 Gecikme süresi genellikle sıfır saniyedir.

##### <a name="examples"></a>Örnekler

-   Araç pencereleri otomatik gizleme

-   Klavye etkinleştirilmiş Düzenleyicisi IntelliSense ve parametre Yardımı gibi kullanıcı Arabirimi

-   Genişletme ve daraltma kod bölgeleri

#### <a name="fade-in-and-fade-out"></a>Belirme ve fade-out
 Bu desen ile UI öğesi görünür değil (opaklığı % 0) geçişleri görünür (% 100 opaklık) ya da tam tersi:

 ![Soldurma&#45;içinde&#47;Soldurma&#45;animasyon Visual Studio'da kullanıma](../../extensibility/ux-guidelines/media/1202-c-fadeinfadeout.png "1202 c_FadeInFadeOut")

##### <a name="correct-usage"></a>Doğru kullanımı
 Bu, en sık UI animasyon önerilir. İlgi akışını kesintiye uğratmadan ekler zarif bir etkisidir. Bazı durumlarda, kullanıcı bile, bir animasyon ve yalnızca bir kesintisiz akışı sağlama kullanıcı Arabirimi sistemi algılar farkında değil.

##### <a name="animation-properties"></a>Animasyon özellikleri

-   Opaklık başlatılıyor: % belirme için 0, %100 fade-out için

-   Opaklık bitiş: %100 belirme için %0 fade-out için

-   Süresi: 200 milisaniye cinsinden tek başına, bir birleşimi animasyon dizisinin bir parçası kullanıldığında 100 milisaniye

-   Stil hızlandırma: sinüs Inout

##### <a name="examples"></a>Örnekler

-   Araç pencereleri otomatik gizleme

-   Menü Aç ve Kapat

-   Arka plan ve ön plan sekmesine geçiş

#### <a name="color-blend-from-a-to-b"></a>Renk blend'e a B
 Bu desen ile rengi bir UI öğesi, b rengine değiştirir.

 ![Renk animasyon Visual Studio'da blend](../../extensibility/ux-guidelines/media/1202-d-colorblend.png "1202 d_ColorBlend")

##### <a name="correct-usage"></a>Doğru kullanımı
 Bir kullanıcı Arabirimi öğesi rengi bir içerik veya durumu diğerine değiştiğinde bir animasyonlu geçişi.

##### <a name="animation-properties"></a>Animasyon özellikleri

-   Başlangıç rengi: özel kullanıcı Arabirimi

-   Bitiş rengi: özel kullanıcı Arabirimi

-   Süresi: 200 milisaniye cinsinden tek başına, bir birleşimi animasyon dizisinin bir parçası kullanıldığında 100 milisaniye

-   Stil hızlandırma: sinüs Inout

##### <a name="examples"></a>Örnekler

-   Belge penceresi durumu geçişleri (etkin ve etkin ve etkin olmayan en son)

-   Araç penceresi durumu geçişleri (odaklı ve plana odaklanmadan)

#### <a name="expand-and-contract"></a>Genişlet ve Daralt
 Bu desen ile X, Y veya her iki yönde de kullanıcı Arabirimi öğesi genişletir:

 ![Genişletin&#47;sözleşme animasyon Visual Studio'da](../../extensibility/ux-guidelines/media/1202-e-expandcontract.png "1202 e_ExpandContract")

##### <a name="correct-usage"></a>Doğru kullanımı
 Bir kullanıcı Arabirimi öğesi boyutu bir bağlamdan diğerine değiştiğinde bir animasyonlu geçişi.

##### <a name="animation-properties"></a>Animasyon özellikleri

-   Ölçek x: % veya belirli boyutu (piksel cinsinden)

-   Y Ölçek: % veya belirli boyutu (piksel cinsinden)

-   Bağlantı konumu: genellikle (sağdan sola diller için) sol veya sağ üst köşede (için sağdan sola diller)

-   Süresi: 200 milisaniye cinsinden tek başına, bir birleşimi animasyon dizisinin bir parçası kullanıldığında 100 milisaniye

##### <a name="examples"></a>Örnekler

-   Mimari Gezgini paneli genişletme ve daraltma

-   Başlangıç sayfası öğesi genişletme ve daraltma

#### <a name="x-y-position-change"></a>X-Y Konum Değiştir
 Bu düzende, X veya Y konumunu veya her ikisini de UI öğesi değiştirir:

 ![X&#47;Y konumunu değiştir animasyon Visual Studio'da](../../extensibility/ux-guidelines/media/1202-f-xypositionchange.png "1202 f_XYPositionChange")

##### <a name="correct-usage"></a>Doğru kullanımı
 Bir kullanıcı Arabirimi öğesi konumu bir bağlamdan diğerine değiştiğinde bir animasyonlu geçişi olarak.

##### <a name="animation-properties"></a>Animasyon özellikleri

-   Başlangıç X ve Y konumu: özel kullanıcı Arabirimi

-   Bitiş X ve Y konumu: özel kullanıcı Arabirimi

-   Hareket yolu: yok

-   Süresi: 200 milisaniye cinsinden tek başına, bir birleşimi animasyon dizisinin bir parçası kullanıldığında 100 milisaniye

-   Stil hızlandırma: sinüs Inout

##### <a name="example"></a>Örnek
 Sekme yeniden sıralama

#### <a name="rotate"></a>Döndür
 Bu düzende, kullanıcı Arabirimi öğesi döndürür:

 ![Visual Studio'da animasyon döndürme](../../extensibility/ux-guidelines/media/1202-g-rotate.png "1202 g_Rotate")

##### <a name="correct-usage"></a>Doğru kullanımı
 Yalnızca belirsiz dönen İlerleme göstergesi için.

##### <a name="animation-properties"></a>Animasyon özellikleri

-   Dönüş derecesini: 360

-   Dönüş Merkezi: nesnenin orta

-   Süre: sürekli

##### <a name="example"></a>Örnek
 Belirsiz İlerleme göstergesi (dönen)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Ortak Kabuk UI eylemlerini ve önerilen animasyonları

#### <a name="tab-open"></a>Açık sekmesi

- Stil: görüntülenir

- Süre: Sıfır saniye

  ![Visual Studio'da Aç animasyon sekmesinde](../../extensibility/ux-guidelines/media/1202-h-tabopen.png "1202 h_TabOpen")

#### <a name="tab-close"></a>Sekmesini kapatın

- Stil: X konumunu değiştir

- Süre: 200 milisaniye olarak

  ![Visual Studio'da Kapat animasyon sekmesinde](../../extensibility/ux-guidelines/media/1202-i-tabclose.png "1202 i_TabClose")

#### <a name="tab-reorder"></a>Sekme yeniden sıralama

- Stil: X konumunu değiştir

- Süre: 200 milisaniye olarak

  ![Visual Studio'da yeniden düzenleme animasyon sekmesinde](../../extensibility/ux-guidelines/media/1202-j-tabreorder.png "1202 j_TabReorder")

#### <a name="close-floating-document"></a>Kayan belgeyi Kapat

- Stil: görüntülenir

- Süre: 200 milisaniye olarak

  ![Visual Studio'da belge animasyon kayan Kapat](../../extensibility/ux-guidelines/media/1202-k-closefloatingdocument.png "1202 k_CloseFloatingDocument")

#### <a name="window-state-transition"></a>Pencere durum geçişi

- Stil: diğer windows ile tutarlı olması için belgeyi Kapat animasyon tanımlayın geçerli işletim sistemi sağlar.

- Süre: 200 milisaniye olarak

  ![Visual Studio'da pencere durum geçişi animasyon](../../extensibility/ux-guidelines/media/1202-l-windowstatetransition.png "1202 l_WindowStateTransition")

#### <a name="menu-open"></a>Menü Aç

- Stil: belirme

- Süre: 200 milisaniye olarak

  ![Visual Studio'da menü açık animasyon](../../extensibility/ux-guidelines/media/1202-m-menuopen.png "1202 m_MenuOpen")

#### <a name="menu-close"></a>Menüsünü Kapat

- Stil: Fade-out

- Süre: 200 milisaniye olarak

  ![Visual Studio'da menü Kapat animasyon](../../extensibility/ux-guidelines/media/1202-n-menuclose.png "1202 n_MenuClose")

#### <a name="auto-hide-tool-window-reveal"></a>Otomatik gizleme araç penceresini göster

- Stil: görüntülenir

- Süre: Sıfır saniye

  ![Otomatik&#45;Visual Studio'da araç penceresi animasyon Gizle](../../extensibility/ux-guidelines/media/1202-o-autohidetoolwindowreveal.png "1202 o_AutoHideToolWindowReveal")
