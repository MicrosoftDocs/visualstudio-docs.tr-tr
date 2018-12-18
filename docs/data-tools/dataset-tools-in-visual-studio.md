---
title: Veri kümesi araçları
ms.date: 11/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- data-storage
ms.openlocfilehash: 3a8a1ac0f2ac4e4b147fbe11dba8d88ccea4c255
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304993"
---
# <a name="dataset-tools-in-visual-studio"></a>Visual Studio'da veri kümesi araçları

> [!NOTE]
> Veri kümeleri ve ilgili sınıflar, bellekteki verileri veritabanından uygulamaları değilken çalışmak uygulamaları etkinleştirme erken 2000'li yıllardan eski .NET teknolojiden var. Bunlar, kullanıcıların verileri değiştirme ve veritabanına değişiklikleri kalıcı hale getirmek uygulamalar için özellikle yararlıdır. Veri kümeleri çok başarılı bir teknoloji olacak şekilde kanıtlanmış olsa da, yeni .NET uygulamalarını Entity Framework kullanmanızı öneririz. Entity Framework tablosal verileri nesne modellerini olarak çalışmak için daha doğal bir yol sağlar ve daha basit bir programlama arabirimi vardır.

A `DataSet` temelde kısa bir veritabanı olan bellek içi nesne nesnedir. İçerdiği `DataTable`, `DataColumn`, ve `DataRow` nesneleri depolayabilir ve açık bir bağlantı sağlamak zorunda kalmadan bir veya daha fazla veritabanlarındaki verileri değiştirebilirsiniz. Güncelleştirmeleri izlenen ve uygulamanızı bağlandığınızda olur veritabanına geri gönderilen veri kümesi, verilerde yapılan değişiklikleri ilgili bilgileri tutar.

Veri kümeleri ve ilgili sınıflar içinde tanımlanmıştır <xref:System.Data?displayProperty=fullName> .NET Framework sınıf kitaplığındaki ad alanı. Dinamik olarak kod ADO.NET kullanarak veri kümeleri oluşturup düzenleyebilir. Bu bölümdeki belgelere, Visual Studio tasarımcıları kullanarak veri kümeleriyle çalışan işlemi gösterilmektedir. Tasarımcılar kullanarak oluşturulan veri kümelerini **TableAdapter** veritabanıyla etkileşim kurmanıza imkan nesneleri. Program aracılığıyla oluşturulan veri kümelerini kullanan **DataAdapter** nesneleri. Program aracılığıyla veri kümeleri oluşturma hakkında daha fazla bilgi için bkz: [DataAdapters ve DataReaders](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

Uygulamanız yalnızca bir veritabanından verileri okuyamadı ve olmayan güncelleştirmeleri gerçekleştirmek gereken, eklemesi veya silmesi, genellikle daha iyi performans kullanarak alabileceğiniz bir `DataReader` genel verileri almak üzere nesne `List` veya başka bir koleksiyon nesne. Verileri görüntülüyorsa, veri kullanıcı arabirimi koleksiyona bağlama.

## <a name="dataset-workflow"></a>Veri kümesi iş akışı

Visual Studio, veri kümeleri ile çalışmayı kolaylaştırmak için araçlar sağlar. Temel uçtan uca iş akışı şöyledir:

- Kullanım [veri kaynakları penceresi](add-new-data-sources.md#data-sources-window) bir veya daha fazla veri kaynağından yeni bir veri kümesi oluşturmak için. Kullanım **veri kümesi Tasarımcısı** veri kümesini yapılandırma ve özelliklerini ayarlayın. Örneğin, dahil etmek için veri kaynağından tablolar ve her bir tablodaki hangi sütunların belirtmeniz gerekir. Veri kümesi gerektiren bellek miktarını korumak dikkatle seçin. Daha fazla bilgi için [oluşturun ve veri kümeleri yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Tablolar arasında ilişki, yabancı anahtarlar doğru şekilde işlenir böylece belirtin. Daha fazla bilgi için [TableAdapter kullanarak veri kümelerini dolgu](../data-tools/fill-datasets-by-using-tableadapters.md).

- Kullanım **TableAdapter Yapılandırma Sihirbazı'nı** sorgu ya da veri kümesini doldurur saklı yordam belirlemenizi ve uygulamak için hangi veritabanı işlemleri (güncelleştirme, silme vb.). Daha fazla bilgi için şu konulara bakın:

    - [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)

    - [Veri kümelerindeki verileri düzenleme](../data-tools/edit-data-in-datasets.md)

    - [Veri kümelerindeki verileri doğrulama](../data-tools/validate-data-in-datasets.md)

    - [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)

- Sorgu ve veri kümesinde arayın. Daha fazla bilgi için [sorgu veri kümeleri](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] sağlar [LINQ (dil ile tümleşik sorgu)](/dotnet/csharp/linq/) verileri üzerinde bir <xref:System.Data.DataSet> nesne. Daha fazla bilgi için [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

- Kullanım **veri kaynakları** penceresi kullanıcı arabirimi denetimleri, veri kümesi veya tek tek sütunlarını bağlamak için ve hangi sütunların kullanıcı tarafından düzenlenebilir olduğunu belirtmek için. Daha fazla bilgi için [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Veri kümeleri ve N katmanlı mimari

N katmanlı uygulamalarda veri kümeleri hakkında daha fazla bilgi için bkz: [n katmanlı uygulamalarda veri kümeleriyle çalışmak](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Veri kümeleri ve XML

Veri kümeleri ve XML dönüştürme hakkında daha fazla bilgi için bkz: [okuma XML veri kümesine](../data-tools/read-xml-data-into-a-dataset.md) ve [bir veri kümesini XML olarak kaydetme](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)