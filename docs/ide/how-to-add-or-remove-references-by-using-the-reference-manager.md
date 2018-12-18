---
title: Başvuru Yöneticisi'nde başvurular ekleme
ms.date: 04/11/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ReferenceManager
helpviewer_keywords:
- C# projects, references
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3668b5e4275071513deb31e2e479adcd91d11589
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839277"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Nasıl yapılır: ekleme veya başvuru Yöneticisi'ni kullanarak başvuruları kaldırma

Kullanabileceğiniz **başvuru Yöneticisi** veya başka bir şirketin geliştirdiği eklemek ve yönetmek için iletişim kutusu sizin Microsoft, bileşenine başvuruyor. Bir evrensel Windows uygulaması geliştiriyorsanız, projeniz otomatik olarak tüm doğru Windows SDK'sı DLL'lerin başvuruyor. Bir .NET uygulaması geliştiriyorsanız projeniz otomatik olarak başvuruda *mscorlib.dll*. Bazı .NET API'ları el ile eklemek zorunda bileşenlerde sunulur. COM bileşenleri veya özel bileşenler başvuruları el ile eklenmesi gerekir.

## <a name="reference-manager-dialog-box"></a>Başvuru Yöneticisi iletişim kutusu

**Başvuru Yöneticisi** iletişim kutusunda, sol taraftaki proje türüne bağlı olarak farklı kategorileri gösterilir:

- **Derlemeleri**, ile **Framework** ve **uzantıları** alt gruplar.

- **COM**, başvuru için kullanılabilen tüm COM bileşenlerini listeler.

- **Çözüm**, ile **projeleri** alt.

- **Windows**, ile **çekirdek** ve **uzantıları** alt gruplar. Windows SDK veya uzantı SDK'sındaki başvuruları kullanarak keşfedebilirsiniz **Nesne Tarayıcısı**.

- **Gözat**, ile **son** alt.

## <a name="add-and-remove-a-reference"></a>Bir başvuru ekleyip

### <a name="to-add-a-reference"></a>Başvuru eklemek için

1. İçinde **Çözüm Gezgini**, sağ **başvuruları** veya **bağımlılıkları** düğüm ve **Başvuru Ekle**. Ayrıca proje düğümüne sağ tıklayın ve seçin **Ekle** > **başvuru**.

   **Başvuru Yöneticisi** açılır ve kullanılabilir başvuruları gruba göre listeler.

2. Başvuruları ekleyin ve ardından belirtin **Tamam**.

## <a name="assemblies-tab"></a>Derlemeler sekmesi

**Derlemeleri** sekmesi, başvuru için kullanılabilen tüm .NET Framework derlemelerini listeler. **Derlemeleri** GAC içindeki derlemeler çalışma zamanı ortamının bir parçası olduğu için sekmesinde herhangi bir derleme genel derleme önbelleğinden (GAC) listelenmiyorsa. Dağıtmak veya GAC'ye kayıtlı bir derlemeye bir başvuru içeren bir uygulama kopyalarsanız, derleme olmaz dağıtılacağını veya bakılmaksızın uygulama ile birlikte kopyalanan **Yereli Kopyala** ayarı. Daha fazla bilgi için [bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md).

Başvuru EnvDTE ad alanlarının herhangi birine el ile eklerseniz (<xref:EnvDTE>, <xref:EnvDTE80>, <xref:EnvDTE90>, <xref:EnvDTE90a>, veya <xref:EnvDTE100>) ayarlayın **birlikte çalışma türlerini katıştır** başvuruözelliği**False** içinde **özellikleri** penceresi. Bu özelliği ayarlamak **True** neden sorunları katıştırılamayan belirli EnvDTE özellikleri nedeniyle oluşturabilirsiniz.

Tüm masaüstü projeleri için örtük bir başvuru içeren **mscorlib**. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projeleri örtük bir başvuru içeren <xref:Microsoft.VisualBasic>. Tüm projeleri örtük bir başvuru içeren **System.Core**, başvurular listesinden kaldırılsa bile.

Bir proje türü Derlemeler'i desteklemiyorsa sekmesinde görünmez **başvuru Yöneticisi** iletişim kutusu.

**Derlemeleri** sekmesi iki alt sekmeden oluşur:

