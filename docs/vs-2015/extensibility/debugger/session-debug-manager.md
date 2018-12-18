---
title: Hata ayıklama oturumu Manager | Microsoft Docs
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
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0c3bb1ce939ed54997d8d8b40de75bcd095e4dc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759143"
---
# <a name="session-debug-manager"></a>Oturum Hata Ayıklama Yöneticisi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Oturum hata ayıklama Yöneticisi (SDM) herhangi bir sayıda herhangi bir sayıda makine üzerinde birden çok işlem programlarında hata ayıklama hata ayıklama altyapısı (DE) herhangi bir sayıda yönetir. SDM çoğaltıcı bir hata ayıklama altyapısı olmaya ek olarak, IDE için hata ayıklama oturumu birleşik bir görünümünü sağlar.  
  
## <a name="session-debug-manager-operation"></a>Oturum hata ayıklama Yöneticisi işlemi  
 Oturum hata ayıklama Yöneticisi (SDM) DE yönetir. Çalıştıran bir makinede aynı anda birden fazla hata ayıklama altyapısı olabilir. DEs çoğullamalısınız için SDM DEs arabirimlerden sayısı sarmalar ve bunları tek bir arabirim olarak IDE sunar.  
  
 Performansı artırmak için bazı arabirimler çoğullanır değil. Bunun yerine, doğrudan DE kullanılan ve bu arabirimler çağrıları SDM geçmemektedir. Özel yönerge, bellek veya belirli bir program tarafından belirli bir DE hata ayıklaması belgede başvurduğundan Örneğin, bellek, kod ve belge bağlamı ile kullanılan arabirimleri, çoğullanır değil. Diğer bir DE iletişim, düzeyinde yer alması gerekir.  
  
 Bu tüm içeriklerde geçerli değildir. İfade değerlendirme bağlamı arabirimi çağrılar SDM gidin. SDM ifadesi değerlendirmesi sırasında sarmalar [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) ifade değerlendirildiğinde, programlar olabilir aynı işlemde hata ayıklama birden çok DEs gerektirebilir bulunduğundan IDE verir arabirimi aynı iş parçacığında çalışır.  
  
 SDM genellikle bir temsilci mekanizması olarak görev yapar, ancak bir yayın mekanizması davranan. Örneğin, ifade değerlendirmesi sırasında SDM tüm DEs, belirtilen bir iş parçacığında kod çalıştırabilir bildirmek için bir yayın mekanizması görevi görür. Benzer şekilde, SDM durdurma olayı aldığında, bunların çalışmasını durdurmanız tüm programlar için yayınlar. Bir adım çağrıldığında SDM tüm programlar çalışmaya devam ettiğini yayınlar. Kesme noktaları ayrıca her DE olarak yayınlanır.  
  
 SDM geçerli programı, iş parçacığı veya yığın çerçevesi izlemez. İşlem, program ve iş parçacığı bilgileri SDM belirli hata ayıklama olayları ile birlikte gönderilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)   
 [Hata ayıklayıcı bileşenleri](../../extensibility/debugger/debugger-components.md)   
 [Hata Ayıklayıcı Bağlamları](../../extensibility/debugger/debugger-contexts.md)

