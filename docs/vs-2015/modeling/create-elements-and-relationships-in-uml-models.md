---
title: UML modellerinde öğe ve ilişkiler oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API
ms.assetid: cae81d32-8cc7-4f7c-9f00-20119952bc51
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5ed918bc96168196400dd34d87ec65574fdfc5b6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785878"
---
# <a name="create-elements-and-relationships-in-uml-models"></a>UML modellerinde öğe ve ilişki oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir Visual Studio uzantısı için program kodu içinde oluşturun ve öğeleri ve ilişkileri silin.  
  
## <a name="create-a-model-element"></a>Model öğesi oluşturma  
  
### <a name="namespace-imports"></a>Namespace içeri aktarmalar  
 Aşağıdaki içermelidir `using` deyimleri.  
  
 Oluşturma yöntemleri, bu ad alanında uzantı yöntemlerini olarak tanımlanır:  
  
 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`  
  
### <a name="obtain-the-owner-of-the-element-you-want-to-create"></a>Oluşturmak istediğiniz öğeyi sahibini edinin  
 Bir model, her öğe, model kökünün dışında bir sahibi sahip olacak şekilde tek bir ağaç oluşturur. Model kökü türünde `IModel`, bir tür olduğu `IPackage`.  
  
 Belirli bir şemada görüntülenecek bir öğe oluşturuyorsanız, örneğin, kullanıcının geçerli diyagram, genellikle, bu diyagrama bağlı paketindeki oluşturmanız gerekir. Örneğin:  
  
```  
IPackage linkedPackage = Context.CurrentDiagram.Element as IPackage;  
```  
  
 Bu tabloda ortak modeli öğeleri sahiplik özetlenmektedir:  
  
|Oluşturulacak öğe|Sahip|  
|---------------------------|-----------|  
|`IActor, IUseCase, IComponent, IClass, IInterface, IEnumeration`<br /><br /> `IActivity, IInteraction`|`IPackage, IModel`|  
|`IAttribute, IOperation`|`IClass, IInterface`|  
|`IPart, IPort`|`IComponent`|  
|`IAction, IObjectNode`|`IActivity`|  
|`ILifeline, IMessage, ICombinedFragment`|`IInteraction`|  
  
### <a name="invoke-the-create-method-on-the-owner"></a>Sahip üzerinde Create yöntemini çağırma  
 Yöntem adı biçimindedir: `Create` *OwnedType*`()`. Örneğin:  
  
```  
IUseCase usecase1 = linkedPackage.CreateUseCase();  
```  
  
 Bazı türler, özellikle sıralı diyagramlarında daha karmaşık oluşturma yöntemleri vardır. Bkz: [UML API kullanarak Düzenle UML sıralı diyagramlar](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).  
  
 Bazı öğe türleri için yaşam süresi boyunca, bir öğenin sahibi değiştirebilir kullanarak `SetOwner(newOwner)`.  
  
### <a name="set-the-name-and-other-properties"></a>Adı ve diğer özellikleri ayarlayın  
  
```  
usecase1.Name = "user logs in";  
```  
  
### <a name="example"></a>Örnek  
  
```  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.Uml.Extensions;  
...  
 void InstantiateObserverPattern (IPackage package, string namePrefix)  
 {    IInterface observer = package.CreateInterface();  
      observer.Name = namePrefix + "Observer";  
      IOperation operation = observer.CreateOperation();  
      operation.Name = "Update";  
      IClass subject = package.CreateClass();  
      subject.Name = namePrefix + "Subject"; ...  
```  
  
## <a name="create-an-association"></a>İlişkilendirme oluşturma  
  
#### <a name="to-create-an-association"></a>Bir ilişkilendirme oluşturmak için  
  
1.  İlişki kaynak sonunu içeren model veya paketin genellikle olan ilişkisini sahibini edinin.  
  
2.  Sahibi gerekli Create yöntemini çağırır.  
  
3.  İlişkinin özellikleri gibi adını ayarlayın.  
  
     Örneğin:  
  
    ```  
    IAssociation association = subject.Package.CreateAssociation(subject, observer);  
    association .Name = "Observes";  
    ```  
  
4.  İlişki her uçtaki özelliklerini ayarlayın. Her zaman iki `MemberEnds`. Örneğin:  
  
    ```  
    association .MemberEnds[0].Name = "subject";   // role name  
    association .MemberEnds[1].Name = "observers"; // role name  
    association .MemberEnds[1].SetBounds("0..*");           
                // multiplicity defaults to "1"  
    association.MemberEnds[0].Aggregation = AggregationKind.Composite;  
    ```  
  
## <a name="create-a-generalization"></a>Genelleştirme oluşturma  
  
```  
IGeneralization generalization =   
  subclass.CreateGeneralization(superClass);  
```  
  
## <a name="delete-an-element-relationship-or-generalization-from-the-model"></a>Bir öğe, ilişki veya Genelleştirme modelden Sil  
  
```  
anElement.Delete();  
```  
  
 Bir öğenin bir modelden sildiğinizde:  
  
-   Bağlantı her ilişki de silinir.  
  
-   Bir diyagramda temsil edilen her şekil de silinir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML modellerini ve diyagramları genişletme](../modeling/extend-uml-models-and-diagrams.md)   
 [Diyagramlar üzerinde model görüntüleme](../modeling/display-a-uml-model-on-diagrams.md)



