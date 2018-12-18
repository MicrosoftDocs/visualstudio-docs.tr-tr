---
title: Verileri bir nesneden veritabanına kaydetme | Microsoft Docs
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
- data [Visual Studio], saving
- data access [Visual Studio], objects
- saving data
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: acbbf9f309573f110da3b7dd0a53ede36150a319
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207460"
---
# <a name="save-data-from-an-object-to-a-database"></a>Verileri bir nesneden veritabanına kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Değerleri, bir nesneden bir TableAdapter bağdaştırıcısının DBDirect yöntemleri geçirerek bir veritabanı nesneleri veri kaydedebilir (örneğin, `TableAdapter.Insert`). Daha fazla bilgi için [TableAdapter genel bakışı](../data-tools/tableadapter-overview.md).  
  
 Veri nesneleri (örneğin, bir sonraki için döngü) nesne koleksiyonunu döngü koleksiyonundan kaydedip değerlerin her nesne için TableAdapter bağdaştırıcısının DBDirect yöntemleri birini kullanarak veritabanına göndermek için.  
  
 Varsayılan olarak, doğrudan veritabanında çalıştırılabilir bir TableAdapter DBDirect yöntemleri oluşturulur. Bu yöntem doğrudan çağrılabilir ve gerektirmeyen <xref:System.Data.DataSet> veya <xref:System.Data.DataTable> güncelleştirmeleri bir veritabanına göndermek için değişiklikleri mutabık kılınacak nesneleri.  
  
> [!NOTE]
>  Bir TableAdapter'ı yapılandırırken, ana sorguda yeterli bilgi oluşturulacak DBDirect yöntemleri için sağlamanız gerekir. Örneğin, bir TableAdapter tanımlı bir birincil anahtar sütunu yok. bir tablodan verileri sorgulamak için yapılandırılmışsa, DBDirect yöntemleri oluşturmaz.  
  
|TableAdapter DBDirect yöntemi|Açıklama|  
|----------------------------------|-----------------|  
|`TableAdapter.Insert`|Bir veritabanına yeni kayıtlar ekler ve ayrı ayrı sütun değerlerine yöntem parametreleri olarak geçirilecek sağlar.|  
|`TableAdapter.Update`|Mevcut veritabanındaki kayıtları güncelleştirir. `Update` Yöntemi yöntem parametreleri olarak özgün ve yeni sütun değerlerini alır. Orijinal değerleri özgün kaydı bulmak için kullanılır ve bu kaydı güncelleştirmek için yeni değerler kullanılır.<br /><br /> `TableAdapter.Update` Yöntemi dataset içindeki değişiklikleri veritabanına geri alarak karşılaştırmak için kullanılan ayrıca bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, veya bir dizi <xref:System.Data.DataRow>yöntem parametreleri olarak s.|  
|`TableAdapter.Delete`|Yöntem parametreleri olarak geçirilen var olan kayıtların özgün sütun değerlerine göre veritabanından siler.|  
  
### <a name="to-save-new-records-from-an-object-to-a-database"></a>Yeni kayıtlar bir nesneden veritabanına kaydetme için  
  
-   İçin değerler geçirerek kayıtları oluşturma `TableAdapter.Insert` yöntemi.  
  
     Aşağıdaki örnek, yeni bir müşteri kaydı oluşturur `Customers` değerler geçirerek tablo `currentCustomer` nesnesini `TableAdapter.Insert` yöntemi.  
  
     [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
     [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]  
  
### <a name="to-update-existing-records-from-an-object-to-a-database"></a>Var olan bir nesne kayıtları bir veritabanına güncelleştirmek için  
  
-   Çağırarak kayıtların değiştirilmesi `TableAdapter.Update` kaydı güncelleştirmek için yeni değerler geçirerek ve kaydı bulmak için özgün değerlerine geçirme yöntemi.  
  
    > [!NOTE]
    >  Nesneniz için geçirmek için orijinal değerleri tutması gerekir `Update` yöntemi. Bu örnekte bu özelliklere sahip bir `orig` orijinal değerleri depolamak için önek.  
  
     Aşağıdaki örnek, mevcut kaydı güncelleştirir `Customers` yeni ve özgün değerler geçirerek tablo `Customer` nesnesini `TableAdapter.Update` yöntemi.  
  
     [!code-csharp[VbRaddataSaving#24](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#24)]
     [!code-vb[VbRaddataSaving#24](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#24)]  
  
### <a name="to-delete-existing-records-from-a-database"></a>Mevcut kayıtlarını veritabanından silmek için  
  
-   Çağırarak kayıtları silmek `TableAdapter.Delete` yöntemi ve kaydı bulmak için özgün değerlerini geçirirsiniz.  
  
    > [!NOTE]
    >  Nesneniz için geçirmek için orijinal değerleri tutması gerekir `Delete` yöntemi. Bu örnekte bu özelliklere sahip bir `orig` orijinal değerleri depolamak için önek.  
  
     Aşağıdaki örnek, bir kaydı siler `Customers` özgün değerler geçirerek tablo `Customer` nesnesini `TableAdapter.Delete` yöntemi.  
  
     [!code-csharp[VbRaddataSaving#25](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#25)]
     [!code-vb[VbRaddataSaving#25](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#25)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Seçili ekleme yapma iznine sahip olmalıdır UPDATE veya DELETE veritabanı tablosunda.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)

