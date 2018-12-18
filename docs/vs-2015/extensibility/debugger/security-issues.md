---
title: Güvenlik sorunları | Microsoft Docs
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
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6807ea81d1898bfaf9c766e25e3c84c021c3aae5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799645"
---
# <a name="security-issues"></a>Güvenlik Sorunları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio kullanarak bir programda hata ayıklamak için gerekli tek izinler programı çalıştırmak için bir geliştiricinin ihtiyaç duyduğu bilgilerle aynı değil. Bu, çoğu durum için (Internet bilgi hizmeti gibi diğer hizmetlerle ilgili bazı durumlarda, daha yüksek düzeyde izinleri gerektirebilir) uzaktan hata ayıklamayı içerir.  
  
 Visual Studio çalışırken, işlem hata ayıklama Yöneticisi (PDM) yerel makine üzerinde hata ayıklama işlemlerini izler. Uzaktan msvsmon.exe adlı bir program, uzaktan hata ayıklama işlemek ve PDM kullanılabilir hale getirmek için geliştirici tarafından başlatılır. (Unutmayın. msvsmon.exe'in hizmet değildir ve bu makinede uzaktan hata ayıklamayı etkinleştirmek için el ile başlatılması gerekir.) Visual Studio'nun (veya msvsmon.exe) çalışmadığında, hiçbir işlem hata ayıklama için izlenir.  
  
 Başka bir deyişle, bir geliştirici isterse, hiçbir özel izinlerle başlatılan programlar ayıklayabilirsiniz. Geliştirici, başka bir kişi aynı güvenlik grubunun bir üyesi ise başkası tarafından başlatılan işlemler bile hata ayıklaması yapabilirsiniz. Ve yalnızca gerekli kopyalamak için dosyaları uzak makine'ı ve msvsmon.exe Başlat uzaktan hata ayıklamayı etkinleştirmek için gerekli olur (bkz [ayarlanmış yukarı uzak Araçlar cihazda](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) daha fazla ayrıntı için).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)   
 [İşlem Hata Ayıklama Yöneticisi](../../extensibility/debugger/process-debug-manager.md)   
 [Cihazda uzak araçları ayarlama](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)

