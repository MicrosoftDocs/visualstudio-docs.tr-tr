---
title: Hata ayıklama için dil hizmet desteği | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 59c044f6ffc3f2cdf0749f0192f4b8fa458b00cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128667"
---
# <a name="language-service-support-for-debugging"></a>Hata ayıklama için dil hizmeti desteği
Bir dil hizmeti aracılığıyla bir hata ayıklayıcı desteği özellikleri sağlayabilir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> arabirimi. Kesme noktaları doğrulama ve ifadeleri için listesini sağladığı bu özellikleri **otomobiller** penceresi.  
  
 Ancak, dilinizi hata ayıklamak için bir ifade değerlendiricisi olması gerekir. İfade değerlendirici, hata ayıklama sırasında değeri oluşturmak üzere ifadeleri değerlendirme için sorumludur. CLR ifade değerlendiricisi uygulama hakkında daha fazla bilgi için lütfen bkz.  
  
-   [CLR ifade değerlendiricisi](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Yönetilen ifade değerlendiricisi örnek](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>Derleyici çıktısı  
 Diliniz için hata ayıklama uygulamak için yapmanız gerekenler derleyici türünü belirler. Windows işletim sistemini hedefleyen ve .pdb dosyasını yazar, derleyici, Visual Studio'ya tümleşik altyapısı hata ayıklama yerel kod ile programları ayıklayabilirsiniz. Derleyici Microsoft Ara dili (MSIL) oluşturursa, Visual Studio'ya Ayrıca tümleşik altyapısı hata ayıklama yönetilen kod ile programları ayıklayabilirsiniz. Derleyici, özel bir işletim sistemi veya farklı bir çalışma zamanı ortamı hedefliyorsa, hata ayıklama altyapınız yazmanız gerekir.  
  
 Diliniz için hata ayıklama uygulama ile ilgili daha fazla bilgi için bkz: [Başlarken](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) hata ayıklama Visual Studio SDK.