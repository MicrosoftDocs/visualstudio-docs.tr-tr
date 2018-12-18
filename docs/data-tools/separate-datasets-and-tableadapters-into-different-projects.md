---
title: Veri kümeleri ile TableAdapter’ları farklı projelere ayırma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 01e572a2ac20d1cfb103e1600307b51bdf58a0b8
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174325"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Veri kümeleri ile TableAdapter’ları farklı projelere ayırma
Türü belirtilmiş datasets Gelişmiş böylece [TableAdapters](create-and-configure-tableadapters.md) ve veri kümesi sınıfları ayrı projelere oluşturulabilir. Bu, hızla uygulama katmanları ayırmak ve n katmanlı veri uygulamaları oluşturmak sağlar.

Aşağıdaki yordamda kullanma işlemi açıklanmaktadır **veri kümesi Tasarımcısı** oluşturulan TableAdapter kodunu içeren projeden farklı bir projeye veri kümesi kodunu oluşturmak için.

## <a name="separate-datasets-and-tableadapters"></a>Ayrı veri kümeleri ve TableAdapters öğelerini
Veri kümesi kodunu TableAdapter koddan ayırdığınızda, veri kümesi kodunu içeren projenin geçerli çözümde bulunması gerekir. Bu projenin geçerli çözümde yer almıyorsa, kullanılabilir olmayacaktır **DataSet projesi** listesinde **özellikleri** penceresi.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Farklı bir projeye veri kümesini ayırmak için

1.  Bir veri kümesini içeren bir çözüm açın (*.xsd* dosyası).

    > [!NOTE]
    >  Veri kümesi kodunuzu ayırmak istediğiniz proje çözüm içermiyorsa, projeyi oluşturmak veya mevcut bir projeyi çözüme ekleyin.

2.  Türü belirtilmiş veri kümesi dosyasına çift tıklayın (bir *.xsd* dosya) içinde **Çözüm Gezgini** açmak için **veri kümesi Tasarımcısı**.

3.  Boş bir alanı seçin **veri kümesi Tasarımcısı**.

4.  İçinde **özellikleri** penceresinde bulun **DataSet projesi** düğümü.

5.  İçinde **DataSet projesi** listesinde, istediğiniz veri kümesi kodunu oluşturmak proje adını seçin.

     Veri kümesi kodunu oluşturmak istediğiniz projeyi seçin sonra **veri kümesi dosyası** özelliği, bir varsayılan dosya adıyla doldurulur. Gerekirse, bu adı değiştirebilirsiniz. Ayrıca, belirli bir dizine veri kümesi kodunu oluşturmak istiyorsanız, ayarlayabileceğiniz **proje klasörü** özelliğini bir klasörün adı.

    > [!NOTE]
    >  Veri kümelerini ve TableAdapter bağdaştırıcılarını ayırdığınızda (ayarlayarak **DataSet projesi** özelliği), projedeki varolan kısmi veri kümesi sınıfları olmaz taşınması otomatik olarak. Varolan kısmi veri kümesi sınıfları, veri kümesi projesine el ile taşınmalıdır.

6.  Veri kümesini kaydetme.

     Veri kümesi kod içinde seçilen projede oluşturulur **DataSet projesi** özelliği ve **TableAdapter** kod, geçerli projenin içine oluşturulur.

Veri kümesini ve TableAdapter kodunu ayırdıktan sonra varsayılan olarak, her proje bir parçalı sınıf dosyasında sonucudur. Adlı bir dosya özgün proje sahip *DatasetName.Designer.vb* (veya *DatasetName.Designer.cs*), TableAdapter kodunu içerir. İçinde belirtilen projeyi **Dataset projesi** özelliği adlı bir dosya var *DatasetName.DataSet.Designer.vb* (veya *DatasetName.DataSet.Designer.cs*), veri kümesi kodunu içerir.

> [!NOTE]
>  Oluşturulan sınıf dosyayı görüntülemek için veri kümesi veya TableAdapter projesini seçin. Ardından **Çözüm Gezgini**seçin **tüm dosyaları göster**.

## <a name="see-also"></a>Ayrıca bkz.

- [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md)
- [İzlenecek yol: bir N katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)
- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)