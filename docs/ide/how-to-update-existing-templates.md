---
title: Mevcut proje öğesi şablonları güncelleştirme
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 52f24f76ff217b694a1e5d2b510d16b0911d2fda
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061474"
---
# <a name="how-to-update-existing-templates"></a>Nasıl yapılır: mevcut şablonları güncelleştirme

Bir şablon oluşturmak ve içine dosyaları sıkıştır sonra bir *.zip* dosyası şablonu değiştirmek isteyebilirsiniz. Şablon dosyaları el ile değiştirerek veya bir projeden şablonu temel alan yeni bir şablon vererek bunu yapabilirsiniz.

## <a name="using-the-export-template-wizard-to-update-an-existing-project-template"></a>Mevcut bir proje şablonu güncellemek için şablonu Dışarı Aktarma Sihirbazı'nı kullanarak

Visual Studio sağlar bir **şablonu Dışarı Aktarma Sihirbazı** mevcut bir şablonu güncellemek için kullanılabilir:

1. Açık **yeni proje** iletişim kutusunu **dosya** > **yeni** > **proje**.

1. Güncelleştirme, bir ad ve projenizin konumunu girin ve seçmek istediğiniz şablonu seçin **Tamam**.

1. Visual Studio'da proje değiştirin.

1. Üzerinde **proje** menüsünde seçin **şablonu dışarı aktar**.

    **Şablonu Dışarı Aktarma Sihirbazı** açılır.

1. Şablon olarak dışarı aktarmak için sihirbazdaki istemleri izleyerek bir *.zip* dosya.

1. (İsteğe bağlı) Şablona eklemek için **yeni proje** iletişim kutusu, bir yerde *.zip* dosyası aşağıdaki dizinde: *%USERPROFILE%\Documents\Visual Studio \<sürüm\>\Templates\ProjectTemplates*. Seçeneğini seçmediyseniz, bu adımı gerçekleştirmeniz gerekecektir **otomatik olarak şablonu Visual Studio'ya içeri aktarma** içinde **şablonu Dışarı Aktarma Sihirbazı**.

1. Eski Şablonu Sil *.zip* dosya.

## <a name="manually-update-an-existing-template"></a>Mevcut bir şablonu el ile güncelleştirme

Mevcut bir şablonu kullanmadan güncelleştirebilirsiniz **şablonu Dışarı Aktarma Sihirbazı**, sıkıştırılmış dosyalarda değiştirerek *.zip* dosya.

### <a name="to-manually-update-an-existing-template"></a>Mevcut bir şablonu el ile güncelleştirmek için

1. Bulun *.zip* şablonu içeren dosya. Kullanıcı proje şablonları konumu *%USERPROFILE%\Documents\Visual Studio \<sürüm\>\Templates\ProjectTemplates*.

1. Ayıklama *.zip* dosya.

1. Değiştirmek ya da geçerli şablon dosyaları silin veya şablona yeni dosyalar ekleyin.

1. Açık, değiştirebilir ve Kaydet *.vstemplate* güncelleştirilmiş davranışı ya da yeni dosyaları işlemek için XML dosyası.

    Hakkında daha fazla bilgi için *.vstemplate* şema bakın [Visual Studio Şablon Şeması Başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md). Kaynak dosyalarında parametreleştirebilirsiniz hakkında daha fazla bilgi için bkz. [şablon parametreleri](../ide/template-parameters.md).

1. Dosyaları şablonunuzdaki ve sağ tıklayın veya bağlam menüsünü seçin ve seçin **göndermek** > **sıkıştırılmış (daraltılmış) klasör**.

    Seçtiğiniz dosyalar sıkıştırılmadan bir *.zip* dosya.

1. Yeni put *.zip* eski ile aynı dizinde dosya *.zip* dosya.

1. Ayıklanan şablon dosyalarını ve eski şablonu silmek *.zip* dosya.

## <a name="see-also"></a>Ayrıca bkz.

- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Şablon parametreleri](../ide/template-parameters.md)