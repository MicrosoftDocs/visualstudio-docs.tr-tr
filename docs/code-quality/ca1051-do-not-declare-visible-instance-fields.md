---
title: 'CA1051: Görünür örnek alanlarını bildirme'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f907b1d8626e8babc88137ed70cf6330386ab92a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832205"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: Görünür örnek alanlarını bildirme

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Dışarıdan görünen bir tür bir dışarıdan görünür örnek alanı vardır.

## <a name="rule-description"></a>Kural açıklaması
 Bir alanın birincil kullanım alanının uygulama ayrıntısı olması gerekir. Alanlar olmalıdır `private` veya `internal` ve özelliklerini kullanmaya maruz kalması. Bir alana erişmek olduğu ve özellikleri türünde bozucu değişiklikler oluşturmaksızın genişlettikçe özellik erişimcileri kodda değiştirebilirsiniz bir özelliğe erişmek oldukça kolaydır. Yalnızca özel veya iç alan değerini döndüren özellikler, bir alana erişim özellik gerçekleştirmek için optimize edilmiş; çok az performans kazancı özellikler üzerinde dışarıdan görünen alanları kullanımı ile ilişkilidir.

 Dışarıdan görünen başvurduğu `public`, `protected`, ve `protected internal` (`Public`, `Protected`, ve `Protected Friend` Visual Basic'te) erişilebilirlik düzeyleri.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için alanın olmasını `private` veya `internal` ve dışarıdan görünen bir özelliğini kullanarak üzerinden kullanıma sunacaksınız.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Dışarıdan görünen alanlar, özellikler için kullanılabilir olan herhangi bir avantaj sağlamaz. Ayrıca, ortak alanları tarafından korunamaz [bağlantı talepleri](/dotnet/framework/misc/link-demands). Bkz: [CA2112: güvenli türler alanları kullanıma](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir tür gösterir (`BadPublicInstanceFields`), bu kuralı ihlal ediyor. `GoodPublicInstanceFields` Düzeltilen kod gösterilmektedir.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>İlgili kuralları
 [CA2112: Güvenli türler alanları açığa çıkarmamalıdır](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Ayrıca bkz.
 [Bağlantı talepleri](/dotnet/framework/misc/link-demands)