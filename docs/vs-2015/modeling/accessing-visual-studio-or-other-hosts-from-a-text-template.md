---
title: Bir metin şablonundan Visual Studio 2015 veya diğer Konaklara erişme | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: dd5f3c1dfacfa256422235647b877373aa714487
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063496"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>Metin Şablonundan Visual Studio'ya veya diğer Konaklara Erişme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metin şablonunda, yöntemleri ve şablon gibi yürüten bir ana bilgisayar tarafından kullanıma sunulan özellikler kullanabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 Bu değil önceden işlenmiş metin şablonlarını normal metin şablonları için geçerlidir.

## <a name="obtaining-access-to-the-host"></a>Konağa erişim elde etme
 Ayarlama `hostspecific="true"` içinde `template` yönergesi. Bu kullanmanıza olanak tanır `this.Host`, türüne sahip <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Bu tür, örneğin, dosya adlarını çözümleme ve hataları günlüğe kaydetmek için kullanabileceğiniz üyeleri var.

### <a name="resolving-file-names"></a>Dosya adları çözme
 Metin şablonu göreli bir dosyanın tam yolunu bulmak için bunu kullanın. Host.ResolvePath().

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

### <a name="displaying-error-messages"></a>Hata iletilerini görüntüleme
 Bu örnekte, şablon dönüştürdüğünüzde iletileri günlüğe kaydeder. Ana bilgisayar ise [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], hata penceresine eklenir.

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

## <a name="using-the-visual-studio-api"></a>Visual Studio API kullanma
 Metin şablonunda çalıştırıldığında [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], kullanabileceğiniz `this.Host` Erişim Hizmetleri tarafından sağlanan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve paketleri veya yüklenen uzantıları.

 Ayarlama hostspecific = "true" ve dönüştürme `this.Host` için <xref:System.IServiceProvider>.

 Bu örnekte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] API <xref:EnvDTE.DTE>, hizmet olarak:

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

## <a name="using-hostspecific-with-template-inheritance"></a>Şablon kalıtım hostSpecific kullanma
 Belirtin `hostspecific="trueFromBase"` da kullanıyorsanız `inherits` özniteliği ve belirten bir şablondan devralıyorsanız `hostspecific="true"`. Bu bir derleyici uyarısı etkisine önler, özellik `Host` iki kez bildirilmiş.
