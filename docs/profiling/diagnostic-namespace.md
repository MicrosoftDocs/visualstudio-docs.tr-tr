---
title: Tanılama Namespace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords:
- Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d781bbfefa59b2e124cf76c11b8fd7c06cc66dda
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764676"
---
# <a name="diagnostic-namespace"></a>Tanılama ad alanı
`diagnostics` Ad alanı, eşzamanlılık görselleştiricisi işaretleyicileri yayma için işlevsellik sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
namespace diagnostic;  
```  
  
## <a name="members"></a>Üyeler  
  
### <a name="classes"></a>Sınıflar  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[marker_series Sınıfı](../profiling/marker-series-class.md)|Tek bir sağlayıcı tarafından oluşturulan olayların seri kanal temsil eder.|  
|[span Sınıfı](../profiling/span-class.md)|Bir uygulama aşaması tanımlar.|  
  
### <a name="enumerations"></a>Numaralandırmalar  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[marker_importance Sabit Listesi](../profiling/marker-importance-enumeration.md)|Eşzamanlılık görselleştiricisi işaret önem düzeyini temsil eder.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** *cvmarkersobj.h*  
  
 **Namespace:** eşzamanlılık  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Eşzamanlılık ad alanı (eşzamanlılık görselleştiricisi)](../profiling/concurrency-namespace-concurrency-visualizer.md)