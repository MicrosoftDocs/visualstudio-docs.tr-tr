---
title: Veri kümelerindeki verileri düzenleme | Microsoft Docs
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
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5a983b671b5c6b43009ad3cc32c2cb287977f05c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949298"
---
# <a name="edit-data-in-datasets"></a>Veri kümelerindeki verileri düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Herhangi bir veritabanı tablosundaki verileri çok düzenlediğiniz gibi veri tablolardaki verileri düzenleyin. İşlem ekleme, güncelleştirme ve tablodaki kayıtları silme içerebilir. Verilere bağlı formunda, hangi alanların kullanıcı tarafından düzenlenebilir olduğunu belirtebilirsiniz. Bu gibi durumlarda, böylece değişiklikleri veritabanına geri daha sonra gönderilebilecek tüm değişiklik izleme veri bağlama altyapı işler. Verileri program aracılığıyla düzenlemeleri yapın ve bu değişiklikleri veritabanına geri göndermek istediğinize, nesneleri ve değişiklik izleme bunu yöntemleri kullanmanız gerekir.  
  
 Gerçek veriler değiştirmenin yanı sıra, ayrıca Sorgulayabileceğiniz bir <xref:System.Data.DataTable> verilerin belirli satırları döndürür. Örneğin, ayrı satırlara, satırları (özgün ve önerilen) belirli sürümleri, değiştirilen satırları veya hatalar içeren satırların sorgu.  
  
