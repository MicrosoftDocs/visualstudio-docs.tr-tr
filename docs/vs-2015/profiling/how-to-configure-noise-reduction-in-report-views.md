---
title: 'Nasıl yapılır: rapor görünümlerinde gürültü azaltmayı yapılandırma | Microsoft Docs'
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
- vs.performance.noisereduction.dialog
helpviewer_keywords:
- profiling tools, trimming
- profiling tools, report noise reduction
- profiling tools, folding
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e85e765ed80b37c7c688f9c0f25e3b7e8782a42f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51767699"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Nasıl yapılır: Rapor Görünümlerinde Gürültü Azaltmayı Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Performans raporları çağrı ağacı görünümü ve ayırma görünümünde görüntülenen veri miktarını sınırlamak için gürültü azaltma yapılandırılabilir. Gürültü azaltma kullanarak performans sorunlarını daha belirgin. Performans raporları çözümlemek istediğinizde yararlıdır.  
  
 Gürültü azaltma yapılandırma seçenekleri aşağıdaki ayarları içerir:  
  
-   **Kırpma** rapor analiz edilirken görünümü içinde yapılandırdığınız, değer ve eşik ayarları izleyen kesme yordamında açıklandığı kalan işlevleri atlayacak. Varsayılan olarak, kırpma etkinleştirilir.  
  
-   **Katlama** katlamayı etkinleştirirseniz, yapılandırdığınız ayarlarını karşılayan art arda gelen işlevlerle yola, izleyen kırılma yordamında açıklandığı birleştirilir. Varsayılan olarak, katlama varsayılan olarak etkindir.  
  
### <a name="to-configure-trimming-for-a-performance-report"></a>Bir performans raporu için kırpmayı yapılandırmak için  
  
1.  Ne zaman bir çağrı ağacı görünümü veya ayırma görünümü görüntülenir oluşturulan raporda **Geliştirici** menüsünde tıklatın **Profiler** ve ardından **gürültü azaltma seçenekleri**.  
  
     **Gürültü azaltma** iletişim kutusu görüntülenir.  
  
2.  Kırpma etkinleştirmek için aşağıdaki adımları izleyin:  
  
    1.  Seçin **kırpmayı etkinleştirme**. Varsayılan ayar budur.  
  
        > [!NOTE]
        >  Gürültü azaltma etkinleştirildiğinde, bir bilgi çubuğu raporunda görüntülenir. Daha fazla bilgi için [çağrı ağacı görünümü](../profiling/call-tree-view.md) ve [ayırma görünümü](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Değer ayarı kullanarak yapılandırma **değer** aşağı açılan liste ve geçerli ayarı seçme.  
  
    3.  Yüzde değerindeki yazarak istenen eşik ayarı yapılandırmak **eşiği** metin kutusu.  
  
    4.  Oluşturulan rapor gürültüsünü azaltma uyarıda etkinleştirmek için seçin **gürültü azaltma etkinleştirildiğinde uyarı görüntüler**. Varsayılan ayar budur.  
  
3.  Temizleyin, kırpma devre dışı bırakmak için **kırpmayı etkinleştirme**.  
  
4.  **Tamam**'ı tıklatın.  
  
### <a name="to-configure-folding-for-a-performance-report"></a>Bir performans raporu için Katlama yapılandırmak için  
  
1.  Üzerinde **Geliştirici** menüsünü tıklatın **Profiler** ve ardından **gürültü azaltma seçenekleri**.  
  
     **Gürültü azaltma** iletişim kutusu görüntülenir.  
  
2.  Katlamayı etkinleştirmek için aşağıdaki adımları izleyin:  
  
    1.  Seçin **katlamayı etkinleştirmek**. Varsayılan ayar budur.  
  
        > [!NOTE]
        >  Gürültü azaltma etkinleştirildiğinde, bir bilgi çubuğu raporunda görüntülenir. Daha fazla bilgi için [çağrı ağacı görünümü](../profiling/call-tree-view.md) ve [ayırma görünümü](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Değer ayarı kullanarak yapılandırma **değer** aşağı açılan liste ve geçerli ayarı seçme.  
  
    3.  Yüzde değerindeki yazarak istenen eşik ayarı yapılandırmak **eşiği** metin kutusu.  
  
    4.  Oluşturulan rapor gürültüsünü azaltma uyarıda etkinleştirmek için seçin **gürültü azaltma etkinleştirildiğinde uyarı görüntüler**. Varsayılan ayar budur.  
  
3.  Katlama devre dışı bırakmak için işareti kaldırın **katlamayı etkinleştirmek**.  
  
4.  **Tamam**'ı tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Rapor görünümlerini özelleştirme performans araçları](../profiling/customizing-performance-tools-report-views.md)   
 [Nasıl yapılır: kısa işlevleri izlemeden dahil veya hariç](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)   
 [Çağrı ağacı görünümü](../profiling/call-tree-view.md)   
 [Ayırmalar Görünümü](../profiling/dotnet-memory-allocations-view.md)



