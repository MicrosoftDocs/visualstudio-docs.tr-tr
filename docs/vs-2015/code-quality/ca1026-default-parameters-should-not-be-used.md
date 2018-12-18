---
title: 'CA1026: Varsayılan parametreler kullanılmamalıdır | Microsoft Docs'
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
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5ab5fd842363c39f23981bdec93635974e2b2582
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894371"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: Varsayılan parametreler kullanılmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Dışarıdan görünen bir tür kullanan bir varsayılan parametresi dışarıdan görünen bir yöntem içerir.

## <a name="rule-description"></a>Kural Tanımı
 Varsayılan parametreleri kullanan yöntemler, ortak dil belirtimi (CLS) altında izin verilir; Ancak, CLS derleyicileri Bu parametreler için atanmış değerleri yok saymasını sağlar. Varsayılan parametre değerlerini yoksay derleyicileri için yazılan kod her varsayılan parametresi için bağımsız değişkenleri açıkça belirtmeniz gerekir. Programlama dilleri arasında istediğiniz davranışı korumak için varsayılan parametreleri kullanan yöntemler varsayılan parametreleri sağlayan yöntem aşırı yüklemeleri ile değiştirilmelidir.

 Yönetilen kod eriştiğinde derleyici C++ için yönetilen uzantısı için varsayılan parametre değerlerini yoksayar. Visual Basic Derleyicisi kullanan varsayılan parametreleri olan yöntemleri destekler [isteğe bağlı](http://msdn.microsoft.com/library/4571ce88-a539-4115-b230-54eb277c6aa7) anahtar sözcüğü.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için varsayılan parametreleri tedarik yöntemi aşırı yüklemeleri ile varsayılan parametreleri kullanan yöntemi değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, varsayılan parametreleri kullanan bir yöntem ve eşdeğer bir işlevselliği sağlayan bir aşırı yüklenmiş yöntemler gösterilmektedir.

 [!code-vb[FxCop.Design.DefaultParameters#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DefaultParameters/vb/FxCop.Design.DefaultParameters.vb#1)]

## <a name="related-rules"></a>İlgili kuralları
 [CA1025: Tekrarlanan bağımsız değişkenleri params dizisi ile değiştirin](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)



