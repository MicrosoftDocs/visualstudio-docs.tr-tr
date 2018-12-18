---
title: Paylaşılan Renkler
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 03cfcf2b4ea2b3a0b4773e9c2632c84091819f45
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063227"
---
# <a name="shared-colors-for-visual-studio"></a>Visual Studio için paylaşılan renkler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ortak Visual Studio shell öğeleri kullanan kullanıcı Arabirimi tasarlarken veya arabirimi öğeniz benzer özellikleri ile tutarlı olmasını istediğiniz, mevcut belirteç adları paket tanımı dosyaları seçin ve renkleri atamak için kullanın. Bu tema eklendiğinde veya güncelleştirildiğinde, otomatik olarak güncelleştirir ve kullanıcı Arabirimi ile genel Visual Studio ortamının tutarlı kalmasını sağlar.

 Bu makalede, sık kullanılan UI öğeleri ve benzer kullanıcı Arabirimi oluşturma sırasında başvuran kullandıkları, belirteç adlarını açıklanır. Bu renk belirteçleri erişim hakkında ayrıntılı bilgi için bkz: [VSColor hizmet](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

 Doğru belirteci adları kullandığınızdan emin olun:

-   **İşlevi, renk üzerinde dayalı belirteç adları kullanın.** Ortak paylaşılan renkler, belirli bir arabirim öğeleri ile ilişkili ve yalnızca aynı veya benzer özellikler için kullanılmak üzere tasarlanmıştır. Örneğin, dönen ilerleme animasyonunun basılı açılan kutusu rengi renk istediğiniz olduğundan yeniden kullanmayın. Birleşik giriş kutusu ve animasyon işlevleri farklıdır ve renk birleşik giriş kutusu değişikliklerle ilişkili, artık animasyon öğeniz için uygun bir renk olabilir. Renk tutarlı kullanımı, kullanıcılarınızın yönlendirmek ve Karışıklığı önlemek yardımcı olur.

-   **Arka plan ve metin renklerini doğru birlikte kullanın.** Metin ile kullanılmaya yönelik arka plan renklerini, ilişkili metin rengi sahip olur. Metin renkler, arka plan bilgileri için belirtilen dışında kullanmayın. İlişkili metin rengi değilse, arka plan rengi metni görüntülemek beklediğiniz tüm yüzeyi için kullanmayın. Diğer metin ve arkaplan renklerini birleşimlerini okunamayan bir arabirimde neden olabilir.

-   **Konumlarına için uygun olan denetim renkleri kullanın.** Bazı durumlarda, bazı Visual Studio denetimler ayrı kenarlık ve arka plan renkleri yoktur. Bunun yerine, bu yüzeyleri arkasına renkleri ayarlama seçin. Her zaman burada denetimin yerleştirme konumu için uygun olan belirteci adları kullandığınızdan emin olun.

> [!IMPORTANT]
>  "Başlangıç sayfası" veya "Şarabıı." kategoride bulunan belirteçleri kullanmayın

## <a name="command-structures"></a>Komut yapıları

###  <a name="BKMK_CommandMenus"></a> Menüler
 Menüleri, Visual Studio içinde çeşitli yerlerde oluşabilir: belge veya araç pencerelerini veya IDE tamamında çeşitli konumlarda sağ katıştırılmış ana menü çubuğu. Menü diğer UI öğeleri ile ilişkili uygulamalar için ilgili öğenin bölümünde ele alınmıştır. Visual Studio ortamı tarafından sağlanan standart menü uygulama her zaman kullanmalısınız. Ancak, bazı ender durumlarda, standart bir Visual Studio menülerinin erişimi olmayabilir. Bu gibi durumlarda, kullanıcı Arabirimi diğer Visual Studio menülerinde ile tutarlı olmasını sağlamak için aşağıdaki belirteci adları kullanın.

 ![Menüler kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303 000_MenuRedline")

 Kullan...
 -   herhangi bir zamanda, özel bir menü oluşturmanız gerekir.

- Visual Studio menülerinin eşleştirmek istediğiniz yeni bir kullanıcı Arabirimi bileşeninin olduğunda.

  Kullanmayın...
  tek başına arka plan rengi. Her zaman arka plan/ön plan birlikte belirtilen kullanın.

#### <a name="menu-title"></a>Menü başlığı
 Genellikle bir Komut çubuğuna menü bulunduğunda menü başlığı arka plan, kenarlık ve başlık metnini yanı isteğe bağlı bir karakter oluşur.

 ![Menü başlığı kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303 001_MenuTitleRedline")

 Kullan...
Her bir özel menü başlığı oluşturuyorsunuz.

 Kullanmayın...
 -   her şey için her zaman istemediğiniz menü başlığının eşleştirin.

- Belirtilen dışındaki tüm arka plan/ön plan arada.

  **Default**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Menü başlığı varsayılan](../../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303 002_MenuTitleDefault")

  **Menü başlığı**

  Arka Plan

  Yok.

  Ön plan (metin)

  `Environment.CommandBarTextActive`

  ![Menü başlığı glif varsayılan](../../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303 003_MenuTitleWithGlyphDefault")

  **Menü başlığı karakter ile**

  Ön plan (karakter)

  `Environment.CommandBarMenuGlyph`

  Kenarlık

  Yok.

  **Vurgulu**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Menü başlığı üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303 004_MenuTitleHover")

  **Menü başlığı**

  Arka Plan

  `Environment.CommandBarMouseOverBackgroundBegin`

  Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

  Ön plan (metin)

  `Environment.CommandBarTextHover`

  ![Menü başlığı ile üzerine gelindiğinde glif](../../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303 005_MenuTitleWithGlyphHover")

  **Menü başlığı karakter ile**

  Ön plan (karakter)

  `Environment.CommandBarMenuMouseOverGlyph`

  Kenarlık

  `Environment.CommandBarBorder`

  **Basılan**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Menü başlığı basılı](../../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303 006_MenuTitlePressed")

  **Menü başlığı**

  Arka Plan

  `Environment.CommandBarMenuBackgroundGradientBegin`

  Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

  Ön plan (metin)

  `Environment.CommandBarTextActive`

  ![Menü başlığı basılı karakteri ile](../../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303 007_MenuTitleWithGlyphPressed")

  **Menü başlığı karakter ile**

  Ön plan (karakter)

  `Environment.CommandBarMenuMouseDownGlyph`

  Kenarlık

  `Environment.CommandBarMenuBorder`

  Yalnızca sol, üst ve sağ.

  **Devre dışı**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Menü başlığı devre dışı karakter ile](../../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")

  **Menü başlığı karakter ile**

  Arka Plan

  Yok.

  Ön plan (metin)

  `Environment.CommandBarTextInactive`

  Ön plan (karakter)

  `Environment.CommandBarTextInactive`

  Kenarlık

  Yok.

#### <a name="menu"></a>Menü
 Bir tek menü öğesinin menü metnini ve bir isteğe bağlı simge, onay kutusu veya alt simge oluşur. Arka plan ve metin rengi değişiklik üzerine gelindiğinde. Bu renk belirteci, bir arka plan/ön plan çiftidir.

 ![Menü öğelerini kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303 009_MenuItemRedline")

 Kullan...
herhangi bir aşağı açılan listesi için menü çubuğunun ya da komut çubuğu başlatılır.

 Kullanmayın...
 -   herhangi bir aşağı açılan listeyi, başka bir bağlamda gerçekleşir.

- Belirtilen dışındaki tüm arka plan/ön plan arada.

  **Default**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Menü varsayılan](../../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")

  **Menü**

  Arka Plan

  `Environment.CommandBarMenuBackgroundGradientBegin`

  Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

  Ön plan (metin)

  `Environment.CommandBarTextActive`

  Ön plan (alt karakter)

  `Environment.CommandBarMenuSubmenuGlyph`

  Kenarlık

  `Environment.CommandBarMenuBorder`

  Simge kanal arka planı

  `Environment.CommandBarMenuIconBackground`

  Ayırıcı

  `Environment.CommandBarMenuSeparator`

  Gölge

  `Environment.DropShadowBackground`

  ![İşaretli menü](../../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303 011_MenuChecked")

  **İşaretli**

  Onay işareti

  `Environment.CommandBarCheckBox`

  Onay işareti arka plan

  `Environment.CommandBarSelectedIcon`

  ![Seçili menü](../../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303 012_MenuSelected")

  **Seçili**

  Simge arka planı

  `Environment.CommandBarSelected`

  Simge kenarlık

  `Environment.CommandBarSelectedBorder`

  **Vurgulu**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Menü vurgulu](../../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 013_MenuHover")

  **Menü öğesi**

  Arka Plan

  `Environment.CommandBarMenuItemMouseOver`

  Ön plan (metin)

  `Environment.CommandBarMenuItemMouseOver`

  Ön plan (alt karakter)

  `Environment.CommandBarMenuMouseOverSubmenuGlyph`

  ![İşaretli menü vurgulu](../../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303 014_MenuHoverChecked")

  **İşaretli**

  Onay işareti

  `Environment.CommandBarCheckBoxMouseOver`

  Onay işareti arka plan

  `Environment.CommandBarHoverOverSelectedIcon`

  ![Seçili menü vurgulu](../../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303 015_MenuHoverSelected")

  **Seçili**

  Simge arka planı

  `Environment.CommandBarHoverOverSelected`

  Simge kenarlık

  `Environment.CommandBarHoverOverSelectedIconBorder`

  **Devre dışı**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Devre dışı menü](../../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303 016_MenuDisabled")

  Menü öğesi

  Ön plan (metin)

  `Environment.CommandBarTextInactive`

  Ön plan (alt karakter)

  `Environment.CommandBarMenuSubmenuGlyph`

  ![Menü devre dışı işaretli](../../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303 017_MenuDisabledChecked")

  İşaretli

  Onay işareti

  `Environment.CommandBarCheckBoxDisabled`

  Onay işareti arka plan

  `Environment.CommandBarSelectedIconDisabled`

### <a name="command-bar"></a>Komut çubuğu
 Komut çubuğunda, birden fazla yerde Visual Studio IDE içinde komut raf ve katıştırılmış araç veya belge pencereleri özellikle görünebilir.

 Genel olarak, Visual Studio ortamı tarafından sağlanan standart komut çubuğu uygulaması her zaman kullanın. Standart mekanizmasını kullanarak tüm görsel Ayrıntılar doğru görünür ve etkileşimli öğeleri davrandığını tutarlı bir şekilde ile diğer Visual Studio komut çubuğu denetimleri sağlar. Ancak, kendi komut çubuğu oluşturmak için gerekli değilse, doğru aşağıdaki belirteci adları kullanarak stil emin olun.

 ![Komut çubuğu kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303 018_CommandBarRedline")

 ![Taşma düğmesi kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303 019_OverflowButtonRedline")

 Kullan...
Katıştırılmış bir komut için gerek duyduğunuz yerde çubuğu ancak standart bir Visual Studio komut çubuğu uygulaması kullanamaz.

 Kullanmayın...
 -   Kullanıcı Arabirimi öğeleri için Komut çubuğuna benzer değildir.

-   belirteç adları dışında olduğu için istediklerinizi belirtilen komut çubuğu bileşenleri için.

#### <a name="command-bar-group"></a>Komut çubuğu grubu
 Bir komut çubuğu grubuyla ilgili bir komut çubuğu denetimleri kümesinden oluşur ve herhangi bir sayıda düğmeler, aşağı açılan menüler, birleşik giriş kutuları veya menüler Bölünmüş düğme içerebilir. Bu denetimler için renkleri ayrı belirteci adlarına göre düzenlenen ve ayrı olarak başka bir yerde bu kılavuzda ele alınmıştır. Ayırıcı çizginin bir komut çubuğu grubuyla ilgili alt gruplar ayırmak için kullanılır.

 ![Komut çubuğu grubu kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303 020_CommandBarGroupRedline")

 Kullan...
Katıştırılmış bir komut için gerek duyduğunuz yerde çubuğu ancak standart bir Visual Studio komut çubuğu uygulaması kullanamaz.

 Kullanmayın...
 -   Kullanıcı Arabirimi öğeleri için Komut çubuğuna benzer değildir.

- belirteç adları dışında olduğu için istediklerinizi belirtilen komut çubuğu bileşenleri için.

  **Varsayılan** (başka hiçbir durum)

  Öğe

  Belirteç adı: Category.color

  Arka Plan

  `Environment.CommandBarGradientBegin`

  Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

  Kenarlık

  `Environment.CommandBarToolBarBorder`

  Sürükleme tutamacı

  `Environment.CommandBarDragHandle`

  Ayırıcı

  `Environment.CommandBarToolBarSeparator`

  `Environment.CommandBarToolBarSeparatorHighlight`

#### <a name="command-icons"></a>Komut simgeleri
 ![Komut simgesi kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303 021_CommandIconRedline1")

 ![Komut simgesi kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303 022_CommandIconRedline2")

 Kullan...
düğmeleri için komut çubuğunda yer alır.

 Kullanmayın...
 -   denetimler için belirteç adlarına sahip.

- Belirtilen dışındaki tüm arka plan/ön plan arada.

  **Default**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Komut simgesinin varsayılan](../../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 023_CommandIconDefault")

  **Default**

  Arka Plan

  Yok (komut çubuğu arka planından devralır)

  Ön plan (metin)

  `Environment.CommandBarTextActive`

  Kenarlık

  Yok

  ![Komut simgesinin varsayılan seçili](../../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")

  **Seçili**

  Arka Plan

  `Environment.CommandBarSelected`

  Ön plan (metin)

  `Environment.CommandBarTextSelected`

  Kenarlık

  `Environment.CommandBarSelectedBorder`

  **Hover ve klavye odaklı**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Komut simgesinin üzerine gelindiğinde kullanılacak](../../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 025_CommandIconHover")

  **Üzerine gelindiğinde standart**

  Arka Plan

  `Environment.CommandBarMouseOverBackgroundBegin`

  Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

  Ön plan (metin)

  `Environment.CommandBarTextHover`

  Kenarlık

  `Environment.CommandBarBorder`

  ![Komut simgesinin üzerine gelindiğinde kullanılacak seçili](../../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 026_CommandIconHoverSelected")

  **Üzerine gelindiğinde seçili**

  Arka Plan

  `Environment.CommandBarHoverOverSelected`

  Ön plan (metin)

  `Environment.CommandBarTextHoverOverSelected`

  Kenarlık

  `Environment.CommandBarHoverOverSelectedIconBorder`

  **Basılan**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Komut simgesinin basılı](../../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 027_CommandIconPressed")

  **Basılan komut simgesi**

  Arka Plan

  `Environment.CommandBarMouseDownBackgroundBegin`

  Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

  Ön plan (metin)

  `Environment.CommandBarTextMouseDown`

  Kenarlık

  `Environment.CommandBarBorder`

  **Devre dışı**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Komut simgesinin devre dışı](../../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 028_CommandIconDisabled")

  **Devre dışı bir komut simgesi**

  Arka Plan

  Yok (komut çubuğu arka planından devralır)

  Ön plan (metin)

  `Environment.CommandBarTextInactive`

  Kenarlık

  Yok

####  <a name="BKMK_CommandComboBox"></a> Birleşik giriş kutusu

> [!IMPORTANT]
>  Birleşik giriş kutuları, açılan listeler için benzerdir, ancak düzenlenebilir metin bölge. Düzenlenebilir metin bölge, açılan içermez, altında bulunan renk belirteçleri kullanın. [açılan](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

 ![Birleşik giriş kutusu kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303 029_ComboBoxRedline")

 Kullan...
 -   özel bir birleşik giriş kutuları oluştururken.

- bir birleşik giriş kutusuna benzeyen bir komut çubuğu denetimini oluştururken.

  Kullanmayın...
  -   her şey için her zaman komut eşleştirilecek istemediğiniz çubuğu kullanıcı Arabirimi.

- erişim için bir stil uygulanmış bir birleşik giriş kutusu olduğunda.

  **Default**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Birleşik giriş kutusu giriş alanı](../../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 030_ComboBoxInputField")

  **Giriş alanı**

  Arka Plan

  `Environment.ComboBoxBackground`

  Ön plan (metin)

  `Environment.ComboBoxText`

  Kenarlık

  `Environment.ComboBoxBorder`

  Ayırıcı

  Hiçbir ayırıcısı

  ![Açılan birleşik giriş kutusu&#45;Kapat düğmesi](../../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303 031_ComboBoxDropdownButton")

  **Aşağı açılan düğmesi**

  Arka Plan

  Yok (devralınan)

  Ön plan (karakter)

  `Environment.ComboBoxGlyph`

  ![Birleşik giriş kutusu&#47;bırak&#45;açılan listesinde](../../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 032_ComboBoxDropdownList")

  **Aşağı açılan listesi**

  Arka Plan

  `Environment.ComboBoxPopupBackgroundBegin`

  Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

  Ön plan (metin)

  `Environment.ComboBoxItemText`

  Kenarlık

  `Environment.ComboBoxPopupBorder`

  **Vurgulu**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Birleşik giriş kutusu giriş alanı üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")

  **Giriş alanı**

  Arka Plan

  `Environment.ComboBoxMouseOverBackgroundBegin`

  Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

  Ön plan (metin)

  `Environment.ComboBoxMouseOverText`

  Kenarlık

  `Environment.ComboBoxMouseOverBorder`

  Ayırıcı

  `Environment.ComboBoxMouseOverSeparator`

  ![Birleşik giriş kutusu&#47;bırak&#45;Kapat düğmesi üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303 034_ComboBoxDropdownButtonHover")

  **Aşağı açılan düğmesi**

  Arka Plan

  `Environment.ComboBoxButtonMouseOverBackground`

  Ön plan (karakter)

  `Environment.ComboBoxMouseOverGlyph`

  ![Birleşik giriş kutusu&#47;bırak&#45;açılan listesinde üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")

  **Aşağı açılan listesi**

  Arka plan (menü öğesi)

  `Environment.ComboBoxItemMouseOverBackground`

  Ön plan (metin)

  `Environment.ComboBoxItemMouseOverText`

  Kenarlık (menü öğesi)

  `Environment.ComboBoxItemMouseOverBorder`

  **Odaklanmış**

  Bileşen

  Öğe

  Belirteç adı: Color.category

  ![Birleşik giriş kutusu giriş alanı odaklanmış](../../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")

  **Giriş alanı**

  Arka Plan

  `Environment.ComboBoxFocusedBackground`

  Ön plan (metin)

  `Environment.ComboBoxFocusedText`

  Kenarlık

  `Environment.ComboBoxFocusedBorder`

  Ayırıcı

  `Environment.ComboBoxFocusedButtonSeparator`

  ![Birleşik giriş kutusu&#47;bırak&#45;odaklanmış düğmesini basılı](../../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303 037_ComboBoxDropdownButtonFocused")

  **Aşağı açılan düğmesi**

  Arka Plan

  `Environment.ComboBoxFocusedButtonBackground`

  Ön plan (karakter)

  `Environment.ComboBoxFocusedGlyph`

  **Basılan**

  Bileşen

  Öğe

  Belirteç adı: Color.category

  ![Birleşik giriş kutusu giriş alanı basılı](../../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")

  **Giriş alanı**

  Arka Plan

  `Environment.ComboBoxMouseDownBackground`

  Ön plan (metin)

  `Environment.ComboBoxMouseDownText`

  Kenarlık

  `Environment.ComboBoxMouseDownBorder`

  Ayırıcı

  `Environment.ComboBoxMouseDownSeparator`

  ![Birleşik giriş kutusu&#47;bırak&#45;düğmeye basıldığını aşağı](../../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303 039_ComboBoxDropdownButtonPressed")

  **Aşağı açılan düğmesi**

  Arka Plan

  `Environment.ComboBoxButtonMouseDownBackground`

  Ön plan (karakter)

  `Environment.ComboBoxMouseDownGlyph`

  **Devre dışı**

  ![Birleşik giriş kutusu giriş alanını devre dışı](../../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")

  **Giriş alanı**

  Arka Plan

  `Environment.ComboBoxDisabledBackground`

  Ön plan (metin)

  `Environment.ComboBoxDisabledText`

  Kenarlık

  `Environment.ComboBoxDisabledBorder`

  Ayırıcı

  Hiçbir ayırıcısı

  ![Birleşik giriş kutusu&#47;bırak&#45;Kapat düğmesi devre dışı](../../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303 040_ComboBoxDropdownButtonDisabled")

  **Aşağı açılan düğmesi**

  Arka Plan

  Yok.

  Ön plan (karakter)

  `Environment.ComboBoxDisabledGlyph`

####  <a name="BKMK_CommandDropDown"></a> Açılan

> [!IMPORTANT]
>  Açılan listeler, birleşik giriş kutuları için benzerdir, ancak düzenlenebilir metin bölgeleri yoksundur. Düzenlenebilir metin bölge, açılan içerir, altında bulunan renk belirteçleri kullanın. [birleşik giriş kutusu](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

 ![DROP&#45;aşağı kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303 042_DropdownRedline")

 Kullan...
ne zaman özel aşağı açılan liste denetimleri oluşturuyorsunuz.

 Kullanmayın...
 -   her şey için aşağı açılan listesine benzer değil.

- Birleşik giriş kutuları veya Bölünmüş düğme.

  **Default**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![DROP&#45;seçim alanı aşağı](../../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 043_DropdownSelectionField")

  **Seçim alanı**

  Arka Plan

  `Environment.DropDownBackground`

  Ön plan (metin)

  `DropDownText`

  Kenarlık

  `DropDownBorder`

  Ayırıcı

  Hiçbir ayırıcısı

  ![DROP&#45;Kapat düğmesi](../../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303 044_DropdownButton")

  **Aşağı açılan düğmesi**

  Arka Plan

  Yok.

  Ön plan (karakter)

  `Environment.DropDownGlyph`

  ![DROP&#45;açılan listesinde](../../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 045_DropdownList")

  **Aşağı açılan listesi**

  Arka Plan

  `Environment.DropDownPopupBackgroundBegin`

  Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

  Ön plan (metin)

  `Environment.ComboBoxItemText`

  Kenarlık

  `Environment.DropDownPopupBorder`

  Gölge

  `Environment.DropShadowBackground`

  **Vurgulu**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![DROP&#45;seçim alanı üzerine gelindiğinde aşağı](../../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")

  **Seçim alanı**

  Arka Plan

  `Environment.DropDownMouseOverBackgroundBegin`

  Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

  Ön plan (metin)

  `Environment.DropDownMouseOverText`

  Kenarlık

  `Environment.DropDownMouseOverBorder`

  Ayırıcı

  `Environment.DropDownButtonMouseOverSeparator`

  ![DROP&#45;Kapat düğmesi üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303 047_DropdownButtonHover")

  **Aşağı açılan düğmesi**

  Arka Plan

  `Environment.DropDownButtonMouseOverBackground`

  Ön plan (karakter)

  `Environment.DropDownMouseOverGlyph`

  ![DROP&#45;açılan listesinde üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 048_DropdownListHover")

  **Aşağı açılan listesi**

  Arka plan (menü öğesi)

  `Environment.ComboBoxItemMouseOverBackground`

  Ön plan (metin)

  `Environment.ComboBoxItemMouseOverText`

  Kenarlık (menü öğesi)

  `Environment.ComboBoxItemMouseOverBorder`

  **Basılan**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![DROP&#45;tuşunu basılı seçim alanı](../../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")

  **Seçim alanı**

  Arka Plan

  `Environment.DropDownMouseDownBackground`

  Ön plan (metin)

  `Environment.DropDownMouseDownText`

  Kenarlık

  `Environment.DropDownMouseDownBorder`

  Ayırıcı

  `Environment.DropDownButtonMouseDownSeparator`

  ![DROP&#45;düğmeye basıldığını aşağı](../../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303 050_DropdownButtonPressed")

  **Aşağı açılan düğmesi**

  Arka Plan

  `Environment.DropDownButtonMouseDownBackground`

  Ön plan (karakter)

  `Environment.DropDownMouseDownGlyph`

  **Devre dışı**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![DROP&#45;devre dışı seçim alanı aşağı](../../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")

  Arka Plan

  `Environment.DropDownDisabledBackground`

  Ön plan (metin)

  `Environment.DropDownDisabledText`

  Kenarlık

  `Environment.DropDownDisabledBorder`

  Ayırıcı

  Hiçbir ayırıcısı

  ![DROP&#45;Kapat düğmesi devre dışı](../../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303 052_DropdownButtonDisabled")

  Arka Plan

  Yok

  Ön plan (karakter)

  `Environment.DropDownDisabledGlyph`

#### <a name="split-button"></a>Bölünmüş düğme
 Bölünmüş düğme fazla belirteç ad düğmeler, menüler ve komut çubuğu metni gibi diğer komut çubuğu denetimleri ile paylaşın. Tüm gerekli eylem ve açılan düğmeyi belirteci adları kolaylık olması için burada yinelenir. Bölünmüş düğme açılan listeleri, uygulamaları komut çubuğunun [menüleri](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).

 ![Bölünmüş düğme kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303 053_SplitButtonRedline")

 Kullan...
ne zaman özel bir Bölünmüş düğme oluşturuyorsunuz.

 Kullanmayın...
 -   diğer düğme türleri için.

- Belirtilen dışındaki tüm arka plan/ön plan arada.

  **Default**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Bölünmüş düğme](../../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 054_SplitButton")

  **Bölünmüş düğme (varsayılan)**

  Arka Plan

  Yok.

  Ön plan (metin)

  `Environment.CommandBarTextActive`

  Ön plan (karakter)

  `Environment.CommandBarSplitButtonGlyph`

  Kenarlık

  Yok

  Ayırıcı

  Yok

  **Vurgulu**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Bölünmüş düğme üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 055_SplitButtonHover")

  **Bölünmüş düğme (üzerine gelindiğinde)**

  Arka Plan

  `Environment.CommandBarMouseOverBackgroundBegin`

  Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

  Ön plan (metin)

  `Environment.CommandBarTextHover`

  Ön plan (karakter)

  `Environment.CommandBarSplitButtonMouseOverGlyph`

  Kenarlık

  `Environment.CommandBarBorder`

  Ayırıcı

  `Environment.CommandBarSplitButtonSeparator`

  **Basılan**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Bölünmüş düğmeye basıldığını](../../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 056_SplitButtonPressed")

  **Bölünmüş düğme (basılı)**

  Arka Plan

  `Environment.CommandBarMouseDownBackgroundBegin`

  Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

  Ön plan (metin)

  `Environment.CommandBarTextMouseDown`

  Ön plan (karakter)

  `Environment.CommandBarSplitButtonMouseDownGlyph`

  Kenarlık

  `Environment.CommandBarBorder`

  Ayırıcı

  Yok

  **Devre dışı**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Bölünmüş düğme devre dışı](../../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 057_SplitButtonDisabled")

  **Bölünmüş düğme (devre dışı)**

  Arka Plan

  Yok

  Ön plan (metin)

  `Environment.ComboBoxItemTextInactive`

  Ön plan (karakter)

  `Environment.CommandBarTextInactive`

  Kenarlık

  Yok

  Ayırıcı

  Yok

#### <a name="more-options-and-overflow-buttons"></a>'Daha Seçenekleri' ve 'Overflow' düğmeleri
 "Diğer seçenekler" düğmesi, bir komut çubuğu grubu özelleştirilebilir ekleme veya kaldırma ilgili komut çubuğu düğmelerinin olduğunda kullanılır. Bir komut çubuğu için yatay boşluk eksikliği nedeniyle kesilmiş ve görüntülenemiyor komut çubuğu düğmelerini içeren bir menü çubuğunda gösterir "Taşma" düğmesi görünür. Bu iki düğme için renkleri belirteci adları aynı kümesi tarafından denetlenir.

 ![Daha fazla seçenek kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303 058_MoreOptionsRedline")

 Kullan...
Özel 'daha fazla seçenek' veya 'Overflow' düğmeler için.

 Kullanmayın...
'Daha Seçenekleri' veya 'Overflow' düğmesini benzer bir işlevsellik yoksa düğmeler.

 **Default**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Daha fazla seçenek](../../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303 059_MoreOptions")

 **Daha fazla seçenek**

 ![Taşma düğmesi](../../extensibility/ux-guidelines/media/0303-060-overflow.png "0303 060_Overflow")

 **taşma**

 Arka Plan

 `Environment.CommandBarOptionsBackground`

 Ön plan (karakter)

 `Environment.CommandBarOptionsGlyph`

 **Vurgulu**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Daha fazla seçenek üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303 061_MoreOptionsHover")

 **Daha fazla seçenek**

 ![Overflow üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303 062_OverflowOptions")

 **taşma**

 Arka Plan

 `Environment.CommandBarOptionsMouseOverBackgroundBegin`

 Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

 Ön plan (karakter)

 `Environment.CommandBarOptionsMouseDownGlyph`

 **Basılan**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Daha fazla seçenek basılı](../../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303 063_MoreOptionsPressed")

 **Daha fazla seçenek**

 ![Basılan taşma](../../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303 064_OverflowPressed")

 **taşma**

 Arka Plan

 `Environment.CommandBarOptionsMouseDownBackgroundBegin`

 Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

 Ön plan (karakter)

 `Environment.CommandBarOptionsMouseDownGlyph`

## <a name="document-windows"></a>Belge pencereleri
 Visual Studio ortamı tarafından sağlandığından belge pencereleri çoğaltmak için gerek yoktur. Ancak, kullanıcı Arabirimi her zaman Visual Studio ortamının bu bölümü ile tutarlı görünmesi belge pencerelerinin kullanılan renkleri yararlanmak istediğinize karar verin.

 Belge penceresi renk belirteçleri kullanırken, yalnızca benzer öğeleri için ve her zaman çiftler halinde kullanmak dikkatli olmanız gerekir. Bunu yaparsanız, olması, kullanıcı arabiriminde beklenmeyen sonuçlar.

### <a name="document-window-frame"></a>Belge pencere çerçevesi
 Belge pencereleri IDE içindeki yerleşik veya ayrı bir pencerede olarak kayan olabilir. Belge penceresini IDE dışında kayan noktalı, yine de bir belge kutusu içinde bulunur ve arka plan, kenarlık, metin ve IDE parçası olduğunda, aynı olan sekme renkleri vardır. Ancak, belgeyi kendi arka plan, kenarlık ve metin renklerini olan bir çerçeve içinde bulunur. Araç pencereleri belge iyi yerleştirildiğinde, bunların davranışı ve kendi sekme rengini belge penceresi belirteci adlarından devralır.

 ![Yerleşik belge penceresi kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303 065_DockedDocumentWindowRedline")

 **Yerleşik belge penceresi**

 ![Belge penceresi kayan kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303 066_FloatingDocumentWindowRedline")

 **Kayan belge penceresi**

 Kullan...
herhangi bir belge penceresi eşleştirmek istediğiniz kullanıcı Arabirimi oluşturuyorsunuz.

 Kullanmayın...
otomatik olarak değiştirmeyi istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir.

 **Default**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 Belge: yerleşik veya kayan

 Arka Plan

 Belge türüne göre değişir

 Ön plan (metin)

 Belge türüne göre değişir

 Kenarlık

 `Environment.ToolWindowBorder`

 ![Odaklanmış çerçeve](../../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 067_FrameFocused")

 **Çerçeve: kayan, odaklanmış**

 Arka Plan

 `Environment.ToolWindowFloatingFrame`

 Ön plan (metin)

 `Environment.ToolWindowFloatingFrame`

 Ön plan (karakter)

 `Environment.RaftedWindowButtonActiveGlyph`

 Kenarlık

 `Environment.MainWindowActiveDefaultBorder`

 Kenarlık (karakter)

 `Environment.RaftedWindowButtonActiveBorder`

 Saydam ayarlayın

 ![Çerçeve odaklanmadan](../../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 068_FrameUnfocused")

 **Çerçeve: kayan bu plana odaklanmadan**

 Arka Plan

 `Environment.ToolWindowFloatingFrameInactive`

 Ön plan (metin)

 `Environment.ToolWindowFloatingFrameInactive`

 Ön plan (karakter)

 `Environment.RaftedWindowButtonInactiveGlyph`

 Kenarlık

 `Environment.MainWindowInactiveBorder`

 Kenarlık (karakter)

 `Environment.RaftedWindowButtonInactiveBorder`

 Saydam ayarlayın

 **Vurgulu**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Çerçeve üzerine gelindiğinde odaklanmış](../../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 069_FrameFocusedHover")

 **Çerçeve: kayan, odaklanmış**

 Arka plan (karakter)

 `Environment.RaftedWindowButtonHoverActive`

 Ön plan (karakter)

 `Environment.RaftedWindowButtonHoverActiveGlyph`

 Kenarlık (karakter)

 `Environment.RaftedWindowButtonHoverActiveBorder`

 ![Çerçeve üzerine gelindiğinde odaklanmadan](../../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 070_FrameUnfocusedHover")

 **Çerçeve: kayan bu plana odaklanmadan**

 Arka plan (karakter)

 `EnvironmentRaftedWindowButtonHoverInactive`

 Ön plan (karakter)

 `Environment.RaftedWindowButtonHoverInactiveGlyph`

 Kenarlık (karakter)

 `Environment.RaftedWindowButtonHoverInactiveBorder`

 **Basılan**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Çerçeve odaklanmış basılı](../../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 071_FrameFocusedPressed")

 **Çerçeve: kayan, odaklanmış**

 Arka plan (karakter)

 `Environment.RaftedWindowButtonDown`

 Ön plan (karakter)

 `Environment.RaftedWindowButtonDownGlyph`

 Kenarlık (karakter)

 `Environment.RaftedWindowButtonDownBorder`

### <a name="document-tabs"></a>Belge sekmeleri
 Belge sekmeleri hangi belgelerin yanı sıra etkin belgeyi hangisinin seçili geçerli olduğu veya şu anda açık olan belirtmek için sekmesinde kanaldaki durur. Kullanıcı var. bunları yerleştirir, araç pencerelerini de belge sekme kanalda sabitlenebilir. Bu durumda, bunlar aynı sekme renkleri ve belge pencereleri kullanır. Kullanıcı Arabirimi, oluşturuyorsanız, her zaman (Tema güncelleştirmeleri veya yeni temalar yüklediyseniz dahil) belge penceresini renkleriyle eşleşecek ve ardından bu renk belirteçleri başvuru istiyorsunuz.

 ![Belge sekmesini kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303 072_DocumentTabRedline")

 Kullan...
herhangi bir belge sekmeleri eşleşen ve tema güncelleştirmeleri veya yeni Tema renkleri otomatik olarak seçmek istediğiniz kullanıcı Arabirimi oluşturuyorsunuz.

 Kullanmayın...
Kabuk güncelleştirme bir tema olduğunda otomatik olarak değiştirmek istemediğiniz herhangi bir UI için.

#### <a name="open-document-tabs"></a>Açık belge sekmeleri
 Her açık belge adını görüntüleyen belge sekme kanalda bir sekmesi vardır. Belge ya da seçilebilir veya arka planda açın ve bu durumları sekmeleri yansıtacak:

- Seçili belgeyi de şu anda görüntülenen belgenin temsil eder. Seçili bir sekme iyi belgenin üst kenarı genişlettiği belge kenarlık vardır.

- Arka plan sekmeleri şu anda seçilen sekmesi olmayan herhangi bir belge sekme var. Tıklattıktan sonra seçili duruma ve tüm arka plan, kenarlık ve metin renklerini Bu belirteci adlarından Al.

  ![Açık belge sekme kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303 073_OpenDocumentTabRedline")

  Kullan...
  ne zaman özel belge sekmeleri oluşturuyorsunuz.

  Kullanmayın...
  -   (Önizleme) provisional sekmeler için.

- otomatik olarak değiştirmeyi istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir.

#### <a name="selected-tab"></a>Seçilen sekmesi
 **Odaklanmış**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Seçili sekme odaklanmış](../../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 074_SelectedTabFocused")

 **Odaklanmış, seçilen belge sekmesi**

 Arka Plan

 `Environment.FileTabSelectedGradientTop`

 Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

 Ön plan (metin)

 `Environment.FileTabSelectedText`

 Kenarlık

 `Environment.FileTabSelectedBorder`

 Aynı arka plan rengini ayarlayın.

 Belge kenarlık

 `Environment.FileTabDocumentBorderBackground`

 **Plana odaklanmadan**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Seçili sekme odaklanmadan](../../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 075_SelectedTabUnfocused")

 **Seçilen belge sekmesini, plana odaklanmadan**

 Arka Plan

 `Environment.FileTabInactiveGradientTop`

 Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

 Ön plan (metin)

 `Environment.FileTabInactiveText`

 Kenarlık

 `Environment.FileTabInactiveBorder`

 Aynı arka plan rengini ayarlayın.

 Belge kenarlık

 `Environment.FileTabInactiveDocumentBorderBackground`

#### <a name="background-tab"></a>Arka plan sekmesi
 **Default**

 ![Arka plan sekmesine](../../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 076_BackgroundTab")

 **Arka plan sekmesine varsayılan**

 Arka Plan

 `Environment.FileTabBackground`

 Ön plan (metin)

 `Environment.FileTabText`

 Kenarlık

 `Environment.FileTabBorder`

 Aynı arka plan rengini ayarlayın.

 **Vurgulu**

 ![Üzerine gelindiğinde kullanılacak arka plan sekmesinde](../../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 077_BackgroundTabHover")

 **Üzerine gelindiğinde kullanılacak arka plan sekmesinde**

 Arka Plan

 `Environment.FileTabHotGradientTop`

 Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

 Ön plan (metin)

 `Environment.FileTabHotText`

 Kenarlık

 `Environment.FileTabHotBorder`

 Aynı arka plan rengini ayarlayın.

#### <a name="preview-tab"></a>Önizleme sekmesi
 Önizleme sekmesini, kullanıcı Çözüm Gezgini araç penceresindeki bir öğeyi tıklattığında belge sekme kanal sağ tarafında görünür. Bu belgenin önizleme olarak davranır ve kullanıcı belgeyi belge sekme kanal sol tarafında açık tutmak için seçeneği de sunar. Bir kerede yalnızca bir Önizleme sekmesini Aç açık olabilir. Önizleme sekmeleri sahip hem de arka plan ve seçili durumlardan sekmeleri Aç gibi ve kullanıcıların etkin durumda odaklanmış veya plana odaklanmadan olabilir.

 ![Önizleme sekmesini kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303 078_PreviewTabRedline")

 Kullan...
herhangi bir provisional Önizleme oluşturma ve bazı öğesi geçerli Önizleme sekme rengini eşleştirilecek istiyor.

 Kullanmayın...
 -   Belge ya da geçici olmayan sekmesinde herhangi bir türdeki (Önizleme).

- otomatik olarak değiştirmeyi istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir.

  **Seçili Önizleme sekmesi: odaklanmış**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Önizleme sekmesini odaklanmış](../../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 079_PreviewTabFocused")

  **Odaklanmış Önizleme sekmesi**

  Arka Plan

  `Environment.FileTabProvisionalSelectedActive`

  Ön plan (metin)

  `Environment.FileTabProvisionalSelectedActiveForeground`

  Kenarlık

  `Environment.FileTabProvisionalSelectedActiveBorder`

  Aynı arka plan rengini ayarlayın.

  Belge kenarlık

  `Environment.FileTabProvisionalSelectedActiveBorder`

  **Seçili Önizleme sekmesi: Odaklanmadan**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Önizleme sekmesini odaklanmadan](../../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 080_PreviewTabUnfocused")

  **Plana odaklanmadan Önizleme sekmesi**

  Arka Plan

  `Environment.FileTabProvisionalSelectedInactive`

  Ön plan (metin)

  `Environment.FileTabProvisionalSelectedInactiveForeground`

  Kenarlık

  `Environment.FileTabProvisionalSelectedInactiveBorder`

  Belge kenarlık

  `Environment.FileTabProvisionalSelectedInactiveBorder`

  **Arka plan Önizleme sekmesi: varsayılan**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Önizleme arka plan sekmesine](../../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 081_PreviewBackgroundTab")

  **Önizleme sekmesini arka plan sekmesi**

  Arka Plan

  `Environment.FileTabProvisionalInactive`

  Ön plan (metin)

  `Environment.FileTabProvisionalInactiveForeground`

  Kenarlık

  `Environment.FileTabProvisionalInactiveBorder`

  Aynı arka plan rengini ayarlayın.

  **Arka plan Önizleme sekmesi: getirin**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Önizleme arka plan sekmesine üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")

  **Önizleme sekmesini arka plan sekmesine üzerine gelindiğinde**

  Arka Plan

  `Environment.FileTabProvisionalHover`

  Ön plan (metin)

  `Environment.FileTabProvisionalHoverForeground`

  Kenarlık

  `Environment.FileTabProvisionalHoverBorder`

  Aynı arka plan rengini ayarlayın.

#### <a name="document-overflow-button"></a>Belge Taşma düğmesi
 Belge Taşma düğmesi, bir veya daha fazla belge olup olmamasına bakılmaksızın açık, mevcut ise tüm belge sekmeleri uyacak şekilde, geçerli yapılandırma dikey boşluk yoktur. Denetlenen belge taşma açılan menüsünü **CommandBarMenu** renkleri (bkz [menüleri](../../misc/shared-colors.md#BKMK_CommandMenus)), bütün açık belgeleri, görünür ve gizli ve taşma glif değişikliklerin bir listesini görüntüler bağlı olarak tüm açık belgeleri sekmesini kanalda olup görüntülenir.

 ![Taşma kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303 083_OverflowRedline")

 Kullan...
ne zaman bir özel belge taşma düğmesini oluşturuyorsunuz.

 Kullanmayın...
 -   taşma düğmesini için benzer değil kullanıcı Arabirimi için.

- Komut çubuğu taşma düğmeleri.

  **Default**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Overflow](../../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 084_Overflow")

  **Belge Taşma düğmesi**

  Arka Plan

  `Environment.DocWellOverflowButtonBackground`

  Ön plan (karakter)

  `Environment.DocWellOverflowButtonGlyph`

  Kenarlık

  Yok

  **Vurgulu**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Overflow üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 085_OverflowHover")

  **Üzerine gelindiğinde belge taşma düğmesi**

  Arka Plan

  `Environment.DocWellOverflowButtonMouseOverBackground`

  Ön plan (karakter)

  `Environment.DocWellOverflowButtonMouseOverGlyph`

  Kenarlık

  `Environment.DocWellOverflowButtonMouseOverBorder`

  **Basılan**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Basılan taşma](../../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 086_OverflowPressed")

  **Belge taşma düğmesini basılı**

  Arka Plan

  `Environment.DocWellOverflowButtonMouseDownBackground`

  Ön plan (karakter)

  `Environment.DocWellOverflowButtonMouseDownGlyph`

  Kenarlık

  `Environment.DocWellOverflowButtonMouseDownBorder`

## <a name="tool-windows"></a>Araç pencereleri
 Visual Studio ortamı tarafından sağlandığından, araç pencerelerini çoğaltmak için gerek yoktur. Ancak, kullanıcı Arabirimi her zaman Visual Studio ortamının bu bölümü ile tutarlı görünmesi araç pencerelerinde kullanılan renkleri yararlanmak istediğinize karar verin.

 ![Araç penceresi kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303 087_ToolWindowRedline")

 Kullan...
herhangi bir yerde araç pencerelerini eşleştirmek istediğiniz kullanıcı Arabirimi oluşturuyorsunuz.

 Kullanmayın...
otomatik olarak değiştirmeyi istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir.

### <a name="tool-window-frame"></a>Araç pencere çerçevesi
 Visual Studio araç pencereleri, birçok farklı görevler için kullanılır ve birçok farklı durumdan birinde bulunabilir. Araç penceresi açık değilse, tüm belge alanını dört tarafına atanabilir. Araç pencerelerini de herhangi bir kullanıcının ekranında konumlandırılmasına olanak tanıyan IDE dışında kaydırabilirsiniz. Kayan windows her zaman, IDE üzerinde durur. Son olarak, araç pencerelerini belge pencereleri yerleştirilmiş olabilir ve iyi belge sekme olarak görünür. Belge pencereleri yerleştirilmiş araç pencereleri, kısmen belge penceresi simge adları kullanarak renklendirilmiştir.

 ![Araç pencere çerçevesi kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303 088_ToolWindowFrameRedline")

 Kullan...
herhangi bir yerde araç pencerelerini eşleştirmek istediğiniz kullanıcı Arabirimi oluşturuyorsunuz.

 Kullanmayın...
otomatik olarak değiştirmeyi istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir.

 **Yuvalanmış**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Araç penceresi yerleştirilmiş](../../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303 089_ToolWindowDocked")

 Arka Plan

 `Environment.ToolWindowBackground`

 Kenarlık

 `Environment.ToolWindowBorder`

 **Kayan: odaklanmış**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Araç penceresi odaklanmış](../../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303 090_ToolWindowFocused")

 Arka Plan

 `Environment.ToolWindowBackground`

 Kenarlık

 `Environment.MainWindowActiveDefaultBorder`

 **Kayan: odaklanmadan**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Araç penceresi odaklanmadan](../../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303 091_ToolWindowUnfocused")

 Arka Plan

 `Environment.ToolWindowBackground`

 Kenarlık

 `Environment.MainWindowInactiveBorder`

### <a name="tool-window-title-bar"></a>Araç penceresinin başlık çubuğu
 Başlık çubuğu kenarlığı doğru kenarlık ancak kalın çizgi başlık çubuğunun üst kısmında değil. Bir plana odaklanmadan durumuna belirteç adı yok.

 ![Araç penceresinin başlık çubuğu kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303 092_ToolWindowTitleBarRedline")

 Kullan...
herhangi bir yerde araç pencerelerini eşleştirmek istediğiniz kullanıcı Arabirimi oluşturuyorsunuz.

 Kullanmayın...
otomatik olarak değiştirmeyi istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir.

 **Odaklanmış**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Başlık çubuğu odaklanmış](../../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 093_TitleBarFocused")

 **Odaklanmış başlık çubuğu**

 Arka Plan

 `Environment.TitleBarActiveGradientBegin`

 Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

 Ön plan (metin)

 `Environment.TitleBarActiveText`

 Kenarlık

 `Environment.TitleBarActiveBorder`

 Aynı arka plan rengini ayarlayın.

 Sürükleme tutamacı

 `Environment.TitleBarDragHandleActive`

 **Plana odaklanmadan**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Başlık çubuğu odaklanmadan](../../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 094_TitleBarUnfocused")

 **Plana odaklanmadan başlık çubuğu**

 Arka Plan

 `Environment.TitleBarInactiveGradientBegin`

 Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

 Ön plan (metin)

 `Environment.TitleBarInactiveText`

 Kenarlık

 Yok

 Sürükleme tutamacı

 `Environment.TitleBarDragHandle`

#### <a name="title-bar-buttons"></a>Başlık çubuğu düğmeleri
 ![Başlık çubuğu düğme kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303 095_TitleBarButtonRedline")

 Kullan...
araç penceresinin başlık çubuğu renk belirteçleri kullanan kullanıcı arabiriminde görünen düğme.

 Kullanmayın...
 -   diğer konumlardaki düğmeler.

- Belirtilen dışındaki tüm arka plan/ön plan arada.

  **Default**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Başlık düğme odaklanmış](../../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")

  **Odaklanmış**

  Arka Plan

  Yok

  Ön plan (karakter)

  `Environment.ToolWindowButtonActiveGlyph`

  Kenarlık

  Yok

  ![Başlık düğme odaklanmadan](../../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")

  **Plana odaklanmadan**

  Arka Plan

  Yok

  Ön plan (karakter)

  `Environment.ToolWindowButtonInactiveGlyph`

  Kenarlık

  Yok

  **Vurgulu**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Başlık çubuğu düğme üzerine gelindiğinde odaklanmış](../../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")

  **Odaklanmış**

  Arka Plan

  `Environment.ToolWindowButtonHoverActive`

  Ön plan (karakter)

  `Environment.ToolWindowButtonHoverActiveGlyph`

  Kenarlık

  `Environment.ToolWindowButtonHoverActiveBorder`

  ![Başlık çubuğu düğme üzerine gelindiğinde odaklanmadan](../../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")

  **Plana odaklanmadan**

  Arka Plan

  `Environment.ToolWindowButtonHoverInactive`

  Ön plan (karakter)

  `Environment.ToolWindowButtonHoverInactiveGlyph`

  Kenarlık

  `Environment.ToolWindowButtonHoverInactiveBorder`

  **Basılan**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Başlık odaklı ve basılı düğmesi](../../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")

  **Odaklanmış**

  Arka Plan

  `Environment.ToolWindowButtonDown`

  Ön plan (karakter)

  `Environment.ToolWindowButtonDownActiveGlyph`

  Kenarlık

  `Environment.ToolWindowButtonDownBorder`

  ![Başlık çubuğu düğme odaklanmadan ve basılı](../../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")

  **Plana odaklanmadan**

  Arka Plan

  `Environment.ToolWindowButtonDown`

  Ön plan (karakter)

  `Environment.ToolWindowButtonDownInactiveGlyph`

  Kenarlık

  `Environment.ToolWindowButtonDownBorder`

### <a name="tool-window-tabs"></a>Araç penceresi sekmeleri
 ![Araç penceresi sekmesindeki kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303 102_ToolWindowTabRedline")

 Kullan...
herhangi bir yerde araç pencerelerini eşleştirmek istediğiniz kullanıcı Arabirimi oluşturuyorsunuz.

 Kullanmayın...
otomatik olarak değiştirmeyi istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir.

 **Seçilen sekmesi**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Araç penceresi sekmesinin odaklanmış](../../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")

 **Seçildiğinde, odaklanmış aracı penceresi sekmesi**

 Arka Plan

 `Environment.ToolWindowTabSelectedTab`

 Ön plan (metin)

 `Environment.ToolWindowTabSelectedActiveText`

 Kenarlık

 `Environment.ToolWindowTabSelectedBorder`

 Aynı arka plan rengini ayarlayın.

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Araç penceresi sekmesinin odaklanmadan](../../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")

 **Seçildiğinde, plana odaklanmadan aracı penceresi sekmesi**

 Arka Plan

 `Environment.ToolWindowTabSelectedTab`

 Ön plan (metin)

 `Environment.ToolWindowTabSelectedText`

 Kenarlık

 `Environment.ToolWindowTabSelectedBorder`

 Aynı arka plan rengini ayarlayın.

 **Arka plan sekmesi**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Araç penceresi arka plan sekmesine](../../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")

 **Arka plan aracı penceresi sekmesi**

 Arka Plan

 `Environment.ToolWindowTabGradientBegin`

 Visual Studio 2013'te aynı renk değeri kümesine gradyan durdurur.

 `Environment.ToolWindowTabGradientEnd`

 Visual Studio 2013'te aynı renk değeri kümesine gradyan durdurur.

 Ön plan (metin)

 `Environment.ToolWindowTabText`

 Kenarlık

 `Environment.ToolWindowTabBorder`

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Üzerine gelindiğinde araç penceresi arka plan sekmesine](../../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")

 **Üzerine gelindiğinde arka plan aracı penceresi sekmesi**

 Arka Plan

 `Environment.ToolWindowTabMouseOverBackgroundBegin`

 Visual Studio 2013'te aynı renk değeri kümesine gradyan durdurur.

 `Environment.ToolWindowTabMouseOverBackgroundEnd`

 Visual Studio 2013'te aynı renk değeri kümesine gradyan durdurur.

 Ön plan (metin)

 `Environment.ToolWindowTabMouseOverText`

 Kenarlık

 `Environment.ToolWindowTabMouseOverBorder`

 Aynı arka plan rengini ayarlayın.

### <a name="auto-hide-tabs"></a>Sekmeleri otomatik olarak gizle
 ![Otomatik&#45;Gizle kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303 107_AutoHideRedline")

 Kullan...
herhangi bir otomatik olarak gizlendiğinde araç penceresi sekmeleri eşleştirmek istediğiniz kullanıcı Arabirimi oluşturuyorsunuz.

 Kullanmayın...
otomatik olarak değiştirmeyi istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir.

 **Default**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Otomatik&#45;sekmesini gizle](../../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 108_AutoHideTab")

 **Varsayılan otomatik gizleme sekmesi**

 Arka Plan

 `Environment.AutoHideTabBackgroundBegin`

 Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

 Ön plan (metin)

 `Environment.AutoHideTabText`

 Kenarlık

 `Environment.AutoHideTabBorder`

 **Vurgulu**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Otomatik&#45;sekmesini üzerine gelindiğinde Gizle](../../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 109_AutoHideTabHover")

 **Üzerine gelindiğinde otomatik gizleme sekmesi**

 Arka Plan

 `Environment.AutoHideTabMouseOverBackgroundBegin`

 Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

 Ön plan (metin)

 `Environment.AutoHideTabMouseOverText`

 Kenarlık

 `Environment.AutoHideTabMouseOverBorder`

## <a name="common-shared-controls"></a>Paylaşılan ortak denetimleri
 Standart bir Visual Studio komut çubuğu, özelliğini kullandığınızda, stil uygulanmış bir kabuk denetimlerini erişebilir ve bu ortak denetimleri yeniden-template gerekir. Ancak, özel bir komut çubuğu oluşturmak ihtiyacınız varsa, özel denetimler de gerekebilir. Bu durumda, kullanıcı Arabirimi Visual Studio geri kalanı ile tutarlı olmasını sağlayın, her biri aşağıdaki denetimleri için doğru belirteci adları kullandığınızdan emin olun.

### <a name="search-box"></a>Arama kutusu
 Mümkün olduğunda, Visual Studio ortamı tarafından sağlanan genel arama denetimini kullanın. Arama kutusuna renklerini bulundu "SearchControl" kategorisinde **ShellColors.pkgdef** giriş alanı, eylem düğmesi, açılan düğmeyi ve açılan menü için belirteç adları içeren dosya.

 Bir arama kutusu bazıları birbirini dışlayan olan çeşitli durumları biri olabilir:

- "Odaklı" veya "odaklanmadan" olup olmadığını imleç ve metin kutusundaki için kısaltmasıdır.

- Kullanıcının metin kutusuna bir arama sorgusu girişinin için "Etkin" veya "etkin" anlamına gelir.

- "Vurgu", kullanıcı (Bu durumda, diğer tüm durumları geçersiz kılar) fare ile arama kutusuna moused anlamına gelir.

- "Devre dışı" arama işlevi için geçerli bağlam kapalı anlamına gelir.

  ![Arama kutusuna kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303 110_SearchBoxRedline")

  Kullan...
  ne zaman bir özel arama kutusu tasarlarken.

  Kullanmayın...
  -   her şey için bir arama kutusu değil.

- her zaman arama eşleştirilecek istemediğiniz her şey için kullanıcı Arabirimi kutusu.

  **Odaklanmış**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Arama giriş alanı odaklanmış](../../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")

  **Giriş alanı**

  Arka Plan

  `SearchControl.FocusedBackground`

  Ön plan (metin)

  `SearchControl.FocusedBackground`

  Kenarlık

  `SearchControl.FocusedBorder`

  Ayırıcı

  `SearchControl.FocusedDropDownSeparator`

  ![Arama eylem düğmesi odaklanmış](../../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")

  **Eylem düğmesi**

  Arka Plan

  Yok.

  Ön plan (arama karakter)

  `SearchControl.SearchGlyph`

  Ön plan (durdurma karakter)

  `SearchControl.StopGlyph`

  Ön plan (NET karakter)

  `SearchControl.ClearGlyph`

  Kenarlık

  Yok

  ![Arama açılan&#45;odaklanmış düğmesini basılı](../../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")

  **Aşağı açılan düğmesi**

  Arka Plan

  `SearchControl.FocusedDropDownButton`

  Ön plan (karakter)

  `SearchControl.FocusedDropDownButtonGlyph`

  Kenarlık

  `SearchControl.FocusedDropDownButtonBorder`

  **Plana odaklanmadan**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Arama giriş alanı odaklanmadan](../../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")

  **Etkin giriş alanı**

  Arka Plan

  `SearchControl.SearchActiveBackground`

  Ön plan (metin)

  `SearchControl.SearchActiveBackground`

  Kenarlık

  `SearchControl.UnfocusedBorder`

  Ayırıcı

  `SearchControl.DropDownSeparator`

  ![Arama giriş alanı odaklanmadan ve etkin olmayan](../../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303 114 1_SearchInputFieldUnfocusedInactive")

  **Etkin olmayan giriş alanı**

  Arka Plan

  `SearchControl.Unfocused`

  Ön plan (metin)

  `SearchControl.Unfocused`

  Kenarlık

  `SearchControl.UnfocusedBorder`

  Ayırıcı

  `SearchControl.DropDownSeparator`

  ![Arama eylem düğmesi odaklanmadan](../../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")

  **Eylem düğmesi**

  Arka Plan

  Yok

  Ön plan (arama karakter)

  `SearchControl.SearchGlyph`

  Ön plan (durdurma karakter)

  `SearchControl.StopGlyph`

  Ön plan (NET karakter)

  `SearchControl.ClearGlyph`

  Kenarlık

  Yok

  ![Arama açılan&#45;Kapat düğmesi odaklanmadan](../../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")

  **Aşağı açılan düğmesi**

  Arka Plan

  `SearchControl.UnfocusedDropDownButton`

  Ön plan (karakter)

  `SearchControl.UnfocusedDropDownButtonGlyph`

  Kenarlık

  `SearchControl.UnfocusedDropDownButtonBorder`

  **Basılan**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Arama eylem düğmesi basılı](../../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303 116 1_SearchActionButtonPressed")

  **Eylem düğmesi**

  Arka Plan

  `SearchControl.ActionButtonMouseDown`

  Ön plan (karakter)

  `SearchControl.ActionButtonMouseDownGlyph`

  Kenarlık

  `SearchControl.ActionButtonMouseDownBorder`

  ![Arama açılan&#45;düğmeye basıldığını aşağı](../../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303 116 2_SearchDropdownButtonPressed")

  **Aşağı açılan düğmesi**

  Arka Plan

  `SearchControl.MouseDownDropDownButton`

  Ön plan (karakter)

  `SearchControl.MouseDownDropDownButtonGlyph`

  Kenarlık

  `SearchControl.MouseDownDropDownButtonBorder`

  **Vurgulanan (yalnızca metin)**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Arama giriş alanı vurgulama](../../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")

  **Giriş alanı vurgulanmış metin**

  Arka Plan

  `SearchControl.Selection`

  Ön plan (metin)

  `SearchControl.FocusedBackground`

  Kenarlık

  Yok.

  Ayırıcı

  `SearchControl.FocusedDropDownSeparator`

  **Devre dışı**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Arama giriş alanını devre dışı](../../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")

  **Giriş alanı**

  Arka Plan

  `SearchControl.Disabled`

  Ön plan (metin)

  `SearchControl.Disabled`

  Kenarlık

  `SearchControl.DisabledBorder`

  Ayırıcı

  `SearchControl.DropDownSeparator`

  ![Arama eylem düğmesi devre dışı](../../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")

  **Eylem düğmesi**

  Arka Plan

  Yok.

  Ön plan (karakter)

  `SearchControl.ActionButtonDisabledGlyph`

  Kenarlık

  Yok.

  ![Arama açılan&#45;Kapat düğmesi devre dışı](../../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")

  **Aşağı açılan düğmesi**

  Arka Plan

  Yok.

  Ön plan (karakter)

  `SearchControl.DisabledDownButtonGlyph`

  Kenarlık

  Yok.

#### <a name="search-drop-down-lists"></a>Arama açılan listeler
 Arama kutusu açılır menüsünde, Visual Studio'daki diğer açılan menüler biraz daha karmaşık hale olasılığına sahiptir. "Önerilen aramalar" ve "Arama Seçenekleri" bölümleri tek başına görünebilir veya birlikte menü ve her biri ayrı ayrı renktedir. Bir satır da birlikte görünür ve tüm açılan menüden bir kenarlık çevreleyen bu iki bölüme ayırır.

 ![Arama açılan&#45;aşağı kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303 124_SearchDropdownRedline")

 Kullan...
 -   ne zaman bir özel arama açılan listedeki oluşturuyorsunuz.

- Düzeltme listesi bileşenleri için doğru belirteci adları.

  Kullanmayın...
  -   diğer bağlamlarda görünen açılan listeler.

- Belirtilen dışındaki tüm arka plan/ön plan arada.

  **Varsayılan (başka hiçbir durum)**

  Öğe

  Belirteç adı: Category.color

  Kenarlık

  `SearchControl.PopupBorder`

  Ayırıcı

  `SearchControl.PopupSectionHeaderSeparator`

  Gölge

  `Environment.DropShadowBackground`

  **Default**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Önerilen arama](../../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303 125_SearchSuggested")

  **Önerilen aramalar**

  Arka Plan

  `SearchControl.PopupItemsListBackgroundGradientBegin`

  Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

  Ön plan (metin)

  `SearchControl.PopupItemText`

  ![Arama onay kutusunu](../../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 126_SearchCheckbox")

  **Arama Seçenekleri (onay kutusu)**

  ![Arama Seçenekleri](../../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 127_SearchOptions")

  **Arama Seçenekleri (bağlantı)**

  Arka Plan

  `SearchControl.PopupSectionBackgroundGradientBegin`

  Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

  Ön plan (onay kutusu metni)

  `SearchControl.PopupCheckboxText`

  Ön plan (bağlantı metni)

  `SearchControl.PopupButtonText`

  Başlık arka plan

  `SearchControl.PopupSectionHeaderGradientBegin`

  Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

  Ön plan (üst bilgi metni)

  `SearchControl.PopupSectionHeaderText`

  **Vurgulu**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Üzerine gelindiğinde önerilen arama](../../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 128_SearchSuggestedHover")

  **Önerilen aramalar**

  Arka Plan

  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`

  Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

  Ön plan (metin)

  `SearchControl.PopupMouseOverItemText`

  Kenarlık

  `SearchControl.PopupControlMouseOverBorder`

  ![Arama onay kutusunu üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 129_SearchCheckboxHover")

  **Önerilen aramalar (onay kutusu)**

  ![Arama seçenekleri üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 130_SearchOptionsHover")

  **Arama Seçenekleri**

  Arka Plan

  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`

  Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

  Ön plan (onay kutusu metni)

  `SearchControl.PopupCheckboxMouseDownText`

  Ön plan (bağlantı metni)

  `SearchControl.PopupButtonMouseDownText`

  Kenarlık

  `SearchControl.PopupControlMouseOverBorder`

  **Basılan**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Arama önerilen basılı](../../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")

  **Önerilen aramalar (onay kutusu)**

  ![Arama Seçenekleri basılı](../../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 132_SearchOptionsPressed")

  **Arama Seçenekleri**

  Onay kutusu arka plan

  `SearchControl.PopupControlMouseDownBackgroundGradientBegin`

  Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

  `SearchControl.PopupControlMouseDownBackgroundGradientEnd`

  Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

  Ön plan (onay kutusu metni)

  `SearchControl.PopupCheckboxMouseDownText`

  Bağlantı arka plan

  `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`

  Modern temalı Arabiriminde kullanılmaz, ancak gradyan durakları ve arka planı için bu değerleri vardır.

  Ön plan (bağlantı metni)

  `SearchControl.PopupButtonMouseDownText`

### <a name="hyperlink"></a>Köprü
 Köprüyü bir ön plan/arka plan çifti sahip olmayan bir denetimdir. Her durumda, doğru koyu gri ve beyaz arka plan üzerinde görünür köprü ön plan rengini kullanın. Köprü denetim için renk belirteç kullanmazsanız "basılı için" varsayılan sistem renk görürsünüz ", kırmızı flash. Bu denetim doğru ortamı renk belirteci kullanmıyor sinyaldir.

 ![Köprü kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303 133_HyperlinkRedline")

 Kullan...
özel bir köprü oluşturmak gerektiğinde.

 Kullanmayın...
her şey için köprü değil.

 **Default**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Köprü varsayılan](../../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303 134_Hyperlink")

 Ön plan (metin)

 `Environment.PanelHyperlink`

 **Vurgulu**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Üzerine gelindiğinde köprü](../../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303 135_HyperlinkHover")

 Ön plan (metin)

 `Environment.PanelHyperlinkHover`

 **Basılan**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Basılan köprü](../../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303 136_HyperlinkPressed")

 Ön plan (metin)

 `Environment.PanelHyperlinkPressed`

 **Devre dışı**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Devre dışı köprü](../../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303 137_HyperlinkDisabled")

 Ön plan (metin)

 `Environment.PanelHyperlinkDisabled`

### <a name="infobar"></a>Bilgi Çubuğu
 Infobars her zaman bir belge penceresi veya araç penceresinin üst kısmında görünür ve belirli bir bağlam hakkında daha fazla bilgi sağlamak için kullanılır.

 ![Bilgi çubuğu kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303 138_InfobarRedline")

 Kullan...
Özel infobars oluştururken.

 Kullanmayın...
bir bilgi çubuğu için benzer olmayan kullanıcı Arabirimi öğeleri için.

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Bilgi Çubuğu](../../extensibility/ux-guidelines/media/0303-139-infobar.png "0303 139_Infobar")

 **Bilgi Çubuğu**

 Arka Plan

 `Environment.InfoBackground`

 Ön plan (metin)

 `Environment.InfoText`

 Kenarlık

 `Environment.ToolWindowBorder`

### <a name="scroll-bar"></a>Kaydırma çubuğu
 Kaydırma çubukları Visual Studio ortamı tarafından stillere ve temalı olması gerekmez. Ancak, kullanıcı Arabirimi her zaman Visual Studio ortamının bu bölümü ile tutarlı görünmesi kaydırma çubuklarında kullanılan renkleri yararlanmak istediğinize karar verin.

 ![Kaydırma çubuğu kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303 140_ScrollbarRedline")

 Kullan...
ne zaman Visual Studio kaydırma çubukları eşleştirmek istediğiniz kullanıcı Arabirimi oluşturuyorsunuz.

 ... Kaydırma çubuğu kullanıcı Arabirimi her zaman aynı istemediğiniz her şey için kullanmayın.

 **Default**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Kaydırma çubuğu](../../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303 141_Scrollbar")

 **Kaydırma çubuğu**

 Kaydırma çubuğu

 `Environment.ScrollBarBackground`

 Ön plan (Flash)

 `Environment.ScrollBarThumbBackground`

 ![Kaydırma ok](../../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303 142_ScrollbarArrow")

 **Kaydırma ok**

 Arka Plan

 `Environment.ScrollBarArrowBackground`

 Kaydırma çubuğu aynı renge ayarlayın.

 Ön plan (karakter)

 `Environment.ScrollBarArrowGlyph`

 **Vurgulu**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Kaydırma çubuğu üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303 143_ScrollbarHover")

 **Kaydırma çubuğu**

 Kaydırma çubuğu

 `Environment.ScrollBarBackground`

 Ön plan (Flash)

 `Environment.ScrollBarThumbMouseOverBackground`

 ![Kaydırma çubuğu üzerine gelindiğinde ok](../../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303 144_ScrollbarArrowHover")

 **Kaydırma ok**

 Arka Plan

 `Environment.ScrollBarArrowMouseOverBackground`

 Kaydırma çubuğu aynı renge ayarlayın.

 Ön plan (karakter)

 `Environment.ScrollBarArrowGlyphMouseOver`

 **Basılan**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Basılan kaydırma çubuğu](../../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303 145_ScrollbarPressed")

 **Kaydırma çubuğu**

 Kaydırma çubuğu

 `Environment.ScrollBarBackground`

 Ön plan (Flash)

 `Environment.ScrollBarThumbPressedBackground`

 ![Kaydırma basılı ok](../../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303 146_ScrollbarArrowPressed")

 **Kaydırma ok**

 Arka Plan

 `Environment.ScrollBarArrowPressedBackground`

 Kaydırma çubuğu aynı renge ayarlayın.

 Ön plan (karakter)

 `Environment.ScrollBarArrowGlyphPressed`

###  <a name="BKMK_TreeView"></a> Ağaç görünümü
 Çözüm Gezgini, Sunucu Gezgini ve sınıf görünümü de dahil olmak üzere birçok araç pencereleri, renklerini rengi adları TreeView kategorisinde denetlediği hiyerarşik bir kuruluş uygulamaz. Ağaç görünümünde tüm öğeler, arka plan ve metin renklerini içerir. Alt öğelerinin iç içe geçmiş öğeler de öğe genişletilmiş veya daraltılmış olup olmadığını belirten karakterler var.

 ![Ağaç görünümü kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303 147_TreeViewRedline")

 Kullan...
herhangi bir hiyerarşik bir kuruluş görünümü yapması gerekir.

 Kullanmayın...
 -   her şey için bir ağaç görünümüne benzer değil.

- Belirtilen dışındaki tüm arka plan/ön plan arada.

  **Default**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Ağaç görünümü](../../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 148_TreeView")

  Arka Plan

  `TreeView.Background`

  Ön plan (metin)

  `TreeView.Background`

  Ön plan (karakter)

  `TreeView.Glyph`

  Kenarlık

  Yok.

  **Vurgulu**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Ağaç görünümü üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 149_TreeViewHover")

  Arka Plan

  `TreeView.Background`

  Ön plan (metin)

  `TreeView.Background`

  Ön plan (karakter)

  `TreeView.GlyphMouseOver`

  Kenarlık

  Yok.

  **Üzerine sürükleyin**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Ağaç görünümü dragover](../../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 150_TreeViewDragOver")

  Arka Plan

  `TreeView.DragOverItem`

  Ön plan (metin)

  `TreeView.DragOverItem`

  Ön plan (karakter)

  `TreeView.DragOverItemGlyph`

  Kenarlık

  Yok.

  **Seçili**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Ağaç görünümü odaklanmış](../../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 151_TreeViewFocused")

  **Odaklanmış**

  Arka Plan

  `TreeView.SelectedItemActive`

  Ön plan (metin)

  `TreeView.SelectedItemActive`

  Ön plan (karakter)

  `TreeView.SelectedItemActiveGlyph`

  Kenarlık

  `TreeView.FocusVisualBorder`

  ![Ağaç görünümü odaklanmadan](../../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 152_TreeViewUnfocused")

  **Plana odaklanmadan**

  Arka Plan

  `TreeView.SelectedItemInactive`

  Ön plan (metin)

  `TreeView.SelectedItemInactive`

  Ön plan (karakter)

  `TreeView.SelectedItemInactiveGlyph`

  Kenarlık

  Yok.

  **Seçili üzerine gelin**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![Ağaç görünümü üzerine gelindiğinde odaklanmış](../../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")

  **Odaklanmış**

  Arka Plan

  `TreeView.SelectedItemActive`

  Ön plan (metin)

  `TreeView.SelectedItemActive`

  Ön plan (karakter)

  `TreeView.SelectedItemActiveGlyphMouseOver`

  Kenarlık

  Yok`TreeView.FocusVisualBorder`

  ![Ağaç görünümü odaklanmadan üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")

  **Plana odaklanmadan**

  Arka Plan

  `TreeView.SelectedItemInactive`

  Ön plan (metin)

  `TreeView.SelectedItemInactive`

  Ön plan (karakter)

  `TreeView.SelectedItemActiveGlyphMouseOver`

  Kenarlık

  Yok.

### <a name="button-controls"></a>Düğme denetimleri
 ![Düğme denetimi kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303 155_ButtonControlRedline")

 Kullan...
Visual Studio temasından (açık, koyu, mavi veya bir sistem yüksek karşıtlıklı tema) ile tümleştirmek istediğiniz belge kutusu düğmeleri için.

 Kullanmayın...
Visual Studio temasını bulunmayan özel bir arka plan karşı görüntüler düğmeler.

 **Default**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Düğme](../../extensibility/ux-guidelines/media/0303-156-button.png "0303 156_Button")

 Düğme

 `CommonControls.Button`

 Düğme kenarlığı

 `CommonControls.ButtonBorder`

 **Devre dışı**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Düğme devre dışı](../../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303 157_ButtonDisabled")

 Düğme

 `CommonControls.ButtonDisabled`

 Düğme kenarlığı

 `CommonControls.ButtonBorderDisabled`

 **Vurgulu**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Düğme üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303 158_ButtonHover")

 Düğme

 `CommonControls.ButtonHover`

 Düğme kenarlığı

 `CommonControls.ButtonBorderHover`

 **Basılan**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Düğmeye basıldığını](../../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303 159_ButtonPressed")

 Düğme

 `CommonControls.ButtonPressed`

 Düğme kenarlığı

 `CommonControls.ButtonBorderPressed`

 **Odaklanmış**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Odaklanmış düğmesi](../../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303 160_ButtonFocused")

 Düğme

 `CommonControls.ButtonFocused`

 Düğme kenarlığı

 `CommonControls.ButtonBorderFocused`

### <a name="check-box-controls"></a>Onay kutusu denetimleri
 ![Onay kutusu kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303 161_CheckboxRedline")

 Kullan...
Belgenin içinde bulunan onay kutusu denetimleri için yanı sıra.

 Kullanmayın...
herhangi bir UI için bu onay kutusu denetimi değil.

 **Default**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Onay kutusu](../../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 162_Checkbox")

 Arka Plan

 `CommonControls.CheckBoxBackground`

 Kenarlık

 `CommonControls.CheckBoxBorder`

 Metin

 `CommonControls.CheckBoxText`

 Glif

 `CommonControls.CheckBoxGlyph`

 **Devre dışı**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Devre dışı onay kutusu](../../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 163_CheckboxDisabled")

 Arka Plan

 `CommonControls.CheckBoxBackgroundDisabled`

 Kenarlık

 `CommonControls.CheckBoxBorderDisabled`

 Metin

 `CommonControls.CheckBoxTextDisabled`

 Glif

 `CommonControls.CheckBoxGlyphDisabled`

 **Vurgulu**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Onay kutusu üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 164_CheckboxHover")

 Arka Plan

 `CommonControls.CheckBoxBackgroundHover`

 Kenarlık

 `CommonControls.CheckBoxBorderHover`

 Metin

 `CommonControls.CheckBoxTextHover`

 Glif

 `CommonControls.CheckBoxGlyphHover`

 **Basılan**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Onay kutusu basılı](../../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 165_CheckboxPressed")

 Arka Plan

 `CommonControls.CheckBoxBackgroundPressed`

 Kenarlık

 `CommonControls.CheckBoxBorderPressed`

 Metin

 `CommonControls.CheckBoxTextPressed`

 Glif

 `CommonControls.CheckBoxGlyphPressed`

 **Odaklanmış**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Onay kutusu odaklanmış](../../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 166_CheckboxFocused")

 Arka Plan

 `CommonControls.CheckBoxBackgroundFocused`

 Kenarlık

 `CommonControls.CheckBoxBorderFocused`

 Metin

 `CommonControls.CheckBoxTextFocused`

 Glif

 `CommonControls.CheckBoxGlyphFocused`

### <a name="drop-boxcombo-box-controls"></a>Açılan kutusu/birleşik giriş kutusu denetimleri
 ![DROP&#45;aşağı&#47;birleşik giriş kutusu kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303 167_DropDownComboBoxRedline")

 Kullan...
açılan listeler ve birleşik giriş kutuları da belgeyi bir parçası olan.

 Kullanmayın...
 -   bir açılan veya birleşik giriş kutusu değil herhangi bir UI için.

- için bir [açılan](../../misc/shared-colors.md#BKMK_CommandDropDown) veya [birleşik giriş kutusu](../../misc/shared-colors.md#BKMK_CommandComboBox) komut çubuğunda.

  **Default**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![DROP&#45;aşağı&#47;birleşik giriş kutusu](../../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 168_DropDownComboBox")

  Arka Plan

  `CommonControls.ComboBoxBackground`

  Kenarlık

  `CommonControls.ComboBoxBorder`

  Metin

  `CommonControls.ComboBoxText`

  Ayırıcı

  `CommonControls.ComboBoxSeparator`

  Glif

  `CommonControls.ComboBoxGlyph`

  Simge arka plan

  `CommonControls.ComboBoxGlyphBackground`

  **Devre dışı**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![DROP&#45;aşağı&#47;birleşik giriş kutusu devre dışı](../../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")

  Arka Plan

  `CommonControls.ComboBoxBackgroundDisabled`

  Kenarlık

  `CommonControls.ComboBoxBorderDisabled`

  Metin

  `CommonControls.ComboBoxTextDisabled`

  Ayırıcı

  `CommonControls.ComboBoxSeparatorDisabled`

  Glif

  `CommonControls.ComboBoxGlyphDisabled`

  Simge arka plan

  `CommonControls.ComboBoxGlyphBackgroundDisabled`

  **Vurgulu**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![DROP&#45;aşağı&#47;birleşik giriş kutusu üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")

  Arka Plan

  `CommonControls.ComboBoxBackgroundHover`

  Kenarlık

  `CommonControls.ComboBoxBorderHover`

  Metin

  `CommonControls.ComboBoxTextHover`

  Ayırıcı

  `CommonControls.ComboBoxSeparatorHover`

  Glif

  `CommonControls.ComboBoxGlyphHover`

  Simge arka plan

  `CommonControls.ComboBoxGlyphBackgroundHover`

  **Basılan**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![DROP&#45;aşağı&#47;basılı birleşik giriş kutusu](../../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")

  Arka Plan

  `CommonControls.ComboBoxBackgroundPressed`

  Kenarlık

  `CommonControls.ComboBoxBorderPressed`

  Metin

  `CommonControls.ComboBoxTextPressed`

  Ayırıcı

  `CommonControls.ComboBoxSeparatorPressed`

  Glif

  `CommonControls.ComboBoxGlyphPressed`

  Simge arka plan

  `CommonControls.ComboBoxGlyphBackgroundPressed`

  **Odaklanmış**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![DROP&#45;aşağı&#47;odaklanmış birleşik giriş kutusu](../../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")

  Arka Plan

  `CommonControls.ComboBoxBackgroundFocused`

  Kenarlık

  `CommonControls.ComboBoxBorderFocused`

  Metin

  `CommonControls.ComboBoxTextFocused`

  Ayırıcı

  `CommonControls.ComboBoxSeparatorFocused`

  Glif

  `CommonControls.ComboBoxGlyphFocused`

  Simge arka plan

  `CommonControls.ComboBoxGlyphBackgroundFocused`

  **Giriş metin seçimi**

  Bileşen

  Öğe

  Belirteç adı: Category.color

  ![DROP&#45;aşağı&#47;birleşik giriş kutusu metin girişi](../../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303 173_DropDownComboBoxTextInput")

  Vurgulayın

  `CommonControls.ComboBoxTextInputSelection`

  **Basılan – liste öğesi görünümü**

  ![DROP&#45;aşağı&#47;birleşik giriş kutusu liste görünümü](../../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")

  Arka Plan

  `CommonControls.ComboBoxListBackground`

  `CommonControls.ComboBoxListBackgroundHover`

  `CommonControls.ComboBoxListItemBackgroundPressed`

  `CommonControls.ComboBoxListItemBackgroundFocused`

  Kenarlık

  `CommonControls.ComboBoxListBorder`

  `CommonControls.ComboBoxListBorderHover`

  `CommonControls.ComboBoxListBorderPressed`

  `CommonControls.ComboBoxListBorderFocused`

  Öğe metni

  `CommonControls.ComboBoxListItemText`

  `CommonControls.ComboBoxListItemTextHover`

  `CommonControls.ComboBoxListItemTextPressed`

  `CommonControls.ComboBoxListItemTextFocused`

  Arka plan gölge

  `CommonControls.ComboBoxListBackgroundShadow`

### <a name="tabular-data-grid-controls"></a>Tablosal veri (Kılavuz) denetimleri
 Tablosal veri denetimleri, kılavuz denetimleri olarak da bilinir, yüksek miktarda verilerden oluşan birden çok sütunda sunmak için kullanılan Visual Studio için ortak denetimlerdir. Standart tablo veri denetimleri Visual Studio içinde birden fazla yerde bulunabilir: hata listesi araç penceresi, IntelliTrace raporlar ve diğerlerinin yanı sıra bellek yığın görünümü. Her zaman sağlanan standart tablo veri denetimleri kullanın. Bazı ender durumlarda, standart tablo veri denetimleri erişimi olmayabilir. Bu gibi durumlarda, kullanıcı Arabirimi diğer Visual Studio'da tablosal veri denetimleriyle tutarlı olduğundan emin olmak için aşağıdaki belirteci adları kullanın.

 ![Tablo veri &#40;kılavuz denetimi&#41; kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303 197_TabularDataGridControlRedline")

 Kullan...
için tablo veya kılavuz denetimleri.

 Kullanmayın...
bir tablo veya kılavuz denetimi değil herhangi bir UI için.

#### <a name="column-headers"></a>Sütun üstbilgileri
 Sütun üst bilgilerini arka plan, kenarlık, başlık metnini ve kılavuz, sütuna göre sıralanmış genellikle kullanılan isteğe bağlı bir karakter oluşur.

 Durum

 Öğe

 Belirteç adı: Category.color

 Varsayılan

 Arka Plan

 `Header.Default`

 Ön plan (metin)

 `Environment.CommandBarTextActive`

 Ön plan (karakter)

 `Header.Glyph`

 Kenarlık

 `Header.SeparatorLine`

 Vurgulu

 Arka Plan

 `Header.MouseOver`

 Ön plan (metin)

 `Environment.CommandBarTextHover`

 Ön plan (karakter)

 `Header.MouseOverGlyph`

 Kenarlık

 `Header.SeparatorLine`

 Basılan

 Arka Plan

 `CommonControls.CheckBoxBackgroundPressed`

 Ön plan (metin)

 `CommonControls.CheckBoxBorderPressed`

 Ön plan (karakter)

 `CommonControls.CheckBoxTextPressed`

 Kenarlık

 `CommonControls.CheckBoxGlyphPressed`

#### <a name="list-view-items"></a>Liste Görünümü öğelerini
 Liste Görünümü öğelerini bir arka plan ve içeriği oluşur. İçerik, metin, simge veya her ikisi de olabilir.

 Durum

 Öğe

 Belirteç adı: Category.color

 Varsayılan

 Arka Plan

 Geçirgen

 Ön plan (metin)

 `Environment.CommandBarTextActive`

 Kenarlık

 Yok.

 Seçili (etkin)

 Arka Plan

 `TreeView.SelectedItemActive`

 Ön plan (metin)

 `TreeView.SelectedItemActiveText`

 Kenarlık

 Yok.

 Seçili (etkin)

 Arka Plan

 `TreeView.SelectedItemInactive`

 Ön plan (metin)

 `TreeView.SelectedItemInactiveText`

 Kenarlık

 Yok.

## <a name="manifest-designer"></a>Bildirim Tasarımcısı
 Bildirim Tasarımcısı, Windows 8 ve Windows Phone 8 projeleri bildirim dosyasında düzenlemek daha kolay bir şekilde tasarlanmıştır. Tüketim için kullanılabilir paylaşılan çerçeve ederken tasarım düzeni ve yön/gezinme sekmeleri ve genel yapısı renklerini eşleştirmek için uygun olabilir. Düzen ayrıntıları hakkında daha fazla bilgi için bkz. [Visual Studio için Düzen](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

 ![Bildirim Tasarımcısı kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303 175_ManifestDesignerRedline")

 Kullan...
 -   Bildirim Tasarımcısı için benzer tasarımcıları.

- bir düzenleyici belgesi içinde üst kısmındaki ortak sekme denetimleri kullanarak yerine yanı sıra.

  Kullanmayın...
  -   altıdan fazla sekme varsa.

- Bildirim Tasarımcısı gibi yapılandırılmamış herhangi bir UI için.

  Durum

  Bileşen

  Öğe

  Belirteç adı: Category.color

  Varsayılan (Seçili)

  Tab

  Arka Plan

  `ManifestDesigner.TabActive`

  Kenarlık

  Yok.

  Açıklama bölmesi

  Arka Plan

  `ManifestDesigner.DescriptionPane`

  İçerik sayfası

  Arka Plan

  `ManifestDesigner.Background`

  İletişim yardımcı metni

  `ManifestDesigner.WatermarkText`

  Bu belirteç adı işlevini eşleşmiyor.

  Olmayan seçili

  Tab

  Arka Plan

  `ManifestDesigner.Tab.Inactive`

  Vurgulu

  Tab

  Arka Plan

  `ManifestDesigner.Tab.Mouseover`

## <a name="tagging"></a>Etiketleme
 Visual Studio etiketleme, izleme amacıyla aranabilir anahtar sözcükleri bildirmek bir kullanıcı sağlayan destekler. Örneğin, proje yöneticileri ve geliştiriciler Team Foundation Server (TFS) iş öğelerini etiketlemek için kullanabilirsiniz. Aşağıdaki tablolarda, etiket hem üzerine gelin ve seçili durumlardan görünür "simge" Kapat"karakteri için renk adlar verin.

 ![Etiketleme kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303 176_TaggingRedline")

 Kullan...
Kullanıcı Arabirimi için etiketleme destekleyen.

 Kullanmayın...
başka türde UI için.

### <a name="tag"></a>Etiket
 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Etiket](../../extensibility/ux-guidelines/media/0303-177-tag.png "0303 177_Tag")

 **Default**

 Arka Plan

 `Tag.Background`

 Ön plan (metin)

 `Tag.Background`

 ![Üzerine gelindiğinde etiketi](../../extensibility/ux-guidelines/media/0303-178-taghover.png "0303 178_TagHover")

 **Vurgulu**

 Arka Plan

 `Tag.HoverBackground`

 Ön plan (metin)

 `Tag.HoverBackgroundText`

 ![Basılan etiketi](../../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303 179_TagPressed")

 **Basılan**

 Arka Plan

 `Tag.PressedBackground`

 Ön plan (metin)

 `Tag.PressedBackgroundText`

 ![Seçili etiketi](../../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303 180_TagSelected")

 **Seçili**

 Arka Plan

 `Tag.SelectedBackground`

 Ön plan (metin)

 `Tag.SelectedBackgroundText`

### <a name="glyph-close-icon"></a>Glif (Kapat simgesi)
 **Default**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Etiket &#40;glif&#41;](../../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303 181_TagGlyph")

 **Varsayılan (etiketi varsayılan)**

 Arka Plan

 Yok

 Ön plan (karakter)

 `Tag.TagHoverGlyph`

 **Vurgulu**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Etiket &#40;glif&#41; üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 182_TagGlyphHover")

 **Vurgulu (etiketi varsayılan)**

 Arka Plan

 `Tag.TagHoverGlyphHoverBackground`

 Ön plan (karakter)

 `Tag.TagHoverGlyphHover`

 Kenarlık

 `Tag.TagHoverGlyphHoverBorder`

 **Basılan**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Etiket &#40;glif&#41; basılı](../../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 183_TagGlyphPressed")

 **Basılan (etiketi varsayılan)**

 Arka Plan

 `Tag.TagHoverGlyphPressedBackground`

 Ön plan (karakter)

 `Tag.TagHoverGlyphPressed`

 Kenarlık

 `Tag.TagHoverGlyphPressedBorder`

 **Seçili simge varsayılan etiket**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Seçili etiketi](../../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303 184_TagSelected")

 **Varsayılan (Seçili etiketi)**

 Arka Plan

 Yok

 Ön plan (karakter)

 `Tag.TagSelectedGlyph`

 **Etiket seçili simge üzerine gelme**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Üzerine gelindiğinde seçili etiketi](../../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 185_TagSelectedHover")

 **Vurgulu (Seçili etiketi)**

 Arka Plan

 `Tag.TagSelectedGlyphHoverBackground`

 Ön plan (karakter)

 `Tag.TagSelectedGlyphHover`

 Kenarlık

 `Tag.TagSelectedGlyphHoverBorder`

 **Etiket seçili/basılı karakteri**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Seçili etiketi basılı](../../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 186_TagSelectedPressed")

 **(Basılı etiketi seçili)**

 Arka Plan

 `Tag.TagSelectedGlyphPressedBackground`

 Foreground(glyph)

 `Tag.TagSelectedGlyphPressed`

 Kenarlık

 `Tag.TagSelectedGlyphPressedBorder`

## <a name="shell"></a>Kabuk

### <a name="background"></a>Arka Plan
 Ortam arka plan iki katmandan oluşur. Tüm IDE kapsayan düz renk alt katmanıdır. Üst katman komut raf altında ve araç penceresi otomatik gizleme kanalları IDE'nin sol ve sağ kenarları arasındaki uyar. Visual Studio 2013'ten itibaren aynı açık ve koyu Tema rengi için üst ve alt arka plan katmanlarının ayarlanır.

 ![Kabuk arka plan kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303 187_ShellBackgroundRedline")

 Kullan...
Visual Studio ortamının arka eşleştirmek istediğiniz yerde.

 Kullanmayın...
 -   arka plan yüzeyleri olmayan basamak için dolgu olarak.

- ön plan öğeleri yerleştirmek istediğiniz arka plan olarak.

  Bileşen

  Öğe

  Belirteç adı: Category.color

  Alt Katman

  Arka Plan

  `Environment.EnvironmentBackground`

  Bileşen

  Öğe

  Belirteç adı: Category.color

  Üst katman

  Arka Plan

  *Visual Studio 2013'ün açık ve koyu temaları aynı renk değeri kümesine gradyan durdurur.*

  `Environment.EnvironmentBackgroundGradientBegin`

  `Environment.EnvironmentBackgroundGradientEnd`

  `Environment.EnvironmentBackgroundGradientMiddle1`

  `Environment.EnvironmentBackgroundGradientMiddle2`

### <a name="command-shelf"></a>Komut raf
 İki simge adları, komut raf planları kullanılır: menü çubuğu burada yer alan, biri burada komut çubukları sit ayarlayın. Bir tek tek komut çubuğu grubu "Komut çubuğunda" bölümünde daha ayrıntılı olarak ele alınmıştır, kendi arka plan renk değerleri var. Menü çubuğu ve komut çubuğundan metin sırasıyla menü ve komut çubuğu bölümlerinde ele alınmıştır.

 ![Komut raf kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303 188_CommandShelfRedline")

 Kullan...
 -   menüleri ve araç çubukları yerleştirdiğiniz alanları.

- doğru arka plan /? ön plan belirteç adı birleşimi.

  Kullanmayın...
  bir komut raf için benzer olmayan alanları.

  Bileşen

  Öğe

  Belirteç adı: Category.color

  Menü çubuğu

  Arka Plan

  *Visual Studio 2013'ün açık ve koyu temaları aynı renk değeri kümesine gradyan durdurur.*

  `Environment.CommandShelfHighlightGradientBegin`

  `Environment.CommandShelfHighlightGradientMiddle`

  `Environment.CommandShelfHighlightGradientEnd`

  Komut çubuğu

  Arka Plan

  *Visual Studio 2013'ün açık ve koyu temaları aynı renk değeri kümesine gradyan durdurur.*

  `Environment.CommandShelfBackgroundGradientBegin`

  `Environment.CommandShelfBackgroundGradientMiddle`

  `Environment.CommandShelfBackgroundGradientEnd`

## <a name="toolbox"></a>Araç Kutusu
 Araç, Visual Studio'daki sık kullanılan ortak bir araç pencereleri biridir. Aslında bir ağaç denetimi ile özel teması ve stil uygulanmış olduğu.

 ![Araç kutusu kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303 189_ToolboxRedline")

 Kullan...
ne zaman, her zaman shell araç ile tutarlı olmasını istediğiniz araç penceresi tasarlarken.

 Kullanmayın...
Araç kutusu kullanıcı Arabirimi, benzer olmayan her şey için ya da değişiklik shell araç kutusuna renklerini, kullanıcı Arabirimi sorunları olup olmadığını olacak emin değilseniz.

 **Default**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Araç kutusu üst düğümü](../../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 190_ToolboxParentNode")

 **Üst düğümü**

 ![Araç kutusu alt düğüm](../../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 191_ToolboxChildNode")

 **Alt düğümü**

 Arka Plan

 `Environment.ToolboxContent`

 Başlıkları

 `Environment.ToolWindowBackground`

 Bireysel öğeleri veya hiçbir kullanılabilir denetimleri, tüm pencere

 Kenarlık

 Yok.

 Ön plan (karakter)

 `Environment.ToolboxContent`

 Ön plan (metin)

 `Environment.ToolboxContent`

 **Vurgulu**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Üzerine gelindiğinde Araç kutusu alt düğüm](../../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")

 **Alt düğümü üzerine gelindiğinde Araç kutusu**

 Arka Plan

 `Environment.ToolboxContentMouseOver`

 Yalnızca tek tek öğeleri

 Kenarlık

 Yok.

 Ön plan (metin)

 `Environment.ToolboxContentMouseOver`

 Yalnızca tek tek öğeleri

 **Seçili**

 Bileşen

 Öğe

 Belirteç adı: Category.color

 ![Araç kutusu üst düğümü odaklanmış](../../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")

 **Odaklanmış üst düğümü**

 ![Araç kutusu alt düğüm odaklanmış](../../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")

 **Odaklanmış alt düğümü**

 Arka Plan

 `TreeView.SelectedItemActive`

 Gelen [ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisi

 Kenarlık

 `TreeView.FocusVisualBorder`

 Gelen [ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisi

 Ön plan (karakter)

 `TreeView.SelectedItemActive`

 Gelen [ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisi

 Ön plan (metin)

 `TreeView.SelectedItemActive`

 Gelen [ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisi

 ![Araç kutusu üst düğümü odaklanmadan](../../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")

 **Plana odaklanmadan üst düğümü**

 ![Araç kutusu alt düğüm odaklanmadan](../../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")

 **Plana odaklanmadan alt düğümü**

 Arka Plan

 `TreeView.SelectedItemInactive`

 Gelen [ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisi

 Kenarlık

 Yok.

 Ön plan (karakter)

 `TreeView.SelectedItemInactive`

 Gelen [ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisi

 Ön plan (metin)

 `TreeView.SelectedItemInactive`

 Gelen [ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisi
