---
title: Genelleştirme Uyarıları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- warnings, globalization
- globalization warnings
- globalization [Visual Studio], warnings
- managed code analysis warnings, globalization warnings
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7db942f410b9a6a8c2f12a044d0e48ad1ad19950
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667576"
---
# <a name="globalization-warnings"></a>Genelleştirme Uyarıları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Genelleştirme Uyarıları, dünyaya yönelik kitaplıkları ve uygulamaları destekler.

## <a name="in-this-section"></a>Bu Bölümde

|Kural|Açıklama|
|----------|-----------------|
|[CA1300: MessageBoxOptions belirt](../code-quality/ca1300-specify-messageboxoptions.md)|Doğru olarak sağdan sola okuma düzeni kullanan kültürler için bir ileti kutusu görüntülemek için Show yöntemi MessageBoxOptions numaralandırma RightAlign ve RtlReading üyeleri geçirilmelidir.|
|[CA1301: Yinelenen hızlandırıcılardan kaçının](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Giriş anahtarı, bir hızlandırıcı olarak da bilinir, ALT anahtarını kullanarak klavye giriş denetimini sağlar. Birden çok denetimin yinelenen erişim tuşları varsa, erişim tuşunun davranışı iyi tanımlı değildir.|
|[CA1302: Yerel özel dizeleri doğrudan programın içine gömmeyin](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|System.Environment.SpecialFolder numaralandırma özel sistem klasörlerine başvuran üyeleri içerir. Bu klasörlerin konumları farklı işletim sistemleri üzerinde farklı değerlere sahip olabilir; kullanıcı konumları değiştirebilir ve konumlar yerelleştirilmiştir. Environment.GetFolderPath yöntemi yerelleştirilmiş ve o anda çalışan bilgisayara uygun Environment.SpecialFolder numaralandırma ile ilişkili olan konumları döndürür.|
|[CA1303: Harfleri yerelleştirilmiş parametreler olarak göndermeyin](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Dışarıdan görünen bir yöntem, sınıf kitaplığındaki bir oluşturucuya veya yönteme parametre olarak bir dize sabiti geçirir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ve bu dize yerelleştirilebilir olmalıdır.|
|[CA1304: CultureInfo belirt](../code-quality/ca1304-specify-cultureinfo.md)|Yöntem veya Oluşturucu System.Globalization.CultureInfo parametre kabul eden aşırı yüklenmiş üye arar ve yöntem veya oluşturucu CultureInfo parametresi aşırı yükleme çağıramaz. Bir CultureInfo veya System.IFormatProvider nesnesi sağlanamadığında, aşırı yüklü üye tarafından sağlanan varsayılan değer, tüm yerel ayarlarda istediğiniz etkiyi vermeyebilir.|
|[CA1305: IFormatProvider belirt](../code-quality/ca1305-specify-iformatprovider.md)|Yöntem veya oluşturucu System.IFormatProvider parametresini kabul eden aşırı yüklü bir veya daha fazla üye arar ve yöntem veya oluşturucu IFormatProvider parametre yüklemesini çağırmaz. Bir System.Globalization.CultureInfo veya IFormatProvider nesnesi sağlanamadığında, aşırı yüklü üye tarafından sağlanan varsayılan değer, tüm yerel ayarlarda istediğiniz etkiyi vermeyebilir.|
|[CA1306: Veri türleri için yereli ayarlayın](../code-quality/ca1306-set-locale-for-data-types.md)|Yerel ayarlar, veri için kültür-özel sunum öğelerini, örneğin para birimi sembolleri, sayısal değerler için biçimleri ve sıralama düzeni için kullanılan biçimlendirme gibi değerleri belirler. Bir DataTable veya DataSet oluşturduğunuzda, yerel ayarı açık olarak ayarlamanız gerekir.|
|[CA1307: StringComparison belirt](../code-quality/ca1307-specify-stringcomparison.md)|StringComparison parametresi ayarlanmamış bir yöntemi aşırı bir dize karşılaştırma işleminde kullanır.|
|[CA1308: Dizeleri büyük harfe normalleştirin](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Dizeler büyük harfe normalleştirilmeli. Küçük bir karakter grubu küçük harfe dönüştürüldüğünde gidiş dönüş yapamaz.|
|[CA1309: Sıralı StringComparison kullanın](../code-quality/ca1309-use-ordinal-stringcomparison.md)|StringComparison parametresini Ordinal ya da OrdinalIgnoreCase'a ayarlayamayan dilbilimsel olmayan dize karşılaştırma işlemi. Açıkça StringComparison.Ordinal veya StringComparison.OrdinalIgnoreCase için parametre ayarıyla kodunuz genellikle hızlanır, daha doğru olur ve daha güvenilir hale gelir.|
|[CA2101: P/Invoke dize bağımsız değişkenleri için sıralama belirtin](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Platform çağırma üyesi kısmen güvenilen çağıranlar için izin verir, bir dize parametresine sahiptir ve dizeyi açıkça sıralamaz. Bu, olası bir güvenlik açığına neden olabilir.|
