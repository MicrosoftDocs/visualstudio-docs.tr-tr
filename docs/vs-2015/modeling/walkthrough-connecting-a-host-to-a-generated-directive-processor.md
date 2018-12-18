---
title: 'İzlenecek yol: üretilen bir yönerge işlemcisine ana bilgisayar bağlama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
ms.assetid: 254540d9-90d6-42de-8c1c-068affd56e83
caps.latest.revision: 49
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 329cb0a6008824b23d7188c0ea6c4cf5e524476d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817879"
---
# <a name="walkthrough-connecting-a-host-to-a-generated-directive-processor"></a>İzlenecek yol: Üretilen bir Yönerge İşlemcisine Ana Bilgisayar Bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metin şablonlarını işleme kendi ana bilgisayar yazabilirsiniz. Temel özel bir ana bilgisayar gösterilmiştir [izlenecek yol: bir özel metin şablonu konağı oluşturma](../modeling/walkthrough-creating-a-custom-text-template-host.md). Birden çok çıktı dosyaları oluşturmak gibi işlevler eklemek için bu konak genişletebilirsiniz.  
  
 Yönerge işlemcileri çağıran metin şablonlarını destekler, böylece bu kılavuzda, özel bir ana bilgisayar genişletin. Bu, bir etki alanına özgü dil tanımladığınızda, oluşturur bir *yönerge işlemcisi* için etki alanı modeli. Yönerge işlemcisini bütünleştirilmiş kod yazma ve içeri aktarma yönergeleri şablonlarındaki gereksinimini azaltır modeline erişim şablonları yazmak kullanıcılar için kolaylaştırır.  
  
> [!WARNING]
>  Bu izlenecek yolda yapılar [izlenecek yol: özel metin şablonu konağı oluşturma](../modeling/walkthrough-creating-a-custom-text-template-host.md). Bu izlenecek yol önce gerçekleştirin.  
  
 Bu izlenecek yol aşağıdaki görevleri içerir:  
  
-   Kullanarak [!INCLUDE[dsl](../includes/dsl-md.md)] bir etki alanı modeline dayalı bir yönerge işlemcisi oluşturmak için.  
  
-   Özel metin şablonu ana bilgisayar üretilen bir yönerge işlemcisine bağlama.  
  
-   Özel ana bilgisayarı ile oluşturulan yönerge işlemcisini test etme.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bir DSL tanımlamak için aşağıdaki bileşenler yüklemiş olmanız gerekir:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|Visual Studio Görselleştirme ve modelleme SDK'sı|[http://go.microsoft.com/fwlink/?LinkID=186128](http://go.microsoft.com/fwlink/?LinkID=186128)|  
  
 Ayrıca, oluşturduğunuz özel metin şablonu dönüştürme olmalıdır [izlenecek yol: bir özel metin şablonu konağı oluşturma](../modeling/walkthrough-creating-a-custom-text-template-host.md).  
  
## <a name="using-domain-specific-language-tools-to-generate-a-directive-processor"></a>Bir yönerge işlemcisi oluşturmak için etki alanına özgü dil araçları kullanma  
 Bu kılavuzda, bir etki alanına özgü dil çözümü DSLMinimalTest oluşturmak için etki alanına özgü dil Tasarımcısı Sihirbazı'nı kullanın.  
  
#### <a name="to-use-domain-specific-language-tools-to-generate-a-directive-processor-that-is-based-on-a-domain-model"></a>Bir etki alanı modeline dayalı bir yönerge işlemcisi oluşturmak için etki alanına özgü dil araçları kullanmak için  
  
