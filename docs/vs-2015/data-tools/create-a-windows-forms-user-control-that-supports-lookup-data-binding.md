---
title: Arama verileri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturun | Microsoft Docs
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
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6a1393f45c46709e4085d7e170265b92c6e00266
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219490"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Arama verileri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Windows Forms'ta veri görüntüleme, mevcut denetimleri seçebilirsiniz **araç kutusu**, veya uygulamanıza işlevsellik standart denetimleri yok gerekiyorsa özel denetimler yazabilirsiniz. Bu izlenecek yol, uygulayan bir denetim oluşturma işlemi gösterilmektedir <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. Denetimleri uygulayan <xref:System.ComponentModel.LookupBindingPropertiesAttribute> verilere bağlı üç özellik içerebilir. Bu tür denetimler benzer bir <xref:System.Windows.Forms.ComboBox>.  
  
 Denetim yazma ile ilgili daha fazla bilgi için bkz: [tasarım zamanında Windows Forms denetimleri geliştirme](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Veri bağlama senaryoları denetimler yazarken aşağıdaki veri bağlama özniteliklerden birini yapması gerekir:  
  
|Veri bağlama öznitelik kullanımı|  
|-----------------------------------|  
|Uygulama <xref:System.ComponentModel.DefaultBindingPropertyAttribute> basit denetimlerinde gibi bir <xref:System.Windows.Forms.TextBox>, tek bir sütun (veya özellik) veri görüntüler. Daha fazla bilgi için [basit veri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Uygulama <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> denetimler üzerinde gibi bir <xref:System.Windows.Forms.DataGridView>, veri listeleri'ı (veya tablo) görüntüler. Daha fazla bilgi için [karmaşık veri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Uygulama <xref:System.ComponentModel.LookupBindingPropertiesAttribute> denetimler üzerinde gibi bir <xref:System.Windows.Forms.ComboBox>, veri listeleri (veya tablo) görüntüler, ancak tek bir sütun veya özelliği sunmak de gerekir. (Bu işlem, bu izlenecek yol sayfasında açıklanmıştır.)|  
  
 Bu kılavuz iki tablodaki verilere bağlanan bir arama denetimi oluşturur. Bu örnekte `Customers` ve `Orders` Northwind örnek veritabanındaki tablolar. Arama denetimine bağlı `CustomerID` alanını `Orders` tablo. Aramak için bu değeri kullanır `CompanyName` gelen `Customers` tablo.  
  
 Bu kılavuz boyunca, öğreneceksiniz nasıl yapılır:  
  
-   Yeni bir **Windows uygulama**.  
  
-   Yeni bir **kullanıcı denetimi** projenize.  
  
-   Görsel olarak kullanıcı denetiminin tasarım.  
  
-   Uygulama `LookupBindingProperty` özniteliği.  
  
-   Bir veri kümesi oluşturmak **veri kaynağı yapılandırması** Sihirbazı.  
  
-   Ayarlama **CustomerID** sütunu **siparişler** tablosu **veri kaynakları** penceresinde yeni denetimi kullanmak için.  
  
-   Verileri yeni denetimde görüntülemek için bir form oluşturun.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için şunlar gerekir:  
  
-   Northwind örnek veritabanına erişim.  
  
## <a name="create-a-windows-application"></a>Bir Windows uygulaması oluşturma  
 İlk adım oluşturmaktır bir **Windows uygulama**.  
  
#### <a name="to-create-the-new-windows-project"></a>Yeni Windows projesi oluşturmak için  
  
1.  Visual Studio'da gelen **dosya** menüsünden Yeni bir **proje**.  
  
2.  Projeyi adlandırın **LookupControlWalkthrough**.  
  
3.  Seçin **Windows Forms uygulaması**, tıklatıp **Tamam**.  
  
     **LookupControlWalkthrough** projesi oluşturulur ve eklenen **Çözüm Gezgini**.  
  
## <a name="add-a-user-control-to-the-project"></a>Projeye kullanıcı denetimi Ekle  
 Bu izlenecek yol, bir arama denetimi oluşturur bir **kullanıcı denetimi**, bu nedenle ekleyin bir **kullanıcı denetimi** öğesinin **LookupControlWalkthrough** proje.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Projeye kullanıcı denetimi eklemek için  
  
1.  Gelen **proje** menüsünde **kullanıcı denetimi Ekle**.  
  
2.  Tür `LookupBox` içinde **adı** alan ve ardından **Ekle**.  
  
     **LookupBox** denetim eklenir **Çözüm Gezgini**ve tasarımcıda açılır.  
  
## <a name="design-the-lookupbox-control"></a>Tasarım LookupBox denetimi  
  
#### <a name="to-design-the-lookupbox-control"></a>Tasarım LookupBox denetimi  
  
-   Sürükleme bir <xref:System.Windows.Forms.ComboBox> gelen **araç kutusu** kullanıcı denetiminin tasarım yüzeyine.  
  
## <a name="add-the-required-data-binding-attribute"></a>Gerekli veri bağlama öznitelik Ekle  
 Arama söz konusu destek veri bağlama denetimleri için uygulayabileceğiniz <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.  
  
#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>LookupBindingProperties öznitelik uygulamak için  
  
1.  Anahtar **LookupBox** kod görünümü denetimi. (Üzerinde **görünümü** menüsünde seçin **kod**.)  
  
2.  Değiştirin `LookupBox` aşağıdaki:  
  
     [!code-csharp[VbRaddataDisplaying#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/LookupBox.cs#5)]
     [!code-vb[VbRaddataDisplaying#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/LookupBox.vb#5)]  
  
3.  Gelen **derleme** menüsünde seçin **Çözümü Derle**.  
  
## <a name="create-a-data-source-from-your-database"></a>Veritabanından bir veri kaynağı oluşturun  
 Bu adımda, bir veri kaynağı kullanılarak oluşturulur **veri kaynağı yapılandırması** Sihirbazı temel `Customers` ve `Orders` Northwind örnek veritabanındaki tablolar. Bağlantı oluşturmak için Northwind örnek veritabanına erişiminiz olmalıdır. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz. [yüklemek SQL Server örnek veritabanları](../data-tools/install-sql-server-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için  
  
1.  Üzerinde **veri** menüsünü tıklatın **veri kaynaklarını Göster**.  
  
2.  İçinde **veri kaynakları** penceresinde **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı yapılandırması** Sihirbazı.  
  
3.  Seçin **veritabanı** üzerinde **bir veri kaynağı türü seçin** sayfasında ve ardından **sonraki**.  
  
4.  Üzerinde **veri bağlantınızı seçin** sayfasında aşağıdakilerden birini yapın:  
  
    -   Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.  
  
    -   Seçin **yeni bağlantı** başlatmak için **Bağlantı Ekle/Değiştir** iletişim kutusu.  
  
5.  Veritabanınız parola gerektiriyorsa, hassas verileri eklemek ve ardından seçeneğini **sonraki**.  
  
6.  Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfasında **sonraki**.  
  
7.  Üzerinde **veritabanı nesnelerinizi seçin** sayfasında **tabloları** düğümü.  
  
8.  Seçin `Customers` ve `Orders` tablolar ve ardından **son**.  
  
     **NorthwindDataSet** projenize eklenir ve `Customers` ve `Orders` tablolar görünür **veri kaynakları** penceresi.  
  
## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>LookupBox denetimi kullanmak için Siparişler tablosunun CustomerID sütununda ayarlayın  
 İçinde **veri kaynakları** penceresindeki öğeleri formunuza sürükleyerek önce oluşturulacak denetimi ayarlayabilirsiniz.  
  
#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>LookupBox denetime bağlanacak CustomerID sütununda ayarlamak için  
  
1.  Açık **Form1** Tasarımcısı'nda.  
  
2.  Genişletin **müşteriler** düğümünde **veri kaynakları** penceresi.  
  
3.  Genişletin **siparişler** düğümü (bir **müşteriler** düğümünün altındaki **faks** sütunu).  
  
4.  Aşağı açılan oka tıklayın **siparişler** düğümünü seçip **ayrıntıları** denetim listesinden.  
  
5.  Aşağı açılan oka tıklayın **CustomerID** sütun (içinde **siparişler** düğümü) ve **Özelleştir**.  
  
6.  Seçin **LookupBox** listesinden **ilişkili denetimler** içinde **veri kullanıcı Arabirimi özelleştirme seçenekleri** iletişim kutusu.  
  
7.  **Tamam**'ı tıklatın.  
  
8.  Aşağı açılan oka tıklayın **CustomerID** sütunu seçip **LookupBox**.  
  
## <a name="addcontrols-to-the-form"></a>Forma Addcontrols  
 Öğe sürükleyerek veriye bağlı denetimler oluşturabilirsiniz **veri kaynakları** penceresinden **Form1**.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Windows Form üzerindeki verilere bağlı denetimler oluşturmak için  
  
-   Sürükle **siparişler** düğümünden **veri kaynakları** penceresinden Windows Form doğrulayın **LookupBox** denetim verileri görüntülemek için kullanılan `CustomerID` sütun.  
  
## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Müşteriler tablosundan CompanyName ' aramak için denetim bağlama  
  
#### <a name="to-setup-the-lookup-bindings"></a>Arama bağlantıları kurmak için  
  
-   Ana seçin **müşteriler** düğümünde **veri kaynakları** penceresi ve üzerine birleşik giriş kutusunda Sürükle **CustomerIDLookupBox** üzerinde **Form1** .  
  
     Görüntülenecek veri bağlamasını ayarlamak ayarlar bu `CompanyName` gelen `Customers` sürdürürken tablo `CustomerID` değerini `Orders` tablo.  
  
## <a name="running-the-application"></a>Uygulamayı çalıştırma  
  
#### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için  
  
-   Uygulamayı çalıştırmak için F5 tuşuna basın.  
  
-   Bazı kayıtlarda gezinmek ve doğrulayın `CompanyName` görünür `LookupBox` denetimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

