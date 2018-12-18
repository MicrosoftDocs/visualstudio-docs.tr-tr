---
title: 'CA1800: Gereksiz atamalar yapmayın'
ms.date: 10/26/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: a1db0f421f72e5b63b14c95a706b738bea1a4174
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550524"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Gereksiz atamalar yapmayın

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Kategori|Microsoft.Performance|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
Bir yöntem yinelenen atamalardan biri kendi bağımsız değişkenler veya yerel değişkenler üzerinde gerçekleştirir.

Tam çözümleme bu kural tarafından test edilen derleme, hata ayıklama bilgileri kullanılarak oluşturulmalıdır ve ilişkili bir program veritabanı (.pdb) dosyası kullanılabilir olmalıdır.

## <a name="rule-description"></a>Kural açıklaması
Özellikle yayınlar sıkıştırılmış yineleme deyiminde gerçekleştirildiğinde yinelenen yayınların performansını azaltır. Yinelenen açık tür dönüştürme işlemleri için atamanın sonucu yerel bir değişkende depolayın ve yinelenen atama işlemleri yerine yerel değişkenini kullanın.

C# `is` işleci gerçek atama yapılmadan önce atama başarılı olup olmadığını sınamak için kullanılan test sonucunu göz önünde bulundurun `as` işleci bunun yerine. Bu örtük dönüştürme işlemi tarafından gerçekleştirilen olmadan aynı işlevlere `is` işleci. Ya da C# 7.0 ve daha sonra kullanmak `is` işleciyle [desen eşleştirme](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) tür dönüştürme denetleyin ve tek bir adımda bir değişken ifade türü dönüştürün.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için tür dönüştürme işlemlerinin sayısını en aza indirmek için yöntem uygulaması değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Performans önemli değilse bu kuraldan bir uyarıyı bastırmak için ya da kural tamamen yok saymak için güvenlidir.

## <a name="examples"></a>Örnekler
 Aşağıdaki örnek C# kullanarak kuralı ihlal eden bir yöntemi gösterir `is` işleci. İkinci yöntem değiştirerek kural karşılayan `is` işleci ile bir test sonucunu karşı `as` işleci atama işlemleri her ikisinden birine yinelemesi sayısını azaltır. Ayrıca üçüncü bir yöntem kullanarak kural karşılar `is` ile [desen eşleştirme](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) tür dönüştürme başarılı olabilir, istenen türde bir değişken oluşturmak için.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

 Aşağıdaki örnek bir yöntemi gösterir `start_Click`, birden çok yinelenen açık Atamalar, kural ve bir yöntem ihlal olan `reset_Click`, hangi karşılayan kural dönüştürme bir yerel değişkende depolayarak.

 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [(, C# Başvurusu)](/dotnet/csharp/language-reference/keywords/as)
- [(C# Başvurusu)](/dotnet/csharp/language-reference/keywords/is)