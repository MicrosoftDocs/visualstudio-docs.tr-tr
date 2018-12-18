---
title: GPU etkinliği (Bu işlem) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1b0949a71dc4db1ee217d691d4aae7928faf301
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751415"
---
# <a name="gpu-activity-this-process"></a>GPU Etkinliği (Bu İşlem)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**GPU etkinliği (Bu işlem)** kesimlerinde eşzamanlılık görselleştiricisi'ndeki iş parçacıkları görünümü zaman GPU işlem istekleri geçerli işlem adına bir kez temsil eder. Bu istekler GPU'ya doğrudan bellek erişimi (DMA) paketleri gönderilir. Segment uzunluğunu GPU DMA paket adına geçerli işlem işleme zamanı temsil eder.  
  
 Üzerinde GPU etkinliği segment, raporun seçtiğinizde **geçerli** sekmesini işlenmiş DMA paket hakkında bilgileri görüntüler. Bu bilgiler, DirectX altyapısı, paketi gönderilen işlem ve paket işlemek için gereken zamanı ile ilişkili donanım kuyruğundaki paket beklenen süre miktarını içerir. Geçerli işlemin dışında bir işlem GPU DMA paketi fiziksel olarak gönderilen. Eşzamanlılık görselleştiricisi, başka bir işlem geçerli işlemin adına GPU iş gönderildiğinde algılayabilir.



