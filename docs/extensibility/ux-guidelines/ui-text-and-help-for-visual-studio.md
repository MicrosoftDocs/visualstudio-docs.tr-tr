---
title: UI metni ve Yardımı için Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 52260b2cd401f8cdbd3a94704ab29db2f64fdc6d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842241"
---
# <a name="ui-text-and-help-for-visual-studio"></a>UI metni ve Visual Studio için Yardım
##  <a name="BKMK_UITextAndTerminology"></a> UI metni ve terminoloji  
 Anlaşılır metin etkin kullanıcı Arabirimi için çok önemlidir. Yazılım kullanıcıları eğilimli okumak için ilk olarak, yani bu görevi tamamlamak için en uygun etiketler. Statik metin daha az sıklık ile okunur. Planı iş oturumlarını yaklaşık bu sırada kullanıcı arabiriminin bir okuma ardından pencerenin tamamını bir hızlı tarama başlatmak kullanıcılar için:  
  
1.  Merkezi'ndeki etkileşimli denetimleri  
  
2.  Yürütme düğmeleri  
  
3.  Etkileşimli denetimleri başka bir yerde  
  
4.  Ana yönergeleri  
  
5.  Ek açıklamaları  
  
6.  Pencere Başlığı  
  
7.  Ana gövdesi içinde başka bir statik metin  
  
### <a name="usage-patterns-for-ui-text"></a>UI metni için kullanım desenleri  
  
#### <a name="title-bar-text"></a>Başlık çubuğu metni  
 Başlık çubuğu metni UI kökenli komut eşleşmesi gerekir.  
  
#### <a name="instructional-text-helper-text"></a>Açıklayıcı metni (Yardımcısı metin)  
 Bazı iletişim kutularında, pencere veya sayfa yapmanız gerekenler açıklamak için belirgin ana yönergeler sağlamak yararlıdır. Bu bazen "Yardımcısı text." adlandırılır  
  
##### <a name="writing-style-rules-for-helper-text"></a>Stil kuralları Yardımcısı metin yazma  
  
-   Belirgin açıklamak değildir. Kesinlikle gerekli olmadıkça, eğitici metin içermez.  
  
-   Eğitici metin her zaman iletişim kutusunun en üstünde yer alır ve gerçekleştirilen görev başvurmanız gerekir.  
  
-   Tam olarak kullanıcılara yapmak için ihtiyaçları açıklayın. Aşırı iletişim ve yedeklilik kaçının.  
  
-   Her pencere gözden geçirin ve yinelenen sözcükleri ve ifadeleri ortadan kaldırın.  
  
-   Eğitici metin kısa tutun. Daha fazla bilgi gerekli belirli kullanıcılar veya senaryoları ise, daha sonra ayrıntılı kavramsal çevrimiçi konusuna bağlantı sağlamak.  
  
-   Metninizi yazın, böylece her sözcük ağırlık tutar ve gereklidir.  
  
-   Mevcut Microsoft yönergeleri için [kullanıcı arabirimi metinlerini](/windows/desktop/uxguide/text-ui) ve [stil ve üslup](/windows/desktop/uxguide/text-style-tone).  
  
