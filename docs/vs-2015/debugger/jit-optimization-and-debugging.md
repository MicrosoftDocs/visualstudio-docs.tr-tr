---
title: JIT iyileştirmesi ve hata ayıklama | Microsoft Docs
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
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab86e023b99f524651b56bbca4ddea2d613448e2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770737"
---
# <a name="jit-optimization-and-debugging"></a>JIT İyileştirmesi ve Hata Ayıklaması
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yönetilen bir uygulamada hata ayıklaması yaparken [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] just-in-time (JIT) kod iyileştirme varsayılan olarak gizler. En iyi duruma getirme, JIT gizleme en iyileştirilmemiş kod hata ayıklaması yaptığınız anlamına gelir. Kod optimize, ancak hata ayıklama deneyiminiz çok daha kapsamlı için biraz daha yavaş çalışır. En iyi duruma getirilmiş kodun hatalarının ayıklanması daha zordur ve yalnızca, en iyi duruma getirilmiş kodda oluşan, ancak getirilmemiş sürümde üretilemeyen bir hatayla karşılaşırsanız önerilir.  
  
 JIT iyileştirmesini kontrol edilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tarafından **yüklemesinde JIT iyileştirmesini Modül yükleme** seçeneği. Bu seçeneği bulabilirsiniz **genel** altındaki **hata ayıklama** düğümünde **seçenekleri** iletişim kutusu.  
  
 Silerseniz **yüklemesinde JIT iyileştirmesini Modül yükleme** seçeneği, en iyi duruma getirilmiş JIT kodunun hatalarını ayıklayabilirsiniz, ancak en iyi duruma getirilmiş kodun kaynak kodunu eşleşmediğinden hata ayıklama yeteneğiniz sınırlı olabilir. Sonuç olarak, windows gibi hata ayıklayıcı **Yereller** ve **Otolar** penceresi durumda olmayan optimize edilmiş kodda hata ayıkladığınız zamanki kadar çok bilgi görüntülenemeyebilir.  
  
 Yalnızca kendi kodum ile hata ayıklamada başka bir önemli fark oluşur. Yalnızca kendi kodum ile hata ayıklaması yapıyorsanız, hata ayıklama sırasında görüntülenmemelidir kullanıcı olmayan kodun duruma getirilmiş kodu hata ayıklayıcı değerlendirir. En iyi duruma getirilmiş JIT kodunun ayıklıyorsanız, sonuç olarak, büyük olasılıkla Just My Code'u devre dışı bırakmak istediğiniz. Daha fazla bilgi için [Adımlamayı yalnızca kendi kodum kısıtlama](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code).  
  
 Unutmayın **yüklemesinde JIT iyileştirmesini Modül yükleme** seçeneği modüller yüklendiğinde kodun iyileştirme bastırır. Zaten çalışan bir işleme eklerseniz, önceden yüklenmiş, JIT olarak derlenmiş ve en iyi duruma getirilmiş kod içeriyor olabilir. **Yüklemesinde JIT iyileştirmesini Modül yükleme** seçeneği üzerinde hiçbir etkisi, bu kodların siz ekledikten sonra yüklenen modülleri etkiler. Ayrıca, **yüklemesinde JIT iyileştirmesini Modül yükleme** seçeneği, NGEN ile oluşturulan WinForms.dll gibi modülleri, etkilemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)   
 [Hata ayıklayıcısı ile kodlarda gezinme](../debugger/navigating-through-code-with-the-debugger.md)   
 [Çalıştırma işlemleri iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Yönetilen Yürütme İşlemi](http://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)



