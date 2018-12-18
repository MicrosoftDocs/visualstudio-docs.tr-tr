---
title: 'CA1045: türleri başvuruya göre geçirmeyin | Microsoft Docs'
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
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1aa9077a0d27c105cd7008d550a4315ce8daf91a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836573"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: Türleri başvuruya göre geçirmeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPassTypesByReference|
|CheckId|CA1045|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak türde ortak veya korumalı bir yöntem olan bir `ref` ilkel tür, bir başvuru türü veya değer türü alan parametresi yerleşik türlerden biri değil.

## <a name="rule-description"></a>Kural Tanımı
 Türleri başvuruya göre geçirme (kullanarak `out` veya `ref`) değer türleri ve başvuru türleri farkı anlama ve işleme birden çok değer yöntemi işaretçileri deneyimiyle gerektirir. Ayrıca, arasındaki farkı `out` ve `ref` parametreleri anlaşılmadı.

 Bir başvuru türü "başvuruya göre" geçirildiğinde, parametre nesnesinin farklı bir örneğine geri dönmek için kullanılacak yöntemi amaçlamaktadır. (Bir başvuru türü başvuruya göre geçirme da çift işaretçisi, bir işaretçi veya çift yöneltme işaretçisi kullanılarak olarak bilinir.) Zaten bir başvuru türü alan bir parametre için varsayılan çağırma kuralı, "değeriyle" geçti kullanarak nesneye bir işaretçi alır. İşaretçi, işaret ettiği, nesnenin değil değere göre geçirilir. Yöntemi, işaretçi, başvuru yeni bir örneğine işaret edecek şekilde değiştiremezsiniz anlamına gelir yazın, ancak işaret ettiği nesnenin içeriğini değiştirebilirsiniz değere göre geçirme. Çoğu uygulama için bu yeterli olur ve istediğiniz davranışı üretir.

 Bir yöntem başka bir örneği döndürmelidir, bunu gerçekleştirmek için yöntemin dönüş değerini kullanın. Bkz: <xref:System.String?displayProperty=fullName> sınıfı için çeşitli yöntemler dizeler üzerinde çalışan ve bir dize yeni bir örneğini döndürür. Bu modeli kullanarak, özgün nesneye korunup korunmayacağını karar arayana bırakılır.

 Dönüş değerleri sıradan bir hale ve yoğun olarak kullanılan, doğru uygulama olsa da `out` ve `ref` Ara tasarım ve kodlama becerilerinde parametrelerine gereksinim duyar. Genel kitle asıl kullanıcılara beklememelidir bilgilendirmelidir tasarım Kütüphane mimarları `out` veya `ref` parametreleri.

> [!NOTE]
>  Büyük yapılar olan parametreler ile çalışırken, değere göre geçirdiğinizde bu yapıları kopyalamak için gereken ek kaynakları bir performans etkisi neden olabilir. Bu gibi durumlarda kullanmayı düşünebilirsiniz `ref` veya `out` parametreleri.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bir değer türü tarafından neden bu kural ihlalini düzeltmek için yöntemin dönüş değeri olarak nesneyi döndürmek sahip. Yöntemi, birden çok değer döndürmelidir, tek bir örneği değerleri içeren nesneyi döndürmek için yeniden tasarlayın.

 Bir başvuru türüne göre neden bu kural ihlalini düzeltmek için istediğiniz davranışı başvurusu yeni bir örneğini döndürülecek olduğundan emin olun. İse, bunu yapmak için yöntemin dönüş değerini kullanmanız gerekir.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı bastırmak güvenlidir; Ancak, bu tasarım, kullanılabilirlik sorunları neden olabilir.

## <a name="example"></a>Örnek
 Aşağıdaki Kitaplık kullanıcının geri bildirim yanıtlarını oluşturan bir sınıfın iki uygulamaları gösterir. İlk uygulama (`BadRefAndOut`) kitaplığı üç dönüş değerleri yönetme açmaya zorlar. İkinci uygulama (`RedesignedRefAndOut`) bir kapsayıcı sınıfının bir örneğini döndürerek kullanıcı deneyimini basitleştirir (`ReplyData`), verileri tek bir birim olarak yönetir.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama, kullanıcı deneyimini gösterir. Yeniden tasarlanan kitaplık çağrısı (`UseTheSimplifiedClass` yöntemi) daha basit ve yöntem tarafından döndürülen bilgileri kolayca yönetilebilir. İki yöntem çıkışı aynıdır.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek kitaplığı gösterir nasıl `ref` parametreleri başvuru türleri için kullanılır ve bu işlevselliği uygulamak için daha iyi bir yolunu gösterir.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama davranışını göstermek için kitaplıkta her yöntemini çağırır.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **Değiştirme işaretçi - geçirilen değere göre:**
**12345**
**12345**
**değiştirme işaretçi, başvuru tarafından geçirilmediğine -:** 
 ** 12345**
**12345 ABCDE**
**dönüş değere göre geçirme:**
**12345 ABCDE**
## <a name="related-rules"></a>İlgili kuralları
 [CA1021: Out parametrelerinden kaçının](../code-quality/ca1021-avoid-out-parameters.md)



