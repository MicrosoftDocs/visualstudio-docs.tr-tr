---
title: 'İzlenecek yol: sıfırdan MSBuild proje dosyası oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: e3acff7c-cb4e-4ae1-8be2-a871bcff847b
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad32edc94bea49010dfb7073cacbd84419513783
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913897"
---
# <a name="walkthrough-creating-an-msbuild-project-file-from-scratch"></a>İzlenecek Yol: Sıfırdan MSBuild Proje Dosyası Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
.NET Framework'ü hedefleyen programlama dilleri, tanımlamak ve uygulama oluşturma işlemini denetlemek için MSBuild proje dosyaları kullanın. Bir MSBuild proje dosyası oluşturmak için Visual Studio kullandığınızda, uygun XML dosyasına otomatik olarak eklenir. Ancak, XML'in nasıl düzenlendiğini anlamak yararlı ve bunu bir yapıyı denetlemek üzere nasıl değiştirebilirsiniz.  
  
 Bir C++ projesi için proje dosyası oluşturma hakkında daha fazla bilgi için bkz: [MSBuild (Visual C++)](http://msdn.microsoft.com/library/7a1be7ff-0312-4669-adf2-5f5bf507d560).  
  
 Bu izlenecek yol yalnızca bir metin düzenleyicisi kullanarak basit bir proje dosyasının parça parça oluşturma işlemini gösterir. İzlenecek yol aşağıdaki adımları izleyin:  
  
- En az uygulama kaynak dosyası oluşturun.  
  
- Bir minimal MSBuild proje dosyası oluşturun.  
  
- PATH ortam değişkenini, MSBuild öğesini içerecek şekilde genişletin.  
  
- Proje dosyasını kullanarak uygulama oluşturun.  
  
- Yapıyı denetlemek için özellikler ekleyin.  
  
- Özellik değerlerini değiştirerek yapıyı denetleyin.  
  
- Yapıya hedefler ekleyin.  
  
- Hedefleri belirleyerek yapıyı denetleyin.  
  
- Artımlı olarak derleyin.  
  
  Bu izlenecek yol, komut isteminde projeyi oluşturun ve sonuçları inceleyin işlemi gösterilmektedir. MSBuild ve MSBuild komut isteminde çalıştırmak hakkında daha fazla bilgi için bkz. [izlenecek yol: MSBuild kullanma](../msbuild/walkthrough-using-msbuild.md).  
  
  İzlenecek yolu tamamlamak için gözden geçirme için gerekli olan MSBuild ve Visual C# derleyicisi, içerdiği için yüklü .NET Framework (sürüm 2.0, 3.5, 4.0 veya 4.5) olması gerekir.  
  
## <a name="creating-a-minimal-application"></a>Minimal uygulama oluşturma  
 Bu bölümde, bir minimal Visual C# uygulama kaynak dosyası bir metin kullanarak düzenleyici oluşturma işlemi gösterilmektedir.  
  
#### <a name="to-create-the-minimal-application"></a>Minimal uygulamayı oluşturmak için  
  
1.  Komut isteminde Documents\ veya \Desktop bu gibi bir durumda uygulamayı oluşturmak istediğiniz klasöre göz atın\\.  
  
2.  Tür **md HelloWorld** \HelloWorld adlı bir alt klasör oluşturmak için\\.  
  
3.  Tür **cd HelloWorld** yeni klasöre değiştirmek için.  
  
4.  Not Defteri veya başka bir metin düzenleyicisini başlatın ve aşağıdaki kodu yazın.  
  
    ```  
    using System;  
  
    class HelloWorld  
    {  
        static void Main()  
        {  
    #if DebugConfig  
            Console.WriteLine("WE ARE IN THE DEBUG CONFIGURATION");  
    #endif  
  
            Console.WriteLine("Hello, world!");  
        }  
    }  
    ```  
  
5.  Bu kaynak kodu dosyasını kaydedin ve HelloWorld.cs olarak adlandırın.  
  
6.  Yazarak uygulamayı derleyin **csc HelloWorld.cs olarak** komut isteminde.  
  
7.  Yazarak uygulamayı test **helloworld** komut isteminde.  
  
     **Hello, world!** iletisi görüntülenmelidir.  
  
8.  Yazarak uygulamayı silin **del helloworld.exe** komut isteminde.  
  
## <a name="creating-a-minimal-msbuild-project-file"></a>Bir Minimal MSBuild proje dosyası oluşturma  
 En az uygulama kaynak dosyasına sahip olduğunuza göre uygulamanızı oluşturmak için en az proje dosyasını oluşturabilirsiniz. Bu proje dosyası aşağıdaki öğeleri içerir:  
  
-   Gerekli kök `Project` düğümü.  
  
-   Bir `ItemGroup` Item öğeleri içermesi düğümü.  
  
-   Uygulama kaynak dosyasına başvuruda bulunan bir item öğesi.  
  
-   A `Target` uygulamayı oluşturmak için gerekli görevleri içermek amacıyla düğümü.  
  
-   A `Task` uygulamayı oluşturmak için Visual C# derleyicisini başlatmak için öğesi.  
  
#### <a name="to-create-a-minimal-msbuild-project-file"></a>Bir minimal MSBuild proje dosyası oluşturmak için  
  
1. Metin düzenleyicisinde varolan metni bu iki satır kullanarak değiştirin:  
  
   ```  
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   </Project>  
   ```  
  
2. Bu ekleme `ItemGroup` düğümü alt öğesi olarak `Project` düğüm:  
  
   ```  
   <ItemGroup>  
     <Compile Include="helloworld.cs" />  
   </ItemGroup>  
   ```  
  
    Bildirim bu `ItemGroup` zaten bir öğe içeriyor.  
  
3. Ekleme bir `Target` düğümü alt öğesi olarak `Project` düğümü. Düğüm adı `Build`.  
  
   ```  
   <Target Name="Build">  
   </Target>  
   ```  
  
4. Bu görev öğesi bir alt öğesi olarak ekleyin `Target` düğüm:  
  
   ```  
   <Csc Sources="@(Compile)"/>  
   ```  
  
5. Bu proje dosyasını kaydedin ve HelloWorld.csproj olarak adlandırın.  
  
   Minimal proje dosyanız, aşağıdaki koda benzemelidir:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
  </ItemGroup>  
  <Target Name="Build">  
    <Csc Sources="@(Compile)"/>    
  </Target>  
</Project>  
```  
  
 Derleme hedefindeki Görevler sırayla yürütülür. Bu durumda, Visual C# derleyicisi `Csc` görevi tek görevdir. Derlenecek kaynak dosyaların listesini bekler ve bu değeri tarafından verilen `Compile` öğesi. `Compile` Öğesi yalnızca bir kaynak dosyasına: HelloWorld.cs'ye başvuruyor.  
  
> [!NOTE]
>  Öğede, aşağıdaki gibi .cs dosya adı uzantısına sahip tüm dosyalara başvurmak için yıldız işareti joker karakter (*) kullanabilirsiniz:  
>   
>  `<Compile Include="*.cs" />`  
>   
>  Hata ayıklamayı ve Seçici yaptığından ancak joker karakter kullanımını önermeyiz kaynak dosyalar eklenirse veya silinirse hedeflemeyi daha zor.  
  
## <a name="extending-the-path-to-include-msbuild"></a>Yolu, Msbuild'i içerecek şekilde genişletme  
 MSBuild'e erişmeden önce PATH ortam değişkenini .NET Framework klasörünü içerecek şekilde genişletmeniz gerekir.  
  
#### <a name="to-add-msbuild-to-your-path"></a>MSBuild yolunuza dosya eklemek için  
  
-   Visual Studio 2013 itibariyle, MSBuild.exe MSBuild klasöründe bulabilirsiniz (`%ProgramFiles%\MSBuild` bir 32-bit işletim sisteminde veya `%ProgramFiles(x86)%\MSBuild` 64-bit işletim sisteminde).  
  
     Komut isteminde **PATH=%PATH%;%ProgramFiles%\MSBuild ayarlamak** veya **yolu = % PATH %; % ProgramFiles (x86) %\MSBuild**.  
  
     Alternatif olarak, Visual Studio yüklü, kullanabileceğiniz **Visual Studio komut istemi**, MSBuild klasörünü de içeren bir yolu vardır.  
  
## <a name="using-the-project-file-to-build-the-application"></a>Uygulamayı oluşturmak için proje dosyasını kullanma  
 Şimdi uygulamayı oluşturmak için yeni oluşturduğunuz proje dosyasını kullanın.  
  
#### <a name="to-build-the-application"></a>Uygulamayı oluşturmak için  
  
1.  Komut isteminde **msbuild, helloworld.csproj /t:Build**.  
  
     Bu, Helloworld uygulamasını oluşturmak için Visual C# derleyicisini çağırarak Helloworld proje dosyasının derleme hedefini oluşturur.  
  
2.  Yazarak uygulamayı test **helloworld**.  
  
     **Hello, world!** iletisi görüntülenmelidir.  
  
> [!NOTE]
>  Ayrıntı düzeyini yükselterek, yapı hakkında daha fazla ayrıntı görebilirsiniz. Ayrıntı düzeyini "ayrıntılı" ayarlamak için komut isteminde aşağıdaki komutlardan birini yazın:  
>   
>  **MSBuild, helloworld.csproj /t:Build /verbosity: ayrıntılı**  
  
## <a name="adding-build-properties"></a>Derleme özellikleri ekleme  
 Daha fazla denetim derleme proje dosyasına yapı özellikleri ekleyebilirsiniz. Şimdi bu özellikleri ekleyin:  
  
-   Bir `AssemblyName` özelliği uygulamasının adını belirtin.  
  
-   Bir `OutputPath` özelliği uygulamayı içeren klasörü belirtin.  
  
#### <a name="to-add-build-properties"></a>Yapı özellikleri eklemek için  
  
1. Yazarak var olan uygulamayı silin **del helloworld.exe** komut isteminde.  
  
2. Bu proje dosyasında, ekleme `PropertyGroup` öğesini hemen açılış `Project` öğesi:  
  
   ```  
   <PropertyGroup>  
     <AssemblyName>MSBuildSample</AssemblyName>  
     <OutputPath>Bin\</OutputPath>  
   </PropertyGroup>  
   ```  
  
3. Bu görevi derleme hedefine hemen önüne ekleyin `Csc` görevi:  
  
   ```  
   <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />  
   ```  
  
    `MakeDir` Görev tarafından adlandırılan bir klasör oluşturur `OutputPath` hiçbir klasör şu anda mevcut sağlanan özelliği.  
  
4. Bu ekleme `OutputAssembly` özniteliğini `Csc` görevi:  
  
   ```  
   <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
   ```  
  
    Bu tarafından adlandırılan bir derleme oluşturmak için Visual C# derleyicisini üretirken `AssemblyName` özelliği tarafından adlandırılan klasöre yerleştirin ve `OutputPath` özelliği.  
  
5. Değişikliklerinizi kaydedin.  
  
   Proje dosyanız şimdi aşağıdaki kodu benzemelidir:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <AssemblyName>MSBuildSample</AssemblyName>  
    <OutputPath>Bin\</OutputPath>  
  </PropertyGroup>  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
  </ItemGroup>  
  <Target Name="Build">  
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />  
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
  </Target>  
</Project>  
```  
  
> [!NOTE]
>  Ters eğik çizgi eklemenizi öneririz (\\) yol sınırlayıcısını öğesinde belirttiğinizde klasör adının sonunda `OutputPath` eklemek yerine öğesi `OutputAssembly` özniteliği `Csc` görev. Bu nedenle,  
>   
>  `<OutputPath>Bin\</OutputPath>`  
>   
>  `OutputAssembly=="$(OutputPath)$(AssemblyName).exe" />`  
>   
>  daha iyidir  
>   
>  `<OutputPath>Bin</OutputPath>`  
>   
>  `OutputAssembly=="$(OutputPath)\$(AssemblyName).exe" />`  
  
## <a name="testing-the-build-properties"></a>Derleme özelliklerini test etme  
 Artık, çıkış klasörünü ve uygulama adını belirtmek için derleme özelliklerini kullandığınız proje dosyasını kullanarak uygulamayı oluşturabilirsiniz.  
  
#### <a name="to-test-the-build-properties"></a>Yapı özelliklerini test etmek için  
  
1.  Komut isteminde **msbuild, helloworld.csproj /t:Build**.  
  
     Bu \Bin\ klasörünü oluşturur ve ardından MSBuildSample uygulaması oluşturmak için Visual C# derleyicisini çağırır ve \Bin\ klasörüne yerleştirir.  
  
2.  \Bin\ klasörünün oluşturulduğunu ve MSBuildSample uygulaması içerdiğini doğrulamak için **dizini depo**.  
  
3.  Yazarak uygulamayı test **Bin\MSBuildSample**.  
  
     **Hello, world!** iletisi görüntülenmelidir.  
  
## <a name="adding-build-targets"></a>Derleme hedefleri ekleme  
 Ardından, iki daha fazla hedefi gibi proje dosyasına ekleyin:  
  
- Eski dosyaları silen temiz bir hedef.  
  
- Kullanan yeniden oluştur hedefi `DependsOnTargets` Oluştur görevinden önce çalıştırılacak temizleme görevini zorlamak için özniteliği.  
  
  Birden çok hedefe sahip olduğunuza göre derleme hedefini varsayılan hedef olarak ayarlayabilirsiniz.  
  
#### <a name="to-add-build-targets"></a>Yapı hedefleri ekleme  
  
1. Proje dosyasında bu iki hedefi hemen yapı hedefinin arkasına ekleyin:  
  
   ```  
   <Target Name="Clean" >  
     <Delete Files="$(OutputPath)$(AssemblyName).exe" />  
   </Target>  
   <Target Name="Rebuild" DependsOnTargets="Clean;Build" />  
   ```  
  
    Temiz hedef uygulamayı silmek için Sil görevini çağırır. Yeniden oluşturma hedefi hem temizleme hedefi hem de yapı hedefi çalıştırılmadan çalıştırılamaz. Yeniden oluşturma hedefinin görevi olmasa da temizleme hedefinin yapı hedefinden önce çalışmasına neden olur.  
  
2. Bu ekleme `DefaultTargets` özniteliğini açılan `Project` öğesi:  
  
   ```  
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   ```  
  
    Bu derleme hedefini varsayılan hedef olarak ayarlar.  
  
   Proje dosyanız şimdi aşağıdaki kodu benzemelidir:  
  
```  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <AssemblyName>MSBuildSample</AssemblyName>  
    <OutputPath>Bin\</OutputPath>  
  </PropertyGroup>  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
  </ItemGroup>  
  <Target Name="Build">  
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />  
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
  </Target>  
  <Target Name="Clean" >  
    <Delete Files="$(OutputPath)$(AssemblyName).exe" />  
  </Target>  
  <Target Name="Rebuild" DependsOnTargets="Clean;Build" />  
</Project>  
```  
  
## <a name="testing-the-build-targets"></a>Oluşturulmuş hedefleri test etme  
 Proje dosyasının bu özelliklerini sınamak için yeni yapı hedeflerini çalıştırabilirsiniz:  
  
-   Varsayılan derlemeyi oluşturma.  
  
-   Uygulama adını komut isteminde ayarlama.  
  
-   Başka bir uygulama oluşturulmadan önce uygulamayı silme.  
  
-   Başka bir uygulama oluşturmadan uygulamayı silme.  
  
#### <a name="to-test-the-build-targets"></a>Yapı hedeflerini test etmek için  
  
1.  Komut isteminde **msbuild, helloworld.csproj /p:AssemblyName Greetings =**.  
  
     Kullanmadığınız **/t** hedefi açıkça ayarlamak için geçiş, MSBuild varsayılan derleme hedefini çalıştırır. **/P** geçiş geçersiz kılmaları `AssemblyName` özelliği ve yeni değeri verir `Greetings`. Bu, \Bin\ klasöründe yeni bir uygulama, Greetings.exe neden olur.  
  
2.  \Bin\ klasörünün MSBuildSample uygulaması hem de yeni Greetings uygulaması içerdiğini doğrulamak için şunu yazın **dizini depo**.  
  
3.  Yazarak Greetings uygulamasını test **Bin\Greetings**.  
  
     **Hello, world!** iletisi görüntülenmelidir.  
  
4.  Yazarak MSBuildSample uygulamasını silin **msbuild, helloworld.csproj /t: temiz**.  
  
     Bu varsayılan olan uygulamayı kaldırmak için temizleme görevini çalıştırır `AssemblyName` özellik değeri `MSBuildSample`.  
  
5.  Yazarak Greetings uygulamasını silin **msbuild, helloworld.csproj /t: temiz /p:AssemblyName Greetings =**.  
  
     Bu uygulamanın kaldırmak için temizleme görevini çalıştırır verilen **AssemblyName** özellik değeri `Greetings`.  
  
6.  \Bin\ klasörünün artık boş olduğunu doğrulamak için **dizini depo**.  
  
7.  Tür **msbuild**.  
  
     Bir proje dosyası belirtilmemiş olsa da, geçerli klasörde yalnızca bir proje dosyası olduğundan MSBuild helloworld.csproj dosyasını oluşturur. Bu, \Bin\ klasöründe MSBuildSample uygulamasının neden olur.  
  
     \Bin\ klasörünün MSBuildSample uygulaması içerdiğini doğrulamak için şunu yazın **dizini depo**.  
  
## <a name="building-incrementally"></a>Artımlı olarak derleme  
 MSBuild yalnızca kaynak dosyaları veya hedefin bağlı olduğu hedef dosyaları değişmişse bir hedef oluşturmayı söyleyebilirsiniz. MSBuild, zaman damgası bir dosyanın değişip değişmediğini belirlemek için kullanır.  
  
#### <a name="to-build-incrementally"></a>Artımlı olarak oluşturmak için  
  
1.  Proje dosyasında bu öznitelikleri açılış yapı hedefine ekleyin:  
  
    ```  
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"  
    ```  
  
     Bu yapı hedefi belirtilen giriş dosyaları bağlı olduğunu belirtir `Compile` öğesi grubu ve çıkış hedefinin uygulama dosyası olduğunu.  
  
     Sonuçta oluşan yapı hedefi aşağıdaki koda benzemelidir:  
  
    ```  
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">  
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />  
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
    </Target>  
    ```  
  
2.  Yapı hedefi yazarak test edin **msbuild /v:d** komut isteminde.  
  
     HelloWorld.csproj'nin varsayılan proje dosyası olduğunu ve bu yapı varsayılan hedef olduğunu unutmayın.  
  
     **/V:d** anahtarı derleme işleminin ayrıntılı bir açıklamasını belirtir.  
  
     Bu satırların görüntülenmesi gerekir:  
  
     **Hedef "Derleme", tüm çıktı dosyalarının göre giriş dosyaları güncel olduğu için atlanıyor.**  
  
     **Giriş dosyalarını: HelloWorld.cs olarak**  
  
     **Çıkış dosyalarını: BinMSBuildSample.exe**  
  
     Uygulamanın son oluşturulmasında beri kaynak dosyaların hiçbiri değişiklik yapılmadığından MSBuild yapı hedefini atlar.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, bir proje dosyasını derler gösterir. bir [!INCLUDE[csprcs](../includes/csprcs-md.md)] uygulama ve çıktı dosyası adını içeren bir ileti kaydeder.  
  
### <a name="code"></a>Kod  
  
```csharp  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>HelloWorldCS</appname>  
    </PropertyGroup>  
  
    <!-- Specify the inputs by type and file name -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input files of type CSFile -->  
        <CSC  
            Sources = "@(CSFile)"  
            OutputAssembly = "$(appname).exe">  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
### <a name="comments"></a>Açıklamalar  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, bir proje dosyasını derler gösterir. bir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] uygulama ve çıktı dosyası adını içeren bir ileti kaydeder.  
  
### <a name="code"></a>Kod  
  
```vb  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>HelloWorldVB</appname>  
    </PropertyGroup>  
  
    <!-- Specify the inputs by type and file name -->  
    <ItemGroup>  
        <VBFile Include = "consolehwvb1.vb"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">      
        <!-- Run the Visual Basic compilation using input files of type VBFile -->  
        <VBC  
            Sources = "@(VBFile)"  
            OutputAssembly= "$(appname).exe">  
            <!-- Set the OutputAssembly attribute of the VBC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </VBC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="whats-next"></a>Sırada ne var?  
 Visual Studio otomatik olarak bu izlenecek yolda gösterilen işin çoğunu gerçekleştirebilirsiniz. Oluşturma, düzenleme, derleme ve MSBuild proje dosyaları test etmek için Visual Studio'u kullanmayı öğrenmek için bkz: [izlenecek yol: MSBuild kullanma](../msbuild/walkthrough-using-msbuild.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
[MSBuild'e genel bakış](msbuild.md)  
 [MSBuild Başvurusu](../msbuild/msbuild-reference.md)


