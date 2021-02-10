---
title: Şablonları bulma
description: Proje ve öğe şablonlarını bulmayı ve düzenlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: ba986fee3f5cf6098b72f3b7a52340a61d3449d0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962866"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Nasıl yapılır: proje ve öğe şablonlarını bulma ve düzenleme

Şablon dosyalarının yeni proje ve yeni öğe iletişim kutularında gösterilmesi için bilinen bir konuma yerleştirilmesi gerekir.

::: moniker range="vs-2017"

Kullanıcı şablonu konumunda özel alt kategoriler de oluşturabilirsiniz ve kategoriler **Yeni proje** ve **Yeni öğe Ekle** iletişim kutularında gösterilir.

::: moniker-end

## <a name="locate-templates"></a>Şablonları bulma

Yüklü şablonlar ve Kullanıcı şablonları iki farklı konumda depolanır.

### <a name="installed-templates"></a>Yüklü şablonlar

Varsayılan olarak, Visual Studio ile yüklenen şablonlar şu konumda bulunur:

::: moniker range="vs-2017"

- *% ProgramFiles (x86)% \\ Microsoft Visual Studio \\ 2017 \\ \<edition> \\ Common7\IDE\ProjectTemplates \\<dil \> \\<yerel ayar kimliği\>*

- *% ProgramFiles (x86)% \\ Microsoft Visual Studio \\ 2017 \\ \<edition> \Common7\IDE\ItemTemplates \\<dil \> \\<yerel ayar kimliği\>*

Örneğin, aşağıdaki dizin Ingilizce için Visual Basic öğesi şablonlarına sahiptir (LCıD 1033):

*C: \\ Program Files (x86) \\ Microsoft Visual Studio \\ 2017 \\ Community \\ Common7 \\ IDE \\ ItemTemplates \\ VisualBasic \\ 1033*

::: moniker-end

::: moniker range=">=vs-2019"

- *% ProgramFiles (x86)% \\ Microsoft Visual Studio \\ 2019 \\ \<edition> \\ Common7\IDE\ProjectTemplates \\<dil \> \\<yerel ayar kimliği\>*

- *% ProgramFiles (x86)% \\ Microsoft Visual Studio \\ 2019 \\ \<edition> \Common7\IDE\ItemTemplates \\<dil \> \\<yerel ayar kimliği\>*

Örneğin, aşağıdaki dizin Ingilizce için Visual Basic öğesi şablonlarına sahiptir (LCıD 1033):

*C: \\ Program Files (x86) \\ Microsoft Visual Studio \\ 2019 \\ Community \\ Common7 \\ IDE \\ ItemTemplates \\ VisualBasic \\ 1033*

::: moniker-end

### <a name="user-templates"></a>Kullanıcı şablonları

Kullanıcı şablonu dizinine *. vstemplate* dosyasını içeren bir sıkıştırılmış (*. zip*) dosya eklerseniz, şablon yeni proje ve yeni öğe iletişim kutularında görünür. Varsayılan olarak, Kullanıcı şablonları içinde bulunur:

::: moniker range="vs-2017"

- *%Userprofile%\, Studio 2017 \ Templates\ProjectTemplates*

- *%Userprofile%\, Studio 2017 \ Templates\ıtemtemplates*

Örneğin, aşağıdaki dizin C# için Kullanıcı projesi şablonlarına sahiptir:

- *C:\users\username\k\studio 2017 \ Templates\ProjectTemplates\Visual C #*

::: moniker-end

::: moniker range=">=vs-2019"

- *%Userprofile%\, Studio 2019 \ Templates\ProjectTemplates*

- *%Userprofile%\, Studio 2019 \ Templates\ıtemtemplates*

Örneğin, aşağıdaki dizin C# için Kullanıcı projesi şablonlarına sahiptir:

- *C:\users\username\k\studio 2019 \ Templates\ProjectTemplates\Visual C #*

::: moniker-end

> [!TIP]
> **Araçlar**  >  **Seçenekler**  >  **projelerinde ve çözüm**  >  **konumlarında** Kullanıcı şablonlarının bilinen konumunu değiştirebilirsiniz.

::: moniker range="vs-2017"

