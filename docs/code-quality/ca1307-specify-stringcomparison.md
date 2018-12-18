---
title: 'CA1307: StringComparison belirtme'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67f0d5152dcdef5ffa3abb76d92e68fd99f9b637
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550420"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: StringComparison belirtme

|||
|-|-|
|TypeName|SpecifyStringComparison|
|CheckId|CA1307|
|Kategori|Microsoft.Globalization|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Ayarlanmamış bir yöntemi aşırı bir dize karşılaştırma işlemi kullanan bir <xref:System.StringComparison> parametresi.

## <a name="rule-description"></a>Kural açıklaması
 Çoğu dize işlemleri, en önemli <xref:System.String.Compare%2A> ve <xref:System.String.Equals%2A> yöntemlerini sağlar kabul eden bir aşırı bir <xref:System.StringComparison> numaralandırma değeri olarak bir parametre.

 Her bir aşırı var. Bu alır bir <xref:System.StringComparison> parametresi, bu parametre almayan bir aşırı yükleme yerine kullanılmalıdır. Bu parametre açıkça ayarlayarak, genellikle yapılan daha açık ve bakımını kodudur.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için dize karşılaştırma yöntemleri kabul eden aşırı yüklemeler için değişiklik <xref:System.StringComparison> parametre olarak numaralandırması. Örneğin: değiştirmek `String.Compare(str1, str2)` için `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Uygulama ve kitaplık yerel sınırlı bir kitle için tasarlanmıştır ve değil yerelleştirilecek olduğunda bu kuraldan bir uyarıyı bastırmak güvenlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirme Uyarıları](../code-quality/globalization-warnings.md)
- [CA1309: Sıralı StringComparison kullanın](../code-quality/ca1309-use-ordinal-stringcomparison.md)