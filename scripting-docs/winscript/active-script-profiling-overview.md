---
title: Etkin komut dosyası profil oluşturmaya genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Active Script Profiling
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9413e8b6e6db0c81eb1853c24506d20c8d06f3e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791924"
---
# <a name="active-script-profiling-overview"></a>Etkin Komut Dosyası Profil Oluşturmaya Genel Bakış
[Etkin komut dosyası profil oluşturucu arabirimleri](../winscript/reference/active-script-profiler-interfaces.md) komut dosyası altyapısı profil oluşturmayı etkinleştirin. Etkin komut dosyası profil oluşturma, aşağıdaki bölümlerden oluşur:  
  
-   Dil altyapısı  
  
-   Ana bilgisayar  
  
-   Profil Oluşturucu  
  
## <a name="language-engine"></a>Dil altyapısı  
 Komut dosyası dili altyapısı yürütür. Komut dosyası kodu yürütülür gibi profil sağlayan yöntemler sağlar. Profil oluşturma etkinleştirildiğinde, dil altyapısı bağımsız değişken olarak COM nesnesi profil oluşturucu sınıfı tanımlayıcısı (CLSID) alır. Profil Oluşturucu COM nesnesinin örneği oluşturur ve çeşitli olaylar meydana geldiğinde profil oluşturucu çağırır.  
  
 Dil altyapısı uygulayan [Iactivescriptprofilercontrol arabirimi](../winscript/reference/iactivescriptprofilercontrol-interface.md).  
  
> [!NOTE]
>  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] Dil çalışma zamanı JS_PROFILER ortam değişkeni oluşturma profil etkinleştirilmesi gerekip gerekmediğini belirlemek için denetler. Bu değişken profil oluşturucu CLSID değerine ayarlanırsa, dil çalışma zamanı oluşturmak için hangi profil oluşturucu belirlemek için değişkenin değerini kullanarak profil oluşturucu COM nesnesinin örneği oluşturur.  
  
## <a name="host"></a>Ana bilgisayar  
 Ana bilgisayar dil motoru oluşturur ve dil altyapısı yürütülecek komut dosyaları sağlar. Bir akıllı ana bilgisayar aynı zamanda bir hata ayıklayıcı veya profil oluşturucu ile hata ayıklama veya profil daha iyi bilgi sağlamak için kullanılabilir bir belge bağlam sağlar.  
  
## <a name="profiler"></a>Profil Oluşturucu  
 Çeşitli olaylar meydana geldiğinde profil oluşturucu çağrıları dil altyapısı alır. Profil Oluşturucu COM nesnesi olarak kayıtlı olması gerekir ve uygulamalıdır [Iactivescriptprofilercallback arabirimi](../winscript/reference/iactivescriptprofilercallback-interface.md) arabirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası profil oluşturucu arabirimleri](../winscript/reference/active-script-profiler-interfaces.md)