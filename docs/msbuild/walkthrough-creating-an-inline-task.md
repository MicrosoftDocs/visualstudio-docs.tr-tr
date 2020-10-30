---
title: 'İzlenecek yol: satır Içi görev oluşturma | Microsoft Docs'
description: Görevi barındırmak için ayrı bir derleme oluşturmak zorunda kalmadan, proje dosyasında satır içi bir MSBuild görevi oluşturma konusunda ilerleyin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
- MSBuild, tasks
ms.assetid: 438194cb-668c-41a9-a7e2-c118d14c1ea7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2d72745aebedb5dad5efc86d33804a51e36b762
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046628"
---
# <a name="walkthrough-create-an-inline-task"></a>İzlenecek yol: satır içi görev oluşturma

MSBuild görevleri genellikle arabirimini uygulayan bir sınıf derlenerek oluşturulur <xref:Microsoft.Build.Framework.ITask> . .NET Framework sürüm 4 ' den başlayarak, proje dosyasında görevleri satır içinde oluşturabilirsiniz. Görevi barındırmak için ayrı bir derleme oluşturmanız gerekmez. Daha fazla bilgi için bkz. [satır içi görevler](../msbuild/msbuild-inline-tasks.md).

 Bu izlenecek yolda, bu satır içi görevlerin nasıl oluşturulacağı ve çalıştırılacağı gösterilmektedir:

- Giriş veya çıkış parametrelerine sahip olmayan bir görev.

- Bir giriş parametresi ve çıkış parametresi olmayan bir görev.

- İki giriş parametresine sahip bir görev ve bir MSBuild özelliği döndüren bir çıkış parametresi.

- İki giriş parametresine sahip bir görev ve bir MSBuild öğesi döndüren bir çıktı parametresi.

Görevleri oluşturmak ve çalıştırmak için, Visual Studio ve **Visual Studio komut Istemi penceresini** aşağıdaki gibi kullanın:

1. Visual Studio 'Yu kullanarak bir MSBuild proje dosyası oluşturun.

2. Satır içi görevi oluşturmak için Visual Studio 'da proje dosyasını değiştirin.

3. Projeyi derlemek ve sonuçları incelemek için **komut Istemi penceresini** kullanın.

## <a name="create-and-modify-an-msbuild-project"></a>MSBuild projesi oluşturma ve değiştirme

 Visual Studio proje sistemi MSBuild'i temel alır. Bu nedenle, Visual Studio 'Yu kullanarak bir yapı proje dosyası oluşturabilirsiniz. Bu bölümde, bir Visual C# proje dosyası oluşturun. (Bunun yerine Visual Basic proje dosyası oluşturabilirsiniz. Bu öğreticinin bağlamında, iki proje dosyası arasındaki fark küçük.)

#### <a name="to-create-and-modify-a-project-file"></a>Proje dosyası oluşturmak ve değiştirmek için

1. Visual Studio 'da C# **Windows Forms uygulama** şablonunu kullanarak yeni bir proje oluşturun. **Ad** kutusuna `InlineTasks` yazın. Çözüm için bir **konum** yazın, örneğin, *D: \\* . **Çözüm için dizin oluştur** ' un seçili olduğundan emin olun, **kaynak denetimine Ekle** ' nin Işaretli olmadığından ve **çözüm adının** **InlineTasks** olması gerekir.

3. Proje dosyasını oluşturmak için **Tamam** ' ı tıklatın.

3. **Çözüm Gezgini** , **InlineTasks** proje düğümüne sağ tıklayın ve ardından **Projeyi Kaldır** ' a tıklayın.

4. Proje düğümüne tekrar sağ tıklayın ve ardından **InlineTasks. csproj öğesini Düzenle** ' ye tıklayın.

     Proje dosyası kod düzenleyicisinde görüntülenir.

## <a name="add-a-basic-hello-task"></a>Temel bir Merhaba görev ekleme

 Şimdi, proje dosyasına "Hello, World!" iletisini görüntüleyen temel bir görev ekleyin Ayrıca, görevi çağırmak için varsayılan bir TestBuild hedefi de ekleyin.

#### <a name="to-add-a-basic-hello-task"></a>Temel bir Merhaba görev eklemek için

