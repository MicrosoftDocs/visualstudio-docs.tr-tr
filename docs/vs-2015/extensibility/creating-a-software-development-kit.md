---
title: Bir yazılım geliştirme seti oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: 55
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a7c3ff7a3a8c872c4b624c8d2956a6802a0ab139
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723679"
---
# <a name="creating-a-software-development-kit"></a>Yazılık Geliştirme Seti Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir yazılım geliştirme seti (SDK), Visual Studio'da tek bir öğe olarak başvurabilirsiniz API koleksiyonudur. **Başvuru Yöneticisi** iletişim kutusu, projeye ilgili tüm SDK'ları listeler. Bir SDK için bir proje eklediğinizde, API'ler, Visual Studio'da kullanılabilir.  
  
 SDK'ları iki tür vardır:  
  
- Platform SDK'larını bir platform için uygulamalar geliştirmeye yönelik zorunlu bileşenlerdir. Örneğin, [!INCLUDE[win81](../includes/win81-md.md)] geliştirmek için SDK'sı gereklidir [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamalar.  
  
- Uzantı Sdk'leri, platform için uygulamalar geliştirmek için zorunlu değildir ancak bir platformunu genişletmeye isteğe bağlı bileşenlerdir.  
  
  Aşağıdaki bölümlerde SDK'ları ve platform SDK'sı oluşturma genel altyapı ve uzantı SDK.  
  
- [Platform SDK'ları](#PlatformSDKs)  
  
- [Uzantı SDK'ları](#ExtensionSDKs)  
  
##  <a name="PlatformSDKs"></a> Platform SDK'ları  
 Platform SDK'larını, bir platform için uygulamalar geliştirmek için gereklidir. Örneğin, [!INCLUDE[win81](../includes/win81-md.md)] uygulamaları geliştirmek için SDK'sı gereklidir [!INCLUDE[win81](../includes/win81-md.md)].  
  
### <a name="installation"></a>Yükleme  
 HKLM\Software\Microsoft\Microsoft SDK'ları tüm platform SDK'ları yüklenecek\\[TPV] [TPI] \v\\ @InstallationFolder [SDK kök] =. Buna [!INCLUDE[win81](../includes/win81-md.md)] SDK'sı HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1 yüklü.  
  
### <a name="layout"></a>Düzen  
 Platform SDK'ları aşağıdaki düzen olacaktır:  
  
```  
\[InstallationFolder root]  
            SDKManifest.xml  
            \References  
                  \[config]  
                        \[arch]  
            \DesignTime  
                  \[config]  
                        \[arch]  
```  
  
|Düğüm|Açıklama|  
|----------|-----------------|  
|Başvurular klasörü|Karşı kodlanmış API'leri içeren bir ikili dosyalarını içerir. Bu, Windows Metadata (WinMD) dosya veya derlemeleri içerebilir.|  
|Tasarım zamanı klasörü|Yalnızca öncesi-run/hata ayıklama sırasında gereken dosyaları içerir. Bu XML belgeleri, kitaplıklar, üst bilgiler, araç kutusu tasarım zamanı ikili dosyalarını, MSBuild yapıtları ve diğerleri dahil olabilir<br /><br /> XML belgeleri ideal olarak, \DesignTime klasörüne yerleştirilmesi ancak XML belgeleri başvurular için referans dosyasını Visual Studio'da yanı sıra yerleştirilecek devam edecektir. Örneğin, XML belge için bir başvuru \References\\[yapılandırma]\\[arch]\sample.dll \References olacaktır\\[yapılandırma]\\[arch]\sample.xml ve bu belge yerelleştirilmiş sürümünü \Referencesolacaktır\\[yapılandırma]\\[arch]\\[locale]\sample.xml.|  
|Yapılandırma klasörü|Yalnızca üç klasör olabilir: hata ayıklama, perakende ve CommonConfiguration. SDK dosyalarını aynı kümesini, SDK'sı tüketici hedefleyen yapılandırmayı bağımsız olarak kullanılması SDK yazarlar dosyalarına CommonConfiguration altında koyabilirsiniz.|  
|Mimari klasörü|Herhangi bir desteklenen mimari klasör bulunabilir. Visual Studio aşağıdaki mimarilerine destekler: x86, x64, ARM ve neutral. Not: Win32 için x86 eşlenir ve buna AnyCPU için nötr eşler.<br /><br /> MSBuild için Platform SDK'ları yalnızca \CommonConfiguration\neutral altında görünür.|  
|SDKManifest.xml|Bu dosya, Visual Studio SDK'yı nasıl tüketmesi gereken açıklar. SDK bildirimi için bakın [!INCLUDE[win81](../includes/win81-md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** değerin Nesne Tarayıcısı göz atma listesinde görüntülenir.<br /><br /> **PlatformIdentity:** bu öznitelik varlığını Visual Studio ve MSBuild SDK'sı bir platform SDK'sı olduğunu ve ondan eklenen başvuruları kopyalanan olmamalıdır yerel olarak bildirir.<br /><br /> **TargetFramework:** bu öznitelik, yalnızca hedefleyen projelerde bu değeri belirtildiği gibi aynı çerçeveleri emin olmak için Visual Studio tarafından kullanılan öznitelik, SDK'sını kullanabilir.<br /><br /> **MinVSVersion:** bu öznitelik için geçerli olan SDK'lar kullanmak için Visual Studio tarafından kullanılır.<br /><br /> **Başvuru:** bu öznitelik denetimler içeren yalnızca bu başvuruları için belirtilmesi gerekir. Bir başvuru denetimleri içerip içermediğini belirtme hakkında daha fazla bilgi için aşağıya bakın.|  
  
##  <a name="ExtensionSDKs"></a> Uzantı SDK'ları  
 Aşağıdaki bölümlerde, uzantı SDK dağıtmak için yapmanız gerekenler açıklanmaktadır.  
  
### <a name="installation"></a>Yükleme  
 Uzantı SDK'ları için belirli bir kullanıcı veya tüm kullanıcılar için bir kayıt defteri anahtarı belirtmeden yüklenebilir. Tüm kullanıcılar için bir SDK'yı yüklemek için aşağıdaki yola kullanın:  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Bir kullanıcıya özel yükleme için aşağıdaki yol kullanın:  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Farklı bir konum kullanmak istiyorsanız, ikisinden birini yapmanız gerekir:  
  
1.  Bu kayıt defteri anahtarında belirtin:  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     ve değeri olan bir (varsayılan) alt ekleyin `<path to SDK><SDKName><SDKVersion>`.  
  
2.  MSBuild özelliği Ekle `SDKReferenceDirectoryRoot` proje dosyanıza. Bu özelliğin değeri bir başvurmak istediğiniz uzantı Sdk'lerine bulunduğu dizin noktalı virgülle ayrılmış listesidir.  
  
### <a name="installation-layout"></a>Yükleme düzeni  
 Uzantı SDK'ları aşağıdaki yükleme düzenini vardır:  
  
```  
\<ExtensionSDKs root>  
           \<SDKName>  
                 \<SDKVersion>  
                        SDKManifest.xml  
                        \References  
                              \<config>  
                                    \<arch>  
                        \Redist  
                              \<config>  
                                    \<arch>  
                        \DesignTime  
                               \<config>  
                                     \<arch>  
  
```  
  
1.  \\< SDKName\>\\< SDKVersion\>: SDK türetilen yol karşılık gelen klasör adlarında SDK kök uzantı sürümünü ve adı. MSBuild SDK'sı diskte bulmak için bu kimliği kullanır ve Visual Studio görüntüler bu kimliğinde **özellikleri** penceresi ve **başvuru Yöneticisi** iletişim.  
  
2.  Başvurular klasörü: API'ları içeren ikili dosyaları. Bunlar, Windows Metadata (WinMD) dosya veya derlemeleri olabilir.  
  
3.  Redist klasöründen: kullanıcı uygulamasının bir parçası olarak paketlenmiş ve çalışma zamanı/hata ayıklama için gereken dosyaları. Tüm ikili dosyaları \redist yerleştirilmelidir\\< yapılandırma\>\\< arch\>, ve ikili adları benzersiz olmasını sağlamak için şu biçimde olmalıdır:  **\<şirket >.\< Ürün >. \<amaçlı >. \<uzantısı >**. Örneğin, Microsoft.Cpp.Build.dll. Dosya adlarından (örneğin, javascript, css, PRI, xaml, png ve jpg dosyaları) diğer SDK'lar ile çakışabilir adlara sahip tüm dosyaları \redist yerleştirilmelidir\\< yapılandırma\>\\< arch\> \\< sdkname\>\ XAML ile ilişkili olan dosyaları hariç denetler. Bu dosyaları \redist yerleştirilmelidir\\< yapılandırma\>\\< arch\>\\< componentname\>\\.  
  
4.  Tasarım zamanı klasörü: yalnızca öncesi-run/hata ayıklama sırasında gerekli olan dosyaların zaman ve kullanıcı uygulamasının bir parçası olarak paketlenmiş olmamalıdır. Bunlar, XML belgeleri, kitaplıklar, üst bilgiler, araç kutusu tasarım zamanı ikili dosyalarını, MSBuild yapıtları ve benzeri olabilir. Yerel bir proje tüketimi bulunmalıdır kullanılmaya SDK bir *SDKName*.props dosyası. Aşağıda, bu dosya türü örneği gösterilmektedir.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>  
        <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>  
        <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>  
        <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>  
        <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>  
        <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>  
        <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>  
      </PropertyGroup>  
    </Project>  
  
    ```  
  
     XML başvuru belgeleri başvurusu dosyasını yerleştirilir. Örneğin, başvuru için XML belgesi **\References\\< yapılandırma\>\\< arch\>\sample.dll** derleme **\References\\ < yapılandırma\>\\< arch\>\sample.xml**, ve bu belge yerelleştirilmiş sürümünü **\References\\< yapılandırma\>\\< arch\>\\< yerel ayar\>\sample.xml**.  
  
5.  Yapılandırma klasörü: üç alt klasörleri: hata ayıklama, perakende ve CommonConfiguration. SDK dosyalarını aynı kümesini, SDK'sı tüketici tarafından hedeflenen yapılandırma bağımsız olarak kullanılması zaman, SDK yazarlar dosyalarına CommonConfiguration altında yerleştirebilirsiniz.  
  
6.  Mimari klasör: aşağıdaki mimarilerine desteklenir: x86, x64, ARM, nötr. Win32 için x86 eşlenir ve buna AnyCPU için nötr eşler.  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 Bu dosya, Visual Studio SDK'yı nasıl tüketmesi gereken açıklar. Bir örnek verilmiştir.  
  
```  
<FileList>  
DisplayName = "My SDK"  
ProductFamilyName = "My SDKs"  
TargetFramework = ".NETCore, version=v4.5.1; .NETFramework, version=v4.5.1"  
MinVSVersion = "14.0"  
MaxPlatformVersion = "8.1"  
AppliesTo = "WindowsAppContainer + WindowsXAML"  
SupportPrefer32Bit = "True"  
SupportedArchitectures = "x86;x64;ARM"  
SupportsMultipleVersions = "Error"  
CopyRedistToSubDirectory = "."  
DependsOn = "SDKB, version=2.0"  
MoreInfo = "http://msdn.microsoft.com/MySDK">  
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">  
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />  
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />  
<ToolboxItems VSCategory = "Toolbox.Default" />  
</File>  
</FileList>  
```  
  
 Aşağıdaki listede, dosya öğeleri sağlar.  
  
1.  DisplayName: başvuru Yöneticisi, Çözüm Gezgini'nde, Nesne Tarayıcısı ve kullanıcı arabirimi başka konumlarda Visual Studio için görüntülenen değeri.  
  
2.  ProductFamilyName: Genel SDK ürün adı. Örneğin, [!INCLUDE[winjs_long](../includes/winjs-long-md.md)] SDK'sı, SDK ürünleri ailesi, "Microsoft.WinJS" aynı ailesine ait "Microsoft.WinJS.1.0" ve "Microsoft.WinJS.2.0" adlandırılır. Bu öznitelik, bu bağlantı kurmak Visual Studio ve MSBuild sağlar. Bu öznitelik yoksa, SDK adı ürün ailesi adı olarak kullanılır.  
  
3.  Frameworkıdentity: bağımlılık bu özniteliğin değeri, alıcı uygulamanın bildirimine yerleştirilir bir veya daha fazla Windows bileşeni kitaplıklarındaki belirtir. Bu öznitelik, yalnızca Windows bileşeni kitaplıklar için geçerlidir.  
  
4.  TargetFramework: başvuru Yöneticisi ve araç kullanılabilir SDK'lar belirtir. Bu örneğin hedef framework takma ad, noktalı virgül ile ayrılmış bir listesini, ".NET Framework, sürüm = v2.0; .NET Framework, sürüm v4.5.1 =". Aynı hedef framework'ün çeşitli sürümlerinden belirtilirse, başvuru Yöneticisi filtreleme amaçlı için belirtilen en düşük sürümü kullanır. Örneğin, ".NET Framework, sürüm v2.0; = .NET Framework, sürüm v4.5.1 =" belirtilirse, başvuru Yöneticisi'ni kullanır ".NET Framework, sürüm = v2.0". Belirli hedef çerçeve profilini belirtilirse, filtreleme amaçlı için yalnızca bu profili başvuru Yöneticisi tarafından kullanılır. Örneğin, "Silverlight, sürüm = v4.0, profili WindowsPhone =" belirtilen filtreler yalnızca Windows Phone profilinde; başvuru Yöneticisi Silverlight 4.0 Framework'ün tamamını hedefleyen bir proje başvuru Yöneticisi'nde SDK görmez.  
  
5.  MinVSVersion: en düşük Visual Studio sürümü.  
  
6.  MaxPlatformVerson: Uzantı SDK'nızı değil çalışır platform sürümlerini belirtmek için en fazla hedef platform sürümü kullanılması gerekir. Örneğin, Microsoft Visual C++ Runtime Package v11. 0 yalnızca Windows 8 projeleri tarafından başvurulması gerekir. Bu nedenle, Windows 8 projenin MaxPlatformVersion 8.0 ' dir. Bu başvuru Yöneticisi, Windows 8.1 projesi için Microsoft Visual C++ Runtime Package filtreler ve MSBuild, bir hata oluşturur anlamına gelir, bir [!INCLUDE[win81](../includes/win81-md.md)] projeye başvuruyor. Not: Bu öğe itibariyle desteklenir [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)].  
  
7.  AppliesTo: geçerli Visual Studio Proje türleri belirterek başvuru Yöneticisi'nde kullanılabilir SDK'lar belirtir. Dokuz değer tanınıyor:; WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, yönetilen ve yerel. SDK'sı yazarı kullanabilirsiniz ve ("+'), veya ("&#124;") değil ("! ") tam olarak SDK'SININ geçerli proje türleri kapsamını belirtmek için işleçler.  
  
     WindowsAppContainer tanıtan projeler için [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamalar.  
  
8.  SupportPrefer32Bit: Desteklenen değerler şunlardır: "True" ve "False". Varsayılan değer "True" şeklindedir. Değer "False" olarak ayarlanırsa, MSBuild için bir hata döndürür [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projeleri (veya Masaüstü projeleri için bir uyarı) SDK'sı başvuran proje etkin Prefer32Bit varsa. Prefer32Bit hakkında daha fazla bilgi için bkz: [derleme sayfası, Proje Tasarımcısı (C#)](../ide/reference/build-page-project-designer-csharp.md) veya [derleme sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).  
  
9. SupportedArchitectures: noktalı virgül SDK'yı destekleyen mimarileri listesidir. Alıcı projedeki hedeflenen SDK mimarisi desteklenmiyorsa MSBuild bir uyarı görüntüler. Bu öznitelik belirtilmezse, MSBuild hiçbir zaman bu tür bir uyarı görüntüler.  
  
10. SupportsMultipleVersions: Bu öznitelik ayarlanırsa **hata** veya **uyarı**, MSBuild gösterir aynı projede birden çok sürümünü aynı SDK'sı ailesi başvuramaz. Bu öznitelik mevcut değil ya da ayarlanmış **izin**, MSBuild olmayan bu tür hata veya uyarı görüntüler.  
  
11. AppX: disk üzerinde Windows bileşeni kitaplığı için uygulama paketlerini yolunu belirtir. Bu değer, yerel hata ayıklama sırasında Windows Bileşen kitaplığının kayıt bileşenine geçirilir. Dosya adı için adlandırma kuralı  **\<şirket >.\< Ürün >. \<Mimarisi >. \<Yapılandırma >. \<Sürüm > .appx**. Windows Bileşen kitaplığa uygulamazsanız yapılandırma ve mimari öznitelik adı ve öznitelik değeri isteğe bağlıdır. Bu değer, yalnızca Windows bileşeni kitaplıklar için geçerlidir.  
  
12. CopyRedistToSubDirectory: uygulama paket köküne göreli \redist klasörü altındaki dosyaları nereye kopyalanacağını belirtir. (diğer bir deyişle, **paket konumu** uygulama paketi oluşturma Sihirbazı'nda seçilen) ve çalışma zamanı Düzen kökü. Varsayılan konumu F5 düzenini ve uygulama paketi köküdür.  
  
13. DependsOn: Bu SDK'sı bağımlı olduğu SDK'ları tanımlama SDK kimliklerinin bir listesi. Bu öznitelik başvuru Yöneticisi'nin ayrıntılar bölmesinde görüntülenir.  
  
14. Daha fazla bilgi: Yardım ve daha fazla bilgi sağlayan web sayfası URL'si. Bu değer, başvuru Yöneticisi'nin sağ bölmede daha fazla bilgi bağlantısındaki kullanılır.  
  
15. Kayıt türü: uygulama bildiriminde WinMD kayıt belirtir ve bir DLL karşılığı uygulaması olan yerel WinMD için gereklidir.  
  
16. Dosya başvurusu: yerel Winmd'lerin denetimleri içeren veya yalnızca bu başvuruları için belirtilmiş. Bir başvuru denetimleri içerip içermediğini belirtme hakkında daha fazla bilgi için bkz: [araç kutusu öğeleri konumu belirtme](#ToolboxItems) aşağıda.  
  
##  <a name="ToolboxItems"></a> Araç kutusu öğeleri konumunu belirtme  
 SDKManifest.xml şemasının ToolBoxItems öğesi hem platformu hem de uzantı SDK'ları kategori ve araç kutusu öğeleri konumunu belirtir. Aşağıdaki örnekler, farklı konumlar belirtebilirsiniz gösterilmektedir. WinMD veya DLL başvurularını uygun budur.  
  
1.  Araç kutusu varsayılan kategorideki denetimleri yerleştirin.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Default"/>       
    </File>  
    ```  
  
2.  Belirli bir kategori adı altında denetimlerini yerleştirin.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory= "MyCategoryName"/>  
    </File>  
    ```  
  
3.  Belirli bir kategori adlarıyla denetimlerini yerleştirin.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = "Data">  
        <ToolboxItems />  
    </File>  
    ```  
  
4.  Denetimleri farklı bir kategori adlarıyla Blend ve Visual Studio koyun.  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  Belirli denetimlerle Blend ve Visual Studio farklı şekilde sıralar.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  Belirli denetimler listeleme ve bunları Visual Studio ortak yolunda veya yalnızca tüm denetimleri grubuna yerleştirin.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  Belirli denetimler numaralandırabilir ve yalnızca belirli bir grup içinde ChooseItems onlar olmadan göster araç kutusunda oluşturuluyor.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: C++ kullanarak SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [İzlenecek yol: C# veya Visual Basic kullanarak SDK oluşturma](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)

