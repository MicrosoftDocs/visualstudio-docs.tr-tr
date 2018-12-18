---
title: Komut satırından profil oluşturucu raporları oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3433bef9b30c9b912d721b526ab11692a8de78af
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749277"
---
# <a name="create-profiler-reports-from-the-command-line"></a>Komut satırından profil oluşturucu raporları oluşturma
**VSPerfReport** komut satırı aracı oluşturmanıza olanak sağlar. *XML* veya virgülle ayrılmış değer (. *CSV*) profil oluşturma verilerini gelen raporlar (. *Vsp*) dosyaları. VSPerfReport rapor türleri arabirim için tablo tabanlı görünümlerini karşılayabilmesi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Yalnızca kodunuzun göstermek için ve profil oluşturma veri dosyası yalnızca bir parçasını göstermek için raporu filtreleyebilirsiniz. Daha fazla bilgi için bkz: [VSPerfReport](../profiling/vsperfreport.md).  
  
 Ayrıca, profil oluşturma veri dosyaları sembolleri gömerek paylaşmak daha kolay yapabilirsiniz. *vsp* göre önceden çözümlenen rapor oluşturma ve dosyaları (. *vsps*) açmak daha hızlı ve daha küçük dosyalar.  
  
## <a name="common-tasks"></a>Ortak görevler
  
|Görev|İlgili içerik|  
|----------|---------------------|  
|**Temel bir rapor oluşturun.** Tüm ya da alt kümesini VSPerfReport rapor türleri oluşturun.|-   [Temel raporlar oluşturma](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|  
|**İki profil oluşturma veri dosyaları karşılaştırın.** Profil oluşturma veri dosyaları iki performans verilerini karşılaştırır "fark" rapor oluşturun.|-   [Nasıl yapılır: bir komut isteminden profil oluşturucu Karşılaştırma raporu oluşturma](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|  
|**Görünüm çağrı izleme ve olay izleme için Windows (ETW) verileri.** Her giriş ve çıkış noktası, uygulamanızın işlevlere ve diğer işlevleri işlevinizi tarafından her çağrı için zamanlama bilgileri listeleyen bir çağrı izleme raporu oluşturun. Veya bir profil çalıştırmada toplanmış olan tüm ETW olayları ayrıntılı bir listesini oluşturun.|-   [Nasıl yapılır: çağrı izleme raporu oluşturma](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|  
|**Bir raporu filtreleme.** Bir rapor yalnızca kodunuzda işlevleri veya profil oluşturma veri dosyası belirli bir zamanda sınırlayın.|-   [Nasıl yapılır: komut satırından raporları filtreleme](../profiling/how-to-filter-reports-from-the-command-line.md)|  
|**Taşınabilir profil oluşturma veri dosyaları oluşturun.** Profil oluşturma verilerini daha kolay paylaşımı yapmak için bir profil içine çalıştırmak için simgeler eklenebilir. *vsp* dosya. Önceden çözümlenen bir profil verileri de oluşturabilirsiniz (. *vsps*) küçük ve daha hızlı açmak dosya.|-   [Taşınabilir profil oluşturma veri dosyaları oluşturma](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|