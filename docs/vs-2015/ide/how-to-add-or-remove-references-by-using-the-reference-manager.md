---
title: "Nasıl yapılır: başvurular ekleme veya kaldırma başvuru Yöneticisi'ni kullanarak | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ReferenceManager
helpviewer_keywords:
- Visual C# projects, references
- references [Visual Studio], adding
- assemblies [Visual Studio], references
- Visual Basic projects, references
- project references, adding
- referencing components, adding references
- project references, removing
- referencing assemblies
- referencing components, removing references
- references [Visual Studio], removing
- referencing components, assemblies not listed
ms.assetid: 1aabb520-99b0-46c6-9368-21b4d84793eb
caps.latest.revision: 48
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 82e09b1d27c8ac7905fd0e6511381b97fcae2cd7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917563"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Nasıl Yapılır: Başvuru Yöneticisi'ni Kullanarak Başvuru Ekleme veya Kaldırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanabileceğiniz **başvuru Yöneticisi** veya başka bir şirketin geliştirdiği eklemek ve yönetmek için iletişim kutusu sizin Microsoft, bileşenine başvuruyor. Bir evrensel Windows uygulaması geliştiriyorsanız, projeniz otomatik olarak tüm doğru Windows SDK'sı DLL'lerin başvuruyor. Bir .NET uygulaması geliştiriyorsanız projeniz otomatik olarak mscorlib.dll başvuruyor. Bazı .NET API'ları el ile eklemek zorunda bileşenlerde sunulur. COM bileşenleri veya özel bileşenler başvuruları el ile eklenmesi gerekir.  
  
## <a name="adding-and-removing-a-reference"></a>Başvuru Ekleme ve Kaldırma  
  
#### <a name="to-add-a-reference"></a>Bir başvuru eklemek için  
  
1. İçinde **Çözüm Gezgini**başvurular düğümüne sağ tıklayın ve seçin **Başvuru Ekle**.  
  
2. Başvuruları ekleyin ve ardından belirtin **Tamam** düğmesi.  
  
   **Başvuru Yöneticisi** açılır ve kullanılabilir başvuruları gruba göre listeler. Aşağıdaki grupların hangilerinin görüneceğini proje türü belirler:  
  
-   Derlemeler; Çerçeve ve Uzantılar alt grupları ile.  
  
-   Çözüm; Projeler alt grubu ile.  
  
-   Windows; Çekirdek ve Uzantılar alt grupları ile. Windows SDK veya uzantı SDK'sındaki başvuruları kullanarak keşfedebilirsiniz **Nesne Tarayıcısı**.  
  
-   Gözat; En Son alt grubu ile.  
  
## <a name="assemblies-tab"></a>Derlemeler sekmesi  
 **Derlemeleri** sekmesi, başvuru için kullanılabilen tüm .NET Framework derlemelerini listeler. **Derlemeleri** GAC içindeki derlemeler çalışma zamanı ortamının bir parçası olduğu için sekmesinde herhangi bir derleme genel derleme önbelleğinden (GAC) listelenmiyorsa. GAC'de kayıtlı bir derlemeye başvuru içeren bir uygulamayı dağıtır ya da kopyalarsanız, derleme 'Yereli Kopyala' ayarına bakılmaksızın uygulama ile birlikte dağıtılmaz veya kopyalanmaz. Daha fazla bilgi için [proje başvuruları](http://go.microsoft.com/fwlink/?LinkId=238512).  
  
 EnvDTE ad alanlarının herhangi birine (EnvDTE, EnvDTE80, EnvDTE90, EnvDTE90a veya EnvDTE100) el ile bir başvuru eklediğinizde, Özellikler penceresinde başvurunun 'Birlikte Çalışma Türlerini Katıştır' özelliğini False olarak ayarlayın. Bu özelliğin True olarak ayarlanması, katıştırılamayan belirli EnvDTE özellikleri nedeniyle derleme sorunlarına yol açabilir.  
  
 Tüm masaüstü projeleri, mscorlib öğesine örtük bir başvuru içerir. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projeleri Microsoft.VisualBasic örtük bir başvuru içerir. İçinde [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], başvurular listesinden kaldırılsa bile tüm projeler System.Core, örtük bir başvuru içerir.  
  
 Bir proje türü Derlemeler'i desteklemiyorsa sekmesinde görünmez **başvuru Yöneticisi** iletişim kutusu.  
  
 Derlemeler sekmesi iki alt sekmeden oluşur:  
  
