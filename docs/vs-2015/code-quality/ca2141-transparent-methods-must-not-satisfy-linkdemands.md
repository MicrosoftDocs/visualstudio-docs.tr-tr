---
title: "CA2141: Transparent yöntemleri linkdemands'i karşılamamalıdır | Microsoft Docs"
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
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3e5e34f0b207bc89b4f8928bff999c71f5d6c403
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939325"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141:Transparent yöntemleri LinkDemands'i karşılamamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Saydam güvenlik yöntemi ile işaretlenmiş derlemedeki bir yöntemi çağırır <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği (APTCA) veya saydam güvenlik yöntemi karşılayan bir <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` bir tür ya da yöntem için.

## <a name="rule-description"></a>Kural Tanımı
 Bir LinkDemand karşılamadığınızı yanlışlıkla ayrıcalıkların yükseltilmesine neden güvenlik duyarlı işlem var. Güvenlik açısından kritik kodu aynı güvenlik denetim gereksinimlerine tabi olduğundan güvenliği saydam kod LinkDemands, karşılamalıdır değil. Saydam yöntemler güvenlik kural kümesi düzey 1 derlemelerde, performans sorunlarına yol açabilir çalışma zamanında tüm talepleri dönüştürülecek karşılayan tüm LinkDemands neden olur. Güvenlik kuralı kümesi Düzey 2 derlemeler, saydam yöntemleri bir LinkDemand karşılar çalışırsanız, just-ın-time (JIT) derleyicinin derleme başarısız olur.

 Bu düzey 2 güvenlik, bir LinkDemand karşılar veya APTCA olmayan derlemede bir yöntemi çağırmak için bir güvenlik saydam yöntem denemeleridir usee derlemelerde başlatır bir <xref:System.MethodAccessException>; düzey 1 derlemelerde LinkDemand tam isteğe bağlı olur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için erişim yöntemi işaretlemek <xref:System.Security.SecurityCriticalAttribute> veya <xref:System.Security.SecuritySafeCriticalAttribute> özniteliği ya da LinkDemand erişilen yönteminden kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Bu örnekte, bir LinkDemand içeren bir yöntem çağırmak saydam bir yöntem çalışır. Bu kural, bu kodu ateşlenir.

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2141.transparentmethodsmustnotsatisfylinkdemands/cs/ca2141 - transparentmethodsmustnotsatisfylinkdemands.cs#1)]



