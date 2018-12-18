---
title: 'CA1300: MessageBoxOptions belirtme | Microsoft Docs'
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
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5d1b5e94ab05a5aca551cf0979aa475824a2e8fe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825484"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: MessageBoxOptions belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Kategori|Microsoft.Globalization|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Bir yöntemi çağıran bir aşırı yüklemesini <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> görüntüsünü yöntemi bir <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> bağımsız değişken.

## <a name="rule-description"></a>Kural Tanımı
 Doğru bir sağdan sola okuma düzeni kullanan kültürler için bir ileti kutusu görüntülemek için <xref:System.Windows.Forms.MessageBoxOptions> ve <xref:System.Windows.Forms.MessageBoxOptions> üyeleri <xref:System.Windows.Forms.MessageBoxOptions> numaralandırma geçirilen, için <xref:System.Windows.Forms.MessageBox.Show%2A> yöntemi. İnceleme <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> sağdan sola okuma düzeni kullanan belirlemek için içeren denetiminin özelliği.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için bir aşırı yüklemesini çağırmak <xref:System.Windows.Forms.MessageBox.Show%2A> gereken yöntemini bir <xref:System.Windows.Forms.MessageBoxOptions> bağımsız değişken.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Kod kitaplığı sağdan sola okuma düzeni kullanan bir kültür için yerelleştirilmiş değil olduğunda bu kuraldan bir uyarıyı bastırmak güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kültürün okuma düzeni için uygun olan seçenekleri içeren bir ileti kutusu görüntüleyen bir yöntem gösterilmektedir. Görünmeyen bir kaynak dosyası örneği oluşturmak için gereklidir. Örnek bir kaynak dosyası olmadan örneği oluşturmak ve sağdan sola özelliği test etmek için yorumlarda izleyin.

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Masaüstü uygulamalarındaki kaynaklar](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)



