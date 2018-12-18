---
title: BP_PASSCOUNT_STYLE | Microsoft Docs
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
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e71ecf9abbb670a7d50efd24e778a8f86208b0a4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764494"
---
# <a name="bppasscountstyle"></a>BP_PASSCOUNT_STYLE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Kesme noktası ateşlenmesine neden kesme noktası geçişi sayısı ile ilişkilendirilmiş olan koşul belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```csharp  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## <a name="members"></a>Üyeler  
 BP_PASSCOUNT_NONE  
 Hiçbir kesme noktası geçişi sayısı stilini belirtir.  
  
 BP_PASSCOUNT_EQUAL  
 Eşit olacak şekilde kesme noktası geçişi sayısı stilini ayarlar. Kesme noktası geçişi sayısı kesme noktasına isabet sayısı eşit olduğunda tetiklenir.  
  
 BP_PASSCOUNT_EQUAL_OR_GREATER  
 Eşit veya daha fazla kesme noktası geçişi sayısı stilini ayarlar. Kesme noktasına, kesme noktası isabet sayısını geçişi sayısından büyük veya eşit olduğunda tetiklenir.  
  
 BP_PASSCOUNT_MOD  
 Belirtir bir modül geçiş sayısı. Örneğin, geçiş sayısı türü ise `BP_PASSCOUNT_MOD` ve geçişi sayısı değeri 4, isabet sayısı 4'ün katı her zaman kesme noktası ateşlenir.  
  
## <a name="remarks"></a>Açıklamalar  
 İçin kullanılan `stylePassCount` üyesi [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) sırayla üyesi yapısı [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ve [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) yapıları.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabit listeleri](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)

