---
title: Yardım Görüntüleyicisi Yönetici Kılavuzu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f470c55b08cc559e481ed75e962fda4f0e625a5c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49871296"
---
# <a name="help-viewer-administrator-guide"></a>Yardım Görüntüleyicisi Yönetici Kılavuzu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yardım Görüntüleyici ile veya internet erişimi olmayan ağ ortamları için yerel Yardım yüklemelerini yönetmenize olanak sağlar. Yerel Yardım içeriği makine başına temelinde yapılandırılır. Varsayılan olarak, kullanıcılar, kendi yerel Yardım yüklemesini güncelleştirmek için yönetici haklarına sahip olmalıdır.  
  
 Ağ ortamınız istemcilerin Internet'e erişmesine izin veriyorsa, Yardım Görüntüleyici yerel Yardım içeriğini Internet üzerinden dağıtmak için komut satırı betikleri kullanmanızı sağlar.  
  
 Ağ ortamınız istemcilerin Internet'e erişmesine izin vermez, Yardım Görüntüleyici yerel Yardım içeriğini intranet ve bir ağ paylaşımına dağıtabilirsiniz. Çevrimiçi/çevrimdışı Yardım, IDE'nin ilk başlatılmasında içerik yükleme, intranet içerik hizmeti belirtme IDE'nin gibi Visual Studio IDE Yardım seçeneklerini de devre dışı bırakabilirsiniz ve içeriği yönetme, kayıt defteri anahtarını kullanarak geçersiz kılar.  
  
 Temel sözdizimi aşağıdaki gibidir:  
  
 \<*yolu*> \HlpCtntmgr.exe /operation \< *bağımsız değişken*>/catalogname \< *adı*>/Locale \< *yerelayar*>/sourceurı \< *.msha yolu veya URL'si*>  
  
 HlpCtntMgr.exe komut satırı sözdizimi hakkında daha fazla bilgi için bkz: [için Yardım içeriği Yöneticisi komut satırı bağımsız değişkenleri](../ide/command-line-arguments-for-the-help-content-manager.md).  
  
 Bir intranet Hizmeti uç noktası ve benzeri etkinlik, türleri oluşturma içerik oluşturma hakkında daha fazla bilgi için bkz. Yardım Görüntüleyicisi SDK.  
  
## <a name="deploying-local-help-content-from-the-internet"></a>Yerel Yardım içeriğini Internet üzerinden dağıtma  
 Yerel Yardım içeriğini Internet'ten istemci bilgisayarlara dağıtmak için MSDN içerik paketi hizmetini kullanabilirsiniz. Aşağıdaki sözdizimini kullanın:  
  
 \\<*yolu*> \v2.2\HlpCtntmgr.exe /operation \< *adı*>/catalogname \< *katalog adı*>/Locale \<  *yerel ayar*>  
  
 HlpCtntMgr.exe komut satırı sözdizimi hakkında daha fazla bilgi için bkz: [için Yardım içeriği Yöneticisi komut satırı bağımsız değişkenleri](../ide/command-line-arguments-for-the-help-content-manager.md).  
  
 Gereksinimler:  
  
- İstemci bilgisayarların Internet'e erişimi olmalıdır.  
  
- Kullanıcılar, güncelleştirme, ekleme veya yüklendikten sonra yerel Yardım içeriğini kaldırmak için yönetici haklarına sahip olmalıdır.  
  
  Uyarılar:  
  
- Yardım için varsayılan kaynak çevrimiçi olmaya devam edecektir.  
  
  > [!TIP]
  >  Yardım için varsayılan kaynağı, HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\14.0\help\UseOnlineHelp kayıt defteri anahtarını değiştirerek değiştirebilirsiniz. Daha fazla bilgi için [Yardım İçerik Yöneticisi geçersiz kılmaları](../ide/help-content-manager-overrides.md).  
  
- İstemcileri, Visual Studio'nun ilk başlatma sırasında temel Yardım içeriğini yüklemek için yine de istenir. HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\14.0\Help\DisableFirstRunHelpSelection kayıt defteri anahtarını değiştirerek bu istemi devre dışı bırakabilirsiniz.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek, Visual Studio için İngilizce içeriği bir istemci bilgisayara yükler.  
  
##### <a name="to-install-english-content-from-the-internet"></a>Internet'ten İngilizce içeriği yüklemek için  
  
1.  Seçin **Başlat** seçip **çalıştırma**.  
  
2.  Aşağıdakileri yazın:  
  
     C:\Program dosyaları (x86) \Microsoft Help Viewer\v2.2\hlpctntmgr.exe /operation yüklemek/catalogname VisualStudio14/Locale en-us  
  
3.  ENTER tuşuna basın.  
  
## <a name="deploying-pre-installed-local-help-content-on-client-computers"></a>İstemci bilgisayarlarda önceden yüklenmiş yerel Yardım içeriğini dağıtma  
 İçerik kümesi Online'dan tek bir bilgisayara yükleyin ve ardından, yüklenen içerik kümesini başka bilgisayarlara kopyalayabilirsiniz.  
  
 Gereksinimler:  
  
- İçerik kümesini yüklediğiniz bilgisayarın Internet erişimi olmalıdır.  
  
- Kullanıcılar, güncelleştirme, ekleme veya yüklendikten sonra yerel Yardım içeriğini kaldırmak için yönetici haklarına sahip olmalıdır.  
  
  > [!TIP]
  >  Kullanıcıların yönetici hakları yoksa, Yardım Görüntüleyicisi'nde içeriği Yönet sekmesini devre dışı bırakmanız önerilir. Daha fazla bilgi için [Yardım İçerik Yöneticisi geçersiz kılmaları](../ide/help-content-manager-overrides.md).  
  
  Uyarılar:  
  
