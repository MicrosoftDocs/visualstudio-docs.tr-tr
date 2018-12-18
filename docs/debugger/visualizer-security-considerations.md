---
title: Görselleştirici güvenlik konuları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, security
- security [Visual Studio], visualizers
ms.assetid: cdd86bd5-b729-409b-a7c6-374efa091eb1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 799cc8700c450fb2d8b81293bf410903e498e19c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476523"
---
# <a name="visualizer-security-considerations"></a>Görselleştirici Güvenlik Konuları
Görselleştirici yazma olası güvenlik tehditlerini içerir. Bilinen hiçbir yararlanma şu anda bu olası tehditleri var, ancak geliştiriciler bunları farkında olmalı ve gelecekteki açıklarına karşı koruma sağlamak için burada açıklandığı gibi uygun güvenlik önlemleri alın.  
  
 Hata ayıklayıcı görselleştiriciler kısmi güven uygulama tarafından izin verilenden daha yüksek ayrıcalıklar gerektirir. Kısmi güven ile kodda durduğunda görselleştiriciler yüklemez. Görselleştirici kullanarak hata ayıklamak için tam güven ile kod çalıştırması gerekir.  
  
## <a name="possible-malicious-debuggee-component"></a>Olası zararlı ayıklayıcı bileşeni  
 Görselleştiriciler en az iki sınıfları oluşur: hata ayıklayıcı yan ve diğeri ayıklayıcı tarafında birinde. Görselleştiriciler genellikle özel dizinlerde put ayrı derlemeler dağıtılır, ancak bunlar da ayıklayıcı dışında yüklenebilir. Bu oluştuğunda, hata ayıklayıcı ayıklayıcı dışında kod alır ve hata ayıklayıcısı tam güven içinde çalışır.  
  
 Ayıklayıcı tam olarak güvenilir değil tam güven ile ayıklayıcı tarafı kodu çalışan sorunlu haline gelir. Görselleştirici ayıklayıcıya ayıklayıcı bir kısmi güven derlemeyi yüklemeye çalışırsa, Visual Studio Görselleştirici sona erdirir.  
  
 Ancak, ikincil bir güvenlik açığı hala bulunmaktadır. Başka bir kaynaktan (ayıklayıcı değil) yüklendi bir hata ayıklayıcı kenar ayıklayıcı tarafı ilişkilendirebilirsiniz. Ayıklayıcı yan kendi adına eylemleri gerçekleştirmek için hata ayıklayıcı yan güvenilen anlayabilirsiniz. Örneğin, "Bu dosyayı Sil" mekanizması güvenilir hata ayıklayıcı tarafı sınıfı gösterir, kullanıcının kendi Görselleştirici istediğinde kısmi güven ayıklayıcı Bu mekanizma çağıramadı.  
  
 Bu güvenlik açığından azaltmak için Görselleştirici tarafından kullanıma sunulan arabirimlerinin oluşturduğunu unutmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görselleştirici mimarisi](../debugger/visualizer-architecture.md)   
 [Nasıl yapılır: Görselleştirici yazma](../debugger/how-to-write-a-visualizer.md)   
 [Özel Görselleştiriciler oluşturma](../debugger/create-custom-visualizers-of-data.md)   
 [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)