---
title: Karmaşık veri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturun | Microsoft Docs
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
- data binding, complex
- user controls [Visual Studio], complex data binding
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: de22f93c6fd04f89360fdaf8a2f5d83bd373d93d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284264"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Karmaşık veri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Windows uygulamalarında formların üzerindeki verileri görüntülerken, mevcut denetimleri seçebilirsiniz **araç kutusu**, veya standart denetimlerinde kullanılamıyor işlevi uygulamanızı gerektiriyorsa, özel denetimler yazabilirsiniz. Bu izlenecek yol, uygulayan bir denetim oluşturma işlemi gösterilmektedir <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Denetimleri uygulayan <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> içeren bir `DataSource` ve `DataMember` verilere bağlı özelliği. Bu tür denetimler benzer bir <xref:System.Windows.Forms.DataGridView> veya <xref:System.Windows.Forms.ListBox>.  
  
 Denetim yazma ile ilgili daha fazla bilgi için bkz: [tasarım zamanında Windows Forms denetimleri geliştirme](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Veri bağlama senaryoları denetimler yazarken aşağıdaki veri bağlama özniteliklerden birini yapması gerekir:  
  
|Veri bağlama öznitelik kullanımı|  
|-----------------------------------|  
|Uygulama <xref:System.ComponentModel.DefaultBindingPropertyAttribute> basit denetimlerinde gibi bir <xref:System.Windows.Forms.TextBox>, tek bir sütun (veya özellik) veri görüntüler. Daha fazla bilgi için [basit veri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Uygulama <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> denetimler üzerinde gibi bir <xref:System.Windows.Forms.DataGridView>, veri listeleri'ı (veya tablo) görüntüler. (Bu işlem, bu izlenecek yol sayfasında açıklanmıştır.)|  
|Uygulama <xref:System.ComponentModel.LookupBindingPropertiesAttribute> denetimler üzerinde gibi bir <xref:System.Windows.Forms.ComboBox>, görünen veri listeleri (veya tablo) ancak tek bir sütun veya özelliği sunmak de gerekir. Daha fazla bilgi için [arama verileri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 Bu izlenecek yol, bir tablodaki veri satırlarının görüntüleyen bir karmaşık bir denetim oluşturur. Bu örnekte `Customers` Northwind örnek veritabanından tablo. Müşteriler tablosunda karmaşık kullanıcı denetiminin görüntüleyeceği bir <xref:System.Windows.Forms.DataGridView> özel denetimi.  
  
 Bu kılavuz boyunca, öğreneceksiniz nasıl yapılır:  
  
-   Yeni bir **Windows uygulama**.  
  
-   Yeni bir **kullanıcı denetimi** projenize.  
  
-   Görsel olarak kullanıcı denetiminin tasarım.  
  
-   Uygulama `ComplexBindingProperty` özniteliği.  
  
-   Bir veri kümesi oluşturmak [veri kaynağı Yapılandırma Sihirbazı](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Ayarlama **müşteriler** tablosundaki [veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) yeni karmaşık denetimi kullanmak için.  
  
-   Buradan sürükleyerek yeni denetim ekleme **veri kaynakları penceresi** üzerine **Form1**.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için şunlar gerekir:  
  
-   Northwind örnek veritabanına erişim. Daha fazla bilgi için [nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-a-windows-application"></a>Bir Windows uygulaması oluşturma  
 İlk adım oluşturmaktır bir **Windows uygulama**.  
  
#### <a name="to-create-the-new-windows-project"></a>Yeni Windows projesi oluşturmak için  
  
1.  Visual Studio'da gelen **dosya** menüsünden Yeni bir **proje**.  
  
2.  Projeyi adlandırın **ComplexControlWalkthrough**.  
  
3.  Seçin **Windows uygulama**, tıklatıp **Tamam**. Daha fazla bilgi için [istemci uygulamaları](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **ComplexControlWalkthrough** projesi oluşturulur ve eklenen **Çözüm Gezgini**.  
  
## <a name="add-a-user-control-to-the-project"></a>Projeye kullanıcı denetimi Ekle  
 Bu izlenecek yol, bir karmaşık veri bağlanabilir denetiminden oluşturduğundan bir **kullanıcı denetimi**, eklemelisiniz bir **kullanıcı denetimi** projeye öğe.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Projeye kullanıcı denetimi eklemek için  
  
1.  Gelen **proje** menüsünde seçin **kullanıcı denetimi Ekle**.  
  
2.  Tür **ComplexDataGridView** içinde **adı** alan ve ardından **Ekle**.  
  
     **ComplexDataGridView** denetim eklenir **Çözüm Gezgini**ve tasarımcıda açılır.  
  
## <a name="design-the-complexdatagridview-control"></a>Tasarım ComplexDataGridView denetimi  
 Bu adım ekler bir <xref:System.Windows.Forms.DataGridView> kullanıcı denetimi için.  
  
#### <a name="to-design-the-complexdatagridview-control"></a>Tasarım ComplexDataGridView denetimi  
  
-   Sürükleme bir <xref:System.Windows.Forms.DataGridView> gelen **araç kutusu** kullanıcı denetiminin tasarım yüzeyine.  
  
## <a name="add-the-required-data-binding-attribute"></a>Gerekli veri bağlama öznitelik Ekle  
 Karmaşık, destek veri bağlama denetimleri için uygulayabileceğiniz <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.  
  
#### <a name="to-implement-the-complexbindingproperties-attribute"></a>ComplexBindingProperties öznitelik uygulamak için  
  
1.  Anahtar **ComplexDataGridView** kod görünümü denetimi. (Üzerinde **görünümü** menüsünde **kod**.)  
  
2.  Değiştirin `ComplexDataGridView` aşağıdaki:  
  
     [!code-csharp[VbRaddataDisplaying#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs#4)]
     [!code-vb[VbRaddataDisplaying#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb#4)]  
  
3.  Gelen **derleme** menüsünde seçin **Çözümü Derle**.  
  
## <a name="creating-a-data-source-from-your-database"></a>Veritabanından veri kaynağı oluşturma  
 Bu adımı kullanan **veri kaynağı yapılandırması** bir veri kaynağı oluşturmak için Sihirbazı'nı temel alan `Customers` Northwind örnek veritabanındaki tablo. Bağlantı oluşturmak için Northwind örnek veritabanına erişiminiz olmalıdır. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz. [yüklemek SQL Server örnek veritabanları](../data-tools/install-sql-server-sample-databases.md).  
  
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
  
8.  Seçin `Customers` tablosunu ve ardından **son**.  
  
     **NorthwindDataSet** projenize eklenir ve `Customers` tablo görünür **veri kaynakları** penceresi.  
  
## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Müşteriler tablosu ComplexDataGridView denetimi kullanmak için ayarlama  
 İçinde **veri kaynakları** penceresindeki öğeleri formunuza sürükleyerek önce oluşturulacak denetimi ayarlayabilirsiniz.  
  
#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Müşteriler tablosundaki ComplexDataGridView denetime bağlama ayarlamak için  
  
1.  Açık **Form1** Tasarımcısı'nda.  
  
2.  Genişletin **müşteriler** düğümünde **veri kaynakları** penceresi.  
  
3.  Aşağı açılan oka tıklayın **müşteriler** düğümünü seçip **Özelleştir**.  
  
4.  Seçin **ComplexDataGridView** listesinden **ilişkili denetimler** içinde **veri kullanıcı Arabirimi özelleştirme seçenekleri** iletişim kutusu.  
  
5.  Aşağı açılan oka tıklayın `Customers` tablosuna sağ tıklayıp seçin **ComplexDataGridView** denetim listesinden.  
  
## <a name="addcontrols-to-the-form"></a>Forma Addcontrols  
 Öğe sürükleyerek veriye bağlı denetimler oluşturabilirsiniz **veri kaynakları** formunuza penceresi.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Form üzerinde veri bağlama denetimleri oluşturmak için  
  
-   Ana sürükleyin **müşteriler** düğümünden **veri kaynakları** forma penceresi. Doğrulayın **ComplexDataGridView** denetimi tablonun verilerini görüntülemek için kullanılır.  
  
## <a name="running-the-application"></a>Uygulamayı çalıştırma  
  
#### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için  
  
-   Uygulamayı çalıştırmak için F5 tuşuna basın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Uygulama gereksinimlerinize bağlı olarak veri bağlamasını destekleyen bir denetim oluşturma sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Tipik bir sonraki adımlardan birkaçı şunlardır:  
  
-   Diğer uygulamalarda yeniden kullanabilir, böylece bir denetim kitaplığı içinde özel kontrollerinizi yapılıyor.  
  
-   Arama senaryolarını desteklemek denetimler oluşturma. Daha fazla bilgi için [arama verileri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Windows Forms Denetimleri](http://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)

