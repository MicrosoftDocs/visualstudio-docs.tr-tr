---
title: Kaynak izleme performans kuralları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 433a89ae2a7cf8c9e20ec3711dcebe1514ae021b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31584587"
---
# <a name="resource-monitoring-performance-rules"></a>Kaynak İzleme Performans Kuralları
Kaynak İzleme kategorideki performans iletileri, uygulamanızın performansı ile ilgili ek bilgiler sağlar. Bu veriler, performans sorunlarını analiz etmek için kullanabilirsiniz. Bu, bilgi ve her çalıştırma profili oluşturma için bildirilen kurallardır.  
  
|||  
|-|-|  
|[DA0501: İşlemin ortalama CPU kullanımının profili oluşturuluyor.](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|Bu ileti bir işlemci yönergeleri uygulamadan çalıştırmakla meşgul zamanın yüzde olarak bildirir. Bildirilen ortalama profili oluşturuluyor işlem etkin olan tüm ölçüm aralıklarında değerdir.|  
|[DA0502: İşlemin maksimum CPU kullanımının profili oluşturuluyor](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|Bu ileti, en yüksek işlemci yönergeleri uygulamadan çalıştırmakla meşgul zamanı yüzdesi bildirir. Profili oluşturuluyor işlem etkin olan tüm ölçüm aralıkları arasında bildirilen en büyük değeri bildirilen değerdir.|  
|[DA0503: İşlem için Bayt Cinsinden Ortalama Çalışma Kümesinin profili oluşturuluyor](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Bu ileti ortalama profil oluşturma etkinken, işlemin kullandığı bayt cinsinden fiziksel bellek miktarını raporlar. Bu ölçü fiziksel bellek çalışma kümesi bilinir.|  
|[DA0504: İşlem için izin verilen Bayt Cinsinden En Büyük Çalışma Kümesinin profili oluşturuluyor](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Bu ileti en fazla profil oluşturma etkinken, işlemin kullandığı bayt cinsinden fiziksel bellek miktarını raporlar.|  
|[DA0505: İşlem için izin verilen Ortalama Özel Bayt Sayısının profili oluşturuluyor](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Bu ileti ortalama belleğin sanal profil oluşturma sırasında bayt cinsinden ayrılmış işleminin etkin olduğunu bildirir. Bu ölçü sanal bellek olarak bilinen *özel bayt*. Özel bayt yalnızca işlem içinde çalışan iş parçacıkları tarafından erişilebilecek bir işlem tarafından ayrılan sanal bellek konumlarını temsil eder.|  
|[DA0506: İşlem için izin verilen Maksimum Özel Bayt Sayısının profili oluşturuluyor](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Bu ileti maksimum sanal bellek profili oluşturma sırasında özel bayt cinsinden ayrılmış işleminin etkin olduğunu bildirir.|