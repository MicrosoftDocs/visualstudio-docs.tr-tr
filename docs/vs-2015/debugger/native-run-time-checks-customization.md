---
title: Yerel çalışma zamanı denetimleri özelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.crt
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 216a96a6702bfabc57d235144bf4a6cc05df4224
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721134"
---
# <a name="native-run-time-checks-customization"></a>Yerel Çalışma Zamanı Denetimlerini Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Derleme yaptığınızda **/RTC** (çalışma zamanı denetimleri) veya `runtime_checks` pragması, C çalışma zamanı kitaplığı, yerel çalışma zamanı denetimleri sağlar. Bazı durumlarda, çalışma zamanı denetimi özelleştirmek isteyebilirsiniz:  
  
- Bir dosya ya da varsayılan dışındaki hedef çalışma zamanı denetimi iletileri yönlendirmek için.  
  
- Hedef çalışma zamanı için bir çıktı belirtmek için üçüncü taraf hata ayıklayıcı altında iletileri denetleyin.  
  
- Çalışma zamanı denetimi iletileri yayın sürümü C çalışma zamanı kitaplığı ile derlenmiş bir programdan bildirmek için. Kitaplık sürümleri kullanmayın `_CrtDbgReportW` çalışma zamanı hatalarını raporlamak için. Bunun yerine, görüntüledikleri bir **Assert** her bir çalışma zamanı hata iletişim kutusu.  
  
  Çalışma zamanı hata denetimi özelleştirmek için şunları yapabilirsiniz:  
  
- Çalışma zamanı hata raporlama işlevi yazma. Daha fazla bilgi için [nasıl yapılır: bir çalışma zamanı hata raporlama işlevi yazma](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
- Hata iletisi hedef özelleştirin.  
  
- Sorgu çalıştırma hakkında bilgi için hataları kontrol edin.  
  
## <a name="customize-the-error-message-destination"></a>Hata iletisi hedef özelleştirme  
 Kullanırsanız `_CrtDbgReportW` hatalarını raporlamak için kullanabileceğiniz `_CrtSetReportMode` hata iletileri hedefini belirlemek için.  
  
 Özel bir raporlama işlevini kullanıyorsanız `_RTC_SetErrorType` bir hata rapor türü ile ilişkilendirilecek.  
  
## <a name="query-for-information-about-run-time-checks"></a>Sorgu için çalışma zamanı denetimleri hakkında bilgi  
 `_RTC_NumErrors` çalışma zamanı hata denetimleri tarafından algılanan hata türlerinin sayısını döndürür. Her hata kısa bir açıklamasını almak için 0'dan dönüş değeri olarak döngüye girer `_RTC_NumErrors`, yineleme değeri geçirme `_RTC_GetErrDesc` her döngüde. Daha fazla bilgi için [_RTC_NumErrors](http://msdn.microsoft.com/library/7e82adae-38e2-4f8b-bc0b-37bda8109fd1) ve [_RTC_GetErrDesc](http://msdn.microsoft.com/library/7994ec2b-5488-4fd4-806d-a166c9a9f927).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: yerel çalışma zamanı denetimlerini kullanma](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [_CrtDbgReport, _CrtDbgReportW](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc)





