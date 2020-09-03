---
title: "Nasıl yapılır: başvuru Yöneticisi 'ni kullanarak başvuru ekleme veya kaldırma | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d0763f2cf86d94f96f6f9c907ee306c731994f22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852084"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Nasıl Yapılır: Başvuru Yöneticisi'ni Kullanarak Başvuru Ekleme veya Kaldırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sizin, Microsoft veya başka bir şirketinizin geliştirdiği bileşenlere başvurular eklemek ve bunları yönetmek için **başvuru Yöneticisi** iletişim kutusunu kullanabilirsiniz. Bir Evrensel Windows uygulaması geliştiriyorsanız, projeniz otomatik olarak doğru Windows SDK dll 'Lerine başvurur. Bir .NET uygulaması geliştiriyorsanız, projeniz otomatik olarak mscorlib.dll başvurur. Bazı .NET API 'Leri, el ile eklemeniz gereken bileşenlerde kullanıma sunulur. COM bileşenlerine veya özel bileşenlere yapılan başvuruların el ile eklenmesi gerekir.

## <a name="adding-and-removing-a-reference"></a>Başvuru Ekleme ve Kaldırma

#### <a name="to-add-a-reference"></a>Başvuru eklemek için

1. **Çözüm Gezgini**, Başvurular düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.

2. Eklenecek başvuruları belirtin ve sonra **Tamam** düğmesini seçin.

   **Başvuru Yöneticisi** açılır ve gruba göre kullanılabilir başvuruları listeler. Aşağıdaki grupların hangilerinin görüneceğini proje türü belirler:

- Derlemeler; Çerçeve ve Uzantılar alt grupları ile.

- Çözüm; Projeler alt grubu ile.

- Windows; Çekirdek ve Uzantılar alt grupları ile. **Nesne tarayıcısı**kullanarak Windows SDK veya uzantı SDK 'lerinde başvuruları inceleyebilirsiniz.

- Gözat; En Son alt grubu ile.

## <a name="assemblies-tab"></a>Derlemeler sekmesi
 **Derlemeler** sekmesi, başvuru için kullanılabilen tüm .NET Framework derlemeleri listeler. GAC içindeki derlemeler çalışma zamanı ortamının bir parçası olduğundan, **derlemeler** sekmesi genel derleme ÖNBELLEĞINDEN (GAC) herhangi bir derlemeyi listeetmez. GAC'de kayıtlı bir derlemeye başvuru içeren bir uygulamayı dağıtır ya da kopyalarsanız, derleme 'Yereli Kopyala' ayarına bakılmaksızın uygulama ile birlikte dağıtılmaz veya kopyalanmaz. Daha fazla bilgi için bkz. [Proje başvuruları](https://msdn.microsoft.com/library/ez524kew.aspx).

 EnvDTE ad alanlarının herhangi birine (EnvDTE, EnvDTE80, EnvDTE90, EnvDTE90a veya EnvDTE100) el ile bir başvuru eklediğinizde, Özellikler penceresinde başvurunun 'Birlikte Çalışma Türlerini Katıştır' özelliğini False olarak ayarlayın. Bu özelliğin True olarak ayarlanması, katıştırılamayan belirli EnvDTE özellikleri nedeniyle derleme sorunlarına yol açabilir.

 Tüm masaüstü projeleri, mscorlib öğesine örtük bir başvuru içerir. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projeler Microsoft. VisualBasic 'e örtük bir başvuru içerir. ' De [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] , tüm projeler, başvurular listesinden kaldırılsa bile, System. Core 'a örtük bir başvuru içerir.

 Bir proje türü derlemeleri desteklemiyorsa, sekme **başvuru Yöneticisi** iletişim kutusunda görünmez.

 Derlemeler sekmesi iki alt sekmeden oluşur:

