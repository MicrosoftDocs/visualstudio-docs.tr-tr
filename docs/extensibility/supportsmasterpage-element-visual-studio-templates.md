---
title: SupportsMasterPage öğesi (Visual Studio şablonları) | Microsoft Docs
description: SupportsMasterPage öğesi hakkında bilgi edinin ve yeni öğe Ekle iletişim kutusunda ana sayfa seç onay kutusunun etkin olup olmadığını belirtir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsMasterPage
helpviewer_keywords:
- <SupportsMasterPage> element [Visual Studio Templates]
- SupportsMasterPage element [Visual Studio Templates]
ms.assetid: ce877a6a-9bba-4fd9-92fb-0a8dfec9e75b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c3b779b3626c4ff47fe798fa9f4ff2e7bc9c7ac8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056044"
---
# <a name="supportsmasterpage-element-visual-studio-templates"></a>SupportsMasterPage Öğesi (Visual Studio Şablonları)
**Yeni öğe Ekle** Iletişim kutusunda **Ana sayfa seç** onay kutusunun etkin olup olmadığını belirtir.

 \<VSTemplate> \<TemplateData>
 \<SupportsMasterPage>

## <a name="syntax"></a>Syntax

```
<SupportsMasterPage> true/false </SupportsMasterPage>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt Öğeler
 Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Şablonu kategorilere ayırır ve **Yeni proje** veya **Yeni öğe** iletişim kutusunda nasıl görüntülediğini tanımlar.|

## <a name="text-value"></a>Metin Değeri
 Bir metin değeri gereklidir.

 Metin ya da ya da `true` `false` **Yeni öğe Ekle** Iletişim kutusunda **Ana sayfa seç** onay kutusunun etkin olup olmadığını gösteren bir değer olmalıdır.

## <a name="remarks"></a>Açıklamalar
 `SupportsMasterPage` isteğe bağlı bir öğedir. `false` varsayılan değerdir.

 `SupportsMasterPage`Öğesi yalnızca Web öğesi şablonları için kullanılabilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir ana sayfa için destek içeren bir Web projesinin meta verilerini gösterir.

```
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsMasterPage>true</SupportsMasterPage>
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
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
