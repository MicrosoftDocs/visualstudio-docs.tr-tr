---
title: Bir C++ hata ayıklama yapılandırması proje ayarları
ms.custom: seodec18
ms.date: 11/26/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- VC.Project.VCDebugSettings.WebBrowser.DebuggerType
- VC.Project.IVCGPUDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.SymbolPath
- VC.Project.IVCClusterDebugPageObject.ApplicationCommand
- VC.Project.IVCRemoteDebugPageObject.WorkingDirectory
- VC.Project.VCDebugSettings.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.SQLDebugging
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCGPUDebugPageObject.CommandArguments
- VC.Project.VCDebugSettings.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunWorkingDirectory
- VC.Project.IVCLocalDebugPageObject.SQLDebugging
- VC.Project.IVCWebSvcDebugPageObject.HttpUrl
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCClusterDebugPageObject.MPIRunCommand
- VC.Project.IVCGPUDebugPageObject.WorkingDirectory
- VC.Project.IVCWebSvcDebugPageObject.DebuggerType
- VC.Project.IVCRemoteDebugPageObject.CommandArguments
- VC.Project.IVCRemoteDebugPageObject.DebuggerType
- VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCRemoteDebugPageObject.RemoteMachine
- VC.Project.IVCClusterDebugPageObject.MPIRunArguments
- VC.Project.IVCClusterDebugPageObject.MPIAcceptFilter
- VC.Project.IVCGPUDebugPageObject.RemoteConnection
- VC.Project.VCDebugSettings.PDBPath
- VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory
- VC.Project.VCDebugSettings.SQLDebugging
- VC.Project.VCDebugSettings.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ShimCommand
- VC.Project.IVCLocalDebugPageObject.Command
- VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCLocalDebugPageObject.Attach
- VC.Project.VCDebugSettings.Command
- VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.RemoteCommand
- VC.Project.IVCClusterDebugPageObject.ApplicationArguments
- VC.Project.IVCLocalDebugPageObject.Environment
- VC.Project.IVCGPUDebugPageObject.DeploymentDirectory
- VC.Project.IVCLocalDebugPageObject.EnvironmentMerge
- VC.Project.VCDebugSettings.Environment
- VC.Project.IVCGPUDebugPageObject.BreakpointBehavior
- VC.Project.IVCLocalDebugPageObject.DebuggerType
- VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl
- VC.Project.IVCWebSvcDebugPageObject.SQLDebugging
- VC.Project.IVCGPUDebugPageObject.AcceleratorType
- VC.Project.IVCGPUDebugPageObject.Environment
- VC.Project.VCDebugSettings.RemoteMachine
- VC.Project.IVCGPUDebugPageObject.AdditionalFilesToDeploy
- VC.Project.VCDebugSettings.WorkingDirectory
- vs.debug.builds
- VC.Project.VCDebugSettings.Attach
- VC.Project.VCDebugSettings.HttpUrl
- VC.Project.IVCClusterDebugPageObject.MPIAcceptMode
- VC.Project.IVCGPUDebugPageObject.Attach
- VC.Project.IVCRemoteDebugPageObject.AdditionalFiles
- VC.Project.IVCGPUDebugPageObject.Command
- VC.Project.VCDebugSettings.Remote
- VC.Project.IVCRemoteDebugPageObject.Attach
- VC.Project.VCDebugSettings.EnvironmentMerge
- VC.Project.IVCGPUDebugPageObject.MachineName
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DEBUG linker option
- -PDB linker option
- -Zl compiler option [C++]
- /DEBUG linker option
- /PDBSTRIPPED linker option
- /MAPINFO linker option
- -Zd compiler option [C++]
- -DEBUG linker option
- MAPINFO linker option
- /ZI compiler option [C++]
- ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debugger settings
- project settings [Visual Studio], debug configurations
- mapfiles, project settings
- debug configurations, C++
- project settings [Visual Studio]
- /PDB linker option
- -PDBSTRIPPED linker option
- debug builds, project settings
- PDB linker option
- projects [Visual Studio], debug configurations
- project configurations, debug
- Zd compiler option [C++]
- MAP linker option
- /Z7 compiler option [C++]
- .pdb files, debug build project settings
- -MAP linker option
- -MAPINFO linker option
- /Zd compiler option [C++]
- PDBSTRIPPED linker option
- -Z7 compiler option [C++]
- pdb files, debug build project settings
- /MAP linker option
ms.assetid: 860c7f13-a108-4fe5-8fca-d235cd3ca1cb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 951b46bfc6ef0910731dfe76cc9913f2c4a423ad
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066908"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>C++ hata ayıklama yapılandırması proje ayarları
Bir C veya Visual C++ hata ayıklama yapılandırması proje ayarları değiştirebilirsiniz **özellik sayfaları** anlatıldığı gibi iletişim kutusu, [nasıl yapılır: ayarlama hata ayıklama ve dağıtım yapılandırmalarını](../debugger/how-to-set-debug-and-release-configurations.md). Aşağıdaki tablolarda, hata ayıklayıcı ile ilgili ayarların nerede bulunacağı gösterilmektedir **özellik sayfaları** iletişim kutusu.  
  