1. Çerçeve, hedef alınan Çerçeveyi oluşturan tüm derlemeleri listeler.

   - Projeniz hedeflenen Çerçevenin bir Profilini hedef aldığında, tanıtılan derlemeler Tam Çerçeve içindedir ve Çerçeve listesinde numaralandırılır. Tanıtılan derlemeler, projenin hedeflenen Çerçeve profilindeki mevcut derlemelerden ayırt edilmelerini sağlamak için gri renktedir. Örneğin, bir proje .NET Framework 4 İstemcisi'ni hedef alıyorsa, Çerçeve listesi .NET Framework 4 kaynaklı tanıtılan derlemeleri gösterir. Kullanıcı tanıtılan bir derlemeyi eklediğinde, **başvuru Yöneticisi** iletişim kutusu kapatıldıktan sonra, proje .NET Framework 4 ' e yeniden hedeflenecek ve tanıtılan derleme eklenecek şekilde bildirilir.

   - Uygulamalar için projeler [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] , [!INCLUDE[net_win8_profile](../includes/net-win8-profile-md.md)] Proje oluşturma sırasında varsayılan olarak hedeflenen tüm derlemelere başvuru içerir. Yönetilen projelerde, **Çözüm Gezgini** ' deki başvurular klasörü altındaki salt okunurdur bir düğüm, tüm Framework başvurusunu gösterir. Buna göre, Çerçeve sekmesi, Çerçeve kaynaklı derlemelerin hiçbirini numaralandırmaz ve bunun yerine şu iletiyi görüntüler: "Tüm Framework derlemelerine zaten başvurulmuş. Lütfen Framework içindeki başvuruları araştırmak için Nesne Tarayıcısı kullanın. " Masaüstü projeleri için, Framework sekmesi hedeflenen çerçeveden derlemeleri sıralar ve kullanıcının, uygulamanın gerektirdiği başvuruları eklemesi gerekir.

2. Uzantılar, harici bileşen ve denetim satıcılarının hedeflenen Çerçeveyi genişletmek için geliştirdiği tüm derlemeleri listeler. Kullanıcı uygulamasının amacına bağlı olarak, bu derlemelere gerek duyulabilir.

   - Uzantılar, aşağıdaki konumlarda kayıtlı derlemeleri numaralandırmak suretiyle doldurulur:

       ```
       32-bit machine:
       HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
       HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
       64-bit machine:
       HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
       HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
       And older versions of the [Target Framework Identifier]
       ```

        Örneğin, bir proje 32 bitlik bir makinede .NET Framework 4 ' ü hedefliyorsa, uzantılar \Microsoft altında kayıtlı derlemeleri numaralandırır \\ . NETFramework\v4.0\AssemblyFoldersEx \\ , \Microsoft \\ . NETFramework\v3.5\AssemblyFoldersEx \\ , \Microsoft \\ . Netframework\v3,\assemblyfoldersex \\ ve \Microsoft \\ . NETFramework\v2.0\AssemblyFoldersEx \\ .

   Listedeki bazı bileşenler, projenizin sürümüne bağlı olarak gösterilmeyebilir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Bu durum aşağıdaki koşullarda oluşabilir:

