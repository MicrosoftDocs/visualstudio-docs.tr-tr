---
title: Visual Studio API kullanarak UML modeli açın | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API, opening models in Visual Studio
ms.assetid: 38423682-f2a7-4d2a-a2cd-fd680e9b4b4d
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 62b8700e85ccab271dbfdc4f9bac504ee64197a6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779625"
---
# <a name="open-a-uml-model-by-using-the-visual-studio-api"></a>Visual Studio API kullanarak UML modeli açma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ayrıca API kullanarak modelleri ve diyagramları Visual Studio kullanıcı arabiriminde açabilirsiniz.  
  
 Kullanıcıya görünür yapmadan program kodundaki modeli okumak istiyorsanız, aşağıdaki yöntemleri kullanabilirsiniz:  
  
-   Visual Studio Model veri yolu, bunları içindeki modellere ve öğelere erişmenize olanak sağlar ve bir model ile başka arasında bağlantı yapmak için standart bir yöntemini sağlar. Daha fazla bilgi için [tümleştirme UML modellerini diğer modeller ve araçlarla birlikte](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
-   Salt okunur modunda model açabilirsiniz. Daha fazla bilgi için [program kodundaki UML modelini okuma](../modeling/read-a-uml-model-in-program-code.md).  
  
##  <a name="Showing"></a> Visual Studio'da modelleri ve diyagramları açma  
 Kullanıcı arabiriminde model açmak için standart bir Visual Studio API kullanın. `EnvDTE.DTE`. Modelleme projesi öğeleri üzerinde gerçekleştirebileceğiniz iki yararlı dönüştürme vardır:  
  
- `EnvDTE.Project` ve ondan dönüştürme `IModelingProject`, proje bir modelleme projesi ise ve geçerli AppDomain'e durumunda.  
  
- `EnvDTE.ProjectItem` ve ondan dönüştürme `IDiagramContext`, öğe bir UML diyagram ise.  
  
  Aşağıdaki örnek için projenizin bu başvuruları içeri aktarması gerekir:  
  
- EnvDTE  
  
- Microsoft.VisualStudio.ArchitectureTools.Extensibility  
  
- Microsoft.VisualStudio.Modeling.Sdk.[version]  
  
- Microsoft.VisualStudio.Modeling.Sdk.Diagrams. [sürüm]  
  
- Microsoft.VisualStudio.Shell.Immutable. [sürüm]  
  
- Microsoft.VisualStudio.Uml.Interfaces  
  
- System.ComponentModel.Composition  
  
  Bu örnek, Visual Studio'da UML modeli açar:  
  
```  
using EnvDTE; // Visual Studio API for loading diagrams  
using   
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Modeling;   
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;    
   // for ICommandExtension and other handler types  
using Microsoft.VisualStudio.Uml.Classes;   
   // for basic UML types  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   // for model construction methods  
using EnvDTE;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;  
Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;   
                             // for IDiagram   
...  
```  
  
 Bir Visual Studio Uzantısında ana hizmet sağlayıcısına erişimi sağlamak için bu bildirimi yapabilirsiniz:  
  
```  
[Import] public Microsoft.VisualStudio.Shell.SVsServiceProvider ServiceProvider {get;set;}  
...  
```  
  
 Bir yöntem içinde bir proje, örneğin, geçerli proje erişebilirsiniz:  
  
```  
DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;  
IModelingProject modelingProject = project as IModelingProject;  
if (modelingProject == null) return; // not a modeling project  
  
// Access the model's store and contents.  
IModelStore store = modelingProject.Store;  
foreach (IElement element in store.Root.OwnedElements) {...}  
  
// Open all the project's diagrams.  
foreach (ProjectItem item in project.ProjectItems)  
{   
     IDiagramContext modelingItem = item as IDiagramContext;  
     if (modelingItem == null)  
         continue; // not a model diagram  
     IDiagram diagram = modelingItem.CurrentDiagram;  
     if (diagram == null)  
     {  
        // Diagram is closed. Open it.  
        item.Open().Activate();  
        diagram = modelingItem.CurrentDiagram;  
     }  
     // Access the shapes.  
     foreach (IShape<IElement> shape   
               in diagram.GetChildShapes<IElement>())  
     {  
       IElement displayedElement = shape.Element;  
       ...  
     }  
   }  
}   
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML API ile programlama](../modeling/programming-with-the-uml-api.md)   
 [UML modellerini ve diyagramları genişletme](../modeling/extend-uml-models-and-diagrams.md)



