---
title: IDebugEngine2::CauseBreak | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 08544fb80e1006dbed08e51689c1bb3b01212edb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820518"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Tüm programları bu hata ayıklama altyapısı yürütme sonraki durdurmak için (DE) hata ayıklaması yapılan istekleri, iş parçacıkları birini çalıştırmayı dener.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CauseBreak(   
   void   
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa döndürür `S_OK`; Aksi takdirde bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu zaman uyumsuz bir yöntemdir: bir [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) program bu yöntem çağrıldıktan sonra yürütülecek sonraki denediğinde olay gönderilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)