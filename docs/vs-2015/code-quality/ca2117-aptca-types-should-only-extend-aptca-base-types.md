---
title: 'CA2117: APTCA türleri yalnızca APTCA taban türlerini genişletmelidir | Microsoft Docs'
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
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4b069674827ab266b4a4b7a99f81e039d487f6da
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922659"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: APTCA türleri yalnızca APTCA taban türlerini genişletmelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bir ortak veya korumalı tür ile bir derlemede <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> özniteliğine sahip bir derlemede bildirilmiş bir tür özniteliğini devralır.

## <a name="rule-description"></a>Kural Tanımı
 Varsayılan olarak, ortak veya korumalı tür tanımlayıcı ada sahip derlemelerde örtük olarak tarafından korunan bir [devralma taleplerini](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9) tam güven için. Tanımlayıcı adlandırılmış derlemeler ile işaretlenen <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği (APTCA) Bu koruma sahip değil. Öznitelik devralma talebi devre dışı bırakır. Bu, tam güven olmayan türleri tarafından sunulan türleri derlemesinde devralınabilir bildirilen sağlar.

 APTCA özniteliği tam olarak güvenilen bir derlemede yapılandırıldığında ve derlemedeki tür, kısmen güvenilmeyen çağrıcılara izin vermeyen tür tarafından devralındığında güvenlik yararlanması mümkündür. İki yazdığında `T1` ve `T2` zararlı çağıranlar türü kullanabilir, aşağıdaki koşullara uyması `T1` korur örtük tam güven devralma talebi atlamak için `T2`:

- `T1` bir genel türü APTCA özniteliği tam olarak güvenilen bir derlemede bildirilmiş.

- `T1` bir tür tarafından devralındığında `T2` kendi derlemesi dışında.

- `T2`kişinin derleme APTCA özniteliği yok ve bu nedenle, kısmen güvenilen derlemelerde türlerine göre devralınabilir olmamalıdır.

  Kısmen güvenilen bir tür `X` öğesinden devralabilir `T1`, sağlayan, erişim için bildirilen devralınan üyeleri `T2`. Çünkü `T2` APTCA özniteliği, hemen türetilmiş türü yok (`T1`) için tam güven; bir devralma talebi karşılayamaz hale gerekir `T1` tam güvene sahip ve bu nedenle bu denetimi karşılar. Güvenlik riski çünkü `X` koruyan bir devralma talebi karşılamadığınızı içinde yer almaz `T2` güvenilmeyen sınıflara öğesinden. Bu nedenle, APTCA özniteliği türleriyle özniteliğine sahip olmayan türleri geçmemelidir.

  Başka bir güvenlik sorunu ve belki de daha yaygın bir tane, türetilmiş bir tür olan (`T1`) Programcı hata, tam güven gerektiren türünden korumalı üyeler açığa çıkarabilir (`T2`). Bu durumda, güvenilmeyen çağıranlar yalnızca tam olarak güvenilen türleri için kullanması gereken bilgilere erişin.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bir derlemede APTCA özniteliği gerektirmez ihlali tarafından bildirilen türü ise kaldırın.

 APTCA özniteliği gerekiyorsa, bir devralma talebi için tam güven türüne ekleyin. Bu, güvenilmeyen türlerine göre devralma karşı korur.

 APTCA özniteliği ihlali tarafından bildirilen temel türler derlemeleri ekleyerek bir ihlali gidermek mümkündür. Bunu, ilk derlemelerdeki tüm kod ve derlemeler bağlı olan tüm kod bir yoğun güvenlik incelemesi gerçekleştirme olmadan yapmayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Güvenli bir şekilde bu kuraldan bir uyarıyı bastırmak için korumalı üyeleri türünüz tarafından kullanıma sunulan doğrudan veya dolaylı olarak hassas bilgileri, işlem ya da yıkıcı bir şekilde kullanılabilir kaynaklara erişimi güvenilmeyen çağrı yapanların izin vermediğinden emin olmanız gerekir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kural tarafından algılanan güvenlik açığı göstermek için iki derleme ve test uygulamasını kullanır. İlk derleme APTCA özniteliği yok ve kısmen güvenilen türlerine göre devralınabilir olmamalıdır (tarafından temsil edilen `T2` önceki tartışmada).

 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptcaInherit/cs/FxCop.Security.NoAptcaInherit.cs#1)]

## <a name="example"></a>Örnek
 Tarafından temsil edilen ikinci derleme `T1` önceki tartışmada tam olarak güvenilirdir ve kısmen güvenilen arayanlara izin verir.

 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit/cs/FxCop.Security.YesAptcaInherit.cs#1)]

## <a name="example"></a>Örnek
 Tarafından temsil edilen test türü `X` önceki tartışmada kısmen güvenilen bir derlemedir.

 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit/cs/FxCop.Security.TestAptcaInherit.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **Karşılayan shady glen, 22/2/2003 12:00:00 AM'den! ** 
 **Gelen Test: güneşli çayırı**
**karşılayacak güneşli çayırı 22/2/2003 12:00:00 AM'den!**
## <a name="related-rules"></a>İlgili kuralları
 [CA2116Ç APTCA yöntemleri yalnızca APTCA yöntemlerini çağırmalıdır](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Güvenli kodlama yönergeleri](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [kısmen güvenilen kod tarafından çağrılabilen .NET Framework derlemeleri](http://msdn.microsoft.com/en-us/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [güvenilen kod kitaplıklarından kısmen kullanarak](http://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [devralma talepleri](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9)




