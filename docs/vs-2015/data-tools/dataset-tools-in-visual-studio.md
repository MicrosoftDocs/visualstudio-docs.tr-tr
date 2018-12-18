---
title: Veri kümesi araçları
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.data.DataSet
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- untyped datasets
- datasets [Visual Basic], extended properties
- typed datasets
- current record in dataset
- XML [Visual Basic], datasets
- DataSet class, about datasets
- unique constraints (datasets)
- data relationships
- parent records in datasets
- extended properties, in typed datasets
- datasets [Visual Basic]
- schemas [Visual Basic], datasets
- datasets [Visual Basic], msprop
- master-detail tables, datasets
- databases [Visual Basic], updating
- msprop
- foreign keys, datasets
- DataSet class
- datasets [Visual Basic], filling
- case sensitivity, datasets
- constraints [Visual Basic], datasets
- child records
- related tables, datasets
- updating datasets, about dataset updates
- data caching, datasets
- DataRelation object, datasets
- untyped datasets, compared to typed datasets
- cache [Visual Studio], datasets
- datasets [Visual Basic], relationships
- related tables
- XML schemas, about XML schemas and datasets
- relationships, datasets
- typed datasets, compared to untyped datasets
- datasets [Visual Basic], populating
- datasets [Visual Basic], namespace
- data adapters, populating datasets
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bc15e9e683a56e1cba2a8747efd15f4c09f8441c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058200"
---
# <a name="dataset-tools-in-visual-studio"></a>Visual Studio'da veri kümesi araçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


[NOT]
>  Veri kümeleri ve ilgili sınıflar, bellekteki verileri veritabanından uygulamaları değilken çalışmak uygulamaları etkinleştirme erken 2000'li yıllardan eski .NET teknolojiden var. Bunlar, kullanıcıların verileri değiştirme ve veritabanına değişiklikleri kalıcı hale getirmek uygulamalar için özellikle yararlıdır. Veri kümeleri çok başarılı bir teknoloji olacak şekilde kanıtlanmış olsa da, yeni .NET uygulamalarını Entity Framework kullanmanızı öneririz. Entity Framework tablosal verileri nesne modellerini olarak çalışmak için daha doğal bir yol sağlar ve daha basit bir programlama arabirimi vardır.

 Bir veri kümesi nesnesi temelde kısa bir veritabanı olan bir bellek içi nesnedir. Bu, depolayabilir ve açık bir bağlantı korumak zorunda kalmadan bir veya daha fazla veritabanlarındaki verileri değiştirme DataTable ve DataColumn DataRow nesnelerini içerir. Güncelleştirmeleri izlenen ve uygulamanızı bağlandığınızda olur veritabanına geri gönderilen veri kümesi, verilerde yapılan değişiklikleri ilgili bilgileri tutar.

 Veri kümeleri ve ilgili sınıflar, .NET Framework sınıf kitaplığındaki System.Data ad alanında tanımlanır. Dinamik olarak kod içinde veri kümeleri oluşturup düzenleyebilir. ADO.NET bunu nasıl yapacağınız hakkında daha fazla bilgi için bkz. Bu bölümdeki belgelere, Visual Studio tasarımcıları kullanarak veri kümeleriyle çalışan işlemi gösterilmektedir. Bilmeniz gereken bir şey: tasarımcıları yapılan veri kümelerini kullanan TableAdapter nesneleri veritabanıyla etkileşim kurmanıza imkan program aracılığıyla yapılan veri kümeleri DataAdapter nesneleri kullanmasa. Program aracılığıyla veri kümeleri oluşturma hakkında daha fazla bilgi için bkz: [DataAdapters ve DataReaders](http://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74).

 Uygulamanız yalnızca bir veritabanından verileri okuyamadı ve olmayan güncelleştirmeleri gerçekleştirmek gereken, eklemesi veya silmesi, genel bir liste nesnesi veya başka bir koleksiyon nesnesi içinde veri almak için bir DataReader nesnesi kullanarak, genellikle daha iyi performans alabilirsiniz. Verileri görüntülüyorsa, veri kullanıcı arabirimi koleksiyona bağlama.

## <a name="dataset-workflow"></a>Veri kümesi iş akışı
 Visual Studio, çok sayıda veri kümeleri ile çalışmayı kolaylaştırmak için araçlar sağlar. Temel uçtan uca iş akışı şöyledir:

-   Kullanım **veri kaynağı** bir veya daha fazla veri kaynağından yeni bir veri kümesi oluşturmak için pencere. Kullanım **veri kümesi Tasarımcısı** veri kümesini yapılandırma ve özelliklerini ayarlayın. Örneğin, dahil etmek için veri kaynağından tablolar ve her bir tablodaki hangi sütunların belirtmeniz gerekir. Veri kümesi gerektiren bellek miktarını korumak dikkatle seçin. Daha fazla bilgi için [oluşturun ve veri kümeleri yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md).

-   Tablolar arasında ilişki, yabancı anahtarlar doğru şekilde işlenir böylece belirtin. Daha fazla bilgi için [TableAdapter kullanarak veri kümelerini dolgu](../data-tools/fill-datasets-by-using-tableadapters.md).

-   Kullanım **TableAdapter Yapılandırma Sihirbazı'nı** sorgu ya da veri kümesini doldurur saklı yordam belirlemenizi ve uygulamak için hangi veritabanı işlemleri (güncelleştirme, silme vb.). Daha fazla bilgi için şu konulara bakın:

    -   [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)

    -   [Veri kümelerindeki verileri düzenleme](../data-tools/edit-data-in-datasets.md)

    -   [Veri kümelerindeki verileri doğrulama](../data-tools/validate-data-in-datasets.md)

    -   [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)

-   Sorgu ve veri kümesinde arayın. Daha fazla bilgi için [sorgu veri kümeleri](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] sağlar [LINQ (dil ile tümleşik sorgu)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) verileri üzerinde bir <xref:System.Data.DataSet> nesne. Daha fazla bilgi için [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).

-   Kullanım **veri kaynakları** penceresi kullanıcı arabirimi denetimleri, veri kümesi veya tek tek sütunlarını bağlamak için ve hangi sütunların kullanıcı tarafından düzenlenebilir olduğunu belirtmek için. Daha fazla bilgi için [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Veri kümeleri ve N katmanlı mimari
 N katmanlı uygulamalarda veri kümeleri hakkında daha fazla bilgi için bkz: [n katmanlı uygulamalarda veri kümeleriyle çalışmak](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Veri kümeleri ve XML
 Veri kümeleri ve XML dönüştürme hakkında daha fazla bilgi için bkz: [okuma XML veri kümesine](../data-tools/read-xml-data-into-a-dataset.md) ve [bir veri kümesini XML olarak kaydetme](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
