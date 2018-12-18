---
title: Kod bağlamı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 31b1f3d91fd44308c1737f8066c13af730454abe
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203351"
---
# <a name="code-context"></a>Kod bağlamı
İçinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklama, bir **kod bağlamı**:  
  
-   Hata ayıklama Altyapısı'na (DE) bilinen bir konum kod bir soyutlamasıdır sağlar. Çoğu çalışma zamanı mimarileri için bugün, bir kod bağlamı, bir programın yönerge stream'de adresi olarak düşünülebilir. Burada kod yönergeleri ile gösterilebilir değil, nontraditional diller için kod bağlamı başka bir yolla tarafından temsil edilebilir.  
  
-   Hata ayıklama programı yürütme stream'de geçerli konumu açıklar.  
  
-   Yalnızca bir programın bir kesme noktasında ne zaman durdurdu var.  
  
-   İlişkili belge içeriğine sahiptir.  
  
-   Tarafından uygulanan bir [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) arabirimi.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Belge bağlamı](../../extensibility/debugger/document-context.md)   
 [Hata ayıklayıcı bağlamları](../../extensibility/debugger/debugger-contexts.md)