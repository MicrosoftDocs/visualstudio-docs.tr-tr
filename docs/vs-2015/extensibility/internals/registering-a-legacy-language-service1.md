---
title: Bir eski dil hizmeti kaydetme1 | Microsoft Docs
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
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e473df78787b83655c402bae666448e718216b36
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769591"
---
# <a name="registering-a-legacy-language-service"></a>Eski dil hizmeti kaydediliyor
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Yönetilen paket çerçevesini (MPF), dil hizmeti tarafından bir VSPackage proffered (bkz [VSPackages](../../extensibility/internals/vspackages.md)) ve kayıtlı [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kayıt defteri anahtarları ve girişleri ekleyerek. Bu kayıt işlemi kısmen yükleme sırasında ve kısmen çalışma zamanı içinde yapılır.  
  
## <a name="register-the-language-service-by-using-attributes"></a>Dil hizmeti öznitelikleri kullanarak kaydetme  
 Aşağıdaki öznitelikler, bir dil hizmeti kaydetmek için kullanılır.  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>  
  
  Bu öznitelikler aşağıda açıklanmıştır  
  
### <a name="provideserviceattribute"></a>ProvideServiceAttribute  
 Bu öznitelik, bir dil hizmeti hizmet olarak kaydeder.  
  
### <a name="example"></a>Örnek  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideServiceAttribute(typeof(TestLanguageService),  
                             ServiceName = "Test Language Service")]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageserviceattribute"></a>ProvideLanguageServiceAttribute  
 Bu öznitelik, bir dil hizmeti özel bir dil hizmeti kaydeder. Dil hizmetinize sunan özellikleri belirten seçenekleri ayarlamanıza olanak sağlar. Bu örnek, bir dil hizmeti sağlayan seçenekler kümesini gösterir. Dil hizmeti seçenekleri tam kümesi için bkz: <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>.  
  
### <a name="example"></a>Örnek  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageServiceAttribute(typeof(TestLanguageService),  
                             "Test Language",  
                             106,             // resource ID of localized language name  
                             CodeSense = true,             // Supports IntelliSense  
                             RequestStockColors = false,   // Supplies custom colors  
                             EnableCommenting = true,      // Supports commenting out code  
                             EnableAsyncCompletion = true  // Supports background parsing  
                             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageextensionattribute"></a>ProvideLanguageExtensionAttribute  
 Bu öznitelik, bir dosya uzantısına sahip, dil hizmeti ilişkilendirir. Uzantıya sahip bir dosya yüklendiğinde bir proje, dil hizmetinin başlatıldığından ve dosyanın içeriğini görüntülemek için kullanılır.  
  
### <a name="example"></a>Örnek  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageExtensionAttribute(typeof(TestLanguageService),  
                                       ".Testext")]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguagecodeexpansionattribute"></a>ProvideLanguageCodeExpansionAttribute  
 Bu öznitelik, hangi koddan genişletme veya parçacık şablonu elde edilen bir konuma kaydeder. Bu bilgileri tarafından kullanılan **kod parçacıkları tarayıcı** ve bir kod parçacığı kaynak dosyaya eklendiğinde, düzenleyici.  
  
### <a name="example"></a>Örnek  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageCodeExpansionAttribute(  
             typeof(TestLanguageService),  
             "Test Language", // Name of language used as registry key.  
             106,           // Resource ID of localized name of language service.  
             "testlanguage",  // language key used in snippet templates.  
             @"%InstallRoot%\Test Language\SnippetsIndex.xml",  // Path to snippets index  
             SearchPaths = @"%InstallRoot%\Test Language\Snippets\%LCID%\Snippets\;" +  
                           @"%TestDocs%\Code Snippets\Test Language\Test Code Snippets"  
             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageeditoroptionpageattribute"></a>ProvideLanguageEditorOptionPageAttribute  
 Bu öznitelik, görüntülenecek özellik sayfası kaydeder **seçenekleri** iletişim kutusunun altında **metin düzenleyici** kategorisi. Dil hizmetiniz için görüntülenecek her sayfa için özniteliklerden birini kullanın. Sayfalarınızı bir ağaç yapısı içinde düzenlemek istiyorsanız, her bir ağaç düğümünü tanımlamak için ek öznitelikler kullanın.  
  
### <a name="example"></a>Örnek  
 Bu örnek, iki özellik sayfalarını gösterir. **seçenekleri** ve **Indenting**ve ikinci özellik sayfasını içeren bir düğüm.  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             "Options",      // Registry key name for property page  
             "#242",         // Localized name of property page  
             OptionPageGuid = "{A2FE74E1-FFFF-3311-4342-123052450768}"  // GUID of property page  
             )]  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             "Advanced",     // Registry key name for node  
             "#243",         // Localized name of node  
             )]  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             @"Advanced\Indenting",     // Registry key name for property page  
             "#244",         // Localized name of property page  
             OptionPageGuid = "{A2FE74E2-FFFF-3311-4342-123052450768}"  // GUID of property page  
             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