#### <a name="supplemental-instructions"></a>Ek yönergeler  
 Ek yönergeler kullanıcı denetimleri anlamak veya gruplandırmaları denetim yardımcı olacak ek bilgileri sağlayın. Bu, İpucu metin girişi denetimi bekleniyor hangi biçimde anlamak için gerekli de içerebilir. Ek yönergeler tedbirli şekilde kullanın. Bunları, kullanıcı, yapmakta olan seçim etkilerini tam olarak anlamak olmaz olası olduğu durumlar için saklı tutarız.  
  
 ![Visual Studio'da ek metin](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "b_SupplementalText1 0601")  
  
 **Visual Studio'da ek metni**  
  
 ![Visual Studio'da ek metin](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "c_SupplementalText2 0601")  
  
 **Visual Studio'da ek metni**  
  
#### <a name="infotips"></a>InfoTips  
 Genellikle, açıklayıcı metni kullanıcı Arabiriminde yerleşik yerleştirmek için çok uzun olabilir veya deneyimli kullanıcılar için dağınıklık gibi HİSSEDİYORSUNUZ yalnızca yeni kullanıcılar için yararlı olabilir. Bu durumda, bir bilgi ipucu altında bir araç ipucu olarak eğitici/bilgilendirici metin yerleştirilmelidir.  
  
 InfoTips belirgin olarak ilgili ve henüz örtük belirli bilgi ipucu simgesi kullanması gereken denetimleri yerleştirilmelidir.  
  
 ![Visual Studio'da Bilgi İpucu](../../extensibility/ux-guidelines/media/0601-d_infotip.png "d_InfoTip 0601")  
  
 **Visual Studio'da bir bilgi ipucu örneği**  
  
##### <a name="writing-style-rules-for-infotips"></a>InfoTips için yazma stil kuralları  
  
-   InfoTips tam cümle yazın. Bunlar, belirli fiillere, cümle ve bitiş için noktalama işaretleri gerektirir.  
  
-   Ana yönerge veya bilgi desteklemek üzere InfoTips kullanın. Buradaki ana fikir yazmayı yalnızca farklı sözcük kullanıyorsanız, bir bilgi ipucu gerekmez.  
  
-   InfoTips ve tatlı kısa tutun. Küçük kelimeleri ve düz, gündelik dil destekler ve kullanıcı teşvik eder.  
  
-   Mevcut Microsoft yönergeleri için [kullanıcı arabirimi metinlerini](/windows/desktop/uxguide/text-ui) ve [stil ve üslup](/windows/desktop/uxguide/text-style-tone).  
  
#### <a name="control-labels"></a>Denetim etiketleri  
 Denetim etiketleri kısa ve NET ve izleyin [denetimleri için Windows Masaüstü Kılavuzu](/windows/desktop/uxguide/controls).  
  
 Denetim etiket biçimi ve kullanıcı Arabirimi içinde yerleşimi hakkında daha fazla bilgi için [Visual Studio için Düzen](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="help-links"></a>Yardım bağlantıları  
 Yardım bağlantıları ya da eğitici metin veya gövdesini kullanıcı arabiriminin yerleştirilebilir. Yardım bağlantılarını olması veya iç iletişim kutuları başlatın.  
  
##### <a name="visual-style-rules-for-help-links"></a>Yardım bağlantıları için görsel stil kuralları  
  
-   Doğru ortamı renkleri için köprüler kullanın. Düzgün stil uygulanmış bir köprü kısaca tıklandığında kırmızı yanar değil. Bunu görürseniz, ardından bu ortam renkleri kullanılmayan göstergesidir.  
  
-   Alt çizgi, üzerine gelindiğinde veya bağlantı bir paragraf içinde ne zaman katıştırılmış yalnızca kullanılmalıdır.  
  
-   Köprüler için görsel ve etkileşim stilleri hakkında ayrıntılı bilgi için düğmeler ve köprüler bakın.  
  
##### <a name="writing-style-rules-for-help-links"></a>Yardım bağlantıları için yazma stil kuralları  
  
-   İletişim kutularını başlatma sırasında üç nokta standartları korumak: gezinme, görev ek kullanıcı Arabirimi gerektiriyorsa, üç nokta için hiçbir üç nokta.  
  
     ![Visual Studio'da yardım bağlantısına](../../extensibility/ux-guidelines/media/0601-e_helplink.png "e_HelpLink 0601")  
  
     **Görev ek kullanıcı Arabirimi gerektirecek bir Yardım bağlantısını bir nokta (...) gösterir.**  
  
-   Kullanıcının amacını olmadığından bağlantıları "İle öğrenin," başlamamalıdır. Kullanıcının istediği belirli bir soruya yanıt, genel bir eğitim alma.  
  
-   Böylece bunlar konu yanıtlayacak soru sorun, tümcecik Yardım bağlar.  
  
     Yanlış:  
     "Windows Azure mobil hizmetler fiyatlandırma hakkında daha fazla bilgi edinin"  
  
     Düzeltin:  
     "Hangi fiyatlandırma seçeneği, Windows Azure mobil hizmetler için kullanılabilir mi?"  
  
-   Hiçbir zaman kullanmayın *tıklayın...*  bağlantı metni.  
  
-   Hiç bağlantı yalnızca sözcük "burada". Yalnızca köprülü word sesli bazı ekran okuyucular için sorunlu budur.  
  
     Yanlış:  
     "Windows Azure mobil hizmetler hakkında bilgi bulmak **burada**"  
  
     Düzeltin:  
     "Hangi fiyatlandırma seçeneği, Windows Azure mobil hizmetler için kullanılabilir mi?"  
  
-   Yardım bağlantıları için doğru yazma stili hakkında daha fazla bilgi için bkz. [konusunda yardım almak için Windows Masaüstü Kılavuzu](/windows/desktop/uxguide/winenv-help).  
  
#### <a name="hint-text"></a>İpucu metni  
 İpucu metni, bir denetimi veya denetim altına filigran olarak görüntülenir. Doğru biçimlendirilmiş uygulanacak uygun VSColors belirtecini kullanarak `Environment.GrayText`.  
  
 Bu, çok sayıda formu görünebilir.  
  
-   Denetim etiketinin yerine:  
  
     ![Visual Studio'da metin İpucu](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "f_HintText1 0601")  
  
-   Bir eylem ile yönergeler verir:  
  
     ![Visual Studio'da metin İpucu](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "g_HintText2 0601")  
  
-   Gerekli bir giriş gösteren metin ile:  
  
     ![Visual Studio'da metin İpucu](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "h_HintText3 0601")  
  
#### <a name="watermark-text"></a>Filigran metni  
 Boş bir tasarım yüzeyine bir metin ne yapmak yanı sıra diğer ilgili pencerelerde uygunsa açmak için bağlantılar sağlar belirtmeniz gerekir:  
  
 ![Filigran metni Visual Studio'da](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "i_WatermarkText 0601")  
  
 **Filigran metni Visual Studio örneği**  
  
### <a name="common-terminology"></a>Sık kullanılan terimler  
  
|Terim|Açıklama|Yorum|  
|----------|-----------------|-------------|  
|Oturum açma / Oturumu Kapat|Fiilleri maliyetle aynı anlamda ile web kimlik doğrulaması web özelliği içinde temsil etmek için kullanılır. İstemcileri, bu kez en üst düzey bir kavram IDE kullanıcı bağlantısı, lisanslama ve dolaşım gibi daha üst düzey özellikleri ile tüm diğer bağlantılar kullanılamaz sağlayan bir üst düzey kimliğini temsil eder ve imzalama için kullanırız.|Üst düzey IDE kullanıcı temsil ettiğinden IDE kullanıcı temsil eden bir oturum açma / oturum fiili yalnızca özelliğidir.|  
|Connect / bağlantısını kes|Burada bir özellik bir çevrimiçi hizmet tek bir bağlantı tutar yerlerde kullanın.|Sunucu Gezgini, burada yalnızca bir etkin Azure bağlantı bir zaman olabilir, Bağlan/bağlantısını kes örneğidir.|  
|Ekle / Kaldır|Olmayan yıkıcı. Ekleme veya bir listeden kaldırma işlevini kullanın.|TFS Bağlantı Yöneticisi sunucu listesi iletişim kutusu Ekle/Kaldır örneğidir.|  
|Sil|Yıkıcı. Yalnızca kaldırılan öğe kalıcı olarak atılacak veya diskten silindikçe kullanın.|Sonuç diskten bir dosya silindiğinde "Sil" genellikle bir istemi gerektirir.|  
  
## <a name="error-messages"></a>Hata iletileri  
  
### <a name="overview"></a>Genel Bakış  
 Hataları gerçekleşir. Kullanıcı neler yapabileceğinizi kısıtlamaları ayarlama kaçınılabilir hata iletileri engelleyen bir mantıklı ilk adımıdır. Ancak, bir hata oluştuğunda, bu iyi-yazılan hata iletisi sorunu azaltmaya yönelik uzun yol gidebilirsiniz. Hata iletileri tartışmaya zaman uyumlu ve çözülmesi gereken bir sorunu gösterir çünkü kullanıcı, görür bildirim en önemli türlerinden biridir. Kullanıcılar, kötü yazılmış hata iletileri hatalarının nedenini karar vermek için kendi ve tüm olası çözümleri bırakın.  
  
 Kullanıcılar için aşırı kullanılmasına dikkat veya değer kullanıcıyı eklemek yalnızca gerekli iletileri yazma deneyimi için hata iletileri kafa karıştırıcı durabilir. Yalnızca bir bildirim iletisi ise alternatif bir sunu'ni kullanın.  
  
### <a name="rules-for-creating-an-error-message"></a>Bir hata iletisi oluşturmak için kurallar  
  
-   Hata iletileri oluştururken, izleyici için uygun hata düzeyini seçin. Kullanıcı alabilir, bir eylem varsa sağlamak için basit özetlerini hedeflenir. Durumu kullanıcı bilmeniz gerekmez. herhangi bir şey yoktur.  
  
-   Yapıcı Yardımı sağlarız. Okuma ve yönerge içeren bir hata iletisi üzerinde işlem yapma daha kolaydır.  
  
-   Çift negatif kullanmayın.  
  
-   Her iki otomatikleştirilmiş gerçekleştirmek ve el ile dil bilgisi ve yazım denetimi, yazdığınız herhangi bir hata iletisi denetleyin.  
  
-   Karmaşık hata iletileri için sıralı iletişimleri kaçının. Hiçbir zaman F1 birleştirme için hata iletisini kullanın. İleti yeterli olur.  
  
-   Doğru simgesini kullanın.  
  
-   Sorular anlamak ve "Sil" ve "İptal" gibi açık seçeneğiniz vardır düğmelerini kolaylaştırır  
  
-   Uyarılar için ne devam etmeden adımlamayla olacağı hakkında açık olun. Düğmeleri adımlamayla belirtmeniz gerekir.  
  
-   Hatalar için kullanıcı sorunu gidermek için neler yapabileceğini açıklayın. Düğme eylemleri olması veya "Kapat" söyleyin Bir hata iletisi için "Tamam" düğmesini kullanmayın.  
  
-   Kendinize bir hata iletisi oluşturulurken sorun gereken bazı sorular:  
  
    -   Kullanıcı başına bu hata sorunu çözmek nasıl ekleyeceğimi?  
  
    -   Kullanıcı, bu hata olarak aynı sözlük kullanıyor mu?  
  
    -   Bu hata belirsiz veya birden çok durumlarda paylaşılan? Nasıl bu durumda, kullanıcıların ihtiyacı olan çözümü kılavuzu?  
  
#### <a name="build-errors"></a>Derleme hataları  
 Visual Studio yazılım geliştirme aracı olduğundan, çoğu bileşenlerinden biri bir derleme, dönüştürme veya kodlama Geliştirici iş ikili biçimine dönüştürmek için adım vardır. Bu dönüştürmeler, derleyici yanlış yazılan dosyaları işleyemediğinde veya derleyici seçenekleri düzgün ayarladığınızda olmayan hatalara neden olabilir.  
  
 Visual Studio kullanıcılarına devasa bir derleme hatalarını çözme geliştirme saat sayısı ayırabilirsiniz. Hataları bağımlılıkları veya ne zaman hata iletileri kötü, hangi, hatanın kaynağını ortaya çıkarmak zorlaştırabilir yazılır olduğunda bu çözümleme süresini artırır.  
  
 Bu nedenle ilk yerinde Visual Studio oluşmaz otomatik tamamlama sağlar en iyi derleme hataları olan ve IntelliSense dalgalı çizgiler. Şema doğrulayıcılar ve benzer araçları aynı türde bir geri bildirim sağlayın. Bu mekanizmalar proaktif olarak biçimlendirilmiş kod, derleme hataları olasılığını lessening oluşturmak için Kullanıcı Kılavuzu.  
  
 Visual Studio araç penceresi burada kullanıcılar okuyabilir ve belge pencerelerini meydana gelen hatalara gezinmek sağlar. Böylece kullanıcı, hızla kod büyük miktarlarda gidin ve doğrudan sorun konuma gidin, klavye kısayollarını sağlanır. Visual Studio, her yapı hatası kullanıcıya hata hakkında daha ayrıntılı bilgi sağlayan bir Yardım konusu için doğrudan çalışabilmeniz için belirli bir Yardım anahtar sözcüğü/bağlam Kimliğine bağlanması de sağlar.  
  
 Yazma NET, kısa ve öz derleme hataları:  
  
-   **Düz bir dil kullanmak** , çok az kayıpla veya hiç derleyici terminolojisinin sorunu açıklar. Bir yapı hatası metnini aşırı teknik olmamalıdır.  
  
-   **Olası nedenler özetler.** Örneğin, "özellik ve değer arasında iki nokta üst üste eksik ' (özellik): (değer)' bildirimi."  
  
-   Olası düzeltmeleri hakkında ayrıntılar verir. Yeterli alan yoksa, ek ayrıntılar karşılık gelen Yardım konusunu yerleştirilebilir.  
  
### <a name="components-of-a-well-written-error-message"></a>İyi yazılmış hata iletisinin bileşenleri  
  
#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Hata iletileri Kabuk iletişim hizmeti kullanın.  
 Kabuk iletişim hizmeti kullanarak tek tek öğeleri ana değişiklik yapmadan özellikle, yazı tiplerini iletinin görünümünü denetlemenize olanak tanır. Kullanım **IErrorInfo** mekanizmaları ve bunları rapor kullanarak **IVsUIShell::SetErrorInfo/ReportErrorInfo**.  
  
#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Etkili ve uygun bildirim sunu seçin.  
 Kalıcı bir iletişim kutusu (zaman uyumlu bildirim) veri kaybını önlemek için Acil eylem gerekli kritik bir uyarı ile kullanın. Kritik simgelerini hangi ileti okuma olmadan kapatma, olumsuz sonuçlara yol açabilir durumlar için ayrılmıştır. Veri kaybı Uyarısı Düzeyi yanıt gerektiren kritik bir durumdur. Kritik simgesi aşırı kullanımını önem derecesini kullanıcılara desensitizes. Hata iletisi bilgilendirme ise, kalıcı bir iletişim kutusu (zaman uyumsuz bildirim) alternatifleri düşünün.  
  
#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Neden bir teknik açıklama yerine sorun oluştu, temiz, birleştiren bir açıklama sağlayın.  
 Teknik Ayrıntılar açıklama kullanıcılarla overburdening bunları hata iletileri yok saymak büyük olasılıkla yapar. İyi Mesajlaşma örnekleri:  
  
-   "İstenen dosyası açılamıyor."  
  
-   "Internet'e bağlantı kurulamıyor."  
  
#### <a name="provide-information-about-how-to-fix-the-problem"></a>Sorunun çözümü hakkında bilgi sağlar.  
 Sorunu gidermek nasıl kullanıcı öneriler sunar. Öneri yok ise kullanıcıyla dürüst olun. Teknik destek veya topluluk desteği gibi diğer çevrimiçi kaynakları doğrudan bağlantıları verilmektedir. Kullanıcılar, sorunla ilgili belirli çevrimiçi bilgi işaret edecek şekilde deneyin. Hata kimliği için kullanıcıların belirli bir hata hakkında bir tartışma iş parçacığına bağlama göz önünde bulundurun. İyi Mesajlaşma örnekleri:  
  
-   "Internet'e bağlı ve bu işlemi yeniden deneyin emin olun."  
  
-   "Dosyasının varolduğunu ve ürünü açma izniniz olduğundan emin olun."  
  
#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Kısa ve noktasına olduğunu belirten bir ileti yazın.  
 Bir hata iletisi bildirebilir, açıklayan, ve bir çözüm sunar ancak yine de çok nefesiniz ise yoksayılacak. Tek bir çözüm ayrıntıları düğmeyle aşamalı açığa kullanmaktır. Örneğin, kısa bir açıklama/çözüm verin ve ardından ayrıntılar düğmesine altında daha fazla ayrıntı yerleştirin. Hata hakkında daha fazla bilgi okumak kullanıcılar'ı seçerseniz, bunlar bunu yapabilirsiniz.  
  
 İleti dilde olmalıdır:  
  
-   **Uygun etki alanı.** Kullanıcı anlayacaksınız dil kullanın. Müşterilerimizin geliştiriciler olsa da, bunlar genellikle sahibiz terminoloji ve bağlam yok.  
  
-   **Belirli.** Belirsiz ifadesi önlemek ve belirli adları ve konumları katılan nesnelerin verin. Örneğin, "karakteri geçersiz gibi" bir hata iletisi yararlı değildir. Hangi karakter? "Dosya bulunamadı." Hangi dosya?  
  
-   **Courteous.** Kullanıcı sorumlu veya onları stupid düşünüyorsanız kullanmayın. Tehlikeli ya da rahatsız edici dil kaçının (KILL, yürütün, önemli, geçersiz sonlandırma). Çok shouting olarak görülür ve olarak okunabilir değil tüm harfleri büyük metin kaçının. Anıları kullanmayın.  
  
-   **Düzeltin.** Yazım ve dil bilgisi (hatta alfalar içinde) kullanın. Yazım hatası okuyucunuz ve marifetiyle.  
  
-   **Bağlamsal uygun.** Uygun düğme metni kullanın. "Tamam" düğmesini önlemek ve "Devam" veya "Evet/Hayır" kullanın  
  
### <a name="error-message-examples"></a>Hata iletisi örnekleri  
  
|iyi|hatalı|  
|----------|---------|  
|"Aradığınız sayıdır artık hizmeti. Lütfen numarayı denetleyin ve tekrar arama veya 0 için işleç çevir."|-"Hata (449): Geçersiz sayı"<br />-"Bu işlenmeyen özel durum hatası işleminin başarıyla tamamlandığını gösterir."<br /><br /> ![Visual Studio hatalı hata iletisinde](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "a_ErrorDialog 0602")|  
  
## <a name="accessing-help"></a>Yardımı'na erişme  
  
### <a name="overview"></a>Genel Bakış  
 MSDN belgelerinde yanı sıra, Visual Studio kullanıcı, kullanıcı arabiriminde yardımcı olmak üzere çeşitli erişim noktaları vardır. Bu erişim noktaları sürekli kullanılabilir olmasını sağlamak için ortamı tarafından sunulan Yardım sistemi yararlanmak özellik takımı gerekir. Bu erişim noktaları şunlardır:  
  
-   **Yönerge ve ek metin kutularındaki.** Yön veya açıklaması, üzerinde yüzey veya üzerine bilgi ipucu simgesinin üzerine gelindiğinde kullanılabilen kullanıcı Arabirimi sağlayan statik metin.  
  
-   **F1 Yardımı** (yalnızca Düzenleyicide). Visual Studio düzenleyicisi içinde bir kullanıcı herhangi bir zamanda F1 tuşuna bastığınızda geçerli seçime belirli bir Yardım konusu çıkarır, güvenebilir. F1 ile ilgili konuları ilgili ve bilgilendirici olduğundan emin olun.  
  
-   **Yardım konuları bağlar.** Bir iletişim kutusu, araç penceresi ya da kullanıcı bir teknoloji, özellik veya bir görevi gerçekleştirmek nasıl bilgi hakkında daha fazla yardımcı olmak için bir konu başlatan tasarım yüzeyine içinde köprü.  
  
-   **Akıllı etiketler ve yapı iletişim kutuları gibi kullanıcı Arabirimi mekanizmalarını Yardımcısı.** Bu mekanizmalar kullanıcı UI öğesi anlaşılmasına yardımcı veya akıllı etiketler veya Oluşturucu iletişim kutuları gibi bir görev.  
  
-   **Kullanıcı Arabirimi Yardım düğmeleri** (kullanım dışı). F1 Yardımı ilgili konuya erişmenizi başlık çubuğunda görünür bir göstergesi.  
  
### <a name="text"></a>Metin  
  
#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Yönerge ve ek metin kutularındaki  
 Karmaşık görevleri desteklemek iletişim kutularında, iletişim kutusunun veya karmaşık denetimlerde yakın üst genellikle kullanıcı Arabirimi içinde eğitici metin vermek için bir gereksinim olabilir. Bkz: [UI metni ve terminoloji](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) yazma stili hakkında bilgi.  
  
#### <a name="infotips"></a>InfoTips  
 Genellikle, eğitici metin kullanıcı arabiriminde bir yerde konumlandırmak için çok uzun olabilir veya deneyimli kullanıcılar için dağınıklık gibi HİSSEDİYORSUNUZ yalnızca yeni kullanıcılar için yararlı olabilir. Bu durumda, bir bilgi ipucu altında bir araç ipucu olarak eğitici/bilgilendirici metin yerleştirilmelidir.  
  
 InfoTips belirgin olarak ilgili ve henüz örtük belirli bilgi ipucu simgesi kullanması gereken denetimleri yerleştirilmelidir.  
  
 ![Visual Studio'da Bilgi İpucu](../../extensibility/ux-guidelines/media/0601-d_infotip.png "d_InfoTip 0601")  
  
 **Visual Studio'da bir bilgi ipucu örneği**  
  
### <a name="interactive-help-mechanisms"></a>Etkileşimli yardım mekanizmaları  
  
#### <a name="f1-help"></a>F1 Yardımı  
 F1 Yardımı gerekiyor, içinde bir düzenleyici veya tasarım yüzeyine ancak Visual Studio ortamında değil başka bir yerde.  
  
#### <a name="hyperlinks-to-help-topics"></a>Köprüler Yardım konuları  
 Köprüler, bir eylemi gerçekleştirmek, IDE içinde gidin veya Yardım bir tarayıcıda başlatmak için kullanılabilir. Bkz [UI metni ve terminoloji](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) dil ve 07.10.01 hakkında ayrıntılı bilgi için düğmeler ve köprüler görsel ve düzeni kılavuzları için.  
  
#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>(Kullanım dışı) iletişim başlık çubuğu düğmeleri [?] Yardım  
 Çoğunlukla, iletişim kutuları, başlık çubuğunda Yardımı [?] düğmeleri kullanım dışı bırakılmıştır. Kullanıcı Arabirimi konuları artık doc modelimizi parçasıdır ve bu nedenle olmayabilir bağlamak için uygun bir konu. Aslında başlık çubuğu düğme F1 Yardımı ile aynı şeyi edildi ve artık iletişim kutularında gereklidir. Köprüler yeni kullanıcı Arabiriminde daha yaygın olarak kullanılan karşın bazı durumlarda, bu hala daha fazla kavramsal ya da yordam bilgisi kullanılabilir olduğunu bir gösterge kullanılabilir.  
  
##### <a name="dialogs-created-through-the-environment"></a>Ortamı üzerinden oluşturulan iletişim kutuları  
 Birçok Kabuk iletişim kutuları aracılığıyla oluşturulan **VBDialogBoxParam** işlevi. Taşıma yardımcı olması için bu paylaşılan işlevi güncelleştirildi **yardımcı** iletişim kutusuna düğmesinden **?** Geriye dönük bir mimari korurken düğmesi uyumlu ve genişletilebilir.  
  
 Özellikle, **VBDialogBoxParam** Kimliğine sahip bir düğme için bir iletişim şablonunu bakar işlevi **IDHELP** (9) veya etiket **yardımcı** veya **&Yardım**. Yardım düğmesi bulunursa, gizli ve **WS_EX_CONTEXTHELP** stil yerleştirir iletişim kutusuna eklenen **?** iletişim kutusunun başlık çubuğunda düğme.  
  
 İletişim kutusu oluşturulurken bir yığın üzerine iletişim proc gönderir ve adlı bir ön işleme iletişim proc ile iletişim başlatır **DialogPreProc**. Zaman **?** düğmesine tıklandığında, gönderdiği bir **WM_SYSCOMMAND** , **SC_CONTEXTHELP** iletişim kutusu. **DialogPreProc** bu komut yakalar ve ona değişiklikler bir **WM_HELP** özgün iletişim yordam için geçirilen iletisi  
  
 Çoğu ortam oluşturulan iletişim kutuları, iletişim kutusunda Yardım düğmesine sahip. İletişim kutusu görüntülendiğinde, otomatik olarak gizlendiğinde ve yalnızca Yardım düğmesini **?** Düğme çalışır. Varsa **?** Düğme hiç olmadığı kadar kaldırıldı veya değiştirildi Windows, bu çözümü hızlı bir şekilde geri özgün Yardım düğmelere taşımanızı sağlar.  
  
 Bu çözüm, hatalara neden olabilecek dört varsayımlarda bulunur:  
  
- İletişim kutusunun Yardım düğmesi **IDHELP** (9).  
  
- Yardım düğmesi gizlenir doğru iletişim kutusu görünür.  
  
- İletişim kutusu, kendi winproc yerine değil.  
  
- İletişim kutusu içinde başka bir iletişim kutusu ekli değil.  
  
  İletişim msenv içinde bulunur ve kullanmayan **VBDialogBoxParam**, yararlanarak araştırmak **VBDialogBoxParam** kendi işleyicinizi uygulamadan önce.  
  
##### <a name="dialogs-created-through-other-packages"></a>Diğer paketler aracılığıyla oluşturulan iletişim kutuları  
 Msenv dışında bulunan iletişim kutuları için kendi çözümünüzü uygulayabilirsiniz. İçinde VSPackage paylaşılan iletişim kutusu sınıfı için için başlık çubuğu düğmesini taşıma veya bir işleyici her iletişim kutusunda uygulama göz önünde bulundurun. Aşağıdaki kod, başlamanıza yardımcı olmak için bir uygulama bir skeleton şöyledir:  
  
```  
struct DLGPROCITEM  
{  
    FARPROC proc; // The info used to create the dialog.  
    DLGPROCITEM* procPrev;  
};  
  
DLGPROCITEM* g_dlgProcStack = NULL;  
  
// A dialog starter/wrapper function is used to push the new  
// dialog proc to the top of our dialog proc stack.  
  
int SomeDialogStarterFunction(hinst, id, proc, etc)  
{  
    if (g_dlgProcStack == NULL)  
    {  
        g_dlgProcStack = new DLGPROCITEM;  
        g_dlgProcStack->procPrev = NULL;  
    }  
    else  
    {  
        DLGPROCITEM* procItem = new DLGPROCITEM;  
        g_dlgProcStack->procPrev = g_dlgProcStack;  
        g_dlgProcStack = procItem;  
    }  
}  
  
// Pop this dialog proc off the dialog proc stack.  
  
DialogBoxIndirectParam...(...)  
{  
    DLGPROCITEM* procItem = g_dlgProcStack->procPrev;  
    delete g_dlgProcStack;  
    g_dlgProcStack = procItem;  
}  
  
// A wrapper dialog procedure will allow us to capture the  
// SC_CONTEXTHELP button on the title bar from Windows and  
// forward it as a simple WM_HELP message back to the dialog.  
  
INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg,  
    WPARAM wParam, LPARAM lParam)  
{  
    if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP)  
    {  
        uMsg = WM_HELP;  
        wParam = 0;  
        lParam = 0;  
    }  
    return CallWindowProc((WNDPROC)g_dlgProcStack->proc,  
        hwndDlg, uMsg, wParam, lParam);  
}  
```  
  
##### <a name="help-buttons-in-managed-code"></a>Yönetilen kodda Yardım düğmeleri  
 Pencere başlık çubuğu Yardım düğmesinin varsayılan davranışı geçersiz kılma, yönetilen kodda kolaydır. Aşağıda bu davranışını gösteren bir tam bir tanıtım uygulamasıdır. Esas olarak, form denetiminin geçersiz kılmanız gerekir **WndProc** yöntemi ve ardından yangın F1 Yardım istekleri ne zaman bir **SC_CONTEXTHELP** ileti kesildi.  
  
```  
using System;  
using System.Windows.Forms;  
  
public class HelpForm : Form  
{  
    private const int SC_CONTEXTHELP = 0xF180;  
    private const int WM_SYSCOMMAND = 0x0112;  
  
    public HelpForm()  
    {  
        this.ClientSize = new System.Drawing.Size(300, 250);  
        this.HelpButton = true;  
        this.MaximizeBox = false;  
        this.MinimizeBox = false;  
        this.Name = "HelpForm";  
        this.Text = "Help Form";  
    }  
  
    protected override void WndProc(ref Message m)  
    {  
        if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam)  
            ShowHelp();  
        else  
            base.WndProc(ref m);  
    }  
  
    private void ShowHelp()  
    {  
        MessageBox.Show("F1 Help goes here.");  
    }  
  
     [STAThread]  
    static void Main()  
    {  
        Application.EnableVisualStyles();  
        Application.EnableRTLMirroring();  
        Application.Run(new HelpForm());  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yazı tipleri ve Visual Studio için biçimlendirme](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [Visual Studio düzeni](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [Visual Studio İçin Bildirimler ve İlerleme Durumu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)