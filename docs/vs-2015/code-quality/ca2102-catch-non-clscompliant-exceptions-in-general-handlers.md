---
title: 'CA2102: CLSCompliant olmayan özel durumları Genel işleyiciler içinde yakalayın | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5c2797b32bbcabd1c63fbfd510aec05c8bf54d21
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877432"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: CLSCompliant olmayan özel durumları genel işleyiciler içinde yakalayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 İle işaretlenmiş derlemedeki bir üye <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> veya işaretlenmiş `RuntimeCompatibility(WrapNonExceptionThrows = false)` işleyen yakalama bloğu içerir <xref:System.Exception?displayProperty=fullName> ve hemen arkasından bir genel bir catch bloğu içermez. Bu kural göz ardı eder [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] derlemeler.

## <a name="rule-description"></a>Kural Tanımı
 İşleme bir catch bloğu <xref:System.Exception> ortak dil belirtimi (CLS) uyumlu özel durumların tamamını yakalar. Ancak, CLS olmayan uyumlu özel durumları yakalamaz. CLS olmayan uyumlu özel durumlar yerel koddan veya Microsoft tarafından oluşturulan yönetilen koddan Ara dil (MSIL) derleyici. Dikkat edin C# ve [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] derleyiciler CLS olmayan uyumlu özel durum oluşturulmasına izin verme ve [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] CLS olmayan uyumlu özel durumları yakalamaz. Catch bloğu amacı, tüm özel durumları işlemek için ise, aşağıdaki genel bir catch bloğu sözdizimini kullanın.

- C# İÇİN: `catch {}`

- C++: `catch(...) {}` veya `catch(Object^) {}`

  Daha önce verilen izinler içindeki yakalama bloğunun kaldırıldığında işlenmemiş CLS olmayan uyumlu özel bir güvenlik sorunu haline gelir. CLS olmayan uyumlu özel durum yakalandı çünkü CLS olmayan uyumlu özel durum oluşturur, kötü amaçlı bir yöntem yükseltilmiş izinlerle çalıştırabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Amaç kaynaklananlar olduğunda bu kural ihlalini düzeltmek için özel durumlar, değiştirin veya bir genel bir catch bloğu ekleyin veya derlemeyi işaretlemek `RuntimeCompatibility(WrapNonExceptionThrows = true)`. İzinleri içindeki yakalama bloğunun kaldırılırsa, yinelenen genel işlevleri catch bloğu. İşleyen yakalama bloğu tüm özel durumları işlemek için hedefi değil ise, yerine <xref:System.Exception> belirli özel durum türlerini işleme catch bloğu ile.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Try bloğu CLS olmayan uyumlu özel durum oluşturabilir herhangi bir deyim içermiyorsa bu kuraldan bir uyarıyı bastırmak güvenlidir. Herhangi bir yerel veya yönetilen kod CLS olmayan uyumlu özel durum oluşturma olasılığı nedeniyle bu bilgi try bloğu içindeki tüm kod yolları'nda yürütülen tüm kod gerektirir. CLS olmayan uyumlu ortak dil çalışma zamanı tarafından özel durumlar değil dikkat edin.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, CLS olmayan uyumlu özel durum oluşturur bir MSIL sınıfı gösterir.

```
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

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kural karşılayan bir genel bir catch bloğu içeren bir yöntemi gösterir.

 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.CatchNonClsCompliantException/cs/FxCop.Security.CatchNonClsCompliantException.cs#1)]

 Önceki örneklerde şu şekilde derleyin.

```
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>İlgili kuralları
 [CA1031: Genel özel durum türlerini yakalamayın](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Özel durumlar ve özel durum işleme](http://msdn.microsoft.com/library/0001887f-4fa2-47e2-8034-2819477e2344) [Ilasm.exe (IL derleyici)](http://msdn.microsoft.com/library/4ca3a4f0-4400-47ce-8936-8e219961c76f) [güvenlik denetimlerini geçersiz kılma](http://msdn.microsoft.com/en-us/4acdeff5-fc05-41bf-8505-7387cdbfca28) [dil bağımsızlığı ve dilden bağımsız bileşenler](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)



