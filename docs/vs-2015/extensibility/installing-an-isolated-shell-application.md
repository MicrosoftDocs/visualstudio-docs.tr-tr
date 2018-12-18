---
title: Yalıtılmış Kabuk uygulaması yükleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 41
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1ecec7963b66c20ef08d1e5f3f0917a66f885aa0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796317"
---
# <a name="installing-an-isolated-shell-application"></a>Yalıtılmış Kabuk uygulaması yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir kabuk uygulaması yüklemek için aşağıdaki adımları gerçekleştirmeniz gerekir.  
  
- Çözümünüzü hazırlayın.  
  
- Uygulamanız için bir Windows Installer (MSI) paketi oluşturun.  
  
- Kurulum önyükleyici oluşturun.  
  
  Tüm örnek kodlar bu belgedeki geldiği [Shell dağıtım örnek](http://go.microsoft.com/fwlink/?LinkId=262245), MSDN Web sitesinde kod Galerisi'nden indirebilirsiniz. Örnek, bu adımların her biri gerçekleştirme sonuçlarını gösterir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda açıklanan işlemleri gerçekleştirmek için aşağıdaki araçları bilgisayarınızda yüklü olmalıdır.  
  
- Visual Studio SDK'sı  
  
- [Windows Installer XML araç takımı](http://go.microsoft.com/fwlink/?LinkId=82720) sürümü 3.6  
  
  Örnek ayrıca Microsoft Visualization ve tüm Kabukları gerektiren modelleme SDK gerektirir.  
  
## <a name="preparing-your-solution"></a>Çözümünüzü hazırlama  
 Varsayılan olarak, VSIX paketlerini Kabuk şablonları oluşturun, ancak bu davranış, öncelikli olarak hata ayıklama amacıyla tasarlanmıştır. Bir kabuk uygulaması dağıttığınızda, yükleme sırasında yeniden başlatılır ve kayıt defteri erişimi için izin vermek için MSI paketleri kullanmanız gerekir. Uygulamanız MSI dağıtım için hazırlamak için aşağıdaki adımları gerçekleştirin.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>MSI dağıtım için bir kabuk uygulaması hazırlamak için  
  
1.  Çözümünüzdeki her .vsixmanifest dosyasını düzenleyin.  
  
     İçinde `Identifier` öğe, Ekle bir `InstalledByMSI` öğesi ve bir `SystemComponent` öğesini ve ardından değerlerine ayarlayın `true`.  
  
     Bu öğeleri kullanarak kaldırmasını bileşenlerinizi ve kullanıcı yüklemeye çalıştığınız VSIX yükleyicisi önlemek **Uzantılar ve güncelleştirmeler** iletişim kutusu.  
  
2.  Bir VSIX bildirimi içeren her proje için içinden, MSI yükleyecek konumuna içerik çıkarmak için derleme görevleri düzenleyin. Oluşturma çıktısında VSIX bildirimi içerir, ancak bir .vsix dosyasını oluşturmayın.  
  
## <a name="creating-an-msi-for-your-shell"></a>Bir MSI Kabuğunuzu oluşturma  
 MSI paketinizi oluşturmak için kullanmanızı öneririz [Windows Installer XML araç takımı](http://go.microsoft.com/fwlink/?LinkId=82720) standart bir kurulum projesi çok esneklik sağlar.  
  
 Product.wxs dosyanızda algılama blokları ve Kabuk bileşenleri düzenini ayarlayın.  
  
 Ardından, kayıt defteri girdilerini, çözümünüz için .reg dosyasını hem de ApplicationRegistry.wxs oluşturun.  
  
### <a name="detection-blocks"></a>Algılama blokları  
 Algılama blok oluşan bir `Property` algılamak için bir önkoşul belirten öğe ve bir `Condition` belirten bir ileti önkoşul bilgisayarda mevcut değilse döndürülecek öğesi. Örneğin, kabuk uygulamanızı Microsoft Visual Studio Shell yeniden dağıtılabilir gerektirir ve algılama blok aşağıdaki biçimlendirme benzer.  
  
```xml  
<Property Id="ISOSHELLSFX">  
  <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
<Property Id="INTSHELLSFX">  
  <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
  
<Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again.">  
  <![CDATA[Installed OR ISOSHELLSFX]]>  
</Condition>  
<Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again.">  
  <![CDATA[Installed OR INTSHELLSFX]]>  
</Condition>  
  
```  
  
### <a name="layout-of-shell-components"></a>Kabuk bileşenlerinin yerleşimi  
 Hedef dizin yapısını ve yüklenecek bileşenleri belirlemek için öğeleri eklemeniz gerekir.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>Kabuk bileşenleri düzenini ayarlamak için  
  
1.  Bir hiyerarşisini oluşturmak `Directory` tüm hedef bilgisayarda dosya sistemi aşağıdaki örnekte gösterildiği gibi oluşturmak için dizinleri temsil edecek öğeleri.  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir">  
      <Directory Id="ProgramFilesFolder">  
        <Directory Id="CompanyDirectory" Name="$(var.CompanyName)">  
          <Directory Id="INSTALLDIR" Name="$(var.FullProductName)">  
            <Directory Id="ExtensionsFolder" Name="Extensions" />  
            <Directory Id="Folder1033" Name="1033" />  
          </Directory>  
        </Directory>  
      </Directory>  
      <Directory Id="ProgramMenuFolder">  
        <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/>  
      </Directory>  
    </Directory>  
    ```  
  
     Bu dizinler tarafından başvurulan `Id` yüklenmesi gereken dosyaları belirtildiği zaman.  
  
2.  Kabuk ve Kabuk uygulamanızı, aşağıdaki örnekte gösterildiği gibi gerekli bileşenleri tanımlayın.  
  
    > [!NOTE]
    >  Bazı öğeleri .wxs tanımlarını bakabilirsiniz.  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1">  
      <ComponentGroupRef Id="ApplicationGroup" />  
      <ComponentGroupRef Id="HelpAboutPackage" />  
      <ComponentRef Id="GeneralProfile" />  
      <ComponentGroupRef Id="EditorAdornment"/>        
      <ComponentGroupRef Id="SlideShowDesignerGroup"/>  
  
      <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. -->  
      <ComponentGroupRef Id="Product.Generated" />  
    </Feature>  
    ```  
  
    1.  `ComponentRef` Öğesi geçerli bileşenin gerektirdiği dosyaları tanımlayan başka bir .wxs dosyasına başvuruyor. Örneğin, GeneralProfile aşağıdaki tanımını HelpAbout.wxs vardır.  
  
        ```xml  
        <Fragment Id="FragmentProfiles">  
          <DirectoryRef Id="INSTALLDIR">  
            <Directory Id="ProfilesFolder" Name="Profiles">  
              <Component Id='GeneralProfile' Guid='*'>  
                <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' />  
              </Component>  
            </Directory>  
          </DirectoryRef>  
        </Fragment>  
        ```  
  
         `DirectoryRef` Öğesi, bu dosyalar, kullanıcının bilgisayarında nereye belirtir. `Directory` Öğesi belirtir, bir alt dizine ve her yüklenecek `File` öğesi oluşturulan veya MSI dosya oluşturulduğunda dosyanın nerede bulunabileceğini tanımlar ve çözümün bir parçası mevcut bir dosyayı temsil eder.  
  
    2.  `ComponentGroupRef` Öğesi diğer bileşenleri (veya bileşenler ve bileşen grupları) grubuna başvuruyor. Örneğin, `ComponentGroupRef` altında ApplicationGroup içinde Application.wxs şu şekilde tanımlanır.  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup">  
          <ComponentGroupRef Id="DebuggerProxy" />  
          <ComponentRef Id="MasterPkgDef" />  
          <ComponentRef Id="SplashResource" />  
          <ComponentRef Id="IconResource" />  
          <ComponentRef Id="WinPrfResource" />  
          <ComponentRef Id="AppExe" />  
          <ComponentRef Id="AppConfig" />  
          <ComponentRef Id="AppPkgDef" />  
          <ComponentRef Id="AppPkgDefUndef" />  
          <ComponentRef Id="$(var.ShortProductName)UI1033" />  
          <ComponentRef Id="ApplicationShortcut"/>  
          <ComponentRef Id="ApplicationRegistry"/>  
        </ComponentGroup>  
        ```  
  
    > [!NOTE]
    >  Shell (yalıtılmış) uygulamalar için bağımlılıkların gereklidir: DebuggerProxy, MasterPkgDef, kaynakları (özellikle .winprf dosyası), uygulama ve PkgDefs.  
  
### <a name="registry-entries"></a>Kayıt defteri girdileri  
 Shell (yalıtılmış) proje şablonu içeren bir *ProjectName*.reg dosyasını yüklemede birleştirmek kayıt defteri anahtarları için. Bu kayıt defteri girdileri MSI yükleme hem de temizleme amaçlar için bir parçası olmalıdır. Ayrıca ApplicationRegistry.wxs eşleşen kayıt defteri blokları oluşturmanız gerekir.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Kayıt defteri girdileri MSI uygulamasına tümleştirmek için  
  
1.  İçinde **Kabuğu özelleştirme** açık klasör *ProjectName*. kayıt  
  
2.  Tüm örneklerini $RootFolder$ belirteç hedef yükleme dizini yolu ile değiştirin.  
  
3.  Uygulamanızın gerektirdiği herhangi bir kayıt defteri girdilerini ekleyin.  
  
4.  ApplicationRegistry.wxs açın.  
  
5.  Her kayıt defteri girişi için *ProjectName*.reg, aşağıdaki örneklerde gösterildiği gibi karşılık gelen bir kayıt bloğunu ekleyin.  
  
    |*ProjectName*.reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @= "PhotoStudio DTE nesnesi"|\<RegistryKey Kimliği = 'DteClsidRegKey' kök = 'HKCR' anahtar =' $(var. DteClsidRegKey)' eylemi 'createAndRemoveOnUninstall' = ><br /><br /> \<REGISTRYVALUE türü = 'string' Name =' @' değer =' $(var. ShortProductName) DTE nesnesi ' / ><br /><br /> \</ RegistryKey >|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6} \LocalServer32]<br /><br /> @= "$RootFolder$\PhotoStudio.exe"|\<RegistryKey Kimliği = 'DteLocSrv32RegKey' kök = 'HKCR' anahtar =' $(var. DteClsidRegKey) \LocalServer32' eylemi 'createAndRemoveOnUninstall' = ><br /><br /> \<REGISTRYVALUE türü = 'string' Name =' @' değer ='[INSTALLDIR] $(var. ShortProductName) .exe ' / ><br /><br /> \</ RegistryKey >|  
  
     Bu örnekte, en üst satır kayıt defteri anahtarında Var.DteClsidRegKey çözümler. Var.ShortProductName çözümler için `PhotoStudio`.  
  
## <a name="creating-a-setup-bootstrapper"></a>Kurulum bir önyükleyici oluşturma  
 Yalnızca önce tüm önkoşulların yüklü değilse, tamamlanan MSI yükler. Son kullanıcı deneyimini kolaylaştırmak için toplar ve uygulamanızı yüklemeden önce tüm önkoşulların yükleyen bir Kurulum programı oluşturun. Yükleme başarılı olmak için bu eylemleri gerçekleştirin:  
  
-   Yükleme Yöneticisi tarafından uygular.  
  
-   Visual Studio Kabuğu (yalıtılmış) yüklü olup olmadığını belirler.  
  
-   Biri veya ikisi de Kabuk yükleyicileri sırayla çalıştırın.  
  
-   Yeniden başlatma istekleri işler.  
  
-   Msi dosyasını çalıştırın.  
  
### <a name="enforcing-installation-by-administrator"></a>Yükleme Yöneticisi tarafından zorlanması  
 Bu yordam, \Program dosyaları gibi gerekli dizinlere erişim için Kurulum programı etkinleştirmek için gerekli\\.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Yükleme Yöneticisi tarafından zorunlu kılmak için  
  
1.  Kurulum projesi için kısayol menüsünü açın ve ardından **özellikleri**.  
  
2.  Altında **yapılandırma özellikleri/bağlayıcı/bildirim dosyası**ayarlayın **UAC yürütme düzeyi** için **requireAdministrator'a**.  
  
     Bu özellik, yönetici olarak katıştırılmış bildirim dosyasına çalıştırılması için programın gerektirdiği öznitelik koyar.  
  
### <a name="detecting-shell-installations"></a>Kabuk yüklemelerini algılamaya  
 Visual Studio Kabuğu (yalıtılmış) yüklü olup olmadığını belirlemek için önce bunu HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install kayıt defteri değerini denetleyerek yüklü olup olmadığını belirleyin.  
  
> [!NOTE]
>  Bu değerleri de Product.wxs Kabuk algılama bloğunda tarafından okunur.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder burada Visual Studio Kabuğu yüklendi ve dosya için kontrol edebilirsiniz konumunu belirtir.  
  
 Bir kabuk yüklemesini algılamak nasıl bir örnek için bkz `GetProductDirFromReg` Shell dağıtım örneğinde Utilities.cpp işlevi.  
  
 Bilgisayarda birini veya her ikisini paketinizi gerektiren Visual Studio Kabukları yüklü değil ise, yüklenecek bileşenlerin listesine eklemeniz gerekir. Bir örnek için bkz `ComponentsPage::OnInitDialog` Shell dağıtım örneğinde ComponentsPage.cpp işlevi.  
  
### <a name="running-the-shell-installers"></a>Kabuk yükleyicileri çalıştırma  
 Kabuk yükleyicileri çalıştırmak için Visual Studio Shell yeniden dağıtılabilir dosyaları, doğru komut satırı bağımsız değişkenleri kullanarak çağırın. Komut satırı bağımsız değişkenlerini en az kullanmalısınız **/q/norestart** ve sonraki ne yapılmalı belirlemek dönüş kodunu izleyin. Aşağıdaki örnek Shell (yalıtılmış yeniden dağıtılabilir'i) çalıştırır.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Shell dil paketi yükleyicileri çalıştırma  
 Bunun yerine Kabuk veya kabuklar yüklü ve yalnızca bir dil paketi fark ederseniz, aşağıdaki örnekte gösterildiği gibi dil paketlerini yükleyebilirsiniz.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Dönüş değerleri şifresini çözme  
 Bazı işletim sistemlerinde, Visual Studio Kabuğu (yalıtılmış) yükleme yeniden başlatma gerekir. Bu durum, yapılan çağrının dönüş kodu tarafından belirlenebilir `ExecCmd`.  
  
|Dönüş Değeri|Açıklama|  
|------------------|-----------------|  
|ERROR_SUCCESS|Yükleme tamamlandı. Uygulamanızı şimdi yükleyebilirsiniz.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Yükleme tamamlandı. Bilgisayar yeniden başlatıldıktan sonra uygulamanızın yükleyebilirsiniz.|  
|3015|Yükleme işlemi devam ediyor. Yüklemeye devam etmek için bilgisayarın yeniden başlatılması gerekir.|  
  
### <a name="handling-restarts"></a>Yeniden işleme  
 Çalıştırdığınızda Kabuk yükleyiciyi kullanarak **/norestart** bağımsız değişkeni, belirttiğiniz mıydı bilgisayarı yeniden başlatın veya bilgisayarın yeniden başlatılması için sorun olduğunu. Ancak, bir yeniden başlatma gerekebilir ve bilgisayar yeniden başlatıldıktan sonra yükleyici ettiğinden emin olmanız gerekir.  
  
 Doğru bir şekilde yeniden işlemek için devam etmek için ayarlama ve sürdürme işlemi doğru işlenmesi, yalnızca bir Kurulum programı olduğundan emin olun.  
  
 ERROR_SUCCESS_REBOOT_REQUIRED ya da 3015 döndürülür, kodunuzu bir yükleme devam etmeden önce bilgisayarı yeniden başlatmanız gerekir.  
  
 Yeniden işlemek için bu eylemleri gerçekleştirin:  
  
-   Windows başladığında yüklemeye devam etmek için kayıt defteri ayarlayın.  
  
-   Önyükleyici çift yeniden gerçekleştirin.  
  
-   Kabuk yükleyici ResumeData anahtarını silin.  
  
-   Windows yeniden başlatın.  
  
-   MSI başlangıç yolu sıfırlayın.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Windows başladığında kurulum devam etmek için kayıt defteri ayarı  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ kayıt defteri anahtarı yönetim izinlerine sahip sistem başlangında yürütür ve ardından silinir. HKEY_CURRENT_USER benzer bir anahtar içeriyor, ancak normal bir kullanıcı olarak çalışır ve yüklemelerinde uygun değildir. Yükleme yükleyicinizi çağıran RunOnce anahtar bir dize değeri koyarak sürdürebilirsiniz. Ancak, kullanarak yükleyici çağırmanızı öneririz bir **/yeniden** veya sürdürme çalışmaya başlamak yerine uygulamaya bildirmek için benzer bir parametre. Birden çok kez yeniden gerektirebilecek yüklemelerini kullanışlıdır yükleme işleminde nerede göstermek için parametreleri de ekleyebilirsiniz.  
  
 Aşağıdaki örnek, bir yükleme sürdürülüyor için bir RunOnce kayıt defteri anahtarı değerini gösterir.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Önyükleyici çift yeniden yükleme  
 Kurulum doğrudan RunOnce kullanılırsa, Masaüstü tamamen yüklenmesini mümkün olmayacaktır. Tam kullanıcı arabirimi kullanılabilir yapmak için başka bir kurulum yürütülmesini oluşturup RunOnce örneği son gerekir.  
  
 Kurulum programı doğru izinleri alır ve aşağıdaki örnekte gösterildiği gibi yeniden başlatmadan önce durduğu öğrenmek için yeterli bilgi vermelidir yeniden yürütmeniz gerekir.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Kabuk yükleyici ResumeData anahtarı siliniyor  
 Kabuk yükleyici kurulumu yeniden başlatıldıktan sonra devam etmek için veri HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData kayıt defteri anahtarı ayarlar. Kabuk yükleyici uygulamanızın sürdürme olduğundan, aşağıdaki örnekte gösterildiği gibi bu kayıt defteri anahtarını silin.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Windows yeniden başlatma  
 Gerekli kayıt defteri anahtarını ayarladıktan sonra Windows yeniden başlatabilirsiniz. Aşağıdaki örnek, farklı Windows işletim sistemleri için yeniden başlatma komutları çağırır.  
  
```  
OSVERSIONINFO ov;  
HANDLE htoken ;  
//Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown.  
if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken))  
{  
    LUID luid ;  
    LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ;  
    TOKEN_PRIVILEGES    privs ;  
    privs.Privileges[0].Luid = luid ;  
    privs.PrivilegeCount = 1 ;  
    privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ;  
    AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ;  
}   
  
//Use InitiateSystemShutdownEx to avoid unexpected restart message box  
try  
{              
    if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) ))  
    {  
        bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG);  
    }  
    else  
    {  
#pragma prefast(suppress:380,"ignore warning about legacy api")  
        bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE);  
    }  
}  
catch(...)  
{  
    //advapi32.dll call not available! Will not restart!  
}  
  
