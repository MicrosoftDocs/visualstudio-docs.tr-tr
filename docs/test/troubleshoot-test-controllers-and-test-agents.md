---
title: Test denetleyicileri ve Test aracılarının sorunlarını giderme
ms.date: 10/20/2016
ms.topic: troubleshooting
helpviewer_keywords:
- load tests, test controllers
- load tests, troubleshooting
- load tests, test agents
- troubleshooting, test controllers and agents in load tests
ms.assetid: 77329348-3a5d-43de-b6cb-90f93296a081
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 274585d864393877b225fe6231c1f775342620f6
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894748"
---
# <a name="strategies-for-troubleshooting-test-controllers-and-test-agents-in-load-tests"></a>Sorun giderme stratejilerini test denetleyicilerini ve test aracıları yük testlerinde

Bu makalede, test denetleyicileri ve test aracıları Visual Studio ile çalışırken karşılaşabileceğiniz bazı yaygın sorunlar ele alınmıştır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

##  <a name="unable-to-collect-performance-counters-on-test-agent-computer"></a>Test aracısı bilgisayarda performans sayaçları toplanamıyor

Bir yük testi çalıştırdığınızda performans sayaçlarını toplayan ve bir test ajanı bilgisayarına bağlanmaya çalıştığınızda hatalar alabilirsiniz. Uzak Kayıt Defteri hizmeti uzak bir bilgisayara performans sayacı verisi sağlamaktan sorumlu hizmettir. Bazı işletim sistemlerinde, uzak kayıt defteri hizmeti otomatik olarak başlatılmaz. Bu sorunu gidermek için uzak kayıt defteri hizmetini el ile başlatın.

> [!NOTE]
> Uzak Kayıt Defteri hizmeti erişebileceğiniz **Denetim Masası.** Seçin **Yönetimsel Araçlar** seçip **Hizmetleri**.

Başka bir sorunun nedenini performans sayaçlarını okumak için yeterli izinlere sahip değil ' dir. Yerel test çalıştırmalarında, testi çalıştıran kullanıcının hesap Power Users grubunun veya daha yüksek bir üyesi olmanız veya Performance Monitor Users grubunun bir üyesi olmanız gerekir. Uzaktan test denetleyicisi Power Users grubunun bir üyesi olarak çalıştırmak için yapılandırılmış veya sonraki bir sürümünü hesabı çalışır ya da Performance Monitor Users grubunun bir üyesi olmanız için.

## <a name="set-the-logging-level-on-a-test-controller-computer"></a>Bir test denetleyicisi bilgisayarda günlük düzeyini ayarlama

Bir test denetleyicisi bilgisayarda günlük düzeyini denetleyebilirsiniz. Bir ortamda bir yük testi çalıştırırken bir problemi tanılamaya çalışıyorsanız bu kullanışlıdır.

### <a name="to-set-the-logging-level-on-a-test-controller-computer"></a>Bir test denetleyicisi bilgisayarda günlük düzeyini ayarlamak için

1.  Test denetleyicisi hizmetini durdurun. Bir komut isteminde `net stop vsttcontroller`.

2.  Dosyayı açmak *QTController.exe.config*. Bu dosya, denetleyici yükleme dizininde bulunur.

3.  Girişini Düzenle `EqtTraceLevel` dosyanın sistem tanılama bölümüne geçin. Kodunuzu şuna benzemelidir:

    ```xml
    <system.diagnostics>
        <trace autoflush="true" indentsize="4">
            <listeners>
                <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="d:\VSTestHost.log" />
            </listeners>
        </trace>
        <switches>
            <!-- You must use integral values for "value":
                    0 = off,
                    1 = error,
                    2 = warn,
                    3 = info,
                    4 = verbose. -->
            <add name="EqtTraceLevel" value="4" />
        </switches>
    </system.diagnostics>
    ```

4.  Dosyayı kaydedin.

5.  Denetleyici hizmetini başlatın. Bir komut isteminde `net start vsttcontroller`.

Bu test denetleyicisi, test aracısı servisi ve test aracısı işlemi için geçerlidir. Sorunları tanılarken, her üç işlemde de günlük tutmayı etkinleştirmek yardımcı. Günlük tutma düzeyini ayarlamaya ilişkin yordam, test denetleyicisi için daha önce belirtildiği gibi her üç işlem için aynıdır. Test aracısı için hizmet ve aracı işleminin günlük düzeylerini ayarlamak için aşağıdaki yapılandırma dosyalarını kullanın:

-   *QTController.exe.config* denetleyici hizmeti

