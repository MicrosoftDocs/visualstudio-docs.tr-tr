---
title: Bir bağlantı noktası sağlayıcısı uygulama | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cdde98a85175692ed4717c8a9af0b26799c35214
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233041"
---
# <a name="implement-a-port-supplier"></a>Bağlantı noktası sağlayıcısı uygulama
Bağlantı noktası sağlayıcısı oturum hata ayıklama Yöneticisi (SDM) istek bağlantı noktaları sağlar. Bağlantı noktası sağlayıcısı, DCOM olmayan bir makine ya da yeni bir cihaz desteği gerektirdiğinde için hata ayıklama sırasında uygulanmalıdır. Örneğin, bir cep telefonu için hata ayıklama sağlamak için cep telefonu (belki de yoluyla veya bir hücre bağlantı IR) bağlanma ve bir telefonda çalışan programlar ve işlemleri numaralandırır bağlantı noktaları sağlayan bir bağlantı noktası sağlayıcısı ayarlayabilirsiniz.  
  
 Kendi bağlantı noktası sağlayıcısı bu durumlarda ayarlama gerekmez. Bu nedenle Windows tabanlı makineler (uzaktan hata ayıklama dahil) üzerinde hata ayıklama programları için bağlantı noktası sağlayıcıları için yerel ve ortak dil çalışma zamanı (CLR) işlemleri, Visual Studio sağlar.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [Uygulama ve bağlantı noktası sağlayıcısı kaydetme](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 SDM bağlantı noktalarını ve bağlantı noktası sağlayıcısı ile nasıl etkileşim kurduğu açıklanır.  
  
 [Gerekli bağlantı noktası sağlayıcısı arabirimleri](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Bağlantı noktası sağlayıcısı almak için uygulamanız gereken arabirimleri belgeler.  
  
## <a name="related-sections"></a>İlgili bölümler  
 [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)  
 Hata ayıklama ana mimari kavramlarını açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio hata ayıklayıcı genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md)