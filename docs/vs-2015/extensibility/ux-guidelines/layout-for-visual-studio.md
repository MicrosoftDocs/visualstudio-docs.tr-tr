---
title: Düzen
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ce6d1a39f568986dfd77ed47fc2da18bf3da7ee4
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063683"
---
# <a name="layout-for-visual-studio"></a>Visual Studio düzeni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio iletişim kutularını etkinleştirildiklerinde [yardımcı iletişim düzeni](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), bu izleme standart iletişim kutuları unthemed olduğu [Windows Masaüstü iletişim düzeni ilkeleri](https://msdn.microsoft.com/library/windows/desktop/dn742499\(v=vs.85\).aspx). Visual Studio kullanıcı arabirimini yenilemek hareket ettikçe daha belirgin iletişim kutularının bunları olarak ürün tanımlama deneyimler oluşturur, yeni bir tasarım vardır. Bunlar [temalı iletişim düzeni](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) konulu bir görünüme sahip.

##  <a name="BKMK_UtilityDialogLayout"></a> Yardımcı program iletişim düzeni

-   Bir yardımcı programı iletişim kutusu içindeki tüm denetimleri, üst/sol başlaması ve aşağı akış gerekir.

-   Merkezi denetimleri büyük alanını doldurmak için bir iletişim kutusu üzerinde hiçbir zaman.

