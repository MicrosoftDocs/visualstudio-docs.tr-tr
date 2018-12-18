---
title: 'CA1407: COM görünebilir türler içinde statik üyelerden kaçının | Microsoft Docs'
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
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9b3d14351ddb0e7e98c5c93bd1fe62c5b106dca1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889054"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: COM görünebilir türler içinde statik üyelerden kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Kategori|Microsoft.Interoperability|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Özel Bileşen Nesne Modeli (COM) görünür olarak işaretlenmiş bir tür içeren bir `public``static` yöntemi.

## <a name="rule-description"></a>Kural Tanımı
 COM desteklemiyor `static` yöntemleri.

 Bu kural, özellik ve olay erişimcileri, işleç yöntemleri ya da kullanarak işaretlenmiş yöntem aşırı yüklemesi yoksayar <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> özniteliği veya <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> özniteliği.

 Varsayılan olarak, COM görünür şunlardır: derlemeleri, genel tür, genel türlerde ortak örnek üyeleri ve tüm ortak türlerin üyeleri.

 Gerçekleşmesi, bir derleme düzeyi bu kural için <xref:System.Runtime.InteropServices.ComVisibleAttribute> ayarlanmalıdır `false` ve sınıf - <xref:System.Runtime.InteropServices.ComVisibleAttribute> ayarlanmalıdır `true`aşağıdaki kodda gösterildiği gibi.

```csharp
using System;
using System.Runtime.InteropServices;

[assembly: ComVisible(false)]
namespace Samples
{
    [ComVisible(true)]
    public class MyClass
    {
        public static void DoSomething()
        {
        }
    }
}
```

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için aynı işlevselliği sağlayan bir örnek yöntemi kullanmak için tasarım değiştirme `static` yöntemi.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bir COM istemcisi tarafından sağlanan işlevselliğe erişim gerektirmiyorsa, bu kuraldan bir uyarıyı bastırmak güvenlidir `static` yöntemi.

## <a name="example-violation"></a>Örnek ihlali

### <a name="description"></a>Açıklama
 Aşağıdaki örnekte gösterildiği bir `static` bu kuralı ihlal yöntemi.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersViolation/cs/FxCop.Interoperability.ComVisibleStaticMembersViolation.cs#1)]

### <a name="comments"></a>Açıklamalar
 Bu örnekte, **Book.FromPages** COM'dan yöntemi çağrılamaz

## <a name="example-fix"></a>Örnek düzeltme

### <a name="description"></a>Açıklama
 Önceki örnekte ve ihlali gidermek için yöntem bir örnek yöntemi olarak değiştirebilirsiniz, ancak, bu örnekte mantıklı değildir. Açıkça uygulamak için en iyi çözümdür `ComVisible(false)` Temizle yöntemi COM'dan görülen diğer geliştiriciler yapmak için yöntemi

 Aşağıdaki örnek geçerli <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> yöntemi.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersFixed/cs/FxCop.Interoperability.ComVisibleStaticMembersFixed.cs#1)]

## <a name="related-rules"></a>İlgili kuralları
 [CA1017: Derlemeleri ComVisibleAttribute ile işaretleyin](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: Visual Basic 6 istemcileri için Int64 bağımsız değişkenlerinden kaçının](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: COM görünebilir değer türleri içinde genel olmayan alanlardan kaçının](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Yönetilmeyen Kod ile Birlikte Çalışma](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



