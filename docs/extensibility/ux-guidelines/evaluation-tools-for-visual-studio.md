---
title: Visual Studio için değerlendirme araçları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a149d9163e61dd49105f123b373ecd9c7c1c278
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31147339"
---
# <a name="evaluation-tools-for-visual-studio"></a>Visual Studio için değerlendirme araçları
## <a name="craftsmanship-checklist-for-visual-studio"></a>Visual Studio için craftsmanship denetim listesi  
 Ayrıntılar visual ve etkileşim için kullanıcı deneyimi kalitesini değerlendirmek için bu denetim listesini kullanın.  
  
### <a name="overview"></a>Genel Bakış  
  
-   Tüm komutları kullanıcılar kendi komutları gerçekleştirildikten olduğunu söyler geri bildirim neden olduğunu doğrulayın.  
  
-   Tüm kullanıcı Arabirimi öğeleri ve denetimleri tüm temalar ve yüksek karşıtlık modunda görünür olduğunu doğrulayın.  
  
-   Etkin ve etkin seçimi her zaman Ayrıştırılan hem standart ve yüksek karşıtlık modunda olduğundan, doğrulayın.  
  
-   Odağı her zaman görünür ve görünür olduğunu doğrulayın.  
  
### <a name="performance"></a>Performans  
  
-   Bir komutu tamamlamak için birden fazla bir saniye sürer varsa bazı "meşgul" tür göstergesi göründüğünü doğrulayın.  
  
-   Bir komut, bir açık ilerleme çubuğu ya da tamamlamak için birden fazla 10 saniye sürerse doğrulayın belirli (önerilen) veya belirsiz, görüntülenir.  
  
### <a name="ui-text"></a>UI metin  
  
-   Tüm etiketleri cümle veya harfler büyük olduğunu ve hiçbir metin tamamen küçük harf olduğundan emin olun.  
  
    ||Düzeltin|Yanlış|  
    |-|-------------|---------------|  
    |**Komut metni (Tümü)**|Cümle:<br /><br /> **Dizin adı:**|Dizin adı:|  
    |**Düğme metni (istemci)**|İlk harfler büyük:<br /><br /> **[Varsayılan olarak ayarla]**|SET AS VARSAYILAN|  
    |**Düğme metni (çevrimiçi)**|Cümle:<br /><br /> **[Varsayılan olarak ayarla]**||  
  
-   Grup üstbilgileri ve düğmeleri, dışındaki tüm etiketleri noktayla bitmelidir ve sahip oldukları eşleştirilmelidir denetim adından önce doğrulayın.  
  
-   Düğmeler, komutları ve kullanıcı girişi yakalama için kullanıcı Arabirimi başlatma komut bağlantıları üç nokta bulunan end doğrulayın **[...]** .  
  
     Örnekler:  
  
    -   Bir **[Gelişmiş...]**  bir iletişim kutusu düğmesinde.  
  
    -   Araçlar menüsündeki komut seçenekleri (**Araçlar > Seçenekler**) iletişim başlatma komut hedefi olduğundan bir üç nokta almalısınız değil.  
  
-   Kullanıcı arabirimini endüstri standardı koşulları dışında hiçbir kısaltmalar içerdiğini doğrulayın. Örneği için HTML ne TCP/IP'yi gerekir, yazılması OOM (bellek) yetersiz ve PII (kişisel bilgi) gereken ancak.  
  
### <a name="keyboard-access"></a>Klavye erişimi  
  
-   Klavye ile her görevi gerçekleştirmek için bir yol olduğundan emin olun. Genellikle bu her denetim için klavye erişimi aracılığıyla gerçekleştirilir, ancak kod görünümüne giderek gibi geçici bir çözüm için yüksek oranda visual bazı alanlar, kabul edilebilir.  
  
-   Bir mantıksal sırasına (soldan sağa ve üst-alt) denetimlerinde aracılığıyla sekme tuşuyla doğrulayın. Bu çoğu denetimleri için en iyi yöntem olsa da, tüm denetimler bu yaklaşımı gerektirir. Örneğin, bu radyo düğmesi grubunda tek sekme durağı ile denetimleridir doğrulayın.  
  
