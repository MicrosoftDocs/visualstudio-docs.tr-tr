---
title: Visual Studio için animasyonları | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f28e4d6f9ae1a0af060723047621b3e205d012c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148944"
---
# <a name="animations-for-visual-studio"></a>Visual Studio için animasyonları
## <a name="animation-fundamentals"></a>Animasyon temelleri  
  
### <a name="animation-best-practices-in-visual-studio"></a>Visual Studio'da animasyon en iyi uygulamalar  
Visual Studio IDE arasında tutarlı ve kullanıcı dostu animasyon stilleri sağlamak için bu kurallar izleyin.  
  
-   **Seçici olun.** Belirli bir amaca hizmet eder o animasyonları sınırlayın.  
  
-   **Zamanlama ve hız önemli** geçişleri hızlı ve doğal eşitleyerek emin olmak için:  
  
    -   Animasyonlu geçişler yarım saniye (500 milisaniye) içinde tamamlayın.  
  
    -   Sık oluşacak animasyonları kullanıcının iş akışı kesintiye yok yeterince hızlı olması gerekir. Animasyon döngü izlemek ve sağ hissi kadar zamanlamasını ayarlayın. 
  
    -   Animasyon, böylece hızlı veya jarring anlaşılması zor ancak değil çok yavaş bir geçişi tamamlamak için sabırsız kolaylaştırır, olduğunu olmamalıdır.  
  
    -   Değişken zamanlama önem vurgulamak için kullanın. Örneğin, bir sınıf diyagramında öğelerinin bir dizisini gezinme, öğeleri arasında geçişler hızlandırmak ardından önemli öğeye odaklanmayı yavaşlayabilir.  
  
-   **Aşamalı doğrusal olmayan kolaylaştırma kullanmak** diğerine bir durumdan diğerine sakin ve doğal hareket duygusu vermiş.  
  
-   Mümkün olduğunda, **gidildiğinde zarif bir animasyon kullanın** fare altında etkileşimli öğeleri göstermek için.  
  
-   Yoğun animasyonları özelliklerinizi, ardından kullanır, **bunları devre dışı bırakmak için bir yol sağlar** yerel olarak (için tüm özelliklerinizi) bir seçenek olarak **Araçlar > Seçenekler** iletişim.  
  
-   **Aynı anda yalnızca bir animasyon gerçekleşmelidir** ve yalnızca bir bilgi parçasını taşır. Taşıma veya birden çok şey iletmek çalışırken birden fazla nesne kafa karıştırıcı olabilir. 
  
-   **Subtlety önemlidir.** Çoğu durumda, animasyon amacı sunmak için isteğe bağlı kullanıcı dikkat sahip değil. Zamanlama, sıralama ve davranış ince değişiklikler algısına önemli ölçüde etkileyebilir ve etkili ve etkisiz animasyonun arasındaki fark yaratabilir.  
  
-   Animasyon dikkat çekmek için bir şey, kullanırken **kullanıcı kesintiye değerinde olduğundan emin olun**'s düşünce eğitimi.  
  
-   **İlerleme veya durum gösterilirken** animasyon aracılığıyla:  
  
    -   Temel alınan işlem zaman ilerledikten değil ilerleme taşıma gösteren durdurun. 
  
    -   Belirsiz işlemleri belirli işlemlerini ayırt.  
  
    -   Bir animasyon tanımlanabilen tamamlama ve hata durumları olduğundan emin olun.  
  
    -   Durumu gösteren ve gerçek kullanımını ek bilgileri sağlayarak gerçek değer olduğundan emin olun etkisi animasyonları kullanımını en aza indirin. Geçici durum değişikliklerini ve acil durumlar örnekler  
  
#### <a name="animation-donts"></a>Animasyon yapılmaması gerekenler:
  
-   Küçük hareketleri (küçük bir yer hareket) kullanmayın. Silinmeleri tercih ve nesneleri taşıma değiştirir.  
  
