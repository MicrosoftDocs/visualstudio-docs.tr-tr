---
title: Dosya izleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 394b40a304d2aba3b79c5878befe33a8a1aaf8b8
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37945565"
---
# <a name="file-tracking"></a>Dosya izleme
Dosya izleme bir işlem ve onun alt işlemleri için Windows dosya sistemi çağrıları günlüğe kaydeder. Aşağıda listelenen işlevleri çağırarak, programlar bu oturum açıp kapatmak ve kullanmak için günlük dosyasını belirtmek ne zaman denetler.  
  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 Geçerli bağlamı İzlemeyi Durdur.  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 Çağrısı yapıldıktan sonra izlemeyi Sürdür [SuspendTracking](../msbuild/suspendtracking.md).  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 İzleme için kullanılacak iş parçacığı sayısını ayarlayın.  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 Yeni bir izleme bağlamına başlayın.  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 Belirtilen kök ile yeni bir izleme bağlamına başlayın.  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 İzleme ve kullanılan yayın kaynaklarını sonlandır.  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 Geçici olarak askıya alma izleme.  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 Tüm Bağlamlar için izleme günlüklerini dışarı yazın.  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 Geçerli bağlam için izleme günlüğünü dışarı yazın.