```  
  
### <a name="resetting-the-start-path-of-msi"></a>MSI başlangıç yolunu sıfırlanıyor  
 Yeniden başlatma önce kurulum programınıza konumunu geçerli dizin olduğu ancak yeniden başlatıldıktan sonra konumu system32 dizininde haline gelir. Kurulum programınıza aşağıdaki örnekte gösterildiği gibi her MSI çağrıdan önce geçerli dizin sıfırlamanız gerekir.  
  
```  
CString GetSetupPath()  
{  
    TCHAR file[MAX_PATH];  
    GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR));  
    CString path(file);  
    int fpos = path.ReverseFind('\\');  
    if (fpos != -1)  
    {  
        path = path.Left(fpos + 1);  
    }  
  
    return path;  
}  
  
```  
  
### <a name="running-the-application-msi"></a>MSI uygulaması çalıştırma  
 Visual Studio Shell yükleyici ERROR_SUCCESS döndükten sonra uygulamanız için MSI çalıştırabilirsiniz. Kullanıcı arabirimi, Kurulum programınız sağladığından, MSI sessiz modda başlatın (**/q**) ile günlüğe kaydetme (**/L**), aşağıdaki örnekte gösterildiği gibi.  
  
```cpp#  
TCHAR temp[MAX_PATH];  
GetTempPath(MAX_PATH, temp);  
  
CString boutiqueInstallCmd, msi, log;  
CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress"));  
CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi"));  
log.Format(_T("\"%s%s.log\""), temp, name);  
msi.Format(_T("\"%s%s\""), GetSetupPath(), name);  
boutiqueInstallCmd.Format(cmdLine, msi, log);  
  
//TODO: You can use MSI API to gather and present install progress feedback from your MSI.  
dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Temel Yalıtılmış Kabuk Uygulaması Oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)

