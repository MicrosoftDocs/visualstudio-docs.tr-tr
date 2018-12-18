---
title: 'CA1060: P-Invokes öğesini NativeMethods sınıfına taşıyın'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bf3e3f01eb6decb1ac2705655675455485bceb5b
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551957"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: P/Invokes öğesini NativeMethods sınıfına taşıyın

|||
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep

Bir yöntem, yönetilmeyen kod erişmek için Platform çağırma Hizmetleri kullanır ve birinin üyesi değil **NativeMethods** sınıfları.

## <a name="rule-description"></a>Kural açıklaması

Platform çağırma yöntemleri kullanarak işaretlenenler gibi <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> özniteliği veya kullanılarak tanımlanan yöntemleri `Declare` anahtar sözcüğünü [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], yönetilmeyen koda erişebilirsiniz. Bu yöntemler aşağıdaki sınıflar biri olmalıdır:

- **NativeMethods** -Bu sınıf, yönetilmeyen kod iznini için yığın Yürüyüşü engellemez. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> bu sınıfa uygulanmadığından.) Yığın ilerlemesi gerçekleştirilecek çünkü her yerde kullanılabilir yöntemler için sınıftır.

- **SafeNativeMethods** -yığın Yürüyüşü yönetilmeyen kod iznini için bu sınıf bastırır. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> bu sınıfa uygulanır.) Bu sınıf, herkesin çağırmak güvenlidir yöntemleri içindir. Bu yöntemlerin çağıranlar yöntemleri için herhangi bir çağırıcı zararsız olduğundan kullanım güvenli olduğundan emin olmak için tam bir güvenlik incelemesi gerçekleştirme gerekli değildir.

- **UnsafeNativeMethods** -yığın Yürüyüşü yönetilmeyen kod iznini için bu sınıf bastırır. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> bu sınıfa uygulanır.) Potansiyel olarak tehlikeli yöntemleri sınıftır. Bu yöntemlerin herhangi bir çağıran hiçbir yığın ilerlemesi gerçekleştirilecek çünkü kullanım güvenli olduğundan emin olmak için tam bir güvenlik incelemesi gerçekleştirmeniz gerekir.

Bu sınıflar olarak bildirilen `internal` (`Friend`, Visual Basic'te) ve yeni örnekleri oluşturulmasını engellemek için özel bir oluşturucu bildirin. Bu sınıfların yöntemleri olmalıdır `static` ve `internal` (`Shared` ve `Friend` Visual Basic'te).

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için uygun move yöntemi **NativeMethods** sınıfı. Çoğu uygulama için P/Invoke'lar adlı yeni bir sınıf taşıma **NativeMethods** yeterlidir.

 Diğer uygulamalarda kullanmak için kitaplıkları geliştiriyorsanız Bununla birlikte, çağrılan diğer iki sınıfları tanımlama dikkate almanız gereken **SafeNativeMethods** ve **UnsafeNativeMethods**. Bu sınıflar benzer **NativeMethods** sınıfı; ancak, bunlar adlı bir özel özniteliği kullanılarak işaretlenir **SuppressUnmanagedCodeSecurityAttribute**. Bu öznitelik uygulandığında, çalışma zamanı tüm çağıranların sahip olduğunuzdan emin olmak için tam bir yığın ilerlemesi gerçekleştirmez **UnmanagedCode** izni. Çalışma zamanı, başlangıçta bu izin için normalde denetler. Denetim yapılmaz, yönetilmeyen bu yöntemlere yapılan çağrılar için performansı büyük ölçüde artırabilir, ayrıca bu yöntemleri çağırmak için izinleri sınırlı olan kod sağlar.

 Ancak, bu öznitelik ile çok dikkatli kullanmanız gerekir. Yanlış uygulanırsa, ciddi güvenlikle ilgili etkileri sahip olabileceği...

 Yöntemleri hakkında daha fazla bilgi için bkz. **NativeMethods** örnek, **SafeNativeMethods** , örnek ve **UnsafeNativeMethods** örnek.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek bu kuralı ihlal eden bir yöntem bildirir. İhlali gidermek için **RemoveDirectory** P/Invoke yalnızca P/Invoke'lar tutmak için tasarlanmış bir uygun sınıf getirilmelidir.

 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]

## <a name="nativemethods-example"></a>NativeMethods örneği

### <a name="description"></a>Açıklama
 Çünkü **NativeMethods** sınıfı kullanarak işaretlenmemelidir **SuppressUnmanagedCodeSecurityAttribute**, içine yerleştirdiğiniz P/Invoke'lar gerektirecek **UnmanagedCode** izni. Yerel bilgisayardan çoğu uygulamayı çalıştırabilir ve tam güven ile birlikte çalıştırın, bu genellikle bir sorun değildir çünkü. Yeniden kullanılabilir kitaplıklar geliştiriyorsanız ancak tanımlama dikkate almanız gereken bir **SafeNativeMethods** veya **UnsafeNativeMethods** sınıfı.

 Aşağıdaki örnekte gösterildiği bir **Interaction.Beep** sarmalar yöntemi **MessageBeep** user32.dll işlevden. **MessageBeep** P/Invoke yerleştirildiğini **NativeMethods** sınıfı.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]

## <a name="safenativemethods-example"></a>SafeNativeMethods örneği

### <a name="description"></a>Açıklama
 P/Invoke yöntemleri, güvenli bir şekilde ortaya herhangi bir uygulama ve yan etkileri yok adlı bir sınıfta put **SafeNativeMethods**. İçin isteğe bağlı izinlere sahip değilsiniz ve gelen burada adlı için çok dikkat gerekmez.

 Aşağıdaki örnekte gösterildiği bir **Environment.TickCount** sarmalar özelliği **GetTickCount** kernel32.dll öğesinden işlevi.

### <a name="code"></a>Kod
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]

## <a name="unsafenativemethods-example"></a>UnsafeNativeMethods örneği

### <a name="description"></a>Açıklama
 P/Invoke yöntemleri, güvenli bir şekilde çağrılamaz ve yan etkilere neden olabilecek adlı bir sınıfta put **UnsafeNativeMethods**. Bu yöntemler, bunlar kullanıcıya yanlışlıkla gösterilmez emin olmak için titizlikle denetlenmelidir. Kural [CA2118: gözden geçirme SuppressUnmanagedCodeSecurityAttribute kullanımını](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) bu konuda yardımcı olabilir. Alternatif olarak, yöntemler yerine talep başka bir iznine sahip olması gereken **UnmanagedCode** kullandığında bunları.

 Aşağıdaki örnekte gösterildiği bir **Cursor.Hide** sarmalar yöntemi **sayı değil geçiş** user32.dll işlevden.

### <a name="code"></a>Kod
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_4.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_4.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Tasarım Uyarıları](../code-quality/design-warnings.md)