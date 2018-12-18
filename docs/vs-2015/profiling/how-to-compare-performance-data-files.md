---
title: 'Nasıl yapılır: performans veri dosyalarını karşılaştırma | Microsoft Docs'
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
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf80c86f233a40ba0d65d239ae1668d575a66bb2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752615"
---
# <a name="how-to-compare-performance-data-files"></a>Nasıl yapılır: performans veri dosyalarını karşılaştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir karşılaştırma ("fark") rapor ya da görünüm oluşturarak iki farklı profil oluşturucu veri dosyalarını (.vsp veya .vsps) sonuçlarını karşılaştırabilirsiniz. Farklar, performans gerilemeleri ve bir profil oluşturma oturumundan diğerine oluştu iyileştirmeleri karşılaştırmasını gösterir.  
  
 Fark rapor verilerin tablo bir görünümünü sunar. Tablo, delta veya taban çizgisinden Değiştir sunar. Bu, eski değeri, temel değeri ve sonuç değeri arasındaki farkı yeni analiz belirleyerek hesaplanır.  
  
 Profil Oluşturucu veri karşılaştırmalarını temel işlevler kodu, uygulama, çizgiler, yönerge işaretçileri (IP) ve türleri modüllerde alabilir.  
  
 Bir eşiği gürültüsünü azaltmak ve Tablo görünümünde değişip değişmediğini satırların herhangi bir veri filtrelemek için belirli bir miktarda ayarlanabilir.  
  
### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Performans Gezgini içinde bir proje için karşılaştırma dosya görünümü oluşturmak için  
  
1.  İçinde **performans Gezgini**altında **raporları**, taban çizgisi değerlerini karşılaştırma için kullanmak istediğiniz .vsp veya .vsps rapor dosyası seçin.  
  
2.  Karşılaştırmak istediğiniz .vsp veya .vsps rapor dosyalarını seçin.  
  
3.  Seçilen dosyalardan birine sağ tıklayın ve ardından **karşılaştırma raporları**.  
  
### <a name="to-compare-values"></a>Değerleri karşılaştırmak için  
  
1.  Seçin **Karşılaştırma raporu** rapor görünümü penceresindeki sekmesi.  
  
2.  İçinde **tablo** aşağı açılan listesinde, işlev veya karşılaştırmak için modülleri seçin.  
  
3.  İçinde **sütun** aşağı açılan listesinde, karşılaştırmak istediğiniz değer seçin.  
  
4.  (isteğe bağlı) İçin bir değer yazın **eşiği**.  
  
5.  Tıklayın **uygulamak**.  
  
### <a name="to-compare-report-files"></a>Rapor dosyalarını karşılaştırma  
  
1.  Üzerinde **Çözümle** menüsünde **Performans raporlarını Karşılaştır**.  
  
2.  İçinde **seçin analiz dosyaları karşılaştırma** penceresinde, Gözat ve Seç **ana hat dosyası** analiz dosyası (.vsp veya .vsps) ve **karşılaştırma dosyasını** (.vsp veya .vsps).  
  
3.  **Tamam**'ı tıklatın.



