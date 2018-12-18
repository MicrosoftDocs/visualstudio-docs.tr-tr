---
title: 'İzlenecek yol: ortam derleme birden çok bilgisayarda oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, building on multiple computers
- build environment, MSBuild
ms.assetid: ae5391b1-3eec-42f5-beb3-f28630615a9e
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1422a126f88e72d0eca662aaa5348a6af500b8bb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820700"
---
# <a name="walkthrough-creating-a-multiple-computer-build-environment"></a>İzlenecek yol: Birden Çok Bilgisayarda Derleme Ortamı Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio bir ana bilgisayara yükleyerek, kuruluşunuzda bir yapı ortamı oluşturabilirsiniz ve böylece katılabilmesi çeşitli dosya ve ayarları başka bir bilgisayara ardından kopyalama oluşturur. Visual Studio'yu diğer bilgisayara yüklemeniz gerekmez.  
  
 Bu belge, yazılımın harici olarak dağıtılması veya üçüncü taraflara yapı ortamları sağlamak için hakları confer değil.  
  
||  
|-|  
|Sorumluluk reddi<br /><br /> Bu belge bir "olarak-olan" olarak. Özetlenen adımları Test ettiğimiz olsa da her yapılandırma tamamen test etmek yükümlü değiliz. Belgeyi öğrenilen herhangi ek bilgilerle güncel tutmaya dener. Bilgi ve URL ve diğer Internet Web sitesi referansları da dahil olmak üzere bu belgede, bildirilmeksizin değiştirilebilir. Microsoft hiçbir açık veya zımni bilgilerle garantide bulunmaz. Bunu kullanarak riski size aittir.<br /><br /> Bu belge ile herhangi bir Microsoft ürünü üzerinde hiçbir fikri mülkiyet hakkı sağlamaz. Kopyalayabilir ve dahili olarak, bu belgeyi kullanmak amacıyla başvuru.<br /><br /> Herhangi bir öneri, yorum veya bu belgeyle ilgili geribildirimde ("Geribildirim") Microsoft vermek zorunda değilsiniz. Ancak, gönüllü olarak sağlayacağınız her türlü geribildirim, Microsoft Products ve ilgili belirtimlerde veya hangi sırayla bağlı kendi ürünlerini geliştirmek için diğer üçüncü taraflarca dayanan diğer belgeleri (topluca, "Microsoft Offerings") kullanılabilir. Buna göre bu belgenin veya Microsoft uygulandıkları Offerings herhangi bir sürümü üzerinde Microsoft Feedback bildirimde bulunursanız, kabul etmiş olursunuz: (a) Microsoft serbestçe kullanın, yeniden oluşturma, lisans, dağıtmak ve aksi takdirde herhangi bir Microsoft geri bildirim tanımış olursunuz Teklif; (b), ayrıca üçüncü taraflara, ücretsiz, yalnızca diğer ürünleri kullanmayı veya kendi geri bildirim bir araya getiren herhangi belirli bir Microsoft Product ile arabirim parçaları etkinleştirmek için gereken bu patent hakkı vermek; ve (c) aldığınız düşünmenize neden olan herhangi bir Geri bildiriminiz (i) herhangi bir patent, telif hakkını veya diğer fikri mülkiyet veya üçüncü taraf sağ tabi olan Microsoft vermeyiz. veya (ii) konu Microsoft Offering geribildirimler veya bu geri bildirimlerden veya diğer Microsoft fikri mülkiyet için lisanslı veya aksi türetilmiş Lisans Koşulları'nı herhangi bir üçüncü tarafla paylaşılmaz.|  
  
 Bu izlenecek yol MSBuild komut satırında yürüterek ve Team Foundation Yapısı kullanılarak aşağıdaki işletim sistemlerine karşı doğrulandı.  
  
- Windows 8 (x86 ve x64)  
  
- Windows 7 Ultimate  
  
