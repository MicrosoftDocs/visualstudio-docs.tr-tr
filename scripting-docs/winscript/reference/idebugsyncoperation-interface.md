---
title: Idebugsyncoperation arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSyncOperation interface
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6705c2aa990aef3cf551a94546bf78a64026cecc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794258"
---
# <a name="idebugsyncoperation-interface"></a>IDebugSyncOperation Arabirimi
Belirli bir engellenmiş iş parçacığı, iç içe geçmiş sırada gerçekleştirilmesi gerekir (örneğin, ifade değerlendirme) bir işlem soyut için bir komut dosyası altyapısı sağlar. Arabirim ayrıca yanıt vermeyen işlemleri iptal ediliyor için bir mekanizma sağlar.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IUnknown`, `IDebugSyncOperation` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|Bu zaman uyumlu işlem için hedef uygulama iş parçacığı döndürür.|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|Zaman uyumlu olarak işlemi gerçekleştirir ve döndürür.|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|Devam eden başka bir iş parçacığı üzerinde bir işlemi iptal eder.|