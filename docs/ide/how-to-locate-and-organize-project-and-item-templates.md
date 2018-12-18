---
title: Şablon düzenleme
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
- Visual Studio templates, organizing
- templates [Visual Studio], organizing
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c6bca61dd88b164fcae2b2ccb7e2a98086bf102b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066294"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Nasıl yapılır: Proje ve öğe şablonları bulma ve düzenleme

Şablon dosyaları, Visual Studio şablonları görünmesi için tanıdığı bir konumda yerleştirilmelidir **yeni proje** ve **Yeni Öğe Ekle** iletişim kutuları. Kullanıcı şablonu konumu özel alt kategoriler de oluşturabilirsiniz ve kategorileri gösterilir **yeni proje** ve **Yeni Öğe Ekle** iletişim kutuları.

## <a name="locate-templates"></a>Şablonları bulun

Yüklü Şablonlar ve kullanıcı şablonları iki farklı konumlarda depolanır.

### <a name="user-templates"></a>Kullanıcı Şablonları

Sıkıştırılmış eklerseniz (*.zip*) içeren dosyaya bir *.vstemplate* kullanıcı şablon dizini, şablon dosyasına görünür **yeni proje** veya  **Yeni Öğe Ekle** iletişim kutusu. Kullanıcı şablonları varsayılan olarak bulunur:

- *%USERPROFILE%\Documents\Visual studio \<sürüm\>\Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual studio \<sürüm\>\Templates\ItemTemplates*

Örneğin, kullanıcı proje şablonları için aşağıdaki dizine sahip C#:

- *C:\Users\UserName\Documents\Visual Studio 2017\Templates\ProjectTemplates\VisualC#*

> [!TIP]
> Kullanıcı şablonlarında konumunu ayarlayabilirsiniz **Araçları** > **seçenekleri** > **projeler ve çözümler**  >   **Konumları**.

### <a name="installed-templates"></a>Yüklü Şablonlar

Visual Studio ile yüklü şablonlar varsayılan olarak bulunur:

- *\\< VisualStudioInstallationDirectory\>\Common7\IDE\ItemTemplates\\< programlama dili\>\\<Locale ID>*

- *\\< VisualStudioInstallationDirectory\>\Common7\IDE\ProjectTemplates\\< programlama dili\>\\<Locale ID>*

Örneğin, aşağıdaki dizine Visual Basic öğesi şablonları için İngilizce (LCID 1033) vardır:

- *C:\\< VisualStudioInstallationDirectory\>\Common7\IDE\ItemTemplates\VisualBasic\1033*

## <a name="organize-templates"></a>Şablon düzenleme

Kategorileri **yeni proje** ve **Yeni Öğe Ekle** iletişim kutuları yüklü şablon ve kullanıcı şablonu konumlarda mevcut dizin yapılarını yansıtır. Kullanıcı şablonu dizine yeni klasörler ekleyerek kullanıcı şablonları kendi kategoriler halinde düzenlenebilir. **Yeni proje** ve **Yeni Öğe Ekle** iletişim kutuları, kullanıcı şablonu kategorilere yaptığınız herhangi bir değişiklik gösterir.

> [!NOTE]
> Yeni bir kategori programlama dili düzeyinde oluşturulamıyor. Yeni kategori her bir dilin yalnızca oluşturulabilir.

### <a name="to-create-new-user-project-template-categories"></a>Proje şablonu kategorileri yeni kullanıcı oluşturmak için

1. Kullanıcı proje şablonu dizini programlama dili klasörde bir klasör oluşturun. Örneğin, kurmak için bir **HelloWorld** kategorisi için C# proje şablonları, şu dizin oluşturma:

    - *\%USERPROFILE%\Documents\Visual Studio \<sürüm\>\Templates\ProjectTemplates\Visual C#\HelloWorld*

1. Bu kategori için tüm şablonları yeni klasöre yerleştirin.

1. Üzerinde **dosya** menüsünde seçin **yeni** > **proje**.

   **HelloWorld** kategorisi görünür **yeni proje** iletişim kutusunun **yüklü** > **Visual C#** .

### <a name="to-create-new-user-item-template-categories"></a>Öğe şablonu kategorileri yeni kullanıcı oluşturmak için

1. Kullanıcı öğesi şablon dizini programlama dili klasörde bir klasör oluşturun. Örneğin, kurmak için bir **HelloWorld** kategorisi için C# öğe şablonları, şu dizin oluşturma:

    - *\%USERPROFILE%\Documents\Visual Studio \<sürüm\>\Templates\ItemTemplates\Visual C#\HelloWorld*

1. Bu kategori için tüm şablonları yeni klasöre yerleştirin.

1. Bir proje oluşturun veya varolan bir projeyi açın. Ardından **proje** menüsünde seçin **Yeni Öğe Ekle**.

   **HelloWorld** kategorisi görünür **Yeni Öğe Ekle** iletişim kutusunun **yüklü** > **Visual C# öğeleri**.

### <a name="display-templates-in-parent-categories"></a>Üst kategoriler görüntüleme şablonları

Alt kategoriler kullanarak kendi üst kategorilerde görüntülenecek şablonlarında etkinleştirebilirsiniz `NumberOfParentCategoriesToRollUp` öğesinde *.vstemplate* dosya. Bu adımları proje şablonları ve öğe şablonları ile aynıdır.

#### <a name="to-display-templates-in-parent-categories"></a>Üst kategorilerdeki şablonları görüntülemek için

1. Bulun *.zip* şablonu içeren dosya.

1. Ayıklama *.zip* dosya.

1. Açık *.vstemplate* dosyasını Visual Studio'da.

1. İçinde `TemplateData` öğe, Ekle bir `NumberOfParentCategoriesToRollUp` öğesi. Örneğin, aşağıdaki kodu, üst kategori görünür, ancak bundan daha yüksek şablonu sağlar.

    ```xml
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

1. Kaydet ve Kapat *.vstemplate* dosya.

1. Şablonunuzda dosyaları seçin, seçime sağ tıklayın ve seçin **göndermek** > **sıkıştırılmış (daraltılmış) klasör**.

   Dosyalar sıkıştırılmadan bir *.zip* dosya.

1. Ayıklanan şablon dosyalarını ve eski şablonu silmek *.zip* dosya.

1. Yeni put *.zip* silinmiş olan dizinindeki *.zip* dosya.

## <a name="see-also"></a>Ayrıca bkz.

- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Visual Studio Şablon Şeması Başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md)
- [NumberOfParentCategoriesToRollUp (Visual Studio şablonları)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)
- [Nasıl yapılır: Proje şablonları oluşturma](../ide/how-to-create-project-templates.md)
- [Nasıl yapılır: öğe şablonları oluşturma](../ide/how-to-create-item-templates.md)