---
title: 'CA1021: Out parametrelerinden kaçının'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1082aaef3422923e0f74e8bd5eb242f3ae8e6023
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549501"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: Out parametrelerinden kaçının

|||
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak türde ortak veya korumalı bir yöntem olan bir `out` parametresi.

## <a name="rule-description"></a>Kural açıklaması
 Türleri başvuruya göre geçirme (kullanarak `out` veya `ref`) deneyimi işaretçilerle değer türleri ve başvuru türleri farkı anlama ve işleme yöntemi ile birden çok değer gerektirir. Ayrıca, arasındaki farkı `out` ve `ref` parametreleri anlaşılmadı.

 Bir başvuru türü "başvuruya göre" geçirildiğinde, parametre nesnesinin farklı bir örneğine geri dönmek için kullanılacak yöntemi amaçlamaktadır. Bir başvuru türü başvuruya göre geçirme çift işaretçisi, bir işaretçi veya çift yöneltme işaretçisi kullanılarak olarak da bilinir. Zaten bir başvuru türü alan bir parametre için varsayılan çağırma kuralı, "değeriyle" geçti kullanarak nesneye bir işaretçi alır. İşaretçi, işaret ettiği, nesnenin değil değere göre geçirilir. Değer yollarla yöntemi yeni bir başvuru türü örneğine işaret için işaretçiyi değiştiremezsiniz geçirin. Ancak, işaret ettiği nesnenin içeriğini değiştirebilirsiniz. Çoğu uygulama için bu yeterli olur ve istenen davranışı üretir.

 Bir yöntem başka bir örneği döndürmelidir, bunu gerçekleştirmek için yöntemin dönüş değerini kullanın. Bkz: <xref:System.String?displayProperty=fullName> sınıfı için çeşitli yöntemler dizeler üzerinde çalışan ve bir dize yeni bir örneğini döndürür. Bu modelde kullanıldığında, arayanın özgün nesneye korunup korunmayacağını karar vermeniz gerekir.

 Dönüş değerleri sıradan bir hale ve yoğun olarak kullanılan, doğru uygulama olsa da `out` ve `ref` Ara tasarım ve kodlama becerilerinde parametrelerine gereksinim duyar. Genel kitle asıl kullanıcılara beklememelidir bilgilendirmelidir tasarım Kütüphane mimarları `out` veya `ref` parametreleri.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bir değer türü tarafından neden bu kural ihlalini düzeltmek için yöntemin dönüş değeri olarak nesneyi döndürmek sahip. Yöntemi, birden çok değer döndürmelidir, tek bir örneği değerleri içeren nesneyi döndürmek için yeniden tasarlayın.

 Bir başvuru türüne göre neden bu kural ihlalini düzeltmek için istenen davranışı başvurusu yeni bir örneğini döndürülecek olduğundan emin olun. İse, bunu yapmak için yöntemin dönüş değerini kullanmanız gerekir.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Bu kuraldan bir uyarıyı bastırmak güvenlidir. Ancak, bu tasarım, kullanılabilirlik sorunları neden olabilir.

## <a name="example"></a>Örnek
 Aşağıdaki kitaplığı, bir kullanıcının geri bildirim yanıtlarını oluşturan bir sınıfın iki uygulamaları gösterir. İlk uygulama (`BadRefAndOut`) kitaplığı üç dönüş değerleri yönetme açmaya zorlar. İkinci uygulama (`RedesignedRefAndOut`) bir kapsayıcı sınıfının bir örneğini döndürerek kullanıcı deneyimini basitleştirir (`ReplyData`), verileri tek bir birim olarak yönetir.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama, kullanıcı deneyimini gösterir. Yeniden tasarlanan kitaplık çağrısı (`UseTheSimplifiedClass` yöntemi) daha basit ve yöntem tarafından döndürülen bilgileri kolayca yönetilebilir. İki yöntem çıkışı aynıdır.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek kitaplığı gösterir nasıl `ref` parametreleri başvuru türleri için kullanılır ve bu işlevselliği uygulamak için daha iyi bir yolunu gösterir.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama davranışını göstermek için kitaplıkta her yöntemini çağırır.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]

Bu örnek aşağıdaki çıktıyı üretir:

```txt
Changing pointer - passed by value:
12345
12345
Changing pointer - passed by reference:
12345
12345 ABCDE
Passing by return value:
12345 ABCDE
```

## <a name="try-pattern-methods"></a>Desen yöntemleri deneyin

### <a name="description"></a>Açıklama
 Uygulayan yöntemler **deneyin\<bir şey >** desen gibi <xref:System.Int32.TryParse%2A?displayProperty=fullName>, bu ihlali geçirmeyin. Uygulayan bir yapısı (değer türü) aşağıdaki örnekte <xref:System.Int32.TryParse%2A?displayProperty=fullName> yöntemi.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.TryPattern#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_5.cs)]

## <a name="related-rules"></a>İlgili kuralları
 [CA1045: Türleri başvuruya göre geçirmeyin](../code-quality/ca1045-do-not-pass-types-by-reference.md)