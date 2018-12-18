---
title: IDebugProgram3::ExecuteOnThread | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4e183d9d55c8527cdead0d7108c12ac3fd527e94
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788634"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Hata ayıklayıcı programın yürütür. İş parçacığı üzerinde hangi iş parçacığının kullanıcı program çalıştırılırken görüntüleyen hata ayıklayıcı bilgiler vermemiz döndürülür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```csharp  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pThread`  
 [in] Bir [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesne.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa döndürür `S_OK`; Aksi takdirde bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir hata ayıklayıcı durduruluyor sonra yürütmeye devam edebilir üç farklı yolu vardır:  
  
- Yürütün: herhangi bir önceki adımı iptal etmek ve vb. sonraki kesme noktasına kadar çalıştırın.  
  
- Adım: eski herhangi bir adımı iptal edin ve yeni adım tamamlanana kadar çalıştırın.  
  
- Devam Et: yeniden çalıştırın ve herhangi bir eski adımı etkin bırakın.  
  
  İş parçacığı geçirilen `ExecuteOnThread` hangi iptal etmek için kullanmak adımda saptarken yararlı olur. Tüm adımları Yürüt çalışan iş parçacığı, bilmiyorsanız, iptal eder. İş parçacığı bilgiyle etkin iş parçacığı üzerinde adımı iptal etmek yeterlidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yürütme](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)

