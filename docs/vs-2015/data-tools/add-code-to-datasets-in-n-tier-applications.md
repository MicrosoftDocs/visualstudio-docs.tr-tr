---
title: N katmanlı uygulamalarda veri kümelerine kod ekleme | Microsoft Docs
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
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 48f27d2e1bb72b7c5c0aaf1a66673beae003dd66
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202221"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>N katmanlı uygulamalarda veri kümelerine kod ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Veri kümesi için bir parçalı sınıf dosyası oluşturma ve kod eklemeyi tarafından bir veri kümesinin işlevselliğini genişletebilirsiniz (kod eklemek yerine *DatasetName*. Dataset.Designer dosyası). Kısmi sınıflar arasında birden çok fiziksel dosyaları Bölünecek belirli bir sınıf için kod etkinleştirin. Daha fazla bilgi için [kısmi](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) veya [kısmi sınıflar ve yöntemler](http://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).  
  
 Veri kümesi tanımı için yapılan değişiklikler her zaman bir veri kümesini tanımlayan bir kod oluşturulur (içinde [oluşturma ve yazılan veri kümelerini düzenleme](../data-tools/creating-and-editing-typed-datasets.md)). Bu kod Ayrıca, herhangi bir veri kümesinin yapılandırmasını değiştirir Sihirbazı'nı çalıştırılması sırasında değişiklik yaptığınızda oluşturulur. Kodunuzu bir veri kümesi oluşturma işlemi sırasında silinmesini önlemek için veri kümesinin parçalı sınıf dosyası için kodu ekleyin.  
  
 Veri kümesi ayırdıktan sonra varsayılan olarak ve `TableAdapter` kod sonucu olan her proje bir parçalı sınıf dosyasında. Özgün proje sahip bir filenamed *DatasetName*. Designer.vb olarak adlandırılır (veya *DatasetName*. Designer.cs) içeren `TableAdapter` kod. İçinde belirtilen projeyi **Dataset projesi** özellik adında bir dosya var *DatasetName*. DataSet.Designer.vb (veya *DatasetName*. DataSet.Designer.cs). Bu dosya, veri kümesi kodunu içerir.  
  
> [!NOTE]
>  Veri kümelerini ve `TableAdapter`s (ayarlayarak **DataSet projesi** özelliği), projedeki varolan kısmi veri kümesi sınıfları olmaz taşınması otomatik olarak. Var olan veri kümesi kısmi sınıflarının veri kümesi projesine el ile taşınması gerekir.  
  
> [!NOTE]
>  Doğrulama kodu eklenmesi, gerektiğinde [oluşturma ve yazılan veri kümelerini düzenleme](../data-tools/creating-and-editing-typed-datasets.md)oluşturmak için işlevsellik sağlar <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.RowChanging> olay işleyicileri. Daha fazla bilgi için [bir n katmanlı bir veri kümesine doğrulama ekleme](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
### <a name="to-add-code-to-datasets-in-n-tier-applications"></a>N katmanlı uygulamalarda veri kümelerine kod ekleme  
  
1.  .Xsd dosyasını içeren proje bulun ( [oluşturma ve yazılan veri kümelerini düzenleme](../data-tools/creating-and-editing-typed-datasets.md)).  
  
2.  Seçin **.xsd** açmak için dosyaya [oluşturma ve yazılan veri kümelerini düzenleme](../data-tools/creating-and-editing-typed-datasets.md).  
  
3.  Kod (başlık çubuğundaki tablo adı) ve thenselect eklemek istediğiniz veri tablosuna sağ**kodu görüntüle**.  
  
     Kısmi sınıf oluşturulur ve Kod Düzenleyicisi'nde açılır.  
  
4.  Kısmi sınıf bildirimi içinde kod ekleyin.  
  
     Aşağıdaki örnek, NorthwindDataSet'teki CustomersDataTable kod ekleme yeri gösterir:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md)   
 [N katmanlı uygulamalarda Tableadapter'lara kod ekleyin](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)   
 [TableAdapter'ları](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [TableAdapterManager genel bakış](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)   
 [Hiyerarşik güncelleştirmeye genel bakış](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)   
 [Veri uygulamaları oluşturma](../data-tools/creating-data-applications.md)   
 [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)

