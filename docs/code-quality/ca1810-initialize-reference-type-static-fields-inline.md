---
title: 'CA1810: Başvuru türü statik alanları satır içi başlatın'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2a6fdfebe506fb2edb1814e18d3d090025c665fa
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549449"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: Başvuru türü statik alanları satır içi başlatın

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|Kategori|Microsoft.Performance|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Bir başvuru türü açık bir statik Oluşturucu bildirir.

## <a name="rule-description"></a>Kural açıklaması
 Bir tür açık statik yapıcı bildirdiğinde, JIT derleyici her bir statik yöntemi kontrol ekler ve türün yapıcı örneği statik yapıcının daha önceden çağrıldığından emin olur. Statik başlatma, statik bir üyeye erişildiğinde veya türünün bir örneği oluşturulduğunda tetiklenir. Ancak, statik başlatma türünün bir değişkeni bildirmek, ancak bunu olabilen başlatma genel durumu değişirse önemli kullanmayın tetiklenmiyor.

 Tüm statik veriler başlatılmış satır içi ve açık bir statik Oluşturucu bildirimi yapılmadı, Microsoft Ara dil (MSIL) derleyicileri ekleme `beforefieldinit` bayrağı ve MSIL türüne statik verinin başlatır örtük bir statik Oluşturucu, tanımı. JIT derleyicisi karşılaştığında `beforefieldinit` bayrak, çoğu zaman statik Oluşturucu denetimleri eklenmez. Statik başlatma, tüm statik alanları erişebilmek için önce ancak statik bir yöntemi veya örnek oluşturucusu olmayan çağrılmadan önce bir süre sonra gerçekleşmesi için sağlanır. Bu statik başlatma türünde bir değişken bildirildikten sonra herhangi bir zamanda meydana gelebilir unutmayın.

 Statik oluşturucu denetimleri performansı düşürebilir. Genellikle bir statik Oluşturucu, yalnızca statik alanları, servis talebi, yalnızca statik başlatmanın emin olmalısınız statik bir alana erişim ilk önce oluştuğu başlatmak için kullanılır. `beforefieldinit` Davranıştır bu ve diğer birçok tür için uygun. Yalnızca statik başlatma genel durumunu etkiler ve aşağıdaki koşullardan biri uygunsuz olur:

- Genel durum üzerindeki etkisini, pahalıdır ve türü kullanılmaz, gerekli değildir.

- Genel durum etkileri herhangi türü statik alanları erişmeden erişilebilir.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için bildirildiğinde, tüm statik veriyi başlatın ve statik oluşturucuyu kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Performans önemli değilse bu kuraldan bir uyarıyı bastırmak güvenlidir; türün statik bir yöntem çağrılır veya türünün bir örneği oluşturulduktan önce gerçekleşmesi için statik başlatma tarafından neden genel durum değişiklikleri pahalıdır veya gerekir veya garanti.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir tür gösterir `StaticConstructor`, kural ve bir tür ihlal `NoStaticConstructor`, kural karşılamak için satır içi başlatma ile statik oluşturucuyu değiştirir.

[!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
[!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]

Ek unutmayın `beforefieldinit` bayrağının MSIL tanımında `NoStaticConstructor` sınıfı.

```
.class public auto ansi StaticConstructor
extends [mscorlib]System.Object
{
} // end of class StaticConstructor

.class public auto ansi beforefieldinit NoStaticConstructor
extends [mscorlib]System.Object
{
} // end of class NoStaticConstructor
```

## <a name="related-rules"></a>İlgili kuralları

- [CA2207: Değer türü statik alanları satır içi başlatın](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)