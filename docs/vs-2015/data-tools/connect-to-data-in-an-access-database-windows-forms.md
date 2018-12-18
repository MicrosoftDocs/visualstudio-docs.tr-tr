---
title: (Windows Forms) bir erişim veritabanındaki verilere bağlanma | Microsoft Docs
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
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4741dedb907bb88513147a98b916831abd965576
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207356"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>(Windows Forms) bir erişim veritabanındaki verilere bağlanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual Studio kullanarak bir Access veritabanına (.mdf dosyası veya .accdb dosyası) bağlanabilirsiniz. Veri bağlantı tanımlandıktan sonra görünür **veri kaynakları** penceresi. Burada, tabloları veya görünümleri formlarınıza sürükleyebilirsiniz. Visual Studio'daki proje sisteminin bu yerel veritabanı dosyalarını nasıl yönettiğini anlamak istiyorsanız bkz [nasıl yapılır: Manage Local Data Files in Your Project](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu yordamları kullanmak için bir Windows Forms uygulaması projesi ve bir Access veritabanı (.accdb dosyası) veya bir Access 2000-2003 veritabanına (.mdb dosyası) gerekir. Dosya türünüze karşılık gelen yordamı izleyin.  
  
## <a name="creating-the-dataset-for-an-accdb-file"></a>.Accdb dosyası için veri kümesi oluşturma  
 Aşağıdaki yordamı kullanarak Access 2013, Office 365, Access 2010 veya Access 2007 ile oluşturulan veritabanlarına bağlanabilirsiniz.  
  
#### <a name="to-create-the-dataset"></a>Veri kümesi oluşturma  
  
1.  Verileri bağlamak istediğiniz Windows Forms uygulamasını açın.  
  
