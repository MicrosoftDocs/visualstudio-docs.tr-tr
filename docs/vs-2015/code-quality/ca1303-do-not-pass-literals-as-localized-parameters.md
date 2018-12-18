---
title: 'CA1303: harfleri yerelleştirilmiş parametreler göndermeyin | Microsoft Docs'
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
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d900abe23dab4d950b5790798916fe728a44af4a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886571"
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: Harfleri yerelleştirilmiş parametreler olarak göndermeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPassLiteralsAsLocalizedParameters|
|CheckId|CA1303|
|Kategori|Microsoft.Globalization|
|Yeni Değişiklik|Bozucu olmayan|

## <a name="cause"></a>Sebep
 Bir yöntem bir dize değişmez değer parametre olarak yapıcıya veya yönteme geçirir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sınıf kitaplığı ve dize yerelleştirilebilir olmalıdır.

 Bu uyarı, bir değişmez dize değeri olarak bir parametre veya özellik geçirilir ve bir veya daha fazla aşağıdaki durumlarda true olduğunda ortaya çıkar:

-   <xref:System.ComponentModel.LocalizableAttribute> Özniteliği parametre ya da özelliğin true.

-   Parametresi veya özellik adı "Metin", "İleti" veya "Başlık" içeriyor.

-   "Value" veya "biçim" Console.Write veya Console.WriteLine yönteme geçirilen dize parametresi adıdır.

## <a name="rule-description"></a>Kural Tanımı
 Kaynak koduna gömülü dize değişmez değerleri yerelleştirmek zordur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için dize sabit değeri bir örneği üzerinden alınan bir dize yerine <xref:System.Resources.ResourceManager> sınıfı.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Kod kitaplığı yerelleştirilmemiş veya dizenin son kullanıcı veya kod kitaplığı kullanarak bir geliştirici için açık değilse bu kuraldan bir uyarıyı bastırmak güvenlidir.

 Kullanıcılar ya da parametre veya adlı özellik yeniden adlandırma ya da bu öğeleri koşullu olarak işaretleme yerelleştirilmiş dizeleri geçirilmemelidir yöntemleri karşı gürültü ortadan kaldırabilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek iki bağımsız değişkenlerinden biri aralık dışında olduğunda özel durum oluşturan bir yöntemi gösterir. İlk bağımsız değişken için özel Oluşturucu bu kuralı ihlal bir sabit dizesi geçirilir. İkinci bağımsız değişkeni için oluşturucu üzerinden alınan bir dize doğru geçirilen bir <xref:System.Resources.ResourceManager>.

 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cpp/FxCop.Globalization.DoNotPassLiterals.cpp#1)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/cs/FxCop.Globalization.DoNotPassLiterals.cs#1)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.DoNotPassLiterals/vb/FxCop.Globalization.DoNotPassLiterals.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Masaüstü Uygulamalarındaki Kaynaklar](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)



