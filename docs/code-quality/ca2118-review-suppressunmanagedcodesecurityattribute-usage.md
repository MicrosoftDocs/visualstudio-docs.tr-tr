---
title: 'CA2118: SuppressUnmanagedCodeSecurityAttribute kullanımını gözden geçir'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 900abe516ebd07cf5a8849f269f915623500731e
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859711"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: SuppressUnmanagedCodeSecurityAttribute kullanımını gözden geçir

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bir ortak veya korumalı tür veya üye <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> özniteliği.

## <a name="rule-description"></a>Kural açıklaması
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> COM birlikte çalışma veya platform çağırma kullanan yönetilmeyen kodu yürüten üyeler için varsayılan güvenlik sistemi davranışını değiştirir. Genellikle, sistemi yapan bir [veri ve modelleme](/dotnet/framework/data/index) yönetilmeyen kod izni. Bu isteğe bağlı üye her çalıştırılışı için çalışma zamanında gerçekleştirilir ve izin için çağrı yığınında her çağıranı denetler. Özniteliği olduğunda sistemi yapan bir [bağlantı talepleri](/dotnet/framework/misc/link-demands) izni: şu anki çağırıcı izinlerini arayan JIT olarak derlenmiş olduğunda denetlenir.

 Bu öznitelik, öncelikle performansı artırmak için kullanılır; ancak, gelen performans artışı önemli güvenlik riskleri ile gelir. Öznitelik yerel yöntemlerini çağıran ortak üyelerde yerleştirirseniz, çağıranlar çağrı yığını (şu anki çağırıcı dışında) yönetilmeyen kod yönetilmeyen kod yürütme izni gerekmez. Genel üye Eylemler ve giriş işleme bağlı olarak, normalde güvenilir koda kısıtlı erişim işlevini güvenilmez arayanlara izin verebilir.

 .NET Framework Güvenlik denetimleri çağıranlar geçerli işlemin adres alanına doğrudan erişim kazanmasını engellemek için kullanır. Bu öznitelik normal güvenlik atladığından okumak veya yazmak için işlemin belleğinin için kullanılabiliyorsa kodunuzu önemli bir tehlike doğurur. Risk kasıtlı olarak işlem bellek erişimi sağlayan yöntemler için sınırlı olduğunu unutmayın; Mevcut hiçbir senaryoda burada kötü amaçlı kod erişim herhangi bir yolla, örneğin, şaşırtıcı, hatalı biçimlendirilmiş veya geçersiz bir giriş sağlayarak elde edebilirsiniz.

 Yerel bilgisayardan yürütme ya da aşağıdaki gruplardan birinin üyesi olduğu sürece varsayılan güvenlik ilkesini yönetilmeyen kodu bir bütünleştirilmiş kod izni vermez:

- Bilgisayar bölge kodu grubum

- Microsoft güçlü adı kod grubu

- ECMA tanımlayıcı adı kod grubu

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu öznitelik kesinlikle gerekli olduğundan emin olmak için kodunuzu dikkatle inceleyin. İle yönetilen kod güvenlik bilginiz ya da bu özniteliği kullanarak güvenlik etkilerini anlamak değil, kodunuzdan kaldırın. Öznitelik gerekliyse, Arayanların kodunuzu amaçla kullanamazsınız emin olmanız gerekir. Kodunuzu yönetilmeyen kod yürütmek için izinlere sahip değilse, bu öznitelik etkiye sahip değildir ve kaldırılması gerekiyor.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Güvenli bir şekilde bu kuraldan bir uyarıyı bastırmak için kodunuzu yerel işlemler veya yıkıcı bir şekilde kullanılabilecek kaynaklara erişim çağıranlar sağlamaz emin olmanız gerekir.

## <a name="example-1"></a>Örnek 1
 Aşağıdaki örnek bu kuralı ihlal ediyor.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]

## <a name="example-2"></a>Örnek 2
 Aşağıdaki örnekte, `DoWork` yöntemi sağlayan platform çağırma yöntemi genel olarak erişilebilir kod yolu `FormatHardDisk`.

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]

## <a name="example-3"></a>Örnek 3
 Aşağıdaki örnekte, genel yöntem `DoDangerousThing` bir ihlaline neden olur. İhlali gidermek için `DoDangerousThing` özel yapılmalıdır ve erişimi olmalıdır bir güvenlik talebi tarafından güvenli bir genel yöntem aracılığıyla tarafından gösterildiği gibi `DoWork` yöntemi.

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>
- [Güvenli Kodlama Yönergeleri](/dotnet/standard/security/secure-coding-guidelines)
- [Veri ve Modelleme](/dotnet/framework/data/index)
- [Bağlantı talepleri](/dotnet/framework/misc/link-demands)