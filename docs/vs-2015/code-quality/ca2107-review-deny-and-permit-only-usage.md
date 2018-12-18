---
title: 'CA2107: Gözden geçirmeyi reddetmek ve yalnızca kullanımına izin ver | Microsoft Docs'
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
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f7a82e6b1acdb8eee1d97dcf6f264ebf66343b58
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851124"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Gözden geçirmeyi reddet ve yalnızca kullanımına izin ver
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bir yöntem PermitOnly veya reddetme güvenlik eylem belirten bir güvenlik denetimi içerir.

## <a name="rule-description"></a>Kural Tanımı
 [PermitOnly yöntemini kullanma](http://msdn.microsoft.com/en-us/8c7bdb7f-882f-45b7-908c-6cbaa1767649) ve <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> güvenlik eylemleri yalnızca bir bilgiye sahip olan olanlar tarafından kullanılmalıdır, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] güvenlik. Bu güvenlik eylemlerini kullanan kod güvenlik incelemesi altından geçmelidir.

 Reddetmek için bir güvenlik talebi karşılamak üzere oluşuyor yığın ilerlemesi varsayılan davranışını değiştirir. Çağrı yığınında çağıranlar, gerçek izinlerinden reddeden yöntem süresince verilmelidir değil izinleri belirtmenize olanak tanır. Yığın ilerlemesi Reddet tarafından güvenli bir yöntem algılar ve talep edilen izni reddedildi izinler eklenirse, yığın ilerlemesi başarısız olursa. PermitOnly ayrıca yığın ilerlemesi varsayılan davranışını değiştirir. Çağıranlar izinlerine bakılmaksızın verilebilecek izinleri belirlemek kod sağlar. Yığın ilerlemesi PermitOnly tarafından güvenli hale getirilmiş bir yöntem algılar ve talep edilen izni PermitOnly tarafından belirtilen izinler dahil edilmemişse, yığın ilerlemesi başarısız olursa.

 Bu eylemleri bağımlı kod kendi sınırlı yararlılığını ve ince davranışı nedeniyle güvenlik açıklarını dikkatlice değerlendirilmelidir. Aşağıdakileri göz önünde bulundurun:

-   [Bağlantı talepleri](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) izin verme ya da PermitOnly tarafından etkilenmez.

-   Yığın ilerlemesi neden olan isteğe bağlı olarak aynı yığın çerçevesinde izin verme ya da PermitOnly ortaya çıkarsa, güvenlik eylemleri bir etkisi yoktur.

-   Yol tabanlı izinler oluşturmak için kullanılan değerleri genellikle birden çok yolla belirtilebilir. Yolun bir form erişimi reddetmeden tüm formlara erişimi reddet değil. Örneğin, bir dosya paylaşımı, \\\Server\Share bir ağ sürücüsünde bir dosya paylaşımında erişimini X:, eşlenmiş durumda, engellemelisiniz \\\Server\Share\File X:\File ve dosyaya erişen her bir yol.

-   Bir <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> reddetme ya da PermitOnly ulaşılmadan önceki bir yığın ilerlemesi sonlandırabilirsiniz.

-   Reddetme herhangi bir etkisi, çağıran Reddet tarafından engellenen izni, yani, çağıran korumalı kaynağa doğrudan Reddet atlayarak erişebilirsiniz. Benzer şekilde, çağırana reddedilen iznine sahip değil, yığın ilerlemesi izin verme başarısız.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu güvenlik eylemlerini kullanımı bir ihlali neden olur. Bir ihlali gidermek için bu güvenlik eylemlerini kullanmayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yalnızca bir güvenlik incelemesi tamamladıktan sonra bu kuraldan bir uyarıyı gizler.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bazı kısıtlamalar Reddet gösterir.

 Aşağıdaki kitaplık korumak güvenlik taleplerini dışında aynı olan iki yöntem sahip bir sınıf içerir.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny/cs/FxCop.Security.PermitAndDeny.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama Kitaplığı'ndan güvenli yöntemlere izin verme etkilerini gösterir.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestPermitAndDeny/cs/FxCop.Security.TestPermitAndDeny.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **İsteğe bağlı: Çağıranın Reddet isteğe bağlı olarak onaylanan izni olan etkisi yoktur. ** 
 **LinkDemand: çağıranın Reddet üzerinde hiçbir etkisi LinkDemand olarak onaylanan iznine sahip.** 
 **LinkDemand: çağıranın Reddet LinkDemand ile korunan kodla hiçbir etkisi.** 
 **LinkDemand: Bu Reddet LinkDemand ile korunan kod ile hiçbir etkiye sahiptir.**
## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName><xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
 [Güvenli kodlama yönergeleri](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [güvenlik denetimlerini geçersiz kılma](http://msdn.microsoft.com/en-us/4acdeff5-fc05-41bf-8505-7387cdbfca28) [PermitOnly yöntemini kullanma](http://msdn.microsoft.com/en-us/8c7bdb7f-882f-45b7-908c-6cbaa1767649)



