---
title: 'CA2101: P-Invoke dize bağımsız değişkenleri için sıralama belirtin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ae65e922d1b4946300155bbf148abac574a2ec2a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544384"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: P/Invoke dize bağımsız değişkenleri için sıralama belirtin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|Kategori|Microsoft. Globalization|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Platform çağırma üyesi kısmen güvenilen çağıranlar için izin verir, bir dize parametresine sahiptir ve dizeyi açıkça sıralamaz.

## <a name="rule-description"></a>Kural Tanımı
 Unicode 'dan ANSI 'ye dönüştürdüğünüzde, tüm Unicode karakterlerin belirli bir ANSI kod sayfasında gösterilemeyeceği olasıdır. *En uygun eşleme* , temsil edilemeyecek karakter için bir karakteri değiştirerek bu sorunu çözmeye çalışır. Seçilen karakteri denetleyemediği için bu özelliğin kullanılması olası bir güvenlik açığına neden olabilir. Örneğin, kötü amaçlı kod kasıtlı olarak, belirli bir kod sayfasında bulunmayan ve '.. ' gibi dosya sistemi özel karakterlerine dönüştürülen karakterleri içeren bir Unicode dizesi oluşturabilir. ya da '/'. Ayrıca, dize ANSI 'ye dönüştürülmeden önce özel karakterler için güvenlik denetimlerinin sıklıkla meydana geldiğine göz önüne alın.

 En uygun eşleme, yönetilmeyen dönüştürme için varsayılan değer olan WChar 'dan Mbfit 'e. En uygun eşlemeyi açıkça devre dışı bırakmadığınız takdirde, kodunuz bu sorundan dolayı açıktan yararlanabilecek bir güvenlik açığı içerebilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, dize veri türlerini açıkça sıralama.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden bir yöntemi gösterir ve sonra ihlalin nasıl düzeltileceğini gösterir.

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PinvokeAnsiUnicode/cs/FxCop.Security.PinvokeAnsiUnicode.cs#1)]