-   Büyük bir ekran Gayrimenkul alanı üzerinde gerçekleşmesi animasyonları kullanmayın. Boyutundan bağımsız olarak, bu stili animasyonun kullanıcıya dağıtıyor.  
  
-   Kullanıcı şu anda odaklanmıştır nesne ilişkisiz veya etkileşimde animasyonları kullanmayın.  
  
-   Gibi kullanıcıya, onu yanıp durdurmak için yanıp sönen bir bildirime yanıt vermek zorlama durumu, sıfırlamak için kullanıcı etkileşimi gerektiren bir animasyon kullanmayın. Bunları herhangi bir şekilde etkileşim bunları kapatmak yeterli olmalıdır.  
  
Bu en iyi uygulamaları uygulamalar hakkında daha fazla bilgi için bkz: [animasyon desenleri](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).  
  
### <a name="animation-metrics"></a>Animasyon ölçümleri  
  
-   Sistem görünür şekilde 10 milisaniyeden kısa kullanıcı hareketleri tepki.  
  
-   Animasyonlu geçişler tamamlamak için 500 milisaniye uzun sürer döndürmemelidir.  
  
-   Uzun sürelerle gerektiren geçişleri dengelemek için bir iki parçalarına ayırmak için yoludur. Örneğin, bir animasyon ilk kısmı (en fazla 500 milisaniye) kapsayıcıya içerik Soluklaşan tarafından izlenen boş içerik kapsayıcı (en fazla 500 milisaniye) olabilir.  
  
-   Hesaplanabilir yükleme süreleri için determinant İlerleme göstergesi (yüzde bitti İlerleme göstergesi) tercih edilir.  
  
-   İmleç veya katıştırılmış dönen animasyon (yükleme veya çalışma göstergesi) gibi meşgul bir göstergesi hesaplanamaz yükleme süreleri için uygundur.  
  
### <a name="animation-as-communicator"></a>Animasyon communicator olarak  
Visual STUDİO'da animasyon yalnızca bir iletişim aracı işlev görür.  Bu bilgi, yapısal değişiklikler kullanıcı arabiriminde (örneğin, bir menüsü açtığında veya kapatır) gibi çeşitli iletişim kurmak için kullanılır. Animasyon, yükleme ilerleme durumu görselleştirme gibi karmaşık sistemlerinin zamana bağımlı davranışını görselleştirmenize yardımcı olabilir. Animasyon, uyarılar ve bildirimler ile dikkat çekmek için de kullanılabilir.  
  
 UI animasyonları genellikle dört yolla çalışabilmesi: Görselleştirme, dikkat çekmek, benzetimini yapmak, ve yanıt sürelerini/İlerleme göstergesi.  
  
#### <a name="visualize"></a>Görselleştirme  
Animasyon nesneleri üç boyutlu yapısını vurgulamak ve kullanıcıların kendi uzamsal yapısı görselleştirmek kolaylaştırır. Bunu başarmak için animasyon dolu daire nesnesinde dönmeye yavaş geri ve İleri kapatma veya nesneyi yakın getirin ve biraz rollover veya odak vurgulamak için boyutunu artırın.  
  
Üç boyutlu nesneler kullanıcı denetimi ile Tasarımcı önceden (programlı olarak veya el ile) belirlemelisiniz taşınmış olabilir ancak nasıl en iyi nesne en iyi anlaşılmasını sağlayan bir taşıma animasyon. Bu animasyon can programlanmış sonra kullanıcı tarafından denetlenen hareketleri nesnesi öğrenmek kullanıcının gerektiren ancak kullanıcı tarafından nesnenin üzerine imleci koyarak etkinleştirilmesi. Sınır tek eksen veya aynı anda yönünü taşımayı; ya da ölçeklendirme, döndürme, veya Çevir, ancak aynı anda birden fazla desteklemez.  
  
