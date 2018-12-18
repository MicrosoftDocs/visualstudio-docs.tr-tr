---
title: Değerlendirme Araçları
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18d055e5fc38c4bd212455773bc5d02ca741edf0
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052459"
---
# <a name="evaluation-tools-for-visual-studio"></a>Visual Studio için değerlendirme araçları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="craftsmanship-checklist-for-visual-studio"></a>Visual Studio için craftsmanship denetim listesi
 Görsel ve etkileşim Ayrıntılar için kullanıcı deneyimi kalitesini değerlendirmek için bu denetim listesini kullanın.

### <a name="overview"></a>Genel Bakış

-   Tüm komutlar kullanıcılar kendi komutları gerçekleştirildikten olduğunu bildiren bir geri bildirim neden olduğunu doğrulayın.

-   Tüm kullanıcı Arabirimi öğeleri ve denetimleri tüm temalar ve yüksek karşıtlık modunda görünür olduğundan emin olun.

-   Bu etkin olmayan doğrulayın ve etkin seçimin her zaman Ayrıştırılan, standart ve yüksek karşıtlık modunu kullanmak.

-   Odağı her zaman görünür ve görünür olduğundan emin olun.

### <a name="performance"></a>Performans

-   Bir komutu tamamlamak için birden fazla bir saniye sürüyorsa, bazı tür "meşgul" göstergesi göründüğünü doğrulayın.

-   Bir komut 10, bir açık bir ilerleme çubuğu ya da tamamlamak için saniyeden uzun sürerse doğrulayın kararlı (tercih edilen) veya belirsiz, görüntülenir.

### <a name="ui-text"></a>UI metni

-   Tüm etiketler cümle veya başlık durumda olduğunu ve hiçbir metin tamamen küçük harf olduğunu doğrulayın.

    ||Düzeltin|Yanlış|
    |-|-------------|---------------|
    |**Komut metni (Tümü)**|Cümle:<br /><br /> **Dizin adı:**|Dizin adı:|
    |**Düğme metni (istemci)**|İlk harfler büyük:<br /><br /> **[Varsayılan olarak ayarla]**|KÜMESİ AS VARSAYILAN|
    |**Düğme metni (çevrimiçi)**|Cümle:<br /><br /> **[Varsayılan olarak ayarla]**||

-   Grup başlıklarının ve düğmeler, hariç tüm etiketleri iki nokta ile bitemez ve bunlar ile eşleştirilmiş durumda denetim adından önce doğrulayın.

-   Düğmeler, komutları ve kullanıcı girişi yakalamak için kullanıcı arabirimini Başlat komutu bağlantıları üç nokta son doğrulayın **[...]** .

     Örnekler:

    -   Bir **[Gelişmiş...]**  düğmesine bir iletişim kutusu.

    -   Araçlar menüsü altına komut seçenekleri (**Araçlar > Seçenekler**) iletişim başlatma komut hedefi olduğu için üç nokta simgesine almalısınız değil.

-   Kullanıcı arabirimini endüstri standardı koşulları hariç hiçbir kısaltmalar içerdiğini doğrulayın. Örneğin, HTML ne TCP/IP'yi gerekir, yazılması karşılaştığınız OOM (yetersiz bellek) ve PII (kişisel bilgiler) gerekir ancak.

### <a name="keyboard-access"></a>Klavye erişimi

-   Klavye ile her bir görevi gerçekleştirmek için bir yol olduğundan emin olun. Genellikle bu her denetimin klavye erişim aracılığıyla gerçekleştirilir, ancak kod görünümüne giderek gibi geçici bir çözüm yüksek ölçüde görsel bazı alanlar için kabul edilebilir.

-   Bir mantıksal sırasına (soldan sağa ve yukarıdan aşağıya) denetimleri aracılığıyla sekme tuşuyla doğrulayın. Tüm denetimleri, bu çoğu denetimleri için en iyi yöntem olsa da, bu yaklaşım gerektirir. Örneğin, bu radyo düğmesi grubundaki tek sekme durağı ile denetimlerdir doğrulayın.