-   Ortam yazı tipi için tüm iletişim metin kullanın. Bir görsel spec yazarken, belirli bir yazı tipi ve boyutu seçmek yerine ortam yazı tipi belirtin. Bkz: [ortam yazı tipi](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

-   Tutarlı denetim aralığı ve yerleşim hedef craftsmanship kalite desteklemek için kullanın.

-   İletişim kutuları arasında denetimleri, benzersiz bir juxtaposition denetimlerin veya her ikisini de daha büyük bir sayı daha karmaşık hale gelebilir. Bu karmaşık durumlarda, kullanıcıya ayrıştırmak için bir mantıksal akış vermek için Denetim gruplandırmaları arasında yeterli boşluk izin verir.

### <a name="utility-dialog-layout-examples"></a>Yardımcı program iletişim düzeni örnekleri
 Tüm boyutlar piksel cinsinden ifade edilir.

 ![Etiketleri yukarıda denetimleri için iletişim aralığı](../../extensibility/ux-guidelines/media/0801-a-utilityspacingabove.png "0801 a_UtilitySpacingAbove")

 **Şekil 08.01-a: yönergeleri denetimleri yukarıda etiketlerle yardımcı programı iletişim kutuları için Boşluklandırma**

 ![Denetimleri solundaki etiketlerin iletişim aralığı](../../extensibility/ux-guidelines/media/0801-b-utilityspacingleft.png "0801 b_UtilitySpacingLeft")

 **Şekil 08.01-b: yönergeleri denetimleri solundaki etiketlerle yardımcı programı iletişim kutuları için Boşluklandırma**

### <a name="layout-details"></a>Düzen ayrıntıları

#### <a name="margins"></a>Kenar boşlukları

-   Tüm iletişim kutuları, tüm köşelerindeki 12-piksel kenarlık olması gerekir.

-   Kenar boşlukları bir grup çerçevesinde çerçevenin kenarına 9 piksel olmalıdır.

-   Kenar boşlukları sekme denetimindeki sekme denetimi kenarından 6 piksel olmalıdır.

#### <a name="command-buttons"></a>Komut düğmeleri

- Komut düğmeleri içeriği değil, iletişim kutusu çerçevesi üzerinde çalışır. Bunlar, altta sağ yerleştirilmesi gerektiğini ve düğmeleri sonuçlanmaz ayrı ayarlamak için yukarıdaki değişken yeterli alana sahip olmalıdır.

- İletişim kutusu içinde çalışan yatay düğmeler varsa, diğer komut düğmesi yapılandırması sağ üst dikey bir yığınıdır. Bkz: [iç komut düğmeleri](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) aşağıda.

- Sol (alt sol/Merkezi iletişim) komut düğmesi alanı "bant" iletişim işlemi denetimlerinin bir parçası olarak kabul edilir. Bu alan intrude tek şey, genel görev ya da iletişim ile ilgili Yardım bağlantısıdır.

- Komut düğmeleri, 75 x 23 piksel olmalıdır.

- Komut düğmeleri uzaklıkta 6 piksel olmalıdır.

  ![Temel düğme hizalaması](../../extensibility/ux-guidelines/media/0801-c-buttonalign.png "0801 c_ButtonAlign")

  **Şekil 08.01-c: Temel düğme hizalaması**

#### <a name="labels"></a>Etiketler

-   Sola Hizala tüm etiketleri.

-   Bir denetimin üzerine sit etiketler, bunlar sol-denetimi altındaki ile tam olarak hizalanmasını ve alt etiketinin üst denetimin diğer (örneğin, bir birleşik giriş kutusu) yukarıda 5 piksel olmalıdır.

-   Denetimleri solunda sit etiketleri, minimum genişliğini giriş denetiminin etiket arasındaki 10 pikseldir. Metin kutuları, birleşik giriş kutuları veya diğer denetimleri hizalama için örtük bir ikinci sütunda kurulmalıdır.

-   Etiketleri cümle olduğunu ve bir üste. Bkz: [metin stili](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

#### <a name="distance-between-controls"></a>Denetimler arasındaki uzaklığı
 Denetimleri makul yığın. Yığılmış denetimler arasındaki aralığı için mutlak hiçbir kılavuz yoktur. Denetimler arasındaki tightness iletişim kutuları arasında biraz farklılık gösterebilir. Önerilen boşluk dikey denetim/etiket çiftleri için 20 piksel ve yatay denetimi etiketi çiftleri için 9 piksel olabilir. Yatay çiftleri için en az bir denetim aralığı 6 pikseldir.

 ![Denetimler arasındaki uzaklığı önerilen](../../extensibility/ux-guidelines/media/0801-d-controldistance.png "0801 d_ControlDistance")

 **Şekil 08.01-d: Denetimler arasındaki uzaklığı önerileri**

#### <a name="control-indentation"></a>Denetim girinti
 Denetimleri iç içe geçmiş, iç denetimleri denetimi yukarıdaki genellikle etiket sol kenarı ile yatay olarak hizalayın.

 ![İç içe geçmiş denetim hizalaması](../../extensibility/ux-guidelines/media/0801-e-controlalign.png "0801 e_ControlAlign")

 **Şekil 08.01-e: İç içe geçmiş denetim hizalaması**

#### <a name="control-width"></a>Denetim genişliği
 Bir metin kutusu veya benzer diğer denetimlerin genişliğini ortalama giriş alanı için daha uzun olmamalıdır. Ortalama İngilizce word beş karakterdir. Örneğin, bir uzun yol adı gerekli bir metin kutusu yatay düzeni sağlar, sürece olmalıdır çalışırken bir açılır platform adları yalnızca uzun girişini sağlayan bir uzunlukta olmalıdır.

#### <a name="helper-text"></a>Yardımcı metni

-   Bir iletişim kutusu iletişim amacı hakkında daha fazla bilgi sağlayan bir yardımcı metni görüntüleyebilirsiniz. Bu genellikle en üstünde yer alan ve 1-2 cümleler olabilir.

-   Satır uzunluğu, ayrıştırma ve okumak bir kullanıcı için rahat genişliği olmalıdır. Orta ölçekli bir iletişim kutusu, en fazla 550 piksel genişliğinde olmalıdır.

####  <a name="BKMK_InteriorCommandButtons"></a> İç komut düğmeleri
 Daha karmaşık iletişim kutularında, bir iç denetim iletişim kutusunun yürütme düğmeleri bulunduğu yere şeklinizi etkileyebilecek olan ilgili kendi düğmeleri olabilir.

- İç bir dikey hizalama (sütun) düğmelerini kullanın **Tamam**/**iptal** sağ alt köşede yatay olarak yerleştirilir.

- Düğmeleri yatay hizalama (satır), iç kullanım **Tamam**/**iptal** sağ üst köşedeki dikey olarak yerleştirilir. Bu durum daha az yaygındır.

- İç düğme boyutu, 75 x 23 piksel cinsinden boyutu ile eşleşen standart düğme boyutu hedef **Tamam**/**iptal** mümkün olduğunda düğme. Bir düğme etiketi standart düğme boyutu aşan düğmesi yaparsa bu kümedeki diğer düğmeleri, daha geniş bir boyutu ile hizalamanız gerekir.

  ![Yatay Tamam ve İptal düğmeleri](../../extensibility/ux-guidelines/media/0801-f-horizokcan.png "0801 f_HorizOKCan")

  **Şekil 08.01-f: Dikey iç yatay Tamam/iptal düğmesi**

  ![Dikey Tamam ve İptal düğmeleri](../../extensibility/ux-guidelines/media/0801-g-vertokcan.png "0801 g_VertOKCan")

  **Şekil 08.01-g: Yatay iç düğmeleriyle dikey Tamam/iptal**

#### <a name="browse-button"></a>[Gözat...] Düğme
 **[Gözat...]**  izleyen bir metin kutusu düğmeleri nokta dahil olmak üzere, tam olarak "Gözat..." Yazım. Alanı sıkı veya birden fazla varsa **[Gözat...]**  ekrandaki düğmeye düğmeleri yalnızca üç nokta sınırlı.

##  <a name="BKMK_ThemedDialogLayout"></a> Temalı iletişim düzeni
 Visual Studio'da temalı iletişim kutuları, daha açık bir görünüme sahip ve daha fazla boşluk sunar. Daha fazla vurgu ve ilgi alanı, daha açık satır aralığı ve yazı tipi boyutu ve ağırlıklarını çeşitlemesi sunan tipografi sağlar. Mümkünse, chrome ve başlık çubukları sınırlı veya kaldırılan. Bu iletişim kutularını düzenini temel bu deseni izlemelidir:

1.  İletişim kutusunun arka plan beyaz.

2.  Orta değer gri renkle kural 1 piksel kenarlık yoktur.

3.  İletişim kutusu başlığı artık, başlık çubuğunda bulunur, ancak görsel açıdan ilgi çekici ve Vurgu daha büyük bir nokta boyutu sağlar. (Yazı tipi boyutu bölümüne bakın [metin stili](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)

4.  Bir açıklama gibi ek metin ile birlikte etiketleri olmalıdır **ortam yazı tipi + kalın**.

5.  İç sütun açık gri 1 piksel kuralda tarafından ayrılır.

6.  Altı çizili olmadığı varsayılan bağlantıları vardır. Hover ve basılı durumları rengi değiştirme ve alt çizgi vardır.

7.  Yürütme düğmeleri (gibi **Tamam**/**iptal**) sağ alt köşesinde yaslanın.

### <a name="themed-dialog-layout-examples"></a>Temalı iletişim düzeni örnekleri
 ![Temalı iletişim düzeni](../../extensibility/ux-guidelines/media/0801-h-themeddialog.png "0801 h_ThemedDialog")

 **Şekil 08.01-h: Temalı iletişim**

 ![Temalı iletişim boyutları](../../extensibility/ux-guidelines/media/0801-i-themeddialogdimensions.png "0801 i_ThemedDialogDimensions")

 **Şekil 08.01-ı: Temalı iletişim – boyutları**

 ![Temalı iletişim kutusu yazı tipleri](../../extensibility/ux-guidelines/media/0801-j-themeddialogfonts.png "0801 j_ThemedDialogFonts")

 **Şekil 08.01-j: Temalı iletişim – yazı tipleri**

 ![Renk teması iletişim](../../extensibility/ux-guidelines/media/0801-k-themeddialogcolors.png "0801 k_ThemedDialogColors")

 **Şekil 08.01-k: Temalı iletişim – renkleri**

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio için uygulama desenleri](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md) [denetimleri (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx) [iletişim kutuları (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742499\(v=vs.85\).aspx)
