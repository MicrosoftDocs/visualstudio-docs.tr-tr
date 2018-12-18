---
title: '8. adım: testi özelleştirme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 559bd2a1b908ab5b1590a2ec2dd71225020db79a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260149"
---
# <a name="step-8-customize-the-quiz"></a>8. Adım: Testi Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Öğreticinin son bölümünde testi özelleştirme ve zaten öğrendiklerinizi üzerinde genişletmek için bazı yollar hakkında bilgi edineceksiniz. Örneğin, programın yanıt hiçbir zaman bir kesir olduğu rastgele bölme problemleri nasıl oluşturduğunu hakkında düşünün. Daha fazla bilgi için kapatma `timeLabel` farklı bir renkte denetlemek ve sınava giren bir ipucu verir.  
  
### <a name="to-customize-the-quiz"></a>Test özelleştirmek için  
  
-   Yalnızca beş saniyede bir sınavda kalan zaman **timeLabel** denetiminde kırmızı renkte ayarlayarak onun **BackColor** özelliği (`timeLabel.BackColor = Color.Red;`). Test bittiğinde rengi sıfırlayın.  
  
-   Sınava giren bir NumericUpDown denetimine doğru yanıtı girildiğinde ses çalma bir ipucu verir. (Her denetim için bir olay işleyicisi yazmanız gereken `ValueChanged()` sınava denetimin değeri değiştiğinde harekete olayı,.)  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Sınavın tamamlanmış bir sürümünü indirmek için bkz [matematik sınavı öğretici örneği](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
-   Sonraki eğitime gitmek için bkz: [Tutorial 3: Create a Matching Game](../ide/tutorial-3-create-a-matching-game.md).  
  
-   Önceki öğretici adımına dönmek için bkz: [7. adım: ekleme çarpma ve bölme problemleri](../ide/step-7-add-multiplication-and-division-problems.md).



