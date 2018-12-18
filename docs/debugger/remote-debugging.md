---
title: Uzaktan hata ayıklama | Microsoft Docs
ms.custom:
- remotedebugging
- seodec18
ms.date: 07/02/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6701a05d76117e0b8164488de3ec858c61021e17
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065512"
---
# <a name="remote-debugging"></a>Uzaktan Hata Ayıklama
Farklı bir bilgisayara dağıtılan bir Visual Studio uygulamada hata ayıklaması yapabilirsiniz. Bunu yapmak için Visual Studio uzaktan hata ayıklayıcıyı kullanın.

Uzaktan hata ayıklama hakkındaki ayrıntılı yönergeler için aşağıdaki konulara bakın.

|Senaryo|Bağlantı|
|-|-|-|
|Azure uygulama hizmeti|[Anlık görüntü hata ayıklayıcısı](../debugger/debug-live-azure-applications.md) veya [uzaktan Azure üzerinde ASP.NET hatalarını ayıklama](../debugger/remote-debugging-azure.md)|
|Azure VM|[Azure’da ASP.NET hatalarını uzaktan ayıklama](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Bir Azure Service Fabric uygulamasının hatalarını ayıklama](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Uzaktan hata ayıklama ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) veya [uzaktan hata ayıklama ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# veya Visual Basic|[Uzaktan C# veya Visual Basic projesi hatası ayıklama](../debugger/remote-debugging-csharp.md)|
|C++|[C++ projesinin hatalarını uzaktan ayıklama](../debugger/remote-debugging-cpp.md)|
|Evrensel Windows uygulamaları (UWP)|[Uzak makinede UWP uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md) veya [yüklü uygulama paketinin hatalarını ayıklama](../debugger/debug-installed-app-package.md)|

Hemen indirin ve uzaktan hata ayıklayıcıyı yüklemek istediğiniz ve senaryonuz için tüm ek yönergeleri gerekmez, bu makaledeki adımları izleyin.

## <a name="download-and-install-the-remote-tools"></a>Uzak araçları indirme ve yükleme

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements_msvsmon"></a> Gereksinimleri

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="fileshare_msvsmon"></a> (İsteğe bağlı) Uzaktan hata ayıklayıcıyı bir dosya paylaşımından çalıştırmak için

Uzaktan hata ayıklayıcıyı bulabilirsiniz (*msvsmon.exe*) bir bilgisayarda Visual Studio Community, Professional veya Enterprise zaten yüklü. Bazı senaryolarda, uzaktan hata ayıklamayı kurma en kolay yolu uzaktan hata ayıklayıcı (msvsmon.exe) bir dosya paylaşımından çalıştırmaktır. Kullanım kısıtlamaları için uzaktan hata ayıklayıcının yardım sayfasına bakın (**Yardım > kullanım** uzaktan hata ayıklayıcı).

1. Bulma *msvsmon.exe* Visual Studio sürümünüzle eşleşen dizinde. Visual Studio Enterprise 2017 için:

      *Program dosyaları (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

      *Program dosyaları (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

2. Paylaşım **uzaktan hata ayıklayıcı** Visual Studio bilgisayardaki klasör.

3. Uzak bilgisayarda çalıştırmak *msvsmon.exe* paylaşılan klasörden. İzleyin [kurulum yönergeleri](#bkmk_setup).

> [!TIP]
> Komut satırı yükleme ve komut satırı başvurusu için yardım sayfasına bakın *msvsmon.exe* yazarak ``msvsmon.exe /?`` Visual Studio'nun yüklü olan bilgisayarda bir komut satırında (veya Git **Yardım > kullanım**uzaktan hata ayıklayıcı).

## <a name="bkmk_setup"></a> Uzaktan hata ayıklayıcı ayarlayın

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure_msvsmon"></a> Uzaktan hata ayıklayıcı yapılandırma
İlk kez başlattıktan sonra bazı yönleri uzaktan hata ayıklayıcı yapılandırmasını değiştirebilirsiniz.

-   Öğesini uzaktan hata ayıklayıcıya bağlanmak diğer kullanıcılar için izinler eklemek gerekiyorsa **Araçlar > izinleri**. İzinleri vermek veya reddetmek için yönetici ayrıcalıklarınızın olması gerekir.

     > [!IMPORTANT]
     > Visual Studio bilgisayarda kullandığınız kullanıcı hesabına ait farklı bir kullanıcı hesabı altında uzaktan hata ayıklayıcı çalıştırabilirsiniz, ancak farklı bir kullanıcı hesabı için uzaktan hata ayıklayıcının izinleri eklemeniz gerekir.

     Alternatif olarak, komut satırından uzaktan hata ayıklayıcıyı başlatabilirsiniz **/ allow \<kullanıcıadı >** parametresi: **msvsmon / allow \< username@computer>**.

-   Kimlik doğrulama modunu veya bağlantı noktası numarasını değiştirin veya uzak araçlar için bir zaman aşımı değeri belirtmek gerekirse: seçin **Araçlar > Seçenekler**.

     Varsayılan olarak kullanılan bağlantı noktası numaraları listesi için bkz. [uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     >  Uzak araçları Kimlik Doğrulaması Yok modunda çalıştırmayı seçebilirsiniz, fakat bu mod kesinlikle önerilmez. Bu modda çalıştırdığınızda, ağ güvenliği yoktur. Yalnızca ağ kötü amaçlı veya tehlikeli trafik karşı risk altında olduğunu eminseniz kimlik doğrulaması yok modu seçin.

##  <a name="bkmk_configureService"></a> (İsteğe bağlı) Uzaktan hata ayıklayıcıyı bir hizmet olarak yapılandırma
ASP.NET ve diğer sunucu ortamlarında hata ayıklama için uzaktan hata ayıklayıcı yönetici olarak çalıştırın veya gerekir, her zaman çalışır, isterseniz, uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırın.

 Uzaktan hata ayıklayıcıyı bir hizmet olarak yapılandırmak istiyorsanız, aşağıdaki adımları izleyin.

1. Bulma **uzaktan hata ayıklayıcı Yapılandırma Sihirbazı'nı** (rdbgwiz.exe). (Uzaktan hata ayıklayıcı ayrı bir uygulamadan budur.) Yalnızca uzak araçları yüklediğinizde kullanılabilir. Visual Studio ile yüklü değil.

2. Yapılandırma Sihirbazı'nı çalıştırmaya başlayın İlk sayfasına geldiğinde tıklayın **sonraki**.

3. Denetleme **Visual Studio 2015 uzaktan hata ayıklayıcı bir hizmet olarak çalıştırmak** onay kutusu.

4. Parola ve hesap adını ekleyin.

    Eklemeniz gerekebilir **hizmet oturum açma** sağ bu hesap için kullanıcı (Bul **yerel güvenlik ilkesi** (secpol.msc) içinde **Başlat** sayfası veya pencere (veya türü  **secpol** bir komut isteminde). Penceresi açıldığında, çift **kullanıcı hakları ataması**, ardından bulun **hizmet oturum açma** sağ bölmede. Çift tıklatın. Kullanıcı hesabına eklemek **özellikleri** penceresini açın ve **Tamam**). **İleri**'ye tıklayın.

5. Uzak araçların iletişim kurmak istediğiniz ağ türünü seçin. En az bir ağ türü seçilmelidir. Bilgisayarları bir etki alanına bağlıysanız, ilk öğe seçmeniz gerekir. Bilgisayar bir çalışma grubunda veya ev grubu bağlıysa, ikinci veya üçüncü öğe seçmeniz gerekir. **İleri**'ye tıklayın.

6. Hizmetin başlatılması, görürsünüz **Visual Studio uzaktan hata ayıklayıcı Yapılandırma Sihirbazı başarıyla tamamladınız**. Hizmet başlatılamazsa göreceğiniz **Visual Studio uzaktan hata ayıklayıcı Yapılandırma Sihirbazı tamamlanamadı**. Sayfa aynı zamanda hizmetin başlatılması almak için izlemeniz gereken bazı ipuçları sağlar.

7. **Son**'a tıklayın.

   Bu noktada uzaktan hata ayıklayıcıyı bir hizmet olarak çalışıyor. Bu sayfasına giderek kontrol **Denetim Masası > Hizmetleri** ve örnek kod **Visual Studio 2015 uzaktan hata ayıklayıcı**.

   Uzaktan hata ayıklayıcı hizmetini durdurup **Denetim Masası > Hizmetleri**.

## <a name="set-up-debugging-with-remote-symbols"></a>Uzak simgeleri ile hata ayıklamayı kurma

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcısı özellik turu](../debugger/debugger-feature-tour.md)
- [Windows Güvenlik Duvarı’nı Uzaktan Hata Ayıklama İçin Yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları](../debugger/remote-debugger-port-assignments.md)
- [Uzaktan hata ayıklama Uzak IIS bilgisayarında ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)