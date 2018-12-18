---
title: 'İzlenecek yol: XSLT Profiler | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4f401d253c81385dc197e912a7f9cc7d6156e393
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229456"
---
# <a name="walkthrough-xslt-profiler"></a>İzlenecek Yol: XSLT Profil Oluşturucusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
XSLT Profiler ölçülmesine yardımcı olmak, değerlendirme ve performans ile ilgili sorunları XSLT kodda hedef ayrıntılı XSLT performans raporları oluşturur. XSLT Profiler XSL ve XSLT stil sayfası iyileştirmeler için faydalı ipuçları içerir. XSLT uygulamaları için isteğe bağlı en yüksek performans, bu aracı gerekli olabilir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Aşağıdaki örneklerde yer alan yordamlar, Visual Studio 2010 and.NET Framework sürüm 4.0 gerektirir. XSLT Profiler, yalnızca Microsoft Visual Studio Team System ile profil oluşturma araçları ile kullanılabilir.  
  
### <a name="create-the-performance-report"></a>Performans raporu oluşturun  
  
1.  XSLT belge Visual Studio'da açın.  
  
2.  Tıklayarak **profil XSLT** XML menüsünde sağlanır seçeneği.  
  
3.  Girdi XML belgesini sağlar. Bir XML belgesi zaten açık değilse, dosya için istenir.  
  
4.  Analiz başlar ve bir ilerleme çubuğu Düzenleyicisi içinde ilerlemesini görüntüler.  
  
5.  XSLT çıkış çıkış Bölmesi'nde görünür.  
  
6.  Performans oturumu sona erdikten sonra bu performans raporu denetleyin. Bir performans raporda kaydedilen verileri görüntüleyin ve XSLT Performans analiz sağlar.  
  
### <a name="get-all-the-available-views"></a>Tüm kullanılabilir görünümlere Al  
  
1.  Tıklayarak **Geçerli Görünüm** tüm kullanılabilir görünümlere almak için aşağı açılan listesi.  
  
2.  Seçin **özeti görünümünü** seçeneğini **Geçerli Görünüm** aşağı açılan listesi. Varsayılan olarak, bir performans raporu görüntülenen **özeti görünümünü**. Bu görünüm, XSLT belge ile performans sorunlarını belirlemek için bir başlangıç noktasıdır. **Özeti görünümünü** aşağıdaki veri noktaları listelenmektedir:  
  
    -   En çok çağrılan İşlevler  
  
    -   En bireysel işlerle İşlevler  
  
    -   Yürütmek için en uzun zaman ayırdığınız işlevleri  
  
3.  Varsayılan olarak, her veri noktası için üç sütun vardır: işlev, mutlak değeri içinde çağrı sayısı ve toplam işlev çağrısı adlandırılmış işlevinin bir yüzde değeri adı. Her bir veri noktası **özeti görünümünü**, daha ayrıntılı görünüm için işlev veri noktalarına sağ tıklayarak gidebilirsiniz.  
  
4.  Seçin **işlev görünümü** seçeneğini **Geçerli Görünüm** aşağı açılan listesi. **İşlev görünümü** profil oluşturma sırasında çağrılan işlevlerin listeler. Bir sütun adına tıklayarak verileri yeniden sıralayabilirsiniz. Varsayılan olarak görüntülenen sütunlar şunlardır:  
  
    -   **İşlev adı**  
  
    -   **Geçen kapsamlı süre**  
  
    -   **Geçen dışlamalı süre**  
  
    -   **Kapsamlı uygulama süresi**  
  
    -   **Dışlamalı uygulama süresi**  
  
    -   **Çağrı sayısı**  
  
5.  Tüm saat sütunları hem mutlak değerler hem de yüzde görüntülenir. Terim **özel** diğer işlevleri tarafından harcanan zamanı fiyatlara geçen yürütülürken, bu işlevin yürütülmesi sırasında çağrılan işlev için toplam süreyi ifade eder.  
  
6.  Terim **Inclusive** adlı ve diğer işlevleri olarak adlandırılan işlevlerin çağrılma bunlardan herhangi bir işlev, yürütme süresi dahil olmak üzere tüm işlevlerin yürütülürken harcanan toplam süreyi gösterir.  
  
