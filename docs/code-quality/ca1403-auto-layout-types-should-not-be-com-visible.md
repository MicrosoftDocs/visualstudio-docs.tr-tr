---
title: 'CA1403: Otomatik yerleşim türleri COM görünebilir olmamalıdır'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d84fdd4f352a823614832cc8d5d1b9e57c7a9dfb
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058080"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Otomatik yerleşim türleri COM görünebilir olmamalıdır

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Kategori|Microsoft.Interoperability|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep

Bileşen Nesne Modeli (COM) görünür değer türü ile işaretlenmiş <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> özniteliği kümesine <xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName>.

## <a name="rule-description"></a>Kural açıklaması

<xref:System.Runtime.InteropServices.LayoutKind> Yerleşim türleri, ortak dil çalışma zamanı tarafından yönetilir. Bu tür düzeni belirli bir düzen beklediğiniz COM istemcileri keser .NET Framework sürümleri arasında değiştirebilirsiniz. Varsa <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliği belirtilmezse, C#, Visual Basic ve C++ Derleyicileri belirtin [LayoutKind.Auto](<xref:System.Runtime.InteropServices.LayoutKind.Auto>) değer türleri için.

Aksi takdirde işaretlenmiş sürece, tüm ortak, genel olmayan türleri COM görünür ve tüm genel ve genel türleri COM'a görünmez Ancak, hatalı pozitif sonuçları azaltmak için bu kural türünü açıkça belirtilen COM görünürlüğünü gerektirir. İçeren derleme ile işaretlenmiş olmalıdır <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> kümesine `false` ve tür ile işaretlenmelidir <xref:System.Runtime.InteropServices.ComVisibleAttribute> kümesine `true`.

## <a name="how-to-fix-violations"></a>İhlallerini düzeltmek nasıl

Bu kural ihlal düzeltmek için değerini değiştirme <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliğini [LayoutKind.Explicit](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>) veya [LayoutKind.Sequential](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>), veya türü COM'a görünmez yapma

## <a name="when-to-suppress-warnings"></a>Ne zaman uyarıları bastırma

Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek

Aşağıdaki örnek kuralını ihlal eden bir tür ile kural karşılayan bir tür gösterir.

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>İlgili kuralları

[CA1408: AutoDual ClassInterfaceType kullanma](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Birlikte çalışma için .NET türleri nitelemek](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Yönetilmeyen kod ile birlikte çalışma](/dotnet/framework/interop/index)