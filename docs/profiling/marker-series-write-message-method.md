---
title: marker_series::write_message yöntemi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::write_message
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::write_message method
ms.assetid: 546121bc-67e0-4a5a-a456-12bd78fd6de2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70e413267623d4e9bb4b8d4c1f46fd9c6ecf7808
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237958"
---
# <a name="markerserieswritemessage-method"></a>marker_series::write_message yöntemi
Eşzamanlılık görselleştiricisi izleme dosyası için bir ileti yazar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
void write_message(  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `_Format`  
 Metin içeren bileşik biçim dizesi bağımsız değişken listesinde nesnelere karşılık gelen, sıfır veya daha fazla biçimi öğeleri ile intermixed.  
  
 `_Importance`  
 Önem düzeyi.  
  
 `_Category`  
 Category.Importance düzeyi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** *cvmarkersobj.h*  
  
 **Namespace:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [marker_series sınıfı](../profiling/marker-series-class.md)