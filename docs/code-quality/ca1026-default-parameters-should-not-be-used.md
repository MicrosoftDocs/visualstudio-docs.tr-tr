---
title: 'CA1026: Varsayılan parametreler kullanılmamalıdır'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec4a248be45489eafcbd208329a52cfc06d8237f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825360"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: Varsayılan parametreler kullanılmamalıdır

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Dışarıdan görünen bir tür kullanan bir varsayılan parametresi dışarıdan görünen bir yöntem içerir.

## <a name="rule-description"></a>Kural açıklaması
 Varsayılan parametreleri kullanan yöntemler, ortak dil belirtimi (CLS) altında izin verilir; Ancak, CLS derleyicileri Bu parametreler için atanmış değerleri yok saymasını sağlar. Varsayılan parametre değerlerini yoksay derleyicileri için yazılan kod her varsayılan parametresi için bağımsız değişkenleri açıkça belirtmeniz gerekir. Programlama dilleri arasında istediğiniz davranışı korumak için varsayılan parametreleri kullanan yöntemler varsayılan parametreleri sağlayan yöntem aşırı yüklemeleri ile değiştirilmelidir.

 Yönetilen kod eriştiğinde derleyici C++ için yönetilen uzantısı için varsayılan parametre değerlerini yoksayar. Visual Basic Derleyicisi kullanan varsayılan parametreleri olan yöntemleri destekler [isteğe bağlı](/dotnet/visual-basic/language-reference/modifiers/optional) anahtar sözcüğü.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için varsayılan parametreleri tedarik yöntemi aşırı yüklemeleri ile varsayılan parametreleri kullanan yöntemi değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, varsayılan parametreleri kullanan bir yöntem ve eşdeğer bir işlevselliği sağlayan bir aşırı yüklenmiş yöntemler gösterilmektedir.

 [!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]

## <a name="related-rules"></a>İlgili kuralları
 [CA1025: Tekrarlanan bağımsız değişkenleri params dizisi ile değiştirin](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Ayrıca bkz.
 [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](/dotnet/standard/language-independence-and-language-independent-components)