- .NET Framework son sürümünü kullanan bir bileşen, .NET Framework önceki bir sürümünü hedefleyen bir proje ile uyumsuzdur.

     Bir proje için hedef .NET Framework sürümünün nasıl değiştirileceği hakkında bilgi için bkz. [nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

- Kullanan bir bileşen, ' i [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] hedefleyen bir projeyle uyumlu değildir [!INCLUDE[net_v45](../includes/net-v45-md.md)] .

     Yeni bir uygulama oluşturduğunuzda, bazı projeler varsayılan olarak öğesini hedefler [!INCLUDE[net_v45](../includes/net-v45-md.md)] . Daha fazla bilgi için bkz. [.NET Framework Istemci profili](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).

- Aynı çözümdeki başka bir projenin çıktılarına dosya başvuruları eklemekten kaçının, çünkü bunu yapmak derleme hatalarına neden olabilir. Bunun yerine, projeden projeye başvurular oluşturmak için **Başvuru Ekle** Iletişim kutusunun **Projeler** sekmesini kullanın. Bu, projelerinizde oluşturduğunuz sınıf kitaplıklarının daha iyi yönetimini etkinleştirerek takım geliştirmeyi kolaylaştırır. Daha fazla bilgi için bkz. [Hatalı başvuruların sorunlarını giderme](../ide/troubleshooting-broken-references.md).

- > [!NOTE]
    > Visual Studio 2015 ' de, bir projenin .NET Framework hedef sürümü 4,5 ise ve diğer projenin hedef sürümü sürüm 2, 3, 3,5 veya 4,0 ise, proje başvurusu yerine bir dosya başvurusu oluşturulur.

#### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Başvuru Ekle iletişim kutusunda bir derlemeyi göstermek için

- Derlemeyi aşağıdaki konumlardan birine taşıyın veya kopyalayın:

  - Geçerli proje dizini. (Bu derlemeleri, **tarayıcı** sekmesini kullanarak bulabilirsiniz.)

  - Aynı çözümdeki diğer proje dizinleri. ( **Projeler** sekmesini kullanarak bu derlemeleri bulabilirsiniz.)

    \- veya

- Görüntülenecek derlemelerin konumunu belirten bir kayıt defteri anahtarı ayarlayın:

   32 bitlik bir işletim sistemi için aşağıdaki kayıt defteri anahtarlarından birini ekleyin.

  - [HKEY_CURRENT_USER \SOFTWARE\Microsoft \\ . NETFramework \\ *VersionMinimum*\AssemblyFoldersEx\MyAssemblies] @ = "*AssemblyLocation*"

  - [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . NETFramework \\ *VersionMinimum*\AssemblyFoldersEx\MyAssemblies] @ = "*AssemblyLocation*"

    64 bitlik bir işletim sistemi için, 32 bit kayıt defteri kovanında aşağıdaki kayıt defteri anahtarlarından birini ekleyin.

  - [HKEY_CURRENT_USER \SOFTWARE\Wow6432Node\Microsoft \\ . NETFramework \\ *VersionMinimum*\AssemblyFoldersEx\MyAssemblies] @ = "*AssemblyLocation*"

  - [HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft \\ . NETFramework \\ *VersionMinimum*\AssemblyFoldersEx\MyAssemblies] @ = "*AssemblyLocation*"

    *VersionMinimum* , uygulanan en düşük .NET Framework sürümüdür. *VersionMinimum* değeri v 3.0 Ise, AssemblyFoldersEx içinde belirtilen klasörler, .NET Framework 3,0 ve üstünü hedefleyen projeler için geçerlidir.

    *AssemblyLocation* , **Başvuru Ekle** iletişim kutusunda görünmesini istediğiniz derlemelerin dizinidir, örneğin, C:\MyAssemblies \\ .

    HKEY_LOCAL_MACHINE düğümü altında kayıt defteri anahtarı oluşturmak, tüm kullanıcıların **Başvuru Ekle** iletişim kutusunda belirtilen konumdaki derlemeleri görmesini sağlar. HKEY_CURRENT_USER düğümü altında kayıt defteri anahtarı oluşturmak yalnızca geçerli kullanıcının ayarını etkiler.

    **Başvuru Ekle** iletişim kutusunu tekrar açın. Derlemeler **.net** sekmesinde görünmelidir. Aksi takdirde, derlemelerin belirtilen *AssemblyLocation* dizininde bulunduğundan emin olun, Visual Studio 'yu yeniden başlatın ve yeniden deneyin.

## <a name="com-tab"></a>COM sekmesi
 COM sekmesi, başvuru için kullanılabilen tüm COM bileşenlerini listeler. Dahili bildirim içeren kayıtlı bir COM DLL öğesine başvuru eklemek isterseniz, önce DLL kaydını silin. Aksi takdirde, Visual Studio, derleme başvurusunu yerel bir DLL olarak değil, bir ActiveX Denetimi olarak ekler.

 Bir proje türü COM 'u desteklemiyorsa, sekme **başvuru Yöneticisi** iletişim kutusunda görünmez.

## <a name="solution-tab"></a>Çözüm sekmesi
 Çözüm sekmesi, geçerli çözüm içindeki tüm uyumlu projeleri Projeler alt sekmesinde listeler.

 Bir proje, farklı bir .NET Framework sürümünü hedef alan başka bir projeye başvuruda bulunabilir. Örneğin, [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] .NET Framework 2 için oluşturulmuş bir derlemeye başvuran, ancak hedefleyen bir proje oluşturabilirsiniz. Ancak, .NET Framework 2 projesi bir [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] projeye başvuramaz. Daha fazla bilgi için bkz. [belirli bir .NET Framework sürümünü hedefleme](../ide/targeting-a-specific-dotnet-framework-version.md).

 ' İ hedefleyen bir proje [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] , öğesini hedefleyen bir projeyle uyumsuzdur [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] .

 ' De [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] , bir proje .NET Framework 4 ' ü hedefliyorsa ve başka bir proje daha önceki bir sürümü hedefliyorsa, proje başvurusu yerine bir dosya başvurusu oluşturulur.

 ' İ hedefleyen bir proje, .NET Framework bir projeye [!INCLUDE[net_win8_profile](../includes/net-win8-profile-md.md)] başvuru ekleyemez ve tam tersi de geçerlidir.

## <a name="windows-tab"></a>Windows sekmesi
 Windows sekmesi, Windows işletim sisteminin çalıştığı platformlara özgü tüm SDK'ları listeler.

 Visual Studio'da bir WinMD dosyasını iki şekilde oluşturabilirsiniz:

- ** [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulama tarafından yönetilen projeler**: [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulama projeleri, proje özelliklerini &#124; çıktı türü = winmd dosyası ayarlayarak winmd ikililerini çıktısını alabilir. WinMD dosya adı, içinde varolan tüm alan adlarının üst küme alan adı olmalıdır. Örneğin, bir proje A.B ve A.B.C ad alanlarından oluşuyorsa, çıktısı verilen WinMD için olası adlar A.winmd ve A.B.winmd olur. Bir Kullanıcı, projedeki ad alanları kümesinden kopuk olan veya bir proje içinde bir üst küme ad alanı olmayan &#124; derleme adı veya proje özellikleri &#124; ad alanı değeri girerse, bir derleme uyarısı oluşturulur: ' A. winmd ' Bu derleme için geçerli bir. winmd dosya adı değil. Bir Windows Meta Veri dosyası içindeki tüm türler, dosya adının bir alt ad alanında mevcut olmalıdır. Dosya adının alt ad alanında mevcut olmayan türler çalışma zamanında bulunamaz. Bu derlemede, en küçük ortak ad alanı 'CSWSClassLibrary1'dir. Masaüstü Visual Basic veya Visual C# projesi yalnızca [!INCLUDE[win8](../includes/win8-md.md)] birinci taraf wınmds olarak bilinen SDK 'lar kullanılarak oluşturulan Wınmds 'yi kullanabilir ve WinMDs oluşturmazlar.

- ** [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulama yerel projeleri**: yerel bir WinMD dosyası yalnızca meta verilerden oluşur. Uygulaması ayrı bir DLL dosyası içinde var olur. **Yeni proje** iletişim kutusunda Windows çalışma zamanı bileşen proje şablonunu seçerek veya boş bir projeden başlayıp ve proje özelliklerini bir WinMD dosyası oluşturacak şekilde değiştirerek, yerel ikili dosyalar üretebilir. Proje kopuk ad alanlarından oluşuyorsa, bir yapı hatası kullanıcıya ad alanlarını birleştirmesi veya MSMerge aracını çalıştırması gerektiğini söyler.

  Windows sekmesi iki alt gruptan oluşur.

### <a name="core-subgroup"></a>Çekirdek Alt Grubu
 Çekirdek alt grubu, hedeflenen Windows sürümü için SDK içindeki tüm WinMD'leri (Windows Çalışma Zaman öğeleri için) listeler.

 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulama projeleri, [!INCLUDE[win8](../includes/win8-md.md)] proje oluştururken varsayılan olarak SDK 'daki tüm Wınmds başvuruları içerir. Yönetilen projelerde, **Çözüm Gezgini** ' deki başvurular klasörü altındaki salt okunurdur bir düğüm, tüm SDK 'nın başvurusunu gösterir [!INCLUDE[win8](../includes/win8-md.md)] . Buna uygun olarak, başvuru yöneticisindeki çekirdek alt grup, SDK 'daki derlemelerin hiçbirini numaralandırmaz [!INCLUDE[win8](../includes/win8-md.md)] ve bunun yerine bir ileti görüntüler: "Windows SDK zaten Başvurulmuş. Lütfen Windows SDK'sındaki başvuruları araştırmak için Nesne Gezgini'ni kullanın.”

 Masaüstü projelerinde, varsayılan olarak çekirdek alt grubu görünmez. Proje düğümü için kısayol menüsünü açıp, **Projeyi Kaldır**' ı seçip, aşağıdaki kod parçacığını ekleyerek ve projeyi yeniden açarak Windows çalışma zamanı ekleyebilirsiniz (proje düğümünde projeyi **yeniden yükle**' yi seçin). **Başvuru Yöneticisi** iletişim kutusunu çağırdığınızda, çekirdek alt grubu görünür.

```
<PropertyGroup>
  <TargetPlatformVersion>8.0</TargetPlatformVersion>
</PropertyGroup>
```

 Bu alt grup üzerinde **Windows** onay kutusunu seçtiğinizden emin olun. Bundan sonra Windows Çalışma Zamanı öğelerini kullanabilmeniz gerekir. Bununla birlikte, Windows Çalışma Zamanı'nın IEnumerable gibi bazı standart sınıfları ve arabirimleri (Windows Çalışma Zamanı kitaplıklarının her yerinde kullanılan) tanımladığı System.Runtime öğesini de eklemek isteyeceksiniz. System. Runtime ekleme hakkında daha fazla bilgi için bkz. [yönetilen masaüstü uygulamaları ve Windows çalışma zamanı](https://msdn.microsoft.com/library/windows/apps/jj856306.aspx#consuming_standard_windows_runtime_types).

### <a name="extensions-subgroup"></a>Uzantılar Alt Grubu
 Uzantılar, hedeflenen Windows platformunu genişleten kullanıcı SDK'larını listeler. Bu sekme [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] yalnızca uygulama projeleri için görüntülenir. Masaüstü projeleri yalnızca birinci taraf .winmd dosyalarını kullanabildiğinden, bu sekmeyi göstermezler.

 SDK, Visual Studio'nun tek bir bileşen olarak kabul ettiği dosyalar topluluğudur. Uzantılar sekmesinde, **başvuru Yöneticisi** iletişim kutusunun çağrıldığı proje Için uygulanan SDK 'lar tek girdi olarak listelenir. Bir projeye eklendiğinde, SDK içeriğinin tümü Visual Studio tarafından kullanılır; öyle ki kullanıcının IntelliSense, araç kutusu, tasarımcılar, Nesne Tarayıcısı, yapı, dağıtım, hata ayıklama ve paketleme içinde SDK içeriğinden faydalanmak için başka hiçbir işlem yapmasına gerek kalmaz. SDK 'larınızı Uzantılar sekmesinde görüntüleme hakkında daha fazla bilgi için bkz. [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md).

> [!NOTE]
> Proje başka bir SDK'ya bağımlı olan bir SDK'ya başvuruda bulunursa, kullanıcı ikinci SDK için el ile bir başvuru eklemediği sürece Visual Studio ikinci SDK'yı kullanmaz. Bir Kullanıcı **Uzantılar** SEKMESINDE bir SDK seçtiğinde, **başvuru Yöneticisi** iletişim kutusu kullanıcının SDK 'nın adını ve sürümünü değil ayrıntı bölmesinde SDK BAĞıMLıLıKLARıNıN adını değil, SDK bağımlılıklarını belirlemesine yardımcı olur. Kullanıcı bağımlılıkları fark etmez ve yalnızca SDK'yı eklerse, MSBuild kullanıcıdan bağımlılıkları eklemesini ister.

 Bir proje türü **uzantıları**desteklemiyorsa, sekme **başvuru Yöneticisi** iletişim kutusunda görünmez.

## <a name="browse-button"></a>Gözat düğmesi
 Dosya sistemindeki bir bileşene gitmek için, **Araştır** düğmesini kullanabilirsiniz.

 Bir proje, farklı bir .NET Framework sürümünü hedef alan başka bir bileşene başvuruda bulunabilir. Örneğin, .NET Framework 2'yi hedefleyen bir bileşene başvuruda bulunan .NET Framework 4 İstemci Profili'ni hedef alan bir uygulama oluşturabilirsiniz. Daha fazla bilgi için bkz. [belirli bir .NET Framework sürümünü hedefleme](../ide/targeting-a-specific-dotnet-framework-version.md).

 Aynı çözümdeki başka bir projenin çıktılarına dosya başvuruları eklemekten kaçınmalısınız; bu taktik derleme hatalarına neden olabilir. Bunun yerine, projeden projeye başvurular oluşturmak için **başvuru Yöneticisi** Iletişim kutusunun **çözüm** sekmesini kullanın. Bu taktik, projelerinizde oluşturduğunuz sınıf kitaplıklarının daha iyi yönetimine olanak tanıyarak takım geliştirmeyi kolaylaştırır. Daha fazla bilgi için bkz. [Hatalı başvuruların sorunlarını giderme](../ide/troubleshooting-broken-references.md).

 Bir SDK'ye göz atamaz ve projenize ekleyemezsiniz. Yalnızca bir dosyaya (örneğin, bir derleme veya .winmd) göz atabilir ve bu dosyayı projenize ekleyebilirsiniz.

 Bir WinMD 'ye dosya başvurusu yaparken, beklenen Düzen *filename*. winmd, *filename*. dll ve *filename*. pri dosyalarının tümünün birbirlerine yerleştirilme halidir. Aşağıdaki senaryolarda bir WinMD'ye başvuruda bulunursanız, proje çıkış dizinine eksik bir dosya kümesi kopyalanır ve sonuç olarak, derleme ve çalışma zamanı hataları meydana gelir.

- **Yerel bileşen**: yerel bir proje, her ayrık ad alanı kümesi ve uygulamadan oluşan bir dll Için bir WinMD oluşturur. WinMD'ler ayrı adlara sahip olur. MSBuild bu yerel bileşen dosyasına başvururken, benzemeyecek şekilde adlandırılmış WinMD'lerin tek bir bileşen oluşturduğunu algılamaz. Sonuç olarak, yalnızca aynı *filename*. dll ve *filename*. winmd adlı bir ad gönderilir ve çalışma zamanı hataları oluşur. Bu sorunu geçici bir çözümle aşmak için bir Uzantı SDK oluşturun. Daha fazla bilgi için bkz. [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md).

- **Denetimleri**kullanma: en azından bir XAML denetimi *dosya adı*. winmd, *filename*. dll, *filename*. pri, *XamlName*. xaml ve bir *ImageName*. jpg bilgisinden oluşur. Proje oluşturulduğunda, dosya başvurusuyla ilişkili kaynak dosyaları projenin çıkış dizinine kopyalanmaz ve yalnızca *filename*. winmd, *filename*. dll ve *filename*. pri kopyalanır. Kullanıcıya *XamlName*. xaml ve *ImageName*. jpg kaynaklarının eksik olduğunu bildirmek için bir yapı hatası kaydedilir. Başarılı olması için, kullanıcının bu kaynak dosyaları oluşturma ve hata ayıklama/çalışma zamanı için proje çıkış dizinine el ile kopyalaması gerekir. Bu sorunu geçici olarak çözmek için, [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md) veya proje dosyasını düzenleme bölümündeki adımları Izleyerek bir uzantı SDK 'sı oluşturun ve aşağıdaki özelliği ekleyin:

    ```
    <PropertyGroup>
    <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Özelliği eklerseniz, yapı daha yavaş çalışabilir.

## <a name="recent"></a>En Son
 Derlemeler, COM, Windows ve Gözat'ın her biri, bir En Son sekmesini destekler ve bu sekme projelere yakın zamanda eklenmiş bileşenlerin listesini numaralandırır.

## <a name="search"></a>Arayın
 **Başvuru Yöneticisi** iletişim kutusundaki arama çubuğu, odağa sahip olan sekmenin üzerinde çalışır. Örneğin, **çözüm** sekmesi odağa karşın bir Kullanıcı arama çubuğuna "sistem" yazdığında, çözüm "sistem" içeren bir proje adından oluşmadığı sürece arama hiçbir sonuç döndürmez.

## <a name="see-also"></a>Ayrıca Bkz.
 Nib nasıl yapılır: [bir projedeki başvuruları yöneten](../ide/managing-references-in-a-project.md) [Başvuru Ekle Iletişim kutusunu kullanarak başvuru ekleme veya kaldırma](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
