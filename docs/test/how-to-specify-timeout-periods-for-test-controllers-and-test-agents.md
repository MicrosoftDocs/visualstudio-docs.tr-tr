---
title: Test denetleyicileri ve Test aracıları için zaman aşımı süreleri
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring
- agetns, timeouts
- controllers, configuring
- controllers, timeouts
ms.assetid: 777d0db5-0073-458a-a2a3-58b1c1f24c60
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 53127df8837f9f86d49cb5d5fa36ca3b50f401fa
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064685"
---
# <a name="how-to-specify-timeout-periods-for-test-controllers-and-test-agents"></a>Nasıl yapılır: test denetleyicileri için zaman aşımı sürelerini belirtme ve test aracıları

Test denetleyicisi ve test aracısını hem ne kadar bunlar birbirinden veya bir hata ile başarısız olmadan önce bir veri kaynağından yanıt beklemesi gerektiğini belirten birkaç zaman aşımı ayarı vardır. Belirli koşullar altında topolojinizin veya diğer ortam sorunlarının ihtiyaçlarını karşılamak için zaman aşımı değerlerini düzenlemek gerekli olabilir. Zaman aşımı değerlerini düzenlemek için aşağıdaki yordamlarda anlatıldığı gibi test denetleyicisi veya test aracısı ile ilişkili XML yapılandırma dosyasını düzenleyin.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Test denetleyicisi veya test aracısın çeşitli zaman aşımı ayarlarını düzenlemek için tablolardaki anahtar isimleri ve değerleri kullanarak aşağıdaki yapılandırma dosyalarını değiştirin:

-   Test denetleyicisi: *QTController.exe.config*

    |Anahtar adı|Açıklama|Değer|
    |-|-----------------|-|
    |AgentConnectionTimeoutInSeconds|Bağlantının kaybedildiğini düşünmeden önce aracının ping isteği için beklenecek saniye sayısını kaybolur.|"n" saniye.|
    |AgentSyncTimeoutInSeconds|Bir eşitleme test çalışması çalıştırma iptal edilmeden önce eşitlemek tüm aracılar için beklenecek saniye sayısını başlattığınızda.|"n" saniye.|
    |AgentInitializeTimeout|Test çalıştırması iptal edilmeden önce tüm aracıların beklenecek saniye ve veri toplayıcılarının testinin başında başlatmak için çalıştırın. Bu değer, veri toplayıcıları kullanıyorsanız oldukça büyük olmalıdır.|"n" saniye. Varsayılan: "120" (iki dakika).|
    |AgentCleanupTimeout|Ve veri toplayıcılarının temizlemek, test tamamlanmadan önce tüm aracıları için beklenecek saniye sayısı'nı çalıştırın. Bu değer, veri toplayıcıları kullanıyorsanız oldukça büyük olmalıdır.|"n" saniye. Varsayılan: "120" (iki dakika).|

-   Test aracısı: *QTAgentService.exe.config*

    |Anahtar adı|Açıklama|Değer|
    |-|-----------------|-|
    |ControllerConnectionPeriodInSeconds|Denetleyiciyi bağlama girişimleri arasında saniye sayısı.|"n" saniye. Varsayılan: "30" (otuz saniye).|
    |RemotingTimeoutSeconds|En uzun süreyi saniye cinsinden bir çağrının sürebileceği dayanabilir.|"n" saniye. Varsayılan: "600" (on dakika).|
    |StopTestRunCallTimeoutInSeconds|Çağrının testi durdurması için beklenen saniye sayısı'nı çalıştırın.|"n" saniye. Varsayılan: "120" (iki dakika).|
    |GetCollectorDataTimeout|Veri Toplayıcı için beklenen saniye sayısı.|"n" saniye. Varsayılan: "300" (beş dakika).|

## <a name="to-specify-agent-timeout-options-for-a-test-controller"></a>Bir test denetleyicisi için aracı zamanaşımı seçeneklerini belirtmek için

1. Açık *QTCcontroller.exe.config* bulunan XML yapılandırma dosyasını *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. bulun `<appSettings>` etiketi.

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

3. Test denetleyicisinin zaman aşımı anahtarlarından biri için bir varolan değeri düzenleyin. Örneğin, anahtar için varsayılan değer değiştirebilirsiniz `AgentConnectionTimeoutInSeconds` iki dakikadan üç dakikaya:

    ```xml
    <add key="AgentConnectionTimeoutInSeconds" value="180"/>
    ```

    veya

    İlave bir anahtar ekleyin ve bir zaman aşımı değeri belirtin. Örneğin, ekleyebileceğiniz `AgentInitializeTimeout` anahtarını `<appSettings>` bölümünde ve beş dakikalık bir değer belirtin:

    ```xml
    <appSettings>
            <add key="AgentInitializeTimeout" value="300"/>
    </appSettings>
    ```

## <a name="to-specify-agent-timeout-options-for-a-test-agent"></a>Bir test aracısı için aracı zamanaşımı seçeneklerini belirtmek için

1. Açık *QTAgentService.exe.config* bulunan XML yapılandırma dosyasını *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. bulun `<appSettings>` etiketi.

    ```xml
    <appSettings>
      <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentServicePort" value="6910"/>
      <add key="ControllerConnectionPeriodInSeconds" value="30"/>
      <add key="StopTestRunCallTimeoutInSeconds" value="120"/>
      <add key="CreateTraceListener" value="no"/>
      <add key="GetCollectorDataTimeout" value="300"/>
    </appSettings>  </appSettings>
    ```

3. Test aracısın zaman aşımı anahtarlarından biri için bir varolan değeri düzenleyin. Örneğin, anahtar için varsayılan değer değiştirebilirsiniz `ControllerConnectionPeriodInSeconds` otuz dakikadan bir dakikaya:

    ```xml
    <add key="ControllerConnectionPeriodInSeconds" value="60"/>
    ```

    veya

    İlave bir anahtar ekleyin ve bir zaman aşımı değeri belirtin. Örneğin, ekleyebileceğiniz `RemotingTimeoutSeconds` anahtarını `<appSettings>` bölümünde ve on beş dakikalık bir değer belirtin:

    ```xml
    <appSettings>
            <add key=" RemotingTimeoutSeconds " value="900"/>
    </appSettings>
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
- [Yük testi günlüğü ayarlarını değiştirme](../test/modify-load-test-logging-settings.md)
- [Test denetleyicileri için bağlantı noktalarını yapılandırın ve test aracıları](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Nasıl yapılır: günlük dosyası boyutu üst sınırı belirtin](../test/how-to-specify-the-maximum-size-for-the-log-file.md)
- [Nasıl yapılır: bir ağ bağdaştırıcısına bir test denetleyicisi veya test aracısı bağlama](../test/how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter.md)