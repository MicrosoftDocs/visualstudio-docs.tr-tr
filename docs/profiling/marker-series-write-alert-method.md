---
title: marker_series::write_alert yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic:marker_series::write_alert
helpviewer_keywords:
- Concurrency::diagnostic:marker_series::write_alert method
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a8d6909ee08984d0bff57f993538957b8958dcf2
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237373"
---
# <a name="markerserieswritealert-method"></a>marker_series::write_alert yöntemi
Bir uyarı eşzamanlılık görselleştiricisi izleme dosyasına yazar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
void write_alert(  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `_Format`  
 Metin içeren bileşik biçim dizesi bağımsız değişken listesinde nesnelere karşılık gelen, sıfır veya daha fazla biçimi öğeleri ile intermixed.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** *cvmarkersobj.h*  
  
 **Namespace:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [marker_series sınıfı](../profiling/marker-series-class.md)