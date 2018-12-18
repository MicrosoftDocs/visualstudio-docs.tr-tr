---
title: Deneysel örneği | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b529ba3a0ea8b38a27d06e03ce15106cbd7512a5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787997"
---
# <a name="the-experimental-instance"></a>Deneysel Örnek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio geliştirme ortamınızı değişiklik yapmış olabilir, test edilmemiş uygulamalardan korumak için VSSDK denemek için kullanabileceğiniz bir Deneysel alanı sağlar. Visual Studio zamanki kullanarak yeni uygulamalar geliştirin, ancak bunları bu deneysel örneği kullanarak çalıştırın.  
  
 Bir VSIX paketi olan her bir uygulama, hata ayıklama modunda Visual Studio deneysel örneği başlatır.  
  
 Visual Studio'nun deneysel örneğinde belirli bir çözüm dışında başlatmak istiyorsanız, komut penceresinde aşağıdaki komutu çalıştırın:  
  
 "*\<Visual studio yükleme yolu >* \Common7\IDE\devenv.exe" RootSuffix üs  
  
> [!NOTE]
>  Deneysel örneği altındaki kayıt defterine yazılır `<version number>Exp` ve `<version number>Exp_Config` düğümleri. Örneğin Visual Studio 2015 Deneysel kayıt defteri alandır  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` ve `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Bunu geliştirirken deneysel örneğinde uzantınızı çalıştırmanızı öneririz. Uzantı dağıttığınızda, geliştirme örneğinde çalışır. Uygulamaları kaydetme hakkında daha fazla bilgi için bkz. [VSPackage kaydetme](../extensibility/internals/registering-vspackages.md).

