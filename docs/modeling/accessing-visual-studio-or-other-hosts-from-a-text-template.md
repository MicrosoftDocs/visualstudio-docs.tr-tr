---
title: Metin Şablonundan Visual Studio'ya veya diğer Konaklara Erişme
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 9bb7bce5cb047018540599c9488fa4471dad2d1c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059304"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>Metin Şablonundan Visual Studio’ya veya diğer Konaklara Erişme

Metin şablonunda, yöntemleri ve şablonu yürütür ana bilgisayar tarafından gösterilen özelliklerin kullanabilirsiniz. Visual Studio, bir konak örneğidir.

> [!NOTE]
> Konak yöntemleri ve özellikleri normal metin şablonlarında kullanabilirsiniz, ancak değil *önceden işlenmiş* metin şablonları.

## <a name="obtain-access-to-the-host"></a>Konak erişim sağlamak

Konak erişmek için `hostspecific="true"` içinde `template` yönergesi. Artık `this.Host`, türüne sahip <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> Türünün, örneğin, dosya adlarını çözümleme ve hataları günlüğe kaydetmek için kullanabileceğiniz üyeleri vardır.

### <a name="resolve-file-names"></a>Dosya adlarını çözümleme

Metin şablonu göreli bir dosyanın tam yolunu bulmak için kullanın `this.Host.ResolvePath()`.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>
```

### <a name="display-error-messages"></a>Hata iletilerini görüntüleme

Bu örnekte, şablon dönüştürdüğünüzde iletileri günlüğe kaydeder. Visual Studio ana bilgisayar ise hataları eklenen **hata listesi**.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.CodeDom.Compiler" #>
<#
  string message = "test message";
  this.Host.LogErrors(new CompilerErrorCollection()
    { new CompilerError(
       this.Host.TemplateFile, // Identify the source of the error.
       0, 0, "0",   // Line, column, error ID.
       message) }); // Message displayed in error window.
#>
```

## <a name="use-the-visual-studio-api"></a>Visual Studio API kullanın

Visual Studio'da bir metin şablonu yürütme, kullanabileceğiniz `this.Host` Visual Studio ve paketleri veya yüklü uzantılar tarafından sağlanan Erişim Hizmetleri için.

Ayarlama hostspecific = "true" ve dönüştürme `this.Host` için <xref:System.IServiceProvider>.

Bu örnek, Visual Studio API alır <xref:EnvDTE.DTE>, hizmet olarak:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>
```

## <a name="use-hostspecific-with-template-inheritance"></a>Şablon kalıtım hostSpecific kullanın

Belirtin `hostspecific="trueFromBase"` da kullanıyorsanız `inherits` özniteliği ve belirten bir şablondan devralıyorsanız `hostspecific="true"`. Aksi takdirde, derleyici, uyarısı özelliği alabilirsiniz `Host` iki kez bildirilmiş.