1. Aşağıdaki özelliklere sahip bir etki alanına özgü dil çözümü oluşturun:  
  
   - Ad: DSLMinimalTest  
  
   - Çözüm şablonu: en az bir dil  
  
   - Dosya uzantısı: en düşük  
  
   - Şirket adı: Fabrikam  
  
     Bir etki alanına özgü dil çözümü oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir etki alanına özgü dil çözümü oluşturma](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
2. Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
   > [!IMPORTANT]
   >  Bu adım, yönerge işlemcisi oluşturur ve anahtar için bunu kayıt defterine ekler.  
  
3. Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Başlat**.  
  
    İkinci bir örneğini [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] açılır.  
  
4. Deneysel yapı içinde **Çözüm Gezgini**, dosyayı çift **sample.min**.  
  
    Dosyası tasarımcıda açılır. Model iki öğe, ExampleElement1 ve ExampleElement2 ve bunlar arasında bir bağlantı olduğuna dikkat edin.  
  
5. İkinci örneğini kapatın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
6. Çözüm kaydedin ve ardından etki alanına özgü dil tasarımcısını kapatın.  
  
## <a name="connecting-a-custom-text-template-host-to-a-directive-processor"></a>Özel metin şablonu ana bilgisayar bir yönerge işlemcisine bağlama  
 Yönerge işlemcisini ve oluşturduğunuz özel metin şablonu konağı yönerge işlemcisini oluşturduktan sonra bağlandığınız [izlenecek yol: bir özel metin şablonu konağı oluşturma](../modeling/walkthrough-creating-a-custom-text-template-host.md).  
  
#### <a name="to-connect-a-custom-text-template-host-to-the-generated-directive-processor"></a>Bir özel metin şablonu konağı üretilen bir yönerge işlemcisine bağlanmak için  
  
1.  CustomHost çözümü açın.  
  
2.  Üzerinde **proje** menüsünü tıklatın **Başvuru Ekle**.  
  
     **Başvuru Ekle** iletişim kutusu açılır **.NET** sekmesi görüntülenir.  
  
3.  Aşağıdaki başvuruları ekleyin:  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.11.0  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.Interfaces.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.VSHost.11.0  
  
4.  Program.cs veya Module1.vb üst kısmında, aşağıdaki kod satırını ekleyin:  
  
    ```csharp  
    using Microsoft.Win32;  
    ```  
  
    ```vb  
    Imports Microsoft.Win32  
    ```  
  
5.  Bir özellik için kodu bulun `StandardAssemblyReferences`, aşağıdaki kodla değiştirin:  
  
    > [!NOTE]
    >  Bu adımda, ana destekleyecek oluşturulan yönerge işlemcisi tarafından gerekli derlemelere başvurular ekleyin.  
  
    ```csharp  
    //the host can provide standard assembly references  
    //the engine will use these references when compiling and  
    //executing the generated transformation class  
    //--------------------------------------------------------------  
    public IList<string> StandardAssemblyReferences  
    {  
        get  
        {  
            return new string[]  
            {  
                //if this host searches standard paths and the GAC  
                //we can specify the assembly name like this:  
                //"System"  
                //since this host only resolves assemblies from the   
                //fully qualified path and name of the assembly  
                //this is a quick way to get the code to give us the  
                //fully qualified path and name of the System assembly  
                //---------------------------------------------------------  
                typeof(System.Uri).Assembly.Location,  
                            typeof(System.Uri).Assembly.Location,  
                typeof(Microsoft.VisualStudio.Modeling.ModelElement).Assembly.Location,  
                typeof(Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape).Assembly.Location,  
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating).Assembly.Location,  
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation).Assembly.Location  
  
            };  
        }  
    }  
    ```  
  
6.  İşlev kodunu bulun `ResolveDirectiveProcessor`, aşağıdaki kodla değiştirin:  
  
    > [!IMPORTANT]
    >  Bu kod, bağlanmak istediğiniz üretilen bir yönerge işlemcisine adını sabit kodlanmış başvurular içerir. Kolayca bu daha genel yapabileceğiniz, kayıt defterinde listelenen tüm yönerge işlemcileri için bu durumda görünüyor ve bir eşleşme bulmayı dener. Bu durumda, konak ile üretilen bir yönerge işlemcisine işe yarar.  
  
    ```csharp  
    //the engine calls this method based on the directives the user has   
            //specified it in the text template  
            //this method can be called 0, 1, or more times  
            //---------------------------------------------------------------------  
            public Type ResolveDirectiveProcessor(string processorName)  
            {  
                //check the processor name, and if it is the name of the processor the   
                //host wants to support, return the type of the processor  
                //---------------------------------------------------------------------  
                if (string.Compare(processorName, "DSLMinimalTestDirectiveProcessor", StringComparison.InvariantCultureIgnoreCase) == 0)  
                {  
                    try  
                    {  
                        string keyName = @"Software\Microsoft\VisualStudio\10.0Exp_Config\TextTemplating\DirectiveProcessors\DSLMinimalTestDirectiveProcessor";  
                        using (RegistryKey specificKey = Registry.CurrentUser.OpenSubKey(keyName))  
                        {  
                            if (specificKey != null)  
                            {  
                                List<string> names = new List<String>(specificKey.GetValueNames());  
                                string classValue = specificKey.GetValue("Class") as string;  
                                if (!string.IsNullOrEmpty(classValue))  
                                {  
                                    string loadValue = string.Empty;  
                                    System.Reflection.Assembly processorAssembly = null;  
                                    if (names.Contains("Assembly"))  
                                    {  
                                        loadValue = specificKey.GetValue("Assembly") as string;  
                                        if (!string.IsNullOrEmpty(loadValue))  
                                        {  
                                            //the assembly must be installed in the GAC  
                                            processorAssembly = System.Reflection.Assembly.Load(loadValue);  
                                        }  
                                    }  
                                    else if (names.Contains("CodeBase"))  
                                    {  
                                        loadValue = specificKey.GetValue("CodeBase") as string;  
                                        if (!string.IsNullOrEmpty(loadValue))  
                                        {  
                                            //loading local assembly  
                                            processorAssembly = System.Reflection.Assembly.LoadFrom(loadValue);  
                                        }  
                                    }  
                                    if (processorAssembly == null)  
                                    {  
                                        throw new Exception("Directive Processor not found");  
                                    }  
                                    Type processorType = processorAssembly.GetType(classValue);  
                                    if (processorType == null)  
                                    {  
                                        throw new Exception("Directive Processor not found");  
                                    }  
                                    return processorType;  
                                }  
                            }  
                        }  
                    }  
                    catch (Exception e)  
                    {  
                        //if the directive processor can not be found, throw an error  
                        throw new Exception("Directive Processor not found");  
                    }  
                }  
  
                //if the directive processor is not one this host wants to support  
                throw new Exception("Directive Processor not supported");  
            }  
    ```  
  
7.  Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet**.  
  
8.  Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
## <a name="testing-the-custom-host-with-the-directive-processor"></a>Özel ana bilgisayarı ile yönerge işlemcisini test etme  
 İlk özel metin şablonu ana bilgisayarı sınamak için üretilen bir yönerge işlemcisine çağıran bir metin şablonu yazmanız gerekir. Ardından, özel ana bilgisayarı çalıştırırsınız, metin şablonunun adını geçirin ve yönerge düzgün şekilde işlendiğinden emin olun.  
  
#### <a name="to-create-a-text-template-to-test-the-custom-host"></a>Özel ana bilgisayarı sınamak amacıyla metin şablonu oluşturmak için  
  
1.  Bir metin dosyası oluşturun ve adlandırın `TestTemplateWithDP.tt`. Not Defteri gibi herhangi bir metin düzenleyicisi, dosyayı oluşturmak için kullanabilirsiniz.  
  
2.  Aşağıdakileri metin dosyasına ekleyin:  
  
    > [!NOTE]
    >  Metin şablonunun programlama diline özel ana bilgisayarı eşleşmesi gerekmez.  
  
    ```csharp  
    Text Template Host Test  
  
    <#@ template debug="true" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
    <# //this is the call to the examplemodel directive in the generated directive processor #>  
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>  
    <# //uncomment this line to test that the host allows the engine to set the extension #>  
    <# //@ output extension=".htm" #>  
  
    <# //uncomment this line if you want to see the generated transformation class #>  
    <# //System.Diagnostics.Debugger.Break(); #>  
    <# //this code uses the results of the examplemodel directive #>  
    <#  
        foreach ( ExampleElement box in this.ExampleModel.Elements )   
        {   
            WriteLine("Box: {0}", box.Name);  
  
            foreach (ExampleElement linkedTo in box.Targets)  
            {  
                WriteLine("Linked to: {0}", linkedTo.Name);  
            }  
  
            foreach (ExampleElement linkedFrom in box.Sources)  
            {  
                WriteLine("Linked from: {0}", linkedFrom.Name);  
            }  
  
            WriteLine("");  
        }   
    #>  
    ```  
  
    ```vb  
    Text Template Host Test  
  
    <#@ template debug="true" language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
  
    <# 'this is the call to the examplemodel directive in the generated directive processor #>  
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>  
  
    <# 'Uncomment this line to test that the host allows the engine to set the extension. #>  
    <# '@ output extension=".htm" #>  
  
    <# 'Uncomment this line if you want to see the generated transformation class. #>  
    <# 'System.Diagnostics.Debugger.Break() #>  
  
    <# 'this code uses the results of the examplemodel directive #>  
  
    <#      
       For Each box as ExampleElement In Me.ExampleModel.Elements   
  
           WriteLine("Box: {0}", box.Name)  
  
            For Each LinkedTo as ExampleElement In box.Targets  
                WriteLine("Linked to: {0}", LinkedTo.Name)  
            Next  
  
            For Each LinkedFrom as ExampleElement In box.Sources  
                WriteLine("Linked from: {0}", LinkedFrom.Name)  
            Next  
  
            WriteLine("")  
  
       Next   
    #>  
    ```  
  
3.  Kod içinde \<bilgisayarınızı yolu > ile ilk yordamda oluşturduğunuz özel tasarım dili Sample.min dosyasının yolu.  
  
4.  Dosyayı kaydedin ve kapatın.  
  
#### <a name="to-test-the-custom-host"></a>Özel ana bilgisayarı sınamak için  
  
1.  Bir komut istemi penceresi açın.  
  
2.  Özel ana bilgisayar için yürütülebilir dosyanın yolunu yazın, ancak henüz ENTER'a basmayın.  
  
     Örneğin, şunu yazın:  
  
     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`  
  
    > [!NOTE]
    >  Adresi yazmak yerine CustomHost.exe dosyasına göz atabilir, **Windows Explorer**ve ardından da dosyayı komut istemi penceresine sürükleyebilirsiniz.  
  
3.  Bir boşluk yazın.  
  
4.  Metin şablonu dosyasının yolunu yazın ve ENTER tuşuna basın.  
  
     Örneğin, şunu yazın:  
  
     `<YOUR PATH>TestTemplateWithDP.txt`  
  
    > [!NOTE]
    >  Adresi yazmak yerine TestTemplateWithDP.txt dosyasına göz atabilir, **Windows Explorer**ve ardından da dosyayı komut istemi penceresine sürükleyebilirsiniz.  
  
     Özel ana bilgisayar uygulaması çalışır ve metin şablonu dönüştürme süreci başlar.  
  
5.  İçinde **Windows Explorer**, TestTemplateWithDP.txt dosyasını içeren klasöre göz atın.  
  
     Klasör, dosya TestTemplateWithDP1.txt da içerir.  
  
6.  Metin şablonu dönüştürme sonuçlarını görmek için bu dosyayı açın.  
  
     Sonuçları oluşturulan metin çıktısı görüntülenir ve şu şekilde görünmelidir:  
  
    ```  
    Text Template Host Test  
  
    Box: ExampleElement1  
    Linked to: ExampleElement2  
  
    Box: ExampleElement2  
    Linked from: ExampleElement1  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Özel Metin Şablonu Konağı Oluşturma](../modeling/walkthrough-creating-a-custom-text-template-host.md)



