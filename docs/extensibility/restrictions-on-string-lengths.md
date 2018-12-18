---
title: Dize uzunluğu kısıtlamaları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b3552a88f5a78b627e72e877758cf6b7d12de95
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638540"
---
# <a name="restrictions-on-string-lengths"></a>Dize uzunluğu kısıtlamaları
Kaynak Denetimi Eklentisi API çeşitli işlevler için kullanılan dizelerin uzunluklarının sınırlar.  
  
## <a name="string-length-values"></a>Dize uzunluğu değerleri  
  
|Sabit|Değer|  
|--------------|-----------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  Uzunluğu sonlandırma içermez `null`. Bir "_LEN" yerine "_boyut" soneki ile diğer sabitleri sonlandırmak için boşluk `null`.  
  
|Sabit|Değer|  
|--------------|-----------|  
|SCC_NAME_SIZE|32|  
|SCC_AUXLABEL_SIZE|32|  
|SCC_USER_SIZE|32|  
|SCC_PRJPATH_SIZE|301|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)