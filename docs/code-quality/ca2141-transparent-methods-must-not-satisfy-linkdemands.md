---
title: CA2141:Transparent yöntemleri LinkDemands'i karşılamamalıdır
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 21e112ee1236d711e2f62a70c91a6b7bce993b33
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880032"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141:Transparent yöntemleri LinkDemands'i karşılamamalıdır

|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Saydam güvenlik yöntemi ile işaretlenmiş derlemedeki bir yöntemi çağırır <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği (APTCA) veya saydam güvenlik yöntemi karşılayan bir <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` bir tür ya da yöntem için.

## <a name="rule-description"></a>Kural açıklaması
 Bir LinkDemand karşılamadığınızı yanlışlıkla ayrıcalıkların yükseltilmesine neden olabilecek bir güvenlik hassas bir işlemdir. Güvenlik açısından kritik kodu aynı güvenlik denetim gereksinimlerine tabi olduğundan güvenliği saydam kod LinkDemands, karşılamalıdır değil. Saydam yöntemler güvenlik kural kümesi düzey 1 derlemelerde, performans sorunlarına yol açabilir çalışma zamanında tüm talepleri dönüştürülecek karşılayan tüm LinkDemands neden olur. Güvenlik kuralı kümesi Düzey 2 derlemeler, saydam yöntemleri bir LinkDemand karşılar çalışırsanız, just-ın-time (JIT) derleyicinin derleme başarısız olur.

 Bir LinkDemand karşılar veya APTCA olmayan derlemede bir yöntemi çağırmak için bir güvenlik saydam yöntem denemeleridir Düzey 2 güvenlik derlemelerde başlatır bir <xref:System.MethodAccessException>; düzey 1 derlemelerde LinkDemand tam isteğe bağlı olur.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için erişim yöntemi işaretlemek <xref:System.Security.SecurityCriticalAttribute> veya <xref:System.Security.SecuritySafeCriticalAttribute> özniteliği ya da LinkDemand erişilen yönteminden kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Bu örnekte, bir LinkDemand içeren bir yöntem çağırmak saydam bir yöntem çalışır. Bu kural, bu kodu ateşlenir.

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]