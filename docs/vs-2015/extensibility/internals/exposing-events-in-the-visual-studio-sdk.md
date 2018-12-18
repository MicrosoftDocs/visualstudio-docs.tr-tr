---
title: Visual Studio SDK'da olayları kullanıma sunma | Microsoft Docs
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
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4c65220114328f1630ef9c9457a3c971b730957b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761494"
---
# <a name="exposing-events-in-the-visual-studio-sdk"></a>Visual Studio SDK’da Olayları Kullanıma Sunma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sağlar Otomasyon kullanarak olayları kaynağı. Projeleri ve proje öğeleri için olayları kaynağı öneririz.  
  
 Olaylar, Otomasyon tüketicilerden tarafından alınır <xref:EnvDTE.DTEClass.Events%2A> nesne veya <xref:EnvDTE.DTEClass.GetObject%2A> ("EventObjectName"). Ortam çağrıları `IDispatch::Invoke` kullanarak `DISPATCH_METHOD` veya `DISPATCH_PROPERTYGET` olaya döndürülecek bayrakları.  
  
 VSPackage özgü olaylar nasıl döndürülür aşağıdaki işlem açıklanmaktadır.  
  
1. Ortamı başlatır.  
  
2. Tüm değer adları tüm VSPackage'ları otomatikleştirme ve AutomationEvents AutomationProperties anahtarları altındaki kayıt defterinden okur ve bu adlardan bir tabloya kaydeder.  
  
3. Bu örnekte, bir Otomasyon tüketicisi, çağıran `DTE.Events.AutomationProjectsEvents` veya `DTE.Events.AutomationProjectItemsEvents`.  
  
4. Ortam dize parametresi tabloda bulur ve karşılık gelen VSPackage'ı yükler.  
  
5. Ortam çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> adını kullanarak yöntemi çağrısında; Bu örnekte, AutomationProjectsEvents veya AutomationProjectItemsEvents geçirildi.  
  
6. VSPackage'ı yöntemleri gibi bir kök nesnesi oluşturur `get_AutomationProjectsEvents` ve `get_AutomationProjectItemEvents` ve IDispatch işaretçinin nesneyi döndürür.  
  
7. Ortam Otomasyon çağrısına geçirilen adı esas alarak uygun yöntemini çağırır.  
  
8. `get_` Yöntemi oluşturur hem de uygulayan başka bir olay IDispatch tabanlı nesne `IConnectionPointContainer` arabirimi ve `IConnectionPoint` arabirim ve nesnenin bir IDispatchpointer döndürür.  
  
   Otomasyon kullanarak bir olay kullanıma sunmak için yanıt gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> ve kayıt defterine ekleyin dizelerin izleyin. Temel Proje Bu örnekte "BscProjectsEvents" ve "BscProjectItemsEvents" dizelerdir.  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>Temel Proje örnekteki kayıt defteri girdileri  
 Bu bölümde, kayıt defterine Otomasyon olay değerleri ekleyebileceğimi gösterilir.  
  
 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\< PkgGUID\>\AutomationEvents]  
  
 "AutomationProjectEvents nesneyi döndürür AutomationProjectEvents"=""  
  
 "AutomationProjectItemsEvents nesneyi döndürür AutomationProjectItemEvents"=""  
  
|Ad|Tür|Aralık|Açıklama|  
|----------|----------|-----------|-----------------|  
|Varsayılan (@)|REG_SZ|Kullanılmıyor|Kullanılmayan. Veri alanı belgeleri için kullanabilirsiniz.|  
|AutomationProjectsEvents|REG_SZ|Olay nesnesinin adı.|Anahtar adı yalnızca büyük/küçük harf geçerlidir. Veri alanı belgeleri için kullanabilirsiniz.<br /><br /> Bu örnek, temel proje örnekten gelir.|  
|AutomationProjectItemEvents|REG_SZ|Olay nesne adı|Anahtar adı yalnızca büyük/küçük harf geçerlidir. Veri alanı belgeleri için kullanabilirsiniz.<br /><br /> Bu örnek, temel proje örnekten gelir.|  
  
 Olay nesnelerinin herhangi bir Otomasyon tüketici tarafından istendiğinde, yöntemleri, VSPackage'ı destekleyen herhangi bir olay için bir kök nesnesi oluşturun. Ortam uygun çağırır `get_` bu nesne üzerindeki yöntemi. Örneğin, varsa `DTE.Events.AutomationProjectsEvents` çağrıldığında `get_AutomationProjectsEvents` kök nesnesi üzerinde yöntemi çağrılır.  
  
 ![Visual Studio Proje etkinliklerinin](../../extensibility/internals/media/projectevents.gif "ProjectEvents")  
Olaylar için otomasyon modeli  
  
 Sınıf `CProjectEventsContainer` BscProjectsEvents için kaynak nesneyi temsil ederken `CProjectItemsEventsContainer` BscProjectItemsEvents için kaynak nesneyi temsil eder.  
  
 Çoğu durumda, çünkü çoğu olay nesneleri filtre nesnesi her olay istek için yeni bir nesne döndürmesi gerekir. Olay tetiklendiğinde olay işleyicisi çağrılışıysa doğrulamak için bu filtreyi denetleyin.  
  
 AutomationEvents.h ve AutomationEvents.cpp bildirimleri ve sınıfları aşağıdaki tabloda uygulamaları içerir.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|`CAutomationEvents`|Alınan olay kök nesnesi uygulayan `DTE.Events` nesne.|  
|`CProjectsEventsContainer` ve `CProjectItemsEventsContainer`|Karşılık gelen olayları tetiklemesine olay kaynağı nesnelerini uygulayın.|  
  
 Aşağıdaki kod örneği, bir olay nesne için bir isteğe yanıt gösterilmektedir.  
  
```cpp#  
STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
{  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)   
        //Is the requested name our Projects object?  
    {  
        return GetAutomationProjects(ppIDispatch);  
        // Gets our Projects object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        //Is the requested name our ProjectsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectEvents object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectItemsEvents object.  
    }  
    return E_INVALIDARG;  
}  
```  
  
 Yukarıdaki kodda `g_wszAutomationProjects` projesi koleksiyonunuzun ("FigProjects") adı `g_wszAutomationProjectsEvents` ("FigProjectsEvents") ve `g_wszAutomationProjectItemsEvents` ("FigProjectItemEvents") olan proje etkinliklerinin adları ve proje öğelerini kaynağı olayları, VSPackage uygulaması.  
  
 Olay nesneleri aynı merkezi konumundan alınan `DTE.Events` nesne. Böylece son kullanıcı, belirli bir olay bulmak için tüm nesne modelini Gözat gerekmez. Bu şekilde tüm olay nesneleri birlikte gruplandırılır. Bu ayrıca, sistem genelinde olayları için kendi kodunuzu uygulamak yerine, belirli VSPackage nesneleri sağlamanıza olanak tanır. Ancak, son kullanıcının, kimin gerekir bulma için bir olay, `ProjectItem` arabirimi, bu olay nesnesi nerede alınır hemen NET olmadığı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
 [VSSDK örnekleri](../../misc/vssdk-samples.md)

