---
title: Uzaktan hata ayıklama iletişim kutusu için güvenlik duvarını | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c899de05321ee8c6579b9dbbdb35befa0b97d2b3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762065"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Uzaktan Hata Ayıklama İçin Güvenlik Duvarını Yapılandır İletişim Kutusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Güvenlik Duvarı, ağ üzerinden bilgi almasını hata ayıklayıcı engellediğinde bu iletişim kutusu görüntülenir. Uzaktan hata ayıklamaya devam etmek için hata ayıklayıcı bilgi alabilir. böylece delik Güvenlik Duvarı'nda açmanız gerekir.  
  
> [!CAUTION]
>  Güvenlik Duvarı'nda delik açma makinenize bir güvenlik duvarı tehditleri engellemek için tasarlanmış güvenlik getirebilir. Uzaktan hata ayıklama delik açma 4020 ve Visual Studio 2015'te 4021 bağlantı noktalarını engellemesini kaldırır. Visual Studio'nun diğer sürümlerinde de diğer bağlantı noktası numaralarını kullanılır. Daha fazla bilgi için [uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md). Ayrıca, ek bağlantı noktalarını açmak hata ayıklayıcı sağlar. Daha fazla bilgi için [uzaktan hata ayıklama için Windows Güvenlik Duvarı Yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="uielement-list"></a>UIElement Listesi  
 **Uzaktan hata ayıklamayı iptal et**  
 Uzaktan hata ayıklama denemesi iptal eder. Makinenizin güvenlik ayarlarını değişmeden kalır.  
  
 **Yerel ağa (alt ağ) bilgisayarlarda uzaktan hata ayıklamasını engelini kaldırma**  
 Yerel alt ağınız makinelerde uzaktan hata ayıklamasını etkinleştirir. Bu güvenlik açıkları, yerel alt ağdaki makinelere açabilir, ancak bilgi alt ağın dışına geldiğini engellemek güvenlik duvarı devam eder.  
  
 **Herhangi bir bilgisayarda uzaktan hata ayıklama engelini kaldırma**  
 Herhangi bir ağdaki makineler uzaktan hata ayıklamasını etkinleştirir. Bu ayar, en az güvenli seçenektir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)   
 [Cihazda uzak araçları ayarlama](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Kullanıcı arabirim başvurusunda hata ayıklama](../debugger/debugging-user-interface-reference.md)



