---
title: Toplama istatistikleri ASP.NET web uygulamaları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 9350d96911e818402f7e32ebcd83fe832f31f9d9
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34263035"
---
# <a name="collect-statistics-for-aspnet-web-apps"></a>ASP.NET web uygulamaları için istatistikleri toplama

Bu bölümdeki yordamları ve kullanarak bir ASP.NET Web uygulaması için performans istatistikleri toplamak için seçenekleri açıklar **VSPerfASPNETCmd** ve **VSPerfCmd** komut satırı aracı ve örnekleme profili oluşturma yöntemi.  
  
> [!NOTE]
>  Gelişmiş güvenlik özellikleri Windows 8 ve Windows Server 2012 Visual Studio profil oluşturucu bu platformlarda toplar şekilde önemli değişiklikler gerekmiştir. UWP uygulamalar için yeni koleksiyon teknikler de gerekir. Bkz: [Windows 8 ve Windows Server 2012 uygulamaların performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Ancak **VSPerfCmd** aracı size tam erişim duraklatma ve profil oluşturma, yeniden başlatma da dahil olmak üzere profil oluşturma araçları işlevselliği için ve ek verileri işlemci ve Windows performans sayaçlarını toplama, kullanmanız gerekir **VSPerfASPNETCmd** bu işlevselliği gerekmediğinde komut satırı aracı. **VSPerfASPNETCmd** komut satırı aracıdır tercih edilen yöntem zaman olduğunuz bağımsız profil oluşturucuyu kullanarak ASP.NET Web siteleri profil oluşturma. İle karşılaştırılan [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracı, ortam değişkenleri ayarlanmış olması gerekir ve bilgisayar yeniden başlatıldığı gerekli değildir. Daha fazla bilgi için bkz: [VSPerfASPNETCmd ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Ortak görevler  
  
|Görev|İlgili içerik|  
|----------|---------------------|  
|**Bir ASP.NET uygulamasına profil oluşturucu ekleme**|-   [Nasıl yapılır: uygulama istatistikleri toplamak için bir ASP.NET web uygulamasına profil oluşturucu ekleme](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>İlişkili görevler  
  
### <a name="profile-aspnet-web-applications"></a>Profil ASP.NET web uygulamaları  
  
|Görev|İlgili içerik|  
|----------|---------------------|  
|**İzleme metodunu kullanarak profil**|-   [İzleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|  
|**Bellek ayırma ve atık toplama profil**|-   [Bellek verileri toplama](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|  
|**Kaynak çakışması ve iş parçacığı etkinliği profil**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|  
  
### <a name="sample-method"></a>Örnek yöntemi  
  
|Görev|İlgili içerik|  
|----------|---------------------|  
|**Profil tek başına (istemci) uygulamaları**|-   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|  
|-   **Profil Hizmetleri**|-   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
  
### <a name="analyze-sampling-data-views-and-reports"></a>Veri görünümlerini örnekleme ve raporları analiz eder.  
 [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)