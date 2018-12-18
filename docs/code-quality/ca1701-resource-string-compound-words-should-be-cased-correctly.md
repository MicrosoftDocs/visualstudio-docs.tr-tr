---
title: 'CA1701: Kaynak dize bileşik sözcüklerinin küçük/büyük harfleri doğru yazılmalıdır'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ecc558cb9c069c19b545434afe0a851130fdb300
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915663"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: Kaynak dize bileşik sözcüklerinin küçük/büyük harfleri doğru yazılmalıdır

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Kategori|Microsoft.Naming|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep

Kaynak dizesi doğru ortası görünmüyor bileşik bir sözcük içeriyor.

## <a name="rule-description"></a>Kural açıklaması

Her sözcüğün kaynak dizesi büyük/küçük harf üzerinde temel belirteçler içine ayrılır. Her bir bitişik ikili-işaret kombinasyonu Microsoft yazım kitaplığı tarafından denetlenir. Tanınırsa, kelime kural ihlali üretir. "Sağlama" ve "Sağlama" ve "Multipart" sırasıyla ortası "MultiPart" bir ihlaline neden bileşik sözcüklerin örnekleridir. Önceki yaygın kullanım nedeniyle bazı özel durumlar kurala yerleşiktir ve "Araç" ve "iki ayrı sözcükleri ortası Filename" gibi birkaç tek sözcük işaretlenir. Bu örnekte, "Araç" ve "Dosya adı" bayrağı.

Adlandırma kuralları hedefleyen ortak dil çalışma zamanı kitaplıkları için genel bir bakış sağlar. Bu, yeni yazılım kitaplıkları için gereklidir ve kitaplık geliştirme yönetilen kodda uzmanlığa sahip olan kişi tarafından geliştirilmiştir müşteri güvenini artırır öğrenme eğrisini azaltır.

## <a name="how-to-fix-violations"></a>İhlallerini düzeltmek nasıl

Word doğru ortası şekilde değiştirin.

## <a name="change-the-dictionary-language"></a>Sözlük dilini değiştirme

Varsayılan olarak, yazım İngilizce (TR) sürümü kullanılır. Yazım denetimi dilini değiştirmek istiyorsanız, ekleyerek aşağıdakilerden birini özniteliklerini şekilde bunu yapabilirsiniz, *AssemblyInfo.cs* veya *AssemblyInfo.vb* dosyası:

- Kullanım <xref:System.Reflection.AssemblyCultureAttribute> kültürü kaynaklarınızı uydu derlemesi içinde olup olmadığını belirtmek için.
- Kullanım <xref:System.Resources.NeutralResourcesLanguageAttribute> belirtmek için *bağımsız kültür* kodunuzu aynı bütünleştirilmiş kaynaklarınız varsa, derleme.

> [!IMPORTANT]
> Bir İngilizce tabanlı kültürü dışında her şey için kültürü ayarlama, bu kod analizi kural sessiz bir şekilde devre dışı bırakılır.

## <a name="when-to-suppress-warnings"></a>Ne zaman uyarıları bastırma

Bu kural bir uyarıdan bileşik word kısımlarını yazım sözlüğüyle tanınır ve iki sözcükler kullanmayı hedefi ise gizlemek güvenlidir.

Özel sözlük yazım denetimi için bileşik sözcüklerin ekleyebilirsiniz. Özel sözlük sözcükleri ihlalleri neden olmaz. Daha fazla bilgi için bkz: [nasıl yapılır: Kod Analizi dizinini özelleştirme](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>İlgili kuralları

- [CA1702: Bileşik sözcüklerin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)
- [CA1709: Tanımlayıcıların büyük/küçük harfleri doğru yazılmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Tanımlayıcılar örnekten daha fazla farklı olmalıdır](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Büyük/Küçük Harf Kuralları](/dotnet/standard/design-guidelines/capitalization-conventions)
- [Adlandırma Kuralları](/dotnet/standard/design-guidelines/naming-guidelines)