---
title: Uygulama ve bağlantı noktası sağlayıcısı kaydetme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 10e68f06cde3cd562b145bd64f94581c65f7d7f6
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231652"
---
# <a name="implement-and-register-a-port-supplier"></a>Uygulama ve bağlantı noktası sağlayıcısı kaydetme
Bağlantı noktası sağlayıcısı izlemek ve sırayla işlemlerini yönetmek bağlantı noktaları sağlamanız için rolüdür. Bir bağlantı noktası oluşturulması gerektiğinde, bağlantı noktası sağlayıcısı (oturum hata ayıklama Yöneticisi [SDM] proje sistemi tarafından seçilen kullanıcıya veya bağlantı noktası sağlayıcısı belirtilen bağlantı noktası sağlayıcısı kullanırsınız) bağlantı noktası tedarikçi GUID'e sahip CoCreate kullanılarak başlatılır. SDM sonra çağıran [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) tüm bağlantı noktaları eklenip eklenemeyeceğini görmek için. Bir bağlantı noktası eklenebilir, yeni bir bağlantı noktası çağırarak istenen [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) ve geçirerek bir [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) , bağlantı noktası açıklar. `AddPort` tarafından temsil edilen yeni bir bağlantı noktası döndüren bir [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) arabirimi.  
  
## <a name="discussion"></a>Tartışma  
 Bir bağlantı noktası, bir makine ya da hata ayıklama sunucusuyla ilişkilendirilmiş bağlantı noktası sağlayıcısı tarafından oluşturulur. Bir sunucu bağlantı noktası tedarikçileri aracılığıyla numaralandırır[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) yöntemi ve bağlantı noktası sağlayıcısı aracılığıyla bağlantı noktalarını numaralandırır [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) yöntemi.  
  
 Tipik COM kayıt ek olarak, bağlantı noktası sağlayıcısı kendisi ile Visual Studio ad ve CLSID belirli kayıt defteri konumlara yerleştirerek kaydetmeniz gerekir. Hata ayıklama SDK'sı yardımcı işlevini çağırdı `SetMetric` bu işleme:, bu nedenle kaydedilecek her öğe için bir kez çağrılır:  
  
```cpp  
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
  
```cpp  
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
>  [Hata ayıklama için SDK Yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` ve `RemoveMetric` statik işlevler tanımlanan *dbgmetric.h* ve içine derlenmiş *ad2de.lib*. `metrictypePortSupplier`, `metricCLSID`, Ve `metricName` Yardımcıları tanımlanmış ayrıca *dbgmetric.h*.  
  
 Bağlantı noktası sağlayıcısı yöntemlerle GUID ve ad sağlayabilirsiniz [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) ve [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)sırasıyla.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Bağlantı noktası sağlayıcısı uygulama](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Hata ayıklama için SDK Yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Bağlantı noktası sağlayıcıları](../../extensibility/debugger/port-suppliers.md)