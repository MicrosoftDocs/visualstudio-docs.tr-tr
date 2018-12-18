---
title: Bir veri kümesine WPF denetimleri bağlama
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 43b262344965091cf7599a9e1b2c43d6bcdb94f2
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305734"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Bir veri kümesine WPF denetimleri bağlama

Bu kılavuzda, verilere bağlı denetimler içeren bir WPF uygulaması oluşturun. Denetimler bir veri kümesinde kapsüllenmiş ürün kayıtları bağlıdır. Ayrıca, düğmeler ürünlere göz atabilir ve ürün kayıtları için değişiklikleri kaydetmek için de ekleyin.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- Bir WPF uygulamasını ve verileri AdventureWorksLT örnek veritabanını kullanarak oluşturulan bir veri kümesi oluşturma.

- Bir veri tablosundan sürükleyerek veriye bağlı denetimler kümesini oluşturma **veri kaynakları** WPF Tasarımcısı penceresinde penceresine.

- Ürün kayıtlarında ileriye ve geriye doğru gezinmek düğmeleri oluşturuluyor.

- Bir düğme oluşturma, veri tablosu ve temel alınan veri kaynağı için ürün kayıtları kullanıcılar yaptığınız değişiklikleri kaydeder.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio

- Çalışan bir SQL Server veya bağlı AdventureWorks ışık (AdventureWorksLT) örnek veritabanının bulunduğu SQL Server Express örneğine erişim. AdventureWorksLT veritabanı indirebileceğiniz [CodePlex arşiv](https://archive.codeplex.com/?p=awlt2008dbscript).

Aşağıdaki kavramları bilgisi de faydalıdır, ancak izlenecek yolu tamamlamak için gerekli değil:

- Veri kümeleri ve TableAdapters öğelerini. Daha fazla bilgi için [Visual Studio'daki veri kümesi Araçları](../data-tools/dataset-tools-in-visual-studio.md) ve [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

- WPF veri bağlaması. Daha fazla bilgi için [Data Binding Overview](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="create-the-project"></a>Projeyi oluşturma

Ürün kayıtları görüntülemek için yeni bir WPF projesi oluşturun.

1. Visual Studio'yu başlatın.

2. Üzerinde **dosya** menüsünde **yeni** > **proje**.

3. Genişletin **Visual Basic** veya **Visual C#** ve ardından **Windows**.

4. Seçin **WPF uygulaması** proje şablonu.

5. İçinde **adı** kutusuna **AdventureWorksProductsEditor** seçip **Tamam**.

   Visual Studio AdventureWorksProductsEditor projesi oluşturur.

## <a name="create-a-dataset-for-the-application"></a>Uygulama için bir veri kümesi oluşturma

Verilere bağlı denetimler oluşturabilmeniz için uygulamanız için bir veri modeli tanımlamanızı ve kendisine eklemeniz gerekir **veri kaynakları** penceresi. Bu izlenecek yolda veri modeli olarak kullanılacak bir veri kümesi oluşturun.

1. Üzerinde **veri** menüsünü tıklatın **veri kaynaklarını Göster**.

   **Veri kaynakları** penceresi açılır.

2. İçinde **veri kaynakları** penceresinde tıklayın **yeni veri kaynağı Ekle**.

   **Veri kaynağı yapılandırması** Sihirbazı açılır.

3. Üzerinde **bir veri kaynağı türü seçin** sayfasında **veritabanı**ve ardından **sonraki**.

4. Üzerinde **veritabanı modeli seçin** sayfasında **veri kümesi**ve ardından **sonraki**.

5. Üzerinde **veri bağlantınızı seçin** sayfasında, aşağıdaki seçeneklerden birini seçin:

   - AdventureWorksLT örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir haldeyse, onu seçin ve ardından **sonraki**.

   - Tıklayın **yeni bağlantı**ve AdventureWorksLT veritabanına bağlantı oluşturun.

6. Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfasında **Evet, bağlantıyı bu adla Kaydet** onay kutusunu işaretleyin ve ardından **sonraki**.

7. Üzerinde **veritabanı nesnelerinizi seçin** sayfasında **tabloları**ve ardından **ürün (SalesLT)** tablo.

8. **Son**'a tıklayın.

   Yeni bir Visual Studio ekler `AdventureWorksLTDataSet.xsd` ve proje dosyasına ekler karşılık gelen **AdventureWorksLTDataSet** öğesinin **veri kaynakları** penceresi. `AdventureWorksLTDataSet.xsd` Dosyası adlı bir türü belirtilmiş veri kümesi tanımlar `AdventureWorksLTDataSet` ve adlı bir TableAdapter `ProductTableAdapter`. Bu kılavuzda daha sonra kullanacağınız `ProductTableAdapter` veri kümesini verilerle doldurma ve değişiklikleri veritabanına geri kaydedin.

9. Projeyi oluşturun.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>TableAdapter'ın varsayılan dolgu yöntemi Düzenle

Veri kümesini verilerle doldurmak için kullanın `Fill` yöntemi `ProductTableAdapter`. Varsayılan olarak, `Fill` yöntemi dolgular `ProductDataTable` içinde `AdventureWorksLTDataSet` veri Ürün tablosundan tüm satırları içeren. Bu yöntem yalnızca bir alt satır döndürülecek değiştirebilirsiniz. Bu kılavuz için değiştirme `Fill` döndürülecek yöntemi yalnızca Fotoğraf sahip ürünleri için satır.

1. İçinde **Çözüm Gezgini**, çift *AdventureWorksLTDataSet.xsd* dosya.

     Veri kümesi Tasarımcısı'nı açar.

2. Tasarımcıda sağ **dolgu**, **GetData()** sorgulamak ve seçin **yapılandırma**.

     **TableAdapter yapılandırma** Sihirbazı açılır.

3. İçinde **bir SQL deyimi girin** sayfasında, aşağıdaki WHERE yan tümcesinden sonra eklemek `SELECT` metin kutusuna deyimi.

    ```sql
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4. **Son**'a tıklayın.

## <a name="define-the-user-interface"></a>Kullanıcı arabirimi tanımlama

Çeşitli düğmeler, XAML içinde WPF Tasarımcısı değiştirerek pencereye ekleyin. Bu kılavuzda daha sonra kullanıcıların bu düğmeleri kullanarak ürünleri kayıtları yapılan değişiklikleri kaydedin ve aracılığıyla kaydırma olanak sağlayan bir kod ekleyeceksiniz.

1. İçinde **Çözüm Gezgini**, çift *MainWindow.xaml*.

    Açılır pencere **WPF Tasarımcısı**.

2. İçinde [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] görüntülemek tasarımcısına, arasına aşağıdaki kodu ekleyin `<Grid>` etiketler:

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="625" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. Projeyi oluşturun.

## <a name="create-data-bound-controls"></a>Verilere bağlı denetimler oluşturma

Müşteri kayıtları sürükleyerek görüntüleyen denetimler oluşturma `Product` tablosunda **veri kaynakları** penceresinden WPF tasarımcısına.

1. İçinde **veri kaynakları** penceresinde açılan menüsüne tıklayın **ürün** düğümünü seçip alt **ayrıntıları**.

2. Genişletin **ürün** düğümü.

3. Bu örnekte, bazı alanlar görüntülenmez, bu nedenle aşağıdaki düğümler yanındaki açılır menüyü tıklayın ve seçin **hiçbiri**:

    - ProductCategoryID

    - ProductModelID

    - ThumbnailPhotoFileName

    - ROWGUID

    - ModifiedDate

4. Yanındaki açılır menüyü tıklayın **ThumbNailPhoto** düğümünü seçip alt **görüntü**.

    > [!NOTE]
    > Varsayılan olarak, öğeler **veri kaynakları** resimleri temsil eden pencere sahip ayarlamak varsayılan denetim **hiçbiri**. Bu resimler veritabanlarındaki bayt dizisi olarak depolanır ve bayt dizileri her şey basit bir yürütülebilir dosyanın büyük bir uygulamanın bir bayt dizisi içerebilir olmasıdır.

5. Gelen **veri kaynakları** penceresinde Sürükle **ürün** kılavuz satırı düğmeleri içeren satırı altında düğüm.

     Visual Studio'nun oluşturduğu verilere bağlı denetimler kümesini tanımlayan XAML **ürünleri** tablo. Ayrıca, veri yükleyen kod oluşturur. Oluşturulan XAML ve kod hakkında daha fazla bilgi için bkz. [Visual Studio'da veri bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. Tasarımcıda metin kutusunun yanındaki tıklatın **ürün kimliği** etiketi.

7. İçinde **özellikleri** yanındaki onay kutusunu penceresinde **IsReadOnly** özelliği.

## <a name="navigate-product-records"></a>Ürün kaydı gidin

Kullanıcıların kullanarak ürün kayıtlarda gezinin olanak sağlayan bir kod ekleme **\<** ve **>** düğmeleri.

1. Tasarımcıda çift **<** penceresi yüzeyinde düğmesi.

     Visual Studio arka plan kod dosyasını açar ve yeni bir oluşturur `backButton_Click` için olay işleyicisi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.

2. Değiştirme `Window_Loaded` olay işleyicisi, böylece `ProductViewSource`, `AdventureWorksLTDataSet`, ve `AdventureWorksLTDataSetProductTableAdapter` yöntemi dışında ve formun tamamı için erişilebilir durumdadır. Yalnızca bu forma genel olarak bildirmek ve bunların içinde Ata `Window_Loaded` olay işleyicisi aşağıdakine benzer:

     [!code-csharp[Data_WPFDATASET#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_1.cs)]
     [!code-vb[Data_WPFDATASET#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_1.vb)]

3. Aşağıdaki kodu ekleyin `backButton_Click` olay işleyicisi:

     [!code-csharp[Data_WPFDATASET#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_2.cs)]
     [!code-vb[Data_WPFDATASET#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_2.vb)]

4. İade tasarımcı ve çift **>** düğmesi.

5. Aşağıdaki kodu ekleyin `nextButton_Click` olay işleyicisi:

     [!code-csharp[Data_WPFDATASET#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_3.cs)]
     [!code-vb[Data_WPFDATASET#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_3.vb)]

## <a name="save-changes-to-product-records"></a>Değişiklikleri kaydetmek için ürün kayıtları

Kullanarak ürün kayıtları için değişiklikleri kaydedin açmasına sağlayan kodu ekleme **değişiklikleri kaydetmek** düğmesi.

1. Tasarımcıda çift **değişiklikleri kaydetmek** düğmesi.

     Visual Studio arka plan kod dosyasını açar ve yeni bir oluşturur `saveButton_Click` için olay işleyicisi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.

2. Aşağıdaki kodu ekleyin `saveButton_Click` olay işleyicisi:

     [!code-csharp[Data_WPFDATASET#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_4.cs)]
     [!code-vb[Data_WPFDATASET#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_4.vb)]

    > [!NOTE]
    > Bu örnekte `Save` yöntemi `TableAdapter` değişiklikleri kaydedin. Yalnızca bir veri tablosunun değiştiği için bu kılavuzda, bu uygundur. Birden çok veri tablolarına değişiklikleri kaydetmek istiyorsanız, alternatif olarak kullanabilirsiniz `UpdateAll` yöntemi `TableAdapterManager` , Visual Studio ile veri kümesi oluşturur. Daha fazla bilgi için [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="test-the-application"></a>Uygulamayı test etme

Derleme ve uygulamayı çalıştırın. Görüntüleyin ve güncelleştirme Ürün kayıtlarını doğrulayın.

1. Tuşuna **F5**.

     Uygulamayı derler ve çalıştırır. Aşağıdakileri doğrulayın:

    - Metin kutuları, fotoğraf olan ilk ürün kaydın verileri görüntüler. Bu ürün ürün kimliği 713 ve adına sahip **uzun kollu logolu forma, S**.

    - Tıklayabilirsiniz **>** veya **<** diğer ürün Kayıtlarda gezinmek için düğmeler.

2. Ürün kayıtların her birinde değişiklik **boyutu** değeri ve ardından **değişiklikleri kaydetmek**.

3. Uygulamayı kapatın ve ardından tuşlarına basarak uygulamayı yeniden **F5** Visual Studio'da.

4. Değiştirdiğiniz ürün kaydı için gezinme ve değişiklik kalıcı olduğunu doğrulayın.

5. Uygulamayı kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Bu kılavuzu tamamladıktan sonra aşağıdaki görevleri deneyebilirsiniz:

- Nasıl kullanacağınızı öğrenin **veri kaynakları** WPF bağlama için Visual Studio penceresinde başka türde veri kaynaklarını denetler. Daha fazla bilgi için [denetimleri bir WCF veri hizmetine WPF bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

- Nasıl kullanacağınızı öğrenin **veri kaynakları** Visual Studio'daki WPF denetimlerindeki ilgili verileri (diğer bir deyişle, bir üst-alt ilişkisi veri) görüntülenecek. Daha fazla bilgi için [izlenecek yol: WPF uygulamasında ilgili verileri görüntüleyen](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
- [Veri Bağlamaya Genel Bakış](/dotnet/framework/wpf/data/data-binding-overview)
