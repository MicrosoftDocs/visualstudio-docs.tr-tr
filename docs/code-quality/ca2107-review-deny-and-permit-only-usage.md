---
title: 'CA2107: Gözden geçirmeyi reddet ve yalnızca kullanımına izin ver'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4324805c90c3a0f1b8dbfddcdfe277c5c8a2fd05
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49868046"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Gözden geçirmeyi reddet ve yalnızca kullanımına izin ver

|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bir yöntem PermitOnly veya reddetme güvenlik eylem belirten bir güvenlik denetimi içerir.

## <a name="rule-description"></a>Kural açıklaması
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> Güvenlik eylemi yalnızca .NET Framework güvenliğinin Gelişmiş bir bilgiye sahip olan olanlar tarafından kullanılmalıdır. Bu güvenlik eylemlerini kullanan kod güvenlik incelemesi altından geçmelidir.

 Reddetmek için bir güvenlik talebi karşılamak üzere oluşuyor yığın ilerlemesi varsayılan davranışını değiştirir. Çağrı yığınında çağıranlar, gerçek izinlerinden reddeden yöntem süresince verilmelidir değil izinleri belirtmenize olanak tanır. Yığın ilerlemesi Reddet tarafından güvenli bir yöntem algılar ve talep edilen izni reddedildi izinler eklenirse, yığın ilerlemesi başarısız olursa. PermitOnly ayrıca yığın ilerlemesi varsayılan davranışını değiştirir. Çağıranlar izinlerine bakılmaksızın verilebilecek izinleri belirlemek kod sağlar. Yığın ilerlemesi PermitOnly tarafından güvenli hale getirilmiş bir yöntem algılar ve talep edilen izni PermitOnly tarafından belirtilen izinler dahil edilmemişse, yığın ilerlemesi başarısız olursa.

 Bu eylemleri bağımlı kod kendi sınırlı yararlılığını ve ince davranışı nedeniyle güvenlik açıklarını dikkatlice değerlendirilmelidir. Aşağıdakileri göz önünde bulundurun:

- [Bağlantı talepleri](/dotnet/framework/misc/link-demands) izin verme ya da PermitOnly tarafından etkilenmez.

- Yığın ilerlemesi neden olan isteğe bağlı olarak aynı yığın çerçevesinde izin verme ya da PermitOnly ortaya çıkarsa, güvenlik eylemleri bir etkisi yoktur.

- Yol tabanlı izinler oluşturmak için kullanılan değerleri genellikle birden çok yolla belirtilebilir. Yolun bir form erişimi reddetmeden tüm formlara erişimi reddet değil. Örneğin, bir dosya paylaşımı, \\\Server\Share bir ağ sürücüsünde bir dosya paylaşımında erişimini X:, eşlenmiş durumda, engellemelisiniz \\\Server\Share\File X:\File ve dosyaya erişen her bir yol.

- Bir <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> reddetme ya da PermitOnly ulaşılmadan önceki bir yığın ilerlemesi sonlandırabilirsiniz.

- Reddetme herhangi bir etkisi, çağıran Reddet tarafından engellenen izni, yani, çağıran korumalı kaynağa doğrudan Reddet atlayarak erişebilirsiniz. Benzer şekilde, çağırana reddedilen iznine sahip değil, yığın ilerlemesi izin verme başarısız.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu güvenlik eylemlerini kullanımı bir ihlali neden olur. Bir ihlali gidermek için bu güvenlik eylemlerini kullanmayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Yalnızca bir güvenlik incelemesi tamamladıktan sonra bu kuraldan bir uyarıyı gizler.

## <a name="example-1"></a>Örnek 1
 Aşağıdaki örnek, bazı kısıtlamalar Reddet gösterir.

 Aşağıdaki kitaplık korumak güvenlik taleplerini dışında aynı olan iki yöntem sahip bir sınıf içerir.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]

## <a name="example-2"></a>Örnek 2
 Aşağıdaki uygulama Kitaplığı'ndan güvenli yöntemlere izin verme etkilerini gösterir.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_2.cs)]

Bu örnek aşağıdaki çıktıyı üretir:

```txt
Demand: Caller's Deny has no effect on Demand with the asserted permission.
LinkDemand: Caller's Deny has no effect on LinkDemand with the asserted permission.
LinkDemand: Caller's Deny has no effect with LinkDemand-protected code.
LinkDemand: This Deny has no effect with LinkDemand-protected code.
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>
- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
- <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
- [Güvenli Kodlama Yönergeleri](/dotnet/standard/security/secure-coding-guidelines)