---
title: Belge bağlamı | Microsoft Docs
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
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c5753e2353b351f6aa4bd73c5aced3d4959b3cde
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741185"
---
# <a name="document-context"></a>Belge Bağlamı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İçinde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] hata ayıklama, bir **belge bağlamına**:  
  
-   Kaynak dosyada bir konumu temsil eder. Burada kaynak dosyanın mevcut olmayabilir diller için tipik olarak çalışma zamanı ortamı tarafından oluşturulan bir belge bir konumda bir belge bağlamı tanımlar. Örneğin, bir komut dosyası altyapısı bir belge betikten üretebilir. Daha fazla bilgi için [belge konumu](../../extensibility/debugger/document-position.md).  
  
-   Bir konuma karşılık gelen bir kod bağlamı için bir kaynak belgedeki açıklar. Sembol işleyici belgeleri bağlam, bir derleyici veya yorumlayıcısı tarafından oluşturulan bilgileri kullanarak bir kod bağlamı eşlenir.  
  
-   Tarafından uygulanan bir [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) arabirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kod bağlamı](../../extensibility/debugger/code-context.md)   
 [Sembol sağlayıcısı](../../extensibility/debugger/symbol-provider.md)   
 [Sembol sağlayıcısı arabirimleri](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Hata Ayıklayıcı Bağlamları](../../extensibility/debugger/debugger-contexts.md)

