---
title: Uzaktan hata ayıklama iletişim kutusu için güvenlik duvarını yapılandırma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 982e677639cec6a98ae3aafe3d0ae624df588ccd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459655"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Uzaktan Hata Ayıklama İçin Güvenlik Duvarını Yapılandır İletişim Kutusu
Windows Güvenlik Duvarı'nı ağ üzerinden bilgileri almasını hata ayıklayıcı engellediğinde bu iletişim kutusu görüntülenir. Uzaktan hata ayıklama devam etmek için hata ayıklayıcı bilgi alabilir şekilde delik Güvenlik Duvarı'nda açmanız gerekir.  
  
> [!CAUTION]
>  Güvenlik Duvarı'nda delik açma makinenize engellemek için güvenlik duvarı tehditleri tasarlanmış güvenlik getirebilir. Uzaktan hata ayıklama için delik açma 4020 ve Visual Studio 2015'te 4021 bağlantı noktalarını kaldırır. Diğer Visual Studio sürümlerinde, diğer bağlantı noktası numaraları kullanılır. Daha fazla bilgi için bkz: [uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md). Ayrıca, ek bağlantı noktalarını açmak hata ayıklayıcı sağlar. Daha fazla bilgi için bkz: [uzaktan hata ayıklama için Windows Güvenlik Duvarı Yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="uielement-list"></a>UIElement Listesi  
 **Uzaktan hata ayıklama iptal et**  
 Uzaktan hata ayıklama girişimi iptal eder. Güvenlik ayarları makinenizin değişmeden kalır.  
  
 **Yerel ağa (alt ağ) bilgisayarlardan Uzaktan hata ayıklama Engellemeyi Kaldır**  
 Yerel alt ağdaki makineler uzaktan hata ayıklamayı etkinleştirir. Bu, yerel alt ağdaki makineler güvenlik açıklarına açabilir, ancak alt ağın dışından gelen bilgileri engellemek güvenlik duvarı sürdürür.  
  
 **Herhangi bir bilgisayardan uzaktan hata ayıklama Engellemeyi Kaldır**  
 Ağ üzerinde herhangi bir yere makinelerin uzaktan hata ayıklamayı etkinleştirir. Bu ayarı en az güvenli olanıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama güvenliği](../debugger/debugger-security.md)   
 [Uzaktan hata ayıklama](../debugger/remote-debugging.md)  
 [Kullanıcı arabirim başvurusunda hata ayıklama](../debugger/debugging-user-interface-reference.md)