1. Çerçeve, hedef alınan Çerçeveyi oluşturan tüm derlemeleri listeler.  
  
   -   Projeniz hedeflenen Çerçevenin bir Profilini hedef aldığında, tanıtılan derlemeler Tam Çerçeve içindedir ve Çerçeve listesinde numaralandırılır. Tanıtılan derlemeler, projenin hedeflenen Çerçeve profilindeki mevcut derlemelerden ayırt edilmelerini sağlamak için gri renktedir. Örneğin, bir proje .NET Framework 4 İstemcisi'ni hedef alıyorsa, Çerçeve listesi .NET Framework 4 kaynaklı tanıtılan derlemeleri gösterir. Bir kullanıcı tanıtılan derleme eklediğinde, kullanıcının olduğu, sonra bildirim **başvuru Yöneticisi** iletişim kutusu kapatıldığında, proje .NET Framework 4'e yeniden hedefleneceği ve tanıtılan derlemenin eklenir.  
  
   -   Projeler için [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamaları hedeflenen içindeki derlemelerin tümüne başvurular içerir [!INCLUDE[net_win8_profile](../includes/net-win8-profile-md.md)] varsayılan olarak proje oluşturma. Yönetilen projelerde nde başvurular klasörünün altındaki bir salt okunur düğüm **Çözüm Gezgini** çerçeve'nin tümüne yönelik başvuruyu belirtir. Buna göre, Çerçeve sekmesi, Çerçeve kaynaklı derlemelerin hiçbirini numaralandırmaz ve bunun yerine şu iletiyi görüntüler: "Tüm Framework derlemelerine zaten başvurulmuş. Lütfen Nesne Tarayıcısı Framework'deki başvuruları araştırmak için kullanın." Masaüstü projeleri, çerçeve sekmesi, hedeflenen çerçeveden derlemeleri numaralandırır ve kullanıcı uygulamanın gerek duyduğu başvuruları eklemelidir.  
  
2. Uzantılar, harici bileşen ve denetim satıcılarının hedeflenen Çerçeveyi genişletmek için geliştirdiği tüm derlemeleri listeler. Kullanıcı uygulamasının amacına bağlı olarak, bu derlemelere gerek duyulabilir.  
  
   -   Uzantılar, aşağıdaki konumlarda kayıtlı derlemeleri numaralandırmak suretiyle doldurulur:  
  
       ```  
       32-bit machine:  
       HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
       HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
       64-bit machine:  
       HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
       HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
       And older versions of the [Target Framework Identifier]  
       ```  
  
        Örneğin, bir proje 32-bit makinede .NET Framework 4 hedefliyse, uzantıları \Microsoft altında kayıtlı derlemeleri numaralandıracaktır\\. NETFramework\v4.0\AssemblyFoldersEx\\, \Microsoft\\. NETFramework\v3.5\AssemblyFoldersEx\\, \Microsoft\\. NETFramework\v3.0\AssemblyFoldersEx\\ve \Microsoft\\. NETFramework\v2.0\AssemblyFoldersEx\\.  
  
   Listedeki bazı bileşenler, bağlı olarak gösterilmeyebilir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] projenizin sürüm. Bu, aşağıdaki koşullarda oluşabilir:  
  
-   .NET Framework'ün yeni bir sürümünü kullanan bileşen, .NET Framework'ün önceki bir sürümünü hedefleyen bir proje ile uyumlu değil.  
  
     Bir proje için hedef .NET Framework sürümünü değiştirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: .NET Framework sürümü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
-   Kullanan bileşen [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] hedefleyen bir projeyle uyumsuzdur [!INCLUDE[net_v45](../includes/net-v45-md.md)].  
  
     Bazı projeler hedef yeni bir uygulama oluşturduğunuzda [!INCLUDE[net_v45](../includes/net-v45-md.md)] varsayılan olarak. Daha fazla bilgi için [.NET Framework istemci profili](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).  
  
