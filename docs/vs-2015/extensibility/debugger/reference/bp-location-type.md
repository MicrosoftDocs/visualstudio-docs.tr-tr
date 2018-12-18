---
title: BP_LOCATION_TYPE | Microsoft Docs
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
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 16f990ef25e5a7e16519d3eed67becee20d236e2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817392"
---
# <a name="bplocationtype"></a>BP_LOCATION_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir kesme noktası istek için bir kesme noktası konumu türünü belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
typedef DWORD BP_LOCATION_TYPE;  
```  
  
```csharp  
public enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
```  
  
## <a name="members"></a>Üyeler  
 BPLT_NONE  
 Hiçbir kesme noktası konumu belirtir.  
  
 BPLT_FILE_LINE  
 Kesme noktası konum türü, bir dosya satırı belirtir.  
  
 BPLT_FUNC_OFFSET  
 Kesme noktası konum türü bir işlev uzaklığı belirtir.  
  
 BPLT_CONTEXT  
 Kesme noktası konum türü bağlamı olarak belirtir.  
  
 BPLT_STRING  
 Kesme noktası konum türü bir dize olarak belirtir.  
  
 BPLT_ADDRESS  
 Kesme noktası konum türü bir adresi belirtir.  
  
 BPLT_RESOLUTION  
 Kesme noktası konum türü bir çözüm belirtir.  
  
 BPLT_CODE_FILE_LINE  
 Kesme noktası konum türü, bir kaynak kod satırı belirtir.  
  
 BPLT_CODE_FUNC_OFFSET  
 Kesme noktası konum türü bir kod işlevi uzaklığı belirtir.  
  
 BPLT_CODE_CONTEXT  
 Kesme noktası konum türü kod bağlamı olarak belirtir.  
  
 BPLT_CODE_STRING  
 Kesme noktası konum türü, bir kod dize olarak belirtir.  
  
 BPLT_CODE_ADDRESS  
 Kesme noktası konum türü bir kod adresiyle belirtir.  
  
 BPLT_DATA_STRING  
 Kesme noktası konum türü verileri dize olarak belirtir.  
  
 BPLT_TYPE_MASK  
 Kesme noktası türü, değer dışında ayıklanabileceği bir bit maskesi belirtir.  
  
 BPLT_LOCATION_TYPE_MASK  
 Kesme noktası konum türü değeri dışında ayıklanabileceği bir bit maskesi belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir parametre olarak geçirilen [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) yöntemi.  
  
 Bir kesme noktası konum türü, bir kesme noktası türü ve konum türü oluşur. Bu bir kesme noktası konum türü hiçbir zaman yalnızca bir kesme noktası türü olduğu anlamına gelir (örneğin, `BPT_CODE`) veya bir konum türü (örneğin, `BPLT_FILE_LINE`). Şu anda desteklenen tüm kesme noktası konumu türleri için önceden tanımlanmış sabitleri bu numaralandırmada dahil edilir (`BPLT_CODE_FILE_LINE` aracılığıyla `BPLT_DATA_STRING`).  
  
 `BPT_CODE` ve `BPT_DATA` üyeleri [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) sabit listesi.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabit listeleri](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)

