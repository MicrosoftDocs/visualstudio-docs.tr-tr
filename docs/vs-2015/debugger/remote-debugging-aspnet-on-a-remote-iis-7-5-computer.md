---
title: Uzak bir IIS 7.5 ASP.NET hata ayıklama uzak bilgisayarı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71d249571830ac608bef12c4a47d0243de1859a5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764066"
---
# <a name="remote-debugging-aspnet-on-a-remote-iis-computer"></a>Uzaktan hata ayıklama Uzak IIS bilgisayarında ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IIS ile Windows Server bilgisayarı için bir ASP.NET Web uygulamasını dağıtma ve uzaktan hata ayıklama için ayarlayın. Bu kılavuz, ayarlayın ve Visual Studio 2015 MVC 4.5.2 uygulama yapılandırmak, IIS'ye dağıtma ve Visual Studio'dan uzak hata ayıklayıcıyı iliştirmek açıklanmaktadır.

Bu yordamlar bu sunucu yapılandırmaları üzerinde test edilmiştir:
* Windows Server 2012 R2 ve IIS 10
* Windows Server 2008 R2 ve IIS 7.5

Bu makaledeki bilgilerin çoğu için de geçerlidir ASP.NET core uygulamaları dağıtımını farklıdır ve ek adımlar gerektirir dışında uzak bir ASP.NET Core uygulaması hata ayıklama için. IIS ile ASP.NET Core uygulaması dağıtmak için tüm bölümleri tamamlayın gerekecektir [bu makalede](https://docs.asp.net/en/latest/publishing/iis.html).

## <a name="prerequisites-install-the-remote-debugger-on-the-windows-server-computer"></a>Önkoşullar: uzaktan hata ayıklayıcıyı Windows Server yüklü bir bilgisayara yükleyin.

Uzaktan hata ayıklayıcıyı Windows Server'a yükleme hakkında yönergeler için bkz: [uzaktan hata ayıklama](../debugger/remote-debugging.md).

ASP.NET uygulamalarının uzaktan hata ayıklama yapmak için uzaktan hata ayıklayıcı uygulamasını yönetici olarak çalıştırmak veya uzaktan hata ayıklayıcıyı bir hizmet olarak başlat. Uzaktan hata ayıklayıcıyı bir hizmet içinde bulunan çalıştırma hakkında ayrıntılar [uzaktan hata ayıklama](../debugger/remote-debugging.md).

Yüklendikten sonra uzaktan hata ayıklayıcı hedef makinede çalıştığından emin olun. (Yüklü değilse, arama **uzaktan hata ayıklayıcı** içinde **Başlat** menüsü. ) Uzaktan hata ayıklayıcı penceresini aşağıdaki gibi görünür. (varsayılan bağlantı noktası numarası 4020 olduğu)

![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
## <a name="create-the-application-on-the-visual-studio-computer"></a>Visual Studio bilgisayarında uygulama oluşturun  
  
1. Yeni bir ASP.NET MVC uygulaması oluşturun. (**Dosya / yeni / Project**, ardından **Visual C# / Web / ASP.NET Web uygulaması** . İçinde **ASP.NET 4.5.2** şablonları bölümünden **MVC**. Emin olun **buluttaki konak** Azure bölümü altında seçilmedi. Projeyi adlandırın **MyMVC**.)
1. HomeController.cs dosyasını açın ve bir kesim noktası `About()` yöntemi.
1. İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Yayımla**.
1. İçin **yayımlama hedefi seçin**seçin **özel** ve profil adı **MyMVC**. **İleri**'ye tıklayın.
1. Üzerinde **bağlantı** sekmesinde, belirleyin **yayımlama yöntemi** alanı **dosya sistemi** ve **hedef konum** yerel bir dizin alanı. **İleri**'ye tıklayın.

    ![RemoteDBG_Publish_Local](../debugger/media/remotedbg-publish-local.png "RemoteDBG_Publish_Local")
1. Yapılandırmayı ayarlamak **hata ayıklama**. Tıklayın **yayımlama**.

    ![RemoteDBG_Publish_Debug_Config](../debugger/media/remotedbg-publish-debug-config.png "RemoteDBG_Publish_Debug_Config")
    
    Uygulama yerel dizine yayımlanması gerekir.

## <a name="BKMK_deploy_asp_net"></a> Windows Server Uzak bilgisayarda ASP.NET uygulaması dağıtma

 Bu bölümde, Windows Server bilgisayarında zaten IIS etkinleştirilmiş olduğunu varsayar. Windows Server 2012 R2 üzerinde görmek [IIS yapılandırması](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration) IIS etkinleştirmek için. (Bir ASP.NET Core uygulaması dağıtmaya çalıştığınız sürece, bu makalede diğer bölümlerini atlayabilirsiniz. ASP.NET Core için aşağıda açıklanan adımları yerine uygulamayı dağıtmak için bu makaledeki adımları izleyin.)
1. ASP.NET ASP.NET 4.5 yüklemek için Web Platformu bileşenlerini yükleyin (Windows Server 2012 R2'de sunucu düğümünden seçin **yeni Web Platformu bileşenlerini Al** ve ASP.NET için arama)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg-iis-aspnet-45.png "RemoteDBG_IIS_AspNet_45")

    Windows Server 2008 R2'de ASP.NET 4'ü bunun yerine şu komutu kullanarak yükleyin: **\v4.0.30319\aspnet_regiis.exe C:\Windows\Microsoft.NET\Framework (64) - IR**
1. ASP.NET proje dizini Visual Studio bilgisayarı yerel bir dizine kopyalayın (hangi sizi ararız **C:\Publish**) Windows Server bilgisayarında. Projeyi el ile kopyalayın, Xcopy, Web dağıtımı, Robocopy, Powershell veya diğer seçenekleri kullanın.

    > [!CAUTION]
    >  Kod veya yeniden oluşturma için değişiklikler yapmanız gerekirse yeniden yayımlamanız ve bu adımı yineleyin. Yerel kaynak ve simgeler, uzak makineye kopyaladığınız yürütülebilir dosyanın tam olarak eşleşmelidir.
1. Web.config dosyasının doğru sürümü .NET Framework'ün gösterdiğinden emin olun.  Örneğin, Windows Server 2008 R2 üzerinde varsayılan olarak yüklü .NET Framework sürüm 4.0.30319 ancak bir ASP.NET 4.5.2 oluşturduğumuz sürümü. Windows Server bilgisayarında ASP.NET 4.0 uygulama çalışıyorsa, sürümü değiştirmek gerekir:
  
    ```xml
    <system.web>
        <authentication mode="None" />  
        <compilation debug="true" targetFramework="4.0.30319" />
        <httpRuntime targetFramework="4.0.30319" />
      </system.web>
  
    ```
1. Açık **Internet Information Services (IIS) Yöneticisi'ni** gidin **siteleri**.
1. Sağ **varsayılan Web sitesi** düğümünü seçip alt **uygulama Ekle**.
1. Ayarlama **diğer** alanı **MyMVC** uygulama havuzu alanını **ASP.NET v4.0** (ASP.NET 4.5 uygulama havuzu için bir seçenek değildir). Ayarlama **fiziksel yolu** için **C:\Publish** (kopyaladığınız ASP.NET proje dizini).

    >[!NOTE] 
    > ASP.NET Core uygulamaları için uygulama havuzu alanın ayarlanacağı **yönetilen kod yok**.
1. Sağ tıklayarak dağıtımı test etme **varsayılan Web sitesi** seçip **Gözat**.
    Uygulama başarıyla dağıtıldı, web sayfasını görürsünüz.

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a>Visual Studio bilgisayardan ASP.NET uygulamasına ekleme

1. Visual Studio bilgisayarda açın **MyMVC** çözüm.
1. Visual Studio'da **hata ayıklama / iliştirme** (**Ctrl + Alt + P**).
1. Niteleyici alanın ayarlanacağı  **\<uzak bilgisayar adı >: 4020**.
1. Tıklayın **Yenile**.
    Bazı işlemler görünür görmelisiniz **kullanılabilir işlemler** penceresi.

    Herhangi bir işlem görmüyorsanız (bağlantı noktası gereklidir) uzak bilgisayar adı yerine IP adresini kullanarak deneyin. Kullanım `ipconfig` IPv4 adresini almak için komut satırında.
1. Denetleme **tüm kullanıcıların işlemlerini göster**.
1. Aranacak **w3wp.exe** tıklatıp **iliştirme**.

     İşlem adı hızlıca bulmak için işlemi ilk harflerini yazın.
     
    >[!NOTE]
    > ASP.NET Core uygulaması için w3wp.exe yerine dnx.exe işlem'i seçin. (Bu işlem adı gelecek bir sürümde değişebilir.)

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")

1. Uzak bilgisayarın Web sitesini açın. Bir tarayıcıda Git **http://\<uzak bilgisayar adı >**.
    
    ASP.NET web sayfası görmeniz gerekir.
1. ASP.NET web sayfasındaki bağlantısını tıklatın **hakkında** sayfası.

    Visual Studio'da kesme noktasına isabet.