-   Bunun yapılması, derleme hatalarına neden olabilir, başka bir projenin çıktılarına dosya başvuruları aynı çözümde eklemekten kaçının. Bunun yerine, **projeleri** sekmesinde **Başvuru Ekle** projeden projeye başvuru oluşturmak için iletişim kutusu. Bu takım geliştirme projelerinizde oluşturduğunuz sınıf kitaplıklarının daha iyi yönetimine etkinleştirerek kolaylaştırır. Daha fazla bilgi için [bozuk başvuruları sorun giderme](../ide/troubleshooting-broken-references.md).  
  
-   > [!NOTE]
    >  Visual Studio 2015'te, bir projenin .NET Framework hedef sürümü sürüm 4.5 ise ve diğer projenin hedef sürümü sürüm 2, 3, 3.5 veya 4.0 ise bir proje başvurusu yerine dosya başvurusu oluşturulur.  
  
#### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Bir derlemeyi Başvuru Ekle iletişim kutusunda görüntülemek için  
  
- Taşıma veya derlemeyi aşağıdaki konumlardan birine kopyalayın:  
  
  - Geçerli proje dizini. (Kullanarak bu derlemeleri bulabilirsiniz **Gözat** sekmesini.)  
  
  - Aynı çözüm içindeki diğer proje dizinleri. (Kullanarak bu derlemeleri bulabilirsiniz **projeleri** sekmesini.)  
  
    \- veya -  
  
