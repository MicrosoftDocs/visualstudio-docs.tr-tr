---
title: Bir veri kümesine WPF denetimleri bağlama | Microsoft Docs
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
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9b77e8211d8f76627f16f96abed8a61e6dae03d7
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219802"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Bir veri kümesine WPF denetimleri bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bu kılavuzda, verilere bağlı denetimler içeren bir WPF uygulaması oluşturacaksınız. Denetimler bir veri kümesinde kapsüllenmiş ürün kayıtları bağlıdır. Ayrıca, ürünlere göz atabilir ve ürün kayıtları için değişiklikleri kaydetmek için düğmeler ekleyeceksiniz.  
  
 Bu izlenecek yol aşağıdaki görevleri gösterir:  
  
- Bir WPF uygulamasını ve verileri AdventureWorksLT örnek veritabanını kullanarak oluşturulan bir veri kümesi oluşturma.  
  
- Bir veri tablosundan sürükleyerek veriye bağlı denetimler kümesini oluşturma **veri kaynakları** WPF Tasarımcısı penceresinde penceresine.  
  
- Ürün kayıtlarında ileriye ve geriye doğru gezinmek düğmeleri oluşturuluyor.  
  
- Bir düğme oluşturma, veri tablosu ve temel alınan veri kaynağı için ürün kayıtları kullanıcılar yaptığınız değişiklikleri kaydeder.  
  
   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
