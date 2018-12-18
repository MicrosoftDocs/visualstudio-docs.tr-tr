---
title: Visual Studio için UX temel bileşenleri | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 37d2942e64a4c964ad696d1eb2c0d4bf3c777b87
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49848598"
---
# <a name="ux-essentials-for-visual-studio"></a>Visual Studio için UX temel bileşenleri
## <a name="best-practices"></a>Önerilen uygulamalar  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Visual Studio ortamında tutarlı olmalıdır.  
  
-   Varolan izleyin [etkileşim desenleri](interaction-patterns-for-visual-studio.md) kabuktan.  
  
-   Özellikleri kabuğun visual dili ile tutarlı olacak şekilde tasarlayın ve [craftsmanship gereksinimleri](evaluation-tools-for-visual-studio.md).  
  
-   Bunlar mevcut paylaşılan komutlara ve denetimlere kullanın.  
  
-   Visual Studio hiyerarşi ve nasıl bağlam oluşturur ve kullanıcı arabirimini yönlendirir anlayın.  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Yazı tipleri ve renkler ortam hizmeti kullanın.  
  
-   Geçerli kullanıcı Arabirimi dikkate [ortam yazı tipi](fonts-and-formatting-for-visual-studio.md) özelleştirme seçenekleri iletişim kutusu yazı tipleri ve renkler sayfasında sunulan sürece ayarlama.  
  
-   Kullanıcı Arabirimi öğeleri kullanmalıdır [VSColor hizmet](colors-and-styling-for-visual-studio.md), kullanılarak paylaşılan ortam belirteçleri veya özelliğe özgü belirteçleri.  
  
### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Tüm görüntüleri yeni VS stil ile tutarlı olun.  
  
-   Simgeler, karakterleri ve diğer grafikleri için Visual Studio tasarım ilkelerini izleyin.  
  
-   Metin, grafik öğeleri yerleştirmeyin.  
  
### <a name="4-design-from-a-user-centric-perspective"></a>4. Kullanıcı merkezli bir açısından tasarlayın.  
  
-   İçindeki tek tek özellikler önce Görev akışı oluşturun.  
  
-   Kullanıcılarınızla bilgi sahibi olmanız ve bu bilgi, teknik özellikler, açık olun.  
  
-   Kullanıcı arabirimini gözden geçirirken, ayrıntıları yanı sıra eksiksiz deneyimi değerlendirin.  
  
-   Kullanıcı Arabirimi yerel ayar veya dil bağımsız olarak çekici ve işlevsel kalır şekilde tasarlayın.  
  
## <a name="screen-resolution"></a>Ekran çözünürlüğü  
  
### <a name="minimum-resolution"></a>En düşük çözünürlük  
 - Visual Studio Dev14 için minimum çözünürlük **1280 x 720**. Bu, anlamına gelir *olası* bir en iyi kullanıcı deneyimini olmayabilir rağmen bu çözünürlükte, Visual Studio'yu kullanma. Tüm yönleriyle 1280 x 720 ' daha düşük çözünürlüklerde kullanılabilir olacağını garanti yoktur.  
  
 - Visual Studio için hedef çözüm **1366 x 768**. Başlangıçtan etmeyeceğiz düşük çözüm budur bir *iyi* kullanıcı deneyimi.

 - İlk iletişim yükseklik olmalıdır **700 pikselden küçük**, içinde IDE çerçevesinin 96 DPI, minimum çözünürlük sığmasını sağlayın.
  
### <a name="high-density-displays"></a>Yüksek yoğunluklu görüntüler  
 Visual Studio kullanıcı Arabiriminde da kullanıma hazır Windows destekleyen Etkenler ölçeklendirme tüm DPI çalışmak gerekir: % 150 %200 ve % 250.  
  
## <a name="anti-patterns"></a>Ters desenler  
 Visual Studio UI kılavuz İlkelerimizi ve en iyi uygulamaları izleyin birçok örnekleri içerir. Geliştirilmiştir tutarlı olması için ürün UI tasarım desenleri ne, oluşturmakta olduğumuz için benzer geliştiriciler genellikle alın. Kullanıcı etkileşimi ve görsel tasarım tutarlılık sürücü bize yardımcı olur, biz bazen koşullarımıza Zamanlama kısıtlamaları nedeniyle karşılamaz veya hata önceliklendirme birkaç ayrıntıları sunmaya başlayamıyorsunuz, iyi bir yaklaşım budur ancak. Bunlar Visual Studio ortamının içinde hatalı veya tutarsız UI yayılmaya çünkü bu gibi durumlarda, takımlar bu "ters desenler" birini kopyalayıp istiyoruz değil.  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Hata durumunda varsayılan olarak gösterilen gerekli alanlar/ayarları  
  
