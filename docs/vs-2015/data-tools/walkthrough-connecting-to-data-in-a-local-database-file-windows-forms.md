---
title: 'İzlenecek yol: bir yerel veritabanı dosyası (Windows Forms) verilere bağlanma | Microsoft Docs'
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
- databases, connecting to
- local data, SQL Express
- SQL Express, walkthroughs
- SQL Express, connecting
- data [Visual Studio], local
- data [Visual Studio], connecting to SQL Express
ms.assetid: 5e16b7da-3fdc-4e69-bdb4-e8e700481811
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 71898c88a8d7a1d4a119a7e7a932e295ae12eb34
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176169"
---
# <a name="walkthrough-connecting-to-data-in-a-local-database-file-windows-forms"></a>İzlenecek yol: Yerel Veritabanı Dosyasındaki Verilere Bağlanma (Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir veri kümesi oluşturup uygulamanıza sınırlı veri denetimleri ekleyerek uygulamanızda yerel bir veritabanı dosyasından hızlı ve kolay bir şekilde veri alabilirsiniz. Bu izlenecek yolda adımları izleyerek oluşturduğunuz yerel veritabanı dosyasındaki verileri görüntüleyeceksiniz [Tasarımcı kullanarak bir SQL veritabanı oluşturma](../data-tools/create-a-sql-database-by-using-a-designer.md). Windows Forms projesi oluşturduktan sonra, bu veritabanına bağlanıp Müşteriler tablosundaki verilerin uygulama için formda veri kılavuzunda görüntülenmesini istediğinizi belirtebilirsiniz.  
  
 Visual Studio 2013 içinde veritabanı oluşturduğunuzda, SQL Server Express LocalDB altyapısı kullanılarak SQL Server 2012 içinde bir veritabanı dosyasına (.mdf) erişilir. Visual Studio'nun eski sürümlerinde veritabanı dosyasına (.mdf) erişmek için SQL Server Express altyapısı kullanılıyordu. Bkz: [yerel verilere genel bakış](../data-tools/local-data-overview.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
 Bu izlenecek yol aşağıdaki görevleri içerir:  
  
-   [Oluşturma ve bir veri kümesi yapılandırma](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_CreateDataset)  
  
-   [Verilere bağlı denetimler ekleme](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_AddCtrls)  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için tamamlayarak oluşturduğunuz SampleDatabase.mdf veritabanına erişmeniz [Tasarımcı kullanarak bir SQL veritabanı oluşturma](../data-tools/create-a-sql-database-by-using-a-designer.md).  
  
##  <a name="BKMK_CreateDataset"></a> Oluşturma ve bir veri kümesi yapılandırma  
  
#### <a name="to-create-and-configure-a-dataset"></a>Veri kümesi oluşturmak ve yapılandırmak için  
  
