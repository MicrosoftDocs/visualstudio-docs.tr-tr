---
title: Oluşturma ve veri kümelerini yapılandırma
ms.date: 11/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- data-storage
ms.openlocfilehash: 23837bcfb1d3761f8ebf23020c15e901833d63b3
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305228"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Visual Studio’da veri kümeleri oluşturma ve yapılandırma

Bellekte bir veritabanından veri depolayan ve etkinleştirmek için değişiklik izlemeyi destekleyen bir nesne oluşturma bir veri kümesi olduğundan, okuma, güncelleştirme ve silme (CRUD) işlemleri veritabanına her zaman bağlı gerek kalmadan bu verileri. Veri kümeleri, basit için tasarlanmış *veriler üzerinden formlar* iş uygulamaları. Yeni uygulamalar için bellekteki verileri depolamak ve modellemek için Entity Framework kullanarak göz önünde bulundurun. Veri kümeleriyle çalışmak için veritabanı kavramlarını temel bilgiye sahip olmalıdır.

Oluşturabileceğiniz bir türü belirtilmiş <xref:System.Data.DataSet> Visual Studio'da bir sınıf kullanarak tasarım zamanında **veri kaynağı Yapılandırma Sihirbazı**. Program aracılığıyla veri kümeleri oluşturma hakkında daha fazla bilgi için bkz: [(ADO.NET) veri kümesi oluşturma](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Veri Kaynağı Yapılandırma Sihirbazı'nı kullanarak yeni bir veri kümesi oluşturma

1. Projenizi Visual Studio'da açın ve ardından **proje** > **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı Yapılandırma Sihirbazı**.

2. Bağlanmakta, veri kaynağı türü seçin.

     ![Veri Kaynağı Yapılandırma Sihirbazı](../data-tools/media/data-source-configuration-wizard.png)

3. Veritabanını veya veri kaynağı, veri kümesi için olan veritabanlarını seçin.

     ![Veri kaynağı bağlantısı seçin](../data-tools/media/data-source-choose-a-connection.png)

4. Tablolar (veya tek tek sütun) depolanan yordamları, işlevleri ve görünümleri kümesinde temsil edilmesini istediğiniz veritabanını seçin.

     ![Veritabanı nesneleri seçin](../data-tools/media/raddata-chose-objects.png)

5. **Son**'a tıklayın.

   Veri kümesine bir düğüm olarak görünür **Çözüm Gezgini**.

   ![Çözüm Gezgini'nde veri kümesi](../data-tools/media/dataset-in-solution-explorer.png)

6. Veri kümesi düğümünde tıklayın **Çözüm Gezgini** açmak için **veri kümesi Tasarımcısı**. Her veri kümesinde ilişkili bir tablolu `TableAdapter` alt kısmında gösterilen nesnesidir. Tablo bağdaştırıcısı DataSet'i doldurmak için ve isteğe bağlı olarak komut veritabanına göndermek için kullanılır.

   ![Veri kümesi Tasarımcısı](../data-tools/media/dataset-designer.png)

7. Tabloları bağlanan ilişkisi satırları tablo ilişkileri veritabanında tanımlanan temsil eder. Varsayılan olarak, bir veritabanındaki yabancı anahtar kısıtlamaları yalnızca bir ilişki güncelleştirme ile temsil edilir ve yok olarak ayarlanmış kuralları silin. Genellikle, istediğiniz olmasıdır. Ancak, ortaya çıkarmak için satırları tıklayabilirsiniz **ilişkisi** iletişim kutusunda, sıradüzensel güncellemeleri davranışını değiştirebileceğiniz. Daha fazla bilgi için [veri kümelerindeki ilişkiler](../data-tools/relationships-in-datasets.md) ve [hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md).

     ![Veri kümesi ilişkisi iletişim](../data-tools/media/raddata-relation-dialog.png)

8. Tablo, tablo bağdaştırıcısı veya bir tablodaki sütun adı özelliklerini görmek için tıklayın **özellikleri** penceresi. Bazı değerler burada değiştirebilirsiniz. Yalnızca veri kümesi, kaynak veritabanı değiştirmekte olduğunuz unutmayın.

     ![Veri kümesi sütun özellikleri](../data-tools/media/dataset-column-properties.png)

9. Yeni Tablo veya tablo bağdaştırıcıları veri kümesine ekleyebilir veya var olan tablo bağdaştırıcıları için yeni sorgular eklemek veya bu öğeleri sürükleyerek tablolar arasında yeni ilişkiler belirtin **araç kutusu** sekmesi. Bu sekme görüntülenir **veri kümesi Tasarımcısı** odakta olan.

     ![Veri kümesi araç kutusu](../data-tools/media/raddata-dataset-toolbox.png)

Ardından, veri kümesini verilerle doldurmak nasıl belirtmek isteyebilirsiniz. Bunun için kullandığınız **TableAdapter Yapılandırma Sihirbazı'nı**. Daha fazla bilgi için [TableAdapter kullanarak veri kümelerini dolgu](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Varolan bir veri kümesi için bir veritabanı tablosu veya diğer nesne Ekle

Bu yordamda, ilk veri kümesini oluşturmak için kullanılan aynı veritabanından tablo ekleme gösterilmiştir.

1. Veri kümesi düğümünde tıklayın **Çözüm Gezgini** getirilecek **veri kümesi Tasarımcısı** odaklanır.

2. Tıklayın **veri kaynakları** sekmesinde Visual Studio veya türü sol kenar boşluğunda **veri kaynakları** içinde **hızlı başlatma** kutusu.

3. Veri kümesi düğümüne sağ tıklayıp **veri kaynağı Yapılandırma Sihirbazı'nı**.

     ![Veri kaynağı bağlam menüsü](../data-tools/media/data-source-context-menu.png)

4. Ek tabloları, saklı yordamları ya da diğer veritabanı nesneleri veri kümesine eklenecek belirtmek için bu sihirbazı kullanın.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Tek başına veri tablosu ekleme

1. Kümenizde açın **veri kümesi Tasarımcısı**.

2. Sürükleme bir <xref:System.Data.DataTable> gelen sınıfı **veri kümesi** sekmesinde **araç kutusu** üzerine **veri kümesi Tasarımcısı**.

3. Veri tablosu tanımlamak için sütunları ekleyin. Tabloyu sağ tıklatın ve seçin **Ekle** > **sütun**. Kullanım **özellikleri** gerekirse sütunu ve bir anahtar veri türünü ayarlamak için penceresi.

Tek başına tabloları uygulamak için gereken `Fill` mantığı tek başına tablolar, böylece bunları verilerle doldurabilirsiniz. Tek başına veri tablolarını doldurmak hakkında daha fazla bilgi için bkz: [dataadapter'dan bir DataSet doldurma](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
- [Veri kümelerindeki ilişkiler](../data-tools/relationships-in-datasets.md)
- [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)
- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)