---
title: Oluşturma ve veri kümelerini yapılandırma
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- typed datasets, creating
- datasets [Visual Basic], creating
ms.assetid: 58f33b43-24e1-43b1-b08b-b74329960bd6
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 33b272143c58058d23945986ea9b6594183307c9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065216"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Visual Studio’da veri kümeleri oluşturma ve yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


A *veri kümesi* bellekte bir veritabanından veri depolayan ve etkinleştirmek için değişiklik izleme desteği nesneleri bir dizi oluşturma, okuma, güncelleştirme ve silme (CRUD) işlemleri veritabanına her zaman bağlı gerek kalmadan bu verileri. Veri kümeleri, basit için tasarlanmış *veriler üzerinden formlar* iş uygulamaları. Yeni uygulamalar için bellekteki verileri depolamak ve modellemek için Entity Framework kullanarak göz önünde bulundurun. Veri kümeleriyle çalışmak için veritabanı kavramlarını temel bilgiye sahip olmalıdır.

 Bir türü belirtilmiş oluşturduğunuz <xref:System.Data.DataSet> Visual Studio'da bir sınıf kullanarak tasarım zamanında **veri kaynağı Yapılandırma Sihirbazı**. Program aracılığıyla veri kümeleri oluşturma hakkında daha fazla bilgi için bkz: [bir veri kümesi oluşturma](http://msdn.microsoft.com/library/57629d8f-393e-4677-8b83-29ffde27f5fc).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Veri Kaynağı Yapılandırma Sihirbazı'nı kullanarak yeni bir veri kümesi oluşturma

1.  Üzerinde **proje** menüsünü tıklatın **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı Yapılandırma Sihirbazı**.

2.  İçin bağlanırsınız veri kaynağı türü seçin.

     ![Veri Kaynağı Yapılandırma Sihirbazı'nı](../data-tools/media/data-source-configuration-wizard.png "veri kaynağı Yapılandırma Sihirbazı")

3.  Veritabanları için veritabanı veya veri kaynağı, veri kümesi için olan veritabanlarını seçin.

     ![Veri kaynağı bağlantısı seçin](../data-tools/media/data-source-choose-a-connection.png "veri kaynağı bağlantısı seçin")

4.  Tablolar (veya tek tek sütun) depolanan yordamları, işlevleri ve görünümleri kümesinde temsil edilmesini istediğiniz veritabanını seçin.

     ![Veritabanı nesneleri seçmenizi](../data-tools/media/raddata-chose-objects.png "raddata seçtiğiniz nesneleri")

5.  **Son**'a tıklayın.

6.  Veri kümesine bir düğüm olarak görünür **Çözüm Gezgini**:

     ![Çözüm Gezgini'nde DataSet](../data-tools/media/dataset-in-solution-explorer.png "Çözüm Gezgini'nde veri kümesi")

     Bu düğüme tıklayın ve veri kümesi görünür **veri kümesi Tasarımcısı**. Her veri kümesi tablosunda alt kısmında gösterilen bir ilişkili TableAdapter nesnesi olduğuna dikkat edin. Tablo bağdaştırıcısı DataSet'i doldurmak için ve isteğe bağlı olarak komut veritabanına göndermek için kullanılır.

     ![Veri kümesi Tasarımcısı](../data-tools/media/dataset-designer.png "veri kümesi Tasarımcısı")

7.  Tabloları bağlanan ilişkisi satırları tablo ilişkileri veritabanında tanımlanan temsil eder. Varsayılan olarak, bir veritabanındaki yabancı anahtar kısıtlamaları yalnızca bir ilişki güncelleştirme ile temsil edilir ve yok olarak ayarlanmış kuralları silin. Genellikle, istediğiniz olmasıdır. Ancak, ortaya çıkarmak için satırları tıklayabilirsiniz **ilişkisi** iletişim kutusunda, sıradüzensel güncellemeleri davranışını değiştirebileceğiniz. Daha fazla bilgi için [veri kümelerindeki ilişkiler](../data-tools/relationships-in-datasets.md) ve [hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md).

     ![Veri kümesi ilişkisi iletişim](../data-tools/media/raddata-relation-dialog.png "raddata ilişkisi iletişim")

8.  Tablo, tablo bağdaştırıcısı veya bir tablodaki sütun adı özelliklerini görmek için tıklayın **özellikleri** penceresi. Bazı değerler burada değiştirebilirsiniz. Yalnızca veri kümesi, kaynak veritabanı değiştirmekte olduğunuz unutmayın.

     ![Veri kümesi sütunu özellikleri](../data-tools/media/dataset-column-properties.png "veri kümesi sütun özellikleri")

9. Yeni Tablo veya tablo bağdaştırıcıları veri kümesine ekleyebilir veya var olan tablo bağdaştırıcıları için yeni sorgular eklemek veya bu öğeleri sürükleyerek tablolar arasında yeni ilişkiler belirtin **araç kutusu** sekmesi. Bu sekme görüntülenir **veri kümesi Tasarımcısı** odakta olan.

     ![Veri kümesi araç kutusu](../data-tools/media/raddata-dataset-toolbox.png "raddata veri kümesi araç kutusu")

10. Ardından, büyük olasılıkla veri kümesini verilerle doldurmak nasıl belirtmek isteyebilirsiniz. Bunun için kullandığınız **TableAdapter Yapılandırma Sihirbazı'nı**. Daha fazla bilgi için [TableAdapter kullanarak veri kümelerini dolgu](../data-tools/fill-datasets-by-using-tableadapters.md) .

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Varolan bir veri kümesi için bir veritabanı tablosu veya diğer nesne Ekle
 Bu yordamda, ilk veri kümesini oluşturmak için kullanılan aynı veritabanından tablo ekleme gösterilmiştir.

1.  Veri kümesi düğümünde tıklayın **Çözüm Gezgini** veri kümesi Tasarımcısı ile odaklanmak için.

2.  Tıklayın **veri kaynakları** sekmesinde Visual Studio'nun sol kenar boşluğunda veya girin `Data Sources` içinde **hızlı başlatma**.

3.  Veri kümesi düğümüne sağ tıklayıp **veri kaynağı Yapılandırma Sihirbazı'nı** .

     ![Veri kaynağı bağlam menüsü](../data-tools/media/data-source-context-menu.png "veri kaynağı bağlam menüsü")

4.  Sihirbaz, hangi ek tablolar veya saklı yordamları veya veri kümesine eklemek için diğer veritabanı nesnesi belirtmek için kullanın.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Tek başına veri tablosu ekleme

1.  Kümenizde açın **veri kümesi Tasarımcısı**.

2.  Sürükleme bir <xref:System.Data.DataTable> gelen sınıfı **veri kümesi** sekmesinde **araç kutusu** üzerine **veri kümesi Tasarımcısı**.

3.  Veri tablosu tanımlamak için sütunları ekleyin. Daha fazla bilgi için [nasıl yapılır: bir DataTable sütunları ekleme](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).

4.  Tek başına tabloları uygulamak için gereken `Fill` mantığı tek başına tablolar, böylece bunları verilerle doldurabilirsiniz. Tek başına veri tablolarını doldurmak hakkında daha fazla bilgi için bkz: [dataadapter'dan bir DataSet doldurma](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).
