---
title: Komut satırından Profiler raporları oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c4cf566affff500d372a980a6f07122c2df33a23
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788595"
---
# <a name="creating-profiler-reports-from-the-command-line"></a>Komut Satırından Profil Oluşturma Raporları Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**VSPerfReport** komut satırı aracı profil oluşturma veri (.vsp) dosyalarını gelen .xml veya virgülle ayrılmış değer (.csv) raporlarını oluşturmanıza olanak sağlar. VSPerfReport rapor türleri arabirimi tablo tabanlı görünümlerini karşılayabilmesi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Rapor yalnızca sizin kodunuzu gösterir ve profil oluşturma veri dosyasını yalnızca bir segmentini gösterecek şekilde filtreleyebilirsiniz. Daha fazla bilgi için [VSPerfReport](../profiling/vsperfreport.md).  
  
 Ayrıca, profil oluşturma veri dosyaları semboller .vsp dosyalarına katıştırarak ve önceden analiz edilmiş raporu oluşturarak daha küçük ve daha hızlı açmak (.vsps) dosyaları paylaşmak daha kolay yapabilirsiniz.  
  
## <a name="common-tasks"></a>Ortak Görevler  
  
|Görev|İlgili içerik|  
|----------|---------------------|  
|**Temel bir rapor oluşturun.** Tüm oluşturur veya bir alt kümesini VSPerfReport rapor türleri.|-   [Temel raporlar oluşturma](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|  
|**İki profil oluşturma veri dosyaları karşılaştırın.** İki profil oluşturma veri dosyaları performans verilerini karşılaştıran bir "fark" raporu oluşturun.|-   [Nasıl yapılır: bir komut isteminden bir Profiler Karşılaştırma raporu oluşturma](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|  
|**Görünüm çağrı izleme ve olay izleme için Windows (ETW) verileri.** Uygulamanızın işlevlerine her giriş ve çıkış noktası ve işlevinizden diğer işlevlere her çağrı için zamanlama bilgileri listeleyen bir çağrı izleme raporu oluşturun. Veya profil oluşturma yürütmesine toplanmış olan tüm ETW olayları ayrıntılı bir listesi oluşturun.|-   [Nasıl yapılır: çağrı izleme raporu oluşturma](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|  
|**Bir raporu filtreleyebilirsiniz.** Bir raporu yalnızca kodunuzu işlevler veya belirli bir zaman profil oluşturma veri dosyasını içinde sınırlar.|-   [Nasıl yapılır: komut satırından raporları filtreleme](../profiling/how-to-filter-reports-from-the-command-line.md)|  
|**Taşınabilir profil oluşturma veri dosyaları oluşturun.** Profil oluşturma verilerini daha kolay paylaşım yapmak için bir .vsp dosyasına profil oluşturma için semboller ekleyebilir. Ayrıca, daha küçük ve daha hızlı açmak önceden çözümlenmiş bir profil oluşturma veri (.vsps) dosyası da oluşturabilirsiniz.|-   [Taşınabilir profil oluşturma veri dosyaları oluşturma](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|



