---
title: EndTrackingContext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f3506e87c1468ff66143b672dca95cd70b0b3dff
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39177415"
---
# <a name="endtrackingcontext"></a>EndTrackingContext
Son geçerli izleme bağlamı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT WINAPI EndTrackingContext();  
```  
  
## <a name="return-value"></a>Dönüş değeri  
 Bir **HRESULT** ile **başarılı** izleme bağlamına sona erdi, biti ayarlanmamış.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** *FileTracker.h*  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)