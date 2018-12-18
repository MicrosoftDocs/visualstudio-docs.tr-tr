---
title: 'CA1057: Dize URI aşırı yüklemeleri System.Uri aşırı yüklemelerini çağırır'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 44130632cb416bf03819ddff13b797ac3b799354
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547182"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Dize URI aşırı yüklemeleri System.Uri aşırı yüklemelerini çağırır

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep

Bir tür yalnızca bir dize parametresi adlandırılan farklı yöntem aşırı yüklemeleri bildirir bir <xref:System.Uri?displayProperty=fullName> parametresi ve dize parametresi alan aşırı yüklemesini alan aşırı yüklemesini çağırmaz <xref:System.Uri> parametresi.

## <a name="rule-description"></a>Kural açıklaması
 Yalnızca dize tarafından aşırı yüklemeler farklı olduğundan veya <xref:System.Uri> parametresi dize bir Tekdüzen Kaynak Tanımlayıcısı (URI) temsil etmek için varsayılır. Bir URI'nın dize sunumu ayrıştırma ve hataları kodlama eğilimindedir ve güvenlik açıklarına yol açabilir. <xref:System.Uri> Sınıfı bu hizmetleri güvenli bir biçimde sunar. Avantajlarını kazanmak için <xref:System.Uri> sınıfı, dize aşırı yüklemesi çağırmanız <xref:System.Uri> dize bağımsız değişkeni kullanılarak aşırı yükleme.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 URI'ın dize gösterimini kullanır ve böylece bir örneğini oluşturur yöntemi yeniden uygulayın <xref:System.Uri> dize bağımsız değişkeni kullanarak ve ardından geçirir <xref:System.Uri> olan aşırı yüklenmiş bir nesneye <xref:System.Uri> parametresi.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Dize parametresi bir URI temsil etmiyorsa, bu kuraldan bir uyarıyı bastırmak güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, doğru uygulanmış bir aşırı gösterir.

 [!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
 [!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>İlgili kuralları
 [CA2234: Dizeler yerine System.Uri nesneleri gönderin](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: URI özellikleri dize olmamalıdır](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: URI parametreleri dizeler olmamalıdır](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI dönüş değerleri dizeler olmamalıdır](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)