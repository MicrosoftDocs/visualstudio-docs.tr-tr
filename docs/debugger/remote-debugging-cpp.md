---
title: Uzaktan hata ayıklama Visual C++ projesi | Microsoft Docs
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 8b8eca0d-122f-4eda-848a-cf0945f207d0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 4677380081aaa0ac79f589ea7594f19f78750613
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844113"
---
# <a name="remote-debugging-a-visual-c-project-in-visual-studio"></a>Uzaktan hata ayıklama Visual Studio'da Visual C++ projesi
Farklı bir bilgisayarda bir Visual Studio uygulamasında hata ayıklama, yükleme ve uygulamanızı dağıtacağınız bilgisayarda Uzak araçları çalıştırmak için projenizi Visual Studio'dan uzak bilgisayara bağlanın ve ardından dağıtmak ve uygulamanızı çalıştırmak için yapılandırın.

![Uzaktan hata ayıklayıcı bileşenleri](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Uzaktan hata ayıklama Evrensel Windows uygulamaları (UWP) hakkında daha fazla bilgi için bkz. [bir yüklenen uygulama paketinin hatalarını ayıklama](debug-installed-app-package.md).

## <a name="requirements"></a>Gereksinimler

Desteklenen Windows 7 ve daha yeni uzaktan hata ayıklayıcı (telefon değil) ve Windows Server 2008 Service Pack 2'ile başlayan Windows Server sürümleri. Gereksinimlerinin tam listesi için bkz. [gereksinimleri](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Bir proxy üzerinden bağlı iki bilgisayar arasında hata ayıklama desteklenmiyor. Ülkeler yüksek gecikme süresi veya çevirmeli, Internet gibi düşük bant genişliği bağlantı üzerinden veya Internet üzerinden hata ayıklama önerilmez ve başarısız olabilir veya edilemeyecek kadar yavaş.
  
## <a name="download-and-install-the-remote-tools"></a>Uzak araçları indirme ve yükleme

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
> [!TIP]
> Bazı senaryolarda, uzaktan hata ayıklayıcıyı bir dosya paylaşımından çalıştırma en verimli olabilir. Daha fazla bilgi için [uzaktan hata ayıklayıcıyı bir dosya paylaşımından çalıştırma](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a> Uzaktan hata ayıklayıcı ayarlayın

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Gerektiğinde ek kullanıcılar için izinler eklemek için kimlik doğrulama modunu değiştirmek veya bağlantı noktası numarası için uzaktan hata ayıklayıcı değilse [uzaktan hata ayıklayıcı yapılandırma](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote_cplusplus"></a> Visual C++ projesinin hatalarını uzaktan ayıklama  
 Aşağıdaki yordamda projesinin yolunu ve adını C:\remotetemp\MyMfc ve uzak bilgisayarın adını **MJO DL**.  
  
1. Adlı bir MFC uygulaması oluşturmak **mymfc.**  
  
2. Herhangi bir kolayca, örnekte için ulaşıldığında uygulamada bir kesme noktası ayarlayın **MainFrm.cpp**, başlangıcında `CMainFrame::OnCreate`.  
  
3. Çözüm Gezgini'nde sağ tıklatın ve proje **özellikleri**. Açık **hata ayıklama** sekmesi.  
  
4. Ayarlama **başlatmak için hata ayıklayıcı** için **uzaktan Windows hata ayıklayıcı**.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. Aşağıdaki özelliklerde değişiklik:  
  
   |Ayar|Değer|
   |-|-|  
   |Uzaktan komut|C:\remotetemp\mymfc.exe|  
   |Çalışma dizini|C:\remotetemp|  
   |Uzak sunucu adı|MJO DL:*BağlantıNoktasıNumarası*|  
   |bağlantı|Windows kimlik doğrulaması ile uzaktan|  
   |Hata ayıklayıcı türü|Yalnızca yerel|  
   |Dağıtım dizini|C:\remotetemp.|  
   |Dağıtılacak ek dosyalar|C:\data\mymfcdata.txt.|  
  
    (İsteğe bağlı) ek dosyaları dağıtmak istiyorsanız her iki makinelerde klasörü bulunmalıdır.  
  
6. Çözüm Gezgini'nde çözüme sağ tıklayıp seçin **Configuration Manager**.  
  
7. İçin **hata ayıklama** yapılandırma, select **Dağıt** onay kutusu.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Hata Ayıklamayı Başlat (**hata ayıklama > hata ayıklamayı Başlat**, veya **F5**).  
  
9. Yürütülebilir dosyayı uzak bilgisayara otomatik olarak dağıtılır.  
  
10. İstenirse, uzak makineye bağlanmak için ağ kimlik bilgilerini girin.  
  
     Gerekli kimlik bilgilerinin, ağınızın güvenlik yapılandırması'nı özgüdür. Örneğin, bir etki alanı bilgisayarında güvenlik sertifikasını seçin veya etki alanı adınızı ve parolanızı girin. Bir etki alanı olmayan makinede, makine adı ve geçerli kullanıcı hesabı adı gibi girebilirsiniz <strong>MJO-DL\name@something.com</strong>, doğru parola ile birlikte.  
  
11. Visual Studio bilgisayarda yürütme kesme noktasında durdurulduğunu görmeniz gerekir.  
  
    > [!TIP]
    >  Alternatif olarak, dosyaların ayrı bir adım olarak dağıtabilirsiniz. İçinde **Çözüm Gezgini** sağ **mymfc** düğümünü seçip **Dağıt**.  
  
    Uygulama tarafından kullanılması gereken kod dışı dosyalara varsa, bunları Visual Studio projenize eklemeniz gerekir. Ek dosyalar için bir proje klasörü oluşturun (içinde **Çözüm Gezgini**, tıklayın **Ekle > Yeni klasör**.) Dosyaları klasöre eklersiniz (içinde **Çözüm Gezgini**, tıklayın **Ekle > var olan öğe**, ardından dosyaları seçin). Üzerinde **özellikleri** sayfasında her dosya için **çıkış dizinine Kopyala** için **her zaman Kopyala**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Uzak simgeleri ile hata ayıklamayı kurma 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)] 
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio’da hata ayıklama](../debugger/index.md)  
 [Hata ayıklayıcısı özellik turu](../debugger/debugger-feature-tour.md)   
 [Uzaktan hata ayıklama için Windows Güvenlik duvarını yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md)   
 [Uzak IIS Bilgisayarında Uzaktan ASP.NET ile Hata Ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)