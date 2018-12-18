---
title: 'CA1702: Bileşik sözcüklerin küçük/büyük harfleri doğru yazılmalıdır'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4703c43c81df13432f45fb4ba519a02b39a839e0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917849"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: Bileşik sözcüklerin küçük/büyük harfleri doğru yazılmalıdır

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|Kategori|Microsoft.Naming|
|Yeni Değişiklik|En son ne zaman derlemelerini gönderildi.<br /><br /> Tür parametreleri harekete zaman bölünemez -.|

## <a name="cause"></a>Sebep

Tanımlayıcının adı birden çok sözcük içerir ve bu sözcüklerden en az biri büyük harf kullanımı hatasına maruz kalmış birleşik kelime olarak görülür.

## <a name="rule-description"></a>Kural açıklaması

Tanımlayıcı adı büyük/küçük harf üzerinde dayalı sözcükler bölündüğünü. Bitişik her iki word birleşimi Microsoft Yazım kitaplığı tarafından denetlenir. Tanımlıysa, kural ihlal tanımlayıcı oluşturur. "Sağlama" ve "Sağlama" ve "Multipart" sırasıyla ortası "MultiPart" bir ihlaline neden bileşik sözcüklerin örnekleridir. Önceki yaygın kullanımı nedeniyle, birkaç özel durum dışında kurala yerleşiktir ve birden fazla tek sözcük işaretlendi, "Araç" ve "Dosya adı" gibi ortası (Bu durumda, "Araç" ve "Dosya adı") iki ayrı sözcükleri olarak.

Adlandırma kuralları hedefleyen ortak dil çalışma zamanı kitaplıkları için genel bir bakış sağlar. Bu, yeni yazılım kitaplıkları için gereklidir ve kitaplık geliştirme yönetilen kodda uzmanlığa sahip olan kişi tarafından geliştirilmiştir müşteri güvenini artırır öğrenme eğrisini azaltır.

## <a name="how-to-fix-violations"></a>İhlallerini düzeltmek nasıl

Böylece doğru ortası adını değiştirin.

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

## <a name="when-to-suppress-warnings"></a>Ne zaman uyarıları bastırma

Bu kural bir uyarıdan bileşik word kısımlarını yazım sözlüğüyle tanınır ve amacı iki sözcükler kullanın ise gizlemek güvenlidir.

## <a name="related-rules"></a>İlgili kuralları

- [CA1701: Kaynak dize bileşik sözcüklerinin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1709: Tanımlayıcıların büyük/küçük harfleri doğru yazılmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Tanımlayıcılar örnekten daha fazla farklı olmalıdır](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Adlandırma Kuralları](/dotnet/standard/design-guidelines/naming-guidelines)
- [Büyük/Küçük Harf Kuralları](/dotnet/standard/design-guidelines/capitalization-conventions)