---
title: Visual Studio için bileşik desenler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14d9f233d41638092d1a722094cb0c86f368a748
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951606"
---
# <a name="composite-patterns-for-visual-studio"></a>Visual Studio için bileşik desenler
Bileşik desenler farklı yapılandırmalarda etkileşim ve tasarım öğeleri birleştirin. Tutarlılık açısından en önemli bileşik desenler Visual Studio'da bazıları şunlardır:  

-   [Veri Görselleştirme](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)  

-   [Nesne üzerinde kullanıcı Arabirimi ve gözatma](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  

-   [Seçimi modelleri](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  

-   [Kalıcılığı ve ayarları kaydediliyor](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  

-   [Dokunma girişi](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)  

##  <a name="BKMK_DataVisualization"></a> Veri Görselleştirme  

### <a name="overview"></a>Genel Bakış  
 Grafikler, toplamak ve karar alma geliştirmek için verileri görselleştirmek için görsel bir yoludur. Bunlar, kullanıcıların karşılaştığı veri ancak ne dikkat hak ve eylem ihtiyaç duyabilirsiniz az anlamına gelen çok fazla ile yardımcı olabilir.  

 Aşağıdaki koşullardan herhangi biri doğruysa, kullanıcı bir grafikten yararlı olacaktır:  

-   Grafik üzerinde işlem yapabileceğiniz görevleri tanımasına yardımcı olur?  

-   Grafik olası değişikliklerin sonuçlarını tahmin olanak tanıyacak?  

-   Grafik, eğilimleri ve desenleri kullanıcılara yardımcı olur?  

-   Grafik daha iyi kararlar açmasına izin veriyor musunuz?  

-   Grafik, kullanıcılar verilen içerikte olabilecek belirli bir soruya yanıt yardımcı olur?  

#### <a name="general-rules-for-charts"></a>Grafikler için genel kurallar  

-   Açıkça etiket verileri. Açıklama olmadan çizimler olan yalnızca yapıyorsak resim.  

-   Eksen eğriltme oranlarını önlemek için sıfırdan başlayın. Veri noktaları arasındaki ilişkileri anlamak için önemli görsel ipuçları satır uzunluğu ve çubuğu boyutu var.  

-   Grafikler, değil infografikleri oluşturun. İnfografikleri veri Artistik temsillerini ve bunların birincil hedef visual Öykü anlatımı olduğundan. Grafikleri kullanabilirsiniz ve kullanmalısınız görsel olarak çekici ancak şeklini veri sağlar.  

-   Skeumorphism, anlatımlarda çubuk grafikler, karşıtlık hashmarks ve diğer bilgi grafiği dokunmalar kaçının.  

-   3B Efektleri dekoratif bir öğe olarak kullanmayın. Yalnızca aşağıdaki durumlarda kullanın, kullanıcının yeteneği bilgileri kavrama gerçekten tam sayı.  

-   Bu grafik türünü ikiden fazla renkleri okumak ve yorumlamak doğru zor hale getirebilir olarak birden fazla satır ve dolgular kullanma kaçının.  

-   Bir kavramı anlamak veya veri etkileşimi tek yolu olarak bir grafik (veya herhangi bir çizim) kullanmayın. Bu görsel engelli kullanıcılar için sorunlar sunar.  

-   Bir sayfadaki karşılıksız veya dekoratif öğeleri olarak grafikleri kullanmayın. Diğer bir deyişle, herhangi bir değer ya da Yardım kullanıcı sorunu bir grafik eklemez, kullanmayın.  

### <a name="chart-types"></a>Grafik türleri  
 Visual Studio'da kullanılan grafik türleri dahil çubuk grafikler, çizgi grafikleri, halka grafik ya da "halka grafiği," zaman çizelgeleri olarak bilinen değiştirilmiş bir pasta grafiğinin dağılım çizimleri ("grafikleri küme" da denir) ve Gantt grafikleri. Grafik türlerinin farklı türde bilgi iletişim kurmak için kullanışlıdır.  

### <a name="other-charting-considerations"></a>Grafik dikkat edilecek diğer noktalar  

#### <a name="color"></a>Renk  
 Visual Studio'da kullanmak için tanımlanmış renkleri grafiği, belirli bir palet yoktur. Palet ana renk körlüğü türleri için erişilebilir olduğundan ve renklerin renk çok dar dilimleri kullanıldığında bile ayırt edilebilir. Bu renklerin herhangi bir birleşimini, kullanıcı Arabiriminde grafik veya graf herhangi bir türü için kullanabilirsiniz. Diğer birçok farklı renkler ihtiyacınız yoksa, tüm yedi renklerini kullan gerekmez. Bu renklerin metin veya karakterleri bu renklerin üzerine yerleştirmeyin için tüm ön plan öğeleri ile kullanılmak üzere tasarlanmamıştır. Bu tonları sabit kodlanmış verilecek ve kullanıcı özelleştirmesinde maruz **Araçlar > Seçenekler** (bkz [son kullanıcılar için renk gösterme](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).  

|Renk örneği|onaltılık|RGB|  
|------------|---------|---------|  
|![Renk örneği 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|  
|![Renk örneği BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|  
|![Renk örneği FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|  
|![Renk örneği 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|  
|![Renk örneği 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|  
|![Renk örneği 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|  
|![Renk örneği B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|  

##  <a name="BKMK_OnObjectUI"></a> Nesne üzerinde kullanıcı Arabirimi ve gözatma  
 Bu bölüm, kod Özet görünümü olarak da bilinir, nesne üzerindeki kullanıcı Arabirimi Visual Studio için benzersiz bir tür gözatma için bağlam sağlar.  

### <a name="overview"></a>Genel Bakış  

- Nesne üzerindeki UI kullanıcı daha fazla bilgi veya etkileşim olmadan kendi ana görevden detracting vermeniz gerekir.  

- Nesne üzerindeki Visual Studio kullanıcı Arabiriminde ana desenini "bilgileri dikkat noktasında." olarak bilinir  

- Nesne üzerindeki Visual Studio kullanıcı Arabiriminde veya satır içi veya kayan ve dayanıklı veya geçici değil.  

  -   Kod göz atma görünümünde, bir nesne üzerindeki Visual Studio kullanıcı Arabiriminde türü satır içi ve dayanıklı ' dir.  

  -   CodeLens, bir tür nesne üzerindeki Visual Studio kullanıcı Arabiriminde kayan ve geçici  

  Kod parçasını nasıl çalıştığını anlamak ve bu kodu ayrıntılarını bulma genellikle bağlam değiştirmek ve diğer içerik veya başka bir geliştirici gerektirir penceresi. Bunlar, ana pencereyi bırakırsanız kullanıcıların özgün görevini odaklanmak kaybedebilir bu bağlam kaydırmalar aksatıcı olabilir. Ayrıca, özgün içerik geri özellikle pencereler arasında geçiş yapma özgün kodlarını diğer kullanıcı Arabirimi tarafından gizlenmesine neden oluyorsa zor olabilir alınıyor.  

  Nesne üzerinde kullanıcı Arabirimi "bilgileri dikkat noktasında." adlı bir desen izler Bu iletiler, açılan pencereler ve iletişim kutuları, kullanıcılara kendi ana görev odağınızı kaybetmeden bildirimizi veya açıklamanızı etkileşim ekler, ilgili ek bilgi verin. Bir kullanıcı kendi işaretçi geldiğinde bildirim alanında bir simge, bir sözcüğü ve Visual Studio 2013'te göz atma görünümünde altında kırmızı dalgalı çizgi üzerinde görünen açılır pencereleri nesne üzerindeki UI örnekleridir.  

### <a name="decision-points"></a>Karar noktaları  
 Visual Studio içinden dikkat noktasında bilgilerinin bu düzeni kullanmak için birkaç yol vardır. Doğru mekanizması seçme ve tutarlı, öngörülebilir bir şekilde uygulama genel deneyimi için gereklidir. Aksi takdirde, kullanıcıların içeriği odağı detracts karmaşık veya tutarsız deneyimi ile sunulabilir.  

#### <a name="relationships-between-master-and-detail-content"></a>Ana ve ayrıntılı içerik arasındaki ilişkileri  
 Bir ilişki görüntülemek için kullanılan bilgi noktasında dikkat arasında içeriğiyle ilgili içerik ("ayrıntılı" içerik) ("ana" içerik) odaklanır ve ek kullanıcıdır. Bu düzende, ayrıntılı içerik açıkça kullanıcı ile çalışma ve yakın ana içerik görüntülenebilir içerik ilişkilidir. Ek veya ana içerik aşırı yüklenilmesini olmadan özetlenen olamaz bilgileri araç penceresi gibi başka bir deseni izlemelidir.  

-   **Her zaman** ana içerik yakınında ayrıntılı içeriklerin.  

-   **Her zaman** yine de ana içerik odaklanmış kalmasına olanak ayrıntılı içerik olanak tanıdığından emin olun. Genellikle, bunu yapmanın en iyi ana içerik mümkün olduğunca yakın ayrıntılı içerik olarak işlemek için yoludur. Bu, ana içeriğin yanındaki açılır pencerede ayrıntılı içerik işleme ya da işleme ayrıntıları, ana içerik altındaki içeriği satır içi yapılabilir.  

-   **Hiçbir zaman** ana içerik uzağa kullanıcının gerçekleştirdiği dikkat noktasında bilgileri kullanın. Kullanıcılar, ayrıntılı içerik ayrı olarak görüntülemek gerekiyorsa, bunu yapmak kullanıcının sağlayan belirli bir işlem kullanıma sunar.  

#### <a name="design-details"></a>Tasarım ayrıntıları  
 Nesne üzerinde kullanıcı Arabirimi doğru seçim olduğunu belirledikten sonra dört temel tasarım hakkında önemli noktalar vardır:  

1. **Kalıcılık:** içeriği kalıcı veya geçici olması beklenir?   
   Kullanıcılar bilgileri bakın veya etkileşime geçmek için görünür tutmak istersiniz? Veya kullanıcılar bilgilerine Hızlı bakış ve ana görevini ile devam etmek istersiniz?  

2. **İçerik türü:** içeriği bilgilendirici, eyleme dönüştürülebilir veya gezinme olur?   
   Kullanıcı ana içerik hakkında ek ayrıntılar gerekiyor mu? Ana içerik etkileyen bir görevi tamamlamak kullanıcının gerekir? Veya kullanıcı başka bir kaynağa yönlendirilen olması gerekiyor mu?  

3. **Gösterge türünü:** bir ortam göstergesi mantıklı?   
   Bilgilerin kullanılabilir yararlı bir şekilde özetlenen ve ana içerik aşırı yüklenilmesini olmadan görüntülenir?  

4. **Hareketlerini:** ne hareketlerine çağırır ve kullanıcı arabirimini kapatmak için kullanılacak?   
   Nasıl kullanıcı ayrıntılı içerik getirin ve hemen gönderebilir? Geçici ve kalıcı durumlar arasında geçiş yapmak için sabitleme gibi hareket ekleme değeri mı?  

   Bu dört karar noktaları her bir nesne üzerindeki kullanıcı Arabirimi ana bileşenleri üzerinde etkisi olacaktır.  

### <a name="on-object-ui-components"></a>Nesne üzerinde kullanıcı Arabirimi bileşenleri  

1.  Kapsayıcı (içerik sunan) türü  

    -   Kayan  

    -   Satır içi  

2.  İçerik türü  

    -   Bilgi amaçlı: veri, statik veya dinamik olabilir  

    -   Eyleme dönüştürülebilir: ana içerik değiştirme komutları  

    -   Gezinme: başka bir pencereye veya MSDN gibi uygulamanın kullanıcı yönlendiren bağlantılar  

3.  Hareketler  

    -   Çağırma  

    -   İşten çıkarma  

    -   Sabitleme  

    -   Diğer etkileşimler  

4.  Kalıcılığı ve yürütme modeli  

    -   Geçici  

    -   dayanıklı  

    -   Otomatik  

    -   İsteğe bağlı  

5.  Ortam göstergeleri (isteğe bağlı)  

    -   Dalgalı çizgi  

    -   Akıllı etiket simgesi  

    -   Diğer ortam göstergeleri  

#### <a name="container-content-presenter-type"></a>Kapsayıcı (içerik sunan) türü  
 Dikkat etmeniz noktasında içerik sunmak kullanılabilir iki ana seçeneğiniz vardır:  

1.  **Satır içi:** var olan içeriğin ilerletmeniz Visual Studio 2013 Kod Düzenleyicisi'nde kullanıma sunulmuştur Özet görünümü gibi bir satır içi sunan yeni içerik için alan sağlar.  

    -   **Tercih ettiğiniz** , kullanıcılar önemli miktarda başvuran veya içeriğiyle etkileşimde bulunmaya zaman harcamamız Environment bekliyorsanız satır içi sunucuları sunar.  

    -   **Önlemek** kullanıcılar bekliyorsanız satır içi sunucuları sunmak ve ardından ana görevini en az devam bilgilere genel bakış istediğiniz.  

2.  **Kayan:** kayan sunucu seçilen içeriği gibi mümkün olduğunca yakın konumlandırılır, ancak mevcut içeriğinin düzenini değiştirmez. Kayan bir içerik bölmesi üzerinden görüntüleme gibi çeşitli stratejiler çalıştırılacağı boşluk seçili sembol kullanılabilir en yakın.  

    -   **Tercih ettiğiniz** kullanıcılar bekliyorsanız sunucuları kayan istediğiniz sunmak ve ardından ana görevini en az devam bilgilere genel bakış.  

    -   **Önlemek** kullanıcılar bekliyorsanız sunucuları kayan Environment başvuran veya içeriğiyle etkileşimde bulunmaya süresi önemli ölçüde harcayabileceğiniz, mevcut.  

#### <a name="content-type"></a>İçerik türü  
 İçinde herhangi bir nesne üzerinde kullanıcı Arabirimi kapsayıcısına görüntülenebilir içerik üç ana türü vardır. Bu tür bilgilerin herhangi bir birleşimini gösterilebilir. Üç tür şunlardır:  

1.  **Bilgi amaçlı:** çoğu nesne üzerindeki UI kapsayıcıları, bazı tür bilgilendirici içerik görüntülenir. İçerik ortamın mevcut durumu hakkındaki bilgileri gösterebilir veya ortam olası gelecekteki durumuyla ilgili bilgileri temsil edebilir. Örneğin, bir, mevcut kodu yeniden düzenleme gibi belirli bir komut etkisini göstermek için kullanılabilir.  

    -   **Her zaman** görüntü bilgileri kurallı gösterimini kullanın. Örneğin, kod söz dizimi vurgulama, tam kod gibi görünmelidir ve yazı tipinde ve kullanıcı diğer ortam ayarları dikkate.  

    -   **Her zaman** ana içerik olarak aynı bilgileri sunulmazsa sağlayabileceğinizden bilgilendirme içerik üzerinde herhangi bir eylem desteklemeyi düşünün. Örneğin, bir nesne üzerinde kullanıcı Arabirimi kapsayıcısı içinde var olan kod sunma, kesinlikle göz atın ve bu kodu değiştirme olanağı desteklemeyi düşünün.  

    -   **Her zaman** farklı arka plan rengi, bilgilendirici içerik sunma olası gelecekteki bir durumu temsil ediyorsa kullanmayı düşünün.  

2.  Eyleme dönüştürülebilir: Bazı nesne üzerinde kullanıcı Arabirimi kapsayıcıları yeniden düzenleme işlemi gerçekleştirme gibi ana içerik üzerinde bazı eylemler gerçekleştirme olanağı sunar.  

    -   **Her zaman** bilgilendirici içeriğinden ayrı olarak eyleme dönüştürülebilir komutları getirin.  

    -   **Her zaman** etkinleştirin ve uygun olduğunda eylemleri devre dışı bırakın.  

    -   **Her zaman** iletişim kutusu içindeki komutları temsil eden standart yönergelere bakın.  

    -   **Her zaman** mutlak bir nesne üzerinde kullanıcı Arabirimi kapsayıcıya sunulan eylemleri sayısı en düşük tutun. Nesne üzerindeki kullanıcı Arabirimi ile etkileşim basit, hızlı bir deneyim olmalıdır. Kullanıcı nesne üzerinde kullanıcı Arabirimi Kapsayıcının kendisi yönetme enerji harcaması gerekmez.  

    -   **Her zaman** nasıl ve ne zaman bir nesne üzerinde kullanıcı Arabirimi kapsayıcısı kapalı kapatıldı veya göz önünde bulundurun. En iyi uygulama, bu eylem çalıştırıldığında ana ayrıntı içerik arasındaki iletişim sonucuna herhangi bir işlem nesne üzerinde kullanıcı Arabirimi kapsayıcısı da kapatmalısınız.  

3.  **Gezinme:** bazı kullanıcı Arabirimi kapsayıcılar dahil başka bir pencereye veya bir MSDN makalesi kullanıcının web tarayıcısında açarak gibi uygulama, kullanıcının yönlendiren bağlantılar nesne üzerindeki.  

    -   **Her zaman** böylece kullanıcılar diğer içerikler çıkıldığında tarafından sürprizle değil "Açık" herhangi bir gezinme bağlantısına önüne ekleyin.  

    -   **Her zaman** gezinme bağlantılarını eyleme dönüştürülebilir bağlantılardan ayırın.  

#### <a name="ambient-indicators-optional"></a>Ortam göstergeleri (isteğe bağlı)  
 Ortam göstergeleri, zarif, metin, kodun geri kalanını renklerden bir renk sunulan dahil olmak üzere veya belirgin dalgalı alt çizgiler ve akıllı etiket simgeler gibi tickler simgeleri dahil olabilir. Ortam göstergeleri ilgili ek bilgiler kullanılabilirliğini iletişim kurar. İdeal olarak, kullanıcının etkileşime geçilebileceği bile gerek kalmadan yararlı bilgiler sağlar.  

-   **Her zaman** bir ortam göstergesi bırakmaz departmanınızı veya kullanıcının sık zora şekilde konumlandırın. Bir ortam göstergesi biçimde konumlandırmak mümkün değildir, başka bir çözümü göz önünde bulundurun.  

-   **Her zaman** ortam göstergesi ilişkili içeriğe mümkün olduğunca yakın yerleştirin.  

-   **Her zaman** kullanılabilir bilgi özetleyen bir göstergesi oluşturmayı deneyin. Bir sayısını kullanılabilir olan veri öğeleri (örneğin, "3 başvurular" Basit "başvuru" yerine) sağlamayı göz önüne alın veya verileri özetlemek için başka bir şekilde düşünün.  

    -   Burada bir göstergesi için veriler her zaman hesaplanan görüntülenir ve durumlarda değerler hesaplanan aşamalı geri bildirim sağlayarak hemen göz önünde bulundurun. Örneğin, benzer şekilde, Windows Phone şirket e-posta Canlı kutucuk sayısı arttıkça okunmamış e-postaları yeniler kullanılabilir veri güncelleştirmeleri yansıtan değişiklikler hareketlendirme göz önünde bulundurun.  

-   **Hiçbir zaman** bir kullanıcı belirli bir içerik parçasına için makul bir şekilde ele çok daha fazla göstergeleri ekleyin. Ortam göstergeleri kullanıcı etkileşimi gerektirmeden faydalı olması gerekir. Taşma ve bunları görüntülenebilmesi için diğer yönetim denetimleri gerekiyorsa göstergeleri, çevre kaybedersiniz.  

#### <a name="gestures"></a>Hareketler  
 Ana içerik odaklanmak korumak kullanıcı izin vermenin bir anahtar açıp ek ayrıntı içeriği kapatmak için sağ hareketlerini destekleyerek yönüdür.  

-   **Her zaman** gerektirmek ek içeriği açmak için bazı açık hareketi gerçekleştirin. Ortak açık hareketlerini içerir:  

    -   **Vurgulu:** araç ipuçları veya etkileşimli olmayan bilgi içeriği  

    -   **Açık komut:** satır içi sunan  

    -   **Ortam göstergesi çift:** CodeLens açılır penceresi  

-   **Her zaman** her kullanıcı Esc tuşuna bastığında ayrıntılı içerik yok sayın.  

-   **Her zaman** nesne üzerindeki UI bağlamı göz önünde bulundurun. Kapsayıcı içinde etkileşimi için izin içerik sunucuları için ek bilgi üzerine gelindiğinde, kullanıcının iş akışı için karışıklığa neden olma olasılığı olan gösterilip gösterilmeyeceğini dikkatlice düşünün.  

-   **Hiçbir zaman** düzenlenebilir özelliğe sahip gibi görünüyor veya kullanıcı etkileşimi davet üzerine gelindiğinde içeriği görüntüler. İmleci, üretilen içerik ana artık olduğunda hemen kapatmak için bir araç ipucu için standart davranış olduğu gibi bunlar ayrıntı içeriklerde imleç çalışırsanız, bu davranışı kullanıcıları rahatsız edebilir.  

##  <a name="BKMK_SelectionModels"></a> Seçimi modelleri  

### <a name="overview"></a>Genel Bakış  
 Bir seçim modeli belirtin ve onaylayın veya daha fazla nesne kullanıcı arabiriminde ilgilendiğiniz işlemleri için kullanılan mekanizmadır. Bu konu Visual Studio belge Düzenleyicisi içinde seçimi etkileşim desenleri açıklar: metin düzenleyiciler, tasarım yüzeyleriyle ve modelleme yüzeyleri.  

 Kullanıcıların ne üzerinde çalıştıkları için Visual Studio belirten bir yol olmalıdır ve Visual Studio, kullanıcılara ne üzerinde çalışıyor hakkında geri bildirim ile tahmin edilebilir bir biçimde yanıtlamalıdır. Farklılıkları veya kullanıcı ve kullanıcı arabirimi arasında bir miscommunication içerebilen bir eylem, bildirimde bulunmadan değil kullanıcı sonuçlanabilir istenmeyen sonuçları. Genellikle, bir şeyin eksik olduğunu veya değişti kullanıcının gördüğü kadar hata gözden kaçan gider. Seçimi modelleridir bu nedenle en önemli parçaları kullanıcı arabirimi tasarım birine. Visual Studio'da seçim modelleri Windows ile tutarlı olsa da, küçük farklılıklar vardır.  

 Windows, olduğu gibi Visual Studio'da seçim modelleri etkileşimi gerçekleştiği bağlamı bağlı olarak farklılık gösterir. Seçim nesneleri dört tür oluşabilir:  

- Metin  

- Grafik nesneleri  

- Listeler ve ağaç  

- Kılavuzları  

  Bu nesneler içinde seçimleri üç tür vardır:  

- Bitişik  

- Ayrık  

- Bölge  

#### <a name="scope"></a>Kapsam  
 Seçimi en önemli bileşeni, kullanıcının hangi penceresinde (etkinleştirme) çalışan ve odağı bulunduğu (seçim) olduğu bildiği sağlamaktır. Visual Studio Windows penceresi yönetim işlevselliği genişletir, ancak etkinleştirme şeması aynıdır: bir pencere ile etkileşim kurma, penceresine odak getirir. Visual Studio etkinleştirme için iki göstergeleri sahiptir: biri belge pencereleri ve bir araç pencereleri için.  

 Belge pencereleri için etkin pencere öne çıkacak ve arka plan rengini değiştirerek bir belge penceresi sekmesine tarafından belirtilir:  

 ![Visual Studio'da etkin sekme seçimi](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713 01_ActiveTab")  

 **Etkin sekmede seçimi**  

 Araç pencereleri için etkin pencere bir araç penceresinin başlık çubuğu alanına rengi değişiklik belirtilir:  

 ![Visual Studio'da etkin araç penceresini seçimi](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713 02_ActiveToolWindow")  

 **Bir düğümün birincil seçimi gösteren etkin araç penceresi**  

 ![Visual Studio'da etkin araç penceresini seçimi](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713 03_InactiveToolWindow")  

 **Düğümün görünmeyen seçimi gösteren etkin olmayan araç penceresi**  

 Bir pencere etkin olduktan sonra odak yönergeleri Bu bölümde açıklanan seçimi modelleri göre belirtilir.  

#### <a name="context"></a>Bağlam  
 Visual Studio, kullanıcının nerede çalıştığını, izleme tutma bağlam, güçlü bir kavramı korumak için tasarlanmıştır. Yalnızca bir pencere bir araç veya belge penceresi olup olmadığını etkindir. Ancak, en üstteki belge penceresi, her zaman görünmeyen bir seçim korur. Araç penceresine odak olabilir, ancak son etkin belge penceresi bile etkin olmayan bir durumda bir seçim görüntüler. Bu, kullanıcının bağlamında bunlar, böylece geri dönün ve araç pencerelerini ve belge pencereleri arasında sorunsuz bir şekilde kaydırma Visual Studio durumlarına korudu gösteren düzenlemekte olduğunuz belgeyi korumak için gerçekleştirilir.  

### <a name="text-selection"></a>Metin seçimi  
 Aynı metin seçim modeli gibi yerleşik metin düzenleyici, kesin olarak metinsel visual Studio düzenleyicisi kullanın ve görünüm açıklanan [işaretçileri ve fare](/windows/desktop/uxguide/inter-mouse) üzerinde Windows kullanıcı deneyimi etkileşim kuralları sayfası MSDN. Giriş odağını metin düzenleyicisinde, ekleme noktasını adlı bir çubukla gösterilir. Ekleme, tek bir piksel kalın ve renkli arkasında görünür tersi olarak noktasıdır. Belirlenen oranı göre yanıp **imleç yanıp sönme hızı** ayarı **hızı** sekmesinde **klavye** uygulaması Denetim Masası'nda.  

#### <a name="contiguous-and-disjoint-selection"></a>Sürekli ve ayrık seçimi  
 Seçimi Metin Düzenleyicisi içinde yalnızca bitişik değil. Seçimleri izin verilmez, ancak grafik nesnesi düzenleyicilerde ele alınması gereken metin ayrık. Kullanıcının fare işaretçisi bir metin alanı üzerinde olduğunda, imleç bir ı ışını için değiştirir. Tek tıklamayla noktasını tıklatın konumda metin düzenleyicisinde yerleştirir. Fare düğmesini basılı seçimi Vurgu başlar ve fare düğmesini bırakmadan seçim Vurgusu sona erer.  

#### <a name="region-selection-box-selection"></a>Kayıt seçimi (seçim kutusu)  
 Visual Studio Metin Düzenleyicisi'nde bölge seçimleri destekler ve bu seçim kutusu çağrılır. Seçim kutusunu kullanıcının normal metin akışına izlemez metnin bir bölge seçin izin verir. İle gibi standart metin seçimi, seçim bitişik olması gerekir. Fare ile sürüklerken Alt tuşunu basılı tutarak seçim kutusunu başlatılır. Seçim kutusunu Alt ve üst karakter tuşları seçimi bölgesini belirtmek için ok tuşlarını kullanarak tutarak da başlatılabilir. Seçim kutusu normal seçim Vurgusu kullanır ve seçim alanı sonunda yanıp sönen ekleme noktası imleç gösterir.  

 ![Bölgesel &#40;kutusu&#41; Visual Studio'da seçim](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713 04_BoxSelection")  

 **Visual Studio'da bölge (kutu) Seçimi**  

#### <a name="text-selection-appearance"></a>Metin seçimi görünümü  
 Düzenleyicide etkin ve etkin olmayan seçim için kullanılan renkleri özelleştirilebilir. Düzenleyici görünümünü özelleştirmek için bir kullanıcı giderek **Araçlar > Seçenekler**, altında olup olmadığına bakın **ortam > yazı tipleri ve renkler > Metin Düzenleyicisi**.  

### <a name="graphical-selection"></a>Grafik seçimi  

#### <a name="interaction"></a>Etkileşimi  
 Grafik Nesne Seçimi karmaşık olabilir ve bir dizi faktöre bağlıdır:  

-   **Editör'ün birincil seçim modeli.** Grafik nesneleri içeren düzenleyicileri, metin ya da kılavuzlarda düzenlemek için de kullanılabilir. Örneğin, düzenleyici ayrıca Visual Studio XAML Tasarımcısı gibi grafik nesneleri yerleşimini destekler metin tabanlı bir düzenleyici olabilir. Birden çok nesne türlerini destekleyen nasıl farklı türde nesne oluşan gruplar kullanıcının seçtiği etkileyebilir.  

-   **Birincil ve ikincil seçimi durumları için destek.** Bir düzenleyici, böylece çubuğuyla, nesneleri düzenlenebilir durumları, yeniden boyutlandırılabilir birlikte, vb. hizada birincil ve ikincil seçimi sağlayabilirsiniz.  

-   **Yerinde düzenleme desteği.** Ayrıca düzenleyicileri düzenlenmesi için kendi grafik nesneleri içeriğini izin verebilirsiniz. Örneğin, bir dikdörtgen kullanıcı tarafından değiştirilebilir iç metin içerebilir. Ayrıca, bu metni ortalanmış açısından haklı bir gerekçesi veya açılamadı. Yerinde düzenleme daha ayrıntılı bir düzeyde kullanıcı etkileşimini gerektirir ve bu nedenle kullanıcıya durum bilgileri sunmak için uygun bir görsel ipuçları kümesi gerektirir.  

#### <a name="mouse-interaction"></a>Fare etkileşimi  

|Giriş|Sonuç|  
|-----------|------------|  
|Seçili olmayan bir nesneye tıklayın|Nesneyi seçer ve nesne yeniden boyutlandırılabilir ise kesik çizgi ve seçim tutamaçları görüntüler.|  
|Seçili nesneye tıklayın|Nesne destekliyorsa, yerinde düzenleme etkinleştirir. Yerinde düzenleme modu dışında nesneye tıklayarak devre dışı bırakır.|  
|Bir nesneyi çift|Kodu düzenleme için nesnenin arkasında açılır ve uygunsa bir varsayılan olay işleyicisini ekleyebilirsiniz.|  
|Bir nesneye işaret|İşaretçi taşıma imlecine dönüşür. Parlaklık ya da rengi gibi nesnenin görünümünü değiştirebilirsiniz.|  
|Bir seçim tutamacını işaretleyin|İşaretçi yeniden boyutlandırma imlecine dönüşür. İşaretçi (uzağa taşınmış farklı Örneğin,) göre tutamacı konumlandırılmış şekilde döndürme desteği nesneler için bazı seçimi işleyen bir döndürme imlece kadar işaretçiyi değişebilir.|  
|Sürükle|Nesne önceden seçili değilse, taşıma imleci işaretçi ve nesneyi taşır.|  
|Düzenleyici odağından|Nesne içeriği ve görünümü en son işlem/seçim durumunda sırasında vardı korusa da, yerinde düzenleme modunu devre dışı bırakır.|  
|Nesne Seçimi|Kenarlık, noktalı çizgi veya diğer görsel olarak ayrı bir işleme nesnesinin sınır vurgulamak için gösterilir.|  
|Seçili nesneyi yeniden boyutlandırma|Seçimi tutamaçları ile gösterilir.<br /><br /> Yeniden boyutlandırılabilir bir nesne içinde boyutlandırılabilir her yönünü temsil eden sekiz tanıtıcıları sahiptir. Nesne yalnızca belirli bir yönde boyutlandırılabilir daha az tanıtıcıları kullanılabilir. Kullanıcı nesneyi nereye sekiz tanıtıcıları etkileşimli olmazdı aşağı boyutları, dört tanıtıcıları kullanılabilir. Tanıtıcı boyutları bağlı ile penceresi kenarlık ve edge ölçümlerine **GetSystemMetrics** ekran çözünürlüğünü derlemekten boyuta API işlevi.<br /><br /> ![Yeniden boyutlandırma tutamaçları](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713 05_ResizeHandles")|  
|Seçilen bir nesne döndürme|![Döndürme tutamaçları](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713 06_Rotate")|  

#### <a name="keyboard-interaction"></a>Klavye etkileşimi  

|Giriş|Sonuç|  
|-----------|------------|  
|Tab|Odak göstergesi arasında nesnelerin mantıksal sırası Düzenleyicisi'nde taşır. Bu soldan sağa veya üste alt bağlı olarak olabilir **TabIndex** (veya eşdeğer) özellik değeri, nesne oluşturma sırası ve genel amaçlı Düzenleyici. Shift + Sekme odağı belirtecini yönünü tersine çevirir.|  
|Ara çubuğu|Tuş vuruşu korunur ancak kaydırma modunu etkinleştirir. Ek fare girdisi, Görünüm penceresi konumu kaydırmak için gereklidir.|  
|Ctrl+Ara Çubuğu|Tuş vuruşu korunur ancak yakınlaştırma modunu etkinleştirir. Ek fare girişi artırmak ve yakınlaştırma faktörünü azaltmak için gereklidir.|  
|Ctrl + Alt + eksi işareti|Yakınlaştırma faktörünü bir düzey azalır.|  
|Ctrl + Alt + artı işareti|Yakınlaştırma faktörünü bir düzeyine göre artar.|  
|SHIFT veya Ctrl|Nesne Seçimi gruba ekler. CTRL nesneleri ayrı ayrı seçimi gruptan kaldırmanızı sağlar.|  
|Enter|Nesne için varsayılan komut gerçekleştirir (genellikle açın veya düzenleyin).|  
|F2|Nesne için yerinde düzenleme etkinleştirir.|  
|Ok tuşları|Seçilen nesneler ok tuşu basılı küçük artışlarla (örneğin, aynı anda 1 piksel) yönünde taşır|  
|CTRL + ok tuşları|Seçilen nesneler ok tuşu basılı büyük artışlarla (örneğin, aynı anda 10 piksel) yönünde taşır|  
|SHIFT + ok tuşları|Seçilen nesneler (örneğin, aynı anda 1 piksel) küçük artışlarla karşılık gelen yönde yeniden boyutlandırır|  
|CTRL + SHIFT + ok tuşları|Seçilen nesneler (örneğin, aynı anda 10 piksel) daha büyük artışlarla karşılık gelen yönde yeniden boyutlandırır|  

 Kullanıcı denetimleri düzenlediğinizde, bu kullanıcı girişi ile otomatik olarak yeniden boyutlandırmak nesneler için mantıklı olabilir. Kullanıcının bir etiket denetimi düzenlerse, örneğin, ardından etiketin yalnızca kullanıcının yazdığı metni görüntülemek için büyümesini. Bu yapılmazsa, kullanıcı denetimi el ile metni düzenledikten sonra yeniden boyutlandırmanız gerekir. Kullanıcı denetimleri çok fazla varsa, bu rote ve üretken bir görev haline gelir.  

#### <a name="graphical-containers"></a>Grafik kapsayıcıları  
 Bazı durumlarda, grafik düzenleyicilerden Windows Forms Panel denetimi veya kılavuz düzeni denetimin HTML Tasarımcısı'nda gibi diğer grafik nesneleri için kapsayıcılar sağlar. Düzenleyici için diğer grafik nesneleri kapsayıcıları sağlıyorsa, aşağıdaki seçim modeli kapsayıcısı için yalnızca (standart model olarak yukarıda açıklanan kapsayıcı izleme nesnelerinde) kullanılmalıdır:  

|Giriş|Sonuç|  
|-----------|------------|  
|Tek tıklamayla kapsayıcıdaki|Kapsayıcı nesnesi herhangi bir kapsanan nesneleri doğrudan seçmeden seçer. Kapsayıcı taşınır ve/veya standart fare ve klavye (yukarıda açıklandığı gibi) ile yeniden boyutlandırıldı. Kapsanan nesneler kapsayıcıya ilişkisinde taşınır, ancak aynı zamanda doğrudan seçmediğiniz sürece kapsanan nesneleri yeniden boyutlandırılacağını değil.|  
|Kapsayıcının sınırları bölgesini üzerine gelme|Fare kapsayıcının taşınabilir belirten taşıma imleci açar.|  
|Kapsayıcının sınır bölgesi sürükleyin|Fare imleci taşıma değiştirir ve kapsayıcı (ve içinde kapsanan nesneler) hareket ettirir. Kapsayıcı ilk taşınamaz tek bir tıklamayla seçili.|  
|Kapsayıcı içindeki bir nesnede tek tıkla|Kapsayıcı (belirlediyseniz) dilimleyiciye ve yalnızca tıklandı nesneyi seçer.|  
|Shift + tıklayın veya Ctrl + bir kapsanan nesne ya da kapsayıcı tıklayın|Tıklandı nesne bir varolan seçimi veya seçimi gruba ekler. Tıklandı Nesne Seçimi grubunun bir üyesi ise, seçim gruptan kaldırılır.|  

 Kapsanan nesneler, önceki bölümde açıklandığı gibi temel seçim modeli uymanız gerekir. Windows Forms tasarımcısına kullanılabilirlik testing'e kullanıcılar kapsanan nesneler sorunsuz erişim (kapsama nesne tarafından uygulanan) müdahalede bulunan adımlar olmadan bekleniyor.  

#### <a name="disjoint-and-region-selections"></a>Ayrık ve bölge seçimleri  
 Grafik nesne düzenleyicileri ayrık seçimleri desteklemelidir. Bu grafik Visual Studio için Denetim görünümü göstermez unutmayın. Bkz: [grafik Nesne Seçimi görünümü](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) visual ayrıntılı belirtimler için.  

 ![Ayrık ve bölge Seçici](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713 07_DisjointRegionSelectors")  

 **Ayrık seçimi**  

 Grafik düzenleyicilerden Kayan yazı tipi seçimi göstergesi ile bölgeye seçimleri da sağlamanız gerekir. Grafik düzenleyicisini (metin gibi) diğer nesne türlerini destekliyorsa, bölge seçimleri bu diğer nesne türlerini kısıtlamalarına bağlı olarak mümkün olmayabilir.  

 ![Seçim çerçevesi](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713 08_MarqueeSelection")  

 **Seçim çerçevesi**  

#### <a name="primary-and-secondary-selections"></a>Birincil ve ikincil seçimleri  
 Bazı grafik nesnesi düzenleyicileri düzenlemek veya gruplardaki nesneleri Hizala izin verin. Bu durumda, birincil ve ikincil seçimleri kavramını olması gerekir. Birincil seçimin diğer tüm nesnelerin grubunu işlemlerinde yanıt verme nesnedir. Birincil denetimden önce kullanıcının seçtiği nesne haline gelir ve sonraki seçimleri ikincil seçim haline gelir. Birincil seçimi hangi nesnenin birincil belirtmek için ikincil selection(s)'dan farklı bir visual işlemden sahiptir:  

 ![Birincil ve ikincil seçimi](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713 09_PrimarySecondary")  

 **İki ikincil seçimleri birincil seçimi**  

####  <a name="BKMK_GraphicalObjectSelectionAppearance"></a> Grafik Nesne Seçimi Görünümü  
 Seçim tutamaçlarını, nesnenin sınırlayıcı kutu çevresinde bir dikdörtgen deseninde çizilmiş karelerdir. Aşağıdaki grafik, bir grafik nesnesi tanıtıcı, boyutlandırma ve yerinde düzenleme görünümü ile olabilen çeşitli durumları örneklerini gösterir. Tutamaçları boyutunu pencere sınırı ve edge ölçümleri kullanarak bağlı olması **GetSystemMetrics** API.  


| Durum | Görünüm | Görsel ayrıntıları |
|-------------------------|---------------| - |
| **Seçimi kaldırıldı** | Varsayılan | ![Varsayılan düğme durumu](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713 10_DefaultState") |
| **Birincil seçimi** | Yeniden boyutlandırılabilir | ![Birincil seçimiyle yeniden boyutlandırma tutamaçları](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713 11_PrimaryResize") |
| **Birincil seçimi** | Yeniden boyutlandırılabilir değil | ![Birincil seçimi olmadan yeniden boyutlandırma tutamaçları](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713 13_PrimaryNoResize") |
| **Birincil seçimi** | Kilitli | ![Kilitli birincil seçimi](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713 15_PrimaryLocked") |
| **İkincil seçimi** | Yeniden boyutlandırılabilir | ![İkincil seçimiyle yeniden boyutlandırma tutamaçları](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713 17_SecondaryResize") |
| **İkincil seçimi** | Yeniden boyutlandırılabilir değil | ![İkincil seçimi olmadan yeniden boyutlandırma tutamaçları](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713 19_SecondaryNoResize") |
| **İkincil seçimi** | Kilitli | ![Kilitli ikincil seçimi](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713 21_SecondaryLocked") |
| **Etkin kullanıcı Arabirimi** | Varsayılan | ![Etkin durumdaki kullanıcı Arabirimi](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713 23_UIActive") |

### <a name="view-selection-models"></a>Seçimi modelleri görüntüle  

#### <a name="tree-view"></a>Ağaç görünümü  
 Ağaç görünümünde seçimi ile basit bir vurgulama gösterilmektedir. Kullanıcı, bir düğüm adı veya bir düğüm simgesi tıklarsa, düğüm seçili olur. Üçgen karakterleri sol tarafındaki düğümü genişletin veya ağaç denetimi sözleşme ancak bir özel durum ile bir kullanıcının seçimi etkilemez: seçim bu düğümün alt düğümü üzerinde olduğunda bir üst düğümün daraltma bağlı üst seçimi taşır.  

 ![Visual Studio tipik ağaç görünümünde](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713 25_TreeView")  

 **Visual Studio'da tipik ağaç görünümü**  

 Ağaç görünümlerini ağacında birden çok düzeyi arasında sürekli ve ayrık seçimleri destekleyebilir. Bitişik veya ayrık görünür ağaç düğümleri üzerinde birden fazla seçim yapılması gerekir. Bir düğüm daraltılmışsa, ayrık seçimi kaybolur ve seçim sbalil düğümünü alır. Bu şekilde, kullanıcı bir işlemden etkilenen düğümleri görebilirsiniz. Düğümleri daraltıldığında hangi düğümleri etkilenebilecek belirsiz olur.  

 Üst düğümü seçildiğinde olabilir ancak üst ve tüm alt öğelerini uygulamak bir işlem için yarayacak yerde çalışmaları işlemi üst öğeye uygulamanız gerekir. Bu durumda, onay kutusu veya "tüm alt öğelere uygula" seçeneği kullanıcıya açık hale getirmek için onay iletişim kutusu gibi işlemi sırasında ek kullanıcı Arabirimi sağlar.  

##### <a name="renaming"></a>Yeniden adlandırma  
 Yeniden adlandırma Ağaçtaki düğümler destekliyorsa, yeniden adlandırma yerinde yapılması gerekir. Yerinde işlemi standart, Visual Studio tüm ağaç denetimlerinde arasında olmalıdır. Yerinde düzenleme modu, adın tamamını düğümünün, kullanıcı girişi kabul etmeye hazır kapsayan metin seçimi ile hemen etkinleştiren bir yeniden adlandırma komutu belirtin. Düğüm bir dosyayı temsil ediyorsa, dosya adı uzantısını içermelidir. Seçim Vurgusu, yalnızca dosya adını ve uzantısını değil gövdesi içermelidir.  

|Giriş|Sonuç|  
|-----------|------------|  
|Enter tuşu|Yeniden adlandırma işlemi tamamlar.|  
|ESC tuşu|Yeniden adlandırma işlemi iptal eder|  
|Yerinde düzenleme bölgesi dışında tıklayarak|Yeniden adlandırma işlemi tamamlar.|  
|Geri alma|Yeniden adlandırma işlemi iptal etmek için bir kolayca geri alma sağlayın|  

#### <a name="selection-within-lists-and-grid-controls"></a>Seçim listeleri ve kılavuz denetimleri içinde  
 Liste seçimdeki en önemli kavram olan satır tabanlı, tam satır seçimi yapıldığında, yani bir birim olarak seçilir. Aksine, kılavuzlar, belirli bir satırın herhangi bir özelliği etkilemeden seçilmesi hücrelere izin verebilirsiniz. Kılavuzlar hiyerarşisi seçili ve üst satırları ile etkileşim kurarak seçimi için hiyerarşinin tüm dalları sağlayan iç içe geçmiş satırlar (olduğu gibi bir TreeGrid gibi) de içerebilir. Seçim listeleri tüm veri satırı üzerinde basit Vurgu rengi tarafından gösterilir. Odağı geçerli düzenlenebilir satır veya hücre (satır tüm hücreler salt okunur ise) çevresine tek pikselli noktalı bir kenarlık tarafından gösterilir.  

> [!NOTE]
>  **Odak** ve **seçimi** farklı kavram olmasıdır. *Odak* göstergesidir hangi UI öğesi hedeflediği açıkça başka bir nesnede yönlendirilmiş giriş almaya çalışırken *seçimi* sonraki olan bir nesne nesnenin edilme durumunu gösterir işlemleri yer alabilir.  

 Bitişik, ayrık, seçim listelerindeki olabilir veya bölge. Ne zaman birden çok seçime izin verilen, sürekli ve ayrık seçimi her zaman, bölge (kutu) seçimleri için destek sırasında desteklenmelidir isteğe bağlıdır. Bölge seçim listesi gövdesi içinde beyaz boşluk sürükleyerek başlatılır.  


| Nesne | Seçim |
|--------|------------|
| List | Bitişik |
| List | Ayrık |
| List | Bölge |

 Bir listede bir kez tıklayarak tıklayarak oluştuğu satırı seçer. Kullanıcı yerinde düzenleme destekleyen bir liste hücreyi tıklatın olursa, hücre da hemen yerinde düzenleme için etkinleştirilir. Aksi takdirde, tüm satırı hemen seçilir ve bir vurgulama gösterilmektedir.  

 Liste gövdesinde sürükleyerek üç şey yapar:  

-   Kayıt Seçimi liste destekliyorsa ve fare aşağı boşluk varsa başlatır.  

-   Bir sürükleme kaynağı olan bir listesi veya satır destekliyorsa, bir Sürükle ve bırak işlemi başlatır.  

-   Geçerli satırı seçer  

##### <a name="in-place-editing"></a>Yerinde düzenleme  
 Yerinde düzenleme izin verildiğinde, iki temel modeli vardır: Basit Düzen denetimi ve özellik Seçici. Bir basit düzen denetimi ile içeriği vurgulanan ve kullanıcı yerinde düzenleme etkin olarak girişi için hazır olur. Özellik Seçici uygulanan burada özellik Seçici çağıran düğme yerinde düzenleme modu etkinleştirilir ve geçerli seçimi Vurgulanmayan sonra görüntülenir. Seçici düğmesi hücresinde sağa dayalı olmalıdır. Yerinde düzenleme örnekler için bkz **Özellikler penceresi** ve **görev listesi** Visual Studio'da.  

##### <a name="keyboard-support"></a>Klavye desteği  
 Seçim listeleri ve Kılavuzlar klavye desteği, standart Windows kuralları aşağıdaki gibidir:  

-   Ok tuşları listenin odağı hareket ettirildiğinde her satır/hücre Ekle'ye gidin.  

-   SHIFT + ok ok tuşlarını yönünde bir aralık seçimi gerçekleştirir.  

-   CTRL + ok ekleme ve ayrık bir seçim oluşturma seçim, liste öğelerini kaldırma arasında boşluk değiştirir tarafından izlenen.  

-   İç içe Hiyerarşiler içermelidir kılavuzlar, üst satırın sağ ok tuşu genişletir ve bir sol ok tuşunu daraltır.  

-   Sekme tuşunu odak hücreler düzenlenebilir durumlarda geçerli satırda hücreleri arasında taşır.  

-   Varsayılan komut Enter tuşunu listedeki öğeye gerçekleştirir (genellikle **açık**).  

-   Yerinde düzenleme için şu anda seçili hücreden F2 tuşuna etkinleştirir.  

##  <a name="BKMK_PersistenceAndSavingSettings"></a> Kalıcılığı ve ayarları kaydediliyor  

### <a name="overview"></a>Genel Bakış  
 Visual Studio'da her yazılım bileşen kendi durumu ve Kalıcılık için genellikle sorumlu olsa da, Visual Studio gibi bazı durumlarda, ayarları otomatik olarak penceresi boyutları ve pozisyonları ile kaydeder. Aşağıdaki tabloda, otomatik olarak kaydedilir ve açık bir kullanıcı gerektiren veya gerçekleştirilecek eylemi programlanmış ayarlarını birleşimidir.  

|Nesne|Ne kaydetmek için|Ne zaman Kaydet|Kaydedileceği yeri|  
|------------|------------------|------------------|-------------------|  
|Seçilebilir nesne (örneğin, bir kod satırı)|Kod satırında bir kesme noktası<br /><br /> Kod satırı ile ilişkili bir kullanıcı kısayol|Proje zaman kaydedilir|**Kullanıcı seçenekleri (. suo)** proje dosyası|  
|İletişim kutusu|Taşınmış, iletişim kutusunda, konumu<br /><br /> Kullanıcı iletişim kutusundaki en son kullanılan görünümü|Ne zaman iletişim kutusunu kapatır<br /><br /> Visual Studio oturumu sona erdiğinde|Bellekte<br /><br /> Kayıt defterinde **HKEY_Current_User**|  
|Pencere|Pencerenin konumunu ve boyutunu|Ne zaman pencereyi kapatır<br /><br /> Visual Studio modu değiştiğinde<br /><br /> Visual Studio oturumu sona erdiğinde|**Kullanıcı seçenekleri (. suo)** proje dosyası<br /><br /> Pencere ayarları için özel seçenekleri dosyası|  
|Belge|Belgedeki geçerli seçimi<br /><br /> Belgenin görünümünü<br /><br /> Kullanıcı ziyaret son çeşitli yerlerde|Belgenin ne zaman kaydedilir|**Kullanıcı seçenekleri (. suo)** proje dosyası|  
|Proje|Dosya başvuruları<br /><br /> Disk üzerindeki dizinler başvuruları<br /><br /> Diğer yazılım başvuruları<br /><br /> Bileşenler<br /><br /> Proje hakkında durum bilgileri|Proje zaman kaydedilir|Proje dosyası|  
|Çözüm|Proje başvuruları<br /><br /> Dosya başvuruları|Ne zaman proje veya çözüm kaydedildi|**Çözüm (.sln)** dosyası|  
|Ayarlarında **Araçlar > Seçenekler**|Klavye özelleştirmeleri<br /><br /> Araç çubuğunu özelleştirme<br /><br /> Renk düzenleri|Zaman **Araçlar > Seçenekler** iletişim kutusunu kapatır<br /><br /> Visual Studio oturumu sona erdiğinde|Kayıt defterinde **HKEY_Current_User**|  

 Hangi kullanıcı yapıyor ve bunlar yaparken, proje veya çözüm dosyasının kendisini bir parçası olarak bir parçası olarak bir ayar (oturumu sırasında), diske kaydedilir (oturumları arasında bir kayıt defteri ayarı olarak), bellekte kaydediliyor olup olmadığını belirleyen **çözümü Seçenekleri (. suo)** dosya ya da yazılım bileşeni yalnızca o özel ayarlar dosyası olarak bilmektedir. Yukarıdaki tabloda ayarları kaydedilebilmesi için çeşitli olayları gösterir. Ancak, bazen durumu kaydetmek isteyebilirsiniz vardır:  

-   Kullanıcı iletişim kutusu veya pencere konumu değiştiğinde  

-   Ne zaman kullanıcı için başka bir pencere odağı aktarır.  

-   Hata ayıklama modu olarak kullanıcı gelen geçiş yaptığında tasarlama  

-   Kullanıcı hesabını devre dışı oturum açtığında  

-   Ne zaman bilgisayar hazırda beklemeye veya kapatıldığında  

-   Bilgisayar/sabit sürücüyü hakkında yeniden biçimlendirildi ve yeniden kurmanız olduğunda  

### <a name="window-configurations"></a>Pencere yapılandırmaları  
 Bir pencere yapılandırmasının geliştirme ortamının temel sunu'dur - mevcut araç pencereleri listesini ve bunların düzenlenme şeklini oluşan bir düzeni değildir. Bunlar en son ne zaman Visual Studio IDE, pencere düzenini aynı görünür bir kullanıcı başlatır, çıkıldı şekilde IDE (IDE windows) tarafından yönetilen windows için kullanıcı başına düzen bilgilerini kalıcı hale getirilir. IDE pencerelerinde konumu ve durumu XML biçimi özel seçenekleri dosyasında kalıcıdır. IDE'ye yüklü paketleri tarafından oluşturulan araç pencereleri, durum bilgilerinin kayıt defterinde kalıcı olabilir veya kullanıcı başına olabilir.  

#### <a name="profile-specific-layouts"></a>Profili özel düzenler  
 Her profil aracı pencere düzenlerini, belirli bir geliştirici kişilikler için tanıdık bir şekilde organize içerir (Visual C++ geliştiricileri beklediğiniz görmek **Çözüm Gezgini** görmekC#geliştiricilerinsıradaIDE'ninsoltarafındaki **Çözüm Gezgini** sağ). Kullanıcı bir başlatma profilinde seçtikten sonra profili özel pencere düzenlerini yüklenir. Bir paket yazarı için pencere yapılandırmasının kullanıcının yaptığı değişiklikleri daha sonra kalıcı olduğunu bilmek, müşteri deneyimi için en uygun pencere düzenini belirlemeniz gerekir.  

##  <a name="BKMK_TouchInput"></a> Dokunma girişi  
 Kullanıcılar, dokunmatik cihazlarda giderek Microsoft geliştirme ürünleri kullanıyorsunuz. Ancak, dokunmatik cihazlarda geliştirme araçlarını kullanmayı zorlaştıran engelleri vardır. Kullanıcılar, güvenilir ve kesin dokunma deneyimi sağlamak üzere Ürünlerimizin istedikleri. Bu yönergelerin amacı hangi touch özellikleri eklemelerine ve Visual Studio ve ilgili ürünler arasında tutarlı dokunma deneyimi teşvik etmek için hakkında kararlar bildirmektir.  

### <a name="levels-of-experience"></a>Deneyimi düzeyleri  
 Aşağıdaki düzeylerde deneyimi sunmak için gereken touch özellikleri istenen touch yatırım ilgi düzeyini temel ekiplerin karar vermenize yardımcı olmak için bir kılavuz olarak görev yapacak yöneliktir.  

-   **Temel deneyim** hiçbir atılacak uçlarını işlerini boyunca olduklarından yetenekleri sağlamak isteyen takımlara touch aranır.  

-   **Deneyimi en iyi duruma getirilmiş** en ortak dokunma özellikler (örneğin, Internet tarayıcı uygulamalarında genellikle mevcut kodlar) sağlamak isteyen takımlara yöneliktir.  

-   **Yükseltilmiş deneyimi** gibi özellikleri eklemek isteyen takımlar için olarak hareketlerine veya kendi uygulama yapabileceğiniz diğer isteğe bağlı özellikleri ilk dokunmatik ekranları kolay.  

||Temel deneyim|En iyi duruma getirilmiş deneyimi|Yükseltilmiş deneyimi|  
|-|----------------------|--------------------------|-------------------------|  
|Kullanıcılara sağlar...|Kod ve çözüm/proje-seviyesi atılacak uçlarını okuma|Bakım, refactors ve gezinme görevleri|Tutarlı, sezgisel ve akıcı bir deneyim güvenle çalışır.|  
|Düzenleyici|Dokunmatik kaydırma ve seçim<br /><br /> Atlama ve basın + sürükleme için kaydırma çubuğunu dokunun|Sıkıştırarak yakınlaştırma<br /><br /> Hızlı kaydırma<br /><br /> Seçim<br /><br /> Bağlam menüsünün kullanımı kolay||  
|Üst araç pencereleri|Liste kaydırma<br /><br /> Öğe seçimi<br /><br /> Atlama ve basın + sürükleme için kaydırma çubuğunu dokunun|Kolay öğesi kaydırmayı ve seçimi||  
|Pencereleme||Pencereyi yeniden boyutlandırma<br /><br /> Hızlı erişim||  
|Belge iyi||Açık dosyalar arasında kolay gezinti||  
|Hareketler||IDE arasında ortak hareketlerini çalıştığından emin olmak|Hareket tabanlı eylemleri<br /><br /> Sürükle ve bırak ve tasarımcıları destekler|  
|Dikkat edilecek diğer noktalar|||Özel Ekran Klavyesi|  

#### <a name="gestures"></a>Hareketler  
 Hareketlerini kullanıcılar, aksi takdirde daha karmaşık bir etkileşimi gerektiren komutlar için bir kısayol sağlar. Üzerinde Windows yönergelerine başvurun [Masaüstü uygulamaları için ortak dokunma hareketlerini](/windows/desktop/wintouch/windows-touch-gestures-overview)ve kaydırma ve yakınlaştırma gibi basit hareketler dahil olmak üzere çoğu hareketler için bu yönergeleri izleyin.