---
title: Proje Subtypes başlatma sırası | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fe7e7a574d04ec9a49252e32e0fbb8b5685778aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131619"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Proje Subtypes başlatma sırası
Temel Proje Fabrika uygulanması çağırarak ortam bir proje oluşturur <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. Bir proje alt yapı ortamı proje dosyasının uzantısı için proje türü GUID listesi boş olmadığını belirlerken başlatır. Proje GUID ve proje dosya uzantısının proje olup olmadığını belirtin bir [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] veya [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] proje türü. Örneğin, .vbproj uzantısı ve {tanımlamak F184B08F-C81C-45F6-A57F-5ABD9991F28F} bir [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projesi.

## <a name="environments-initialization-of-project-subtypes"></a>Proje Subtypes Ortamı'nın başlatılması
 Aşağıdaki yordamı birden çok proje alt türleri tarafından toplanan proje sistemi başlatma sırası ayrıntılarını verir.

1.  Ortam temel projenin çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, ve kendi proje dosyası projeye ayrıştırır sırada birleşik proje türü GUID'ler listesi olmadığını bulur `null`. Proje doğrudan kendi projesi oluşturma sona erdirir.

2.  Proje çağrıları `QueryService` üzerinde <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> ortam uygulamasını kullanarak bir proje alt oluşturmak için hizmet <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> yöntemi. Bu yöntem içinde ortamı özyinelemeli işlev çağrıları, uygulamalarına yapar <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> proje listesi taramasını sırada yöntemleri GUID'ler en dıştaki proje alt türü ile başlayarak, yazın.

     Başlatma adımları ayrıntıları.

    1.  Ortam uyarlamasını <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> yöntem çağrılarını `HrCreateInnerProj` aşağıdaki işlev bildirimi yöntemiyle:

         <CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Ne zaman bu işlevi çağrıldığında ilk olarak, diğer bir deyişle, en dıştaki proje alt türü için parametreler `pOuter` ve `pOwner` olarak iletilen `null` ve en dıştaki proje alt işlevi ayarlar `IUnknown` için `pOuter`.

    2.  Sonraki ortamı çağırır `HrCreateInnerProj` listesindeki ikinci proje türü GUID ile işlevi. Bu GUID toplama dizisi temel projede doğru atlama ikinci iç proje alt karşılık gelir.

    3.  `pOuter` Şimdi işaret `IUnknown` en dıştaki proje alt ve `HrCreateInnerProj` uygulamanıza çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> uygulamanıza bir çağrı tarafından izlenen <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>. İçinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> geçirdiğiniz denetleme yöntemi `IUnknown` en dıştaki proje alt `pOuter`. Sahibi projeye (iç proje alt türü), toplama proje nesne oluşturması gerekir. İçinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> geçirdiğiniz gösteren bir işaretçi yöntem uygulaması `IUnknown` toplanmakta iç projesinin. Bu iki yöntem toplama nesnesi oluşturun ve başvuru sayısı kendisine bulunduran proje alt bitmez emin olmak için COM toplama kurallarına, uygulamaları gerekir.

    4.  `HrCreateInnerProj` uygulamanıza çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>. Bu yöntemde, proje alt başlatma işini yapar. Örneğin, çözüm olayları kayıt yaptırabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.

    5.  `HrCreateInnerProj` Listedeki son GUID (Temel Proje) ulaşılana kadar yinelemeli olarak adlandırılır. Her bu çağrılardan adımları, d c yinelenir. `pOuter` işaret en dıştaki proje alt `IUnknown` her düzeyi toplama için.

## <a name="example"></a>Örnek

Aşağıdaki örnek yaklaşık bir temsili programlı işleminde ayrıntıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> yöntemi olarak ortamı tarafından gerçekleştirilir. Kod yalnızca bir örnektir; derlenecek amaçlanmamıştır ve daha anlaşılır olması için tüm hata denetimi kaldırıldı.

```cpp
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

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [Proje Alt Türleri](../../extensibility/internals/project-subtypes.md)