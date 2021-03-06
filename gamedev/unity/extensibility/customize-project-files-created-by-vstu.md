---
title: VSTU tarafından oluşturulan proje dosyalarını özelleştirme | Microsoft Docs
description: Unity için Visual Studio Araçları (VSTU) tarafından oluşturulan proje dosyalarını özelleştirmeyi öğrenin. Bir C# kod örneğini inceleyin.
ms.custom: ''
ms.date: 04/19/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: a4a5973863877db2d071f9be8d4689928b21a689
ms.sourcegitcommit: 3e1ff87fba290f9e60fb4049d011bb8661255d58
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2021
ms.locfileid: "107879323"
---
# <a name="customize-project-files-created-by-vstu"></a>VSTU tarafından oluşturulan proje dosyalarını özelleştirme
Unity, proje dosyası oluşturma sırasında geri çağrılar sağlar. Öğesini `OnGeneratedSlnSolution` `OnGeneratedCSProject` kullanarak, [`AssetPostprocessor`](https://docs.unity3d.com/ScriptReference/AssetPostprocessor.html) Proje veya çözüm dosyasını her yeniden oluşturulduğunda değiştirmek için kullanın.

## <a name="demonstrates"></a>Gösteriler
Unity için Visual Studio Araçları tarafından oluşturulan Visual Studio proje dosyalarını özelleştirme.

## <a name="example"></a>Örnek

```csharp
using System;
using UnityEditor;
using UnityEngine;

public class ProjectFilePostprocessor : AssetPostprocessor
{
  public static string OnGeneratedSlnSolution(string path, string content)
  {
    // TODO: process solution content
    return content;
  }

  public static string OnGeneratedCSProject(string path, string content)
  {
    // TODO: process project content
    return content;
  }
}
```
