---
title: ImportGroup öğesi | Microsoft Docs
description: MSBuild 'in, isteğe bağlı bir koşul altında gruplanmış bir Içeri aktarma öğeleri koleksiyonu içermesi için ImportGroup öğesini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ImportGroup> element [MSBuild]
- ImportGroup element [MSBuild]
ms.assetid: dac3fa2d-6678-4017-af35-93686f53f302
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2e5ece72d83dd530a855d583ce061a22554d45a5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914089"
---
# <a name="importgroup-element"></a>ImportGroup öğesi

  
`Import`İsteğe bağlı bir koşul altında gruplandırılan öğelerin bir koleksiyonunu içerir. Daha fazla bilgi için bkz. [Import element (MSBuild)](../msbuild/import-element-msbuild.md).

```xml
<Project>
  <ImportGroup>
```

## <a name="syntax"></a>Syntax

```xml
<ImportGroup Condition="'String A' == 'String B'">
    <Import ... />
    <Import ... />
</ImportGroup>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[İçeri Aktarma](../msbuild/import-element-msbuild.md)|Bir proje dosyasının içeriğini başka bir proje dosyasına aktarır.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | MSBuild proje dosyasının gerekli kök öğesi. |

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği `ImportGroup` öğesini gösterir.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ImportGroup>
        <Import Project="$(Targets1.targets)" />
        <Import Project="$(Targets2.targets)" />
    </ImportGroup>
...
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [Öğeler](../msbuild/msbuild-items.md)
