---
title: T4 Parametre yönergesi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d590387-1d9d-40a5-a72c-65fae7a8bdf3
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 87e493667af1626cd97e575ddb614e7fd12c21d3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294560"
---
# <a name="t4-parameter-directive"></a>T4 Parametre Yönergesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçinde bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] metin şablonu `parameter` yönergesine geçirilen dış bağlamdan değerlerden başlatılır, şablon kodunun özelliklerinde bildirir. Metin dönüştürme çağıran bir kod yazarsanız, bu değerleri ayarlayabilirsiniz.  
  
## <a name="using-the-parameter-directive"></a>Parametre yönergesini kullanma  
  
```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 `parameter` Yönergesine geçirilen dış bağlamdan değerlerden başlatılır, şablon kodunun özelliklerinde bildirir. Metin dönüştürme çağıran bir kod yazarsanız, bu değerleri ayarlayabilirsiniz. Değerleri de geçirilebilir `Session` sözlük veya <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 Herhangi bir Uzaktan erişilebilir türde parametreler bildirebilirsiniz. Diğer bir deyişle, türü ile bildirilmelidir <xref:System.SerializableAttribute>, veya öğesinden türetilmelidir <xref:System.MarshalByRefObject>. Bu şablon işlenme AppDomain'e geçirilecek parametre değerlerini sağlar.  
  
 Örneğin, aşağıdaki içeriğe sahip bir metin şablonu yazabilirsiniz:  
  
```  
<#@ template language="C#" #>  
  
<#@ parameter type="System.Int32" name="TimesToRepeat" #>  
  
<# for (int i = 0; i < TimesToRepeat; i++) { #>  
Line <#= i #>  
<# } #>  
  
```  
  
## <a name="passing-parameter-values-to-a-template"></a>Bir şablon parametre değerlerini geçirme  
 Yazıyorsanız bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısı gibi bir menü komutu veya bir olay işleyicisi, metin şablonu oluşturma hizmetini kullanarak bir şablonu işleyebilir:  
  
```csharp  
// Get a service provider – how you do this depends on the context:  
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example   
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;  
// Create a Session in which to pass parameters:  
host.Session = host.CreateSession();  
// Add parameter values to the Session:  
session["TimesToRepeat"] = 5;  
// Process a text template:  
string result = t4.ProcessTemplate("MyTemplateFile.t4",  
  System.IO.File.ReadAllText("MyTemplateFile.t4"));  
  
```  
  
## <a name="passing-values-in-the-call-context"></a>Değerleri çağrı bağlamında geçirme  
 Alternatif olarak, mantıksal olarak veri değerlerinin geçmesini sağlayabilirsiniz <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 Aşağıdaki örnek, her iki yöntemi kullanarak değerleri geçirir:  
  
```csharp  
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;  
host.Session = host.CreateSession();  
// Pass a value in Session:  
host.Session["p1"] = 32;  
// Pass another value in CallContext:  
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");  
  
// Process a small template inline:  
string result = t4.ProcessTemplate("",   
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"  
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"  
 + "Test <#=p1#> <#=p2#>");  
  
// Result value is:  
//     Test 32 test  
  
```  
  
## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Değerlerin bir çalışma zamanı (önceden işlenmiş) metin şablonu  
 Kullanılacak genellikle gerekli değildir `<#@parameter#>` çalışma zamanı (önceden işlenmiş) metin şablonları ile yönergesi. Bunun yerine, ek bir oluşturucuda veya bir ayarlanabilir özelliği parametre değerlerini geçirmek oluşturulan kodun tanımlayabilirsiniz. Daha fazla bilgi için [T4 metin şablonları ile çalışma süresi metni oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Ancak, kullanmak istiyorsanız `<#@parameter>` bir çalışma zamanı şablonunda değerleri için oturumu sözlüğünü kullanarak geçirebilirsiniz. Örnek olarak, dosya adlı önceden işlenmiş şablon olarak oluşturduğunuz düşünün `PreTextTemplate1`. Aşağıdaki kodu kullanarak şablon programınızda çağırabilirsiniz.  
  
```csharp  
PreTextTemplate1 t = new PreTextTemplate1();  
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();  
t.Session["TimesToRepeat"] = 5;  
// Add other parameter values to t.Session here.  
t.Initialize(); // Must call this to transfer values.  
string resultText = t.TransformText();  
  
```  
  
## <a name="obtaining-arguments-from-texttemplateexe"></a>Bağımsız değişkenler TextTemplate.exe edinme  
  
> [!IMPORTANT]
>  `parameter` Yönergesi alamadı kümesinde değerleri `–a` parametresinin `TextTransform.exe` yardımcı programı. Bu değerleri almak üzere `hostSpecific="true"` içinde `template` yönergesi ve kullanım `this.Host.ResolveParameterValue("","","argName")`.



