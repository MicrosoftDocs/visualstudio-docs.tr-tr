---
title: Metin şablonlarından modellere erişme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, accessing models
ms.assetid: cf65395a-0ca3-4826-89c7-b1869562685c
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: f311018197040c0c908964a49f63ab130121c8c2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919864"
---
# <a name="accessing-models-from-text-templates"></a>Metin Şablonlarından Modellere Erişme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metin şablonları kullanarak rapor dosyaları, kaynak kodu dosyaları ve etki alanına özgü dil modelleri tabanlı diğer metin dosyaları oluşturabilirsiniz. Temel metin şablonları hakkında daha fazla bilgi için [kod oluşturma ve T4 metin şablonları](../modeling/code-generation-and-t4-text-templates.md). Metin şablonlarını DSL'nizi ayıklanırken Deneysel modda çalışır ve DSL dağıtmış olan bir bilgisayar üzerinde de çalışır.  
  
> [!NOTE]
>  Bir DSL çözümü, örnek metin şablonu oluşturduğunuzda  **\*.tt** dosyaları, hata ayıklama projede oluşturulur. Etki alanı sınıflarının adları değiştirdiğinizde, bu şablonları artık çalışmayacak. Bununla birlikte, bunlar gereken temel yönergeleri içerir ve DSL'nizi eşleşecek şekilde güncelleştirebilirsiniz örnekler sunar.  
  
 Bir model bir metin şablonundan erişmek için:  
  
- Şablon yönergesi için devral özelliğini <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>. Bu, Store için erişim sağlar.  
  
- Yönerge işlemcileri, erişmek istediğiniz DSL için belirtin. Bu, böylece kendi etki alanı sınıfları, özellikleri ve ilişkileri metin şablonunuzu kodda kullanabilirsiniz DSL'nizi için derlemeleri yükler. Ayrıca, belirttiğiniz model dosyası yükler.  
  
  A `.tt` dosyası aşağıdaki örneğe benzer, hata ayıklama projede oluşturulursa, yeni bir oluşturduğunuzda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] DSL Minimal dil şablondan çözüm.  
  
```  
<#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
<#@ output extension=".txt" #>  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
  
This text will be output directly.  
  
This is the name of the model: <#= this.ModelRoot.Name #>  
  
Here is a list of elements in the model:  
<#  
  // When you change the DSL Definition, some of the code below may not work.  
  foreach (ExampleElement element in this.ExampleModel.Elements)  
  {#>  
<#= element.Name #>  
<#      
  }  
#>  
  
```  
  
 Bu şablon ilgili şu noktalara dikkat edin:  
  
-   Şablon, etki alanı sınıfları, özellikleri ve DSL tanım içinde tanımlanan ilişkileri kullanabilirsiniz.  
  
-   Belirttiğiniz model dosyası şablon yüklendikten `requires` özelliği.  
  
-   Bir özelliğin `this` kök öğe içeriyor. Burada, kodunuzun diğer model öğelerine gidebilirsiniz. Özelliğin adı genellikle kök etki alanı sınıfı, DSL'nin ile aynıdır. Bu örnekte olduğu `this.ExampleModel`.  
  
-   C# kod parçalarını yazıldığı dili olmasına karşın, herhangi bir türdeki metin oluşturabilirsiniz. Alternatif olarak kod yazabileceğiniz [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] özelliği ekleyerek `language="VB"` için `template` yönergesi.  
  
-   Şablon hata ayıklamak için ekleme `debug="true"` için `template` yönergesi. Şablon içinde başka bir örneği açılır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir özel durum oluşursa. Kodda belirli bir noktada hata ayıklayıcısına kesmek istiyorsanız, deyim Ekle `System.Diagnostics.Debugger.Break();`  
  
     Daha fazla bilgi için [bir T4 metin şablonuna ilişkin hata ayıklama](../modeling/debugging-a-t4-text-template.md).  
  
## <a name="about-the-dsl-directive-processor"></a>DSL yönerge işlemcisini hakkında  
 Şablon, DSL tanım içinde tanımlanan alan sınıfları kullanabilirsiniz. Bu genellikle şablon başlangıcı görünür bir yönerge tarafından getirilir. Önceki örnekte, aşağıda verilmiştir.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
