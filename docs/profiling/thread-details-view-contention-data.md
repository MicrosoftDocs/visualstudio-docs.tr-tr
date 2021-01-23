---
title: İş parçacığı Ayrıntıları görünümü-çekişme verileri | Microsoft Docs
description: Iş parçacığı ayrıntıları görünümünün, bir profil oluşturma çalıştırmasının seçili iş parçacığında engelleme olaylarının bir zaman çizelgesi grafiğini nasıl sunmadığını öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threaddetails
helpviewer_keywords:
- Thread Details view
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d1cf1d9d7afeef8962026739116f75d4289d6283
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98718804"
---
# <a name="thread-details-view---contention-data"></a>İş parçacığı Ayrıntıları görünümü-çekişme verileri
Iş parçacığı Ayrıntıları görünümü, kaynak üzerinde çekişmeler nedeniyle oluşan profil oluşturma çalıştırmasının seçili iş parçacığındaki engelleme olaylarının zaman çizelgesi grafiğini sunar. Başka bir iş parçacığının bir kaynağa erişimi kilitlendiğinden, iş parçacığı yürütmeyi beklemeye zorken engelleyici bir olay oluşur.

 Bu görünüm, iş parçacığının yürütme zaman çizelgesini yatay bir çubuk olarak ve engelleyici olayları iş parçacığı için yatay bir zaman çizelgesinde dikey çubuk olarak gösterir. Gerektiğinde, tek tek olayları görüntülemek için zaman çizelgesinin bir bölümünü yakınlaştırabilirsiniz. Olaya işaret eden işlevlerin yürütme yolunu görüntülemek için olay çubuğuna tıklayın. İşlevler **çağrı yığını** penceresinde görünür. Bir işlevin kaynak kodu kullanılabilir olduğunda, Visual Studio IDE 'de kaynak dosyayı düzenlemek için işlev adına tıklayabilirsiniz.

## <a name="navigate-the-timeline"></a>Zaman çizelgesinde gezin

#### <a name="to-zoom-in-on-a-timeline-segment"></a>Bir zaman çizelgesi segmentini yakınlaştırmak için

- Zaman çizelgesindeki bir alanı seçmek için fare işaretçisini tıklatın ve sürükleyin.

     Fareyi serbest bırakırsanız, görünüm seçilen zaman segmentine yakınlaştırır. Daha ayrıntılı bir şekilde yakınlaştırmak için işlemi yineleyebilirsiniz. Zaman kaydırma çubuğundaki kaydırma kutusu, görünümde görüntülenen zaman diliminin göreli boyutunu temsil eder.

#### <a name="to-zoom-out-on-a-timeline"></a>Bir zaman çizelgesinde uzaklaştırmak için

- Önceki yakınlaştırma düzeyine dönmek için **uzaklaştır** ' ı tıklatın.

- Görünümdeki tüm zaman çizelgesini göstermek için **Yakınlaştırma sıfırlaması** ' na tıklayın.

#### <a name="to-view-the-call-stack-of-an-event"></a>Bir olayın çağrı yığınını görüntülemek için

- Zaman çizelgesi grafiğinde, olayı temsil eden dikey çubuğa tıklayın.

#### <a name="to-view-or-edit-the-source-code-of-a-function-in-the-call-stack"></a>Çağrı yığınında bir işlevin kaynak kodunu görüntülemek veya düzenlemek için

- **Çağrı yığını** penceresinde, işlev adına tıklayın.

  İşlev kaynak kodu, geçerli projenin bir parçası olmalıdır.

#### <a name="to-view-the-contention-events-of-a-resource-in-all-threads-in-the-profiling-run"></a>Profil oluşturma çalıştırmasında tüm iş parçacıklarında bir kaynağın çekişme olaylarını görüntülemek için

- Zaman çizelgesi grafiğinde kaynağın adına veya KIMLIğINE tıklayın.

     Seçili kaynak için [Kaynak Ayrıntıları görünümü](../profiling/resource-details-view-contention-data.md) görüntülenir.

#### <a name="to-view-the-thread-contention-data-in-the-processes-window"></a>Işler penceresinde iş parçacığı çakışması verilerini görüntülemek için

- Zaman çizelgesi grafiğinde **Toplam**' a tıklayın.

     [Işlem görünümü](../profiling/process-view-contention-data.md) seçili iş parçacığı ile görüntülenir.
