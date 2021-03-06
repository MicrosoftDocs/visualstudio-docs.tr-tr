---
title: Deneysel örnek | Microsoft Docs
description: Visual Studio SDK 'nın test edilmemiş uygulamaları hata ayıklama modunda çalıştırmak için deneysel alan nasıl sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: aefac4efc706d195d8471952da3914d35d27ddc2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055888"
---
# <a name="the-experimental-instance"></a>Deneysel Örnek
Visual Studio geliştirme ortamınızı, onu değiştirebilen test edilmemiş uygulamalardan korumak için, VSSDK, denemek için kullanabileceğiniz bir deneysel alan sağlar. Visual Studio 'Yu her zamanki gibi kullanarak yeni uygulamalar geliştirirsiniz, ancak bunları bu deneysel örneği kullanarak çalıştırırsınız.

 VSıX paketi olan her uygulama, hata ayıklama modunda Visual Studio Deneysel örneğini başlatır.

 Visual Studio 'nun Deneysel örneğini belirli bir çözüm dışında başlatmak istiyorsanız, komut penceresinde aşağıdaki komutu çalıştırın:

 " *\<Visual studio installation path>* \Common7\IDE\devenv.exe"/rootsuffix exp

> [!NOTE]
> Deneysel örnek, ve düğümleri altında kayıt defterine yazılır `<version number>Exp` `<version number>Exp_Config` . Örneğin, Visual Studio 2015 Deneysel kayıt defteri alanı
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` ve `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Genişletirken, uzantınızı deneysel örnekte çalıştırmanızı öneririz. Uzantıyı dağıttığınızda, geliştirme örneğinde çalışır. Uygulamaları kaydetme hakkında daha fazla bilgi için bkz. [VSPackages kaydetme](../extensibility/internals/registering-vspackages.md).