```  
  
 Yönergenin adı ( `MyLanguage`, bu örnekte) DSL'nizi adından türetilir. Çağırdığı bir *yönerge işlemcisi* , DSL'nin bir parçası olarak oluşturulur. Kendi kaynak kodunda bulabilirsiniz **Dsl\GeneratedCode\DirectiveProcessor.cs**.  
  
 DSL yönerge işlemcisini asıl iki görevleri gerçekleştirir:  
  
-   Etkili bir şekilde derleme ve içeri aktarma yönergeleri DSL'nizi başvuran şablona ekler. Bu, etki alanı sınıfları şablon kodunda kullanmanızı sağlar.  
  
-   Belirttiğiniz dosya yükler `requires` parametre ve bir özellik ayarlar `this` yüklenen modelin kök öğesine başvuruyor.  
  
## <a name="validating-the-model-before-running-the-template"></a>Şablonu çalıştırmadan önce model doğrulama  
 Şablon yürütülmeden önce doğrulanması modeli neden olabilir.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>  
  
```  
  
 Şunlara dikkat edin:  
  
1. `filename` Ve `validation` parametreleri ile ayrılmış ";" ve diğer ayırıcı veya boşluk olması gerekir.  
  
2. Doğrulama kategori listesi, hangi doğrulama yöntemlerinin yürütülecek belirler. Birden çok kategori ile ayrılmalıdır "&#124;" ve diğer ayırıcı veya boşluk olması gerekir.  
  
   Bir hata bulunursa hataları penceresinde bildirilir ve sonuç dosyası bir hata iletisi içerir.  
  
##  <a name="Multiple"></a> Bir metin şablonundan birden çok modellere erişme  
  
