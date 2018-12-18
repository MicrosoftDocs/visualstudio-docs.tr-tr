---
title: '8. adım: testi özelleştirme'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09d020e2d83e7e631fefcb1503eb8f1938894986
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672125"
---
# <a name="step-8-customize-the-quiz"></a>8. adım: testi özelleştirme
Öğreticinin son bölümünde testi özelleştirme ve zaten öğrendiklerinizi üzerinde genişletmek için bazı yollar hakkında bilgi edineceksiniz. Örneğin, programın yanıt hiçbir zaman bir kesir olduğu rastgele bölme problemleri nasıl oluşturduğunu hakkında düşünün. Daha fazla bilgi için kapatma `timeLabel` farklı bir renkte denetlemek ve sınava giren bir ipucu verir.  

## <a name="to-customize-the-quiz"></a>Test özelleştirmek için  

-   Yalnızca beş saniyede bir sınavda kalan zaman **timeLabel** denetiminde kırmızı renkte ayarlayarak onun **BackColor** özelliği (`timeLabel.BackColor = Color.Red;`). Test bittiğinde rengi sıfırlayın.  
  
-   Sınava halinde doğru yanıtı girildiğinde ses çalma bir ipucu verir. bir <xref:System.Windows.Forms.NumericUpDown> denetimi. (Her denetim için bir olay işleyicisi yazmanız gereken <xref:System.Windows.Forms.NumericUpDown.ValueChanged> sınava denetimin değeri değiştiğinde harekete olayı,.)  
  
## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Sınavın tamamlanmış bir sürümünü indirmek için bkz [tam matematik sınavı öğretici örneği](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
-   Sonraki eğitime gitmek için bkz: [Tutorial 3: eşleşen bir oluşturma oyun](../ide/tutorial-3-create-a-matching-game.md).  
  
-   Önceki öğretici adımına dönmek için bkz: [7. adım: çarpma ve bölme soruları ekleyin](../ide/step-7-add-multiplication-and-division-problems.md).
