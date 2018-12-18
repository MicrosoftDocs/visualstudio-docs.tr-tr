---
title: IDebugDisassemblyStream2::Read | Microsoft Docs
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
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9bfa4fec20b715493a4f2f74c4a19aa845a44916
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725776"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ayrıştırılmış kodu stream'de geçerli konumundan başlayarak yönergeleri okur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
HRESULT Read(   
   DWORD                     dwInstructions,  
   DISASSEMBLY_STREAM_FIELDS dwFields,  
   DWORD*                    pdwInstructionsRead,  
   DisassemblyData*          prgDisassembly  
);  
```  
  
```csharp  
int Read(   
   uint                           dwInstructions,  
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,  
   out uint                       pdwInstructionsRead,  
   DisassemblyData[]              prgDisassembly  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwInstructions`  
 [in] Ayrıştırmak için yönergeler sayısı. Bu değer ayrıca uzunluğunun üst sınırı olan `prgDisassembly` dizi.  
  
 `dwFields`  
 [in] Bayraklarının bir birleşimi [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) hangi alanları gösteren numaralandırma `prgDisassembly` doldurulması için.  
  
 `pdwInstructionsRead`  
 [out] Aslında çözülürken yönerge sayısını döndürür.  
  
 `prgDisassembly`  
 [out] Bir dizi [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) ayrıştırılmış kodu, ayrıştırılmış yönerge başına bir yapı doldurulur yapılar. Bu dizinin uzunluğu tarafından dikte `dwInstructions` parametresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa döndürür `S_OK`; Aksi takdirde bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Geçerli kapsamdaki kullanılabilir olan yönergeleri sayısı çağrılarak alınabilir [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) yöntemi.  
  
 Burada sonraki yönergesi okuma geçerli konumu çağırarak değiştirilebilir [arama](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) yöntemi.  
  
 `DSF_OPERANDS_SYMBOLS` Bayrağı eklenebilir `DSF_OPERANDS` bayrağını `dwFields` sembol adlarını yönergeleri derlemesini açma işlemlerini uygulama zaman kullanılması gerektiğini belirtmek için parametre.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)

