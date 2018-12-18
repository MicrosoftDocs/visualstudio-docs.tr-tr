---
title: 'CA1404: P-Invoke ardından hemen GetLastError çağırın | Microsoft Docs'
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
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1f3cbded489eab995b4a37f4a80145645d80d856
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909750"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: P/Invoke ardından hemen GetLastError çağır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Kategori|Microsoft.Interoperability|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 İçin bir çağrı yapılır <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> yöntemi veya eşdeğer Win32 `GetLastError` işlevi ve hemen önce gelen çağrı değil bir platformda yöntemi çağır.

## <a name="rule-description"></a>Kural Tanımı
 Bir platform yöntemi erişimleri yönetilmeyen kod çağırmak ve tarafından tanımlanan `Declare` anahtar sözcüğünü [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] veya <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> özniteliği. Genellikle, başarısızlık durumunda, yönetilmeyen Win32 işlevlerini `SetLastError` hata ile ilişkili bir hata kodu ayarlamak için işlevi. Başarısız işlev çağıran Win32 çağırır `GetLastError` hata kodunu alabilir ve hatanın nedenini belirlemek için işlevi. Hata kodu, bir iş parçacığı başına temelinde korunur ve sonraki çağrı tarafından üzerine `SetLastError`. Yöntem çağrısı başarısız bir platform çağırma sonra yönetilen kod hata kodunu çağırarak alabilirsiniz <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> yöntemi. Hata kodu iç çağrılarından diğer yönetilen sınıf kitaplığı yöntemleri tarafından üzerine yazılabilir olmadığından `GetLastError` veya <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> yöntem çağrısının hemen platform çağırma sonra yöntemi'nin çağrılabilir.

 Kural aşağıdaki çağrıları göz ardı eder platform çağrısı arasında gerçekleştiğinde yönetilen üyeleri çağırma yöntemini ve çağrısı <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Bu üyeleri hata değiştirmeyin kod ve bazı platform başarısını belirlemek için yararlı olan çağırma yöntemi çağırır.

-   <xref:System.IntPtr.Zero?displayProperty=fullName>

-   <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

-   <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

-   <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için çağrı taşıma <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> böylece platform çağrısının hemen izleyen yöntemi çağır.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yöntem çağrısının platform arasında yer alan kodunu çağırma bu kuraldan bir uyarıyı bastırmak güvenlidir ve <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> yöntem çağrısı yapamazsınız açıkça veya dolaylı olarak neden değiştirilecek hata kodu.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralını ihlal eden bir yöntem ve kural karşılayan bir yöntemi gösterir.

 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/cs/FxCop.Interoperability.LastErrorPInvoke.cs#1)]
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/vb/FxCop.Interoperability.LastErrorPInvoke.vb#1)]

## <a name="related-rules"></a>İlgili kuralları
 [CA1060: P/Invokes öğesini NativeMethods sınıfına taşıyın](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: P/Invoke giriş noktaları bulunmalıdır](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: P/Invoke'lar görünür olmamalıdır](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: P/Invoke dize bağımsız değişkenleri için hazırlama belirtin](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205: Win32 API'sının yönetilen eşdeğerlerini kullanın](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)



