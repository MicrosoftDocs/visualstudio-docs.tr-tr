---
title: Bayrak işaretleyicileri | Microsoft Docs
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
- vs.cv.markers.flag
ms.assetid: f3ec919e-63e5-484b-adbf-8f0e79342e75
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c4d1e5c119c5402501efaafcdccd9c3d0885ce75
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803207"
---
# <a name="flag-markers"></a>Bayrak İşaretleyicileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bayrak işareti anlık uygulama zamanda gerçekleşen bir sorun temsil eder. Bayrak pek çok uygulama olayları temsil edebilir. Örneğin, belirli iş öğesi zaman zamanlanan veya özel durum oluştuğunda bir bayrak gösterebilirsiniz. Görev paralel kitaplığı gibi çalışma zamanları bayrakları da oluşturabilirsiniz.  
  
## <a name="flag-importance"></a>Bayrağı önem derecesi  
 Bayrakları, farklı boyutlarda önemine bağlı olarak görüntülenir. Herhangi bir işaretçi gibi düşük, normal, yüksek veya kritik önem olabilir.  Bu çizim önem düzeyine göre işaretçiler görünümünü gösterir:  
  
 ![Düşük, Normal, yüksek ve kritik önem işaretçileri](../profiling/media/cvmarkerimportance.png "CVMarkerImportance")  
Bayrağı önemini gösteren işaretçiler  
  
## <a name="flag-category"></a>Bayrağı kategorisi  
 Bayrak kategori bağlı olarak beş farklı renkler biriyle görüntülenir. Beşten fazla kategorileri varsa renkleri yeniden kullanılır. Renk seçemezsiniz. Herhangi bir işaretçi gibi kategori herhangi bir tamsayı olabilir. Bir sonraki resimde, ilk beş kategorileri için renkleri gösterir.  
  
 ![Kategori işaretçilerinin beş renkleri](../profiling/media/cvmarkercategory.png "CVMarkerCategory")  
Kategorileri gösteren işaretçiler  
  
## <a name="alerts"></a>Uyarılar  
 Bir uyarı, bir özel durum gibi kritik uygulama yer alan bir olayı temsil eden kırmızı renkli bayrak belirtir.  Bir uyarı şu şekildedir:  
  
 ![Eşzamanlılık görselleştiricisi uyarı işaret](../profiling/media/cvmarkeralert.png "CVMarkerAlert")  
Bir uyarı işareti  
  
## <a name="aggregation-flags"></a>Toplama bayrakları  
 Bazen bayrakları bunu birbirine yakın bunlar ayrı ayrı çekilemez eşzamanlılık görselleştiricisi içinde oluşur. Bu oluştuğunda, bir gri *toplama bayrağı* temsil temel alınan bayrakları gösterilir. Bu simgeler biri üzerinde işaretçiyi getirdiğinizde araç ipucu temsil edilen temel alınan bayrakları sayısını görüntüler. Bayrakları görüntülemek için yakınlaştırın. Tüm yakınlaştırmak ve toplama bayrağı almaya devam ediyorsanız, temel alınan bayrakları görüntüleyebileceğiniz [işaretçiler raporu](../profiling/markers-report.md).  
  
 Toplama bayrakları, farklı boyutlardaki çizilir. Toplama en önemli bayrağı önem düzeyini boyutuna bağlıdır. Aşağıdaki çizim, artan sırada önem toplama bayrakları gösterir.  
  
 ![Toplam dört önem düzeylerini gösteren bayraklar](../profiling/media/cvmarkeraggregate.png "CVMarkerAggregate")  
Önem düzeyine göre toplama bayrakları  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eşzamanlılık görselleştiricisi işaretleyicileri](../profiling/concurrency-visualizer-markers.md)   
 [Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)



