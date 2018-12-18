---
title: Visual Studio için renkleri paylaşılan | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 19d628f2f83943b88a415699dddd78f033597983
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833349"
---
# <a name="shared-colors-for-visual-studio"></a>Visual Studio için paylaşılan renkler
Ortak Visual Studio shell öğeleri kullanan kullanıcı Arabirimi tasarlama konusunda ya da arabirimi öğeniz benzer özellikleri ile tutarlı olmasını istediğiniz seçin ve renkleri atamak için paket tanım dosyalarında mevcut belirteci adları kullanın. Bu tema eklendiğinde veya güncelleştirildiğinde, otomatik olarak güncelleştirir ve kullanıcı Arabirimi ile genel Visual Studio ortamının tutarlı kalmasını sağlar.  

Bu makalede, sık kullanılan UI öğeleri ve benzer kullanıcı Arabirimi oluşturma sırasında başvuran kullandıkları, belirteç adlarını açıklanır. Bu renk belirteçleri erişim hakkında ayrıntılı bilgi için bkz: [VSColor hizmet](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  

Doğru belirteci adları kullandığınızdan emin olun:  

-   **İşlevi, renk üzerinde dayalı belirteç adları kullanın.** Ortak paylaşılan renkler, belirli bir arabirim öğeleri ile ilişkili ve yalnızca aynı veya benzer özellikler için kullanılmak üzere tasarlanmıştır. Örneğin, dönen ilerleme animasyonunun basılı açılan kutusu rengi renk istediğiniz olduğundan yeniden kullanmayın. Birleşik giriş kutusu ve animasyon işlevleri farklıdır ve renk birleşik giriş kutusu değişikliklerle ilişkili, artık animasyon öğeniz için uygun bir renk olabilir. Renk tutarlı kullanımı, kullanıcılarınızın yönlendirmek ve Karışıklığı önlemek yardımcı olur.  

-   **Arka plan ve metin renklerini doğru birlikte kullanın.** Metin ile kullanılmaya yönelik arka plan renklerini, ilişkili metin rengi sahip olur. Metin renkler, arka plan bilgileri için belirtilen dışında kullanmayın. İlişkili metin rengi değilse, bu arka plan rengi metni görüntülemek beklediğiniz tüm yüzeyi için kullanmayın. Diğer metin ve arkaplan renklerini birleşimlerini okunamayan bir arabirimde neden olabilir.  

-   **Konumlarına için uygun olan denetim renkleri kullanın.** Bazı durumlarda, bazı Visual Studio denetimler ayrı kenarlık ve arka plan renkleri yok. Bunun yerine, bu yüzeyleri arkasına renkleri ayarlama seçin. Her zaman burada denetimin yerleştirme konumu için uygun olan belirteci adları kullandığınızdan emin olun.  

> [!IMPORTANT]
> "Başlangıç sayfası" veya "Şarabıı." kategoride bulunan belirteçleri kullanmayın  

## <a name="common-shared-controls"></a>Paylaşılan ortak denetimleri

Standart bir Visual Studio komut çubuğu, özelliğini kullandığınızda, stil uygulanmış bir kabuk denetimleri için erişim gerekir. Bu ortak denetimleri yeniden şablon eklememelisiniz. Ancak, özel bir komut çubuğu oluşturmak ihtiyacınız varsa, özel denetimler de gerekebilir. Bu durumda, kullanıcı Arabirimi Visual Studio geri kalanı ile tutarlı olmasını sağlayın, her biri aşağıdaki denetimleri için doğru belirteci adları kullandığınızdan emin olun.

### <a name="button-controls"></a>Düğme denetimleri

![Düğme denetimi kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303 155_ButtonControlRedline")

| Kullan... | Kullanmayın... |
| --- | --- |
| Visual Studio temasından (açık, koyu, mavi veya bir sistem yüksek karşıtlıklı tema) ile tümleştirmek istediğiniz belge kutusu içinde... düğmeler için. | Visual Studio temasını bulunmayan özel bir arka plan karşı görüntüleyecek... düğmeler için. |

**Düğme: standart durumu**

![Standart düğme](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Standart düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Düğme | `CommonControls.Button` |
| Düğme kenarlığı | `CommonControls.ButtonBorder` |

**Düğme: varsayılan durumu**

![Varsayılan düğme](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Varsayılan düğme

| Öğe | Belirteç adı: Category.color | 
| --- | --- | 
| Düğme | `CommonControls.ButtonDefault` |
| Düğme kenarlığı | `CommonControls.ButtonBorderDefault` |

**Düğme: devre dışı bırakılmış**  

![Devre dışı bırakılmış düğmesi](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />Devre dışı bırakılmış düğmesi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Düğme | `CommonControls.ButtonDisabled` |
| Düğme kenarlığı | `CommonControls.ButtonBorderDisabled` |

**Düğme: vurgulu durumu**  

![Düğme üzerine gelindiğinde](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Üzerine gelindiğinde düğmesi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Düğme | `CommonControls.ButtonHover` |
| Düğme kenarlığı | `CommonControls.ButtonBorderHover` |

**Düğme: basılı durumu**  

![Basılan düğme](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />Basılan düğme  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Düğme | `CommonControls.ButtonPressed` |
| Düğme kenarlığı | `CommonControls.ButtonBorderPressed` |

**Düğme: odaklanmış durumu**  

![Odaklanmış düğmesi](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Odaklanmış düğmesi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Düğme | `CommonControls.ButtonFocused` |
| Düğme kenarlığı | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Onay kutusu denetimleri  
![Onay kutusunu (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303 161_CheckboxRedline")<br />Onay kutusunu (kırmızı çizgi)  

| Kullan... | Kullanmayın... |
| --- | --- |
| Belgenin içinde bulunan onay kutusu denetimleri için... yanı sıra. | ... herhangi bir UI için bu onay kutusu denetimi değil. |

**Onay kutusu: varsayılan durumu**  

![Onay kutusu](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303 162_Checkbox")<br />Varsayılan onay kutusu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `CommonControls.CheckBoxBackground` |
| Kenarlık | `CommonControls.CheckBoxBorder` |
| Metin | `CommonControls.CheckBoxText` |
| Glif | `CommonControls.CheckBoxGlyph` |

**Onay kutusu: devre dışı durum**  

![Devre dışı onay kutusu](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303 163_CheckboxDisabled")<br />Devre dışı onay kutusu  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `CommonControls.CheckBoxBackgroundDisabled` |
| Kenarlık | `CommonControls.CheckBoxBorderDisabled` |
| Metin | `CommonControls.CheckBoxTextDisabled` |
| Glif | `CommonControls.CheckBoxGlyphDisabled` |

**Onay kutusu: duruma getirin**  

 ![Onay kutusu üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303 164_CheckboxHover")<br />Üzerine gelindiğinde onay kutusu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `CommonControls.CheckBoxBackgroundHover` |
| Kenarlık | `CommonControls.CheckBoxBorderHover` |
| Metin | `CommonControls.CheckBoxTextHover` |
| Glif | `CommonControls.CheckBoxGlyphHover` |  

**Onay kutusu: basılı durumu**  

![Basılan onay kutusunu](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303 165_CheckboxPressed")<br />Basılan onay kutusu  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `CommonControls.CheckBoxBackgroundPressed` |
| Kenarlık | `CommonControls.CheckBoxBorderPressed` |
| Metin | `CommonControls.CheckBoxTextPressed` |
| Glif | `CommonControls.CheckBoxGlyphPressed` |  

**Onay kutusu: odaklanmış durumu**  

![Odaklanmış onay kutusunu](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303 166_CheckboxFocused")<br />Odaklanmış onay kutusu  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `CommonControls.CheckBoxBackgroundFocused` |
| Kenarlık | `CommonControls.CheckBoxBorderFocused` |
| Metin | `CommonControls.CheckBoxTextFocused` |
| Glif | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Açılan listeler ve birleşik giriş kutuları
![Aşağı/birleşik açılır kutusunu (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303 167_DropDownComboBoxRedline")<br />Aşağı/birleşik açılır kutusunu (kırmızı çizgi)  

| Kullan... | Kullanmayın... |
| --- | --- |
| ... açılan listeler ve birleşik giriş kutuları belgede iyi. | ... için herhangi bir kullanıcı Arabirimi, açılan veya birleşik giriş kutusu değil. |  
| | Komut çubuğu için... [açılan listeler](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) veya [birleşik giriş kutuları](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Açılan listeler ve birleşik giriş kutuları: varsayılan durumu**  

![Varsayılan bırakma-aşağı/birleşik giriş kutusu](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303 168_DropDownComboBox")<br />Varsayılan bırakma-aşağı/birleşik giriş kutusu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `CommonControls.ComboBoxBackground` |
| Kenarlık | `CommonControls.ComboBoxBorder` |
| Metin | `CommonControls.ComboBoxText` |
| Ayırıcı | `CommonControls.ComboBoxSeparator` |
| Glif | `CommonControls.ComboBoxGlyph` |
| Simge arka plan | `CommonControls.ComboBoxGlyphBackground` |

**Açılan listeler ve birleşik giriş kutuları: devre dışı durum**  

![Devre dışı bırakma-aşağı/birleşik giriş kutusu](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")<br />Devre dışı bırakma-aşağı/açılan kutusu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `CommonControls.ComboBoxBackgroundDisabled` |
| Kenarlık | `CommonControls.ComboBoxBorderDisabled` |
| Metin | `CommonControls.ComboBoxTextDisabled` |
| Ayırıcı | `CommonControls.ComboBoxSeparatorDisabled` |
| Glif | `CommonControls.ComboBoxGlyphDisabled` |
| Simge arka plan | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Açılan listeler ve birleşik giriş kutuları: duruma getirin**  

![Bırakma-aşağı/birleşik giriş kutusu üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")<br />Üzerine gelindiğinde bırakma-aşağı/birleşik giriş kutusu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `CommonControls.ComboBoxBackgroundHover` |
| Kenarlık | `CommonControls.ComboBoxBorderHover` |
| Metin | `CommonControls.ComboBoxTextHover` |
| Ayırıcı | `CommonControls.ComboBoxSeparatorHover` |
| Glif | `CommonControls.ComboBoxGlyphHover` |
| Simge arka plan | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Açılan listeler ve birleşik giriş kutuları: basılı durumu**  

![Bırakma-aşağı/birleşik giriş kutusu basılı](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")<br />Basılı bırakma-aşağı/birleşik giriş kutusu  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `CommonControls.ComboBoxBackgroundPressed` |
| Kenarlık | `CommonControls.ComboBoxBorderPressed` |
| Metin | `CommonControls.ComboBoxTextPressed` |
| Ayırıcı | `CommonControls.ComboBoxSeparatorPressed` |
| Glif | `CommonControls.ComboBoxGlyphPressed` |
| Simge arka plan | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Açılan listeler ve birleşik giriş kutusu liste öğesi görünümü: basılı durumu**  

 ![Liste öğesi görünümü basılı aşağı/birleşik açılır kutusunu](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")<br />Liste öğesi görünümü basılı bırakma-aşağı/açılan kutusu  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Kenarlık | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Öğe metni | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Arka plan gölge | `CommonControls.ComboBoxListBackgroundShadow` |

**Açılan listeler ve birleşik giriş kutuları: odaklanmış durumu**  

![Odağı aşağı/birleşik açılır kutusu](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")<br />Odağı aşağı/birleşik açılır kutusu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `CommonControls.ComboBoxBackgroundFocused` |
| Kenarlık | `CommonControls.ComboBoxBorderFocused` |
| Metin | `CommonControls.ComboBoxTextFocused` |
| Ayırıcı | `CommonControls.ComboBoxSeparatorFocused` |
| Glif | `CommonControls.ComboBoxGlyphFocused` |
| Simge arka plan | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Açılan listeler ve birleşik giriş kutuları: metin seçimi giriş**  

![Aşağı/birleşik açılır kutusunda metin seçimi giriş](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303 173_DropDownComboBoxTextInput")<br />Giriş metin seçimi, bırakma-aşağı/birleşik giriş kutusu  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Vurgulayın | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Tablosal veri (Kılavuz) denetimleri  
Tablosal veri denetimleri, kılavuz denetimleri olarak da bilinir, yüksek miktarda verilerden oluşan birden çok sütunda sunmak için kullanılan Visual Studio için ortak denetimlerdir. Standart tablo veri denetimleri Visual Studio içinde birden fazla yerde bulunabilir: hata listesi araç penceresi, IntelliTrace raporlar ve diğerlerinin yanı sıra bellek yığın görünümü. Her zaman sağlanan standart tablo veri denetimleri kullanın. Bazı ender durumlarda, standart tablo veri denetimleri erişimi olmayabilir. Bu gibi durumlarda, kullanıcı Arabirimi diğer Visual Studio'da tablosal veri denetimleriyle tutarlı olduğundan emin olmak için aşağıdaki belirteci adları kullanın.  

![Tablosal veri Kılavuzu denetimi (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303 197_TabularDataGridControlRedline")<br />Tablosal veri Kılavuzu denetimi (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |
| ... için tablo veya kılavuz denetimleri. | ... için herhangi bir kullanıcı Arabirimi, bir tablo veya kılavuz denetimi değil. |

#### <a name="column-headers"></a>Sütun üstbilgileri  
Sütun üst bilgilerini arka plan, kenarlık, başlık metnini ve kılavuz, sütuna göre sıralanmış genellikle kullanılan isteğe bağlı bir karakter oluşur.  

**Sütun üst bilgisine: varsayılan durumu**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Header.Default` |
| Ön plan (metin) | `Environment.CommandBarTextActive` |
| Ön plan (karakter) | `Header.Glyph` |
| Kenarlık | `Header.SeparatorLine` |

**Sütun üst bilgisine: duruma getirin**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Header.MouseOver` |
| Ön plan (metin) | `Environment.CommandBarTextHover` |
| Ön plan (karakter) | `Header.MouseOverGlyph` |
| Kenarlık | `Header.SeparatorLine` |

**Sütun üst bilgisine: basılı durumu**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `CommonControls.CheckBoxBackgroundPressed` |
| Ön plan (metin) | `CommonControls.CheckBoxBorderPressed` |
| Ön plan (karakter) | `CommonControls.CheckBoxTextPressed` |
| Kenarlık | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Liste Görünümü öğelerini  
 Liste Görünümü öğelerini bir arka plan ve içeriği oluşur. İçerik, metin, simge veya her ikisi de olabilir.  

**Liste Görünümü öğelerini: varsayılan durumu**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | Geçirgen |
| Ön plan (metin) | `Environment.CommandBarTextActive` |
| Kenarlık | Yok. |

**Liste öğeleri görüntüle: Etkin durumu**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `TreeView.SelectedItemActive` |
| Ön plan (metin) | `TreeView.SelectedItemActiveText` |
| Kenarlık | Yok. |

**Liste öğeleri görüntüle: etkin olmayan duruma**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `TreeView.SelectedItemInactive` |
| Ön plan (metin) | `TreeView.SelectedItemInactiveText` |
| Kenarlık | Yok. |  

### <a name="ui-text"></a>UI metni

#### <a name="instructional-text"></a>Açıklayıcı metni
Şeyi bir iletişim kutusu veya belge sayfasında tanınmış bir ana açıklama açıklayıcı metni sağlar.

![Varsayılan eğitici metin](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Varsayılan eğitici metin

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>İkincil eğitici metin
Belge sayfaları metin ve denetimleri çok sayıda'de, bazı eğitici metin farklı renk değeri kullanır. Bu, en önemli bilgileri iletmek ve genel kullanıcı Arabirimi öğeleri yoğunluğunu azaltmak için yardımcı olur. (Ayrıca bkz: bölüm ipucu metnini aşağıda.)

![İkincil eğitici metin](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />İkincil eğitici metin

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>İpucu metni
İpucu metni boş bir denetimi, bir denetimin altında ya da bundan sonra yapmanız gerekenler kullanıcıya göstermek için bir boş belge yüzeyine görünür. İpucu metnini penceresini veya denetim arka plan ile kullanabilirsiniz.

**Varsayılan İpucu metni**

![Varsayılan ipucu metnini](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Varsayılan İpucu metni

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Environment.ControlEditHintText` |

**Gerekli İpucu metni**

![Gerekli ipucu metnini](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Gerekli İpucu metni

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Environment.ControlRequiredHintText` |
| Arka Plan | `Environment.ControlRequiredBackground` |

**Arama kutusu denetim metin**

> Bkz: [arama kutularını](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) arama denetimi ile ilgili diğer renk belirteçleri.

![Arama kutusu denetim metin](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Arama kutusu denetim metin

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Köprü  
Köprüyü bir ön plan/arka plan çifti sahip olmayan bir denetimdir. Her durumda, doğru koyu gri ve beyaz arka plan üzerinde görünür köprü ön plan rengini kullanın. Köprü denetim için renk belirteç kullanmazsanız, kırmızı yanar "basıldığında" için varsayılan sistem rengi görürsünüz. Bu denetim doğru ortamı renk belirteci kullanmıyor sinyaldir.  

![Köprü (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303 133_HyperlinkRedline")<br />Köprü (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |
| ... gerektiğinde özel bir köprü oluşturabilir. | ... her şey için köprü değil. |

**Köprü: varsayılan durumu**  

![Varsayılan köprüyü](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303 134_Hyperlink")<br />Varsayılan köprüyü

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Environment.PanelHyperlink` |

**Köprü: vurgulu durumu**

![Üzerine gelindiğinde köprü](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303 135_HyperlinkHover")<br />Üzerine gelindiğinde köprü  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Environment.PanelHyperlinkHover` |

**Köprü: basılı durumu**

![Basılan köprü](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303 136_HyperlinkPressed")<br />Basılan köprü  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Environment.PanelHyperlinkPressed` |

**Köprü: devre dışı bırakılmış**

![Devre dışı köprü](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303 137_HyperlinkDisabled")<br />Devre dışı bırakılmış bir köprü  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Infobars  
Infobars her zaman bir belge penceresi veya araç penceresinin üst kısmında görünür ve belirli bir bağlam hakkında daha fazla bilgi sağlamak için kullanılır.  

![Bilgi Çubuğu (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303 138_InfobarRedline")<br />Bilgi Çubuğu (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |
| ... özel infobars oluştururken. | bir bilgi çubuğu için benzer olmayan... için kullanıcı Arabirimi öğeleri. |

**Bilgi Çubuğu: varsayılan durumu**

![Bilgi çubuğu varsayılan](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303 139_Infobar")<br />Varsayılan bilgi çubuğu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `InfoBar.InfoBarBackground` |
| Ön plan (metin) | `InfoBar.InfoBar` |
| Kenarlık | `InfoBar.InfoBarBorder` |

**Bilgi çubuğu Kapat (&times;) düğmesi: varsayılan durumu**

![Varsayılan bilgi çubuğu Kapat (&times;) düğmesini](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Varsayılan bilgi çubuğu Kapat (&times;) düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `InfoBar.CloseButton` |
| Kenarlık | `InfoBar.CloseButtonBorder` |
| Glif | `InfoBar.CloseButtonGlyph` |

**Bilgi çubuğu Kapat (&times;) düğmesi: duruma getirin**

![Bilgi çubuğu Kapat (&times;) düğme üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Bilgi çubuğu Kapat (&times;) üzerine gelindiğinde düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `InfoBar.CloseButtonHover` |
| Kenarlık | `InfoBar.CloseButtonHoverBorder` |
| Glif | `InfoBar.CloseButtonHoverGlyph` |

**Bilgi çubuğu Kapat (&times;) düğmesi: basılı durumu**

![Bilgi çubuğu Kapat basıldığında (&times;) düğmesini](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Bilgi çubuğu Kapat basıldığında (&times;) düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `InfoBar.CloseButtonDown` |
| Kenarlık | `InfoBar.CloseButtonDownBorder` |
| Glif | `InfoBar.CloseButtonDownGlyph` |

**Bilgi çubuğu köprü düğmesi: varsayılan durumu**

![Varsayılan bilgi çubuğu köprü düğme](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Varsayılan bilgi çubuğu köprü düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `InfoBar.Hyperlink` |

**Bilgi çubuğu köprü düğmesi: duruma getirin**

![Bilgi çubuğu köprü düğme üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Bilgi çubuğu üzerine gelindiğinde köprü düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Infobar.HyperlinkMouseOver`<br />(Alt çizgi ile) |

**Bilgi çubuğu köprü düğmesi: basılı durumu**

![Köprü düğmesini basılı bilgi çubuğu](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Köprü düğmesini basılı bilgi çubuğu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Infobar.HyperlinkMouseDown`<br />(Alt çizgi ile) |

**Bilgi Çubuğu (bir cümlede içinde) satır içi köprü: varsayılan durumu**

![Varsayılan satır içi bilgi çubuğu köprü düğme](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Varsayılan satır içi bilgi çubuğu köprü düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `InfoBar.Hyperlink` |

**Bilgi Çubuğu (bir cümlede içinde) satır içi köprü: duruma getirin**

![Bilgi çubuğu satır içi köprü düğme üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Bilgi çubuğu satır içi köprü düğme üzerine gelindiğinde

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Infobar.HyperlinkMouseOver`<br />(Alt çizgi ile) |

**Bilgi Çubuğu (bir cümlede içinde) satır içi köprü: basılı durumu**

![Satır içi köprü düğmesini basılı bilgi çubuğu](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Bilgi çubuğu satır içi köprü düğmesine basıldı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Infobar.HyperlinkMouseDown`<br />(Alt çizgi ile) |

**Bilgi çubuğu düğme: varsayılan durumu**

![Varsayılan bilgi çubuğu düğme](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Varsayılan bilgi çubuğu düğme

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `InfoBar.Button` |
| Ön plan (metin) | `InfoBar.Button` |
| Kenarlık | `InfoBar.ButtonBorder` |

**Bilgi çubuğu düğme: duruma getirin**

![Bilgi çubuğu düğme üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Bilgi çubuğu düğme üzerine gelindiğinde

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `InfoBar.ButtonMouseOver` |
| Ön plan (metin) | `InfoBar.ButtonMouseOver` |
| Kenarlık | `InfoBar.ButtonMouseOverBorder` |

**Bilgi çubuğu düğme: basılı durumu**

![Basılan bilgi çubuğu düğme](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Basılan bilgi çubuğu düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `InfoBar.ButtonMouseDown` |
| Ön plan (metin) | `InfoBar.ButtonMouseDown` |
| Kenarlık | `InfoBar.ButtonMouseDownBorder` |

**Bilgi çubuğu düğme: devre dışı durum**

![Devre dışı bırakılmış bir bilgi çubuğu düğme](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Devre dışı bırakılmış bir bilgi çubuğu düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `InfoBar.ButtonDisabled` |
| Ön plan (metin) | `InfoBar.ButtonDisabled` |
| Kenarlık | `InfoBar.ButtonDisabledBorder` |

**Bilgi çubuğu düğme: odaklanmış durumu**

![Odaklanmış bir bilgi çubuğu düğme](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Odaklanmış bir bilgi çubuğu düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `InfoBar.ButtonFocus` |
| Ön plan (metin) | `InfoBar.ButtonFocus` |
| Kenarlık | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Kaydırma çubukları  
Kaydırma çubukları Visual Studio ortamı tarafından stillere ve temalı olması gerekmez. Ancak, kullanıcı Arabirimi her zaman Visual Studio ortamının bu bölümü ile tutarlı görünmesi kaydırma çubuklarında kullanılan renkleri yararlanmak istediğinize karar verin.  

![Kaydırma çubuğu (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303 140_ScrollbarRedline")<br />Kaydırma çubuğu (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |
| ... Visual Studio kaydırma çubukları eşleştirmek istediğiniz kullanıcı Arabirimi, oluştururken. | ... her şey her zaman aynı istemediğiniz için kaydırma kullanıcı Arabirimi. |

**Kaydırma çubuğu: varsayılan durumu**  

![Varsayılan kaydırma çubuğu](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303 141_Scrollbar")<br />Varsayılan kaydırma çubuğu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Kaydırma çubuğu | `Environment.ScrollBarBackground` |
| Ön plan (Flash) | `Environment.ScrollBarThumbBackground` |

**Kaydırma çubuğu: duruma getirin**

![Kaydırma çubuğu üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303 143_ScrollbarHover")<br />Üzerine gelindiğinde kaydırma çubuğu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Kaydırma çubuğu | `Environment.ScrollBarBackground` |
| Ön plan (Flash) | `Environment.ScrollBarThumbMouseOverBackground` |

*Kaydırma çubuğu: basılı durumu**

![Basılan kaydırma çubuğu](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303 145_ScrollbarPressed")<br />Basılan kaydırma çubuğu  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Kaydırma çubuğu | `Environment.ScrollBarBackground` |
| Ön plan (Flash) | `Environment.ScrollBarThumbPressedBackground` |

**Kaydırma ok: varsayılan durumu**  

![Varsayılan kaydırma çubuğu ok](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303 142_ScrollbarArrow")<br />Varsayılan kaydırma çubuğu oku

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ScrollBarArrowBackground`<br />(Kaydırma çubuğu aynı renge ayarlayın.) |
| Ön plan (karakter) | `Environment.ScrollBarArrowGlyph` |

**Kaydırma ok: duruma getirin**

![Kaydırma çubuğu üzerine gelindiğinde ok](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303 144_ScrollbarArrowHover")<br />Üzerine gelindiğinde kaydırma çubuğu oku  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ScrollBarArrowMouseOverBackground`<br />(Kaydırma çubuğu aynı renge ayarlayın.) |
| Ön plan (karakter) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Kaydırma ok: basılı durumu**  

![Basılan kaydırma çubuğu ok](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303 146_ScrollbarArrowPressed")<br />Basılan kaydırma çubuğu oku

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ScrollBarArrowPressedBackground`<br />(Kaydırma çubuğu aynı renge ayarlayın.) |
| Ön plan (karakter) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="BKMK_SearchBoxes"></a>Arama kutusu  
Mümkün olduğunda, Visual Studio ortamı tarafından sağlanan genel arama denetimini kullanın. Arama kutusuna renklerini bulundu "SearchControl" kategorisinde **ShellColors.pkgdef** giriş alanı, eylem düğmesi, açılan düğmeyi ve açılan menü için belirteç adları içeren dosya.  

Bir arama kutusu bazıları birbirini dışlayan olan çeşitli durumları biri olabilir:  

-   "Odaklı" veya "odaklanmadan" olup olmadığını imleç ve metin kutusundaki için kısaltmasıdır.  

-   Kullanıcının metin kutusuna bir arama sorgusu girişinin için "Etkin" veya "etkin" anlamına gelir.  

-   "Vurgu", kullanıcı (Bu durumda, diğer tüm durumları geçersiz kılar) fare ile arama kutusuna moused anlamına gelir.  

-   "Devre dışı" arama işlevi için geçerli bağlam kapalı anlamına gelir.  

![Arama kutusuna (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303 110_SearchBoxRedline")<br />Arama kutusuna (kırmızı çizgi)  

| Kullan... | Kullanmayın... |
| --- | --- |
| ... olduğunda, tasarlama bir özel arama kutusu. | ... her şey için bir arama kutusu değil. |
| | ... arama her zaman aynı istemediğiniz her şey için kullanıcı Arabirimi kutusu. |

**Arama giriş alanı odaklanır**

![Odaklanmış arama giriş alanı](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")<br />Arama giriş alanı odaklanır  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `SearchControl.FocusedBackground` |
| Ön plan (metin) | `SearchControl.FocusedBackground` |
| Kenarlık | `SearchControl.FocusedBorder` |
| Ayırıcı | `SearchControl.FocusedDropDownSeparator` |

**Giriş odaklanmadan, etkin bir arama alanı**

![Arama giriş alanı odaklanmadan](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")<br />Giriş odaklanmadan, etkin bir arama alanı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `SearchControl.SearchActiveBackground` |
| Ön plan (metin) | `SearchControl.SearchActiveBackground` |
| Kenarlık | `SearchControl.UnfocusedBorder` |
| Ayırıcı | `SearchControl.DropDownSeparator` |

**Giriş odaklanmadan, etkin olmayan bir arama alanı**

![Plana odaklanmadan, etkin olmayan arama giriş alanı](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303 114 1_SearchInputFieldUnfocusedInactive")<br />Giriş odaklanmadan, etkin olmayan bir arama alanı  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `SearchControl.Unfocused` |
| Ön plan (metin) | `SearchControl.Unfocused` |
| Kenarlık | `SearchControl.UnfocusedBorder` |
| Ayırıcı | `SearchControl.DropDownSeparator` |

**Vurgulanan arama giriş alanı (yalnızca metin)**

![Vurgulanan arama giriş alanı](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")<br />Vurgulanan arama giriş alanı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `SearchControl.Selection` |
| Ön plan (metin) | `SearchControl.FocusedBackground` |
| Kenarlık | Yok. |
| Ayırıcı | `SearchControl.FocusedDropDownSeparator` |

**Arama giriş alanı devre dışı bırakıldı**

![Arama giriş alanını devre dışı](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")<br />Arama giriş alanı devre dışı bırakıldı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `SearchControl.Disabled` |
| Ön plan (metin) | `SearchControl.Disabled` |
| Kenarlık | `SearchControl.DisabledBorder` |
| Ayırıcı | `SearchControl.DropDownSeparator` |

**Odaklanmış arama eylem düğmesi**

![Arama eylem düğmesi odaklanmış](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")<br />Odaklanmış arama eylem düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | Yok. |
| Ön plan (arama karakter) | `SearchControl.SearchGlyph` |
| Ön plan (durdurma karakter) | `SearchControl.StopGlyph` |
| Ön plan (NET karakter) | `SearchControl.ClearGlyph` |
| Kenarlık | Yok |

**Plana odaklanmadan arama eylem düğmesi**  

![Plana odaklanmadan arama eylem düğmesi](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")<br />Plana odaklanmadan arama eylem düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (arama karakter) | `SearchControl.SearchGlyph` |
| Ön plan (durdurma karakter) | `SearchControl.StopGlyph` |
| Ön plan (NET karakter) | `SearchControl.ClearGlyph` |
| Kenarlık | Yok |

**Arama eylemi düğmesine basıldı**

![Eylem düğmesi basılı arama](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303 116 1_SearchActionButtonPressed")<br />Arama eylemi düğmesine basıldı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `SearchControl.ActionButtonMouseDown` |
| Ön plan (karakter) | `SearchControl.ActionButtonMouseDownGlyph` |
| Kenarlık | `SearchControl.ActionButtonMouseDownBorder` |

**Devre dışı arama eylem düğmesi**

![Arama eylem düğmesi devre dışı](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")<br />Devre dışı arama eylem düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | Yok. |
| Ön plan (karakter) | `SearchControl.ActionButtonDisabledGlyph` |
| Kenarlık | Yok. |

**Odaklanmış arama açılan düğmesi**

![Odaklanmış arama açılan düğmeyi](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")<br />Odaklanmış arama açılan düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `SearchControl.FocusedDropDownButton` |
| Ön plan (karakter) | `SearchControl.FocusedDropDownButtonGlyph` |
| Kenarlık | `SearchControl.FocusedDropDownButtonBorder` |

**Plana odaklanmadan arama açılan düğmesi**

![Plana odaklanmadan arama açılan düğmeyi](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")<br />Plana odaklanmadan arama açılan düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `SearchControl.UnfocusedDropDownButton` |
| Ön plan (karakter) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Kenarlık | `SearchControl.UnfocusedDropDownButtonBorder` |

**Arama açılan düğmesine basıldı**

![Basılan arama açılan düğmeyi](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303 116 2_SearchDropdownButtonPressed")<br />Arama açılan düğmesine basıldı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `SearchControl.MouseDownDropDownButton` |
| Ön plan (karakter) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Kenarlık | `SearchControl.MouseDownDropDownButtonBorder` |

**Açılan düğmeyi devre dışı arama**

![Arama açılan düğmeyi devre dışı](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")<br />Açılan düğmeyi devre dışı arama

| Öğe | Belirteç adı: Category.color |
| --- | --- |  
| Arka Plan | Yok. |
| Ön plan (karakter) | `SearchControl.DisabledDownButtonGlyph` |
| Kenarlık | Yok. |

#### <a name="search-drop-down-lists"></a>Arama açılan listeler  
Arama kutusunun yanıdaki açılan menüsü diğer Visual Studio açılan menülerde biraz daha karmaşık olma olasılığına sahiptir. "Önerilen aramalar" ve "Seçenekler arama" olarak bölümlerde tek başına veya birlikte menüsünde görünür ve her biri ayrı ayrı renklendirilmiştir. Bir satır da birlikte görünür ve tüm açılan menüden bir kenarlık çevreleyen bu iki bölüme ayırır.  

![Arama açılan listesi (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303 124_SearchDropdownRedline")<br />Arama açılan listesi (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |
| ... özel arama açılan listesini oluştururken. | ... aşağı açılan listesi için diğer bağlamlarda görünür. |
| ... doğru listesi bileşenleri için doğru belirteci adları. | Belirtilen dışındaki... tüm arka plan/ön plan birlikte. |

**Aşağı açılan liste öğelerini ara**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Kenarlık | `SearchControl.PopupBorder` |
| Ayırıcı | `SearchControl.PopupSectionHeaderSeparator` |
| Gölge | `Environment.DropShadowBackground` |

**Önerilen aramalar: varsayılan durumu**

![Önerilen aramalar varsayılan](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303 125_SearchSuggested")<br />Varsayılan önerilen aramalar  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (metin) | `SearchControl.PopupItemText` |

**Önerilen aramalar: duruma getirin**

![Önerilen aramalar üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303 128_SearchSuggestedHover")<br />Üzerine gelindiğinde önerilen aramalar

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (metin) | `SearchControl.PopupMouseOverItemText` |
| Kenarlık | `SearchControl.PopupControlMouseOverBorder` |

**Arama Seçenekleri: varsayılan durumu**

![Arama onay kutusunu](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303 126_SearchCheckbox")<br />Varsayılan arama seçenekleri (onay kutusu)  

![Arama Seçenekleri](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303 127_SearchOptions")<br />Varsayılan arama seçenekleri (bağlantı)  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (onay kutusu metni) | `SearchControl.PopupCheckboxText` |
| Ön plan (bağlantı metni) | `SearchControl.PopupButtonText` |
| Başlık arka plan | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (üst bilgi metni) | `SearchControl.PopupSectionHeaderText` |

**Arama Seçenekleri: duruma getirin**

![Arama Seçenekleri (onay kutusu) üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303 129_SearchCheckboxHover")<br />Üzerine gelindiğinde, (onay kutusu) arama seçenekleri  

![Arama Seçenekleri (bağlantı) üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303 130_SearchOptionsHover")<br />Üzerine gelindiğinde arama seçenekleri (bağlantı)  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (onay kutusu metni) | `SearchControl.PopupCheckboxMouseDownText` |
| Ön plan (bağlantı metni) | `SearchControl.PopupButtonMouseDownText` |
| Kenarlık | `SearchControl.PopupControlMouseOverBorder` |

**Arama Seçenekleri: basılı durumu**  

![Arama Seçenekleri (onay kutusu) basıldı](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")<br />Arama Seçenekleri (onay kutusu) basıldı   

![Arama Seçenekleri (bağlantı) basıldı](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303 132_SearchOptionsPressed")<br />Arama Seçenekleri (bağlantı) basıldı  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Onay kutusu arka plan | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (onay kutusu metni) | `SearchControl.PopupCheckboxMouseDownText` |
| Bağlantı arka plan | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (bağlantı metni) | `SearchControl.PopupButtonMouseDownText` |

###  <a name="BKMK_TreeView"></a> Ağaç görünümleri  
Çözüm Gezgini, Sunucu Gezgini ve sınıf görünümü de dahil olmak üzere birçok araç pencereleri renklerini, renk adlarında tarafından denetlenen bir hiyerarşik kuruluş şeması uygulayan `TreeView` kategorisi. Ağaç görünümünde tüm öğeler, arka plan ve metin renklerini içerir. Alt öğelerinin iç içe geçmiş öğeler de öğe genişletilmiş veya daraltılmış olup olmadığını belirten karakterler var.  

![Ağaç görünümü (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303 147_TreeViewRedline")<br />Ağaç görünümü (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |
| ... herhangi bir hiyerarşik bir kuruluş görünümü uygulamanız gerekir. | ... her şey için bir ağaç görünümüne benzer olmayan. |
| | Belirtilen dışındaki... tüm arka plan/ön plan birlikte. |

**Ağaç görünümü öğesi: varsayılan durumu**

![Varsayılan ağacı görünümü öğesi](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303 148_TreeView")<br />Varsayılan ağacı görünümü öğesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `TreeView.Background` |
| Ön plan (metin) | `TreeView.Background` |
| Ön plan (karakter) | `TreeView.Glyph` |
| Kenarlık | Yok. |

**Ağaç görünümü öğesi: duruma getirin**

![Ağaç görünümü öğesinin üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303 149_TreeViewHover")<br />Üzerine gelindiğinde ağaç görünümü öğesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `TreeView.Background` |  
| Ön plan (metin) | `TreeView.Background` |
| Ön plan (karakter) | `TreeView.GlyphMouseOver` |
| Kenarlık | Yok. |

**Ağaç görünümü öğesi: durum sürükleyin.**

![Ağaç görünümü öğeyi sürükleyin üzerinden](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303 150_TreeViewDragOver")<br />Ağaç görünümü öğesi üzerinde sürükleyin üzerinden  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `TreeView.DragOverItem` |
| Ön plan (metin) | `TreeView.DragOverItem` |
| Ön plan (karakter) | `TreeView.DragOverItemGlyph` |
| Kenarlık | Yok. |

**Ağaç görünümü öğesi: Seçili, odaklanmış durumu**

![Seçili ve ağaç görünümü öğesi odaklanmış](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303 151_TreeViewFocused")<br />Seçilen ve odaklanmış ağaç görünümü öğesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `TreeView.SelectedItemActive` |
| Ön plan (metin) | `TreeView.SelectedItemActive` |
| Ön plan (karakter) | `TreeView.SelectedItemActiveGlyph` |
| Kenarlık | `TreeView.FocusVisualBorder` |

**Ağaç görünümü öğesi: Seçili plana odaklanmadan durumu**  

![Seçilen ve plana odaklanmadan ağaç görünümü öğesi](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303 152_TreeViewUnfocused")<br />Seçilen ve plana odaklanmadan ağaç görünümü öğesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `TreeView.SelectedItemInactive` |
| Ön plan (metin) | `TreeView.SelectedItemInactive` |
| Ön plan (karakter) | `TreeView.SelectedItemInactiveGlyph` |
| Kenarlık | Yok. |

**Ağaç görünümü öğesi: durumu odaklı vurgulanan ve seçili**

![Seçili ve ağaç görünümü öğesinin üzerine gelindiğinde odaklanmış](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")<br />Üzerine gelindiğinde seçili ve odaklanmış ağaç görünümü öğesi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `TreeView.SelectedItemActive` |
| Ön plan (metin) | `TreeView.SelectedItemActive` |
| Ön plan (karakter) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Kenarlık | `TreeView.FocusVisualBorder` |

**Ağaç görünümü öğesi: vurgulanan, seçilen ve plana odaklanmadan durumu**

![Seçilen ve plana odaklanmadan ağaç görünümü öğesinin üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")<br />Üzerine gelindiğinde seçili ve plana odaklanmadan ağaç görünümü öğesi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `TreeView.SelectedItemInactive` |
| Ön plan (metin) | `TreeView.SelectedItemInactive` |
| Ön plan (karakter) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Kenarlık | Yok. |

## <a name="shell-appearance"></a>Shell görünümü

### <a name="background"></a>Arka Plan  
Ortam arka plan iki katmandan oluşur. Tüm IDE kapsayan düz renk alt katmanıdır. Üst katman komut raf altında ve araç penceresi otomatik gizleme kanalları IDE'nin sol ve sağ kenarları arasındaki uyar. Üst ve alt arka plan katmanlarının açık ve koyu Tema rengi aynı şekilde ayarlanmıştır.  

![Visual Studio shell arka plan (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303 187_ShellBackgroundRedline")<br />Visual Studio shell arka plan (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |
| Visual Studio ortamının arka planını eşleştirmek istediğiniz... yerlerde. | ... bir dolgu arka plan yüzeyleri olmayan basamak. |
| | ön plan öğeleri yerleştirmek için... arka plan olarak. |

**Alt Katman shell görünümü**

| Öğe | Belirteç adı: Category.color |
| --- | --- |  
| Arka Plan | `Environment.EnvironmentBackground` |

**Üst katman shell görünümü**

> Visual Studio 2013'ün açık ve koyu temaları aynı renk değeri kümesine gradyan durdurur.

| Öğe | Belirteç adı: Category.color |
| --- | --- |  
| Arka Plan | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |  

### <a name="command-shelf"></a>Komut raf  
İki simge adları, komut raf planları kullanılır: menü çubuğu burada yer alan, biri burada komut çubukları sit ayarlayın. Bir tek tek komut çubuğu grubu "Komut çubuğunda" bölümünde daha ayrıntılı olarak ele alınmıştır, kendi arka plan renk değerleri var. Menü çubuğu ve komut çubuğundan metin sırasıyla menü ve komut çubuğu bölümlerinde ele alınmıştır.  

![Visual Studio komut raf (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303 188_CommandShelfRedline")<br />Visual Studio komut raf (kırmızı çizgi)  

| Kullan... | Kullanmayın... |
| --- | --- |
| menüleri ve araç çubukları yerleştirdiğiniz... alanları. | bir komut raf için benzer olmayan... alanları. |
|... doğru arka plan/ön plan belirteç adı ile birlikte. | |

**Komut raf menü çubuğu**

> Visual Studio 2013'ün açık ve koyu temaları aynı renk değeri kümesine gradyan durdurur.

| Öğe | Belirteç adı: Category.color |
| --- | --- |  
| Arka Plan | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

** Komut raf komut çubuğu **

> Visual Studio 2013'ün açık ve koyu temaları aynı renk değeri kümesine gradyan durdurur.

| Öğe | Belirteç adı: Category.color |
| --- | --- |  
| Arka Plan | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Bildirim Tasarımcısı  
Bildirim Tasarımcısı, Windows 8 ve Windows Phone 8 projeleri bildirim dosyasında düzenlemek daha kolay bir şekilde tasarlanmıştır. Tüketim için kullanılabilir paylaşılan çerçeve ederken tasarım düzeni ve yön/gezinme sekmeleri ve genel yapısı renklerini eşleştirmek için uygun olabilir. Düzen ayrıntıları hakkında daha fazla bilgi için bkz. [Visual Studio için Düzen](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  

![Bildirim Tasarımcısı (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303 175_ManifestDesignerRedline")<br />Bildirim Tasarımcısı (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |
| Bildirim Tasarımcısı için benzer... tasarımcıları için. | ... altıdan fazla sekme varsa. |
| ... Genel sekmesini kullanarak yerine bir düzenleyici belgesi içinde üst kısmındaki de denetler. | ... herhangi bir UI, bildirim Tasarımcısı gibi yapılandırılmaz. |

**Bildirim Tasarımcısı seçilen sekmesi: varsayılan durumu**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `ManifestDesigner.TabActive` |
| Kenarlık | Yok. |

**Bildirim Tasarımcısı seçilen açıklama bölmesi: varsayılan durumu**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `ManifestDesigner.DescriptionPane` |

**Bildirim Tasarımcısı seçili içerik sayfası: varsayılan durumu**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `ManifestDesigner.Background` |
| İletişim yardımcı metni | `ManifestDesigner.WatermarkText`<br />(Bu belirteç adı işlevini eşleşmiyor.) |

**Bildirim Tasarımcısı sekmesi: Seçili durum**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `ManifestDesigner.Tab.Inactive` |

**Bildirim Tasarımcısı sekmesi: duruma getirin**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Komut yapıları  

###  <a name="BKMK_CommandMenus"></a> Menüler  
Menüleri, Visual Studio içinde çeşitli yerlerde oluşabilir: belge veya araç pencerelerini veya IDE tamamında çeşitli konumlarda sağ katıştırılmış ana menü çubuğu. Menü diğer UI öğeleri ile ilişkili uygulamalar için ilgili öğenin bölümünde ele alınmıştır. Visual Studio ortamı tarafından sağlanan standart menü uygulama her zaman kullanmalısınız. Ancak, bazı ender durumlarda, standart bir Visual Studio menülerinin erişimi olmayabilir. Bu gibi durumlarda, kullanıcı Arabirimi diğer Visual Studio menülerinde ile tutarlı olmasını sağlamak için aşağıdaki belirteci adları kullanın.  

![Visual Studio menüsünde (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303 000_MenuRedline")<br />Visual Studio menüsünde (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |
| ... olduğunda özel bir menü oluşturmanız gerekir.| ... tek başına bir arka plan rengi. Her zaman arka plan/ön plan birlikte belirtilen kullanın. |
| ... Visual Studio menülerinin eşleştirmek istediğiniz yeni bir kullanıcı Arabirimi bileşeninin olduğunda.| |

#### <a name="menu-titles"></a>Menü başlığı  
Genellikle bir Komut çubuğuna menü bulunduğunda menü başlığı arka plan, kenarlık ve başlık metnini yanı isteğe bağlı bir karakter oluşur.  

![Menü başlığı (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303 001_MenuTitleRedline")<br />Menü başlığı (kırmızı çizgi)  

| Kullan... | Kullanmayın... |
| --- | --- |
| ... her oluşturduğunuz özel menü başlığı. | ... her şey için her zaman istemediğiniz menü başlığının eşleştirin. |
| | Belirtilen dışındaki... tüm arka plan/ön plan birlikte. |

**Menü başlığı: varsayılan durumu**

![Menü başlığı varsayılan](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303 002_MenuTitleDefault")<br />Varsayılan menü başlığı

![Varsayılan karakter ile menü başlığı](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303 003_MenuTitleWithGlyphDefault")<br />Varsayılan karakter ile menü başlığı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | Yok. |
| Ön plan (metin) | `Environment.CommandBarTextActive` |
| Ön plan (karakter) | `Environment.CommandBarMenuGlyph` |
| Kenarlık | Yok. |

**Menü başlığı: duruma getirin**  

![Menü başlığı üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303 004_MenuTitleHover")<br />Üzerine gelindiğinde menü başlığı  

![Menü başlığı ile üzerine gelindiğinde glif](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303 005_MenuTitleWithGlyphHover")<br />Menü başlığı ile üzerine gelindiğinde karakter

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (metin) | `Environment.CommandBarTextHover` |
| Ön plan (karakter) | `Environment.CommandBarMenuMouseOverGlyph` |  
| Kenarlık | `Environment.CommandBarBorder` |

**Menü başlığı: basılı durumu**  

![Menü başlığı basılı](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303 006_MenuTitlePressed")<br />Basılan menü başlığı

![Menü başlığı karakter ile basılı](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303 007_MenuTitleWithGlyphPressed")<br />Menü başlığı karakter ile basıldı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (metin) | `Environment.CommandBarTextActive` |
| Ön plan (karakter) | `Environment.CommandBarMenuMouseDownGlyph` |
| Kenarlık | `Environment.CommandBarMenuBorder`<br />(Yalnızca sol, üst ve sol tarafında.) |  

**Menü başlığı: devre dışı durum**  

![Menü başlığı karakter ile devre dışı](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")<br />Glif devre dışı bırakılmış menü başlığı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | Yok. |
| Ön plan (metin) | `Environment.CommandBarTextInactive` |
| Ön plan (karakter) | `Environment.CommandBarTextInactive` |
| Kenarlık | Yok. |

#### <a name="menu-items"></a>Menü öğeleri
Bir tek menü öğesinin menü metnini ve bir isteğe bağlı simge, onay kutusu veya alt simge oluşur. Arka plan ve metin rengi değişiklik üzerine gelindiğinde. Bu renk belirteci, bir arka plan/ön plan çiftidir.  

![Menü öğelerini kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303 009_MenuItemRedline")  

| Kullan... | Kullanmayın... |
|---|---|
| ... menü çubuğunun ya da komut çubuğu'da, bir herhangi bir aşağı açılan listeyi başlatılır. | ... tüm aşağı açılan listesinde için başka bir bağlam. |
| | Belirtilen dışındaki... tüm arka plan/ön plan birlikte. |

**Menü öğelerini: varsayılan durumu**

![Menü öğelerini varsayılan](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303 010_MenuDefault")<br />Varsayılan menü öğeleri  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (metin) | `Environment.CommandBarTextActive` |
| Ön plan (alt karakter) | `Environment.CommandBarMenuSubmenuGlyph` |
| Kenarlık | `Environment.CommandBarMenuBorder` |
| Simge kanal arka planı | `Environment.CommandBarMenuIconBackground` |
| Ayırıcı | `Environment.CommandBarMenuSeparator` |
| Gölge | `Environment.DropShadowBackground` |

**Menü öğelerini: işaretli ve seçili durumları**  

![İşaretli menü](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303 011_MenuChecked")<br />İşaretli menü öğesi

![Seçili menü](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303 012_MenuSelected")<br />Seçili bir menü öğesi    

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Onay işareti | `Environment.CommandBarCheckBox` |  
| Onay işareti arka plan | `Environment.CommandBarSelectedIcon` |  
| Simge arka planı | `Environment.CommandBarSelected` |
| Simge kenarlık | `Environment.CommandBarSelectedBorder` |

**Menü öğelerini: duruma getirin**  

![Menü vurgulu](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303 013_MenuHover")<br />Üzerine gelindiğinde menü öğesi

![İşaretli menü vurgulu](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303 014_MenuHoverChecked")<br />Üzerine gelindiğinde menü öğesinin denetlenmesi

![Seçili menü vurgulu](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303 015_MenuHoverSelected")<br />Üzerine gelindiğinde seçili menü öğesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.CommandBarMenuItemMouseOver` |
| Ön plan (metin) | `Environment.CommandBarMenuItemMouseOver` |
| Ön plan (alt karakter) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Onay işareti | `Environment.CommandBarCheckBoxMouseOver` |
| Onay işareti arka plan | `Environment.CommandBarHoverOverSelectedIcon` |
| Simge arka planı | `Environment.CommandBarHoverOverSelected` |
| Simge kenarlık | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Menü öğelerini: devre dışı durum**  

![Devre dışı menü](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303 016_MenuDisabled")<br />Devre dışı menü öğesi

![Menü devre dışı işaretli](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303 017_MenuDisabledChecked")<br />Onay işareti ile devre dışı menü öğesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Environment.CommandBarTextInactive` |
| Ön plan (alt karakter) | `Environment.CommandBarMenuSubmenuGlyph` |
| Onay işareti | `Environment.CommandBarCheckBoxDisabled` |
| Onay işareti arka plan | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Komut çubukları  
Bir komut çubuğu, birden fazla yerde Visual Studio IDE içinde komut raf ve katıştırılmış araç veya belge pencereleri özellikle görünebilir.  

Genel olarak, Visual Studio ortamı tarafından sağlanan standart komut çubuğu uygulaması her zaman kullanın. Standart mekanizmasını kullanarak tüm görsel Ayrıntılar doğru görünür ve etkileşimli öğeleri davrandığını tutarlı bir şekilde ile diğer Visual Studio komut çubuğu denetimleri sağlar. Ancak, kendi komut çubuğu oluşturmak için gerekli değilse, doğru aşağıdaki belirteci adları kullanarak stil emin olun.  

![Komut çubuğu kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303 018_CommandBarRedline")<br />Komut çubuğu (kırmızı çizgi)  

![Taşma düğmesi kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303 019_OverflowButtonRedline")<br />Taşma düğmesi (kırmızı çizgi)  

| Kullan... | Kullanmayın... |
| --- | --- |
| ... katıştırılmış komut çubuğu gerek duyduğunuz yerlerde, ancak standart bir Visual Studio komut çubuğu uygulaması kullanamaz olduğundan. | Komut çubuğuna benzer olmayan... için kullanıcı Arabirimi öğeleri. |
| | belirteç adları dışında olduğu için istediklerinizi belirtilen... komut çubuğu için bileşenler. |

#### <a name="command-bar-groups"></a>Komut çubuğu grupları  
Bir komut çubuğu grubuyla ilgili bir komut çubuğu denetimleri kümesinden oluşur ve herhangi bir sayıda düğmeler, aşağı açılan menüler, birleşik giriş kutuları veya menüler Bölünmüş düğme içerebilir. Bu denetimler için renkleri ayrı belirteci adlarına göre düzenlenen ve ayrı olarak başka bir yerde bu kılavuzda ele alınmıştır. Ayırıcı çizginin bir komut çubuğu grubuyla ilgili alt gruplar ayırmak için kullanılır.  

![Komut çubuğu grubu kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303 020_CommandBarGroupRedline")<br />Komut çubuğu grubu (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |  
| ... katıştırılmış komut çubuğu gerek duyduğunuz yerlerde, ancak standart bir Visual Studio komut çubuğu uygulaması kullanamaz olduğundan. | Komut çubuğuna benzer olmayan... için kullanıcı Arabirimi öğeleri. |
| | belirteç adları dışında olduğu için istediklerinizi belirtilen... komut çubuğu için bileşenler. |

**Komut çubuğu grubu: varsayılan durumu**  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.CommandBarGradientBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Kenarlık | `Environment.CommandBarToolBarBorder` |
| Sürükleme tutamacı | `Environment.CommandBarDragHandle` |
| Ayırıcı | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Komut simgeleri  
![Komut simgesi kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303 021_CommandIconRedline1")<br />Komut simgesinin (kırmızı çizgi)  

![Komut metni simgesiyle kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303 022_CommandIconRedline2")<br />Komut simgesinin metinle (kırmızı çizgi)  

| Kullan... | Kullanmayın... |
| --- | --- |
| ... düğmeleri için komut çubuğunda yer alır. | ... denetimler için belirteç adlarına sahip. |
| | Belirtilen dışındaki... tüm arka plan/ön plan birlikte. |

**Komut simgesinin: varsayılan durumu**  

![Komut simgesinin varsayılan](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303 023_CommandIconDefault")<br />Varsayılan komut simgesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | Yok (komut çubuğu arka planından devralır) |
| Ön plan (metin) | `Environment.CommandBarTextActive` |
| Kenarlık | Yok |

**Komut simgesinin: varsayılan seçili duruma**

![Varsayılan, seçili komut simgesinin](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")<br />Varsayılan, seçili komut simgesi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.CommandBarSelected` |
| Ön plan (metin) | `Environment.CommandBarTextSelected` |
| Kenarlık | `Environment.CommandBarSelectedBorder` |

**Komut simgesinin: üzerine gelindiğinde veya odağı durumları**  

![Komut simgesinin üzerine gelin veya odak](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303 025_CommandIconHover")<br />Komut simgesinin üzerine gelin veya odağı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (metin) | `Environment.CommandBarTextHover` |
| Kenarlık | `Environment.CommandBarBorder` |

**Komut simgesinin: Seçili üzerine gelindiğinde veya odağı durumları**

![Komut simgesinin üzerine gelin veya odak seçili](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303 026_CommandIconHoverSelected")<br />Seçili komut simgesinin üzerine gelindiğinde veya odağı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.CommandBarHoverOverSelected` |
| Ön plan (metin) | `Environment.CommandBarTextHoverOverSelected` |
| Kenarlık | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Komut simgesinin: basılı durumu**  

![Komut simgesinin basılı](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303 027_CommandIconPressed")<br />Basılan komut simgesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (metin) | `Environment.CommandBarTextMouseDown` |
| Kenarlık | `Environment.CommandBarBorder` |

**Komut simgesinin: devre dışı durum**  

![Devre dışı bir komut simgesi](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303 028_CommandIconDisabled")<br />Devre dışı bir komut simgesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | Yok (komut çubuğu arka planından devralır) |
| Ön plan (metin) | `Environment.CommandBarTextInactive` |
| Kenarlık | Yok |

####  <a name="BKMK_CommandComboBox"></a> Komut çubuğu birleşik giriş kutuları

> [!IMPORTANT]
> Birleşik giriş kutuları, açılan listeler için benzerdir, ancak düzenlenebilir metin bölge. Düzenlenebilir metin bölge, açılan içermez, renk belirteçleri için kullanın. [komut çubuğu açılır listeleri](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).  

![Birleşik giriş kutusu çubuğu komut kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303 029_ComboBoxRedline")<br />Komut çubuğu birleşik giriş kutusu (kırmızı çizgi)  

| Kullan... | Kullanmayın... |
| --- | --- |
| ... özel birleşik giriş kutuları oluştururken. | ... her şey için her zaman komut eşleştirilecek istemediğiniz çubuğu kullanıcı Arabirimi. |
| ... bir birleşik giriş kutusuna benzeyen bir komut çubuğu denetimini oluştururken. | ... erişim için bir stil uygulanmış bir birleşik giriş kutusu olduğunda. |

**Komut çubuğu birleşik giriş kutusu giriş alanını: varsayılan durumu**

![Komut çubuğu birleşik giriş kutusu giriş alanı](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303 030_ComboBoxInputField")<br />Komut çubuğu birleşik giriş kutusu giriş alanı  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ComboBoxBackground` |
| Ön plan (metin) | `Environment.ComboBoxText` |
| Kenarlık | `Environment.ComboBoxBorder` |
| Ayırıcı | Hiçbir ayırıcısı |

**Komut çubuğu aşağı açılan düğmesi: varsayılan durumu**  

![Açılan birleşik giriş kutusu&#45;Kapat düğmesi](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303 031_ComboBoxDropdownButton")<br />Komut çubuğu aşağı açılan düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | Yok (komut çubuğu arka planından devralır) |
| Ön plan (karakter) | `Environment.ComboBoxGlyph` |

**Komut çubuğu açılır listesi: varsayılan durumu**

![Komut çubuğu açılır listesi](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303 032_ComboBoxDropdownList")<br />Komut çubuğu açılır listesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ComboBoxPopupBackgroundBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (metin) | `Environment.ComboBoxItemText` |
| Kenarlık | `Environment.ComboBoxPopupBorder` |

**Komut çubuğu birleşik giriş kutusu giriş alanını: duruma getirin**  

![Komut çubuğu birleşik giriş kutusu giriş alanı üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")<br />Komut çubuğu birleşik giriş kutusu giriş alanı üzerine gelindiğinde  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (metin) | `Environment.ComboBoxMouseOverText` |
| Kenarlık | `Environment.ComboBoxMouseOverBorder` |
| Ayırıcı | `Environment.ComboBoxMouseOverSeparator` |

 **Komut çubuğu aşağı açılan düğmesi: duruma getirin**  

![Komut çubuğu açılır düğme üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303 034_ComboBoxDropdownButtonHover")<br />Komut çubuğu açılır düğme üzerine gelindiğinde

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ComboBoxButtonMouseOverBackground` |
| Ön plan (karakter) | `Environment.ComboBoxMouseOverGlyph` |

**Komut çubuğu açılır listesi: duruma getirin**

 ![Komut çubuğu açılır listesi üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")<br />Üzerine gelindiğinde komut çubuğu açılır listesi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan (menü öğesi) | `Environment.ComboBoxItemMouseOverBackground` |
| Ön plan (metin) | `Environment.ComboBoxItemMouseOverText` |
| Kenarlık (menü öğesi) | `Environment.ComboBoxItemMouseOverBorder` |

 **Komut çubuğu birleşik giriş kutusu giriş alanını: odaklanmış durumu**  

![Komut çubuğu birleşik giriş kutusu giriş alanı odaklanmış](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")<br />Komut çubuğu birleşik giriş kutusu giriş alanı odaklanır

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ComboBoxFocusedBackground` |
| Ön plan (metin) | `Environment.ComboBoxFocusedText` |
| Kenarlık | `Environment.ComboBoxFocusedBorder` |
| Ayırıcı | `Environment.ComboBoxFocusedButtonSeparator` |

**Komut çubuğu aşağı açılan düğmesi: odaklanmış durumu**  

![Komut çubuğu açılan düğmeyi odaklanmış](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303 037_ComboBoxDropdownButtonFocused")<br />Odaklanmış komut çubuğu açılır düğme

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ComboBoxFocusedButtonBackground` |
| Ön plan (karakter) | `Environment.ComboBoxFocusedGlyph` |

 **Komut çubuğu birleşik giriş kutusu giriş alanını: basılı durumu**  

![Komut birleşik giriş kutusu giriş alanı basılı](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")<br />Komut çubuğu birleşik giriş kutusu giriş alanı basıldı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ComboBoxMouseDownBackground` |
| Ön plan (metin) | `Environment.ComboBoxMouseDownText` |
| Kenarlık | `Environment.ComboBoxMouseDownBorder` |
| Ayırıcı | `Environment.ComboBoxMouseDownSeparator` |

**Komut çubuğu aşağı açılan düğmesi: basılı durumu**

![Komut çubuğu aşağı açılan düğmesine basıldığında](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303 039_ComboBoxDropdownButtonPressed")<br />Komut çubuğu aşağı açılan düğmesine basıldı  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ComboBoxButtonMouseDownBackground` |
| Ön plan (karakter) | `Environment.ComboBoxMouseDownGlyph` |

**Komut çubuğu birleşik giriş kutusu giriş alanını: devre dışı durum**  

![Komut çubuğu birleşik giriş kutusu giriş alanını devre dışı](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")<br />Devre dışı bir komut çubuğu birleşik giriş kutusu giriş alanı  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ComboBoxDisabledBackground` |
| Ön plan (metin) | `Environment.ComboBoxDisabledText` |
| Kenarlık | `Environment.ComboBoxDisabledBorder` |
| Ayırıcı | Hiçbir ayırıcısı |

**Komut çubuğu aşağı açılan düğmesi: devre dışı durum**  

![Komut çubuğu açılan düğmeyi devre dışı](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303 040_ComboBoxDropdownButtonDisabled")<br />Devre dışı bir komut çubuğu açılır düğme

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | Yok. |
| Ön plan (karakter) | `Environment.ComboBoxDisabledGlyph` |

####  <a name="BKMK_CommandDropDown"></a> Komut çubuğu açılır listeleri

> [!IMPORTANT]
>  Açılan listeler, birleşik giriş kutuları için benzerdir, ancak düzenlenebilir metin bölgeleri yoksundur. Renk belirteçleri için açılan bir düzenlenebilir metin bölgesi içeriyorsa kullanmak [komut çubuğu birleşik giriş kutuları](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).  

![Komut açılır (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303 042_DropdownRedline")<br />Komut açılır (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |
| ... özel aşağı açılan liste denetimleri oluştururken. | ... her şey için aşağı açılan listesine benzer olmayan. |
| | ... birleşik giriş kutuları veya Bölünmüş düğme. |   

**Komut çubuğu aşağı açılan seçimi alanını: varsayılan durumu**  

![Varsayılan komut çubuğu aşağı açılan seçimi alanını](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303 043_DropdownSelectionField")<br />Varsayılan komut çubuğu aşağı açılan seçimi alanı  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.DropDownBackground` |
| Ön plan (metin) | `DropDownText` |
| Kenarlık | `DropDownBorder` |
| Ayırıcı | Hiçbir ayırıcısı |

**Komut çubuğu aşağı açılan düğmesi: varsayılan durumu**

![Varsayılan komut çubuğu açılan düğmeyi](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303 044_DropdownButton")<br />Varsayılan komut çubuğu aşağı açılan düğmesi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | Yok. |
| Ön plan (karakter) | `Environment.DropDownGlyph` |

**Komut çubuğu açılır listesi: varsayılan durumu**

![Varsayılan komut çubuğu açılır listede](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303 045_DropdownList")<br />Varsayılan komut çubuğu açılır listesi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.DropDownPopupBackgroundBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (metin) | `Environment.ComboBoxItemText` |
| Kenarlık | `Environment.DropDownPopupBorder` |
| Gölge | `Environment.DropShadowBackground` |

**Komut çubuğu aşağı açılan seçimi alanını: duruma getirin**  

![Komut çubuğu aşağı açılan seçimi alanını üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")<br />Komut çubuğu aşağı açılan seçimi alanını üzerine gelindiğinde  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.DropDownMouseOverBackgroundBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (metin) | `Environment.DropDownMouseOverText` |
| Kenarlık | `Environment.DropDownMouseOverBorder` |
| Ayırıcı | `Environment.DropDownButtonMouseOverSeparator` |

**Komut çubuğu aşağı açılan düğmesi: duruma getirin**  

![Komut çubuğu açılır düğme üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303 047_DropdownButtonHover")<br />Komut çubuğu açılır düğme üzerine gelindiğinde  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.DropDownButtonMouseOverBackground` |
| Ön plan (karakter) | `Environment.DropDownMouseOverGlyph` |

**Komut çubuğu açılır listesi: duruma getirin**  

![Komut çubuğu açılır listesi üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303 048_DropdownListHover")<br />Üzerine gelindiğinde komut çubuğu açılır listesi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan (menü öğesi) | `Environment.ComboBoxItemMouseOverBackground` |
| Ön plan (metin) | `Environment.ComboBoxItemMouseOverText` |
| Kenarlık (menü öğesi) | `Environment.ComboBoxItemMouseOverBorder` |

 **Komut çubuğu aşağı açılan seçimi alanını: basılı durumu**  

![DROP&#45;tuşunu basılı seçim alanı](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")<br />Komut aşağı açılan seçimi alanını basıldı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.DropDownMouseDownBackground` |
| Ön plan (metin) | `Environment.DropDownMouseDownText` |
| Kenarlık | `Environment.DropDownMouseDownBorder` |
| Ayırıcı | `Environment.DropDownButtonMouseDownSeparator` |

**Komut çubuğu aşağı açılan düğmesi: basılı durumu**

![Komut çubuğu aşağı açılan düğmesine basıldığında](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303 050_DropdownButtonPressed")<br />Komut çubuğu aşağı açılan düğmesine basıldı  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.DropDownButtonMouseDownBackground` |
| Ön plan (karakter) | `Environment.DropDownMouseDownGlyph` |

**Komut çubuğu aşağı açılan seçimi alanını: devre dışı durum**  

![Komut çubuğu aşağı açılan seçimi alanını devre dışı](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")<br />Devre dışı bir komut çubuğu aşağı açılan seçimi alan

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.DropDownDisabledBackground` |
| Ön plan (metin) | `Environment.DropDownDisabledText` |
| Kenarlık | `Environment.DropDownDisabledBorder` |
| Ayırıcı | Hiçbir ayırıcısı |

**Komut çubuğu aşağı açılan düğmesi: devre dışı durum**

![Komut çubuğu açılan düğmeyi devre dışı](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303 052_DropdownButtonDisabled")<br />Devre dışı bir komut çubuğu açılır düğme

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (karakter) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Komut çubuğu düğmelerinin Böl
Bölünmüş düğme fazla belirteç ad düğmeler, menüler ve komut çubuğu metni gibi diğer komut çubuğu denetimleri ile paylaşın. Tüm gerekli eylem ve açılan düğmeyi belirteci adları kolaylık olması için burada yinelenir. Bölünmüş düğme açılan listeleri, uygulamaları [menü çubuğu komut](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).  

![Bölünmüş düğme kırmızı çizgi](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303 053_SplitButtonRedline")<br />Komut çubuğu Bölünmüş düğme (kırmızı çizgi)  

| Kullan... | Kullanmayın... |
| --- | --- |
| ... özel Bölünmüş düğme oluştururken. | ... diğer türlerdeki düğmeleri için. |
| | Belirtilen dışındaki... tüm arka plan/ön plan birlikte. |

**Komut çubuğu Bölünmüş düğme: varsayılan durumu**  

![Varsayılan komut çubuğu Bölünmüş düğme](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303 054_SplitButton")<br />Varsayılan komut çubuğu Bölünmüş düğme  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | Yok. |
| Ön plan (metin) | `Environment.CommandBarTextActive` |
| Ön plan (karakter) | `Environment.CommandBarSplitButtonGlyph` |
| Kenarlık | Yok |
| Ayırıcı | Yok |

**Komut çubuğu Bölünmüş düğme: duruma getirin**  

![Komut çubuğu Bölünmüş düğme üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303 055_SplitButtonHover")<br />Bölünmüş düğme üzerine gelindiğinde komut çubuğu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (metin) | `Environment.CommandBarTextHover` |
| Ön plan (karakter) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Kenarlık | `Environment.CommandBarBorder` |
| Ayırıcı | `Environment.CommandBarSplitButtonSeparator` |

**Komut çubuğu Bölünmüş düğme: basılı durumu**  

![Komut çubuğu Bölünmüş düğme](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303 056_SplitButtonPressed")<br />Bölünmüş düğme basılı komut çubuğu  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (metin) | `Environment.CommandBarTextMouseDown` |
| Ön plan (karakter) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Kenarlık | `Environment.CommandBarBorder` |
| Ayırıcı | Yok |

**Komut çubuğu Bölünmüş düğme: devre dışı durum**

![Komut çubuğu Bölünmüş düğme devre dışı](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303 057_SplitButtonDisabled")<br />Bölünmüş düğme devre dışı bir komut çubuğu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (metin) | `Environment.ComboBoxItemTextInactive` |
| Ön plan (karakter) | `Environment.CommandBarTextInactive` |
| Kenarlık | Yok |
| Ayırıcı | Yok |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Düğmeler 'Fazla Seçenekleri' ve 'Overflow' komutu  
"Diğer seçenekler" düğmesi, bir komut çubuğu grubu özelleştirilebilir ekleme veya kaldırma ilgili komut çubuğu düğmelerinin olduğunda kullanılır. Bir komut çubuğu için yatay boşluk eksikliği nedeniyle kesilmiş ve görüntülenemiyor komut çubuğu düğmelerini içeren bir menü çubuğunda gösterir "Taşma" düğmesi görünür. Bu iki düğme için renkleri belirteci adları aynı kümesi tarafından denetlenir.  

![Komut çubuğu 'Daha fazla seçenek' düğmesini (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303 058_MoreOptionsRedline")<br />Komut çubuğu 'Daha fazla seçenek' düğmesini (kırmızı çizgi)  

| Kullan... | Kullanmayın... |
| --- | --- |
| ... Özel 'daha fazla seçenek' veya 'Overflow' düğmeler için. | benzer bir işlevsellik 'Fazla Seçenekleri' veya 'Overflow' düğmesine sahip olmayan... düğmeler için. |

**Komut çubuğu 'Fazla Seçenekleri' ve 'Overflow' düğmeleri: varsayılan durumu**  

![Varsayılan komut çubuğu 'Daha fazla seçenek' düğmesini](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303 059_MoreOptions")<br />Komut çubuğu varsayılan 'Daha fazla seçenek' düğmesi

![Varsayılan komut çubuğu 'Overflow' düğmesini](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303 060_Overflow")<br />Varsayılan komut çubuğu 'Overflow' düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.CommandBarOptionsBackground` |
| Ön plan (karakter) | `Environment.CommandBarOptionsGlyph` |

**Komut çubuğu 'Fazla Seçenekleri' ve 'Overflow' düğmeleri: duruma getirin**

![Komut çubuğu üzerine gelindiğinde 'Daha fazla seçenek' düğmesini](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303 061_MoreOptionsHover")<br />Komut çubuğu üzerine gelindiğinde 'Daha fazla seçenek' düğmesi  

!['Overflow' komut çubuğu düğmesinin üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303 062_OverflowOptions")<br />'Overflow' komut çubuğu düğmesinin üzerine gelindiğinde   

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (karakter) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Komut çubuğu 'Fazla Seçenekleri' ve 'Overflow' düğmeleri: basılı durumu**  

![Komut çubuğu 'Daha fazla seçenek' düğmesine basıldığında](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303 063_MoreOptionsPressed")<br />Komut çubuğu 'Daha fazla seçenek' düğmesine basıldı  

![Basılan taşma](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303 064_OverflowPressed")<br />Komut çubuğu 'Overflow' düğmesine basıldı  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (karakter) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Belge pencereleri  
Visual Studio ortamı tarafından sağlanan çünkü belge pencereleri çoğaltmak için gerek yoktur. Ancak, kullanıcı Arabirimi her zaman Visual Studio ortamının bu bölümü ile tutarlı görünmesi belge pencerelerinin kullanılan renkleri yararlanmak istediğinize karar verin.  

Belge penceresi renk belirteçleri kullanırken, yalnızca benzer öğeleri için ve her zaman çiftler halinde kullanma konusunda dikkatli olun. Bunu yapmak, kullanıcı Arabiriminize beklenmeyen sonuçlar alabilirsiniz.  

### <a name="document-window-frames"></a>Belge pencere çerçeveleri  
Belge pencereleri IDE içindeki yerleşik veya ayrı bir pencerede olarak kayan olabilir. Belge penceresini IDE dışında kayan noktalı, yine de bir belge kutusu içinde bulunur ve arka plan, kenarlık, metin ve IDE parçası olduğunda, aynı olan sekme renkleri vardır. Ancak, belgeyi kendi arka plan, kenarlık ve metin renklerini olan bir çerçeve içinde bulunur. Araç pencereleri belge iyi yerleştirildiğinde, bunların davranışı ve kendi sekme rengini belge penceresi belirteci adlarından devralır.  

![Yerleşik belge penceresi (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303 065_DockedDocumentWindowRedline")<br />Yerleşik belge penceresi (kırmızı çizgi)  

![Kayan belge penceresi (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303 066_FloatingDocumentWindowRedline")<br />Kayan belge penceresi (kırmızı çizgi)  

| Kullan... | Kullanmayın... |
| --- | --- |
| ... herhangi bir belge penceresi eşleştirmek istediğiniz kullanıcı Arabirimi oluşturmakta olduğunuz. | ... değiştirmeyi otomatik olarak istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir. |

**Yerleşik veya kayan belge penceresi: varsayılan durumu**  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | Belge türüne göre değişir |
| Ön plan (metin) | Belge türüne göre değişir |
| Kenarlık | `Environment.ToolWindowBorder` |

**Odaklanmış, belge pencere çerçevesi kayan: varsayılan durumu**

![Odaklanmış, varsayılan belge pencere çerçevesi kayan](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303 067_FrameFocused")<br />Odaklanmış, varsayılan belge pencere çerçevesi kayan

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowFloatingFrame` |
| Ön plan (metin) | `Environment.ToolWindowFloatingFrame` |
| Ön plan (karakter) | `Environment.RaftedWindowButtonActiveGlyph` |
| Kenarlık | `Environment.MainWindowActiveDefaultBorder` |
| Kenarlık (karakter) | `Environment.RaftedWindowButtonActiveBorder`<br />(Saydam olarak ayarlayın) |

**Belge odaklanmadan, kayan pencere çerçevesi: varsayılan durumu**  

![Varsayılan Belge odaklanmadan, kayan pencere çerçevesi](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303 068_FrameUnfocused")<br />Varsayılan Belge odaklanmadan, kayan pencere çerçevesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowFloatingFrameInactive` |
| Ön plan (metin) | `Environment.ToolWindowFloatingFrameInactive` |
| Ön plan (karakter) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Kenarlık | `Environment.MainWindowInactiveBorder` |
| Kenarlık (karakter) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Saydam olarak ayarlayın) |

**Odaklanmış, belge pencere çerçevesi kayan: duruma getirin**

![Odaklanmış, belge pencere çerçevesi üzerine gelindiğinde kayan](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303 069_FrameFocusedHover")<br />Odaklanmış, belge pencere çerçevesi üzerine gelindiğinde kayan  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan (karakter) | `Environment.RaftedWindowButtonHoverActive` |
| Ön plan (karakter) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Kenarlık (karakter) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Belge odaklanmadan, kayan pencere çerçevesi: duruma getirin**  

![Belge odaklanmadan, kayan pencere çerçevesi üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303 070_FrameUnfocusedHover")<br />Üzerine gelindiğinde odaklanmadan, kayan bir belge pencere çerçevesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan (karakter) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Ön plan (karakter) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Kenarlık (karakter) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Odaklanmış, belge pencere çerçevesi kayan: basılı durumu**  

![Odaklanmış, belge pencere çerçevesi makinesinde kayan](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303 071_FrameFocusedPressed")<br />Odaklanmış, belge pencere çerçevesi makinesinde kayan

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan (karakter) | `Environment.RaftedWindowButtonDown` |
| Ön plan (karakter) | `Environment.RaftedWindowButtonDownGlyph` |
| Kenarlık (karakter) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Belge sekmeleri  
Belge sekmeleri hangi belgelerin yanı sıra etkin belgeyi hangisinin seçili geçerli olduğu veya şu anda açık olan belirtmek için sekmesinde kanaldaki durur. Kullanıcı var. bunları yerleştirir, araç pencerelerini de belge sekme kanalda sabitlenebilir. Bu durumda, bunlar aynı sekme renkleri ve belge pencereleri kullanır. Kullanıcı Arabirimi, oluşturuyorsanız, her zaman (Tema güncelleştirmeleri veya yeni temalar yüklediyseniz dahil) belge penceresini renkleriyle eşleşecek ve ardından bu renk belirteçleri başvuru istiyorsunuz.  

![Belge sekmeleri (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303 072_DocumentTabRedline")<br />Belge sekmeleri (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |
| ... belge sekmeleri eşleşen ve tema güncelleştirmeleri veya yeni Tema renkleri otomatik olarak seçmek istediğiniz kullanıcı Arabirimi oluşturmakta olduğunuz herhangi bir yerde. | Kabuk güncelleştirme bir tema olduğunda otomatik olarak değiştirmek istemediğiniz... herhangi bir UI için. |

#### <a name="open-document-tabs"></a>Açık belge sekmeleri  
Her açık belge adını görüntüleyen belge sekme kanalda bir sekmesi vardır. Belge ya da seçilebilir veya arka planda açın ve bu durumları sekmeleri yansıtacak:  

-   Seçili belgeyi de şu anda görüntülenen belgenin temsil eder. Seçili bir sekme iyi belgenin üst kenarı genişlettiği belge kenarlık vardır.  

-   Arka plan sekmeleri şu anda seçilen sekmesi olmayan herhangi bir belge sekme var. Tıklattıktan sonra seçili duruma ve tüm arka plan, kenarlık ve metin renklerini Bu belirteci adlarından Al.  

![Açık belge sekme (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303 073_OpenDocumentTabRedline")<br />Açık belge sekme (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |
| ... özel belge sekmeleri oluştururken. | ... (Önizleme) provisional sekmeler için. |
| | ... varsa otomatik olarak değiştirmek istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir. |

**Seçili, odaklanmış bir belge sekmesi**  

![Seçili, belge sekmesini odaklanmış](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303 074_SelectedTabFocused")<br />Seçili, odaklanmış bir belge sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.FileTabSelectedGradientTop`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (metin) | `Environment.FileTabSelectedText` |
| Kenarlık | `Environment.FileTabSelectedBorder`<br />(Aynı arka plan rengini ayarlayın.) |
| Belge kenarlık | `Environment.FileTabDocumentBorderBackground` |

**Seçildiğinde, plana odaklanmadan belge sekmesi**

![Seçildiğinde, plana odaklanmadan belge sekmesini](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303 075_SelectedTabUnfocused")<br />Seçildiğinde, plana odaklanmadan belge sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.FileTabInactiveGradientTop`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (metin) | `Environment.FileTabInactiveText` |
| Kenarlık | `Environment.FileTabInactiveBorder`<br />(Aynı arka plan rengini ayarlayın.) |
| Belge kenarlık | `Environment.FileTabInactiveDocumentBorderBackground` |

**Arka plan belge sekmesini: varsayılan durumu**  

![Varsayılan arka plan belge sekmesini](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303 076_BackgroundTab")<br />Varsayılan arka plan belge sekmesi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.FileTabBackground` |
| Ön plan (metin) | `Environment.FileTabText` |
| Kenarlık | `Environment.FileTabBorder`<br />(Aynı arka plan rengini ayarlayın.) |

**Arka plan belge sekmesini: duruma getirin**  

![Arka plan belge sekme üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303 077_BackgroundTabHover")<br />Arka plan üzerine gelindiğinde belge sekmesi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.FileTabHotGradientTop`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (metin) | `Environment.FileTabHotText` |
| Kenarlık | `Environment.FileTabHotBorder`<br />(Aynı arka plan rengini ayarlayın.) |

#### <a name="preview-tab"></a>Önizleme sekmesi  
"Geçici" sekmesinde olarak da adlandırılır. Önizleme sekmesini, kullanıcı Çözüm Gezgini araç penceresindeki bir öğeyi tıklattığında belge sekme kanal sağ tarafında görünür. Bu belgenin önizleme olarak davranır ve kullanıcı belgeyi belge sekme kanal sol tarafında açık tutmak için seçeneği de sunar. Bir kerede yalnızca bir Önizleme sekmesini Aç açık olabilir. Önizleme sekmeleri sahip hem de arka plan ve seçili durumlardan sekmeleri Aç gibi ve kullanıcıların etkin durumda odaklanmış veya plana odaklanmadan olabilir.  

![Önizleme sekmesini (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303 078_PreviewTabRedline")<br />Önizleme sekmesini (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |
| ... her yerden oluşturduğunuz provisional Önizleme ve bazı öğesi geçerli Önizleme sekme rengini eşleştirilecek istiyorsanız. | Belge ya da geçici olmayan sekmesinde herhangi bir türden için... (Önizleme). |
| | ... varsa otomatik olarak değiştirmek istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir. |

**Odaklanmış, seçili Önizleme sekmesi**  

![Odaklanmış, seçili bir önizleme sekmesinde](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303 079_PreviewTabFocused")<br />Odaklanmış, seçili Önizleme sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.FileTabProvisionalSelectedActive` |
| Ön plan (metin) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Kenarlık | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Aynı arka plan rengini ayarlayın.) |
| Belge kenarlık | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Plana odaklanmadan, seçili Önizleme sekmesi**  

![Plana odaklanmadan, seçili bir önizleme sekmesinde](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303 080_PreviewTabUnfocused")<br />Plana odaklanmadan, seçili Önizleme sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.FileTabProvisionalSelectedInactive` |
| Ön plan (metin) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Kenarlık | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Belge kenarlık | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Arka plan Önizleme sekmesi: varsayılan durumu**  

![Varsayılan arka plan Önizleme sekmesinde](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303 081_PreviewBackgroundTab")<br />Varsayılan arka plan Önizleme sekmesi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.FileTabProvisionalInactive` |
| Ön plan (metin) | `Environment.FileTabProvisionalInactiveForeground` |
| Kenarlık | `Environment.FileTabProvisionalInactiveBorder`<br />(Aynı arka plan rengini ayarlayın.) |

**Arka plan Önizleme sekmesi: duruma getirin**  

![Üzerine gelindiğinde kullanılacak arka plan Önizleme sekmesinde](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")<br />Arka plan üzerine gelindiğinde Önizleme sekmesi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.FileTabProvisionalHover` |
| Ön plan (metin) | `Environment.FileTabProvisionalHoverForeground` |
| Kenarlık | `Environment.FileTabProvisionalHoverBorder`<br />(Aynı arka plan rengini ayarlayın.) |

#### <a name="document-overflow-button"></a>Belge Taşma düğmesi  
Belge Taşma düğmesi, bir veya daha fazla belge olup olmamasına bakılmaksızın açık, mevcut ise tüm belge sekmeleri uyacak şekilde, geçerli yapılandırma dikey boşluk yoktur. Denetlenen belge taşma açılan menüsünü [menü çubuğu komut](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) renkleri, bütün açık belgeleri, görünür ve gizli ve taşma glif değişiklikleri tüm açık belgeleri olmanıza bağlı olarak bir listesini görüntüler Sekme kanalda görüntülenir.  

![Belge taşma düğmesini (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303 083_OverflowRedline")<br />Belge taşma düğmesini (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |
| ... bir özel belge taşma düğmesini oluştururken. | taşma düğmesini için benzer olmayan... için kullanıcı Arabirimi. |
| | ... komut çubuğu taşma düğmeleri için. |

**Belge Taşma Düğmesi: varsayılan durumu**  

![Varsayılan Belge taşma düğmesini](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303 084_Overflow")<br />Varsayılan Belge Taşma düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.DocWellOverflowButtonBackground` |
| Ön plan (karakter) | `Environment.DocWellOverflowButtonGlyph` |
| Kenarlık | Yok |

**Belge Taşma Düğmesi: duruma getirin**

![Belge taşma düğmesini üzerine gelindiğinde](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303 085_OverflowHover")<br />Üzerine gelindiğinde belge taşma düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Ön plan (karakter) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Kenarlık | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Belge Taşma Düğmesi: basılı durumu**  

![Belge taşma düğmesini makinesinde](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303 086_OverflowPressed")<br />Belge Taşma düğmesine basın

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Ön plan (karakter) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Kenarlık | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Etiketleme  
Visual Studio etiketleme, izleme amacıyla aranabilir anahtar sözcükleri bildirmek bir kullanıcı sağlayan destekler. Örneğin, proje yöneticileri ve geliştiriciler Team Foundation Server (TFS) iş öğelerini etiketlemek için kullanabilirsiniz. Aşağıdaki tablolarda, etiket hem üzerine gelin ve seçili durumlardan görünür "simge" Kapat"karakteri için renk adlar verin.  

![Visual Studio'da etiketleme (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303 176_TaggingRedline")<br />Visual Studio'da etiketleme (kırmızı çizgi)  

| Kullan... | Kullanmayın... |
| --- | --- |
| etiketleme destekleyen... için kullanıcı Arabirimi. | ... başka türde UI için. |

#### <a name="tags"></a>Etiketler  

**Etiket: varsayılan durumu**

![Varsayılan etiket](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303 177_Tag")<br />Varsayılan etiketi

| Öğe | Belirteç adı: Category.color |
| --- | --- |  
| Arka Plan | `Tag.Background` |
| Ön plan (metin) | `Tag.Background` |

**Etiket: vurgulu durumu**  

![Üzerine gelindiğinde etiketi](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303 178_TagHover")<br />Üzerine gelindiğinde etiketi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |  
| Arka Plan | `Tag.HoverBackground` |
| Ön plan (metin) | `Tag.HoverBackgroundText` |

**Etiket: basılı durumu**

![Etiket basılı](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303 179_TagPressed")<br />Basılan etiketi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Tag.PressedBackground` |
| Ön plan (metin) | `Tag.PressedBackgroundText` |

**Etiketi: seçilen durum**

![Seçili etiketi](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303 180_TagSelected")<br />Seçili etiketi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Tag.SelectedBackground` |
| Ön plan (metin) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Kapat (&times;) simge etiketi

**Kapat (&times;) simge etiketi: varsayılan durumu**

![Varsayılan Kapat (&times;) simge etiketi](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303 181_TagGlyph")<br />Varsayılan Kapat (&times;) simge etiketi

| Öğe | Belirteç adı: Category.color |
| --- | --- |  
| Arka Plan | Yok |
| Ön plan (karakter) | `Tag.TagHoverGlyph` |

**Kapat (&times;) simge etiketi: duruma getirin**

![Kapat (&times;) üzerine gelindiğinde simge etiketi](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303 182_TagGlyphHover")<br />Kapat (&times;) üzerine gelindiğinde simge etiketi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Tag.TagHoverGlyphHoverBackground` |
| Ön plan (karakter) | `Tag.TagHoverGlyphHover` |
| Kenarlık | `Tag.TagHoverGlyphHoverBorder` |

**Kapat (&times;) simge etiketi: basılı durumu**

![Basılan Kapat (&times;) simge etiketi](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303 183_TagGlyphPressed")<br />Basılan Kapat (&times;) simge etiketi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Tag.TagHoverGlyphPressedBackground` |
| Ön plan (karakter) | `Tag.TagHoverGlyphPressed` |
| Kenarlık | `Tag.TagHoverGlyphPressedBorder` |

**Kapanış etiketi seçili (&times;) karakter: varsayılan durumu**

![Seçili kapatma etiketi varsayılan (&times;) karakter](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303 184_TagSelected")<br />Seçili kapatma etiketi varsayılan (&times;) karakteri

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (karakter) | `Tag.TagSelectedGlyph` |

**Kapanış etiketi seçili (&times;) karakter: duruma getirin**  

![Kapanış etiketi seçili (&times;) üzerine gelindiğinde glif](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303 185_TagSelectedHover")<br />Kapanış etiketi seçili (&times;) üzerine gelindiğinde karakter  


| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Tag.TagSelectedGlyphHoverBackground` |
| Ön plan (karakter) | `Tag.TagSelectedGlyphHover` |
| Kenarlık | `Tag.TagSelectedGlyphHoverBorder` |

**Kapanış etiketi seçili (&times;) karakter: basılı durumu**  

![Seçili, basılı kapanış etiketi (&times;) karakter](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303 186_TagSelectedPressed")<br />Seçili, basılı kapanış etiketi (&times;) karakteri

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Tag.TagSelectedGlyphPressedBackground` |
| Foreground(glyph) | `Tag.TagSelectedGlyphPressed` |
| Kenarlık | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Araç pencereleri  
Visual Studio ortamı tarafından sağlanan çünkü araç pencerelerinin çoğaltmak için gerek yoktur. Ancak, kullanıcı Arabirimi her zaman Visual Studio ortamının bu bölümü ile tutarlı görünmesi araç pencerelerinde kullanılan renkleri yararlanmak istediğinize karar verin.  

![Araç penceresi (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303 087_ToolWindowRedline")<br />Araç penceresi (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |
| ... herhangi bir yerde araç pencerelerini eşleştirmek istediğiniz kullanıcı Arabirimi oluşturmakta olduğunuz. | ... varsa otomatik olarak değiştirmek istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir. |

### <a name="tool-window-frame"></a>Araç pencere çerçevesi  
Visual Studio araç pencereleri, birçok farklı görevler için kullanılır ve birçok farklı durumdan birinde bulunabilir. Araç penceresi açık değilse, tüm belge alanını dört tarafına atanabilir. Araç pencerelerini de herhangi bir kullanıcının ekranında konumlandırılmasına olanak tanıyan IDE dışında kaydırabilirsiniz. Kayan windows her zaman, IDE üzerinde durur. Son olarak, araç pencerelerini belge pencereleri yerleştirilmiş olabilir ve iyi belge sekme olarak görünür. Belge pencereleri yerleştirilmiş araç pencereleri, kısmen belge penceresi simge adları kullanarak renklendirilmiştir.  

![Araç pencere çerçevesi (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303 088_ToolWindowFrameRedline")<br />Araç pencere çerçevesi (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |
| ... herhangi bir yerde araç pencerelerini eşleştirmek istediğiniz kullanıcı Arabirimi oluşturmakta olduğunuz. | ... varsa otomatik olarak değiştirmek istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir. |

**Yerleşik araç penceresi**  

![Yerleşik araç penceresi](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303 089_ToolWindowDocked")<br />Yerleşik araç penceresi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowBackground` |
| Kenarlık | `Environment.ToolWindowBorder` |

**Kayan, odaklanmış araç penceresi**

![Kayan, araç penceresi odaklanmış](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303 090_ToolWindowFocused")<br />Kayan, odaklanmış araç penceresi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowBackground` |
| Kenarlık | `Environment.MainWindowActiveDefaultBorder` |

**Kayan, plana odaklanmadan araç penceresi**  

![Kayan, plana odaklanmadan araç penceresi](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303 091_ToolWindowUnfocused")<br />Kayan, plana odaklanmadan araç penceresi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowBackground` |
| Kenarlık | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Araç kutusu gibi windows
Araç, Visual Studio'da en sık kullanılan ortak araç pencereleri biridir. Aslında bir ağaç denetimi ile özel teması ve stil uygulanmış olduğu.  

![Araç kutusu benzeri penceresi (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303 189_ToolboxRedline")<br />Araç kutusu benzeri penceresi (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |
| ... olduğunda, tasarlama, her zaman shell araç ile tutarlı olmasını istediğiniz araç penceresi. | Araç kutusu kullanıcı Arabirimi, benzer olmayan her şey için... veya değişiklik shell araç kutusuna renklerini, kullanıcı Arabirimi sorunları olup olmadığını olacak emin değilseniz. |

**Araç kutusu düğümleri: varsayılan durumu**

![Varsayılan araç kutusunu üst düğümü](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303 190_ToolboxParentNode")<br />Varsayılan araç kutusunu üst düğümü

![Varsayılan araç kutusunu alt düğüm](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303 191_ToolboxChildNode")<br />Varsayılan araç kutusunu alt düğümü

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ToolboxContent`<br />(Başlıkları) |
| Arka Plan | `Environment.ToolWindowBackground`<br />(Ayrı ayrı öğeleri veya hiçbir kullanılabilir denetimleri, tüm pencere) |
| Kenarlık | Yok. |
| Ön plan (karakter) | `Environment.ToolboxContent` |
| Ön plan (metin) | `Environment.ToolboxContent` |

**Araç kutusu alt düğümleri: duruma getirin**

![Üzerine gelindiğinde Araç kutusu alt düğüm](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")<br />Üzerine gelindiğinde Araç kutusu alt düğümü  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ToolboxContentMouseOver`<br />(Yalnızca tek tek öğeleri) |
| Kenarlık | Yok. |
| Ön plan (metin) | `Environment.ToolboxContentMouseOver`<br />(Yalnızca tek tek öğeleri) |

**Araç kutusu düğümleri seçilen: odaklanmış durumu**

![Odaklanmış, seçilen araç kutusu üst düğümü](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")<br />Odaklanmış, seçilen araç kutusu üst düğümü  

![Araç odaklanmış, seçili alt düğüm](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")<br />Odaklanmış, seçilen araç kutusu alt düğümü

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `TreeView.SelectedItemActive`<br />Gelen [ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisi |
| Kenarlık | `TreeView.FocusVisualBorder`<br />Gelen [ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisi |
| Ön plan (karakter) | `TreeView.SelectedItemActive`<br />Gelen [ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisi |
| Ön plan (metin) | `TreeView.SelectedItemActive`<br />Gelen [ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisi |

**Araç kutusu düğümleri seçilen: odaklanmadan durumu**

![Üst düğümü seçildiğinde, plana odaklanmadan araç kutusu](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")<br />Üst düğümü seçildiğinde, plana odaklanmadan araç kutusu  

![Alt düğümü seçildiğinde, plana odaklanmadan araç kutusu](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")<br />Alt düğümü seçildiğinde, plana odaklanmadan araç kutusu  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `TreeView.SelectedItemInactive`<br />Gelen [ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisi |
| Kenarlık | Yok. |
| Ön plan (karakter) | `TreeView.SelectedItemInactive`<br />Gelen [ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisi |
| Ön plan (metin) | `TreeView.SelectedItemInactive`<br />Gelen [ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisi |

### <a name="tool-window-title-bar"></a>Araç penceresinin başlık çubuğu  
Başlık çubuğu kenarlığı doğru kenarlık değil, kalın çizgi başlık çubuğunun üst kısmında. Bu, bir belirteç adı odaklanmadan durumuna sahip değil.  

![Araç penceresinin başlık çubuğu (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303 092_ToolWindowTitleBarRedline")<br />Araç penceresinin başlık çubuğu (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |
| ... herhangi bir yerde araç pencerelerini eşleştirmek istediğiniz kullanıcı Arabirimi oluşturmakta olduğunuz. | ... varsa otomatik olarak değiştirmek istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir. |

**Odaklanmış başlık çubuğu**

![Odaklanmış başlık çubuğu](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303 093_TitleBarFocused")<br />Odaklanmış başlık çubuğu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.TitleBarActiveGradientBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (metin) | `Environment.TitleBarActiveText` |
| Kenarlık | `Environment.TitleBarActiveBorder`<br />(Aynı arka plan rengini ayarlayın.) |
| Sürükleme tutamacı | `Environment.TitleBarDragHandleActive` |

**Plana odaklanmadan başlık çubuğu**  

![Başlık çubuğu odaklanmadan](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303 094_TitleBarUnfocused")<br />Plana odaklanmadan başlık çubuğu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.TitleBarInactiveGradientBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (metin) | `Environment.TitleBarInactiveText` |
| Kenarlık | Yok |
| Sürükleme tutamacı | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Araç penceresinin başlık çubuğu düğmeleri  
![Başlık düğme (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303 095_TitleBarButtonRedline")<br />Başlık düğme (kırmızı çizgi)  

| Kullan... | Kullanmayın... |
| --- | --- |
| ... tuşları araç penceresinin başlık çubuğu renk belirteçleri kullanan kullanıcı arabiriminde görüntülenen. | diğer konumlardaki... düğmeler için. |
| | Belirtilen dışındaki... tüm arka plan/ön plan birlikte. |

**Başlık çubuğu düğmelerinin odaklanır: varsayılan durumu**

![Varsayılan, başlık çubuğu düğmelerinin odaklanmış](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")<br />Varsayılan, odaklanmış başlık çubuğu düğmeleri  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (karakter) | `Environment.ToolWindowButtonActiveGlyph` |
| Kenarlık | Yok |

**Plana odaklanmadan başlık çubuğu düğmelerinin: varsayılan durumu**

![Varsayılan, plana odaklanmadan başlık çubuğu düğmelerinin](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")<br />Varsayılan, plana odaklanmadan başlık çubuğu düğmeleri    

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (karakter) | `Environment.ToolWindowButtonInactiveGlyph` |
| Kenarlık | Yok |

**Başlık çubuğu düğmelerinin odaklanır: duruma getirin**  

![Başlık çubuğu düğme üzerine gelindiğinde odaklanmış](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")<br />Üzerine gelindiğinde odaklanmış başlık çubuğu düğmeleri

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowButtonHoverActive` |
| Ön plan (karakter) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Kenarlık | `Environment.ToolWindowButtonHoverActiveBorder` |

**Plana odaklanmadan başlık çubuğu düğmelerinin: duruma getirin**  

![Üzerine gelindiğinde odaklanmadan başlık çubuğu düğmelerinin](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")<br />Üzerine gelindiğinde odaklanmadan başlık çubuğu düğmeleri

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowButtonHoverInactive` |
| Ön plan (karakter) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Kenarlık | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Başlık çubuğu düğmelerinin odaklanır: basılı durumu**

![Başlık çubuğu düğmelerinin makinesinde odaklanmış](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")<br />Odaklanmış başlık çubuğu düğmelerinin makinesinde

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowButtonDown` |
| Ön plan (karakter) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Kenarlık | `Environment.ToolWindowButtonDownBorder` |

**Plana odaklanmadan başlık çubuğu düğmelerinin: basılı durumu**

![Plana odaklanmadan başlık çubuğu düğmelerinin makinesinde](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")<br />Plana odaklanmadan başlık çubuğu düğmelerinin makinesinde  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowButtonDown` |
| Ön plan (karakter) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Kenarlık | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Araç penceresi sekmeleri  
![Araç penceresi sekmesine (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303 102_ToolWindowTabRedline")<br />Araç penceresi sekmesine (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |
| ... herhangi bir yerde araç pencerelerini eşleştirmek istediğiniz kullanıcı Arabirimi oluşturmakta olduğunuz. | ... varsa otomatik olarak değiştirmek istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir. |

**Seçildiğinde, odaklanmış aracı penceresi sekmesi**

![Seçili, araç penceresi sekmesinin odaklanmış](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")<br />Seçildiğinde, odaklanmış aracı penceresi sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowTabSelectedTab` |
| Ön plan (metin) | `Environment.ToolWindowTabSelectedActiveText` |
| Kenarlık | `Environment.ToolWindowTabSelectedBorder`<br />(Aynı arka plan rengini ayarlayın.) |

**Seçildiğinde, plana odaklanmadan aracı penceresi sekmesi**  

![Seçildiğinde, plana odaklanmadan araç penceresi sekmesinin](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")<br />Seçildiğinde, plana odaklanmadan aracı penceresi sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowTabSelectedTab` |
| Ön plan (metin) | `Environment.ToolWindowTabSelectedText` |
| Kenarlık | `Environment.ToolWindowTabSelectedBorder`<br />(Aynı arka plan rengini ayarlayın.) |

**Arka plan aracı penceresi sekmesi: varsayılan durumu**

![Varsayılan arka plan araç penceresi sekmesinin](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")<br />Varsayılan arka plan aracı penceresi sekmesi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Visual Studio 2013'te aynı renk değeri kümesine gradyan durdurur.) |
| Ön plan (metin) | `Environment.ToolWindowTabText` |
| Kenarlık | `Environment.ToolWindowTabBorder` |

**Arka plan aracı penceresi sekmesi: duruma getirin**

![Üzerine gelindiğinde kullanılacak arka plan araç penceresi sekmesinde](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")<br />Üzerine gelindiğinde arka plan aracı penceresi sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Visual Studio 2013'te aynı renk değeri kümesine gradyan durdurur.) |
| Ön plan (metin) | `Environment.ToolWindowTabMouseOverText` |
| Kenarlık | `Environment.ToolWindowTabMouseOverBorder`<br />(Aynı arka plan rengini ayarlayın.) |  

### <a name="auto-hide-tabs"></a>Sekmeleri otomatik olarak gizle  

![Otomatik gizleme sekmeler (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303 107_AutoHideRedline")otomatik gizleme sekmeler (kırmızı çizgi)

| Kullan... | Kullanmayın... |
| --- | --- |
| ... otomatik olarak gizlendiğinde araç penceresi sekmeleri eşleştirmek istediğiniz kullanıcı Arabirimi oluşturmakta olduğunuz herhangi bir yerde. | ... varsa otomatik olarak değiştirmek istemediğiniz herhangi bir kullanıcı Arabirimi için bir tema güncelleştirme Kabuk sahiptir. |

**Sekmeleri otomatik gizleme: varsayılan durumu**  

![Varsayılan otomatik gizleme sekmesi](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303 108_AutoHideTab")<br />Varsayılan otomatik gizleme sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.AutoHideTabBackgroundBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (metin) | `Environment.AutoHideTabText` |
| Kenarlık | `Environment.AutoHideTabBorder` |

**Sekmeleri otomatik gizleme: duruma getirin**

![Üzerine gelindiğinde otomatik gizleme sekmesini](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303 109_AutoHideTabHover")<br />Üzerine gelindiğinde otomatik gizleme sekmesi  

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Temalı kullanıcı Arabiriminde kullanılmayan bu belirteç için gradyan duraklarının.) |
| Ön plan (metin) | `Environment.AutoHideTabMouseOverText` |
| Kenarlık | `Environment.AutoHideTabMouseOverBorder` |
