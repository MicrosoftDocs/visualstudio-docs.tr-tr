---
title: Evrensel Windows Platformu (UWP) uygulamaları geçirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5279ab9b-71d9-4be5-81f6-a1f24b06f5fb
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8d4bc5d8e8a24483c30ac813d3253626e58dd353
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791754"
---
# <a name="migrate-apps-to-the-universal-windows-platform-uwp"></a>Uygulamaları Evrensel Windows Platformu’na (UWP) geçirme
Visual Studio 2015 RTM ile kullanılabilir böylece mevcut proje dosyalarınıza Windows Store 8.1 uygulamaları, Windows Phone 8.1 uygulamaları ya da Visual Studio 2015 RC ile oluşturulmuş Evrensel Windows uygulamaları için gerekli el ile değişiklikleri yapın. (Windows 8.1 Evrensel uygulamasıyla bir Windows uygulaması projesi ve Windows Phone projesi varsa, her projeyi geçirmek için adımları izlemeniz gerekir.)  
  
 Evrensel Windows platformu ile uygulamanıza bir veya daha fazla cihaz aileleri hedefleyin. Evrensel Windows uygulamaları hakkında daha fazla bilgi istiyorsanız, bu göz atın [platform Kılavuzu](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx).  
  
- [Mevcut C# /VB Windows Store 8.1 veya Windows Phone 8.1 uygulamalarınızın geçirme](#MigrateCSharp) Evrensel Windows platformu kullanılacak.  
  
- [Var olan C++ Windows Store 8.1 veya Windows Phone 8.1 uygulamaları geçirme](#MigrateCPlusPlus) Evrensel Windows platformu kullanılacak.  
  
- [Visual Studio 2015 RC ile oluşturulmuş mevcut bir evrensel Windows uygulamaları için gerekli değişiklikleri](#PreviousVersions).  
  
- [Mevcut Visual Studio 2015 RC ile oluşturulmuş Evrensel Windows uygulamaları için birim testi projeleri için gerekli değişiklikleri](#MigrateUnitTest).  
  
  Bu değişiklikleri yapmak istemiyorsanız, bilgi nasıl [mevcut uygulamalarınızı bağlantı noktası](http://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) içine yeni bir evrensel Windows projesi.  
  
##  <a name="MigrateCSharp"></a> Evrensel Windows Platformu'nu kullanmak için C# /VB Windows Store 8.1 veya Windows Phone 8.1 uygulamaları geçirme  
  
#### <a name="migrate-your-cvb-project-files"></a>C# /VB proje dosyalarınızı geçirme  
  
1.  Yüklediğiniz hangi Evrensel Windows platformu bulmak için şu dosyayı açın: **\Program dosyaları (x86) \Windows Kits\10\Platforms\UAP**. Bu, yüklü Evrensel her Windows platformu için klasörlerin listesini içerir. Klasör adı yüklemiş olduğunuz Evrensel Windows platformu sürümüdür. Örneğin, bu Windows 10 cihazına yüklü sürüm 10.0.10240.0 Evrensel Windows platformu vardır.  
  
     ![Yüklü sürüm görüntülemek için klasörü açın](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
     Evrensel Windows platformu birden çok sürümü yüklenebilir. Uygulamanız için en son sürümünü kullanmanızı öneririz.  
  
2.  Dosya Gezgini'ni kullanarak UWP projenizin depolandığı klasöre gidin. Bu klasörde bir .json dosyası oluşturun. Dosya adı: project.json ve ardından bu dosyaya aşağıdaki içeriği ekleyin:  
  
    ```json  
    {  
      "dependencies": {  
        "Microsoft.ApplicationInsights": "1.0.0",  
        "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",  
        "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",  
        "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"  
      },  
      "frameworks": {  
        "uap10.0": {}  
      },  
      "runtimes": {  
        "win10-arm": {},  
        "win10-arm-aot": {},  
        "win10-x86": {},  
        "win10-x86-aot": {},  
        "win10-x64": {},  
        "win10-x64-aot": {}  
      }  
    }  
  
    ```  
  
3.  Aşağıdaki içeriklerle default.RD.xml adlı bir dosya oluşturun. Bir VB projesi varsa, bu dosya projeniz için Projem dizin ekleyin. Bir C# projesi varsa, bu dosya, projeniz için özellikleri dizinine ekleyin.  
  
    ```xml  
    <?xml version="1.0"?>  
    <!-- This file contains Runtime Directives used by .NET Native. The defaults here are suitable for most developers. However, you can modify these parameters to modify the behavior of the .NET Native optimizer. Runtime Directives are documented at http://go.microsoft.com/fwlink/?LinkID=391919 To fully enable reflection for App1.MyClass and all of its public/private members <Type Name="App1.MyClass" Dynamic="Required All"/> To enable dynamic creation of the specific instantiation of AppClass<T> over System.Int32 <TypeInstantiation Name="App1.AppClass" Arguments="System.Int32" Activate="Required Public" /> Using the Namespace directive to apply reflection policy to all the types in a particular namespace <Namespace Name="DataClasses.ViewModels" Seralize="All" /> -->  
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata"><Application>  
    <!-- An Assembly element with Name="*Application*" applies to all assemblies in the application package. The asterisks are not wildcards. -->  
    <Assembly Dynamic="Required All" Name="*Application*"/>  
    <!-- Add your application specific runtime directives here. -->  
    </Application></Directives>  
    ```  
  
4.  Çözümünüzü içeren mevcut Windows Store 8.1 uygulaması veya Windows Phone 8.1 uygulamayı Visual Studio'da açın.  
  
5.  Çözüm Gezgini'nde, uygulamanız için mevcut projeyi sağ tıklayın ve ardından **projeyi**. Proje kaldırılmadan sonra proje dosyasını tekrar sağ tıklayın ve .csproj veya .vbproj dosyasını düzenlemek seçin.  
  
     ![Projeye sağ tıklayın ve Düzen](../misc/media/uap-editproject.png "UAP_EditProject")  
  
6.  Bulma \<PropertyGroup > öğesini içeren \<TargetPlatformVersion > 8.1 bir değere sahip öğe. Aşağıdaki adımlarda bunu \<PropertyGroup > öğesi:  
  
    1.  Değerini \<Platform > öğesine: **x86**.  
  
    2.  Ekleme bir \<Targetplatformıdentifier > öğesi ve onun değerine: **UAP**.  
  
    3.  Mevcut değiştirin \<TargetPlatformVersion > öğesi değeri Evrensel Windows platformu sürümünün yüklü olması. Ayrıca bir \<TargetPlatformMinVersion > öğesi ve aynı değeri verin.  
  
    4.  Değiştirin \<MinimumVisualStudioVersion > öğesine: **14**.  
  
    5.  Değiştirin \<ProjectTypeGuids > aşağıda gösterildiği gibi bir öğe:  
  
         C# için:  
  
        ```xml  
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
        ```  
  
         VB için:  
  
        ```xml  
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        ```  
  
    6.  Ekleme bir \<EnableDotNetNativeCompatibleProfile > öğesi ve onun değerine: **true**.  
  
    7.  Evrensel Windows uygulamaları için varsayılan varlık ölçek 200'dür. Projenize varlıklar 200 ölçeği değil içeriyorsa, eklemeniz gerekecektir bir \<UapDefaultAssetScale > Bu PropertyGroup varlıklarınızı ölçeğini değere sahip öğe. Daha fazla bilgi edinin [varlıklar ve ölçekler](http://msdn.microsoft.com/library/jj679352.aspx).  
  
         Şimdi, \<PropertyGroup > öğesi bu örnektekine benzer görünmelidir:  
  
        ```xml  
        <PropertyGroup>  
            …  
             <Platform Condition=" '$(Platform)' == '' ">x86</Platform>  
             <TargetPlatformVersion>10.0.10240.0</TargetPlatformVersion>  
             <TargetPlatformMinVersion>10.0.10240.0</TargetPlatformMinVersion>  
             <TargetPlatformIdentifier>UAP</TargetPlatformIdentifier>  
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>  
             <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
             <UapDefaultAssetScale>100</UapDefaultAssetScale>  
             …  
        </PropertyGroup>  
        ```  
  
7.  Tüm örneklerini 12.0 artık kullanmakta olduğunuz Visual Studio sürümünü yansıtacak şekilde 14.0 ile değiştirin. Bu örnekler gibi:  
  
    ```xml  
    <Project Tools Version="14.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ```  
  
    ```  
    <PropertyGroup Condition=" '$(VisualStudioVersion)' == '' or '$(VisualStudioVersion)' < '14.0' ">  
        <VisualStudioVersion>14.0</VisualStudioVersion>  
    ```  
  
8.  Bulma \<PropertyGroup > AnyCPU platformu koşul özniteliği bir parçası olarak yapılandırılmış olan öğeler. Bu öğeleri ve tüm alt öğelerini kaldırın. AnyCPU, Windows 10 uygulamaları Visual Studio 2015'te desteklenmiyor. Örneğin, kaldırmalısınız \<PropertyGroup > Bu olanlar gibi öğeler:  
  
    ```xml  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <PlatformTarget>AnyCPU</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <PlatformTarget>AnyCPU</PlatformTarget>  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
    ```  
  
9. Her kalan \<PropertyGroup > öğesinde, bir yayın yapılandırmasına sahip bir koşul özniteliği öğe olup olmadığını denetleme. Bunu yapar, ancak içermediğinden bir \<UseDotNetNativeToolchain > öğesi, bir ekleyin. Değerini \<UseDotNetNativeToolchain > öğesini true, şöyle:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|x64'">  
        <OutputPath>bin\x64\Release\</OutputPath>  
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
        <Optimize>true</Optimize>  
        <NoWarn>;2008</NoWarn>  
        <DebugType>pdbonly</DebugType>  
        <PlatformTarget>x64</PlatformTarget>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
        <ErrorReport>prompt</ErrorReport>  
        <Prefer32Bit>true</Prefer32Bit>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
    ```  
  
10. Windows Phone için yalnızca, projeleri kaldırma \<PropertyGroup > öğesini içeren bir \<Targetplatformıdentifier > öğesi WindowsPhoneApp değerine sahip. Ayrıca bu öğenin alt öğeleri kaldırın:  
  
    ```xml  
    <PropertyGroup Condition=" '$(TargetPlatformIdentifier)' == '' ">  
      <TargetPlatformIdentifier>WindowsPhoneApp</TargetPlatformIdentifier>  
    </PropertyGroup>  
    ```  
  
11. Bulma \<ItemGroup > öğesini içeren \<AppxManifest > öğesi. Aşağıdaki \<yok > öğesi alt öğesi olarak \<ItemGroup > öğesi:  
  
    ```xml  
    <None Include="project.json" />  
    ```  
  
12. Bulma \<ItemGroup > öğesini projenize logo .png dosyaları gibi eklenen diğer varlıklar içeren (\<içerik Include="Assets\Logo.scale-100.png" / >). Aşağıdaki \<içerik > alt öğe bu \<ItemGroup > öğesi:  
  
     **C# için:**  
  
    ```xml  
    <Content Include="Properties\default.rd.xml" />  
    ```  
  
     **VB için:**  
  
    ```xml  
    <Content Include="My Project\default.rd.xml" />  
    ```  
  
13. Bulma \<ItemGroup > içeren öğe \<başvuru > NuGet paketlerine alt öğeleri. Projenizi yeniden yüklendikten sonra bunları ile NuGet Paket Yöneticisi karşıdan yüklemek ihtiyacınız olacağı için kullanabileceğiniz NuGet paketlerini not alın. Bu kaldırma \<ItemGroup > alt yanı sıra. Örneğin, bir UWP projesi kaldırılması gereken aşağıdaki NuGet paketlerini olabilir:  
  
    ```xml  
    <ItemGroup>  
        <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">  
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">  
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
      </ItemGroup>  
    ```  
  
14. Değişikliklerinizi kaydedin.  
  
15. .Csproj veya .vbproj dosyasını kapatın.  
  
16. Çözüm Gezgini'nde projenize sağ tıklayın ve bağlam menüsünden projeyi seçin. Projenizdeki tüm dosyaları artık Çözüm Gezgini içinde görüntülenmesi gerekir.  
  
17. Sildiğiniz paketleri daha önceki bir adımda geri eklemek için NuGet Yöneticisi'ni kullanın.  
  
     İçin adımları takip etmeniz artık [paket bildirim dosyalarını güncelleştirme](#PackageManifest) tüm Windows Store 8.1 veya Windows Phone 8.1 projeleri için.  
  
##  <a name="MigrateCPlusPlus"></a> Evrensel Windows Platformu'nu kullanmak için C++ Windows Store 8.1 veya Windows Phone 8.1 uygulamaları geçirme  
  
#### <a name="migrate-your-c-project-files"></a>C++ proje dosyalarını geçirme  
  
1.  Yüklediğiniz hangi Evrensel Windows platformu bulmak için şu dosyayı açın: **\Program dosyaları (x86) \Windows Kits\10\Platforms\UAP**. Bu, yüklü Evrensel her Windows platformu için klasörlerin listesini içerir. Klasör adı yüklemiş olduğunuz Evrensel Windows platformu sürümüdür. Örneğin, bu Windows 10 cihazına yüklü sürüm 10.0.10240.0 Evrensel Windows platformu vardır.  
  
     ![Yüklü sürüm görüntülemek için klasörü açın](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
     Evrensel Windows platformu birden çok sürümü yüklenebilir. Uygulamanız için en son sürümünü kullanmanızı öneririz.  
  
2.  Var olan C++ Windows Store 8.1 uygulaması veya Windows Phone 8.1 uygulamayı Visual Studio'da içeren çözümünüzü açın.  
  
     Mevcut Çözüm Gezgini'nden projenize sağ tıklayın ve ardından **projeyi**. Proje kaldırılmadan sonra proje dosyasını tekrar sağ tıklayın ve .vcxproj dosyasını düzenlemek seçin.  
  
     ![Sağ&#45;proje dosyasına tıklayın ve düzenlemek seçin](../misc/media/uap-editcplusproject.png "UAP_EditCPlusProject")  
  
3.  Bulma \<PropertyGroup > öğesini içeren \<ApplicationTypeRevision > 8.1 bir değere sahip öğe. Aşağıdaki adımlarda bunu \<PropertyGroup > öğesi:  
  
    1.  Ekleme bir \<WindowsTargetPlatformVersion > öğesi ve bir \<WindowsTargetPlatformMinVersion > öğesi ve yüklediğiniz Evrensel Windows platformu sürümü değerini verin.  
  
    2.  8.1 ApplicationTypeRevision öğesinden 10.0 için değeri güncelleştirin.  
  
    3.  Değiştirin \<MinimumVisualStudioVersion > öğesine: 14.  
  
    4.  Ekleme bir \<EnableDotNetNativeCompatibleProfile > öğesi ve onun değerine: true.  
  
    5.  Evrensel Windows uygulamaları için varsayılan varlık ölçek 200'dür. Projenize varlıklar 200 ölçeği değil içeriyorsa, eklemeniz gerekecektir bir \<UapDefaultAssetScale > Bu PropertyGroup varlıklarınızı ölçeğini değere sahip öğe. Daha fazla bilgi edinin [varlıklar ve ölçekler](http://msdn.microsoft.com/library/jj679352.aspx).  
  
    6.  Windows Phone için projeleri yalnızca değerini değiştirmek \<ApplicationType > Windows Phone için Windows Store'dan.  
  
         Şimdi, \<PropertyGroup > öğesi bu örnektekine benzer görünmelidir:  
  
        ```xml  
        <PropertyGroup>  
            …  
                  <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>  
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>  
             <ApplicationType>Windows Store</ApplicationType>  
             <ApplicationTypeRevision>10.0</ApplicationTypeRevision>  
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>  
             <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
             <UapDefaultAssetScale>100</UapDefaultAssetScale>  
             …  
        </PropertyGroup>  
        ```  
  
4.  Tüm örneklerini değiştirmek \<PlatformToolset > değer v140 için öğesi. Örneğin:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">  
        <ConfigurationType>Application</ConfigurationType>  
        <UseDebugLibraries>false</UseDebugLibraries>  
        <WholeProgramOptimization>true</WholeProgramOptimization>  
        <PlatformToolset>v140</PlatformToolset>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
    ```  
  
5.  Her kalan \<PropertyGroup > öğesinde, bir yayın yapılandırmasına sahip bir koşul özniteliği öğe olup olmadığını denetleme. Bunu yapar, ancak içermediğinden bir \<UseDotNetNativeToolchain > öğesi, bir ekleyin. Değerini \<UseDotNetNativeToolchain > öğesini true, şöyle:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|X64'" Label="Configuration">  
        <ConfigurationType>Application</ConfigurationType>  
        <UseDebugLibraries>false</UseDebugLibraries>  
        <WholeProgramOptimization>true</WholeProgramOptimization>  
        <PlatformToolset>v140</PlatformToolset>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
  
    ```  
  
6.  Değişikliklerinizi kaydedin. Ardından Proje dosyasını kapatın.  
  
7.  Çözüm Gezgini proje dosyanıza sağ tıklayın ve bağlam menüsünden projeyi seçin. Projenizdeki tüm dosyaları artık Çözüm Gezgini içinde görüntülenmesi gerekir.  
  
     İçin adımları takip etmeniz artık [paket bildirim dosyalarını güncelleştirme](#PackageManifest) tüm Windows Store 8.1 veya Windows Phone 8.1 projeleri için.  
  
##  <a name="PackageManifest"></a> Tüm Windows Store 8.1 veya Windows Phone 8.1 projeleri için paket bildirim dosyasını güncelleştirme  
 Çözümünüzde her proje için paket bildirim dosyasını güncelleştirmeniz gerekir.  
  
#### <a name="update-your-package-manifest-file"></a>Paket bildirim dosyanızı güncelleştirin  
  
1. Package.appxmanifest dosyasını açın. Her biri, Windows Store ve Windows Phone projeleri için Package.AppxManifest dosyasını düzenlemeniz gerekebilir.  
  
2. Güncelleştirmeye gerek duyduğunuz \<paket > Yeni şemaları öğeyle mevcut proje türünüz temel. İlk Windows Store veya Windows Phone projesi olup olmadığına göre aşağıdaki şemaları kaldırın.  
  
    **Windows Store projesi için eski:** , \<paket > öğesi şuna benzer görünür.  
  
   ```xml  
   <Package  
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"     
       xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest">  
  
   ```  
  
    **Windows Phone projesi için eski:** , \<paket > öğesi şuna benzer görünür.  
  
   ```xml  
   <Package  
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"     
   xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest"  
   xmlns:m3="http://schemas.microsoft.com/appx/2014/manifest"  
   xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest">  
   ```  
  
    **Evrensel Windows platformu için yeni:** aşağıdaki şema eklemek, \<paket > öğesi. Tüm ilişkili ad alanı tanımlayıcısı ön ekleri için az önce kaldırdığınız şemaları öğeleri kaldırın. IgnorableNamespaces özelliğini güncelleştirin: uap mp. Yeni \<paket > öğesi şuna benzer görünmelidir.  
  
   ```xml  
   <Package  
       xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"  
       xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"  
       xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"  
      IgnorableNamespaces= "uap mp">  
  
   ```  
  
3. Ekleme bir \<bağımlılıkları > alt öğe \<paket > öğesi. Ardından Ekle bir \<TargetDeviceFamily > alt öğe bu \<bağımlılıkları > öğesi adı, MinVersion ve MaxVersionTested özniteliklere sahip. Ad özniteliği değeri vermek: Windows.Universal. MinVersion ve MaxVersionTested yüklediğiniz Evrensel Windows platformu sürümü değerini verin. Bu öğe, şuna benzer görünmelidir:  
  
   ```xml  
   <Dependencies>  
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10069.0" MaxVersionTested="10.0.10069.0" />  
   </Dependencies>  
   ```  
  
4. **Yalnızca Windows Store için:** eklemenize gerek bir \<mp:PhoneIdentity > alt öğe \<paket > öğesi. Bir PhoneProductId ve PhonePublisherId özniteliklerini ekleyin. Ad özniteliği ile aynı değere sahip PhoneProductId ayarlamak \<kimlik > öğesi. PhonePublishedId değerini şuna ayarlayın: 00000000-0000-0000-0000-000000000000. Böyle:  
  
   ```xml  
   <Identity Name="aa3815a1-2d97-4c71-8c99-578135b28cd8" Publisher="CN=xxxxxxxx" Version="1.0.0.0" />   
   <mp:PhoneIdentity PhoneProductId="aa3815a1-2d97-4c71-8c99-578135b28cd8" PhonePublisherId="00000000-0000-0000-0000-000000000000"/>  
   ```  
  
5. Bulma \<önkoşulları > öğesi ve bu öğeyi ve bunun tüm alt öğeleri silin.  
  
6. Ekleme **uap** ad alanına aşağıdaki \<kaynak > öğeleri: DXFeatureLevel, ölçeklendirin. Örneğin:  
  
   ```xml  
   <Resources>  
     <Resource Language="en-us"/>  
    <Resource uap:Scale="180"/>  
    <Resource uap:DXFeatureLevel="dx11"/>  
   </Resources>  
  
   ```  
  
7. Ekleme **uap** ad alanına aşağıdaki \<yeteneği > öğeleri: documentsLibrary, picturesLibrary, videosLibrary, musicLibrary, enterpriseAuthentication, sharedUserCertificates, removableStorage, randevular ve kişiler. Örneğin:  
  
   ```xml  
   <Capabilities>  
     <uap:Capability Name="documentsLibrary"/>  
     <uap:Capability Name="removableStorage"/>  
   </Capabilities>  
  
   ```  
  
8. Ekleme **uap** ad alanına \<VisualElements > öğesi ve tüm alt öğeleri. Örneğin:  
  
   ```xml  
   <uap:VisualElements  
       DisplayName="My WWA App"  
       Square150x150Logo="images/150x150.png"  
       Square44x44Logo="images/44x44.png"  
       Description="My WWA App"  
       BackgroundColor="#777777">  
     <uap:SplashScreen Image="images/splash.png"/>  
   </uap:VisualElements>  
  
   ```  
  
    **Yalnızca Windows Store için geçerlidir:** döşeme boyutu adları değiştirilmiştir. Öznitelikleri değiştirmek \<VisualElements > yakınsanmış kutucuk boyutlarından seçim yaparak yeni yansıtacak şekilde öğesi. 70 x 70 71 x 71 haline gelir ve 30 x 30 44 x 44 haline gelir.  
  
    **Eski:** döşeme boyutu adları  
  
   ```xml  
   <m2:VisualElements  
       …  
       Square30x30Logo="Assets\SmallLogo.png"  
       …>  
    <m2:DefaultTile  
         …  
         Square70x70Logo="images/70x70.png">  
   </m2:VisualElements>  
  
   ```  
  
    **Yeni:** döşeme boyutu adları  
  
   ```xml  
   <uap:VisualElements  
       …  
       Square44x44Logo="Assets\SmallLogo.png"  
       …>  
    <uap:DefaultTile  
         …  
         Square71x71Logo="images/70x70.png">  
   </uap:VisualElements>  
  
   ```  
  
9. Ekleme **uap** ad alanına \<ApplicationContentUriRules > ve onun tüm alt öğeleri. Örneğin:  
  
    ```xml  
    <uap:ApplicationContentUriRules>  
      <uap:Rule Type="include" Match="https://www.microsoft.com/"/>  
      <uap:Rule Type="exclude" Match="*.pdf"/>  
    </uap:ApplicationContentUriRules>  
  
    ```  
  
10. Ekleme **uap** ad alanına aşağıdaki \<uzantısı > öğeleri ve tüm alt öğeleri: windows.accountPictureProvide, windows.alarm windows.appointmentsProvider windows.autoPlayContent  windows.autoPlayDevice windows.cachedFileUpdate, windows.cameraSettings, windows.fileOpenPicker, windows.fileTypeAssociation, windows.fileSavePicke, windows.lockScreenCall, windows.printTaskSettings, windows.protocol, windows.search, windows.shareTarget. Örneğin:  
  
    ```xml  
    <Extensions>  
      <uap:Extension Category="windows.alarm"/>  
      <uap:Extension Category="windows.search" EntryPoint="MyActivateableClassId.baz"/>  
      <uap:Extension Category="windows.protocol">  
        <uap:Protocol Name="mailto" DesiredView="useHalf">  
         <uap:DisplayName>MailTo Protocol</uap:DisplayName>  
        </uap:Protocol>  
      </uap:Extension>  
    </Extensions>  
  
    ```  
  
11. Ekleme **uap** türü chatMessageNotification arka plan görevleri için ad alanı. Örneğin:  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">  
     <BackgroundTasks ServerName="MyBackgroundTasks">  
        <uap:Task Type="chatMessageNotification"/>  
      </BackgroundTasks>  
    </Extension>  
  
    ```  
  
12. Çerçeve bağımlılıklarını değiştirin. Bir yayımcı adı tümüne Ekle \<PackageDependency > öğeleri ve bir MinVersion zaten belirtilmişse belirtin.  
  
     **Eski:** \<PackageDependency > öğesi  
  
    ```xml  
    <Dependencies>  
     <PackageDependency Name="Microsoft.VCLibs.120.00" />  
    </Dependencies>  
  
    ```  
  
     **Yeni:** \<PackageDependency > öğesi  
  
    ```xml  
    <Dependencies>  
     <PackageDependency  
          Name="Microsoft.VCLibs.120.00"  
          Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"  
          MinVersion="12.0.30113.0" />  
    </Dependencies>  
  
    ```  
  
     Uygun yayımcı ve MinVersion değerleri, kullanmakta olduğunuz gerçek çerçevesini kullanın. Windows 10 için bu adlar değişebileceğini unutmayın.  
  
13. GattCharacteristicNotification ve rfcommConnection arka plan türü görevleri Bluetooth türü görev ile değiştirin. Örneğin:  
  
     **ESKİ:**  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">  
    <BackgroundTasks ServerName="MyBackgroundTasks">  
                <Task Type="rfcommConnection"/>  
               <Task Type="gattCharacteristicNotification"/>  
    </BackgroundTasks>  
    </Extension>  
    ```  
  
     **Yeni:** Bluetooth türü görev ile.  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">  
    <BackgroundTasks ServerName="MyBackgroundTasks">  
               <Task Type="bluetooth"/>  
    </BackgroundTasks>  
    </Extension>  
    ```  
  
14. Bluetooth cihaz özellikleri bluetooth.rfcomm ve bluetooth.genericAttributeProfile ile genel bir Bluetooth özelliğini değiştirin. Örneğin:  
  
     **ESKİ:**  
  
    ```xml  
    <Capabilities>  
      <m2:DeviceCapability Name="bluetooth.rfcomm">  
        <m2:Device Id="any">  
         <m2:Function Type="serviceId:34B1CF4D-1069-4AD6-89B6-E161D79BE4D8"/>  
        </m2:Device>  
      </m2:DeviceCapability>  
      <m2:DeviceCapability Name="bluetooth.genericAttributeProfile">  
        <m2:Device Id="any">  
         <m2:Function Type="name:heartRate"/>  
        </m2:Device>  
      </m2:DeviceCapability>  
    </Capabilities>  
    ```  
  
     **Yeni:** genel bir Bluetooth özelliği ile değiştirildi.  
  
    ```xml  
    <Capabilities>  
      <uap:DeviceCapability Name="bluetooth"/>  
    </Capabilities>  
  
    ```  
  
15. Kullanım dışı öğeleri kaldırın.  
  
    1. Bu öznitelikler için \<VisualElements > kullanım dışı bırakılmıştır ve kaldırılması gerekiyor:  
  
       - \<VisualElements > öznitelikleri: ForegroundText, ToastCapable  
  
       - \<DefaultTile > DefaultSize özniteliği  
  
       - \<ApplicationView > öğesi  
  
         Örneğin:  
  
       ```xml  
       <m2:VisualElements  
           …  
           ForegroundText="dark"  
           ToastCapable="true">  
       <m2:DefaultTile DefaultSize="square150x150Logo"/>  
         <m2:ApplicationView MinWidth="width320"/>  
       </m2:VisualElements>  
  
       ```  
  
    2. Windows.Contact ve windows.contactPicker uzantıları ve bu uzantıları altındaki tüm öğeleri kaldırın.  
  
16. Package.appxmanifest dosyasını kaydedin. Ardından Visual Studio'yu kapatın.  
  
17. Bazı gizli dosyalar çözümünüzü yeniden açmadan önce kaldırmanız gerekir.  
  
    1.  Dosya Gezgini'ni açın, **görünümü** seçip araç **öğelerin gizli** ve **dosya adı uzantıları**. Makinenizde şu dosyayı açın: \<konumun çözümünüzün yolu >\\.vs\\{proje adı} \v14. .Suo dosya uzantılı bir dosya varsa, onu silin.  
  
    2.  Şimdi geri çözümünüzü bulunduğu klasöre gidin. Çözümünüzde mevcut projeler için herhangi bir klasörde açın. Klasörler aşağıdakilerden herhangi biri içinde bir dosya proje sahipse bir. csproj.user veya. vbproj.user uzantısını silin.  
  
         Artık Visual Studio'da çözümünüzü yeniden açabilirsiniz. Kod, derleme ve evrensel Windows platformu kullanarak uygulamanızda hata ayıklama hazır olursunuz.  
  
         Bilgi nasıl [kodunuzu uyum](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx) Evrensel Windows Platform ile yenilikleri avantajlarından yararlanmak için.  
  
##  <a name="PreviousVersions"></a> Visual Studio 2015 RC ile oluşturulmuş mevcut bir evrensel Windows uygulamaları için gerekli değişiklikleri  
 Visual Studio 2015 RC ile Windows 10 Evrensel uygulamaları oluşturduysanız, projenizi Visual Studio 2015'in en son sürümüyle yüklü Evrensel Windows platformu sürümünü kullanacak şekilde yeniden hedeflemek gerekir. Herhangi bir önceki sürümü desteklenmiyor. Gerekli değişiklikler, uygulamanızı oluşturmak için kullandığınız dile bağlı olarak farklılık gösterir:  
  
-   [C# /VB uygulamaları](#RCUpdate10CSharp)  
  
-   [C++ uygulamaları](#RCUpdate10CPlusPlus)  
  
###  <a name="RCUpdate10CSharp"></a> C# /VB projelerinizi en son Evrensel Windows Platformu'nu kullanmak için güncelleştirme  
 Mevcut uygulamanızı çözümünüzü açın, uygulamanız için bir güncelleştirme gerekli olduğunu görürsünüz:  
  
 ![Çözüm Gezgini'nde projenizi görüntülemek](../misc/media/uwp-updaterequired.png "UWP_UpdateRequired")  
  
 Çözüm Gezgini'nden bu projeyi tekrar yüklemek isterseniz, bu iletişim kutusunu görürsünüz:  
  
 ![Doğru SDK'yı kullanmak için uygulamanızı yeniden hedefle](../misc/media/missingsdkforuap.png "MissingSDKforUAP")  
  
 Projeniz için evrensel Windows Platform SDK artık olduğundan desteklenmeyen, yüklemek mümkün olmayacaktır. Yalnızca Tamam'ı tıklatın ve ardından aşağıdaki adımları izleyin.  
  
##### <a name="update-your-cvb-projects-to-use-the-latest-universal-windows-platform"></a>C# /VB projelerinizi en son Evrensel Windows Platformu'nu kullanmak için güncelleştirme  
  
1. Yüklediğiniz hangi Evrensel Windows platformu bulmak için şu dosyayı açın: **\Program dosyaları (x86) \Windows Kits\10\Platforms\UAP**. Bu, yüklü Evrensel her Windows platformu için klasörlerin listesini içerir. Klasör adı yüklemiş olduğunuz Evrensel Windows platformu sürümüdür. Örneğin, bu Windows 10 cihazına yüklü sürüm 10.0.10240.0 Evrensel Windows platformu vardır.  
  
    ![Yüklü sürüm görüntülemek için klasörü açın](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
    Evrensel Windows platformu birden çok sürümü yüklenebilir. Uygulamanız için en son sürümünü kullanmanızı öneririz.  
  
2. Dosya Gezgini'ni kullanarak UWP projenizin depolandığı klasöre gidin. Dosya packages.config silin ve bu klasöre yeni bir .json dosyası oluşturun. Dosya adı: project.json ve ardından bu dosyaya aşağıdaki içeriği ekleyin:  
  
   ```json  
  
   {  
     "dependencies": {  
       "Microsoft.ApplicationInsights": "1.0.0",  
       "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",  
       "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",  
       "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"  
     },  
     "frameworks": {  
       "uap10.0": {}  
     },  
     "runtimes": {  
       "win10-arm": {},  
       "win10-arm-aot": {},  
       "win10-x86": {},  
       "win10-x86-aot": {},  
       "win10-x64": {},  
       "win10-x64-aot": {}  
     }  
   }  
  
   ```  
  
3. Visual Studio ile C# /VB Evrensel Windows uygulamanızı içeren çözümünüzü açın. Proje dosyanız (.csproj veya .vbproj dosyası) güncelleştirilmesi gerektiğini görürsünüz. Proje dosyasını sağ tıklayın ve bu dosyayı düzenlemek seçin.  
  
    ![Projeye sağ tıklayın ve Düzen](../misc/media/uap-editproject.png "UAP_EditProject")  
  
4. Bulma \<PropertyGroup > öğesini içeren \<TargetPlatformVersion > ve \<TargetPlatformMinVersion > öğeleri. Mevcut değiştirin \<TargetPlatformVersion > ve \<TargetPlatformMinVersion > yüklediğiniz Evrensel Windows platformu aynı sürümde olması için öğeleri.  
  
    Evrensel Windows uygulamaları için varsayılan varlık ölçek 200'dür. 100 ile ölçeği dahil Visual Studio 2015 RC varlıklar ile oluşturulan projeleri, ihtiyaç duyacağınız eklemek bir \<UapDefaultAssetScale > Bu PropertyGroup 100 değerini içeren öğe. Daha fazla bilgi edinin [varlıklar ve ölçekler](http://msdn.microsoft.com/library/jj679352.aspx).  
  
5. UWP uzantı SDK'ları herhangi bir referansı eklediyseniz (örneğin: Windows Mobile SDK'sı), SDK sürümü güncelleştirmeniz gerekecektir. Örneğin bu \<SDKReference > öğesi:  
  
   ```xml  
   <SDKReference Include="WindowsMobile, Version=10.0.0.1">  
         <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>  
   </SDKReference>  
  
   ```  
  
    Bu değiştirilmelidir:  
  
   ```xml  
   <SDKReference Include="WindowsMobile, Version=10.0.10240.0">  
         <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>  
   </SDKReference>  
  
   ```  
  
6. Bulma \<hedef > değeri olan bir ad özniteliği olan öğe: EnsureNuGetPackageBuildImports. Bu öğenin ve tüm alt öğelerini silin.  
  
   ```xml  
   <Target Name="EnsureNuGetPackageBuildImports" BeforeTargets="PrepareForBuild">  
       <PropertyGroup>  
         <ErrorText>This project references NuGet package(s) that are missing on this computer. Use NuGet Package Restore to download them.  For more information, see http://go.microsoft.com/fwlink/?LinkID=322105. The missing file is {0}.</ErrorText>  
       </PropertyGroup>  
       <Error Condition="!Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets'))" />  
       <Error Condition="!Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets'))" />  
   </Target>  
   ```  
  
7. Bulup silmesine \<alma > öğeleri proje ve koşul öznitelikleriyle gt;Microsoft.Diagnostics.tracing.EventSource ve Microsoft.applicationınsights, başvuru şöyle:  
  
   ```xml  
   <Import Project="..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets" Condition="Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" />  
   <Import Project="..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets" Condition="Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" />  
  
   ```  
  
8. Bulma \<ItemGroup > olan \<başvuru > NuGet paketlerine alt öğeleri. Bir sonraki adım için bu bilgiler gerekeceğinden, başvurulan, NuGet paketlerini not alın. Bir Windows 10 proje biçimi Visual Studio 2015 RC ve Visual Studio 2015 RTM arasında arasında önemli bir fark RTM biçimini kullandığını [NuGet](http://docs.nuget.org/) sürüm 3.  
  
    Kaldırma \<ItemGroup > ve tüm alt öğeleri. Örneğin, Visual Studio RC ile oluşturulmuş bir UWP projesi kaldırılması gereken aşağıdaki NuGet paketlerini olacaktır:  
  
   ```xml  
   <ItemGroup>  
       <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
         <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>  
         <Private>True</Private>  
       </Reference>  
       <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
         <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>  
         <Private>True</Private>  
       </Reference>  
       <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
         <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>  
         <Private>True</Private>  
       </Reference>  
       <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">  
         <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>  
         <Private>True</Private>  
       </Reference>  
       <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">  
         <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>  
         <Private>True</Private>  
       </Reference>  
     </ItemGroup>  
  
   ```  
  
9. Bulma \<ItemGroup > öğesini içeren bir \<AppxManifest > öğesi. Varsa bir \<yok > kümesine bir dahil etme özniteliği olan öğe: packages.config, silin. Ayrıca, bir \<yok > öğesi ile bir dahil etme özniteliği ve değerini ayarlamak: project.json.  
  
10. Değişikliklerinizi kaydedin. Ardından Proje dosyasını kapatın.  
  
11. Çözüm Gezgini proje dosyanıza sağ tıklayın ve bağlam menüsünden projeyi seçin. Projenizdeki tüm dosyaları artık Çözüm Gezgini içinde görüntülenmesi gerekir.  
  
12. Çözüm Gezgini'nde Applicationınsights.config dosyasını seçin ve özelliklerini açın. Derleme eylemi özelliğini "İçerik" ve kopya "Yeniyse Kopyala" çıkış dizini özelliğini ayarlayın.  
  
13. Package.appxmanifest dosyasını açın.  
  
    1.  Bulma \<TargetDeviceFamily > öğesi. Yüklemiş olduğunuz Evrensel Windows platformu sürümüne karşılık olarak MinVersion ve MaxVersionTested özniteliklerini değiştirin. Böyle:  
  
        ```xml  
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />  
        ```  
  
    2.  Değişikliklerinizi kaydedin.  
  
14. Önceki adımda sildiğiniz paketleri eklemek için NuGet Yöneticisi'ni kullanın. Bir Windows 10 proje biçimi Visual Studio 2015 RC ve Visual Studio 2015 RTM arasında arasında önemli bir fark RTM biçimini kullandığını [NuGet](http://docs.nuget.org/) sürüm 3.  
  
    Artık, kod, derleme ve uygulamanızda hata ayıklama.  
  
    Evrensel Windows uygulamaları için birim testi projelerini varsa, ayrıca izlemeniz gereken [adımları](#MigrateUnitTest).  
  
###  <a name="RCUpdate10CPlusPlus"></a> C++ projelerinizin en yeni evrensel Windows platformu Kullan'ı güncelleştirme  
  
1.  Yüklediğiniz hangi Evrensel Windows platformu bulmak için şu dosyayı açın: **\Program dosyaları (x86) \Windows Kits\10\Platforms\UAP**. Bu, yüklü Evrensel her Windows platformu için klasörlerin listesini içerir. Klasör adı yüklemiş olduğunuz Evrensel Windows platformu sürümüdür. Örneğin, bu Windows 10 cihazına yüklü sürüm 10.0.10240.0 Evrensel Windows platformu vardır.  
  
     ![Yüklü sürüm görüntülemek için klasörü açın](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
     Evrensel Windows platformu birden çok sürümü yüklenebilir. Uygulamanız için en son sürümünü kullanmanızı öneririz.  
  
2.  C++ Evrensel Windows uygulamanızı içeren çözümünüzü açın. Proje .vcxproj dosyasını sağ tıklayın ve proje dosyasını kaldırmak seçin. Proje kaldırıldı sonra proje dosyasını tekrar sağ tıklayın ve düzenlemek seçin.  
  
     ![Projeyi kaldırmak ve ardından Proje dosyasını düzenleyerek](../misc/media/uap-editearliercplus.png "UAP_EditEarlierCPlus")  
  
3.  Bulma \<PropertyGroup > bir koşul özniteliği içermeyen ancak içeren öğeleri bir \<ApplicationTypeRevision > öğesi. 8.2 ApplicationTypeRevision değerinden 10.0 için güncelleştirin. Ekleme bir \<WindowsTargetPlatformVersion > ve \<WindowsTargetPlatformMinVersion > öğe ve değer Evrensel Windows platformu sürümünün yüklü olmasını değerlerine ayarlayın.  
  
     Ekleme bir \<EnableDotNetNativeCompatibleProfile > öğesi ve değerini, öğenin zaten mevcut değilse true olarak ayarlayın.  
  
     Evrensel Windows uygulamaları için varsayılan varlık ölçek 200'dür. 100 ile ölçeği dahil Visual Studio 2015 RC varlıklar ile oluşturulan projeleri, ihtiyaç duyacağınız eklemek bir \<UapDefaultAssetScale > Bu PropertyGroup 100 değerini içeren öğe. Daha fazla bilgi edinin [varlıklar ve ölçekler](http://msdn.microsoft.com/library/jj679352.aspx).  
  
     Bu nedenle bu \<PropertyGroup > öğesi şimdi şuna benzer olacaktır:  
  
    ```xml  
    <PropertyGroup Label="Globals">  
        …  
        <MinimumVisualStudioVersion>14.0</MinimumVisualStudioVersion>  
        <ApplicationType>Windows Store</ApplicationType>  
        <ApplicationTypeRevision>10.0</ApplicationTypeRevision>  
        <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>  
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>  
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
        <UapDefaultAssetScale>100</UapDefaultAssetScale>  
      </PropertyGroup>  
  
    ```  
  
4.  Her kalan \<PropertyGroup > öğesinde, bir yayın yapılandırmasına sahip bir koşul özniteliği öğe olup olmadığını denetleme. Bunu yapar, ancak içermediğinden bir \<UseDotNetNativeToolchain > öğesi, bir ekleyin. Değerini \<UseDotNetNativeToolchain > öğesini true, şöyle:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">  
        <ConfigurationType>Application</ConfigurationType>  
        <UseDebugLibraries>false</UseDebugLibraries>  
        <WholeProgramOptimization>true</WholeProgramOptimization>  
        <PlatformToolset>v140</PlatformToolset>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
  
    ```  
  
5.  Güncelleştirmeye gerek duyduğunuz \<EnableDotNetNativeCompatibleProfile > öğesi ve \<UseDotNetNativeToolchain > öğesi .NET Native ve .NET Native etkinleştirmek için C++ şablonlarında etkin değil.  
  
     Değişikliklerinizi kaydedin. Ardından Proje dosyasını kapatın.  
  
6.  Çözüm Gezgini proje dosyanıza sağ tıklayın ve bağlam menüsünden projeyi seçin. Projenizdeki tüm dosyaları artık Çözüm Gezgini içinde görüntülenmesi gerekir.  
  
7.  Package.appxmanifest dosyasını açın.  
  
    1.  Bulma \<TargetDeviceFamily > öğesi. Yüklemiş olduğunuz Evrensel Windows platformu sürümüne karşılık olarak MinVersion ve MaxVersionTested özniteliklerini değiştirin. Böyle:  
  
        ```xml  
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />  
        ```  
  
    2.  Değişikliklerinizi kaydedin.  
  
         Artık, kod, derleme ve uygulamanızda hata ayıklama.  
  
         Evrensel Windows uygulamaları için birim testi projelerini varsa, ayrıca izlemeniz gereken [adımları](#MigrateUnitTest).  
  
##  <a name="MigrateUnitTest"></a> Mevcut Visual Studio 2015 RC ile oluşturulmuş Evrensel Windows uygulamaları için birim testi projeleri için gerekli değişiklikleri  
 Birim testi projeleri Windows 10 Evrensel uygulamaları için Visual Studio 2015 RC ile oluşturduğunuz projenize bu ek değişiklikler yapmanız gerekirse bunları kullanmak için dosyaları test projeleri Visual Studio 2015'in en son sürüm ile. Gerekli değişiklikler, uygulamanızı oluşturmak için kullandığınız dile bağlı olarak farklılık gösterir:  
  
-   [C# /VB uygulamaları](#UnitTestRCUpdate10CSharp)  
  
-   [C++ uygulamaları](#UnitTestRCUpdate10CPlusPlus)  
  
###  <a name="UnitTestRCUpdate10CSharp"></a> C# /VB birim testi projelerini güncelleştirme  
  
1. Visual Studio ile C# /VB birim testi projesi içeren çözümünüzü açın. Değiştirin \<OuttputType > öğesine: AppContainerExe.  
  
   ```xml  
  
   <OutputType>AppContainerExe</OutputType>  
  
   ```  
  
2. Bu öğeyi değiştirin \<EnableCoreRuntime > false\</EnableCoreRuntime > öğesi ile:  
  
   ```xml  
  
   <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
  
   ```  
  
3. Aşağıdaki satırları kaldırın:  
  
   ```xml  
  
   <PropertyGroup>  
       <AppXPackage>True</AppXPackage>  
       <AppxPackageIncludePrivateSymbols>true</AppxPackageIncludePrivateSymbols>  
    </PropertyGroup>  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
    <PlatformTarget>AnyCPU</PlatformTarget>  
    <DebugSymbols>true</DebugSymbols>  
    <DebugType>full</DebugType>  
    <Optimize>false</Optimize>  
    <OutputPath>bin\Debug\</OutputPath>  
    <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
    <ErrorReport>prompt</ErrorReport>  
    <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
       <PlatformTarget>AnyCPU</PlatformTarget>  
       <DebugType>pdbonly</DebugType>  
       <Optimize>true</Optimize>  
       <OutputPath>bin\Release\</OutputPath>  
       <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
       <ErrorReport>prompt</ErrorReport>  
       <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
  
   ```  
  
4. Bu öğe ekleme \<UseDotNetNativeToolchain > true\</UseDotNetNativeToolchain > Bu özelliği gruplara bir alt öğesi olarak:  
  
   ```xml  
  
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|ARM'">  
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X86'">  
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X64'">  
  
   ```  
  
5. Aşağıdaki Sil \<ItemGroup > öğeleri:  
  
   ```xml  
  
   <ItemGroup>  
      <Compile Include="Properties\AssemblyInfo.cs" />  
      <Compile Include="UnitTest.cs" />  
   </ItemGroup>  
   <ItemGroup>  
      <AppxManifest Include="Package.appxmanifest">  
         <SubType>Designer</SubType>  
      </AppxManifest>  
      <None Include="packages.config" />  
      <None Include="UnitTestProject1_TemporaryKey.pfx" />  
   </ItemGroup>  
   <ItemGroup>  
      <Content Include="Properties\Default.rd.xml" />  
      <Content Include="Assets\Logo.scale-240.png" />  
      <Content Include="Assets\SmallLogo.scale-240.png" />  
      <Content Include="Assets\SplashScreen.scale-240.png" />  
      <Content Include="Assets\Square71x71Logo.scale-240.png" />  
      <Content Include="Assets\StoreLogo.scale-240.png" />  
      <Content Include="Assets\WideLogo.scale-240.png" />  
   </ItemGroup>  
  
   ```  
  
    Bunları, bu öğeleri ile değiştirin:  
  
   ```xml  
  
   <ItemGroup>  
      <Compile Include="Properties\AssemblyInfo.cs" />  
      <Compile Include="UnitTestApp.xaml.cs">  
         <DependentUpon>UnitTestApp.xaml</DependentUpon>  
      </Compile>  
      <Compile Include="UnitTest.cs" />  
   </ItemGroup>  
   <ItemGroup>  
      <ApplicationDefinition Include="UnitTestApp.xaml">  
         <Generator>MSBuild:Compile</Generator>  
         <SubType>Designer</SubType>  
      </ApplicationDefinition>  
   </ItemGroup>  
   <ItemGroup>  
      <AppxManifest Include="Package.appxmanifest">  
         <SubType>Designer</SubType>  
      </AppxManifest>  
      <None Include="UnitTestProject1_TemporaryKey.pfx" />  
   </ItemGroup>  
   <ItemGroup>  
      <Content Include="Properties\UnitTestApp.rd.xml" />  
      <Content Include="Assets\LockScreenLogo.scale-200.png" />  
      <Content Include="Assets\SplashScreen.scale-200.png" />  
      <Content Include="Assets\Square150x150Logo.scale-200.png" />  
      <Content Include="Assets\Square44x44Logo.scale-200.png" />  
      <Content Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />  
      <Content Include="Assets\StoreLogo.png" />  
      <Content Include="Assets\Wide310x150Logo.scale-200.png" />  
   </ItemGroup>  
   ```  
  
6. Yeni bir birim testi projesi oluşturun ve UnitTestApp.xaml ve UnitTestApp.xaml.cs dosyaları bu yeni proje oluştur güncelleştirmekte olduğunuz mevcut birim test projenize kopyalayın.  
  
7. UnitTestApp.rd.xml dosyayı yeni birim testi projesinin özellikleri klasöründen güncelleştirmekte olduğunuz mevcut birim testi projesi özellikleri klasörüne kopyalayın.  
  
8. Package.appxmanifest dosyasını açın. Ardından bu öğeleri, ondan silin:  
  
   ```xml  
  
   <Applications>  
      <Application Id="vstest.executionengine.universal.App"  
            Executable="vstest.executionengine.appcontainer.uap.exe"  
            EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">  
         <uap:VisualElements  
            DisplayName="UnitTestProject1"  
            Square150x150Logo="Assets\Logo.png"  
            Square44x44Logo="Assets\SmallLogo.png"  
            Description="UnitTestProject1"  
            BackgroundColor="#464646">  
            <uap:SplashScreen Image="Assets\SplashScreen.png" />  
         </uap:VisualElements>  
      </Application>  
   </Applications>  
   <Capabilities>  
      <Capability Name="internetClientServer" />  
   </Capabilities>  
   ```  
  
    Bu silinen öğeleri aşağıdaki öğeleri ile değiştirin. Aşağıdaki öğeleri UnitTestProject1 yerine projenizin adına dayanarak ProjectName için uygun değeri kullanın:  
  
   ```xml  
  
   <Applications>  
      <Application Id="vstest.executionengine.universal.App"   
            Executable="$targetnametoken$.exe"  
            EntryPoint="UnitTestProject1.App">  
         <uap:VisualElements  
               DisplayName="UnitTestProject1"  
               Square150x150Logo="Assets\Square150x150Logo.png"  
               Square44x44Logo="Assets\Square44x44Logo.png"  
               Description="UnitTestProject1"  
               BackgroundColor="transparent">  
            <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>  
            <uap:SplashScreen Image="Assets\SplashScreen.png" />  
         </uap:VisualElements>  
      </Application>  
   </Applications>  
   <Capabilities>  
      <Capability Name="internetClient" />  
   </Capabilities>  
   ```  
  
   Artık, birim testleri çalıştırabilirsiniz.  
  
###  <a name="UnitTestRCUpdate10CPlusPlus"></a> C++ projelerinizin en yeni evrensel Windows platformu Kullan'ı güncelleştirme  
  
1.  Visual Studio ile C++ birim test projenizi içeren çözümünüzü açın. Aşağıdaki öğeleri kaldırın:  
  
    ```xml  
  
    <TestApplication>true</TestApplication>  
    <AppxPackage>True</AppxPackage>  
    <CppWindowsStoreUnitTestLibraryType>true</CppWindowsStoreUnitTestLibraryType>  
    <EnableCoreRuntime>false</EnableCoreRuntime>  
  
    ```  
  
2.  Aşağıdaki \<ProjectConfiguration > Bu öğe aşağıdaki öğeleri \<ItemGroup etiket "ProjectConfigurations" = > değil zaten bu fille olmaları durumunda:  
  
    ```xml  
  
    <ProjectConfiguration Include="Debug|x64">  
       <Configuration>Debug</Configuration>  
       <Platform>x64</Platform>  
    </ProjectConfiguration>  
    <ProjectConfiguration Include="Release|x64">  
       <Configuration>Release</Configuration>  
       <Platform>x64</Platform>  
    </ProjectConfiguration>  
  
    ```  
  
3.  Bu öğe her örneğini değiştirin:  
  
    ```xml  
  
    <ConfigurationType>DynamicLibrary</ConfigurationType>  
  
    ```  
  
     Şununla değiştirin:  
  
    ```xml  
  
    <ConfigurationType>Application</ConfigurationType>  
  
    ```  
  
4.  Bu ekleme \<PropertyGroup > değil zaten dosyasında olmaları durumunda öğeleri:  
  
    ```xml  
  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'" Label="Configuration">  
       <ConfigurationType>Application</ConfigurationType>  
       <UseDebugLibraries>true</UseDebugLibraries>  
       <PlatformToolset>v140</PlatformToolset>  
    </PropertyGroup>  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'" Label="Configuration">  
       <ConfigurationType>Application</ConfigurationType>  
       <UseDebugLibraries>false</UseDebugLibraries>  
       <WholeProgramOptimization>true</WholeProgramOptimization>  
       <PlatformToolset>v140</PlatformToolset>  
       <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
    </PropertyGroup>  
  
    ```  
  
5.  Bu öğe her örneğini değiştirin:  
  
    ```xml  
  
    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
    ```  
  
     Şununla değiştirin:  
  
    ```xml  
  
    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
  
    ```  
  
6.  Bu öğe her örneğini değiştirin:  
  
    ```xml  
  
    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\Lib;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
  
    ```  
  
     Şununla değiştirin:  
  
    ```xml  
  
    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
  
    ```  
  
7.  Bu ekleme \<Itemdefinitiongroup > diğer içeren bölümü öğelerinde \<Itemdefinitiongroup > öğeleri:  
  
    ```xml  
  
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">  
       <ClCompile>  
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>  
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>  
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%     (AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
       </ClCompile>  
    <Link>  
       <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
    </Link>  
    </ItemDefinitionGroup>  
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'">  
       <ClCompile>  
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>  
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>  
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
       </ClCompile>  
       <Link>  
          <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
       </Link>  
    </ItemDefinitionGroup>  
  
    ```  
  
8.  Aşağıdaki Sil \< ItemGroup > öğesi:  
  
    ```xml  
  
    <ItemGroup>  
       <Image Include="Assets\Logo.scale-100.png" />  
       <Image Include="Assets\SmallLogo.scale-100.png" />  
       <Image Include="Assets\StoreLogo.scale-100.png" />  
       <Image Include="Assets\SplashScreen.scale-100.png" />  
       <Image Include="Assets\WideLogo.scale-100.png" />  
    </ItemGroup>  
  
    ```  
  
     Bununla değiştirin \<ItemGroup > öğesi:  
  
    ```xml  
  
    <ItemGroup>  
       <Image Include="Assets\LockScreenLogo.scale-200.png" />  
       <Image Include="Assets\SplashScreen.scale-200.png" />  
       <Image Include="Assets\Square44x44Logo.scale-200.png" />  
       <Image Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />  
       <Image Include="Assets\Square150x150Logo.scale-200.png" />  
       <Image Include="Assets\StoreLogo.png" />  
       <Image Include="Assets\Wide310x150Logo.scale-200.png" />  
    </ItemGroup>  
  
    ```  
  
9. Aşağıdaki Sil \< ItemGroup > öğesi:  
  
    ```xml  
  
    <ItemGroup>  
       <ClInclude Include="pch.h" />  
    </ItemGroup>  
    ```  
  
     Bunları değiştirmek \<ItemGroup > öğeleri:  
  
    ```xml  
  
    <ItemGroup>  
       <ClInclude Include="pch.h" />  
       <ClInclude Include="UnitTestApp.xaml.h">  
          <DependentUpon>UnitTestApp.xaml</DependentUpon>  
       </ClInclude>  
    </ItemGroup>  
    <ItemGroup>  
       <ApplicationDefinition Include="UnitTestApp.xaml">  
          <SubType>Designer</SubType>  
       </ApplicationDefinition>  
    </ItemGroup>  
  
    ```  
  
10. Şu öğe silin:  
  
    ```xml  
    <ClCompile Include="UnitTest.cpp"/>  
    ```  
  
     Bunları değiştirmek \<CICompile > öğeleri:  
  
    ```xml  
  
    <ClCompile Include="UnitTestApp.xaml.cpp">  
       <DependentUpon>UnitTestApp.xaml</DependentUpon>  
    </ClCompile>  
    <ClCompile Include="UnitTest.cpp"/>  
  
    ```  
  
11. Bu öğe ekleyin:  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />  
    ```  
  
     Dosyasında bu öğe üzerinde:  
  
    ```xml  
  
    <ItemGroup>  
       <Xml Include="UnitTestApp.rd.xml" />  
    </ItemGroup>  
    ```  
  
12. Yeni Birim Test C++ projesi oluşturma ve UnitTestApp.xaml, UnitTestApp.xaml.cpp UnitTestApp.xaml.h ve UnitTestApp.rd.xml bu projeden güncelleştirmekte olduğunuz mevcut projenize kopyalayın.  
  
13. Package.appxmanifest dosyasını açın. Ardından bu öğeleri, ondan silin:  
  
    ```xml  
  
    <Applications>  
       <Application Id="vstest.executionengine.universal.App"  
             Executable="vstest.executionengine.appcontainer.uap.exe"  
             EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">  
          <uap:VisualElements  
             DisplayName="UnitTestProject1"  
             Square150x150Logo="Assets\Logo.png"  
             Square44x44Logo="Assets\SmallLogo.png"  
             Description="UnitTestProject1"  
             BackgroundColor="#464646">  
             <uap:SplashScreen Image="Assets\SplashScreen.png" />  
          </uap:VisualElements>  
       </Application>  
    </Applications>  
    <Capabilities>  
       <Capability Name="internetClientServer" />  
    </Capabilities>  
  
    ```  
  
     Bu silinen öğeleri aşağıdaki öğeleri ile değiştirin. Aşağıdaki öğeleri UnitTestProject1 yerine projenizin adına dayanarak ProjectName için uygun değeri kullanın:  
  
    ```xml  
  
    <Applications>  
       <Application Id="vstest.executionengine.universal.App"   
                Executable="$targetnametoken$.exe"  
                EntryPoint="UnitTestProject1.App">  
          <uap:VisualElements  
                DisplayName="UnitTestProject1"  
                Square150x150Logo="Assets\Square150x150Logo.png"  
                Square44x44Logo="Assets\Square44x44Logo.png"  
                Description="UnitTestProject1"  
                BackgroundColor="transparent">  
                <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>  
                <uap:SplashScreen Image="Assets\SplashScreen.png" />  
          </uap:VisualElements>  
       </Application>  
    </Applications>  
    <Capabilities>  
       <Capability Name="internetClient" />  
    </Capabilities>  
  
    ```