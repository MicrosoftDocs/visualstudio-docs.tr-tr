---
title: Web şablonları oluşturma
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: cff4fda5113cdbacba2d9389e360707f49ba595b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063674"
---
# <a name="how-to-manually-create-web-templates"></a>Nasıl yapılır: web şablonlarını elle oluşturma

Bir web şablonu oluşturma, diğer türlerdeki şablonları oluşturmaktan daha farklıdır. Web projesi şablonları görünür çünkü **yeni Web sitesi Ekle** iletişim kutusu ve web projesi öğeleri programlama dili tarafından kategorilere *vstemplate* dosya şablonu bir web şablonu belirtmeniz gerekir ve programlama dilini tanımlar.

> [!NOTE]
> Web şablonları, boş bir içermelidir *.webproj* içindeki dosya ve başvurulmalıdır *vstemplate* dosyası `File` özniteliği `Project` öğesi. Web projeleri gerektirmez, ancak bir *.proj* proje dosyası, bu düzgün çalışması web şablonu için bu saplama dosyası oluşturmak için gerekli.

## <a name="to-manually-create-a-web-template"></a>El ile bir web şablonu oluşturmak için

1. Web projesi oluşturun.

2. Değiştirme veya proje dosyaları silin veya yeni dosyalar projeye ekleyin.

3. Bir XML dosyası oluşturun ve ile kaydetmek bir *vstemplate* projeniz gibi aynı dizinde dosya adı uzantısı. Visual Studio'da projeye eklemeyin.

4. Düzen *vstemplate* proje şablon meta verilerini sağlamak için XML dosyası. Daha fazla bilgi için [örnekte](#example).

5. Bulun `ProjectType` öğesinde *vstemplate* dosya ve metin değerine `Web`.

6. Aşağıdaki `ProjectType` öğe, Ekle bir `ProjectSubType` öğesi ve metin şablonunun programlama dili değeri ayarlayın. Programlama dili, aşağıdaki değerlerden biri olabilir:

   - CSharp
   - VisualBasic

     Örneğin:

     ```xml
     <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
     </TemplateData>
     ```

7. Şablonunuzda dosyaları seçin (Bu içerir *vstemplate* dosyası), seçime sağ tıklayın ve seçme **göndermek** > **sıkıştırılmış (daraltılmış) klasör**. Dosyalar sıkıştırılmadan bir *.zip* dosya.

8. PUT *.zip* Visual Studio Proje şablonu dizininde şablon dosyası. Varsayılan olarak, bu dizindir *%USERPROFILE%\Documents\Visual Studio \<sürüm\>\ProjectTemplates*.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir temel gösterir *vstemplate* dosyası için bir web projesi şablonu:

```xml
<VSTemplate Version="2.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Visual Studio Şablon Şeması Başvurusu (genişletilebilirlik)](../extensibility/visual-studio-template-schema-reference.md)
