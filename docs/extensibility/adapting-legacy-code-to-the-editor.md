---
title: Eski kod düzenleyicisine uyarlama | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e04ae5484b6c1fd5bcc56154c6cec23334e7ef8d
ms.sourcegitcommit: 8cdc6e2ad2341f34bd6b02859a7c975daa0c9320
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53307797"
---
# <a name="adapt-legacy-code-to-the-editor"></a>Eski kod düzenleyicisine uyum
Visual Studio düzenleyicisinde, mevcut kod bileşenlerini erişebileceğiniz birçok özelliğe sahiptir. Aşağıdaki yönergeler, olmayan MEF Bileşeni, düzenleyici işlevselliği kullanmak için örneğin, bir VSPackage, uyum gösterilmektedir. Yönergeler ayrıca hem yönetilen hem de yönetilmeyen kod düzenleyicisinin Hizmetleri almak için bağdaştırıcıları kullanmayı gösterir.  
  
## <a name="editor-adapters"></a>Düzenleyici bağdaştırıcıları  
 Düzenleyici bağdaştırıcıları ya da dolgular, olan sınıfları ve arabirimleri de kullanıma Düzenleyicisi nesneleri için sarmalayıcılar <xref:Microsoft.VisualStudio.TextManager.Interop> API. Örneğin Düzenleyici olmayan hizmetleri arasında taşımak için bağdaştırıcılar, Visual Studio Kabuk komutları ve düzenleyici Hizmetleri kullanabilirsiniz. (Bu, düzenleyici Visual Studio şu anda nasıl barındırılan içindir.) Bağdaştırıcıları ayrıca Visual Studio'da düzgün çalışması eski düzenleyici ve dil hizmeti uzantıları sağlar.  
  
## <a name="use-editor-adapters"></a>Düzenleyici bağdaştırıcıları kullanmak  
 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> Yeni düzenleyici arabirimler ve eski arabirimleri arasında geçiş yapma yöntemleri ve bağdaştırıcıları oluşturma yöntemleri sağlar.  
  
 Bu hizmet bir MEF Bileşeni bölümünde kullanıyorsanız, hizmet aşağıda gösterildiği gibi aktarabilirsiniz.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Bu hizmet bir olmayan MEF Bileşeni olarak kullanmak istiyorsanız, bu konunun ilerleyen bölümlerindeki "Kullanarak Visual Studio Düzenleyicisi hizmetler bir MEF olmayan bileşeni" bölümündeki yönergeleri izleyin.  
  
## <a name="switch-between-the-new-editor-api-and-the-legacy-api"></a>Düzenleyici API ve eski API yeni arasında geçiş  
 Düzenleyici nesneyi bir eski arabirimi arasında geçiş yapmak için aşağıdaki yöntemleri kullanın.  
  
|Yöntem|Dönüştürme|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Dönüştürür bir <xref:Microsoft.VisualStudio.Text.ITextBuffer> için bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Dönüştürür bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> için bir <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Dönüştürür bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> için bir <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Dönüştürür bir <xref:Microsoft.VisualStudio.Text.Editor.ITextView> için bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Dönüştürür bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> için bir <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
  
## <a name="create-adapters"></a>Bağdaştırıcıları oluşturun  
 Eski arabirimleri için bağdaştırıcıları oluşturmak için aşağıdaki yöntemleri kullanın.  
  
|Yöntem|Dönüştürme|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Oluşturur bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Oluşturur bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> için belirtilen <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Oluşturur bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Oluşturur bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Oluşturur bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> için bir <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Oluşturur bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>Yönetilmeyen kodda bağdaştırıcıları oluşturma  
 Yerel olarak kayıtlı tüm bağdaştırıcısı sınıflar birlikte oluşturulabilir ve kullanarak oluşturulabilir `VsLocalCreateInstance()` işlevi.  
  
 Tüm bağdaştırıcıları tanımlanan GUID'ler kullanılarak oluşturulan *vsshlids.h* dosyası *\..\VisualStudioIntegration\Common\Inc\\* Visual Studio SDK klasörü yükleme. VsTextBufferAdapter bir örneğini oluşturmak için aşağıdaki kodu kullanın.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="create-adapters-in-managed-code"></a>Yönetilen kodda bağdaştırıcıları oluşturma  
 Yönetilen kodda, bağdaştırıcılar aynı şekilde yönetilmeyen kod için tanımlanan birlikte oluşturabilirsiniz. Oluşturma ve bağdaştırıcıları ile etkileşime olanak tanıyan bir MEF hizmet de kullanabilirsiniz. Bu şekilde bir bağdaştırıcı alma birlikte oluşturduğunuzda olandan daha ayrıntılı denetim sağlar.  
  