-   Tüm denetimler etiketleri varsa ve her etiket bir anımsatıcı sahip olduğunu doğrulayın (özel durumlar sekmesini etiketli denetiminde uygulayabilir bazı etiketli olmayan denetimler içerir).  
  
-   Anımsatıcı çakışmalar olduğunu doğrulayın.  
  
### <a name="fonts"></a>Yazı Tipleri  
  
-   Tüm yazı tipleri (yüz, boyutunu, rengini) sürekli olarak kullanılır ve Hiyerarşiyi Koru doğrulayın.  
  
-   Tüm kullanıcı Arabirimi öğeleri ortamı yazı tipi Hizmet kullandığından emin olun. (Bkz [yazı tipleri ve Visual Studio için biçimlendirme](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))  
  
     Hizmet kullanılmakta olup olmadığını denetlemek için Git **Araçlar > Seçenekler > yazı tiplerini ve renkleri**. Ayarları açılır ortamı yazı tipi seçin ve (Etikan veya Comic Sans gibi) stylistically farklı bir şey için yazı tipi değiştirin ve 12 pt-boyutunu ayarlayın. Ardından Tamam'a tıklayın. IDE yeniden başlatmanız gerekebilir, ancak çoğu UI hemen değiştirir. Yazı tipi değişiklik bile yeniden başlatmayı alması olmayan alanları ortamı yazı tipi kullanmıyor.  
  
-   Hizmet (örneğin, kalın veya büyütülmüş metin) türevi yazı tipleri boyutlarına ve ortam yazı tipi boyutu değiştirildiğinde bağlantılı olarak "normal" metin biçimlendirmesini korumak doğrulayın.  
  
-   Büyütülmüş yazı tipleri nedeniyle hiçbir kırpma hatalar olduğunu doğrulayın. Kırpılmış yazı tipleri büyük olasılıkla sabit yükseklik denetimleri veya sabit yükseklik kapsayıcıları sonucudur.  
  
### <a name="dialogs"></a>İletişim kutuları  
  
-   İletişim kutusu başlığı, başlatılan komutu ile aynı olduğunu doğrulayın.  
  
-   Tüm standart denetimler işletim sistemi ile tutarlı olduğunu doğrulayın: arka plan rengi standart ve hiçbir denetim bunları standart denetimlerini farklı görünür hale getirir özel bir yeniden şablonlu stil olması.  
  
-   Formun içindeki kenar boşluklarını 12 piksel olmalı ve Tekdüzen ve tutarlı görünmelidir doğrulayın.  
  
-   İletişim kutuları IDE Kabuğu'nu veya bunları kökenli penceresi içinde ortalanmış göründüğünü doğrulayın.  
  
-   Yararlı, iletişim kutuları yeniden boyutlandırılabilir olması gerekir. Yeniden boyutlandırılabilir iletişim kutuları için diğer bölümleriyle iletişim sabit kalırken yeniden boyutlandırma bağlı uygun denetimleri yeniden boyutlandırma gerekir olduğunu doğrulayın.  
  
-   Yeniden boyutlandırılabilir iletişim kutuları (boyutu, konum, genişletme iletişim kutusu denetimleri ve benzeri) kullanıcı ayarlanmış boyutu kalıcı doğrulayın.  
  
-   Başlık çubuğunda simge olduğunu doğrulayın.  
  
-   Başlık çubuğunda hiçbir simge durumuna küçült ve Ekranı Kapla düğmeleri olduğunu doğrulayın.  
  
#### <a name="dialog-operation-buttons-vs-client-only"></a>İletişim işlemi düğmeler (yalnızca VS istemci)  
  
-   Bu sırada işlemi düğmeleri doğrulayın: **Tamam**, **iptal**, **Uygula**.  
  
-   Doğrulayın **Tamam** ve **iptal** düğme standart boyutu vardır: 75 x 23 piksel.  
  
-   Doğrulayın **Tamam** ve **iptal** düğmeleri olan dize uzunluğu bakılmaksızın aynı boyutta.  
  
