---
description: Belirli bir program için program düğümünü alır.
title: 'IDebugProgramProvider2:: GetProviderProgramNode | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 07e7184c189d501b2fcb604590eeb121bae8ccdc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065287"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Belirli bir program için program düğümünü alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetProviderProgramNode(
   PROVIDER_FLAGS       Flags,
   IDebugDefaultPort2*  pPort,
   AD_PROCESS_ID        processId,
   REFGUID              guidEngine,
   UINT64               programId,
   IDebugProgramNode2** ppProgramNode
);
```

```csharp
int GetProviderProgramNode(
   enum_PROVIDER_FLAGS    Flags,
   IDebugDefaultPort2     pPort,
   AD_PROCESS_ID          ProcessId,
   ref Guid               guidEngine,
   ulong                  programId,
   out IDebugProgramNode2 ppProgramNode
);
```

## <a name="parameters"></a>Parametreler
`Flags`\
'ndaki [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) numaralandırmasındaki bayrakların birleşimi. Aşağıdaki bayraklar bu çağrı için tipik olarak verilmiştir:

|Bayrak|Açıklama|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Çağıran uzak makinede çalışıyor.|
|`PFLAG_DEBUGGEE`|Çağıranın Şu anda hata ayıklaması yapılıyor (her düğüm için sıralama ile ilgili ek bilgiler döndürülecek).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Çağıran, hata ayıklayıcı tarafından eklenmiş ancak başlatılmamış.|

`pPort`\
'ndaki Çağıran işlemin üzerinde çalıştığı bağlantı noktası.

`processId`\
'ndaki Söz konusu programı içeren işlemin KIMLIĞINI tutan bir [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) yapısı.

`guidEngine`\
'ndaki Programın iliştirildiği hata ayıklama altyapısının GUID 'SI (varsa).

`programId`\
'ndaki Program düğümünün alınacağı programın KIMLIĞI.

`ppProgramNode`\
dışı İstenen program düğümünü temsil eden bir [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
