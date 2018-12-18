---
title: 'CA1720: Tanımlayıcılar tür adları içermemelidir | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ec0980d312d4a65a770e63f0a23203a7e95c546f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862345"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Tanımlayıcılar tür adları içermemelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Kategori|Microsoft.Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Dışarıdan görünen üye bir parametre adını veri türü adı içerir.

 veya

 Açıkça görünen üyenin adı dil özellikli veri türü adı içerir.

## <a name="rule-description"></a>Kural Tanımı
 Parametreleri ve üyelerin adları, daha iyi geliştirme araçları tarafından sağlanan bekleniyor, türü tanımlamak üzere daha anlamları iletişim kurmak için kullanılır. Bir veri türü adı kullanılmalıdır, üyelerinin adları için dile özgü bir yerine dilden bağımsız bir ad kullanın. Örneğin, C# türü adı 'int yerine', verileri dilden bağımsız tür adı, Int32 kullanın.

 Parametre ya da üye adını ayrık her belirteç aşağıdaki dile bağlı veri türü adları karşı duyarlı bir şekilde denetlenir:

- bool

- WChar

- Int8

- UInt8

- kısa

- UShort

- int

- UInt

- Tamsayı

- Uınteger

- uzun

- ULong

- İşaretsiz

- İmzalı

- kayan nokta

- float32

- float64

  Ayrıca, bir parametre adlarını büyük küçük harf duyarlı bir şekilde de aşağıdaki dilden bağımsız veri türü adları karşı denetlenir:

- Nesne

- obj

- Boole değeri

- Char

- Dize

- SByte

- Bayt

- UByte

- Int16

- UInt16

- Int32

- UInt32

- Int64

- UInt64

- IntPtr

- PTR

- İşaretçi

- UInptr

- UPtr

- UPointer

- Tek

- Çift

- Ondalık

- Guid

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 **Bir parametre karşı harekete varsa:**

 Parametre adını veri türü tanımlayıcısı, daha iyi anlamını açıklayan bir terim ya da 'value' gibi daha genel bir terim ile değiştirin.

 **Üye karşı harekete varsa:**

 Bunun anlamı, bir dil bağımsız eşdeğeriyle ya da 'value' gibi daha genel bir terim daha iyi açıklayan bir terim ile dile bağlı veri türü tanımlayıcısı ' üye adını değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Parametre ve üye adları türüne göre ara sıra kullanılmasını uygun olabilir. Ancak, hiçbir bilinen yeni geliştirme için senaryolar ortaya burada bu kuraldan bir uyarıyı bastırmak. Önceki sevk sahip kitaplıkları için bu kuraldan bir uyarıyı bastırmak olabilir.

## <a name="related-rules"></a>İlgili kuralları
 [CA1709: Tanımlayıcıların büyük/küçük harfleri doğru yazılmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Tanımlayıcılar örnekten daha fazla farklı olmalıdır](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Tanımlayıcılar alt çizgi içermemelidir](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719: Parametre adları üye adlarıyla eşleşmemelidir](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)