1. Kök `Project` düğümünde, `DefaultTargets` özniteliğini olarak değiştirin `TestBuild` . Elde edilen `Project` düğüm Şu örneğe benzemelidir:

   ```xml
   <Project ToolsVersion="4.0" DefaultTargets="TestBuild" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   ```

2. Aşağıdaki satır içi görevi ve hedefi, etiketinden hemen önce proje dosyasına ekleyin `</Project>` .

   ```xml
   <UsingTask TaskName="Hello" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup />
     <Task>
       <Code Type="Fragment" Language="cs">
         Log.LogMessage(MessageImportance.High, "Hello, world!");
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Hello />
   </Target>
   ```

3. Proje dosyasını kaydedin.

   Bu kod, Merhaba adlı bir satır içi görev oluşturur ve hiçbir parametre, başvuru veya yönergesi içermez `Using` . Merhaba görev, genellikle konsol penceresi olan varsayılan günlük cihazında bir Merhaba ileti görüntüleyen yalnızca bir kod satırı içerir.

### <a name="run-the-hello-task"></a>Merhaba görevi çalıştırma

 Merhaba görevi oluşturmak ve bunu çağıran TestBuild hedefini işlemek için **komut Istemi penceresini** kullanarak MSBuild 'i çalıştırın.

##### <a name="to-run-the-hello-task"></a>Merhaba görevi çalıştırmak için

1. **Başlat** ' a tıklayın, **tüm programlar** ' a tıklayın ve ardından **Visual Studio Araçları** klasörünü bulun ve **Visual Studio komut istemi** ' ne tıklayın.

2. **Komut Istemi penceresinde** , proje dosyasını içeren klasörü bulun, bu durumda *D:\ınlinetasks\ınlinetasks \\* .

3. Komut anahtarları olmadan **MSBuild** yazın ve ardından **ENTER** tuşuna basın. Bu, varsayılan olarak, *InlineTasks. csproj* dosyasını oluşturur ve varsayılan hedef TestBuild öğesini işler ve bu da Hello görevini çağırır.

4. **Komut Istemi penceresindeki** çıktıyı inceleyin. Şu satırı görmeniz gerekir:

    `Hello, world!`

   > [!NOTE]
   > Merhaba iletisini görmüyorsanız, proje dosyasını tekrar kaydetmeyi deneyin ve ardından Merhaba görevini çalıştırın.

   Kod Düzenleyicisi ve **komut Istemi penceresi** arasında değişiklik yaparak, proje dosyasını değiştirebilir ve sonuçları hızlıca görebilirsiniz.

## <a name="define-the-echo-task"></a>Yankı görevini tanımlama

 Dize parametresini kabul eden ve varsayılan günlük cihazında dizeyi görüntüleyen bir satır içi görev oluşturun.

#### <a name="to-define-the-echo-task"></a>Yankı görevini tanımlamak için

1. Kod Düzenleyicisi 'nde, aşağıdaki kodu kullanarak Hello görevini ve TestBuild hedefini değiştirin.

   ```xml
   <UsingTask TaskName="Echo" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <Text Required="true" />
     </ParameterGroup>
     <Task>
       <Code Type="Fragment" Language="cs">
         Log.LogMessage(MessageImportance.High, Text);
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Echo Text="Greetings!" />
   </Target>
   ```

2. **Komut Istemi penceresinde** , komut anahtarları olmadan **MSBuild** yazın ve ardından **ENTER** tuşuna basın. Varsayılan olarak, bu, Echo görevini çağıran varsayılan hedef TestBuild öğesini işler.

3. **Komut Istemi penceresindeki** çıktıyı inceleyin. Şu satırı görmeniz gerekir:

    `Greetings!`

   Bu kod, Echo adlı ve yalnızca bir tane gerekli giriş parametresi metnine sahip olan bir satır içi görevi tanımlar. Varsayılan olarak, parametreler System. String türündedir. Metin parametresinin değeri, TestBuild hedefi Echo görevi istediğinde ayarlanır.

## <a name="define-the-adder-task"></a>Adder görevini tanımlama

 İki tamsayı parametresi ekleyen ve toplamlarını MSBuild özelliği olarak yayar bir satır içi görev oluşturun.

