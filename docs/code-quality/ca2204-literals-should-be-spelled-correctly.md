---
title: 'CA2204: Değişmez değerler doğru yazılmalıdır'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f86658978a105c1fa4f3c4602b5c838f4c80726
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918429"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Değişmez değerler doğru yazılmalıdır

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Kategori|Microsoft.Usage|
|Yeni Değişiklik|Olmayan sonu|

## <a name="cause"></a>Sebep

Sabit değerli bir dize yerelleştirilebilir parametresi için ya da yerelleştirilebilir özelliği bağımsız değişken olarak geçirilir ve dize Microsoft Yazım kitaplığı tarafından tanınmayan bir veya daha fazla sözcükler içeriyor.

## <a name="rule-description"></a>Kural açıklaması

Bu kural bir parametre veya bir özellik için bir değer olarak geçirilen sabit değerli bir dize ya da daha fazla aşağıdaki durumlarda doğrudur:

- <xref:System.ComponentModel.LocalizableAttribute> Parametresi ya da özelliğin özniteliği true.

- Parametresi veya özellik adı "Metin", "İletisi" veya "Resim yazısı" içerir.

- Geçirilen dize değişkeninin adı bir <xref:System.Console.Write%2A> veya <xref:System.Console.WriteLine> yöntemdir "value" veya "biçim".

Bu kural değişmez değer dize bileşik sözcüklerinin belirtece dönüştürmek sözcüklere ayrıştırır ve her bir sözcük veya belirteç yazımını denetler. Ayrıştırma algoritması hakkında daha fazla bilgi için bkz: [CA1704: tanımlayıcılar yazıldığından](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="language"></a>Dil

Yazım denetimi şu anda yalnızca İngilizce tabanlı kültürü sözlükler karşı denetler. Proje dosyası projenizde kültürünü ekleyerek değiştirebilirsiniz **CodeAnalysisCulture** öğesi.

Örneğin:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Bir İngilizce tabanlı kültürü dışında her şey için kültürü ayarlama, bu kod analizi kural sessiz bir şekilde devre dışı bırakılır.

## <a name="how-to-fix-violations"></a>İhlallerini düzeltmek nasıl

Bu kural ihlal düzeltmek için Word yazımı düzeltin veya sözcüğü özel sözlüğe ekleyin. Özel sözlük kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Kod Analizi dizinini özelleştirme](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Ne zaman uyarıları bastırma

Bu kuraldan uyarıyı bastırmayın. Doğru yazılmış kelimeler yeni yazılım kitaplıkları için gerekli öğrenme eğrisini düşürebilir.

## <a name="related-rules"></a>İlgili kuralları

- [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703: Kaynak dizeler doğru yazılmalıdır](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)