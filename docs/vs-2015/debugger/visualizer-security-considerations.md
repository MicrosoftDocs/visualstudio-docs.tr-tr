---
title: Görselleştirici güvenlik konuları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, security
- security [Visual Studio], visualizers
ms.assetid: cdd86bd5-b729-409b-a7c6-374efa091eb1
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b25c9a183a843130861818f8a80948a68a8b1ed5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800633"
---
# <a name="visualizer-security-considerations"></a>Görselleştirici Güvenlik Konuları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Görselleştirici yazma, olası güvenlik tehditlerini içerir. Bilinen hiçbir yararlanma şu anda bu olası tehditleri var, ancak geliştiriciler bunları kullanan ve gelecek saldırılara karşı koruma sağlamak için burada açıklandığı gibi uygun güvenlik önlemleri alın.  
  
 Hata ayıklama görselleştiricileri kısmi güven uygulama tarafından izin verilenden daha yüksek ayrıcalıklar gerektirir. Kısmi güven ile koddaki durdurulduğunda görselleştiriciler yüklemez. Görselleştirici kullanarak hata ayıklama için tam güven ile kodu çalıştırmanız gerekir.  
  
## <a name="possible-malicious-debuggee-component"></a>Olası kötü amaçlı hata ayıklanan bileşeni  
 Görselleştiriciler, en az iki sınıf oluşur: bir hata ayıklayıcı yan ve bir hata ayıklanan taraftaki. Görselleştiriciler genellikle özel dizinlerde put ayrı derlemeler dağıtılır, ancak bunlar da dışında hata ayıklanan yüklenmiş olabilir. Bu durumda, hata ayıklayıcı hata ayıklanan kodunun alır ve tam güven hata ayıklayıcısı içinde çalıştırır.  
  
 Hata ayıklanan tam güvenilir değil. hata ayıklanan tarafın kod tam güven ile çalışan sorunlu duruma gelir. Görselleştiriciyi hata ayıklayıcıya hata ayıklanan bir kısmi güvenli bütünleştirilmiş kod yüklenemedi çalışırsa, Visual Studio Görselleştirici sona erer.  
  
 Ancak, ikincil bir güvenlik açığı hala mevcut. Hata ayıklanan tarafın başka bir kaynaktan (hata ayıklanan değil) yüklenen bir hata ayıklayıcı yan ile ilişkilendirebilirsiniz. Hata ayıklanan yanında, kendi adına eylem gerçekleştirmek için hata ayıklayıcı yan güvenilen söyleyebilirsiniz. Örneğin, "Bu dosya silme" bir mekanizma güvenilir hata ayıklayıcı tarafı sınıf sunarsa, kullanıcının kendi görselleştiricisi çağırdığında kısmi güven hata ayıklanan Bu mekanizma çağırabilirsiniz.  
  
 Bu güvenlik açığını gidermek için visualizer tarafından kullanıma sunulan arabirimlerin oluşturduğunu unutmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görselleştirici mimarisi](../debugger/visualizer-architecture.md)   
 [Nasıl yapılır: Görselleştirici yazma](../debugger/how-to-write-a-visualizer.md)   
 [Özel Görselleştiriciler oluşturma](../debugger/create-custom-visualizers-of-data.md)   
 [Hata Ayıklayıcıda Verileri Görüntüleme](../debugger/viewing-data-in-the-debugger.md)



