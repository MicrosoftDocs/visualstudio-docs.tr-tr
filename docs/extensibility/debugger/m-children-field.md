---
title: m_children alanı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e27704484e5cfb320c8b65432fb3efb283054019
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231154"
---
# <a name="mchildren-field"></a>m_children alanı
Bu göreve kaydedilmiş alt görevlerin listesi.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Bütünleştirilmiş kod:** mscorlib (içinde *mscorlib.dll*)  
  
 .NET Framework'den bu iç üye erişemediği için aşağıdaki söz dizimini ortak Ara dil (CIL) sağlanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp 
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Görev yürütülürken, görevi yürüten iş parçacığı bu dizinin erişmelidir.  
  
 Görev tamamlandıysa, diğer iş parçacıkları yoksa hiçbir şey eklemenize veya herhangi bir şey kaldırın sürece bu alan erişebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ContingentProperties sınıfı](../../extensibility/debugger/contingentproperties-class-internal-members.md)