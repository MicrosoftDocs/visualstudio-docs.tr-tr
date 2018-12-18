---
title: 'CA2147: Saydam türler güvenlik bildirimlerini kullanmamalıdır'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3f701a0e39124327c897043590b318cb6e645c1f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923803"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147: Saydam türler güvenlik bildirimlerini kullanmamalıdır

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Olarak işaretlenmiş kod <xref:System.Security.SecurityTransparentAttribute> onay için yeterli izinlerin verilmiş olmasını garanti etmez.

## <a name="rule-description"></a>Kural açıklaması
 Bu kural, tüm yöntemler ve türleri ya da % 100 saydam veya karma saydam/kritik öneme sahiptir ve bildirim temelli veya kesinlik temelli kullanımı bayrakları bir derleme çözümler <xref:System.Security.CodeAccessPermission.Assert%2A>.

 Çalışma zamanında, çağrıları <xref:System.Security.CodeAccessPermission.Assert%2A> saydam koddan neden olacak bir <xref:System.InvalidOperationException> oluşturulması için. Bu, hem de % 100 saydam derlemeleri ve ayrıca burada bir yöntem veya tür saydam olarak bildirilmiş ancak bildirim temelli veya kesinlik temelli bir onay içerir saydam/kritik karma derlemelerdeki ortaya çıkabilir.

 Adlı bir özellik .NET Framework 2.0 sunulan *saydamlık*. Her bir yöntem, alanlar, arabirimler, sınıflar ve türleri, saydam veya kritik olabilir.

 Saydam kod güvenlik ayrıcalıklarını izin verilmiyor. Bu nedenle, tüm izinleri verilir veya bu talep kodlardan otomatik olarak çağıran ya da konak uygulama etki alanına geçirilir. İndirmeyi örnekler Asserts LinkDemands, SuppressUnmanagedCode, ve `unsafe` kod.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Sorunu çözmek için ya da onay ile çağıran kodu işaretlemek <xref:System.Security.SecurityCriticalAttribute>, onay Kaldır.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Bu kural bir iletiden bastırmayın.

## <a name="example"></a>Örnek
 Bu kod başarısız olur `SecurityTestClass` saydam olduğunda `Assert` yöntem bir <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]

## <a name="example"></a>Örnek
 Kod incelemesi SecurityTransparentMethod yöntemi aşağıdaki örnekte bir seçenektir ve yöntem yükseltme için güvenli olarak kabul edilir, SecurityTransparentMethod güvenli-kritik ile işaretleyin. Bu, ayrıntılı, tam ve hatasız güvenlik denetim yöntemi hiçbir çağrı Assert altındaki yöntemin içindeki ortaya çıkarmayı birlikte gerçekleştirilmelidir gerektirir:

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]

 Başka bir seçenek Assert koddan kaldırın ve herhangi bir sonraki dosya Itanium tabanlı sistemler için g/ç izni taleplerin akışı SecurityTransparentMethod ötesinde çağırana izin oluşturmaktır. Bu, güvenlik denetimleri sağlar. İzin istekleri çağıran ve/veya bir uygulama etki alanı akış çünkü bu durumda, hiçbir güvenlik denetimi, gereklidir. İzin istekleri yakından barındırma ortamı ve kod kaynağı izin verir, güvenlik ilkesi aracılığıyla denetlenir.

## <a name="see-also"></a>Ayrıca bkz.
 [Güvenlik Uyarıları](../code-quality/security-warnings.md)