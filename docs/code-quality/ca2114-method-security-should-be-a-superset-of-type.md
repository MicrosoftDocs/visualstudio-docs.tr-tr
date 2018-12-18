---
title: 'CA2114: Yöntem güvenliği türün bir üst kümesi olmalıdır'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66fe0031380139c55942a1a47f71066a327d5e24
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551434"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: Yöntem güvenliği türün bir üst kümesi olmalıdır

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bildirim temelli güvenlik türünde yöntemlerinden birine sahip aynı güvenlik eylemi için bildirime dayalı güvenlik ve güvenlik eylem [bağlantı talepleri](/dotnet/framework/misc/link-demands), ve türüne göre kullanıma izinleri izinler kümesini değildir. yöntem tarafından iade.

## <a name="rule-description"></a>Kural açıklaması
 Hem yöntem düzeyine hem de tür düzeyine bir bildirim temelli güvenlik aynı eylem için bir yöntem olmamalıdır. İki denetimleri birleştirilmez; yöntem düzeyi isteğe uygulanır. Örneğin, bir tür izin talep ederse `X`, ve yöntemlerinden birini talepleri izni `Y`, kod izni yok `X` metodunu yürütmek için.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Her iki eylem gerekli olduğundan emin olmak için kodunuzu gözden geçirin. Her iki eylem gerekiyorsa, yöntem düzeyi eylem tür düzeyindeki güvenlik içerdiğinden emin olun. Örneğin türüne izin talep ederse `X`, ve onun yöntemi de izin talep gerekir `Y`, yöntemi açıkça talep `X` ve `Y`.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Yöntem türü tarafından belirtilen güvenliği gerektirmiyorsa, bu kuraldan bir uyarıyı bastırmak güvenlidir. Ancak, sıradan bir senaryo değildir ve dikkatli bir tasarım incelemesi için bir gereksinimi olduğunu gösteriyor olabilir.

## <a name="example-1"></a>Örnek 1

Aşağıdaki örnek, bu kuralın ihlali tehlikeleri göstermek için ortam izinleri kullanır. Bu örnekte, uygulama kodu türü tarafından gerekli izni reddetme önce güvenli türün bir örneğini oluşturur. Tehdit gerçek dünya senaryosunda, uygulama nesnesinin bir örneği elde etmek için başka bir yolu olması gerekir.

Aşağıdaki örnekte, kitaplık taleplerini yazma izni bir tür için ve bir yöntem için okuma izni.

[!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]

## <a name="example-2"></a>Örnek 2

Aşağıdaki uygulama kodu, güvenlik gereksinimleri karşılamıyor olsa bile yöntemi çağırarak Kitaplığı'nın güvenlik açığı gösterir.

[!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]

Bu örnek aşağıdaki çıktıyı üretir:

```txt
[All permissions] Personal information: 6/16/1964 12:00:00 AM
[No write permission (demanded by type)] Personal information: 6/16/1964 12:00:00 AM
[No read permission (demanded by method)] Could not access personal information: Request failed.
```

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](/dotnet/standard/security/secure-coding-guidelines)
- [Bağlantı talepleri](/dotnet/framework/misc/link-demands)
- [Veri ve Modelleme](/dotnet/framework/data/index)