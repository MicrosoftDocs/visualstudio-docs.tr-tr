---
title: DISASSEMBLY_STREAM_FIELDS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9489b8c4399ae72bf7f6a70011eec347d870ca80
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928340"
---
# <a name="disassemblystreamfields"></a>DISASSEMBLY_STREAM_FIELDS
Ayrıştırılmış kod alana almak için hangi bilgilerin belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
typedef DWORD DISASSEMBLY_STREAM_FIELDS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
```  
  
## <a name="members"></a>Üyeler  
 DSF_ADDRESS  
 Başlat/kullanım `bstrAddress` alan.  
  
 DSF_ADDRESSOFFSET  
 Başlat/kullanım `bstrAddressOffset` alan.  
  
 DSF_CODEBYTES  
 Başlat/kullanım `bstrCodeBytes` alan.  
  
 DSF_OPCODE  
 Başlat/kullanım `bstrOpCode` alan.  
  
 DSF_OPERANDS  
 Başlat/kullanım `bstrOperands` alan.  
  
 DSF_SYMBOL  
 Başlat/kullanım `bstrSymbol` alan.  
  
 DSF_CODELOCATIONID  
 Başlat/kullanım `uCodeLocationId` alan.  
  
 DSF_POSITION  
 Başlat/kullanım `posBeg` ve `posEnd` alanları.  
  
 DSF_DOCUMENTURL  
 Başlat/kullanım `bstrDocumentUrl` alan.  
  
 DSF_BYTEOFFSET  
 Başlat/kullanım `dwByteOffset` alan.  
  
 DSF_FLAGS  
 Başlat/kullanım `dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) alan.  
  
 DSF_OPERANDS_SYMBOLS  
 Sembol adlarında `bstrOperands` alan.  
  
 DSF_ALL  
 Tüm alanlar için Ayrıştırılmış kod akışını belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir parametre olarak geçirilen [okuma](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) hangi alanları göstermek için yöntemi [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) yapısı olan başlatılacak.  
  
 İçin kullanılan `dwFields` üyesi `DisassemblyData` yapısı yapısı döndürüldüğünde hangi alanların kullanılan ve geçerli olduğunu belirtmek için.  
  
 Bu değerler, bit düzeyinde ile birleştirilebilir `OR`.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sabit listeleri](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Okuma](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)