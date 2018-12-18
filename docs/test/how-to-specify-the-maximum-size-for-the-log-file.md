---
title: Yük testleri için günlük dosyası boyutu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging
ms.assetid: 417059bf-37ae-4e7a-b9b0-29bd71f1414f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: eb77c9c037a46ad1195482abfddd102f50bcd1ae
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067281"
---
# <a name="how-to-specify-the-maximum-size-for-the-log-file-for-load-tests"></a>Nasıl yapılır: yük testleri için günlük dosyası boyutu üst sınırı belirtin

Varsayılan olarak, yük testleri için kullanılan günlük dosyasının en büyük boyutu, 20 megabayt olarak ayarlanır. Denetleyici hizmetiyle ilişkilendirilmiş yapılandırma dosyasını düzenleyerek bu değeri değiştirebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-maximum-log-file-size-for-load-test"></a>Yük testi için en fazla günlük dosyası boyutunu belirtme

1.  Açık *QTCcontroller.exe.config* bulunan XML yapılandırma dosyasını *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config*.

2.  Bulun `<add key="LogSizeLimitInMegs" value="20"/>` altında girdisi `<appSettings>` etiketi.

    ```xml
    <appSettings>
        <add key="LogSizeLimitInMegs" value="20"/>
        <add key="AgentConnectionTimeoutInSeconds" value="120"/>
        <add key="AgentSyncTimeoutInSeconds" value="300"/>
        <add key="ControllerServicePort" value="6901"/>
        <add key="ControllerUsersGroup" value="TeamTestControllerUsers"/>
        <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins"/>
        <add key="CreateTraceListener" value="no"/>
      </appSettings>
    ```

3.  Değiştirme `value ="20"` günlük dosyası için belirtmek istediğiniz izin verilen maksimum boyutu.

    > [!NOTE]
    > "0" değeri girme günlük dosyasının boyut olarak kullanılabilir disk alanı yalnızca sınırlıdır belirtir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi günlüğü ayarlarını değiştirme](../test/modify-load-test-logging-settings.md)
- [Test denetleyicileri için bağlantı noktalarını yapılandırın ve test aracıları](../test/configure-ports-for-test-controllers-and-test-agents.md)