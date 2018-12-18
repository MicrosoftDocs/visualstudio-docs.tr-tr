---
title: Tür Görselleştiricileri ve özel görüntüleyiciler uygulama | Microsoft Docs
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
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 11d047904e932646eedc974a50590dbe0a9ea99e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791286"
---
# <a name="implementing-type-visualizers-and-custom-viewers"></a>Tür Görselleştiricileri ve Özel Görüntüleyiciler Uygulama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015'te, bu şekilde ifade değerlendiricisi uygulama kullanım dışı bırakılmıştır. CLR ifade değerlendiricisi uygulama hakkında daha fazla bilgi için lütfen bkz [CLR ifade Değerlendiricilerini](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendiricisi örnek](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Tür görselleştiricileri ve özel görüntüleyiciler onaltılık sayı döküm basit daha anlamlı bir şekilde belirli bir türdeki verileri görüntülemek bir kullanıcı izin verir. İfade değerlendiricisi (EE) özel görüntüleyiciler belirli veri türlerine veya değişkenleri ile ilişkilendirebilirsiniz. Bu özel görüntüleyiciler EE tarafından uygulanır. Başka bir üçüncü taraf satıcı veya bile son kullanıcının gelebilir dış tür görselleştiriciler, EE de destekler.  
  
## <a name="discussion"></a>Tartışma  
  
### <a name="type-visualizers"></a>Tür Görselleştiricileri  
 Tür görselleştiricileri ve özel görüntüleyiciler Her nesne için izleme penceresinde görüntülenecek bir listesi için Visual Studio ister. İfade değerlendiricisi (EE) kendisi için tür görselleştiricileri ve özel görüntüleyiciler desteklemek istediği her türü için böyle bir liste sağlar. Çağrılar [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) ve [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) tür görselleştiricileri ve özel görüntüleyiciler erişen tüm işlemini başlatmak (bkz [Visualizing ve verileri görüntüleme](../../extensibility/debugger/visualizing-and-viewing-data.md)çağrı sırası hakkında ayrıntılı bilgi için).  
  
### <a name="custom-viewers"></a>Özel görüntüleyiciler  
 Özel görüntüleyiciler EE belirli bir tür için uygulanır ve tarafından temsil edilen [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) arabirimi. Özel Görüntüleyici yalnızca bu belirli özel Görüntüleyici uygulayan EE çalıştırılırken kullanılabilir bir tür görselleştiricisi kadar esnek değildir. Özel Görüntüleyici uygulama tür görselleştiricileri desteği uygulamak daha kolaydır. Ancak tür görselleştiricileri destekleyen maksimum esneklik için son kullanıcı kendi verilerini görselleştirmek için sağlar. Bu tartışma geri kalanında, yalnızca tür görselleştiricileri ilgilidir.  
  
## <a name="interfaces"></a>Arabirimler  
 Tür görselleştiricileri, Visual Studio tarafından tüketilmesi desteklemek için aşağıdaki arabirimlerinden EE uygular:  
  
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
  Tür görselleştiricileri desteklemek için aşağıdaki arabirimlerinden EE kullanır:  
  
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Verileri Görselleştirme ve görüntüleme](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)

