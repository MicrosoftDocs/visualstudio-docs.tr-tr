---
title: Deneysel örneği | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c80c071866e46528fe7edd287e082df3af166973
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138931"
---
# <a name="the-experimental-instance"></a>Deneysel örneği
Visual Studio geliştirme ortamınızı değişiklik yapmış olabilir sınanmamış uygulamalardan korumak için VSSDK denemek için kullanabileceğiniz Deneysel bir alan sağlar. Visual Studio her zamanki gibi kullanarak yeni uygulamaları geliştirmek, ancak bunları bu deneysel örneği kullanarak çalıştırın.  
  
 VSIX paketi olan her uygulama hata ayıklama modunda Visual Studio deneysel örneği başlatır.  
  
 Visual Studio Deneysel örnek bir çözüm dışında başlatmak istiyorsanız, komut penceresinde aşağıdaki komutu çalıştırın:  
  
 "*\<Visual studio yükleme yolu >* \Common7\IDE\devenv.exe" RootSuffix Exp  
  
> [!NOTE]
>  Deneysel örneği altında kayıt defterine yazılır `<version number>Exp` ve `<version number>Exp_Config` düğümleri. Örneğin Visual Studio 2015 Deneysel kayıt defteri alanıdır  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` Ve `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Bunu geliştirirken uzantınızı deneysel örneğinde çalıştırmanızı öneririz. Uzantı dağıttığınızda, geliştirme örneğinde çalışır. Uygulamaları kaydetme hakkında daha fazla bilgi için bkz: [kaydetme VSPackages](../extensibility/internals/registering-vspackages.md).