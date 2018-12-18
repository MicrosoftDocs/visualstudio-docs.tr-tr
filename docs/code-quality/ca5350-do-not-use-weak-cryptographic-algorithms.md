---
title: 'CA5350: Zayıf Şifreleme Algoritmaları Kullanmayın'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba5e70505db86b1497e625b216da955bba677245
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547860"
---
# <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Zayıf Şifreleme Algoritmaları Kullanmayın

|||
|-|-|
|TypeName|DoNotUseWeakCryptographicAlgorithms|
|CheckId|CA5350|
|Kategori|Microsoft.Cryptography|
|Yeni Değişiklik|Bozucu olmayan|

> [!NOTE]
> Bu uyarı, Kasım 2015 tarihinde güncelleştirildiği.

## <a name="cause"></a>Sebep

Şifreleme algoritmaları gibi <xref:System.Security.Cryptography.TripleDES> ve karma algoritmaları gibi <xref:System.Security.Cryptography.SHA1> ve <xref:System.Security.Cryptography.RIPEMD160> zayıf olarak değerlendirilir.

Bu şifreleme algoritmaları kadar güvenlik güvencesi daha modern ortaklarınıza olarak sağlamaz. Şifreleme karma algoritmaları <xref:System.Security.Cryptography.SHA1> ve <xref:System.Security.Cryptography.RIPEMD160> daha modern karma algoritmaları daha az çakışma Direnci sağlayın. Şifreleme algoritması <xref:System.Security.Cryptography.TripleDES> daha az güvenlik bitten daha modern şifreleme algoritmaları sağlar.

## <a name="rule-description"></a>Kural açıklaması

Zayıf şifreleme algoritmalarını ve karma işlevler bir dizi nedenden ötürü bugün kullanılır, ancak bunlar bunların koruduğu verilerin gizliliği güvence altına almak için kullanılmamalıdır.

Kural tetikler 3DES, SHA1 veya RIPEMD160 algoritmaları oluşturur ve kod içinde bulduğunda kullanıcıya bir uyarı.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Şifreleme bakımından daha güçlü seçenekleri kullanın:

- TripleDES şifreleme için <xref:System.Security.Cryptography.Aes> şifreleme.

- SHA1 veya RIPEMD160 karma işlevler için olanları içinde kullanmak [SHA-2](/windows/desktop/SecCrypto/hash-and-signature-algorithms) ailesi (örneğin <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Verileri için gereken koruma düzeyini güvenlik garantisi gerekmiyorsa, bu kuraldan bir uyarıyı gizler.

## <a name="pseudo-code-examples"></a>Sözde kod örnekleri

Bu makalenin yazıldığı zaman itibariyle, aşağıdaki sözde kod örneği bu kural tarafından algılanan düzeni göstermektedir.

### <a name="sha-1-hashing-violation"></a>SHA-1 karma ihlali

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA1.Create();
```

Çözüm:

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="ripemd160-hashing-violation"></a>RIPEMD160 Karma ihlali

```csharp
using System.Security.Cryptography;
...
var hashAlg = RIPEMD160Managed.Create();
```

Çözüm:

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="tripledes-encryption-violation"></a>TripleDES şifreleme ihlali

```csharp
using System.Security.Cryptography;
...
using (TripleDES encAlg = TripleDES.Create())
{
  ...
}
```

Çözüm:

```csharp
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```