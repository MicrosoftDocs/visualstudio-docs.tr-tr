---
title: 'CA1303: Harfleri yerelleştirilmiş parametreler olarak göndermeyin'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8716a16ea3b141e7c5053e526d92531d0a77bc1e
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859412"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Harfleri yerelleştirilmiş parametreler olarak göndermeyin

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Kategori|Microsoft.Globalization|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep
 Bir yöntem bir dize değişmez değer parametre olarak bir oluşturucu veya .NET Framework Sınıf Kitaplığı'nda yöntemi geçirir ve bu dize yerelleştirilebilir olmalıdır.

 Bu uyarı, bir değişmez dize değeri olarak bir parametre veya özellik geçirilir ve bir veya daha fazla aşağıdaki durumlarda true olduğunda ortaya çıkar:

- <xref:System.ComponentModel.LocalizableAttribute> Özniteliği parametre ya da özelliğin true.

- Parametresi veya özellik adı "Metin", "İleti" veya "Başlık" içeriyor.

- "Value" veya "biçim" Console.Write veya Console.WriteLine yönteme geçirilen dize parametresi adıdır.

## <a name="rule-description"></a>Kural açıklaması
 Kaynak koduna gömülü dize değişmez değerleri yerelleştirmek zordur.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için dize sabit değeri bir örneği üzerinden alınan bir dize yerine <xref:System.Resources.ResourceManager> sınıfı.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
 Kod kitaplığı yerelleştirilmemiş veya dizenin son kullanıcı veya kod kitaplığı kullanarak bir geliştirici için açık değilse bu kuraldan bir uyarıyı bastırmak güvenlidir.

 Kullanıcılar ya da parametre veya adlı özellik yeniden adlandırma ya da bu öğeleri koşullu olarak işaretleme yerelleştirilmiş dizeleri geçirilmemelidir yöntemleri karşı gürültü ortadan kaldırabilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek iki bağımsız değişkenlerinden biri aralık dışında olduğunda özel durum oluşturan bir yöntemi gösterir. İlk bağımsız değişken için özel Oluşturucu bu kuralı ihlal bir sabit dizesi geçirilir. İkinci bağımsız değişkeni için oluşturucu üzerinden alınan bir dize doğru geçirilen bir <xref:System.Resources.ResourceManager>.

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]

## <a name="see-also"></a>Ayrıca bkz.
 [Masaüstü Uygulamalarındaki Kaynaklar](/dotnet/framework/resources/index)