## <a name="organize-templates"></a>Şablonları düzenleme

**Yeni proje** ve **Yeni öğe Ekle** iletişim kutularında bulunan kategoriler, yüklü şablonda ve Kullanıcı şablonu konumlarında bulunan dizin yapılarını yansıtır. Kullanıcı şablonları, Kullanıcı şablonu dizinine yeni klasörler eklenerek kendi kategorilerine göre düzenlenebilir. **Yeni proje** ve **Yeni öğe Ekle** iletişim kutuları, Kullanıcı şablonu kategorileriniz üzerinde yaptığınız tüm değişiklikleri gösterir.

> [!NOTE]
> Programlama dili düzeyinde yeni bir kategori oluşturamazsınız. Yeni kategoriler yalnızca her bir dil içinde oluşturulabilir.

### <a name="create-new-user-project-template-categories"></a>Yeni Kullanıcı projesi şablon kategorileri oluştur

1. Kullanıcı projesi şablon dizinindeki programlama dili klasöründe bir klasör oluşturun. Örneğin, C# proje şablonları için **HelloWorld** kategorisi oluşturmak için aşağıdaki dizini oluşturun:

    - *\%USERPROFILE%\Documents\Visual Studio \<Version\> \Templates\projecttemplates\visual C# \helloworld*

1. Bu kategorinin tüm şablonlarını yeni klasöre yerleştirin.

1. **Dosya** menüsünde **Yeni** > **Proje**' yi seçin.

   **HelloWorld** kategorisi, **Yeni proje** iletişim kutusunda, **yüklü** > **Visual C#** altında görünür.

### <a name="create-new-user-item-template-categories"></a>Yeni Kullanıcı öğesi şablon kategorileri oluştur

1. Kullanıcı öğesi şablon dizinindeki programlama dili klasöründe bir klasör oluşturun. Örneğin, C# öğe şablonları için **HelloWorld** kategorisi oluşturmak için aşağıdaki dizini oluşturun:

    - *\%USERPROFILE%\Documents\Visual Studio \<Version\> \Templates\ıtemtemplates\visual C# \helloworld*

1. Bu kategorinin tüm şablonlarını yeni klasöre yerleştirin.

1. Proje oluşturun veya var olan bir projeyi açın. Ardından, **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

   **HelloWorld** kategorisi, **Yeni öğe Ekle** iletişim kutusunda, **yüklü** > **Visual C# öğeleri** altında görünür.

### <a name="display-templates-in-parent-categories"></a>Şablonları üst kategorilerde görüntüle

Alt kategorilerindeki şablonları, `NumberOfParentCategoriesToRollUp` *. vstemplate* dosyasındaki öğesini kullanarak üst kategorilerinde görüntülenmek üzere etkinleştirebilirsiniz. Bu adımlar proje şablonları ve öğe şablonları için aynıdır.

1. Şablonu içeren *. zip* dosyasını bulun.

1. *. Zip* dosyasını ayıklayın.

1. Visual Studio 'da *. vstemplate* dosyasını açın.

1. `TemplateData`Öğesinde, bir `NumberOfParentCategoriesToRollUp` öğesi ekleyin. Örneğin, aşağıdaki kod, şablonu üst kategoride görünür hale getirir, ancak daha fazlasını yapmaz.

    ```xml
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

1. *. Vstemplate* dosyasını kaydedin ve kapatın.

1. Şablonunuzda dosyaları seçin, seçime sağ tıklayın ve  > **Sıkıştırılmış (daraltılmış) klasöre** Gönder ' i seçin.

   Dosyalar bir *. zip* dosyasında sıkıştırılır.

1. Ayıklanan şablon dosyalarını ve eski şablon *. zip* dosyasını silin.

1. Yeni *. zip* dosyasını silinen *. zip* dosyasına sahip olan dizine yerleştirin.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Visual Studio Şablon Şeması Başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md)
- [NumberOfParentCategoriesToRollUp (Visual Studio şablonları)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)
- [Nasıl yapılır: proje şablonları oluşturma](../ide/how-to-create-project-templates.md)
- [Nasıl yapılır: öğe şablonları oluşturma](../ide/how-to-create-item-templates.md)
