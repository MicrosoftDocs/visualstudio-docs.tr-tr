---
title: 'İzlenecek yol: veri kümesi tasarımcısında DataTable oluşturma | Microsoft Docs'
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
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 1f0f31528239794b9c7a3b4a4bf98542ed4bbcf2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49299968"
---
# <a name="walkthrough-creating-a-datatable-in-the-dataset-designer"></a>İzlenecek Yol: Veri Kümesi Tasarımcısında DataTable Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yolda nasıl oluşturulacağını açıklar bir <xref:System.Data.DataTable> (olmadan bir TableAdapter) kullanarak **veri kümesi Tasarımcısı**. TableAdapter'ları içeren veri tabloları oluşturma hakkında daha fazla bilgi için bkz. [oluştur ve TableAdapter yapılandırma](../data-tools/create-and-configure-tableadapters.md).  
  
 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:  
  
-   Yeni bir Windows uygulaması projesi oluşturma  
  
-   Yeni bir veri kümesi için uygulama ekleme  
  
-   Veri kümesine yeni bir veri tablosu ekleme  
  
-   Veri tablosuna sütun ekleme  
  
-   Tablo için birincil anahtar ayarlama  
  
## <a name="creating-a-new-windows-application"></a>Yeni bir Windows uygulaması oluşturma  
  
#### <a name="to-create-a-new-windows-application-project"></a>Yeni bir Windows uygulaması projesi oluşturmak için  
  
1.  Gelen **dosya** menüsünden Yeni bir proje oluşturun.  
  
2.  Bir programlama dili seçin **proje türleri** bölmesi.  
  
3.  Tıklayın **Windows uygulama** içinde **şablonları** bölmesi.  
  
4.  Projeyi adlandırın `DataTableWalkthrough`ve ardından **Tamam**.  
  
     Visual Studio projeyi ekler **Çözüm Gezgini** ve görüntüler **Form1** Tasarımcısı'nda.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Yeni bir veri kümesi için uygulama ekleme  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Projeye yeni bir veri kümesi öğe eklemek için  
  
1.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.  
  
     Yeni öğe iletişim kutusunu görünür.  
  
2.  İçinde **şablonları** kutusunda **veri kümesi**.  
  
3.  **Ekle**'yi tıklatın.  
  
     Visual Studio'ya adlı bir dosya ekleyin **dataSet1.xsd dosyasını** projeye ve açılır **veri kümesi Tasarımcısı**.  
  
## <a name="adding-a-new-datatable-to-the-dataset"></a>Veri kümesine yeni bir DataTable ekleme  
  
#### <a name="to-add-a-new-data-table-to-the-dataset"></a>Yeni bir veri tablosu veri kümesine eklemek için  
  
1.  Sürükleme bir **DataTable** gelen **veri kümesi** sekmesinde **araç kutusu** üzerine **veri kümesi Tasarımcısı**.  
  
     Adlı bir tablo **DataTable1** veri kümesine eklenir.  
  
    > [!NOTE]
    >  Bir TableAdapter'ı içeren bir veri tablosu oluşturmak için bkz [izlenecek yol: birden çok sorgu içeren bir TableAdapter oluşturma](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md).  
  
2.  Başlık çubuğuna tıklayın **DataTable1** ve yeniden adlandırmak `Music`.  
  
## <a name="adding-columns-to-the-data-table"></a>Veri tablosuna sütun ekleme  
  
#### <a name="to-add-columns-to-the-data-table"></a>Veri tablosuna sütun eklemek için  
  
1.  Sağ **müzik** tablo. İşaret **Ekle**ve ardından **sütun**.  
  
2.  Sütun adı `SongID`.  
  
3.  İçinde **özellikleri** penceresinde <xref:System.Data.DataColumn.DataType%2A> özelliğini <xref:System.Int16?displayProperty=fullName>.  
  
4.  Bu işlemi tekrarlayın ve aşağıdaki sütunları ekleyin:  
  
     `SongTitle`: <xref:System.String?displayProperty=fullName>  
  
     `Artist`: <xref:System.String?displayProperty=fullName>  
  
     `Genre`: <xref:System.String?displayProperty=fullName>  
  
## <a name="setting-the-primary-key-for-the-table"></a>Tablo için birincil anahtar ayarlama  
 Tüm veri tablolarının birincil anahtarı olmalıdır. Bir birincil anahtar, bir veri tablosu belirli bir kaydı benzersiz olarak tanımlar.  
  
#### <a name="to-set-the-primary-key-of-the-data-table"></a>Veri tablosunun birincil anahtarını ayarlamak için  
  
-   Sağ **SongID** sütun ve ardından **birincil anahtarı Ayarla**.  
  
     Bir anahtar simgesi görünür **SongID** sütun.  
  
## <a name="saving-your-project"></a>Projenizi kaydetme  
  
#### <a name="to-save-the-datatablewalkthrough-project"></a>DataTableWalkthrough projeyi kaydetmek için  
  
-   Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet**.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Tablo oluşturduğunuza göre aşağıdaki eylemlerden birini gerçekleştirmek isteyebilirsiniz:  
  
|Bitiş|Bkz. |  
|--------|---------|  
|Veri girişi için form oluşturma|[İzlenecek yol: Bir Windows formunda veri görüntüleme](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).|  
|Tabloya veri ekleme|[Bir DataTable tablosuna veri ekleme](http://msdn.microsoft.com/library/d6aa8474-7bde-48f7-949d-20dc38a1625b).|  
|Bir tablodaki verileri görüntüle|[DataTable'daki verileri görüntüleme](http://msdn.microsoft.com/library/1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc).|  
|Verileri düzenleme|[DataTable Düzenlemeleri](http://msdn.microsoft.com/library/f08008a9-042e-4de9-94f3-4f0e502b1eb5)|  
|Tablodan bir satır silme|[DataRow Silme](http://msdn.microsoft.com/library/c34f531d-4b9b-4071-b2d7-342c402aa586)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da verilere bağlanma](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Uygulamanızı veri almaya hazırlama](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Uygulamanıza veri getirme](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Uygulamanızdaki verileri düzenleme](../data-tools/editing-data-in-your-application.md)   
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Verileri kaydetme](../data-tools/saving-data.md)   
 [Veri izlenecek yollar](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)