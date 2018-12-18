---
title: MSBuild özel karakterleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa1e52e61f4003a9495e1bff5bd64e4edc40a323
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078660"
---
# <a name="msbuild-special-characters"></a>MSBuild özel karakterleri
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] belirli bağlamlarda özel kullanım için bazı karakterler ayırır. Bunları tam anlamıyla ayrılmış oldukları bağlamda kullanmak istiyorsanız bu tür karakter kaçış yeterlidir. Örneğin, bir yıldız işareti yalnızca özel anlamı vardır `Include` ve `Exclude` öznitelikleri bir öğe tanımının ve yapılan çağrıda `CreateItem`. Bu bağlamı birinde bir yıldız işareti olarak görünmesi için bir yıldız işareti istiyorsanız, atlatmak gerekir. Diğer her bir bağlam içinde görünmesini istediğiniz yere yıldız yazmanız yeterlidir.  
  
 Bir özel karakter kaçış için söz dizimi % kullanın\<xx >, burada \<xx > karakter ASCII onaltılık değerini temsil eder. Daha fazla bilgi için [nasıl yapılır: MSBuild özel karakterleri kaçış](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## <a name="special-characters"></a>Özel karakterler  
 Aşağıdaki tabloda [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] özel karakterler:  
  
|**Karakter**|**ASCII**|**Ayrılmış kullanım**|  
|-------------------|---------------|------------------------|  
|%|%25|Meta veri başvurma|  
|$|%24|Başvuru özellikleri|  
|@|%40|Başvuru öğesi listeleri|  
|'|%27|Koşullar ve diğer ifadeler|  
|;|% 3B|Liste ayırıcı|  
|?|% 3F|Dosya adlarında joker karakter `Include` ve `Exclude` öznitelikleri|  
|*|%2A|Dosya adlarında kullanmak için joker karakter `Include` ve `Exclude` öznitelikleri|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)   
 [Öğeleri](../msbuild/msbuild-items.md)