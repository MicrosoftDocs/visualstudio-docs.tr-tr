---
title: IActiveScriptProfilerControl2::PrepareProfilerStop | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::PrepareProfilerStop
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78078cd874be1d7d3d169be2d3d70e65866be3fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793433"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Profil Oluşturucu, tüm geçerli komut dosyası motorlarına profil oluşturmayı durdurmak zorunda kalacaklarını bildirir. Bu yöntemi kullanarak, tam çağrı yığını edinebilirsiniz [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] profil durdurduğunuzda çalışıyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>Parametreler  
 Yöntemi, herhangi bir parametre almaz.  
  
## <a name="return-value"></a>Dönüş Değeri  
 HRESULT döndürür. Olası değerler aşağıdaki gibidir:  
  
|Dönüş değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Yöntem başarılı oldu.|  
|`E_FAIL`|Profil oluşturma başlatılamadı.|  
|`S_FALSE`|Bir komut dosyası değil çalıştırılırken profil durduruldu.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profil oluşturma etkin değil.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çağırma `IActiveScriptProfilerControl2::PrepareProfilerStop` çağrı yığınındaki işlevler için olayları gönderilmesini sağlar. Bu yöntem, geçerli sekmesinde herhangi bir komut dosyası altyapısı profil oluşturma durdurmadan önce çağrılacak sahiptir. Her komut dosyası altyapısı yöntemi çağrılabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [Iactivescriptprofilercontrol2 arabirimi](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)