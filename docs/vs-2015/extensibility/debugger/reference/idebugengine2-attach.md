---
title: IDebugEngine2::Attach | Microsoft Docs
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
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 260d3fcbe58b9db1b1f465c249a44a5ee6d9a6aa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781991"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir programı veya programları için hata ayıklama altyapısı (DE) ekler. DE çalışan işlem içinde SDM oturum hata ayıklama Yöneticisi (SDM) tarafından çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```csharp  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pProgram`  
 [in] Bir dizi [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) eklenmesi için programlar temsil eden nesneleri. Bu, bağlantı noktası programlardır.  
  
 `rgpProgramNodes`  
 [in] Bir dizi [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) her program için bir program düğümleri temsil eden nesneleri. Bu dizi program düğümleri aynı programları olarak temsil eden `pProgram`. Böylece DE program eklemek için program düğümleri verilir.  
  
 `celtPrograms`  
 [in] Programlar ve/veya program düğümlerin sayısını `pProgram` ve `rgpProgramNodes` dizileri.  
  
 `pCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) SDM için hata ayıklama olayları göndermek için kullanılacak nesne.  
  
 `dwReason`  
 [in] Bir değer [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) bu programları ekleme nedenini belirten sabit listesi. Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa döndürür `S_OK`; Aksi takdirde bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir programa, aşağıdaki gibi ekleme için üç neden vardır:  
  
- `ATTACH_REASON_LAUNCH` Kullanıcı içerdiği işlemini başlattı çünkü DE programa ekleme gösterir.  
  
- `ATTACH_REASON_USER` kullanıcının bir program (veya program içeren işlem) eklemek için DE açıkça istediği gösterir.  
  
- `ATTACH_REASON_AUTO` belirli bir işlemde diğer programları zaten hata ayıklama için DE belirli bir programa ekleme gösterir. Bu da adlandırılır otomatik iliştirme.  
  
  Bu yöntem çağrıldığında, sırayla bu olayları göndermek DE gerekir:  
  
1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (Bunu zaten hata ayıklama altyapısı belirli bir örneği için gönderildiğini değil)  
  
2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
   Ayrıca ekleme nedeni, `ATTACH_REASON_LAUNCH`, göndermek DE gerekli [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) olay.  
  
   Bir kez DE alır [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , sorgulanabilen için herhangi bir özel arabirimi hata ayıklaması yapılan programa karşılık gelen nesne.  
  
   Tarafından verilen dizideki bir program düğümün yöntemleri çağrılmadan önce `pProgram` veya `rgpProgramNodes`, kimliğe bürünme, gerekirse etkinleştirilmelidir üzerinde `IDebugProgram2` program düğümünü temsil eden arabirim. Normalde, ancak bu adım gerekli değildir. Daha fazla bilgi için [güvenlik sorunları](../../../extensibility/debugger/security-issues.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)

