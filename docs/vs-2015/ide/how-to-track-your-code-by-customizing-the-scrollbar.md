---
title: 'Nasıl yapılır: kaydırma çubuğunu özelleştirerek kodunuzu izleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a9ebe7ec-4b6f-4ba2-a79e-80fab3db485b
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bcbce0884dbc5be78371b6df00b0eb482aa8c26e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49270796"
---
# <a name="how-to-track-your-code-by-customizing-the-scrollbar"></a>Nasıl yapılır: kaydırma çubuğunu özelleştirerek kodunuzu izleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uzun kod dosyaları ile çalışırken, her şeyi göz önünde bulundurmanız zor olabilir. Kaydırma çubuğu kodunuzda olup bitenleri bir Kuşbakışı görünüm sağlamak için kod penceresinin özelleştirebilirsiniz.  
  
### <a name="to-show-annotations-on-the-scroll-bar"></a>Ek açıklamalar kaydırma çubuğundaki göstermek için  
  
1.  Kod değişiklikleri, kesme noktaları, hataları ve yer işaretlerini göstermek için kaydırma çubuğunu ayarlayabilirsiniz.  
  
     Açık **kaydırma çubuğu** seçenekler sayfası (**Araçlar, Seçenekler, metin düzenleyici. Tüm diller** veya belirli bir dil, veya tür **kaydırma çubuğu** hızlı başlatma penceresinde).  
  
2.  Seçin **dikey kaydırma çubuğunun üzerinde ek açıklamalarını göster**, görmek istediğiniz ek açıklamaları'ı seçin. ( **İşaretleri** seçeneği, kesme noktaları ve yer imlerini içerir.)  
  
3.  Şimdi deneyin. Büyük kod dosyasını açın ve dosyanın çeşitli yerlerde oluşan bir şey değiştirin. Kaydırma çubuğu bir şey kaydetmemeniz değiştirirse, değişikliklerinizi yedekleyebilirsiniz bu nedenle değişiklik etkisini gösterir.  
  
     İşte nasıl bir dize için arama yaptıktan sonra kaydırma çubuğu görünür. Dizesinin tüm örnekleri görüntülendiğine dikkat edin.  
  
     ![Bir dize için arama sonra kaydırma çubuğu. ](../ide/media/enhancedscrollbarsearch.png "EnhancedScrollbarSearch")  
  
     Dizesinin tüm örnekleri değiştirildikten sonra kaydırma çubuğu aşağıdadır. İşlemi bazı sorunlar nedeniyle hemen görebilirsiniz.  
  
     ![Hatalarla bir dize değiştirdikten sonra kaydırma çubuğu](../ide/media/enhancedscrollbarreplace.png "EnhancedScrollbarReplace")  
  
### <a name="to-set-the-display-mode-for-the-scroll-bar"></a>Kaydırma çubuğu için görüntü modunu ayarlamak için  
  
1.  Kaydırma çubuğu iki mod, çubuk modu (varsayılan) eşleme modu sahiptir. Yalnızca modu ek açıklama göstergeleri kaydırma çubuğundaki görüntüler. Harita modunda kod satırlarını kaydırma çubuğunu temsil edilir. Olduklarını ne kadar geniş ve olup, arka plandaki kod Göster bunlar üzerinde işaretçiyi getirdiğinizde seçebilirsiniz. İmleç kaydırma çubuğundaki bir konuma tıkladığınızda, kod içinde ilgili konuma taşır. Daraltılmış bölgeleri farklı büyük/küçük harf gölgeliyse; bunları çift tıkladığınızda genişletilir.  
  
     Üzerinde **kaydırma çubuğu** seçenekleri sayfasında **dikey kaydırma çubuğu için kullanım çubuğu modu** veya **dikey kaydırma çubuğu için eşleme kullanma modunu**. Genişliği seçebilirsiniz **kaynak genel bakış** açılır.  
  
     Eşleme modu etkindir ve orta genişliği ayarlandığında nasıl görüneceğini gösteren araması örneği aşağıda verilmiştir:  
  
     ![Kaydırma çubuğu eşleme modunda](../ide/media/enhancedscrollbar.png "EnhancedScrollbar")  
  
2.  İmleç kaydırma çubuğu yukarı ve Aşağı Taşı kodun önizlemeler etkinleştirmek için eşleme modunda seçin **önizleme araç ipucunu göster** seçeneği. İşte şöyle:  
  
     ![Bir araç ipucu ile kaydırma çubuğunu](../ide/media/enhancedscrollbarsearchtooltip.png "EnhancedScrollbarSearchTooltip")  
  
     Davranış ve önizleme araç ipucunu kaydırma eşleme modunu tutmak istiyor, ancak kaynak kod genel bakış görmek istemediğiniz ayarlayabileceğiniz **kaynak genel bakış** için **kapalı**.

