---
title: Idisperror arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispError interface
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9f139d317db5aa00f03f8e9abd71020e5ff35b03
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794588"
---
# <a name="idisperror-interface"></a>IDispError Arabirimi
Bağlamsal ayrıntılı hata bilgileri sağlar.  
  
> [!NOTE]
>  Bu arabirim uygulanmadı.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IUnknown`, `IDispError` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|Hata bilgilerini belirli bir türü alır.|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|Sonraki alır `IDispError` nesnesi.|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|Gelen hata kodunu alır `IDispError` nesnesi.|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|Sınıf veya hataya neden uygulama için dile bağlı programlı tanımlayıcısını döndürür.|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|Yardım dosyasının yolunu ve hata mümkünse açıklayan konu bağlam Kimliğini döndürür.|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|Hata metinsel açıklaması döndürür.|