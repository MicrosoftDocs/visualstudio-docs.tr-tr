---
title: Toplama ayrıntılı zamanlama verileri komut satırından profil oluşturucu izleme yöntemini kullanarak bir ASP.NET Web uygulaması için | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: a62c0fc4aca0c14d51e2f9e3ffda5b8d976681e8
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2018
ms.locfileid: "34335638"
---
# <a name="collect-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Komut satırından profil oluşturucu izleme yöntemini kullanarak bir ASP.NET web uygulaması için ayrıntılı zamanlama verileri toplama
Bu bölümdeki yordamları ve ayrıntılı performans toplamak için seçenekleri açıklar için verileri bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulaması kullanarak **VSPerfCmd** komut satırı aracı ve izleme yöntemi.  
  
> [!NOTE]
>  **VSPerfCmd** aracı duraklatma ve sürdürme profil oluşturma ve ek veri işlemci ve Windows performans sayaçlarını toplama dahil olmak üzere profil oluşturma araçları işlevine tam erişimi olan, sağlar. Aynı zamanda **VSPerfASPNETCmd** bu işlevselliği gerekmediğinde komut satırı aracı. Comparison için [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracı, ortam değişkenleri ayarlanması zorunda ve bilgisayar yeniden başlatıldığı gerekli değildir. Daha fazla bilgi için bkz: [VSPerfASPNETCmd ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  

## <a name="common-tasks"></a>Ortak görevler  
  
|Görev|İlgili içerik|  
|----------|---------------------|  
|**Statik olarak derlenmiş ikili dosyaları profil**|-   [Nasıl yapılır: statik olarak derlenmiş bir ASP.NET uygulamasını izleme ve ayrıntılı zamanlama verileri toplama](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)|  
|**Dinamik olarak derlenmiş ikili dosyaları profil**|-   [Nasıl yapılır: dinamik olarak derlenmiş bir ASP.NET uygulamasını izleme ve ayrıntılı zamanlama verileri toplama](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)|  
  

## <a name="related-tasks"></a>İlişkili görevler

  
### <a name="profile-aspnet-web-applications"></a>Profil ASP.NET web uygulamaları  
  
|Görev|İlgili içerik|  
|----------|---------------------|  
|**Örnekleme yöntemini kullanarak profil**|-   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|  
|**Bellek ayırma ve atık toplama profil**|-   [Bellek verileri toplama](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|  
|**Kaynak çakışması ve iş parçacığı etkinliği profil**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|  
  
### <a name="profile-by-using-the-instrumentation-method"></a>İzleme metodunu kullanarak profil  
  
|Görev|İlgili içerik|  
|----------|---------------------|  
|**Profil tek başına (istemci) uygulamaları**|-   [İzleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|  
|**Profil Hizmetleri**|-   [İzleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|  
  
### <a name="analyze-instrumentation-data-views-and-reports"></a>İzleme veri görünümleri ve raporları analiz eder.  
 [İzleme yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)