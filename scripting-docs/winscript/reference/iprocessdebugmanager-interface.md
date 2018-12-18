---
title: Iprocessdebugmanager arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProcessDebugManager interface
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26c97fda6fc8657164e22d51eb041017a6239d98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794921"
---
# <a name="iprocessdebugmanager-interface"></a>IProcessDebugManager Arabirimi
İşlem Hata Ayıklama Yöneticisi'ni birincil arabirim. Bu arabirim oluşturmak, eklemek veya bir sanal uygulamayı bir işlemden kaldırın. Yığın çerçeveleri ve uygulama iş parçacığı sıralayabilirsiniz.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IUnknown`, `IProcessDebugManager` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|Bu uygulama için yeni bir hata ayıklama uygulama nesnesi oluşturur.|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|Geçerli işlem için bir varsayılan uygulama nesnesi döndürür.|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|Çalışan uygulamalar Makine Hata Ayıklama Yöneticisi'nin listesine bir uygulama ekler.|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|Bir uygulamanın çalışmasını kaldırır uygulama listesi.|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|Bu uygulama için yeni bir hata ayıklama belge Yardımcısı oluşturur.|