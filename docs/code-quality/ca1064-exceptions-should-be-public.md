---
title: 'CA1064: Özel durumlar genel olmamalıdır'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 904aa1fe83677e2d53d2e93964619a5c2aa82625
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816834"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: Özel durumlar genel olmamalıdır

|||
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep
 Doğrudan genel olmayan özel durum türetilen <xref:System.Exception>, <xref:System.SystemException>, veya <xref:System.ApplicationException>.

## <a name="rule-description"></a>Kural açıklaması
 Bir iç özel durum yalnızca kendi iç kapsamı içinde görülebilir. İç kapsam dışında kalan özel durumlardan sonra, sadece basit istisnalar istisna yakalamak için kullanılabilir. İç özel durum öğesinden devralınan <xref:System.Exception>, <xref:System.SystemException>, veya <xref:System.ApplicationException>, harici kod özel durum ne olduğunu bilmek yeterli bilgiye sahip değildir.

 Ancak, kodu daha sonra bir iç özel durum için temel olarak kullanılan genel bir özel durum varsa, çıkış kodu daha ayrıntılı temel özel durum ile akıllı bir şey mümkün olacaktır varsaymak uygun olur. Genel özel durum tarafından sağlanan değerinden daha fazla bilgi olacaktır <xref:System.Exception>, <xref:System.SystemException>, veya <xref:System.ApplicationException>.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Özel durum Genel hale getirmek ya da iç özel durum olmayan genel bir özel durumdan türetilen <xref:System.Exception>, <xref:System.SystemException>, veya <xref:System.ApplicationException>.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Kendi iç kapsamı içinde özel durum yakalandı, tüm durumlarda eminseniz bu kuraldan bir iletiyi gösterme.

## <a name="example"></a>Örnek
 Bu kural, çünkü özel durum sınıfı doğrudan özel durumdan türetilen ve iç ilk örnek yöntem üzerinde FirstCustomException tetikler. Sınıfı ayrıca doğrudan özel durumdan türetilen olsa da, sınıfın genel olarak bildirildiğinden, kural SecondCustomException sınıfında etkinleşmez. Doğrudan türemediği üçüncü sınıfı kuralı da başlatılmıyor <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, veya <xref:System.ApplicationException?displayProperty=fullName>.

 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]