- Görüntülenecek derlemelerin konumunu belirten bir kayıt defteri anahtarını ayarlayın:  
  
   Bir 32-bit işletim sistemi için aşağıdaki kayıt defteri anahtarlarından birini ekleyin.  
  
  - [Arasına\\. NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@= "*AssemblyLocation*"  
  
  - [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@= "*AssemblyLocation*"  
  
    Bir 64-bit işletim sistemi için bir 32-bit kayıt defteri kovanında bulunan aşağıdaki kayıt defteri anahtarlarından birini ekleyin.  
  
  - [HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"  
  
  - [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"  
  
    *VersionMinimum* geçerli en düşük .NET Framework sürümü. Varsa *VersionMinimum* v3.0, AssemblyFoldersEx içinde belirtilen klasörler uygulamadığınız projeleri için .NET Framework 3.0 ve üstünü hedefleyen.  
  
    *AssemblyLocation* görünmesini istediğiniz derlemelerin dizinidir **Başvuru Ekle** iletişim kutusunda, örneğin, C:\MyAssemblies\\.  
  
    HKEY_LOCAL_MACHINE düğümü altında kayıt defteri anahtarı oluşturma sağlayan tüm kullanıcıların belirtilen konumda derlemelerde **Başvuru Ekle** iletişim kutusu. HKEY_CURRENT_USER düğümü altında kayıt defteri anahtarı oluşturma yalnızca geçerli kullanıcı ayarını etkiler.  
  
    Açık **Başvuru Ekle** iletişim kutusunu bir daha. Derlemeleri görünmelidir **.NET** sekmesi. Aksi takdirde, derlemelerin yer olduğundan emin olun belirtilen *AssemblyLocation* dizin, Visual Studio'yu yeniden başlatın ve yeniden deneyin.  
  
## <a name="com-tab"></a>COM sekmesi  
 COM sekmesi, başvuru için kullanılabilen tüm COM bileşenlerini listeler. Dahili bildirim içeren kayıtlı bir COM DLL öğesine başvuru eklemek isterseniz, önce DLL kaydını silin. Aksi takdirde, Visual Studio, derleme başvurusunu yerel bir DLL olarak değil, bir ActiveX Denetimi olarak ekler.  
  
 Bir proje türü COM'u desteklemiyorsa sekmesinde görünmez **başvuru Yöneticisi** iletişim kutusu.  
  
## <a name="solution-tab"></a>Çözüm sekmesi  
 Çözüm sekmesi, geçerli çözüm içindeki tüm uyumlu projeleri Projeler alt sekmesinde listeler.  
  
 Bir proje, farklı bir .NET Framework sürümünü hedef alan başka bir projeye başvuruda bulunabilir. Örneğin, hedefleyen bir proje oluşturabilirsiniz [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] ancak .NET Framework 2 için oluşturulmuş bir derlemeyi başvuruyor. Ancak, .NET Framework 2 projesi başvuramaz bir [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] proje. Daha fazla bilgi için [belirli bir .NET Framework sürümünü hedefleme](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
 Hedefleyen bir projeye [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] hedefleyen bir projeyle uyumsuzdur [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)].  
  
 İçinde [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], bir proje .NET Framework 4 hedefliyor ve başka bir proje daha önceki bir sürümünü hedefleyen bir proje başvurusu yerine dosya başvurusu oluşturulur.  
  
 Hedefleyen bir projeye [!INCLUDE[net_win8_profile](../includes/net-win8-profile-md.md)] .NET Framework geçme veya tam tersi hedefleyen bir projeye bir proje başvurusu eklenemiyor.  
  
## <a name="windows-tab"></a>Windows sekmesi  
 Windows sekmesi, Windows işletim sisteminin çalıştığı platformlara özgü tüm SDK'ları listeler.  
  
 Visual Studio'da bir WinMD dosyasını iki şekilde oluşturabilirsiniz:  
  
- **[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulaması yönetilen projeleri**: [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulaması projeleri WinMD ikili dosyalarını çıktı proje özelliklerini ayarlayarak &#124; Output Type = WinMD dosyası. WinMD dosya adı, içinde varolan tüm alan adlarının üst küme alan adı olmalıdır. Örneğin, bir proje A.B ve A.B.C ad alanlarından oluşuyorsa, çıktısı verilen WinMD için olası adlar A.winmd ve A.B.winmd olur. Bir kullanıcı bir Project Properties girerse &#124; derleme adı veya proje özellikleri &#124; projedeki ad alanları kümesinden kopuk Namespace değeri veya bir proje içinde hiçbir üst küme ad alanı, bir derleme uyarısı oluşturulur: 'A.winmd' olmayan bir Bu derleme için geçerli bir .winmd dosyası adı. Bir Windows Meta Veri dosyası içindeki tüm türler, dosya adının bir alt ad alanında mevcut olmalıdır. Dosya adının alt ad alanında mevcut olmayan türler çalışma zamanında bulunamaz. Bu derlemede, en küçük ortak ad alanı 'CSWSClassLibrary1'dir. Bir masaüstü Visual Basic veya Visual C# projesi yalnızca kullanılarak oluşturulmuş winmd'leri [!INCLUDE[win8](../includes/win8-md.md)] birinci Winmd'ler bilinir ve winmd oluşturamaz, SDK.  
  
- **[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulaması yerel projeleri**: yerel bir WinMD dosyası yalnızca meta verilerden oluşur. Uygulaması ayrı bir DLL dosyası içinde var olur. Bir üretebilir yerel ikili dosyaları Windows çalışma zamanı bileşeni proje şablonu seçilerek **yeni proje** iletişim kutusu ya da boş bir projeden başlatarak ve bir WinMD dosyası oluşturmak için proje özelliklerini değiştirme. Proje kopuk ad alanlarından oluşuyorsa, bir yapı hatası kullanıcıya ad alanlarını birleştirmesi veya MSMerge aracını çalıştırması gerektiğini söyler.  
  
  Windows sekmesi iki alt gruptan oluşur.  
  
### <a name="core-subgroup"></a>Çekirdek Alt Grubu  
 Çekirdek alt grubu, hedeflenen Windows sürümü için SDK içindeki tüm WinMD'leri (Windows Çalışma Zaman öğeleri için) listeler.  
  
 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] Uygulama projeleri içindeki winmd'lerin tümüne başvurular içerir [!INCLUDE[win8](../includes/win8-md.md)] SDK'sı varsayılan olarak proje oluşturma. Yönetilen projelerde nde başvurular klasörünün altındaki bir salt okunur düğüm **Çözüm Gezgini** nin tamamına yönelik başvuruyu belirtir [!INCLUDE[win8](../includes/win8-md.md)] SDK. Buna göre başvuru Yöneticisi'nde Çekirdek alt grubu derlemelerin hiçbirini numaralandırmaz [!INCLUDE[win8](../includes/win8-md.md)] SDK ve bunun yerine bir ileti görüntüler: "Windows SDK'sı zaten başvurulmuş. Lütfen Windows SDK'sındaki başvuruları araştırmak için Nesne Gezgini'ni kullanın.”  
  
 Masaüstü projelerinde, varsayılan olarak çekirdek alt grubu görünmez. Windows çalışma zamanı proje düğümü için kısayol menüsünü açarak ekleyebilirsiniz seçme **projeyi**, aşağıdaki kod parçacığını ekleyerek ve projeyi yeniden açarak (proje düğümünü seçin **projeyiyenidenyükle**). Çağırdığınızda **başvuru Yöneticisi** iletişim kutusu çekirdek alt grubu görünür.  
  
```  
<PropertyGroup>  
  <TargetPlatformVersion>8.0</TargetPlatformVersion>  
</PropertyGroup>  
```  
  
 Seçtiğinizden emin olun **Windows** bu alt grupta onay kutusu. Bundan sonra Windows Çalışma Zamanı öğelerini kullanabilmeniz gerekir. Bununla birlikte, Windows Çalışma Zamanı'nın IEnumerable gibi bazı standart sınıfları ve arabirimleri (Windows Çalışma Zamanı kitaplıklarının her yerinde kullanılan) tanımladığı System.Runtime öğesini de eklemek isteyeceksiniz. System.Runtime öğesini ekleme hakkında daha fazla bilgi için bkz: [yönetilen Masaüstü uygulamaları ve Windows çalışma zamanı](http://msdn.microsoft.com/library/windows/apps/jj856306.aspx#consuming_standard_windows_runtime_types).  
  
### <a name="extensions-subgroup"></a>Uzantılar Alt Grubu  
 Uzantılar, hedeflenen Windows platformunu genişleten kullanıcı SDK'larını listeler. Bu sekme görünür [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulaması projeleri yalnızca. Masaüstü projeleri yalnızca birinci taraf .winmd dosyalarını kullanabildiğinden, bu sekmeyi göstermezler.  
  
 SDK, Visual Studio'nun tek bir bileşen olarak kabul ettiği dosyalar topluluğudur. Uzantılar sekmesinde, proje için geçerli bir SDK'ları **başvuru Yöneticisi** iletişim kutusunun çağrıldığı tek varlıklar halinde listelenir. Bir projeye eklendiğinde, SDK içeriğinin tümü Visual Studio tarafından kullanılır; öyle ki kullanıcının IntelliSense, araç kutusu, tasarımcılar, Nesne Tarayıcısı, yapı, dağıtım, hata ayıklama ve paketleme içinde SDK içeriğinden faydalanmak için başka hiçbir işlem yapmasına gerek kalmaz. Uzantılar sekmesinde SDK'nızı görüntüleme hakkında daha fazla bilgi için bkz: [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md).  
  
> [!NOTE]
>  Proje başka bir SDK'ya bağımlı olan bir SDK'ya başvuruda bulunursa, kullanıcı ikinci SDK için el ile bir başvuru eklemediği sürece Visual Studio ikinci SDK'yı kullanmaz. Ne zaman bir kullanıcının seçtiği bir SDK'sı üzerinde **uzantıları** sekmesinde **başvuru Yöneticisi** iletişim kutusu yalnızca adı ve SDK sürüm aynı zamanda tüm SDK adı listeleyerek SDK bağımlılıklarını tanımlamak kullanıcı yardımcı olur Ayrıntılar bölmesinde bağımlılıkları. Kullanıcı bağımlılıkları fark etmez ve yalnızca SDK'yı eklerse, MSBuild kullanıcıdan bağımlılıkları eklemesini ister.  
  
 Bir proje türü desteklemiyorsa **uzantıları**, sekmesinde görünmez **başvuru Yöneticisi** iletişim kutusu.  
  
## <a name="browse-button"></a>Gözat düğmesi  
 Kullanabileceğiniz **Gözat** düğmesini dosya sistemindeki bir bileşen için göz atın.  
  
 Bir proje, farklı bir .NET Framework sürümünü hedef alan başka bir bileşene başvuruda bulunabilir. Örneğin, .NET Framework 2'yi hedefleyen bir bileşene başvuruda bulunan .NET Framework 4 İstemci Profili'ni hedef alan bir uygulama oluşturabilirsiniz. Daha fazla bilgi için [belirli bir .NET Framework sürümünü hedefleme](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
 Aynı çözümdeki başka bir projenin çıktılarına dosya başvuruları eklemekten kaçınmalısınız; bu taktik derleme hatalarına neden olabilir. Bunun yerine, **çözüm** sekmesinde **başvuru Yöneticisi** projeden projeye başvuru oluşturmak için iletişim kutusu. Bu taktik, projelerinizde oluşturduğunuz sınıf kitaplıklarının daha iyi yönetimine olanak tanıyarak takım geliştirmeyi kolaylaştırır. Daha fazla bilgi için [bozuk başvuruları sorun giderme](../ide/troubleshooting-broken-references.md).  
  
 Bir SDK'ye göz atamaz ve projenize ekleyemezsiniz. Yalnızca bir dosyaya (örneğin, bir derleme veya .winmd) göz atabilir ve bu dosyayı projenize ekleyebilirsiniz.  
  
 Bir Winmd'ye dosya başvurusu yaparken olan beklenen Düzen *FileName*.winmd, *FileName*, .dll ve *FileName*.pri dosyaları tüm yanı sıra yerleştirilmesidir. Aşağıdaki senaryolarda bir WinMD'ye başvuruda bulunursanız, proje çıkış dizinine eksik bir dosya kümesi kopyalanır ve sonuç olarak, derleme ve çalışma zamanı hataları meydana gelir.  
  
-   **Yerel bileşen**: yerel bir proje her kopuk ad alanları kümesi için tek bir WinMD ve uygulamayı içeren bir DLL oluşturur. WinMD'ler ayrı adlara sahip olur. MSBuild bu yerel bileşen dosyasına başvururken, benzemeyecek şekilde adlandırılmış WinMD'lerin tek bir bileşen oluşturduğunu algılamaz. Sonuç olarak, yalnızca aynı adlı *FileName*.dll ve *FileName*.winmd kopyalanır ve çalışma zamanı hataları oluşur. Bu sorunu geçici bir çözümle aşmak için bir Uzantı SDK oluşturun. Daha fazla bilgi için [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md).  
  
-   **Denetimleri kullanma**: en az bir XAML denetimi oluşan bir *FileName*.winmd, *FileName*.dll, *FileName*.pri, *XamlName* , .xaml ve bir *IMAGENAME*.jpg. Proje oluşturulduğunda, dosya başvurusu ile ilişkili kaynak dosyalar projenin çıkış dizinine kopyalanmaz ve yalnızca vermeyeceğiz *FileName*.winmd, *FileName*.dll ve *FileName*.pri kopyalanır. Bir yapı hatası kullanıcıya bildirmek için oturum açmış olan kaynakları *XamlName*.xaml ve *IMAGENAME*.jpg eksik. Başarılı olması için, kullanıcının bu kaynak dosyaları oluşturma ve hata ayıklama/çalışma zamanı için proje çıkış dizinine el ile kopyalaması gerekir. Bu sorunu geçici olarak çözmek için ya da bir uzantı SDK'sı içindeki adımları izleyerek oluşturun [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md) veya aşağıdaki özellik eklemek için proje dosyasını düzenleyin:  
  
    ```  
    <PropertyGroup>  
    <GenerateLibraryOutput>True</GenerateLibraryOutput>  
    </PropertyGroup>  
    ```  
  
    > [!NOTE]
    >  Özelliği eklerseniz, yapı daha yavaş çalışabilir.  
  
## <a name="recent"></a>En Son  
 Derlemeler, COM, Windows ve Gözat'ın her biri, bir En Son sekmesini destekler ve bu sekme projelere yakın zamanda eklenmiş bileşenlerin listesini numaralandırır.  
  
## <a name="search"></a>Ara  
 Arama çubuğuna **başvuru Yöneticisi** iletişim kutusu'nın, odakta olan sekme üzerinde çalışır. Örneğin, bir kullanıcı sırasında arama çubuğuna "Sistem" yazarsa **çözüm** sekme odağı, arama Çözüm "Sistem" içeren bir proje adından oluşmadığı sürece herhangi bir sonuç döndürmek olmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [NIB nasıl yapılır: başvurular ekleme veya kaldırma Başvuru Ekle iletişim kutusunu kullanarak](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)



