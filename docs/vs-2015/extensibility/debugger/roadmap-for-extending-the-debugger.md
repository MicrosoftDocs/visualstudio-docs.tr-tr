---
title: Hata ayıklayıcıyı genişletmek için yol haritası | Microsoft Docs
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
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 806a5ebb4bf27f4d46bbe5b81a5dba6b319ee02e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816690"
---
# <a name="roadmap-for-extending-the-debugger"></a>Hata Ayıklayıcıyı Genişletmek için Yol Haritası
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu belgeler genişletmeye yönelik kılavuz ve başvuru bilgileri sağlar [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] ile hata ayıklayıcı [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] belgeleri hata ayıklama, örnekler, kapsamlı bir referans ve tipik Hata Ayıklayıcısı'nı özelleştirme yolları gösteren birkaç temsili senaryo içerir.  
  
 Derleyici ve çıktısını ürününüzü hata ayıklama uygulamak için yapılması gerekenleri belirleyin. Varsa, derleyici:  
  
-   Windows yerel işletim sistemini hedefleyen ve yazan bir. PDB dosyası içinde tümleşik olarak yerel kod hata ayıklama altyapısı (DE) ile programlar ayıklayabilir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Bir DE ya da ifade değerlendiricisi uygulama gerekmez. İfade değerlendirici, C++ programlama dilinin sözdizimi yazılır.  
  
-   Microsoft Ara dili (MSIL) çıktı, içine tümleştirilmiştir yönetilen kod hata ayıklama altyapısıyla DE, programların ayıklayabilir üretir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Bu nedenle, yalnızca bir ifade değerlendiricisi uygulama. Örnek ifade değerlendiricisi sağlanır. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
     [İfade Değerlendirme](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [İfadeleri Değerlendirme](../../extensibility/debugger/evaluating-expressions.md)  
  
     [İfade Değerlendirme Bağlamı](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Kesme Modunda İfade Değerlendirme](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Ortak Dil Çalışma Zamanı İfade Değerlendiricisi Yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   Bir işletim sistemi veya başka bir çalışma zamanı ortamında özel hedefler, kendi DE yazmanız gerekir. ATL COM kullanarak basit bir DE oluşturan bir Öğreticisi sağlanır. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
     [Özel Hata Ayıklama Altyapısı Oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Öğretici: ATL COM kullanarak bir hata ayıklama altyapısı oluşturma](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Bağlantı Noktası Sağlayıcısı Uygulama](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Örnekler](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)

