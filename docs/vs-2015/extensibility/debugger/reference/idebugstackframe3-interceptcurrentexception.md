---
title: IDebugStackFrame3::InterceptCurrentException | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0dde6935a343d7ba915bd7d3954c4462056be851
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781653"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Geçerli yığın çerçevesinde hata ayıklayıcı tarafından müdahale geçerli özel durumun istediğinde çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```csharp  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwFlags`  
 [in] Farklı eylemleri belirtir. Şu anda yalnızca [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) değer `IEA_INTERCEPT` desteklenir ve belirtilmesi gerekir.  
  
 `pqwCookie`  
 [out] Belirli bir özel durum tanımlayan benzersiz bir değerdir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılıysa S_OK döndürür; Aksi takdirde bir hata kodu döndürür.  
  
 En yaygın hata döndürür aşağıda verilmiştir.  
  
|Hata|Açıklama|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|Geçerli özel durumun müdahale edilebilir.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|Geçerli yürütme çerçevesi için bir işleyici henüz arandığını edilmemiş.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Bu yöntem, bu çerçeve için desteklenmiyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir özel durum oluştuğunda, hata ayıklayıcı özel durum işleme işlemi sırasında önemli noktaları çalışma zamanında denetiminden kazanır. Bu anahtar dakika hata ayıklayıcı çerçeve özel durum ıntercept isteyip istemediğini geçerli yığın çerçevesi sorabilirsiniz. Bu yığın çerçevesi (örneğin, bir try/catch bloğu program kodu içinde) özel durum işleyicisi almasa bile bu şekilde, aslında bir yığın çerçevesi için üzerinde halindeyken özel durum işleyicisi bir ilerlemesinden özel durumdur.  
  
 Hata ayıklayıcı özel durum kesildi bilmek istediğinde, geçerli yığın çerçevesi nesne üzerinde bu yöntemi çağırır. Bu yöntem, özel durumun tüm ayrıntıları işlenmesinden sorumludur. Varsa [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) arabirimi uygulanmadı veya `InterceptStackException` yöntemi herhangi bir hata döndürür ve hata ayıklayıcı özel durum normal işleme devam eder.  
  
> [!NOTE]
>  Ayıklanan programın çalışma zamanı .NET altında çalışırken özel durum diğer bir deyişle, yalnızca yönetilen kodda geçirilebilir. Elbette, üçüncü taraf dil uygulayıcılar uygulayabilirsiniz `InterceptStackException` , bu nedenle seçerseniz, kendi hata ayıklama altyapısı.  
  
 Durdurma işlemi tamamlandıktan sonra bir [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) işareti verilen.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)

