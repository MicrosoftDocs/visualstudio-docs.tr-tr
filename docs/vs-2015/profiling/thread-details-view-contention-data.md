---
title: İş parçacığı Ayrıntıları görünümü - çakışma verileri | Microsoft Docs
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
- vs.performance.view.threaddetails
helpviewer_keywords:
- Thread Details view
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da2cac3503f97976fe5c0918f86e5b25f2b89329
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795666"
---
# <a name="thread-details-view---contention-data"></a>İş Parçacığı Ayrıntıları Görünümü - Çakışma Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İş parçacığı Ayrıntıları görünümü kaynaklar üzerinde Çekişme tarafından neden Seçili iş parçacığı profil oluşturma çalıştırmasını engelleme olayları bir zaman çizelgesi grafiği gösterir. İş parçacığı başka bir iş parçacığının bir kaynağa erişim kilitlediği için yürütmeyi askıya almak zorunda engelleyen bir olayı oluşur.  
  
 Bu görünüm, yürütme zaman çizelgesi yatay bir çubuk olarak iş parçacığı ve iş parçacığı için yatay bir zaman çizelgesi üzerinde dikey çubuk olarak engelleme olayları temsil eder. Gerekli olduğunda bir bölüm olayları tek tek görüntülemek için zaman çizelgesinin yakınlaştırma yapabilirsiniz. Olaya yol açan işlevlerin yürütme yolu görüntülemek için olay Çubuğu'nu tıklatın. İşlevler çağrı yığını penceresinde görünür. Bir işlev için kaynak kodu kullanılabilir olduğunda, Visual Studio IDE'de kaynak dosyayı düzenlemek için işlev adına tıklayabilirsiniz.  
  
## <a name="navigating-the-timeline"></a>Zaman Çizelgesi gezinme  
  
#### <a name="to-zoom-in-on-a-timeline-segment"></a>Bir zaman çizelgesi segmenti yakınlaştırmak için  
  
-   Tıklayın ve zaman çizelgesi bir alanı seçmek için fareyi sürükleyin.  
  
     Fare düğmesini bırakın, seçilen zaman segmente görünümü yakınlaştırır. Daha ayrıntılı olarak yakınlaştırmak için işlemini tekrar edebilirsiniz. Kaydırma kutusunun zaman kaydırma çubuğundaki görünümünde görüntülenen zaman diliminin göreli boyutu temsil eder.  
  
#### <a name="to-zoom-out-on-a-timeline"></a>Bir zaman çizelgesinde uzaklaştırmak için  
  
-   Tıklayın **Uzaklaştır** önceki yakınlaştırma düzeyi için döndürülecek.  
  
-   Tıklayın **yakınlaştırma sıfırlama** görünümde tüm zaman çizelgesini göstermek için.  
  
#### <a name="to-view-the-call-stack-of-an-event"></a>Bir olayın çağrı yığınını görüntülemek için  
  
-   Zaman Çizelgesi grafiğe, olayı temsil eden dikey çubuk tıklayın...  
  
#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Görüntüleme veya çağrı yığınında bir işlevin kaynak kodunu düzenleme  
  
- Çağrı yığını penceresinde işlev adına tıklayın.  
  
  İşlev kaynak kodu, geçerli projenin bir parçası olması gerekir.  
  
#### <a name="to-view-the-contention-events-of-a-resource-in-all-threads-in-the-profiling-run"></a>Profil oluşturma, tüm iş parçacıklarının kaynak Çekişme olayları görüntülemek için  
  
-   Adı veya kimliği kaynak zaman çizelgesi grafiğe tıklayın.  
  
     [Kaynak Ayrıntıları görünümü](../profiling/resource-details-view-contention-data.md) seçili kaynak için görünür.  
  
#### <a name="to-view-the-thread-contention-data-in-the-processes-window"></a>İş parçacığı Çekişme verisi işlemleri penceresinde görüntülemek için  
  
-   Zaman Çizelgesi grafiğe **toplam**.  
  
     [İşlem görünümü](../profiling/process-view-contention-data.md) Seçili iş parçacığı ile görünür.



