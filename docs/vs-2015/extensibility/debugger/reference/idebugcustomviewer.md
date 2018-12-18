---
title: IDebugCustomViewer | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6b9e068591961e7eafa9d4fdc588da2694532463
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759509"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, ifade değerlendiricisi her biçimi gerekli bir özelliğin değerini görüntülemek için (EE) sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Bir EE özel bir biçimde bir özelliğin değerini görüntülemek için bu arabirimi uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 COM'ın bir çağrı `CoCreateInstance` işlevi bu arabirimin örneğini oluşturur. `CLSID` Geçirilen `CoCreateInstance` kayıt defterinden alınır. Bir çağrı [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) kayıt defteri konumu alır. Açıklamalar örnek yanı sıra ayrıntılar için bkz.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Bu arabirim, aşağıdaki yöntemi uygular:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|İnovasyonunuz ne olursa olsun, belirli bir değeri görüntülemek için gerekli yapar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir özelliğin değerini normal yollarla görüntülendiğinde bu arabirimi kullanılır — Örneğin, bir veri tablosu veya başka bir karmaşık özellik türü ile. Tarafından temsil edildikleri haliyle bir özel Görüntüleyici `IDebugCustomViewer` arabirim, EE ne olursa olsun, belirli bir türdeki verileri görüntülemek için bir dış program bir tür görselleştiricisi farklıdır. EE, EE için belirli bir özel Görüntüleyici uygular. Bir kullanıcı kullanmak için bir tür görselleştiricisi veya özel bir Görüntüleyici olması görselleştiricisi türünü seçer. Bkz: [Visualizing ve verileri görüntüleme](../../../extensibility/debugger/visualizing-and-viewing-data.md) bu işlemle ilgili ayrıntılar için.  
  
 Özel bir Görüntüleyici bir EE aynı şekilde kaydedilir ve bu nedenle, bir dil GUID ve satıcı GUID gerektirir. Ölçümün (veya kayıt defteri girdisi adı) için yalnızca EE bilinir. Bu ölçüm döndürülür [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) sırayla bir çağrı tarafından döndürülen yapısı [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). Ölçümde depolanan değer `CLSID` COM ait geçirilen `CoCreateInstance` işlev (örneğe bakın).  
  
 [Hata ayıklama için SDK Yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) işlevi `SetEEMetric`, özel bir Görüntüleyici kaydetmek için kullanılabilir. "İfade Değerlendiricilerini" kayıt defteri bölümüne bakın `Debugging SDK Helpers` özel Görüntüleyici, belirli kayıt defteri anahtarları için gerekiyor. İfade değerlendiricisi önceden tanımlanmış çeşitli ölçümleri gerektirirken özel Görüntüleyici (hangi EE'ın uygulayan tarafından tanımlanır) yalnızca bir ölçüm gerektiğini unutmayın.  
  
 Normalde, bir özel Görüntüleyici beri veri salt okunur bir görünümünü sağlar [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimi sağlanan için [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) yöntemi dışında özelliğin değerini bir dize olarak değiştirmek için yok. EE rastgele veri bloklarını değiştirilmesini desteklemesi için uygulayan aynı nesne üzerinde özel bir arabirimi uygulayan `IDebugProperty3` arabirimi. Bu özel arabirim ardından rastgele bir veri bloğu değiştirmek için gereken yöntemleri sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Örnek  
 Bu örnekte, bu özellik, herhangi bir özel görüntüleyiciler varsa bir özellikten ilk özel Görüntüleyici alma gösterilmektedir.  
  
```cpp#  
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)  
{  
    // This string is typically defined globally.  For this example, it  
    // is defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugCustomViewer *pViewer = NULL;  
    if (pProperty != NULL) {  
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);  
        if (pProperty3 != NULL) {  
            HRESULT hr;  
            ULONG viewerCount = 0;  
            hr = pProperty3->GetCustomViewerCount(&viewerCount);  
            if (viewerCount > 0) {  
                ULONG viewersFetched = 0;  
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };  
                hr = pProperty3->GetCustomViewerList(0,  
                                                     1,  
                                                     &viewerInfo,  
                                                     &viewersFetched);  
                if (viewersFetched == 1) {  
                    CLSID clsidViewer = { 0 };  
                    CComPtr<IDebugCustomViewer> spCustomViewer;  
                    // Get the viewer's CLSID from the registry.  
                    ::GetEEMetric(viewerInfo.guidLang,  
                                  viewerInfo.guidVendor,  
                                  viewerInfo.bstrMetric,  
                                  &clsidViewer,  
                                  strRegistrationRoot);  
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {  
                        // Instantiate the custom viewer.  
                        spCustomViewer.CoCreateInstance(clsidViewer);  
                        if (spCustomViewer != NULL) {  
                            pViewer = spCustomViewer.Detach();  
                        }  
                    }  
                }  
            }  
        }  
    }  
    return(pViewer);  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [Hata ayıklama için SDK Yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)

