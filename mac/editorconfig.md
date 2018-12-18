---
title: EditorConfig
description: Mac için Visual Studio'da stilleri kodlama tutarlı proje için bir editorconfig dosyası kullanma
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: d42103d17b64ee9b3fb2a0660017824490655808
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294025"
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Oluşturma ve özel bir EditorConfig dosyasını düzenleme

Mac için Visual Studio'da ekleyebileceğiniz bir [EditorConfig](http://editorconfig.org/) projenizi veya çözümünüzü tutarlı kodlama uygulamak için dosya stiller herkes kod temelinde çalışır. EditorConfig dosyasında bildirilen ayarları için Mac metin düzenleyici ayarları genel Visual Studio önceliklidir. Bir EditorConfig kullanarak projeniz dosya ya da kod tabanı, kodlama stili tercihleri ve projeniz için uyarılar ayarlamanıza olanak tanır. Dosyayı kod temelinizde bir parçası olduğundan, tüm kullanıcıların kullandıkları IDE ya da kod düzenleyicinizi bakılmaksızın, bir projenin kodlama uygulamalarını izliyor kolaylaştırır.

[EditorConfig](http://editorconfig.org/) dosyaları, Visual Studio 2017'de dahil olmak üzere birçok IDE ve kod düzenleyicilerini üzerinde desteklenir.

## <a name="supported-settings"></a>Desteklenen ayarlar

Mac için Visual Studio düzenleyicisinde çekirdek kümesini destekleyen [EditorConfig özellikleri](http://editorconfig.org/#supported-properties):

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig da destekler [kodlama kuralları](/visualstudio/ide/editorconfig-code-style-settings-reference) C#.

## <a name="add-an-editorconfig-file-to-a-project"></a>EditorConfig dosyası bir projeye ekleyin.

### <a name="adding-a-new-editorconfig-file"></a>Yeni bir EditorConfig dosya ekleme

1. Mac için Visual Studio projenizi açın EditorConfig dosyasına eklemek istediğiniz çözümü veya proje düğümünü seçin. Çözüm dizinine dosya ekleme, Çözümdeki tüm projelere .editorconfig ayarlarını uygular.

2. Sağ tıklatın ve düğüm **Ekle > yeni dosya** açmak için **yeni dosya** iletişim:

    ![İçerik menü öğeleri](media/editorconfig-image0.png)

3. Seçin **çeşitli > boş metin dosyası** ve verin **adı** `.editorconfig`. Tuşuna **yeni** dosyası oluşturma ve düzenleyicide açın:

    ![Yeni dosya iletişim kutusu](media/editorconfig-image1.png)

    Öğe Çözüm düzeyinde otomatik olarak ekleme oluşturur ve bunu katmandan bir **çözüm öğeleri** klasörü:

    ![Çözüm panelinde görüntülenen çözüm öğesi](media/editorconfig-image1a.png)

4. Dosyayı düzenleyin. Örneğin:

    ```EditorConfig
    # This file is the top-most EditorConfig file
    root = true

    # All Files
    [*]
    indent_style = space
    indent_size = 8
    insert_final_newline = false
    trim_trailing_whitespace = false

    [*.cs]
    csharp_new_line_before_open_brace = none
    ```

4. Ayarlardan `.editorconfig` dosya yazdığınız yeni kod için geçerli, ancak mevcut kodu yeni ayarlar ile tutarlı olacak şekilde yeniden biçimlendirildi gerekebilir. Ayarları uygulamak için `.editorconfig` dosya mevcut bir kaynak dosyasına, dosyayı açın ve seçin **Düzenle > biçim > Belgeyi Biçimlendir** menü çubuğundan::

    ![Biçim belgesi menü öğesi](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Mevcut bir EditorConfig dosyasını ekleme

Çalıştığınız bir proje veya çözüm zaten içeren bir `.editorconfig` dosya, ayarları uygulamak için gerçekleştirmeniz gereken bir şey yoktur. Yeni bir kod satırlarını EditorConfig ayarlarına göre biçimlendirilir.

Mevcut bir yeniden kullanmak isteyebileceğiniz `.editorconfig` projenizdeki dosya. Varolan bir dosyayı eklemek için aşağıdakileri yapın:

1. Seçin ve eklemek istediğiniz klasörü sağ tıklatın **Ekle > Add Files**.

2. Gerekli dosyanın dizinine gidin.

3. İle başlayan dosyaları `.` (gibi `.editorconfig`) gizli dosyalar macOS, bu nedenle basın **Command + Shift +.** yapmak `.editorconfig` dosya görünür.

4. Seçin `.editorconfig` tıklayın ve dosya **açık**:

    ![Yeni bir dosya penceresi ekleme](media/editorconfig-image3b.png)

5. Aşağıdaki iletişim kutusuyla karşılaşırsınız bittiğinde **dosyayı dizine kopyalayın** seçeneğini işaretleyip **Tamam**:

    ![Klasör iletişim kutusu seçenekleri dosyası ekleme](media/editorconfig-image3.png)

### <a name="reflecting-editorconfig-settings"></a>.Editorconfig ayarları yansıtılıyor

Kod temelinizde yapılan bir EditorConfig dosyası ekledikten sonra eklenen herhangi bir yeni kod otomatik olarak belirtilen ayarlarına göre biçimlendirilir. Kod temeli biçimlendirme sürece varolan kodu otomatik olarak ayarlarını yansıtmaz.

Ayarları yansıtacak şekilde `.editorconfig` dosya, çözüm düğümü seçin ve seçin **Düzenle > biçim > Belgeyi Biçimlendir** menü çubuğundan:

![Menü çubuğundan belgeyi Biçimlendir](media/editorconfig-image3a.png)

## <a name="editing-an-editorconfig-file"></a>EditorConfig dosyasını düzenleme

EditorConfig dosyaları basit dosya düzeni kullanarak önceki örneğin aşağıda açıklanan ayarlarını belirtmek için kullanın:

```EditorConfig
# This file is the top-most EditorConfig file
root = true

# All Files
[*]
indent_style = space
indent_size = 4
insert_final_newline = false
trim_trailing_whitespace = false

[*.cs]
csharp_new_line_before_open_brace = none
```

Ayarı `root` için `true` en üstteki dosyası olarak kod tabanının ve daha bu dosyayı işaretler `.editorconfig` projesindeki dosyalar yok sayılır açıklandığı şekilde [EditorConfig ayarlarını geçersiz kıl](#override-editorconfig-settings) bölümü.

Her bölümde kare gösterilir (**[]**) küme ayraçları ve bilgi aşağıdaki özellikleri ilgilidir dosya türlerini belirtir.

Yukarıdaki örnekte, projedeki tüm dosyalar için bazı ayarlar uygulanır ve diğerleri yalnızca C# dosyaları için eklenir. Önce ve sonra aşağıdaki ekran görüntüleri Göster `.editorconfig` ayarları uygulanır:

**Önce**:

![Editorconfig önce ayarları uygulandı](media/editorconfig-image4.png)

**Sonra**:

![editorconfig ayarları uygulandıktan sonra](media/editorconfig-image5.png)

EditorConfig kullanılabilir ayarlar hakkında daha fazla bilgi için bkz. [.NET kodlama kuralı ayarlarına EditorConfig için](/visualstudio/ide/editorconfig-code-style-settings-reference) makale ve [desteklenen özellikleri](http://editorconfig.org/#supported-properties) resmi belgelerine bölümü.

## <a name="override-editorconfig-settings"></a>EditorConfig ayarlarını geçersiz kıl

Birden fazla olması mümkündür `.editorconfig` dosyasında her bir çözüm. Visual Studio Mac okuma için `.editorconfig` çözümde alt üst dosyaları, ekleme ve bu ayarlarda geçersiz kılma gider. Ayarları buna `.editorconfig` _en yakın_ düzenlediğiniz dosya öncelikli olur. Ayarları verilerinden alınır `.editorconfig` dosyası (varsa) aynı klasörü sonra `.editorconfig` (varsa) üst klasörü, vs. Bu bulana kadar `root=true`.

Emin olmak istiyorsanız _hiçbir_ ayarlarından herhangi üst düzey `.editorconfig` dosyaları kod tabanının kısmına uygulanır, ekleme `root=true` en düşük düzeyli özelliğini `.editorconfig` dosyası:

```EditorConfig
# top-most EditorConfig file
root = true
```

## <a name="see-also"></a>Ayrıca bkz.

- [EditorConfig (Windows için Visual Studio) ile özel düzenleyici ayarları oluşturma](/visualstudio/ide/create-portable-custom-editor-options)