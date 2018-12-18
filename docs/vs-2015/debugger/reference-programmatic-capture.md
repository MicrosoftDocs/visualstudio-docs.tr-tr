---
title: Başvuru (programlı yakalama) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66e80d02ac41d78f2c79e7b2accb11388d456ad8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744269"
---
# <a name="reference-programmatic-capture"></a>Başvuru (Programlı Yakalama)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Grafik tanılama yakalama özelliklerini programlı yakalama bir API aracılığıyla programlı denetime destekler. Geçiş ve iletileri grafik tanılama baş üstü (baş yukarı Göster) eklemek, başlatmak ve grafik günlük dosyaları oluşturmak ve grafik bilgilerini yakalamak için bu API'yi kullanabilirsiniz.  
  
## <a name="programmatic-capture-apis"></a>Programlı yakalama API'leri  
  
### <a name="classes"></a>Sınıflar  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[VsgDbg Sınıfı](../debugger/vsgdbg-class.md)|Üzerinden grafik tanılama uygulama bileşeninin programlı bir şekilde denetlenen bir arabirimi temsil eder.|  
  
### <a name="preprocessor-symbols"></a>Önişlemci sembolleri  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)|Grafik günlük dosyası, kullanıcı için geçici dosyalar dizini kaydedilip kaydedilmediğini kendi varlığı tanımlar.|  
|[VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)|Grafik günlük dosyası varsayılan dosya adını tanımlar.|  
|[VSG_NODEFAULT_INSTANCE](../debugger/vsg-nodefault-instance.md)|Varsayılan örneği olup olmadığını, varlığı tanımlayan `VsgDbg` sınıfı sağlanır.|  
  
## <a name="related-articles"></a>İlgili Makaleler  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Grafik Bilgilerini Yakalama](../debugger/capturing-graphics-information.md)|Böylece kullanabilirsiniz, DirectX tabanlı uygulamanızdan grafik bilgilerini yakalama gösterir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] işleme sorunlarını tanılamak için grafik tanılama araçları.|  
|[Genel bakış](../debugger/overview-of-visual-studio-graphics-diagnostics.md)|Grafik tanılama DirectX oyunlarındaki ve uygulamalarındaki işleme hatalarını ayıklamanıza nasıl yardımcı olduğu gösterilmektedir.|



