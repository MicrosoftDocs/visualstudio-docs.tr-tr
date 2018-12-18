---
title: '9. adım: Diğer özellikleri deneyin | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4e0eefc947f71da5332ac3ef248cc73a41818880
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49255131"
---
# <a name="step-9-try-other-features"></a>9. Adım: Diğer Özellikleri Deneme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Daha fazla bilgi edinmek için simgeleri ve renkleri değiştirmeyi, oyun zamanlayıcısı ve sesler eklemeyi deneyin. Oyunu daha zorlu hale getirmek için tahtayı büyütmeyi ve zamanlayıcıyı ayarlamayı deneyin.  
  
 Örnek tamamlanmış bir sürümünü indirmek için bkz [eksiksiz eşleştirme oyunu Öğreticisi örneği](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).  
  
### <a name="to-try-other-features"></a>Diğer özellikleri denemek için  
  
-   Simgelerin ve renklerin yerine kendi tercih ettiklerinizi kullanın.  
  
    > [!TIP]
    >  Etiketin bakmayın deneyin [Forecolor](http://msdn.microsoft.com/library/system.windows.forms.control.forecolor%28v=vs.110%29.aspx) özelliği.  
  
-   Oyuncunun oyunu kazanmasının ne kadar sürdüğünü izleyen bir oyun zamanlayıcısı ekleyin.  
  
    > [!TIP]
    >  Bunun için, TableLayoutPanel üzerindeki forma geçen süreyi gösterecek bir etiket ekleyebilir ve süreyi izlemek için de forma bir diğer zamanlayıcı ekleyebilirsiniz. Oyuncu oyuna başladığında zamanlayıcıyı başlatmak ve son iki simgeyi eşleştirdikten sonra zamanlayıcıyı durdurmak için kod kullanın.  
  
-   Oyuncu bir eşleşme bulduğunda çalacak bir ses, eşleşmeyen iki simgeyi açtığında çalacak başka bir ses ve program simgeleri yeniden gizlediğinde çalacak üçüncü bir ses ekleyin.  
  
    > [!TIP]
    >  Sesleri çalmak için System.media ad alanını kullanabilirsiniz. Bkz: [Play Sounds in Windows Forms uygulaması (C# .NET)](http://youtu.be/qOh4ooHg1UU) veya [nasıl için Play Audio ın Visual Basic](http://youtu.be/-4oPDeQrtMs) daha fazla bilgi için.  
  
-   Oyun tahtasını büyüterek oyunu zorlaştırın.  
  
    > [!TIP]
    >  TableLayoutPanel denetimine satır ve sütunları eklemekten fazlasını yapmanız ve oluşturduğunuz simge sayısını da düşünmeniz gerekir.  
  
-   Oyuncunun tepki verirken çok yavaş davranması ve belirli bir süre dolmadan önce ikinci simgeyi seçmemesi durumunda ilk simgeyi gizleyerek oyunu daha zorlu hale getirin.  
  
### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için  
  
-   Bir yerde tıkanıp kalırsanız veya programlamayla ilgili sorularınız olursa, MSDN forumlarından birinde sorunuzu göndermeyi deneyin. Bkz: [Visual Basic Forumu](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral) ve [Visual C# Forumu](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral).  
  
-   Yararlanabileceğiniz harika ve ücretsiz video öğrenme kaynakları vardır. Visual Basic'te programlama hakkında daha fazla bilgi için bkz. [Visual Basic Fundamentals: Development for Absolute Beginners](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Visual C# programlama hakkında daha fazla bilgi için bkz. [C# Fundamentals: Development for Absolute Beginners](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).  
  
-   Önceki öğretici adımına dönmek için bkz: [adım 8: doğrulama olmadığını oyuncunun kazanıp için bir yöntem ekleyin](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).



