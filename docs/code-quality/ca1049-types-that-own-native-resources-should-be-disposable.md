---
title: 'CA1049: Yerel kaynaklara sahip olan türler atılabilir olmalıdır'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- cplusplus
ms.openlocfilehash: f9a2eeb032951df86d38075220c14fe98488edef
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45552002"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Yerel kaynaklara sahip olan türler atılabilir olmalıdır

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep

Bir türe başvuran bir <xref:System.IntPtr?displayProperty=fullName> alan, bir <xref:System.UIntPtr?displayProperty=fullName> alanın veya bir <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> alan, ancak uygulamıyor <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Kural açıklaması

Bu kural, varsayar <xref:System.IntPtr>, <xref:System.UIntPtr>, ve <xref:System.Runtime.InteropServices.HandleRef> alanları yönetilmeyen kaynakları işaretçileri depolayın. Yönetilmeyen kaynakların tahsis türlerini uygulamanız gerekir <xref:System.IDisposable> bağlı kaynakları serbest bırakmak ve kaynakları tutan nesnelerin yaşam süreleri kısaltmak için arayanlara izin vermek için.

Yönetilmeyen kaynakları temizlemek için önerilen tasarım desenini örtük ve kullanarak bu kaynakları serbest bırakmak için açık bir yol sağlamaktır <xref:System.Object.Finalize%2A?displayProperty=fullName> yöntemi ve <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> yöntemi, sırasıyla. Çöp toplayıcı çağrıları <xref:System.Object.Finalize%2A> nesnenin artık erişilebilir olması belirlendikten sonra bazı belirsiz zaman bir nesnenin yöntemi. Sonra <xref:System.Object.Finalize%2A> çağrılır, ek bir çöp toplama, nesne için gereklidir. <xref:System.IDisposable.Dispose%2A> Yöntemi arayan açıkça bağlı kaynakları çöp Toplayıcıya bırakılırsa serbest bırakılır'den önceki kaynakları serbest bırakmak sağlar. Yönetilmeyen kaynakları temizler sonra <xref:System.IDisposable.Dispose%2A> çağırmalıdır <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> biliyor atıktoplayıcı olanak yöntemi <xref:System.Object.Finalize%2A> çağrılacak; artık sahip bu ek çöp toplama işlemine ihtiyacı ortadan kaldırır ve kısaltır nesne ömrü.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için uygulama <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Yönetilmeyen bir kaynağı türü başvurmuyorsa bu kuraldan bir uyarıyı bastırmak güvenlidir. Aksi takdirde, bu kuraldan bir uyarıyı çünkü bastırmayın uygulamak için hata <xref:System.IDisposable> yönetilmeyen kaynakları kullanılamıyor veya kapatacağı kilitlenmesine neden olabilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, uygulayan bir tür gösterir <xref:System.IDisposable> bir yönetilmeyen kaynağı temizlemek için.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>İlgili kuralları
 [CA2115: Yerel kaynaklar kullanırken GC.KeepAlive'ı çağırın](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: GC.SuppressFinalize öğesini doğru çağırın](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: Atılabilir türler sonlandırıcıyı bildirmelidir](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: Atılabilir alanlara sahip olan türler atılabilir olmalıdır](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen Kaynakları Temizleme](/dotnet/standard/garbage-collection/unmanaged)
- [Dispose Deseni](/dotnet/standard/design-guidelines/dispose-pattern)