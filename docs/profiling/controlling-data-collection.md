---
title: Veri toplama denetimi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: deafe488fdb44216f0a6750f532c2e0d2363b453
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262286"
---
# <a name="control-data-collection"></a>Denetimin veri toplama
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları, bir performans oturumu sırasında profil oluşturma verilerinin ne zaman toplanacağını kontrol etmenizi ve profillenen işlevleri belirtmenizi sağlar. Bu bölümde, veri koleksiyonunu durdurmak ve başlatmak açıklar **performans Gezgini** ve **veri toplama denetimi** windows ve kendisi için profil oluşturma verilerini toplanır nesneleri sınırlandırmak nasıl.  
  
## <a name="common-tasks"></a>Ortak görevler
  
|Görev|İlgili içerik|  
|----------|---------------------|  
|**Profil oluşturma durdurup başlatın:** uygulama başlatıldığında bir uygulamayı veya iliştirebilirsiniz profil oluşturucu zaten çalışan bir işlemin profili başlayabilirsiniz. Hedef uygulama çalışırken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Hedef uygulamayı kapatarak veya profil oluşturucuyu çalışan bir işlemden ayırarak bir profil oluşturma oturumunu sonlandırabilirsiniz. |-   [Nasıl yapılır: Başlangıç ve bitiş performans verileri toplama](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Nasıl yapılır: ekleme ve ayırma işlemleri çalıştırmanın performans araçları](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Nasıl yapılır: duraklatma ve sürdürme performans verileri toplama](../profiling/how-to-pause-and-resume-performance-data-collection.md)|  
|**Toplanan verileri sınırlamak için profil oluşturma Araçları'nı yapılandırın:** izleme metodunu kullanın çalıştırmalarının profil toplanan verileri sınırlamak için performans oturumu yapılandırma özelliklerini kullanabilirsiniz. Belirli .dll dosyalarını, ad alanlarını, sınıfları ve işlevleri dahil edebilir veya hariç tutabilirsiniz. Ayrıca, belirttiğiniz bir boyut eşiğini karşılamayan işlevleri çıkarabilirsiniz.|-   [Nasıl yapılır: belirli DLL'ler için araçları sınırlama](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Nasıl yapılır: belirli işlevler için araçları sınırlama](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Nasıl yapılır: hariç tutma veya kısa işlevleri izlemeden içerir](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|  
  
## <a name="related-sections"></a>İlgili bölümler  
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Performans Gezgini](../profiling/performance-explorer.md)