---
title: 'İzlenecek yol: birden çok bilgisayarda derleme ortamı oluşturma'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building on multiple computers
- build environment, MSBuild
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2dc88c3861adb8b1d9f239d6ceedee2b76bc2e25
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951619"
---
# <a name="walkthrough-create-a-multiple-computer-build-environment"></a>İzlenecek yol: birden çok bilgisayarda derleme ortamı oluşturma

Visual Studio bir ana bilgisayara yükleyerek, kuruluşunuzda bir yapı ortamı oluşturabilirsiniz ve böylece katılabilmesi çeşitli dosya ve ayarları başka bir bilgisayara ardından kopyalama oluşturur. Visual Studio'yu diğer bilgisayara yüklemeniz gerekmez.

Bu belge, yazılımın harici olarak dağıtılması veya üçüncü taraflara yapı ortamları sağlamak için hakları confer değil.

> Sorumluluk reddi<br /><br /> Bu belge bir "olarak-olan" olarak. Özetlenen adımları Test ettiğimiz olsa da her yapılandırma tamamen test etmek yükümlü değiliz. Belgeyi öğrenilen herhangi ek bilgilerle güncel tutmaya dener. Bilgi ve URL ve diğer Internet Web sitesi referansları da dahil olmak üzere bu belgede, bildirilmeksizin değiştirilebilir. Microsoft hiçbir açık veya zımni bilgilerle garantide bulunmaz. Bunu kullanarak riski size aittir.<br /><br /> Bu belge ile herhangi bir Microsoft ürünü üzerinde hiçbir fikri mülkiyet hakkı sağlamaz. Kopyalayabilir ve dahili olarak, bu belgeyi kullanmak amacıyla başvuru.<br /><br /> Herhangi bir öneri, yorum veya bu belgeyle ilgili geribildirimde ("Geribildirim") Microsoft vermek zorunda değilsiniz. Ancak, gönüllü olarak sağlayacağınız her türlü geribildirim, Microsoft Products ve ilgili belirtimlerde veya hangi sırayla bağlı kendi ürünlerini geliştirmek için diğer üçüncü taraflarca dayanan diğer belgeleri (topluca, "Microsoft Offerings") kullanılabilir. Buna göre bu belgenin veya Microsoft uygulandıkları Offerings herhangi bir sürümü üzerinde Microsoft Feedback bildirimde bulunursanız, kabul etmiş olursunuz: (a) Microsoft serbestçe kullanın, yeniden oluşturma, lisans, dağıtmak ve aksi takdirde herhangi bir Microsoft geri bildirim tanımış olursunuz Teklif; (b), ayrıca üçüncü taraflara, ücretsiz, yalnızca diğer ürünleri kullanmayı veya kendi geri bildirim bir araya getiren herhangi belirli bir Microsoft Product ile arabirim parçaları etkinleştirmek için gereken bu patent hakkı vermek; ve (c) aldığınız düşünmenize neden olan herhangi bir Geri bildiriminiz (i) herhangi bir patent, telif hakkını veya diğer fikri mülkiyet veya üçüncü taraf sağ tabi olan Microsoft vermeyiz. veya (ii) konu Microsoft Offering geribildirimler veya bu geri bildirimlerden veya diğer Microsoft fikri mülkiyet için lisanslı veya aksi türetilmiş Lisans Koşulları'nı herhangi bir üçüncü tarafla paylaşılmaz.

Bu kılavuz, aşağıdaki işletim sistemlerine karşı doğrulandı:

- Windows 8 (x86 ve x64)
- Windows 7 Ultimate
- Windows Server 2008 R2 Standard

Bu izlenecek yolda adımları tamamladıktan sonra bu tür uygulamalar oluşturmak için çoklu bilgisayar ortamı kullanabilirsiniz:

- Windows 8 SDK kullanan C++ Masaüstü uygulamaları
- .NET Framework 4.5 hedefleyen Visual Basic veya C# Masaüstü uygulamaları

Bu tür uygulamalar oluşturmak için çoklu bilgisayar ortamı kullanılamaz:

