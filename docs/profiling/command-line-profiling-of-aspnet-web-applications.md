---
title: ASP.NET Web uygulamalarının komut satırı profili oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 03cb8a6b28ed5f5fece49644d9b1df2608f3e36d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895671"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>ASP.NET web uygulamalarının komut satırı profili oluşturma
Bu bölümde yordamları ve performans verilerini toplamak için seçenekleri açıklar [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamaları kullanarak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] komut satırından profil oluşturma araçları.  
  
> [!NOTE]
>  Windows 8 ve Windows Server 2012'deki Gelişmiş güvenlik özellikleri Visual Studio profil oluşturucu bu platformlarda veri toplayan bir şekilde önemli değişiklikler gerekmiştir. UWP uygulamaları, ayrıca yeni toplama teknikleri gerektirir. Bkz: [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Ortak görevler
  
| Görev | İlgili içerik |
| - | - |
| **Temel ASP.NET profil oluşturma verilerini kolayca toplamak:** kullanım **VSPerfASPNETCmd** örnekleme, izleme, .NET bellek, çekişmeyi toplamak veya yapılandırma gereksinimleri olmadan etkileşim veri katmanı için araç ve Internet Information Services (IIS) yeniden başlatmaları için gerekli **VSPerfCmd**. **VSPerfASPNETCmd** ek veri toplamak için veya veri toplamayı denetlemek için izin vermez. **Not:****VSPerfASPNETCmd** kullanmayı tercih edilen araç bağımsız profil oluşturucu profil ASP.NET Web siteleri için kullanın. | -   [Profil oluşturma VSPerfASPNETCmd ile hızlı web sitesi](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) |
| **Uygulama istatistikleri toplamak:** performans istatistikleri toplamak için örnekleme yöntemini kullanın. Veri örnekleme, CPU kullanım sorunlarını analiz etmek için ve bir uygulamanın genel performans özelliklerini anlamak için kullanışlıdır. | -   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) |
| **Ayrıntılı zamanlama verileri toplama:** ayrıntılı zamanlama bilgileri toplamak için izleme metodunu kullanın. Ölçümlü izleme verileri ayrıntılı analiz uygulama senaryoları biri için g/ç sorunlarını analiz etmek için yararlı olacaktır. | -   [İzleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md) |
| **.NET bellek verileri toplamak:** kullanım örnekleme veya Araçlar boyutunu ve sayısını gösteren .NET bellek ayırma verilerini toplamak için ayrılan nesneler. Her çöp toplama nesildeki kazanılır nesnelerinin sayısı ve boyutu gösteren nesne yaşam süresi verilerini de toplayabilirsiniz. | -   [Bellek verileri toplama](../profiling/collecting-memory-data-from-an-aspnet-web-application.md) |
| **Eşzamanlılık verileri toplamak:** kaynak çekişmesi verisini toplamak için eşzamanlılık yöntemi kullanın. **Not:** iş parçacığı etkinliği ve görselleştirme verilerini toplamak için Web uygulamaları desteklenmez. | -   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md) |
| **Katman etkileşim verileri ekleme:** zaman uyumlu ilişkin performans verilerini ekleyebilirsiniz [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] çağrılarının [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulaması için bir Microsoft yapar [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] veritabanı. | -   [Katman etkileşim verileri toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md) |
  
## <a name="related-tasks"></a>İlişkili görevler

  
|Görev|İlgili içerik|  
|----------|---------------------|  
|**(İstemci) tek başına uygulamaların profilini oluşturma**|-   [Bağımsız uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Profil hizmetler**|-   [Profil hizmetler](../profiling/command-line-profiling-of-services.md)|