-   Tüm denetimleri etiketlere sahip ve her etiket bir anımsatıcı olduğunu doğrulayın (özel durumlar, etiketlenmiş bir sekme denetiminde uygulayabilir bazı olmayan etiketli denetimler içerir).

-   Anımsatıcı çakışma olduğundan emin olun.

### <a name="fonts"></a>Yazı Tipleri

-   Tüm yazı tipleri (yüz tanıma, boyutunu, rengini) tutarlı bir şekilde kullanılır ve hiyerarşi Bakımı olduğunu doğrulayın.

-   Tüm kullanıcı Arabirimi öğeleri ortam yazı tipi Hizmet kullandığından emin olun. (Bkz [yazı tipleri ve biçimlendirme için Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Hizmet kullanılıp kullanılmadığını kontrol etmek için Git **Araçlar > Seçenekler > yazı tipleri ve renkler**. Ayarları açılır listesinde, ortam yazı tipi seçin ve stylistically (Harp veya Comic SAN'ları gibi) farklı bir şey yazı tipini değiştirmek ve 12 punto Georgia boyutunu ayarlayın. Ardından Tamam'a tıklayın. IDE yeniden başlatmanız gerekebilir, ancak çoğu UI hemen değişir. Yazı tipi değişiklik bile yeniden'kurmak seçmeyin alanları ortam yazı tipi kullanmıyorsunuz demektir.

-   Hizmet (örneğin, kalın veya genişletilmiş metin) türevi olan yazı tipi, boyutu ve ortam yazı tipi boyutu değiştirildiğinde ile ilgili "normal" metin biçimlendiriliyor korumak doğrulayın.

-   Büyütülmüş yazı tipleri nedeniyle hiçbir kırpma hata olmadığını doğrulayın. Kırpılmış yazı tipleri büyük olasılıkla sabit yükseklik denetimleri veya sabit yükseklik kapsayıcıları sonucudur.

### <a name="dialogs"></a>İletişim Kutuları

-   İletişim kutusu başlığı onu başlatan komut ile aynı olduğunu doğrulayın.

-   Tüm standart denetimler işletim sistemi ile tutarlı olduğundan emin olun: arka plan rengi, standart ve hiçbir denetim standart denetimlerden farklı görünmesini yaptığına özel bir yeniden şablonlu stil olması gerekir.

-   Kenar boşluklarının içine formun 12 piksel olmalıdır ve Tekdüzen ve tutarlı görünmelidir olduğunu doğrulayın.

-   İletişim kutuları IDE kabuğu veya bunları kökenli penceresi içinde ortalanmış göründüğünü doğrulayın.

-   İletişim kutuları, kullanışlı, yeniden boyutlandırılabilir olmalıdır. Yeniden boyutlandırılabilir, iletişim kutuları için iletişim diğer bölümlerini sabit kalırken yeniden boyutlandırma sırasında uygun denetimleri yeniden boyutlandırmanız gerekir olduğunu doğrulayın.

-   Yeniden boyutlandırılabilir iletişim kutuları (boyut, konum, genişletme iletişim kutusu denetimleri ve benzeri) kullanıcı ayarlanmış boyutu kalıcı olduğunu doğrulayın.

-   Başlık çubuğunda herhangi bir simge olduğundan emin olun.

-   Başlık çubuğunda hiçbir simge durumuna küçült ve Ekranı Kapla düğmeleri olduğunu doğrulayın.

#### <a name="dialog-operation-buttons-vs-client-only"></a>İletişim işlemi düğmeler (yalnızca VS istemci)

-   İşlem düğmeler bu sırada olduğundan emin olun: **Tamam**, **iptal**, **Uygula**.

-   Doğrulayın **Tamam** ve **iptal** düğmelerdir standart boyutu: 75 x 23 piksel.

-   Doğrulayın **Tamam** ve **iptal** dize uzunluğu bağımsız olarak aynı boyutta düğme vardır.

-   Etiket işlemi düğmesindeki standart geniş olmasını gerektiriyorsa, doğrulayın karşılık gelen **iptal** aynı boyutta düğmesidir.

-   Bir düğme ve ilişkili denetimler arasında 6-piksel doldurma olduğundan emin olun.

-   Doğrulayın **Tamam** ve **iptal** düğmeleri anımsatıcıları (erişim tuşları bir altı çizili harfi ile tanımlanır) sahip değil.

-   Bir düğmenin doğrulayın (genellikle **Tamam**) varsayılan olarak odağa sahip.

-   Doğrulayın **Esc** iletişim kutusunu iptal eder

-   Doğrulayın **Enter** varsayılan düğme odak Enter işleyen bir denetimde değilse yürütür.

-   Doğrulayın **Tamam** ve **iptal** düğmeler iletişim kutusunun sağ alt köşede konumlandırılmıştır. Nadir durumlar için sağ üst köşede dikey yığın için kabul edilebilir.

-   Yalnızca bir yatay hizalama iletişim kutusu içinde diğer düğmeleri, dikey yapılandırma kullanıldığını doğrulayın.

### <a name="control-standards"></a>Denetimi standartları

#### <a name="general"></a>Genel

-   Mümkün olduğunda, kullanıcı etkileşimi ve kullanıcıların güvenli veya ortak bir sonucu doğru hızlandırmak için iyi bir varsayılan değerleri doğrulayın.

-   Standart denetimler kullanıcılara göre daha eski deneyimi ne olacağını öğrenmek için aynı şekilde davrandığından emin olun.

#### <a name="label-controls"></a>Etiket denetimleri

-   Her denetim bir etiketi vardır ve her bir etiket denetimi (genellikle bir aralıkta 4-6 piksel) ile görsel olarak eşleştirilir ve onun ilgili denetimin diğer denetimlere yakın doğrulayın.

-   Etiket temizleme konumlandırılır doğrulayın denetimi ile sol üstündeki konumlandırılmışsa sol kenarının ve böylece temel etiketin solunda konumlandırılmışsa giriş metni taban çizgisi ile hizalanır Yatay Orta.

-   Birkaç Yığılmış etiket ve giriş denetimlerinin bir denetimin sola konumlandırılır etiketleri temizleme bırakılır ve iletişim kenarı arasındaki uzaklık eşit hiçbir zaman temizleme sağ ve denetimler arasındaki uzaklık eşit olduğunu doğrulayın. Ek boşluk gruplandırma belirtmek için ihtiyaç duydukları sürece çiftleri eşit olarak dağıtılmış.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Giriş denetimlerini (metin kutuları ve birleşik giriş kutuları)

-   Varsayılan ortam yazı tipi kullanırken, metin kutuları, birleşik giriş kutuları ve düğmeler görüntü yüksekliğini tüm 23 piksel doğrulayın.

-   İpucu metni kullanılır, renk değerine ayarlandığını doğrulayın `Environment.ControlEditHintText` renk hizmetini kullanarak.

-   Alan şekilde tanımlanması gerekir gerekli bir alan ise doğrulayın:

    -   arka plan ayarlanan `Environment.ControlEditRequiredBackground` ve ön ayarlanır `Environment.ControlEditRequiredHintText`

    -   görünen denetimindeki İpucu metni olduğunu **"\<gerekli >"**

#### <a name="button-controls"></a>Düğme denetimleri

-   Düğmeler 75 x 23 piksel cinsinden boyutu için alt uzun metin destekleme sürece doğrulayın.

-   Düğmeler kaldı ve 3-5 piksel yanı sıra içerik için doldurma, kenar boşlukları sağ doğrulayın.

-   Küçük bir kare düğme yalnızca üç nokta ile kullanmak için kabul edilebilir **[...]**  yerine bunu üzerinde bir **[Gözat...]**  düğme (veya benzer bir işlevsellik). Kullandıysanız, düğmenin boyutu 23 x 23 olduğunu doğrulayın.

-   Varsa birden fazla **[Gözat...]**  düğme bir iletişim kutusunda, ardından doğrulayın kısaltılmış sürümü (yalnızca üç nokta **[...]** ) tüm için kullanılır.

-   Bu üç nokta doğrulayın **[...]**  düğmeleri bir anımsatıcı sahip değil. Bir sekme odağı yanında giriş denetiminin açık olduğunda, odağı üç nokta düğmesini taşımanız gerekir.

-   Düğmeler, komutları ve daha fazla kullanıcı girişi yakalayan İkincil kullanıcı arabirimini Başlat komutu bağlantıları üç nokta bitmelidir doğrulayın **[...]** .

#### <a name="hyperlinks"></a>Köprüleri

-   Bir hyperlink denetimi hiç etkin olduğunda kırmızı yanıp doğrulayın. Bu renk hizmeti kullanım düzenlenmiyor göstergesidir

-   VS kullanılan renkleri olduğundan emin olun:

    -   `Environment.ControlLinkText`

    -   `Environment.ControlLinkTextHover`

    -   `Environment.ControlLinkTextPressed`

-   Köprüler bir paragraf içinde gömülü sürece hiçbir alt çizgi ile mavi göründüğünü doğrulayın.

#### <a name="check-boxes"></a>Onay kutuları

-   Çok satırlı metin onay kutusu varsa kutunun tüm satırlar ortalanmış değil dikey metnin ilk satırı ile hizalar doğrulayın.

-   Onay kutularını her zaman ikili bir seçenek belirtmek ve değil kullanıcı gidin veya yeni bir windows veya sayfaları doğrulayın.

-   Bir onay kutusu için bir giriş denetimini ilgili bir seçenek sunar, temizleme sola ve çok yakın ilişkisi belirtmek için bu denetim altında konumlandırılmış olduğunu doğrulayın.

-   Bir onay kutusu olduğundan emin olun **hiçbir zaman** bir iletişim kutusu veya sayfanın tüm içeriğini etkinleştirmek için bir yol kullanılır.

#### <a name="group-boxes"></a>Grup kutuları

-   Bir iletişim kutusu iletişim tüm içeriğini içeren bir tek Grup kutusu içindeki içermediğinden emin olun.

-   Her grup kutusu içinde en az iki denetimi olduğunu doğrulayın.

-   Nadiren var. bir iletişim kutusundaki ikiden fazla Grup kutuları olmalıdır.

-   Hiçbir iç içe grup kutuları olduğunu doğrulayın.

### <a name="icons"></a>Simgeler

-   Simgeler, koyu tema doğru ters göründüğünü doğrulayın.

-   Tüm simgeleri çekirdek kavrama dayalıdır doğrulayın.

-   Her simge ayrı, kolay tanımaya ve ikiden fazla kavramları (olmadan durumu değiştiricisi/dil) içermiyor olduğunu doğrulayın.

-   Temel simgesi alanı içinde ortalanmış göründüğünü doğrulayın.

-   Tüm simgeleri yüksek karşıtlık modunda okunaklı göründüğünü doğrulayın.

-   Kullanılan herhangi bir rengi renk kullanımı standartlarıyla uyuştuğundan emin olun.

-   Hiçbir haleler (kenarlıklar) olmadığını simgeleri doğrulayın. (Varsa, halo bitişik kullanıcı arabiriminin arka plan rengi eşleşmelidir).

### <a name="touch-enabled-ui"></a>Dokunmatik özellikli kullanıcı Arabirimi

-   Etkileşimli denetimleri kolayca touchable – en az olacak şekilde büyük olduğundan emin olun **23 x 23 piksel** boyutu

-   En sık kullanılan denetimler en az olduğundan emin olun **40 x 40 piksel** boyutu.

-   Etkileşimli denetimleri en az sahip olduğunuzu doğrulayın **aralığı 5 piksel** aralarında
