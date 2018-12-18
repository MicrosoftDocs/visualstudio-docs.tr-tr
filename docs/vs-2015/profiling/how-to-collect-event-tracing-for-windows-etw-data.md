---
title: 'Nasıl yapılır: olay izleme için Windows (ETW) verilerini toplama | Microsoft Docs'
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
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
ms.assetid: aa2261fe-d5f5-49fc-a171-d18842e1dc7d
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b840f320495437bbabb35290b81a87bc2db545d5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762499"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Nasıl yapılır: Windows için Olay İzleme (ETW) Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Olay izleme için Windows (ETW), profil oluşturucu günlük çekirdek veya uygulama tarafından tanımlanan olayları sağlayan verimli çekirdek düzeyinde izleme sistemidir. Olay sağlayıcısı'ndan toplanan verileri yalnızca kullanılarak görüntülenebilir /**Summary: ETW** seçeneği [VSPerfReport](../profiling/vsperfreport.md) komut satırı aracı. Performans sorunlarını uygulamada nerede oluştuğunu belirlemek için bu raporu kullanabilirsiniz.  
  
 **Gereksinimler**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
>  Windows 8 ve Windows Server 2012'deki Gelişmiş güvenlik özellikleri Visual Studio profil oluşturucu bu platformlarda veri toplayan bir şekilde önemli değişiklikler gerekmiştir. Windows Store apps ayrıca yeni toplama teknikleri gerektirir. Bkz: [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-enable-event-trace-providers"></a>Olay izleme sağlayıcılarını etkinleştirme  
  
1.  İçinde **performans Gezgini**performans oturumu sağ tıklayın ve ardından **özellikleri**.  
  
2.  İçinde **özellik sayfaları**, tıklayın **Windows olayları** özellikleri.  
  
3.  İçinde **verileri toplamak için Select olayı izleme sağlayıcısı** listesinde, uygulamanızın profilini için kullanmak istediğiniz olay sağlayıcılarını seçin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans Oturumlarını Yapılandırma](../profiling/configuring-performance-sessions.md)



