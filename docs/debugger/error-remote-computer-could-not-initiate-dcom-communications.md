---
title: 'Hata: Uzak bilgisayar DCOM iletişimini başlatamadı | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 111c8b010f9d1415e8e9e4e86e1401346f78702d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471963"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Hata: Uzak bilgisayar DCOM iletişimini başlatamadı
Uzak makinede yerel makineyle iletişim kurmak çalışırken bir DCOM hata oluştu. Yerel makine olan makinesidir  
  
 Visual Studio çalışıyor. Bu hata, çeşitli nedenlerle oluşabilir:  
  
-   Yerel makinede etkin bir güvenlik duvarı vardır.  
  
-   Yerel makinede uzak makinede Windows kimlik doğrulaması çalışmıyor.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Yerel makinede Windows Güvenlik Duvarı etkinse, bkz: [uzaktan hata ayıklama](../debugger/remote-debugging.md) yerel hata ayıklama için Güvenlik Duvarı'nı yapılandırma hakkında yönergeler için.  
  
2.  Uzak sunucudan yerel makine üzerinde bir dosya paylaşımı açılmaya çalışılırken test Windows kimlik doğrulama.  
  
3.  Windows kimlik doğrulaması geri yüklemek için her iki makine yeniden deneyin. Yerel ve Uzak makinelerde Kerberos hataları için olay günlüklerini inceleyin ve bilinen sorunlar için etki alanı yöneticileri ile iletişime geçin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzaktan hata ayıklama](../debugger/remote-debugging.md)