#### <a name="to-define-the-adder-task"></a>Adder görevini tanımlamak için

1. Kod Düzenleyicisi 'nde, aşağıdaki kodu kullanarak yankı görevini ve TestBuild hedefini değiştirin.

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

2. **Komut Istemi penceresinde** , komut anahtarları olmadan **MSBuild** yazın ve ardından **ENTER** tuşuna basın. Varsayılan olarak, bu, Echo görevini çağıran varsayılan hedef TestBuild öğesini işler.

3. **Komut Istemi penceresindeki** çıktıyı inceleyin. Şu satırı görmeniz gerekir:

    `The sum is 9`

   Bu kod, Adder adlı bir satır içi görevi tanımlar ve iki gerekli tamsayı giriş parametresine, A ve B ve bir tamsayı çıkış parametresi olan C ' yi içerir. Adder görevi iki giriş parametrelerini ekler ve çıkış parametresindeki toplamı döndürür. Toplam, MSBuild özelliği olarak yayınlanır `Sum` . Giriş parametrelerinin değerleri, TestBuild hedefi Adder görevini çalıştırdığında ayarlanır.

## <a name="define-the-regx-task"></a>RegX görevini tanımlama

 Bir öğe grubunu ve normal ifadeyi kabul eden bir satır içi görev oluşturun ve ifadesiyle eşleşen dosya içeriğine sahip tüm öğelerin bir listesini döndürür.

#### <a name="to-define-the-regx-task"></a>RegX görevini tanımlamak için

1. Kod düzenleyicisinde, aşağıdaki kodu kullanarak Adder görevini ve TestBuild hedefini değiştirin.

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

2. **Komut Istemi penceresinde** , komut anahtarları olmadan **MSBuild** yazın ve ardından **ENTER** tuşuna basın. Varsayılan olarak, bu, RegX görevini çağıran varsayılan hedef TestBuild öğesini işler.

3. **Komut Istemi penceresindeki** çıktıyı inceleyin. Şu satırları görmeniz gerekir:

   ```
   Input files: Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
   ```

   ```
   Matched files: Form1.cs;Form1.Designer.cs;Properties\Settings.Designer.cs
   ```

   Bu kod, RegX adlı bir satır içi görevi tanımlar ve bu üç parametreye sahiptir:

- `Expression` , eşleştirilecek normal ifade olan bir değere sahip gerekli bir dize giriş parametresidir. Bu örnekte, ifade "public" veya "Protected" kelimelerle eşleşir.

- `Files` , eşleşme için aranacak dosyaların listesi olan bir değere sahip gerekli bir öğe listesi giriş parametresidir. Bu örnekte, `Files` `Compile` Proje kaynak dosyalarını listeleyen öğesine ayarlanır.

- `Result` , normal ifadeyle eşleşen içeriği olan dosyaların listesi olan bir çıkış parametresidir.

  Giriş parametrelerinin değeri, TestBuild hedefi RegX görevini çalıştırdığında ayarlanır. RegX görevi her dosyayı okur ve normal ifadeyle eşleşen dosyaların listesini döndürür. Bu liste, `Result` MSBuild öğesi olarak yayılan çıkış parametresi olarak döndürülür `MatchedFiles` .

### <a name="handle-reserved-characters"></a>Ayrılan karakterleri işle

 MSBuild ayrıştırıcısı satır içi görevleri XML olarak işler. XML olarak ayrılmış anlamı olan karakterler (örneğin, ""), \<" and "> .net kaynak kodu değil, XML gibi algılanır ve işlenir. Gibi kod ifadelerinde ayrılmış karakterleri dahil etmek için `Files.Length > 0` , `Code` öğesinin IÇERIĞINI bir CDATA ifadesinde içermeleri için aşağıdaki gibi yazın:

 ```xml
<Code Type="Fragment" Language="cs">
  <![CDATA[

  if (Files.Length > 0)
  {
      // Your code goes here.
  }
  ]]>
</Code>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Satır içi görevleri](../msbuild/msbuild-inline-tasks.md)
- [Görevler](../msbuild/msbuild-tasks.md)
- [Targets](../msbuild/msbuild-targets.md)