- Çalışan bir SQL Server veya SQL Server bağlı AdventureWorksLT örnek veritabanı içeren bir Express örneğine erişim. AdventureWorksLT veritabanı indirebileceğiniz [CodePlex Web site](http://go.microsoft.com/fwlink/?linkid=87843).  
  
  Aşağıdaki kavramları bilgisi de faydalıdır, ancak izlenecek yolu tamamlamak için gerekli değil:  
  
- Veri kümeleri ve TableAdapters öğelerini. Daha fazla bilgi için [Visual Studio'daki veri kümesi Araçları](../data-tools/dataset-tools-in-visual-studio.md) ve [TableAdapter genel bakışı](../data-tools/tableadapter-overview.md).  
  
- WPF Tasarımcısı ile çalışma. Daha fazla bilgi için [WPF ve Silverlight Tasarımcısı genel bakış](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
- WPF veri bağlaması. Daha fazla bilgi için [Data Binding Overview](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).  
  
## <a name="create-the-project"></a>Projeyi oluşturma  
 Yeni bir WPF projesi oluşturun. Proje ürün kayıtları görüntüler.  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  Visual Studio'yu başlatın.  
  
2.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.  
  
3.  Genişletin **Visual Basic** veya **Visual C#** ve ardından **Windows**.  
  
4.  Seçin **WPF uygulaması** proje şablonu.  
  
5.  İçinde **adı** kutusuna `AdventureWorksProductsEditor` tıklatıp **Tamam**.  
  
     Visual Studio oluşturur `AdventureWorksProductsEditor` proje.  
  
## <a name="create-a-dataset-for-the-application"></a>Uygulama için bir veri kümesi oluşturma  
 Verilere bağlı denetimler oluşturabilmeniz için uygulamanız için bir veri modeli tanımlamanızı ve kendisine eklemeniz gerekir **veri kaynakları** penceresi. Bu izlenecek yolda veri modeli olarak kullanılacak bir veri kümesi oluşturun.  
  
#### <a name="to-create-a-dataset"></a>Bir veri kümesini oluşturmak için  
  
1.  Üzerinde **veri** menüsünü tıklatın **veri kaynaklarını Göster**.  
  
     **Veri kaynakları** penceresi açılır.  
  
2.  İçinde **veri kaynakları** penceresinde tıklayın **yeni veri kaynağı Ekle**.  
  
     **Veri kaynağı yapılandırması** Sihirbazı açılır.  
  
3.  Üzerinde **bir veri kaynağı türü seçin** sayfasında **veritabanı**ve ardından **sonraki**.  
  
4.  Üzerinde **veritabanı modeli seçin** sayfasında **veri kümesi**ve ardından **sonraki**.  
  
5.  Üzerinde **veri bağlantınızı seçin** sayfasında, aşağıdaki seçeneklerden birini seçin:  
  
    -   AdventureWorksLT örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir haldeyse, onu seçin ve ardından **sonraki**.  
  
    -   Tıklayın **yeni bağlantı**ve AdventureWorksLT veritabanına bağlantı oluşturun.  
  
6.  Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfasında **Evet, bağlantıyı bu adla Kaydet** onay kutusunu işaretleyin ve ardından **sonraki**.  
  
7.  Üzerinde **veritabanı nesnelerinizi seçin** sayfasında **tabloları**ve ardından **ürün (SalesLT)** tablo.  
  
8.  **Son**'a tıklayın.  
  
     Visual Studio, projeye yeni bir AdventureWorksLTDataSet.xsd dosyası ekler ve ilgili ekler **AdventureWorksLTDataSet** öğesinin **veri kaynakları** penceresi. AdventureWorksLTDataSet.xsd dosyası adlı bir türü belirtilmiş veri kümesi tanımlar `AdventureWorksLTDataSet` ve adlı bir TableAdapter `ProductTableAdapter`. Bu kılavuzda daha sonra kullanacağınız `ProductTableAdapter` veri kümesini verilerle doldurma ve değişiklikleri veritabanına geri kaydedin.  
  
9. Projeyi oluşturun.  
  
## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>TableAdapter'ın varsayılan dolgu yöntemi Düzenle  
 Veri kümesini verilerle doldurmak için kullanın `Fill` yöntemi `ProductTableAdapter`. Varsayılan olarak, `Fill` yöntemi dolgular `ProductDataTable` içinde `AdventureWorksLTDataSet` veri Ürün tablosundan tüm satırları içeren. Bu yöntem yalnızca bir alt satır döndürülecek değiştirebilirsiniz. Bu kılavuz için değiştirme `Fill` döndürülecek yöntemi yalnızca Fotoğraf sahip ürünleri için satır.  
  
#### <a name="to-load-product-rows-that-have-photos"></a>Fotoğraf içeren ürün satırları yüklemek için  
  
1.  İçinde **Çözüm Gezgini**, AdventureWorksLTDataSet.xsd dosyasına çift tıklayın.  
  
     Veri kümesi Tasarımcısı'nı açar.  
  
2.  Tasarımcıda sağ **Fill,GetData()** seçin ve sorgu **yapılandırma**.  
  
     **TableAdapter yapılandırma** Sihirbazı açılır.  
  
3.  İçinde **bir SQL deyimi girin** sayfasında, aşağıdaki WHERE yan tümcesinden sonra eklemek `SELECT` metin kutusuna deyimi.  
  
    ```  
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'  
    ```  
  
4.  **Son**'a tıklayın.  
  
## <a name="define-the-user-interface"></a>Kullanıcı arabirimi tanımlama  
 Çeşitli düğmeler, XAML içinde WPF Tasarımcısı değiştirerek pencereye ekleyin. Bu kılavuzda daha sonra kullanıcıların bu düğmeleri kullanarak ürünleri kayıtları yapılan değişiklikleri kaydedin ve aracılığıyla kaydırma olanak sağlayan bir kod ekleyeceksiniz.  
  
#### <a name="to-define-the-user-interface-of-the-window"></a>Kullanıcı arabirimi penceresinin tanımlamak için  
  
1.  İçinde **Çözüm Gezgini**, MainWindow.xaml çift tıklayın.  
  
     WPF Tasarımcısı'nda penceresi açılır.  
  
2.  İçinde [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] görüntülemek tasarımcısına, arasına aşağıdaki kodu ekleyin `<Grid>` etiketler:  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="625" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  Projeyi oluşturun.  
  
## <a name="createdata-bound-controls"></a>Veri bağlama denetimleri  
 Müşteri kayıtları sürükleyerek görüntüleyen denetimler oluşturma `Product` tablosunda **veri kaynakları** penceresinden WPF tasarımcısına.  
  
#### <a name="to-create-data-bound-controls"></a>Verilere bağlı denetimler oluşturmak için  
  
1.  İçinde **veri kaynakları** penceresinde açılan menüsüne tıklayın **ürün** düğümünü seçip alt **ayrıntıları**.  
  
2.  Genişletin **ürün** düğümü.  
  
3.  Bu örnekte, bazı alanlar görüntülenmez, bu nedenle aşağıdaki düğümler yanındaki açılır menüyü tıklayın ve seçin **hiçbiri**:  
  
    -   ProductCategoryID  
  
    -   ProductModelID  
  
    -   ThumbnailPhotoFileName  
  
    -   ROWGUID  
  
    -   ModifiedDate  
  
4.  Yanındaki açılır menüyü tıklayın **ThumbNailPhoto** düğümünü seçip alt **görüntü**.  
  
    > [!NOTE]
    >  Varsayılan olarak, öğeler **veri kaynakları** resimleri temsil eden pencere sahip ayarlamak varsayılan denetim **hiçbiri**. Bu resimler veritabanlarındaki bayt dizisi olarak depolanır ve bayt dizileri her şey basit bir yürütülebilir dosyanın büyük bir uygulamanın bir bayt dizisi içerebilir olmasıdır.  
  
5.  Gelen **veri kaynakları** penceresinde Sürükle **ürün** kılavuz satırı düğmeleri içeren satırı altında düğüm.  
  
     Visual Studio'nun oluşturduğu verilere bağlı denetimler kümesini tanımlayan XAML **ürünleri** tablo. Ayrıca, veri yükleyen kod oluşturur. Oluşturulan XAML ve kod hakkında daha fazla bilgi için bkz. [Visual Studio'da veri bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
6.  Tasarımcıda metin kutusunun yanındaki tıklatın **ürün kimliği** etiketi.  
  
7.  İçinde **özellikleri** yanındaki onay kutusunu penceresinde **IsReadOnly** özelliği.  
  
## <a name="navigating-product-records"></a>Ürün kayıtların gezinmesi  
 Kullanıcıların kullanarak ürün kayıtlarda gezinin olanak sağlayan bir kod ekleme **\<** ve **>** düğmeleri.  
  
#### <a name="to-enable-users-to-navigate-product-records"></a>Kullanıcıların bu ürün kaydı etkinleştirmek için  
  
1.  Tasarımcıda çift **<** penceresi yüzeyinde düğmesi.  
  
     Visual Studio arka plan kod dosyasını açar ve yeni bir oluşturur `backButton_Click` için olay işleyicisi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.  
  
2.  Değiştirme `Window_Loaded` olay işleyicisi, böylece `ProductViewSource`, `AdventureWorksLTDataSet`, ve `AdventureWorksLTDataSetProductTableAdapter` yöntemi dışında ve formun tamamı için erişilebilir durumdadır. Yalnızca bu forma genel olarak bildirmek ve bunların içinde Ata `Window_Loaded` olay işleyicisi aşağıdakine benzer:  
  
     [!code-csharp[Data_WPFDATASET#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#1)]
     [!code-vb[Data_WPFDATASET#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#1)]  
  
3.  Aşağıdaki kodu ekleyin `backButton_Click` olay işleyicisi:  
  
     [!code-csharp[Data_WPFDATASET#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFDATASET#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#2)]  
  
4.  İade tasarımcı ve çift **>** düğmesi.  
  
5.  Aşağıdaki kodu ekleyin `nextButton_Click` olay işleyicisi:  
  
     [!code-csharp[Data_WPFDATASET#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFDATASET#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#3)]  
  
## <a name="savechanges-to-product-records"></a>Ürün kaydı için SaveChanges  
 Kullanarak ürün kayıtları için değişiklikleri kaydedin açmasına sağlayan kodu ekleme **değişiklikleri kaydetmek** düğmesi.  
  
#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>Değişiklikleri kaydetmek için ürün kayıtları özelliği eklemek için  
  
1.  Tasarımcıda çift **değişiklikleri kaydetmek** düğmesi.  
  
     Visual Studio arka plan kod dosyasını açar ve yeni bir oluşturur `saveButton_Click` için olay işleyicisi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.  
  
2.  Aşağıdaki kodu ekleyin `saveButton_Click` olay işleyicisi:  
  
     [!code-csharp[Data_WPFDATASET#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFDATASET#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#4)]  
  
    > [!NOTE]
    >  Bu örnekte `Save` yöntemi `TableAdapter` değişiklikleri kaydedin. Yalnızca bir veri tablosunun değiştiği için bu kılavuzda, bu uygundur. Birden çok veri tablolarına değişiklikleri kaydetmek istiyorsanız, alternatif olarak kullanabilirsiniz `UpdateAll` yöntemi `TableAdapterManager` , Visual Studio ile veri kümesi oluşturur. Daha fazla bilgi için [TableAdapterManager genel bakışı](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).  
  
## <a name="test-the-application"></a>Uygulamayı test etme  
 Derleme ve uygulamayı çalıştırın. Görüntüleyin ve güncelleştirme Ürün kayıtlarını doğrulayın.  
  
#### <a name="to-test-the-application"></a>Uygulamayı test etmek için  
  
1.  Tuşuna **F5**.  
  
     Uygulamayı derler ve çalıştırır. Aşağıdakileri doğrulayın:  
  
    -   Metin kutuları, fotoğraf olan ilk ürün kaydın verileri görüntüler. Bu ürün ürün kimliği 713 ve adına sahip **uzun kollu logolu forma, S**.  
  
    -   Tıklayabilirsiniz **>** veya **<** diğer ürün Kayıtlarda gezinmek için düğmeler.  
  
2.  Ürün kayıtların her birinde değişiklik **boyutu** değeri ve ardından **değişiklikleri kaydetmek**.  
  
3.  Uygulamayı kapatın ve ardından tuşlarına basarak uygulamayı yeniden **F5** Visual Studio'da.  
  
4.  Değiştirdiğiniz ürün kaydı için gezinme ve değişiklik kalıcı olduğunu doğrulayın.  
  
5.  Uygulamayı kapatın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu kılavuzu tamamladıktan sonra aşağıdaki görevleri gerçekleştirebilirsiniz:  
  
-   Nasıl kullanacağınızı öğrenin **veri kaynakları** WPF bağlama için Visual Studio penceresinde başka türde veri kaynaklarını denetler. Daha fazla bilgi için [denetimleri bir WCF veri hizmetine WPF bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
-   Nasıl kullanacağınızı öğrenin **veri kaynakları** Visual Studio'daki WPF denetimlerindeki ilgili verileri (diğer bir deyişle, bir üst-alt ilişkisi veri) görüntülenecek. Daha fazla bilgi için [izlenecek yol: WPF uygulamasında ilgili verileri görüntüleme](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Visual Studio'da veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)   
 [WPF ve Silverlight Tasarımcısı genel bakış](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [Veri Bağlamaya Genel Bakış](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)

