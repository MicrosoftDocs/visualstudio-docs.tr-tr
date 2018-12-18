---
title: N katmanlı uygulamalarda TableAdapter’lara kod ekleme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e5a9aad4aaecb629f5860fadf56e35a55455be63
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38783096"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>N katmanlı uygulamalarda TableAdapter’lara kod ekleme
TableAdapter için bir parçalı sınıf dosyası oluşturarak ve kodu eklemeden bir TableAdapter işlevini genişletme (kod eklemek yerine *DatasetName.DataSet.Designer* dosyası). Kısmi sınıflar arasında birden çok fiziksel dosyaları Bölünecek belirli bir sınıf için kod etkinleştirin. Daha fazla bilgi için [kısmi](/dotnet/visual-basic/language-reference/modifiers/partial) veya [partial (tür)](/dotnet/csharp/language-reference/keywords/partial-type).

TableAdapter bağdaştırıcısının veri kümesinde değişiklik her zaman bir TableAdapter tanımlayan kod oluşturulur. TableAdapter bağdaştırıcısının yapılandırmasını değiştirir herhangi bir sihirbazı çalıştırma sırasında değişiklik yapıldığında bu kod ayrıca oluşturulur. Kodunuzu bir TableAdapter oluşturma işlemi sırasında silinmesini önlemek için TableAdapter'ın kısmi sınıf dosyaya kod ekleyin.

Veri kümesini ve TableAdapter kodunu ayırdıktan sonra varsayılan olarak, her proje bir parçalı sınıf dosyasında sonucudur. Adlı bir dosya özgün proje sahip *DatasetName.Designer.vb* (veya *DatasetName.Designer.cs*), TableAdapter kodunu içerir. İçinde belirtilen projeyi **Dataset projesi** özelliği adlı bir dosya var *DatasetName.DataSet.Designer.vb* (veya *DatasetName.DataSet.Designer.cs*), veri kümesi kodunu içerir.

> [!NOTE]
>  Veri kümelerini ve TableAdapter bağdaştırıcılarını ayırdığınızda (ayarlayarak **DataSet projesi** özelliği), projedeki varolan kısmi veri kümesi sınıfları taşınmaz otomatik olarak. Varolan kısmi veri kümesi sınıfları, veri kümesi projesine el ile taşınmalıdır.

> [!NOTE]
> Veri kümesini oluşturmak için işlevsellik sağlar <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.RowChanging> doğrulama gerektiğinde olay işleyicileri. Daha fazla bilgi için [bir n katmanlı bir veri kümesine doğrulama ekleme](../data-tools/add-validation-to-an-n-tier-dataset.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Bir TableAdapter n katmanlı bir uygulama içinde kullanıcı kodu eklemek için

1.  İçeren proje bulun *.xsd* dosya.

2.  Çift tıklayarak *.xsd* açmak için dosyaya **veri kümesi Tasarımcısı**.

3.  Kodu ekleyin ve ardından istediğiniz TableAdapter sağ **kodu görüntüle**.

     Kısmi sınıf oluşturulur ve Kod Düzenleyicisi'nde açılır.

4.  Kısmi sınıf bildirimi içinde kod ekleyin.

5.  Aşağıdaki örnek için kodunun nereye ekleneceğini gösterir `CustomersTableAdapter` içinde `NorthwindDataSet`:

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md)
- [N katmanlı uygulamalarda veri kümelerine kod ekleme](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [TableAdapter’lar oluşturma ve yapılandırma](create-and-configure-tableadapters.md)
- [Hiyerarşik güncelleştirmeye genel bakış](hierarchical-update.md)
