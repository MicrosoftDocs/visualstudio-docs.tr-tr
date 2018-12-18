---
title: 'Nasıl yapılır: Düzenleyici dosya türlerini kaydetme | Microsoft Docs'
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 326b29574d8ff2562196652cdcde9865aee24c0e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896932"
---
# <a name="how-to-register-editor-file-types"></a>Nasıl yapılır: Düzenleyici dosya türlerini kaydetme
Bir parçası olarak sağlanan kayıt öznitelikleri kullanarak dosya türleri Düzenleyicisi kaydetmek için en kolay yolu olan [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] yönetilen paket framework (MPF) sınıfları. Yerel paketinizi uyguluyorsanız [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], düzenleyici ve ilişkili uzantıları kaydeden bir kayıt defteri betik da yazabilirsiniz.

## <a name="registration-using-mpf-classes"></a>Kayıt MPF sınıflarını kullanma

### <a name="to-register-editor-file-types-using-mpf-classes"></a>Düzenleyici dosya türleri MPF sınıflarını kullanarak kaydetmek için

1. Sağlamak <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> , VSPackage sınıfına düzenleyiciniz için uygun parametrelerle sınıfın.

   ```
   [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,
        ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",
        TemplateDir = "..\\..\\Templates",
        NameResourceID = 106)]
   ```

    Burada *. Örnek* bu düzenleyici için kaydedilen uzantısı olduğundan ve "32" kendi öncelik düzeyi.

    `projectGuid` Tanımlanan, çeşitli dosya türleri için GUID'dir <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid>. Çeşitli dosya türü sağlanır, böylece sonuç dosyası derleme sürecinin bir parçası olacağı değil.

    *TemplateDir* yönetilen temel Düzenleyici örneği ile birlikte gelen şablon dosyalarını içeren klasörü temsil eder.

    `NameResourceID` tanımlanan *Resources.h* BasicEditorUI proje dosyasını ve Düzenleyici "My Düzenleyicisi" olarak tanımlar.

2. Geçersiz kılma <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> yöntemi.

    Uygulamanızda <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> yöntemi, çağrı <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> yöntemi ve örneği, düzenleyici fabrikası gösterilen aşağıda geçirin.

   ```csharp
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

3. Düzenleyici fabrikaları kaydını silin.

    VSPackage'ı çıkarıldığından, düzenleyici fabrikaları otomatik kaydı. Düzenleyici Üreteç nesnesi uyguluyorsa <xref:System.IDisposable> arabirimi, kendi `Dispose` ile Fabrika kaydını sonra yöntemi çağrıldığında [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="registration-using-a-registry-script"></a>Kayıt defteri betik kullanarak kayıt
 Yerel Düzenleyici fabrikaları ve dosya türlerini kaydetme [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] yapılır aşağıdaki gösterildiği gibi windows kayıt defterine yazmak için kayıt defteri betik kullanarak.

### <a name="to-register-editor-file-types-using-a-registry-script"></a>Editor konfigurace kaydetmek için kayıt defteri betik kullanarak türleri

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

     Bu örnekte Düzenleyicisi dosya uzantısı olarak tanımlanan *.rtf* ve onun "50" bir önceliktir. GUID dizeleri tanımlanan *Resource.h* BscEdit örnek proje dosyası.

2.  VSPackage kaydetme.

3.  Düzenleyici üreteci kaydettirir.

     Düzenleyici üreteci kaydedilmiştir <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> uygulaması.

    ```cpp
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

     GUID dizeleri tanımlanan *Resource.h* BscEdit proje dosyası.