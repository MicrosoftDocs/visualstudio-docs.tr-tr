---
title: Proje Modelleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 37b237a462900735ea641407d10719d43334262e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808420"
---
# <a name="project-modeling"></a>Proje Modelleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Projenizi standart proje nesnelerini uygulamak için Otomasyon sağlama sonraki adım: <xref:EnvDTE.Projects> ve `ProjectItems` koleksiyonları; `Project` ve <xref:EnvDTE.ProjectItem> nesneler; ve uygulamanız için benzersiz kalan nesneler. Bu standart nesneleri Dteinternal.h dosyasında tanımlanır. Standart nesneleri uygulaması BscPrj örnekte sağlanır. Bu sınıfların modelleri olarak yan yana bekleme kendi standart proje nesneleri oluşturmak için kullanabileceğiniz diğer proje türleri proje nesneleri ile.  
  
 Çağrı yapabilmeniz için bir Otomasyon tüketici varsayar <xref:EnvDTE.Solution>("`<UniqueProjName>")` ve <xref:EnvDTE.ProjectItems> (`n`) burada n, çözümdeki belirli bir projeyi almak için bir dizin numarası. Bu Otomasyon çağrıyı yapan neden çağırmak ortamı <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> VSITEMID_ROOT VSHPROPID_ExtObject VSHPROPID parametre olarak ve öğe kimliği parametresi olarak geçirerek uygun proje hiyerarşisindeki. `IVsHierarchy::GetProperty` döndürür bir `IDispatch` sağlayan çekirdek Otomasyon nesne işaretçisi `Project` uyguladıysanız arabirimi.  
  
 Söz dizimi aşağıdaki gibidir `IVsHierarchy::GetProperty`.  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT``*pvar`  
  
 `);`  
  
 Projeleri iç içe yerleştirmek ve proje öğesi grupları oluşturmak için koleksiyonları kullanın. Hiyerarşi şöyle görünür.  
  
```  
Projects  
  |– Project  
      |– ProjectItems (a collection of ProjectItem)  
          |– ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 İç içe geçme anlamına gelir bir <xref:EnvDTE.ProjectItem> nesnesi olabilir <xref:EnvDTE.ProjectItems> aynı zamanda koleksiyon için bir `ProjectItems` koleksiyon iç içe geçmiş nesneleri içerebilir. Temel Proje örneği, bu iç içe geçme göstermemiz gerekmez. Uygulayarak `Project` nesne genel otomasyon modeli tasarımını belirtir gibi ağaç yapısında katılın.  
  
 Proje Otomasyon, aşağıdaki diyagramda yolu izler.  
  
 ![Visual Studio Proje nesnelerini](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
Proje Otomasyon  
  
 Uygulamaz, bir `Project` nesnesi ortam hala genel dönüş `Project` yalnızca proje adını içeren nesne.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>

