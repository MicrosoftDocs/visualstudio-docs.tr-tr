---
title: Proje alt türlerinin başlatılma sırası başlatma | Microsoft Docs
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
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 53c0a474a5a5caf887599bc50e623bd25e7be782
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51746517"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Proje Alt Türlerinin Başlatılma Sırası
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ortam, temel proje fabrikası uygulamasını çağırarak bir proje oluşturur <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. Bir proje alt yapı ortamı için bir proje dosyasının uzantısı proje türü GUID listesi boş olmadığını belirlerken başlatır. GUID proje ve proje dosya uzantısıyla proje olup olmadığını belirtin. bir [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../includes/csprcs-md.md)] proje türü. Örneğin, .vbproj uzantısı ve {tanımlamak F184B08F-C81C-45F6-A57F-5ABD9991F28F} bir [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] proje.  
  
## <a name="environments-initialization-of-project-subtypes"></a>Proje alt türlerinin başlatılma ortamın başlatma  
 Aşağıdaki yordam başlatma sırası için bir proje sistemi birden çok proje alt türleri tarafından toplanan ayrıntılı olarak açıklanmaktadır.  
  
1. Temel projenin ortam çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, ve proje, proje dosyası Ayrıştırma sırasında toplama proje türü GUID listesi olmadığını bulur `null`. Proje, doğrudan kendi proje oluşturma sona erdirir.  
  
2. Proje çağrıları `QueryService` üzerinde <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> ortamın uygulamasını kullanarak bir proje alt türü oluşturmak için hizmet <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> yöntemi. Bu yöntem içinde ortamı özyinelemeli işlev çağrıları, uygulamalarına hale <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, `M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)` ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> GUID'leri, en dıştaki proje alt türü ile başlayarak, proje listesi walking sırasında yöntemlerin yazın.  
  
    Başlatma adımları açıklanmaktadır.  
  
   1.  Ortamın uygulaması <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> yöntem çağrıları ' HrCreateInnerProj'' ' aşağıdaki işlev bildirimi ile yöntemi:  
  
       ```  
       HRESULT HrCreateInnerProj  
       (  
           WCHAR *pwszGuids,  
           IUnknown *pOuter,  
           IVsAggregatableProject *pOwner,  
           LPCOLESTR pszFilename,  
           LPCOLESTR pszLocation,  
           LPCOLESTR pszName,  
           VSCREATEPROJFLAGS grfCreateFlags,  
           IUnknown **ppInner,  
           BOOL *pfCancelled  
       )  
       ```  
  
        Ne zaman bu işlev çağrılır ilk kez, diğer bir deyişle, en dıştaki proje alt türü için parametreler `pOuter` ve `pOwner` olarak geçirilir `null` ve işlevin en dıştaki proje alt ayarlar `IUnknown` için `pOuter`.  
  
   2.  Sonraki ortam çağırır `HrCreateInnerProj` listede ikinci proje türü GUID ile işlevi. Bu GUID, temel proje toplama dizideki doğru Adımlama ikinci iç proje alt karşılık gelir.  
  
   3.  `pOuter` Artık işaret `IUnknown` , en dıştaki proje alt türü ve `HrCreateInnerProj` uygulamanıza çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> uygulamanız için bir çağrı tarafından izlenen <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>. İçinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> geçirdiğiniz denetleme yöntemi `IUnknown` , en dıştaki proje alt `pOuter`. Sahip olunan proje (iç proje alt türü), toplama proje nesne oluşturmak gerekir. İçinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> geçirdiğiniz bir işaretçiye yöntem uygulaması `IUnknown` toplanmakta olan iç projenin. Bu iki yöntem toplama nesnesi oluşturun ve proje alt türü bir başvuru sayısı kendisine tutarak bitmiyor emin olmak için COM toplama kurallarını izleyin, uygulamaları gerekir.  
  
   4.  `HrCreateInnerProj` Uygulamanız, çağıran <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>. Bu yöntemi başlatma işini proje alt türü yapar. Örneğin, çözüm olayları kaydedebilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.  
  
   5.  `HrCreateInnerProj` Son GUID (Temel Proje) listesinde tarihe kadar yinelemeli olarak adlandırılır. Her biri bu çağrılar için adımları, c d yinelenir. `pOuter` en dıştaki proje alt türü için işaret `IUnknown` her düzeyi bir toplama.  
  
   Aşağıdaki örnekte, yaklaşık bir temsilini programlı işlemde ayrıntıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> yöntemi olarak, ortamı tarafından gerçekleştirilir. Kodu yalnızca örnek olarak verilmiştir; derlenecek tasarlanmamıştır ve açıklık için tüm hata denetimi kaldırıldı.  
  
## <a name="example"></a>Örnek  
  
### <a name="code"></a>Kod  
  
```  
HRESULT CreateAggregateProject  
(  
    LPCOLESTR lpstrGuids,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    REFIID iidProject,   
    void **ppvProject)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpunkProj;  
    CComPtr<IVsAggregatableProject> srpAggProject;  
    CComBSTR bstrGuids = lpstrGuids;  
    BOOL fCanceled = FALSE;  
    *ppvProject = NULL;  
  
    HrCreateInnerProj(  
         bstrGuids, NULL, NULL, pszFilename, pszLocation,   
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);  
    srpunkProj->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggProject));  
    srpAggProject->OnAggregationComplete();  
    srpunkProj->QueryInterface(iidProject, ppvProject);  
}  
  
HRESULT HrCreateInnerProj  
(  
    WCHAR *pwszGuids,   
    IUnknown *pOuter,   
    IVsAggregatableProject *pOwner,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    IUnknown **ppInner,   
    BOOL *pfCanceled  
)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpInner;  
    CComPtr<IVsAggregatableProject> srpAggInner;  
    CComPtr<IVsProjectFactory> srpProjectFactory;  
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;  
    GUID guid = GUID_NULL;  
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');  
    WCHAR wszText[_MAX_PATH+150] = L"";  
  
    if (pwszNextGuids)  
    {  
        *pwszNextGuids++ = 0;  
    }  
  
    CLSIDFromString(pwszGuids, &guid);  
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(  
        guid, &srpProjectFactory);  
    srpProjectFactory->QueryInterface(  
        IID_IVsAggregatableProjectFactory,   
        (void **)&srpAggPF);  
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);  
    srpInner->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggInner);  
  
    if (pOwner)  
    {  
        IfFailGo(pOwner->SetInnerProject(srpInner));  
    }  
  
    if (pwszNextGuids)  
    {  
        CComPtr<IUnknown> srpNextInner;  
        HrCreateInnerProj(  
            pwszNextGuids, pOuter ? pOuter : srpInner,   
            srpAggInner, pszFilename, pszLocation, pszName,   
            grfCreateFlags, &srpNextInner, pfCanceled);  
    }  
  
    return srpAggInner->InitializeForOuter(  
        pszFilename, pszLocation, pszName, grfCreateFlags,   
        IID_IUnknown, (void **)ppInner, pfCanceled);  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [Proje Alt Türleri](../../extensibility/internals/project-subtypes.md)

