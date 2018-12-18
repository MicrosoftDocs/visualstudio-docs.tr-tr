---
title: Idebugasyncoperation arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugAsyncOperation interface
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 157ed1248535855fcb53ca2eb6f49427fea94149
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793985"
---
# <a name="idebugasyncoperation-interface"></a>IDebugAsyncOperation Arabirimi
Hata ayıklama işlemi Yöneticisi uygulayan `IDebugAsyncOperation` arabirimi. Bir dil altyapısı çağırır `IDebugApplication::CreateAsyncDebugOperation` bu arabirim için bir başvuru elde etmek için yöntemi. Dil Altyapısı'nı kullanan `IDebugAsyncOperation` zaman uyumlu hata ayıklama işlemi zaman uyumsuz erişim sağlamak için arabirim.  
  
 Kaynağından devralındı yöntemleri yanı sıra `IUnknown`, `IDebugAsyncOperation` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|Bu nesneyle ilişkili zaman uyumlu hata ayıklama işlemi döndürür.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|Başlamak zaman uyumsuz işlemi neden olur.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|Bir işlem iptal eder.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|Hata ayıklama işlemi tamamlanıp tamamlanmadığını belirler.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|Zaman uyumlu hata ayıklama işlemi dönüş nesnesi parametresinden ve dönüş değeri sağlar.|