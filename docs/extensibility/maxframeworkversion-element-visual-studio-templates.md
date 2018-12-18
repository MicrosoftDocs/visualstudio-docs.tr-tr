---
title: MaxFrameworkVersion öğesi (Visual Studio şablonları) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 12433fd96aee78c0f8f9ead3b531ae11b1d28f17
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636366"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion öğesi (Visual Studio şablonları)

Şablon tarafından gerekli .NET Framework'ün en yüksek sürümü belirtir. Kullanılabilen en yüksek değeri belirler **hedef Framework sürümü** , açılan **yeni proje** iletişim. Kullanıcıların bir framework sürümünü seçmek için sırada de belirtmeniz gerekir [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) şablonu için en düşük .NET Framework sürümü olarak.

> [!IMPORTANT]
> Visual Studio 2017 sürüm 15.6, başlangıç **hedef Framework sürümü** açılan bir filtre görüntülenen şablonları için artık değil **şablonları** bölümünü **YeniProje** iletişim. Bunun yerine, **hedef Framework sürümü** seçilen şablonu için bir çerçeve Seçici açılan işlevlerinin.

 \<VSTemplate > \<TemplateData > \<MaxFrameworkVersion >

## <a name="syntax"></a>Sözdizimi

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırır ve ya da nasıl görüntüleneceğini tanımlar **yeni proje** veya **Yeni Öğe Ekle** iletişim kutusu.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Metin şablon tarafından izin verilen .NET Framework'ün en yüksek sürüm numarası olmalıdır.

## <a name="remarks"></a>Açıklamalar

`MaxFrameworkVersion` İsteğe bağlı bir öğedir. `MaxFrameworkVersion` Şekilde yanlışlıkla şablonu için desteklenen aralığın, .NET Framework sürümlerini sınırlama değil olarak gerekli olmadığı sürece öğesi'nin etmeyebilirsiniz. .NET Framework şablon için geçerli değilse de alınmamalıdır.

## <a name="example"></a>Örnek

Standart için meta veriler aşağıdaki örnekte [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] sınıf şablonu.

```xml
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>3.0</RequiredFrameworkVersion>
        <MaxFrameworkVersion>4.7.1</MaxFrameworkVersion>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

Bu örnekte, şablon tarafından gerekli .NET Framework'ün en yeni sürümün temsil ettiği `MaxFrameworkVersion`, 4.7.1 olduğu. Bu şablon kullanılarak oluşturulan bir proje .NET Framework sürümlerini 4.7.1 kadar hedefleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
