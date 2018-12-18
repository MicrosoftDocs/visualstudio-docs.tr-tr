---
title: IDebugCoreServer3::CreateInstanceInServer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 171eda8b7c1b206ea54839366686ad43f690afe0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886480"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Sunucuda bir hata ayıklama altyapısı örneğini oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```csharp  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `szDll`  
 [in] Belirtilen CLSID uygulayan dll yolu `clsidObject` parametresi. Bu ise `NULL`, ardından COM's `CoCreateInstance` işlevi çağrılır.  
  
 `wLangId`  
 [in] Yerel hata ayıklama altyapısı. Bu 0 olabilir [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) yöntemi çağırılmalıdır.  
  
 `clsidObject`  
 [in] Oluşturmak için CLSID hata ayıklama altyapısı.  
  
 `riid`  
 [in] Sınıf nesneyi almak için belirli arabirimi arabirim kimliği.  
  
 `ppvObject`  
 [out] `IUnknown` arabiriminden oluşturulan nesne. Cast veya istenen arabirim için bu nesnesi hazırlanamadı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa döndürür `S_OK`; Aksi takdirde bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)