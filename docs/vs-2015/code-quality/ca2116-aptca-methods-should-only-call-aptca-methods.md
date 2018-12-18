---
title: 'CA2116: APTCA yöntemleri yalnızca APTCA yöntemlerini çağırmalıdır | Microsoft Docs'
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
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 766de62f4781dc7ce164155a2090ffabac913a22
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819556"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116Ç APTCA yöntemleri yalnızca APTCA yöntemlerini çağırmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bir derlemeye bir yöntemde <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> özniteliği özniteliğine sahip bir derlemede bir yöntemi çağırır.

## <a name="rule-description"></a>Kural Tanımı
 Varsayılan olarak, ortak veya korumalı yöntem tanımlayıcı ada sahip derlemelerde örtük olarak tarafından korunan bir [bağlantı talepleri](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) tam güven için; yalnızca tam olarak güvenilen Arayanların bir katı adlı derleme erişim sağlayabilir. Tanımlayıcı adlandırılmış derlemeler ile işaretlenen <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği (APTCA) Bu koruma sahip değil. Öznitelik yalnızca intranet veya internette çalıştırılan kod gibi tam güven derleme üstlenir bağlantı talebi, devre dışı bırakır.

 APTCA özniteliği tam olarak güvenilen bir derlemede yapılandırıldığında ve derleme, kodu kısmen güvenilmeyen çağrıcılara izin vermeyen başka bir derlemede yürütür, güvenlik yararlanması mümkündür. İki yöntem `M1` ve `M2` aşağıdaki koşullara uyması, zararlı çağıranlar yöntemi kullanabileceğiniz `M1` korur örtük tam güven bağlantı talebi atlamak için `M2`:

- `M1` Genel bir yöntem APTCA özniteliği tam olarak güvenilen bir derlemede bildirilmiş.

- `M1` bir yöntemi çağıran `M2` dışında `M1`ait derleme.

- `M2`kişinin derleme APTCA özniteliği yok ve bu nedenle, kısmen güvenilen Arayanların tarafınıza sağladığı veya müşteriler yürütülmemesi.

  Kısmen güvenilen bir çağıranın `X` yöntemi çağırabilirsiniz `M1`, neden `M1` çağrılacak `M2`. Çünkü `M2` APTCA özniteliği veya onun şu anki çağırıcı sahip değil (`M1`); tam güven için bağlantı talebi karşılamalıdır `M1` tam güvene sahip ve bu nedenle bu denetimi karşılar. Güvenlik riski çünkü `X` korur bağlantı talebi karşılamadığınızı içinde yer almaz `M2` güvenilmeyen çağıranlar öğesinden. Bu nedenle, özniteliğine sahip olmayan yöntemleri APTCA özniteliğine sahip yöntemleri çağırmamalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 APCTA öznitelik gerekliyse, isteğe bağlı tam güven bütünleştirilmiş koda çağıran yöntemin korumak için kullanın. Tam izinler yönteminizi tarafından sunulan işlevselliği, isteğe bağlıdır. Mümkünse, alttaki işlevsellik kısmen güvenilen arayanlara gösterilmez emin olmak tam güven için talep yöntemi koruyun. Bu mümkün değilse, etkili bir şekilde sunulan işlevlerini koruyan bir izin kümesi seçin. Talepleri hakkında daha fazla bilgi için bkz: [taleplerini](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48).

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Güvenli bir şekilde bu kuraldan bir uyarıyı bastırmak için yönteminizi tarafından kullanıma sunulan işlevselliğini doğrudan veya dolaylı olarak hassas bilgileri, işlemler veya yıkıcı bir şekilde kullanılabilir kaynaklara erişmek bir çağırıcıya izin vermeyen emin emin olmanız gerekir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kural tarafından algılanan güvenlik açığı göstermek için iki derleme ve test uygulamasını kullanır. İlk derleme APTCA özniteliği yok ve kısmen güvenilen arayanlar için erişilebilir olmamalıdır (tarafından temsil edilen `M2` önceki tartışmada).

 [!code-csharp[FxCop.Security.NoAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptca/cs/FxCop.Security.NoAptca.cs#1)]

## <a name="example"></a>Örnek
 İkinci derleme tam olarak güvenilirdir ve kısmen güvenilen arayanlara izin verir (tarafından temsil edilen `M1` önceki tartışmada).

 [!code-csharp[FxCop.Security.YesAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptca/cs/FxCop.Security.YesAptca.cs#1)]

## <a name="example"></a>Örnek
 Test uygulaması (tarafından temsil edilen `X` önceki tartışmada) kısmen güvenilir.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaMethods/cs/FxCop.Security.TestAptcaMethods.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **Tam güven: istek için istek başarısız oldu. ** 
 **ClassRequiringFullTrust.DoWork çağrıldı.**
## <a name="related-rules"></a>İlgili kuralları
 [CA2117: APTCA türleri yalnızca APTCA taban türlerini genişletmelidir](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Güvenli kodlama yönergeleri](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [kısmen güvenilen kod tarafından çağrılabilen .NET Framework derlemeleri](http://msdn.microsoft.com/en-us/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [güvenilen kod kitaplıklarından kısmen kullanarak](http://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [taleplerini](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48) [Bağlantı talepleri](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [veri ve modelleme](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



