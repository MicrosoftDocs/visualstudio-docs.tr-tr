---
title: T4 İçe yönergesi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6fa8f027fbb3418fff47b0459628afb691c8a05a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893682"
---
# <a name="t4-import-directive"></a>T4 İçe Aktarma Yönergesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod blokları bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] T4 metin şablonu `import` yönergesi, tam bir ad sağlamadan başka bir ad alanındaki öğeler başvurmak olanak sağlar. Denk olan `using` C# veya `imports` içinde [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)].  
  
 T4 metin şablonlarını yazmayla ilgili genel bilgiler için bkz: [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md).  
  
## <a name="using-the-import-directive"></a>İçeri Aktarma Yönergesini Kullanma  
  
```  
<#@ import namespace="namespace" #>  
```  
  
 Bu örnekte, şablonu kodu, System.IO üyeleri için açık ad alanını atlayabilir:  
  
```  
<#@ import namespace="System.IO" #>  
<#   
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File  
#>   
The file contains: <#=  fileContent #>  
```  
  
## <a name="standard-imports"></a>Standart İçeri Aktarmalar  
 Aşağıdaki ad alanı otomatik olarak içeri aktarılır, böylece onun için içeri aktarma yönergesi yazmanıza gerek kalmaz:  
  
- `System`  
  
  Ayrıca, özel yönerge kullanıyorsanız, yönerge işlemcisi bazı ad alanlarını otomatik olarak içeri aktarabilir.  
  
  Örneğin, etki alanına özgü dil (DSL) için şablonlar yazarsanız, aşağıdaki ad alanları için içeri aktarma yönergeleri yazmak gerekmez:  
  
- `Microsoft.VisualStudio.Modeling`  
  
- DSL'nizin ad alanı  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [T4 Derleme Yönergesi](../modeling/t4-assembly-directive.md)



