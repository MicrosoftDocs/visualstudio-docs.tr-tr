---
title: Proje ayarları C++ hata ayıklama yapılandırması | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
- FSharp
- VB
- CSharp
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
caps.latest.revision: 52
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 404bbc753b2729ad5ec7625fa01803b8a6bdf5c8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800802"
---
# <a name="project-settings-for-a-c-debug-configuration"></a>C++ Hata Ayıklama Yapılandırması Proje Ayarları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir C veya Visual C++ hata ayıklama yapılandırması proje ayarları değiştirebilirsiniz **özellik sayfaları** anlatıldığı gibi iletişim kutusu, [nasıl yapılır: ayarlama hata ayıklama ve yayın yapılandırmaları](../debugger/how-to-set-debug-and-release-configurations.md). Aşağıdaki tablolarda, hata ayıklayıcı ile ilgili ayarların nerede bulunacağı gösterilmektedir **özellik sayfaları** iletişim kutusu.  
  
> [!WARNING]
>  Hata ayıklama proje ayarları **yapılandırma özellikleri/hata ayıklama** kategori Windows Store uygulamaları ve C++ ile yazılmış bileşenler için farklıdır. Bkz: [(VB, C#, C++ ve XAML) bir hata ayıklama oturumunu başlatmada](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) Windows geliştirme Merkezi'nde.  
  
 Hangi hata ayıklayıcının kullanılacağını belirtin **başlatmak için hata ayıklayıcı** liste kutusu. Seçiminiz hangi özelliklerin görülebileceğini etkiler.  
  
 Her hata ayıklama özelliği ayarı otomatik olarak yazılır ve kaydedilen "kullanıcı başına" dosyaya (. vcxproj.user) çözümünüzün çözümünüz olduğunda.  
  
### <a name="configuration-properties-folder-debugging-category"></a>Yapılandırma özellikleri klasörü (hata ayıklama kategorisi)  
  
|**Ayarı**|**Açıklama**|  
|-----------------|---------------------|  
|**Başlatmak için hata ayıklayıcı**|Hata ayıklayıcının, aşağıdaki seçenekler ile Çalıştır belirtir:<br /><br /> -   **Yerel Windows hata ayıklayıcı**<br />-   **Uzak Windows hata ayıklayıcı**<br />-   **Web tarayıcı hata ayıklayıcısı**<br />-   **Web hizmeti hata ayıklayıcısı**|  
|**Komut** (yerel Windows hata ayıklayıcı)|Yerel bilgisayarda hata ayıklaması yaptığınız programı başlatma komutunu belirtir.|  
|**Uzak komut** (uzak Windows hata ayıklayıcı)|Uzak bilgisayardaki .exe yolu. Yalnızca uzak makinede girersiniz gibi yolu girin.|  
|**Komut bağımsız değişkenleri** (yerel Windows hata ayıklayıcısı ve uzak Windows hata ayıklayıcı)|-Daha önce belirtilen komut için bağımsız değişkenleri belirtir.<br /><br /> Bu kutuda aşağıdaki yönlendirme işleçlerini kullanabilirsiniz:<br /><br /> < `file`<br /> Dosyadan stdin okur.<br /><br /> > `file`<br /> Dosyaya STDOUT yazar.<br /><br /> >> `file`<br /> Dosyaya STDOUT ekler.<br /><br /> 2> `file`<br /> Stderr dosyasına yazar.<br /><br /> 2>> `file`<br /> Dosyaya stderr ekler.<br /><br /> 2> &1<br /> Stderr (2) çıktısını stdout (1) ile aynı konuma gönderir.<br /><br /> 1> &2<br /> STDOUT (1) çıktısını stderr (2) ile aynı konuma gönderir.<br /><br /> Çoğu durumda, bu işleçler yalnızca konsol uygulamaları için geçerlidir.|  
|**Çalışma dizini**|EXE dosyanızın bulunduğu proje dizinine göre ayıklanan programın çalışma dizini belirtir. Burayı boş bırakırsanız, çalışma dizini proje dizini bağlıdır. Uzaktan hata ayıklama için proje dizini uzak sunucu üzerinde olacaktır.|  
|**Ekleme** (yerel Windows hata ayıklayıcısı ve uzak Windows hata ayıklayıcı)|Başlatma veya uygulamasına belirtir. Varsayılan ayar Hayır|  
|**Uzak sunucu adı** (uzak Windows hata ayıklayıcı)|Bir uygulamada hata ayıklamak istediğiniz bilgisayarın (sizin dışında) adını belirtir.<br /><br /> RemoteMachine yapı makrosu bu özelliğin değerine ayarlanır; Daha fazla bilgi için [yapı komutları ve Özellikler makroları](http://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b).|  
|**Bağlantı** (uzak Windows hata ayıklayıcı)|Uzaktan hata ayıklama için standart ve kimlik doğrulamasız bağlantı türleri arasında geçiş yapmanıza izin verir. Bir uzak bilgisayar adı belirtin **uzak sunucu adı** kutusu. Bağlantı türleri aşağıdakileri kapsamaktadır:<br /><br /> -   **Windows kimlik doğrulaması ile uzaktan**<br />-   **Uzaktan kimlik doğrulaması olmayan (yalnızca yerel)**<br /><br /> **Not** uzaktan hata ayıklama kimlik doğrulamasısız uzak bilgisayarı güvenlik ihlallerine karşı savunmasız. Windows kimlik doğrulama modu daha güvenlidir.<br /><br /> Daha fazla bilgi için [uzaktan hata ayıklama Kurulumu](../debugger/remote-debugging.md).|  
|**HTTP URL** (Web hizmeti hata ayıklayıcısı ve Web tarayıcı hata ayıklayıcısı)|Hata ayıklaması yaptığınız projenin bulunduğu URL'yi belirtir.|  
|**Hata ayıklayıcı türü**|Kullanılacak hata ayıklayıcı türünü belirtir: **yalnızca yerel**, **yalnızca yönetilen**, **yalnızca GPU**, **karma**, **otomatik**(varsayılan) veya **betik**.<br /><br /> -   **Yalnızca yerel** yönetilmeyen C++ kodu içindir.<br />-   **Yalnızca yönetilen** ortak dil çalışma zamanı altında (yönetilen kod) çalışan kod içindir.<br />-   **Karma** hem yönetilen hem de yönetilmeyen kod için hata ayıklayıcıları çağırır.<br />-   **Otomatik** derleyici ve EXE bilgilerini temel alan bir hata ayıklayıcı türünü belirler.<br />-   **Betik** komut dosyaları için bir hata ayıklayıcı çağırır.<br />-   **Yalnızca GPU** bir GPU cihazında veya DirectX başvuru tarayıcısında çalışan C++ AMP kodu içindir. Bkz: [GPU kodunda hata ayıklama](../debugger/debugging-gpu-code.md).|  
|**Ortam** (yerel Windows hata ayıklayıcı)|Hata ayıklaması yaptığınız program için ortam değişkenlerini belirtir. Standart ortam değişkeni sözdizimini kullanın (örneğin, `PATH="%SystemRoot%\..."`). Bu değişkenler, sistem ortamını geçersiz kılar veya bağlı olarak, sistem ortamıyla birleştirilir **ortamı Birleştir** ayarı. Ayarlar sütununu tıklattığınızda, "Düzenle..." görünür. Ortam değişkenlerini düzenlemek için bu bağlantıyı tıklatın.|  
|**Ortam birleştirme** (yerel Windows hata ayıklayıcı)|Değişkenleri belirler belirtilen **ortam** kutusunda, işletim sistemi tarafından tanımlanan ortam ile birleştirilir. Varsayılan ayar evet'tir.|  
|**SQL hata ayıklama** (tüm ancak MPI Kümesi hata ayıklayıcısı)|Uygulamanızdan SQL yordamlarının hata ayıklamasını etkinleştirir, [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] uygulama. Varsayılan ayar Hayır|  
|**Hata ayıklama Hızlandırıcı türü** (yalnızca GPU hata ayıklama)|Hata ayıklama için kullanılacak GPU cihazını belirtir. GPU uyumlu cihazlar için cihaz sürücülerinin yüklenmesi ek seçenekler ekler. Varsayılan ayar "GPU - yazılım öykünücüsü." dır.|  
|**GPU varsayılan kesme noktası davranışı** (yalnızca GPU hata ayıklama)|Bir kesme noktası olayının SIMD eğriltme içindeki her bir iş parçacığı için oluşturup oluşturmadığını belirtir. Varsayılan ayar kesme noktası olayı eğriltme başına yalnızca bir kez başlatılmasıdır.|  
|**Amp varsayılan Hızlandırıcı** (yalnızca GPU hata ayıklama)|GPU kodunda hata ayıklama sırasında varsayılan AMP hızlandırıcıyı belirtir. Seçin **WARP Yazılım hızlandırıcı** soruna donanım veya sürücüden kodunuz yerine nedeni araştırmak için.|  
|**Dağıtım dizini** (uzak Windows hata ayıklayıcı)|Proje çıktısı başlatmadan önce kopyalanacağı burada olacaktır uzak bilgisayardaki yolunu belirtir. Yol, uzak bilgisayardaki bir ağ paylaşımı veya uzak bilgisayardaki bir klasöre bir yol olabilir. Varsayılan ayar boş proje çıkışının bir ağ paylaşımına kopyalanmadığı anlamına gelir. Dosyaların dağıtımını etkinleştirmek için de seçmeniz gerekir **Dağıt** Configuration Manager iletişim kutusundaki onay kutusu. Daha fazla bilgi için [nasıl yapılır: yapılandırmaları oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md).|  
|**Dağıtılacak ek dosyalar** (uzak Windows hata ayıklayıcı)|Dağıtım dizini özelliği ayarlanmışsa, bu dağıtım dizinine kopyalanacak ek dosyaların noktalı virgülle ayrılmış listesini budur. Varsayılan ayar boş, hiçbir ek dosyaları dağıtım dizinine kopyalanmadığı anlamına gelir. Dosyaların dağıtımını etkinleştirmek için de seçmeniz gerekir **Dağıt** Configuration Manager iletişim kutusundaki onay kutusu. Daha fazla bilgi için [nasıl yapılır: yapılandırmaları oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md).|  
|**Visual C++ hata ayıklama çalışma zamanı kitaplıklarını Dağıt** (uzak Windows hata ayıklayıcı)|Dağıtım dizini özelliği ayarlanmışsa, bu geçerli platform için Visual C++ hata ayıklama çalışma zamanı kitaplıklarının ağ paylaşımına kopyalanıp kopyalanmayacağını belirtir. Varsayılan ayar evet'tir.|  
  
### <a name="cc-folder-general-category"></a>C/C++ klasörü (genel kategori)  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**Hata ayıklama bilgi biçimi** ([/z7, / ZD, Zi, /zı](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8))|Proje için oluşturulacak hata ayıklama bilgilerinin türünü belirtir.<br /><br /> Varsayılan seçenek (/zı) Düzenle ve devam et uyumlu formatında bir program veritabanı (PDB) oluşturur. Daha fazla bilgi için [/z7, / ZD, / zi, /zı (hata ayıklama bilgileri biçimi)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8).|  
  
### <a name="cc-folder-optimization-category"></a>C/C++ klasörü (iyileştirme kategorisi)  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**En iyi duruma getirme**|Derleyicinin ürettiği kodu en iyileştirip iyileştirmeyeceğini belirtir. İyileştirme yürütülen kodu değiştirir. İyileştirilmiş kod artık kaynak kodu eşleşmiyor. Bu nedenle, hata ayıklama kolay değildir.<br /><br /> Varsayılan seçenek (**devre dışı (/ 0d**) en iyi duruma getirme bastırır. İyileştirme bastırılmış ile geliştirin ve kodunuzun ürün sürümünü oluşturduğunuzda açın.|  
  
### <a name="linker-folder-debugging-category"></a>Bağlayıcı klasörü (hata ayıklama kategorisi)  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|**Hata ayıklama bilgileri üret** ([/DEBUG](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103))|/ Z7, / ZD, Zi veya /zı tarafından belirlenen biçimde olan hata ayıklama bilgilerini dahil etmesini söyler.|  
|**Program veritabanı dosyası oluştur** ([/PDB:name](http://msdn.microsoft.com/library/d23db0ce-10cb-427a-bc60-d6b2a852723d))|Bu kutuya PDB dosyanın adını belirtin. Hata ayıklama bilgi biçimi için zı ya da / seçmeniz gerekir.|  
|**Özel sembolleri sök** ([/PDBSTRIPPED:filename](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55))|PDB dosyasında özel simgeler dahil etmek istemiyorsanız bu kutuya PDB dosyanın adını belirtin. / Debug, / z7, /Zd gibi bir PDB dosyası üretmek seçenekleri herhangi bir derleyici veya bağlayıcı ile program görüntüsünü oluşturduğunuzda bu seçenek ikinci program veritabanı (PDB) dosyası oluşturur. Veya/zi. Bu ikinci PDB dosyası, size gönderilen müşterilerinize istemezsiniz sembolleri atar. Daha fazla bilgi için [/pdbstrıpped (özel simgeleri)](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|  
|**Eşlem dosyası oluştur** ([/MAP](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63))|Bağlama sırasında bir eşleme dosyası oluşturulacak söyler. Varsayılan ayar Hayır Daha fazla bilgi için [Map (eşlem dosyası oluştur)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Eşlem dosyası adı** ([/MAP:](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63)*adı*)|Eşlem dosyası oluştur seçerseniz, bu kutuda harita dosyasını belirtebilirsiniz. Daha fazla bilgi için [Map (eşlem dosyası oluştur)](http://msdn.microsoft.com/library/9ccce53d-4e36-43da-87b0-7603ddfdea63).|  
|**Eşlem aktarımları** ([/MAPINFO:EXPORTS](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Eşleme dosyasında dışarı aktarılan işlevleri içerir. Varsayılan ayar Hayır Daha fazla bilgi için [mapınfo (eşlem dosyası bilgileri dahil)](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b).|  
|**Hatası ayıklanabilir bütünleşmiş kod** ([assemblydebug](http://msdn.microsoft.com/library/533d2bce-f9b7-4fea-ae1c-0b4864c9d10b))|Bağlayıcı ayarlarını belirler assemblydebug seçeneği. Olası değerler aşağıdaki gibidir:<br /><br /> -   **Debuggable özniteliği yayınlanmadı**.<br />-   **Çalışma zamanı iyileştirmeleri ve Takibi devre dışı bırak (/ ASSEMBLYDEBUG)**. Bu varsayılan ayardır,<br />-   **Hiçbir çalışma zamanı izleme ve iyileştirmeleri etkinleştir(/assemblydebug:DISABLE)**.<br />-   **\<Üstten veya proje varsayılanlarından devral >**.<br />-Daha fazla bilgi için [assemblydebug (DebuggableAttribute ekleme)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982).|  
  
 Yapılandırma özellikleri klasörü (hata ayıklama kategorisi) bu ayarları Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings arabirimini kullanarak programlama yoluyla değiştirebilirsiniz. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)   
 [Hata ayıklayıcı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)   
 [Visual C++ proje oluşturma ve yönetme](http://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047)   
 [/ ASSEMBLYDEBUG (DebuggableAttribute ekleme)](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)   
 [Genel Derleme Komutları ve Özellikler Makroları](http://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b)



