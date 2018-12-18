---
title: IDebugApplication::HandleRuntimeError | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleRuntimeError
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleRuntimeError
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eead4780ff061ff9c7280aeee0936c8f64741981
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793892"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Engellemek geçerli iş parçacığının neden olur ve IDE hata ayıklayıcısı hata bir bildirim gönderir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pErrorDebug`  
 [in] Gerçekleşen hata.  
  
 `pScriptSite`  
 [in] İş parçacığı betik sitesi.  
  
 `pbra`  
 [out] Hata ayıklayıcı uygulama çıktığında yapılacak eylem.  
  
 `perra`  
 [out] Bir hata varsa hata ayıklayıcı uygulama çıktığında yapılacak eylem.  
  
 `pfCallOnScriptError`  
 [out] Olan bayrağı `TRUE` altyapısı çağırmalıdır varsa `IActiveScriptSite::OnScriptError` yöntemi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem bir `HRESULT`. Olası değerler aşağıdaki tablodakileri içerir, ancak bunlarla da sınırlı değildir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`S_OK`|Yöntem başarılı oldu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir dil alt yapısı bir çalışma zamanı hatası neden olan bir iş parçacığı bağlamında bu yöntemi çağırır. Bu yöntem engellemek geçerli iş parçacığının neden olur ve hata ayıklayıcı IDE gönderilmek üzere bir hata bildirimi gönderir. Hata ayıklayıcı IDE uygulama devam ettiğinde, bu yöntem gerçekleştirilecek eylemin döndürür.  
  
> [!NOTE]
>  Çalışma zamanı hatası içinde dil altyapısı yığın çerçeveleri listeleme veya ifadeleri değerlendirme gibi görevleri yapmak için iş parçacığı tarafından çağrılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugapplication arabirimi](../../winscript/reference/idebugapplication-interface.md)   
 [Iactivescripterrordebug arabirimi](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [Iactivescriptsite](../../winscript/reference/iactivescriptsite.md)   
 [BREAKRESUMEACTION numaralandırması](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION numaralandırması](../../winscript/reference/errorresumeaction-enumeration.md)