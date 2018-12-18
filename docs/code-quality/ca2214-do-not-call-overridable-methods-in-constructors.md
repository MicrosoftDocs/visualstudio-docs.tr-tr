---
title: 'CA2214: Geçersiz kılınabilir yöntemleri oluşturucular içinde çağırmayın'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ddc827e77b37de6490cb4bee081748f317865b57
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549566"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Geçersiz kılınabilir yöntemleri oluşturucular içinde çağırmayın

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep

Mühürlenmemiş bir tür Oluşturucu, sınıfta tanımlanan sanal bir yöntemi çağırır.

## <a name="rule-description"></a>Kural açıklaması

Sanal bir yöntem çağrıldığında yöntem gerçek tür çalışma zamanına kadar seçilmedi. Bir kurucu sanal bir yöntemi çağırdığında, yapıcı yöntemini çağıran örneği için değil yürütüldü mümkündür.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Bu kural ihlalini düzeltmek için türün sanal yöntemleri türün oluşturucular içinde çağırmayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Bu kuraldan uyarıyı bastırmayın. Sanal yöntem çağrısı ortadan kaldırmak için oluşturucu yeniden tasarlanması gerekir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bu kuralın ihlali etkisini gösterir. Test uygulama örneği oluşturur `DerivedType`, onun temel sınıfından neden olur (`BadlyConstructedType`) yürütmek için oluşturucu. `BadlyConstructedType`ın Oluşturucusu yanlış sanal yöntemini çağırır `DoSomething`. Çıktıda gösterildiği gibi `DerivedType.DoSomething()` yürütür ve bu nedenle önce yapar `DerivedType`'s Oluşturucusu yürütür.

[!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
[!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

Bu örnek aşağıdaki çıktıyı üretir:

```txt
Calling base ctor.
Derived DoSomething is called - initialized ? No
Calling derived ctor.
```