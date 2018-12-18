---
title: Idebugdocumenthost arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHost interface
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adaeb98f18a052106036a91885696dd4b4760dea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794252"
---
# <a name="idebugdocumenthost-interface"></a>IDebugDocumentHost Arabirimi
Sözdizimi, hata ayıklayıcı için renklendirme gibi ana bilgisayara özgü işlevselliği kullanıma sunar. `IDebugDocumentHelper::SetDebugDocumentHost` Yöntemi bu arabirim bağımsız değişken olarak alır.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IUnknown`, `IDebugDocumentHost` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|Kullanarak eklenen karakter aralığı döndürür `IDebugDocumentHelper::AddDeferredText`, özgün konak belgedeki.|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|Bir belge metin bloğunu metin özniteliklerini döndürür.|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|Ana bilgisayar yeni bir belge bağlam oluşturuldu ve isteğe bağlı olarak yeni bağlam denetleyen bir nesne döndürmek ana bilgisayar tanır bildirir.|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|Belgenin kaynak dosyasının tam yolu (dosya adı dahil) döndürür.|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|Yol bilgisi olmadan belgenin adını döndürür.|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|Ana bilgisayar belgenin kaynak dosya kaydedildi ve içeriğini yenilenmesi gereken bildirir.|