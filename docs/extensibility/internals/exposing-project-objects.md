---
title: Proje nesnelerini kullanıma sunma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae7b34df55593f07adeaffe8d654b59629baaae5
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510916"
---
# <a name="expose-project-objects"></a>Proje nesnelerini kullanıma sunma

Özel proje türleri Otomasyon arabirimlerini kullanarak proje erişmesine izin vermek için Otomasyon nesneleri sağlar. Her proje türü standart sağlaması beklenir <xref:EnvDTE.Project> erişilen Otomasyon nesnesi <xref:EnvDTE.Solution>, IDE'de açık olan tüm projelerin bir koleksiyonunu içerir. Her proje öğesi tarafından kullanıma sunulan beklenen bir <xref:EnvDTE.ProjectItem> erişilen nesne `Project.ProjectItems`. Bu standart Otomasyon nesnelerin yanı sıra, projeye özgü Otomasyon nesneleri sunmak projeleri seçebilirsiniz.

Geç DTE nesnesini kullanarak kök bağlama erişebileceğiniz özel kök düzeyinde Otomasyon nesneleri oluşturabileceğiniz `DTE.<customObjectName>` veya `DTE.GetObject("<customObjectName>")`. Örneğin, Visual C++ adında bir C++ projeye özgü proje koleksiyonu oluşturur *VCProjects* kullanarak erişebileceğiniz `DTE.VCProjects` veya `DTE.GetObject("VCProjects")`. Ayrıca oluşturabilirsiniz bir `Project.Object`, proje türü için benzersiz olan bir `Project.CodeModel`, sorgulanabilen, en türetilmiş nesne için ve bir `ProjectItem`, kullanıma sunan `ProjectItem.Object` ve `ProjectItem.FileCodeModel`.

Proje, projeye özgü özel proje koleksiyonu kullanıma sunmak için ortak bir kuraldır. Örneğin, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] kullanarak daha sonra erişebileceğiniz bir C++ belirli proje koleksiyonu oluşturur `DTE.VCProjects` veya `DTE.GetObject("VCProjects")`. Ayrıca oluşturabilirsiniz bir `Project.Object`, proje türü için benzersiz olan bir `Project.CodeModel`, hangi sorgulanabilen, en türetilmiş nesne için bir `ProjectItem`, kullanıma sunan `ProjectItem.Object`ve `ProjectItem.FileCodeModel`.  
  
## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>VSPackage özgü bir nesne için bir proje katkıda bulunma  
  
1.  Eklemek için uygun anahtarlara *.pkgdef* , VSPackage dosya.  
  
     Örneğin, işte *.pkgdef* C++ dil projesi ayarları:  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2.  Koda uygulanması <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> yöntemi, aşağıdaki örnekte olduğu gibi.  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
    {  
    ExpectedPtrRet(pszPropName);  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
        if (m_fZombie)  
            return E_UNEXPECTED;  
  
        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)  
        {  
            return GetAutomationProjects(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        return E_INVALIDARG;  
    }   
    ```  
  
     Kodda, `g_wszAutomationProjects` projesi koleksiyonunuzun adı. `GetAutomationProjects` Yöntemini uygulayan bir nesne oluşturur `Projects` arabirimi ve döndürür bir `IDispatch` aşağıdaki kod örneğinde gösterildiği gibi çağrı nesnesi işaretçisi.  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)  
    {  
        ExpectedPtrRet(ppIDispatch);  
        *ppIDispatch = NULL;  
  
        if (!m_srpAutomationProjects)  
        {  
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);  
            IfFailRet(hr);  
            ExpectedExprRet(m_srpAutomationProjects != NULL);  
        }  
        return m_srpAutomationProjects.CopyTo(ppIDispatch);  
    }  
    ```  
  
     Otomasyon nesneniz için benzersiz bir ad seçin. Ad çakışmaları tahmin edilemez ve birden fazla proje türü adın aynısını kullanırsanız, rasgele oluşturulabilecek çakışan bir nesne adı Çarpışmaları neden. Şirket adınızı veya benzersiz bir unsurunu Otomasyon nesne adını, ürün adı içermesi gerekir.  
  
     Özel `Projects` koleksiyon nesnesi, proje otomasyon modeli kalan kısmı için bir kolaylık giriş noktasıdır. Proje nesnenizin de erişilebilir <xref:EnvDTE.Solution> proje koleksiyonu. Tüketicileriyle sağlayan ilgili kod ve kayıt defteri girdileri oluşturduktan sonra `Projects` koleksiyon nesnelerini, uygulamanız, standart nesneleri proje modeli için kalan sağlamalıdır. Daha fazla bilgi için [proje modelleme](../../extensibility/internals/project-modeling.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
