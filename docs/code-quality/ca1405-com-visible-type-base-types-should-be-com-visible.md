---
title: 'CA1405: COM görünebilir tür taban türler COM görünebilir olmalıdır'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: efaac5fc5b5f8784d204c31e537a5279a81e2699
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548323"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: COM görünebilir tür taban türler COM görünebilir olmalıdır

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Kategori|Microsoft.Interoperability|
|Yeni Değişiklik|DependsOnFix|

## <a name="cause"></a>Sebep
 Bileşen Nesne Modeli (COM) görünen bir tür COM görünür olmayan bir türden türetilir.

## <a name="rule-description"></a>Kural açıklaması
 COM görünebilir tür üyeleri yeni bir sürümde eklediğinde, geçerli sürümüne bağlanan COM istemcilerini bozmayı önlemek için katı yönergelerimiz tarafından uymanız gerekir. COM görünmez bir türün yeni üye eklediğinde, bu COM sürüm oluşturma kurallarını takip ettiğinizden yok varsayılır. Ancak, bir COM görünür türü COM görünmez türünden türetilen ve bir sınıf arabirimi kullanıma sunan <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> veya <xref:System.Runtime.InteropServices.ClassInterfaceType> (varsayılan), temel türün tüm genel üyeleri (bunlar özellikle COM görünmez işaretlenmediği sürece, olacak yedekli) COM'a sunulur Temel türün bir sonraki sürümde yeni üye eklerse, sınıf türetilmiş bir türde arayüze herhangi bir COM istemcileri bozulabilir. COM görünebilir türler COM istemcileri bozucu olasılığını azaltmak için yalnızca COM görünebilir türler türetilmelidir.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için taban türler COM görünebilir veya türetilmiş bir tür COM görünmez yapma.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek kuralını ihlal eden bir tür gösterir.

 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>
- [Yönetilmeyen Kod ile Birlikte Çalışma](/dotnet/framework/interop/index)