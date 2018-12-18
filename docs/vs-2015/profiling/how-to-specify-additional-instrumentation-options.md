---
title: 'Nasıl yapılır: ek izleme seçeneklerini belirtme | Microsoft Docs'
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
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
ms.assetid: 639afe26-8335-4bd4-8aa5-f2c607b81f07
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8e8fa3029f98084645bc56e490a93d5d8880b06
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743046"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Nasıl yapılır: Ek İzleme Seçeneklerini Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İkili dosyalarını işaretleyebilir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] tümleşik geliştirme ortamı (IDE) veya komut satırı araçlarını kullanarak. IDE içinde bir ikili izleme, ek izleme seçeneklerini belirterek izleme sırasında toplanan verilerin hacmini denetleyebilirsiniz [Vsınstr](../profiling/vsinstr.md) aracı. Bu seçenekler, oturum veya hedef düzeyinde kullanılabilir. Örneğin, dahil etmek veya izleme işlemi sırasında belirli işlevleri hariç tutmak için hedef düzeyinde ek izleme seçeneği kullanın.  
  
 **Gereksinimler**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!IMPORTANT]
>  Eklenen her araştırma biraz özgün programın davranışını değiştirir. Bu değişikliği yükü analiz zamanında neden olur. Bu ek yükü yaklaşık çıkarılır olsa da, yine de çok iş parçacıklı uygulamalar üzerinde ince zamanlama etkileri vardır. [Vsınstr](../profiling/vsinstr.md) aracı profil oluşturma sırasında seçenekleri Yardım denetim veri koleksiyonu.  
  
### <a name="to-specify-additional-instrumentation-option"></a>Ek izleme seçeneği belirlemek için  
  
1.  İçinde **performans Gezgini**seçin **performans oturumu** ve ardından sağ tıklayıp **özellikleri**.  
  
2.  İçinde **özellikler sayfaları**, tıklayın **Gelişmiş** özellikleri.  
  
3.  Tür seçenekleri **ek izleme seçeneklerini** kutusu.  
  
     Örneğin, /CONTROL:THREAD profil oluşturma düzeyini belirtmek için kullanın. Seçeneklerinin tam listesi için bkz: [Vsınstr](../profiling/vsinstr.md).  
  
4.  **Tamam**'ı tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [Komut Satırından Profil Oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)



