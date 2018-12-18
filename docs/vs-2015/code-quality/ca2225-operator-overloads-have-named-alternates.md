---
title: 'CA2225: İşleç aşırı yüklemeleri adlandırılmış Alternatiflere sahiptir | Microsoft Docs'
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
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 427bd7756e1bf7a9e1b7056a84dd90c29bf504fe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860259"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep
 Operatör aşırı yüklemesi bulundu ve beklenen adlandırılmış alternatif yöntem bulunamadı.

## <a name="rule-description"></a>Kural Tanımı
 İşleç aşırı yüklemesi hesaplamaları için bir türü temsil etmek için semboller kullanımına izin verir. Örneğin, eklenmesi için (+) artı simgesini aşırı bir türü genellikle 'Ekle' adlı alternatif bir üye yoktur. Adlandırılmış alternatif üye işleci ile aynı işlevlere erişim sağlar ve aşırı yüklenmiş operatörlere destek olmayan dilleri içinde program geliştiriciler için sağlanır.

 Bu kural aşağıdaki tabloda listelenen işleçlerden inceler.

|C#|Visual Basic|C++|Diğer adı|
|---------|------------------|-----------|--------------------|
|+ (ikili)|+|+ (ikili)|Ekle|
|+=|+=|+=|Ekle|
|&|ve|&|BitwiseAnd|
|&=|Ve =|&=|BitwiseAnd|
|&#124;|Veya|&#124;|BitwiseOr|
|&#124;=|Veya =|&#124;=|BitwiseOr|
|--|Yok|--|Azaltma|
|/|/|/|Bölme|
|/=|/=|/=|Bölme|
|==|=|==|Eşittir|
|^|Xor|^|Xor|
|^=|Xor =|^=|Xor|
|>|>|>|{1&gt;Karşılaştır&lt;1}|
|>=|>=|>=|{1&gt;Karşılaştır&lt;1}|
|++|Yok|++|Artırma|
|<>|!=|Eşittir|
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|{1&gt;Karşılaştır&lt;1}|
|<=|<=|\<=|{1&gt;Karşılaştır&lt;1}|
|&&|Yok|&&|LogicalAnd|
|&#124;&#124;|Yok|&#124;&#124;|LogicalOr|
|!|Yok|!|LogicalNot|
|%|Mod|%|Mod veya kalan|
|%=|Yok|%=|Mod|
|* (ikili)|*|*|Çarp|
|*=|Yok|*=|Çarp|
|~|değil|~|OnesComplement|
|>>|>>|>>|RightShift|
=|Yok|>>=|RightShift|
|-(ikili)|-(ikili)|-(ikili)|Çıkarma|
|-=|Yok|-=|Çıkarma|
|true|IsTrue|Yok|IsTrue (özellik)|
|-(tekli)|Yok|-|negate|
|+ (tekli)|Yok|+|artı|
|false|IsFalse|False|IsTrue (özellik)|

 Yok == seçtiğiniz dilde aşırı yüklenemez.

 Kural türü örtük ve açık dönüştürme işleçleri de denetler (`SomeType`) adlı yöntemleri için işaretleyerek `ToSomeType` ve `FromSomeType`.

 İkili İşleç aşırı C# ' ta karşılık gelen bir atama işleci varsa, aynı zamanda örtük olarak aşırı yüklenmiş olur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için alternatif yöntem için işleç uygulayın; önerilen alternatif adını kullanarak adlandırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Paylaşılan bir kitaplık uyguluyorsanız, bu kuraldan bir uyarıyı bastırmayın. Uygulamalar bu kuraldan bir uyarıyı yok sayabilirsiniz.

## <a name="example"></a>Örnek
 Aşağıdaki örnek bu kuralı ihlal eden bir yapı tanımlar. Örnek düzeltmek için bir genel ekleme `Add(int x, int y)` yapısına yöntemi.

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorOverloadsHaveNamedAlternates/cs/FxCop.Usage.OperatorOverloadsHaveNamedAlternates.cs#1)]

## <a name="related-rules"></a>İlgili kuralları
 [CA1046: Başvuru türlerinde eşittir işleçlerini aşırı yüklemeyin](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226: İşleçler simetrik aşırı yüklemelere sahip olmalıdır](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Eşittir işlecini aşırı yükleyerek eşittiri geçersiz kılın](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: GetHashCode'u Eşittir'i geçersiz kılarak geçersiz kılın](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: ValueType.Equals değerini geçersiz kılmada eşittir işlecini aşırı yükle](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)