### <a name="to-create-an-adapter-for-ivstextview"></a>Bir bağdaştırıcı için Ivstextview oluşturmak için  
  
1.  Bir başvuru ekleyin *Microsoft.VisualStudio.Editor.dll*. Emin olun `CopyLocal` ayarlanır `false`.  
  
2.  Örneği <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>aşağıdaki gibi.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3.  Çağrı `CreateX()` yöntemi.  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="use-the-visual-studio-editor-directly-from-unmanaged-code"></a>Yönetilmeyen kod doğrudan Visual Studio Düzenleyicisi'ni kullanın  
 COM çağrılabilir arabirimleri, Microsoft.VisualStudio.Platform.VSEditor ad alanı ve Microsoft.VisualStudio.Platform.VSEditor.Interop ad alanı IVx * arabirimleri olarak kullanıma sunar. Örneğin, COM sürümünü Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer arabirimi olan <xref:Microsoft.VisualStudio.Text.ITextBuffer> arabirimi. Gelen `IVxTextBuffer`, arabellek anlık görüntüleri erişin, önbelleği değiştiren, arabellek metin değişikliği olaylarını dinler ve izleme noktaları ve yayılma oluşturun. Aşağıdaki adımları nasıl erişileceğini gösteren bir `IVxTextBuffer` gelen bir `IVsTextBuffer`.  
  
### <a name="to-get-an-ivxtextbuffer"></a>Bir IVxTextBuffer almak için  
  
1.  IVx tanımlarında\* arabirimdir içinde *VSEditor.h* dosyası *\..\VisualStudioIntegration\Common\Inc\\* Visual Studio'nun klasörü SDK yükleme.  
  
2.  Aşağıdaki kodu kullanarak bir metin arabelleği başlatır `IVsUserData->GetData()` yöntemi. Aşağıdaki kodda, `pData` işaretçisidir bir `IVsUserData` nesne.  
  
    ```cpp  
    #include <textmgr.h>  
    #include <VSEditor.h>  
    #include <vsshlids.h>  
  
    CComPtr<IVsTextBuffer> pVsTextBuffer;  
    CComPtr<IVsUserData> pData;  
    CComPtr<IVxTextBuffer> pVxBuffer;  
    ...  
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))  
    {  
        CComVariant vt;  
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&  
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))  
        {  
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);  
        }  
    }  
    ```  
  
## <a name="use-visual-studio-editor-services-in-a-non-mef-component"></a>Visual Studio Düzenleyicisi Hizmetleri bir olmayan MEF Bileşeni olarak kullanın  
 MEF kullanmayan varolan yönetilen kod bileşeni varsa ve Visual Studio Düzenleyicisi hizmetlerini kullanmak istediğiniz ComponentModelHost VSPackage'ı içeren derlemeyi bir başvuru ekleyin ve onun SComponentModel hizmeti alın.  
  
### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>Visual Studio Düzenleyicisi bileşenleri olmayan MEF Bileşeni kullanmak için  
  
1.  Bir başvuru ekleyin *Microsoft.VisualStudio.ComponentModelHost.dll* derlemede *\..\Common7\IDE\\* Visual Studio yükleme klasörü. Emin olun `CopyLocal` ayarlanır `false`.  
  
2.  Özel bir ekleme `IComponentModel` gibi Visual Studio Düzenleyicisi Hizmetleri, kullanmak istediğiniz sınıf üyesi.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3.  Başlatma yöntemi bileşeniniz için bileşen modelinde örneği oluşturur.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4.  Bundan sonra herhangi bir Visual Studio Düzenleyicisi hizmetin çağırarak alabileceğiniz `IComponentModel.GetService<T>()` istediğiniz hizmeti için yöntemi.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```
