---
title: 'CA2122: Bağlantı talepleri olan yöntemleri dolaylı olarak açığa çıkarmayın'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d17c2981e4dabe82817aeedcf4fcab93e970b47
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548906"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Bağlantı talepleri olan yöntemleri dolaylı olarak açığa çıkarmayın

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep
 Ortak veya korumalı bir üyenin bir [bağlantı talepleri](/dotnet/framework/misc/link-demands) ve herhangi bir güvenlik denetimi gerçekleştirmeyen üye tarafından çağrılır.

## <a name="rule-description"></a>Kural açıklaması
 Bağlantı talebi, yalnızca o anki çağırıcı izinlerini denetler. Üye ise `X` hiçbir güvenlik taleplerini çağıranlar ve kod gerekli izne kullanabilirsiniz olmadan bu bağlantı talebi tarafından çağıran korumalı çağrıları yapar `X` korunan üyesine erişmek için.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Güvenlik ekleme [veri ve modelleme](/dotnet/framework/data/index) veya artık bağlantı talebi tarafından korunan üyesine güvenli erişim sağlar, böylece üyesine bağlantısını isteğe bağlı.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Güvenli bir şekilde bu kuraldan bir uyarıyı bastırmak için kodunuzu işlemleri veya yıkıcı bir şekilde kullanılabilir kaynaklara erişimi çağıranlarını tanımaz emin olmanız gerekir.

## <a name="example-1"></a>Örnek 1
 Aşağıdaki örnekler, kural ihlal eden bir kitaplık ve kitaplığın zayıflık gösteren bir uygulama gösterir. Örnek kitaplığı birlikte bu kuralı ihlal eden iki yöntem sunar. `EnvironmentSetting` Ortam değişkenlerini sınırsız erişim için bir bağlantı talebi tarafından güvenli yöntemi. `DomainInformation` Yöntemi çağırmadan önce hiçbir güvenlik taleplerini çağıranlarını yapar `EnvironmentSetting`.

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]

## <a name="example-2"></a>Örnek 2
 Aşağıdaki uygulama güvenli olmayan kitaplık üyesini çağırır.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]

Bu örnek aşağıdaki çıktıyı üretir:

```txt
*Value from unsecured member: seattle.corp.contoso.com
```

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](/dotnet/standard/security/secure-coding-guidelines)
- [Bağlantı talepleri](/dotnet/framework/misc/link-demands)
- [Veri ve Modelleme](/dotnet/framework/data/index)