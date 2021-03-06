---
title: Çalışma zamanında bir projenin alt türlerini doğrulama | Microsoft Docs
description: VSPackage 'ın bağımlı olduğu belirtilen özel proje alt türünün varlığını nasıl doğrulayacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 621a40e1857d7c78ec4c5be08a3b7c3808a0d48b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905479"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Çalışma zamanında bir projenin alt türlerini doğrulama
Özel bir proje alt türüne bağımlı olan VSPackage, alt tür yoksa düzgün bir şekilde başarısız olması için o alt türü aramak için mantık içermelidir. Aşağıdaki yordamda, belirtilen bir alt tür varlığının nasıl doğrulanyapılacağı gösterilmektedir.

### <a name="to-verify-the-presence-of-a-subtype"></a>Bir alt tür varlığını doğrulamak için

1. VSPackage 'a aşağıdaki kodu ekleyerek proje ve çözüm nesnelerinden proje hiyerarşisini bir nesne olarak alın <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> .

    ```csharp
    EnvDTE.DTE dte;
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));

    EnvDTE.Project project;
    project = dte.Solution.Projects.Item(1);

    IVsSolution solution;
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));

    IVsHierarchy hierarchy;
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);

    ```

2. Hiyerarşiyi <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> arabirime atayın.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Öğesini çağırarak proje türü GUID 'Lerinin listesini alın <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A> .

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. Belirtilen alt tür için GUID listesini denetleyin.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>Ayrıca bkz.
- [Proje alt türleri](../extensibility/internals/project-subtypes.md)
- [Proje alt türleri tasarımı](../extensibility/internals/project-subtypes-design.md)
- [Proje alt türleri tarafından genişletilen Özellikler ve Yöntemler](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
