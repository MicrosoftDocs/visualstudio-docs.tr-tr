---
title: Proje öğesine öznitelik ekleme | Microsoft Docs
description: Visual Studio 'daki bir proje öğesine bir özniteliği ekleme hakkında bilgi edinmek için bkz. Gettitemattribute ve SetItemAttribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 36fc5905fd2b1423865982a80a6cb2ba6a803cc5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902026"
---
# <a name="add-an-attribute-to-a-project-item"></a>Proje öğesine öznitelik ekleme
Yöntemler <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> bir proje öğesinin özniteliklerinin değerini alır ve ayarlar. SetItemAttribute, zaten mevcut değilse özniteliği oluşturur ve proje öğesi meta verilerine ekler.

## <a name="add-an-attribute-to-a-project-item"></a>Proje öğesine öznitelik ekleme

- Aşağıdaki kod, <xref:EnvDTE.DTE> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> bir proje öğesine öznitelik eklemek için Automation nesnesini ve yöntemini kullanır. Proje öğesi KIMLIĞI, "program. cs" proje öğesi adından elde edilir. "MyAttribute" özniteliği bu proje öğesine eklenir ve "MyValue" değeri verilir.

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "MyAttribute", "MyValue");
    }

    ```

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild proje dosyasında verileri kalıcı hale getirme](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
