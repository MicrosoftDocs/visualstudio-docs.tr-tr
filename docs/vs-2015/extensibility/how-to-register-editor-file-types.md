---
title: 'Nasıl yapılır: Düzenleyici dosya türlerini kaydetme | Microsoft Docs'
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
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 39b1cde8dec71df9cb85bf737c23c883fbdcd615
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777272"
---
# <a name="how-to-register-editor-file-types"></a>Nasıl yapılır: Düzenleyici dosya türlerini kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir parçası olarak sağlanan kayıt öznitelikleri kullanarak dosya türleri Düzenleyicisi kaydetmek için en kolay yolu olan [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] yönetilen paket framework (MPF) sınıfları. Yerel paketinizi uyguluyorsanız [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], düzenleyici ve ilişkili uzantıları kaydeden bir kayıt defteri betik da yazabilirsiniz.  
  
## <a name="registration-using-mpf-classes"></a>Kayıt MPF sınıflarını kullanma  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>Düzenleyici dosya türleri MPF sınıflarını kullanarak kaydetmek için  
  
1.  Sağlamak <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> , VSPackage sınıfına düzenleyiciniz için uygun parametrelerle sınıfın.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Burada ". Bu düzenleyici için kaydedilen uzantısı SAMPLE"ve"32"öncelik düzeyini ise.  
  
     `projectGuid` Tanımlanan, çeşitli dosya türleri için GUID'dir <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid>. Çeşitli dosya türü sağlanır, böylece sonuç dosyası derleme sürecinin bir parçası olacağı değil.  
  
     `TemplateDir` Yönetilen temel Düzenleyici örneği ile birlikte gelen şablon dosyalarını içeren klasörü temsil eder.  
  
     `NameResourceID` BasicEditorUI proje Resources.h dosyasında tanımlanır ve Düzenleyici "My Düzenleyicisi" olarak tanımlar.  
  
2.  Geçersiz kılma <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> yöntemi.  
  
     Uygulamanızda <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> yöntemi, çağrı <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> yöntemi ve örneği, düzenleyici fabrikası gösterilen aşağıda geçirin.  
  
    ```  
    protected override void Initialize()  
    {  
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,   
        "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
           //Create Editor Factory  
        editorFactory = new EditorFactory(this);  
        base.RegisterEditorFactory(editorFactory);  
    }  
    ```  
  
     Bu adım, düzenleyici fabrikası hem Düzenleyici dosya uzantıları kaydeder.  
  
3.  Düzenleyici fabrikaları kaydını silin.  
  
     VSPackage'ı çıkarıldığından, düzenleyici fabrikaları otomatik kaydı. Düzenleyici Üreteç nesnesi uyguluyorsa <xref:System.IDisposable> arabirimi, kendi `Dispose` ile Fabrika kaydını sonra yöntemi çağrıldığında [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="registration-using-a-registry-script"></a>Kayıt defteri betik kullanarak kayıt  
 Yerel Düzenleyici fabrikaları ve dosya türlerini kaydetme [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] yapılır aşağıdaki gösterildiği gibi windows kayıt defterine yazmak için kayıt defteri betik kullanarak.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>Editor konfigurace kaydetmek için kayıt defteri betik kullanarak türleri  
  
1.  Kayıt defteri betiğinizde Düzenleyici üreteci ve GUID dize Düzenleyici fabrikası gösterildiği gibi tanımlayın `GUID_BscEditorFactory` aşağıdaki kayıt defteri betik bölümü. Ayrıca, uzantı ve düzenleyici uzantısı önceliğini tanımlayın:  
  
    ```  
  
          NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions            {                val rtf = d 50            }  
        }  
    }  
    ```  
  
     Bu örnekte Düzenleyicisi dosya uzantısı ".rtf" tanımlanır ve önceliği "50" olur. GUID dizeleri BscEdit kodunuzla Resource.h dosyasında tanımlanır.  
  
2.  VSPackage kaydetme.  
  
3.  Düzenleyici üreteci kaydettirir.  
  
     Düzenleyici üreteci kaydedilmiştir <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> uygulaması.  
  
    ```  
    // create editor factory.  
    if (m_srpEdFact == NULL)   
    {  
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;  
        if (NULL == pEdFact)  
          return E_OUTOFMEMORY;  
  
        if (!pEdFact->FInit(this))  
          return E_UNEXPECTED;  
  
        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()  
    }  
    // Query service for IVsRegisterEditors, register the editor factory  
    CComPtr<IVsRegisterEditors> srpRegEd;  
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))  
      {  
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));  
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,  
                      m_srpEdFact, &m_dwEditorCookie)))   
          {  
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));  
            return E_FAIL;  
          }  
      }  
        return S_OK;  
    }  
    ```  
  
     GUID dizeleri BscEdit proje Resource.h dosyasında tanımlanır.

