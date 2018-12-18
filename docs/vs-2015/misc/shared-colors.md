---
title: Paylaşılan renkler | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d3186f3-07d2-441f-b33e-435e95d8a0b8
caps.latest.revision: 11
ms.author: v-brickg
ms.openlocfilehash: fa4d2235660ecd7cc61998aa0e4ba568f0f28593
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805521"
---
# <a name="shared-colors"></a>Paylaşılan renkler
Açıklamayı buraya ekleyin.  
  
## <a name="shared-colors"></a>Paylaşılan renkler  
 Ortak Visual Studio shell öğeleri kullanan kullanıcı Arabirimi tasarlarken veya arabirimi öğeniz benzer özellikleri ile tutarlı olmasını istediğiniz, mevcut belirteç adları paket tanımı dosyaları seçin ve renkleri atamak için kullanın. Bu tema eklendiğinde veya güncelleştirildiğinde, otomatik olarak güncelleştirir ve kullanıcı Arabirimi ile genel Visual Studio ortamının tutarlı kalmasını sağlar.  
  
 Bu makalede, sık kullanılan UI öğeleri ve benzer kullanıcı Arabirimi oluşturma sırasında başvuran kullandıkları, belirteç adlarını açıklanır. Bu renk belirteçleri erişim hakkında ayrıntılı bilgi için bkz: [VSColor hizmet](../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
 Doğru belirteci adları kullandığınızdan emin olun:  
  
-   **İşlevi, renk üzerinde dayalı belirteç adları kullanın.** Ortak paylaşılan renkler, belirli bir arabirim öğeleri ile ilişkili ve yalnızca aynı veya benzer özellikler için kullanılmak üzere tasarlanmıştır. Örneğin, dönen ilerleme animasyonunun basılı açılan kutusu rengi renk istediğiniz olduğundan yeniden kullanmayın. Birleşik giriş kutusu ve animasyon işlevleri farklıdır ve renk birleşik giriş kutusu değişikliklerle ilişkili, artık animasyon öğeniz için uygun bir renk olabilir. Renk tutarlı kullanımı, kullanıcılarınızın yönlendirmek ve Karışıklığı önlemek yardımcı olur.  
  
-   **Arka plan ve metin renklerini doğru birlikte kullanın.** Metin ile kullanılmaya yönelik arka plan renklerini, ilişkili metin rengi sahip olur. Metin renkler, arka plan bilgileri için belirtilen dışında kullanmayın. İlişkili metin rengi değilse, arka plan rengi metni görüntülemek beklediğiniz tüm yüzeyi için kullanmayın. Diğer metin ve arkaplan renklerini birleşimlerini okunamayan bir arabirimde neden olabilir.  
  
-   **Konumlarına için uygun olan denetim renkleri kullanın.** Bazı durumlarda, bazı Visual Studio denetimler ayrı kenarlık ve arka plan renkleri yoktur. Bunun yerine, bu yüzeyleri arkasına renkleri ayarlama seçin. Her zaman burada denetimin yerleştirme konumu için uygun olan belirteci adları kullandığınızdan emin olun.  
  
> [!IMPORTANT]
>  "Başlangıç sayfası" veya "Şarabıı" kategoride bulunan belirteçleri kullanmayın!  
  
### <a name="command-structures"></a>Komut yapıları  
  
####  <a name="BKMK_CommandMenus"></a> Menüler  
 Menüleri, Visual Studio 2013 içinde çeşitli yerlerde oluşabilir: belge veya araç pencerelerini veya IDE tamamında çeşitli konumlarda sağ katıştırılmış ana menü çubuğu. Menü diğer UI öğeleri ile ilişkili uygulamalar için ilgili öğenin bölümünde ele alınmıştır. Visual Studio ortamı tarafından sağlanan standart menü uygulama her zaman kullanmalısınız. Ancak, bazı ender durumlarda, standart bir Visual Studio menülerinin erişimi olmayabilir. Bu gibi durumlarda, kullanıcı Arabirimi diğer Visual Studio menülerinde ile tutarlı olmasını sağlamak için aşağıdaki belirteci adları kullanın.  
  
 ![Menüler kırmızı çizgi](../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303 000_MenuRedline")  
  
 Kullan...  
 -   herhangi bir zamanda, özel bir menü oluşturmanız gerekir.  
  
- Visual Studio menülerinin eşleştirmek istediğiniz yeni bir kullanıcı Arabirimi bileşeninin olduğunda.  
  
  Kullanmayın...  
  tek başına arka plan rengi. Her zaman arka plan/ön plan birlikte belirtilen kullanın.  
  
##### <a name="menu-title"></a>Menü başlığı  
 Genellikle bir Komut çubuğuna menü bulunduğunda menü başlığı arka plan, kenarlık ve başlık metnini yanı isteğe bağlı bir karakter oluşur.  
  
 ![Menü başlığı kırmızı çizgi](../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303 001_MenuTitleRedline")  
  
 Kullan...  
 Her bir özel menü başlığı oluşturuyorsunuz.  
  
 Kullanmayın...  
 -   her şey için her zaman istemediğiniz menü başlığının eşleştirin.  
  
- Belirtilen dışındaki tüm arka plan/ön plan arada.  
  
  **Default**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menü başlığı varsayılan](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303 002_MenuTitleDefault")<br /><br /> **Menü başlığı**|Arka Plan|Yok.|  
|![Menü başlığı varsayılan](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303 002_MenuTitleDefault")<br /><br /> **Menü başlığı**|Ön plan (metin)|`Environment.CommandBarTextActive`|  
|![Menü başlığı glif varsayılan](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303 003_MenuTitleWithGlyphDefault")<br /><br /> **Menü başlığı karakter ile**|Ön plan (karakter)|`Environment.CommandBarMenuGlyph`|  
|![Menü başlığı glif varsayılan](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303 003_MenuTitleWithGlyphDefault")<br /><br /> **Menü başlığı karakter ile**|Kenarlık|Yok.|  
  
 **Vurgulu**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menü başlığı üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303 004_MenuTitleHover")<br /><br /> **Menü başlığı**|Arka Plan|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Menü başlığı üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303 004_MenuTitleHover")<br /><br /> **Menü başlığı**|Ön plan (metin)|`Environment.CommandBarTextHover`|  
|![Menü başlığı ile üzerine gelindiğinde glif](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303 005_MenuTitleWithGlyphHover")<br /><br /> **Menü başlığı karakter ile**|Ön plan (karakter)|`Environment.CommandBarMenuMouseOverGlyph`|  
|![Menü başlığı ile üzerine gelindiğinde glif](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303 005_MenuTitleWithGlyphHover")<br /><br /> **Menü başlığı karakter ile**|Kenarlık|`Environment.CommandBarBorder`|  
  
 **Basılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menü başlığı basılı](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303 006_MenuTitlePressed")<br /><br /> **Menü başlığı**|Arka Plan|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Menü başlığı basılı](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303 006_MenuTitlePressed")<br /><br /> **Menü başlığı**|Ön plan (metin)|`Environment.CommandBarTextActive`|  
|![Menü başlığı basılı karakteri ile](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303 007_MenuTitleWithGlyphPressed")<br /><br /> **Menü başlığı karakter ile**|Ön plan (karakter)|`Environment.CommandBarMenuMouseDownGlyph`|  
|![Menü başlığı basılı karakteri ile](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303 007_MenuTitleWithGlyphPressed")<br /><br /> **Menü başlığı karakter ile**|Kenarlık|`Environment.CommandBarMenuBorder`<br /><br /> Yalnızca sol, üst ve sağ.|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menü başlığı devre dışı karakter ile](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")<br /><br /> **Menü başlığı karakter ile**|Arka Plan|Yok.|  
|![Menü başlığı devre dışı karakter ile](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")<br /><br /> **Menü başlığı karakter ile**|Ön plan (metin)|`Environment.CommandBarTextInactive`|  
|![Menü başlığı devre dışı karakter ile](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")<br /><br /> **Menü başlığı karakter ile**|Ön plan (karakter)|`Environment.CommandBarTextInactive`|  
|![Menü başlığı devre dışı karakter ile](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")<br /><br /> **Menü başlığı karakter ile**|Kenarlık|Yok.|  
  
##### <a name="menu"></a>Menü  
 Bir tek menü öğesinin menü metnini ve bir isteğe bağlı simge, onay kutusu veya alt simge oluşur. Arka plan ve metin rengi değişiklik üzerine gelindiğinde. Bu renk belirteci, bir arka plan/ön plan çiftidir.  
  
 ![Menü öğelerini kırmızı çizgi](../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303 009_MenuItemRedline")  
  
 Kullan...  
 herhangi bir aşağı açılan listesi için menü çubuğunun ya da komut çubuğu başlatılır.  
  
 Kullanmayın...  
 -   herhangi bir aşağı açılan listeyi, başka bir bağlamda gerçekleşir.  
  
- Belirtilen dışındaki tüm arka plan/ön plan arada.  
  
  **Default**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menü varsayılan](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")<br /><br /> **Menü**|Arka Plan|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Menü varsayılan](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")<br /><br /> **Menü**|Ön plan (metin)|`Environment.CommandBarTextActive`|  
|![Menü varsayılan](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")<br /><br /> **Menü**|Ön plan (alt karakter)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Menü varsayılan](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")<br /><br /> **Menü**|Kenarlık|`Environment.CommandBarMenuBorder`|  
|![Menü varsayılan](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")<br /><br /> **Menü**|Simge kanal arka planı|`Environment.CommandBarMenuIconBackground`|  
|![Menü varsayılan](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")<br /><br /> **Menü**|Ayırıcı|`Environment.CommandBarMenuSeparator`|  
|![Menü varsayılan](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")<br /><br /> **Menü**|Gölge|`Environment.DropShadowBackground`|  
|![İşaretli menü](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303 011_MenuChecked")<br /><br /> **İşaretli**|Onay işareti|`Environment.CommandBarCheckBox`|  
|![İşaretli menü](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303 011_MenuChecked")<br /><br /> **İşaretli**|Onay işareti arka plan|`Environment.CommandBarSelectedIcon`|  
|![Seçili menü](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303 012_MenuSelected")<br /><br /> **Seçili**|Simge arka planı|`Environment.CommandBarSelected`|  
|![Seçili menü](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303 012_MenuSelected")<br /><br /> **Seçili**|Simge kenarlık|`Environment.CommandBarSelectedBorder`|  
  
 **Vurgulu**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menü vurgulu](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 013_MenuHover")<br /><br /> **Menü öğesi**|Arka Plan|`Environment.CommandBarMenuItemMouseOver`|  
|![Menü vurgulu](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 013_MenuHover")<br /><br /> **Menü öğesi**|Ön plan (metin)|`Environment.CommandBarMenuItemMouseOver`|  
|![Menü vurgulu](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 013_MenuHover")<br /><br /> **Menü öğesi**|Ön plan (alt karakter)|`Environment.CommandBarMenuMouseOverSubmenuGlyph`|  
|![İşaretli menü vurgulu](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303 014_MenuHoverChecked")<br /><br /> **İşaretli**|Onay işareti|`Environment.CommandBarCheckBoxMouseOver`|  
|![İşaretli menü vurgulu](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303 014_MenuHoverChecked")<br /><br /> **İşaretli**|Onay işareti arka plan|`Environment.CommandBarHoverOverSelectedIcon`|  
|![Seçili menü vurgulu](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303 015_MenuHoverSelected")<br /><br /> **Seçili**|Simge arka planı|`Environment.CommandBarHoverOverSelected`|  
|![Seçili menü vurgulu](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303 015_MenuHoverSelected")<br /><br /> **Seçili**|Simge kenarlık|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Devre dışı menü](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303 016_MenuDisabled")<br /><br /> Menü öğesi|Ön plan (metin)|`Environment.CommandBarTextInactive`|  
|![Devre dışı menü](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303 016_MenuDisabled")<br /><br /> Menü öğesi|Ön plan (alt karakter)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Menü devre dışı işaretli](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303 017_MenuDisabledChecked")<br /><br /> İşaretli|Onay işareti|`Environment.CommandBarCheckBoxDisabled`|  
|![Menü devre dışı işaretli](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303 017_MenuDisabledChecked")<br /><br /> İşaretli|Onay işareti arka plan|`Environment.CommandBarSelectedIconDisabled`|  
  
#### <a name="command-bar"></a>Komut çubuğu  
 Komut çubuğunda, birden fazla yerde Visual Studio IDE içinde komut raf ve katıştırılmış araç veya belge pencereleri özellikle görünebilir.  
  
 Genel olarak, Visual Studio ortamı tarafından sağlanan standart komut çubuğu uygulaması her zaman kullanın. Standart mekanizmasını kullanarak tüm görsel Ayrıntılar doğru görünür ve etkileşimli öğeleri davrandığını tutarlı bir şekilde ile diğer Visual Studio komut çubuğu denetimleri sağlar. Ancak, kendi komut çubuğu oluşturmak için gerekli değilse, doğru aşağıdaki belirteci adları kullanarak stil emin olun.  
  
 ![Komut çubuğu kırmızı çizgi](../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303 018_CommandBarRedline")  
  
 ![Taşma düğmesi kırmızı çizgi](../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303 019_OverflowButtonRedline")  
  
 Kullan...  
 Katıştırılmış bir komut için gerek duyduğunuz yerde çubuğu ancak standart bir Visual Studio komut çubuğu uygulaması kullanamaz.  
  
 Kullanmayın...  
 -   Kullanıcı Arabirimi öğeleri için Komut çubuğuna benzer değildir.  
  
-   belirteç adları dışında olduğu için istediklerinizi belirtilen komut çubuğu bileşenleri için.  
  
##### <a name="command-bar-group"></a>Komut çubuğu grubu  
 Bir komut çubuğu grubuyla ilgili bir komut çubuğu denetimleri kümesinden oluşur ve herhangi bir sayıda düğmeler, aşağı açılan menüler, birleşik giriş kutuları veya menüler Bölünmüş düğme içerebilir. Bu denetimler için renkleri ayrı belirteci adlarına göre düzenlenen ve ayrı olarak başka bir yerde bu kılavuzda ele alınmıştır. Ayırıcı çizginin bir komut çubuğu grubuyla ilgili alt gruplar ayırmak için kullanılır.  
  
 ![Komut çubuğu grubu kırmızı çizgi](../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303 020_CommandBarGroupRedline")  
  
 Kullan...  
 Katıştırılmış bir komut için gerek duyduğunuz yerde çubuğu ancak standart bir Visual Studio komut çubuğu uygulaması kullanamaz.  
  
 Kullanmayın...  
 -   Kullanıcı Arabirimi öğeleri için Komut çubuğuna benzer değildir.  
  
- belirteç adları dışında olduğu için istediklerinizi belirtilen komut çubuğu bileşenleri için.  
  
  **Varsayılan** (başka hiçbir durum)  
  
|Öğe|Belirteç adı: Category.color|  
|-------------|--------------------------------|  
|Arka Plan|`Environment.CommandBarGradientBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|Kenarlık|`Environment.CommandBarToolBarBorder`|  
|Sürükleme tutamacı|`Environment.CommandBarDragHandle`|  
|Ayırıcı|`Environment.CommandBarToolBarSeparator`<br /><br /> `Environment.CommandBarToolBarSeparatorHighlight`|  
  
##### <a name="command-icons"></a>Komut simgeleri  
 ![Komut simgesi kırmızı çizgi](../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303 021_CommandIconRedline1")  
  
 ![Komut simgesi kırmızı çizgi](../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303 022_CommandIconRedline2")  
  
 Kullan...  
 düğmeleri için komut çubuğunda yer alır.  
  
 Kullanmayın...  
 -   denetimler için belirteç adlarına sahip.  
  
- Belirtilen dışındaki tüm arka plan/ön plan arada.  
  
  **Default**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Komut simgesinin varsayılan](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 023_CommandIconDefault")<br /><br /> **Default**|Arka Plan|Yok (komut çubuğu arka planından devralır)|  
|![Komut simgesinin varsayılan](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 023_CommandIconDefault")<br /><br /> **Default**|Ön plan (metin)|`Environment.CommandBarTextActive`|  
|![Komut simgesinin varsayılan](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 023_CommandIconDefault")<br /><br /> **Default**|Kenarlık|Yok|  
|![Komut simgesinin varsayılan seçili](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")<br /><br /> **Seçili**|Arka Plan|`Environment.CommandBarSelected`|  
|![Komut simgesinin varsayılan seçili](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")<br /><br /> **Seçili**|Ön plan (metin)|`Environment.CommandBarTextSelected`|  
|![Komut simgesinin varsayılan seçili](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")<br /><br /> **Seçili**|Kenarlık|`Environment.CommandBarSelectedBorder`|  
  
 **Hover ve klavye odaklı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Komut simgesinin üzerine gelindiğinde kullanılacak](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 025_CommandIconHover")<br /><br /> **Üzerine gelindiğinde standart**|Arka Plan|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Komut simgesinin üzerine gelindiğinde kullanılacak](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 025_CommandIconHover")<br /><br /> **Üzerine gelindiğinde standart**|Ön plan (metin)|`Environment.CommandBarTextHover`|  
|![Komut simgesinin üzerine gelindiğinde kullanılacak](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 025_CommandIconHover")<br /><br /> **Üzerine gelindiğinde standart**|Kenarlık|`Environment.CommandBarBorder`|  
|![Komut simgesinin üzerine gelindiğinde kullanılacak seçili](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 026_CommandIconHoverSelected")<br /><br /> **Üzerine gelindiğinde seçili**|Arka Plan|`Environment.CommandBarHoverOverSelected`|  
|![Komut simgesinin üzerine gelindiğinde kullanılacak seçili](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 026_CommandIconHoverSelected")<br /><br /> **Üzerine gelindiğinde seçili**|Ön plan (metin)|`Environment.CommandBarTextHoverOverSelected`|  
|![Komut simgesinin üzerine gelindiğinde kullanılacak seçili](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 026_CommandIconHoverSelected")<br /><br /> **Üzerine gelindiğinde seçili**|Kenarlık|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Basılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Komut simgesinin basılı](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 027_CommandIconPressed")<br /><br /> **Basılan komut simgesi**|Arka Plan|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Komut simgesinin basılı](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 027_CommandIconPressed")<br /><br /> **Basılan komut simgesi**|Ön plan (metin)|`Environment.CommandBarTextMouseDown`|  
|![Komut simgesinin basılı](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 027_CommandIconPressed")<br /><br /> **Basılan komut simgesi**|Kenarlık|`Environment.CommandBarBorder`|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Komut simgesinin devre dışı](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 028_CommandIconDisabled")<br /><br /> **Devre dışı bir komut simgesi**|Arka Plan|Yok (komut çubuğu arka planından devralır)|  
|![Komut simgesinin devre dışı](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 028_CommandIconDisabled")<br /><br /> **Devre dışı bir komut simgesi**|Ön plan (metin)|`Environment.CommandBarTextInactive`|  
|![Komut simgesinin devre dışı](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 028_CommandIconDisabled")<br /><br /> **Devre dışı bir komut simgesi**|Kenarlık|Yok|  
  
#####  <a name="BKMK_CommandComboBox"></a> Birleşik giriş kutusu  
  
> [!IMPORTANT]
>  Birleşik giriş kutuları, açılan listeler için benzerdir, ancak düzenlenebilir metin bölge. Düzenlenebilir metin bölge, açılan içermez, altında bulunan renk belirteçleri kullanın. [açılan](../misc/shared-colors.md#BKMK_CommandDropDown).  
  
 ![Birleşik giriş kutusu kırmızı çizgi](../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303 029_ComboBoxRedline")  
  
 Kullan...  
 -   özel bir birleşik giriş kutuları oluştururken.  
  
- bir birleşik giriş kutusuna benzeyen bir komut çubuğu denetimini oluştururken.  
  
  Kullanmayın...  
  -   her şey için her zaman komut eşleştirilecek istemediğiniz çubuğu kullanıcı Arabirimi.  
  
- erişim için bir stil uygulanmış bir birleşik giriş kutusu olduğunda.  
  
  **Default**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Birleşik giriş kutusu giriş alanı](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 030_ComboBoxInputField")<br /><br /> **Giriş alanı**|Arka Plan|`Environment.ComboBoxBackground`|  
|![Birleşik giriş kutusu giriş alanı](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 030_ComboBoxInputField")<br /><br /> **Giriş alanı**|Ön plan (metin)|`Environment.ComboBoxText`|  
|![Birleşik giriş kutusu giriş alanı](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 030_ComboBoxInputField")<br /><br /> **Giriş alanı**|Kenarlık|`Environment.ComboBoxBorder`|  
|![Birleşik giriş kutusu giriş alanı](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 030_ComboBoxInputField")<br /><br /> **Giriş alanı**|Ayırıcı|Hiçbir ayırıcısı|  
|![Açılan birleşik giriş kutusu&#45;Kapat düğmesi](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303 031_ComboBoxDropdownButton")<br /><br /> **Aşağı açılan düğmesi**|Arka Plan|Yok (devralınan)|  
|![Açılan birleşik giriş kutusu&#45;Kapat düğmesi](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303 031_ComboBoxDropdownButton")<br /><br /> **Aşağı açılan düğmesi**|Ön plan (karakter)|`Environment.ComboBoxGlyph`|  
|![Birleşik giriş kutusu&#47;bırak&#45;açılan listesinde](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 032_ComboBoxDropdownList")<br /><br /> **Aşağı açılan listesi**|Arka Plan|`Environment.ComboBoxPopupBackgroundBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Birleşik giriş kutusu&#47;bırak&#45;açılan listesinde](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 032_ComboBoxDropdownList")<br /><br /> **Aşağı açılan listesi**|Ön plan (metin)|`Environment.ComboBoxItemText`|  
|![Birleşik giriş kutusu&#47;bırak&#45;açılan listesinde](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 032_ComboBoxDropdownList")<br /><br /> **Aşağı açılan listesi**|Kenarlık|`Environment.ComboBoxPopupBorder`|  
  
 **Vurgulu**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Birleşik giriş kutusu giriş alanı üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")<br /><br /> **Giriş alanı**|Arka Plan|`Environment.ComboBoxMouseOverBackgroundBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Birleşik giriş kutusu giriş alanı üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")<br /><br /> **Giriş alanı**|Ön plan (metin)|`Environment.ComboBoxMouseOverText`|  
|![Birleşik giriş kutusu giriş alanı üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")<br /><br /> **Giriş alanı**|Kenarlık|`Environment.ComboBoxMouseOverBorder`|  
|![Birleşik giriş kutusu giriş alanı üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")<br /><br /> **Giriş alanı**|Ayırıcı|`Environment.ComboBoxMouseOverSeparator`|  
|![Birleşik giriş kutusu&#47;bırak&#45;Kapat düğmesi üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303 034_ComboBoxDropdownButtonHover")<br /><br /> **Aşağı açılan düğmesi**|Arka Plan|`Environment.ComboBoxButtonMouseOverBackground`|  
|![Birleşik giriş kutusu&#47;bırak&#45;Kapat düğmesi üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303 034_ComboBoxDropdownButtonHover")<br /><br /> **Aşağı açılan düğmesi**|Ön plan (karakter)|`Environment.ComboBoxMouseOverGlyph`|  
|![Birleşik giriş kutusu&#47;bırak&#45;açılan listesinde üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")<br /><br /> **Aşağı açılan listesi**|Arka plan (menü öğesi)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Birleşik giriş kutusu&#47;bırak&#45;açılan listesinde üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")<br /><br /> **Aşağı açılan listesi**|Ön plan (metin)|`Environment.ComboBoxItemMouseOverText`|  
|![Birleşik giriş kutusu&#47;bırak&#45;açılan listesinde üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")<br /><br /> **Aşağı açılan listesi**|Kenarlık (menü öğesi)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Odaklanmış**  
  
|Bileşen|Öğe|Belirteç adı: Color.category|  
|---------------|-------------|--------------------------------|  
|![Birleşik giriş kutusu giriş alanı odaklanmış](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")<br /><br /> **Giriş alanı**|Arka Plan|`Environment.ComboBoxFocusedBackground`|  
|![Birleşik giriş kutusu giriş alanı odaklanmış](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")<br /><br /> **Giriş alanı**|Ön plan (metin)|`Environment.ComboBoxFocusedText`|  
|![Birleşik giriş kutusu giriş alanı odaklanmış](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")<br /><br /> **Giriş alanı**|Kenarlık|`Environment.ComboBoxFocusedBorder`|  
|![Birleşik giriş kutusu giriş alanı odaklanmış](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")<br /><br /> **Giriş alanı**|Ayırıcı|`Environment.ComboBoxFocusedButtonSeparator`|  
|![Birleşik giriş kutusu&#47;bırak&#45;odaklanmış düğmesini basılı](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303 037_ComboBoxDropdownButtonFocused")<br /><br /> **Aşağı açılan düğmesi**|Arka Plan|`Environment.ComboBoxFocusedButtonBackground`|  
|![Birleşik giriş kutusu&#47;bırak&#45;odaklanmış düğmesini basılı](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303 037_ComboBoxDropdownButtonFocused")<br /><br /> **Aşağı açılan düğmesi**|Ön plan (karakter)|`Environment.ComboBoxFocusedGlyph`|  
  
 **Basılan**  
  
|Bileşen|Öğe|Belirteç adı: Color.category|  
|---------------|-------------|--------------------------------|  
|![Birleşik giriş kutusu giriş alanı basılı](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")<br /><br /> **Giriş alanı**|Arka Plan|`Environment.ComboBoxMouseDownBackground`|  
|![Birleşik giriş kutusu giriş alanı basılı](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")<br /><br /> **Giriş alanı**|Ön plan (metin)|`Environment.ComboBoxMouseDownText`|  
|![Birleşik giriş kutusu giriş alanı basılı](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")<br /><br /> **Giriş alanı**|Kenarlık|`Environment.ComboBoxMouseDownBorder`|  
|![Birleşik giriş kutusu giriş alanı basılı](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")<br /><br /> **Giriş alanı**|Ayırıcı|`Environment.ComboBoxMouseDownSeparator`|  
|![Birleşik giriş kutusu&#47;bırak&#45;düğmeye basıldığını aşağı](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303 039_ComboBoxDropdownButtonPressed")<br /><br /> **Aşağı açılan düğmesi**|Arka Plan|`Environment.ComboBoxButtonMouseDownBackground`|  
|![Birleşik giriş kutusu&#47;bırak&#45;düğmeye basıldığını aşağı](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303 039_ComboBoxDropdownButtonPressed")<br /><br /> **Aşağı açılan düğmesi**|Ön plan (karakter)|`Environment.ComboBoxMouseDownGlyph`|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Color.category|  
|---------------|-------------|--------------------------------|  
|![Birleşik giriş kutusu giriş alanını devre dışı](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")<br /><br /> **Giriş alanı**|Arka Plan|`Environment.ComboBoxDisabledBackground`|  
|![Birleşik giriş kutusu giriş alanını devre dışı](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")<br /><br /> **Giriş alanı**|Ön plan (metin)|`Environment.ComboBoxDisabledText`|  
|![Birleşik giriş kutusu giriş alanını devre dışı](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")<br /><br /> **Giriş alanı**|Kenarlık|`Environment.ComboBoxDisabledBorder`|  
|![Birleşik giriş kutusu giriş alanını devre dışı](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")<br /><br /> **Giriş alanı**|Ayırıcı|Hiçbir ayırıcısı|  
|![Birleşik giriş kutusu&#47;bırak&#45;Kapat düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303 040_ComboBoxDropdownButtonDisabled")<br /><br /> **Aşağı açılan düğmesi**|Arka Plan|Yok.|  
|![Birleşik giriş kutusu&#47;bırak&#45;Kapat düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303 040_ComboBoxDropdownButtonDisabled")<br /><br /> **Aşağı açılan düğmesi**|Ön plan (karakter)|`Environment.ComboBoxDisabledGlyph`|  
  
#####  <a name="BKMK_CommandDropDown"></a> Açılan  
  
> [!IMPORTANT]
>  Açılan listeler, birleşik giriş kutuları için benzerdir, ancak düzenlenebilir metin bölgeleri yoksundur. Düzenlenebilir metin bölge, açılan içerir, altında bulunan renk belirteçleri kullanın. [birleşik giriş kutusu](../misc/shared-colors.md#BKMK_CommandComboBox).  
  
 ![DROP&#45;aşağı kırmızı çizgi](../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303 042_DropdownRedline")  
  
 Kullan...  
 ne zaman özel aşağı açılan liste denetimleri oluşturuyorsunuz.  
  
 Kullanmayın...  
 -   her şey için aşağı açılan listesine benzer değil.  
  
- Birleşik giriş kutuları veya Bölünmüş düğme.  
  
  **Default**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![DROP&#45;seçim alanı aşağı](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 043_DropdownSelectionField")<br /><br /> **Seçim alanı**|Arka Plan|`Environment.DropDownBackground`|  
|![DROP&#45;seçim alanı aşağı](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 043_DropdownSelectionField")<br /><br /> **Seçim alanı**|Ön plan (metin)|`DropDownText`|  
|![DROP&#45;seçim alanı aşağı](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 043_DropdownSelectionField")<br /><br /> **Seçim alanı**|Kenarlık|`DropDownBorder`|  
|![DROP&#45;seçim alanı aşağı](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 043_DropdownSelectionField")<br /><br /> **Seçim alanı**|Ayırıcı|Hiçbir ayırıcısı|  
|![DROP&#45;Kapat düğmesi](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303 044_DropdownButton")<br /><br /> **Aşağı açılan düğmesi**|Arka Plan|Yok.|  
|![DROP&#45;Kapat düğmesi](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303 044_DropdownButton")<br /><br /> **Aşağı açılan düğmesi**|Ön plan (karakter)|`Environment.DropDownGlyph`|  
|![DROP&#45;açılan listesinde](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 045_DropdownList")<br /><br /> **Aşağı açılan listesi**|Arka Plan|`Environment.DropDownPopupBackgroundBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![DROP&#45;açılan listesinde](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 045_DropdownList")<br /><br /> **Aşağı açılan listesi**|Ön plan (metin)|`Environment.ComboBoxItemText`|  
|![DROP&#45;açılan listesinde](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 045_DropdownList")<br /><br /> **Aşağı açılan listesi**|Kenarlık|`Environment.DropDownPopupBorder`|  
|![DROP&#45;açılan listesinde](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 045_DropdownList")<br /><br /> **Aşağı açılan listesi**|Gölge|`Environment.DropShadowBackground`|  
  
 **Vurgulu**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![DROP&#45;seçim alanı üzerine gelindiğinde aşağı](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")<br /><br /> **Seçim alanı**|Arka Plan|`Environment.DropDownMouseOverBackgroundBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![DROP&#45;seçim alanı üzerine gelindiğinde aşağı](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")<br /><br /> **Seçim alanı**|Ön plan (metin)|`Environment.DropDownMouseOverText`|  
|![DROP&#45;seçim alanı üzerine gelindiğinde aşağı](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")<br /><br /> **Seçim alanı**|Kenarlık|`Environment.DropDownMouseOverBorder`|  
|![DROP&#45;seçim alanı üzerine gelindiğinde aşağı](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")<br /><br /> **Seçim alanı**|Ayırıcı|`Environment.DropDownButtonMouseOverSeparator`|  
|![DROP&#45;Kapat düğmesi üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303 047_DropdownButtonHover")<br /><br /> **Aşağı açılan düğmesi**|Arka Plan|`Environment.DropDownButtonMouseOverBackground`|  
|![DROP&#45;Kapat düğmesi üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303 047_DropdownButtonHover")<br /><br /> **Aşağı açılan düğmesi**|Ön plan (karakter)|`Environment.DropDownMouseOverGlyph`|  
|![DROP&#45;açılan listesinde üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 048_DropdownListHover")<br /><br /> **Aşağı açılan listesi**|Arka plan (menü öğesi)|`Environment.ComboBoxItemMouseOverBackground`|  
|![DROP&#45;açılan listesinde üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 048_DropdownListHover")<br /><br /> **Aşağı açılan listesi**|Ön plan (metin)|`Environment.ComboBoxItemMouseOverText`|  
|![DROP&#45;açılan listesinde üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 048_DropdownListHover")<br /><br /> **Aşağı açılan listesi**|Kenarlık (menü öğesi)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Basılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![DROP&#45;tuşunu basılı seçim alanı](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")<br /><br /> **Seçim alanı**|Arka Plan|`Environment.DropDownMouseDownBackground`|  
|![DROP&#45;tuşunu basılı seçim alanı](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")<br /><br /> **Seçim alanı**|Ön plan (metin)|`Environment.DropDownMouseDownText`|  
|![DROP&#45;tuşunu basılı seçim alanı](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")<br /><br /> **Seçim alanı**|Kenarlık|`Environment.DropDownMouseDownBorder`|  
|![DROP&#45;tuşunu basılı seçim alanı](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")<br /><br /> **Seçim alanı**|Ayırıcı|`Environment.DropDownButtonMouseDownSeparator`|  
|![DROP&#45;düğmeye basıldığını aşağı](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303 050_DropdownButtonPressed")<br /><br /> **Aşağı açılan düğmesi**|Arka Plan|`Environment.DropDownButtonMouseDownBackground`|  
|![DROP&#45;düğmeye basıldığını aşağı](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303 050_DropdownButtonPressed")<br /><br /> **Aşağı açılan düğmesi**|Ön plan (karakter)|`Environment.DropDownMouseDownGlyph`|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![DROP&#45;devre dışı seçim alanı aşağı](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")|Arka Plan|`Environment.DropDownDisabledBackground`|  
|![DROP&#45;devre dışı seçim alanı aşağı](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")|Ön plan (metin)|`Environment.DropDownDisabledText`|  
|![DROP&#45;devre dışı seçim alanı aşağı](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")|Kenarlık|`Environment.DropDownDisabledBorder`|  
|![DROP&#45;devre dışı seçim alanı aşağı](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")|Ayırıcı|Hiçbir ayırıcısı|  
|![DROP&#45;Kapat düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303 052_DropdownButtonDisabled")|Arka Plan|Yok|  
|![DROP&#45;Kapat düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303 052_DropdownButtonDisabled")|Ön plan (karakter)|`Environment.DropDownDisabledGlyph`|  
  
##### <a name="split-button"></a>Bölünmüş düğme  
 Bölünmüş düğme fazla belirteç ad düğmeler, menüler ve komut çubuğu metni gibi diğer komut çubuğu denetimleri ile paylaşın. Tüm gerekli eylem ve açılan düğmeyi belirteci adları kolaylık olması için burada yinelenir. Bölünmüş düğme açılan listeleri, uygulamaları komut çubuğunun [menüleri](../misc/shared-colors.md#BKMK_CommandMenus).  
  
 ![Bölünmüş düğme kırmızı çizgi](../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303 053_SplitButtonRedline")  
  
 Kullan...  
 ne zaman özel bir Bölünmüş düğme oluşturuyorsunuz.  
  
 Kullanmayın...  
 -   diğer düğme türleri için.  
  
- Belirtilen dışındaki tüm arka plan/ön plan arada.  
  
  **Default**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Bölünmüş düğme](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 054_SplitButton")<br /><br /> **Bölünmüş düğme (varsayılan)**|Arka Plan|Yok.|  
|![Bölünmüş düğme](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 054_SplitButton")<br /><br /> **Bölünmüş düğme (varsayılan)**|Ön plan (metin)|`Environment.CommandBarTextActive`|  
|![Bölünmüş düğme](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 054_SplitButton")<br /><br /> **Bölünmüş düğme (varsayılan)**|Ön plan (karakter)|`Environment.CommandBarSplitButtonGlyph`|  
|![Bölünmüş düğme](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 054_SplitButton")<br /><br /> **Bölünmüş düğme (varsayılan)**|Kenarlık|Yok|  
|![Bölünmüş düğme](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 054_SplitButton")<br /><br /> **Bölünmüş düğme (varsayılan)**|Ayırıcı|Yok|  
  
 **Vurgulu**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Bölünmüş düğme üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 055_SplitButtonHover")<br /><br /> **Bölünmüş düğme (üzerine gelindiğinde)**|Arka Plan|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Bölünmüş düğme üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 055_SplitButtonHover")<br /><br /> **Bölünmüş düğme (üzerine gelindiğinde)**|Ön plan (metin)|`Environment.CommandBarTextHover`|  
|![Bölünmüş düğme üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 055_SplitButtonHover")<br /><br /> **Bölünmüş düğme (üzerine gelindiğinde)**|Ön plan (karakter)|`Environment.CommandBarSplitButtonMouseOverGlyph`|  
|![Bölünmüş düğme üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 055_SplitButtonHover")<br /><br /> **Bölünmüş düğme (üzerine gelindiğinde)**|Kenarlık|`Environment.CommandBarBorder`|  
|![Bölünmüş düğme üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 055_SplitButtonHover")<br /><br /> **Bölünmüş düğme (üzerine gelindiğinde)**|Ayırıcı|`Environment.CommandBarSplitButtonSeparator`|  
  
 **Basılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Bölünmüş düğmeye basıldığını](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 056_SplitButtonPressed")<br /><br /> **Bölünmüş düğme (basılı)**|Arka Plan|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Bölünmüş düğmeye basıldığını](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 056_SplitButtonPressed")<br /><br /> **Bölünmüş düğme (basılı)**|Ön plan (metin)|`Environment.CommandBarTextMouseDown`|  
|![Bölünmüş düğmeye basıldığını](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 056_SplitButtonPressed")<br /><br /> **Bölünmüş düğme (basılı)**|Ön plan (karakter)|`Environment.CommandBarSplitButtonMouseDownGlyph`|  
|![Bölünmüş düğmeye basıldığını](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 056_SplitButtonPressed")<br /><br /> **Bölünmüş düğme (basılı)**|Kenarlık|`Environment.CommandBarBorder`|  
|![Bölünmüş düğmeye basıldığını](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 056_SplitButtonPressed")<br /><br /> **Bölünmüş düğme (basılı)**|Ayırıcı|Yok|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Bölünmüş düğme devre dışı](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 057_SplitButtonDisabled")<br /><br /> **Bölünmüş düğme (devre dışı)**|Arka Plan|Yok|  
|![Bölünmüş düğme devre dışı](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 057_SplitButtonDisabled")<br /><br /> **Bölünmüş düğme (devre dışı)**|Ön plan (metin)|`Environment.ComboBoxItemTextInactive`|  
|![Bölünmüş düğme devre dışı](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 057_SplitButtonDisabled")<br /><br /> **Bölünmüş düğme (devre dışı)**|Ön plan (karakter)|`Environment.CommandBarTextInactive`|  
|![Bölünmüş düğme devre dışı](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 057_SplitButtonDisabled")<br /><br /> **Bölünmüş düğme (devre dışı)**|Kenarlık|Yok|  
|![Bölünmüş düğme devre dışı](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 057_SplitButtonDisabled")<br /><br /> **Bölünmüş düğme (devre dışı)**|Ayırıcı|Yok|  
  
##### <a name="more-options-and-overflow-buttons"></a>'Daha Seçenekleri' ve 'Overflow' düğmeleri  
 "Diğer seçenekler" düğmesi, bir komut çubuğu grubu özelleştirilebilir ekleme veya kaldırma ilgili komut çubuğu düğmelerinin olduğunda kullanılır. Bir komut çubuğu için yatay boşluk eksikliği nedeniyle kesilmiş ve görüntülenemiyor komut çubuğu düğmelerini içeren bir menü çubuğunda gösterir "Taşma" düğmesi görünür. Bu iki düğme için renkleri belirteci adları aynı kümesi tarafından denetlenir.  
  
 ![Daha fazla seçenek kırmızı çizgi](../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303 058_MoreOptionsRedline")  
  
 Kullan...  
 Özel 'daha fazla seçenek' veya 'Overflow' düğmeler için.  
  
 Kullanmayın...  
 'Daha Seçenekleri' veya 'Overflow' düğmesini benzer bir işlevsellik yoksa düğmeler.  
  
 **Default**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Daha fazla seçenek](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303 059_MoreOptions")<br /><br /> **Daha fazla seçenek**|Arka Plan|`Environment.CommandBarOptionsBackground`|  
|![Daha fazla seçenek](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303 059_MoreOptions")<br /><br /> **Daha fazla seçenek**|Ön plan (karakter)|`Environment.CommandBarOptionsGlyph`|  
|![Taşma düğmesi](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303 060_Overflow")<br /><br /> **taşma**|Arka Plan|`Environment.CommandBarOptionsBackground`|  
|![Taşma düğmesi](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303 060_Overflow")<br /><br /> **taşma**|Ön plan (karakter)|`Environment.CommandBarOptionsGlyph`|  
  
 **Vurgulu**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Daha fazla seçenek üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303 061_MoreOptionsHover")<br /><br /> **Daha fazla seçenek**|Arka Plan|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Daha fazla seçenek üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303 061_MoreOptionsHover")<br /><br /> **Daha fazla seçenek**|Ön plan (karakter)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Overflow üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303 062_OverflowOptions")<br /><br /> **taşma**|Arka Plan|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Overflow üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303 062_OverflowOptions")<br /><br /> **taşma**|Ön plan (karakter)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
 **Basılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Daha fazla seçenek basılı](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303 063_MoreOptionsPressed")<br /><br /> **Daha fazla seçenek**|Arka Plan|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Daha fazla seçenek basılı](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303 063_MoreOptionsPressed")<br /><br /> **Daha fazla seçenek**|Ön plan (karakter)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Basılan taşma](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303 064_OverflowPressed")<br /><br /> **taşma**|Arka Plan|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Basılan taşma](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303 064_OverflowPressed")<br /><br /> **taşma**|Ön plan (karakter)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
### <a name="document-windows"></a>Belge pencereleri  
 Visual Studio ortamı tarafından sağlandığından belge pencereleri çoğaltmak için gerek yoktur. Ancak, kullanıcı Arabirimi her zaman Visual Studio ortamının bu bölümü ile tutarlı görünmesi belge pencerelerinin kullanılan renkleri yararlanmak istediğinize karar verin.  
  
 Belge penceresi renk belirteçleri kullanırken, yalnızca benzer öğeleri için ve her zaman çiftler halinde kullanmak dikkatli olmanız gerekir. Bunu yaparsanız, olması, kullanıcı arabiriminde beklenmeyen sonuçlar.  
  
#### <a name="document-window-frame"></a>Belge pencere çerçevesi  
 Belge pencereleri IDE içindeki yerleşik veya ayrı bir pencerede olarak kayan olabilir. Belge penceresini IDE dışında kayan noktalı, yine de bir belge kutusu içinde bulunur ve arka plan, kenarlık, metin ve IDE parçası olduğunda, aynı olan sekme renkleri vardır. Ancak, belgeyi kendi arka plan, kenarlık ve metin renklerini olan bir çerçeve içinde bulunur. Araç pencereleri belge iyi yerleştirildiğinde, bunların davranışı ve kendi sekme rengini belge penceresi belirteci adlarından devralır.  
  
 ![Yerleşik belge penceresi kırmızı çizgi](../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303 065_DockedDocumentWindowRedline")  
  
 **Yerleşik belge penceresi**  
  
 ![Belge penceresi kayan kırmızı çizgi](../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303 066_FloatingDocumentWindowRedline")  
  
 **Kayan belge penceresi**  
  
 Kullan...  
 herhangi bir belge penceresi eşleştirmek istediğiniz kullanıcı Arabirimi oluşturuyorsunuz.  
  
 Kullanmayın...  
 otomatik olarak değiştirmeyi istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir.  
  
 **Default**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|Belge: yerleşik veya kayan|Arka Plan|Belge türüne göre değişir|  
|Belge: yerleşik veya kayan|Ön plan (metin)|Belge türüne göre değişir|  
|Belge: yerleşik veya kayan|Kenarlık|`Environment.ToolWindowBorder`|  
|![Odaklanmış çerçeve](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 067_FrameFocused")<br /><br /> **Çerçeve: kayan, odaklanmış**|Arka Plan|`Environment.ToolWindowFloatingFrame`|  
|![Odaklanmış çerçeve](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 067_FrameFocused")<br /><br /> **Çerçeve: kayan, odaklanmış**|Ön plan (metin)|`Environment.ToolWindowFloatingFrame`|  
|![Odaklanmış çerçeve](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 067_FrameFocused")<br /><br /> **Çerçeve: kayan, odaklanmış**|Ön plan (karakter)|`Environment.RaftedWindowButtonActiveGlyph`|  
|![Odaklanmış çerçeve](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 067_FrameFocused")<br /><br /> **Çerçeve: kayan, odaklanmış**|Kenarlık|`Environment.MainWindowActiveDefaultBorder`|  
|![Odaklanmış çerçeve](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 067_FrameFocused")<br /><br /> **Çerçeve: kayan, odaklanmış**|Kenarlık (karakter)|`Environment.RaftedWindowButtonActiveBorder`<br /><br /> Saydam ayarlayın|  
|![Çerçeve odaklanmadan](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 068_FrameUnfocused")<br /><br /> **Çerçeve: kayan bu plana odaklanmadan**|Arka Plan|`Environment.ToolWindowFloatingFrameInactive`|  
|![Çerçeve odaklanmadan](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 068_FrameUnfocused")<br /><br /> **Çerçeve: kayan bu plana odaklanmadan**|Ön plan (metin)|`Environment.ToolWindowFloatingFrameInactive`|  
|![Çerçeve odaklanmadan](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 068_FrameUnfocused")<br /><br /> **Çerçeve: kayan bu plana odaklanmadan**|Ön plan (karakter)|`Environment.RaftedWindowButtonInactiveGlyph`|  
|![Çerçeve odaklanmadan](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 068_FrameUnfocused")<br /><br /> **Çerçeve: kayan bu plana odaklanmadan**|Kenarlık|`Environment.MainWindowInactiveBorder`|  
|![Çerçeve odaklanmadan](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 068_FrameUnfocused")<br /><br /> **Çerçeve: kayan bu plana odaklanmadan**|Kenarlık (karakter)|`Environment.RaftedWindowButtonInactiveBorder`<br /><br /> Saydam ayarlayın|  
  
 **Vurgulu**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Çerçeve üzerine gelindiğinde odaklanmış](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 069_FrameFocusedHover")<br /><br /> **Çerçeve: kayan, odaklanmış**|Arka plan (karakter)|`Environment.RaftedWindowButtonHoverActive`|  
|![Çerçeve üzerine gelindiğinde odaklanmış](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 069_FrameFocusedHover")<br /><br /> **Çerçeve: kayan, odaklanmış**|Ön plan (karakter)|`Environment.RaftedWindowButtonHoverActiveGlyph`|  
|![Çerçeve üzerine gelindiğinde odaklanmış](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 069_FrameFocusedHover")<br /><br /> **Çerçeve: kayan, odaklanmış**|Kenarlık (karakter)|`Environment.RaftedWindowButtonHoverActiveBorder`|  
|![Çerçeve üzerine gelindiğinde odaklanmadan](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 070_FrameUnfocusedHover")<br /><br /> **Çerçeve: kayan bu plana odaklanmadan**|Arka plan (karakter)|`EnvironmentRaftedWindowButtonHoverInactive`|  
|![Çerçeve üzerine gelindiğinde odaklanmadan](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 070_FrameUnfocusedHover")<br /><br /> **Çerçeve: kayan bu plana odaklanmadan**|Ön plan (karakter)|`Environment.RaftedWindowButtonHoverInactiveGlyph`|  
|![Çerçeve üzerine gelindiğinde odaklanmadan](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 070_FrameUnfocusedHover")<br /><br /> **Çerçeve: kayan bu plana odaklanmadan**|Kenarlık (karakter)|`Environment.RaftedWindowButtonHoverInactiveBorder`|  
  
 **Basılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Çerçeve odaklanmış basılı](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 071_FrameFocusedPressed")<br /><br /> **Çerçeve: kayan, odaklanmış**|Arka plan (karakter)|`Environment.RaftedWindowButtonDown`|  
|![Çerçeve odaklanmış basılı](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 071_FrameFocusedPressed")<br /><br /> **Çerçeve: kayan, odaklanmış**|Ön plan (karakter)|`Environment.RaftedWindowButtonDownGlyph`|  
|![Çerçeve odaklanmış basılı](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 071_FrameFocusedPressed")<br /><br /> **Çerçeve: kayan, odaklanmış**|Kenarlık (karakter)|`Environment.RaftedWindowButtonDownBorder`|  
  
#### <a name="document-tabs"></a>Belge sekmeleri  
 Belge sekmeleri hangi belgelerin yanı sıra etkin belgeyi hangisinin seçili geçerli olduğu veya şu anda açık olan belirtmek için sekmesinde kanaldaki durur. Kullanıcı var. bunları yerleştirir, araç pencerelerini de belge sekme kanalda sabitlenebilir. Bu durumda, bunlar aynı sekme renkleri ve belge pencereleri kullanır. Kullanıcı Arabirimi, oluşturuyorsanız, her zaman (Tema güncelleştirmeleri veya yeni temalar yüklediyseniz dahil) belge penceresini renkleriyle eşleşecek ve ardından bu renk belirteçleri başvuru istiyorsunuz.  
  
 ![Belge sekmesini kırmızı çizgi](../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303 072_DocumentTabRedline")  
  
 Kullan...  
 herhangi bir belge sekmeleri eşleşen ve tema güncelleştirmeleri veya yeni Tema renkleri otomatik olarak seçmek istediğiniz kullanıcı Arabirimi oluşturuyorsunuz.  
  
 Kullanmayın...  
 Kabuk güncelleştirme bir tema olduğunda otomatik olarak değiştirmek istemediğiniz herhangi bir UI için.  
  
##### <a name="open-document-tabs"></a>Açık belge sekmeleri  
 Her açık belge adını görüntüleyen belge sekme kanalda bir sekmesi vardır. Belge ya da seçilebilir veya arka planda açın ve bu durumları sekmeleri yansıtacak:  
  
- Seçili belgeyi de şu anda görüntülenen belgenin temsil eder. Seçili bir sekme iyi belgenin üst kenarı genişlettiği belge kenarlık vardır.  
  
- Arka plan sekmeleri şu anda seçilen sekmesi olmayan herhangi bir belge sekme var. Tıklattıktan sonra seçili duruma ve tüm arka plan, kenarlık ve metin renklerini Bu belirteci adlarından Al.  
  
  ![Açık belge sekme kırmızı çizgi](../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303 073_OpenDocumentTabRedline")  
  
  Kullan...  
  ne zaman özel belge sekmeleri oluşturuyorsunuz.  
  
  Kullanmayın...  
  -   (Önizleme) provisional sekmeler için.  
  
- otomatik olarak değiştirmeyi istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir.  
  
##### <a name="selected-tab"></a>Seçilen sekmesi  
 **Odaklanmış**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Seçili sekme odaklanmış](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 074_SelectedTabFocused")<br /><br /> **Odaklanmış, seçilen belge sekmesi**|Arka Plan|`Environment.FileTabSelectedGradientTop`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Seçili sekme odaklanmış](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 074_SelectedTabFocused")<br /><br /> **Odaklanmış, seçilen belge sekmesi**|Ön plan (metin)|`Environment.FileTabSelectedText`|  
|![Seçili sekme odaklanmış](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 074_SelectedTabFocused")<br /><br /> **Odaklanmış, seçilen belge sekmesi**|Kenarlık|`Environment.FileTabSelectedBorder`<br /><br /> Aynı arka plan rengini ayarlayın.|  
|![Seçili sekme odaklanmış](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 074_SelectedTabFocused")<br /><br /> **Odaklanmış, seçilen belge sekmesi**|Belge kenarlık|`Environment.FileTabDocumentBorderBackground`|  
  
 **Plana odaklanmadan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Seçili sekme odaklanmadan](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 075_SelectedTabUnfocused")<br /><br /> **Seçilen belge sekmesini, plana odaklanmadan**|Arka Plan|`Environment.FileTabInactiveGradientTop`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Seçili sekme odaklanmadan](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 075_SelectedTabUnfocused")<br /><br /> **Seçilen belge sekmesini, plana odaklanmadan**|Ön plan (metin)|`Environment.FileTabInactiveText`|  
|![Seçili sekme odaklanmadan](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 075_SelectedTabUnfocused")<br /><br /> **Seçilen belge sekmesini, plana odaklanmadan**|Kenarlık|`Environment.FileTabInactiveBorder`<br /><br /> Aynı arka plan rengini ayarlayın.|  
|![Seçili sekme odaklanmadan](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 075_SelectedTabUnfocused")<br /><br /> **Seçilen belge sekmesini, plana odaklanmadan**|Belge kenarlık|`Environment.FileTabInactiveDocumentBorderBackground`|  
  
##### <a name="background-tab"></a>Arka plan sekmesi  
 **Default**  
  
|Bileşen|Öğe|Belirteç adı: Color.category|  
|---------------|-------------|--------------------------------|  
|![Arka plan sekmesine](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 076_BackgroundTab")<br /><br /> **Arka plan sekmesine varsayılan**|Arka Plan|`Environment.FileTabBackground`|  
|![Arka plan sekmesine](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 076_BackgroundTab")<br /><br /> **Arka plan sekmesine varsayılan**|Ön plan (metin)|`Environment.FileTabText`|  
|![Arka plan sekmesine](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 076_BackgroundTab")<br /><br /> **Arka plan sekmesine varsayılan**|Kenarlık|`Environment.FileTabBorder`<br /><br /> Aynı arka plan rengini ayarlayın.|  
  
 **Vurgulu**  
  
|Bileşen|Öğe|Belirteç adı: Color.category|  
|---------------|-------------|--------------------------------|  
|![Üzerine gelindiğinde kullanılacak arka plan sekmesinde](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 077_BackgroundTabHover")<br /><br /> **Üzerine gelindiğinde kullanılacak arka plan sekmesinde**|Arka Plan|`Environment.FileTabHotGradientTop`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Üzerine gelindiğinde kullanılacak arka plan sekmesinde](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 077_BackgroundTabHover")<br /><br /> **Üzerine gelindiğinde kullanılacak arka plan sekmesinde**|Ön plan (metin)|`Environment.FileTabHotText`|  
|![Üzerine gelindiğinde kullanılacak arka plan sekmesinde](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 077_BackgroundTabHover")<br /><br /> **Üzerine gelindiğinde kullanılacak arka plan sekmesinde**|Kenarlık|`Environment.FileTabHotBorder`<br /><br /> Aynı arka plan rengini ayarlayın.|  
  
##### <a name="preview-tab"></a>Önizleme sekmesi  
 Önizleme sekmesini, kullanıcı Çözüm Gezgini araç penceresindeki bir öğeyi tıklattığında belge sekme kanal sağ tarafında görünür. Bu belgenin önizleme olarak davranır ve kullanıcı belgeyi belge sekme kanal sol tarafında açık tutmak için seçeneği de sunar. Bir kerede yalnızca bir Önizleme sekmesini Aç açık olabilir. Önizleme sekmeleri sahip hem de arka plan ve seçili durumlardan sekmeleri Aç gibi ve kullanıcıların etkin durumda odaklanmış veya plana odaklanmadan olabilir.  
  
 ![Önizleme sekmesini kırmızı çizgi](../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303 078_PreviewTabRedline")  
  
 Kullan...  
 herhangi bir provisional Önizleme oluşturma ve bazı öğesi geçerli Önizleme sekme rengini eşleştirilecek istiyor.  
  
 Kullanmayın...  
 -   Belge ya da geçici olmayan sekmesinde herhangi bir türdeki (Önizleme).  
  
- otomatik olarak değiştirmeyi istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir.  
  
  **Seçili Önizleme sekmesi: odaklanmış**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Önizleme sekmesini odaklanmış](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 079_PreviewTabFocused")<br /><br /> **Odaklanmış Önizleme sekmesi**|Arka Plan|`Environment.FileTabProvisionalSelectedActive`|  
|![Önizleme sekmesini odaklanmış](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 079_PreviewTabFocused")<br /><br /> **Odaklanmış Önizleme sekmesi**|Ön plan (metin)|`Environment.FileTabProvisionalSelectedActiveForeground`|  
|![Önizleme sekmesini odaklanmış](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 079_PreviewTabFocused")<br /><br /> **Odaklanmış Önizleme sekmesi**|Kenarlık|`Environment.FileTabProvisionalSelectedActiveBorder`<br /><br /> Aynı arka plan rengini ayarlayın.|  
|![Önizleme sekmesini odaklanmış](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 079_PreviewTabFocused")<br /><br /> **Odaklanmış Önizleme sekmesi**|Belge kenarlık|`Environment.FileTabProvisionalSelectedActiveBorder`|  
  
 **Seçili Önizleme sekmesi: Odaklanmadan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Önizleme sekmesini odaklanmadan](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 080_PreviewTabUnfocused")<br /><br /> **Plana odaklanmadan Önizleme sekmesi**|Arka Plan|`Environment.FileTabProvisionalSelectedInactive`|  
|![Önizleme sekmesini odaklanmadan](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 080_PreviewTabUnfocused")<br /><br /> **Plana odaklanmadan Önizleme sekmesi**|Ön plan (metin)|`Environment.FileTabProvisionalSelectedInactiveForeground`|  
|![Önizleme sekmesini odaklanmadan](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 080_PreviewTabUnfocused")<br /><br /> **Plana odaklanmadan Önizleme sekmesi**|Kenarlık|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
|![Önizleme sekmesini odaklanmadan](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 080_PreviewTabUnfocused")<br /><br /> **Plana odaklanmadan Önizleme sekmesi**|Belge kenarlık|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
  
 **Arka plan Önizleme sekmesi: varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Önizleme arka plan sekmesine](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 081_PreviewBackgroundTab")<br /><br /> **Önizleme sekmesini arka plan sekmesi**|Arka Plan|`Environment.FileTabProvisionalInactive`|  
|![Önizleme arka plan sekmesine](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 081_PreviewBackgroundTab")<br /><br /> **Önizleme sekmesini arka plan sekmesi**|Ön plan (metin)|`Environment.FileTabProvisionalInactiveForeground`|  
|![Önizleme arka plan sekmesine](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 081_PreviewBackgroundTab")<br /><br /> **Önizleme sekmesini arka plan sekmesi**|Kenarlık|`Environment.FileTabProvisionalInactiveBorder`<br /><br /> Aynı arka plan rengini ayarlayın.|  
  
 **Arka plan Önizleme sekmesi: getirin**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Önizleme arka plan sekmesine üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")<br /><br /> **Önizleme sekmesini arka plan sekmesine üzerine gelindiğinde**|Arka Plan|`Environment.FileTabProvisionalHover`|  
|![Önizleme arka plan sekmesine üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")<br /><br /> **Önizleme sekmesini arka plan sekmesine üzerine gelindiğinde**|Ön plan (metin)|`Environment.FileTabProvisionalHoverForeground`|  
|![Önizleme arka plan sekmesine üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")<br /><br /> **Önizleme sekmesini arka plan sekmesine üzerine gelindiğinde**|Kenarlık|`Environment.FileTabProvisionalHoverBorder`<br /><br /> Aynı arka plan rengini ayarlayın.|  
  
##### <a name="document-overflow-button"></a>Belge Taşma düğmesi  
 Belge Taşma düğmesi, bir veya daha fazla belge olup olmamasına bakılmaksızın açık, mevcut ise tüm belge sekmeleri uyacak şekilde, geçerli yapılandırma dikey boşluk yoktur. Denetlenen belge taşma açılan menüsünü **CommandBarMenu** renkleri (bkz [menüleri](../misc/shared-colors.md#BKMK_CommandMenus)), bütün açık belgeleri, görünür ve gizli ve taşma glif değişikliklerin bir listesini görüntüler bağlı olarak tüm açık belgeleri sekmesini kanalda olup görüntülenir.  
  
 ![Taşma kırmızı çizgi](../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303 083_OverflowRedline")  
  
 Kullan...  
 ne zaman bir özel belge taşma düğmesini oluşturuyorsunuz.  
  
 Kullanmayın...  
 -   taşma düğmesini için benzer değil kullanıcı Arabirimi için.  
  
- Komut çubuğu taşma düğmeleri.  
  
  **Default**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Overflow](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 084_Overflow")<br /><br /> **Belge Taşma düğmesi**|Arka Plan|`Environment.DocWellOverflowButtonBackground`|  
|![Overflow](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 084_Overflow")<br /><br /> **Belge Taşma düğmesi**|Ön plan (karakter)|`Environment.DocWellOverflowButtonGlyph`|  
|![Overflow](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 084_Overflow")<br /><br /> **Belge Taşma düğmesi**|Kenarlık|Yok|  
  
 **Vurgulu**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Overflow üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 085_OverflowHover")<br /><br /> **Üzerine gelindiğinde belge taşma düğmesi**|Arka Plan|`Environment.DocWellOverflowButtonMouseOverBackground`|  
|![Overflow üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 085_OverflowHover")<br /><br /> **Üzerine gelindiğinde belge taşma düğmesi**|Ön plan (karakter)|`Environment.DocWellOverflowButtonMouseOverGlyph`|  
|![Overflow üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 085_OverflowHover")<br /><br /> **Üzerine gelindiğinde belge taşma düğmesi**|Kenarlık|`Environment.DocWellOverflowButtonMouseOverBorder`|  
  
 **Basılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Basılan taşma](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 086_OverflowPressed")<br /><br /> **Belge taşma düğmesini basılı**|Arka Plan|`Environment.DocWellOverflowButtonMouseDownBackground`|  
|![Basılan taşma](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 086_OverflowPressed")<br /><br /> **Belge taşma düğmesini basılı**|Ön plan (karakter)|`Environment.DocWellOverflowButtonMouseDownGlyph`|  
|![Basılan taşma](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 086_OverflowPressed")<br /><br /> **Belge taşma düğmesini basılı**|Kenarlık|`Environment.DocWellOverflowButtonMouseDownBorder`|  
  
### <a name="tool-windows"></a>Araç pencereleri  
 Visual Studio ortamı tarafından sağlandığından, araç pencerelerini çoğaltmak için gerek yoktur. Ancak, kullanıcı Arabirimi her zaman Visual Studio ortamının bu bölümü ile tutarlı görünmesi araç pencerelerinde kullanılan renkleri yararlanmak istediğinize karar verin.  
  
 ![Araç penceresi kırmızı çizgi](../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303 087_ToolWindowRedline")  
  
 Kullan...  
 herhangi bir yerde araç pencerelerini eşleştirmek istediğiniz kullanıcı Arabirimi oluşturuyorsunuz.  
  
 Kullanmayın...  
 otomatik olarak değiştirmeyi istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir.  
  
#### <a name="tool-window-frame"></a>Araç pencere çerçevesi  
 Visual Studio araç pencereleri, birçok farklı görevler için kullanılır ve birçok farklı durumdan birinde bulunabilir. Araç penceresi açık değilse, tüm belge alanını dört tarafına atanabilir. Araç pencerelerini de herhangi bir kullanıcının ekranında konumlandırılmasına olanak tanıyan IDE dışında kaydırabilirsiniz. Kayan windows her zaman, IDE üzerinde durur. Son olarak, araç pencerelerini belge pencereleri yerleştirilmiş olabilir ve iyi belge sekme olarak görünür. Belge pencereleri yerleştirilmiş araç pencereleri, kısmen belge penceresi simge adları kullanarak renklendirilmiştir.  
  
 ![Araç pencere çerçevesi kırmızı çizgi](../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303 088_ToolWindowFrameRedline")  
  
 Kullan...  
 herhangi bir yerde araç pencerelerini eşleştirmek istediğiniz kullanıcı Arabirimi oluşturuyorsunuz.  
  
 Kullanmayın...  
 otomatik olarak değiştirmeyi istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir.  
  
 **Yuvalanmış**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Araç penceresi yerleştirilmiş](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303 089_ToolWindowDocked")|Arka Plan|`Environment.ToolWindowBackground`|  
|![Araç penceresi yerleştirilmiş](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303 089_ToolWindowDocked")|Kenarlık|`Environment.ToolWindowBorder`|  
  
 **Kayan: odaklanmış**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Araç penceresi odaklanmış](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303 090_ToolWindowFocused")|Arka Plan|`Environment.ToolWindowBackground`|  
|![Araç penceresi odaklanmış](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303 090_ToolWindowFocused")|Kenarlık|`Environment.MainWindowActiveDefaultBorder`|  
  
 **Kayan: odaklanmadan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Araç penceresi odaklanmadan](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303 091_ToolWindowUnfocused")|Arka Plan|`Environment.ToolWindowBackground`|  
|![Araç penceresi odaklanmadan](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303 091_ToolWindowUnfocused")|Kenarlık|`Environment.MainWindowInactiveBorder`|  
  
#### <a name="tool-window-title-bar"></a>Araç penceresinin başlık çubuğu  
 Başlık çubuğu kenarlığı doğru kenarlık ancak kalın çizgi başlık çubuğunun üst kısmında değil. Bir plana odaklanmadan durumuna belirteç adı yok.  
  
 ![Araç penceresinin başlık çubuğu kırmızı çizgi](../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303 092_ToolWindowTitleBarRedline")  
  
 Kullan...  
 herhangi bir yerde araç pencerelerini eşleştirmek istediğiniz kullanıcı Arabirimi oluşturuyorsunuz.  
  
 Kullanmayın...  
 otomatik olarak değiştirmeyi istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir.  
  
 **Odaklanmış**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Başlık çubuğu odaklanmış](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 093_TitleBarFocused")<br /><br /> **Odaklanmış başlık çubuğu**|Arka Plan|`Environment.TitleBarActiveGradientBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Başlık çubuğu odaklanmış](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 093_TitleBarFocused")<br /><br /> **Odaklanmış başlık çubuğu**|Ön plan (metin)|`Environment.TitleBarActiveText`|  
|![Başlık çubuğu odaklanmış](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 093_TitleBarFocused")<br /><br /> **Odaklanmış başlık çubuğu**|Kenarlık|`Environment.TitleBarActiveBorder`<br /><br /> Aynı arka plan rengini ayarlayın.|  
|![Başlık çubuğu odaklanmış](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 093_TitleBarFocused")<br /><br /> **Odaklanmış başlık çubuğu**|Sürükleme tutamacı|`Environment.TitleBarDragHandleActive`|  
  
 **Plana odaklanmadan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Başlık çubuğu odaklanmadan](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 094_TitleBarUnfocused")<br /><br /> **Plana odaklanmadan başlık çubuğu**|Arka Plan|`Environment.TitleBarInactiveGradientBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Başlık çubuğu odaklanmadan](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 094_TitleBarUnfocused")<br /><br /> **Plana odaklanmadan başlık çubuğu**|Ön plan (metin)|`Environment.TitleBarInactiveText`|  
|![Başlık çubuğu odaklanmadan](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 094_TitleBarUnfocused")<br /><br /> **Plana odaklanmadan başlık çubuğu**|Kenarlık|Yok|  
|![Başlık çubuğu odaklanmadan](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 094_TitleBarUnfocused")<br /><br /> **Plana odaklanmadan başlık çubuğu**|Sürükleme tutamacı|`Environment.TitleBarDragHandle`|  
  
##### <a name="title-bar-buttons"></a>Başlık çubuğu düğmeleri  
 ![Başlık çubuğu düğme kırmızı çizgi](../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303 095_TitleBarButtonRedline")  
  
 Kullan...  
 araç penceresinin başlık çubuğu renk belirteçleri kullanan kullanıcı arabiriminde görünen düğme.  
  
 Kullanmayın...  
 -   diğer konumlardaki düğmeler.  
  
- Belirtilen dışındaki tüm arka plan/ön plan arada.  
  
  **Default**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Başlık düğme odaklanmış](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")<br /><br /> **Odaklanmış**|Arka Plan|Yok|  
|![Başlık düğme odaklanmış](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")<br /><br /> **Odaklanmış**|Ön plan (karakter)|`Environment.ToolWindowButtonActiveGlyph`|  
|![Başlık düğme odaklanmış](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")<br /><br /> **Odaklanmış**|Kenarlık|Yok|  
|![Başlık düğme odaklanmadan](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")<br /><br /> **Plana odaklanmadan**|Arka Plan|Yok|  
|![Başlık düğme odaklanmadan](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")<br /><br /> **Plana odaklanmadan**|Ön plan (karakter)|`Environment.ToolWindowButtonInactiveGlyph`|  
|![Başlık düğme odaklanmadan](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")<br /><br /> **Plana odaklanmadan**|Kenarlık|Yok|  
  
 **Vurgulu**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Başlık çubuğu düğme üzerine gelindiğinde odaklanmış](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")<br /><br /> **Odaklanmış**|Arka Plan|`Environment.ToolWindowButtonHoverActive`|  
|![Başlık çubuğu düğme üzerine gelindiğinde odaklanmış](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")<br /><br /> **Odaklanmış**|Ön plan (karakter)|`Environment.ToolWindowButtonHoverActiveGlyph`|  
|![Başlık çubuğu düğme üzerine gelindiğinde odaklanmış](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")<br /><br /> **Odaklanmış**|Kenarlık|`Environment.ToolWindowButtonHoverActiveBorder`|  
|![Başlık çubuğu düğme üzerine gelindiğinde odaklanmadan](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")<br /><br /> **Plana odaklanmadan**|Arka Plan|`Environment.ToolWindowButtonHoverInactive`|  
|![Başlık çubuğu düğme üzerine gelindiğinde odaklanmadan](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")<br /><br /> **Plana odaklanmadan**|Ön plan (karakter)|`Environment.ToolWindowButtonHoverInactiveGlyph`|  
|![Başlık çubuğu düğme üzerine gelindiğinde odaklanmadan](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")<br /><br /> **Plana odaklanmadan**|Kenarlık|`Environment.ToolWindowButtonHoverInactiveBorder`|  
  
 **Basılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Başlık odaklı ve basılı düğmesi](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")<br /><br /> **Odaklanmış**|Arka Plan|`Environment.ToolWindowButtonDown`|  
|![Başlık odaklı ve basılı düğmesi](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")<br /><br /> **Odaklanmış**|Ön plan (karakter)|`Environment.ToolWindowButtonDownActiveGlyph`|  
|![Başlık odaklı ve basılı düğmesi](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")<br /><br /> **Odaklanmış**|Kenarlık|`Environment.ToolWindowButtonDownBorder`|  
|![Başlık çubuğu düğme odaklanmadan ve basılı](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")<br /><br /> **Plana odaklanmadan**|Arka Plan|`Environment.ToolWindowButtonDown`|  
|![Başlık çubuğu düğme odaklanmadan ve basılı](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")<br /><br /> **Plana odaklanmadan**|Ön plan (karakter)|`Environment.ToolWindowButtonDownInactiveGlyph`|  
|![Başlık çubuğu düğme odaklanmadan ve basılı](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")<br /><br /> **Plana odaklanmadan**|Kenarlık|`Environment.ToolWindowButtonDownBorder`|  
  
#### <a name="tool-window-tabs"></a>Araç penceresi sekmeleri  
 ![Araç penceresi sekmesindeki kırmızı çizgi](../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303 102_ToolWindowTabRedline")  
  
 Kullan...  
 herhangi bir yerde araç pencerelerini eşleştirmek istediğiniz kullanıcı Arabirimi oluşturuyorsunuz.  
  
 Kullanmayın...  
 otomatik olarak değiştirmeyi istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir.  
  
 **Seçilen sekmesi**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Araç penceresi sekmesinin odaklanmış](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")<br /><br /> **Seçildiğinde, odaklanmış aracı penceresi sekmesi**|Arka Plan|`Environment.ToolWindowTabSelectedTab`|  
|![Araç penceresi sekmesinin odaklanmış](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")<br /><br /> **Seçildiğinde, odaklanmış aracı penceresi sekmesi**|Ön plan (metin)|`Environment.ToolWindowTabSelectedActiveText`|  
|![Araç penceresi sekmesinin odaklanmış](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")<br /><br /> **Seçildiğinde, odaklanmış aracı penceresi sekmesi**|Kenarlık|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Aynı arka plan rengini ayarlayın.|  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Araç penceresi sekmesinin odaklanmadan](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")<br /><br /> **Seçildiğinde, plana odaklanmadan aracı penceresi sekmesi**|Arka Plan|`Environment.ToolWindowTabSelectedTab`|  
|![Araç penceresi sekmesinin odaklanmadan](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")<br /><br /> **Seçildiğinde, plana odaklanmadan aracı penceresi sekmesi**|Ön plan (metin)|`Environment.ToolWindowTabSelectedText`|  
|![Araç penceresi sekmesinin odaklanmadan](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")<br /><br /> **Seçildiğinde, plana odaklanmadan aracı penceresi sekmesi**|Kenarlık|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Aynı arka plan rengini ayarlayın.|  
  
 **Arka plan sekmesi**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Araç penceresi arka plan sekmesine](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")<br /><br /> **Arka plan aracı penceresi sekmesi**|Arka Plan|`Environment.ToolWindowTabGradientBegin`<br /><br /> Visual Studio 2013'te aynı renk değeri kümesine gradyan durdurur.<br /><br /> `Environment.ToolWindowTabGradientEnd`<br /><br /> Visual Studio 2013'te aynı renk değeri kümesine gradyan durdurur.|  
|![Araç penceresi arka plan sekmesine](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")<br /><br /> **Arka plan aracı penceresi sekmesi**|Ön plan (metin)|`Environment.ToolWindowTabText`|  
|![Araç penceresi arka plan sekmesine](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")<br /><br /> **Arka plan aracı penceresi sekmesi**|Kenarlık|`Environment.ToolWindowTabBorder`|  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Üzerine gelindiğinde araç penceresi arka plan sekmesine](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")<br /><br /> **Üzerine gelindiğinde arka plan aracı penceresi sekmesi**|Arka Plan|`Environment.ToolWindowTabMouseOverBackgroundBegin`<br /><br /> Visual Studio 2013'te aynı renk değeri kümesine gradyan durdurur.<br /><br /> `Environment.ToolWindowTabMouseOverBackgroundEnd`<br /><br /> Visual Studio 2013'te aynı renk değeri kümesine gradyan durdurur.|  
|![Üzerine gelindiğinde araç penceresi arka plan sekmesine](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")<br /><br /> **Üzerine gelindiğinde arka plan aracı penceresi sekmesi**|Ön plan (metin)|`Environment.ToolWindowTabMouseOverText`|  
|![Üzerine gelindiğinde araç penceresi arka plan sekmesine](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")<br /><br /> **Üzerine gelindiğinde arka plan aracı penceresi sekmesi**|Kenarlık|`Environment.ToolWindowTabMouseOverBorder`<br /><br /> Aynı arka plan rengini ayarlayın.|  
  
#### <a name="auto-hide-tabs"></a>Sekmeleri otomatik olarak gizle  
 ![Otomatik&#45;Gizle kırmızı çizgi](../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303 107_AutoHideRedline")  
  
 Kullan...  
 herhangi bir otomatik olarak gizlendiğinde araç penceresi sekmeleri eşleştirmek istediğiniz kullanıcı Arabirimi oluşturuyorsunuz.  
  
 Kullanmayın...  
 otomatik olarak değiştirmeyi istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir.  
  
 **Default**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Otomatik&#45;sekmesini gizle](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 108_AutoHideTab")<br /><br /> **Varsayılan otomatik gizleme sekmesi**|Arka Plan|`Environment.AutoHideTabBackgroundBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Otomatik&#45;sekmesini gizle](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 108_AutoHideTab")<br /><br /> **Varsayılan otomatik gizleme sekmesi**|Ön plan (metin)|`Environment.AutoHideTabText`|  
|![Otomatik&#45;sekmesini gizle](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 108_AutoHideTab")<br /><br /> **Varsayılan otomatik gizleme sekmesi**|Kenarlık|`Environment.AutoHideTabBorder`|  
  
 **Vurgulu**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Otomatik&#45;sekmesini üzerine gelindiğinde Gizle](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 109_AutoHideTabHover")<br /><br /> **Üzerine gelindiğinde otomatik gizleme sekmesi**|Arka Plan|`Environment.AutoHideTabMouseOverBackgroundBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Otomatik&#45;sekmesini üzerine gelindiğinde Gizle](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 109_AutoHideTabHover")<br /><br /> **Üzerine gelindiğinde otomatik gizleme sekmesi**|Ön plan (metin)|`Environment.AutoHideTabMouseOverText`|  
|![Otomatik&#45;sekmesini üzerine gelindiğinde Gizle](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 109_AutoHideTabHover")<br /><br /> **Üzerine gelindiğinde otomatik gizleme sekmesi**|Kenarlık|`Environment.AutoHideTabMouseOverBorder`|  
  
### <a name="common-shared-controls"></a>Paylaşılan ortak denetimleri  
 Standart bir Visual Studio komut çubuğu, özelliğini kullandığınızda, stil uygulanmış bir kabuk denetimlerini erişebilir ve bu ortak denetimleri yeniden-template gerekir. Ancak, özel bir komut çubuğu oluşturmak ihtiyacınız varsa, özel denetimler de gerekebilir. Bu durumda, kullanıcı Arabirimi Visual Studio geri kalanı ile tutarlı olmasını sağlayın, her biri aşağıdaki denetimleri için doğru belirteci adları kullandığınızdan emin olun.  
  
#### <a name="search-box"></a>Arama kutusu  
 Mümkün olduğunda, Visual Studio ortamı tarafından sağlanan genel arama denetimini kullanın. Arama kutusuna renklerini bulundu "SearchControl" kategorisinde **ShellColors.pkgdef** giriş alanı, eylem düğmesi, açılan düğmeyi ve açılan menü için belirteç adları içeren dosya.  
  
 Bir arama kutusu bazıları birbirini dışlayan olan çeşitli durumları biri olabilir:  
  
- "Odaklı" veya "odaklanmadan" olup olmadığını imleç ve metin kutusundaki için kısaltmasıdır.  
  
- Kullanıcının metin kutusuna bir arama sorgusu girişinin için "Etkin" veya "etkin" anlamına gelir.  
  
- "Vurgu", kullanıcı (Bu durumda, diğer tüm durumları geçersiz kılar) fare ile arama kutusuna moused anlamına gelir.  
  
- "Devre dışı" arama işlevi için geçerli bağlam kapalı anlamına gelir.  
  
  ![Arama kutusuna kırmızı çizgi](../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303 110_SearchBoxRedline")  
  
  Kullan...  
  ne zaman bir özel arama kutusu tasarlarken.  
  
  Kullanmayın...  
  -   her şey için bir arama kutusu değil.  
  
- her zaman arama eşleştirilecek istemediğiniz her şey için kullanıcı Arabirimi kutusu.  
  
  **Odaklanmış**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Arama giriş alanı odaklanmış](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")<br /><br /> **Giriş alanı**|Arka Plan|`SearchControl.FocusedBackground`|  
|![Arama giriş alanı odaklanmış](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")<br /><br /> **Giriş alanı**|Ön plan (metin)|`SearchControl.FocusedBackground`|  
|![Arama giriş alanı odaklanmış](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")<br /><br /> **Giriş alanı**|Kenarlık|`SearchControl.FocusedBorder`|  
|![Arama giriş alanı odaklanmış](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")<br /><br /> **Giriş alanı**|Ayırıcı|`SearchControl.FocusedDropDownSeparator`|  
|![Arama eylem düğmesi odaklanmış](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")<br /><br /> **Eylem düğmesi**|Arka Plan|Yok.|  
|![Arama eylem düğmesi odaklanmış](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")<br /><br /> **Eylem düğmesi**|Ön plan (arama karakter)|`SearchControl.SearchGlyph`|  
|![Arama eylem düğmesi odaklanmış](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")<br /><br /> **Eylem düğmesi**|Ön plan (durdurma karakter)|`SearchControl.StopGlyph`|  
|![Arama eylem düğmesi odaklanmış](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")<br /><br /> **Eylem düğmesi**|Ön plan (NET karakter)|`SearchControl.ClearGlyph`|  
|![Arama eylem düğmesi odaklanmış](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")<br /><br /> **Eylem düğmesi**|Kenarlık|Yok|  
|![Arama açılan&#45;odaklanmış düğmesini basılı](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")<br /><br /> **Aşağı açılan düğmesi**|Arka Plan|`SearchControl.FocusedDropDownButton`|  
|![Arama açılan&#45;odaklanmış düğmesini basılı](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")<br /><br /> **Aşağı açılan düğmesi**|Ön plan (karakter)|`SearchControl.FocusedDropDownButtonGlyph`|  
|![Arama açılan&#45;odaklanmış düğmesini basılı](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")<br /><br /> **Aşağı açılan düğmesi**|Kenarlık|`SearchControl.FocusedDropDownButtonBorder`|  
  
 **Plana odaklanmadan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Arama giriş alanı odaklanmadan](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")<br /><br /> **Etkin giriş alanı**|Arka Plan|`SearchControl.SearchActiveBackground`|  
|![Arama giriş alanı odaklanmadan](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")<br /><br /> **Etkin giriş alanı**|Ön plan (metin)|`SearchControl.SearchActiveBackground`|  
|![Arama giriş alanı odaklanmadan](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")<br /><br /> **Etkin giriş alanı**|Kenarlık|`SearchControl.UnfocusedBorder`|  
|![Arama giriş alanı odaklanmadan](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")<br /><br /> **Etkin giriş alanı**|Ayırıcı|`SearchControl.DropDownSeparator`|  
|![Arama giriş alanı odaklanmadan ve etkin olmayan](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303 114 1_SearchInputFieldUnfocusedInactive")<br /><br /> **Etkin olmayan giriş alanı**|Arka Plan|`SearchControl.Unfocused`|  
|![Arama giriş alanı odaklanmadan ve etkin olmayan](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303 114 1_SearchInputFieldUnfocusedInactive")<br /><br /> **Etkin olmayan giriş alanı**|Ön plan (metin)|`SearchControl.Unfocused`|  
|![Arama giriş alanı odaklanmadan ve etkin olmayan](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303 114 1_SearchInputFieldUnfocusedInactive")<br /><br /> **Etkin olmayan giriş alanı**|Kenarlık|`SearchControl.UnfocusedBorder`|  
|![Arama giriş alanı odaklanmadan ve etkin olmayan](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303 114 1_SearchInputFieldUnfocusedInactive")<br /><br /> **Etkin olmayan giriş alanı**|Ayırıcı|`SearchControl.DropDownSeparator`|  
|![Arama eylem düğmesi odaklanmadan](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")<br /><br /> **Eylem düğmesi**|Arka Plan|Yok|  
|![Arama eylem düğmesi odaklanmadan](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")<br /><br /> **Eylem düğmesi**|Ön plan (arama karakter)|`SearchControl.SearchGlyph`|  
|![Arama eylem düğmesi odaklanmadan](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")<br /><br /> **Eylem düğmesi**|Ön plan (durdurma karakter)|`SearchControl.StopGlyph`|  
|![Arama eylem düğmesi odaklanmadan](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")<br /><br /> **Eylem düğmesi**|Ön plan (NET karakter)|`SearchControl.ClearGlyph`|  
|![Arama eylem düğmesi odaklanmadan](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")<br /><br /> **Eylem düğmesi**|Kenarlık|Yok|  
|![Arama açılan&#45;Kapat düğmesi odaklanmadan](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")<br /><br /> **Aşağı açılan düğmesi**|Arka Plan|`SearchControl.UnfocusedDropDownButton`|  
|![Arama açılan&#45;Kapat düğmesi odaklanmadan](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")<br /><br /> **Aşağı açılan düğmesi**|Ön plan (karakter)|`SearchControl.UnfocusedDropDownButtonGlyph`|  
|![Arama açılan&#45;Kapat düğmesi odaklanmadan](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")<br /><br /> **Aşağı açılan düğmesi**|Kenarlık|`SearchControl.UnfocusedDropDownButtonBorder`|  
  
 **Basılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Arama eylem düğmesi basılı](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303 116 1_SearchActionButtonPressed")<br /><br /> **Eylem düğmesi**|Arka Plan|`SearchControl.ActionButtonMouseDown`|  
|![Arama eylem düğmesi basılı](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303 116 1_SearchActionButtonPressed")<br /><br /> **Eylem düğmesi**|Ön plan (karakter)|`SearchControl.ActionButtonMouseDownGlyph`|  
|![Arama eylem düğmesi basılı](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303 116 1_SearchActionButtonPressed")<br /><br /> **Eylem düğmesi**|Kenarlık|`SearchControl.ActionButtonMouseDownBorder`|  
|![Arama açılan&#45;düğmeye basıldığını aşağı](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303 116 2_SearchDropdownButtonPressed")<br /><br /> **Aşağı açılan düğmesi**|Arka Plan|`SearchControl.MouseDownDropDownButton`|  
|![Arama açılan&#45;düğmeye basıldığını aşağı](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303 116 2_SearchDropdownButtonPressed")<br /><br /> **Aşağı açılan düğmesi**|Ön plan (karakter)|`SearchControl.MouseDownDropDownButtonGlyph`|  
|![Arama açılan&#45;düğmeye basıldığını aşağı](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303 116 2_SearchDropdownButtonPressed")<br /><br /> **Aşağı açılan düğmesi**|Kenarlık|`SearchControl.MouseDownDropDownButtonBorder`|  
  
 **Vurgulanan (yalnızca metin)**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Arama giriş alanı vurgulama](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")<br /><br /> **Giriş alanı vurgulanmış metin**|Arka Plan|`SearchControl.Selection`|  
|![Arama giriş alanı vurgulama](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")<br /><br /> **Giriş alanı vurgulanmış metin**|Ön plan (metin)|`SearchControl.FocusedBackground`|  
|![Arama giriş alanı vurgulama](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")<br /><br /> **Giriş alanı vurgulanmış metin**|Kenarlık|Yok.|  
|![Arama giriş alanı vurgulama](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")<br /><br /> **Giriş alanı vurgulanmış metin**|Ayırıcı|`SearchControl.FocusedDropDownSeparator`|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Arama giriş alanını devre dışı](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")<br /><br /> **Giriş alanı**|Arka Plan|`SearchControl.Disabled`|  
|![Arama giriş alanını devre dışı](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")<br /><br /> **Giriş alanı**|Ön plan (metin)|`SearchControl.Disabled`|  
|![Arama giriş alanını devre dışı](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")<br /><br /> **Giriş alanı**|Kenarlık|`SearchControl.DisabledBorder`|  
|![Arama giriş alanını devre dışı](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")<br /><br /> **Giriş alanı**|Ayırıcı|`SearchControl.DropDownSeparator`|  
|![Arama eylem düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")<br /><br /> **Eylem düğmesi**|Arka Plan|Yok.|  
|![Arama eylem düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")<br /><br /> **Eylem düğmesi**|Ön plan (karakter)|`SearchControl.ActionButtonDisabledGlyph`|  
|![Arama eylem düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")<br /><br /> **Eylem düğmesi**|Kenarlık|Yok.|  
|![Arama açılan&#45;Kapat düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")<br /><br /> **Aşağı açılan düğmesi**|Arka Plan|Yok.|  
|![Arama açılan&#45;Kapat düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")<br /><br /> **Aşağı açılan düğmesi**|Ön plan (karakter)|`SearchControl.DisabledDownButtonGlyph`|  
|![Arama açılan&#45;Kapat düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")<br /><br /> **Aşağı açılan düğmesi**|Kenarlık|Yok.|  
  
##### <a name="search-drop-down-lists"></a>Arama açılan listeler  
 Arama kutusu açılır menüsünde, Visual Studio'daki diğer açılan menüler biraz daha karmaşık hale olasılığına sahiptir. "Önerilen aramalar" ve "Arama Seçenekleri" bölümleri tek başına görünebilir veya birlikte menü ve her biri ayrı ayrı renktedir. Bir satır da birlikte görünür ve tüm açılan menüden bir kenarlık çevreleyen bu iki bölüme ayırır.  
  
 ![Arama açılan&#45;aşağı kırmızı çizgi](../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303 124_SearchDropdownRedline")  
  
 Kullan...  
 -   ne zaman bir özel arama açılan listedeki oluşturuyorsunuz.  
  
- Düzeltme listesi bileşenleri için doğru belirteci adları.  
  
  Kullanmayın...  
  -   diğer bağlamlarda görünen açılan listeler.  
  
- Belirtilen dışındaki tüm arka plan/ön plan arada.  
  
  **Varsayılan (başka hiçbir durum)**  
  
|Öğe|Belirteç adı: Category.color|  
|-------------|--------------------------------|  
|Kenarlık|`SearchControl.PopupBorder`|  
|Ayırıcı|`SearchControl.PopupSectionHeaderSeparator`|  
|Gölge|`Environment.DropShadowBackground`|  
  
 **Default**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Önerilen arama](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303 125_SearchSuggested")<br /><br /> **Önerilen aramalar**|Arka Plan|`SearchControl.PopupItemsListBackgroundGradientBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Önerilen arama](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303 125_SearchSuggested")<br /><br /> **Önerilen aramalar**|Ön plan (metin)|`SearchControl.PopupItemText`|  
|![Arama onay kutusunu](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 126_SearchCheckbox")<br /><br /> **Arama Seçenekleri (onay kutusu)**|Arka Plan|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Arama Seçenekleri](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 127_SearchOptions")<br /><br /> **Arama Seçenekleri (bağlantı)**|Arka Plan|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Arama onay kutusunu](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 126_SearchCheckbox")<br /><br /> **Arama Seçenekleri (onay kutusu)**|Ön plan (onay kutusu metni)|`SearchControl.PopupCheckboxText`|  
|![Arama Seçenekleri](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 127_SearchOptions")<br /><br /> **Arama Seçenekleri (bağlantı)**|Ön plan (onay kutusu metni)|`SearchControl.PopupCheckboxText`|  
|![Arama onay kutusunu](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 126_SearchCheckbox")<br /><br /> **Arama Seçenekleri (onay kutusu)**|Ön plan (bağlantı metni)|`SearchControl.PopupButtonText`|  
|![Arama Seçenekleri](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 127_SearchOptions")<br /><br /> **Arama Seçenekleri (bağlantı)**|Ön plan (bağlantı metni)|`SearchControl.PopupButtonText`|  
|![Arama onay kutusunu](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 126_SearchCheckbox")<br /><br /> **Arama Seçenekleri (onay kutusu)**|Başlık arka plan|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Arama Seçenekleri](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 127_SearchOptions")<br /><br /> **Arama Seçenekleri (bağlantı)**|Başlık arka plan|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Arama onay kutusunu](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 126_SearchCheckbox")<br /><br /> **Arama Seçenekleri (onay kutusu)**|Ön plan (üst bilgi metni)|`SearchControl.PopupSectionHeaderText`|  
|![Arama Seçenekleri](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 127_SearchOptions")<br /><br /> **Arama Seçenekleri (bağlantı)**|Ön plan (üst bilgi metni)|`SearchControl.PopupSectionHeaderText`|  
  
 **Vurgulu**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Üzerine gelindiğinde önerilen arama](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 128_SearchSuggestedHover")<br /><br /> **Önerilen aramalar**|Arka Plan|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Üzerine gelindiğinde önerilen arama](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 128_SearchSuggestedHover")<br /><br /> **Önerilen aramalar**|Ön plan (metin)|`SearchControl.PopupMouseOverItemText`|  
|![Üzerine gelindiğinde önerilen arama](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 128_SearchSuggestedHover")<br /><br /> **Önerilen aramalar**|Kenarlık|`SearchControl.PopupControlMouseOverBorder`|  
|![Arama onay kutusunu üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 129_SearchCheckboxHover")<br /><br /> **Önerilen aramalar (onay kutusu)**|Arka Plan|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Arama seçenekleri üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 130_SearchOptionsHover")<br /><br /> **Arama Seçenekleri**|Arka Plan|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Arama onay kutusunu üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 129_SearchCheckboxHover")<br /><br /> **Önerilen aramalar (onay kutusu)**|Ön plan (onay kutusu metni)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Arama seçenekleri üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 130_SearchOptionsHover")<br /><br /> **Arama Seçenekleri**|Ön plan (onay kutusu metni)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Arama onay kutusunu üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 129_SearchCheckboxHover")<br /><br /> **Önerilen aramalar (onay kutusu)**|Ön plan (bağlantı metni)|`SearchControl.PopupButtonMouseDownText`|  
|![Arama seçenekleri üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 130_SearchOptionsHover")<br /><br /> **Arama Seçenekleri**|Ön plan (bağlantı metni)|`SearchControl.PopupButtonMouseDownText`|  
|![Arama onay kutusunu üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 129_SearchCheckboxHover")<br /><br /> **Önerilen aramalar (onay kutusu)**|Kenarlık|`SearchControl.PopupControlMouseOverBorder`|  
|![Arama seçenekleri üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 130_SearchOptionsHover")<br /><br /> **Arama Seçenekleri**|Kenarlık|`SearchControl.PopupControlMouseOverBorder`|  
  
 **Basılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Arama önerilen basılı](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")<br /><br /> **Önerilen aramalar (onay kutusu)**|Onay kutusu arka plan|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Arama Seçenekleri basılı](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 132_SearchOptionsPressed")<br /><br /> **Arama Seçenekleri**|Onay kutusu arka plan|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Arama önerilen basılı](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")<br /><br /> **Önerilen aramalar (onay kutusu)**|Onay kutusu arka plan|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Arama Seçenekleri basılı](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 132_SearchOptionsPressed")<br /><br /> **Arama Seçenekleri**|Onay kutusu arka plan|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Arama önerilen basılı](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")<br /><br /> **Önerilen aramalar (onay kutusu)**|Ön plan (onay kutusu metni)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Arama Seçenekleri basılı](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 132_SearchOptionsPressed")<br /><br /> **Arama Seçenekleri**|Ön plan (onay kutusu metni)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Arama önerilen basılı](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")<br /><br /> **Önerilen aramalar (onay kutusu)**|Bağlantı arka plan|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Arama Seçenekleri basılı](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 132_SearchOptionsPressed")<br /><br /> **Arama Seçenekleri**|Bağlantı arka plan|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.|  
|![Arama önerilen basılı](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")<br /><br /> **Önerilen aramalar (onay kutusu)**|Ön plan (bağlantı metni)|`SearchControl.PopupButtonMouseDownText`|  
|![Arama Seçenekleri basılı](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 132_SearchOptionsPressed")<br /><br /> **Arama Seçenekleri**|Ön plan (bağlantı metni)|`SearchControl.PopupButtonMouseDownText`|  
  
#### <a name="hyperlink"></a>Köprü  
 Köprüyü bir ön plan/arka plan çifti sahip olmayan bir denetimdir. Her durumda, doğru koyu gri ve beyaz arka plan üzerinde görünür köprü ön plan rengini kullanın. Köprü denetim için renk belirteç kullanmazsanız "basılı için" varsayılan sistem renk görürsünüz ", kırmızı flash. Bu denetim doğru ortamı renk belirteci kullanmıyor sinyaldir.  
  
 ![Köprü kırmızı çizgi](../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303 133_HyperlinkRedline")  
  
 Kullan...  
 özel bir köprü oluşturmak gerektiğinde.  
  
 Kullanmayın...  
 her şey için köprü değil.  
  
 **Default**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Köprü varsayılan](../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303 134_Hyperlink")|Ön plan (metin)|`Environment.PanelHyperlink`|  
  
 **Vurgulu**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Üzerine gelindiğinde köprü](../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303 135_HyperlinkHover")|Ön plan (metin)|`Environment.PanelHyperlinkHover`|  
  
 **Basılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Basılan köprü](../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303 136_HyperlinkPressed")|Ön plan (metin)|`Environment.PanelHyperlinkPressed`|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Devre dışı köprü](../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303 137_HyperlinkDisabled")|Ön plan (metin)|`Environment.PanelHyperlinkDisabled`|  
  
#### <a name="infobar"></a>Bilgi Çubuğu  
 Infobars her zaman bir belge penceresi veya araç penceresinin üst kısmında görünür ve belirli bir bağlam hakkında daha fazla bilgi sağlamak için kullanılır.  
  
 ![Bilgi çubuğu kırmızı çizgi](../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303 138_InfobarRedline")  
  
 Kullan...  
 Özel infobars oluştururken.  
  
 Kullanmayın...  
 bir bilgi çubuğu için benzer olmayan kullanıcı Arabirimi öğeleri için.  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Bilgi Çubuğu](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303 139_Infobar")<br /><br /> **Bilgi Çubuğu**|Arka Plan|`Environment.InfoBackground`|  
|![Bilgi Çubuğu](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303 139_Infobar")<br /><br /> **Bilgi Çubuğu**|Ön plan (metin)|`Environment.InfoText`|  
|![Bilgi Çubuğu](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303 139_Infobar")<br /><br /> **Bilgi Çubuğu**|Kenarlık|`Environment.ToolWindowBorder`|  
  
#### <a name="scroll-bar"></a>Kaydırma çubuğu  
 Kaydırma çubukları Visual Studio ortamı tarafından stillere ve temalı olması gerekmez. Ancak, kullanıcı Arabirimi her zaman Visual Studio ortamının bu bölümü ile tutarlı görünmesi kaydırma çubuklarında kullanılan renkleri yararlanmak istediğinize karar verin.  
  
 ![Kaydırma çubuğu kırmızı çizgi](../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303 140_ScrollbarRedline")  
  
 Kullan...  
 ne zaman Visual Studio kaydırma çubukları eşleştirmek istediğiniz kullanıcı Arabirimi oluşturuyorsunuz.  
  
 Kullanmayın...  
 her şey için kaydırma çubuğu kullanıcı Arabirimi her zaman aynı istemezsiniz.  
  
 **Default**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Kaydırma çubuğu](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303 141_Scrollbar")<br /><br /> **Kaydırma çubuğu**|Kaydırma çubuğu|`Environment.ScrollBarBackground`|  
|![Kaydırma çubuğu](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303 141_Scrollbar")<br /><br /> **Kaydırma çubuğu**|Ön plan (Flash)|`Environment.ScrollBarThumbBackground`|  
|![Kaydırma ok](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303 142_ScrollbarArrow")<br /><br /> **Kaydırma ok**|Arka Plan|`Environment.ScrollBarArrowBackground`<br /><br /> Kaydırma çubuğu aynı renge ayarlayın.|  
|![Kaydırma ok](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303 142_ScrollbarArrow")<br /><br /> **Kaydırma ok**|Ön plan (karakter)|`Environment.ScrollBarArrowGlyph`|  
  
 **Vurgulu**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Kaydırma çubuğu üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303 143_ScrollbarHover")<br /><br /> **Kaydırma çubuğu**|Kaydırma çubuğu|`Environment.ScrollBarBackground`|  
|![Kaydırma çubuğu üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303 143_ScrollbarHover")<br /><br /> **Kaydırma çubuğu**|Ön plan (Flash)|`Environment.ScrollBarThumbMouseOverBackground`|  
|![Kaydırma çubuğu üzerine gelindiğinde ok](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303 144_ScrollbarArrowHover")<br /><br /> **Kaydırma ok**|Arka Plan|`Environment.ScrollBarArrowMouseOverBackground`<br /><br /> Kaydırma çubuğu aynı renge ayarlayın.|  
|![Kaydırma çubuğu üzerine gelindiğinde ok](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303 144_ScrollbarArrowHover")<br /><br /> **Kaydırma ok**|Ön plan (karakter)|`Environment.ScrollBarArrowGlyphMouseOver`|  
  
 **Basılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Basılan kaydırma çubuğu](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303 145_ScrollbarPressed")<br /><br /> **Kaydırma çubuğu**|Kaydırma çubuğu|`Environment.ScrollBarBackground`|  
|![Basılan kaydırma çubuğu](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303 145_ScrollbarPressed")<br /><br /> **Kaydırma çubuğu**|Ön plan (Flash)|`Environment.ScrollBarThumbPressedBackground`|  
|![Kaydırma basılı ok](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303 146_ScrollbarArrowPressed")<br /><br /> **Kaydırma ok**|Arka Plan|`Environment.ScrollBarArrowPressedBackground`<br /><br /> Kaydırma çubuğu aynı renge ayarlayın.|  
|![Kaydırma basılı ok](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303 146_ScrollbarArrowPressed")<br /><br /> **Kaydırma ok**|Ön plan (karakter)|`Environment.ScrollBarArrowGlyphPressed`|  
  
####  <a name="BKMK_TreeView"></a> Ağaç görünümü  
 Çözüm Gezgini, Sunucu Gezgini ve sınıf görünümü de dahil olmak üzere birçok araç pencereleri, renklerini rengi adları TreeView kategorisinde denetlediği hiyerarşik bir kuruluş uygulamaz. Ağaç görünümünde tüm öğeler, arka plan ve metin renklerini içerir. Alt öğelerinin iç içe geçmiş öğeler de öğe genişletilmiş veya daraltılmış olup olmadığını belirten karakterler var.  
  
 ![Ağaç görünümü kırmızı çizgi](../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303 147_TreeViewRedline")  
  
 Kullan...  
 herhangi bir hiyerarşik bir kuruluş görünümü yapması gerekir.  
  
 Kullanmayın...  
 -   her şey için bir ağaç görünümüne benzer değil.  
  
- Belirtilen dışındaki tüm arka plan/ön plan arada.  
  
  **Default**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ağaç görünümü](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 148_TreeView")|Arka Plan|`TreeView.Background`|  
|![Ağaç görünümü](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 148_TreeView")|Ön plan (metin)|`TreeView.Background`|  
|![Ağaç görünümü](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 148_TreeView")|Ön plan (karakter)|`TreeView.Glyph`|  
|![Ağaç görünümü](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 148_TreeView")|Kenarlık|Yok.|  
  
 **Vurgulu**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ağaç görünümü üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 149_TreeViewHover")|Arka Plan|`TreeView.Background`|  
|![Ağaç görünümü üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 149_TreeViewHover")|Ön plan (metin)|`TreeView.Background`|  
|![Ağaç görünümü üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 149_TreeViewHover")|Ön plan (karakter)|`TreeView.GlyphMouseOver`|  
|![Ağaç görünümü üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 149_TreeViewHover")|Kenarlık|Yok.|  
  
 **Üzerine sürükleyin**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ağaç görünümü dragover](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 150_TreeViewDragOver")|Arka Plan|`TreeView.DragOverItem`|  
|![Ağaç görünümü dragover](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 150_TreeViewDragOver")|Ön plan (metin)|`TreeView.DragOverItem`|  
|![Ağaç görünümü dragover](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 150_TreeViewDragOver")|Ön plan (karakter)|`TreeView.DragOverItemGlyph`|  
|![Ağaç görünümü dragover](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 150_TreeViewDragOver")|Kenarlık|Yok.|  
  
 **Seçili**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ağaç görünümü odaklanmış](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 151_TreeViewFocused")<br /><br /> **Odaklanmış**|Arka Plan|`TreeView.SelectedItemActive`|  
|![Ağaç görünümü odaklanmış](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 151_TreeViewFocused")<br /><br /> **Odaklanmış**|Ön plan (metin)|`TreeView.SelectedItemActive`|  
|![Ağaç görünümü odaklanmış](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 151_TreeViewFocused")<br /><br /> **Odaklanmış**|Ön plan (karakter)|`TreeView.SelectedItemActiveGlyph`|  
|![Ağaç görünümü odaklanmış](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 151_TreeViewFocused")<br /><br /> **Odaklanmış**|Kenarlık|`TreeView.FocusVisualBorder`|  
|![Ağaç görünümü odaklanmadan](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 152_TreeViewUnfocused")<br /><br /> **Plana odaklanmadan**|Arka Plan|`TreeView.SelectedItemInactive`|  
|![Ağaç görünümü odaklanmadan](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 152_TreeViewUnfocused")<br /><br /> **Plana odaklanmadan**|Ön plan (metin)|`TreeView.SelectedItemInactive`|  
|![Ağaç görünümü odaklanmadan](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 152_TreeViewUnfocused")<br /><br /> **Plana odaklanmadan**|Ön plan (karakter)|`TreeView.SelectedItemInactiveGlyph`|  
|![Ağaç görünümü odaklanmadan](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 152_TreeViewUnfocused")<br /><br /> **Plana odaklanmadan**|Kenarlık|Yok.|  
  
 **Seçili üzerine gelin**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ağaç görünümü üzerine gelindiğinde odaklanmış](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")<br /><br /> **Odaklanmış**|Arka Plan|`TreeView.SelectedItemActive`|  
|![Ağaç görünümü üzerine gelindiğinde odaklanmış](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")<br /><br /> **Odaklanmış**|Ön plan (metin)|`TreeView.SelectedItemActive`|  
|![Ağaç görünümü üzerine gelindiğinde odaklanmış](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")<br /><br /> **Odaklanmış**|Ön plan (karakter)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Ağaç görünümü üzerine gelindiğinde odaklanmış](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")<br /><br /> **Odaklanmış**|Kenarlık|Yok`TreeView.FocusVisualBorder`|  
|![Ağaç görünümü odaklanmadan üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")<br /><br /> **Plana odaklanmadan**|Arka Plan|`TreeView.SelectedItemInactive`|  
|![Ağaç görünümü odaklanmadan üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")<br /><br /> **Plana odaklanmadan**|Ön plan (metin)|`TreeView.SelectedItemInactive`|  
|![Ağaç görünümü odaklanmadan üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")<br /><br /> **Plana odaklanmadan**|Ön plan (karakter)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Ağaç görünümü odaklanmadan üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")<br /><br /> **Plana odaklanmadan**|Kenarlık|Yok.|  
  
#### <a name="button-controls"></a>Düğme denetimleri  
 ![Düğme denetimi kırmızı çizgi](../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303 155_ButtonControlRedline")  
  
 Kullan...  
 Visual Studio temasından (açık, koyu, mavi veya bir sistem yüksek karşıtlıklı tema) ile tümleştirmek istediğiniz belge kutusu düğmeleri için.  
  
 Kullanmayın...  
 Visual Studio temasını bulunmayan özel bir arka plan karşı görüntüler düğmeler.  
  
 **Default**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Düğme](../extensibility/ux-guidelines/media/0303-156-button.png "0303 156_Button")|Düğme|`CommonControls.Button`|  
|![Düğme](../extensibility/ux-guidelines/media/0303-156-button.png "0303 156_Button")|Düğme kenarlığı|`CommonControls.ButtonBorder`|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Düğme devre dışı](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303 157_ButtonDisabled")|Düğme|`CommonControls.ButtonDisabled`|  
|![Düğme devre dışı](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303 157_ButtonDisabled")|Düğme kenarlığı|`CommonControls.ButtonBorderDisabled`|  
  
 **Vurgulu**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Düğme üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303 158_ButtonHover")|Düğme|`CommonControls.ButtonHover`|  
|![Düğme üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303 158_ButtonHover")|Düğme kenarlığı|`CommonControls.ButtonBorderHover`|  
  
 **Basılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Düğmeye basıldığını](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303 159_ButtonPressed")|Düğme|`CommonControls.ButtonPressed`|  
|![Düğmeye basıldığını](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303 159_ButtonPressed")|Düğme kenarlığı|`CommonControls.ButtonBorderPressed`|  
  
 **Odaklanmış**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Odaklanmış düğmesi](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303 160_ButtonFocused")|Düğme|`CommonControls.ButtonFocused`|  
|![Odaklanmış düğmesi](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303 160_ButtonFocused")|Düğme kenarlığı|`CommonControls.ButtonBorderFocused`|  
  
#### <a name="check-box-controls"></a>Onay kutusu denetimleri  
 ![Onay kutusu kırmızı çizgi](../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303 161_CheckboxRedline")  
  
 Kullan...  
 Belgenin içinde bulunan onay kutusu denetimleri için yanı sıra.  
  
 Kullanmayın...  
 herhangi bir UI için bu onay kutusu denetimi değil.  
  
 **Default**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Onay kutusu](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 162_Checkbox")|Arka Plan|`CommonControls.CheckBoxBackground`|  
|![Onay kutusu](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 162_Checkbox")|Kenarlık|`CommonControls.CheckBoxBorder`|  
|![Onay kutusu](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 162_Checkbox")|Metin|`CommonControls.CheckBoxText`|  
|![Onay kutusu](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 162_Checkbox")|Glif|`CommonControls.CheckBoxGlyph`|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Devre dışı onay kutusu](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 163_CheckboxDisabled")|Arka Plan|`CommonControls.CheckBoxBackgroundDisabled`|  
|![Devre dışı onay kutusu](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 163_CheckboxDisabled")|Kenarlık|`CommonControls.CheckBoxBorderDisabled`|  
|![Devre dışı onay kutusu](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 163_CheckboxDisabled")|Metin|`CommonControls.CheckBoxTextDisabled`|  
|![Devre dışı onay kutusu](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 163_CheckboxDisabled")|Glif|`CommonControls.CheckBoxGlyphDisabled`|  
  
 **Vurgulu**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Onay kutusu üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 164_CheckboxHover")|Arka Plan|`CommonControls.CheckBoxBackgroundHover`|  
|![Onay kutusu üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 164_CheckboxHover")|Kenarlık|`CommonControls.CheckBoxBorderHover`|  
|![Onay kutusu üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 164_CheckboxHover")|Metin|`CommonControls.CheckBoxTextHover`|  
|![Onay kutusu üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 164_CheckboxHover")|Glif|`CommonControls.CheckBoxGlyphHover`|  
  
 **Basılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Onay kutusu basılı](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 165_CheckboxPressed")|Arka Plan|`CommonControls.CheckBoxBackgroundPressed`|  
|![Onay kutusu basılı](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 165_CheckboxPressed")|Kenarlık|`CommonControls.CheckBoxBorderPressed`|  
|![Onay kutusu basılı](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 165_CheckboxPressed")|Metin|`CommonControls.CheckBoxTextPressed`|  
|![Onay kutusu basılı](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 165_CheckboxPressed")|Glif|`CommonControls.CheckBoxGlyphPressed`|  
  
 **Odaklanmış**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Onay kutusu odaklanmış](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 166_CheckboxFocused")|Arka Plan|`CommonControls.CheckBoxBackgroundFocused`|  
|![Onay kutusu odaklanmış](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 166_CheckboxFocused")|Kenarlık|`CommonControls.CheckBoxBorderFocused`|  
|![Onay kutusu odaklanmış](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 166_CheckboxFocused")|Metin|`CommonControls.CheckBoxTextFocused`|  
|![Onay kutusu odaklanmış](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 166_CheckboxFocused")|Glif|`CommonControls.CheckBoxGlyphFocused`|  
  
#### <a name="drop-boxcombo-box-controls"></a>Açılan kutusu/birleşik giriş kutusu denetimleri  
 ![DROP&#45;aşağı&#47;birleşik giriş kutusu kırmızı çizgi](../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303 167_DropDownComboBoxRedline")  
  
 Kullan...  
 açılan listeler ve birleşik giriş kutuları da belgeyi bir parçası olan.  
  
 Kullanmayın...  
 -   bir açılan veya birleşik giriş kutusu değil herhangi bir UI için.  
  
- için bir [açılan](../misc/shared-colors.md#BKMK_CommandDropDown) veya [birleşik giriş kutusu](../misc/shared-colors.md#BKMK_CommandComboBox) komut çubuğunda.  
  
  **Default**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 168_DropDownComboBox")|Arka Plan|`CommonControls.ComboBoxBackground`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 168_DropDownComboBox")|Kenarlık|`CommonControls.ComboBoxBorder`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 168_DropDownComboBox")|Metin|`CommonControls.ComboBoxText`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 168_DropDownComboBox")|Ayırıcı|`CommonControls.ComboBoxSeparator`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 168_DropDownComboBox")|Glif|`CommonControls.ComboBoxGlyph`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 168_DropDownComboBox")|Simge arka plan|`CommonControls.ComboBoxGlyphBackground`|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu devre dışı](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")|Arka Plan|`CommonControls.ComboBoxBackgroundDisabled`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu devre dışı](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")|Kenarlık|`CommonControls.ComboBoxBorderDisabled`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu devre dışı](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")|Metin|`CommonControls.ComboBoxTextDisabled`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu devre dışı](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")|Ayırıcı|`CommonControls.ComboBoxSeparatorDisabled`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu devre dışı](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")|Glif|`CommonControls.ComboBoxGlyphDisabled`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu devre dışı](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")|Simge arka plan|`CommonControls.ComboBoxGlyphBackgroundDisabled`|  
  
 **Vurgulu**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")|Arka Plan|`CommonControls.ComboBoxBackgroundHover`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")|Kenarlık|`CommonControls.ComboBoxBorderHover`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")|Metin|`CommonControls.ComboBoxTextHover`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")|Ayırıcı|`CommonControls.ComboBoxSeparatorHover`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")|Glif|`CommonControls.ComboBoxGlyphHover`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")|Simge arka plan|`CommonControls.ComboBoxGlyphBackgroundHover`|  
  
 **Basılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![DROP&#45;aşağı&#47;basılı birleşik giriş kutusu](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")|Arka Plan|`CommonControls.ComboBoxBackgroundPressed`|  
|![DROP&#45;aşağı&#47;basılı birleşik giriş kutusu](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")|Kenarlık|`CommonControls.ComboBoxBorderPressed`|  
|![DROP&#45;aşağı&#47;basılı birleşik giriş kutusu](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")|Metin|`CommonControls.ComboBoxTextPressed`|  
|![DROP&#45;aşağı&#47;basılı birleşik giriş kutusu](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")|Ayırıcı|`CommonControls.ComboBoxSeparatorPressed`|  
|![DROP&#45;aşağı&#47;basılı birleşik giriş kutusu](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")|Glif|`CommonControls.ComboBoxGlyphPressed`|  
|![DROP&#45;aşağı&#47;basılı birleşik giriş kutusu](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")|Simge arka plan|`CommonControls.ComboBoxGlyphBackgroundPressed`|  
  
 **Odaklanmış**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![DROP&#45;aşağı&#47;odaklanmış birleşik giriş kutusu](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")|Arka Plan|`CommonControls.ComboBoxBackgroundFocused`|  
|![DROP&#45;aşağı&#47;odaklanmış birleşik giriş kutusu](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")|Kenarlık|`CommonControls.ComboBoxBorderFocused`|  
|![DROP&#45;aşağı&#47;odaklanmış birleşik giriş kutusu](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")|Metin|`CommonControls.ComboBoxTextFocused`|  
|![DROP&#45;aşağı&#47;odaklanmış birleşik giriş kutusu](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")|Ayırıcı|`CommonControls.ComboBoxSeparatorFocused`|  
|![DROP&#45;aşağı&#47;odaklanmış birleşik giriş kutusu](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")|Glif|`CommonControls.ComboBoxGlyphFocused`|  
|![DROP&#45;aşağı&#47;odaklanmış birleşik giriş kutusu](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")|Simge arka plan|`CommonControls.ComboBoxGlyphBackgroundFocused`|  
  
 **Giriş metin seçimi**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu metin girişi](../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303 173_DropDownComboBoxTextInput")|Vurgulayın|`CommonControls.ComboBoxTextInputSelection`|  
  
 **Basılan – liste öğesi görünümü**  
  
|Bileşen|Öğe|Belirteç adı: Color.category|  
|---------------|-------------|--------------------------------|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu liste görünümü](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Arka Plan|`CommonControls.ComboBoxListBackground`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu liste görünümü](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Arka Plan|`CommonControls.ComboBoxListBackgroundHover`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu liste görünümü](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Arka Plan|`CommonControls.ComboBoxListItemBackgroundPressed`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu liste görünümü](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Arka Plan|`CommonControls.ComboBoxListItemBackgroundFocused`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu liste görünümü](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Kenarlık|`CommonControls.ComboBoxListBorder`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu liste görünümü](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Kenarlık|`CommonControls.ComboBoxListBorderHover`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu liste görünümü](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Kenarlık|`CommonControls.ComboBoxListBorderPressed`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu liste görünümü](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Kenarlık|`CommonControls.ComboBoxListBorderFocused`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu liste görünümü](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Öğe metni|`CommonControls.ComboBoxListItemText`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu liste görünümü](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Öğe metni|`CommonControls.ComboBoxListItemTextHover`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu liste görünümü](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Öğe metni|`CommonControls.ComboBoxListItemTextPressed`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu liste görünümü](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Öğe metni|`CommonControls.ComboBoxListItemTextFocused`|  
|![DROP&#45;aşağı&#47;birleşik giriş kutusu liste görünümü](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")|Arka plan gölge|`CommonControls.ComboBoxListBackgroundShadow`|  
  
#### <a name="tabular-data-grid-controls"></a>Tablosal veri (Kılavuz) denetimleri  
 Tablosal veri denetimleri, kılavuz denetimleri olarak da bilinir, yüksek miktarda verilerden oluşan birden çok sütunda sunmak için kullanılan Visual Studio için ortak denetimlerdir. Standart tablo veri denetimleri Visual Studio içinde birden fazla yerde bulunabilir: hata listesi araç penceresi, IntelliTrace raporlar ve diğerlerinin yanı sıra bellek yığın görünümü. Her zaman sağlanan standart tablo veri denetimleri kullanın. Bazı ender durumlarda, standart tablo veri denetimleri erişimi olmayabilir. Bu gibi durumlarda, kullanıcı Arabirimi diğer Visual Studio'da tablosal veri denetimleriyle tutarlı olduğundan emin olmak için aşağıdaki belirteci adları kullanın.  
  
 ![Tablo veri &#40;kılavuz denetimi&#41; kırmızı çizgi](../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303 197_TabularDataGridControlRedline")  
  
 Kullan...  
 için tablo veya kılavuz denetimleri.  
  
 Kullanmayın...  
 bir tablo veya kılavuz denetimi değil herhangi bir UI için.  
  
##### <a name="column-headers"></a>Sütun üstbilgileri  
 Sütun üst bilgilerini arka plan, kenarlık, başlık metnini ve kılavuz, sütuna göre sıralanmış genellikle kullanılan isteğe bağlı bir karakter oluşur.  
  
|Durum|Öğe|Belirteç adı: Category.color|  
|-----------|-------------|--------------------------------|  
|Varsayılan|Arka Plan|`Header.Default`|  
|Varsayılan|Ön plan (metin)|`Environment.CommandBarTextActive`|  
|Varsayılan|Ön plan (karakter)|`Header.Glyph`|  
|Varsayılan|Kenarlık|`Header.SeparatorLine`|  
|Vurgulu|Arka Plan|`Header.MouseOver`|  
|Vurgulu|Ön plan (metin)|`Environment.CommandBarTextHover`|  
|Vurgulu|Ön plan (karakter)|`Header.MouseOverGlyph`|  
|Vurgulu|Kenarlık|`Header.SeparatorLine`|  
|Basılan|Arka Plan|`CommonControls.CheckBoxBackgroundPressed`|  
|Basılan|Ön plan (metin)|`CommonControls.CheckBoxBorderPressed`|  
|Basılan|Ön plan (karakter)|`CommonControls.CheckBoxTextPressed`|  
|Basılan|Kenarlık|`CommonControls.CheckBoxGlyphPressed`|  
  
##### <a name="list-view-items"></a>Liste Görünümü öğelerini  
 Liste Görünümü öğelerini bir arka plan ve içeriği oluşur. İçerik, metin, simge veya her ikisi de olabilir.  
  
|Durum|Öğe|Belirteç adı: Category.color|  
|-----------|-------------|--------------------------------|  
|Varsayılan|Arka Plan|Geçirgen|  
|Varsayılan|Ön plan (metin)|`Environment.CommandBarTextActive`|  
|Varsayılan|Kenarlık|Yok.|  
|Seçili (etkin)|Arka Plan|`TreeView.SelectedItemActive`|  
|Seçili (etkin)|Ön plan (metin)|`TreeView.SelectedItemActiveText`|  
|Seçili (etkin)|Kenarlık|Yok.|  
|Seçili (etkin)|Arka Plan|`TreeView.SelectedItemInactive`|  
|Seçili (etkin)|Ön plan (metin)|`TreeView.SelectedItemInactiveText`|  
|Seçili (etkin)|Kenarlık|Yok.|  
  
### <a name="manifest-designer"></a>Bildirim Tasarımcısı  
 Bildirim Tasarımcısı, Windows 8 ve Windows Phone 8 projeleri bildirim dosyasında düzenlemek daha kolay bir şekilde tasarlanmıştır. Tüketim için kullanılabilir paylaşılan çerçeve ederken tasarım düzeni ve yön/gezinme sekmeleri ve genel yapısı renklerini eşleştirmek için uygun olabilir. Düzen ayrıntıları hakkında daha fazla bilgi için bkz. [Visual Studio için Düzen](../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
 ![Bildirim Tasarımcısı kırmızı çizgi](../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303 175_ManifestDesignerRedline")  
  
 Kullan...  
 -   Bildirim Tasarımcısı için benzer tasarımcıları.  
  
- bir düzenleyici belgesi içinde üst kısmındaki ortak sekme denetimleri kullanarak yerine yanı sıra.  
  
  Kullanmayın...  
  -   altıdan fazla sekme varsa.  
  
- Bildirim Tasarımcısı gibi yapılandırılmamış herhangi bir UI için.  
  
|Durum|Bileşen|Öğe|Belirteç adı: Category.color|  
|-----------|---------------|-------------|--------------------------------|  
|Varsayılan (Seçili)|Tab|Arka Plan|`ManifestDesigner.TabActive`|  
|Varsayılan (Seçili)|Tab|Kenarlık|Yok.|  
|Varsayılan (Seçili)|Açıklama bölmesi|Arka Plan|`ManifestDesigner.DescriptionPane`|  
|Varsayılan (Seçili)|İçerik sayfası|Arka Plan|`ManifestDesigner.Background`|  
|Varsayılan (Seçili)|İçerik sayfası|İletişim yardımcı metni|`ManifestDesigner.WatermarkText`<br /><br /> Bu belirteç adı işlevini eşleşmiyor.|  
|Olmayan seçili|Tab|Arka Plan|`ManifestDesigner.Tab.Inactive`|  
|Vurgulu|Tab|Arka Plan|`ManifestDesigner.Tab.Mouseover`|  
  
### <a name="tagging"></a>Etiketleme  
 Visual Studio etiketleme, izleme amacıyla aranabilir anahtar sözcükleri bildirmek bir kullanıcı sağlayan destekler. Örneğin, proje yöneticileri ve geliştiriciler Team Foundation Server (TFS) iş öğelerini etiketlemek için kullanabilirsiniz. Aşağıdaki tablolarda, etiket hem üzerine gelin ve seçili durumlardan görünür "simge" Kapat"karakteri için renk adlar verin.  
  
 ![Etiketleme kırmızı çizgi](../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303 176_TaggingRedline")  
  
 Kullan...  
 Kullanıcı Arabirimi için etiketleme destekleyen.  
  
 Kullanmayın...  
 başka türde UI için.  
  
#### <a name="tag"></a>Etiket  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Etiket](../extensibility/ux-guidelines/media/0303-177-tag.png "0303 177_Tag")<br /><br /> **Default**|Arka Plan|`Tag.Background`|  
|![Etiket](../extensibility/ux-guidelines/media/0303-177-tag.png "0303 177_Tag")<br /><br /> **Default**|Ön plan (metin)|`Tag.Background`|  
|![Üzerine gelindiğinde etiketi](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303 178_TagHover")<br /><br /> **Vurgulu**|Arka Plan|`Tag.HoverBackground`|  
|![Üzerine gelindiğinde etiketi](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303 178_TagHover")<br /><br /> **Vurgulu**|Ön plan (metin)|`Tag.HoverBackgroundText`|  
|![Basılan etiketi](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303 179_TagPressed")<br /><br /> **Basılan**|Arka Plan|`Tag.PressedBackground`|  
|![Basılan etiketi](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303 179_TagPressed")<br /><br /> **Basılan**|Ön plan (metin)|`Tag.PressedBackgroundText`|  
|![Seçili etiketi](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303 180_TagSelected")<br /><br /> **Seçili**|Arka Plan|`Tag.SelectedBackground`|  
|![Seçili etiketi](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303 180_TagSelected")<br /><br /> **Seçili**|Ön plan (metin)|`Tag.SelectedBackgroundText`|  
  
#### <a name="glyph-close-icon"></a>Glif (Kapat simgesi)  
 **Default**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Etiket &#40;glif&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303 181_TagGlyph")<br /><br /> **Varsayılan (etiketi varsayılan)**|Arka Plan|Yok|  
|![Etiket &#40;glif&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303 181_TagGlyph")<br /><br /> **Varsayılan (etiketi varsayılan)**|Ön plan (karakter)|`Tag.TagHoverGlyph`|  
  
 **Vurgulu**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Etiket &#40;glif&#41; üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 182_TagGlyphHover")<br /><br /> **Vurgulu (etiketi varsayılan)**|Arka Plan|`Tag.TagHoverGlyphHoverBackground`|  
|![Etiket &#40;glif&#41; üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 182_TagGlyphHover")<br /><br /> **Vurgulu (etiketi varsayılan)**|Ön plan (karakter)|`Tag.TagHoverGlyphHover`|  
|![Etiket &#40;glif&#41; üzerine gelindiğinde](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 182_TagGlyphHover")<br /><br /> **Vurgulu (etiketi varsayılan)**|Kenarlık|`Tag.TagHoverGlyphHoverBorder`|  
  
 **Basılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Etiket &#40;glif&#41; basılı](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 183_TagGlyphPressed")<br /><br /> **Basılan (etiketi varsayılan)**|Arka Plan|`Tag.TagHoverGlyphPressedBackground`|  
|![Etiket &#40;glif&#41; basılı](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 183_TagGlyphPressed")<br /><br /> **Basılan (etiketi varsayılan)**|Ön plan (karakter)|`Tag.TagHoverGlyphPressed`|  
|![Etiket &#40;glif&#41; basılı](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 183_TagGlyphPressed")<br /><br /> **Basılan (etiketi varsayılan)**|Kenarlık|`Tag.TagHoverGlyphPressedBorder`|  
  
 **Seçili simge varsayılan etiket**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Seçili etiketi](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303 184_TagSelected")<br /><br /> **Varsayılan (Seçili etiketi)**|Arka Plan|Yok|  
|![Seçili etiketi](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303 184_TagSelected")<br /><br /> **Varsayılan (Seçili etiketi)**|Ön plan (karakter)|`Tag.TagSelectedGlyph`|  
  
 **Etiket seçili simge üzerine gelme**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Üzerine gelindiğinde seçili etiketi](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 185_TagSelectedHover")<br /><br /> **Vurgulu (Seçili etiketi)**|Arka Plan|`Tag.TagSelectedGlyphHoverBackground`|  
|![Üzerine gelindiğinde seçili etiketi](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 185_TagSelectedHover")<br /><br /> **Vurgulu (Seçili etiketi)**|Ön plan (karakter)|`Tag.TagSelectedGlyphHover`|  
|![Üzerine gelindiğinde seçili etiketi](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 185_TagSelectedHover")<br /><br /> **Vurgulu (Seçili etiketi)**|Kenarlık|`Tag.TagSelectedGlyphHoverBorder`|  
  
 **Etiket seçili/basılı karakteri**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Seçili etiketi basılı](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 186_TagSelectedPressed")<br /><br /> **(Basılı etiketi seçili)**|Arka Plan|`Tag.TagSelectedGlyphPressedBackground`|  
|![Seçili etiketi basılı](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 186_TagSelectedPressed")<br /><br /> **(Basılı etiketi seçili)**|Foreground(glyph)|`Tag.TagSelectedGlyphPressed`|  
|![Seçili etiketi basılı](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 186_TagSelectedPressed")<br /><br /> **(Basılı etiketi seçili)**|Kenarlık|`Tag.TagSelectedGlyphPressedBorder`|  
  
### <a name="shell"></a>Kabuk  
  
#### <a name="background"></a>Arka Plan  
 Ortam arka plan iki katmandan oluşur. Tüm IDE kapsayan düz renk alt katmanıdır. Üst katman komut raf altında ve araç penceresi otomatik gizleme kanalları IDE'nin sol ve sağ kenarları arasındaki uyar. Visual Studio 2013'ten itibaren aynı açık ve koyu Tema rengi için üst ve alt arka plan katmanlarının ayarlanır.  
  
 ![Kabuk arka plan kırmızı çizgi](../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303 187_ShellBackgroundRedline")  
  
 Kullan...  
 Visual Studio ortamının arka eşleştirmek istediğiniz yerde.  
  
 Kullanmayın...  
 -   arka plan yüzeyleri olmayan basamak için dolgu olarak.  
  
-   ön plan öğeleri yerleştirmek istediğiniz arka plan olarak.  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|Alt Katman|Arka Plan|`Environment.EnvironmentBackground`|  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|Üst katman|Arka Plan<br /><br /> *Visual Studio 2013'ün açık ve koyu temaları aynı renk değeri kümesine gradyan durdurur.*|`Environment.EnvironmentBackgroundGradientBegin`|  
|Üst katman|Arka Plan<br /><br /> *Visual Studio 2013'ün açık ve koyu temaları aynı renk değeri kümesine gradyan durdurur.*|`Environment.EnvironmentBackgroundGradientEnd`|  
|Üst katman|Arka Plan<br /><br /> *Visual Studio 2013'ün açık ve koyu temaları aynı renk değeri kümesine gradyan durdurur.*|`Environment.EnvironmentBackgroundGradientMiddle1`|  
|Üst katman|Arka Plan<br /><br /> *Visual Studio 2013'ün açık ve koyu temaları aynı renk değeri kümesine gradyan durdurur.*|`Environment.EnvironmentBackgroundGradientMiddle2`|  
  
#### <a name="command-shelf"></a>Komut raf  
 İki simge adları, komut raf planları kullanılır: menü çubuğu burada yer alan, biri burada komut çubukları sit ayarlayın. Bir tek tek komut çubuğu grubu "Komut çubuğunda" bölümünde daha ayrıntılı olarak ele alınmıştır, kendi arka plan renk değerleri var. Menü çubuğu ve komut çubuğundan metin sırasıyla menü ve komut çubuğu bölümlerinde ele alınmıştır.  
  
 ![Komut raf kırmızı çizgi](../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303 188_CommandShelfRedline")  
  
 Kullan...  
 -   menüleri ve araç çubukları yerleştirdiğiniz alanları.  
  
- doğru arka plan / ön plan belirteç adı birleşimi.  
  
  Kullanmayın...  
  bir komut raf için benzer olmayan alanları.  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|Menü çubuğu|Arka Plan<br /><br /> *Visual Studio 2013'ün açık ve koyu temaları aynı renk değeri kümesine gradyan durdurur.*|`Environment.CommandShelfHighlightGradientBegin`|  
|Menü çubuğu|Arka Plan<br /><br /> *Visual Studio 2013'ün açık ve koyu temaları aynı renk değeri kümesine gradyan durdurur.*|`Environment.CommandShelfHighlightGradientMiddle`|  
|Menü çubuğu|Arka Plan<br /><br /> *Visual Studio 2013'ün açık ve koyu temaları aynı renk değeri kümesine gradyan durdurur.*|`Environment.CommandShelfHighlightGradientEnd`|  
|Komut çubuğu|Arka Plan<br /><br /> *Visual Studio 2013'ün açık ve koyu temaları aynı renk değeri kümesine gradyan durdurur.*|`Environment.CommandShelfBackgroundGradientBegin`|  
|Komut çubuğu|Arka Plan<br /><br /> *Visual Studio 2013'ün açık ve koyu temaları aynı renk değeri kümesine gradyan durdurur.*|`Environment.CommandShelfBackgroundGradientMiddle`|  
|Komut çubuğu|Arka Plan<br /><br /> *Visual Studio 2013'ün açık ve koyu temaları aynı renk değeri kümesine gradyan durdurur.*|`Environment.CommandShelfBackgroundGradientEnd`|  
  
### <a name="toolbox"></a>Araç Kutusu  
 Araç, Visual Studio'daki sık kullanılan ortak bir araç pencereleri biridir. Aslında bir ağaç denetimi ile özel teması ve stil uygulanmış olduğu.  
  
 ![Araç kutusu kırmızı çizgi](../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303 189_ToolboxRedline")  
  
 Kullan...  
 ne zaman, her zaman shell araç ile tutarlı olmasını istediğiniz araç penceresi tasarlarken.  
  
 Kullanmayın...  
 Araç kutusu kullanıcı Arabirimi, benzer olmayan her şey için ya da değişiklik shell araç kutusuna renklerini, kullanıcı Arabirimi sorunları olup olmadığını olacak emin değilseniz.  
  
 **Default**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Araç kutusu üst düğümü](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 190_ToolboxParentNode")<br /><br /> **Üst düğümü**|Arka Plan|`Environment.ToolboxContent`<br /><br /> Başlıkları<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Bireysel öğeleri veya hiçbir kullanılabilir denetimleri, tüm pencere|  
|![Araç kutusu alt düğüm](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 191_ToolboxChildNode")<br /><br /> **Alt düğümü**|Arka Plan|`Environment.ToolboxContent`<br /><br /> Başlıkları<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Bireysel öğeleri veya hiçbir kullanılabilir denetimleri, tüm pencere|  
|![Araç kutusu üst düğümü](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 190_ToolboxParentNode")<br /><br /> **Üst düğümü**|Kenarlık|Yok.|  
|![Araç kutusu alt düğüm](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 191_ToolboxChildNode")<br /><br /> **Alt düğümü**|Kenarlık|Yok.|  
|![Araç kutusu üst düğümü](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 190_ToolboxParentNode")<br /><br /> **Üst düğümü**|Ön plan (karakter)|`Environment.ToolboxContent`|  
|![Araç kutusu alt düğüm](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 191_ToolboxChildNode")<br /><br /> **Alt düğümü**|Ön plan (karakter)|`Environment.ToolboxContent`|  
|![Araç kutusu üst düğümü](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 190_ToolboxParentNode")<br /><br /> **Üst düğümü**|Ön plan (metin)|`Environment.ToolboxContent`|  
|![Araç kutusu alt düğüm](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 191_ToolboxChildNode")<br /><br /> **Alt düğümü**|Ön plan (metin)|`Environment.ToolboxContent`|  
  
 **Vurgulu**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Üzerine gelindiğinde Araç kutusu alt düğüm](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")<br /><br /> **Alt düğümü üzerine gelindiğinde Araç kutusu**|Arka Plan|`Environment.ToolboxContentMouseOver`<br /><br /> Yalnızca tek tek öğeleri|  
|![Üzerine gelindiğinde Araç kutusu alt düğüm](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")<br /><br /> **Alt düğümü üzerine gelindiğinde Araç kutusu**|Kenarlık|Yok.|  
|![Üzerine gelindiğinde Araç kutusu alt düğüm](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")<br /><br /> **Alt düğümü üzerine gelindiğinde Araç kutusu**|Ön plan (metin)|`Environment.ToolboxContentMouseOver`<br /><br /> Yalnızca tek tek öğeleri|  
  
 **Seçili**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Araç kutusu üst düğümü odaklanmış](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")<br /><br /> **Odaklanmış üst düğümü**|Arka Plan|`TreeView.SelectedItemActive`<br /><br /> Gelen [ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisi|  
|![Araç kutusu alt düğüm odaklanmış](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")<br /><br /> **Odaklanmış alt düğümü**|Arka Plan|`TreeView.SelectedItemActive`<br /><br /> Gelen [ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisi|  
|![Araç kutusu üst düğümü odaklanmış](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")<br /><br /> **Odaklanmış üst düğümü**|Kenarlık|`TreeView.FocusVisualBorder`<br /><br /> Gelen [ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisi|  
|![Araç kutusu alt düğüm odaklanmış](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")<br /><br /> **Odaklanmış alt düğümü**|Kenarlık|`TreeView.FocusVisualBorder`<br /><br /> Gelen [ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisi|  
|![Araç kutusu üst düğümü odaklanmış](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")<br /><br /> **Odaklanmış üst düğümü**|Ön plan (karakter)|`TreeView.SelectedItemActive`<br /><br /> Gelen [ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisi|  
|![Araç kutusu alt düğüm odaklanmış](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")<br /><br /> **Odaklanmış alt düğümü**|Ön plan (karakter)|`TreeView.SelectedItemActive`<br /><br /> Gelen [ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisi|  
|![Araç kutusu üst düğümü odaklanmış](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")<br /><br /> **Odaklanmış üst düğümü**|Ön plan (metin)|`TreeView.SelectedItemActive`<br /><br /> Gelen [ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisi|  
|![Araç kutusu alt düğüm odaklanmış](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")<br /><br /> **Odaklanmış alt düğümü**|Ön plan (metin)|`TreeView.SelectedItemActive`<br /><br /> Gelen [ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisi|  
|![Araç kutusu üst düğümü odaklanmadan](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")<br /><br /> **Plana odaklanmadan üst düğümü**|Arka Plan|`TreeView.SelectedItemInactive`<br /><br /> Gelen [ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisi|  
|![Araç kutusu alt düğüm odaklanmadan](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")<br /><br /> **Plana odaklanmadan alt düğümü**|Arka Plan|`TreeView.SelectedItemInactive`<br /><br /> Gelen [ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisi|  
|![Araç kutusu üst düğümü odaklanmadan](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")<br /><br /> **Plana odaklanmadan üst düğümü**|Kenarlık|Yok.|  
|![Araç kutusu alt düğüm odaklanmadan](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")<br /><br /> **Plana odaklanmadan alt düğümü**|Kenarlık|Yok.|  
|![Araç kutusu üst düğümü odaklanmadan](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")<br /><br /> **Plana odaklanmadan üst düğümü**|Ön plan (karakter)|`TreeView.SelectedItemInactive`<br /><br /> Gelen [ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisi|  
|![Araç kutusu alt düğüm odaklanmadan](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")<br /><br /> **Plana odaklanmadan alt düğümü**|Ön plan (karakter)|`TreeView.SelectedItemInactive`<br /><br /> Gelen [ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisi|  
|![Araç kutusu üst düğümü odaklanmadan](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")<br /><br /> **Plana odaklanmadan üst düğümü**|Ön plan (metin)|`TreeView.SelectedItemInactive`<br /><br /> Gelen [ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisi|  
|![Araç kutusu alt düğüm odaklanmadan](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")<br /><br /> **Plana odaklanmadan alt düğümü**|Ön plan (metin)|`TreeView.SelectedItemInactive`<br /><br /> Gelen [ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisi|  
  
## <a name="color-value-reference"></a>Renk değeri başvurusu  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
|Bileşen|Bölümü|Öğe|Durum|Açık|Koyu|Mavi|Yüksek Karşıtlık|  
|Bölücü satırları|||Varsayılan|FFEEEEF2|FF2D2D30|FFEEEEF2|ControlDark|  
|Glif Genişleticisi||Ön plan|Varsayılan|||||  
|Glif Genişleticisi||Ön plan|Vurgulu|||||  
|Glif Genişleticisi||Arka Plan|Varsayılan|||||  
|Glif Genişleticisi||Arka Plan|Vurgulu|||||  
|Glif Genişleticisi||Kenarlık|Varsayılan|||||  
|Glif Genişleticisi||Kenarlık|Vurgulu|||||