- UWP uygulamaları. UWP uygulamaları oluşturmak için yapı bilgisayarında Visual Studio yüklemeniz gerekir.
- .NET Framework 4 veya önceki sürümlerini hedefleyen Masaüstü uygulamaları. Bu tür uygulamalar oluşturmak için ya da Visual Studio veya .NET başvuru bütünleştirilmiş kodları ve Araçları (Windows 7.1 SDK'sı) yapı bilgisayarında yüklemeniz gerekir.

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio ile **.NET Masaüstü geliştirmesinden** iş yükü yüklenmiş.

## <a name="install-software-on-the-computers"></a>Yazılımını bilgisayarlara yükleme

İlk olarak, ana bilgisayarı ayarlayın ve ardından yapı bilgisayarını ayarlayın.

Visual Studio ana bilgisayara yükleyerek, dosya ve daha sonra yapı bilgisayarına kopyalayacak ayarları oluşturun. Visual Studio yüklediğiniz bilgisayar, ancak Yapı bilgisayarının mimarisinin bir x86 veya x x64 ana bilgisayarın mimarisiyle eşleşmelidir.

1. Ana bilgisayarda Visual Studio'yu yükleyin.

2. Yapı bilgisayarında .NET Framework 4.5 veya sonraki bir sürümü yükleyin. Yüklü olduğunu doğrulamak için kontrol **sürüm** girdi kayıt defteri alt anahtarında **hkey_local_machıne\software\microsoft\net Framework Setup\NDP\v4\Full** değeri **4.5** veya üzeri.

## <a name="copy-files-from-the-host-computer-to-the-build-computer"></a>Dosyaları ana bilgisayardan yapı bilgisayarına kopyalayın.

Bu bölüm, belirli dosyaları, derleyicileri, derleme araçları, MSBuild varlıklarını ve yapı bilgisayarı ana bilgisayar kayıt defteri ayarlarını kopyalamayı kapsar. Bu yönergeler, Visual Studio ana bilgisayarda varsayılan konuma yüklediğinizi varsayar; başka bir konuma yüklediyseniz adımları da buna göre ayarlayın.

- X x86 bilgisayar için varsayılan konumdur *C:\Program Files\Microsoft Visual Studio 11.0*
- X x64 bilgisayar için varsayılan konumdur *C:\Program Files (x86) \Microsoft Visual Studio 11.0*

Dikkat adını *Program dosyaları* klasörü, yüklü işletim sisteminde bağlıdır. X x86 bilgisayar adıdır *Program dosyaları*; x x64 bilgisayar adıdır *Program dosyaları (x86)*. Sistem Mimarisi ne olursa olsun, bu izlenecek yolda başvurduğu *Program dosyaları* klasör olarak *% ProgramFiles %*.

> [!NOTE]
> Yapı bilgisayarında, tüm ilgili dosyalar aynı sürücüde olmalıdır; Ancak, söz konusu sürücünün sürücü harfi, Visual Studio ana bilgisayarında yüklü olduğu sürücünün sürücü harfi farklı olabilir. Her iki durumda da, bu belgenin sonraki bölümlerinde açıklandığı şekilde kayıt defteri girdileri oluşturduğunuzda dosyalarının konumunu dikkate alması gerekir.

### <a name="copy-the-windows-sdk-files-to-the-build-computer"></a>Windows SDK dosyalarını yapı bilgisayarına kopyalayın.

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

     .. .önceki dosyalarına yüklemiş *%ProgramFiles%\Windows Kits\8.0* önceki adımı ve bunların lisans koşullarını listelenen klasörler bu dosyalara ilişkin yapı sunucu haklarına izin. Dosyaların derleme bilgisayarınıza kopyalanıp kopyalanmadığını doğrulamak yüklü her Windows Kiti için lisans koşullarını kontrol edin. Lisans koşulları yapı sunucusu haklarına izin verme, dosyaları yapı bilgisayarından kaldırın.

2. Aşağıdaki klasörleri yinelemeli olarak ana bilgisayardan yapı bilgisayarına kopyalayın:

    - %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\ içinde

    - %ProgramFiles%\Common Files\Merge modules\ konumuna

    - %ProgramFiles%\Microsoft visual Studio 11.0\VC\

    - %ProgramFiles%\Microsoft visual Studio 11.0\Common7\Tools\ProjectComponents\

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\V110\

    - %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\. NETCore\v4.5\

    - %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\. NETFramework\v4.5\

3. Bu dosyaları ana bilgisayardan yapı bilgisayarına kopyalayın:

    - %ProgramFiles%\Microsoft visual Studio 11.0\Common7\IDE\msobj110.dll

    - %ProgramFiles%\Microsoft visual Studio 11.0\Common7\IDE\mspdb110.dll

    - %ProgramFiles%\Microsoft visual Studio 11.0\Common7\IDE\mspdbcore.dll

    - %ProgramFiles%\Microsoft visual Studio 11.0\Common7\IDE\mspdbsrv.exe

    - %ProgramFiles%\Microsoft visual Studio 11.0\Common7\IDE\msvcdis110.dll

    - %ProgramFiles%\Microsoft visual Studio 11.0\Common7\Tools\makehm.exe

    - %ProgramFiles%\Microsoft visual Studio 11.0\Common7\Tools\VCVarsQueryRegistry.bat

    - %ProgramFiles%\Microsoft visual Studio 11.0\Common7\Tools\vsvars32.bat

4. Yapı bilgisayarında yapı çıkışları çalıştırırsanız aşağıdaki Visual C++ çalışma zamanı kitaplıkları gereklidir; Örneğin, otomatikleştirilmiş test işleminin parçası olarak. Dosyaları altındaki alt genellikle bulunan *%ProgramFiles%\Microsoft Visual Studio 11.0\VC\redist\x86* veya *%ProgramFiles%\Microsoft Visual Studio 11.0\VC\redist\x64* klasörü Sistem mimarisine bağlı olarak. X86 sistemleri, ikili dosyalarını kopyalama x86 *Windows\System32* klasör. X64 sistemleri, ikili dosyalarını kopyalama x86 *Windows\SysWOW64* klasörü ve x64 ikili dosyalarını *Windows\System32* klasör.

    - \Microsoft.VC110.ATL\atl110.dll

    - \Microsoft.VC110.CRT\msvcp110.dll

    - \Microsoft.VC110.CRT\msvcr110.dll

    - \Microsoft.VC110.CXXAMP\vcamp110.dll

    - \Microsoft.VC110.MFC\mfc110.dll

    - \Microsoft.VC110.MFC\mfc110u.dll

    - \Microsoft.VC110.MFC\mfcm110.dll

    - \Microsoft.VC110.MFC\mfcm110u.dll

    - \Microsoft.VC110.MFCLOC\mfc110chs.dll

    - \Microsoft.VC110.MFCLOC\mfc110cht.dll

    - \Microsoft.VC110.MFCLOC\mfc110deu.dll

    - \Microsoft.VC110.MFCLOC\mfc110enu.dll

    - \Microsoft.VC110.MFCLOC\mfc110esn.dll

    - \Microsoft.VC110.MFCLOC\mfc110fra.dll

    - \Microsoft.VC110.MFCLOC\mfc110ita.dll

    - \Microsoft.VC110.MFCLOC\mfc110jpn.dll

    - \Microsoft.VC110.MFCLOC\mfc110kor.dll

    - \Microsoft.VC110.MFCLOC\mfc110rus.dll

    - \Microsoft.VC110.OPENMP\vcomp110.dll

5. Yalnızca aşağıdaki dosyaları kopyalayın *Debug_NonRedist\x86* veya *Debug_NonRedist\x64* klasör açıklandığı gibi yapı bilgisayara [bir hata ayıklama yürütülebilirçalıştırmakiçintestmakinesihazırlama](/cpp/ide/preparing-a-test-machine-to-run-a-debug-executable). Başka hiçbir dosya kopyalanamaz.

    - \Microsoft.VC110.DebugCRT\msvcp110d.dll

    - \Microsoft.VC110.DebugCRT\msvcr110d.dll

    - \Microsoft.VC110.DebugCXXAMP\vcamp110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110d.dll

    - \Microsoft.VC110.DebugMFC\mfc110ud.dll

    - \Microsoft.VC110.DebugMFC\mfcm110d.dll

    - \Microsoft.VC110.DebugMFC\mfcm110ud.dll

    - \Microsoft.VC110.DebugOpenMP\vcomp110d.dll

## <a name="create-registry-settings"></a>Kayıt defteri ayarları oluşturma

MSBuild ayarlarını yapılandırmak için kayıt defteri girdileri oluşturmanız gerekir.

1. Kayıt defteri girişleri için ana klasörü belirleyin. Tüm kayıt defteri girdilerini aynı üst anahtar altında oluşturulur. X x86 bilgisayardır, üst anahtar **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft**. X x64 bilgisayarında üst anahtar olduğunu **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft**. Sistem Mimarisi ne olursa olsun, bu İnceleme % RegistryRoot % olarak üst anahtara başvurur.

    > [!NOTE]
    > Ana bilgisayarınızın mimarisi yapı farklıysa, her bilgisayarda uygun üst anahtarı kullandığınızdan emin olun. Bu dışarı aktarma işlemini otomatikleştiriyorsanız özellikle önem taşır.
    >
    > Ayrıca, yapı bilgisayarında ana bilgisayarda kullandığınız olandan farklı bir sürücü harfi kullanıyorsanız, eşleşmesi için kayıt defteri girdilerinin değerlerini değiştirdiğinizden emin olun.

2. Yapı bilgisayarında aşağıdaki kayıt defteri girdilerini oluşturun. Tüm bu girdiler dizelerdir (tür == "REG_SZ" kayıt defterinde). Bu girişlerin değerlerini aynı ana bilgisayarda benzer girişlerle değerleri olarak ayarlayın.

   - **% RegistryRoot %\\. NETFramework\v4.0.30319\AssemblyFoldersEx\VCMSBuild Public Assemblies@(varsayılan)**

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools@InstallationFolder</strong>

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x86@InstallationFolder</strong>

   - **% RegistryRoot %\VisualStudio\11.0@Source dizinleri**

   - <strong>% RegistryRoot %\VisualStudio\11.0\Setup\VC@ProductDir</strong>

   - <strong>% RegistryRoot %\VisualStudio\SxS\VC7@FrameworkDir32</strong>

   - <strong>% RegistryRoot %\VisualStudio\SxS\VC7@FrameworkDir64</strong>

   - <strong>% RegistryRoot %\VisualStudio\SxS\VC7@FrameworkVer32</strong>

   - <strong>% RegistryRoot %\VisualStudio\SxS\VC7@FrameworkVer64</strong>

   - **% RegistryRoot %\VisualStudio\SxS\VC7@11.0**

   - **% RegistryRoot %\VisualStudio\SxS\VS7@11.0**

   - <strong>%RegistryRoot%\Windows Kits\Installed Roots@KitsRoot</strong>

   - <strong>% RegistryRoot %\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>% RegistryRoot %\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>% RegistryRoot %\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

   Yapı bilgisayarı üzerinde bir x64, ayrıca şu kayıt defteri girişi oluşturun ve nasıl ayarlanacağını belirlemek için konak bilgisayara başvurun.

   - <strong>%RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x64@InstallationFolder</strong>

   Yapı bilgisayarınız x64 ise ve MSBuild 64 bit sürümünü kullanmak istiyorsanız veya x x64 üzerinde Team Foundation Server yapı Hizmeti'ni kullanıyorsanız, bilgisayar, yerel 64 bit kayıt defterinde aşağıdaki kayıt defteri girdilerini oluşturun. Bu girişlerin nasıl ayarlanacağını belirlemek için konak bilgisayara başvurun.

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Setup\VS@ProductDir</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10</strong>

   - <strong>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11</strong>

## <a name="set-environment-variables-on-the-build-computer"></a>Yapı bilgisayarında ortam değişkenlerini ayarlama

Yapı bilgisayarında MSBuild kullanmak için PATH ortam değişkenleri ayarlamanız gerekir. Kullanabileceğiniz *vcvarsall.bat* veya değişkenleri ayarlamak için bunları el ile yapılandırabilirsiniz.

### <a name="use-vcvarsallbat-to-set-environment-variables"></a>Vcvarsall.bat'ı ortam değişkenlerini ayarlamak için kullanın

Açık bir **komut istemi** çalıştırma ve yapı bilgisayarı üzerinde penceresi *% Program Files%\Microsoft Visual Studio 11.0\VC\vcvarsall.bat*. Kullanmak istediğiniz araç kümesini belirtmek için bir komut satırı bağımsız değişkeni kullanabilirsiniz — x86, yerel x64 veya x64 çapraz derleyici. Bir komut satırı bağımsız değişkeni, araç kümesi kullanılır x86 belirtmezseniz.

Bu tablo için desteklenen bağımsız değişkenleri açıklar *vcvarsall.bat*:

|Vcvarsall.bat bağımsız değişkeni|Derleyici|Bilgisayar mimarisi oluşturun|Çıkış mimarisini oluşturun|
| - |--------------| - | - |
|x86 (varsayılan)|32 bit yerel|x86, x64|x86|
|x86_amd64|platformlar arası x64|x86, x64|X64|
|amd64|x64 yerel|X64|X64|

Varsa *vcvarsall.bat* başarıyla çalıştıktan — diğer bir deyişle, hiçbir hata iletisi görüntülenir; sonraki adıma atla ve devam [yükleme MSBuild derlemeleri için Genel Derleme Önbelleği (GAC) yapı bilgisayarında](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC)bu belgenin bölüm.

### <a name="manually-set-environment-variables"></a>Ortam değişkenlerini el ile ayarlama

1. Komut satırı ortamını el ile yapılandırmak için bu yolu PATH ortam değişkenine ekleyin:

    - % Program Files%\Microsoft Visual Studio 11.0\Common7\IDE

2. İsteğe bağlı olarak, çözümlerinizi derlemek için MSBuild kullanmak daha kolay hale getirmek için PATH değişkenini aşağıdaki yolları da ekleyebilirsiniz.

   Yerel 32-bit MSBuild kullanmak istiyorsanız, bu yolları PATH değişkenine ekleyin:

   - % Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Araçları

   - %windir%\Microsoft.NET\Framework\v4.0.30319

   Yerel 64-bit MSBuild kullanmak istiyorsanız, bu yolları PATH değişkenine ekleyin:

   - % Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\x64

   - %windir%\Microsoft.NET\Framework64\v4.0.30319

## <a name="install-msbuild-assemblies-to-the-global-assembly-cache-gac-on-the-build-computer"></a>İçin Genel Derleme Önbelleği (GAC) yapı bilgisayarında MSBuild derlemeleri yükleme

MSBuild, yapı bilgisayarında GAC'ye yüklenecek bazı ek derlemeler yüklenmesi gerekir.

1. Aşağıdaki derlemeleri ana bilgisayardan yapı bilgisayarına kopyalayın. GAC'ye yüklenecek çünkü burada bunları yapı bilgisayarında yerleştirdiğiniz önemi yoktur.

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.Build.CPPTasks.common.V110.dll

    - %ProgramFiles%\Microsoft visual Studio 11.0\Common7\IDE\CommonExtensions\Microsoft\VC\Project\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll

    - %ProgramFiles%\Microsoft visual Studio 11.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.VCProjectEngine.dll

2. Derlemeleri GAC'ye yüklemek için bulun *gacutil.exe* yapı bilgisayarında — genellikle %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 araçlarında olduğu\\. Bu klasörü bulamıyorsanız, adımları yineleyin [dosya kopyalama ana bilgisayardan yapı bilgisayarına](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) Bu anlatım bölümü.

     Açık bir **komut istemi** penceresini yönetici haklarına sahip ve her dosya için şu komutu çalıştırın:

     **Gacutil -i \<dosyası >**

    > [!NOTE]
    > Bir derlemenin GAC öğesine tam olarak yüklemek için bir yeniden başlatma gerekebilir.

## <a name="build-projects"></a>Projeler derleme

Visual Studio projeleri ve çözümleri oluşturmak için Azure işlem hatlarını kullanın veya komut satırında oluşturabilirsiniz. Projeleri derlemek için Azure işlem hatları kullandığınızda, sistem mimarisine karşılık gelen MSBuild yürütülebilir dosyasını çağırır. Komut satırında, 32-bit MSBuild veya 64-bit MSBuild kullanabilirsiniz ve PATH ortam değişkenini ayarlayarak veya doğrudan mimariye özgü MSBuild yürütülebilir dosyasını çağırarak MSBuild'in mimarisini seçebilirsiniz.

Kullanılacak *msbuild.exe* komut isteminde aşağıdaki komutu çalıştırarak *solution.sln* , uygulamanızın adı için bir yer tutucudur.

**MSBuild** *solution.sln*

Komut satırında Msbuild'i kullanma hakkında daha fazla bilgi için bkz: [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).

## <a name="create-the-build-environment-so-that-it-can-be-checked-into-source-control"></a>Böylece kaynak denetimine iade yapı ortamını oluşturun

"GAC" ing dosyaları veya kayıt defteri ayarlarının değiştirilmesini gerektirmeyen ve çeşitli bilgisayarlara dağıtılan bir yapı ortamı oluşturabilirsiniz. Aşağıdaki adımlarda bunu yapmanın tek yoludur. Bu adımları yapı ortamınızın benzersiz karakteristiğine uyarlayın.

> [!NOTE]
> Artımlı oluşturmayı devre dışı bırakmanız gerekir böylece *tracker.exe* derleme sırasında bir hata oluşturmaz. Artımlı oluşturmayı devre dışı bırakmak için bu yapı parametresini ayarlayın:
>
> **MSBuild** *solution.sln* **/p:TrackFileAccess = false**

1. Oluşturma bir *Depot* ana bilgisayarda dizin.

     Bu adımlar, dizine % Depot % bakın.

2. Dizinleri ve dosyaları açıklandığı gibi kopyalayın [dosya kopyalama ana bilgisayardan yapı bilgisayarına](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) bölümü altında yapıştırın dışında bu kılavuzun *% Depot %* yeni dizin oluşturuldu. Örneğin, kopyalama *%ProgramFiles%\Windows Kits\8.0\bin* için *%Depot%\Windows Kits\8.0\bin*.

3. Dosyalar ne zaman yapıştırılan içinde *% Depot %*, şu değişiklikleri yapın:

    - % Depot%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPP.Targets, \Microsoft.Cpp.InvalidPlatforms.targets\\, \Microsoft.cppbuild.targets\\ve \Microsoft.CppCommon.targets\\, her örneğini değiştirin ,

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, sürüm 4.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a ="

         to

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".

         Önceki Adlandırma gac'lenen derlemeye dayanır.

    - % Depot % \msbuild\microsoft.cpp\v4.0\v110\microsoft.cppclean.targets'ta her örneğini değiştirin:

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, sürüm 4.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a ="

         to

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll".

4. Oluşturma bir *.props* dosya — Örneğin, *Partner.autoımports.props*— ve projelerinizi içeren klasörün kökünde yerleştirin. Bu dosya, çeşitli kaynakları bulmak amacıyla MSBuild tarafından kullanılan değişkenleri ayarlamak için kullanılır. Değişkenler bu dosya tarafından ayarlanmazsa, diğer tarafından ayarlanırlar *.props* dosyaları ve *.targets* kayıt defteri değerlerine dayanan dosyaları. Biz herhangi bir kayıt defteri değeri ayarı olmayan olduğundan, bu değişkenler boş ve yapı başarısız olur. Bunun yerine şuna ekleyin *Partner.autoımports.props*:

    ```xml
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

5. Her proje dosyalarınızı sonra yukarıya aşağıdaki satırı ekleyin `<Project Default Targets...>` satır.

    ```xml
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>
    ```

6. Komut satırı ortamını aşağıdaki gibi değiştirin:

    - Ayarlama Depot =*1. adımda oluşturduğunuz Depot dizininin konumu*

    - Kümesi yolu % path %; = *MSBuild konumunu bilgisayarda*; %D epot%\Windows\System32;%D epot%\Windows\SysWOW64;%D Visual Studio 15.0\Common7\IDE\ epot%\Microsoft

       Yerel 64 bit yapı için 64-bit Msbuild'i gösterin.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama yürütülebilir çalıştırmak için test makinesi hazırlama](/cpp/ide/preparing-a-test-machine-to-run-a-debug-executable)
- [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)