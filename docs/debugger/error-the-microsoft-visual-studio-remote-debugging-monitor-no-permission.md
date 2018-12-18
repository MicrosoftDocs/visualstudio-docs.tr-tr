---
title: 'Hata: Uzak bilgisayardaki Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisinin bu bilgisayara bağlanma izni yok.'
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, Windows version error
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4bd5a9ef53940164c7d83dff0159af4c69f61010
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53053438"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Hata: Uzak bilgisayardaki Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisinin bu bilgisayara bağlanma izni yok.
Visual Studio uzaktan hata ayıklama İzleyicisi (msvsmon) çalıştırmayı denediği kullanıcının yerel bilgisayarda bir hesabı yoksa, bu hata oluşur.  
  
### <a name="to-fix-this-problem"></a>Bu sorunu gidermek için  
  
- Visual Studio hata ayıklayıcısı ana bilgisayar aynı adı ve parola msvsmon uzak bilgisayarda çalışan kullanıcı hesabı için bir kullanıcı hesabı eklemek,  
  
   \- veya -  
  
- Msvsmon yerel bilgisayara çağırma izni olan bir kullanıcı olarak çalıştırın. Başka bir deyişle, kullanıcının bir etki alanı kullanıcısı ve msvsmon bilgisayarda yönetici olması gerekir. Msvsmon iki yoldan biriyle çalıştırmak için kullanıcı hesabı belirtebilirsiniz:  
  
  - Msvsmon simgesini sağ tıklatın ve seçin **Çalıştır** kısayol menüsünden  
  
    \- veya -  
  
  - Komut isteminde çalıştırın `runas.exe`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzaktan hata ayıklama ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)