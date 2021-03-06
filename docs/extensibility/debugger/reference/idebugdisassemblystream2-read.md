---
description: Ayrıştırılmış birleştirme akışındaki geçerli konumdan başlayan yönergeleri okur.
title: 'IDebugDisassemblyStream2:: Read | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bcabd0cc42f013b579ee32deeb33d68cd9d45f5d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066925"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
Ayrıştırılmış birleştirme akışındaki geçerli konumdan başlayan yönergeleri okur.

## <a name="syntax"></a>Sözdizimi

```cpp
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

## <a name="parameters"></a>Parametreler
`dwInstructions`\
'ndaki ' İ çözeceği yönergelerin sayısı. Bu değer aynı zamanda dizinin uzunluk üst sınırıdır `prgDisassembly` .

`dwFields`\
'ndaki [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) Numaralandırmadaki, doldurulacak alanları gösteren bayrakların birleşimi `prgDisassembly` .

`pdwInstructionsRead`\
dışı Aslında ayrıştırılmış yönergelerin sayısını döndürür.

`prgDisassembly`\
dışı Ayrıştırılmış bir yönerge başına bir yapı olan, ayrıştırılmış kodla doldurulmuş, ayrıştırılmış bir [veri](../../../extensibility/debugger/reference/disassemblydata.md) yapıları dizisi. Bu dizinin uzunluğu parametresi tarafından dikte edilir `dwInstructions` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Geçerli kapsamda kullanılabilir olan en fazla yönerge sayısı [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) metodu çağırarak elde edilebilir.

 Next yönergesinin okunduğu geçerli konum, [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) yöntemi çağırarak değiştirilebilir.

 `DSF_OPERANDS_SYMBOLS`Bayrak, `DSF_OPERANDS` `dwFields` yönergeleri oluştururken sembol adlarının kullanılması gerektiğini göstermek için parametresindeki bayrağa eklenebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
