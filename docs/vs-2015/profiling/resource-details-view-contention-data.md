---
title: Kaynak Ayrıntıları görünümü - çakışma verileri | Microsoft Docs
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
- vs.performance.view.resourcedetails
helpviewer_keywords:
- Resource Details view
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 98cc1d3f281108ef23f073ceae69d97fa3c0c32a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782472"
---
# <a name="resource-details-view---contention-data"></a>Kaynak Ayrıntıları Görünümü - Çakışma Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kaynak Ayrıntıları görünümü çakışması tarafından seçilen bir kaynak üzerinde kaynaklanan engelleme olayların bir zaman çizelgesi grafiği gösterir. Bir iş parçacığı başka bir iş parçacığının kaynağa erişim kilitlediği için yürütmeyi askıya almak zorunda engelleyen bir olayı oluşur.  
  
 Bu görünüm, yatay bir çubuk olarak her bir iş parçacığı yürütme zaman çizelgesi temsil eder ve iş parçacığı zaman çizelgesi üzerinde dikey bir çubuk olarak her engelleyen bir olayı temsil eder. Gerekli olduğunda olayları tek tek görüntülemek için zaman çizelgesinin bir bölümü büyütebilirsiniz. Olaya yol açan işlevlerin yürütme yolu (çağrı yığınını) görüntülemek için olay Çubuğu'nu tıklatın. İşlevleri görünür **çağrı yığını** penceresi. Bir işlev için kaynak kodu kullanılabilir duruma geldiğinde arabirimdeki kaynak dosyayı düzenlemek için işlev adını tıklayabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-magnify-a-timeline-segment"></a>Bir zaman çizelgesi segmenti büyütmek için  
  
-   Fare işaretçisi bir zaman çizelgesi alanı üzerine sürükleyin.  
  
     Fare düğmesini bıraktığınızda, seçilen zaman segmente görünümü yakınlaştırır. Daha fazla kesim büyütmek için işlemini tekrar edebilirsiniz. Kaydırma kutusunun zaman kaydırma çubuğundaki görünümünde görüntülenen zaman diliminin göreli boyutu temsil eder.  
  
#### <a name="to-zoom-out-on-a-timeline"></a>Bir zaman çizelgesinde uzaklaştırmak için  
  
-   Aşağıdaki adımlardan birini uygulayın:  
  
    -   Tıklayın **Uzaklaştır** önceki yakınlaştırma düzeyi için döndürülecek.  
  
    -   Tıklayın **yakınlaştırma sıfırlama** tüm zaman çizelgesinin görünümde göstermek için.  
  
#### <a name="to-view-the-call-stack-of-an-event"></a>Bir olayın çağrı yığınını görüntülemek için  
  
-   Zaman Çizelgesi grafikte olay çubuğuna tıklayın.  
  
#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Görüntüleme veya çağrı yığınında bir işlevin kaynak kodunu düzenleme  
  
- İçinde **çağrı yığını** penceresinde işlev adına tıklayın.  
  
  İşlev kaynak kodu, geçerli projenin bir parçası olması gerekir.  
  
#### <a name="to-view-the-call-tree-of-contention-events-for-the-resource"></a>Çağırma ağacına kadar kaynak için Çekişme olayları görüntülemek için  
  
-   Zaman Çizelgesi grafiğe **toplam**.  
  
     Kaynak çekişmeleri görünümü görüntülenir. Daha fazla bilgi için [kaynak çekişmeleri görünümü](../profiling/resource-contentions-view-contention-data.md)  
  
#### <a name="to-view-all-the-contention-events-of-a-thread"></a>Bir iş parçacığının tüm Çekişme olayları görüntülemek için  
  
-   Adını veya iş parçacığının kimliği zaman çizelgesi grafiğe tıklayın.  
  
     Seçili iş parçacığı için iş parçacığı Ayrıntıları görünümü görüntülenir. Daha fazla bilgi için [iş parçacığı Ayrıntıları görünümü](../profiling/thread-details-view-contention-data.md).



