---
title: N katmanlı uygulamalarda Tableadapter'lara kod ekleyin | Microsoft Docs
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
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2b5302790d694c23da9e5385adf43c185dc66583
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207681"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>N katmanlı uygulamalarda TableAdapter’lara kod ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
İşlevlerini genişletmek bir `TableAdapter` için bir parçalı sınıf dosyası oluşturarak `TableAdapter` ve kod eklemeyi (kod eklemek yerine *DatasetName*. DataSet.Designer dosyası). Kısmi sınıflar arasında birden çok fiziksel dosyaları Bölünecek belirli bir sınıf için kod etkinleştirin. Daha fazla bilgi için [kısmi](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) veya [partial (tür)](http://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).  
  
 Tanımlayan kodu bir `TableAdapter` değişiklik her zaman oluşturulan `TableAdapter` (içinde [oluşturma ve yazılan veri kümelerini düzenleme](../data-tools/creating-and-editing-typed-datasets.md)). Her sihirbazın yapılandırmasını değiştirir çalışması sırasında değişiklik yapıldığında bu kod ayrıca oluşturulur `TableAdapter`. Kodunuzu anahtarınızın yeniden oluşturulması sırasında silinmesini önlemek için bir `TableAdapter`, kısmi sınıf dosyaya kod eklemek `TableAdapter`.  
  
 Veri kümesi ayırdıktan sonra varsayılan olarak ve `TableAdapter` kod sonucu olan her proje bir parçalı sınıf dosyasında. Adlı bir dosya özgün proje sahip *DatasetName*. Designer.vb olarak adlandırılır (veya *DatasetName*. Designer.cs) içeren `TableAdapter` kod. İçinde belirtilen projeyi **Dataset projesi** özelliği adlı bir dosya var *DatasetName*. DataSet.Designer.vb (veya *DatasetName*. DataSet.Designer.cs), veri kümesi kodunu içerir.  
  
> [!NOTE]
>  Veri kümelerini ve `TableAdapter`s (ayarlayarak **DataSet projesi** özelliği), projedeki varolan kısmi veri kümesi sınıfları taşınmaz otomatik olarak. Var olan veri kümesi kısmi sınıflarının veri kümesi projesine el ile taşınması gerekir.  
  
> [!NOTE]
>  [Oluşturma ve yazılan veri kümelerini düzenleme](../data-tools/creating-and-editing-typed-datasets.md) oluşturmak için işlevsellik sağlar <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.RowChanging> doğrulama gerektiğinde olay işleyicileri. Daha fazla bilgi için [bir n katmanlı bir veri kümesine doğrulama ekleme](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Bir TableAdapter n katmanlı bir uygulama içinde kullanıcı kodu eklemek için  
  
1.  .Xsd dosyasını içeren proje bulun ( [oluşturma ve yazılan veri kümelerini düzenleme](../data-tools/creating-and-editing-typed-datasets.md)).  
  
2.  Çift tıklayarak **.xsd** açmak için dosyaya [oluşturma ve yazılan veri kümelerini düzenleme](../data-tools/creating-and-editing-typed-datasets.md).  
  
3.  Sağ `TableAdapter` kodu ekleyin ve ardından istediğiniz**kodu görüntüle**.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md)   
 [N katmanlı uygulamalarda veri kümelerine kod ekleme](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
 [TableAdapter'ları](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [TableAdapterManager genel bakış](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)   
 [Hiyerarşik güncelleştirmeye genel bakış](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)   
 [Veri uygulamaları oluşturma](../data-tools/creating-data-applications.md)

