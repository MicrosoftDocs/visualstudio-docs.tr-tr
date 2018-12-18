---
title: 'CA1051: görünür örnek alanlarını bildirmeyin | Microsoft Docs'
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
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 691f5fe87d775d2bff2fc15ff15ca8022478b3a2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910556"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: Görünür örnek alanlarını bildirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Dışarıdan görünen bir tür bir dışarıdan görünür örnek alanı vardır.

## <a name="rule-description"></a>Kural Tanımı
 Bir alanın birincil kullanım alanının uygulama ayrıntısı olması gerekir. Alanlar olmalıdır `private` veya `internal` ve özelliklerini kullanmaya maruz kalması. Bir alana erişmek olduğu ve özellikleri türünde bozucu değişiklikler oluşturmaksızın genişlettikçe özellik erişimcileri kodda değiştirebilirsiniz bir özelliğe erişmek oldukça kolaydır. Yalnızca özel veya iç alan değerini döndüren özellikler, bir alana erişim özellik gerçekleştirmek için optimize edilmiş; çok az performans kazancı özellikler üzerinde dışarıdan görünen alanları kullanımı ile ilişkilidir.

 Dışarıdan görünen başvurduğu `public`, `protected`, ve `protected internal` (`Public`, `Protected`, ve `Protected Friend` Visual Basic'te) erişilebilirlik düzeyleri.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için alanın olmasını `private` veya `internal` ve dışarıdan görünen bir özelliğini kullanarak üzerinden kullanıma sunacaksınız.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Dışarıdan görünen alanlar, özellikler için kullanılabilir olan herhangi bir avantaj sağlamaz. Ayrıca, ortak alanları tarafından korunamaz [bağlantı talepleri](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d). Bkz: [CA2112: güvenli türler alanları kullanıma](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir tür gösterir (`BadPublicInstanceFields`), bu kuralı ihlal ediyor. `GoodPublicInstanceFields` Düzeltilen kod gösterilmektedir.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesPublicInstanceFields/cs/FxCop.Design.TypesPublicInstanceFields.cs#1)]

## <a name="related-rules"></a>İlgili kuralları
 [CA2112: Güvenli türler alanları açığa çıkarmamalıdır](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Bağlantı talepleri](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)



