---
title: (Windows Forms) bir erişim veritabanındaki verilere bağlanma
ms.date: 09/15/2017
ms.topic: conceptual
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 33981ac76d8c502d56571a112ee8cd1e0c11dce0
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304590"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>(Windows Forms) bir erişim veritabanındaki verilere bağlanma

Bir Access veritabanına bağlanabilir (ya da bir *.mdf* dosya veya bir *.accdb* dosya) Visual Studio kullanarak. Veri bağlantı tanımlandıktan sonra görünür **veri kaynakları** penceresi. Burada, tabloları veya görünümleri formlarınıza sürükleyebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

Bu yordamları kullanmak için bir Windows Forms uygulaması projesi ve bir Access veritabanı gerekir (*.accdb* dosyası) veya bir Access 2000-2003 veritabanına (*.mdb* dosyası). Dosya türünüze karşılık gelen yordamı izleyin.

## <a name="creating-the-dataset-for-an-accdb-file"></a>.Accdb dosyası için veri kümesi oluşturma

Aşağıdaki yordamı kullanarak Access 2013, Office 365, Access 2010 veya Access 2007 ile oluşturulan veritabanlarına bağlanabilirsiniz.

### <a name="to-create-the-dataset"></a>Veri kümesi oluşturma

1.  Verileri bağlamak istediğiniz Windows Forms uygulamasını açın.

2.  Açmak için **veri kaynakları** penceresi, **görünümü** menüsünde **diğer Windows** > **veri kaynakları**.

     ![Diğer Windows veri kaynaklarını görüntüleyin](../data-tools/media/viewdatasources.png)

3.  İçinde **veri kaynakları** penceresinde tıklayın **yeni veri kaynağı Ekle**.

     **Veri kaynağı Yapılandırma Sihirbazı** açılır.

4.  Seçin **veritabanı** üzerinde **bir veri kaynağı türü seçin** sayfasında ve ardından **sonraki**.

5.  Seçin **veri kümesi** üzerinde **veritabanı modeli seçin** sayfasında ve ardından **sonraki**.

6.  Üzerinde **veri bağlantınızı seçin** sayfasında **yeni bağlantı** yeni bir veri bağlantısı yapılandırmak için.

     **Bağlantı Ekle** iletişim kutusu açılır.

7.  Seçin **değişiklik** düğmesinin yanındaki **veri kaynağı** metin kutusu.

     **Değişimi veri kaynağı** iletişim kutusu açılır.

8.  Veri Kaynakları listesinde seçin  **\<diğer\>**. İçinde **veri sağlayıcısı** açılan listesinde, select **OLE DB için .NET Framework veri sağlayıcısı**, ardından **Tamam**.

9. Geri **Bağlantı Ekle** iletişim kutusunda **Microsoft Office 12.0 Access veritabanı altyapısı OLE DB sağlayıcısı** gelen **OLE DB sağlayıcısı** açılır.

     ![OLE DB sağlayıcısı Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png)

     > [!NOTE]
     > Görmüyorsanız **Microsoft Office 12.0 Access veritabanı altyapısı OLE DB sağlayıcısı** OLE DB Sağlayıcısında açılan yüklemeniz gerekebilir [2007 Office sistemi sürücüsü: veri bağlantısı bileşenlerinin](https://www.microsoft.com/download/confirmation.aspx?id=23734).

9. İçinde **sunucu veya dosya adı** metin kutusuna yolunu belirtin ve dosya adını *.accdb* bağlanın ve ardından istediğiniz dosyasını **Tamam**. (Veritabanı dosyasının bir kullanıcı adı ve parola varsa, seçtiğiniz önce bunları belirtin **Tamam**.)

10. Seçin **sonraki** üzerinde **veri bağlantınızı seçin** sayfası.

     Veri dosyası değil geçerli projenizde bildiren bir iletişim kutusu alabilirsiniz. Seçin **Evet** veya **Hayır**.

11. Seçin **sonraki** üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfası.

12. Genişletin **tabloları** düğümde **veritabanı nesnelerinizi seçin** sayfası.

13. Seçtiğiniz tabloları veya görünümleri kümenizde olmasını ve ardından seçin **son**.

     Veri kümesi projenize eklenir ve tablolar ve görünümler görünür **veri kaynakları** penceresi.

## <a name="create-the-dataset-for-an-mdb-file"></a>Bir .mdb dosyası için veri kümesi oluşturma

Çalıştırarak veri kümesi oluşturma **veri kaynağı Yapılandırma Sihirbazı**.

### <a name="to-create-the-dataset"></a>Veri kümesi oluşturma

1.  Verileri bağlamak istediğiniz Windows Forms uygulamasını açın.

2.  Üzerinde **görünümü** menüsünde **diğer Windows** > **veri kaynakları**.

     ![Diğer Windows veri kaynaklarını görüntüleyin](../data-tools/media/viewdatasources.png)

3.  İçinde **veri kaynakları** penceresinde tıklayın **yeni veri kaynağı Ekle**.

     **Veri kaynağı Yapılandırma Sihirbazı** açılır.

4.  Seçin **veritabanı** üzerinde **bir veri kaynağı türü seçin** sayfasında ve ardından **sonraki**.

5.  Seçin **veri kümesi** üzerinde **veritabanı modeli seçin** sayfasında ve ardından **sonraki**.

6.  Üzerinde **veri bağlantınızı seçin** sayfasında **yeni bağlantı** yeni bir veri bağlantısı yapılandırmak için.

7.  Veri kaynağı değilse **Microsoft Access veritabanı dosyası (OLE DB)** seçin **değişiklik** açmak için **değişimi veri kaynağı** seçin **Microsoft Veritabanı dosyası erişim**ve ardından **Tamam**.

8.  İçinde **veritabanı dosyası adı**, adını ve yolunu belirtin *.mdb* bağlanın ve ardından istediğiniz dosyasını **Tamam**.

     ![Bağlantı Access veritabanı dosyası ekleme](../data-tools/media/dataaddconnectionaccessmdb.png)

9. Seçin **sonraki** üzerinde **veri bağlantınızı seçin** sayfası.

10. Seçin **sonraki** üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfası.

11. Genişletin **tabloları** düğümde **veritabanı nesnelerinizi seçin** sayfası.

12. Seçtiğiniz tabloları veya görünümleri kümenizde olmasını ve ardından seçin **son**.

     Veri kümesi projenize eklenir ve tablolar ve görünümler görünür **veri kaynakları** penceresi.

## <a name="security"></a>Güvenlik

Önemli bilgileri depolamak (örneğin bir parolayı), uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için [bağlantı bilgilerini koruma](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="next-steps"></a>Sonraki adımlar

Yeni oluşturduğunuz veri kümesi kullanıma sunulduğunu **veri kaynakları** penceresi. Artık aşağıdaki görevlerden herhangi birini gerçekleştirebilirsiniz:

-   Öğe seçin **veri kaynakları** penceresi ve bunları formunuza sürükleyin (bkz [Visual Studio'da verilere Windows Forms bağlama denetimleri](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).

-   Veri kaynağında açın **veri kümesi Tasarımcısı** eklemek veya veri kümesini oluşturan nesneleri düzenlemek için.

-   Doğrulama mantığı eklemenize <xref:System.Data.DataTable.ColumnChanging> veya <xref:System.Data.DataTable.RowChanging> olay veri kümesindeki veri tablolarının (bkz [veri kümelerindeki verileri doğrulama](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı ekleme](../data-tools/add-new-connections.md)