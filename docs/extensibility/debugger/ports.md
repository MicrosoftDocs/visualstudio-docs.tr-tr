---
title: Bağlantı noktaları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f54ec931bc34f854d1c9f1a85961f5af65a56264
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49936348"
---
# <a name="ports"></a>Bağlantı Noktaları
Hata ayıklayıcı mimarisinde bir *bağlantı noktası*:  
  
- Bir dizi işlemleri için bir kapsayıcı, bir sunucu üzerinde çalışıyor. Örneğin, bir bağlantı noktası seri kablo Windows CE tabanlı bir cihaz için veya ağa bağlı DCOM olmayan bir makineye bağlantı temsil edebilir. Yerel bağlantı noktası adı verilen bir özel bağlantı noktası, yerel makine üzerinde çalışan tüm işlemler içeriyor.  
  
- Kendi adına veya tanımlayıcısına göre belirleyebilirsiniz.  
  
- Bağlantı noktası üzerinde çalışan tüm işlemler listeleme ve başlatabileceğini ve bu işlemleri sonlandırın.  
  
- Tarafından temsil edilen bir [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) geçirerek oluşturulduğu arabirimi bir [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) bağımsız değişkeni [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tüm Windows tabanlı işlemler, yerel ve yönetilen işleyen varsayılan bağlantı noktası sağlar. Özel bir bağlantı noktası bağlantılar için Windows tabanlı olmayan dış cihazlarla ayarlanmalıdır. Bu tür özel bağlantı noktaları sağlamanız gerekiyorsa, özel bağlantı noktası sağlayıcısı ayarlamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Sunucuları](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [İşlemler](../../extensibility/debugger/processes.md)   
 [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)