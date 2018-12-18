---
title: Sembol sağlayıcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d54494a8fa23e0714769863ac0fa2e5ddc1f4c2
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276981"
---
# <a name="symbol-provider"></a>Sembol sağlayıcısı
Bir ifade değerlendiricisi uygulama değişkenleri ve ifadeleri değerlendirilebilmesi için dil derleyicisi tarafından üretilen sembolik hata ayıklama bilgileri erişmeniz gerekir. Bunu bir sembol işleyici olarak da adlandırılan bir sembol sağlayıcısı (SP) arabirimleri kullanma tarafından yapar.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Program veritabanı (PDB) sembolü dosya biçimi kullanılarak yerel kod yanı sıra yönetilen kod için SPs sağlar. Olmadığı sürece güçlü özel biçiminde depolanan semboller kullanmak, programınız için gerekir, bu tarafından sağlanan SPs kullanmanız önerilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="implementation-notes"></a>Uygulama notları  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Hata ayıklama motorlarını beklediğiniz ortak dil çalışma zamanı (CLR) arabirimlerini kullanarak SPs ile bahsedeceğiz. Sonuç olarak, Visual Studio hata ayıklama altyapıları ile çalışan bir SP CLR desteklemesi gerekir. Hata ayıklama arabirimleri tüm CLR tam listesi parçası olan debugref.doc içinde bulunabilir, [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].  
  
 Yalnızca özel hata ayıklama altyapısıyla, SP çalışacaksınız ise, hata ayıklama altyapısı gereksinimlerine bağlı olarak uygun gördüğünüz şekilde SP uygulayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Hata ayıklayıcı bileşenleri](../../extensibility/debugger/debugger-components.md)