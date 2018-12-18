---
title: 'CA2118: Gözden geçirme SuppressUnmanagedCodeSecurityAttribute kullanımını | Microsoft Docs'
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
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6d4cee2d7758f467a13875f89a9534ceb0d883b5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904485"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: SuppressUnmanagedCodeSecurityAttribute kullanımını gözden geçir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bir ortak veya korumalı tür veya üye <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> özniteliği.

## <a name="rule-description"></a>Kural Tanımı
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> COM birlikte çalışma veya platform çağırma kullanan yönetilmeyen kodu yürüten üyeler için varsayılan güvenlik sistemi davranışını değiştirir. Genellikle, sistemi yapan bir [veri ve modelleme](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) yönetilmeyen kod izni. Bu isteğe bağlı üye her çalıştırılışı için çalışma zamanında gerçekleştirilir ve izin için çağrı yığınında her çağıranı denetler. Özniteliği olduğunda sistemi yapan bir [bağlantı talepleri](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) izni: şu anki çağırıcı izinlerini arayan JIT olarak derlenmiş olduğunda denetlenir.

 Bu öznitelik, öncelikle performansı artırmak için kullanılır; ancak, gelen performans artışı önemli güvenlik riskleri ile gelir. Öznitelik yerel yöntemlerini çağıran ortak üyelerde yerleştirirseniz, çağıranlar çağrı yığını (şu anki çağırıcı dışında) yönetilmeyen kod yönetilmeyen kod yürütme izni gerekmez. Genel üye Eylemler ve giriş işleme bağlı olarak, normalde güvenilir koda kısıtlı erişim işlevini güvenilmez arayanlara izin verebilir.

 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Çağıranlar geçerli işlemin adres alanına doğrudan erişim kazanmasını engellemek için güvenlik denetimlerini kullanır. Bu öznitelik normal güvenlik atladığından okumak veya yazmak için işlemin belleğinin için kullanılabiliyorsa kodunuzu önemli bir tehlike doğurur. Risk kasıtlı olarak işlem bellek erişimi sağlayan yöntemler için sınırlı olduğunu unutmayın; Mevcut hiçbir senaryoda burada kötü amaçlı kod erişim herhangi bir yolla, örneğin, şaşırtıcı, hatalı biçimlendirilmiş veya geçersiz bir giriş sağlayarak elde edebilirsiniz.

 Yerel bilgisayardan yürütme ya da aşağıdaki gruplardan birinin üyesi olduğu sürece varsayılan güvenlik ilkesini yönetilmeyen kodu bir bütünleştirilmiş kod izni vermez:

-   Bilgisayar bölge kodu grubum

-   Microsoft güçlü adı kod grubu

-   ECMA tanımlayıcı adı kod grubu

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu öznitelik kesinlikle gerekli olduğundan emin olmak için kodunuzu dikkatle inceleyin. İle yönetilen kod güvenlik bilginiz ya da bu özniteliği kullanarak güvenlik etkilerini anlamak değil, kodunuzdan kaldırın. Öznitelik gerekliyse, Arayanların kodunuzu amaçla kullanamazsınız emin olmanız gerekir. Kodunuzu yönetilmeyen kod yürütmek için izinlere sahip değilse, bu öznitelik etkiye sahip değildir ve kaldırılması gerekiyor.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Güvenli bir şekilde bu kuraldan bir uyarıyı bastırmak için kodunuzu yerel işlemler veya yıkıcı bir şekilde kullanılabilecek kaynaklara erişim çağıranlar sağlamaz emin olmanız gerekir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek bu kuralı ihlal ediyor.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesDoNotSuppress/cs/FxCop.Security.TypesDoNotSuppress.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, `DoWork` yöntemi sağlayan platform çağırma yöntemi genel olarak erişilebilir kod yolu `FormatHardDisk`.

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PInvokeAndSuppress/cs/FxCop.Security.PInvokeAndSuppress.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, genel yöntem `DoDangerousThing` bir ihlaline neden olur. İhlali gidermek için `DoDangerousThing` özel yapılmalıdır ve erişimi olmalıdır bir güvenlik talebi tarafından güvenli bir genel yöntem aracılığıyla tarafından gösterildiği gibi `DoWork` yöntemi.

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress/cs/FxCop.Security.TypeInvokeAndSuppress.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> [Güvenli kodlama yönergeleri](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [güvenlik iyileştirmeleri](http://msdn.microsoft.com/en-us/cf255069-d85d-4de3-914a-e4625215a7c0) [veri ve modelleme](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) [bağlantı talepleri](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)



