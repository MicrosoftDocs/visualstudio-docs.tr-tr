---
title: Iperpropertybrowsing2 arabirimi 1 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2 interface
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75a0a7ef30bca2205789a63ea577808c11582791
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794672"
---
# <a name="iperpropertybrowsing2-interface-1"></a>Iperpropertybrowsing2 arabirimi 1
Erişimleri özellik sayfaları bilgilerinde bir nesne tarafından sunulan.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`GetDisplayString`|Belirtilen özellik açıklayan bir metin dizesi döndürür.|  
|`MapPropertyToPage`|Belirtilen özellik işlenmesini sağlar özellik sayfası CLSID döndürür.|  
|`GetPredefinedStrings`|Dizeleri sayılan bir dizi döndürür (`LPOLESTR` işaretçileri) belirtilen özellik kabul edebilir izin verilen değerler açıklamalarını listesi.|  
|`SetPredefinedValue`|Özelliğinin değeri belirtecin tarafından tanımlanan tanımlanmış bir değer ayarlar`dwCookie.`|  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: dbgprop.h