-   Bir işlem düğmesi etiketi düğmeyi standart geniş olacak şekilde gerektiriyorsa, doğrulayın karşılık gelen **iptal** düğme eşit boyutu vardır.  
  
-   Düğmeler ve ilişkili denetimler arasındaki 6 piksel doldurmayı olduğundan emin olun.  
  
-   Doğrulayın **Tamam** ve **iptal** düğmeleri anımsatıcıları (altı çizili harfi ile tanımlanan erişim tuşları) sahip değil.  
  
-   Bu bir düğme doğrulayın (genellikle **Tamam**) varsayılan olarak odağa sahip.  
  
-   Doğrulayın **Esc** iletişim kutusunu iptal eder  
  
-   Doğrulayın **Enter** odak Enter işleyen bir denetiminde değilse varsayılan düğme yürütür.  
  
-   Doğrulayın **Tamam** ve **iptal** düğmeleri iletişim kutusunun sağ alt köşede konumlandırıldı. Nadir durumlar için sağ üst dikey Yığılmış için kabul edilebilir.  
  
-   Yalnızca diğer düğmelerini yatay hizalama iletişim içinde olduğunda dikey yapılandırma kullanıldığını doğrulayın.  
  
### <a name="control-standards"></a>Denetimi standartları  
  
#### <a name="general"></a>Genel  
  
-   Mümkün olduğunda, kullanıcı etkileşimi ve kullanıcıların bir güvenli veya ortak sonucunu doğru hızlandırmak için iyi varsayılan değerleri doğrulayın.  
  
-   Standart denetimler dayalı olarak önceki deneyimi ne olacağını kullanıcılar bilmesi aynı şekilde davranır doğrulayın.  
  
#### <a name="label-controls"></a>Etiket denetimleri  
  
-   Her denetim etiketi varsa ve her etiket görsel olarak denetimiyle (genellikle bir aralıkta 4-6 piksel) ile eşleştirilmiş ve diğer denetimler için karşılık gelen denetimden yakındır doğrulayın.  
  
-   Etiketleri temizleme konumlandırılmış doğrulayın denetimi ile sol yukarıda konumlandırılmış, sol kenarı ve böylece etiketinin temel sola konumlandırılmış durumunda giriş metni taban çizgisiyle hizalanır yatay ortalanmış.  
  
-   Bir denetimin sola yerleştirilmiş birkaç Yığılmış etiket ve giriş denetimlerini, etiketleri temizleme bırakılır ve iletişim kenarından eşit uzaklıkta hiçbir zaman flush hak ve eşit uzaklıkta denetimlerinden doğrulayın. Gruplandırma belirtmek için ek boşluk gerekmedikçe çiftleri eşit bir biçimde dağıtılması.  
  
#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Giriş denetimlerini (metin kutuları ve birleşik giriş kutuları)  
  
-   Varsayılan ortam font kullanırken, metin kutuları, birleşik giriş kutuları ve düğmeleri görüntüleme yüksekliğini tüm 23 piksel doğrulayın.  
  
-   İpucu metnini kullanılırsa, renk değerine ayarlandığını doğrulayın `Environment.ControlEditHintText` renk hizmetini kullanarak.  
  
-   Bu nedenle tanımlanmalıdır gerekli bir alan alanıysa doğrulayın:  
  
    -   arka plan ayarlandığı `Environment.ControlEditRequiredBackground` ve ön ayarı `Environment.ControlEditRequiredHintText`  
  
    -   İpucu metin olarak görünür denetim içindeki olduğunu **"\<gerekli >"**  
  
#### <a name="button-controls"></a>Düğme denetimleri  
  
-   Düğmeleri 75 x 23 piksel cinsinden minimum boyutu uzun metin destekleme sürece doğrulayın.  
  
-   Düğmeler bıraktıysanız ve 3-5 piksel olarak içerik için doldurma, kenar boşlukları sağ doğrulayın.  
  
-   Küçük bir kare düğme yalnızca üç nokta ile kullanmak için kabul edilebilir **[...]**  yerine üzerindeki bir **[Gözat...]**  düğmesi (veya benzer bir işlevsellik). Kullandıysanız, düğme 23 x 23 boyutu olduğundan emin olun.  
  
