---
title: m_children alanı | Microsoft Docs
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
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f044c2dae278a0656f1f9e4c41a3940d87658a64
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731037"
---
# <a name="mchildren-field"></a>m_children Alanı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu göreve kaydedilmiş alt görevlerin listesi.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Bütünleştirilmiş kod:** mscorlib (mscorlib.dll içinde)  
  
 .NET Framework'den bu iç üye erişemediği için aşağıdaki söz dizimini ortak Ara dil (CIL) sağlanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Görev yürütülürken, görevi yürüten iş parçacığı bu dizinin erişmelidir.  
  
 Görev tamamlandıysa, bunlar olmayan herhangi bir şey eklemek veya herhangi bir şey kaldırın sürece diğer iş parçacıkları Bu alan erişebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ContingentProperties Sınıfı](../../extensibility/debugger/contingentproperties-class-internal-members.md)

