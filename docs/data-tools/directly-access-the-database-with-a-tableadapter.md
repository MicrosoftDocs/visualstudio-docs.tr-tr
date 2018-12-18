---
title: Bir TableAdapter ile veritabanına doğrudan erişme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 22a2580809394ba1b41e7923f4f2df458d995a93
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750968"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Bir TableAdapter ile veritabanına doğrudan erişme

Ek olarak `InsertCommand`, `UpdateCommand`, ve `DeleteCommand`, TableAdapter'ları doğrudan veritabanında çalıştırılabilen yöntemleri ile oluşturulur. Bu yöntemleri çağırabilir (`TableAdapter.Insert`, `TableAdapter.Update`, ve `TableAdapter.Delete`) doğrudan veritabanındaki verileri işlemek için.

Bu doğrudan yöntemleri oluşturmak istemiyorsanız TableAdapter bağdaştırıcısının ayarlamak `GenerateDbDirectMethods` özelliğini `false` içinde **özellikleri** penceresi. TableAdapter bağdaştırıcısının ana sorgusunda yanı sıra bir TableAdapter sorguları eklenir, bu üretme tek başına sorgulardır oldukları `DbDirect` yöntemleri.

## <a name="send-commands-directly-to-a-database"></a>Bir veritabanına doğrudan komut gönderme

TableAdapter çağrı `DbDirect` görevi gerçekleştiren yöntemi gerçekleştirmek çalıştığınız.

### <a name="to-insert-new-records-directly-into-a-database"></a>Doğrudan veritabanına yeni kayıtlar eklemek için

-   TableAdapter bağdaştırıcısının çağrı `Insert` değerler her sütun için parametre olarak geçirmeyi yöntemi. Aşağıdaki yordam kullanır `Region` örnek olarak Northwind veritabanındaki tablo.

    > [!NOTE]
    > Kullanmak istediğiniz TableAdapter kullanılabilir bir örnek yoksa örneği.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>Doğrudan veritabanındaki kayıtları güncelleştirmek için

-   TableAdapter bağdaştırıcısının çağrı `Update` yöntemi, yeni ve orijinal değerleri her sütun için parametre olarak geçirerek.

    > [!NOTE]
    > Kullanmak istediğiniz TableAdapter kullanılabilir bir örnek yoksa örneği.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>Kayıtları doğrudan veritabanından silmek için

-   TableAdapter bağdaştırıcısının çağrı `Delete` değerleri her sütun için parametre olarak geçirerek yöntemini `Delete` yöntemi. Aşağıdaki yordam kullanır `Region` örnek olarak Northwind veritabanındaki tablo.

    > [!NOTE]
    > Kullanmak istediğiniz TableAdapter kullanılabilir bir örnek yoksa örneği.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)