---
title: Verileri bir nesneden veritabanına kaydetme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c1203b3b129b42ca65b94cd7a4b9cebf108740f4
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750956"
---
# <a name="save-data-from-an-object-to-a-database"></a>Verileri bir nesneden veritabanına kaydetme

Değerleri, bir nesneden bir TableAdapter bağdaştırıcısının DBDirect yöntemleri geçirerek bir veritabanı nesneleri veri kaydedebilir (örneğin, `TableAdapter.Insert`). Daha fazla bilgi için [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Nesnelerin bir koleksiyondaki verileri kaydetmek için döngü koleksiyonda nesnelerin (örneğin, bir sonraki için döngü) ve her nesne için değerleri, TableAdapter bağdaştırıcısının birini kullanarak veritabanına göndermek `DBDirect` yöntemleri.

Varsayılan olarak, `DBDirect` yöntemlerini doğrudan veritabanında çalıştırılabilir bir TableAdapter üzerinde oluşturulur. Bu yöntem doğrudan çağrılabilir ve gerektirmeyen <xref:System.Data.DataSet> veya <xref:System.Data.DataTable> güncelleştirmeleri bir veritabanına göndermek için değişiklikleri mutabık kılınacak nesneleri.

> [!NOTE]
> Bir TableAdapter'ı yapılandırırken, ana sorguda yeterli bilgi sağlamalısınız `DBDirect` oluşturulacak yöntemleri. Örneğin, bir TableAdapter sorgu veri tanımlı bir birincil anahtar sütunu yok. bir tablodan yapılandırdıysanız, bu oluşturmaz `DBDirect` yöntemleri.

|TableAdapter DBDirect yöntemi|Açıklama|
| - |-----------------|
|`TableAdapter.Insert`|Bir veritabanına yeni kayıtlar ekler ve ayrı ayrı sütun değerlerine yöntem parametreleri olarak geçirilecek sağlar.|
|`TableAdapter.Update`|Mevcut veritabanındaki kayıtları güncelleştirir. `Update` Yöntemi yöntem parametreleri olarak özgün ve yeni sütun değerlerini alır. Orijinal değerleri özgün kaydı bulmak için kullanılır ve bu kaydı güncelleştirmek için yeni değerler kullanılır.<br /><br /> `TableAdapter.Update` Yöntemi dataset içindeki değişiklikleri veritabanına geri alarak karşılaştırmak için kullanılan ayrıca bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, veya bir dizi <xref:System.Data.DataRow>yöntem parametreleri olarak s.|
|`TableAdapter.Delete`|Yöntem parametreleri olarak geçirilen var olan kayıtların özgün sütun değerlerine göre veritabanından siler.|

## <a name="to-save-new-records-from-an-object-to-a-database"></a>Yeni kayıtlar bir nesneden veritabanına kaydetme için

-   İçin değerler geçirerek kayıtları oluşturma `TableAdapter.Insert` yöntemi.

     Aşağıdaki örnek, yeni bir müşteri kaydı oluşturur `Customers` değerler geçirerek tablo `currentCustomer` nesnesini `TableAdapter.Insert` yöntemi.

     [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]

## <a name="to-update-existing-records-from-an-object-to-a-database"></a>Var olan bir nesne kayıtları bir veritabanına güncelleştirmek için

-   Çağırarak kayıtların değiştirilmesi `TableAdapter.Update` kaydı güncelleştirmek için yeni değerler geçirerek ve kaydı bulmak için özgün değerlerine geçirme yöntemi.

    > [!NOTE]
    > Nesneniz için geçirmek için orijinal değerleri tutması gerekir `Update` yöntemi. Bu örnekte bu özelliklere sahip bir `orig` orijinal değerleri depolamak için önek.

     Aşağıdaki örnek, mevcut kaydı güncelleştirir `Customers` yeni ve özgün değerler geçirerek tablo `Customer` nesnesini `TableAdapter.Update` yöntemi.

     [!code-csharp[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]

## <a name="to-delete-existing-records-from-a-database"></a>Mevcut kayıtlarını veritabanından silmek için

-   Çağırarak kayıtları silmek `TableAdapter.Delete` yöntemi ve kaydı bulmak için özgün değerlerini geçirirsiniz.

    > [!NOTE]
    > Nesneniz için geçirmek için orijinal değerleri tutması gerekir `Delete` yöntemi. Bu örnekte bu özelliklere sahip bir `orig` orijinal değerleri depolamak için önek.

     Aşağıdaki örnek, bir kaydı siler `Customers` özgün değerler geçirerek tablo `Customer` nesnesini `TableAdapter.Delete` yöntemi.

     [!code-csharp[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]

## <a name="net-framework-security"></a>.NET Framework güvenliği

Seçili gerçekleştirmek için izni olmalıdır `INSERT`, `UPDATE`, veya `DELETE` veritabanı tablosunda.

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)