> [!NOTE]
>  Hata ayıklama proje ayarları **yapılandırma özellikleri/hata ayıklama** kategorisi için UWP uygulamaları ve C++ ile yazılmış bileşenler için farklı. Bkz: [(VB, C#, C++ ve XAML) bir hata ayıklama oturumunu başlatmada](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).  
  
 Her hata ayıklama özelliği ayarı otomatik olarak yazılır ve kaydedilen "kullanıcı başına" dosyaya (. vcxproj.user) çözümünüzü her kaydettiğinizde, çözümünüz için.  

 Hangi hata ayıklayıcının kullanılacağını belirtin **başlatmak için hata ayıklayıcı** liste kutusunda, aşağıdaki tabloda açıklandığı gibi. Seçiminiz hangi özelliklerin görülebileceğini etkiler.  
    
## <a name="configuration-properties-folder-debugging-category"></a>Yapılandırma özellikleri klasörü (hata ayıklama kategorisi)  
  
| **Ayarı** | **Açıklama** |
| - | - |
| **Başlatmak için hata ayıklayıcı** | Hata ayıklayıcının, aşağıdaki seçenekler ile Çalıştır belirtir:<br /><br /> -   **Yerel Windows hata ayıklayıcı**<br />-   **Uzak Windows hata ayıklayıcı**<br />-   **Web tarayıcı hata ayıklayıcısı**<br />-   **Web hizmeti hata ayıklayıcısı** |
| **Komut** (yerel Windows hata ayıklayıcı) | Yerel bilgisayarda hata ayıklaması yaptığınız programı başlatma komutunu belirtir. |
| **Uzak komut** (uzak Windows hata ayıklayıcı) | Uzak bilgisayardaki .exe yolu. Yalnızca uzak makinede girersiniz gibi yolu girin. |
| **Komut bağımsız değişkenleri** (yerel Windows hata ayıklayıcı)<br /><br /> **Uzak komut satırı bağımsız değişkenlerini** (uzak Windows hata ayıklayıcı) | -Daha önce belirtilen komut için bağımsız değişkenleri belirtir.<br /><br /> Bu kutuda aşağıdaki yönlendirme işleçlerini kullanabilirsiniz:<br /><br /> < `file`<br /> Dosyadan stdin okur.<br /><br /> > `file`<br /> Dosyaya STDOUT yazar.<br /><br /> >> `file`<br /> Dosyaya STDOUT ekler.<br /><br /> 2> `file`<br /> Stderr dosyasına yazar.<br /><br /> 2>> `file`<br /> Dosyaya stderr ekler.<br /><br /> 2> &1<br /> Stderr (2) çıktısını stdout (1) ile aynı konuma gönderir.<br /><br /> 1> &2<br /> STDOUT (1) çıktısını stderr (2) ile aynı konuma gönderir.<br /><br /> Çoğu durumda, bu işleçler yalnızca konsol uygulamaları için geçerlidir. |
| **Çalışma dizini** | EXE dosyanızın bulunduğu proje dizinine göre ayıklanan programın çalışma dizini belirtir. Burayı boş bırakırsanız, çalışma dizini proje dizini bağlıdır. Uzaktan hata ayıklama için proje dizini uzak sunucu üzerinde olur. |
| **Ekleme** (yerel Windows hata ayıklayıcısı ve uzak Windows hata ayıklayıcı) | Başlatma veya uygulamasına belirtir. Varsayılan ayar Hayır |
| **Uzak sunucu adı** (uzak Windows hata ayıklayıcı) | Bir uygulamada hata ayıklamak istediğiniz bilgisayarın (sizin dışında) adını belirtir.<br /><br /> RemoteMachine yapı makrosu bu özelliğin değerine ayarlanır; Daha fazla bilgi için [derleme komutları ve Özellikler makroları için](/cpp/ide/common-macros-for-build-commands-and-properties). |
| **Bağlantı** (uzak Windows hata ayıklayıcı) | Uzaktan hata ayıklama için standart ve kimlik doğrulamasız bağlantı türleri arasında geçiş yapmanıza izin verir. Bir uzak bilgisayar adı belirtin **uzak sunucu adı** kutusu. Bağlantı türleri aşağıdakileri kapsamaktadır:<br /><br /> -   **Windows kimlik doğrulaması ile uzaktan**<br />-   **Kimlik doğrulaması ile uzaktan**<br /><br /> **Not** uzaktan hata ayıklama kimlik doğrulamasısız uzak bilgisayarı güvenlik ihlallerine karşı savunmasız. Windows kimlik doğrulama modu daha güvenlidir.<br /><br /> Daha fazla bilgi için [uzaktan hata ayıklama Kurulumu](../debugger/remote-debugging.md). |
| **HTTP URL** (Web hizmeti hata ayıklayıcısı ve Web tarayıcı hata ayıklayıcısı) | Hata ayıklaması yaptığınız projenin bulunduğu URL'yi belirtir. |
| **Hata ayıklayıcı türü** | Kullanılacak hata ayıklayıcı türünü belirtir: **yalnızca yerel**, **yalnızca yönetilen**, **yalnızca GPU**, **karma**, **otomatik**(varsayılan) veya **betik**.<br /><br /> -   **Yalnızca yerel** yönetilmeyen C++ kodu içindir.<br />-   **Yalnızca yönetilen** ortak dil çalışma zamanı altında (yönetilen kod) çalışan kod içindir.<br />-   **Karma** hem yönetilen hem de yönetilmeyen kod için hata ayıklayıcıları çağırır.<br />-   **Otomatik** derleyici ve EXE bilgilerini temel alan bir hata ayıklayıcı türünü belirler.<br />-   **Betik** komut dosyaları için bir hata ayıklayıcı çağırır.<br />-   **Yalnızca GPU** bir GPU cihazında veya DirectX başvuru tarayıcısında çalışan C++ AMP kodu içindir. Bkz: [GPU hata ayıklama kodu](../debugger/debugging-gpu-code.md). |
| **Ortam** (yerel Windows hata ayıklayıcısı ve uzak Windows hata ayıklayıcı) | Hata ayıklaması yaptığınız program için ortam değişkenlerini belirtir. Standart ortam değişkeni sözdizimini kullanın (örneğin, `PATH="%SystemRoot%\..."`). Bu değişkenler, sistem ortamını geçersiz kılar veya bağlı olarak, sistem ortamıyla birleştirilir **ortamı Birleştir** ayarı. Ayarlar sütununu sol tıklattığınızda, "Düzenle..." görünür. Ortam değişkenlerini düzenlemek için bu bağlantıyı seçin. |
| **Ortam birleştirme** (yerel Windows hata ayıklayıcı) | Değişkenleri belirler belirtilen **ortam** kutusunda, işletim sistemi tarafından tanımlanan ortam ile birleştirilir. Varsayılan ayar evet'tir. |
| **SQL hata ayıklama** (tüm ancak MPI Kümesi hata ayıklayıcısı) | Uygulamanızdan SQL yordamlarının hata ayıklamasını etkinleştirir, [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] uygulama. Varsayılan ayar Hayır |
| **Hata ayıklama Hızlandırıcı türü** (yalnızca GPU hata ayıklama) | Hata ayıklama için kullanılacak GPU cihazını belirtir. GPU uyumlu cihazlar için cihaz sürücülerinin yüklenmesi ek seçenekler ekler. Varsayılan ayar **GPU - yazılım öykünücüsü**. |
| **GPU varsayılan kesme noktası davranışı** (yalnızca GPU hata ayıklama) | Bir kesme noktası olayının SIMD eğriltme içindeki her bir iş parçacığı için oluşturup oluşturmadığını belirtir. Varsayılan ayar kesme noktası olayı eğriltme başına yalnızca bir kez başlatılmasıdır. |
| **Varsayılan amp Hızlandırıcısı** | GPU kodunda hata ayıklama sırasında varsayılan AMP hızlandırıcıyı belirtir. Seçin **WARP Yazılım hızlandırıcı** soruna donanım veya sürücüden kodunuz yerine nedeni araştırmak için. |
| **Dağıtım dizini** (uzak Windows hata ayıklayıcı) | Proje çıktısı başlatmadan önce kopyalanacağı burada olacaktır uzak bilgisayardaki yolunu belirtir. Yol, uzak bilgisayardaki bir ağ paylaşımı veya uzak bilgisayardaki bir klasöre bir yol olabilir. Varsayılan ayar boş proje çıkışının bir ağ paylaşımına kopyalanmadığı anlamına gelir. Dosyaların dağıtımını etkinleştirmek için de seçmeniz gerekir **Dağıt** Configuration Manager iletişim kutusundaki onay kutusu. Daha fazla bilgi için [nasıl yapılır: yapılandırmaları oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md). |
| **Dağıtılacak ek dosyalar** (uzak Windows hata ayıklayıcı) | Dağıtım dizini özelliği ayarlanmışsa, bu dağıtım dizinine kopyalanacak ek dosyaların noktalı virgülle ayrılmış bir listesini budur. Varsayılan ayar boş, hiçbir ek dosyaları dağıtım dizinine kopyalanmadığı anlamına gelir. Dosyaların dağıtımını etkinleştirmek için de seçmeniz gerekir **Dağıt** Configuration Manager iletişim kutusundaki onay kutusu. Daha fazla bilgi için [nasıl yapılır: yapılandırmaları oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md). |
| **Visual C++ hata ayıklama çalışma zamanı kitaplıklarını Dağıt** (uzak Windows hata ayıklayıcı) | Dağıtım dizini özelliği ayarlanmışsa, bu geçerli platform için Visual C++ hata ayıklama çalışma zamanı kitaplıklarının ağ paylaşımına kopyalanıp kopyalanmayacağını belirtir. Varsayılan ayar evet'tir. |
  
## <a name="cc-folder-general-category"></a>C/C++ klasörü (genel kategori)  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**Hata ayıklama bilgi biçimi** ([/z7, / ZD, Zi, /zı](/cpp/build/reference/z7-zi-zi-debug-information-format))|Proje için oluşturulacak hata ayıklama bilgilerinin türünü belirtir.<br /><br /> Varsayılan seçenek (/zı) Düzenle ve devam et uyumlu formatında bir program veritabanı (PDB) oluşturur. Daha fazla bilgi için [/z7, / ZD, / zi, /zı (hata ayıklama bilgileri biçimi)](/cpp/build/reference/z7-zi-zi-debug-information-format).|  
  
## <a name="cc-folder-optimization-category"></a>C/C++ klasörü (iyileştirme kategorisi)  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**En iyi duruma getirme**|Derleyicinin ürettiği kodu en iyileştirip iyileştirmeyeceğini belirtir. İyileştirme yürütülen kodu değiştirir. İyileştirilmiş kod artık kaynak kodu, hata ayıklamayı zorlaştırır eşleşir.<br /><br /> Varsayılan seçenek (**devre dışı (/ 0d)**) en iyi duruma getirme bastırır. İyileştirme bastırılmış ile geliştirin ve kodunuzun ürün sürümünü oluşturduğunuzda açın.|  
  
## <a name="linker-folder-debugging-category"></a>Bağlayıcı klasörü (hata ayıklama kategorisi)  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**Hata ayıklama bilgileri üret** ([/DEBUG](/cpp/build/reference/debug-generate-debug-info))|Tarafından belirtilen biçimde olan hata ayıklama bilgilerini dahil etmesini söyler [/z7, / ZD, Zi veya /zı](/cpp/build/reference/z7-zi-zi-debug-information-format).|  
|**Program veritabanı dosyası oluştur** ([/PDB:name](/cpp/build/reference/pdb-use-program-database))|Program veritabanı (PDB) dosyasının adını bu kutuda belirtin. Hata ayıklama bilgi biçimi için zı ya da / seçmeniz gerekir.|  
|**Özel sembolleri sök** ([/PDBSTRIPPED:filename](/cpp/build/reference/pdbstripped-strip-private-symbols))|PDB dosyasında özel simgeler dahil etmek istemiyorsanız bu kutuya PDB dosyanın adını belirtin. / Debug, / z7, /Zd gibi bir PDB dosyası üretmek seçenekleri herhangi bir derleyici veya bağlayıcı ile program görüntüsünü oluşturduğunuzda bu seçenek ikinci bir PDB dosyası oluşturur. Veya/zi. Bu ikinci PDB dosyası, size gönderilen müşterilerinize istemezsiniz sembolleri atar. Daha fazla bilgi için [/pdbstrıpped (özel simgeleri Şerit)](/cpp/build/reference/pdbstripped-strip-private-symbols).|  
|**Eşlem dosyası oluştur** ([/MAP](/cpp/build/reference/map-generate-mapfile))|Bağlama sırasında bir eşleme dosyası oluşturulacak söyler. Varsayılan ayar Hayır Daha fazla bilgi için [Map (eşlem dosyası oluştur)](/cpp/build/reference/map-generate-mapfile).|  
|**Eşlem dosyası adı** ([/MAP:](/cpp/build/reference/map-generate-mapfile)*adı*)|Eşlem dosyası oluştur seçerseniz, bu kutuda harita dosyasını belirtebilirsiniz. Daha fazla bilgi için [Map (eşlem dosyası oluştur)](/cpp/build/reference/map-generate-mapfile).|  
|**Eşlem aktarımları** ([/MAPINFO:EXPORTS](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Eşleme dosyasında dışarı aktarılan işlevleri içerir. Varsayılan ayar Hayır Daha fazla bilgi için [mapınfo (eşlem dosyası bilgileri dahil)](/cpp/build/reference/mapinfo-include-information-in-mapfile).|  
|**Hatası ayıklanabilir bütünleşmiş kod** ([assemblydebug](/cpp/build/reference/mapinfo-include-information-in-mapfile))|Bağlayıcı ayarlarını belirler assemblydebug seçeneği. Olası değerler şunlardır:<br /><br /> -   **Debuggable özniteliği yayınlanmadı**.<br />-   **Çalışma zamanı iyileştirmeleri ve Takibi devre dışı bırak (/ ASSEMBLYDEBUG)**. Bu varsayılan ayardır,<br />-   **Hiçbir çalışma zamanı izleme ve iyileştirmeleri etkinleştir(/assemblydebug:DISABLE)**.<br />-   **\<Üstten veya proje varsayılanlarından devral >**.<br />-Daha fazla bilgi için [assemblydebug (DebuggableAttribute ekleme)](/cpp/build/reference/assemblydebug-add-debuggableattribute).|  
  
 Yapılandırma özellikleri klasörü (hata ayıklama kategorisi) bu ayarları Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings arabirimini kullanarak programlama yoluyla değiştirebilirsiniz. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.

## <a name="other-project-settings"></a>Diğer proje ayarları

Statik kitaplıklar ve DLL'ler gibi proje türlerinde hata ayıklamak için Visual Studio projenize doğru dosya bulamadı olması gerekir. Kaynak kodu kullanılabilir duruma geldiğinde ayrı projeler statik kitaplıklar ve DLL'ler daha kolay hata ayıklama yapmak için aynı çözüme ekleyebilirsiniz. Bu proje türleri oluşturma konusunda daha fazla bilgi için bkz: [oluşturma ve bir dinamik bağlantı kitaplığı (DLL) kullanarak](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp) ve [kullanarak bir statik kitaplık oluşturma](/cpp/windows/walkthrough-creating-and-using-a-static-library-cpp). Kullanılabilir kaynak kodu ile yeni bir Visual Studio projesi seçerek oluşturabilirsiniz **dosya** > **yeni** > **varolan koddan proje**.

Projenize dış DLL'lerin hata ayıklamak için bkz: [hata ayıklama DLL projelerinde](../debugger/debugging-dll-projects.md#vxtskdebuggingdllprojectsexternal). Gerekirse kendi DLL proje hata ayıklama ancak olmayan projeye erişimi çağıran uygulama için bkz. [DLL projesinde hata ayıklama](../debugger/how-to-debug-from-a-dll-project.md).
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)   
 [Hata ayıklayıcı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)   
 [Visual C++ proje oluşturma ve yönetme](/cpp/ide/creating-and-managing-visual-cpp-projects)   
 [/ ASSEMBLYDEBUG (DebuggableAttribute ekleme)](/cpp/build/reference/assemblydebug-add-debuggableattribute)   
 [Genel derleme komutları ve Özellikler makroları](/cpp/ide/common-macros-for-build-commands-and-properties)