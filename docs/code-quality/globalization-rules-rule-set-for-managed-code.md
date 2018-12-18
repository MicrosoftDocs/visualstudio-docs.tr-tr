---
title: Yönetilen kod için Genelleştirme Kuralları kural kümesi
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 5f260a46d26bfec8af61a39ba8c54910a45772c4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920660"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Yönetilen kod için Genelleştirme Kuralları kural kümesi
Microsoft Genelleştirme kuralları kural kümesi farklı diller, yerel ayarlar ve kültürlere doğru görünmesini uygulamanızdaki verileri engelleyebilecek sorunları odaklanmak için kullanabilirsiniz. Bu kural, uygulama globalized, yerelleştirilmiş ise, kümesi veya her ikisini de içermelidir.

|Kural|Açıklama|
|----------|-----------------|
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|MessageBoxOptions belirtme|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Yinelenen hızlandırıcılardan kaçının|
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Yerel özel dizeleri değil stillerinizin yapın|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Değişmez değerler yerelleştirilmiş parametreler olarak geçmeyin|
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|CultureInfo belirtme|
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|Iformatprovider belirtme|
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Veri türleri için kümesi yerel ayar|
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|StringComparison belirtme|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Dizeleri büyük harfe normalleştirin|
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Sıralı StringComparison kullanın|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|P/Invoke dize bağımsız değişkenleri için sıralama belirtin|