---
title: 'CA5351: Bozuk Şifreleme Algoritmaları Kullanmayın'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 483f51b3-e186-4433-b48e-5ca24a9a9c94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c00d4e8ebb385b987bb49a44af8b241883a566b
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550979"
---
# <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: Bozuk Şifreleme Algoritmaları Kullanmayın

|||
|-|-|
|TypeName|DoNotUseBrokenCryptographicAlgorithms|
|CheckId|CA5351:|
|Kategori|Microsoft.Cryptography|
|Yeni Değişiklik|Bozucu olmayan|

> [!NOTE]
> Bu uyarı, Kasım 2015 tarihinde güncelleştirildiği.

## <a name="cause"></a>Sebep

İşlevleri gibi karma <xref:System.Security.Cryptography.MD5> ve şifreleme algoritmaları gibi <xref:System.Security.Cryptography.DES> ve <xref:System.Security.Cryptography.RC2> önemli risk getirebilir ve önemsiz saldırı teknikleri üzerinden hassas bilgiler açığa yanılma saldırıları gibi sonuçlanabilir ve karma çakışmaları.

Bilinen bir şifreleme saldırılarına maruz aşağıdaki şifreleme algoritmaları listede var. Şifreleme karma algoritması <xref:System.Security.Cryptography.MD5> karma çakışma saldırılarına maruz olduğu.  Kullanımınıza bağlı olarak, bir karma çakışması kimliğe bürünme, değiştirilmesine veya diğer tür saldırıları, bir karma işlevi şifreleme benzersiz çıktısını kullanan sistemlerinde neden olabilir. Şifreleme algoritmaları <xref:System.Security.Cryptography.DES> ve <xref:System.Security.Cryptography.RC2> şifrelenmiş verilerin istenmeyen açıklanmasıyla sonuçlanabilir şifreleme saldırılara maruz şunlardır.

## <a name="rule-description"></a>Kural açıklaması

Bozuk şifreleme algoritmaları güvenli kabul edilmeyen ve bunların kullanılması önerilmez. Belirli güvenlik açığı kullanım bağlam göre farklılık gösterir ancak MD5 karma algoritması bilinen çakışma saldırılara açıktır.  (Örneğin, dosya imzası veya dijital sertifika) veri bütünlüğünü sağlamak için kullanılan karma algoritmaları özellikle savunmasızdır.  Zararsız veri kötü amaçlı veri ile karma değeri değiştirme veya ilişkili bir dijital imza geçersiz kılmalarını yerine kullanılabileceği gibi bu bağlamda, verilerinizin iki ayrı parçaları saldırganlar oluşturabilir.

Şifreleme algoritmaları için:

- <xref:System.Security.Cryptography.DES> Şifreleme, daha az bir gün içinde deneme yanılma yoluyla yapılan zorla olabilir küçük bir anahtar boyutu içerir.

- <xref:System.Security.Cryptography.RC2> Şifreleme ilgili anahtar saldırısına maruz burada saldırganın tüm anahtar değerleri matematiksel ilişkilerini bulur.

Bu kural kaynak kodunda yukarıdaki şifreleme işlevlerden herhangi birinin bulur ve kullanıcı için bir uyarı oluşturduğunda tetiklenir.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Şifreleme bakımından daha güçlü seçenekleri kullanın:

- MD5 karmaları kullanın [SHA-2](/windows/desktop/SecCrypto/hash-and-signature-algorithms) ailesi (örneğin, <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).

- DES ve RC2 <xref:System.Security.Cryptography.Aes> şifreleme.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Bu şifreleme bir uzmana göre gözden geçirilir sürece bu kuraldan bir uyarıyı bastırmayın.

## <a name="pseudo-code-examples"></a>Sözde kod örnekleri

Bu kural ve olası alternatifler tarafından algılanan düzeni aşağıdaki sözde kod örneklerini göstermektedir.

### <a name="md5-hashing-violation"></a>MD5 Karma ihlali

```csharp
using System.Security.Cryptography;
...
var hashAlg = MD5.Create();
```

Çözüm:

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="rc2-encryption-violation"></a>RC2 Şifreleme ihlali

```csharp
using System.Security.Cryptography;
...
RC2 encAlg = RC2.Create();
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

### <a name="des-encryption-violation"></a>DES şifrelemesi ihlali

```csharp
using System.Security.Cryptography;
...
DES encAlg = DES.Create();
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