1. **Framework** hedef alınan çerçeveyi oluşturan tüm derlemeleri listeler.

    Projeleri Windows 8.x Store uygulamaları için hedeflenmiş içindeki derlemelerin tümüne başvurular içerir [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] varsayılan olarak proje oluşturma. Yönetilen projelerde altındaki bir salt okunur düğüm **başvuruları** klasöründe **Çözüm Gezgini** çerçeve'nin tümüne yönelik başvuruyu belirtir. Buna **Framework** sekmesini çerçeveden derlemelerin hiçbirini listeleme yüklemeyecekseniz ve bunun yerine şu iletiyi görüntüler: "tüm Framework derlemelerine zaten başvurulmuş. Lütfen Nesne Tarayıcısı Framework'deki başvuruları araştırmak için kullanın." Masaüstü projeleri için **Framework** sekmesini hedeflenen çerçeveden derlemeleri numaralandırır ve kullanıcı uygulamanın gerek duyduğu başvuruları eklemelidir.

2. **Uzantıları** bileşen ve denetim dış satıcılarının hedeflenen çerçeveyi genişletmek için geliştirilmiştir tüm derlemeleri listeler. Kullanıcı uygulamasının amacına bağlı olarak, bu derlemelere gerek duyulabilir.

   **Uzantıları** aşağıdaki konumlarda kayıtlı derlemeleri numaralandırmak suretiyle doldurulur:

   32-bit makinedeki:
   - `HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   64-bit makinedeki:
   - `HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   Ve önceki sürümleri [hedef çerçeve tanımlayıcısı]

   Örneğin, bir proje 32-bit makinede .NET Framework 4 hedefliyse **uzantıları** altında kayıtlı derlemeleri numaralandıracaktır *\Microsoft\.NETFramework\v4.0\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.5\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.0\AssemblyFoldersEx*, ve  *\Microsoft\.NETFramework\v2.0\AssemblyFoldersEx*.

Listedeki bazı bileşenler, projeniz .NET Framework sürümüne bağlı olarak gösterilmeyebilir. Bu, aşağıdaki koşullarda oluşabilir:

- .NET Framework'ün yeni bir sürümünü kullanan bileşen, .NET Framework'ün önceki bir sürümünü hedefleyen bir proje ile uyumlu değil.

    Bir proje için hedef .NET Framework sürümünü değiştirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: .NET Framework sürümü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

- Kullanan bileşen [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] hedefleyen bir projeyle uyumsuzdur [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)].

    Bazı projeler hedef yeni bir uygulama oluşturduğunuzda [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] varsayılan olarak.

Bunun yapılması, derleme hatalarına neden olabilir, başka bir projenin çıktılarına dosya başvuruları aynı çözümde eklemekten kaçının. Bunun yerine, **projeleri** sekmesinde **Başvuru Ekle** projeden projeye başvuru oluşturmak için iletişim kutusu. Bu takım geliştirme projelerinizde oluşturduğunuz sınıf kitaplıklarının daha iyi yönetimine etkinleştirerek kolaylaştırır. Daha fazla bilgi için [başvuruları bozuk sorun giderme](../ide/troubleshooting-broken-references.md).

> [!NOTE]
> Visual Studio 2015 veya sonraki sürümlerde, bir projenin .NET Framework hedef sürümü 4.5 veya sonraki bir sürümü, ve diğer projenin hedef sürümü, sürüm 2, 3, 3.5 veya 4.0 ise bir proje başvurusu yerine dosya başvurusu oluşturulur.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Bir derlemeyi Başvuru Ekle iletişim kutusunda görüntülemek için

- Taşıma veya derlemeyi aşağıdaki konumlardan birine kopyalayın:

   - Geçerli proje dizini. (Kullanarak bu derlemeleri bulabilirsiniz **Gözat** sekmesini.)

   - Aynı çözüm içindeki diğer proje dizinleri. (Kullanarak bu derlemeleri bulabilirsiniz **projeleri** sekmesini.)

    \- veya -

- Görüntülenecek derlemelerin konumunu belirten bir kayıt defteri anahtarını ayarlayın:

   Bir 32-bit işletim sistemi için aşağıdaki kayıt defteri anahtarlarından birini ekleyin.

   - `[HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   - `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   Bir 64-bit işletim sistemi için bir 32-bit kayıt defteri kovanında bulunan aşağıdaki kayıt defteri anahtarlarından birini ekleyin.

   - `[HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   - `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   *\<VersionMinimum\>*  geçerli en düşük .NET Framework sürümü. Varsa *\<VersionMinimum\>* v3.0, belirtilen klasörleri olan *AssemblyFoldersEx* .NET Framework 3.0 ve üstünü hedefleyen projeler için geçerlidir.

   *\<AssemblyLocation\>*  görünmesini istediğiniz derlemelerin dizinidir **Başvuru Ekle** iletişim kutusu *C:\MyAssemblies*.

   Altında kayıt defteri anahtarı oluşturma `HKEY_LOCAL_MACHINE` düğümü, tüm kullanıcıların belirtilen konumda derlemelerde sağlar **Başvuru Ekle** iletişim kutusu. Altında kayıt defteri anahtarı oluşturma `HKEY_CURRENT_USER` düğümü yalnızca geçerli kullanıcı ayarını etkiler.

   Açık **Başvuru Ekle** iletişim kutusunu bir daha. Derlemeleri görünmelidir **.NET** sekmesi. Aksi takdirde, derlemelerin yer olduğundan emin olun belirtilen *AssemblyLocation* dizin, Visual Studio'yu yeniden başlatın ve yeniden deneyin.