#### <a name="feature-team-goals"></a>Takım hedeflerine özelliği  
  
-   Yapılandırılması gereken bir öğe eklediğiniz kullanıcıları uyarın.  
  
-   Kullanıcının dikkatini fikirlerinize ihtiyacımız alanlarına çizin.  
  
#### <a name="anti-pattern-solution"></a>Koruma düzeni çözümü  
 Hemen kullanıcı tarafından başlatılan bir eylem olarak ve görev tamamlanmadan önce durdurma kritik simgeleri yapılandırma gerektiren alanlar yanındaki yerleştirin.  
  
#### <a name="example-manifest-designer-declarations"></a>Örnek: Bildirim Tasarımcısı bildirimleri  
 Bir bildirimi hemen listeye eklemeyi kullanıcı gerekli özellikleri ayarlar kadar kalıcı bir hata durumunda yerleştirir.  
  
 Bu durumda, yoktur ek bir sorun için uyarı kullanılan simge içerdiğinden bir "&times;" simgesi, bu nedenle ortak Kaldır simgesi yanında kullanılamaz. Sonuç olarak, kullanıcı Arabirimi daha clunky denetimi bir Kaldır düğmesini kullanır.  
  
 ![UI hata durumunda, varsayılan yerleştirme bir Visual Studio koruma desendir. ](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti düzeni")<br />UI hata durumunda, varsayılan yerleştirme bir Visual Studio koruma desendir.
  
#### <a name="alternatives"></a>Alternatifleri  
 Bu sorun için bir çok daha iyi çözüm olacaktır:  
  
-   Bir uyarı bildiriminde eklemek kullanıcının ve öğede özelliklerini ayarlamak hemen taşıyın.  
  
-   Uyarı simgesi (gold üçgen) ekleme zaman odak taşır öğesinden gibi başka bir bildirimi listeye ekleyin veya tasarımcı sekmelerde değiştirme girişimi.  
  
-   Kullanıcının sekme özellikleri tüm bildirimlerinde ayarlamadan önce çalışırsa, uygulaması olmayan oluşturacaksınız açıklayan bir iletişim kutusu açılır (veya hangi etkilerini) uyarıları çözülene kadar. Yine de kullanıcı iletişim kutusunu kapatır ve sekmeleri değiştirirse (kritik veya uyarı, uygun şekilde) simge için bildirimler sekmesine eklenir.  
  
### <a name="multiple-clicks-to-dismiss-ui"></a>UI kapatmak için birden çok tıklama  
  
#### <a name="feature-team-goals"></a>Takım hedeflerine özelliği  
 Kullanıcı, kullanıcı Arabirimi açıklama metni görmeden kapatmak izin verme.  
  
#### <a name="anti-pattern"></a>Koruma düzeni  
 Video bağlantıları VS UI içinde çeşitli yerlerde içine ekleyerek takım sık karşılaşılan desenini karşı karar "&times;" Kapat düğmesi ve araç ipucu açıklaması olarak UX tarafından belirtilen, bunun yerine bir açılan uygulanan ve "bir daha gösterme" bağlayabilirsiniz.  

#### <a name="example-video-links-in-team-explorer"></a>Örnek: Takım Gezgini içinde video bağlantıları
Kullanıcı UI kapatılıyor önce açıklayıcı metin okumak için zorlama, Visual Studio içinden koruma bir desendir. Doğru şekilde tasarlanmış, video bağlantılarını üzerine gelin ve tıklayarak ek bilgileri içeren bir araç ipucu görüntülemesi gereken "&times;" daha fazla etkileşim için gerek kalmadan iletisini kapat.


 ![Kötü amaçlı yazılımdan koruma açıklayıcı metin&#45;deseni &#45; yanlış](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />Video bağlantısı yanlış deseni
  
#### <a name="result"></a>Sonuç  
 Bir basit Kapat düğmesi (tek bir tıklamayla) kullanıcı kullanıcı Arabiriminde görünen video bağlantıları her yerde verilecek iki tıklamada kullanmak için zorlanır.  
  
#### <a name="alternatives"></a>Alternatifleri  
 Internet Explorer, Office ve Visual Studio için ortak desen izlemek için bu durum için doğru tasarım olacaktır: üzerine gelindiğinde, kullanıcı tooltip açıklamasını görebilir ve tek bir tıklamayla kullanıcı arabirimini gizler.  
  
 ![Kötü amaçlı yazılımdan koruma açıklayıcı metin&#45;deseni &#45; doğru](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti desenini düzeltin")<br />Doğru video bağlantısı düzeni
  
### <a name="using-command-bars-for-settings"></a>Komut çubuğu ayarları için kullanma  
 **Şekil A** Bu koruma düzeni temsil eder: ayarı daha fazlasını komutu geçerli bir komut düğmesi altındaki yerleştirme. Bu taslağı hata ayıklamayı Başlat yanı sıra komutları vardır — ister tarayıcı, hata ayıklama olmadan başlat ve içine adımla görünümünde — seçili olan ayar dikkate.  

  ![Şekil y: komut koruma düzeni](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti deseni FigureA")<br />Şekil y: komut çubuğu koruma düzeni
  
 Biraz daha iyi, ancak hala istenmeyen sokarak ayarlar bu türün araç çubuklarını, gösterildiği gibi **şekil B**. Bölünmüş düğme daha az yer kaplar ve bu nedenle bir geliştirme açılan listeler, ancak her iki tasarımın bir araç çubuğu gerçekten bir komut değil bir şey yükseltmek için yine de kullanmaktadır.  
 
 ![Şekil B: daha iyi, ancak yine de bir komut çubuğu koruma düzeni](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti deseni FigureB")<br />Şekil B: daha iyi, ancak yine de bir komut çubuğu koruma düzeni
 
  Gösterilen doğru yaklaşımda **şekil C**, ayar, bir dizi komut bağlıdır. Ayarlanan genel ayar yoktur ve biz yalnızca dört komuttan arasında geçiş yapıyorsanız. Bu, araç çubuğundaki komutları kabul edilebilir tek durumdur. 

 ![Şekil C: düzeltmek Visual Studio komut çubuğu düzeni kullanımını](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti deseni FigureC")<br />Şekil C: doğru Visual Studio komut çubuğu desenini kullanın
   
### <a name="control-anti-patterns"></a>Denetim ters desenler  
 İçin bazı ters desenler, yalnızca yanlış kullanımı veya bir denetim veya denetimlerin Grup sunumu olabilir.  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Bir köprü bir Grup etiketi kullanılan alt çizgi  
 Altı çizili metin yalnızca köprüler için kullanılmalıdır.  
  
 **Hatalı:**    
 ![Köprü değil altı çizili metni bir Visual Studio koruma desendir. ](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102 g_GroupLabelIncorrect")<br />Köprü değil altı çizili metni bir Visual Studio koruma desendir.
  
 **İyi:**   
 ![Doğru biçimlendirilmiş, olmayan köprü metin ortam yazı tipini eksiz görünür. ](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102 h_GroupLabelCorrect")<br />Doğru biçimlendirilmiş, olmayan köprü metin ortam yazı tipini eksiz görünür.
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Bir açılır iletişim kutusu bir onay kutusu sonuçları tıklayarak  
 "Windows Azure uygulaması Yayımla" sihirbazında "Tüm roller için Uzak masaüstünü etkinleştir" onay kutusunu hemen tıklayarak, bir Visual Studio koruma desen gibi açılır bir iletişim kutusunu açar. Ayrıca, onay kutusu alanı içeren bir onay kutusu seçildikten sonra dolmaması başka bir etkileşim koruma modeli.  
  
 ![Bir iletişim kutusu bir onay kutusunu tıklatarak bir Visual Studio koruma desendir sonra getirme. ](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102 i_CheckboxPopup")<br />Bir iletişim kutusu bir onay kutusunu tıklatarak bir Visual Studio koruma desendir sonra getirme.
  
### <a name="hyperlink-anti-patterns"></a>Köprü ters desenler  
 Aşağıdaki örnek, iki ters desenler içerir.  
  
1. Üzerine gelindiğinde kırmızı kapatma ön doğru paylaşılan rengi yazı tipi hizmetinde kullanılmadığı anlamına gelir.  
  
2. "Daha fazla bilgi edinin" değil bir kavramsal konuya bağlantısını için uygun metni. Kullanıcının hedef daha kendi seçtikleri etkilerini öğrenmektir değil öğrenmektir.  
  
   ![Renk hizmet yoksayılıyor ve "daha fazla bilgi edinmek için köprüler" kullanarak Visual Studio ters desenler var. ](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")<br />Renk hizmet yoksayılıyor ve "daha fazla bilgi edinmek için köprüler" kullanarak Visual Studio ters desenler var.  
  
   **Daha iyi bir çözüm:** anın bağlantıya tıklayarak soru konusunda sizi uyarmayı.  
  
-   Windows Azure hizmetleri nasıl çalışır?  
  
-   Bir Windows Azure Mobile Services projesi ne gerekir?  
  
#### <a name="using-click-here-for-links"></a>"Bağlantıları için buraya tıklayın" kullanma  
 Köprüler, kendini açıklayıcı olmalıdır. Bu, "buraya tıklayın" kullanmak için koruma desen veya benzer bir değişim olur.  
  
 **Hatalı:** "Buraya yeni bir proje oluşturma hakkında yönergeler için tıklayın."
  
 **İyi:** "Nasıl oluşturabilirim yeni bir proje?"