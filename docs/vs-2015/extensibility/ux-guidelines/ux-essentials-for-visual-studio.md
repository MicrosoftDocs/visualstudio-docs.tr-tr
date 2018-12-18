---
title: UX Temel Bileşenleri
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8984b0b7854457fcfa8f2b48e82fa8d12f8e539d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53060468"
---
# <a name="ux-essentials-for-visual-studio"></a>Visual Studio için UX temel bileşenleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="best-practices"></a>Önerilen uygulamalar

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Visual Studio ortamında tutarlı olmalıdır.

-   Kabuktan mevcut etkileşim desenleri izleyin.

-   Özellikleri kabuğun visual dil ve craftsmanship gereksinimleri ile tutarlı olacak şekilde tasarlayın.

-   Bunlar mevcut paylaşılan komutlara ve denetimlere kullanın.

-   Visual Studio hiyerarşi ve nasıl bağlam oluşturur ve kullanıcı arabirimini yönlendirir anlayın.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Yazı tipleri ve renkler ortam hizmeti kullanın.

-   Özelleştirme seçenekleri iletişim kutusu yazı tipleri ve renkler sayfasında sunulan sürece, UI geçerli ortam yazı tipi ayarlarını dikkate.

-   Kullanıcı Arabirimi öğeleri paylaşılan ortamı belirteçleri veya özelliğe özgü belirteçleri kullanarak VSColor hizmeti kullanmanız gerekir.

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
 Visual Studio Dev14 için minimum çözünürlük 1280 x 1024'tür. Bu, anlamına gelir *olası* bir en iyi kullanıcı deneyimini olmayabilir rağmen bu çözünürlükte, Visual Studio'yu kullanma. Tüm yönleriyle 1280 x 1024'ten düşük çözünürlüklerde kullanılabilir olacağını garanti yoktur.

 İlk iletişim kutusu boyutu 1000 piksel yüksekliğinde çerçevesinde IDE'nin en az bu 96 DPI çözünürlükte içinde uyacak şekilde aşmamalıdır.

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

 Bu durumda, "x" uyarı için kullanılan simge içerdiği için ek bir sorun olduğundan, ortak kaldırmak için simgesinin yanında kullanılamaz. Sonuç olarak, kullanıcı Arabirimi daha clunky denetimi bir Kaldır düğmesini kullanır.

 ![Bildirim Tasarımcısı hata bildirimi anti&#45;deseni](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti düzeni")

 **UI hata durumunda, varsayılan yerleştirme bir Visual Studio koruma desendir.**

#### <a name="alternatives"></a>Alternatifleri
 Bu sorun için bir çok daha iyi çözüm olacaktır:

-   Bir uyarı bildiriminde eklemek kullanıcının ve öğede özelliklerini ayarlamak hemen taşıyın.

-   Uyarı simgesi (gold üçgen) ekleme zaman odak taşır öğesinden gibi başka bir bildirimi listeye ekleyin veya tasarımcı sekmelerde değiştirme girişimi.

-   Kullanıcının sekme özellikleri tüm bildirimlerinde ayarlamadan önce çalışırsa, uygulaması olmayan oluşturacaksınız açıklayan bir iletişim kutusu açılır (veya hangi etkilerini) uyarıları çözülene kadar. Yine de kullanıcı iletişim kutusunu kapatır ve sekmeleri değiştirirse (kritik veya uyarı, uygun şekilde) simge için bildirimler sekmesine eklenir.

### <a name="forcing-the-user-to-read-text-before-dismissing-ui"></a>Kullanıcı UI kapatılıyor önce metin okuma için zorlama

#### <a name="feature-team-goals"></a>Takım hedeflerine özelliği
 Kullanıcı, kullanıcı Arabirimi açıklama metni görmeden kapatmak izin verme.

#### <a name="anti-pattern"></a>Koruma düzeni
 Video bağlantıları X sık karşılaşılan desenini karşı karar VS UI içinde çeşitli yerlerde içine ekleyerek takım düğmesi ve araç ipucu açıklaması UX tarafından belirtilen kapatın ve bunun yerine bir açılır ve "bir daha gösterme" bağlantı uygulanan.

 ![Kötü amaçlı yazılımdan koruma açıklayıcı metin&#45;deseni &#45; yanlış](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")

 **Yanlış: kullanıcı UI kapatılıyor önce açıklayıcı metin okumak için zorlama bir önleyici Visual Studio içinden modelidir.**

#### <a name="result"></a>Sonuç
 Bir basit Kapat düğmesi (tek bir tıklamayla) kullanıcı kullanıcı Arabiriminde görünen video bağlantıları her yerde verilecek iki tıklamada kullanmak için zorlanır.

#### <a name="alternatives"></a>Alternatifleri
 Internet Explorer, Office ve Visual Studio için ortak desen izlemek için bu durum için doğru tasarım olacaktır: üzerine gelindiğinde, kullanıcı tooltip açıklamasını görebilir ve tek bir tıklamayla kullanıcı arabirimini gizler.

 ![Kötü amaçlı yazılımdan koruma açıklayıcı metin&#45;deseni &#45; doğru](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti desenini düzeltin")

 **Doğru: tasarlandığı gibi ek bilgileri içeren bir araç ipucu üzerine gelindiğinde video bağlantıları görüntülenmelidir ve "X" işaretine tıklayarak daha fazla etkileşim için gerek kalmadan iletisini kapat.**

### <a name="using-command-bars-for-settings"></a>Komut çubuğu ayarları için kullanma
 ![Komut çubuğu anti&#45;deseni &#45; Şekil A](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti deseni FigureA")

 **Şekil y: komut çubuğu koruma düzeni**

 **Şekil A** Bu koruma düzeni temsil eder: ayarı daha fazlasını komutu geçerli bir komut düğmesi altındaki yerleştirme. Bu taslağı hata ayıklamayı Başlat yanı sıra komutları vardır — ister tarayıcı, hata ayıklama olmadan başlat ve içine adımla görünümünde — seçili olan ayar dikkate.

 ![Komut çubuğu anti&#45;deseni &#45; şekil B](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti deseni FigureB")

 **Şekil B: daha iyi, ancak yine de bir komut çubuğu koruma düzeni**

 Biraz daha iyi, ancak hala istenmeyen sokarak ayarlar bu türün araç çubuklarını, gösterildiği gibi **şekil B**. Bölünmüş düğme daha az yer kaplar ve bu nedenle bir geliştirme açılan listeler, ancak her iki tasarımın bir araç çubuğu gerçekten bir komut değil bir şey yükseltmek için yine de kullanmaktadır.

 ![Komut çubuğu anti&#45;deseni &#45; şekil C](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti deseni FigureC")

 **Şekil C: doğru Visual Studio komut çubuğu desenini kullanın**

 İçinde **şekil C**, ayar, bir dizi komut bağlıdır. Ayarlanan genel ayar yoktur ve biz yalnızca dört komuttan arasında geçiş yapıyorsanız. Bu, araç çubuğundaki komutları kabul edilebilir tek durumdur.

### <a name="control-anti-patterns"></a>Denetim ters desenler
 İçin bazı ters desenler, yalnızca yanlış kullanımı veya bir denetim veya denetimlerin Grup sunumu olabilir.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Bir köprü bir Grup etiketi kullanılan alt çizgi
 Altı çizili metin yalnızca köprüler için kullanılmalıdır.

 **Hatalı:**

 ![Kötü amaçlı yazılımdan koruma altı çizili&#45;grubu etiketleri desende](../../extensibility/ux-guidelines/media/0102-g-grouplabelincorrect.png "0102 g_GroupLabelIncorrect")

 **Köprü değil altı çizili metni bir Visual Studio koruma desendir.**

 **İyi:**

 ![Kötü amaçlı yazılımdan koruma altı çizili&#45;grubu etiketleri desende &#40;doğru&#41;](../../extensibility/ux-guidelines/media/0102-h-grouplabelcorrect.png "0102 h_GroupLabelCorrect")

 **Doğru biçimlendirilmiş, olmayan köprü metin ortam yazı tipini eksiz görünür.**

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Bir açılır iletişim kutusu bir onay kutusu sonuçları tıklayarak
 "Windows Azure uygulaması Yayımla" sihirbazında "Tüm roller için Uzak masaüstünü etkinleştir" onay kutusunu hemen tıklayarak, bir Visual Studio koruma desen gibi açılır bir iletişim kutusunu açar. Ayrıca, onay kutusu alanı içeren bir onay kutusu seçildikten sonra dolmaması başka bir etkileşim koruma modeli.

 ![Onay kutusu pop&#45;en kötü&#45;deseni](../../extensibility/ux-guidelines/media/0102-i-checkboxpopup.png "0102 i_CheckboxPopup")

 **Bir iletişim kutusu bir onay kutusunu tıklatarak bir Visual Studio koruma desendir sonra getirme.**

### <a name="hyperlink-anti-patterns"></a>Köprü ters desenler
 Aşağıdaki örnek, iki ters desenler içerir.

1. Üzerine gelindiğinde kırmızı kapatma ön doğru paylaşılan rengi yazı tipi hizmetinde kullanılmadığı anlamına gelir.

2. "Daha fazla bilgi edinin" değil bir kavramsal konuya bağlantısını için uygun metni. Kullanıcının hedef daha kendi seçtikleri etkilerini öğrenmektir değil öğrenmektir.

   ![Kötü amaçlı yazılımdan koruma köprü&#45;desenleri](../../extensibility/ux-guidelines/media/0102-j-hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")

   **Renk hizmet yoksayılıyor ve "daha fazla bilgi edinmek için köprüler" kullanarak Visual Studio ters desenler var.**

   **Daha iyi bir çözüm:** anın bağlantıya tıklayarak soru konusunda sizi uyarmayı.

-   Windows Azure hizmetleri nasıl çalışır?

-   Bir Windows Azure Mobile Services projesi ne gerekir?

#### <a name="using-click-here-for-links"></a>"Bağlantıları için buraya tıklayın" kullanma
 Köprüler, kendini açıklayıcı olmalıdır. Bu, "buraya tıklayın" kullanmak için koruma desen veya benzer bir değişim olur.

 **Hatalı:** "Buraya yeni bir proje oluşturma hakkında yönergeler için tıklayın."

 **İyi:** "Nasıl oluşturabilirim yeni bir proje?"
