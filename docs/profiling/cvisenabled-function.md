---
title: Cvısenabled işlevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1555703c92695090a3c8ac7b04e7a35dadcd7627
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749206"
---
# <a name="cvisenabled-function"></a>Cvısenabled işlevi
Herhangi bir oturumunda belirtilen ETW sağlayıcı etkin olup olmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```C  
HRESULT CvIsEnabled(  
   _In_ PCV_PROVIDER pProvider  
);  
HRESULT CvIsEnabledEx(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ CV_IMPORTANCE level,  
   _In_ int category  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `category`  
 Kategori.  
  
 `level`  
 Önem düzeyi.  
  
 `pProvider`  
 Geçerli sağlayıcı nesnesi. NULL olamaz.  
  
## <a name="return-value"></a>Dönüş değeri  
 Sağlayıcı etkinse S_OK. Sağlayıcı şu anda devre dışıysa S_FALSE. Hata kodu vardı herhangi bir hata durumunda. BAŞARISIZ makrosu S_OK/S_FALSE için denetleyin ve hata koşulu için denetlemek için kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** *cvmarkers.h*  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [C++ Kitaplık Başvurusu](../profiling/cpp-library-reference.md)