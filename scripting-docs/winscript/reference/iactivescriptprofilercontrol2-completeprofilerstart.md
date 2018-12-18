---
title: IActiveScriptProfilerControl2::CompleteProfilerStart | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::CompleteProfilerStart
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5abd4ee4237991714bfe3d8ba21b083f1a1920cd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793418"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Profil Oluşturucu, tüm geçerli komut dosyası motorlarına profil başlattığınız bildirir. Bu yöntemi kullanarak, tam çağrı yığını edinebilirsiniz [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] profil başlattığınızda çalışır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Yöntemi, herhangi bir parametre almaz.  
  
## <a name="return-value"></a>Dönüş Değeri  
 HRESULT döndürür. Olası değerler aşağıdaki gibidir:  
  
|Dönüş değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_FAIL`|Profil oluşturma başlatılamıyor.|  
|`S_FALSE`|Bir komut dosyası değil çalıştırılırken profil başlatıldı.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profil oluşturma etkin değil. Geri arama yok ayarlandı.|  
|`E_OUTOFMEMORY`|Bellek durum nedeniyle çağrı yığını alınamıyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çağırma `IActiveScriptProfilerControl2::CompleteProfilerStart` zaten çağrı yığınındaki işlevler için olayları gönderilmesini sağlar. Bu yöntem, geçerli sekmesinde herhangi bir komut dosyası altyapısı başlar profil sonra çağrılacak sahiptir. Her komut dosyası altyapısı yöntemi çağrılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [Iactivescriptprofilercontrol2 arabirimi](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)