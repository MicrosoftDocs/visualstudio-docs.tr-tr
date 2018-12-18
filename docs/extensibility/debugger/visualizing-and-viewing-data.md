---
title: Verileri Görselleştirme ve görüntüleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50325281fcca92394df5db28cc590cfa1e85f651
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276799"
---
# <a name="visualizing-and-viewing-data"></a>Verileri Görselleştirme ve görüntüleme
Tür görselleştiricileri ve özel görüntüleyiciler mevcut verileri hızlı bir şekilde bir geliştirici için anlamlı bir şekilde. İfade değerlendiricisi (EE) destekleyen üçüncü taraf tür görselleştiricileri yapabilir, kendi özel görüntüleyiciler sağlayın.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaç tür görselleştiricileri ve özel görüntüleyiciler çağırarak nesnenin türüyle ilişkili olduğunu belirleyen [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) yöntemi. Visual Studio varsa en az bir tür görselleştiricisi veya özel Görüntüleyici kullanılabilir çağırır [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) yönteminin bu görselleştiriciler ve görüntüleyiciler listesini almak için (görselleştiriciler uygulayan s gerçekte bir listesi ve Görüntüleyiciler) ve bunları kullanıcıya sunar.  
  
## <a name="supporting-type-visualizers"></a>Tür görselleştiricileri destekleme  
 Tür görselleştiricileri desteklemek için EE uygulamalıdır arabirimleri vardır. Bu arabirimler, iki geniş kategoriye ayrılabilir: tür görselleştiricileri ve özellik verilere arabirimleri listelemek arabirimleri.  
  
### <a name="listing-type-visualizers"></a>Tür görselleştiricileri listeleme  
 EE destekler uygulamaya tür görselleştiricileri listeleme `IDebugProperty3::GetCustomViewerCount` ve `IDebugProperty3::GetCustomViewerList`. Bu yöntemler çağrısına karşılık gelen yöntemlere geçirmek [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) ve [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).  
  
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) çağırılarak alınır [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Bu yöntem gerektirir [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) öğesinden alınan arabirimi [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) arabirimi geçirilen [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` Ayrıca gerektirir [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) ve [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) için geçirilmiş arabirimleri `IDebugParsedExpression::EvaluateSync`. Oluşturmak için gereken son arabirimi `IEEVisualizerService` arabirimi [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) EE uygulayan arabirimi. Bu arabirim görselleştirilen özelliğine yapılacak değişiklikler sağlar. Tüm özellik verileri içinde saklanmış olduğu bir [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) ayrıca EE tarafından uygulanan arabirimi.  
  
### <a name="accessing-property-data"></a>Özellik verilerine erişme  
 Özellik verilerine erişme aracılığıyla gerçekleştirilir [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) arabirimi. Bu arabirim elde etmek için Visual Studio çağırır [QueryInterface](/cpp/atl/queryinterface) almak için özellik nesnesi üzerinde [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) arabirimi (uygulayan aynı nesne üzerinde uygulanan [ IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) arabirimi) ve ardından çağırır [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) elde etmek için yöntemi `IPropertyProxyEESide` arabirimi.  
  
 Tüm veri küme içi ve dışı geçirilen `IPropertyProxyEESide` arabirimi içinde saklanmış olduğu [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) arabirimi. Bu arabirim, bayt dizisini temsil eder ve Visual Studio ve EE tarafından uygulanır. Bir özelliğin veriler değiştirilecek olduğunda, Visual Studio oluşturur bir `IEEDataStorage` aramalar ve yeni verileri tutan nesne [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) yeni almak için bu veri nesnesi ile `IEEDataStorage` , sırasıyla nesnesini geçirilen [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) özelliğin verileri güncelleştirmek için. `IPropertyProxyEESide::CreateReplacementObject` uygulayan kendi sınıf örneği EE sağlayan `IEEDataStorage` arabirimi.  
  
## <a name="supporting-custom-viewers"></a>Özel görüntüleyiciler destekleme  
 Bayrağı `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` ayarlanır `dwAttrib` alanını [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) yapısı (bir çağrı tarafından döndürülen [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) nesne ilişkilendirilmiş özel Görüntüleyici olduğunu belirtmek için kendisiyle. Bu bayrak ayarlandığında, Visual Studio alır [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) alanından arabirim [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabirimi kullanılarak [QueryInterface](/cpp/atl/queryinterface).  
  
 Kullanıcı özel Görüntüleyici seçerse, Visual Studio Görüntüleyicisi'nin kullanarak özel Görüntüleyici başlatır `CLSID` tarafından sağlanan `IDebugProperty3::GetCustomViewerList` yöntemi. Visual Studio sonra çağıran [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) değeri kullanıcıya göstermek için.  
  
 Normalde, `IDebugCustomViewer::DisplayValue` veri salt okunur bir görünümünü sunar. Verilerde yapılan değişiklikleri izin vermek için EE değişen veri özelliği nesnesinde destekleyen özel bir arabirim uygulamalıdır. `IDebugCustomViewer::DisplayValue` Yöntemi veri değiştirilmesini desteklemesi için bu özel arabirim kullanır. Yöntem için özel arabirim durumuna bağlı `IDebugProperty2` olarak arabirimi geçirilen `pDebugProperty` bağımsız değişken.  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Tür görselleştiricileri ve özel görüntüleyiciler hem destekleme  
 Tür görselleştiricileri ve özel görüntüleyiciler içinde hem bir EE destekleyebilir [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) ve [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) yöntemleri. İlk olarak, EE bunu sağlayarak özel görüntüleyiciler sayısı tarafından döndürülen değer ekler [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) yöntemi. İkinci olarak, EE ekler `CLSID`tarafından döndürülen listeye kendi özel görüntüleyiciler sn [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)   
 [Tür görselleştiricisi ve özel Görüntüleyici](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)