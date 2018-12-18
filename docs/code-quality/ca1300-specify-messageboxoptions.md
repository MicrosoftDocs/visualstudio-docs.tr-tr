---
title: 'CA1300: MessageBoxOptions belirtme'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 815fe7b7f839adeb3204e33bb532b70909d92b53
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056393"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: MessageBoxOptions belirtme

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Kategori|Microsoft.Globalization|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep

Bir aşırı yüklemesini bir yöntemi çağırır <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> değil sürer yöntemi bir <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> bağımsız değişkeni.

## <a name="rule-description"></a>Kural açıklaması

Bir ileti kutusu doğru sağdan sola okuma düzeni kullanan kültürler için görüntülenecek geçirmek [MessageBoxOptions.RightAlign](<xref:System.Windows.Forms.MessageBoxOptions.RightAlign>) ve [MessageBoxOptions.RtlReading](<xref:System.Windows.Forms.MessageBoxOptions.RtlReading>) alanları <xref:System.Windows.Forms.MessageBox.Show%2A> yöntem. İncelemek <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> bir sağdan sola okuma sırası kullanıp kullanmayacağınızı belirlemek için içeren denetiminin özelliği.

## <a name="how-to-fix-violations"></a>İhlallerini düzeltmek nasıl

Bu kural ihlal düzeltmek için bir aşırı yüklemesini çağırın <xref:System.Windows.Forms.MessageBox.Show%2A> yönteminin alan bir <xref:System.Windows.Forms.MessageBoxOptions> bağımsız değişkeni.

## <a name="when-to-suppress-warnings"></a>Ne zaman uyarıları bastırma

Kod kitaplığı sağdan sola okuma düzeni kullanan bir kültür için yerelleştirilen değil olduğunda bir uyarı bu kuraldan bastırmak güvenlidir.

## <a name="example"></a>Örnek

Aşağıdaki örnek kültürü okuma sırası için uygun seçenekleri içeren bir ileti kutusu görüntüler bir yöntemi gösterir. Görünmeyen bir kaynak dosyası örneği oluşturmak için gereklidir. Kaynak dosyası olmadan örneği oluşturmak ve sağdan sola özelliği test etmek için örnekte açıklamaları izleyin.

[!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
[!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Masaüstü uygulamalarında (.NET Framework) kaynakları](/dotnet/framework/resources/index)