Veri ilişkileri, durumu, yönlerini Görselleştir kategorisi içerir yapısı, dizisi ve saat.  
  
##### <a name="data"></a>Veri  
Karmaşık ve değişken bilgileri gösterir:  
  
-   Grafikler ve grafikler gibi bilgileri görselleştirmeleri üstünden geçme  
  
-   Bir dizi atlama, Kılavuzlu Tur ve disk belleği  
  
-   Ayrıntılarını çağrılırken, işaret eden ve belirli bilgileri vurgulama  
  
-   Ayrıntılar ve ek bilgiler odaklanılan öğeyi üstünde üst üste getirme
  
-   Başka bir yapısal ya da kuruluş gösteriminden dönüştüğü  
  
-   Değişiklikleri temsil eden saat kaydırıcılar, dokunmatik shuttle tekerlekleri ve Aktarım denetimleri (play, durdurma ve duraklatma) kullanarak zamanla 
  
##### <a name="relationships"></a>İlişkiler  
  
-   Nasıl öğeleri birbirleriyle ya da belirli bir öğe için hangi öğeleri arasında ilişki gösterilmektedir
  
-   Hiyerarşileri ve üst-alt veya eşdüzey ilişkileri göster
  
-   Bir öğe başka olarak çoğaltılır.
  
-   Bir öğe başka bir öğeye en aza indirir.
  
-   Başka bir Internet paylaşımlı bir öğe
  
##### <a name="state"></a>Durum  
  
-   İçerik güncelleştirmeleri
  
-   Kullanıcı odak ve seçimi  
  
-   İlerleme durumu  
  
-   Hatalar  
  
##### <a name="structure"></a>Yapı  
  
-   Bir düğüm üzerindeki yapısı özetleme  
  
-   Reorienting  
  
-   En aza indirmek ve en üst düzeye çıkarmak, veya genişletme ve daraltma  
  
##### <a name="sequence"></a>Sırası  
  
-   Slayt gösterisi sırası  
  
-   Resimleri döndürme  
  
##### <a name="time"></a>Zaman  
  
-   Saat, saat lapse ve ekran kaydı üzerinden göster değiştir  
  
-   Çöp kutusu, geri alma ve yineleme gitme  
  
-   Geçmiş durumunu geri yükle  
  
#### <a name="attract-attention"></a>Dikkat çekmek  
Hedef tek bir öğeye birkaç dışında kullanıcının dikkat çekmek veya güncelleştirilmiş bilgileri kullanıcıyı uyarmak için ise, bir animasyon uygun olabilir. Örneğin, uygulama başlangıç sayfası, Sayfa yüklendikten sonra yerine slayt Başlarken düğme uygulamadığınız.  
  
Bir kural olarak, son taşınan öğesi ekranında kullanıcının dikkatini konuşmanızdaki.  Animasyonlu öğeleri serisinde kullanıcının dikkatini son taşıma nesne izler.  
  
##### <a name="alert"></a>Uyarı  
  
-   Kullanıcıyı uyarmak, dikkatini, ilerlemesini Göster  
  
-   Bir şey doğru veya yanlış yapıldığını göster veya ilerleme durumunu veya ilerleme değişiklikleri göster  
  
-   Daha fazla çevrimiçi bilgi bulma veya geçerli görevle ilgili öğrenme gibi bir görev sırasında kullanıcılara sor  
  
##### <a name="notifications"></a>Bildirimler  
  
-   Kullanıcı bir hata durumu hakkında uyarı  
  
-   Bunlar başka bir şey için katılmak isteyip istemediğinizi görmek için kullanıcı kesme  
  
-   Hafifçe bir işlem tamamlandı kullanıcı bildirmek veya değiştirilen, bir yükleme tamamlandığında, ister.  
  
#### <a name="simulate"></a>Benzetimi  
Bu kategori physicality ve boyut kapsar.  
  
-   Nesneleri alınacağı yeri veya için gidebilecekleri anlatma  
  
