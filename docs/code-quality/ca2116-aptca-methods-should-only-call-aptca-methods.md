---
title: CA2116Ç APTCA yöntemleri yalnızca APTCA yöntemlerini çağırmalıdır
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7decf94644bdb055f38c267c945dc0dcc813550a
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547925"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116Ç APTCA yöntemleri yalnızca APTCA yöntemlerini çağırmalıdır

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep

Bir derlemeye bir yöntemde <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> özniteliği özniteliğine sahip bir derlemede bir yöntemi çağırır.

## <a name="rule-description"></a>Kural açıklaması

Varsayılan olarak, ortak veya korumalı yöntem tanımlayıcı ada sahip derlemelerde örtük olarak tarafından korunan bir [bağlantı talepleri](/dotnet/framework/misc/link-demands) tam güven için; yalnızca tam olarak güvenilen Arayanların bir katı adlı derleme erişim sağlayabilir. Tanımlayıcı adlandırılmış derlemeler ile işaretlenen <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği (APTCA) Bu koruma sahip değil. Öznitelik yalnızca intranet veya internette çalıştırılan kod gibi tam güven derleme üstlenir bağlantı talebi, devre dışı bırakır.

APTCA özniteliği tam olarak güvenilen bir derlemede yapılandırıldığında ve derleme, kodu kısmen güvenilmeyen çağrıcılara izin vermeyen başka bir derlemede yürütür, güvenlik yararlanması mümkündür. İki yöntem `M1` ve `M2` aşağıdaki koşullara uyması, zararlı çağıranlar yöntemi kullanabileceğiniz `M1` korur örtük tam güven bağlantı talebi atlamak için `M2`:

- `M1` Genel bir yöntem APTCA özniteliği tam olarak güvenilen bir derlemede bildirilmiş.

- `M1` bir yöntemi çağıran `M2` dışında `M1`ait derleme.

- `M2`kişinin derleme APTCA özniteliği yok ve bu nedenle, kısmen güvenilen Arayanların tarafınıza sağladığı veya müşteriler yürütülmemesi.

Kısmen güvenilen bir çağıranın `X` yöntemi çağırabilirsiniz `M1`, neden `M1` çağrılacak `M2`. Çünkü `M2` APTCA özniteliği veya onun şu anki çağırıcı sahip değil (`M1`); tam güven için bağlantı talebi karşılamalıdır `M1` tam güvene sahip ve bu nedenle bu denetimi karşılar. Güvenlik riski çünkü `X` korur bağlantı talebi karşılamadığınızı içinde yer almaz `M2` güvenilmeyen çağıranlar öğesinden. Bu nedenle, özniteliğine sahip olmayan yöntemleri APTCA özniteliğine sahip yöntemleri çağırmamalıdır.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 APCTA öznitelik gerekliyse, isteğe bağlı tam güven bütünleştirilmiş koda çağıran yöntemin korumak için kullanın. Tam izinler yönteminizi tarafından sunulan işlevselliği, isteğe bağlıdır. Mümkünse, alttaki işlevsellik kısmen güvenilen arayanlara gösterilmez emin olmak tam güven için talep yöntemi koruyun. Bu mümkün değilse, etkili bir şekilde sunulan işlevlerini koruyan bir izin kümesi seçin.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Güvenli bir şekilde bu kuraldan bir uyarıyı bastırmak için yönteminizi tarafından kullanıma sunulan işlevselliğini doğrudan veya dolaylı olarak hassas bilgileri, işlemler veya yıkıcı bir şekilde kullanılabilir kaynaklara erişmek bir çağırıcıya izin vermeyen emin emin olmanız gerekir.

## <a name="example-1"></a>Örnek 1
 Aşağıdaki örnek, bu kural tarafından algılanan güvenlik açığı göstermek için iki derleme ve test uygulamasını kullanır. İlk derleme APTCA özniteliği yok ve kısmen güvenilen arayanlar için erişilebilir olmamalıdır (tarafından temsil edilen `M2` önceki tartışmada).

 [!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]

## <a name="example-2"></a>Örnek 2
 İkinci derleme tam olarak güvenilirdir ve kısmen güvenilen arayanlara izin verir (tarafından temsil edilen `M1` önceki tartışmada).

 [!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]

## <a name="example-3"></a>Örnek 3
 Test uygulaması (tarafından temsil edilen `X` önceki tartışmada) kısmen güvenilir.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]

Bu örnek aşağıdaki çıktıyı üretir:

```txt
Demand for full trust:Request failed.
ClassRequiringFullTrust.DoWork was called.
```

## <a name="related-rules"></a>İlgili kuralları

- [CA2117: APTCA türleri yalnızca APTCA taban türlerini genişletmelidir](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](/dotnet/standard/security/secure-coding-guidelines)
- [Kısmen güvenilen koddan kitaplıkları kullanma](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
- [Bağlantı talepleri](/dotnet/framework/misc/link-demands)
- [Veri ve Modelleme](/dotnet/framework/data/index)