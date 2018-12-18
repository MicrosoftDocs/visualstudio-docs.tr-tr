---
title: Bildirimler ve ilerleme durumu için Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aee6e5656142d0597ff6101da5e2e5f690f8fcc5
ms.sourcegitcommit: b6dfa1bdf4c23c2e341754454bbd4758db2218e0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48863962"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Bildirimler ve Visual Studio için ilerleme durumu
##  <a name="BKMK_NotificationSystems"></a> Bildirim sistemleri  
  
### <a name="overview"></a>Genel Bakış  
 Visual Studio yazılım geliştirme görevlerini neler olduğunu kullanıcıya bildirmek için birkaç yolu vardır.  
  
 Her türlü bildirim uygularken:  
  
-   **Bildirimleri göndermek için en az sayıda** etkili bir sayı. Bildirim iletileri, Visual Studio kullanıcıların çoğu veya kullanıcılarının belirli özellik/özellik alanı için uygulamanız gerekir. Bildirimleri aşırı kullanımını kullanıcı sidetrack veya algılanan sistem kullanım kolaylığı kötüleşmesiyle olabilir.  
  
-   **NET, eyleme dönüştürülebilir iletileri sunmak emin olun** kullanıcının daha karmaşık seçimleri yapmak ve başka bir eylemde bulunmadan uygun bağlamı çağırmak için kullanabilirsiniz.  
  
-   **Zaman uyumlu ve zaman uyumsuz iletileri uygun şekilde sunar.** Zaman uyumlu bildirimleri hemen ilgilenilmesi gereken bir şey, bir web hizmeti zaman kilitleniyor veya bir kod gibi özel durum belirtin. Kullanıcı, bu durumda hemen kalıcı bir iletişim kutusu gibi kendi girişlerini gerektirdiği şekilde yansıtmalıdır. Zaman uyumsuz bildirimler, kullanıcı hakkında bilmeniz gereken ancak gibi bir yapı işlemi tamamlandığında veya bir web sitesi dağıtımı tamamlandıktan hemen sonra yapması gereken değil ' dir. Bu iletileri, daha fazla ortam ve kullanıcının Görev akışı kesme değil.  
  
-   **Yalnızca gerekli olduğunda kullanıcıların daha fazla eylem fotoğrafını çekmenizi engellemek kalıcı iletişim kutuları kullanma** sıkan ileti veya iletişim kutusunda sunulan bir karar vermeden önce.  
  
-   **Ortam bildirimler artık geçerli olmayan kaldırılır.** Kullanıcının hakkında bilgilendirildi sorunu gidermek için eylem zaten kullanımda durumunda bir bildirimi kapatmak gerek yoktur.  
  
-   **Bildirimler için false bağıntılar açabilir dikkat edin.** Kullanıcılar, aslında nedensel hiçbir ilişki değiştirildiği bir veya daha fazla eylemlerini bildirim tetiklediğini düşünüyorsanız. Clear bağlamı, tetikleyici ve bildirim kaynağı hakkında bildirim iletisi olması.  
  
### <a name="choosing-the-right-method"></a>Doğru yöntemi seçme  
 İletinin kullanıcıya bildirmek için doğru yöntemi seçme içinde size yardımcı olması için bu tabloyu kullanın.  
  