- Windows Server 2008 R2 Standard  
  
  Bu izlenecek yolda adımları tamamladıktan sonra bu tür uygulamalar oluşturmak için çoklu bilgisayar ortamı kullanabilirsiniz:  
  
- Windows 8 SDK kullanan C++ Masaüstü uygulamaları  
  
- .NET Framework 4.5 hedefleyen Visual Basic veya C# Masaüstü uygulamaları  
  
  Bu tür uygulamalar oluşturmak için çoklu bilgisayar ortamı kullanılamaz:  
  
- [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamaları. Oluşturulacak [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamaları, yapı bilgisayarında Visual Studio yüklemeniz gerekir.  
  
- .NET Framework 4 veya önceki sürümlerini hedefleyen Masaüstü uygulamaları. Bu tür uygulamalar oluşturmak için ya da Visual Studio veya .NET başvuru bütünleştirilmiş kodları ve Araçları (Windows 7.1 SDK'sı) yapı bilgisayarında yüklemeniz gerekir.  
  
  Bu izlenecek yol, şu bölümlere ayrılmıştır:  
  
- [Bilgisayarlara yazılım yükleme](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingSoftware)  
  
- [Dosyaları ana bilgisayardan yapı bilgisayarına kopyalanıyor](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles)  
  
- [Kayıt defteri ayarları oluşturma](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingRegistry)  
  
- [Yapı bilgisayarında ortam değişkenlerini ayarlama](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#SettingEnvVariables)  
  
- [İçin Genel Derleme Önbelleği (GAC) yapı bilgisayarında MSBuild derlemeleri yükleme](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC)  
  
- [Proje oluşturma](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#BuildingProjects)  
  
- [Böylece kaynak denetimine iade derleme ortamı oluşturma](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingForSourceControl)  
  
## <a name="prerequisites"></a>Önkoşullar  
  
-   Visual Studio Ultimate, Visual Studio Premium veya Visual Studio Professional lisanslı bir kopyası  
  
-   Karşıdan yükleyebileceğiniz .NET Framework 4.5.1 kopyasını [Visual Studio](http://www.microsoft.com/visualstudio/eng/downloads#d-additional-software) Web sitesi.  
  
##  <a name="InstallingSoftware"></a> Bilgisayarlara yazılım yükleme  
 İlk olarak, ana bilgisayarı ayarlayın ve ardından yapı bilgisayarını ayarlayın.  
  
 Visual Studio ana bilgisayara yükleyerek, dosya ve daha sonra yapı bilgisayarına kopyalayacak ayarları oluşturun. Visual Studio yüklediğiniz bilgisayar, ancak Yapı bilgisayarının mimarisinin bir x86 veya x x64 ana bilgisayarın mimarisiyle eşleşmelidir.  
  
#### <a name="to-install-software-on-the-computers"></a>Yazılımını bilgisayarlara yüklemek için  
  
1.  Ana bilgisayarda Visual Studio'yu yükleyin.  
  
2.  Yapı bilgisayarında .NET Framework 4. 5'i yükleyin. Yüklü olduğunu doğrulamak için kayıt defteri hkey_local_machıne\software\microsoft\net Framework anahtar emin olun Setup\NDP\v4\Full@Version "4.5" ile başlar.  
  
##  <a name="CopyingFiles"></a> Dosyaları ana bilgisayardan yapı bilgisayarına kopyalanıyor  
 Bu bölüm, belirli dosyaları, derleyicileri, derleme araçları, MSBuild varlıklarını ve yapı bilgisayarı ana bilgisayar kayıt defteri ayarlarını kopyalamayı kapsar. Bu yönergeler, Visual Studio ana bilgisayarda varsayılan konuma yüklediğinizi varsayar; başka bir konuma yüklediyseniz adımları da buna göre ayarlayın.  
  
- X x86 bilgisayar, varsayılan konumu: C:\Program Files\Microsoft Visual Studio 11. 0\ dizinidir  
  
- X x64 bilgisayar, varsayılan konumu: C:\Program Files (x86) \Microsoft Visual Studio 11. 0\ dizinidir  
  
  Program dosyaları klasörünün adı yüklü işletim sisteminde olduğuna dikkat edin. X x86 bilgisayar adı olan \Program dosyaları\\; x x64 bilgisayar adı olan \Program dosyaları (x86)\\. Sistem Mimarisi ne olursa olsun, bu İnceleme % ProgramFiles % olarak Program dosyaları klasörüne başvurur.  
  
> [!NOTE]
>  Yapı bilgisayarında, tüm ilgili dosyalar aynı sürücüde olmalıdır; Ancak, söz konusu sürücünün sürücü harfi, Visual Studio ana bilgisayarında yüklü olduğu sürücünün sürücü harfi farklı olabilir. Her iki durumda da, bu belgenin sonraki bölümlerinde açıklandığı şekilde kayıt defteri girdileri oluşturduğunuzda dosyalarının konumunu dikkate alması gerekir.  
  
#### <a name="to-copy-the-windows-sdk-files-to-the-build-computer"></a>Windows SDK dosyalarını yapı bilgisayarına kopyalamak için  
  
1. Yalnızca Windows SDK'sı için Windows 8 yüklü varsa, bu klasörleri tekrar tekrar ana bilgisayardan yapı bilgisayarına kopyalayın:  
  
   - %ProgramFiles%\Windows Kits\8.0\bin\  
  
   - %ProgramFiles%\Windows Kits\8.0\Catalogs\  
  
   - %ProgramFiles%\Windows Kits\8.0\DesignTime\  
  
   - %ProgramFiles%\Windows Kits\8.0\include\  
  
   - %ProgramFiles%\Windows Kits\8.0\Lib\  
  
   - %ProgramFiles%\Windows Kits\8.0\Redist\  
  
   - %ProgramFiles%\Windows Kits\8.0\References\  
  
     Ayrıca bunlar başka Windows 8 setleriniz varsa...  
  
   - Microsoft Windows değerlendirme ve Dağıtım Seti  
  
   - Microsoft Windows Sürücü Seti  
  
   - Microsoft Windows Donanım onay Seti  
  
     .. .önceki dosyaları yüklemiş olabilirler önceki adımda listelenen %ProgramFiles%\Windows Kits\8.0\ klasörler halinde ve lisans koşulları bu dosyalara ilişkin yapı sunucu haklarına izin vermeyebilir. Dosyaların derleme bilgisayarınıza kopyalanıp kopyalanmadığını doğrulamak yüklü her Windows Kiti için lisans koşullarını kontrol edin. Lisans koşulları yapı sunucusu haklarına izin verme, dosyaları yapı bilgisayarından kaldırın.  
  
2. Aşağıdaki klasörleri yinelemeli olarak ana bilgisayardan yapı bilgisayarına kopyalayın:  
  
   -   %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\ içinde  
  
   -   %ProgramFiles%\Common Files\Merge modules\ konumuna  
  
   -   %ProgramFiles%\Microsoft visual Studio 11.0\VC\  
  
   -   %ProgramFiles%\Microsoft visual Studio 11.0\Common7\Tools\ProjectComponents\  
  
   -   %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\V110\  
  
   -   %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\. NETCore\v4.5\  
  
   -   %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\. NETFramework\v4.5\  
  
3. Bu dosyaları ana bilgisayardan yapı bilgisayarına kopyalayın:  
  
   -   %ProgramFiles%\Microsoft visual Studio 11.0\Common7\IDE\msobj110.dll  
  
   -   %ProgramFiles%\Microsoft visual Studio 11.0\Common7\IDE\mspdb110.dll  
  
   -   %ProgramFiles%\Microsoft visual Studio 11.0\Common7\IDE\mspdbcore.dll  
  
   -   %ProgramFiles%\Microsoft visual Studio 11.0\Common7\IDE\mspdbsrv.exe  
  
   -   %ProgramFiles%\Microsoft visual Studio 11.0\Common7\IDE\msvcdis110.dll  
  
   -   %ProgramFiles%\Microsoft visual Studio 11.0\Common7\Tools\makehm.exe  
  
   -   %ProgramFiles%\Microsoft visual Studio 11.0\Common7\Tools\VCVarsQueryRegistry.bat  
  
   -   %ProgramFiles%\Microsoft visual Studio 11.0\Common7\Tools\vsvars32.bat  
  
4. Yapı bilgisayarında yapı çıkışları çalıştırırsanız aşağıdaki Visual C++ çalışma zamanı kitaplıkları gereklidir; Örneğin, otomatikleştirilmiş test işleminin parçası olarak. Dosyalar genellikle %ProgramFiles%\Microsoft Visual Studio 11.0\VC\redist\x86\ veya sistem mimarisine bağlı olarak %ProgramFiles%\Microsoft Visual Studio 11.0\VC\redist\x64\ klasörü altındaki alt bulunur. X86 sistemleri, kopyalama x86 ikili dosyalarını \Windows\System32\ klasörüne. X64 sistemleri, kopyalama x86 ikili dosyalarını Windows\SysWOW64\ klasörüne ve x64 ikili dosyalarını da Windows\System32\ klasörüne.  
  
   -   \Microsoft.VC110.ATL\atl110.dll  
  
   -   \Microsoft.VC110.CRT\msvcp110.dll  
  
   -   \Microsoft.VC110.CRT\msvcr110.dll  
  
   -   \Microsoft.VC110.CXXAMP\vcamp110.dll  
  
   -   \Microsoft.VC110.MFC\mfc110.dll  
  
   -   \Microsoft.VC110.MFC\mfc110u.dll  
  
   -   \Microsoft.VC110.MFC\mfcm110.dll  
  
   -   \Microsoft.VC110.MFC\mfcm110u.dll  
  
   -   \Microsoft.VC110.MFCLOC\mfc110chs.dll  
  
   -   \Microsoft.VC110.MFCLOC\mfc110cht.dll  
  
   -   \Microsoft.VC110.MFCLOC\mfc110deu.dll  
  
   -   \Microsoft.VC110.MFCLOC\mfc110enu.dll  
  
   -   \Microsoft.VC110.MFCLOC\mfc110esn.dll  
  
   -   \Microsoft.VC110.MFCLOC\mfc110fra.dll  
  
   -   \Microsoft.VC110.MFCLOC\mfc110ita.dll  
  
   -   \Microsoft.VC110.MFCLOC\mfc110jpn.dll  
  
   -   \Microsoft.VC110.MFCLOC\mfc110kor.dll  
  
   -   \Microsoft.VC110.MFCLOC\mfc110rus.dll  
  
   -   \Microsoft.VC110.OPENMP\vcomp110.dll  
  
5. Açıklandığı gibi yalnızca aşağıdaki dosyaları \Debug_NonRedist\x86\ veya \Debug_NonRedist\x64\ klasöründen yapı bilgisayarına kopyalayın [bir hata ayıklama yürütülebilir bir Test makinesi için çalıştırın hazırlama](http://msdn.microsoft.com/library/f0400989-cc2e-4dce-9788-6bdbe91c6f5a). Başka hiçbir dosya kopyalanamaz.  
  
   -   \Microsoft.VC110.DebugCRT\msvcp110d.dll  
  
   -   \Microsoft.VC110.DebugCRT\msvcr110d.dll  
  
   -   \Microsoft.VC110.DebugCXXAMP\vcamp110d.dll  
  
   -   \Microsoft.VC110.DebugMFC\mfc110d.dll  
  
   -   \Microsoft.VC110.DebugMFC\mfc110ud.dll  
  
   -   \Microsoft.VC110.DebugMFC\mfcm110d.dll  
  
   -   \Microsoft.VC110.DebugMFC\mfcm110ud.dll  
  
   -   \Microsoft.VC110.DebugOpenMP\vcomp110d.dll  
  
##  <a name="CreatingRegistry"></a> Kayıt defteri ayarları oluşturma  
 MSBuild ayarlarını yapılandırmak için kayıt defteri girdileri oluşturmanız gerekir.  
  
#### <a name="to-create-registry-settings"></a>Kayıt defteri ayarları oluşturmak için  
  
1. Kayıt defteri girişleri için ana klasörü belirleyin. Tüm kayıt defteri girdilerini aynı üst anahtar altında oluşturulur. X x86, üst anahtar bilgisayardır HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. X x64 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft bilgisayarında üst anahtar olduğunu\\. Sistem Mimarisi ne olursa olsun, bu İnceleme % RegistryRoot % olarak üst anahtara başvurur.  
  
   > [!NOTE]
   >  Ana bilgisayarınızın mimarisi yapı farklıysa, her bilgisayarda uygun üst anahtarı kullandığınızdan emin olun. Bu dışarı aktarma işlemini otomatikleştiriyorsanız özellikle önem taşır.  
   >   
   >  Ayrıca, yapı bilgisayarında ana bilgisayarda kullandığınız olandan farklı bir sürücü harfi kullanıyorsanız, eşleşmesi için kayıt defteri girdilerinin değerlerini değiştirdiğinizden emin olun.  
  
2. Yapı bilgisayarında aşağıdaki kayıt defteri girdilerini oluşturun. Tüm bu girdiler dizelerdir (tür == "REG_SZ" kayıt defterinde). Bu girişlerin değerlerini aynı ana bilgisayarda benzer girişlerle değerleri olarak ayarlayın.  
  
   - % RegistryRoot %\\. NETFramework\v4.0.30319\AssemblyFoldersEx\VCMSBuild Public Assemblies@(varsayılan)  
  
   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0@InstallationFolder  
  
   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A@InstallationFolder  
  
   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools@InstallationFolder  
  
   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x86@InstallationFolder  
  
   - % RegistryRoot %\VisualStudio\11.0@Source dizinleri  
  
   - %RegistryRoot%\VisualStudio\11.0\Setup\VC@ProductDir  
  
   - %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir32  
  
   - %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir64  
  
   - %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer32  
  
   - %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer64  
  
   - %RegistryRoot%\VisualStudio\SxS\VC7@11.0  
  
   - %RegistryRoot%\VisualStudio\SxS\VS7@11.0  
  
   - %RegistryRoot%\Windows Kits\Installed Roots@KitsRoot  
  
   - %RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath  
  
   - %RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10  
  
   - %RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11  
  
     Yapı bilgisayarı üzerinde bir x64, ayrıca şu kayıt defteri girişi oluşturun ve nasıl ayarlanacağını belirlemek için konak bilgisayara başvurun.  
  
   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x64@InstallationFolder  
  
     Yapı bilgisayarınız x64 ise ve MSBuild 64 bit sürümünü kullanmak istiyorsanız veya x x64 üzerinde Team Foundation Server yapı Hizmeti'ni kullanıyorsanız, bilgisayarın yerel 64 bit kayıt defterinde aşağıdaki kayıt defteri girdilerini oluşturmalısınız. Bu girişlerin nasıl ayarlanacağını belirlemek için konak bilgisayara başvurun.  
  
   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Setup\VS@ProductDir  
  
   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath  
  
   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10  
  
   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11  
  
##  <a name="SettingEnvVariables"></a> Yapı bilgisayarında ortam değişkenlerini ayarlama  
 Yapı bilgisayarında MSBuild kullanmak için PATH ortam değişkenleri ayarlamanız gerekir. Vcvarsall.bat'ı, değişkenlerini ayarlamak için kullanabilirsiniz veya bunları el ile yapılandırabilirsiniz.  
  
#### <a name="to-use-vcvarsallbat-to-set-environment-variables"></a>Vcvarsall.bat'ı ortam değişkenlerini ayarlamak için kullanılacak  
  
-   Yapı bilgisayarında bir komut istemi penceresi açın ve % Program Files%\Microsoft Visual Studio 11.0\VC\vcvarsall.bat çalıştırın. Kullanmak istediğiniz araç kümesini belirtmek için bir komut satırı bağımsız değişkeni kullanabilirsiniz — x86, yerel x64 veya x64 çapraz derleyici. Bir komut satırı bağımsız değişkeni, araç kümesi kullanılır x86 belirtmezseniz.  
  
     Bu tablo, vcvarsall.bat için desteklenen bağımsız değişkenleri açıklar:  
  
    |Vcvarsall.bat bağımsız değişkeni|Derleyici|Bilgisayar mimarisi oluşturun|Çıkış mimarisini oluşturun|  
    |----------------------------|--------------|---------------------------------|-------------------------------|  
    |x86 (varsayılan)|32 bit yerel|x86, x64|x86|  
    |x86_amd64|platformlar arası x64|x86, x64|X64|  
    |amd64|x64 yerel|X64|X64|  
  
     Vcvarsall.bat sorunsuz çalışırsa — diğer bir deyişle, hiçbir hata iletisi görüntülenir; sonraki adıma atla ve devam [yükleme MSBuild derlemeleri için Genel Derleme Önbelleği (GAC) yapı bilgisayarında](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC) bu belgenin bölüm .  
  
#### <a name="to-manually-set-environment-variables"></a>Ortam değişkenlerini el ile ayarlamak için  
  
1. Komut satırı ortamını el ile yapılandırmak için bu yolu PATH ortam değişkenine ekleyin:  
  
   -   % Program Files%\Microsoft Visual Studio 11.0\Common7\IDE  
  
2. İsteğe bağlı olarak, çözümlerinizi derlemek için MSBuild kullanmak daha kolay hale getirmek için PATH değişkenini aşağıdaki yolları da ekleyebilirsiniz.  
  
    Yerel 32-bit MSBuild kullanmak istiyorsanız, bu yolları PATH değişkenine ekleyin:  
  
   - % Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Araçları  
  
   - %windir%\Microsoft.NET\Framework\v4.0.30319  
  
     Yerel 64-bit MSBuild kullanmak istiyorsanız, bu yolları PATH değişkenine ekleyin:  
  
   - % Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\x64  
  
   - %windir%\Microsoft.NET\Framework64\v4.0.30319  
  
##  <a name="InstallingMSBuildToGAC"></a> İçin Genel Derleme Önbelleği (GAC) yapı bilgisayarında MSBuild derlemeleri yükleme  
 MSBuild, yapı bilgisayarında GAC'ye yüklenecek bazı ek derlemeler yüklenmesi gerekir.  
  
#### <a name="to-copy-assemblies-from-the-host-computer-and-install-them-on-the-build-computer"></a>Ana bilgisayardan derlemeleri kopyalamak ve yapı bilgisayarında bunları yüklemek için  
  
1.  Aşağıdaki derlemeleri ana bilgisayardan yapı bilgisayarına kopyalayın. GAC'ye yüklenecek çünkü burada bunları yapı bilgisayarında yerleştirdiğiniz önemi yoktur.  
  
    -   %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.Build.CPPTasks.common.V110.dll  
  
    -   %ProgramFiles%\Microsoft visual Studio 11.0\Common7\IDE\CommonExtensions\Microsoft\VC\Project\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll  
  
    -   %ProgramFiles%\Microsoft visual Studio 11.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.VCProjectEngine.dll  
  
2.  Derlemeleri GAC'ye yüklemek için yapı bilgisayarında gacutil.exe bulun — genellikle %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 araçlarında olduğu\\. Bu klasörü bulamıyorsanız, adımları yineleyin [dosyaları ana bilgisayardan yapı bilgisayarına kopyalamak](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) Bu anlatım bölümü.  
  
     Yönetici haklarına sahip bir komut istemi penceresi açın ve her dosya için şu komutu çalıştırın:  
  
     **Gacutil -i \<dosyası >**  
  
    > [!NOTE]
    >  Bir derlemenin GAC öğesine tam olarak yüklemek için bir yeniden başlatma gerekebilir.  
  
##  <a name="BuildingProjects"></a> Proje oluşturma  
 Team Foundation derlemesi oluşturmak için kullanabileceğiniz [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] projeleri ve çözümleri veya oluşturabilirsiniz onları komut satırında. Projeleri derlemek için Team Foundation derlemesi kullandığınızda, sistem mimarisine karşılık gelen MSBuild yürütülebilir dosyasını çağırır.  Komut satırında, 32-bit MSBuild veya 64-bit MSBuild kullanabilirsiniz ve PATH ortam değişkenini ayarlayarak veya doğrudan mimariye özgü MSBuild yürütülebilir dosyasını çağırarak MSBuild'in mimarisini seçebilirsiniz.  
  
 Komut isteminde MSBuild.exe'yi kullanmak için aşağıdaki komutu çalıştığı *solution.sln* , uygulamanızın adı için bir yer tutucudur.  
  
 **MSBuild** *solution.sln*  
  
 Komut satırında Msbuild'i kullanma hakkında daha fazla bilgi için bkz: [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Oluşturulacak [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] projeleri, "v110" Platform araç takımını kullanmanız gerekir. Düzenlenecek istemiyorsanız [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] proje dosyaları, bu komut satırı bağımsız değişkenini kullanarak Platform araç takımını ayarlayabilirsiniz:  
>   
>  **MSBuild** *solution.sln* **/p:PlatformToolset v110 =**  
  
##  <a name="CreatingForSourceControl"></a> Böylece kaynak denetimine iade derleme ortamı oluşturma  
 GAC'ing dosyalarını gerektirmeyen veya kayıt defteri ayarlarının değiştirilmesini gerektirmeyen ve çeşitli bilgisayarlara dağıtılan bir yapı ortamı oluşturabilirsiniz. Aşağıdaki adımlarda bunu yapmanın tek yoludur. Bu adımları yapı ortamınızın benzersiz karakteristiğine uyarlayın.  
  
> [!NOTE]
>  Tracker.exe derleme sırasında bir hata oluşturmayacaksa, artımlı oluşturmayı devre dışı bırakmanız gerekir. Artımlı oluşturmayı devre dışı bırakmak için bu yapı parametresini ayarlayın:  
>   
>  **MSBuild** *solution.sln* **/p:TrackFileAccess = false**  
  
#### <a name="to-create-a-build-environment-that-can-be-checked-into-source-control"></a>Kaynak denetimine iade edilebilen bir yapı ortamı oluşturmak için  
  
1.  Ana bilgisayarda bir "Depot" dizini oluşturun.  
  
     Bu adımlar, dizine % Depot % bakın.  
  
2.  Dizinleri ve dosyaları açıklandığı gibi kopyalayın [dosyaları ana bilgisayardan yapı bilgisayarına kopyalamak](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) bu kılavuz, bunları yeni oluşturduğunuz % Depot % dizininin altına yapıştırın dışında bölümünde. Örneğin, %ProgramFiles%\Windows Kits\8.0\bin\ yolundan %Depot%\Windows Kits\8.0\bin için kopyalama\\.  
  
3.  Dosyalar % Depot % içine yapıştırıldığında, şu değişiklikleri yapın:  
  
    -   % Depot%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPP.Targets, \Microsoft.Cpp.InvalidPlatforms.targets\\, \Microsoft.cppbuild.targets\\ve \Microsoft.CppCommon.targets\\, her örneğini değiştirin ,  
  
         AssemblyName="Microsoft.Build.CppTasks.Common.v110, sürüm 4.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a ="  
  
         to  
  
         AssemblyFile = "$(VCTargetsPath11) Microsoft.Build.CppTasks.Common.v110.dll".  
  
         Önceki Adlandırma gac'lenen derlemeye dayanır.  
  
    -   % Depot % \msbuild\microsoft.cpp\v4.0\v110\microsoft.cppclean.targets'ta her örneğini değiştirin:  
  
         AssemblyName="Microsoft.Build.CppTasks.Common.v110, sürüm 4.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a ="  
  
         to  
  
         AssemblyFile = "$(VCTargetsPath11) Microsoft.Build.CppTasks.Common.v110.dll".  
  
4.  Bir .props dosyası oluşturun — Örneğin, Partner.autoımports.props—ve bunu projelerinizi içeren klasörün kökünde koyun. Bu dosya, çeşitli kaynakları bulmak amacıyla MSBuild tarafından kullanılan değişkenleri ayarlamak için kullanılır. Değişkenler bu dosya tarafından ayarlanmazsa, diğer .props dosyaları ve kayıt defteri değerlerine dayanan .targets dosyaları tarafından ayarlanırlar. Biz herhangi bir kayıt defteri değeri ayarı olmayan olduğundan, bu değişkenler boş ve yapı başarısız olur. Bunun yerine, bunu Partner.autoımports.props öğesine ekleyin:  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <!-- This file must be imported by all project files at the top of the project file. -->  
    <Project ToolsVersion="4.0"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
    <VCTargetsPath>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath>  
    <VCTargetsPath11>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath11>  
    <MSBuildExtensionsPath>$(DepotRoot)MSBuild</MSBuildExtensionsPath>  
    <MSBuildExtensionsPath32>$(DepotRoot)MSBuild</MSBuildExtensionsPath32>  
    <VCInstallDir_110>$(DepotRoot)Microsoft Visual Studio 11.0\VC\</VCInstallDir_110>  
    <VCInstallDir>$(VCInstallDir_110)</VCInstallDir>  
    <WindowsKitRoot>$(DepotRoot)Windows Kits\</WindowsKitRoot>  
    <WindowsSDK80Path>$(WindowsKitRoot)</WindowsSDK80Path>  
    <WindowsSdkDir_80>$(WindowsKitRoot)8.0\</WindowsSdkDir_80>  
    <WindowsSdkDir>$(WindowsSDKDir_80)</WindowsSdkDir>  
    <WindowsSdkDir_80A>$(DepotRoot)Microsoft SDKs\Windows\v8.0A\</WindowsSdkDir_80A>  
    </PropertyGroup>  
    </Project>  
    ```  
  
5.  Her proje dosyalarınızı sonra yukarıya aşağıdaki satırı ekleyin `<Project Default Targets…>` satır.  
  
    ```  
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>  
    ```  
  
6.  Komut satırı ortamını aşağıdaki gibi değiştirin:  
  
    -   Ayarlama Depot =*1. adımda oluşturduğunuz Depot dizininin konumu*  
  
    -   Kümesi yolu % path %; = *MSBuild konumunu bilgisayarda*; %D epot%\Windows\System32;%D epot%\Windows\SysWOW64;%D Visual Studio 11.0\Common7\IDE\ epot%\Microsoft  
  
         Yerel 64 bit yapı için 64-bit Msbuild'i gösterin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yürütülebilir hata ayıklamayı çalıştırmak için Test Makinesi hazırlama](http://msdn.microsoft.com/library/f0400989-cc2e-4dce-9788-6bdbe91c6f5a)   
 [Komut Satırı Başvurusu](../msbuild/msbuild-command-line-reference.md)



