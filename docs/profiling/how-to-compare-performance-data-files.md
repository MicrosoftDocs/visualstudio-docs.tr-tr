---
title: 'Nasıl yapılır: performans veri dosyalarını karşılaştırma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eeb9f26091deaf995ef1221d39aa7264553f5c70
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815385"
---
# <a name="how-to-compare-performance-data-files"></a>Nasıl yapılır: performans veri dosyalarını karşılaştırma
İki farklı profil oluşturucu veri dosyalarını sonuçlarını karşılaştırabilirsiniz (. *Vsp* veya. *vsps*) karşılaştırma ("fark") oluşturarak rapor veya görüntüleyin. Karşılaştırma farkları, performans gerileme ve diğer bir profil oluşturma oturumu oluştu iyileştirmeleri gösterir.  
  
 Diff rapor verileri içeren bir tablo görünümü gösterir. Tablo delta veya taban çizgisiyle değişiklik gösterir. Bu, yeni analiz eski değer, taban çizgisi değeri ve sonuç değeri arasındaki farkı belirleyerek hesaplanır.  
  
 Profil Oluşturucu veri karşılaştırmaları temel işlevleri kodda, uygulama, satırları, yönerge işaretçileri (IP) ve türleri modülleri alabilir.  
  
 Bir eşik gürültü azaltmak ve herhangi bir veri değişip değişmediğini satır Tablo görünümünde filtrelemek için belirli bir miktarda ayarlanabilir.  
  
### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Performans Gezgini içinde bir proje için karşılaştırma dosya görünümü oluşturmak için  
  
1.  İçinde **performans Gezgini**altında **raporları**seçin. *Vsp* veya. *vsps* taban çizgisi değerlerini karşılaştırma için kullanmak istediğiniz rapor dosyası.  
  
2.  Seçin. *vsp* veya. *vsps* rapor karşılaştırmak istediğiniz dosyaları.  
  
3.  Seçili dosyaları birine sağ tıklayın ve ardından **karşılaştırmak raporları**.  
  
### <a name="to-compare-values"></a>Değerleri karşılaştırmak için  
  
1.  Seçin **Karşılaştırma raporu** rapor görünümü penceresi sekmesindedir.  
  
2.  İçinde **tablo** aşağı açılan listesinde, işlev veya karşılaştırmak için modülleri seçin.  
  
3.  İçinde **sütun** aşağı açılan listesinde, karşılaştırmak istediğiniz değeri seçin.  
  
4.  (isteğe bağlı) İçin bir değer yazın **eşik**.  
  
5.  Tıklatın **uygulamak**.  
  
### <a name="to-compare-report-files"></a>Rapor dosyalarını karşılaştırma  
  
1.  Üzerinde **Çözümle** menüsünde, select **karşılaştırmak performans raporları**.  
  
2.  İçinde **karşılaştırma için analiz dosyaları seçin** penceresi, Gözat ' nı seçip **temel dosya** analiz dosyası (. *Vsp* veya. *vsps*) ve **karşılaştırma dosya** (. *Vsp* veya. *vsps*).  
  
3.  **Tamam**'ı tıklatın.