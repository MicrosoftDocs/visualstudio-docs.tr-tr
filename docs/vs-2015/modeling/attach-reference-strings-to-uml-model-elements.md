---
title: Başvuru dizelerini UML model öğelerine Ekle | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending, reference strings
ms.assetid: 15dbed99-efce-42fe-a768-714a5804e7d1
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7726379258ef474b57f1ca4a924413cd93cf80bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672786"
---
# <a name="attach-reference-strings-to-uml-model-elements"></a>Model öğelerine başvuru dizeleri ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Model öğelerine rastgele dizeler eklemek için kod yazabilirsiniz. Bir dize, örneğin bir URI, bir hesaplamanın önbelleğe alınmış sonucu veya başka bir modeldeki bir öğeye ModelBus başvurusu olabilir. Her dize bir IReference nesnesinde bulunur. Her bir model öğesine herhangi bir sayıda IReference nesnesi eklenebilir.

 Her IReference nesnesinin bir adı vardır. Bu adı, başvuru değerinin nasıl yorumlanması gerektiğini belirtmek için kullanabilirsiniz. Örneğin, değerin bir URI olarak yorumlanması gerektiğini belirtmek için adı "URI" olarak ayarlayabilirsiniz. Modelleme araçları tarafından kullanılan bazı önceden tanımlanmış başvuru adı değerleri vardır.

## <a name="attaching-a-reference-to-an-ielement"></a>Bir IElement başvurusu iliştirme
 Aşağıdaki yöntemleri kullanmak için bir başvuru eklemeniz gerekir:

 Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll

 Bu yönergeyi kodunuza eklemeniz gerekir:

 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`

|Yöntem çağrısı|Description|
|-----------------|-----------------|
|`element.AddReference (nameString, valueString, duplicatesAllowed)`|`IReference`Verilen ad ve değer dizelerini içeren bir oluşturur ve bunu öğesine bağlar `element` . Döndürür `IReference` .<br /><br /> Yanlışsa bir özel durum oluşturur `duplicatesAllowed` ve `IReference` aynı ada sahip bir adı zaten varsa `element` .|
|`element.GetReferences(name)`|`IReference`Verilen öğesine bağlı tüm nesneleri döndürür `element` `name` .|
|`element.DeleteAllReferences(name)`|`IReference`Verilen ada sahip olan öğeye bağlı tüm nesneleri siler.|
|`reference.Delete()`|Bunu siler `IReference` .|
|`ReferenceConstants.WorkItem`|Çalışma öğesi başvurularını adlandırmak için kullanılan değer.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Bir iş öğesi bağlantı Işleyicisini tanımlama](../modeling/define-a-work-item-link-handler.md) [UML API ile](../modeling/programming-with-the-uml-api.md) [modelleme uzantısı](../modeling/define-and-install-a-modeling-extension.md) programlama
