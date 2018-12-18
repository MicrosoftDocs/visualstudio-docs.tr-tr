---
title: Model öğelerine başvuru dizelerini iliştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, reference strings
ms.assetid: 15dbed99-efce-42fe-a768-714a5804e7d1
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: cf8a9e7e023e9c75f61fdf9a6bfb608edc3a7123
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51804592"
---
# <a name="attach-reference-strings-to-uml-model-elements"></a>Model öğelerine başvuru dizeleri ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Model öğelerine rastgele dize eklemek için kod yazabilirsiniz. Bir dize, örneğin, bir URI, bir hesaplama veya başka bir modelinde bir öğedeki ModelBus başvurusu önbelleğe alınan sonucu olabilir. Her bir dizenin IReference nesnesi içinde yer alır. Herhangi bir sayıda IReference nesneleri her model öğesine bağlı olmalıdır.  
  
 Her IReference nesne bir adı vardır. Bu ad, başvuru değeri nasıl yorumlanması gerektiğini belirtmek için kullanabilirsiniz. Örneğin, adı "URI" değeri olarak bir URI yorumlanması gerektiğini belirtmek için ayarlayabilirsiniz. Modelleme Araçları tarafından kullanılan bazı önceden tanımlı başvuru adı değerleri vardır.  
  
## <a name="attaching-a-reference-to-an-ielement"></a>Bir IElement başvuru ekleme  
 Aşağıdaki yöntemleri kullanmak için bir başvuru eklemeniz gerekir:  
  
 Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll  
  
 Kodunuzda bu yönergesi eklemeniz gerekir:  
  
 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`  
  
|Yöntem çağrısı|Açıklama|  
|-----------------|-----------------|  
|`element.AddReference (nameString, valueString, duplicatesAllowed)`|Oluşturur bir `IReference` verilen ad ve değer dizeleri ve bağlantı `element`. Döndürür `IReference`.<br /><br /> Bir özel durum oluşturur `duplicatesAllowed` false olduğundan ve zaten var. bir `IReference` bağlı aynı ada sahip `element`.|  
|`element.GetReferences(name)`|Tüm döndürür `IReference` bağlı nesneler `element` olan belirli `name`.|  
|`element.DeleteAllReferences(name)`|Tüm siler `IReference` nesneleri belirtilen ada sahip bir öğeye bağlı.|  
|`reference.Delete()`|Bu siler `IReference`.|  
|`ReferenceConstants.WorkItem`|Ad çalışma öğesi başvuruları için kullanılan değer.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir iş öğesi bağlantı işleyicisini tanımlama](../modeling/define-a-work-item-link-handler.md)   
 [Modelleme Uzantısı Tanımlama ve yükleme](../modeling/define-and-install-a-modeling-extension.md)   
 [UML API ile programlama](../modeling/programming-with-the-uml-api.md)



