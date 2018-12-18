---
title: Bir VS Uzantısında Metin Dönüştürmeyi Çağırma
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 01a2b4863736b22e08cf2075e6402d836e9cc671
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926806"
---
# <a name="invoking-text-transformation-in-a-vs-extension"></a>Bir VS Uzantısında Metin Dönüştürmeyi Çağırma
Bir menü komutu gibi bir Visual Studio uzantısı yazıyorsanız veya [etki alanına özgü dil](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md), metin şablonlarını dönüştürmek için metin şablonu oluşturma hizmetini kullanabilirsiniz. Alma <xref:Microsoft.VisualStudio.TextTemplating.VSHost.STextTemplating> hizmet ve bunu <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>.

## <a name="getting-the-text-templating-service"></a>Metin şablonu oluşturma hizmetini alma

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
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
// Get a service provider - how you do this depends on the context:
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
 İşleme sırasında ortaya çıkan hatalar, Visual Studio hata penceresinde görüntülenir. Ayrıca, hataların uygulayan geri aramayı belirterek bilgilendirilebilirsiniz <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplatingCallback>.

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

 Derleyici Uyarısı Visual Studio hata penceresinde görünür ve bir çağrı oluşturur `ErrorCallback`.

## <a name="reference-parameters"></a>Başvuru parametreleri
 Türetilen bir parametre sınıfını kullanarak değerleri bir metin şablonu dışına geçirebilirsiniz <xref:System.MarshalByRefObject>.

## <a name="related-topics"></a>İlgili Konular
 Önceden işlenmiş metin şablonundan metin oluşturmak için: çağrı `TransformText()` oluşturulan sınıfın yöntemi. Daha fazla bilgi için [T4 metin şablonları ile çalışma süresi metni oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Visual Studio uzantısı dışında metin oluşturmak için: özel bir ana bilgisayar tanımlayın. Daha fazla bilgi için [özel konak kullanarak metin şablonlarını işleme](../modeling/processing-text-templates-by-using-a-custom-host.md).

 Daha sonra derlenmiş ve yürütülen kaynak kodu oluşturmak için: çağrı `t4.PreprocessTemplate()` yöntemi <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>.