## <a name="projects-tab"></a>Projeler sekmesi

**Projeleri** sekmesi içinde geçerli çözüm içindeki tüm uyumlu projeleri listeler **çözüm** alt sekmesi.

Bir proje, farklı bir .NET Framework sürümünü hedef alan başka bir projeye başvuruda bulunabilir. Örneğin, hedefleyen bir proje oluşturabilirsiniz [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] ancak .NET Framework 2 için oluşturulmuş bir derlemeyi başvuruyor. Ancak, .NET Framework 2 projesi başvuramaz bir [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] proje. Daha fazla bilgi için [Multi-targeting'e genel bakış](../ide/visual-studio-multi-targeting-overview.md).

Hedefleyen bir projeye [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] hedefleyen bir projeyle uyumsuzdur [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].

Bir proje hedef .NET Framework 4 ve başka bir proje daha önceki bir sürümü hedefliyorsa bir proje başvurusu yerine dosya başvurusu oluşturulur.

Hedefleyen bir projeye [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] .NET Framework hedefleyen bir projeye bir proje başvurusu eklenemiyor ve bunun tersi de geçerlidir.

## <a name="windows-tab"></a>Windows sekmesi

**Windows** sekmesi çalıştırma hangi Windows işletim sistemleri platformlara özgü tüm SDK'ları listeler.

Visual Studio'da bir WinMD dosyasını iki şekilde oluşturabilirsiniz:

- **Windows 8.x Store uygulaması yönetilen projeleri**: Windows 8.x Store uygulaması projeleri WinMD ikili dosyalarını çıktı ayarlayarak **proje özellikleri** > **Output Type = WinMD File**. WinMD dosya adı, içinde varolan tüm alan adlarının üst küme alan adı olmalıdır. Örneğin, bir proje ad alanları oluşuyorsa `A.B` ve `A.B.C`, verilen WinMD için olası adlar *A.winmd* ve *A.B.winmd*. Bir kullanıcı girerse bir **proje özellikleri** > **derleme adı** veya **proje özellikleri** > **Namespace**projedeki ad alanları kümesinden kopuk değer veya bir proje içinde hiçbir üst küme ad alanı, bir derleme uyarısı oluşturulur: "'A.winmd' Bu derleme için geçerli bir .winmd bir dosya adı değil." Bir Windows Meta Veri dosyası içindeki tüm türler, dosya adının bir alt ad alanında mevcut olmalıdır. Dosya adının alt ad alanında mevcut olmayan türler çalışma zamanında mümkün olmayacaktır. Bu derlemede, en küçük ortak ad alanıdır `CSWSClassLibrary1`. Bir masaüstü Visual Basic veya C# projesi yalnızca birinci Winmd'ler bilinir, Windows 8 SDK kullanılarak oluşturulmuş Winmd'lerin kullanabilir ve winmd oluşturamaz.

- **Windows 8.x Store uygulaması yerel projeleri**: yerel bir WinMD dosyası yalnızca meta verilerden oluşur. Uygulaması ayrı bir DLL dosyası içinde var olur. Bir üretebilir yerel ikili dosyaları Windows çalışma zamanı bileşeni proje şablonu seçilerek **yeni proje** iletişim kutusu ya da boş bir projeden başlatarak ve bir WinMD dosyası oluşturmak için proje özelliklerini değiştirme. Proje kopuk ad alanlarından oluşuyorsa, bir yapı hatası kullanıcıya ad alanlarını birleştirmesi veya MSMerge aracını çalıştırması gerektiğini söyler.

**Windows** sekmesi iki alt gruptan oluşur.

### <a name="core-subgroup"></a>Çekirdek alt grubu

**Çekirdek** alt hedeflenen Windows sürümü için SDK içindeki winmd'lerin (Windows çalışma zamanı öğelerini için) tüm listeler.

Windows 8.x Store uygulaması projeleri, proje oluşturma sırasında varsayılan olarak Windows 8 SDK içindeki Winmd'lerin tümüne başvurular içerir. Yönetilen projelerde altındaki bir salt okunur düğüm **başvuruları** klasöründe **Çözüm Gezgini** tüm Windows 8 SDK'sına yönelik başvuruyu belirtir. Buna **çekirdek** alt gruba **başvuru Yöneticisi** Windows 8 SDK'sı derlemelerin hiçbirini numaralandırmaz ve bunun yerine bir ileti görüntüler: "Windows SDK'sı zaten başvurulmuş. Lütfen nesne tarayıcısı Windows SDK'sındaki başvuruları araştırmak için kullanın."

Masaüstü projelerinde **çekirdek** alt grup, varsayılan olarak görünmez. Windows çalışma zamanı proje düğümü için kısayol menüsünü açarak ekleyebilirsiniz seçme **projeyi**, aşağıdaki kod parçacığını ekleyerek ve projeyi yeniden açarak (proje düğümünü seçin **projeyiyenidenyükle**). Çağırdığınızda **başvuru Yöneticisi** iletişim kutusu, **çekirdek** alt grubu görünür.

```xml
<PropertyGroup>
  <TargetPlatformVersion>8.0</TargetPlatformVersion>
</PropertyGroup>
```

Seçtiğinizden emin olun **Windows** bu alt grupta onay kutusu. Bundan sonra Windows Çalışma Zamanı öğelerini kullanabilmeniz gerekir. Ancak, aynı zamanda eklemek isteyebilirsiniz <xref:System.Runtime>, Windows çalışma zamanı bazı standart sınıfları ve arabirimleri gibi tanımlayan içinde <xref:System.Collections.IEnumerable>, Windows çalışma zamanı kitaplıklarının her yerinde kullanılır. Ekleme hakkında daha fazla bilgi için <xref:System.Runtime>, bkz: [yönetilen Masaüstü uygulamaları ve Windows çalışma zamanı](/previous-versions/windows/apps/jj856306(v=win.10)#consuming-standard-windows-runtime-types).

### <a name="extensions-subgroup"></a>Uzantılar alt grubu

**Uzantıları** kullanıcı hedeflenen Windows platformunu genişleten bir SDK'ları listeler. Bu sekme, Windows 8.x Store uygulaması projeleri için yalnızca görünür. Masaüstü projeleri yalnızca birinci taraf tüketebildiğinden Bu sekme Göster olmaz *.winmd* dosyaları.

SDK, Visual Studio'nun tek bir bileşen olarak kabul ettiği dosyalar topluluğudur. İçinde **uzantıları** sekmesi, proje için geçerli bir SDK'ları **başvuru Yöneticisi** iletişim kutusunun çağrıldığı tek varlıklar halinde listelenir. Bir projeye eklendiğinde SDK içeriğinin tümü kullanılır Visual Studio tarafından kullanıcının IntelliSense, araç kutusu, tasarımcılar, içinde SDK içeriğinden yararlanmak için gereken diğer işlemleri olması gerekmez, nesne tarayıcısı, yapı, dağıtım, hata ayıklama ve paketleme. SDK'nıza görüntüleme hakkında bilgi için **uzantıları** sekmesinde bkz [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md).

> [!NOTE]
> Bir proje, başka bir SDK'ya bağımlı bir SDK'ya başvuruda bulunursa, kullanıcı el ile ikinci SDK'sına bir başvuru eklemediği sürece Visual Studio ikinci SDK'sı tüketmezsiniz. Ne zaman bir kullanıcının seçtiği bir SDK'sı üzerinde **uzantıları** sekmesinde **başvuru Yöneticisi** iletişim kutusu yalnızca adı ve SDK sürüm aynı zamanda tüm SDK adı listeleyerek SDK bağımlılıklarını tanımlamak kullanıcı yardımcı olur Ayrıntılar bölmesinde bağımlılıkları. Bir kullanıcı bağımlılıkları fark etmez ve yalnızca SDK'sı, MSBuild kullanıcıdan bağımlılıkları eklemesini ister ekler.

Bir proje türü uzantıları desteklemiyorsa, sekmesinde görünmez **başvuru Yöneticisi** iletişim kutusu.

## <a name="com-tab"></a>COM sekmesi

**COM** sekmesi, başvuru için kullanılabilen tüm COM bileşenlerini listeler. Dahili bildirim içeren kayıtlı bir COM DLL öğesine başvuru eklemek isterseniz, önce DLL kaydını silin. Aksi takdirde, Visual Studio, bir ActiveX denetimi yerel bir DLL olarak bütünleştirilmiş kod başvurusu ekler.

Bir proje türü COM'u desteklemiyorsa sekmesinde görünmez **başvuru Yöneticisi** iletişim kutusu.

## <a name="browse-button"></a>Gözat düğmesi

Kullanabileceğiniz **Gözat** düğmesini dosya sistemindeki bir bileşen için göz atın.

Bir proje, farklı bir .NET Framework sürümünü hedef alan başka bir bileşene başvuruda bulunabilir. Örneğin, bir uygulama hedefleyen .NET Framework 4.7, .NET Framework 4 hedefleyen bir bileşene başvuruda oluşturabilirsiniz. Daha fazla bilgi için [Multi-targeting'e genel bakış](../ide/visual-studio-multi-targeting-overview.md).

Aynı çözümdeki başka bir projenin çıktılarına dosya başvuruları eklemekten kaçınmalısınız; bu taktik derleme hatalarına neden olabilir. Bunun yerine, **çözüm** sekmesinde **başvuru Yöneticisi** projeden projeye başvuru oluşturmak için iletişim kutusu. Bu takım geliştirme projelerinizde oluşturduğunuz sınıf kitaplıklarının daha iyi yönetimine etkinleştirerek kolaylaştırır. Daha fazla bilgi için [başvuruları bozuk sorun giderme](../ide/troubleshooting-broken-references.md).

Bir SDK'ye göz atamaz ve projenize ekleyin. Yalnızca bir dosyaya göz atabilirsiniz (örneğin, bir derleme veya *.winmd*) ve projenize ekleyin.

Bir Winmd'ye dosya başvurusu yaparken olan beklenen Düzen  *<FileName>.winmd*,  *<FileName>.dll*, ve  *<FileName>.pri* dosyalar Tüm diğer yanı sıra yerleştirilir. Aşağıdaki senaryolarda bir WinMD'ye başvuruda bulunursanız, proje çıkış dizinine eksik bir dosya kümesi kopyalanır ve sonuç olarak, derleme ve çalışma zamanı hataları meydana gelir.

- **Yerel bileşen**: yerel bir proje her kopuk ad alanları kümesi için tek bir WinMD ve uygulamayı içeren bir DLL oluşturur. WinMD'ler ayrı adlara sahip olur. Bu yerel bileşen dosyasına başvururken, benzemeyecek şekilde adlandırılmış Winmd'lerin tek bileşen olun MSBuild tanımaz. Sonuç olarak, yalnızca aynı adlı  *<FileName>.dll* ve  *<FileName>.winmd* kopyalanır, ve çalışma zamanı hataları oluşur. Bu sorunu geçici olarak çözmek için uzantı SDK oluşturun. Daha fazla bilgi için [Create a Software Development Kit](../extensibility/creating-a-software-development-kit.md).

- **Denetimleri tüketen**: en az bir XAML denetimi oluşan bir  *<FileName>.winmd*,  *<FileName>.dll*,  *<FileName>.pri*,  *<XamlName>.xaml*ve bir  *<ImageName>.jpg*. Proje oluşturulduğunda, dosya başvurusu ile ilişkili kaynak dosyalar projenin çıkış dizinine kopyalanmaz ve yalnızca vermeyeceğiz  *<FileName>.winmd*,  *<FileName>.dll*ve  *<FileName>.pri* kopyalanır. Bir yapı hatası kullanıcıya bildirmek için oturum açmış olan kaynakları  *<XamlName>.xaml* ve  *<ImageName>.jpg* eksik. Başarılı olması için, kullanıcının bu kaynak dosyaları oluşturma ve hata ayıklama/çalışma zamanı için proje çıkış dizinine el ile kopyalaması gerekir. Bu sorunu geçici olarak çözmek için ya da bir uzantı SDK'sı adımları izleyerek oluşturun, [Create a Software Development Kit](../extensibility/creating-a-software-development-kit.md) veya aşağıdaki özellik eklemek için proje dosyasını düzenleyin:

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Özelliği eklerseniz, yapı daha yavaş çalışabilir.

## <a name="recent"></a>En Son

**Derlemeleri**, **COM**, **Windows**, ve **Gözat** her destek bir **son** listesini numaralandırır sekmesinde projelere yakın zamanda eklenmiş bileşenlerin.

## <a name="search"></a>Ara

Arama çubuğuna **başvuru Yöneticisi** iletişim kutusu'nın, odakta olan sekme üzerinde çalışır. Örneğin, bir kullanıcı sırasında arama çubuğuna "Sistem" yazarsa **çözüm** sekme odağı, arama Çözüm "Sistem" içeren bir proje adından oluşmadığı sürece herhangi bir sonuç döndürmek olmaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)