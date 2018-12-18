---
title: 'CA1819: Özellikler diziler döndürmemelidir'
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 99fd9627c06b11dae9348a85f417cf152ac1c8c9
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859039"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: Özellikler diziler döndürmemelidir

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|Kategori|Microsoft.Performance|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep

Ortak türde ortak veya korumalı bir özellik, bir dizi döndürür.

## <a name="rule-description"></a>Kural açıklaması

Özellik salt okunur olsa bile özellikleri tarafından döndürülen dizi yazma korumalı değildir. Dizi değiştirilmeye kanıt tutulacak özellik dizisinin bir kopyasını döndürmelidir. Genellikle, kullanıcıların böyle bir özellik çağırma performansı olumsuz etkilerini anlamak olmaz. Özellikle, bunlar bir dizinlenmiş özellik olarak özelliğini kullanabilirsiniz.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Bu kural ihlalini düzeltmek için özelliği bir yöntem yapın veya özelliği bir koleksiyon döndürecek şekilde değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Türetilen bir özniteliğin bir özellik için oluşturulan bir uyarıyı bastırmak <xref:System.Attribute> sınıfı. Öznitelikler, dizi döndüren özellikler içerebilir, ancak koleksiyon döndüren özellikler içeremez.

Özelliğin parçası ise uyarıyı gözardı edebileceğini bir [veri aktarım nesnesini (DTO)](/previous-versions/msp-n-p/ff649585(v=pandp.10)) sınıfı.

Aksi takdirde, bu kuraldan bir uyarıyı bastırmayın.

## <a name="example-violation"></a>Örnek ihlali

Aşağıdaki örnek bu kuralı ihlal eden bir özellik gösterilmektedir:

[!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
[!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]

Bu kural ihlalini düzeltmek için özelliği bir yöntem yapın veya özelliği bir dizi yerine bir koleksiyon döndürecek şekilde değiştirin.

### <a name="change-the-property-to-a-method"></a>Özelliği bir yönteme değiştirme

Aşağıdaki örnek, bir yönteme özelliğini değiştirerek ihlali giderir:

[!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
[!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]

### <a name="change-the-property-to-return-a-collection"></a>Özelliği bir koleksiyon döndürecek şekilde değiştirin

Aşağıdaki örnek, döndürülecek özelliği değiştirilerek ihlali giderir bir <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>:

[!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
[!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]

## <a name="allow-users-to-modify-a-property"></a>Kullanıcıların bir özellik değiştirmesine izin ver

Bir özelliği değiştirmek tüketici sınıfı izin vermek isteyebilirsiniz. Aşağıdaki örnek bu kuralı ihlal eden bir okuma/yazma özelliği gösterir:

[!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
[!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]

Aşağıdaki örnek, döndürülecek özelliği değiştirilerek ihlali giderir bir <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>:

[!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
[!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]

## <a name="related-rules"></a>İlgili kuralları

- [CA1024: Uygun yerlerde özellikler kullanın](../code-quality/ca1024-use-properties-where-appropriate.md)