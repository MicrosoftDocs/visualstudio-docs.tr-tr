---
title: IDebugCustomViewer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fb70365304883abe99a87cfec5e78bbed89f2dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107546"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Bu arabirim, bir ifade değerlendiricisi her biçimi gerekli olan bir özelliğin değerini görüntülemek için (EE) sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Uygulayanlar için Notlar  
 Bir EE özel bir biçimde bir özelliğin değerini görüntülemek için bu arabirimi uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 COM'ın bir çağrı `CoCreateInstance` işlevi bu arabirimi başlatır. `CLSID` Geçirilen `CoCreateInstance` kayıt defterinden elde edilir. Çağrı [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) kayıt defteri konumu alır. Açıklamalar örnek yanı sıra ayrıntılar için bkz.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırayla yöntemleri  
 Aşağıdaki yöntem bu arabirimi uygular:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Belirli bir değeri görüntülemek için gerekli ne olursa olsun yapar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir özelliğin değeri normal bir şekilde görüntülendiğinde bu arabirimi kullanılır — Örneğin, veri tablosu veya başka bir karmaşık özellik türüne sahip. Bir özel Görüntüleyici tarafından gösterilen olarak `IDebugCustomViewer` arabirim, EE bakmaksızın belirli bir türde verileri görüntülemek için bir dış program türü Görselleştirici farklıdır. EE bu EE özgü özel Görüntüleyicisi'ni uygular. Bir kullanıcı kullanmak için türü Görselleştirici veya özel bir Görüntüleyici olması Görselleştirici türünü seçer. Bkz: [Visualizing ve veri görüntüleme](../../../extensibility/debugger/visualizing-and-viewing-data.md) bu işlem hakkında ayrıntılı bilgi için.  
  
 Özel bir Görüntüleyici bir EE aynı şekilde kaydedilir ve bu nedenle, bir dil GUID ve satıcı GUID gerektirir. Yalnızca EE tam ölçüm (veya kayıt defteri girdisi adı) adı verilir. Bu ölçüm döndürülür [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) sırayla yapılan bir çağrı tarafından döndürülen yapısı [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). Ölçümde depolanan değer `CLSID` COM ait geçirilen `CoCreateInstance` işlev (örneğe bakın).  
  
 [Hata ayıklama için SDK Yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) işlevi, `SetEEMetric`, özel bir Görüntüleyici kaydetmek için kullanılır. "İfade Değerlendiricileri" kayıt defteri bölümüne bakın `Debugging SDK Helpers` belirli kayıt defteri anahtarları için özel bir Görüntüleyici gerekiyor. Bir ifade değerlendiricisi birkaç önceden tanımlanmış ölçümleri gerekirken özel Görüntüleyicisi (hangi EE'ın uygulayan tarafından tanımlandı) yalnızca bir ölçüm gerektiğini unutmayın.  
  
 Normalde, özel bir Görüntüleyici beri verilerin salt okunur bir görünümünü sağlar [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) arabirimi sağlanan için [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) dize olarak dışında özelliğin değerini değiştirmek için hiçbir yöntemlerine sahiptir. EE rasgele veri bloğu sayısını değiştirme desteklemek için uygulayan aynı nesne üzerinde özel arabirimini uygulayan `IDebugProperty3` arabirimi. Bu özel arabirim sonra rasgele bir veri bloğunun değiştirmek için gereken yöntemleri sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 Başlık: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Örnek  
 Bu örnekte, bu özellik tüm özel görüntüleyiciler varsa bir özellikten ilk özel Görüntüleyicisi alma gösterilmektedir.  
  
```cpp  
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
 [Çekirdek arabirimleri](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [Hata ayıklama için SDK Yardımcıları](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)