---
title: Etkin komut dosyası sabitleri, numaralandırmaları ve hata kodları | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb4165a5471c8e79827f0f7605cef575e82bab75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791993"
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>Etkin Komut Dosyası Sabitleri, Numaralandırmaları ve Hata Kodları
Bu bölümde numaralandırmalar ve Windows komut dosyası motorları içinde kullanılan hata kodları açıklanmaktadır.  
  
## <a name="constants"></a>Sabitler  
  
|Sabit|Açıklama|  
|--------------|-----------------|  
|[SCRIPTTHREADID sabitleri](../../winscript/reference/scriptthreadid-constants.md)|İş parçacığı türünü belirtir.|  
  
## <a name="properties"></a>Özellikler  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|[Scrıptprop_hostkeepalıve özelliği](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Komut dosyası altyapısı bekleyen başvurular varsa tam olarak işlevsel tutulmalıdır olup olmadığını belirtmek için kullanılır.|  
  
## <a name="enumerations"></a>Numaralandırmalar  
  
|Sabit Listesi|Açıklama|  
|-----------------|-----------------|  
|[SCRIPTGCTYPE numaralandırması](../../winscript/reference/scriptgctype-enumeration.md)|Çöp toplama gerçekleştirmek için türü.|  
|[SCRIPTLANGUAGEVERSION numaralandırması](../../winscript/reference/scriptlanguageversion-enumeration.md)|Sürümleri scripting olası belirtir.|  
|[SCRIPTSTATE numaralandırması](../../winscript/reference/scriptstate-enumeration.md)|Bir komut dosyası motoru durumunu belirtir.|  
|||  
|[SCRIPTTHREADSTATE numaralandırması](../../winscript/reference/scriptthreadstate-enumeration.md)|Bir iş parçacığı durumu bir komut dosyası motoru belirtir.|  
|[SCRIPTTRACEINFO numaralandırması](../../winscript/reference/scripttraceinfo-enumeration.md)|İzlenen betik olayını temsil eder. Kullanılan [Iactivescriptsitetraceınfo::sendscripttraceınfo yöntemi](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[SCRIPTUICHANDLING numaralandırması](../../winscript/reference/scriptuichandling-enumeration.md)|UI denetim işleneceğini yolunu temsil eder.|  
|[SCRIPTUICITEM numaralandırması](../../winscript/reference/scriptuicitem-enumeration.md)|Kullanıcı Arabirimi öğesi türünü temsil eder. Kullanılan [Iactivescriptsiteuıcontrol::getuıbehavior yöntemi](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## <a name="error-codes"></a>Hata Kodları  
  
|Hata Kodu|Açıklama|  
|----------------|-----------------|  
|[Scrıpt_e_propagate hata kodu](../../winscript/reference/script-e-propagate-error-code.md)|Bir komut dosyası hatası farklı bir iş parçacığı olabilir çağırana yayılır.|  
|[Scrıpt_e_recorded hata kodu](../../winscript/reference/script-e-recorded-error-code.md)|Betik altyapısı ve ana bilgisayar arasında bir hata geçirildi.|  
|[Scrıpt_e_reported hata kodu](../../winscript/reference/script-e-reported-error-code.md)|Komut dosyası altyapısı ana bilgisayara işlenmeyen bir özel durum bildirdi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Etkin komut dosyası arabirimleri](../../winscript/reference/active-script-interfaces.md)