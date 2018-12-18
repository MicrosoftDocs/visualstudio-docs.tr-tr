---
title: 'CA1405: COM görünebilir tür taban türler COM görünebilir olmalıdır. | Microsoft Docs'
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
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ee4c7a501a7c48118285ff37844af856cf7b4395
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49840517"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: COM görünebilir tür taban türler COM görünebilir olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Kategori|Microsoft.Interoperability|
|Yeni Değişiklik|DependsOnFix|

## <a name="cause"></a>Sebep
 Bileşen Nesne Modeli (COM) görünen bir tür COM görünür olmayan bir türden türetilir.

## <a name="rule-description"></a>Kural Tanımı
 COM görünebilir tür üyeleri yeni bir sürümde eklediğinde, geçerli sürümüne bağlanan COM istemcilerini bozmayı önlemek için katı yönergelerimiz tarafından uymanız gerekir. COM görünmez bir türün yeni üye eklediğinde, bu COM sürüm oluşturma kurallarını takip ettiğinizden yok varsayılır. Ancak, bir COM görünür türü COM görünmez türünden türetilen ve bir sınıf arabirimi kullanıma sunan <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> veya <xref:System.Runtime.InteropServices.ClassInterfaceType> (varsayılan), temel türün tüm genel üyeleri (bunlar özellikle COM görünmez işaretlenmediği sürece, olacak yedekli) COM'a sunulur Temel türün bir sonraki sürümde yeni üye eklerse, sınıf türetilmiş bir türde arayüze herhangi bir COM istemcileri bozulabilir. COM görünebilir türler COM istemcileri bozucu olasılığını azaltmak için yalnızca COM görünebilir türler türetilmelidir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için taban türler COM görünebilir veya türetilmiş bir tür COM görünmez yapma.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek kuralını ihlal eden bir tür gösterir.

 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/cs/FxCop.Interoperability.ComBaseTypes.cs#1)]
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/vb/FxCop.Interoperability.ComBaseTypes.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName> [Sınıf arabirimine giriş](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024) [yönetilmeyen kod ile birlikte](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



