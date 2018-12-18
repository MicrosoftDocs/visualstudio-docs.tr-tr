---
title: 'Nasıl yapılır: şablonda parametreleri ikame etme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- template parameters, substituting
- Visual Studio templates, using parameters
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bab1d1fd7cd08813dadefbcbec27dbd84bd7b66b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279753"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Nasıl Yapılır: Şablonda Parametreleri İkame Etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sınıf adları gibi şablon parametreleri değiştirebilir ve ad alanları bir şablonu temel alan bir dosya oluşturulur. Şablon parametreleri tam bir listesi için bkz. [şablon parametreleri](../ide/template-parameters.md).  
  
## <a name="procedure"></a>Yordam  
 O şablonu temel alan bir proje oluşturulduğunda bir şablon dosyalarını parametrelerinde yerini alabilir. Bu yordam şablonu içeren yeni bir proje oluşturulduğunda, bir ad ile güvenli bir proje adı yerini alan bir şablonun nasıl oluşturulacağını açıklar.  
  
#### <a name="to-use-a-parameter-to-replace-namespace-name-with-the-project-name"></a>Ad alanı adı proje adı ile değiştirin. bir parametre kullanılacak  
  
1.  Bir veya daha fazla kod dosyaları şablonda parametre ekleyin. Örneğin:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    >  Şablon parametreleri biçimi $ yazılır*parametre*$.  
  
2.  Şablonu için .vstemplate dosyasında bulun `ProjectItem` bu dosyayı içeren öğe.  
  
3.  Ayarlama `ReplaceParameters` özniteliğini `true` için `ProjectItem` öğesi. Örneğin:  
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)   
 [Şablon parametreleri](../ide/template-parameters.md)   
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [ProjectItem Öğesi (Visual Studio Öğe Şablonları)](../extensibility/projectitem-element-visual-studio-item-templates.md)



