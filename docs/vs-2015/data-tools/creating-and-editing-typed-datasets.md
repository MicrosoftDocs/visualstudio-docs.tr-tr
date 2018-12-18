---
title: Oluşturma ve düzenleme türü belirtilmiş Datasets | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner
- vs.data.adddataset
dev_langs:
- VB
- CSharp
- C++
- aspx
- aspx
helpviewer_keywords:
- datasets [Visual Basic], visual designer
- data [Visual Studio], Dataset Designer
- Dataset Designer
ms.assetid: cd0dbe93-be9b-41e4-bc39-e9300678c1f2
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 8c18717cd2a5c7e05b79dbe575d919ef0c8670dd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225851"
---
# <a name="creating-and-editing-typed-datasets"></a>Türü Belirtilmiş Veri Kümeleri Oluşturma ve Düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Veri kümesi Tasarımcısı** bir türü belirtilmiş veri kümeleri ve içerdikleri bireysel öğeleri oluşturmak ve düzenlemek için kullanabileceğiniz visual araç kümesidir.  
  
 **Veri kümesi Tasarımcısı** görsel temsilini yazılan veri kümelerinde bulunan nesneleri sağlar. Oluşturma ve değiştirme [TableAdapters](../data-tools/tableadapter-overview.md), [TableAdapter sorguları](../data-tools/how-to-create-tableadapter-queries.md), <xref:System.Data.DataTable>s, <xref:System.Data.DataColumn>s ve <xref:System.Data.DataRelation>s ile **veri kümesi Tasarımcısı**.  
  
 Açmak için **veri kümesi Tasarımcısı**, içinde bir veri kümesine çift tıklayın **Çözüm Gezgini**, veya bir veri kümesinde sağ **veri kaynakları** penceresini açın ve **Düzenle Veri kümesi Tasarımcısı ile**. Daha fazla bilgi için [nasıl yapılır: bir veri kümesini veri kümesi Tasarımcısı'nda açma](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3). Yeni bir ekleme <xref:System.Data.DataSet> sahip olan öğe **Yeni Öğe Ekle** iletişim kutusu açılır **veri kümesi Tasarımcısı** ile boş veri kümesini düzenleme için hazır.  
  
> [!NOTE]
>  **Veri kümesi Tasarımcısı** bir veri kümesi genişletmek için kullanılabilir. Tasarım yüzeyine çift tıklatın veya sağ tıklayıp seçin **kodu görüntüle** ekleyebileceğiniz kod yok edilecek değiştirildi veya tasarımcı tarafından silindi veri kümesi için bir parçalı sınıf dosyası oluşturmak için. Bir TableAdapter işlevini genişletme hakkında daha fazla bilgi için bkz: [bir TableAdapter işlevini genişletme](../data-tools/extend-the-functionality-of-a-tableadapter.md).  
  
 Aşağıdaki tablo ile gerçekleştirmek ortak görevleri listeler **veri kümesi Tasarımcısı**.  
  
|Bitiş|Bkz. |  
|--------|---------|  
|Bir TableAdapter oluşturma|[TableAdapter’lar oluşturma ve yapılandırma](../data-tools/create-and-configure-tableadapters.md)|  
|Bir TableAdapter Düzenle|[Nasıl yapılır: TableAdapters öğesini düzenleme](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855)|  
|TableAdapter Sorgusu Oluştur|[Nasıl yapılır: TableAdapter sorguları oluşturma](../data-tools/how-to-create-tableadapter-queries.md)|  
|TableAdapter sorgusu Düzenle|[Nasıl yapılır: TableAdapter sorgularını düzenleme](../data-tools/how-to-edit-tableadapter-queries.md)|  
|Oluşturma bir <xref:System.Data.DataTable>|[Nasıl yapılır: veri tabloları oluşturma](../data-tools/how-to-create-data-tables.md)|  
|Düzen bir <xref:System.Data.DataTable>|[DataTables tasarlama](../data-tools/designing-datatables.md)|  
|Oluşturma bir <xref:System.Data.DataColumn>|[Nasıl yapılır: DataTable tablosuna sütun ekleme](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)|  
|İki arasında bir ilişki oluşturmamız <xref:System.Data.DataTable>s|[Nasıl yapılır: veri kümesi Tasarımcısı ile DataRelations oluşturma](http://msdn.microsoft.com/library/a3ab4803-0b50-4b74-9920-ab20bfbf1aa2)|  
|Veri kümesinin işlevini genişletme|[Nasıl yapılır: bir veri kümesinin işlevini genişletme](http://msdn.microsoft.com/library/dfbc21eb-7ea2-4942-addd-49677f5493be)|  
|Bir veri tablosuna ait doğrulamanın <xref:System.Data.DataTable.ColumnChanging> olay|[Nasıl yapılır: sütun değişiklikleri sırasında veri doğrulama](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5)|  
|Bir veri tablosuna ait doğrulamanın <xref:System.Data.DataTable.RowChanging> olay|[Nasıl yapılır: satır değişiklikleri sırasında veri doğrulama](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc)|  
  
## <a name="creating-objects-on-the-design-surface"></a>Tasarım yüzeyinde nesneleri oluşturma  
 Ekleme ve bir veri kümesini oluşturan ayrı nesnelerin düzenleme, veri kümeleri oluşturabilirsiniz. Aşağıdaki tabloda farklı nesneleri bir açıklaması verilmiştir **veri kümesi** sekmesinde **araç kutusu** tasarım yüzeyine sürüklenebilir:  
  
|Nesne|Açıklama|  
|------------|-----------------|  
|TableAdapter|Veri komutları ve temel alınan veritabanı ile iletişim kurmak ve veri tablosunu doldurmak için kullanılan bir veri bağlantısı koleksiyonunu içerir. Daha fazla bilgi için [TableAdapter genel bakışı](../data-tools/tableadapter-overview.md) ve [oluştur ve TableAdapter yapılandırma](../data-tools/create-and-configure-tableadapters.md).|  
|Sorgu|TableAdapter sorguları SQL deyimlerini ve depolanan yordamları yürüten kesin türü belirtilmiş yöntemlerdir. Bir TableAdapter sorgusu çalıştırarak verileri tabloyu verilerle doldurur veya diğer veritabanı görevleri gerçekleştirir. Daha fazla bilgi için [nasıl yapılır: TableAdapter sorguları oluşturma](../data-tools/how-to-create-tableadapter-queries.md). Bir sorgu bir tablo sürükleyerek ekler Sorgu tabloya, boş bir alanının bir sorgu sürükleme **veri kümesi Tasarımcısı** genel bir sorgu oluşturur. Daha fazla bilgi için [nasıl yapılır: bir TableAdapter genel sorgular ekleme](../data-tools/how-to-add-global-queries-to-a-tableadapter.md).|  
|<xref:System.Data.DataTable>|Bir veritabanından döndürülen satırlar bir bellek içi koleksiyonunu temsil eder.|  
|İlişki (<xref:System.Data.DataRelation>)|İki üst-alt ilişkisi temsil <xref:System.Data.DataTable>s. Daha fazla bilgi için [DataRelation nesnelerine giriş](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192) ve [izlenecek yol: veri tabloları arasında ilişki oluşturma](http://msdn.microsoft.com/library/9b3f1c87-7098-4ed4-a710-cde8f8059f82).|  
  
> [!NOTE]
>  **Veri kümesi Tasarımcısı** bir temel alınan veritabanına bağlanır yalnızca bir veri kümesi oluşturulur; Tasarımcı otomatik olarak sonraki değişiklikler veritabanına algılamıyor. Mevcut bir .xsd yenilemek için yeniden çalıştırma **Yapılandırma Sihirbazı'nı**. Tablo ilişkileri değişip değişmediğini kaldırın ve ilgili tabloları için .xsd yeniden ekleyin.  
  
## <a name="linq-to-dataset"></a>LINQ to Dataset  
 [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] sağlar [LINQ (dil ile tümleşik sorgu)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) verileri üzerinde bir <xref:System.Data.DataSet> nesne. Daha fazla bilgi için [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: bir veri kümesi Tasarımcısı ile oluşturma](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)   
 [İzlenecek yol: bir TableAdapter ile birden çok sorgu oluşturma](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)   
 [İzlenecek yol: veri kümesi tasarımcısında DataTable oluşturma](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)   
 [İzlenecek yol: veri tabloları arasında ilişki oluşturma](http://msdn.microsoft.com/library/9b3f1c87-7098-4ed4-a710-cde8f8059f82)   
 [İzlenecek yol: Bir Windows formunda veri görüntüleme](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Visual Studio'da veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)   
 [Uygulamanızı veri almaya hazırlama](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Uygulamanıza veri getirme](../data-tools/fetching-data-into-your-application.md)   
 [Uygulamanızdaki verileri düzenleme](../data-tools/editing-data-in-your-application.md)   
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Verileri Kaydetme](../data-tools/saving-data.md)