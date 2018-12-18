---
title: 'CA2105: Dizi alanları salt okunur yok | Microsoft Docs'
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
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 51878d18deb56c77ebbef0d0aa84b399ef2fa722
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894982"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: Dizi alanları salt okunur olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bir dizi içeren bir ortak veya korumalı alan salt okunur bildirilir.

## <a name="rule-description"></a>Kural Tanımı
 Uyguladığınızda `readonly` (`ReadOnly` içinde [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) alan bir dizi içeren alana değiştiricisi, farklı bir dizi olarak başvurmak için değiştirilemez. Bir dizinin öğeleri salt okunur bir alanda depolanmış olsa bile değiştirilebilir. Açıklardan güvenlik açığı kararları veya genel olarak erişilebilen bir salt okunur dizi öğeleri üzerinde temel işlemleri gerçekleştiren kod içerebilir.

 Ortak alan sahip de tasarım kuralı ihlal Not [CA1051: görünür örnek alanlarını bildirmeyin](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural tarafından belirlenen güvenlik açığını gidermek için genel olarak erişilebilen bir salt okunur dizi içeriğine güvenmeyin. Aşağıdaki yordamlardan birini kullanmanız önerilir:

- Dizi değiştirilemez bir türü kesin belirlenmiş koleksiyon ile değiştirin. Daha fazla bilgi için bkz. <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

- Genel alanı özel dizinin bir kopyasını döndüren bir yöntem ile değiştirin. Kodunuzu kopyada kullanmayan olduğundan tehlike öğeleri değiştirdiyseniz.

  İkinci yaklaşım seçerseniz, alana sahip bir özellik değiştirmeyin; olumsuz dizi döndüren özellikler, performansı etkiler. Daha fazla bilgi için [CA1819: özellikler diziler döndürmemelidir](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı, dışlama kesinlikle önerilmez. Salt okunur bir alanın içeriğini önemli olduğu neredeyse hiçbir senaryo oluşur. Senaryonuz Durum buysa, kaldırma `readonly` ileti hariç yerine değiştiricisi.

## <a name="example"></a>Örnek
 Bu örnekte bu kuralın ihlali tehlikelerini göstermektedir. Bir türe sahip bir örnek kitaplığı ilk bölümü gösterir `MyClassWithReadOnlyArrayField`, iki alan içeren (`grades` ve `privateGrades`) güvenli değildir. Alan `grades` genel ve bu nedenle güvenlik açığı bulunan her arayana. Alan `privateGrades` özeldir ancak yine de çağıranlar tarafından döndürdüğünden savunmasızdır `GetPrivateGrades` yöntemi. `securePrivateGrades` Alanı tarafından güvenli bir şekilde kullanıma sunulan `GetSecurePrivateGrades` yöntemi. İyi tasarım yöntemleri izlemek için özel olarak bildirilir. İkinci bölümü içinde depolanan değeri değiştirir kodu gösterir `grades` ve `privateGrades` üyeleri.

 Örnek sınıf kitaplığı, aşağıdaki örnekte görünür.

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ArrayFieldsNotReadOnly/cs/FxCop.Security.ArrayFieldsNotReadOnly.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği sınıf kitaplığı salt okunur bir dizi güvenlik sorunlarını göstermek için kullanır.

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestArrayFieldsRead/cs/FxCop.Security.TestArrayFieldsRead.cs#1)]

 Bu örnekte çıktı.

 **İzinsiz önce: derece: 90, 90, özel 90 derece: 90, 90, 90 güvenli derece, 90, 90, 90**
**oynama sonra: derece: 90, 555, özel 90 derece: 90, 555, 90 güvenli derece, 90, 90, 90**
## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Array?displayProperty=fullName><xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>



