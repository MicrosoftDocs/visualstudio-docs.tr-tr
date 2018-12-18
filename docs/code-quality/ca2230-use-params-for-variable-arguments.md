---
title: 'CA2230: Değişken bağımsız değişkenler için params kullanın'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e8139153be130ef05c150bd9d96d4298554c1269
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866720"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Değişken bağımsız değişkenler için params kullanın

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak veya korumalı tür kullanan bir ortak veya korumalı yöntem içerir `VarArgs` çağırma kuralı.

## <a name="rule-description"></a>Kural açıklaması
 `VarArgs` Çağırma kuralı değişik sayıda parametreyi almayan belirli yöntemi tanımları ile kullanılır. Yöntemini kullanarak `VarArgs` çağırma kuralı, ortak dil belirtimi (CLS) uyumlu değil ve programlama dillerini erişilebilir olmayabilir.

 C# ' ta, `VarArgs` çağırma kuralı kullanılan bir yöntemin parametre listesi ile sona erdiğinde `__arglist` anahtar sözcüğü. Visual Basic desteklemiyor `VarArgs` elipsin kullanan yönetilmeyen kod içinde sağlayan kullanımı çağırma kuralı ve Visual C++ `...` gösterimi.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 C# ' de bu kural ihlalini düzeltmek için kullanın [params](/dotnet/csharp/language-reference/keywords/params) anahtar sözcüğü yerine `__arglist`.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, iki yöntem, kural ihlal eden diğeri kural karşılayan gösterir.

 [!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.CallingConventions?displayProperty=fullName>
- [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](/dotnet/standard/language-independence-and-language-independent-components)