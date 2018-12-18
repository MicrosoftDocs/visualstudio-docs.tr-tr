---
title: Visual Studio şablon bulma sorunlarını giderme | Microsoft Docs
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-sdk
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d183fd664258fbb7dbcf27c913c56c6f6160e6c4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136734"
---
# <a name="troubleshooting-template-installation"></a>Şablon yükleme sorunlarını giderme

Proje veya öğe şablonları dağıtma sorunlarla karşılaşırsanız, tanılama günlük kaydını etkinleştirebilirsiniz.

1. (Örneğin C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) yüklemeniz için bir pkgdef dosyası Common7\IDE\CommonExtensions klasöründe aşağıdaki içeriğe sahip oluşturun:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

1. Windows aramasında arayarak yüklemenizin "Geliştirici komut istemi" açın ve çalıştırın `devenv /updateConfiguration`.

1. Visual Studio'yu başlatın ve her iki şablon ağaçları başlatmak için yeni proje ve yeni öğe iletişim kutuları başlatın. Şablon günlük görüntülenir **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (Visual Studio örneğiniz yükleme Kimliğini InstanceId karşılık gelir). Her şablon ağaç başlatma için bu günlük girdileri ekler.

Günlük dosyası şu sütunları içerir:

- **FullPathToTemplate**, aşağıdaki değerleri vardır:

    - bildirim tabanlı bir dağıtım için 1

    - disk tabanlı bir dağıtım için 0

- **TemplateFileName**

- Diğer şablonu özellikleri

> [!NOTE]
> Günlüğünü devre dışı bırakma pkgdef dosyayı kaldırın veya değerini değiştirmek `EnableTemplateDiscoveryLog` için `dword:00000000`ve ardından çalıştırın `devenv /updateConfiguration` yeniden.

## <a name="see-also"></a>Ayrıca bkz.

[Özel proje ve öğe şablonları oluşturma](creating-custom-project-and-item-templates.md)