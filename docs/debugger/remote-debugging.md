---
title: Uzaktan hata ayıklama | Microsoft Docs
description: Visual Studio uzaktan hata ayıklayıcı kullanılarak farklı bir bilgisayara dağıtılmış bir Visual Studio uygulamasında hata ayıklayın.
ms.custom:
- remotedebugging
- seodec18
- SEO-VS-2020
ms.date: 07/02/2018
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f67035dc2f7a33fb436c0c51ba2214272ab2cf79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891429"
---
# <a name="remote-debugging"></a>Uzaktan Hata Ayıklama
Farklı bir bilgisayara dağıtılmış bir Visual Studio uygulamasında hata ayıklaması yapabilirsiniz. Bunu yapmak için, Visual Studio uzaktan hata ayıklayıcı 'yı kullanırsınız.

Uzaktan hata ayıklama hakkında ayrıntılı yönergeler için bu konulara bakın.

|Senaryo|Bağlantı|
|-|-|-|
|Azure App Service|[Azure 'Da uzaktan hata ayıklama ASP.net](../debugger/remote-debugging-azure.md) veya Visual Studio Enterprise için [Snapshot Debugger](../debugger/debug-live-azure-applications.md)|
|Azure VM|[Azure’da ASP.NET hatalarını uzaktan ayıklama](../debugger/remote-debugging-azure.md)|
|Azure Service Fabric|[Azure Service Fabric uygulamasında hata ayıklama](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)|
|ASP.NET|[Uzaktan hata ayıklama ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) veya [uzaktan hata ayıklama ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# veya Visual Basic|[Uzaktan C# veya Visual Basic projesi hatası ayıklama](../debugger/remote-debugging-csharp.md)|
|C++|[C++ projesinin hatalarını uzaktan ayıklama](../debugger/remote-debugging-cpp.md)|
|Evrensel Windows uygulamaları (UWP)|[UWP uygulamalarını uzak bir makinede çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md) veya [yüklü bir uygulama paketinin hatalarını ayıklama](../debugger/debug-installed-app-package.md)|

Yalnızca uzaktan hata ayıklayıcıyı indirip yüklemek istiyorsanız ve senaryonuz için ek yönergeler gerekmiyorsa, bu makaledeki adımları izleyin.

## <a name="download-and-install-the-remote-tools"></a>Uzak araçları indirme ve yükleme

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="requirements"></a><a name="requirements_msvsmon"></a> Gereklilik

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]

## <a name="optional-to-run-the-remote-debugger-from-a-file-share"></a><a name="fileshare_msvsmon"></a> Seçim Uzaktan hata ayıklayıcıyı bir dosya paylaşımından çalıştırmak için

Uzaktan hata ayıklayıcı 'yı (*msvsmon.exe*) Visual Studio Community, Professional veya Enterprise 'ın zaten yüklü olduğu bir bilgisayarda bulabilirsiniz. Bazı senaryolarda, uzaktan hata ayıklamayı ayarlamanın en kolay yolu, uzaktan hata ayıklayıcıyı (msvsmon.exe) bir dosya paylaşımından çalıştırmalıdır. Kullanım sınırlamaları için, uzaktan hata ayıklayıcının yardım sayfasına bakın (uzaktan hata ayıklayıcı 'da **yardım > kullanımı** ).

1. Visual Studio sürümünüz ile eşleşen dizinde *msvsmon.exe* bulun:

   ::: moniker range=">=vs-2019"

   *Program dosyaları (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program dosyaları (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end
   ::: moniker range="vs-2017"

   *Program dosyaları (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe*

   *Program dosyaları (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe*

   ::: moniker-end

2. Visual Studio bilgisayarında **Uzaktan hata ayıklayıcı** klasörünü paylaşma.

3. Uzak bilgisayarda, paylaşılan klasörden *msvsmon.exe* ' yi çalıştırın. [Kurulum yönergelerini](#bkmk_setup)izleyin.

> [!TIP]
> Komut satırı yüklemesi ve komut satırı başvurusu için, Visual Studio yüklü bilgisayardaki komut satırına yazarak *msvsmon.exe* için yardım sayfasına bakın ``msvsmon.exe /?`` (veya uzaktan hata ayıklayıcıda **Yardım > kullanımı** ' na gidin).

## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a> Uzaktan hata ayıklayıcıyı ayarlama

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure-the-remote-debugger"></a><a name="configure_msvsmon"></a> Uzaktan hata ayıklayıcıyı yapılandırma
Uzaktan hata ayıklayıcı yapılandırmasının bazı yönlerini ilk kez başlattıktan sonra değiştirebilirsiniz.

- Diğer kullanıcıların uzaktan hata ayıklayıcıya bağlanması için izinler eklemeniz gerekiyorsa, **araçlar > izinler**' i seçin. İzinleri vermek veya reddetmek için yönetici ayrıcalıklarınızın olması gerekir.

     > [!IMPORTANT]
     > Uzaktan hata ayıklayıcıyı, Visual Studio bilgisayarında kullandığınız kullanıcı hesabından farklı bir kullanıcı hesabı altında çalıştırabilirsiniz, ancak uzak hata ayıklayıcının izinlerine farklı kullanıcı hesabını eklemeniz gerekir.

     Alternatif olarak, uzaktan hata ayıklayıcıyı **/Allow \<username>** parametresi: **\<username@computer> msvsmon/Allow** ile komut satırından başlatabilirsiniz.

- Kimlik doğrulama modunu veya bağlantı noktası numarasını değiştirmeniz veya uzak Araçlar için bir zaman aşımı değeri belirtmeniz gerekiyorsa: **araçlar > seçenekler**' i seçin.

     Varsayılan olarak kullanılan bağlantı noktası numaralarının listesi için bkz. [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md).

     > [!WARNING]
     > Uzak araçları Kimlik Doğrulaması Yok modunda çalıştırmayı seçebilirsiniz, fakat bu mod kesinlikle önerilmez. Bu modda çalıştırdığınızda, ağ güvenliği yoktur. Yalnızca ağın kötü amaçlı veya tehlikeli trafikten risk altında olmadığından eminseniz kimlik doğrulaması yok modunu seçin.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a> Seçim Uzaktan hata ayıklayıcıyı bir hizmet olarak yapılandırma
ASP.NET ve diğer sunucu ortamlarında hata ayıklama için, uzaktan hata ayıklayıcıyı yönetici olarak çalıştırmanız veya her zaman çalışmasını istiyorsanız, uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırmanız gerekir.

 Uzaktan hata ayıklayıcıyı bir hizmet olarak yapılandırmak istiyorsanız, bu adımları izleyin.

1. **Uzaktan hata ayıklayıcı yapılandırma Sihirbazı 'nı** (rdbgwiz.exe) bulun. (Bu, uzaktan hata ayıklayıcı 'dan ayrı bir uygulamadır.) Yalnızca uzak araçları yüklediğinizde kullanılabilir. Visual Studio ile birlikte yüklenmez.

2. Yapılandırma sihirbazını çalıştırmaya başlayın. İlk sayfa geldiğinde **İleri**' ye tıklayın.

3. **Visual Studio 2015 uzaktan hata ayıklayıcı 'yı hizmet olarak çalıştır** onay kutusunu işaretleyin.

4. Kullanıcı hesabının adını ve parolasını ekleyin.

    Bu hesaba (veya bir komut isteminde **secpol** yazın) **bir hizmet olarak oturum aç** kullanıcısı eklemek için ( **Başlangıç** sayfası veya penceresinde **yerel güvenlik ilkesini** (secpol. msc) bulun. Pencere göründüğünde, **Kullanıcı hakları ataması**' na çift tıklayın ve ardından sağ bölmede **hizmet olarak oturum aç** ' ı bulun. Çift tıklayın. Kullanıcı hesabını **Özellikler** penceresine ekleyin ve **Tamam**' a tıklayın. **İleri**’ye tıklayın.

5. Uzak araçların iletişim kurmasını istediğiniz ağ türünü seçin. En az bir ağ türü seçilmelidir. Bilgisayarlar bir etki alanı üzerinden bağlandıysa, ilk öğeyi seçmeniz gerekir. Bilgisayarlar bir çalışma grubu veya ev grubu üzerinden bağlandıysa, ikinci veya üçüncü öğeleri seçmeniz gerekir. **İleri**’ye tıklayın.

6. Hizmet başlatılabiliyorsanız, **Visual Studio uzaktan hata ayıklayıcı yapılandırma Sihirbazı 'nı başarıyla tamamladınız** görürsünüz. Hizmet başlatılmazsa, **Visual Studio uzaktan hata ayıklayıcı yapılandırma Sihirbazı 'nı tamamlamadığına** Ilişkin bir hata görürsünüz. Bu sayfa, hizmetin başlamasını sağlamak için izlenecek bazı ipuçları da sunar.

7. **Finish (Son)** düğmesine tıklayın.

   Bu noktada, uzaktan hata ayıklayıcı bir hizmet olarak çalışır. Bunu, **Denetim masası > Hizmetleri** ' ne giderek ve **Visual Studio 2015 uzaktan hata ayıklayıcı**' yı arayarak doğrulayabilirsiniz.

   Uzaktan hata ayıklayıcı hizmetini **Denetim masası > Hizmetleri**'nden durdurabilir ve başlatabilirsiniz.

## <a name="set-up-debugging-with-remote-symbols"></a>Uzak simgelerle hata ayıklamayı ayarlama

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Uzaktan hata ayıklama için Windows güvenlik duvarını yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md)
- [Uzak IIS bilgisayarında uzaktan hata ayıklama ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Uzaktan hata ayıklama hataları ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)