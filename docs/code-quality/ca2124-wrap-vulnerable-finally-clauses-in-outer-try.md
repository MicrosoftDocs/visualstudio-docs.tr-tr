---
title: 'CA2124: Savunmasız sonunda yan tümcelerini dış deneme içine sarmalayın'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 50c03a16af9562df40dc04a431fac157c1321fbb
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860088"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Savunmasız sonunda yan tümcelerini dış deneme içine sarmalayın

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep
 1.0 ve 1.1 .NET Framework sürümlerinde, bir ortak veya korumalı yöntem içerir bir `try` / `catch` / `finally` blok. `finally` Blok güvenlik durumunu sıfırlamak için görünür ve sınırlanan değil bir `finally` blok.

## <a name="rule-description"></a>Kural açıklaması
 Bu kural bulur `try` / `finally` sürümleri 1.0 ve 1.1 kötü amaçlı bir özel durum filtreleri çağrı yığınında mevcut savunmasız olabilecek .NET Framework'ün hedefleyen kodda engeller. Kimliğe bürünme gibi hassas işlemler try bloğunda oluşur ve bir özel durum, filtre önce yürütebilir `finally` blok. Kimliğe bürünme örneği için bu filtrenin bürünülen kullanıcıyla yürütmesine anlamına gelir. Şu anda yalnızca Visual Basic'te implementable filtrelerdir.

> [!NOTE]
> 2.0 ve .NET Framework'ün sonraki sürümlerinde, çalışma zamanı otomatik olarak koruyan bir `try` / `catch` /  `finally` sıfırlama doğrudan yöntemi içinde ortaya çıkarsa kötü amaçlı bir özel durum filtrelerden engelleme, özel durum bloğu içerir.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Sarmalanmış halden yerleştirin `try` / `finally` bir dış try bloğu içinde. Aşağıdaki ikinci örneğe bakın. Bu zorlar `finally` filtre kodundan önce yürütülecek.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="pseudo-code-example"></a>Sözde kod örneği

### <a name="description"></a>Açıklama

Bu kural tarafından algılanan düzeni aşağıdaki sözde kod göstermektedir.

```csharp
try {
   // Do some work.
   Impersonator imp = new Impersonator("John Doe");
   imp.AddToCreditCardBalance(100);
}
finally {
   // Reset security state.
   imp.Revert();
}
```

Aşağıdaki sözde kod kodunuzu koruyun ve bu kural karşılamak için kullanabileceğiniz desenini gösterir.

```csharp
try {
     try {
        // Do some work.
     }
     finally {
        // Reset security state.
     }
}
catch()
{
    throw;
}
```