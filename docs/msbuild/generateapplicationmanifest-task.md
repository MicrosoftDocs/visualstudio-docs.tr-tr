---
title: GenerateApplicationManifest görevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateApplicationManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateApplicationManifest task
- HostInBrowser property (MSBuild)
- GenerateApplicationManifest task [MSBuild]
ms.assetid: a494102b-0cb2-4755-8e2a-d2c0f39fac1d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9526c2c62d9ace81127c61ef313cf55971fc1692
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888885"
---
# <a name="generateapplicationmanifest-task"></a>GenerateApplicationManifest görevi
Oluşturur bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildirimi ya da yerel bir bildirim. Yerel bir bildirim bileşene ilişkin benzersiz bir kimliği tanımlayarak ve tüm derlemeleri ve bileşeni oluşturan dosyaları tanımlayan bir bileşeni açıklar. A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildirimi, uygulamanın giriş noktasını gösteren ve uygulama güvenlik düzeyini belirterek yerel bildirimi genişletir.  

## <a name="parameters"></a>Parametreler  
 Parametreler için aşağıdaki tabloda açıklanmıştır `GenerateApplicationManifest` görev.  


| Parametre | Açıklama |
|---------------------------------| - |
| `AssemblyName` | İsteğe bağlı `String` parametresi.<br /><br /> Belirtir `Name` oluşturulan bildirim için derlemenin kimliğinin alan. Bu parametre belirtilmemişse, ad alanından algılanır `EntryPoint` veya `InputManifest` parametreleri. Ad oluşturulmazsa, görev bir hata oluşturur. |
| `AssemblyVersion` | İsteğe bağlı `String` parametresi.<br /><br /> Belirtir `Version` oluşturulan bildirim için derlemenin kimliğinin alan. Bu parametre belirtilmezse, varsayılan "1.0.0.0" değeri kullanılır. |
| `ClrVersion` | İsteğe bağlı `String` parametresi.<br /><br /> En düşük sürüm, ortak dil çalışma zamanı (uygulamanın gerektirdiği CLR) belirtir. Derleme sistemi tarafından kullanılan CLR sürümü varsayılan değerdir. Görev yerel bir bildirim oluşturuyorsa Bu parametre yoksayılır. |
| `ConfigFile` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Uygulama yapılandırma dosyasını hangi öğenin içerdiğini belirtir. Görev yerel bir bildirim oluşturuyorsa Bu parametre yoksayılır. |
| `Dependencies` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Üretilen bildirim için bağımlı derlemeler kümesini tanımlayan bir öğe listesini belirtir. Her öğenin daha fazla ek dağıtım durumunu ve bağımlılık türünü belirtmek için öğe meta verileri tarafından açıklanan. Daha fazla bilgi için [öğe meta verileri](#item-metadata). |
| `Description` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulama bileşeninin açıklamasını belirtir. |
| `EntryPoint` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Üretilen bildirim derlemesi için giriş noktasını gösteren tek bir öğeyi belirtir.<br /><br /> İçin bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildirimi, bu parametre uygulama çalıştırıldığında başlayan derlemeyi belirtir. |
| `ErrorReportUrl` | İsteğe bağlı <xref:System.String?displayProperty=fullName> parametresi.<br /><br /> ClickOnce yüklemelerindeki hata raporları sırasında iletişim kutularında görüntülenen web sayfasının URL'sini belirtir. |
| `FileAssociations` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> ClickOnce dağıtım bildirimi ile ilişkili bir veya daha fazla dosya türü listesini belirtir.<br /><br /> Yalnızca .NET Framework 3.5 veya üzeri hedeflendiğinde ilişkilendirmeleri, yalnızca geçerli dosya. |
| `Files` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Bildirime dahil edilecek dosyalar. Her bir dosyanın tam yolunu belirtin. |
| `HostInBrowser` | İsteğe bağlı <xref:System.Boolean> parametresi.<br /><br /> Varsa `true`, (WPF Web tarayıcı uygulamaları gibi), uygulama bir tarayıcıda barındırılır. |
| `IconFile` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Uygulama simge dosyasını belirtir. Uygulama simgesi, oluşturulan uygulama bildiriminde gösterilir ve kullanılan **Başlat menüsü** ve **Program Ekle/Kaldır** iletişim. Bu giriş belirtilmezse, varsayılan bir simge kullanılır. Görev yerel bir bildirim oluşturuyorsa Bu parametre yoksayılır. |
| `InputManifest` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Bildirim oluşturucu için bir temel olarak hizmet verecek girdi XML belgesini belirtir. Bu, uygulama güvenliği veya çıktı bildiriminde yansıtılmasını özel bildirim tanımları gibi yapılandırılmış verilerin sağlar. XML belgesi kök öğesi asmv1 ad alanı içerisinde bir derleme düğümü olmalıdır. |
| `IsolatedComReferences` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametresi.<br /><br /> Oluşturulan bildirimde ayrılacak COM bileşenlerini belirtir. Bu parametre "Kayıt içermeyen COM" dağıtımı için COM bileşenlerini ayırma özelliğini destekler. Otomatik-standart COM kayıt tanımları içeren bir bildirim oluşturarak çalışır. Ancak, COM bileşenleri düzgün şekilde çalışabilmesi bu sırayla yapı makinesinde kayıtlı olması gerekir. |
| `ManifestType` | İsteğe bağlı `String` parametresi.<br /><br /> Oluşturulacak bildirim türünü belirtir. Bu parametre aşağıdaki değerleri içerebilir:<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> Bu parametre belirtilmezse, görev için varsayılan olarak `ClickOnce`. |
| `MaxTargetPath` | İsteğe bağlı `String` parametresi.<br /><br /> Bir dosya yolu için izin verilen uzunluk üst sınırını belirtir bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama dağıtımı. Bu değer belirtilmişse uygulamadaki her dosya yolunun uzunluğu bu limite karşı denetlenir. Sınırı aşan öğeler bir yapı uyarısına neden olur. Bu giriş belirtilmezse veya sıfırsa, ardından hiçbir denetim yapılmaz. Görev yerel bir bildirim oluşturuyorsa Bu parametre yoksayılır. |
| `OSVersion` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın gerektirdiği en düşük gerekli işletim sistemi (OS) sürümünü belirtir. Örneğin, "5.1.2600.0" değeri, işletim sistemi Windows XP olduğunu gösterir. Bu parametre belirtilmezse, Windows 98 İkinci Sürüm gösteren "ü gösterin 4.10.0.0" değeri kullanılır, desteklenen en düşük .NET Framework'ün işletim sistemi. Görev yerel bir bildirim oluşturuyorsa bu giriş yoksayılır. |
| `OutputManifest` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> çıkış parametresi.<br /><br /> Oluşturulan çıktı bildirim dosyasının adını belirtir. Bu parametre belirtilmemişse, çıkış dosyasının adı oluşturulan bildirim kimliğinden gösterilir. |
| `Platform` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın hedef platformu belirtir. Bu parametre aşağıdaki değerleri içerebilir:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Bu parametre belirtilmezse, görev için varsayılan olarak `AnyCPU`. |
| `Product` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın adını belirtir. Bu parametre belirtilmemişse, ad oluşturulan bildirim kimliğinden gösterilir. Bu ad şirket kısayol adı için kullanılan **Başlat** menü ve görünen adın bir parçasıdır **Program Ekle veya Kaldır** iletişim kutusu. |
| `Publisher` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın yayımcısını belirtir. Bu parametre belirtilmemişse, ad kayıtlı kullanıcıdan veya oluşturulan bildirim kimliği algılanır. Bu ad üzerinde klasör adı için kullanılan **Başlat** menü ve görünen adın bir parçasıdır **Program Ekle veya Kaldır** iletişim kutusu. |
| `RequiresMinimumFramework35SP1` | İsteğe bağlı `Boolean` parametresi.<br /><br /> TRUE ise, uygulama .NET Framework 3.5 SP1 veya daha yeni bir sürümü gerektirir. |
| `TargetCulture` | İsteğe bağlı `String` parametresi.<br /><br /> Uygulamanın kültürünü tanıtır ve belirtir `Language` oluşturulan bildirim için derlemenin kimliğinin alan. Bu parametre belirtilmemişse uygulamanın kültür sabiti olduğu varsayılır. |
| `TargetFrameworkMoniker` | İsteğe bağlı `String` parametresi.<br /><br /> Hedef çerçeve adını belirtir. |
| `TargetFrameworkProfile` | İsteğe bağlı `String` parametresi.<br /><br /> Hedef Çerçeve profilini belirtir. |
| `TargetFrameworkSubset` | İsteğe bağlı `String` parametresi.<br /><br /> Hedef .NET Framework alt adını belirtir. |
| `TargetFrameworkVersion` | İsteğe bağlı `String` parametresi.<br /><br /> ' % S'hedef .NET Framework projesini belirtir. |
| `TrustInfoFile` | İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Uygulama güvenliğini belirten bir XML belgesini belirtir. XML belgesi kök öğesi asmv2 ad alanı içerisinde bir trustInfo düğümü olmalıdır. Görev yerel bir bildirim oluşturuyorsa Bu parametre yoksayılır. |
| `UseApplicationTrust` | İsteğe bağlı `Boolean` parametresi.<br /><br /> TRUE ise `Product`, `Publisher`, ve `SupportUrl` özellikleri uygulama bildirimine yazılır. |

## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelerin yanı sıra, bu görev parametreleri devralan <xref:Microsoft.Build.Tasks.GenerateManifestBase> kendisi sınıfının devraldığı <xref:Microsoft.Build.Utilities.Task> sınıfı. Görev sınıfı parametrelerinin bir listesi için bkz. [görev taban sınıfı](../msbuild/task-base-class.md).  

 Nasıl kullanılacağı hakkında daha fazla bilgi için `GenerateDeploymentManifest` görev bkz [GenerateApplicationManifest görevi](../msbuild/generateapplicationmanifest-task.md).  

 Bağımlılıklar ve dosyalar için girişler her öğe için ek dağıtım durumunu belirtmek için öğe meta verileri ile daha fazla donatılabilir.  

## <a name="item-metadata"></a>Öğe meta verileri  

|Meta veri adı|Açıklama|  
|-------------------|-----------------|  
|`DependencyType`|Bağımlılık yayımlanır ve uygulama ya da bir önkoşul ile yüklü olup olmadığını gösterir. Bu meta verileri tüm bağımlılıklar için geçerlidir, ancak dosyalar için kullanılmaz. Bu meta veriler için kullanılabilen değerler şunlardır:<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Yükleme varsayılan değerdir.|  
|`AssemblyType`|Bağımlılığın yönetilen olup veya yerel bir derleme belirtir. Bu meta verileri tüm bağımlılıklar için geçerlidir, ancak dosyalar için kullanılmaz. Bu meta veriler için kullanılabilen değerler şunlardır:<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> `Unspecified` Bildirim oluşturucu derleme türünü otomatik olarak belirleyeceğini gösteren varsayılan değerdir.|  
|`Group`|Ek dosyalar isteğe bağlı yükleme için grubu gösterir. Grup adı uygulama tarafından tanımlanabilir ve herhangi bir dize olabilir. Dosyanın varsayılan bir yükleme grubunun bölümü değil. boş bir dize belirtir. Grup içinde olmayan dosyalar ilk uygulama indirmesinin parçasıdır. Bir grup içindeki dosyalar yalnızca açıkça kullanan uygulama tarafından istendiğinde indirilen <xref:System.Deployment.Application>.<br /><br /> Bu meta veriler, tüm dosyalar için geçerlidir burada `IsDataFile` olduğu `false` ve tüm bağımlılıklarını burada `DependencyType` olduğu `Install`.|  
|`TargetPath`|Oluşturulan bildirimde yolun nasıl tanımlanmalıdır belirtir. Bu öznitelik tüm dosyalar için geçerlidir. Bu öznitelik belirtilmezse öğe belirtimi kullanılır. Bu öznitelik tüm dosya ve bağımlılıkları için geçerli bir `DependencyType` değerini `Install`.|  
|`IsDataFile`|A `Boolean` dosyayı bir veri dosyası olup olmadığını belirten bir meta veri değeri. Bir veri dosyası uygulama güncellemeleri arasında geçirildiğinden özeldir. Bu meta veriler yalnızca dosyalar için geçerlidir. `False` varsayılan değerdir.|  

## <a name="example"></a>Örnek  
 Bu örnekte `GenerateApplicationManifest` görev oluşturmak için bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildirimi ve `GenerateDeploymentManifest` tek derlemeli bir uygulama için bir dağıtım bildirimi oluşturmak için görev. Ardından kullanır `SignFile` bildirimleri imzalamak için bir görev.  

 Bu basit olası bildirim oluşturma senaryosunu göstermektedir burada [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bildirimleri, tek bir program için oluşturulur. Bildirimi için bir derlemeden bir varsayılan adını ve kimlik olayla.  

> [!NOTE]
>  Aşağıdaki örnekte, tüm uygulama ikilileri, bildirim oluşturma görünüşlerine odaklanabilmek için önceden oluşturulmuş. Bu örnek tam olarak çalışan üretir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım.  
> 
> [!NOTE]
>  Daha fazla bilgi için `Thumbprint` kullanılan özellik `SignFile` görev Bu örnekte, bkz: [SignFile görevi](../msbuild/signfile-task.md).  

```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  

    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  

    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  

    <Target Name="Build">  

        <GenerateApplicationManifest  
            EntryPoint="@(EntryPoint)">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  

        <GenerateDeploymentManifest  
            EntryPoint="@(ApplicationManifest)">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  

        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  

        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  

    </Target>  
</Project>  
```  

## <a name="example"></a>Örnek  
 Bu örnekte `GenerateApplicationManifest` ve `GenerateDeploymentManifest` oluşturmak için görevler [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama adını ve kimliğini belirterek, tek bir derleme ile uygulama ve dağıtım bildirimleri.  

 Kimliğini ve adını açıkça belirtilmesi dışında bu örnek önceki örneğe benzerdir. Ayrıca, bu örnek, yüklü bir uygulama yerine çevrimiçi bir uygulama olarak yapılandırılır.  

> [!NOTE]
>  Aşağıdaki örnekte, tüm uygulama ikilileri, bildirim oluşturma görünüşlerine odaklanabilmek için önceden oluşturulmuş. Bu örnek tam olarak çalışan üretir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım.  
> 
> [!NOTE]
>  Daha fazla bilgi için `Thumbprint` kullanılan özellik `SignFile` görev Bu örnekte, bkz: [SignFile görevi](../msbuild/signfile-task.md).  

```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  

    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  

    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  

    <Target Name="Build">  

        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            EntryPoint="@(EntryPoint)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  

        <GenerateDeploymentManifest  
                AssemblyName="SimpleWinApp.application"  
                AssemblyVersion="1.0.0.0"  
                EntryPoint="@(ApplicationManifest)"  
                Install="false"  
                OutputManifest="SimpleWinApp.application">  
                <Output  
                    ItemName="DeployManifest"  
                    TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  

        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  

        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  

    </Target>  
</Project>  
```  

## <a name="example"></a>Örnek  
 Bu örnekte `GenerateApplicationManifest` ve `GenerateDeploymentManifest` oluşturmak için görevler [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama ve dağıtım birden çok dosya ve derlemesi olan bir uygulama için bildirimleri.  

> [!NOTE]
>  Aşağıdaki örnekte, tüm uygulama ikilileri, bildirim oluşturma görünüşlerine odaklanabilmek için önceden oluşturulmuş. Bu örnek tam olarak çalışan üretir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım.  
> 
> [!NOTE]
>  Daha fazla bilgi için `Thumbprint` kullanılan özellik `SignFile` görev Bu örnekte, bkz: [SignFile görevi](../msbuild/signfile-task.md).  

```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  

    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  

    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
        <DeployUrl>  
            <!-- Insert the deployment URL here -->  
        </DeployUrl>  
        <SupportUrl>  
            <!-- Insert the support URL here -->  
        </SupportUrl>  
    </PropertyGroup>  

    <Target Name="Build">  

    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe"/>  
        <Dependency Include="ClassLibrary1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <Dependency Include="ClassLibrary2.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <Group>Secondary</Group>  
        </Dependency>  
        <Dependency Include="MyAddIn1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <TargetPath>Addins\MyAddIn1.dll</TargetPath>  
        </Dependency>  
        <Dependency Include="ClassLibrary3.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Prerequisite</DependencyType>  
        </Dependency>  

        <File Include="Text1.txt">  
            <TargetPath>Text\Text1.txt</TargetPath>  
            <Group>Text</Group>  
        </File>  
        <File Include="DataFile1.xml ">  
            <TargetPath>Data\DataFile1.xml</TargetPath>  
            <IsDataFile>true</IsDataFile>  
        </File>  

        <IconFile Include="Heart.ico"/>  
        <ConfigFile Include="app.config">  
            <TargetPath>SimpleWinApp.exe.config</TargetPath>  
        </ConfigFile>  
        <BaseManifest Include="app.manifest"/>  
    </ItemGroup>  

    <Target Name="Build">  

        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            ConfigFile="@(ConfigFile)"  
            Dependencies="@(Dependency)"  
            Description="TestApp"  
            EntryPoint="@(EntryPoint)"  
            Files="@(File)"  
            IconFile="@(IconFile)"  
            InputManifest="@(BaseManifest)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  

        <GenerateDeploymentManifest  
            AssemblyName="SimpleWinApp.application"  
            AssemblyVersion="1.0.0.0"  
            DeploymentUrl="$(DeployToUrl)"  
            Description="TestDeploy"  
            EntryPoint="@(ApplicationManifest)"  
            Install="true"  
            OutputManifest="SimpleWinApp.application"  
            Product="SimpleWinApp"  
            Publisher="Microsoft"  
            SupportUrl="$(SupportUrl)"  
            UpdateEnabled="true"  
            UpdateInterval="3"  
            UpdateMode="Background"  
            UpdateUnit="weeks">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  

        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  

        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  

    </Target>  
</Project>  
```  

## <a name="example"></a>Örnek  
 Bu örnekte `GenerateApplicationManifest` uygulaması için yerel bir bildirim oluşturmak üzere görev *Test.exe*, yerel bileşen başvuran *Alpha.dll* ve yalıtılmış bir COM bileşeni  *Bravo.dll'yi*.  

 Bu örnek üretir *Test.exe.manifest*, uygulamayı XCOPY dağıtılabilir ve alınması avantajı ücretsiz COM kayıt yapma  

> [!NOTE]
>  Aşağıdaki örnekte, tüm uygulama ikilileri, bildirim oluşturma görünüşlerine odaklanabilmek için önceden oluşturulmuş. Bu örnek tam olarak çalışan üretir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım.  

```xml  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  

    <ItemGroup>  
        <File Include="Test.exe" />  
        <Dependency Include="Alpha.dll">  
            <AssemblyType>Native</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <ComComponent Include="Bravo.dll" />  
    </ItemGroup>  

    <Target Name="Build">  
        <GenerateApplicationManifest  
            AssemblyName="Test.exe"  
            AssemblyVersion="1.0.0.0"  
            Dependencies="@(Dependency)"  
            Files="@(File)"  
            IsolatedComReferences="@(ComComponent)"  
            ManifestType="Native">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  

    </Target>  
</Project>  
```  

## <a name="see-also"></a>Ayrıca bkz.  
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [GenerateDeploymentManifest görevi](../msbuild/generatedeploymentmanifest-task.md)   
 [SignFile görevi](../msbuild/signfile-task.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)