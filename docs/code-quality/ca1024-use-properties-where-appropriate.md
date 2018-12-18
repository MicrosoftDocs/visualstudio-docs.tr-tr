---
title: 'CA1024: Uygun yerlerde özellikler kullan'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0f74c41584c8dc8960adce2bd253f7d1c38707f7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823222"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Uygun yerlerde özellikler kullan

|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep

Ortak veya korumalı yöntem ile başlayan bir ada sahip `Get`hiçbir parametre almaz ve dizi olmayan bir değer döndürür.

## <a name="rule-description"></a>Kural açıklaması

Çoğu durumda veri özelliklerini temsil eder ve yöntemleri eylemleri gerçekleştirebilirsiniz. Özellikler, bunları kullanmayı kolaylaştırır alanları gibi erişilir. Bir yöntem, Bu koşullardan biri varsa özellik olmak için iyi bir adaydır:

- Hiçbir bağımsız değişkeni alır ve bir nesnenin durum bilgilerini döndürür.

- Bir nesnenin durumu kısmı ayarlamak için tek bir bağımsız değişken kabul eder.

Özellikleri, alanları ise olarak hareket etmesi gerektiğini; yöntem çözemezseniz, bir özelliğe değiştirilmemelidir. Aşağıdaki durumlarda özelliklerini daha iyi yöntemler şunlardır:

- Yöntem, zaman alıcı bir işlem gerçekleştirir. Yöntemi, perceivably ayarlamak veya bir alanın değerini almak için gereken süreden daha yavaştır.

- Bir dönüştürme yöntemi gerçekleştirir. Bir alana erişim depoladığı verilerin dönüştürülmüş bir sürümünü döndürmez.

- Get yöntemi gözlemlenebilir bir yan etkisi vardır. Bir alanın değerini alma yan etkileri üretmez.

- Yürütme sırası önemlidir. Bir alanın değerini ayarlama, diğer işlemleri oluşması bağımlı kalmayacak.

- Yöntemi, art arda iki kez çağırmak farklı sonuçlar oluşturur.

- Yöntem statik olsa da arayan tarafından değiştirilebilen bir nesne döndürür. Bir alanın değerini alma alanı tarafından depolanan verileri değiştirmek çağıranın izin vermez.

- Yöntemi, bir dizi döndürür.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Bu kural ihlalini düzeltmek için yöntem bir özelliğini değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Yöntem en az bir tanesi yukarıda listelenen ölçütlerini karşılıyorsa bu kuraldan bir uyarıyı gizler.

## <a name="controlling-property-expansion-in-the-debugger"></a>Hata ayıklayıcısı özellik genişletme denetleme

Programcıların bir özelliğini kullanmaktan nedenlerinden biri, otomatik-genişletmek için hata ayıklayıcı istemediğiniz olmasıdır. Örneğin, özellik, büyük nesne ayırma veya P/Invoke çağırma gerektirebilir, ancak gözlemlenebilir bir yan etkileri gerçekten olmayabilir.

Hata ayıklayıcı otomatik-aşmasını önlemek özellikler uygulayarak <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. Aşağıdaki örnek, bir örnek özelliğine uygulanan bu özniteliği gösterir.

```vb
Imports System
Imports System.Diagnostics

Namespace Microsoft.Samples

    Public Class TestClass

        ' [...]

        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _
        Public ReadOnly Property LargeObject() As LargeObject
            Get
                ' Allocate large object
                ' [...]
            End Get
        End Property

    End Class

End Namespace
```

```csharp
using System;
using System.Diagnostics;

namespace Microsoft.Samples
{
    publicclass TestClass
    {
        // [...]

        [DebuggerBrowsable(DebuggerBrowsableState.Never)]
        public LargeObject LargeObject
        {
            get
            {
                // Allocate large object
                // [...]
            }
        }
    }
}
```

## <a name="example"></a>Örnek

Aşağıdaki örnek, özelliklerine dönüştürülmesi gerektiğini ve değil gibi alanlarını davranmayabilir olduğundan, birkaç gereken çeşitli yöntemler içerir.

[!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]