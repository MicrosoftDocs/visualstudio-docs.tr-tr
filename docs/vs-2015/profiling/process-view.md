---
title: İşlem görünümü | Microsoft Docs
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
- vs.performance.view.process
helpviewer_keywords:
- performance tools reports, process view
- Process view
- performance tools, process view
- Profiling Tools,process view
- Profiling Tools,process report
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56fb301436b3fbe9374301fa4f7a8fd421485cbb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794510"
---
# <a name="process-view"></a>İşlem Görünümü
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İşlem görünümü, profil oluşturma çalışması sırasında yürütülen iş parçacıkları ve işlemler için profil oluşturma verilerini görüntüler.  
  
 İşlem adına göre listelenmiştir. İş parçacıkları, onları oluşturan işlem alt düğümleri olarak listelenir. İş parçacıkları adlı etiketi veya iş parçacığı çalışmaya işlevi tarafından **[ntdll.dll]** sembol varsa.  
  
 Sütun ekleme veya kaldırma için görünümü sağ tıklayın ve ardından **sütunları Ekle/Kaldır**. Ayrıca, bir sütun adına tıklayarak verileri yeniden sıralayabilirsiniz. Daha fazla bilgi için [nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md).  
  
 İşlem görünümü sütunlarını ve .NET bellek verileri içeren veri örnekleme ve izleme yöntemleri kullanarak oluşturulan verileri için aynıdır. Sütun değerleri aşağıdaki tabloda açıklanmaktadır.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Benzersiz kimliği**|İş parçacığı ve işlem için benzersiz olan bir profil oluşturucu tarafından oluşturulan bir tanımlayıcı.|  
|**ID**|Sistem tarafından oluşturulan bir tanımlayıcı işlem veya iş parçacığı.|  
|**Ad**|İşlem veya iş parçacığı adı.|  
|**Başlangıç zamanı**|Milisaniye veya işlemci sayısını, işlem veya iş parçacığı başına profil oluşturma başlangıç geçiş yapar.|  
|**Bitiş zamanı**|Milisaniye veya işlemci sayısını başından sonuna kadar işlem veya iş parçacığı profil oluşturma.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)   
 [İzleme metodu veri görünümleri](../profiling/instrumentation-method-data-views.md)   
 [.NET Bellek Verisi Görünümleri](../profiling/dotnet-memory-data-views.md)



