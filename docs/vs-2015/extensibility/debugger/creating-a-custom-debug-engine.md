---
title: Hata ayıklama motoru özel oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 516fda63a1a36e407a71cd6711ecdfabdc1e5e58
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784708"
---
# <a name="creating-a-custom-debug-engine"></a>Özel Hata Ayıklama Altyapısı Oluşturma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklama altyapısı (DE), belirli çalışma zamanı mimarileri hata ayıklamasını sağlayan bir bileşendir. Genellikle çalışma zamanı ortam başına yalnızca bir DE uygulama yok.  
  
> [!NOTE]
>  Transact-SQL ve JScript için ayrı DE uygulamaları olsa da, tek bir DE VBScript ve JScript paylaşın.  
  
 Yürütme denetimi, kesme noktaları ve ifade değerlendirme gibi hata ayıklama hizmetleri sağlamak için yorumlayıcı veya işlemi sistemi bir DE çalışır. Bu hizmetler DE arabirimleri aracılığıyla uygulanır ve farklı çalışma modları arasında geçiş için hata ayıklayıcı neden olabilir. Daha fazla bilgi için [çalışma modları](../../extensibility/debugger/operational-modes.md).  
  
 Bir DE oluşturma, aşağıdaki adımlardan oluşur:  
  
1.  Bir DE Visual Studio ile kaydetme  
  
2.  Bir program görüntüde hata ayıklamayı etkinleştirme  
  
3.  Yürütme denetimi ve durum değerlendirmesi  
  
4.  Olayları gönderme  
  
5.  Sonlandırma ve ayırma  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Özel Bir Hata Ayıklama Altyapısını Kaydetme](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Böylece kullanılabilmesi için Visual Studio ile hata ayıklama altyapısı kaydetmek için gereken adımları açıklar.  
  
 [Bir Programı Hataları Ayıklanacak Şekilde Etkinleştirme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Sizin DE bir program hata ayıklama yapılabilmesi gerekir ilk DE başlatın veya varolan bir program ekleyin, açıklar.  
  
 [Yürütme Denetimi ve Durum Değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Neden bir uygulamada hata ayıklama yürütme denetimi özelliklerini uygulama gerektirir açıklanır.  
  
 [Olayları Gönderme](../../extensibility/debugger/sending-events.md)  
 Hata ayıklayıcı ve DE arasındaki iletişim, DCOM göre bir olay modeli olarak açıklar.  
  
 [Sonlandırma ve Ayırma](../../extensibility/debugger/termination-and-detaching.md)  
 Hiçbir kesme noktaları, özel durumlar, çalışma zamanı hataları veya uygulamada hata ayıklaması için sonsuz döngüler olduğu anlamına gelir normal sonlandırması elde etmek açıklanmaktadır.  
  
 [Hata Ayıklayıcısı Olaylarını Çağırma](../../extensibility/debugger/calling-debugger-events.md)  
 Hata ayıklama oturumunda gerçekleşen olayların arama sırası belgeler.  
  
 [Nasıl Yapılır: Özel Hata Ayıklama Altyapısında Hata Ayıklama](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Özel bir DE hata ayıklama açıklanmaktadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Hata Ayıklayıcı Genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

