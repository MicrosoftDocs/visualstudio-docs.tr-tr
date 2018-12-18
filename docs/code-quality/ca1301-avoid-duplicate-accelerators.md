---
title: 'CA1301: Yinelenen hızlandırıcılardan kaçının'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f4dac6beddf43e88d47a54ddf2b0e0d56e387038
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547209"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Yinelenen hızlandırıcılardan kaçının

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Kategori|Microsoft.Globalization|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Bir türü genişleten <xref:System.Windows.Forms.Control?displayProperty=fullName> ve bir kaynak dosyasında depolanan aynı erişim anahtarları olan iki veya daha fazla üst düzey denetimleri içerir.

## <a name="rule-description"></a>Kural açıklaması

Bir Hızlandırıcı olarak da bilinen bir erişim anahtarı kullanarak bir denetimin klavye erişim sağlayan **Alt** anahtarı. Birden çok denetim aynı erişim anahtarı varsa, erişim tuşunun davranışı iyi tanımlı değildir. Kullanıcı erişim anahtarını kullanarak erişim hedeflenen denetimi olmayabilir ve amaçlanan farklı bir denetimin etkin.

Geçerli uygulama bu kuralın menü öğelerini yok sayar. Ancak, aynı alt menü öğeleri aynı erişim anahtarlarını sahip olmamalıdır.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için tüm denetimler için benzersiz bir erişim anahtarları tanımlayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, aynı erişim anahtarları olan iki denetim içeren en az bir form gösterir. Anahtarları gösterilmiyor bir kaynak dosyasında depolanır. Değerlerine açıklamalı görünür ancak çıkış `checkBox.Text` satırlar. Yinelenen hızlandırıcılardan davranışını değiştirerek incelenebilir `checkBox.Text` kullanıma açıklamalı karşılıkları satırıyla. Ancak, bu durumda, örnek bir uyarı kuralından oluşturmaz.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Masaüstü Uygulamalarındaki Kaynaklar](/dotnet/framework/resources/index)