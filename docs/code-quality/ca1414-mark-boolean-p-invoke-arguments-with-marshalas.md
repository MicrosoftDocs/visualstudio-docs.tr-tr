---
title: 'CA1414: Boolean P-Invoke bağımsız değişkenlerini MarshalAs ile işaretleyin'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a5936c07646201ab3988dd7cc792f758ed698063
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548978"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Boolean P/Invoke bağımsız değişkenlerini MarshalAs ile işaretleyin

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Kategori|Microsoft.Interoperability|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bir platform çağırma yöntemi bildirimi içeren bir <xref:System.Boolean?displayProperty=fullName> parametre veya dönüş değerindeki ancak <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> özniteliği için parametre veya dönüş değerindeki uygulanmaz.

## <a name="rule-description"></a>Kural açıklaması
 Bir platform yöntemi erişimleri yönetilmeyen kod çağırmak ve tarafından tanımlanan `Declare` anahtar sözcüğünü [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] veya <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Yönetilen ve yönetilmeyen kod arasında veri türlerine dönüştürmek için kullanılan sıralama davranışını belirtir. Gibi pek çok basit veri türleri <xref:System.Byte?displayProperty=fullName> ve <xref:System.Int32?displayProperty=fullName>, yönetimsiz kod içinde tek bir gösterimi olan ve sıralama davranışları belirtilmesine gerek yoktur; ortak dil çalışma zamanı otomatik olarak doğru davranışı sağlar.

 <xref:System.Boolean> Veri türüne, yönetimsiz kod içinde birden çok temsile sahiptir. Zaman <xref:System.Runtime.InteropServices.MarshalAsAttribute> , varsayılan hazırlama davranışı için belirtilmemiş <xref:System.Boolean> veri türü <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Tüm durumlarda uygun olmayan bir 32 bit tamsayı budur. Yönetilmeyen yöntemi tarafından gerekli Boolean gösterimi belirlenen verilecek ve uygun eşleşen <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType.Bool her zaman 4 bayttır Win32 BOOL türüdür. C++ için UnmanagedType.U1 kullanılmalıdır `bool` ya da diğer 1 baytlık türleri.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için geçerli <xref:System.Runtime.InteropServices.MarshalAsAttribute> için <xref:System.Boolean> parametre veya dönüş değeri. Öznitelik değerini uygun ayarlamak <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Varsayılan hazırlama davranışı uygun olsa bile, davranışı açıkça belirtildiğinde kodu daha kolay korunur.

## <a name="example"></a>Örnek

Platform çağırma uygun ile işaretlenmiş yöntemler, aşağıdaki örnekte gösterildiği <xref:System.Runtime.InteropServices.MarshalAsAttribute> öznitelikleri.

 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>İlgili kuralları
 [CA1901: P/Invoke bildirimleri taşınabilir olmalıdır](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: P/Invoke dize bağımsız değişkenleri için hazırlama belirtin](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [Yönetilmeyen Kod ile Birlikte Çalışma](/dotnet/framework/interop/index)