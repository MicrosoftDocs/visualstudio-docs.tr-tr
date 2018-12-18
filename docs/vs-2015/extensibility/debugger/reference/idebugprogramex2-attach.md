---
title: IDebugProgramEx2::Attach | Microsoft Docs
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
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea96fab360df7b23090ba93918a5bff60a31ea32
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751095"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Oturum, bir programa ekleyin.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pCallback`  
 [in] Bir [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) ekli hata ayıklama altyapısı için olaylar gönderir geri çağırma işlevini temsil eden nesne.  
  
 `dwReason`  
 [in] Bir değer [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) iliştirme işlemi nedenini açıklayan sabit listesi.  
  
 `pSession`  
 [in] Programa ekleme oturum benzersiz olarak tanımlayan bir değer.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa döndürür `S_OK`; Aksi takdirde bir hata kodu döndürür. Bu yöntem döndürmelidir `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` program zaten bağlıysa.  
  
## <a name="remarks"></a>Açıklamalar  
 Programı içeren bağlantı noktası değeri kullanabilirsiniz `pSession` oturum programa ekleme girişiminde belirlemek için. Örneğin, bir bağlantı noktası aynı anda bir işleme iliştirmek yalnızca bir hata ayıklama oturumu izin veriyorsa, bağlantı noktası işlemdeki diğer programlar için aynı oturum zaten eklenmiş olursa belirleyebilirsiniz.  
  
> [!NOTE]
>  Arabirim geçirilen `pSession` yalnızca bir tanımlama bilgisi, bu programa; ekleme oturum hata ayıklama Yöneticisi benzersiz olarak tanımlayan bir değer olarak değerlendirilmesi için sağlanan arabirim yöntemleri hiçbiri işlevsel değildir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)

