---
title: Başlatmış | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 56aa940d65934f7cc72f692f5bdf5e44854d276c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471459"
---
# <a name="uninit"></a>UnInit
Grafik günlük dosyası sonlandırır kapatılır ve uygulama, etkin olarak grafik bilgilerini kaydetme sırasında kullanılan kaynakları serbest bırakır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```C++  
void UnInit();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `UnInit` bir örneği olduğunda otomatik olarak çağrılır `VsgDbg` sınıfı yok. Varsa `VsgDbg` örneği etkin olarak kaydetmediğiniz grafik bilgilerini, bunun hiçbir etkisi olmaz.  
  
 Sonra `UnInit` bir örneği üzerinde çağrıldıktan `VsgDbg` sınıfı, yeni bir grafik günlük dosyası çağırarak oluşturulabilir `Init` ve çağırarak sonuçlandırılmış `UnInit`. Bu sayıda olarak aynı kullanmak istediğiniz yineleyebilirsiniz `VsgDbg` birkaç bağımsız grafik günlük dosyaları oluşturmak için örnek.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Init](init.md)