- Kullanıcıların yönetici hakları yoksa, Yardım Görüntüleyicisi'nde içeriği Yönet sekmesini devre dışı bırakmanız önerilir. Daha fazla bilgi için [Yardım İçerik Yöneticisi geçersiz kılmaları](../ide/help-content-manager-overrides.md).  
  
- Yardım için varsayılan kaynak çevrimiçi olmaya devam edecektir.  
  
- İstemcileri, Visual Studio'nun ilk başlatma sırasında temel Yardım içeriğini yüklemek için yine de istenir. Daha fazla bilgi için [Yardım İçerik Yöneticisi geçersiz kılmaları](../ide/help-content-manager-overrides.md).  
  
### <a name="create-the-content-set"></a>İçerik kümesi oluşturma  
 Temel içerik kümesini oluşturabilmeniz için önce hedef bilgisayardaki tüm yerel Visual Studio içeriğini kaldırmanız gerekir.  
  
##### <a name="to-uninstall-local-help"></a>Yerel Yardımı kaldırmak için  
  
1. Yardım Görüntüleyici'de seçin **içeriği Yönet** sekmesi.  
  
2. Altında **kullanılabilir belgeler**, Visual Studio belge kümesine gidin.  
  
3. Seçin **Kaldır** her bir alt öğenin yanında.  
  
4. Seçin **Başlat** kaldırmak için  
  
5. Gözat *n*: \ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12 ve klasörün yalnızca catalogType.xml dosyasını içerdiğini doğrulayın.  
  
   Tüm önceden yüklenmiş yerel Visual Studio Yardım içeriğini kaldırdıktan sonra temel içerik kümesini yüklemeye hazırsınız demektir.  
  
##### <a name="to-download-the-content"></a>İçerik indirmek için  
  
1. Yardım Görüntüleyici'de seçin **içeriği Yönet** sekmesi.  
  
2. Altında **kullanılabilir belgeler**, indirin ve ardından istediğiniz belge kümelerine gidin **Ekle**.  
  
3. Seçin **Başlat**.  
  
   Ardından, istemci bilgisayarlara dağıtılacak şekilde içeriği paketlemek gerekir.  
  
##### <a name="to-package-the-content"></a>İçeriği paketlemek için  
  
1.  Daha sonra dağıtım için içeriğin kopyalanacağı bir klasör oluşturun.  
  
     Örneğin: c:\VS12Help.  
  
2.  Yönetici izinlerine sahip cmd.exe açın.  
  
3.  1. adımda oluşturduğunuz klasöre gidin.  
  
4.  Aşağıdakileri yazın:  
  
     Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 \< *KlasörAdı*> \ /y /e /k /o  
  
     Örneğin: `Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 c:\VS12Help\ /y /e /k /o`.  
  
### <a name="deploying-the-content"></a>İçerik dağıtma  
  
##### <a name="to-deploy-the-content"></a>İçerik dağıtmak için  
  
1.  Bir ağ paylaşımı oluşturun ve theee Yardım içeriğini bu konuma kopyalayın.  
  
     Örneğin, c:\VS12Help için içeriği kopyalayın \\\myserver\VS12Help.  
  
2.  Yardım içeriği için dağıtım komut dosyasını içerecek bir .bat dosyası oluşturun. İstemci büyük olasılıkla bir okuma kilidi itmenin parçası silinen dosyaların hiçbirinde olabileceğinden, güncelleştirmeleri göndermeden önce kapatma istemci olmalıdır.  
  
     Örneğin:  
  
    ```  
    REM - copy pre-ripped content to ProgramData  
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o  
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to Programdata (%ERRORLEVEL%)  
  
    REM - get processor type and create/run registry update file  
    IF "%PROCESSOR_ARCHITECTURE%"=="AMD64" GOTO AMD64  
  
    @echo Architecture type is x86  
  
    ECHO Windows Registry Editor Version 5.00 > x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs] >> x86.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12] >> x86.reg  
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg  
    ECHO "FirstTimeRun"="False"  >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12\en-US]  >> x86.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg  
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help]  >> x86.reg  
    ECHO "UseOnlineHelp"=dword:00000000  >> x86.reg  
  
    regedit.exe /s x86.reg  
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x86 reg (%ERRORLEVEL%)  
  
    GOTO CONTINUE  
  
    :AMD64  
    @echo Architecture type is AMD64  
  
    ECHO Windows Registry Editor Version 5.00 > x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs] >> x64.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14] >> x64.reg  
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio14\\"  >> x64.reg  
    ECHO "FirstTimeRun"="False"  >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14\en-US]  >> x64.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\en-US\\"  >> x64.reg  
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\VSWinExpress\14.0\help]  >> x64.reg  
    ECHO "UseOnlineHelp"=dword:00000000  >> x64.reg  
  
    regedit.exe /s x64.reg  
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x64 reg (%ERRORLEVEL%)  
  
    :CONTINUE  
    ```  
  
3.  Yardım içeriğinin üzerine yükleneceği yerel makinede bat dosyasını çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Komut satırı bağımsız değişkenleri için Yardım içeriği Yöneticisi](../ide/command-line-arguments-for-the-help-content-manager.md)   
 [Yardım İçerik Yöneticisi Geçersiz Kılmaları](../ide/help-content-manager-overrides.md)



