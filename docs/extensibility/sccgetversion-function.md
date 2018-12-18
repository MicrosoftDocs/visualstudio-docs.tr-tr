---
title: SccGetVersion işlevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 70beb89f13d2f752f3adb0f25e2b370fa272171a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136451"
---
# <a name="sccgetversion-function"></a>SccGetVersion işlevi
Bu işlev, kaynak denetim eklentisi kaynak denetimi eklentisi tarafından desteklenen API sürümü sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Parametreler  
 Yok.  
  
## <a name="return-value"></a>Dönüş Değeri  
 A `LONG` desteklenen kaynak denetim eklentisi API'si sürüm numarasını içeren veri türü:  
  
|WORD|Açıklama|  
|----------|-----------------|  
|HIWORD|Ana sürüm|  
|LOWORD|Alt sürümü|  
  
## <a name="remarks"></a>Açıklamalar  
 Örneğin, kaynak denetim eklentisi sürüm 1.3 kaynak denetim eklentisi API destekliyorsa, bu işlev 0x0103 döndürecektir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)