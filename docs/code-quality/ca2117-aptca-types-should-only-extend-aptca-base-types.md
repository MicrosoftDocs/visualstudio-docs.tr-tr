---
title: 'CA2117: APTCA türleri yalnızca APTCA taban türlerini genişletmelidir'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8dac5acc0b7c7fff02862853bfd996362f80d1cc
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547506"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: APTCA türleri yalnızca APTCA taban türlerini genişletmelidir

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep

Bir ortak veya korumalı tür ile bir derlemede <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> özniteliğine sahip bir derlemede bildirilmiş bir tür özniteliğini devralır.

## <a name="rule-description"></a>Kural açıklaması

Varsayılan olarak, ortak veya korumalı tür tanımlayıcı ada sahip derlemelerde örtük olarak tarafından korunan bir [Inheritancedemand](xref:System.Security.Permissions.SecurityAction#System_Security_Permissions_SecurityAction_InheritanceDemand) tam güven için. Tanımlayıcı adlandırılmış derlemeler ile işaretlenen <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği (APTCA) Bu koruma sahip değil. Öznitelik devralma talebi devre dışı bırakır. Tam güven olmayan türleri tarafından sunulan türleri derlemedeki bir devralma talebi olmadan bildirilen devralınabilir.

APTCA özniteliği tam olarak güvenilen bir derlemede yapılandırıldığında ve derlemedeki tür, kısmen güvenilmeyen çağrıcılara izin vermeyen tür tarafından devralındığında güvenlik yararlanması mümkündür. İki yazdığında `T1` ve `T2` zararlı çağıranlar türü kullanabilir, aşağıdaki koşullara uyması `T1` korur örtük tam güven devralma talebi atlamak için `T2`:

- `T1` bir genel türü APTCA özniteliği tam olarak güvenilen bir derlemede bildirilmiş.

- `T1` bir tür tarafından devralındığında `T2` kendi derlemesi dışında.

- `T2`kişinin derleme APTCA özniteliği yok ve bu nedenle, kısmen güvenilen derlemelerde türlerine göre devralınabilir olmamalıdır.

Kısmen güvenilen bir tür `X` öğesinden devralabilir `T1`, sağlayan, erişim için bildirilen devralınan üyeleri `T2`. Çünkü `T2` APTCA özniteliği, hemen türetilmiş türü yok (`T1`) için tam güven; bir devralma talebi karşılayamaz hale gerekir `T1` tam güvene sahip ve bu nedenle bu denetimi karşılar. Güvenlik riski çünkü `X` koruyan bir devralma talebi karşılamadığınızı içinde yer almaz `T2` güvenilmeyen sınıflara öğesinden. Bu nedenle, APTCA özniteliği türleriyle özniteliğine sahip olmayan türleri geçmemelidir.

Başka bir güvenlik sorunu ve belki de daha yaygın bir tane, türetilmiş bir tür olan (`T1`) Programcı hata, tam güven gerektiren türünden korumalı üyeler açığa çıkarabilir (`T2`). Bu arabirim ortaya çıktığında, güvenilmeyen çağıranlar yalnızca tam olarak güvenilen türleri için kullanması gereken bilgilere erişin.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?

Bir derlemede APTCA özniteliği gerektirmez ihlali tarafından bildirilen türü ise kaldırın.

APTCA özniteliği gerekiyorsa, bir devralma talebi için tam güven türüne ekleyin. Devralma talebi tarafından güvenilmeyen türü devralma karşı korur.

APTCA özniteliği ihlali tarafından bildirilen temel türler derlemeleri ekleyerek bir ihlali gidermek mümkündür. Bunu, ilk derlemelerdeki tüm kod ve derlemeler bağlı olan tüm kod bir yoğun güvenlik incelemesi gerçekleştirme olmadan yapmayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında

Güvenli bir şekilde bu kuraldan bir uyarıyı bastırmak için korumalı üyeleri türünüz tarafından kullanıma sunulan doğrudan veya dolaylı olarak hassas bilgileri, işlem ya da yıkıcı bir şekilde kullanılabilir kaynaklara erişimi güvenilmeyen çağrı yapanların izin vermediğinden emin olmanız gerekir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bu kural tarafından algılanan güvenlik açığı göstermek için iki derleme ve test uygulamasını kullanır. İlk derleme APTCA özniteliği yok ve kısmen güvenilen türlerine göre devralınabilir olmamalıdır (tarafından temsil edilen `T2` önceki tartışmada).

[!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]

Tarafından temsil edilen ikinci derleme `T1` önceki tartışmada tam olarak güvenilirdir ve kısmen güvenilen arayanlara izin verir.

[!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]

Tarafından temsil edilen test türü `X` önceki tartışmada kısmen güvenilen bir derlemedir.

[!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]

Bu örnek aşağıdaki çıktıyı üretir:

```txt
Meet at the shady glen 2/22/2003 12:00:00 AM!
From Test: sunny meadow
Meet at the sunny meadow 2/22/2003 12:00:00 AM!
```

## <a name="related-rules"></a>İlgili kuralları

[CA2116Ç APTCA yöntemleri yalnızca APTCA yöntemlerini çağırmalıdır](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](/dotnet/standard/security/secure-coding-guidelines)
- [Kısmen güvenilen koddan kitaplıkları kullanma](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
