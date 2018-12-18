---
title: 'İzlenecek yol: satır içi göre oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
- MSBuild, tasks
ms.assetid: 438194cb-668c-41a9-a7e2-c118d14c1ea7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2091bfa5408c85e4fb4dd4b8973a74d1da8b7132
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828669"
---
# <a name="walkthrough-create-an-inline-task"></a>İzlenecek yol: satır içi göre oluşturma
MSBuild görevleri, derleme uygulayan bir sınıf tarafından genellikle oluşturulur <xref:Microsoft.Build.Framework.ITask> arabirimi. .NET Framework sürüm 4 ile başlayarak, proje dosyasında görevleri satır içi oluşturabilirsiniz. Görev barındırmak için ayrı bir derleme oluşturmak zorunda değildir. Daha fazla bilgi için [satır içi görevleri](../msbuild/msbuild-inline-tasks.md).  
  
 Bu izlenecek yol, oluşturmak ve bu satır içi görevleri çalıştırmak gösterilmektedir:  
  
-   Giriş veya çıkış parametresi yok bir görev.  
  
-   Bir giriş parametresi ve hiçbir çıktı parametreleri olan bir görev.  
  
-   İki giriş parametresi ve bir MSBuild özellik döndüren bir output parametresi olan bir görev.  
  
-   İki giriş parametresi ve MSBuild öğesi döndüren bir output parametresi olan bir görev.  

Oluşturma ve görevleri çalıştırmak için Visual Studio'yu kullanın ve **Visual Studio komut istemi penceresi**gibi:  
  
1.   Visual Studio kullanarak bir MSBuild proje dosyası oluşturun.  
  
2.   Satır içi görev oluşturmak üzere Visual Studio'da proje dosyasını değiştirin.  
  
3.   Kullanım **komut istemi penceresi** projeyi oluşturun ve sonuçları inceleyin.  
  
## <a name="create-and-modify-an-msbuild-project"></a>MSBuild projesi oluşturup  
 Visual Studio proje sistemi MSBuild'i temel alır. Bu nedenle, Visual Studio kullanılarak yapı projesi dosyası oluşturabilirsiniz. Bu bölümde, bir Visual C# proje dosyası oluşturun. (Visual Basic proje dosyası yerine oluşturabilirsiniz. Bu öğreticide bağlamında, iki proje dosyaları arasındaki fark küçük.)  
  
#### <a name="to-create-and-modify-a-project-file"></a>Oluşturma ve bir proje dosyasını değiştirmek için  
  
1.  Visual Studio'da üzerinde **dosya** menüsünde tıklatın **yeni** ve ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda **Visual C#** proje türü ve ardından **Windows Forms uygulaması** şablonu. İçinde **adı** kutusuna `InlineTasks`. Tür a **konumu** çözümü, örneğin, *D:\\*. Emin **çözüm için dizin oluştur** seçildiğinde **kaynak denetimine Ekle** temizlenir, ve **çözüm adı** olduğu **InlineTasks**.  
  
3.  Tıklayın **Tamam** proje dosyası oluşturmak için.  
  
3.  İçinde **Çözüm Gezgini**, sağ **InlineTasks** proje düğümünü ve ardından **projeyi**.  
  
4.  Proje düğümüne sağ tıklayın ve ardından **Düzenle InlineTasks.csproj**.  
  
     Proje dosyası kod düzenleyicisinde görüntülenir.  
  
## <a name="add-a-basic-hello-task"></a>Temel bir Hello görev ekleyin  
 Şimdi proje dosyasına iletisini gösteren temel bir görev ekleyin "Hello, world!" Ayrıca görev çağırmak için bir varsayılan TestBuild hedef ekleyin.  
  
#### <a name="to-add-a-basic-hello-task"></a>Temel bir Hello görev eklemek için  
  
1. Kök `Project` düğümü, değişiklik `DefaultTargets` özniteliğini `TestBuild`. Ortaya çıkan `Project` düğüm, bu örnekte benzemelidir:  
  
   ```xml
   <Project ToolsVersion="4.0" DefaultTargets="TestBuild" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   ```
  
2. Aşağıdaki satır içi görev ekleyin ve proje dosyasına hemen önce hedef `</Project>` etiketi.  
  
   ```xml  
   <UsingTask TaskName="Hello" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
     <ParameterGroup />  
     <Task>  
       <Code Type="Fragment" Language="cs">  
         Log.LogMessage("Hello, world!", MessageImportance.High);  
       </Code>  
     </Task>  
   </UsingTask>  
   <Target Name="TestBuild">  
     <Hello />  
   </Target>  
   ```  
  
3. Proje dosyasını kaydedin.  
  
   Bu kod Hello olarak adlandırılır ve başvuruları, hiç parametre yok bir satır içi görev oluşturur veya `Using` deyimleri. Başlangıç görevi selamlama iletisine varsayılan günlük kaydı cihazda genellikle konsol penceresinde görüntüler kodun tek satırı içerir.  
  
