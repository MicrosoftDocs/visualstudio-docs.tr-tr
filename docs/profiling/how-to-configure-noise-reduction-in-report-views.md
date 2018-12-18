---
title: 'Nasıl yapılır: rapor görünümlerinde gürültü azaltmayı yapılandırma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.noisereduction.dialog
helpviewer_keywords:
- profiling tools, trimming
- profiling tools, report noise reduction
- profiling tools, folding
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 460251aaa89c22d7bb1320d19882af4f68736cc0
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815190"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Nasıl yapılır: rapor görünümlerinde gürültü azaltmayı yapılandırma
Performans raporları çağrı ağacı görünümü ve ayırma görünümü sunulan veri miktarını sınırlayarak gürültü azaltma için yapılandırılabilir. Gürültü azaltma kullanarak, performans sorunlarını daha belirgin. Performans raporları çözümlediğinizde kullanışlıdır.  
  
 Gürültü azaltma yapılandırma seçenekleri, aşağıdaki ayarları içerir:  
  
-   **Kırpma** bir rapor analiz olduğunda, görünüm izleyen kırpma yordamda açıklandığı şekilde yapılandırmış olduğunuz değeri ve eşik ayarlarında kalan işlevleri atlayın. Varsayılan olarak kırpma etkindir.  
  
-   **Katlama** Katlama etkinleştirirseniz, yapılandırdığınız ayarlarını karşılayan ardışık bir yolu işlevleri, izleyen kırılma yordamında açıklandığı gibi birleştirilir. Varsayılan olarak, katlama varsayılan olarak etkinleştirilir.  
  
### <a name="to-configure-trimming-for-a-performance-report"></a>Bir performans raporu kırpma yapılandırmak için  
  
1.  Ne zaman bir çağrı ağacı görünümü veya ayırma görünümü görüntülenir oluşturulan rapora **Geliştirici** menüsünde tıklatın **profil oluşturucu** ve ardından **gürültü azaltma seçenekleri**.  
  
     **Gürültü azaltma** iletişim kutusu görüntülenir.  
  
2.  Kırpma etkinleştirmek için aşağıdaki adımları izleyin:  
  
    1.  Seçin **bölünmesini etkinleştir**. Varsayılan ayar budur.  
  
        > [!NOTE]
        >  Gürültü azaltma etkinleştirilirse, rapora bir bilgi çubuğu görüntülenir. Daha fazla bilgi için bkz: [çağrı ağacı görünümü](../profiling/call-tree-view.md) ve [ayırmalar görünümü](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Değer ayarı kullanarak yapılandırma **değeri** aşağı açılan liste ve geçerli ayarı seçme.  
  
    3.  Bir yüzde değeri yazarak istenen eşik ayarını yapılandırın **eşik** metin kutusu.  
  
    4.  Oluşturulan rapora gürültü azaltma uyarıda etkinleştirmek için seçin **gürültü azaltma etkin olduğunda uyarı görüntülemek**. Varsayılan ayar budur.  
  
3.  Kesme, Temizle devre dışı bırakmak için **etkinleştirmek kırpma**.  
  
4.  **Tamam**'ı tıklatın.  
  
### <a name="to-configure-folding-for-a-performance-report"></a>Bir performans raporu için Katlama yapılandırmak için  
  
1.  Üzerinde **Geliştirici** menüsünde tıklatın **profil oluşturucu** ve ardından **gürültü azaltma seçenekleri**.  
  
     **Gürültü azaltma** iletişim kutusu görüntülenir.  
  
2.  Katlama etkinleştirmek için aşağıdaki adımları izleyin:  
  
    1.  Seçin **Katlama etkinleştirmek**. Varsayılan ayar budur.  
  
        > [!NOTE]
        >  Gürültü azaltma etkinleştirilirse, rapora bir bilgi çubuğu görüntülenir. Daha fazla bilgi için bkz: [çağrı ağacı görünümü](../profiling/call-tree-view.md) ve [ayırmalar görünümü](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Değer ayarı kullanarak yapılandırma **değeri** aşağı açılan liste ve geçerli ayarını seçme.  
  
    3.  Bir yüzde değeri yazarak istenen eşik ayarını yapılandırın **eşik** metin kutusu.  
  
    4.  Oluşturulan rapora gürültü azaltma uyarıda etkinleştirmek için seçin **gürültü azaltma etkin olduğunda uyarı görüntülemek**. Varsayılan ayar budur.  
  
3.  Katlama devre dışı bırakmak için temizleyin **etkinleştirmek Katlama**.  
  
4.  **Tamam**'ı tıklatın.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Performans araçları rapor görünümlerini özelleştirme](../profiling/customizing-performance-tools-report-views.md)   
 [Nasıl yapılır: hariç tutma veya kısa işlevleri izlemeden içerir](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)   
 [Çağrı ağacı görünümü](../profiling/call-tree-view.md)   
 [Ayırmalar görünümü](../profiling/dotnet-memory-allocations-view.md)