-   Genişletme ve daraltma veya açmak veya kapatmak  
  
-   Kaydırma, kaydırma ve sayfa kapatır  
  
-   Yığınlama ve z sıralama  
  
-   Karusel ve accordion  
  
-   Çevirme ve döndürme kullanıcı Arabirimi  
  
#### <a name="response-and-progress-indicators"></a>Yanıt ve İlerleme göstergesi  
İlerleme göstergesi birkaç önemli avantajı vardır:  
  
-   Her iki belirli ve belirsiz ilerleme göstergeleri sistem değil kilitlendi ve bu sorun üzerinde çalışmaya kullanıcı reassure.  
  
-   Belirli göstergeleri bitiş tarihine yakın alma duyguyu açığa yanı sıra bir fikir eylemi boyunca ne kadar işlendiğini kullanıcı verin.  
  
##  <a name="BKMK_AnimationPatterns"></a> Animasyon desenleri  
  
### <a name="overview"></a>Genel Bakış  
Visual Studio'da animasyonları kullanıcı üretkenliğini hindering olmadan belirli bir işlev sunmaya yöneliktir. Genellikle, Visual Studio animasyonları olması gerekir:  
  
-   Küçük ve örtük  
  
-   Doğal ve gerçekçi  
  
-   İnce ve subdued  
  
-   Hızlı ve verimli  
  
-   Gevşek, değil hurried  
  
Bu çizimde, Visual Studio için öneririz animasyon stilleri gösterir. Hiçbir animasyon veya Zarif animasyon belirerek / Kıs gibi en sık kullanılır. ' I genişletin ve sözleşme gibi hareket animasyonların sınırlı uygulama, değişiklik ve Döndürme X ve Y konumu. 
  