## <a name="proffer-the-language-service-at-runtime"></a>Dil hizmeti zamanında proffer  
 Dil paketinizi yüklendiğinde söylemelisiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dil hizmetiniz hazır hale gelir. Bunun için hizmet proffering tarafından. Bu yapılır <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> yöntemi. Ayrıca, arka plan ayrıştırmayı gerçekleştirilebilir, boş dönemlerde dil hizmetinizi çağırır zamanlayıcıyı başlatmak gerekir. Boşta Bu zamanlayıcı da aracılığıyla uyguladıysanız belge özelliklerini güncelleştirmek için kullanılan <xref:Microsoft.VisualStudio.Package.DocumentProperties> sınıfı. Bir zamanlayıcı desteklemek için paketinizi uygulamalıdır <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> arabirimi (yalnızca <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> yöntemi tam olarak uygulanması gerekiyor; kalan yöntemler, varsayılan değerleri döndürebilir).  
  
### <a name="example"></a>Örnek  
 Bu örnekte, bir hizmet proffering ve boş bir zamanlayıcı sağlama tipik bir yaklaşım gösterilmektedir.  
  
```csharp  
  
using System;  
using System.Runtime.InteropServices;  
using System.ComponentModel.Design;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.OLE.Interop;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    [Microsoft.VisualStudio.Shell.ProvideService(typeof(TestLanguageService))]  
    [Microsoft.VisualStudio.Shell.ProvideLanguageExtension(typeof(TestLanguageService), ".testext")]  
    [Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(TestLanguageService), "Test Language", 0,  
        AutoOutlining = true,  
        EnableCommenting = true,  
        MatchBraces = true,  
        ShowMatchingBrace = true)]  
    [Guid("00000000-0000-0000-0000-00000000000")] //provide a unique GUID for the package  
  
    public class TestLanguagePackage : Package, IOleComponent  
    {  
        private uint m_componentID;  
  
        protected override void Initialize()  
        {  
            base.Initialize();  // required  
  
            // Proffer the service.  
            IServiceContainer serviceContainer = this as IServiceContainer;  
            TestLanguageService langService      = new TestLanguageService();  
            langService.SetSite(this);  
            serviceContainer.AddService(typeof(TestLanguageService),  
                                        langService,  
                                        true);  
  
            // Register a timer to call our language service during  
            // idle periods.  
            IOleComponentManager mgr = GetService(typeof(SOleComponentManager))  
                                       as IOleComponentManager;  
            if (m_componentID == 0 && mgr != null)  
            {  
                OLECRINFO[] crinfo = new OLECRINFO[1];  
                crinfo[0].cbSize            = (uint)Marshal.SizeOf(typeof(OLECRINFO));  
                crinfo[0].grfcrf            = (uint)_OLECRF.olecrfNeedIdleTime |  
                                              (uint)_OLECRF.olecrfNeedPeriodicIdleTime;  
                crinfo[0].grfcadvf          = (uint)_OLECADVF.olecadvfModal     |  
                                              (uint)_OLECADVF.olecadvfRedrawOff |  
                                              (uint)_OLECADVF.olecadvfWarningsOff;  
                crinfo[0].uIdleTimeInterval = 1000;  
                int hr = mgr.FRegisterComponent(this, crinfo, out m_componentID);  
            }  
        }  
  
        protected override void Dispose(bool disposing)  
        {  
            if (m_componentID != 0)  
            {  
                IOleComponentManager mgr = GetService(typeof(SOleComponentManager))  
                                           as IOleComponentManager;  
                if (mgr != null)  
                {  
                    int hr = mgr.FRevokeComponent(m_componentID);  
                }  
                m_componentID = 0;  
            }  
  
            base.Dispose(disposing);  
        }  
  
        #region IOleComponent Members  
  
        public int FDoIdle(uint grfidlef)  
        {  
            bool bPeriodic = (grfidlef & (uint)_OLEIDLEF.oleidlefPeriodic) != 0;  
            // Use typeof(TestLanguageService) because we need to  
            // reference the GUID for our language service.  
            LanguageService service = GetService(typeof(TestLanguageService))  
                                      as LanguageService;  
            if (service != null)  
            {  
                service.OnIdle(bPeriodic);  
            }  
            return 0;  
        }  
  
        public int FContinueMessageLoop(uint uReason,  
                                        IntPtr pvLoopData,  
                                        MSG[] pMsgPeeked)  
        {  
            return 1;  
        }  
  
        public int FPreTranslateMessage(MSG[] pMsg)  
        {  
            return 0;  
        }  
  
        public int FQueryTerminate(int fPromptUser)  
        {  
            return 1;  
        }  
  
        public int FReserved1(uint dwReserved,  
                              uint message,  
                              IntPtr wParam,  
                              IntPtr lParam)  
        {  
            return 1;  
        }  
  
        public IntPtr HwndGetWindow(uint dwWhich, uint dwReserved)  
        {  
            return IntPtr.Zero;  
        }  
  
        public void OnActivationChange(IOleComponent pic,  
                                       int fSameComponent,  
                                       OLECRINFO[] pcrinfo,  
                                       int fHostIsActivating,  
                                       OLECHOSTINFO[] pchostinfo,  
                                       uint dwReserved)  
        {  
        }  
  
        public void OnAppActivate(int fActive, uint dwOtherThreadID)  
        {  
        }  
  
        public void OnEnterState(uint uStateID, int fEnter)  
        {  
        }  
  
        public void OnLoseActivation()  
        {  
        }  
  
        public void Terminate()  
        {  
        }  
  
        #endregion  
    }  
}   
```

