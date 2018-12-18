---
title: Bir VS uzantısında metin dönüştürmeyi çağırma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64674976-841f-43cb-8e61-0645c8a89eec
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0751229e778e13375698f591d789edfd318b3ffc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298630"
---
# <a name="invoking-text-transformation-in-a-vs-extension"></a>Bir VS Uzantısında Metin Dönüştürmeyi Çağırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yazıyorsanız bir [Visual Studio Uzantısı](http://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14) gibi bir menü komutu veya [etki alanına özgü dil](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md), metin şablonlarını dönüştürmek için metin şablonu oluşturma hizmetini kullanabilirsiniz. Alma <xref:Microsoft.VisualStudio.TextTemplating.VSHost.STextTemplating> hizmet ve bunu <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>.  
  
## <a name="getting-the-text-templating-service"></a>Metin şablonu oluşturma hizmetini alma  
  
```csharp  
using Microsoft.VisualStudio.TextTemplating;  
using Microsoft.VisualStudio.TextTemplating.VSHost;  
...  
// Get a service provider – how you do this depends on the context:  
IServiceProvider serviceProvider = ...; // An instance of EnvDTE, for example   
  
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
  
// Process a text template:  
string result = t4.ProcessTemplate(filePath, System.IO.File.ReadAllText(filePath));  
  
```  
  
## <a name="passing-parameters-to-the-template"></a>Parametreleri şablona geçirme  
 Parametreleri şablona geçirebilirsiniz. Şablon içinde parametre değerlerini kullanarak alabilirsiniz `<#@parameter#>` yönergesi.  
  
 Parametre türü için, seri hale getirilebilen veya sıralanabilen bir tür kullanmalısınız. Diğer bir deyişle, türü ile bildirilmelidir <xref:System.SerializableAttribute>, veya nesnesinden türetilmesi gerekir <xref:System.MarshalByRefObject>. Bu kısıtlama gereklidir çünkü metin şablonu ayrı bir AppDomain içinde yürütülür. Gibi tüm yerleşik türler **System.String** ve **System.Int32** seri hale getirilebilir.  
  
 Parametre değerlerini geçirmek için çağıran kodun değerleri koyabilir, `Session` sözlük veya <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 Aşağıdaki örnek bir kısa test şablonunu dönüştürmek için her iki yöntemi kullanmaktadır:  
  
```  
using Microsoft.VisualStudio.TextTemplating;  
using Microsoft.VisualStudio.TextTemplating.VSHost;  
...  
// Get a service provider – how you do this depends on the context:  
IServiceProvider serviceProvider = dte;   
  
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost sessionHost = t4 as ITextTemplatingSessionHost;  
  
// Create a Session in which to pass parameters:  
sessionHost.Session = sessionHost.CreateSession();  
sessionHost.Session["parameter1"] = "Hello";  
sessionHost.Session["parameter2"] = DateTime.Now;  
  
// Pass another value in CallContext:  
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("parameter3", 42);  
  
// Process a text template:  
string result = t4.ProcessTemplate("",  
   // This is the test template:  
   "<#@parameter type=\"System.String\" name=\"parameter1\"#>"  
 + "<#@parameter type=\"System.DateTime\" name=\"parameter2\"#>"  
 + "<#@parameter type=\"System.Int32\" name=\"parameter3\"#>"  
 + "Test: <#=parameter1#>    <#=parameter2#>    <#=parameter3#>");  
  
// This test code yields a result similar to the following line:  
//     Test: Hello    07/06/2010 12:37:45    42  
  
```  
  
## <a name="error-reporting-and-the-output-directive"></a>Hata Raporlama ve Çıkış Yönergesi  
 İşleme sırasında ortaya çıkan hatalar görüntülenmesi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hata penceresi. Ayrıca, hataların uygulayan geri aramayı belirterek bilgilendirilebilirsiniz <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplatingCallback>.  
  
 Sonuç dizesini bir dosyaya yazmak istiyorsanız, hangi dosya uzantısının bilmek isteyebilirsiniz ve kodlamanın belirtildiğini `<#@output#>` yönergesinde şablonda. Bu bilgiler, geri çağırmanıza da geçirilir. Daha fazla bilgi için [T4 çıkış yönergesi](../modeling/t4-output-directive.md).  
  
```csharp  
void ProcessMyTemplate(string MyTemplateFile)  
{  
  string templateContent = File.ReadAllText(MyTemplateFile);  
  T4Callback cb = new T4Callback();  
  // Process a text template:  
  string result = t4.ProcessTemplate(MyTemplateFile, templateContent, cb);  
  // If there was an output directive in the MyTemplateFile,  
  // then cb.SetFileExtension() will have been called.  
  // Determine the output file name:  
  string resultFileName =   
    Path.Combine(Path.GetDirectoryName(MyTemplateFile),   
        Path.GetFileNameWithoutExtension(MyTemplateFile))   
      + cb.fileExtension;  
  // Write the processed output to file:  
  File.WriteAllText(resultFileName, result, cb.outputEncoding);  
  // Append any error messages:  
  if (cb.errorMessages.Count > 0)  
  {  
    File.AppendAllLines(resultFileName, cb.errorMessages);  
  }  
}  
  
class T4Callback : ITextTemplatingCallback  
{  
  public List<string> errorMessages = new List<string>();  
  public string fileExtension = ".txt";  
  public Encoding outputEncoding = Encoding.UTF8;  
  
  public void ErrorCallback(bool warning, string message, int line, int column)  
  { errorMessages.Add(message); }  
  
  public void SetFileExtension(string extension)  
  { fileExtension = extension; }  
  
  public void SetOutputEncoding(Encoding encoding, bool fromOutputDirective)  
  { outputEncoding = encoding; }  
}  
  
```  
  
 Kod, şuna benzer bir şablon dosyasıyla test edilebilir:  
  
```  
<#@output extension=".htm" encoding="ASCII"#>  
<# int unused;  // Compiler warning "unused variable"  
#>  
Sample text.  
```  
  
 Derleyici Uyarısı görünür [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hata penceresi ve ayrıca oluşturacağını çağrısı `ErrorCallback`.  
  
## <a name="reference-parameters"></a>Başvuru parametreleri  
 Türetilen bir parametre sınıfını kullanarak değerleri bir metin şablonu dışına geçirebilirsiniz <xref:System.MarshalByRefObject>.  
  
## <a name="related-topics"></a>İlgili Konular  
 Önceden işlenmiş bir metin şablonundan metin oluşturmak için:  
 Çağrı `TransformText()` oluşturulan sınıfın yöntemi. Daha fazla bilgi için [T4 metin şablonları ile çalışma süresi metni oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Dışında metin oluşturmak için bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısı:  
 Özel bir ana bilgisayar tanımlayın. Daha fazla bilgi için [özel konak kullanarak metin şablonlarını işleme](../modeling/processing-text-templates-by-using-a-custom-host.md).  
  
 Daha sonra derlenebilecek ve yürütülebilecek kaynak kodu oluşturmak için:  
 Çağrı `t4.PreprocessTemplate()` yöntemi <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>.



