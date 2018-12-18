---
title: BP_RESOLUTION_LOCATION | Microsoft Docs
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
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dc70710ea0a811b75e6bad3098fbbc46dae0bd3b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760755"
---
# <a name="bpresolutionlocation"></a>BP_RESOLUTION_LOCATION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Kesme noktası çözünürlüğü konumu yapısını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
struct _BP_RESOLUTION_LOCATION {  
   BP_TYPE bpType;  
   union {  
      BP_RESOLUTION_CODE bpresCode;  
      BP_RESOLUTION_DATA bpresData;  
      int                unused;  
   } bpResLocation;  
} BP_RESOLUTION_LOCATION;  
```  
  
```csharp  
public struct BP_RESOLUTION_LOCATION {  
   public uint bpType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public uint   unionmember4;  
};  
```  
  
## <a name="members"></a>Üyeler  
 `bpType`  
 Bir değer [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) yorumlama belirten numaralandırma `bpResLocation` birleşim veya `unionmemberX` üyeleri.  
  
 `bpResLocation.bpresCode`  
 [Yalnızca C++] İçeren [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) , yapı `bpType`  =  `BPT_CODE`.  
  
 `bpResLocation.bpresData`  
 [Yalnızca C++] İçeren [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) , yapı `bpType`  =  `BPT_DATA`.  
  
 `bpResLocation.unused`  
 [Yalnızca C++] Bir yer tutucu.  
  
 `unionmember1`  
 [C# yalnızca] Yorumlama konusunda açıklamalara bakın.  
  
 `unionmember2`  
 [C# yalnızca] Yorumlama konusunda açıklamalara bakın.  
  
 `unionmember3`  
 [C# yalnızca] Yorumlama konusunda açıklamalara bakın.  
  
 `unionmember4`  
 [C# yalnızca] Yorumlama konusunda açıklamalara bakın.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapı üyesidir [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) ve [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) yapıları.  
  
 [C# yalnızca] `unionmemberX` Üyeleri aşağıdaki tabloya göre yorumlanır. Sol sütundaki için konum `bpType` boyunca hangi her belirlemek için değer `unionmemberX` üye temsil eder ve sıralama `unionmemberX` uygun şekilde. Bu yapı C# yorumlamak bir yol için örneğe bakın.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|  
|`BPT_DATA`|`string` (veri ifadesi)|`string` (işlev adı)|`string` (görüntü adı)|`enum_BP_RES_DATA_FLAGS`|  
  
## <a name="example"></a>Örnek  
 Bu örnek nasıl yorumlanacağını gösterir `BP_RESOLUTION_LOCATION` C# yapısı.  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(BP_RESOLUTION_LOCATION bprl)  
        {  
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)  
            {  
                 IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);  
            }  
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)  
            {  
                 string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);  
                 string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılar ve birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)

