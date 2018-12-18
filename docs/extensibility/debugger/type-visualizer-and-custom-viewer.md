---
title: Tür görselleştiricisi ve özel Görüntüleyici | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5cf2cc9c8f89ed0ecc7935f9afa8e096f05a840
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276500"
---
# <a name="type-visualizer-and-custom-viewer"></a>Tür görselleştiricisi ve özel Görüntüleyici
Tür görselleştiricisi bir veri parçasını belirli bir biçimde görüntüleyen bir bileşenidir. Tamamen biçimidir kimin Görselleştirici uygulayan kadar son kullanıcıya veya bir üçüncü taraf sağlayıcı görselleştiriciler, olması.  
  
 Özel bir Görüntüleyici, bir veri parçasını belirli bir biçimde görüntüleyen bir özel ifade değerlendiricisi parçasıdır. Tamamen biçimi (EE) ifade değerlendiricisi ' uygulayan kadar olduğu anlamına gelir özel Görüntüleyici'nin uygulayan kadar bu biçimidir.  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>İfade değerlendiricisi, tür görselleştiricileri desteği  
 Görselleştiriciler için erişilebilir arabirimleri kümesi destekleyerek tür görselleştiricileri bir EE destekler: gibi arabirimleri [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) ve [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Ancak, EE tür görselleştiricisi uygulamak için sorumlu değildir: EE, dış görselleştiriciler yalnızca tür bilgisi erişmesine izin verir. Tür görselleştiricileri EE birlikte sevk ve uygun bir yerden başka bir üçüncü taraf satıcı veya bile son kullanıcı tarafından sağlanan Visual Studio yüklü.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>İfade değerlendiricisi, özel görüntüleyiciler için destek  
 Özel görüntüleyiciler EE veri türünü görüntülemeye ilişkin kodu sağladığı bir EE de destekler. Özel bir Görüntüleyici uygulayan [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) tüm görevleri, verileri hangi biçimde göstermenin işleyen arabirimi istenen; Görüntüleyici görünümü üzerinde tam denetime sahiptir ve değiştirilmesi veri bile izin verebilirsiniz. Ürün gönderildiğinde EE tarafından sağlanan herhangi bir özel görüntüleyiciler EE ile gelir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Hata ayıklayıcı bileşenleri](../../extensibility/debugger/debugger-components.md)   
 [İfade değerlendirici](../../extensibility/debugger/expression-evaluator.md)   
 [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)