---
title: 'İzlenecek Yol: XSLT Profil Oluşturucusu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 14abf52e65a796325d4af8bd95f5434c105c3fa3
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693805"
---
# <a name="walkthrough-xslt-profiler"></a>İzlenecek Yol: XSLT Profil Oluşturucusu

XSLT profil oluşturucu ölçü Yardım, değerlendirmek ve performans ile ilgili sorunlar XSLT kodda hedef ayrıntılı XSLT performans raporları oluşturur. XSLT profil oluşturucu yararlı ipuçları XSL ve XSLT stil sayfası iyileştirmeler içerir. XSLT uygulamaları için isteğe bağlı en yüksek performans, bu aracı gerekli olabilir.

## <a name="prerequisites"></a>Önkoşullar

Aşağıdaki örneklerde yordamlarda, Visual Studio ve .NET Framework sürüm 4.0 veya üstünü gerektirir.

### <a name="create-the-performance-report"></a>Performans raporu oluşturma

1.  XSLT belge Visual Studio'da açın.

2.  Tıklayın **profil XSLT** bulunan XML menü seçeneği.

3.  Giriş XML belgesi sağlar. Bir XML belgesi açık değilse, dosya için istenir.

4.  Analiz başlatır, ve bir ilerleme çubuğu Düzenleyicisi içinde ilerleme durumunu görüntüler.

5.  XSLT çıkış çıkış Bölmesi'nde görünür olur.

6.  Bir performans oturumu sona erdikten sonra performans raporu denetleyin. Bir performans raporu kaydedilen verileri görüntülemek ve XSLT performansını çözümlemek sağlar.

### <a name="get-all-the-available-views"></a>Tüm kullanılabilir görünümleri Al

1.  Tıklayın **Geçerli Görünüm** kullanılabilen tüm görünümleri almak için aşağı açılan liste.

2.  Seçin **özeti görünümü** seçeneğini **Geçerli Görünüm** aşağı açılan liste. Varsayılan olarak, bir performans raporu görüntülenen **özeti görünümü**. Bu görünüm, XSLT belgelerle performans sorunlarını belirlemek için bir başlangıç noktasıdır. **Özeti görünümü** aşağıdaki veri noktaları listeler:

    -   En çağrılan işlevleri

    -   Ayrı ayrı çoğu iş işlevleri

    -   Yürütmek için uzun zaman ayırdığınız işlevleri

3.  Varsayılan olarak, her veri noktası için üç sütun bulunur: adını işlevi, mutlak değeri çağrılarının sayısı ve toplam işlev çağrıları için adlandırılmış işlevinin bir yüzde değeri. Her veri noktası **özeti görünümü**, daha ayrıntılı görünümler işlevi veri noktalarında sağ tıklayarak gidebilirsiniz.

4.  Seçin **işlev görünümü** seçeneğini **Geçerli Görünüm** aşağı açılan liste. **İşlev görünümü** profil oluşturma sırasında çağrılan işlevler listeler. Verileri bir sütun adı tıklayarak sıralayabilirsiniz. Varsayılan olarak görüntülenen sütunları şunlardır:

    -   **İşlev adı**

    -   **Geçen dahil süre**

    -   **Geçen özel süre**

    -   **Uygulama dahil süresi**

    -   **Uygulama özel süresi**

    -   **Çağrı sayısı**

5.  Tüm saat sütunları mutlak değerler ve yüzde görüntülenir. Terim **özel** diğer işlevleri tarafından harcanan süre dışlayacak biçimde geçen yürütme adında bu işlev yürütülmesi sırasında bir işlevi için toplam süreyi gösterir.

6.  Terim **Inclusive** adlı ve diğer işlevleri olarak adlandırılan bu işlevler adlı herhangi bir işlev, yürütme süresini de dahil olmak üzere tüm işlevleri yürütülen toplam zamanın başvuruyor.

### <a name="select-callercallee-view"></a>Arayan/Aranan görünümü seçin

