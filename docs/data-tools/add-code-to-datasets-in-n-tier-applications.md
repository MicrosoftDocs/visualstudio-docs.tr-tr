---
title: N katmanlı uygulamalarda veri kümelerine kod ekleme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e4c5fbbbe878e14c6c88c872ece2b3d492e3ea7c
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844039"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>N katmanlı uygulamalarda veri kümelerine kod ekleme
Veri kümesi için bir parçalı sınıf dosya oluşturarak ve kod eklemeyi dataset işlevselliğini genişletebilirsiniz (kod eklemek yerine *DatasetName*. Dataset.Designer dosyası). Kısmi sınıflar arasında birden çok fiziksel dosya bölünür için belirli bir sınıf için kod etkinleştirin. Daha fazla bilgi için bkz: [kısmi](/dotnet/visual-basic/language-reference/modifiers/partial) veya [kısmi sınıflar ve yöntemler](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

Veri kümesi tanımında (türü belirtilmiş veri kümesi) yapılan bir değişiklik her zaman bir veri kümesini tanımlamaktadır kodu oluşturulur. Herhangi bir veri kümesinin yapılandırmayı değiştiriyorsa Sihirbazı'nı çalıştırma sırasında değişiklik yaptığınızda bu kodu aynı zamanda oluşturulur. Kodunuzu bir veri kümesini yeniden oluşturma işlemi sırasında silinmesini engellemek için veri kümesi'nin parçalı sınıf dosyasına kodu ekleyin.

TableAdapter kod ve veri kümesi ayrı sonra varsayılan olarak, her proje ayrık sınıf dosyasında sonucudur. Özgün proje adlı bir dosya var *DatasetName.Designer.vb* (veya *DatasetName.Designer.cs*) TableAdapter kodunu içerir. İçinde belirtilen proje **Dataset projesi** özelliğinin adlı bir dosyayı *DatasetName.DataSet.Designer.vb* (veya *DatasetName.DataSet.Designer.cs*) . Bu dosya veri kümesi kodunu içerir.

> [!NOTE]
>  Ne zaman, ayrı veri kümeleri ve TableAdapters öğelerini (ayarlayarak **DataSet projesi** özelliği), projedeki mevcut kısmi veri kümesi sınıflarını olmaz taşınabilir otomatik olarak. Mevcut veri kümesini kısmi sınıflar el ile dataset projesi taşınması gerekir.

> [!NOTE]
>  Doğrulama kodu eklenmesi gerektiğinde türü belirtilmiş veri kümesi oluşturmak için işlevsellik sağlar <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.RowChanging> olay işleyicileri. Daha fazla bilgi için bkz: [n katmanlı veri kümesine doğrulama ekleme](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>N katmanlı uygulamalarda veri kümelerine kod eklemek için

1.  İçeren projeye bulun *.xsd* dosya.

2.  Seçin **.xsd** dosyayı dataset açın.

3.  Kodu (tablo adı başlık çubuğunda) ekleyin ve ardından istediğiniz veri tablosu sağ **görünümü kodu**.

     Bir parçalı sınıf oluşturulur ve Kod Düzenleyicisi'nde açar.

4.  Parçalı sınıf bildirimi içinde kodu ekleyin.

     Aşağıdaki örnek, CustomersDataTable NorthwindDataSet olarak kod ekleme yeri gösterir:

    ```vb
    Partial Public Class CustomersDataTable
        ' Add code here to add functionality
        ' to the CustomersDataTable.
    End Class
    ```
    ```csharp
    partial class CustomersDataTable
    {
        // Add code here to add functionality
        // to the CustomersDataTable.
    }
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [n katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md)
- [N katmanlı uygulamalarda TableAdapter’lara kod ekleme](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [TableAdapter’lar oluşturma ve yapılandırma](create-and-configure-tableadapters.md)
- [Hiyerarşik güncelleştirmeye genel bakış](hierarchical-update.md)
- [Visual Studio'da veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)