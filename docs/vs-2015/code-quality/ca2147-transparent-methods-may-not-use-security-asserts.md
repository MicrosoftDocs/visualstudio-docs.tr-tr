---
title: 'CA2147: Saydam yöntemler güvenlik kullanamaz onaylar | Microsoft Docs'
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
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6542a2063d076cb57750015039f413b2faf4bca4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921645"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: Saydam türler güvenlik bildirimlerini kullanmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Olarak işaretlenmiş kod <xref:System.Security.SecurityTransparentAttribute> onay için yeterli izinlerin verilmiş olmasını garanti etmez.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, tüm yöntemler ve türleri ya da % 100 saydam veya karma saydam/kritik olan ve bildirim temelli veya kesinlik temelli kullanımı bayrakları bir derlemede çözümler <xref:System.Security.CodeAccessPermission.Assert%2A>.

 Çalışma zamanında, çağrıları <xref:System.Security.CodeAccessPermission.Assert%2A> saydam koddan neden olacak bir <xref:System.InvalidOperationException> oluşturulması için. Bu, hem de % 100 saydam derlemeleri ve ayrıca burada bir yöntem veya tür saydam olarak bildirilmiş ancak bildirim temelli veya kesinlik temelli bir onay içerir saydam/kritik karma derlemelerdeki ortaya çıkabilir.

 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 kullanılmaya adlı bir özellik *saydamlık*. Her bir yöntem, alanlar, arabirimler, sınıflar ve türleri, saydam veya kritik olabilir.

 Saydam kod güvenlik ayrıcalıklarını izin verilmiyor. Bu nedenle, tüm izinleri verilir veya bu talep kodlardan otomatik olarak çağıran ya da konak uygulama etki alanına geçirilir. İndirmeyi örnekler Asserts LinkDemands, SuppressUnmanagedCode, ve `unsafe` kod.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Sorunu çözmek için ya da onay ile çağıran kod işaretleme <xref:System.Security.SecurityCriticalAttribute>, onay Kaldır.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kural bir iletiden bastırmayın.

## <a name="example"></a>Örnek
 Bu kod başarısız olur `SecurityTestClass` saydam olduğunda `Assert` yöntem bir <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>Örnek
 Kod incelemesi aşağıdaki örnekte SecurityTransparentMethod yöntemi için bir seçenek olan ve yöntem yükseltme için güvenli olarak kabul edilir, SecurityTransparentMethod işaretleyin ile güvenli-kritik bu gerektiren ayrıntılı, tam ve hatasız bir güvenlik hiçbir çağrı Assert altındaki yöntemin içindeki ortaya çıkarmayı birlikte yöntemi denetim gerçekleştirilmesi gerekir:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 Başka bir seçenek Assert koddan kaldırın ve herhangi bir sonraki dosya Itanium tabanlı sistemler için g/ç izni taleplerin akışı SecurityTransparentMethod ötesinde çağırana izin oluşturmaktır. Bu, güvenlik denetimleri sağlar. İzni taleplerini arayan ve/veya bir uygulama etki alanı akış çünkü bu durumda, hiçbir güvenlik denetim genellikle yeterli olur. İzin istekleri yakından barındırma ortamı ve kod kaynağı izin verir, güvenlik ilkesi aracılığıyla denetlenir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Güvenlik Uyarıları](../code-quality/security-warnings.md)



