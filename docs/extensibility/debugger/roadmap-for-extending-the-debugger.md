---
title: Hata ayıklayıcıyı genişletmek için yol haritası | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7527d142b27e5b49bcf133429dc232614bad04a2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942680"
---
# <a name="roadmap-for-extending-the-debugger"></a>Hata ayıklayıcıyı genişletmek için yol haritası
Bu belgeler genişletmeye yönelik kılavuz ve başvuru bilgileri sağlar [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] ile hata ayıklayıcı [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] belgeleri hata ayıklama, örnekler, kapsamlı bir referans ve tipik Hata Ayıklayıcısı'nı özelleştirme yolları gösteren birkaç temsili senaryo içerir.  
  
 Derleyici ve çıktısını ne ürününüzü hata ayıklamayı kurma için gerekli olan belirleyin. Varsa, derleyici:  
  
- Windows yerel işletim sistemini hedefleyen ve yazan bir *. PDB* dosyası içinde tümleşik olarak yerel kod hata ayıklama altyapısı (DE) ile programlar ayıklayabilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Bir DE ya da ifade değerlendiricisi uygulama gerekmez. İfade değerlendirici, C++ programlama dilinin sözdizimi yazılır.  
  
- Microsoft Ara dili (MSIL) çıktı, içine tümleştirilmiştir yönetilen kod hata ayıklama altyapısıyla DE, programların ayıklayabilir üretir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Bu nedenle, yalnızca bir ifade değerlendiricisi uygulama. Örnek ifade değerlendiricisi sağlanır. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
   [İfade değerlendirme](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
   [İfadeleri değerlendirme](../../extensibility/debugger/evaluating-expressions.md)  
  
   [İfade değerlendirme bağlamı](../../extensibility/debugger/expression-evaluation-context.md)  
  
   [Kesme modunda ifade değerlendirme](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
   [Bir ortak dil çalışma zamanı ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- Bir işletim sistemi veya başka bir çalışma zamanı ortamında özel hedefler, kendi DE yazmanız gerekir. ATL COM kullanarak basit bir DE oluşturan bir Öğreticisi sağlanır. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
   [Bir özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
   [Öğretici: Bir hata ayıklama altyapısı ATL COM kullanarak derleme](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
   [Bağlantı noktası sağlayıcısı uygulama](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
   [Örnekler](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kullanmaya başlama](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)