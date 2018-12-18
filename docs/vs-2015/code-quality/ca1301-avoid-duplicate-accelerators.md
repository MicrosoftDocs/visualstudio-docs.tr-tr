---
title: 'CA1301: Yinelenen hızlandırıcılardan kaçının | Microsoft Docs'
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
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 92c5baefff76626a42553d6ba5380fd07448b109
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886663"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Yinelenen hızlandırıcılardan kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Kategori|Microsoft.Globalization|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Bir türü genişleten <xref:System.Windows.Forms.Control?displayProperty=fullName> ve bir kaynak dosyasında depolanan aynı erişim anahtarları olan iki veya daha fazla üst düzey denetimleri içerir.

## <a name="rule-description"></a>Kural Tanımı
 Giriş anahtarı, bir hızlandırıcı olarak da bilinir, ALT anahtarını kullanarak klavye giriş denetimini sağlar. Birden çok denetimin yinelenen erişim tuşları varsa, erişim tuşunun davranışı iyi tanımlı değildir. Kullanıcı erişim anahtarını kullanarak erişim hedeflenen denetimi olmayabilir ve amaçlanan farklı bir denetimin etkin.

 Geçerli uygulama bu kuralın menü öğelerini yok sayar. Ancak, aynı alt menü öğeleri aynı erişim anahtarlarını sahip olmamalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için tüm denetimler için benzersiz bir erişim anahtarları tanımlayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, aynı erişim anahtarları olan iki denetim içeren en az bir form gösterir. Anahtarları gösterilmiyor bir kaynak dosyasında depolanır; değerlerine açıklamalı görünür ancak çıkış `checkBox.Text` satırlar. Yinelenen hızlandırıcılardan davranışını değiştirerek incelenebilir `checkBox.Text` kullanıma açıklamalı karşılıkları satırıyla. Ancak, bu durumda, örnek bir uyarı kuralından oluşturmaz.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.AvoidDuplicateAccels/cs/FxCop.Globalization.AvoidDuplicateAccels.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Masaüstü uygulamalarındaki kaynaklar](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)



