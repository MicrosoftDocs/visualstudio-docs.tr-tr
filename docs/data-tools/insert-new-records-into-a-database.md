---
title: Veritabanına yeni kayıtlar ekleme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: aae5ec2197ff2a899f27df20e7199fdeb7a02d31
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949207"
---
# <a name="insert-new-records-into-a-database"></a>Veritabanına yeni kayıtlar ekleme

Veritabanına yeni kayıtlar eklemek için kullanabileceğiniz `TableAdapter.Update` yöntemi veya TableAdapter bağdaştırıcısının DBDirect yöntemleri birini (özellikle `TableAdapter.Insert` yöntemi). Daha fazla bilgi için [TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Uygulamanızı TableAdapters kullanmıyorsa, komut nesneleri kullanabilirsiniz (örneğin, <xref:System.Data.SqlClient.SqlCommand>) veritabanınızdaki yeni kayıtları eklemek için.

Uygulama verilerini depolamak için veri kümelerini kullanan kullanırsanız `TableAdapter.Update` yöntemi. `Update` Yöntemi veritabanına (güncelleştirmeler, ekler ve siler) tüm değişiklikleri gönderir.

Uygulamanızın veri depolama ya da hassas denetime veritabanına yeni kayıtlar oluşturmak istiyorsanız kullanın nesneleri kullanıp kullanmadığını `TableAdapter.Insert` yöntemi.

TableAdapter yoksa bir `Insert` yöntemi geldiğini TableAdapter ya da saklı yordamları kullanmak için yapılandırıldığını veya kendi `GenerateDBDirectMethods` özelliği `false`. TableAdapter bağdaştırıcısının yapmayı deneyin `GenerateDBDirectMethods` özelliğini `true` içinden **veri kümesi Tasarımcısı**ve ardından veri kümesini kaydetme. Bu, TableAdapter yeniden oluşturacak. TableAdapter hala yoksa bir `Insert` yöntemi, tabloya büyük olasılıkla sağlamaz arasında bireysel satırları ayırt etmek için yeterli şema bilgileri (örneğin, olabilir tablosunda birincil anahtar ayarlanmadı).

## <a name="insert-new-records-by-using-tableadapters"></a>TableAdapter'ı kullanarak yeni kayıtlar ekleme

TableAdapters uygulamanızın gereksinimlerine bağlı olarak bir veritabanına yeni kayıtlar eklemek için farklı yollar sunar.

Uygulama verilerini depolamak için veri kümelerini kullanıyorsa, yalnızca yeni kayıtlar için istenen ekleyebileceğiniz <xref:System.Data.DataTable> veri kümesini ve sonra çağrı `TableAdapter.Update` yöntemi. `TableAdapter.Update` Yöntemi tüm değişiklikleri gönderir <xref:System.Data.DataTable> (değiştirilen ve silinen kayıtlar da dahil) veritabanı.

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>TableAdapter.Update yöntemini kullanarak bir veritabanına yeni kayıtlar eklemek için

1. Yeni kayıtlar için istenen ekleme <xref:System.Data.DataTable> yeni bir oluşturarak <xref:System.Data.DataRow> ve eklemeyi <xref:System.Data.DataTable.Rows%2A> koleksiyonu.

2. Yeni satırlar eklendikten sonra <xref:System.Data.DataTable>, çağrı `TableAdapter.Update` yöntemi. Tüm geçirerek ya da güncelleştirmek için veri miktarını denetleyebilirsiniz <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, bir dizi <xref:System.Data.DataRow>s ya da tek bir <xref:System.Data.DataRow>.

   Aşağıdaki kod, yeni bir kayıt eklemek gösterilmektedir bir <xref:System.Data.DataTable> ve sonra çağrı `TableAdapter.Update` yeni satır veritabanına kaydetmek için yöntemi. (Bu örnekte `Region` Northwind veritabanındaki tabloda.)

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>TableAdapter.INSERT yöntemi kullanarak bir veritabanına yeni kayıtlar eklemek için

Uygulama verilerini depolamak için nesneleri kullanıyorsa, kullanabileceğiniz `TableAdapter.Insert` yöntemini doğrudan veritabanında yeni satırlar. `Insert` Yöntemi, her bir sütunun değerlerini ayrı ayrı parametre olarak kabul eder. Yeni bir kayıt yöntemini çağırarak geçirilen parametre değerleri ile veritabanına ekler.

- TableAdapter bağdaştırıcısının çağrı `Insert` değerler her sütun için parametre olarak geçirmeyi yöntemi.

Aşağıdaki yordamı kullanarak gösterir `TableAdapter.Insert` satır eklemek için yöntemi. Bu örnek verileri ekler `Region` Northwind veritabanındaki tablo.

> [!NOTE]
> Kullanmak istediğiniz TableAdapter kullanılabilir bir örnek yoksa örneği.

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>Komut nesneleri kullanarak yeni kayıtlar ekleme

Doğrudan komut nesneleri kullanarak bir veritabanına yeni kayıtlar ekleyebilirsiniz.

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>Komut nesneleri kullanarak bir veritabanına yeni kayıtlar eklemek için

- Yeni bir komut nesnesi oluşturur ve ardından kendi `Connection`, `CommandType`, ve `CommandText` özellikleri.

Aşağıdaki örnek komut nesnesi kullanarak bir veritabanına ekleme kayıtları gösterir. Veri ekler `Region` Northwind veritabanındaki tablo.

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-framework-security"></a>.NET Framework güvenliği

İstenen tabloya ekler gerçekleştirme izni yanı sıra, bağlanmaya çalıştığınız veritabanı erişimi olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)