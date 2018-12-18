---
title: Kod ölçümleri penceresi
ms.date: 12/12/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6aa1de7b3c4a029038072e84bea1918ea33031db
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967174"
---
# <a name="use-the-code-metrics-results-window"></a>Kod ölçümleri sonuçları penceresini kullanma

**Kod ölçümleri sonuçları** penceresi kod ölçümleri analiz tarafından oluşturulan verileri görüntüler. Kod ölçüm verileri değerleri hakkında daha fazla bilgi için bkz: [kod ölçüm değerleri](../code-quality/code-metrics-values.md).

## <a name="display-code-metrics-results"></a>Kod ölçümleri sonuçları görüntüleme

**Kod ölçümleri sonuçları** penceresinde kod ölçümleri sonuçları oluşturduğunuzda otomatik olarak görüntülenir. Ayrıca, herhangi bir zamanda penceresinde görüntüleyebilirsiniz.

Kod ölçümleri sonuçları penceresi şu menü sıraları birini kullanarak görüntüleyebilirsiniz:

- Üzerinde **Çözümle** menüsünde seçin **Windows** > **kod ölçümleri sonuçları**.

- Üzerinde **görünümü** menüsünde seçin **diğer Windows** > **kod ölçümleri sonuçları**.

**Kod ölçümleri sonuçları** sonuç içerse bile penceresi açılır.

### <a name="to-view-code-metrics-details"></a>Kod ölçümleri görüntülemek için ayrıntıları

Kod ölçümleri sonuçları oluşturulduysa ağacında genişletin **hiyerarşi** sütun.

## <a name="filter-code-metrics-results"></a>Kod ölçümleri sonuçları filtresi

Görüntülenen sonuçlarını filtreleyebilirsiniz **kod ölçümleri sonuçları** üstündeki araç çubuğunu kullanarak pencere. Örneğin, bir bakım dizini 65 aşağıda olan sonuçları görmek isteyebilirsiniz.

**Filtre** açılan kutusu sonuçları sütun adlarını içerir. Bir filtre tanımlandığında, listenin bir girinti birlikte eklenir. Liste, tanımlanan son 10 filtreler içerebilir.

### <a name="to-filter-the-code-metrics-results"></a>Kod ölçümleri sonuçları filtrelemek için

1.  Gelen **filtre** listesinde, sütun adı seçin.

2.  İçinde **Min**, görüntülenecek en düşük değerini yazın.

3.  İçinde **Max**, görüntülenecek maksimum değeri yazın.

4.  Tıklayın **Filtre Uygula** düğmesi.

5.  Sonuç ayrıntıları görmek için hiyerarşi ağacı genişletin.

## <a name="add-remove-and-rearrange-data-columns"></a>Eklemek, kaldırmak ve veri sütunları yeniden düzenleme

Ekleyebilir ve sütunları Kaldır sonuçları **kod ölçümleri sonuçları** penceresi. Ayrıca, istediğiniz sırayla görünecekleri sonuçları sütunları yeniden düzenleyebilirsiniz.

### <a name="add-or-remove-a-column"></a>Bir sütun ekleyip

1. Tıklayın **sütunları Ekle/Kaldır** düğmesini veya herhangi bir sütunun başlığına sağ tıklayın ve ardından **sütunları Ekle/Kaldır**.

1. İçinde **sütunları Ekle/Kaldır** iletişim kutusu, seçin veya temizleyin ekleyin veya kaldırın ve ardından istediğiniz sütun için onay kutusunu **Tamam**.

### <a name="rearrange-columns"></a>Sütunları yeniden düzenleme

1. Tıklayın **sütunları Ekle/Kaldır** düğmesi.

1. İçinde **sütunları Ekle/Kaldır** iletişim kutusunda, yukarı veya aşağı oku seçin ve taşımak istediğiniz sütunu seçin.

1. Sütun, istediğiniz yerde konumlandırıldığında seçin **Tamam**.

## <a name="copy-data-to-the-clipboard-or-excel"></a>Pano veya Excel veri kopyalama

Seçin ve seçili bir satır kod ölçümleri verileri, adı ve her veri sütununun değeri için bir satır içeren bir metin dizesi olarak panoya kopyalayın. Ayrıca **Microsoft Excel'de Seçimi Aç** tüm kod ölçümleri sonuçları bir Excel elektronik tablosuna dışarı aktarmak için.

## <a name="create-a-work-item-based-on-code-metric-results"></a>Kod ölçüm sonuçlarına göre iş öğesi oluşturma

Oluşturabileceğiniz bir [Azure panoları](/azure/devops/boards/index?view=vsts) temel alan iş öğesi sonuçlanıyor **kod ölçüm sonuçlarını** penceresi. İş öğesi oluşturulduğunda, Visual Studio otomatik olarak bir başlık girer **başlık** alan ve kod ölçümleri verileri altında **geçmişi** sekmesi.

Azure panoları hakkında daha fazla bilgi için iş öğeleri, bkz: [iş öğelerini](/azure/devops/boards/work-items/index?view=vsts).

### <a name="to-create-a-work-item-based-on-a-result"></a>Bir sonuca bağlı bir iş öğesi oluşturmak için

1.  Bir sonuca sağ tıklayın.

2.  İşaret **iş öğesi oluştur**ve ardından oluşturmak istediğiniz iş öğesinin türüne tıklayın (**hata**, **görev**, vb.).

3.  Tüm gerekli alanları doldurarak iş öğesi formu tamamlayın.

4.  Üzerinde **dosya** menüsünde tıklatın **Tümünü Kaydet** iş öğesini kaydetmek için.

### <a name="to-create-a-bug-based-on-a-result"></a>Bir sonuca bağlı bir hata oluşturmak için

1.  Seçmek için sonuca tıklayın.

2.  Tıklayın **iş öğesi oluşturma** düğmesi.

3.  Tüm gerekli alanları doldurarak iş öğesi formu tamamlayın.

4.  Üzerinde **dosya** menüsünde tıklatın **Tümünü Kaydet** iş öğesini kaydetmek için.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod ölçüm değerleri](../code-quality/code-metrics-values.md)
- [Nasıl yapılır: kod ölçümleri verileri üretme](../code-quality/how-to-generate-code-metrics-data.md)