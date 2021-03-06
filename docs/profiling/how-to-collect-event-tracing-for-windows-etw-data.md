---
title: Windows için olay Izleme (ETW) verileri topla | Microsoft Docs
description: Uygulamada performans sorunlarının nerede olduğunu anlamak için Windows için olay Izleme 'yi (ETW) nasıl kullanacağınızı öğrenin. Verileri VSPerfReport.exe görüntüleyebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 77ddd22450786091c5240f26213633a7935c03dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886294"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Nasıl yapılır: Windows için olay Izleme (ETW) verileri toplama

Windows için olay Izleme (ETW), profil oluşturucu günlük çekirdeğini veya uygulama tanımlı olayları sağlayan etkili bir çekirdek düzeyi izleme olanıdır. Olay sağlayıcısından toplanan veriler yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı aracının/**summary: ETW** seçeneği kullanılarak görüntülenebilir. Uygulamada performans sorunlarının nerede olduğunu anlamak için bu raporu kullanabilirsiniz.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-enable-event-trace-providers"></a>Olay izleme sağlayıcılarını etkinleştirmek için

1. **Performans Gezgini**, performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Özellik sayfalarında**, **Windows olayları** özelliklerine tıklayın.

3. **Verileri toplamak için olay izleme sağlayıcısını seçin** listesinden, uygulamanızı profili eklemek için kullanmak istediğiniz olay sağlayıcılarını seçin.

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)
