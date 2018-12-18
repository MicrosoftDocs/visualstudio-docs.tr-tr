---
title: 'Nasıl yapılır: veri kümesi değişikliklerini veritabanına kaydetme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DbDataAdapter.Update
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], saving
- databases, updating
- updating datasets, writing changes to data source
ms.assetid: c9970150-b71b-4c9d-a355-5efb6b510dca
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 60bb855202cfb333820fe2292fedc0b31608c5c6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949025"
---
# <a name="how-to-save-dataset-changes-to-a-database"></a>Nasıl yapılır: Veri Kümesi Değişikliklerini Veritabanına Kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veri kümenizdeki verileri değiştiren ve doğrulanmış sonra büyük olasılıkla bir veritabanına güncelleştirilmiş veriler göndermek istersiniz. Değiştirilmiş verileri bir veritabanına göndermek için çağrı `Update` yöntemi bir [TableAdapter](../data-tools/tableadapter-overview.md) veya veri bağdaştırıcısı. Bağdaştırıcının `Update` yöntemi tek bir veri tablosunu güncelleştirir ve göre doğru komutu (INSERT, UPDATE veya DELETE) yürütür <xref:System.Data.DataRow.RowState%2A> tablodaki her veri satırının.  
  
 Visual Studio, verileri ilgili tabloları kaydedilirken veritabanında tanımlanan yabancı anahtar kısıtlamaları göre doğru sırada kaydeder gerçekleştirmede yönetmenize yardımcı olan bir TableAdapterManager bileşeni sağlar. Daha fazla bilgi için [hiyerarşik güncelleştirme genel bakış](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6).  
  
> [!NOTE]
>  Bir veri kaynağı bir veri kümesinin içeriğiyle güncelleştirilmeye çalışılıyor hatalara yol açabilir çünkü bağdaştırıcının çağıran kodu koymalısınız `Update` yöntemi içinde bir `try` / `catch` blok.  
  
 Bir veri kaynağını güncelleştirmek için tam bir yordam, iş gereksinimlerinize bağlı olarak farklılık gösterebilir, ancak aşağıdaki adımları uygulamanız içermelidir:  
  
1.  Veritabanı içinde güncelleştirmeleri göndermeye çalışan kod yürütme bir `try` / `catch` blok.  
  
