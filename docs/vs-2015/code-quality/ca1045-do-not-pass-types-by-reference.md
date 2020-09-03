---
title: 'CA1045: türleri başvuruya göre geçirmeyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dad2f90a51a4247a4c111ef51e85a28ba1a118ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548479"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: Türleri başvuru olarak geçmeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DoNotPassTypesByReference|
|CheckId|CA1045|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Ortak türde ortak veya korumalı bir yöntem `ref` , temel bir tür, bir başvuru türü veya yerleşik türlerden biri olmayan bir değer türü alan bir parametreye sahiptir.

## <a name="rule-description"></a>Kural Tanımı
 Türlerin başvuruya göre geçirilmesi ( `out` veya kullanılarak `ref` ) işaretçilerle deneyim gerektirir, değer türlerinin ve başvuru türlerinin nasıl farklı olduğunu ve birden çok dönüş değeri olan yöntemleri işleme. Ayrıca, `out` ve parametreleri arasındaki fark `ref` yaygın olarak anlaşılmaz.

 Başvuru türü "başvuruya göre" geçirildiğinde, yöntemi nesnenin farklı bir örneğini döndürmek için parametresini kullanmayı amaçladığı. (Başvuru türü başvuruya göre geçirilmesi, çift işaretçi, işaretçi işaretçisi veya çift yöneltme kullanma olarak da bilinir.) "Değere göre" değeri geçen varsayılan çağırma kuralını kullanma, başvuru türü alan bir parametre zaten nesneye bir işaretçi alır. İşaret ettiği nesne değil, işaretçi değere göre geçirilir. Değere göre geçirme yöntemi, yöntemin, başvuru türünün yeni bir örneğini işaret eden işaretçiyi değiştiremeyeceği, ancak gösterdiği nesnenin içeriğini değiştiremeyeceği anlamına gelir. Çoğu uygulama için bu yeterlidir ve istediğiniz davranışı verir.

 Bir yöntemin farklı bir örnek döndürmesi gerekiyorsa, bunu gerçekleştirmek için yönteminin dönüş değerini kullanın. <xref:System.String?displayProperty=fullName>Dizeler üzerinde çalışan ve bir dizenin yeni bir örneğini döndüren çeşitli yöntemler için sınıfına bakın. Bu modeli kullanarak, özgün nesnenin korunup korunmayacağına karar vermek için çağrı yapana bırakılır.

 Dönüş değerleri çok fazla ve yoğun olarak kullanıldığından, `out` ve parametrelerinin doğru uygulaması `ref` Ara tasarım ve kodlama becerileri gerektirir. Genel bir hedef kitle için tasarlayan kitaplık mimarları, kullanıcıların, veya parametreleriyle birlikte çalışmasını beklememelidir `out` `ref` .

> [!NOTE]
> Büyük yapıları olan parametrelerle çalışırken, bu yapıları kopyalamak için gereken ek kaynaklar, değere göre geçirdiğinizde bir performans etkisine neden olabilir. Bu durumlarda, `ref` veya parametrelerini kullanmayı düşünebilirsiniz `out` .

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın bir değer türünden kaynaklanan ihlalini onarmak için, yönteminin dönüş değeri olarak nesneyi döndürmesini sağlayabilirsiniz. Yöntemin birden çok değer döndürmesi gerekiyorsa, değerleri tutan bir nesnenin tek bir örneğini döndürecek şekilde yeniden tasarlayamalıdır.

 Bir başvuru türü nedeniyle oluşan bu kuralın ihlalini onarmak için, istediğiniz davranışın başvurunun yeni bir örneğini döndürtiğine emin olun. Eğer ise, yöntemi bunu yapmak için dönüş değerini kullanmalıdır.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı gizlemek güvenlidir; Ancak, bu tasarım kullanılabilirlik sorunlarına neden olabilir.

## <a name="example"></a>Örnek
 Aşağıdaki kitaplıkta, kullanıcının geri bildirimlerine yanıtlar üreten bir sınıfın iki uygulaması gösterilmektedir. İlk uygulama ( `BadRefAndOut` ), kitaplık kullanıcısını üç dönüş değerini yönetmeye zorlar. İkinci uygulama ( `RedesignedRefAndOut` ), `ReplyData` verileri tek bir birim olarak yöneten bir kapsayıcı sınıfının () örneğini döndürerek Kullanıcı deneyimini basitleştirir.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama, kullanıcının deneyimini gösterir. Yeniden tasarlanan kitaplığa ( `UseTheSimplifiedClass` Yöntem) yapılan çağrı daha basittir ve yöntemi tarafından döndürülen bilgiler kolayca yönetilir. İki yöntemden oluşan çıkış aynı.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek kitaplık `ref` , başvuru türleri parametrelerinin nasıl kullanıldığını gösterir ve bu işlevselliği uygulamak için daha iyi bir yol gösterir.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama, davranışı göstermek için kitaplıktaki her yöntemi çağırır.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **Işaretçi değiştirme-değere göre geçti:** 
 **12345** 
 **12345** 
 **Işaretçi değiştirme-başvuruya göre geçti:** 
 **12345** 
 **12345 ABCDE** 
 **Dönüş değerine göre geçirme:** 
 **12345 ABCDE**
## <a name="related-rules"></a>İlgili kurallar
 [CA1021: out parametrelerinden kaçının](../code-quality/ca1021-avoid-out-parameters.md)
