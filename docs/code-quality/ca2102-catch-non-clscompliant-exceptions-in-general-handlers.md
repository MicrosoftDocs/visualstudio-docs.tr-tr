---
title: 'CA2102: CLSCompliant olmayan özel durumları genel işleyiciler içinde yakalayın'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f5af37daba4ce1791c5485d65734d1dd8c3d87f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887052"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: CLSCompliant olmayan özel durumları genel işleyiciler içinde yakalayın

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep

İle işaretlenmiş derlemedeki bir üye <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> veya işaretlenmiş `RuntimeCompatibility(WrapNonExceptionThrows = false)` işleyen yakalama bloğu içerir <xref:System.Exception?displayProperty=fullName> ve hemen arkasından bir genel bir catch bloğu içermez. Bu kural göz ardı eder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] derlemeler.

## <a name="rule-description"></a>Kural açıklaması

İşleme bir catch bloğu <xref:System.Exception> ortak dil belirtimi (CLS) uyumlu özel durumların tamamını yakalar. Ancak, CLS olmayan uyumlu özel durumları yakalamaz. CLS olmayan uyumlu özel durumlar yerel koddan veya Microsoft tarafından oluşturulan yönetilen koddan Ara dil (MSIL) derleyici. Dikkat edin C# ve [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] derleyiciler CLS olmayan uyumlu özel durum oluşturulmasına izin verme ve [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] CLS olmayan uyumlu özel durumları yakalamaz. Catch bloğu amacı, tüm özel durumları işlemek için ise, aşağıdaki genel bir catch bloğu sözdizimini kullanın.

- C# İÇİN: `catch {}`

- C++: `catch(...) {}` veya `catch(Object^) {}`

Daha önce verilen izinler içindeki yakalama bloğunun kaldırıldığında işlenmemiş CLS olmayan uyumlu özel bir güvenlik sorunu haline gelir. CLS olmayan uyumlu özel durum yakalandı çünkü CLS olmayan uyumlu özel durum oluşturur, kötü amaçlı bir yöntem yükseltilmiş izinlerle çalıştırabilir.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Amaç kaynaklananlar olduğunda bu kural ihlalini düzeltmek için özel durumlar, değiştirin veya bir genel bir catch bloğu ekleyin veya derlemeyi işaretlemek `RuntimeCompatibility(WrapNonExceptionThrows = true)`. İzinleri içindeki yakalama bloğunun kaldırılırsa, yinelenen genel işlevleri catch bloğu. İşleyen yakalama bloğu tüm özel durumları işlemek için hedefi değil ise, yerine <xref:System.Exception> belirli özel durum türlerini işleme catch bloğu ile.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Try bloğu CLS olmayan uyumlu özel durum oluşturabilir herhangi bir deyim içermiyorsa bu kuraldan bir uyarıyı bastırmak güvenlidir. Herhangi bir yerel veya yönetilen kod CLS olmayan uyumlu özel durum oluşturma olasılığı nedeniyle bu bilgi try bloğu içindeki tüm kod yolları'nda yürütülen tüm kod gerektirir. CLS olmayan uyumlu ortak dil çalışma zamanı tarafından özel durumlar değil dikkat edin.

## <a name="example-1"></a>Örnek 1

Aşağıdaki örnek, CLS olmayan uyumlu özel durum oluşturur bir MSIL sınıfı gösterir.

```cpp
.assembly ThrowNonClsCompliantException {}
.class public auto ansi beforefieldinit ThrowsExceptions
{
   .method public hidebysig static void
         ThrowNonClsException() cil managed
   {
      .maxstack  1
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()
      IL_0005:  throw
   }
}
```

## <a name="example-2"></a>Örnek 2

Aşağıdaki örnek, kural karşılayan bir genel bir catch bloğu içeren bir yöntemi gösterir.

[!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]

Önceki örneklerde şu şekilde derleyin.

```cpp
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>İlgili kuralları

[CA1031: Genel özel durum türlerini yakalamayın](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durumlar ve Özel Durum İşleme](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)
- [Ilasm.exe (IL Derleyici)](/dotnet/framework/tools/ilasm-exe-il-assembler)
- [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](/dotnet/standard/language-independence-and-language-independent-components)