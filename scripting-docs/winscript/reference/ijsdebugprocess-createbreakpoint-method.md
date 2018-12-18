---
title: Ijsdebugprocess::createbreakpoint yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateBreakPoint
apilocation:
- jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10d734f32d092d341dbb1b02a5cc7a0c127223a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794591"
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>IJsDebugProcess::CreateBreakPoint Yöntemi
Kesme noktası belirtilen belge konumuna ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `documentId`  
 [in] Idebugdocumenttext işaretçi.  
  
 `characterOffset`  
 [in] Dosya başına karakter uzaklığı.  
  
 `characterCount`  
 [in] Kesme noktası içinde ekleneceği belge metnin uzunluğu.  
  
 `isEnabled`  
 [in] Kesme noktası etkinleştirilip etkinleştirilmeyeceğini belirtir.  
  
 `ppDebugBreakPoint`  
 [out] Oluşturulan kesme noktası temsil eden nesne.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** jscript9diag.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ijsdebugprocess arabirimi](../../winscript/reference/ijsdebugprocess-interface.md)