-   Varsa birden fazla **[Gözat...]**  düğmesini bir iletişim kutusunda, ardından doğrulayın kısaltılmış sürüm (yalnızca üç nokta **[...]** ) tümü için kullanılır.  
  
-   Bu üç nokta doğrulayın **[...]**  düğmeleri bir anımsatıcı sahip değil. Yanında giriş denetiminin odağı etkin olduğunda, bir sekme için üç nokta düğmesini odak taşımanız gerekir.  
  
-   Düğmeler, komutları ve daha fazla kullanıcı girişi yakalar ikincil kullanıcı arabirimini Başlat komutu bağlantılar üç nokta bulunan bitmelidir doğrulayın **[...]** .  
  
#### <a name="hyperlinks"></a>Köprüler  
  
-   Köprü denetim etkin olduğunda kırmızı hiçbir zaman yanıp sönen doğrulayın. Bu renk hizmeti kullanım alınmıyor bir göstergesidir  
  
-   VS kullanılan renkleri olduğunu doğrulayın:  
  
    -   `Environment.ControlLinkText`  
  
    -   `Environment.ControlLinkTextHover`  
  
    -   `Environment.ControlLinkTextPressed`  
  
-   Köprüler bir paragraf içinde katıştırılmış sürece hiçbir alt çizgiyle mavi göründüğünü doğrulayın.  
  
#### <a name="check-boxes"></a>Onay kutuları  
  
-   Bir onay kutusu çok satırlı metin kutusu tüm satıra ortalanmış değil dikey metnin ilk satırını uyuştuğundan emin olun, varsa.  
  
-   Onay kutuları her zaman ikili bir seçenek belirtmek ve değil kullanıcı gidin veya yeni windows veya sayfalarını açmak doğrulayın.  
  
-   Bir onay kutusu giriş denetimi ile ilgili bir seçenek sunar, onu temizleme sola ve çok Kapat onun belirtmek için bu denetimi altında konumlandırılır olduğunu doğrulayın.  
  
-   Bir onay kutusu olduğundan emin olun **hiçbir zaman** iletişim veya sayfası tüm içeriğini etkinleştirmek için bir araç olarak kullanılır.  
  
#### <a name="group-boxes"></a>Grup kutuları  
  
-   Bir iletişim kutusu, iletişim tüm içeriğini içeren bir tek Grup kutusu içindeki içermediğinden emin olun.  
  
-   Her grup kutusu içinde en az iki denetimleri olduğunu doğrulayın.  
  
-   Nadiren var. bir iletişim kutusundaki ikiden fazla Grup kutuları olmalıdır.  
  
-   İç içe grup kutuları olduğunu doğrulayın.  
  
### <a name="icons"></a>Simgeler  
  
-   Simgeler tıklattığınızda koyu tema doğru ters göründüğünü doğrulayın.  
  
-   Tüm simgeleri temel kavramlar dayalı doğrulayın.  
  
-   Her simge ayrı, tanımak kolay ve ikiden fazla kavramları (olmadan durum değiştiricisi/dil) içermiyor doğrulayın.  
  
-   Temel simge alanı içinde ortalanmış göründüğünden emin olun.  
  
-   Tüm simgeleri yüksek karşıtlık modunda okunaklı göründüğünü doğrulayın.  
  
-   Kullanılan rengi renk kullanım standartlarıyla uyuştuğundan emin olun.  
  
-   Hiçbir haleleri (kenarlıklar) olduğunu simgeleri doğrulayın. (Varsa, hale bitişik UI arka plan rengini eşleşmelidir).  
  
### <a name="touch-enabled-ui"></a>Dokunmatik özellikli kullanıcı Arabirimi  
  
-   Etkileşimli denetimleri kolayca touchable - en az olacak şekilde büyük olduğundan emin olun **23 x 23 piksel** boyutu  
  
-   En sık kullanılan denetimleri en az olduğundan emin olun **40 x 40 piksel** boyutu.  
  
-   Etkileşimli denetimleri en az sahip olduğunuzu doğrulayın **aralığı 5 piksel** aralarında