## <a name="to-edit-rows-in-a-dataset"></a>Bir veri kümesindeki satırları düzenleme  
 Mevcut bir satırı içinde düzenlemek için bir <xref:System.Data.DataTable>, bulmanız gerekir <xref:System.Data.DataRow> düzenleyin ve ardından istenen sütunlar için güncelleştirilmiş değerleri atamak istiyorsunuz.  
  
 Satır dizini bilmiyorsanız istediğiniz düzen kullanın `FindBy` yöntemi birincil anahtara göre aramak için:  
  
 [!code-csharp[VbRaddataEditing#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#3)]
 [!code-vb[VbRaddataEditing#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#3)]  
  
 Satır dizini biliyorsanız erişebilir ve satır şu şekilde düzenler:  
  
 [!code-csharp[VbRaddataEditing#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#5)]
 [!code-vb[VbRaddataEditing#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#5)]  
  
## <a name="to-insert-new-rows-into-a-dataset"></a>Bir veri kümesine satırlar eklemek için  
 Verilere bağlı denetimler genellikle kullanan uygulamalar üzerinden yeni kayıt ekleme **yeni Ekle** düğmesini bir [BindingNavigator denetimine](http://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).  
  
 El ile yeni kayıtlar ekleme için yeni bir veri satırı üzerinde DataTable yöntemi çağırarak oluşturun. Satıra eklersiniz <xref:System.Data.DataRow> koleksiyon (<xref:System.Data.DataTable.Rows%2A>), <xref:System.Data.DataTable>:  
  
 [!code-csharp[VbRaddataEditing#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#1)]
 [!code-vb[VbRaddataEditing#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#1)]  
  
 Veri kümesi güncelleştirmeleri veri kaynağına göndermek gereken bilgileri korumak için kullanılması <xref:System.Data.DataRow.Delete%2A> bir veri tablosundan satırları kaldırmak için yöntemi. Örneğin, uygulamanız bir TableAdapter kullanıyorsa (veya <xref:System.Data.Common.DataAdapter>), TableAdapter bağdaştırıcısının `Update` yöntemi olan veritabanındaki satırları siler bir <xref:System.Data.DataRow.RowState%2A> , <xref:System.Data.DataRowState>.  
  
 Güncelleştirmeleri veri kaynağına geri göndermek uygulamanızı gereksinimi yoksa, ardından veri satır koleksiyonu doğrudan erişerek kayıtları kaldırmak mümkündür (<xref:System.Data.DataRowCollection.Remove%2A>).  
  
#### <a name="to-delete-records-from-a-data-table"></a>Bir veri tablosundan kayıtları silmek için  
  
-   Çağrı <xref:System.Data.DataRow.Delete%2A> yöntemi bir <xref:System.Data.DataRow>.  
  
     Bu yöntem, fiziksel olarak kayıt kaldırmaz. Bunun yerine, kayıt silme işlemi için işaretler.  
  
    > [!NOTE]
    >  Count özelliği alırsanız bir <xref:System.Data.DataRowCollection>, sonuçta elde edilen sayı silinme için işaretlenmiş kayıtları içerir. Doğru bir silme için işaretlenen olmayan kayıt sayısını almak için bakarak koleksiyon döngü <xref:System.Data.DataRow.RowState%2A> her kaydın özellik. (Kayıt silinmek üzere işaretlenmiş bir <xref:System.Data.DataRow.RowState%2A> , <xref:System.Data.DataRowState>.) Alternatif olarak, filtreleri satır durumuna dayalı bir veri kümesinin veri görünümü oluşturabilir ve buradan count özelliği edinin.  
  
     Aşağıdaki örnek nasıl çağrılacağını gösterir <xref:System.Data.DataRow.Delete%2A> yöntemin ilk satırında işaretlemek için `Customers` tablo silindi olarak:  
  
     [!code-csharp[VbRaddataEditing#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#8)]
     [!code-vb[VbRaddataEditing#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#8)]  
  
## <a name="determine-if-there-are-changed-rows"></a>Değiştirilen satırların olup olmadığını belirleme  
 Bir veri kümesindeki kayıtlara değişiklik yapıldığında, onları yürütene kadar o değişiklikler hakkındaki bilgiler depolanır. Çağırdığınızda değişiklikleri `AcceptChanges` yöntemi veya bir veri kümesi veya veri tablosunun çağırdığınızda `Update` bir Tableadapver ya da veri bağdaştırıcısının yöntemi.  
  
 Her veri satırı izlenen iki yolla değişiklikler şunlardır:  
  
- Her veri satırı onun için ilgili bilgiler içeren <xref:System.Data.DataRow.RowState%2A> (örneğin, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, veya <xref:System.Data.DataRowState>).  
  
- Her değiştirilen veri satırı o satırın birden çok sürümünü içerir (<xref:System.Data.DataRowVersion>), özgün sürüm (değişikliklerden önce) ve geçerli sürümü (değişikliklerden sonra). Bir değişiklik olduğunda Beklemede olduğu süre boyunca (ne zaman yanıt süresi <xref:System.Data.DataTable.RowChanging> olay), üçüncü bir sürüm — önerilen sürüm — de kullanılabilir. Daha fazla bilgi için [nasıl yapılır: bir DataRow belirli sürümlerini alma](../data-tools/how-to-get-specific-versions-of-a-datarow.md).  
  
  <xref:System.Data.DataSet.HasChanges%2A> Yöntemi bir veri kümesinin döndürür `true` kümesinde değişiklik yapılmadıysa. Değiştirilen satırların var olduğunu belirledikten sonra çağırabilirsiniz `GetChanges` yöntemi bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable> değiştirilen satırlar kümesini geri dönmek için. Daha fazla bilgi için [nasıl yapılır: değiştirilen satırları alma](http://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).  
  
#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Bir satırda değişiklik yapılıp yapılmadığını belirlemek için  
  
-   Çağrı <xref:System.Data.DataSet.HasChanges%2A> değiştirilen satırları denetlemek için bir veri kümesinin yöntemi.  
  
     Aşağıdaki örnek, dönüş değeri denetleyin işlemi gösterilmektedir <xref:System.Data.DataSet.HasChanges%2A> adlı bir veri kümesinde değiştirilen satırların olup olmadığını algılamak için `NorthwindDataset1`:  
  
     [!code-csharp[VbRaddataEditing#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#12)]
     [!code-vb[VbRaddataEditing#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#12)]  
  
## <a name="determine-the-type-of-changes"></a>Değişikliklerin türünü belirleme  
 Ne tür değişiklikleri görmek için yapıldı bir veri kümesinde bir değer aktararak de göz atabilirsiniz <xref:System.Data.DataRowState> sabit listesine <xref:System.Data.DataSet.HasChanges%2A> yöntemi.  
  
#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Belirlemek için ne tür değişiklikler yapıldığını satır  
  
-   Başarılı bir <xref:System.Data.DataRowState> değerini <xref:System.Data.DataSet.HasChanges%2A> yöntemi.  
  
     Aşağıdaki örnekte adlı veri kümesini denetlemek nasıl gösterir `NorthwindDataset1` herhangi bir yeni satır kendisine eklenmiş olursa belirlemek için:  
  
     [!code-csharp[VbRaddataEditing#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#13)]
     [!code-vb[VbRaddataEditing#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#13)]  
  
## <a name="to-locate-rows-that-have-errors"></a>Hatalar içeren satırların bulmak için  
 Tek tek sütunlara ve veri satırı çalışırken hatalarla karşılaşabilirsiniz. Denetleyebilirsiniz `HasErrors` hataları içinde mevcut olup olmadığını belirlemek için özellik bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, veya <xref:System.Data.DataRow>.  
  
1.  Denetleme `HasErrors` kümesinde herhangi bir hata olup olmadığını görmek için özellik.  
  
2.  Varsa `HasErrors` özelliği `true`, tablolar, koleksiyonlarına yinelemek ve ardından hata satırı bulur. satırlar, aracılığıyla.  
  
     [!code-csharp[VbRaddataEditing#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#23)]
     [!code-vb[VbRaddataEditing#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#23)]

