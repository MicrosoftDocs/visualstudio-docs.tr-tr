---
title: Createınplace öğesi (Visual Studio şablonları)
description: Createınplace öğesi hakkında bilgi edinin ve projenin oluşturulup oluşturulmayacağını ve belirli veya geçici bir konumda parametre değişimini gerçekleştirip gerçekleştirmeyeceğinizi nasıl belirtir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateInPlace
helpviewer_keywords:
- CreateInPlace element [Visual Studio Templates]
- <CreateInPlace> element [Visual Studio Templates]
ms.assetid: 420d46ea-2470-4da9-ad8e-95165588a920
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3da93439b245c2f8f23a8fa5b79d9fef3a48a9d2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089491"
---
# <a name="createinplace-element-visual-studio-templates"></a>Createınplace öğesi (Visual Studio şablonları)
Projenin oluşturulup oluşturulmayacağını ve belirtilen konumda parametre değişimini gerçekleştirip gerçekleştirmeyeceğinizi belirtir ya da geçici bir konumda parametre değişimini gerçekleştirin ve ardından projeyi belirtilen konuma kaydedin.

 \<VSTemplate> \<TemplateData>
 \<CreateInPlace>

## <a name="syntax"></a>Syntax

```
<CreateInPlace> true/false </CreateInPlace>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Şablonu kategorilere ayırır ve **Yeni proje** veya **Yeni öğe Ekle** iletişim kutusunda nasıl görüntülediğini tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Metin ya da olmalıdır `true` `false` . Eğer `true` , proje oluşturulur ve **Yeni proje** iletişim kutusunda belirtilen konumda parametre değişimi gerçekleştirilir. `false`Parametre değiştirme geçici bir konumda gerçekleştirilir ve proje belirtilen konuma kopyalanır.

## <a name="remarks"></a>Açıklamalar
 `CreateInPlace` isteğe bağlı bir öğedir. `true` varsayılan değerdir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir şablon için meta verileri gösterir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <CreateInPlace>false</CreateInPlace>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
