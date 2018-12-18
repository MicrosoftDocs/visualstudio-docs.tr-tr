---
title: Dosya, sembol'e Git satıra Git için Git
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d9ceeb7c4d24871bc0f2ddfc743c2c65e087205
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907059"
---
# <a name="find-code-using-go-to-commands"></a>Git komutlarını kullanarak kod bulma

Visual Studio'nun **Git** komutları belirtilen öğeleri hızlı bir şekilde bulmanıza yardımcı olmak üzere, kodunuzun odaklanmış bir arama gerçekleştirin. Belirli bir satır, tür, sembol, dosya ve üye için basit ve birleşik bir arabirimden gidebilirsiniz. Bu özellik, Visual Studio 2017 ve sonraki sürümlerinde bulunmaktadır.

## <a name="how-to-use-it"></a>Nasıl kullanılacağını

Giriş | İşlev
------------ | ---
**Klavye** | Tuşuna **Ctrl**+**T** veya **Ctrl**+**,**
**Fare** | Seçin **Düzenle** > **Git** > **tümüne Git**

Küçük bir pencere üst kısmında görüntülenir, Kod Düzenleyicisi, doğru.

![Tümüne Git penceresi](media/go-to-all.png)

Metin kutusuna yazdığınız sırada, sonuçları bir metin kutusunun altındaki açılır listede görüntülenir. Bir öğeye gitmek için listeden seçin.

![Git penceresini](../ide/media/vside_navigatetowindow.png)

Bir soru işareti de girebilirsiniz (**?**) ek Yardım almak için.

![Tüm Yardım'a gidin](media/go-to-all-help.png)

## <a name="filtered-searches"></a>Filtrelenmiş aramalar

Varsayılan olarak, tüm çözüm öğeleri için belirtilen öğeyi aranır. Ancak, arama terimleri belirli karakterlerle koyarak tarafından belirli bir öğe türleri için kod arama sınırlayabilirsiniz. Düğmeler seçim yaparak arama filtresi ayrıca bir kolayca değiştirebilirsiniz **Git** iletişim kutusu araç çubuğu. Sol taraftaki türü filtrelerini Değiştir düğmeleri ve sağ taraftaki arama kapsamını değiştirmek düğme vardır.

![Üye gidin](../ide/media/vside_navigation_toolbar.png)

### <a name="filter-to-a-specific-type-of-code-element"></a>Kod öğesinin belirli bir türe göre filtrele

Belirli türde bir kod öğesi için aramanızı daraltmak için arama kutusuna bir ön ek belirtin veya beş filtre simgelerden birini seçebilirsiniz:

Ön eki | Simge | Kısayol | Açıklama
:-: | - | - | -
:| ![Satır simgesi](media/gotoall-line-icon.png) | **CTRL**+**G** | Belirtilen satır numarası gidin
F| ![Dosyalar simgesi](media/gotoall-files-icon.png) | **CTRL**+**1**, **Ctrl**+**F** | Belirtilen dosyaya Git
r| ![Son Dosyalar simgesi](media/gotoall-recent-files-icon.png) | **CTRL**+**1**, **Ctrl**+**R** | Belirtilen en son ziyaret edilen dosyaya Git
t| ![Tür simgesi](media/gotoall-types-icon.png) | **CTRL**+**1**, **Ctrl**+**T** | Belirtilen türe Git
m| ![Üye simgesi](media/gotoall-members-icon.png) | **CTRL**+**1**, **Ctrl**+**M** | Belirtilen üyeye Git
\#| ![Sembol simgesi](media/gotoall-symbols-icon.png) | **CTRL**+**1**, **Ctrl**+**S** | Belirtilen sembol'e Git

### <a name="filter-to-a-specific-location"></a>Belirli bir konuma Filtrele

Belirli bir konuma aramanızı daraltmak için iki belge simgelerden birini seçin:

Simge | Açıklama
---- | ---
![Geçerli belge](media/gotoall_currentdocument.png) | Yalnızca geçerli belgede arama
![Dış belgeleri](media/gotoall_external.png) | Bunlara ek olarak proje/çözüm bulunan dış belge Ara

## <a name="camel-casing"></a>Camel casing

Kullanırsanız [camel casing](https://en.wikipedia.org/wiki/Camel_case) kodunuzda yalnızca büyük harf kod öğe adı girerek daha hızlı kod öğeleri bulabilirsiniz. Kodunuzu adlı bir türü varsa, örneğin, `CredentialViewModel`, seçerek, aramayı daraltmak **türü** filtre (**t**) ve ardından yalnızca büyük harf adı girerek (`CVM`) içinde Git iletişim kutusu. Bu özellik, kodunuzu uzun adı varsa yararlı olabilir.

![Pencere Git ile büyük harflerin arama-](../ide/media/vside_capitalsearch.png)

## <a name="settings"></a>Ayarlar

Dişli simgesini seçme ![Dişli simgesi](media/gotoall_gear.png) Bu özellik çalışma şeklini değiştirmenize olanak sağlar:

Ayar | Açıklama
------- | ---
Önizleme sekmesini kullan | Seçili öğeyi IDE'nin Önizleme sekmesinde hemen görüntüler.
Ayrıntıları Göster | Proje, dosya, satır ve belge açıklamaları Özet bilgilerden pencerede görüntülemektir.
Pencereyi Ortala | Üst Orta kısmındaki Kod düzenleyicisinde, sağ üst yerine bu pencereyi Taşı

## <a name="see-also"></a>Ayrıca bkz.

- [Kod gidin](../ide/navigating-code.md)
- [Satıra Git iletişim kutusu](../ide/reference/go-to-line.md)
- [Tanıma ve Özet Tanıma Gitme](../ide/go-to-and-peek-definition.md)