![Visual Studio için önerilen animasyon stiller](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202 a_VSAnimStyles")<br />Visual Studio için önerilen animasyon stilleri
  
#### <a name="appear-and-disappear"></a>Görünür ve kaybolur  
Bu desen ile öğenin görülebilen görünüme giden geçiş animasyon olmadan geri geçiş yapar.  
  
![Görünür ve animasyon kaybolur](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202 b_AppearAndDisappear")<br />Görünür ve animasyon kaybolur  
  
##### <a name="correct-usage"></a>Doğru kullanımı  
Yeni kullanıcı Arabirimi öğeleri, böylece kullanıcı dikkatinizin obstructed ne kayboluyor veya anında görünür gerekir. Ayrıca, yavaş taşınan animasyonları görünmesi ve gözden kaybolur stiliyle karşılaşılmaz bir performans Sürükle olarak algılanan.  
  
##### <a name="incorrect-usage"></a>Yanlış kullanımı  
UI ne şekilde aniden kullanıcının hiçbir fikir sahip görünür ve bir animasyon ekleme kavramsal anlayış ile yardımcı olacak durumları.  
  
##### <a name="animation-properties"></a>Animasyon özellikleri  
Gecikme süresi genellikle sıfır saniyedir.  
  
##### <a name="examples"></a>Örnekler    
-   Araç pencereleri otomatik gizleme  
  
-   Klavye etkinleştirilmiş Düzenleyicisi IntelliSense ve parametre Yardım gibi kullanıcı Arabirimi  
  
-   Genişletme ve daraltma kod bölgeleri  
  
#### <a name="fade-in-and-fade-out"></a>Belirme ve fade-out  
Bu desen ile bir kullanıcı Arabirimi öğesi geçişleri görünür (saydamlığı % 0) görünür (% 100 opaklık) (veya tersi).  
  
![Belirme ve fade-out animasyon](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202 c_FadeInFadeOut")<br />Belirme ve fade-out animasyon  
  
##### <a name="correct-usage"></a>Doğru kullanımı  
Bu, en yaygın olarak UI animasyon önerilir. İlgi akışını kesintiye uğratmadan ekler zarif bir etkisidir. Bazı durumlarda, kullanıcı bile bir animasyon olduğunu düzgün perceiving ve kullanıcı Arabirimi sistem akan farkına varmazsınız.  
  
##### <a name="animation-properties"></a>Animasyon özellikleri  
  
-   Opaklık başlatılıyor: % soluklaşmasını için 0, %100 fade-out için  
  
-   Opaklık bitiş: %100 soluklaşmasını için fade-out % 0  
  
-   Süre: 200 milisaniye tek başına, bir birleşimi animasyon dizisinin bir parçası olarak kullanıldığında 100 milisaniyede  
  
-   Stil kolaylaştırma: sinüsünü InOut  
  
##### <a name="examples"></a>Örnekler  
  
-   Araç pencereleri otomatik gizleme  
  
-   Menü açma ve kapama  
  
-   Arka plan ve ön plan sekmesini geçişleri  
  
#### <a name="color-blend-from-a-to-b"></a>Renk karışım A'dan B'ye  
Bu desen ile bir kullanıcı Arabirimi öğesi A renkten renk B. değiştirir  
  
![Animasyon Karışım rengi](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202 d_ColorBlend")<br />Renk karışım animasyon  
  
##### <a name="correct-usage"></a>Doğru kullanımı  
Bir kullanıcı Arabirimi öğesi renk bir bağlam veya durumu diğerine değiştiğinde animasyonlu geçişe.  
  
##### <a name="animation-properties"></a>Animasyon özellikleri  
  
-   Başlangıç rengi: kullanıcı Arabirimi özgü  
  
-   Renk bitiş: kullanıcı Arabirimi özgü  
  
-   Süre: 200 milisaniye tek başına, bir birleşimi animasyon dizisinin bir parçası olarak kullanıldığında 100 milisaniyede  
  
-   Stil kolaylaştırma: sinüsünü InOut  
  
##### <a name="examples"></a>Örnekler  
  
-   Belge penceresi durumu geçişleri (etkin, etkin ve etkin olmayan son)  
  
-   Araç penceresi durumu geçişleri (odaklı ve Odaksız)  
  
#### <a name="expand-and-contract"></a>' I genişletin ve sözleşme  
Bu desen ile bir kullanıcı Arabirimi öğesi X, Y veya her iki yönde genişletir.  
  
![' I genişletin ve sözleşme animasyon](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202 e_ExpandContract")<br />' I genişletin ve animasyon sözleşme  
  
##### <a name="correct-usage"></a>Doğru kullanımı  
Bir kullanıcı Arabirimi öğesi boyutu bir bağlamından diğerine değiştiğinde animasyonlu geçişe.  
  
##### <a name="animation-properties"></a>Animasyon özellikleri  
  
-   X ölçeği: % veya belirli boyut (piksel cinsinden)  
  
-   Y ölçeği: % veya belirli boyut (piksel cinsinden)  
  
-   Bağlantı konumu: Genel (soldan sağa diller için) sol üst veya sağ üst köşede (için sağdan sola yazılan diller)  
  
-   Süre: 200 milisaniye tek başına, bir birleşimi animasyon dizisinin bir parçası olarak kullanıldığında 100 milisaniyede  
  
##### <a name="examples"></a>Örnekler  
  
-   Mimari Gezgini paneli genişletme ve daraltma  
  
-   Başlangıç sayfa öğesi genişletme ve daraltma  
  
#### <a name="x-y-position-change"></a>X-Y konumunu değiştirme  
Bu desen ile bir kullanıcı Arabirimi öğesi X veya Y konumunu veya her ikisini de değiştirir.  
  
![X-Y konumunu değiştirme animasyon](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202 f_XYPositionChange")<br />X-Y konumunu değiştirme animasyon  
  
##### <a name="correct-usage"></a>Doğru kullanımı  
Bir kullanıcı Arabirimi öğesi konumu bir bağlamından diğerine değiştiğinde animasyonlu geçişe olarak.  
  
##### <a name="animation-properties"></a>Animasyon özellikleri  
  
-   Başlangıç X ve Y konumunu: kullanıcı Arabirimi özgü  
  
-   Bitiş X ve Y konumunu: kullanıcı Arabirimi özgü  
  
-   Hareket yolu: yok  
  
-   Süre: 200 milisaniye tek başına, bir birleşimi animasyon dizisinin bir parçası olarak kullanıldığında 100 milisaniyede  
  
-   Stil kolaylaştırma: sinüsünü InOut  
  
##### <a name="example"></a>Örnek  
Sekme yeniden sıralama  
  
#### <a name="rotate"></a>Döndür  
Bu desen ile kullanıcı Arabirimi öğesi döndürür.  
  
![Kullanıcı Arabirimi öğesi döndürme animasyon](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202 g_Rotate")<br />Kullanıcı Arabirimi öğesi döndürme animasyon  
  
##### <a name="correct-usage"></a>Doğru kullanımı  
Yalnızca belirsiz dönen İlerleme göstergesi için.  
  
##### <a name="animation-properties"></a>Animasyon özellikleri  
  
-   Dönme derecesi: 360  
  
-   Döndürme Merkezi: nesnenin orta  
  
-   Süre: sürekli  
  
##### <a name="example"></a>Örnek  
Belirsiz İlerleme göstergesi (dönen)  
  
### <a name="common-shell-ui-actions-and-recommended-animations"></a>Ortak Kabuk UI eylemlerini ve önerilen animasyonları  
  
#### <a name="tab-open"></a>Açık sekmesi  
![Sekme açık animasyon](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202 h_TabOpen")<br />Sekme açık animasyon  
    
-   Stil: görünür  
  
-   Süre: sıfır saniye  

#### <a name="tab-close"></a>Sekmesini kapatın  
![Sekme Kapat animasyon](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202 i_TabClose")<br />Sekme Kapat animasyon  
  
-   Stil: X konumunu değiştirme  
  
-   Süre: 200 milisaniye olarak  
  
#### <a name="tab-reorder"></a>Sekme yeniden Sırala  
![Visual Studio'da sipariş animasyon sekmesinde](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202 j_TabReorder")<br />Sekme sipariş animasyon

-   Stil: X konumunu değiştirme  
  
-   Süre: 200 milisaniye olarak  
    
#### <a name="close-floating-document"></a>Kapat kayan belge  
![Belge animasyon kayan Kapat](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202 k_CloseFloatingDocument")<br />Kayan belge animasyon Kapat  
   
-   Stil: görünür  
  
-   Süre: 200 milisaniye olarak   
 
#### <a name="window-state-transition"></a>Pencere durum geçişi  
![Pencere durum geçişi animasyon](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202 l_WindowStateTransition")<br />Pencere durum geçişi animasyon  
    
-   Stili: diğer windows ile tutarlı olacak şekilde belge Kapat animasyon tanımlayın geçerli işletim sistemi sağlar.  
  
-   Süre: 200 milisaniye olarak  
  
#### <a name="menu-open"></a>Menü Aç  
![Menü Aç animasyon](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202 m_MenuOpen")<br />Menü Aç animasyon  
    
-   Stil: soluklaşmasını  
  
-   Süre: 200 milisaniye olarak  
  
#### <a name="menu-close"></a>Menü Kapat  
![Menü Kapat animasyon](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202 n_MenuClose")<br />Menü Kapat animasyon  
    
-   Stil: fade-out  
  
-   Süre: 200 milisaniye olarak  
  
#### <a name="auto-hide-tool-window-reveal"></a>Otomatik olarak gizle araç penceresi gösterme  
![Araç penceresi açığa animasyon otomatik olarak gizle](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202 o_AutoHideToolWindowReveal")<br />Araç penceresi açığa animasyon otomatik olarak gizle  

-   Stil: görünür  
  
-   Süre: sıfır saniye