1.  Bir Windows Forms projesi oluşturun ve adlandırın **ConnectLocalData**.  
  
     Bkz: [istemci uygulamaları](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
2.  Varsa **veri kaynakları** penceresi görüntülenmiyorsa, Shift-Alt-D tuşlarını seçin veya menü çubuğunda, **görünümü**, **diğer Windows**, **verikaynaklarınıGöster**.  
  
3.  İçinde **veri kaynakları** penceresinde seçin **yeni veri kaynağı Ekle** bağlantı.  
  
     İçinde **veri kaynağı Yapılandırma Sihirbazı**, seçin **sonraki** düğmesini iki kez varsayılan ayarları kabul edin.  
  
4.  Üzerinde **veri bağlantınızı seçin** sayfasında **yeni bağlantı** düğmesi.  
  
     **Veri kaynağı Seç** iletişim kutusu görüntülenir.  
  
5.  İçinde **veri kaynağı** listesinde **Microsoft SQL Server veritabanı dosyası**ve ardından **devam** düğmesi.  
  
     **Bağlantı Ekle** iletişim kutusu görüntülenir.  
  
6.  İçinde **veritabanı dosyası adı** kutusunda, tamamlayarak oluşturduğunuz dosyayı belirtin [Tasarımcı kullanarak bir SQL veritabanı oluşturma](../data-tools/create-a-sql-database-by-using-a-designer.md), ya da seçin **Gözat** düğmesine tıklayın ve ardından bulun Bu dosya.  
  
     Varsayılan olarak, kullanıcıların dosyadır\\*hesabınız*\Documents\Visual Studio *sürüm*\Projects\SampleDatabaseWalkthrough\SampleDatabaseWalkthrough.  
  
7.  Altında **sunucuda oturum açın**, varsayılan değerleri kabul edin, seçin **Tamam** düğmesine ve ardından **sonraki** düğmesi.  
  
    > [!NOTE]
    >  Bir yerel veritabanı dosyasına bağlandığınızda, projenizde bir veritabanının kopyasını oluşturabilir veya geçerli konumdaki veritabanı dosyasına bağlanabilirsiniz. Bkz: [nasıl yapılır: projenizdeki yerel veri dosyalarını yönetme](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
8.  Görünen iletişim kutusunda **Evet** veritabanı dosyasını projenize kopyalamak için.  
  
9. Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfasında **sonraki** düğmesi.  
  
10. Üzerinde **veritabanı nesnelerinizi seçin** sayfasında **tabloları** düğümünü **müşteriler** ve **siparişler** onay kutularını ve sonra seçin **son** düğmesi.  
  
     **SampleDatabaseDataSet** projenize eklenir ve **müşteriler** ve **siparişler** tablolar görünür **veri kaynakları** penceresi.  
  
##  <a name="BKMK_AddCtrls"></a> Verilere bağlı denetimler ekleme  
  
#### <a name="to-add-data-bound-controls"></a>Verilere bağlı denetimler eklemek için  
  
1.  Ana taşıma **müşteriler** düğümünden **veri kaynakları** penceresinden **Form1**.  
  
     A <xref:System.Windows.Forms.DataGridView> ve araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) Kayıtlarda gezinmek için formda görünür. A [SampleDatabaseDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.  
  
2.  Uygulamayı çalıştırmak ve önceki yönergelerde eklediğiniz verileri göstermek için F5 tuşuna basın.  
  
3.  Sarı ekleme simgesini (![Windows formu Ekle düğmesini](../data-tools/media/addrecord.png "AddRecord")), bir müşteri kaydı ekleyin ve sonra disk simgesini seçerek değişikliklerinizi kaydedin (![Windows formundaKaydetdüğmesi](../data-tools/media/saveinwf.png "SaveInWF")).  
  
4.  Bunu seçerek ve sonra kırmızı Sil simgesini seçerek yeni oluşturduğunuz kaydı silmek (![Windows formunu Sil düğmesini](../data-tools/media/deleterecord.png "KayıtSil")).  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Oluşturabilir veya veri kaynağındaki açarsanız kümesindeki nesneleri değiştirmek [oluşturma ve yazılan veri kümelerini düzenleme](../data-tools/creating-and-editing-typed-datasets.md). Doğrulama mantığını ayrıca ekleyebilirsiniz <xref:System.Data.DataTable.ColumnChanging> veya <xref:System.Data.DataTable.RowChanging> veri kümesindeki veri tablolarının olayları. Bkz: [veri kümelerindeki verileri doğrulama](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel verilere genel bakış](../data-tools/local-data-overview.md)   
 [Nasıl yapılır: projenizdeki yerel veri dosyalarını yönetme](../data-tools/how-to-manage-local-data-files-in-your-project.md)   
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio'da verilere bağlanma](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Uygulamanızı veri almaya hazırlama](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Uygulamanıza veri getirme](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Uygulamanızdaki verileri düzenleme](../data-tools/editing-data-in-your-application.md)   
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Verileri Kaydetme](../data-tools/saving-data.md)