### <a name="run-the-hello-task"></a>Başlangıç görevi çalıştır  
 MSBuild kullanarak Çalıştır **komut istemi penceresi** Hello görevi oluşturmak ve onu çağıran TestBuild hedef işlemek için.  
  
##### <a name="to-run-the-hello-task"></a>Başlangıç görevi çalıştırmak için  
  
1. Tıklayın **Başlat**, tıklayın **tüm programlar**ve bulun **Visual Studio Araçları** klasörü ve tıklatın **Visual Studio komut istemi**.  
  
2. İçinde **komut istemi penceresi**, bu durumda, proje dosyasını içeren klasörü bulun *D:\InlineTasks\InlineTasks\\*.  
  
3. Tür **msbuild** komut anahtarlar ve ENTER tuşuna olmadan **Enter**. Varsayılan olarak, bu yapıları *InlineTasks.csproj* dosya ve Hello görevini çağırır TestBuild, varsayılan hedef işler.  
  
4. Çıktıyı inceleyin **komut istemi penceresi**. Şu satırı görmeniz gerekir:  
  
    `Hello, world!`  
  
   > [!NOTE]
   >  Selamlama iletisine görmüyorsanız, proje dosyasını kaydetmeyi tekrar deneyin ve sonra başlangıç görevi çalıştırın.  
  
   Kod Düzenleyicisi arasında geçiş yapma tarafından ve **komut istemi penceresi**, proje dosyasını değiştirebilir ve sonuçları hızlı bir şekilde görmek.  
  
## <a name="define-the-echo-task"></a>Yankı görev tanımlayın  
 Bir dize parametresi kabul eder ve dize cihaz günlüğü varsayılan olarak görüntüleyen bir satır içi görev oluşturun.  
  
#### <a name="to-define-the-echo-task"></a>Yankı görev tanımlamak için  
  
1. Kod Düzenleyicisi'nde aşağıdaki kodu kullanarak başlangıç görevi ve TestBuild hedef değiştirin.  
  
   ```xml  
   <UsingTask TaskName="Echo" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
     <ParameterGroup>  
       <Text Required="true" />  
     </ParameterGroup>  
     <Task>  
       <Code Type="Fragment" Language="cs">  
         Log.LogMessage(Text, MessageImportance.High);  
       </Code>  
     </Task>  
   </UsingTask>  
   <Target Name="TestBuild">  
     <Echo Text="Greetings!" />  
   </Target>  
   ```  
  
2. İçinde **komut istemi penceresi**, türü **msbuild** komut anahtarlar ve ENTER tuşuna olmadan **Enter**. Varsayılan olarak, bu varsayılan hedef Echo görev çağıran TestBuild işler.  
  
3. Çıktıyı inceleyin **komut istemi penceresi**. Şu satırı görmeniz gerekir:  
  
    `Greetings!`  
  
   Bu kod, Echo adlandırılmış ve tek gerekli giriş parametresi metin olan bir satır içi görev tanımlar. Varsayılan olarak, System.String türünde parametrelerdir. TestBuild hedef Echo görevi çağırdığında, metin parametresinin değeri ayarlanır.  
  
## <a name="define-the-adder-task"></a>Ekleyici görev tanımlayın  
 İki tamsayı parametre ekler ve bir MSBuild özelliği olarak toplamları yayan bir satır içi görev oluşturun.  
  
#### <a name="to-define-the-adder-task"></a>Ekleyici görev tanımlamak için  
  
1. Kod Düzenleyicisi'nde aşağıdaki kodu kullanarak TestBuild hedef ve yankı görev değiştirin.  
  
   ```xml  
   <UsingTask TaskName="Adder" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
     <ParameterGroup>  
       <A ParameterType="System.Int32" Required="true" />  
       <B ParameterType="System.Int32" Required="true" />  
       <C ParameterType="System.Int32" Output="true" />  
     </ParameterGroup>  
     <Task>  
       <Code Type="Fragment" Language="cs">  
         C = A + B;  
       </Code>  
     </Task>  
   </UsingTask>    
   <Target Name="TestBuild">  
     <Adder A="4" B="5">  
       <Output PropertyName="Sum" TaskParameter="C" />  
     </Adder>  
     <Message Text="The sum is $(Sum)" Importance="High" />  
   </Target>  
   ```  
  
2. İçinde **komut istemi penceresi**, türü **msbuild** komut anahtarlar ve ENTER tuşuna olmadan **Enter**. Varsayılan olarak, bu varsayılan hedef Echo görev çağıran TestBuild işler.  
  
