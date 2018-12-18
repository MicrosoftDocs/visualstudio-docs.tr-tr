---
title: 'CA1302: Yerel özel dizeleri doğrudan programın içine gömmeyin'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e56c57343ae61709b6d5875c865857a7475363fd
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550498"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Yerel özel dizeleri doğrudan programın içine gömmeyin

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Kategori|Microsoft.Globalization|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Belirli sistem klasörlerinin yolu parçası temsil eden bir dize sabit değeri bir yöntem kullanır.

## <a name="rule-description"></a>Kural açıklaması
 <xref:System.Environment.SpecialFolder?displayProperty=fullName> Numaralandırma özel sistem klasörlerine başvuran üyeleri içerir. Bu klasörlerin konumları farklı işletim sistemleri üzerinde farklı değerlere sahip olabilir, kullanıcı konumları değiştirebilir ve konumlar yerelleştirilmiştir. Özel bir klasör "C:\WINDOWS\system32" olan sistem klasörü üzerinde örneğidir [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] ancak üzerinde "C:\WINNT\system32" [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]. <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> Yöntemi ile ilişkili konumları döndürür <xref:System.Environment.SpecialFolder> sabit listesi. Tarafından döndürülen konumları <xref:System.Environment.GetFolderPath%2A> yerelleştirilir ve için o anda çalışan bilgisayara uygun.

 Bu kural kullanarak alınabilecek klasör yollarını tokenizes <xref:System.Environment.GetFolderPath%2A> ayrı dizin düzeylere yöntemi. Her dize sabit değeri belirteçleri karşılaştırılır. Bir eşleşme bulunursa, yöntem belirteçle ilişkilendirilen sistem konuma başvuran bir dize oluşturuyor varsayılır. Taşınabilirlik ve yerelleştirme için <xref:System.Environment.GetFolderPath%2A> dize değişmez değerleri kullanmak yerine özel sistem klasörlerine konumlarını almak için yöntemi.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için konumu kullanarak almak <xref:System.Environment.GetFolderPath%2A> yöntemi.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Dize sabit değeri ile ilişkili sistem konumlardan birine başvurmak için kullanılmıyorsa bu kuraldan bir uyarıyı bastırmak güvenlidir <xref:System.Environment.SpecialFolder> sabit listesi.

## <a name="example"></a>Örnek
 Aşağıdaki örnek bu kuraldan üç uyarıları oluşturur ortak uygulama veri klasörünün yolunu oluşturur. Ardından, kullanarak örnek yolunu alır <xref:System.Environment.GetFolderPath%2A> yöntemi.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]

## <a name="related-rules"></a>İlgili kuralları
 [CA1303: Harfleri yerelleştirilmiş parametreler olarak göndermeyin](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)