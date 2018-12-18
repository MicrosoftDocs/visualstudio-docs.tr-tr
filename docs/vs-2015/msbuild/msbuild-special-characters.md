---
title: MSBuild özel karakterleri | Microsoft Docs
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
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c9ce1697f370ec1beec8ce12faceb15825fbe5f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256457"
---
# <a name="msbuild-special-characters"></a>MSBuild Özel Karakterleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] belirli bağlamlarda özel kullanım için bazı karakterler ayırır. Bunları tam anlamıyla ayrılmış oldukları bağlamda kullanmak istiyorsanız bu tür karakter kaçış yeterlidir. Örneğin, bir yıldız işareti yalnızca özel anlamı vardır `Include` ve `Exclude` öznitelikleri bir öğe tanımının ve yapılan çağrıda `CreateItem`. Bu bağlamı birinde bir yıldız işareti olarak görünmesi için bir yıldız işareti istiyorsanız, atlatmak gerekir. Diğer her bir bağlam içinde görünmesini istediğiniz yere yıldız yazmanız yeterlidir.  
  
 Bir özel karakter kaçış için söz dizimi % kullanın*xx*burada *xx* karakter ASCII onaltılık değerini temsil eder. Daha fazla bilgi için [nasıl yapılır: MSBuild kaçış özel karakterleri](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## <a name="special-characters"></a>Özel Karakterler  
 Aşağıdaki tabloda [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] özel karakterler:  
  
|**Karakter**|**ASCII**|**Ayrılmış kullanım**|  
|-------------------|---------------|------------------------|  
|%|%25|Meta veri başvurma|  
|$|%24|Başvuru özellikleri|  
|@|%40|Başvuru öğesi listeleri|  
|'|%27|Koşullar ve diğer ifadeler|  
|;|% 3B|Liste ayırıcı|  
|?|% 3F|Dosya adlarında joker karakter `Include` ve `Exclude` öznitelikleri|  
|*|%2A|Dosya adlarında kullanmak için joker karakter `Include` ve `Exclude` öznitelikleri|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)   
 [Öğeler](../msbuild/msbuild-items.md)



