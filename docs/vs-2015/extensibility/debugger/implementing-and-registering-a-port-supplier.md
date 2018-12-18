---
title: Uygulama ve bağlantı noktası sağlayıcısı kaydetme | Microsoft Docs
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
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3844d6beca76781f741bfbe0c6bff71923075d36
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728938"
---
# <a name="implementing-and-registering-a-port-supplier"></a>Bağlantı Noktası Sağlayıcısı Uygulama ve Kaydetme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bağlantı noktası sağlayıcısı izlemek ve sırayla işlemlerini yönetmek bağlantı noktaları sağlamanız için rolüdür. Zaman bir bağlantı noktası oluşturulması gerekir, bağlantı noktası sağlayıcısı (oturum hata ayıklama Yöneticisi [SDM] bağlantı noktası sağlayıcısı seçtiğiniz kullanıcı veya proje sistemi tarafından belirtilen bağlantı noktası sağlayıcısı kullanırsınız) bağlantı noktası tedarikçi GUID'e sahip CoCreate kullanılarak başlatılır. SDM ardından çağıracak [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) tüm bağlantı noktaları eklenip eklenemeyeceğini görmek için. Bir bağlantı noktası eklenebilir, yeni bir bağlantı noktası çağırarak istenen [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) ve geçirerek bir [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) , bağlantı noktası açıklar. `AddPort` tarafından temsil edilen yeni bir bağlantı noktası döndüreceği bir [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) arabirimi.  
  
## <a name="discussion"></a>Tartışma  
 Bir bağlantı noktası, bir makine ya da hata ayıklama sunucusuyla ilişkilendirilmiş bağlantı noktası sağlayıcısı tarafından oluşturulur. Bir sunucu bağlantı noktası tedarikçileri aracılığıyla numaralandırabilirsiniz[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) yöntemi ve bağlantı noktası sağlayıcısı aracılığıyla bağlantı noktalarını listeleme [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) yöntemi.  
  
 Tipik COM kayıt ek olarak, bağlantı noktası sağlayıcısı kendisi ile Visual Studio ad ve CLSID belirli kayıt defteri konumlara yerleştirerek kaydetmeniz gerekir. Hata ayıklama SDK'sı yardımcı işlevini çağırdı `SetMetric` bu işleme:, bu nedenle kaydedilecek her öğe için bir kez çağrılır:  
  
```cpp#  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricCLSID,  
          <CLSID of your port supplier>,  
          false,  
          NULL)  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricName,  
          <name of your port supplier>,  
          false,  
          NULL);  
```  
  
 Bağlantı noktası sağlayıcısı kendisini çağırarak kaydını siler `RemoveMetric` (başka bir hata ayıklama SDK'sı yardımcı işlevini), bu nedenle kaydedilen her öğe için bir kez:  
  
```cpp#  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricCLSID,  
             NULL);  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricName,  
             NULL);  
```  
  
> [!NOTE]
>  [Hata ayıklama için SDK Yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` ve `RemoveMetric` dbgmetric.h içinde tanımlanan ve ad2de.lib derlenmiş statik işlev. `metrictypePortSupplier`, `metricCLSID`, Ve `metricName` Yardımcıları de dbgmetric.h içinde tanımlanır.  
  
 Bağlantı noktası sağlayıcısı yöntemlerle GUID ve ad sağlayabilirsiniz [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) ve [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)sırasıyla.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir bağlantı noktası sağlayıcısı uygulama](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Hata ayıklama için SDK Yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Bağlantı Noktası Sağlayıcıları](../../extensibility/debugger/port-suppliers.md)