### <a name="select-callercallee-view"></a>Arayan/Aranan görünümü seçin  
  
1.  Seçin **çağıran/çağrılan** görünümünde **Geçerli Görünüm** aşağı açılan listesi.  
  
2.  **Çağıran/çağrılan** görünümü, aşağıdaki üç ayrı bölümü vardır:  
  
    -   **Çağıran işlevler**: belirli bir işlevi çağrılan tüm işlevleri görünümün üst kısmında listelenir.  
  
    -   **Geçerli işlev**: çağrıldı olan belirli işlev görünümü orta bölümünde listelenir.  
  
    -   **Tarafından çağrılan işlevler** : belirli bir işlev tarafından çağrılan tüm işlevleri görünümün alt kısmında listelenir.  
  
3.  Adlı bir işlev ise `SyncToNavigator` çağrılan tüm işlevleri görünümü ikinci kısmında görünür `SyncToNavigator` işlevi Görünüm ve tarafından çağrılan tüm işlevler üst kısmında görünür `SyncToNavigator` görünümün alt kısmında görüntülenir.  
  
4.  İşlev görünümü Orta kısmındaki görünümün diğer iki bölümü listelenen işlevlerden herhangi birinin çift tıklayarak değiştirebilirsiniz. Görünüm, daha sonra otomatik olarak değişiklikleri yansıtacak şekilde güncelleştirilir.  
  
5.  Ayrıca, verileri sütun adlarını tıklatarak sıralayabilirsiniz.  
  
### <a name="select-calltree-view"></a>CallTree Görüntüle'yi seçin  
  
1.  Seçin **çağrı ağacı görünümü** içinde **Geçerli Görünüm** aşağı açılan listesi. Bu program yürütme ağaç görünümünü görünümüdür.  
  
2.  **Çağrı ağacı görünümü** işlem adı olarak ağacının kökü gösterir. Ağaç düğümleri işlevlerdir. Bu görünüm belirli çağrı izlemeleri ayrıntıya ve hangi izlemeleri en yüksek performans etkisi analiz sağlar. Görünüm benzer **çağrı yığın görünümü** hata ayıklama sırasında kullanılabilir. Ek sütunları **işlev görünümü**, **çağrı ağacı görünümü**, görüntülenecek ek bir sütun yok **modül adı**.  
  
3.  Seçin **işaretleri** içinde **Geçerli Görünüm** aşağı açılan listesi.  
  
4.  SLT Profiler ile ilişkili bir açıklamayla veri koleksiyonu akışında görünmesini işaretleri vardır. İşaretleri sayaçları sahip kodda yerlerdir. XSLT Profiler XSLT performans sayaçları toplamak için size zaman sayaçları biri bu işaretler, yürütülen her zaman toplanan. Veriler içeren bir tablo görüntülenir **işaret kimliği**, **işareti adı** (**başlangıç programı**, **son Program**) ve  **Zaman damgası**. İşaretleri değil toplanır ve kronolojik sırada görünmesini **işaret görünümü** performans raporu.  
  
### <a name="select-modules-in-the-current-view"></a>Geçerli görünümde modülleri seçin  
  
1.  Seçin **modülleri** içinde **Geçerli Görünüm** aşağı açılan listesi.  
  
2.  Modüller görünümü, tüm işlevler için Modül düzeyinde toplanmış düz listesidir. Genişlet veya daralt görüntülemek veya modül performans verileri görünümü kapatmak için modül adı. Bir sütun adına tıklayarak verileri yeniden sıralayabilirsiniz. Varsayılan olarak mevcuttur hem mutlak değerler hem de yüzde sayılar için **geçen kapsamlı süre**, **geçen dışlamalı süre**, **kapsamlı uygulama süresi**, **Dışlamalı uygulama süresi**, ve **çağrılarını**.  
  
3.  Seçin **işlem** içinde **Geçerli Görünüm** aşağı açılan listesi.  
  
4.  İşlem görünümü içeren bir tablo görüntüler **işlem kimliği**, **işlem adı**, **başlaması zamanı**ve **bitiş zamanı**. Veri sütunu adları tıklayarak sıralanabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yol: XSLT Hiyerarşisi Kullanma](../xml-tools/walkthrough-using-xslt-hierarchy.md)