-   *QTAgentService.exe.config* Aracısı hizmeti

-   *QTDCAgent (32).exe.config* 32 bit mimari için aracı verileri bağdaştırıcı işlemi.

-   *QTDCAgent (64).exe.config* 64 bit mimari için aracı verileri bağdaştırıcı işlemi.

-   *QTAgent (32).exe.config* 32 bit mimari için aracı test işlemi.

-   *QTAgent (64).exe.config* 64 bit mimari için aracı test işlemi.

## <a name="bind-a-test-controller-to-a-network-adapter"></a>Bir ağ bağdaştırıcısına bir test denetleyicisi bağlama

Bir test ajanı ayarlamaya çalıştığınızda şu hatayı alabilirsiniz:

**8110 hata oluştu. Belirtilen denetleyici bilgisayara bağlanın veya denetleyici nesneye erişim değiştirilemez.**

Birden fazla ağ bağdaştırıcısı olan bir bilgisayarda test denetleyicisi yükleyerek bu hatayı neden olabilir.

> [!NOTE]
> Test aracıları başarıyla yükleyip, bu sorunla bir testi çalıştırmaya çalışana kadar karşılaşmamanız da olasıdır.

Bu hatayı düzeltmek için test denetleyicisini ağ bağdaştırıcılarından birine bağlamanız gerekir. Ayarlamak zorunda `BindTo` özelliği test denetleyicisi ve ardından değişiklik başvurmak için test aracısı test IP adresiyle yerine adına göre. Adımlar aşağıdaki yordamlarda sağlanır.

### <a name="to-obtain-the-ip-address-of-the-network-adapter"></a>Ağ bağdaştırıcısının IP adresini almak için

1.  Seçin **Başlat**ve ardından **çalıştırma**.

     **Çalıştırma** iletişim kutusu görüntülenir.

2.  Tür `cmd` seçip **Tamam**.

     Bir komut istemi açılır.

3.  Türü `ipconfig /all`

     Ağ bağdaştırıcılarınız için IP adresleri görüntülenir. Denetleyicinizi bağlamak istediğiniz ağ bağdaştırıcısının IP adresini kaydedin.

### <a name="to-bind-a-test-controller-to-a-network-adapter"></a>Bir test denetleyicisi bir ağ bağdaştırıcısına bağlamak için

1.  Test denetleyicisi hizmetini durdurun. Bir komut isteminde `net stop vsttcontroller`.

2.  Dosyayı açmak *QTController.exe.config*. Bu dosya bulunan *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

3.  Bir girdi ekleyin `BindTo` uygulama ayarları için özellik. Denetleyiciyi bağlamak istediğiniz ağ bağdaştırıcısının IP adresini belirtin. Kodunuzu şuna benzemelidir:

    ```xml
    <appSettings>
        <add key="LogSizeLimitInMegs" value="20" />
        <add key="AgentSyncTimeoutInSeconds" value="120" />
        <add key="ControllerServicePort" value="6901" />
        <add key="ControllerUsersGroup" value="TeamTestControllerUsers" />
        <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins" />
        <add key="CreateTraceListener" value="no" />
        <add key="BindTo" value="<YOUR IP ADDRESS>" />
    </appSettings>
    ```

4.  Dosyayı kaydedin.

5.  Test denetleyicisi hizmetini başlatın. Bir komut isteminde `net start vsttcontroller`.

### <a name="to-connect-a-test-agent-to-a-bound-controller"></a>Bir test aracısını bir bağlama denetleyicisine bağlamak için

-   Test aracısını yüklemeyi yeniden çalıştırın. Bu kez, test denetleyicisinin adı yerine test denetleyicisinin IP adresini belirtin.

Bu test denetleyicisi, test aracısı servisi ve test aracısı işlemi için geçerlidir. `BindTo` Özelliği, birden fazla ağ bağdaştırıcısı olan bir bilgisayarda çalışan her işlem için ayarlanmalıdır. Ayarlamaya ilişkin yordam `BindTo` özelliği olduğundan, test denetleyicisi için daha önce belirtildiği gibi her üç işlem için aynıdır. Test aracısı servisi ve test aracısı işleminin günlük düzeylerini ayarlamak için listelenen yapılandırma dosyalarını kullanın. [bir test denetleyicisi bilgisayarda günlük düzeyini ayarlama](#set-the-logging-level-on-a-test-controller-computer).

## <a name="see-also"></a>Ayrıca bkz.

- [Test denetleyicileri ve test aracıları](../test/configure-test-agents-and-controllers-for-load-tests.md)
