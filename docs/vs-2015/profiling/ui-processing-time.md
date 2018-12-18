---
title: UI işleme zamanı | Microsoft Docs
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
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ecf2c33b2af2e57c964e145a334f6dd0d7161a92
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738429"
---
# <a name="ui-processing-time"></a>UI İşleme Zamanı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu segmentlerde faaliyet zaman çizelgesi UI işleme sınıflandırılmış bir kez engelleme ile ilişkilidir. Bu, bir iş parçacığı Windows iletileri Pompalama veya diğer kullanıcı arabirimi (UI) iş yapılırken anlamına gelir. Bu süre boyunca, bir iş parçacığı UI işleme Concurrency Visualizer sayımını bir API'de engellendi. API'leri gibi `GetMessage()` ve `MsgWaitForMultipleObjects()` bu gruba girer.  
  
 Önceden tanımlanmış hiçbir engelleme API belirlenirse, çağrı yığınları ve profil raporlarını gecikmesi temel nedenlerini belirlemek için gözden geçirin.  
  
 UI işleme kategorisi, GUI uygulamalarının yanıt verme becerisini anlamak için önemlidir ve kullanıcı Arabirimi yanıt hızı üzerinde bağlı uygulamalarda tercih edilir. Örneğin, bir uygulama kullanıcı Arabirimi iş parçacığında UI işleme % 100 sürede tutarsa büyük olasılıkla çok yanıt veriyor. Ancak, UI iş parçacığı diğer kategorilerde büyük miktarda zaman harcıyorsa, kök nedeni arayın ve iş parçacığı UI olmayan kategorilerindeki azaltma seçenekleri göz önünde bulundurun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)