2.  Üzerinde **görünümü** menüsünde **diğer Windows** > **veri kaynakları**.  
  
     ![Diğer Windows veri kaynaklarını görüntülemek](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3.  İçinde **veri kaynakları** penceresinde tıklayın **yeni veri kaynağı Ekle**.  
  
     ![Yeni veri kaynağı Ekle](../data-tools/media/dataaddnewdatasource.png "dataAddNewDataSource")  
  
4.  Seçin **veritabanı** üzerinde **bir veri kaynağı türü seçin** sayfasında ve ardından **sonraki**.  
  
5.  Seçin **veri kümesi** üzerinde **veritabanı modeli seçin** sayfasında ve ardından **sonraki**.  
  
6.  Üzerinde **veri bağlantınızı seçin** sayfasında **yeni bağlantı** yeni bir veri bağlantısı yapılandırmak için.  
  
7.  Değişiklik **veri kaynağı** için **OLE DB için .NET Framework veri sağlayıcısı**.  
  
     ![OLE DB veri sağlayıcısı değiştirme](../data-tools/media/datachangedatasourceoledb.png "dataChangeDataSourceOLEDB")  
  
    > [!IMPORTANT]
    >  Veri kaynağını rağmen **Microsoft Access veritabanı dosyası (OLE DB)** görünse de doğru seçim gibi yalnızca .mdb veritabanı dosyaları için bu veri kaynağı türünü kullanın.  
  
8.  İçinde **OLE DB sağlayıcısı**seçin **Microsoft Office 12.0 Access veritabanı altyapısı OLE DB sağlayıcısı**.  
  
     ![OLE DB sağlayıcısı Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")  
  
9. İçinde **sunucu veya dosya adı**, bağlanma ve ardından istediğiniz .accdb dosyasının adını ve yolunu belirtin **Tamam**.  
  
    > [!NOTE]
    >  Veritabanı dosyası bir kullanıcı adı ve parola varsa, seçtiğiniz önce bunları belirtin **Tamam**.  
  
10. Seçin **sonraki** üzerinde **veri bağlantınızı seçin** sayfası.  
  
11. Seçin **sonraki** üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfası.  
  
12. Genişletin **tabloları** düğümde **veritabanı nesnelerinizi seçin** sayfası.  
  
13. Seçtiğiniz tabloları veya görünümleri kümenizde olmasını ve ardından seçin **son**.  
  
     Veri kümesi projenize eklenir ve tablolar ve görünümler görünür **veri kaynakları** penceresi.  
  
## <a name="creating-the-dataset-for-an-mdb-file"></a>.Mdb dosyası için veri kümesi oluşturma  
 Çalıştırarak veri kümesi oluşturma **veri kaynağı Yapılandırma Sihirbazı**.  
  
#### <a name="to-create-the-dataset"></a>Veri kümesi oluşturma  
  
1.  Verileri bağlamak istediğiniz Windows Forms uygulamasını açın.  
  
2.  Üzerinde **görünümü** menüsünde **diğer Windows** > **veri kaynakları**.  
  
     ![Diğer Windows veri kaynaklarını görüntülemek](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3.  İçinde **veri kaynakları** penceresinde tıklayın **yeni veri kaynağı Ekle**.  
  
4.  Seçin **veritabanı** üzerinde **bir veri kaynağı türü seçin** sayfasında ve ardından **sonraki**.  
  
5.  Seçin **veri kümesi** üzerinde **veritabanı modeli seçin** sayfasında ve ardından **sonraki**.  
  
6.  Üzerinde **veri bağlantınızı seçin** sayfasında **yeni bağlantı** yeni bir veri bağlantısı yapılandırmak için.  
  
7.  Veri kaynağı değilse **Microsoft Access veritabanı dosyası (OLE DB)** seçin **değişiklik** açmak için **değişimi veri kaynağı** seçin **Microsoft Veritabanı dosyası erişim**ve ardından **Tamam**.  
  
8.  İçinde **veritabanı dosyası adı**, bağlanma ve ardından istediğiniz .mdb dosyasının adını ve yolunu belirtin **Tamam**.  
  
     ![Bağlantı Access veritabanı dosyası ekleme](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")  
  
9. Seçin **sonraki** üzerinde **veri bağlantınızı seçin** sayfası.  
  
10. Seçin **sonraki** üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfası.  
  
11. Genişletin **tabloları** düğümde **veritabanı nesnelerinizi seçin** sayfası.  
  
12. Seçtiğiniz tabloları veya görünümleri kümenizde olmasını ve ardından seçin **son**.  
  
     Veri kümesi projenize eklenir ve tablolar ve görünümler görünür **veri kaynakları** penceresi.  
  
## <a name="security"></a>Güvenlik  
 Önemli bilgileri depolamak (örneğin bir parolayı), uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için [bağlantı bilgilerini koruma](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Yeni oluşturduğunuz veri kümesi kullanıma sunulduğunu **veri kaynakları** penceresi. Artık aşağıdaki görevlerden herhangi birini gerçekleştirebilirsiniz:  
  
-   Öğe seçin **veri kaynakları** penceresi ve bunları formunuza sürükleyin (bkz [Visual Studio'da verilere Windows Forms bağlama denetimleri](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).  
  
-   Veri kaynağında açın [veri kümesi Tasarımcısı](../data-tools/creating-and-editing-typed-datasets.md) eklemek veya veri kümesini oluşturan nesneleri düzenlemek için.  
  
-   Doğrulama mantığı eklemenize <xref:System.Data.DataTable.ColumnChanging> veya <xref:System.Data.DataTable.RowChanging> olay veri kümesindeki veri tablolarının (bkz [veri kümelerindeki verileri doğrulama](../data-tools/validate-data-in-datasets.md)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da verilere bağlanma](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Uygulamanızı veri almaya hazırlama](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Uygulamanıza veri getirme](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Uygulamanızdaki verileri düzenleme](../data-tools/editing-data-in-your-application.md)   
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Verileri kaydetme](../data-tools/saving-data.md)   
 [Veri izlenecek yollar](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)