|Yöntem|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|Kullanmayın|  
|------------|---------|----------------|  
|[Kalıcı bir hata iletisi iletişim kutuları](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Devam etmeden önce bir kullanıcı yanıtı gerektiğinde kullanın.|Kullanıcı engelleme ve bunların akışını kesintiye gerek olduğunda kullanmayın. Başka bir, çalışılmasını daha az sezgisel şekilde görüntülenmesi mümkünse kalıcı iletişim kutuları kullanmaktan kaçının.|  
|[IDE durum çubuğu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Durumu ile ilgili bir işlemin ortam metin tabanlı bilgiler olduğunda kullanın.|Tek başına kullanmayın. En iyi başka bir geri bildirim mekanizması ile birlikte kullanılır.|  
|[Katıştırılmış bilgi çubuğu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|Araç penceresi veya belge penceresi ilerleme durumunu, hata durumu, sonuçları ve/veya eyleme dönüştürülebilir bilgiler bildirmek için kullanın.|Bilgileri bilgi çubuğu yerleştirildiği konum için uygun değilse kullanmayın.<br /><br /> Belge/araç penceresi dışında kullanmayın.|  
|[Fare imleci değişiklikleri](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Bir işlem sorunu bildirmek için kullanılabilir. Ayrıca, sürükle ve bırak ilerleme veya fare imlecini çizim modu gibi belirli modunda olduğunda gibi fare durumu değişikliği olduğunu bildirmek için kullanılır.|Kısa Süren değişiklikler için kullanmayın veya, fluttering, imleç (örneğin, uzun çalışan bir işleme yerine tüm işlem bölümlerini bağlı değilken) olasılığı yüksektir.|  
|[İlerleme göstergesi](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Rapor işleniyor (belirli veya belirsiz) ihtiyacınız olduğunda kullanın. İlerleme göstergesi türleri ve belirli kullanım her biri için çeşitli vardır. Bkz: [ilerleme göstergeleri](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||  
|[Visual Studio bildirimler penceresi](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|Bildirimler penceresi herkese açık şekilde genişletilebilir değildir. Ancak, bir dizi ileti lisans ve Visual Studio veya paketler için güncelleştirmelerin bilgilendirici bildirimleri kritik sorunlar da dahil olmak üzere Visual Studio hakkında iletişim kurmak için kullanılır.|Diğer bildirim türleri için kullanmayın.|  
|[Hata listesi](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Sorun (uyarı/hata/bilgisi) sorun yaşıyor doğrudan kullanıcının şu anda açık olan çözüme ilişkili olması durumunda, bunlar kod üzerinde harekete gerekebilir.<br /><br /> Bu, örneğin aşağıdakileri içerir:<br /><br /> -Derleyici iletileri (uyarı/hata/bilgisi)<br /><br /> -Kod hakkında kod Çözümleyicisi/tanılama iletileri<br /><br /> -İleti oluşturma<br /><br /> , Proje veya çözüm dosyaları ile ilgili sorunlar için uygun olabilir, ancak Çözüm Gezgini göstergesi önce göz önünde bulundurun.|Herhangi bir kullanıcının açık olan çözüme kod ilişkisine sahip olmayan öğeler için kullanmayın.|  
|Düzenleyici bildirimleri: ampul|Dosya Aç var olan bir sorunu gidermek için kullanılabilecek bir düzeltme sahip olduğunuzda kullanın.<br /><br /> Ampul de yeniden düzenlemeler gibi isteğe bağlı olarak kullanıcı kodunda alınır ancak bu durumda "bildirim style" görünmez hızlı Eylemler barındırmak için kullanılması gerektiğini unutmayın.|Açık dosyanın herhangi bir ilişkisi olmayan öğeler için kullanmayın.|  
|Düzenleyici bildirimleri: dalgalı çizgiler|Belirli bir aralık açık kodlarını (örneğin, bir kırmızı dalgalı hatalara) ile ilgili bir sorun için kullanıcıyı uyarmak için bu seçeneği kullanın.|Belirli bir aralığa açık kodlarını ilişkili olmayan öğeler için kullanmayın.|  
|[Katıştırılmış durum çubukları](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|İlgili içerik veya özel araç penceresi, belge penceresi ya da iletişim penceresi bağlam içinde işlem durumu sağlamak için bu seçeneği kullanın.|Genel Ürün bildirimler, işlemleri veya içeriğe hiçbir ilişki belirli pencereye sahip olmayan öğeler için kullanmayın.|  
|[Windows Tepsisi bildirimi](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|İşlem dışı işlemler için bildirimleri yüzey veya Yahoo! companion uygulamaları için kullanın.|IDE ilgili bildirimler için kullanmayın.|  
|[Bildirim baloncuklar](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Uzak bir işlem bildirim veya değiştirmek için kullanın **dışında** IDE.|Kullanıcı işlemlerinin bildirmek için bir yol kullanmayın **içinde** IDE.|  
  
### <a name="notification-methods"></a>Bildirim yöntemleri  
  
####  <a name="BKMK_ModalErrorMessageDialogs"></a> Kalıcı bir hata iletisi iletişim kutuları  
 Bir kalıcı bir hata iletisi iletişim kutusu, kullanıcının onayı veya eylem gerektiren bir hata iletisi görüntülemek için kullanılır.  
  
 ![Kalıcı bir hata iletisi](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901 01_ModalErrorMessage")  
  
 **Geçersiz bir bağlantı dizesi için bir veritabanı kullanıcısı uyarı kalıcı bir hata iletisi iletişim kutusu**  
  
####  <a name="BKMK_IDEStatusBar"></a> IDE durum çubuğu  
 Kullanıcılar durum çubuğu metni fark olasılığını çepeçevre bilgisayar deneyimi ve belirli Windows platform deneyimiyle ilişkilidir. Visual Studio müşteri tabanı, olsa bile bilgili Windows kullanıcıları değişiklikleri durum çubuğunda kaçırabilirsiniz her iki alanda deneyimli olma eğilimindedir. Bu nedenle, başka bir yerde bilgi sunulan için durum çubuğunu en iyi bilgilendirme amacıyla veya yedekli ipucu olarak kullanılır. Bir iletişim kutusu veya bildirimleri araç penceresinde herhangi bir türden kullanıcı hemen çözümlenmelidir önemli bilgileri sağlanmalıdır.  
  
 Visual Studio durum çubuğunda görüntülenecek bilgi birkaç türde izin vermek için tasarlanmıştır. Bölgeler geribildirim, Tasarımcı, ilerleme çubuğu, animasyon ve istemci için ayrılmıştır.  
  
 Tasarımcı bölge ve geri bildirim bölge her zaman görünürdür. İlerleme çubuğu ve animasyon bölgeler her zaman kullanıcı bağlamı dayalı ve dinamik. Tasarımcı bölge eşlik eden bir kaynak metin iletisi için çekilen dizenin uzunluğunu tarafından belirlenen statik bir genişliğe sahiptir. Bu, bir kod değişikliği gerekmeden genişliğini yeniden boyutlandırmak yerelleştirme sağlar. İngilizce için bu dizenin kabaca 220 piksel genişliğidir. Tasarımcı bölge normal şekilde davranır ve geri bildirim bölge kalan alanı devralarak.  
  
 Durum çubuğu IDE hata ayıklama modunda olduğunda gibi çeşitli IDE durumu değişiklikleri iletişim kurarak görsel açıdan ilgi çekici ve işlevsel değer eklemek için de renklendirilir.  
  
 ![IDE durum çubuğu renk değişiklikleri](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901 02_IDEStatusBar")  
  
 **IDE durum çubuğu renk**  
  
####  <a name="BKMK_EmbeddedInfobar"></a> Katıştırılmış bilgi çubuğu  
 Bir bilgi çubuğu bir belge penceresi veya araç penceresinin en üstündeki durum veya koşulun kullanıcıya bildirmek için kullanılabilir. Böylece kullanıcı bir kolayca harekete şekilde komutları da sağlayabilir. Bilgi çubuğu, bir standart Kabuk denetimidir. Kendi oluşturmaktan kaçının, hangi hareket ve IDE içinde başkalarıyla tutarsız olarak görünür. Bkz: [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) uygulamasının Ayrıntılar ve kullanım kılavuzu için.  
  
 ![Bilgi çubuğu gömülü](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901 03_EmbeddedInfobar")  
  
 **Bir bilgi çubuğu, bir belge penceresinde IDE geçmiş hata ayıklama modunda ve standart hata ayıklama modunda çalıştığı gibi düzenleyici aynı şekilde yanıt vermez kullanıcıyı uyarmak katıştırılmış.**  
  
####  <a name="BKMK_MouseCursorChanges"></a> Fare imleci değişiklikleri  
 Fare imlecini değiştirilirken VSColor hizmete bağlıdır ve imleç zaten ilişkili renk kullanın. İmleç belirten devam eden bir işlem için kullanılabilir, hem de kullanıcı sürüklediğiniz, üzerine bırakılan veya bir nesne seçmek için kullanılan bir hedef nereden geldiği bölgeleri isabet.  
  
 Kullanıcı başka bir giriş ifade dan engelleyen, bir işlem için tüm kullanılabilir CPU süresi yalnızca ayrılmalıdır meşgul bekleme fare imleci kullanın. Çoklu iş parçacığı kullanan iyi-yazılan uygulamalar ile çoğu durumda, diğer işlemleri yapmasını kullanıcıların ne zaman engelleneceğini kez seyrek olmalıdır.  
  
 Başka bir yerde yedekli bir işaret bilgi sunulan imleç yararlıdır göz önünde bulundurun. Kullanıcı çözülmesi gereken kritik tek yolu özellikle bir şey aktarmaya çalışırken kullanıcıyla iletişim kurma, bir imleç değiştikçe güvenmeyin.  
  
####  <a name="BKMK_NotSysProgressIndicators"></a> İlerleme göstergesi  
 İlerleme göstergesi, tamamlanması birkaç saniye Süren işlemleri sırasında kullanıcı geri bildirim vermek için önemlidir. İlerleme göstergeleri gösterilebileceği yerinde (başlatma noktası devam eden eylem), yakın bir gömülü durum çubuğu, kalıcı bir iletişim kutusu veya Visual Studio durum çubuğunda. Sunulan yönergeleri [ilerleme göstergeleri](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) kendi kullanın ve uygulama ile ilgili.  
  
####  <a name="BKMK_VSNotificationsToolWindow"></a> Visual Studio bildirimler penceresi  
 Visual Studio bildirimler penceresi geliştiriciler lisanslama, ortam (Visual Studio), uzantılar ve güncelleştirmeler hakkında bilgilendirir. Kullanıcılar tek tek bildirimleri kapatabilirsiniz veya belirli türdeki bildirimlerin göz ardı etmeyi seçebilir. Yoksayılan bildirimleri listesi içinde yönetilen bir **Araçlar > Seçenekler** sayfası.  
  
 Bildirimler penceresi şu anda Genişletilebilir değildir.  
  
 ![Visual Studio bildirimler penceresi](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901 06_VSNotificationsWindow")  
  
 **Visual Studio bildirimleri araç penceresi**  
  
####  <a name="BKMK_ErrorList"></a> Hata listesi  
 Hata listesindeki bir bildirim belirtin hataları ve Uyarıları, derleme sırasında oluşan ve derleme işlemi ya da belirli bir kod hata koduna gidin izin verir.  
  
 ![Hata listesi](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901 08_ErrorList")  
  
 **Visual Studio hata listesi**  
  
####  <a name="BKMK_EmbeddedStatusBars"></a> Katıştırılmış durum çubukları  
 Etkin belge penceresi ve kullanıcının içeriği ve/veya sistem yanıtları güncelleştirme bilgileri ayarlanan istemci bölge bağlamla IDE durum çubuğu dinamik olduğu için bilgi sürekli bir görünümünü sağlamak ya da durum uzun vadeli şirket vermek zor zaman uyumsuz işlem. Örneğin, IDE durum çubuğu birden çok çalıştırır ve/veya vakit kaybetmeden eyleme öğe seçimleri için test çalıştırması sonuç bildirimleri için uygun değil. Belge veya araç penceresinin, burada, kullanıcı bir seçim yapar veya bir işlem başlatır bağlamında gibi durum bilgileri korumak önemlidir.  
  
 ![Katıştırılmış durum çubuğu](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901 09_EmbeddedStatusBar")  
  
 **Visual Studio'da katıştırılmış durum çubuğu**  
  
####  <a name="BKMK_WindowsTray"></a> Windows Tepsisi bildirimi  
 Bildirim alanı sistemidir yanındaki Windows, Windows görev çubuğundaki saat. Kullanıcının ekran çözünürlüğünü değiştirme veya yazılım güncelleştirmelerini almak gibi sistem genelinde görevler için bir bağlam menüsü alabilmesi simgeler Bu alanda birçok yardımcı programları ve yazılım bileşenleri sağlar.  
  
 Ortam düzeyindeki bildirimleri Visual Studio bildirim Merkezi'nde Windows bildirim alanında ortaya çıkacak.  
  
####  <a name="BKMK_NotificationBubbles"></a> Bildirim baloncuklar  
 Bildirim baloncuklar Düzenleyicisi/Tasarımcısı içinde bilgilendirici veya Windows bildirim alanında bir parçası olarak görünür. Kullanıcı, kritik olmayan bildirimler için bir avantajı olan, daha sonra çözümleyebilir ve sorunları bu kabarcıkların algılar. Kabarcıkların kullanıcı hemen çözmeniz gerekir önemli bilgiler için uygun değildir. Visual Studio'da bildirim baloncuklar kullanıyorsanız, izleyip [bildirim baloncuklar Windows Masaüstü kılavuzunu](/windows/desktop/uxguide/mess-notif).  
  
 ![Bildirim Kabarcık](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901 07_NotificationBubbles")  
  
 **Visual Studio için kullanılan Windows bildirim alanında bildirim Kabarcık**  
  
##  <a name="BKMK_ProgressIndicators"></a> İlerleme göstergesi  
  
### <a name="overview"></a>Genel Bakış  
 İlerleme göstergesi kullanıcıya geribildirim vermek için bir bildirim sistemi önemli bir parçasıdır. İşlemler ve işlem tamamlanır, kullanıcı bilgi verin. İlerleme çubukları, dönen işaretçileri ve animasyonlu simgeler tanıdık bir gösterge türleri içerir. Tür ve bir İlerleme göstergesi yerleşimini ne raporlanan dahil olmak üzere, bağlam ve ne kadar işlem ya da işlemin tamamlanması için gereken bağlıdır.  
  
#### <a name="factors"></a>Faktörleri  
 Hangi Gösterge türünü uygun olduğunu belirlemek için aşağıdaki etmenlere belirlemeniz gerekir.  
  
1.  **Zamanlama:** sürenin uzunluğunu işlemi alır  
  
2.  **Şekil:** işlemi (kilit işlemi tamamlanana kadar kullanıcı Arabirimi) ortama kalıcı olup  
  
3.  **Kalıcı/geçici:** olup olmadığını ilerleme sonucunu daha sonra bildirilen ve/veya görüntülenebilir olması gerekir  
  
4.  **Kararlı/belirsiz:** işlem bitiş saati ve ilerleme durumunu hesaplanabilir  
  
5.  **Grafik/Textual konumu:** ilerleme veya işlem bir ileti ya da ağaç denetimi gibi belirli denetimi gövdesine yakalanan satır içi olup  
  
6.  **Yakınlık:** olup olmadığını ilerleme yakınında ilişkili kullanıcı Arabirimi olması gerekir. (Örneğin, uzakta olabilir, durum çubuğunda olabilir veya bu işlemi başlatan düğme olmak zorunda?)  
  
#### <a name="determinate-progress"></a>Kararlı ilerleme  
  
|İlerleme durumu türü|Ne zaman ve nasıl kullanılır|Notlar|  
|-------------------|-------------------------|-----------|  
|İlerleme çubuğu (kararlı)|Beklenen süre > 5 saniye.<br /><br /> Metinsel işlem ayrıntılarını içerebilir.|**Yoksa** animasyonda metin ekleyin.|  
|Bilgi Çubuğu|Bağlamsal kullanıcı Arabirimi ile ilişkili ileti. Bkz: [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Metinsel işlem ayrıntılarını içerebilir.|**Yoksa** birden çok infobars birden çok işlem belirtmek, ihtiyacınız olduğunda kullanın. Yığın ilerleme çubuğunu kullanın.|  
|Çıktı Penceresi|Geçici bildirim: kullanıcının uygulama düzeyinde işlem istediğiniz **gözden** tamamlandıktan sonra ayrıntıları.|**Yoksa** kullanıcı verilerini daha sonra başvurmanız gerekiyorsa kullanın.|  
|Günlük dosyası|Önemli olduğunda durumlarda intransient bildirimi ile eşleştirilmiş **Kaydet** tamamlandıktan sonra ayrıntıları.||  
|Durum çubuğu|Geçici bildirim: kullanıcının uygulama düzeyinde işlem olacak **gerek** tamamlandıktan sonra ayrıntıları.<br /><br /> Katıştırılmış bir ilerleme çubuğu içerir.<br /><br /> Metinsel işlem ayrıntılarını içerebilir.||  
  
#### <a name="indeterminate-progress"></a>Belirsiz ilerleme  
  
|İlerleme durumu türü|Ne zaman ve nasıl kullanılır|Notlar|  
|-------------------|-------------------------|-----------|  
|İlerleme çubuğu (belirsiz)|Beklenen süre > 5 saniye.<br /><br /> Metinsel işlem ayrıntılarını içerebilir.|**Yoksa** animasyonda metin ekleyin.|  
|Karıncaların (animasyonlu yatay nokta)|Sunucuya gidiş dönüş.<br /><br /> Bağlam yakın noktası üst kapsayıcısının üst kısmında yer.|**Yoksa** tüm kapsayıcı tarafından shapemap değil ise kullanın.|  
|Değer değiştirici (ilerleme halkası)|Bağlamsal kullanıcı Arabirimi ile alan önemli bir unsur olduğu ilgili veya işlemi.<br /><br /> Metinsel işlem ayrıntılarını içerebilir.||  
|Bilgi Çubuğu|Bağlamsal kullanıcı Arabirimi ile ilişkili ileti. Bkz: [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**Yoksa** birden çok infobars birden çok işlem belirtmek, ihtiyacınız olduğunda kullanın. Yığın ilerleme çubuğunu kullanın.|  
|Çıktı Penceresi|Geçici bildirim:, kullanıcı uygulama düzeyinde işlem istediğiniz **gözden** tamamlandıktan sonra ayrıntıları.|**Yoksa** oturumlarda kalıcı hale getirmek için gereken bilgileri belirtmek için kullanın.|  
|Günlük dosyası|Önemli olduğunda durumlarda intransient bildirimi ile eşleştirilmiş **Kaydet** tamamlandıktan sonra ayrıntıları.||  
|Durum çubuğu|Geçici bildirim: kullanıcının uygulama düzeyinde işlem olacak **gerek** tamamlandıktan sonra ayrıntıları.<br /><br /> Katıştırılmış bir ilerleme çubuğu içerir.<br /><br /> Metinsel işlem ayrıntılarını içerebilir.||  
  
### <a name="progress-indicator-types"></a>İlerleme göstergesi türleri  
  
#### <a name="progress-bars"></a>İlerleme çubukları  
  
##### <a name="indeterminate"></a>Belirsiz  
 ![Belirsiz ilerleme çubuğu](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901 04_Indeterminate")  
  
 **Belirsiz ilerleme çubuğu**  
  
 Bir işlemin genel ilerleme durumu "Belirsiz" anlamına gelir veya işlem belirlenemiyor. Belirsiz ilerleme çubukları sınırsız süreyi gerektiren veya bilinmeyen bir nesne sayısını erişim işlemleri için kullanın. Neler olduğunu eşlik edecek bir metinsel kullanın. Zaman aşımları, zamana bağlı işlemler için sınırları vermek için kullanın. Belirsiz ilerleme çubukları, ilerleme yapılıyor, ancak herhangi bir bilgi sağlamaz göstermek için animasyon kullanın. Doğruluk tek başına yalnızca olası eksikliği dayalı bir belirsiz ilerleme çubuğu seçmeyin.  
  
##### <a name="determinate"></a>Kararlı  
 ![Kararlı ilerleme çubuğu](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901 05_Determinate")  
  
 **Kararlı ilerleme çubuğu**  
  
 Bir işlem veya işlem bir sınırlanmış süreyi gerektirdiğini bile bu süreyi doğru şekilde tahmin edilemez "Belirli" anlamına gelir. Tamamlama açıkça belirtin. Yüzde 100'e gidin, işleminin tamamlanmadığı sürece bir ilerleme çubuğu izin vermeyin. Kararlı ilerleme çubuğu animasyon, 0'dan % 100 soldan sağa taşır.  
  
 Hiçbir zaman bir işlemi sırasında geriye dönük bir İlerleme göstergesi taşıyın. Çubuk, işlemi başladığında kararlı bir şekilde ilerler ve sona erdiğinde, % 100 ulaşın. İlerleme çubuğu noktasındaki kullanıcı ne kadar tüm operasyon kaç adımla daha uğraşmanız gerekir bağımsız olarak gerçekleştireceği hakkında fikir vermektir.  
  
##### <a name="concurrent-reporting-stacked-progress-bars"></a>Eşzamanlı (Yığın ilerleme çubukları) raporlama  
 Bir işlem - uzun zaman alacaksa birkaç dakika - sonra iki ilerleme çubukları belki de kullanılabilir, biri, bir işlemin genel ilerleme durumu ve ilerlemeyi, geçerli adım için başka gösterir. Bir Kurulum programı fazla dosya kopyalanıyorsa, örneğin, ardından bir ilerleme çubuğu ne kadar tüm saniyenin yüzde geçerli dosyanın belirtebilir ya da dizin kopyalanırken işleminde belirtmek için kullanılabilir. Beşten fazla eşzamanlı işlem veya yığın ilerleme çubukları kullanarak işlemleri bildirmez. Beşten fazla eşzamanlı işlem veya rapor işlemler varsa, kalıcı bir iletişim kutusu ile bir iptal düğmesi ve rapor ilerleme ayrıntılarını çıkış penceresine kullanın.  
  
##### <a name="textual-descriptions"></a>Metin açıklamaları  
 Neler olduğunu eşlik edecek bir metinsel ve tahmini tamamlanma süresi kullanın. Bir işlemin ne kadar sürer belirlemek mümkün ise, geri bildirim vermek için daha iyi bir seçenek bir ilerleme çubuğu yerine animasyonlu simge olabilir.  
  
 Visual Studio, Visual Studio'ya entegre herhangi bir ürünü tarafından kullanılan durum çubuğunda bir standart ilerleme çubuğu sağlar. Durum çubuğu metni İlerleme çubuğunda bir animasyon görünür sırada neler olduğunu, metin açıklamaları için güncelleştirilebilir.  
  
#### <a name="other-progress-indicators"></a>Diğer bir İlerleme göstergesi  
  
##### <a name="ants-animated-horizontal-dots"></a>Karıncaların (animasyonlu yatay nokta)  
 ![İlerleme karıncaların](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903 01_Ants")  
  
 "Karıncaların," yatay animasyonlu nokta, bir belirsiz gidiş dönüş sunucu işlemi için görsel bir başvuru sağlar.  
  
##### <a name="spinner-progress-ring"></a>Değer değiştirici (ilerleme halkası)  
 ![Devam eden değer değiştiricinin](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903 02_Spinner")  
  
 Değer değiştirici (olarak da bilinen bir "ilerleme halkası") ile ilgili bağlamsal UI öncelikli olarak kullanılan bir belirsiz ilerleme göstergesidir. Bir değer değiştirici yakın bir metinsel kategorisi üst bilgisi, ileti veya denetim gibi ilgili içeriğini görüntüler.  
  
##### <a name="cursor-feedback"></a>İmleç geri bildirim  
 2-7 dakika arasında sürer işlemlerinde, imleç geri bildirim sağlayın. Genellikle, bu işletim sistemi tarafından sağlanan bekleme imlecini kullanarak anlamına gelir. Yönergeler için bkz MSDN makalesi [Cursors.Wait özelliği](/dotnet/api/system.windows.input.cursors.wait).  
  
#### <a name="progress-indicator-locations"></a>İlerleme göstergesi konumları  
  
##### <a name="status-bar"></a>Durum çubuğu  
 Durum çubuğu, uygulamanızın kullanıcının iş kesintiye uğratmadan kullanıcıya iletileri ve yararlı bilgileri görüntülemek için bir yer sağlar. Genellikle, pencerenin alt kısmında görüntülenen, ilerleme durumunun bir ilerleme çubuğu göstergesi ile birlikte ilerleme ölçü hakkında bir ileti içeren bir araç ipucu bölmesini olacaktır.  
  
 ![Durum çubuğunda ilerleme çubuğuyla](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903 03_StatusBarProgressBar")  
  
 **İlerleme çubuğu ile durum çubuğu**  
  
 ![Mesajlaşma ile durum çubuğu](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903 04_StatusBarMessage")  
  
 **Durum çubuğu metinsel açıklaması**  
  
##### <a name="infobar"></a>Bilgi Çubuğu  
 Bilgi çubuğu durum çubuğuna benzer bağlamsal bildirim ve mesajlaşma, hangi de ilerleme çubuğu veya değer değiştiricinin gibi belirsiz ilerleme göstergeleri ile eşleştirilmesi sağlar. Bilgi çubuğu ayrıntılı düzeyi ilerleme veya kararlı İlerleme göstergesi sağlamalıdır değil. Bkz: [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).  
  
 ![Bilgi çubuğu ilerleme çubuğu ve mesajlaşma ile](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903 05_InfoBar")  
  
 **İlerleme çubuğu ve metinsel bilgi çubuğu**  
  
 ![Bilgi çubuğu bir pencere içinde](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903 06_InfoBarInWindow")  
  
##### <a name="inline"></a>Satır içi  
 Satır içi İlerleme göstergesi ilerleme yükleyici türlerinden temsil edilebilir. İlerleme göstergesi Mesajlaşma ile genellikle eşleştirilmiş, ancak bu zorunlu değildir.  
  
 ![Satır içi ilerleme değiştiricisi](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903 07_InlineSpinner")  
  
 **Metinsel ile birleştirilmiş değiştiricisi**  
  
 ![Satır içi ilerleme çubukları Yığılmış](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903 08_InlineStackedProgress")  
  
 **Kararlı bir yığın ilerleme çubukları**  
  
 ![Satır içi ilerleme Mesajlaşma](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903 09_InlineText")  
  
 **Sunucu Gezgini satır içi metin: yenileniyor...**  
  
##### <a name="tool-windows"></a>Araç pencereleri  
 Genel İlerleme göstergesi, doğrudan araç çubuğunun altında konumlandırılmış bir belirsiz ilerleme çubuğu olarak temsil edilir.  
  
 ![Genel belirsiz ilerleme çubuğu](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903 23_GlobalIndeterminate")  
  
 **Takım Gezgini genel belirsiz ilerleme çubuğu**  
  
##### <a name="dialogs"></a>İletişim kutuları  
 İletişim kutuları ilerleme yükleyici türlerinden herhangi birini içerebilir. İlerleme göstergesi Mesajlaşma ile eşleştirilmiş yanı sıra ayrıntılı temsil eder ve alt işlemlerin İlerleme göstergesi birden fazla seviyede birlikte.  
  
 ![Birden çok İlerleme göstergesi türleri ile iletişim](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903 11_Dialog")  
  
 **Visual Studio iletişim eşzamanlı işlemler ve birden çok İlerleme göstergesi türleri**  
  
 ![İlerleme yükleyici ve mesajlaşma ile iletişim](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903 12_Dialog2")  
  
 **İlerleme yükleyici ve satır içi komut vermeye genel Mesajlaşma ile Visual Studio iletişim kutusu**  
  
##### <a name="document-well"></a>Belge iyi  
 Belge denetimleri ile birlikte birden çok ilerleme yükleyici türleri de görüntüleyebilirsiniz.  
  
 ![Belgede iyi Mesajlaşma ilerleme](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903 13_DocumentWell")  
  
 **Araç çubuğunun altında belirsiz ilerleme çubuğu**  
  
##### <a name="output-window"></a>Çıktı Penceresi  
 Çıkış penceresi işleminin ilerleme ve metinsel satır içi Mesajlaşma aracılığıyla sürekli ilerleme durumunu işlemek için uygundur. Tüm çıkış penceresi ilerleme durumunu bildirme yanı sıra durum çubuğunu kullanmanız gerekir.  
  
 ![Çıkış penceresinde Mesajlaşma ilerleme](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903 14_OutputWindow")  
  
 **Pencere devam eden işlem durumu ile çıktı ve mesajlaşma bekleyin**  
  
##  <a name="BKMK_Infobars"></a> Infobars  
  
### <a name="overview"></a>Genel Bakış  
 Kendi uyarı noktası yakın bir göstergesi kullanıcıya Infobars sağlayın ve paylaşılan bir bilgi çubuğu denetimini kullanarak görsel görünümünü ve etkileşim tutarlılık sağlar.  
  
 ![Bilgi Çubuğu](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904 01_Infobar")  
  
 **Visual Studio'da Infobars**  
  
#### <a name="appropriate-uses-for-an-infobar"></a>Bir bilgi çubuğu için uygun kullanır  
  
-   Engelleyici olmayan ancak önemli ileti geçerli bağlamla ilgili kullanıcıya vermek için  
  
-   Geçmiş hata ayıklama gibi bazı etkileşim etkileri yürüten UI belirli bir durumu veya koşulu belirtmek için  
  
-   Sistem, ne zaman bir uzantı performans sorunlarına neden olan gibi sorunları algıladı kullanıcıya bildirmek için  
  
-   Kullanıcı bir kolayca düzenleyiciye bir dosya sekmeleri ve boşlukları karma algıladığında gibi eylemler gerçekleştiren şekilde sağlamak için  
  
##### <a name="do"></a>Yapın:  
  
-   Bilgi çubuğu ileti metni, nokta ve kısa tutun.  
  
-   Bağlantılar ve düğmeler metni Sözün tutun.  
  
-   Kullanıcılara sunmak "action" seçenekleri yalnızca gerekli eylemleri gösteren az olduğundan emin olun.  
  
##### <a name="dont"></a>Yapma:  
  
-   Bir bilgi çubuğu, araç çubuğunda yerleştirilmelidir standart komutlar sunmak için kullanın.  
  
-   Bir bilgi çubuğu kalıcı bir iletişim kutusu yerine kullanın.  
  
-   Penceresi dışında kayan bir ileti oluşturun.  
  
-   Aynı pencerede faza konumda birden çok infobars kullanın.  
  
#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Aynı anda birden çok infobars gösterebilirsiniz?  
 Evet, birden çok infobars aynı anda gösterebilirsiniz. Bunlar, ilk hizmet önce gelen sırayla aşağıdaki üst ve ek infobars gösterme gösteren ilk bilgi çubuğu ile görüntülenir.  
  
 Kullanıcı en fazla üç infobars teker teker görürsünüz. daha fazla infobars kullanılabilir değilse bilgi çubuğu bölge kaydırılabilir olacak, sonra.  
  
### <a name="creating-an-infobar"></a>Bir bilgi çubuğu oluşturma  
 Bilgi çubuğu, soldan sağa doğru dört bölüm içerir:  
  
-   **Simge:** budur burada herhangi bir simge eklemek için bir uyarı simgesi gibi bilgi çubuğu, görüntülemek istediğiniz.  
  
-   **Metin:** metninde bağlantılarıyla birlikte, senaryo/durum kullanıcı açıklamak için metni, gerekirse ekleyebilirsiniz. Metin Sözün tutmak unutmayın.  
  
-   **Eylemler:** bağlantılar ve düğmeler kullanıcı, Bilgi Çubuğu'nda gerçekleştirebileceğiniz eylemler için bu bölümü içermelidir.  
  
-   **Kapat düğmesi:** sağa son bölümde Kapat düğmesine sahip olabilir.  
  
#### <a name="creating-a-standard-infobar-in-managed-code"></a>Yönetilen kodda standart bir bilgi çubuğu oluşturma  
 InfoBarModel sınıfı, bir bilgi çubuğu için bir veri kaynağı oluşturmak için kullanılabilir. Bu dört oluşturuculardan birini kullanın:  
  
```  
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(string text, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(string text, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
```  
  
 Bazı metinlerle köprü, eylem düğmesi ve bir simge ile bir InfoBarModel oluşturan bir örnek aşağıda verilmiştir.  
  
 ![Bilgi Çubuğu ile köprü](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904 02_InfobarHyperlink")  
  
```  
var infoBar = new InfoBarModel(  
    textSpans: new[]  
    {  
        new InfoBarTextSpan("This is a "),  
        new InfoBarHyperlink("hyperlink"),  
        new InfoBarTextSpan(" InfoBar.")  
    },  
    actionItems: new[]  
    {  
        new InfoBarButton("Click Me")  
    },  
    image: KnownMonikers.StatusInformation,  
    isCloseButtonVisible: true);  
  
```  
  
#### <a name="creating-a-standard-infobar-in-native-code"></a>Standart bir bilgi çubuğu yerel kod oluşturma  
 Yerel koddan bir bilgi çubuğu sağlamak amacıyla IVsInfoBar arabirimini uygular.  
  
```  
public interface IVsInfoBar  
{  
    IVsInfoBarActionItemCollection ActionItems { get; }  
    ImageMoniker Image { get; }  
    bool IsCloseButtonVisible { get; }  
    IVsInfoBarTextSpanCollection TextSpans { get; }  
}  
  
```  
  
#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Bir bilgi çubuğu bir bilgi çubuğu UIElement alma  
 InfoBarModel veya IVsInfoBar uygulaması olan veri modelleri, kullanıcı Arabiriminde gösterilmesi için bir UIElement açık olması gerekir. UIElement'i Svsınfobaruıfactory/IVsInfoBarUIFactory hizmetiyle alınabilir.  
  
```  
private bool TryCreateInfoBarUI(IVsInfoBar infoBar, out IVsInfoBarUIElement uiElement)  
{  
    IVsInfoBarUIFactory infoBarUIFactory = serviceProvider.GetService(typeof(SVsInfoBarUIFactory)) as IVsInfoBarUIFactory;  
    if (infoBarUIFactory == null)  
    {  
        uiElement = null;  
        return false;  
    }  
  
    uiElement = infoBarUIFactory.CreateInfoBar(infoBar);  
    return uiElement != null;  
}  
```  
  
### <a name="placement"></a>Yerleştirme  
 Bir veya daha fazla aşağıdaki konumlardan içinde Infobars gösterilebilir:  
  
-   Araç pencereleri  
  
-   İçine bir belge sekmesi  
  
> [!IMPORTANT]
>  Genel bağlamı hakkında bir ileti vermek için bir bilgi çubuğu konumlandırmak mümkündür. Bu, araç çubukları ve belgenin iyi arasında görünür. "Atlamak ve jerk" sorunların neden olduğu için bu önerilmez IDE ve sürece kaçınılmalıdır kesinlikle gerekli ve uygun.  
  
#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>İçinde bir ToolWindowPane bir bilgi çubuğu yerleştirme  
 ToolWindowPane.AddInfoBar(IVsInfoBar) yöntemi, bir bilgi çubuğu için araç penceresi eklemek için kullanılabilir. Bu API ya da (hangi InfoBarModel varsayılan bir uygulama olduğu), bir IVsInfoBar ekleyebilir veya bir IVsUIElement.  
  
#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Bir belge ya da ToolWindowPane olmayan bir bilgi çubuğu yerleştirme  
 Bir bilgi çubuğu tüm IVsWindowFrame yerleştirmek için çerçeveyi IVsInfoBarHost almak için ıvswindowframe.GetProperty özelliğini kullanın ve ardından UIElement bilgi çubuğu ekleyin.  
  
```  
private void AddInfoBar(IVsWindowFrame frame, IVsUIElement uiElement)  
{  
    IVsInfoBarHost infoBarHost;  
    if (TryGetInfoBarHost(frame, out infoBarHost))  
    {  
        infoBarHost.AddInfoBar(uiElement);  
    }  
}  
private bool TryGetInfoBarHost(IVsWindowFrame frame, out IVsInfoBarHost infoBarHost)  
{  
    object infoBarHostObj;  
    if (ErrorHandler.Failed(frame.GetProperty((int)__VSFPROPID7.VSFPROPID_InfoBarHost, out infoBarHostObj)))  
    {  
        infoBarHost = null;  
        return false;  
    }  
  
    infoBarHost = infoBarHostObj as IVsInfoBarHost;  
    return infoBarHost != null;  
}  
  
```  
  
#### <a name="placing-an-infobar-in-the-main-window"></a>Ana pencerede bir bilgi çubuğu yerleştirme  
 Ana penceresinde bir bilgi çubuğu yerleştirmek için VSSPROPID_MainWindowInfoBarHost Ivsshell hizmetin ana pencerenin IVsInfoBarHost gidebilir ve UIElement bilgi çubuğu ekleyin.  
  
### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Bilgi Çubuğu'nda kullanıcının eylemde bulunduğunda bilebilirim?  
 Evet, biz bilgi çubuğu Yazar her olay eylem döndürür. Bilgi çubuğu yazarın bilgi çubuğu kullanıcı seçimlere dayanarak IDE'de harekete kadar sonra olur. Infobars olan Kapat düğmesine tıklandığını ana bilgisayarınızdan otomatik olarak kaldırılacak, ancak diğer infobars sonra kaldırılacak gerek kapatırsanız ek iş gereklidir. Telemetri ayrıca birbirinden bağımsız olarak her bir bilgi çubuğu ile oturum açmış olmanız gerekir.  
  
#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>İçinde bir ToolWindowPane bilgi çubuğu olayları alma  
 ToolWindowPane infobars için iki olay vardır. Bir Bilgi Çubuğu'nda ToolWindowPane kapatıldığında InfoBarClosed olay tetiklenir. Köprü veya içinde bilgi çubuğu düğmesine tıklandığında InfoBarActionItemClicked olay tetiklenir.  
  
#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>UIElement doğrudan alıcı bilgi çubuğu olayları  
 IVsInfoBarUIElement.Advise doğrudan bir bilgi çubuğu 's UIElement olaylarına abone olmak için kullanılabilir. IVsInfoBarUIEvents uygulama yazarı Kapat almak ve tıklama olayları izin verir.  
  
```  
public interface IVsInfoBarUIEvents  
{  
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);  
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);  
}  
  
```  
  
##  <a name="BKMK_ErrorValidation"></a> Hata doğrulama  
 Kullanıcı kabul yanlış biçimde veri girildiğinde veya ne zaman gerekli bir alan atlanır gibi bilgileri girdiğinde kullanımı denetimi doğrulama veya geri bildirim denetimi engelleyen bir açılan pencere hata iletişim kutusu kullanmak yerine yakın iyidir.  
  
### <a name="field-validation"></a>Alan doğrulama  
 Form ve alan doğrulama üç bileşenlerden oluşur: bir denetimin, simge ve bir araç ipucu. Çeşitli denetimler bu kullanabilirsiniz, ancak bir metin kutusu örnek olarak kullanılır.  
  
 ![Alan doğrulama &#40;boş&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905 01_FieldValidation")  
  
 Alanın gerekli olması durumunda olması gerektiğini belirten metin Filigran  **\<gerekli >** ve alan arka ışık olmalıdır sarı (VSColor: `Environment.ControlEditRequiredBackground`) ve ön gri olması gerekir (VSColor: `Environment.ControlEditRequiredHintText`):  
  
 ![Alan doğrulama "Required" etiketli](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905 02_FieldValidationRequired")  
  
 Program denetimi bir durumda olduğunu belirlemek *girilen geçersiz içerik* ne zaman, odak başka bir denetime taşınır veya kullanıcı bir [Tamam] tamamlama düğmesine tıkladığında veya kullanıcı, belge veya form zaman kaydeder.  
  
 Geçersiz içerik durumu belirlendiğinde, denetimin içindeki ya da yalnızca yanında bir simge görünür. Hatayı açıklayan bir araç ipucu simgesi veya denetim gidildiğinde görüntülenmesi gerekir. Buna ek olarak, 1 piksel kenarlık geçersiz bir durum oluşturuyor denetimin etrafında görüntülenmesi gerekir.  
  
 ![Alan doğrulama Düzen belirtimleri](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905 03_LayoutSpecs")  
  
 **Düzen özelliklerini alan doğrulama**  
  
#### <a name="acceptable-variations-for-icon-location"></a>Simge konumu için kabul edilebilir farklılıkları  
 Kullanıcılar doğrulama hataları hakkında bilgilendirilmesi gereken sayısız benzersiz durumlar vardır. Denetim türü ve kullanıcı arabiriminin yapılandırma göz önünde bulundurarak, durumunuza uygun simgeyi yerleştirme'ı seçin.  
  
 ![Simge konumu için kabul edilebilir konumları](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905 04_IconLocation")  
  
 **Alan doğrulama simge konumları için kabul edilebilir farklılıkları**  
  
#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Bir sunucu veya ağ bağlantısı için bir gidiş dönüş gerektiren doğrulama  
 Bazı durumlarda, sunucuya gidiş dönüş içeriği doğrulamak için gereklidir ve hata durumları ve doğrulandı, kullanıcı ilerleme durumunu göstermek önemli. Bu durumda ve önerilen kullanıcı Arabiriminin bir örneği aşağıdaki şekilde gösterir.  
  
 ![Sunucuya gidiş dönüş ilgili doğrulama](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905 05_RoundTrip")  
  
 **Sunucuya gidiş dönüş ilgili doğrulama**  
  
 "Doğrulanıyor..." ve "Deneyin" metin uyum sağlamak için yeterli kullanılabilir alan denetimi sağındaki sağlanmalıdır unutmayın.  
  
#### <a name="in-place-warning-text"></a>Yerinde uyarı metni  
 Oda hata iletisini kontrol yakın bir hata durumuna kullanılabilir olduğunda, bu tek başına araç ipucunu kullanmayı tercih edilir.  
  
 ![İçinde&#45;uyarı yerleştirin](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905 06_InPlaceWarning")  
  
 **Yerinde uyarı metni**  
  
#### <a name="watermarks"></a>Filigranlar  
 Bazen bir tüm denetim veya penceresi bir hata durumunda olabilir. Bu durumda, hatayı göstermek için Filigran kullanın.  
  
 ![Filigran](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905 07_Watermark")  
  
 **Filigran alan doğrulama**