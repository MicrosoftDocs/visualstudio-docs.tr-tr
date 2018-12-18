---
title: MESSAGETYPE | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d75b09377797135e03269bf9f0629a6ff0f81b83
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739562"
---
# <a name="messagetype"></a>MESSAGETYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Neden ve ileti türünü belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```csharp  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## <a name="members"></a>Üyeler  
 MT_OUTPUTSTRING  
 İleti için çıkış penceresine gönderilen olduğunu gösterir. Bu gelen birbirini dışlayan `MT_MESSAGEBOX`.  
  
 MT_MESSAGEBOX  
 İleti bir ileti kutusunda gösterilecek gösterir. Bu gelen birbirini dışlayan `MT_OUTPUTSTRING`.  
  
 MT_TYPE_MASK  
 İleti için hedef yalıtmak için bir maske değeri.  
  
 MT_REASON_EXCEPTION  
 Bir özel durum sonucu olarak bir ileti kutusu gösterilmekte olduğunu gösterir. Bu gelen birbirini dışlayan `MT_REASON_TRACEPOINT`.  
  
 MT_REASON_TRACEPOINT  
 Bir ileti kutusu sonucunda bir izleme noktasına ulaşma gösterilmekte olduğunu gösterir. Bu birbirini dışlayan olan `MT_REASON_EXCEPTION`.  
  
 MT_REASON_MASK  
 Gösterilen iletiyi nedeni yalıtmak için bir maske değeri.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu değerleri döndürülen [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) ve [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) yöntemleri.  
  
 Neden değerlerinden birleştirilebilir bit düzeyinde kullanarak çıkış hedef değerlerden biriyle `OR`.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabit listeleri](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)

