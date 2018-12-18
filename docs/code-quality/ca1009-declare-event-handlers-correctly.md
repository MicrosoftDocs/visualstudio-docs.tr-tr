---
title: 'CA1009: Olay işleyicilerini doğru bildirin'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7697b394396f729133b7cb6a7f3c0501c5c45202
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547402"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Olay işleyicilerini doğru bildirin

|||
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak veya korumalı bir olay işleme bir temsilci türü veya parametre adları, doğru imzaya sahip değil.

## <a name="rule-description"></a>Kural açıklaması
 Olay işleyicisi yöntemleri iki parametre alır. İlk türünde <xref:System.Object?displayProperty=fullName> ve 'sender' olarak adlandırılır. Bu olayda oluşan nesnedir. İkinci parametre türüdür <xref:System.EventArgs?displayProperty=fullName> ve 'e' olarak adlandırılır. Bu olay ile ilişkilendirilmiş olan verilerdir. Örneğin, olay verileri, genellikle her bir dosya açıldığında olay tetiklenir, dosya adını içerir.

 Olay işleyicisi yöntemleri bir değer döndürmemelidir. C# programlama diliyle, bu dönüş türü tarafından belirtilen `void`. Bir olay işleyicisi, birden çok nesne içinde birden çok yöntem çağırabilirsiniz. Yöntem bir değer döndürmek için izin verilirse, birden çok değer, her olay için ortaya çıkabilecek ve yalnızca son yöntemi çağrıldı değerini kullanılabilir olur.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için imza, dönüş türü veya temsilcinin parametre adları düzeltin. Ayrıntılar için aşağıdaki örneğe bakın.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, olayları işlemek için uygun olan bir temsilci gösterir. Bu olay işleyicisi tarafından çağrılan yöntemler tasarım yönergeleri ile ortaya belirtilen imzaya uymanız. `AlarmEventHandler` metot temsilcisinin tür adıdır. `AlarmEventArgs` Olay verileri için bir temel sınıftan türetilen <xref:System.EventArgs>, ve alarm olay verilerini tutar.

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]

## <a name="related-rules"></a>İlgili kuralları
 [CA2109: Görünen olay işleyicileri gözden geçirin](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.EventArgs?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>
- [Olaylar oluşturma ve işleme](/dotnet/standard/events/index)