> [!NOTE]
>  Bu yöntem, aynı şablonu birden çok modeli okumanıza izin verir ancak ModelBus odkazy entit. ModelBus başvurularını birbirine modelleri için bkz [metin şablonunda Visual Studio ModelBus kullanarak](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Birden fazla model aynı metin şablonundan erişmek istiyorsanız, üretilen bir yönerge işlemcisine her model için bir kez çağırmanız gerekir. Her model dosya adını belirtmeniz gerekir `requires` parametresi. Kök etki alanı sınıfı için kullanmak istediğiniz adları belirtmelisiniz `provides` parametresi. İçin farklı değerler belirtmeniz gerekir `provides` her yönerge çağrılarının parametreleri. Örneğin, üç model dosyaları Library.xyz School.xyz ve Work.xyz adlı sahip olduğunuzu varsaymaktadır. Bunları aynı metin şablonundan erişmek için aşağıdaki sorguyu benzer üç yönerge çağrıları yazmanız gerekir.  
  
```  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>  
```  
  
> [!NOTE]
>  Bu kod örneği, en az bir dil çözümü şablonu temel alan bir dil içindir.  
  
 Metin şablonunuzu modellerinde erişmek için artık aşağıdaki örnekte koda benzer bir kod yazabilirsiniz.  
  
```csharp  
<#  
foreach (ExampleElement element in this.LibraryModel.Elements)  
...  
foreach (ExampleElement element in this.SchoolModel.Elements)  
...  
foreach (ExampleElement element in this.WorkModel.Elements)  
...  
#>  
```  
  
```vb  
<#  
For Each element As ExampleElement In Me.LibraryModel.Elements  
...  
For Each element As ExampleElement In Me.SchoolModel.Elements  
...  
For Each element As ExampleElement In Me.WorkModel.Elements  
...  
#>  
```  
  
## <a name="loading-models-dynamically"></a>Modeller dinamik olarak yükleme  
 Çalışma zamanında yükleme için hangi modelleri belirlemek istiyorsanız, bir model dosyası dinamik olarak DSL özgü yönergesi kullanmak yerine, program kodunda yükleyebilirsiniz.  
  
 Böylece şablon kodunu bu DSL içinde tanımlanan alan sınıfları kullanabilirsiniz ancak DSL özgü yönergesi işlevlerini DSL ad alanını içeri aktarmak için biridir. Yönergesi kullanmadığınızdan eklemelisiniz  **\<derleme >** ve  **\<alma >** yük tüm modellerine yönelik yönergeleri. Bu yük farklı modelleri aynı DSL tüm örneklerini olduğunda kolay bir işlemdir.  
  
 Dosya yüklemek için en etkili yöntem kullanmaktır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus. Tipik bir senaryoda, metin şablonunuzu bir DSL özgü yönergesi ilk modeli normal şekilde yüklemek için kullanır. Bu model, başka bir Modeli'ne ModelBus başvuruları içerecektir. ModelBus başvurulan model açmak ve belirli bir öğeye erişmek için kullanabilirsiniz. Daha fazla bilgi için [metin şablonunda Visual Studio ModelBus kullanarak](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Daha az normal bir senaryoda, yalnızca bir dosya adı, elinizde bir model dosyasını açmak isteyebilirsiniz ve geçerli olmayabilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proje. Bu durumda, açıklanan tekniği kullanarak dosyayı açabilmek için [nasıl yapılır: Program kodunda dosyadan Model açma](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
## <a name="generating-multiple-files-from-a-template"></a>Bir şablondan birden çok dosya oluşturma  
 Çeşitli dosyalar – oluşturmak istiyorsanız, örneğin, bir model, her öğe için ayrı bir dosya oluşturmak için birkaç olası yaklaşım vardır. Varsayılan olarak, her şablon dosyasına ait yalnızca bir dosya oluşturulur.  
  
### <a name="splitting-a-long-file"></a>Uzun dosya bölme  
 Bu yöntemde, tek bir sınırlayıcıyla ayrılmış bir dosya oluşturmak için bir şablon kullanın. Ardından dosyayı parçasına bölün. Tek dosya ve diğer bölmek için oluşturmak için iki şablonlar vardır.  
  
 **LoopTemplate.t4** uzun tek dosya oluşturur. Tıkladığınızda, doğrudan bu işlenmemesi çünkü dosya uzantısını ".t4" olduğuna dikkat edin **tüm Şablonları Dönüştür**. Bu şablon, segmentleri ayıran sınırlayıcıyı dizeyi belirtir. bir parametre alır:  
  
```  
<#@ template ninherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
<#@ parameter name="delimiter" type="System.String" #>  
<#@ output extension=".txt" #>  
<#@ MyDSL processor="MyDSLDirectiveProcessor" requires="fileName='SampleModel.mydsl1';validation='open|load|save|menu'" #>  
<#  
  // Create a file segment for each element:  
  foreach (ExampleElement element in this.ExampleModel.Elements)   
  {   
    // First item is the delimiter:  
#>  
<#= string.Format(delimiter, element.Id) #>  
  
   Element: <#= element.Name #>  
<#  
   // Here you generate more content derived from the element.  
  }  
#>  
  
```  
  
 `LoopSplitter.tt` çağıran `LoopTemplate.t4`ve ardından sonuç dosyası, segmentlere ayırır. Modeli okumak değil çünkü bu şablon bir modelleme şablonu gerekmez, dikkat edin.  
  
```  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>  
<#@ import namespace="System.Runtime.Remoting.Messaging" #>  
<#@ import namespace="System.IO" #>  
  
<#  
  // Get the local path:  
  string itemTemplatePath = this.Host.ResolvePath("LoopTemplate.t4");  
  string dir = Path.GetDirectoryName(itemTemplatePath);  
  
  // Get the template for generating each file:  
  string loopTemplate = File.ReadAllText(itemTemplatePath);  
  
  Engine engine = new Engine();  
  
  // Pass parameter to new template:  
  string delimiterGuid = Guid.NewGuid().ToString();  
  string delimiter = "::::" + delimiterGuid + ":::";  
  CallContext.LogicalSetData("delimiter", delimiter + "{0}:::");   
  string joinedFiles = engine.ProcessTemplate(loopTemplate, this.Host);  
  
  string [] separateFiles = joinedFiles.Split(new string [] {delimiter}, StringSplitOptions.None);  
  
  foreach (string nameAndFile in separateFiles)   
  {   
     if (string.IsNullOrWhiteSpace(nameAndFile)) continue;  
     string[] parts = nameAndFile.Split(new string[]{":::"}, 2, StringSplitOptions.None);  
     if (parts.Length < 2) continue;  
#>  
 Generate: [<#= dir #>] [<#= parts[0] #>]  
<#  
     // Generate a file from this item:  
     File.WriteAllText(Path.Combine(dir, parts[0] + ".txt"), parts[1]);    
  }  
#>  
  
```



