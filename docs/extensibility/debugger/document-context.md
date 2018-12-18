---
title: Belge bağlamı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ef82c6533eddf32dd8315193531a57e2e7328ad9
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203566"
---
# <a name="document-context"></a>Belge bağlamı
İçinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklama, bir *belge bağlamına*:  
  
-   Kaynak dosyada bir konumu temsil eder. Burada kaynak dosyanın mevcut olmayabilir diller için tipik olarak çalışma zamanı ortamı tarafından oluşturulan bir belge bir konumda bir belge bağlamı tanımlar. Örneğin, bir komut dosyası altyapısı bir belge betikten üretebilir. Daha fazla bilgi için [belge konumu](../../extensibility/debugger/document-position.md).  
  
-   Bir konuma karşılık gelen bir kod bağlamı için bir kaynak belgedeki açıklar. Sembol işleyici belgeleri bağlam, bir derleyici veya yorumlayıcısı tarafından oluşturulan bilgileri kullanarak bir kod bağlamı eşlenir.  
  
-   Tarafından uygulanan bir [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) arabirimi.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kod bağlamı](../../extensibility/debugger/code-context.md)   
 [Sembol sağlayıcısı](../../extensibility/debugger/symbol-provider.md)   
 [Sembol sağlayıcısı arabirimleri](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Hata ayıklayıcı bağlamları](../../extensibility/debugger/debugger-contexts.md)