3. Çıktıyı inceleyin **komut istemi penceresi**. Şu satırı görmeniz gerekir:  
  
    `The sum is 9`  
  
   Bu kod, ekleyici adlı bir satır içi görev tanımlar ve iki tamsayı giriş parametreleri, A ve B zorunludur ve bir tamsayı çıkış parametresi, c Ekleyici görev iki giriş parametreleri ekler ve toplam çıkış parametresinde döndürür. MSBuild özelliği olarak toplamı yayıldığını `Sum`. TestBuild hedef ekleyici görevi çağırdığında, giriş parametrelerinin değerlerini ayarlanır.  
  
## <a name="define-the-regx-task"></a>RegX görev tanımlayın  
 Bir öğe grubunu ve normal bir ifade kabul eder ve ifadeyle eşleşen dosya içeriğini gösteren tüm öğeleri listesi döndüren bir satır içi görev oluşturun.  
  
#### <a name="to-define-the-regx-task"></a>RegX görev tanımlamak için  
  
1. Kod Düzenleyicisi'nde aşağıdaki kodu kullanarak TestBuild hedef ve görev ekleyici değiştirin.  
  
   ```xml  
   <UsingTask TaskName="RegX" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
     <ParameterGroup>  
       <Expression Required="true" />  
       <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />  
       <Result ParameterType="Microsoft.Build.Framework.ITaskItem[]" Output="true" />  
     </ParameterGroup>  
     <Task>  
       <Using Namespace="System.Text.RegularExpressions"/>  
       <Code Type="Fragment" Language="cs">  
   <![CDATA[  
         if (Files.Length > 0)  
         {  
           Result = new TaskItem[Files.Length];  
           for (int i = 0; i < Files.Length; i++)  
           {  
             ITaskItem item = Files[i];  
             string path = item.GetMetadata("FullPath");  
             using(StreamReader rdr = File.OpenText(path))  
             {  
               if (Regex.Match(rdr.ReadToEnd(), Expression).Success)  
               {  
                 Result[i] = new TaskItem(item.ItemSpec);  
               }  
             }  
           }  
         }  
   ]]>  
       </Code>  
     </Task>  
   </UsingTask>    
   <Target Name="TestBuild">  
     <RegX Expression="public|protected" Files="@(Compile)">  
       <Output ItemName="MatchedFiles" TaskParameter="Result" />  
     </RegX>  
     <Message Text="Input files: @(Compile)" Importance="High" />  
     <Message Text="Matched files: @(MatchedFiles)" Importance="High" />  
   </Target>  
   ```  
  
2. İçinde **komut istemi penceresi**, türü **msbuild** komut anahtarlar ve ENTER tuşuna olmadan **Enter**. Varsayılan olarak, bu varsayılan hedef RegX görev çağıran TestBuild işler.  
  
3. Çıktıyı inceleyin **komut istemi penceresi**. Şu satırları görmeniz gerekir:  
  
   ```
   Input files: Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
   ```  
  
   ```
   Matched files: Form1.cs;Form1.Designer.cs;Properties\Settings.Designer.cs
   ```  
  
   Bu kod, RegX adlı ve şu üç parametreyi içeren bir satır içi görev tanımlar:  
  
- `Expression` eşleştirilecek normal ifade olan bir değere sahip bir gerekli dize giriş parametresidir. Bu örnekte, "Genel" veya "korumalı" sözcüklerini ifadeyi eşleştirir.  
  
- `Files` eşleşme için aranacak dosyaların listesini bir değere sahip bir gerekli öğe listesi giriş parametresidir. Bu örnekte, `Files` ayarlanır `Compile` proje kaynak dosyaları listeleyen öğesi.  
  
- `Result` Normal bir ifadeyle eşleşen içeriğe sahip dosyaların listesini bir değere sahip bir çıktı parametresidir.  
  
  Giriş parametreleri değerini TestBuild hedef RegX görevi çağırdığında ayarlanır. RegX görev her dosyasını okur ve normal bir ifadeyle eşleşen dosyaların listesini döndürür. Bu liste olarak döndürülür `Result` MSBuild öğesi olarak yayılan çıkış parametresi, `MatchedFiles`.  
  
### <a name="handle-reserved-characters"></a>Ayrılmış karakterleri  
 MSBuild ayrıştırıcının XML olarak satır içi görevleri işler. Anlamı XML, örneğin, ayrılmış karakterleri "\<" ve ">", algılanan ve XML ve .NET kaynak kodu değil gibi işlenir. Kod ifadeleri gibi ayrılmış karakterleri eklemek için `Files.Length > 0`, yazma `Code` öğesi böylece içeriğinin bir CDATA ifadesinde gibi yer alır:  
  
 ```xml
<Code Type="Fragment" Language="cs">  
  <![CDATA[  
  
  // Your code goes here.  
  
  ]]>  
</Code>  
```  

## <a name="see-also"></a>Ayrıca bkz.  
 [Satır içi görevleri](../msbuild/msbuild-inline-tasks.md)   
 [Görevleri](../msbuild/msbuild-tasks.md)   
 [Hedefler](../msbuild/msbuild-targets.md)