1.  Seçin **arayan/Aranan** görünümünde **Geçerli Görünüm** aşağı açılan liste.

2.  **Arayan/Aranan** görünümü aşağıdaki üç farklı bölümden vardır:

    -   **Adlı işlevleri**: belirli bir işlev adı verilen tüm işlevleri görünümü üst kısmından listelenir.

    -   **Geçerli işlevi**: çağrıldı belirli işlevi görünümü orta bölümünde listelenir.

    -   **Adı veriliyordu tarafından işlevleri** : belirli bir işlev tarafından çağrılan tüm işlevleri görünümü alt kısmından listelenir.

3.  Bir işlev adlandırırsanız `SyncToNavigator` adlı tüm işlevleri görünümü orta bölümünde görünür `SyncToNavigator` işlevi görünür Görünüm ve adı veriliyordu tarafından tüm işlevler üst kısmında `SyncToNavigator` görünüm alt kısmında görüntülenir.

4.  Görünümün Orta parçası işlevinde herhangi diğer iki bölümden görünümü içinde listelenen işlevlerden çift tıklatarak değiştirebilirsiniz. Görünüm sonra otomatik olarak değişiklikleri yansıtacak şekilde güncelleştirilir.

5.  Sütun adları tıklayarak veri daha da sıralayabilirsiniz.

### <a name="select-call-tree-view"></a>Çağrı ağacı görünümü seçin

1.  Seçin **çağrı ağacı görünümü** içinde **Geçerli Görünüm** aşağı açılan liste. Bu görünüm, program yürütme ağacı görünümdür.

2.  **Çağrı ağacı görünümü** işlem adı olarak ağacının kökü gösterir. Ağaç düğümleri işlevlerdir. Bu görünüm, belirli arama izlemeleri ayrıntıya ve hangi izlemeleri en yüksek performans etkisi çözümlemek sağlar. Görünüm benzer **çağrı yığını Görünüm** hata ayıklama sırasında kullanılabilir. Sütunları yanı sıra **işlev görünümü**, **çağrı ağacı görünümü**, görüntülemek için ek bir sütun **modül adı**.

3.  Seçin **işaretleri** içinde **Geçerli Görünüm** aşağı açılan liste.

4.  SLT Profil Oluşturucu ile ilişkili bir açıklamayı içeren veri toplama akışında görünmesini işaretleri vardır. İşaretleri sayaçları sahip Code yerlerdir. XSLT performans sayaçları toplanamadı XSLT profil oluşturucu söyleyin olduğunda bu işaretlerinden birini yürütülen her zaman sayaçları toplanan. Veriler içeren bir tabloda görüntülenir **işareti kimliği**, **işareti adı** (**Başlat Program**, **Program sonlandırma**) ve  **Zaman damgası**. İşaretleri değil toplanır ve kronolojik sırada görünmesini **işaretleri Görünüm** performans raporu.

### <a name="select-modules-in-the-current-view"></a>Geçerli görünümde modül seçin

1.  Seçin **modülleri** içinde **Geçerli Görünüm** aşağı açılan liste.

2.  Modüller görünümü modül düzeyi toplanan tüm işlevleri düz bir listesidir. Genişlet veya daralt görüntülemek veya modül performans verileri görünümü kapatmak için modül adı. Verileri bir sütun adı tıklayarak sıralayabilirsiniz. Varsayılan olarak, vardır hem mutlak değerler hem de yüzde sayılar için **geçen dahil süre**, **geçen özel zaman**, **uygulama dahil süresi**, **Uygulama özel süresi**, ve **çağrı sayısı**.

3.  Seçin **işlem** içinde **Geçerli Görünüm** aşağı açılan liste.

4.  İşlem görünümü içeren bir tablo görüntüler **işlem kimliği**, **işlem adı**, **başlaması zamanı**ve **bitiş zamanı**. Veri sütunu adları tıklayarak sıralanabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: XSLT hiyerarşi kullanma](../xml-tools/walkthrough-using-xslt-hierarchy.md)