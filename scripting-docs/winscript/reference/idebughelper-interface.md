---
title: Idebughelper arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugHelper interface
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f0f70ecb8ead264d0d4b074f8fc1d9e3a6091eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794348"
---
# <a name="idebughelper-interface"></a>IDebugHelper Arabirimi
Nesne tarayıcılar ve basit bağlantı noktaları için bir üreteci olarak görev yapar. İşlem Hata Ayıklama Yöneticisi'ni (PDM) komut dosyası motorları tarafından tüketilen bu arabirimi uygular.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IUnknown`, `IDebugHelper` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|Bir değişken saran bir özellik tarayıcısı döndürür.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|Bir değişken sarmalar ve değişken değerleri veya VARTYPE türlerini özel dönüştürme dizeleri için sağlayan bir özellik tarayıcısı döndürür.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|Kaydırılan bir olay arabirimi döndürür bir verilen `IDispatch` nesnesi.|