2.  Bir özel durum yakalandığında, hataya neden olan veri satırı bulun. Daha fazla bilgi için [nasıl yapılır: satırlar söz konusu olan hataları bulun](http://msdn.microsoft.com/library/1fa907c5-fe66-4f29-a253-2b97b900050c).  
  
3.  Sorun verilerinde mutabakat (programlı olarak mümkün ise veya geçersiz satır için değişiklik kullanıcıya sunarak) öğesini ve ardından güncelleştirmeyi deneyin (<xref:System.Data.DataRow.HasErrors%2A> özelliği <xref:System.Data.DataTable.GetErrors%2A> yöntemi).  
  
## <a name="saving-data-to-a-database"></a>Verileri bir veritabanına kaydetme  
 Çağrı `Update` yöntemi, veri tablosu adını geçirerek bir Tableadapver ya da veri bağdaştırıcısının veritabanına yazılması için değerleri içerir. Verileri tek bir veri tablosundan bir veritabanına geri kaydediliyor. daha fazla bilgi için bkz: [izlenecek yol: verileri bir veritabanına (tek tablo) kaydetme](http://msdn.microsoft.com/library/68befa96-7463-43e8-abcf-dc2f42ccd53d).  
  
#### <a name="to-update-a-database-with-a-dataset-using-a-tableadapter"></a>Bir TableAdapter'ı kullanarak bir veri kümesiyle bir veritabanını güncelleştirmek için  
  
-   İçine `TableAdapter.Update` yöntem içinde bir `try` / `catch` blok. Aşağıdaki örnek, içeriğini içeren bir güncelleştirme girişiminde gösterilmektedir `Customers` tablosundaki `NorthwindDataSet`.  
  
     [!code-csharp[VbRaddataSaving#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#9)]
     [!code-vb[VbRaddataSaving#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#9)]  
  
#### <a name="to-update-a-database-with-a-dataset-using-a-data-adapter"></a>Veri bağdaştırıcısı kullanarak bir veri kümesiyle bir veritabanını güncelleştirmek için  
  
-   İçine `DataAdapter.Update` yöntem içinde bir `try` / `catch` blok. Aşağıdaki örnek, bir güncelleştirme içeriğini bir veri kaynağına bağlanmaya gösterilmektedir `Table1` içinde `DataSet1`.  
  
     [!code-csharp[VbRaddataSaving#26](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#26)]
     [!code-vb[VbRaddataSaving#26](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#26)]  
  
## <a name="updating-two-related-tables-in-a-dataset"></a>Bir veri kümesindeki iki ilişkili tablolar güncelleştiriliyor  
 Veri kümesinde ilişkili tablolardaki güncelleştirirken başvurusal bütünlük kısıtlamalarını ihlal olasılığını azaltmak için doğru sırada güncelleştirilmesi önemlidir. Komut yürütme sırası dizin de izleyeceği <xref:System.Data.DataRowCollection> kümesindeki. Yaratılmasına veri bütünlüğü hatalarını önlemek için aşağıdaki sırayla veritabanını güncellemek için en iyi yöntem olacaktır:  
  
1. Alt tablo: kayıtları silin.  
  
2. Üst tablo: ekleme, güncelleştirme ve kayıtları silin.  
  
3. Alt tablo: ekleme ve güncelleştirme kaydeder.  
  
   Birden çok tablodan veri kaydetme ile ilgili ayrıntılı bilgi için bkz [veritabanına (birden çok tablo) veri kaydetme](../data-tools/save-data-to-a-database-multiple-tables.md).  
  
   İki veya daha fazla ilgili tablo güncelleştiriyorsanız, bir işlem içinde tüm güncelleştirme mantığı eklemeniz gerekir. Bir işlem herhangi bir değişiklik yapmadan önce tüm ilgili değişiklikler veritabanına başarıyla garantiler bir işlemdir. Daha fazla bilgi edinmek, [işlemler ve eşzamanlılık](http://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).  
  
#### <a name="to-update-two-related-tables-using-a-tableadapter"></a>Bir TableAdapter kullanarak iki ilişkili tablolar güncelleştirilemedi  
  
1.  Üç geçici oluşturma <xref:System.Data.DataTable>farklı kayıtlarını tutacak s.  
  
2.  Çağrı `Update` yöntemi satır içinden her bir alt kümesi için bir `try` / `catch` blok. Güncelleştirme hataları meydana gelirse, önerilen eylem dal ve çözme sağlamaktır.  
  
3.  Değişiklikleri veritabanına veri kümesinden uygulayın.  
  
4.  Dispose kaynakları serbest bırakmak için geçici veri tabloları.  
  
     [!code-csharp[VbRaddataSaving#27](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#27)]
     [!code-vb[VbRaddataSaving#27](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#27)]  
  
#### <a name="to-update-two-related-tables-using-a-data-adapter"></a>Veri bağdaştırıcısı kullanarak iki ilişkili tablolar güncelleştirilemedi  
  
-   Çağrı `Update` her veri bağdaştırıcısının yöntemi.  
  
     Aşağıdaki örnek, ilgili tablolarını içeren bir veri kümesi ile bir veri kaynağını güncelleştirmek gösterilmektedir. Yukarıdaki üç geçici sırasının takip etmek için <xref:System.Data.DataTable>s, farklı kayıtları tutmak için oluşturulacak. Ardından `Update` yöntemin çağrılacağı her satır alt kümesi için içinden bir `try` / `catch` blok. Güncelleştirme hataları meydana gelirse, önerilen eylem dal ve çözme sağlamaktır. Ardından veri kümesini değişiklikleri kaydeder. Son olarak, kaynakları serbest bırakmak için geçici veri tabloları atın.  
  
     [!code-csharp[VbRaddataSaving#28](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#28)]
     [!code-vb[VbRaddataSaving#28](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri izlenecek yollar](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio'da verilere bağlanma](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Uygulamanızı veri almaya hazırlama](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Uygulamanıza veri getirme](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Uygulamanızdaki verileri düzenleme](../data-tools/editing-data-in-your-application.md)   
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Verileri Kaydetme](../data-tools/saving-data.md)