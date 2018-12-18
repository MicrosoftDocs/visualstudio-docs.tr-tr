---
title: 'CA1001: atılabilir alanlara sahip türler atılabilir olmalıdır | Microsoft Docs'
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
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a4bde7f20d1e7c93aec7a4a1a3abf44c21659b6e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176455"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Atılabilir alanlara sahip olan türler atılabilir olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|  
|CheckId|CA1001|  
|Kategori|Microsoft.Design|  
|Yeni Değişiklik|Bölünemez - türü derlemenin dışında görünür değilse.<br /><br /> Derlemenin dışında görünür bir tür ise - kesiliyor.|  
  
## <a name="cause"></a>Sebep  
 Bir sınıfı bildirir ve bir örnek alan uygulayan bir <xref:System.IDisposable?displayProperty=fullName> türü ve sınıf uygulamıyor <xref:System.IDisposable>.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Arabirimini uygulayan bir sınıf <xref:System.IDisposable> sahip olduğu yönetilmeyen kaynaklarını silmek için arabirim. Bir örnek alan bir <xref:System.IDisposable> türü, alan bir yönetilmeyen kaynağa sahip olduğunu gösterir. Bildiren bir sınıf bir <xref:System.IDisposable> alan dolaylı olarak bir yönetilmeyen kaynağa sahip ve uygulamalıdır <xref:System.IDisposable> arabirimi. Sınıf doğrudan herhangi bir yönetilmeyen kaynağa sahip değilse, bir sonlandırıcı uygulamamalıdır.  
  
## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?  
 Bu kural ihlalini düzeltmek için uygulama <xref:System.IDisposable> ve <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> yöntem çağrısının <xref:System.IDisposable.Dispose%2A> alan yöntemi.  
  
## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında  
 Bu kuraldan uyarıyı bastırmayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kuralını ihlal eden bir sınıf ve kural uygulayarak karşılayan bir sınıfı gösterir <xref:System.IDisposable>. Sınıf doğrudan herhangi bir yönetilmeyen kaynağa sahibi değildir çünkü sınıfı bir sonlandırıcı uygulamıyor.  
  
 [!code-csharp[FxCop.Design.DisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/cs/FxCop.Design.DisposableFields.cs#1)]
 [!code-vb[FxCop.Design.DisposableFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/vb/FxCop.Design.DisposableFields.vb#1)]  
  
## <a name="related-rules"></a>İlgili kuralları  
 [CA2213: Atılabilen alanlar atılmalıdır](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2216: Atılabilir türler sonlandırıcıyı bildirmelidir](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA2215: Atma yöntemleri taban sınıf atmayı çağırmalıdır](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA1049: Yerel kaynaklara sahip olan türler atılabilir olmalıdır](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

