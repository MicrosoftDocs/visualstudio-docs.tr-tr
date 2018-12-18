---
title: Bir WCF veri hizmetine WPF denetimleri bağlama
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3330c86c84318be68619a8d031a034b33faa7fd1
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305669"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Bir WCF veri hizmetine WPF denetimleri bağlama

Bu kılavuzda, verilere bağlı denetimler içeren bir WPF uygulaması oluşturacaksınız. Denetimler WCF veri hizmeti kapsüllenmiş müşteri kayıtları bağlıdır. Ayrıca müşteriler kayıtları görüntülemek ve güncelleştirmek için kullanabilir düğmeler ekleyeceksiniz.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- Bir varlık veri modeli oluşturma, AdventureWorksLT örnek veritabanı bulunan verilerden oluşturulur.

- WCF veri hizmeti oluşturma, varlık veri modeline WPF uygulaması verileri kullanıma sunar.

- Öğe sürükleyerek veriye bağlı denetimler kümesini oluşturma **veri kaynakları** penceresinden WPF tasarımcısına.

- Müşteri kayıtlarında ileriye ve geriye doğru gezinmek düğmeleri oluşturuluyor.

- WCF veri hizmeti ve temel alınan veri kaynağına denetimlerinde verileri değişiklikleri kaydeder bir düğme oluşturma.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio

- Çalışan bir SQL Server veya SQL Server bağlı AdventureWorksLT örnek veritabanı içeren bir Express örneğine erişim. AdventureWorksLT veritabanı indirebileceğiniz [CodePlex Web sitesinde](http://go.microsoft.com/fwlink/?linkid=87843).

Aşağıdaki kavramları bilgisi de faydalıdır, ancak izlenecek yolu tamamlamak için gerekli değil:

- WCF Veri Hizmetleri. Daha fazla bilgi için [genel bakış](/dotnet/framework/data/wcf/wcf-data-services-overview).

- Veri modelleri de [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].

- Varlık veri modelleri ve ADO.NET varlık çerçevesi. Daha fazla bilgi için [Entity Framework genel bakış](/dotnet/framework/data/adonet/ef/overview).

- WPF veri bağlaması. Daha fazla bilgi için [veri bağlama genel bakış](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="create-the-service-project"></a>Hizmet projesi oluşturma

Bu izlenecek yol, bir WCF veri hizmeti için bir proje oluşturarak başlayın:

1. Visual Studio'yu başlatın.

2. Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.

3. Genişletin **Visual C#**  veya **Visual Basic**ve ardından **Web**.

4. Seçin **ASP.NET Web uygulaması** proje şablonu.

5. İçinde **adı** kutusuna **AdventureWorksService** tıklatıp **Tamam**.

     Visual Studio oluşturur **AdventureWorksService** proje.

6. İçinde **Çözüm Gezgini**, sağ **Default.aspx** seçip **Sil**. Bu dosya, bu izlenecek yolda gerekli değildir.

## <a name="create-an-entity-data-model-for-the-service"></a>Hizmet için bir varlık veri modeli oluşturma

WCF veri hizmeti kullanarak bir uygulamaya veri kullanıma sunmak için bir hizmet için veri modeli tanımlamanız gerekir. WCF veri hizmeti iki tür veri modellerini destekler: Varlık veri modelleri ve ortak dil çalışma zamanı (CLR) uygulayan kullanılarak tanımlanmış özel veri modelleri <xref:System.Linq.IQueryable%601> arabirimi. Bu kılavuzda, veri modeli için bir varlık veri modeli oluşturun.

1. Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.

2. Yüklü Şablonlar listesinde **veri**ve ardından **ADO.NET varlık veri modeli** proje öğesi.

3. Adla değiştirin `AdventureWorksModel.edmx`, tıklatıp **Ekle**.

     **Varlık veri modeli** Sihirbazı açılır.

4. Üzerinde **Choose Model Contents** sayfasında **veritabanından Oluştur**, tıklatıp **sonraki**.

5. Üzerinde **veri bağlantınızı seçin** sayfasında, aşağıdaki seçeneklerden birini seçin:

    - AdventureWorksLT örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir haldeyse, onu seçin.

    - Tıklayın **yeni bağlantı**ve AdventureWorksLT veritabanına bağlantı oluşturun.

6. Üzerinde **veri bağlantınızı seçin** sayfasında, aşağıdakileri sağlayın **varlığı App.Config dosyasındaki bağlantı ayarlarını Kaydet** seçeneği seçilidir ve ardından **sonraki**.

7. Üzerinde **veritabanı nesnelerinizi seçin** sayfasında **tabloları**ve ardından **SalesOrderHeader** tablo.

8. **Son**'a tıklayın.

## <a name="create-the-service"></a>Hizmet oluşturma

Bir WCF veri hizmetine WPF uygulaması varlık veri Modeli'ne verileri göstermek için oluşturabilir:

1. Üzerinde **proje** menüsünde **Yeni Öğe Ekle**.

2. İçinde **yüklü şablonlar** listesinde **Web**ve ardından **WCF veri hizmeti** proje öğesi.

3. İçinde **adı** kutusuna `AdventureWorksService.svc`, tıklatıp **Ekle**.

     Visual Studio ekler `AdventureWorksService.svc` projeye.

## <a name="configure-the-service"></a>Hizmet yapılandırma

Oluşturduğunuz varlık veri modeli üzerinde çalışılacak hizmet yapılandırmanız gerekir:

1. İçinde `AdventureWorks.svc` kod dosyası, değiştirin **AdventureWorksService** sınıf bildiriminin aşağıdaki kod ile.

     [!code-csharp[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]

     Bu kodu güncelleştirir **AdventureWorksService** böylece öğesinden türetilen sınıf bir <xref:System.Data.Services.DataService%601> , yeniden kopyalarında `AdventureWorksLTEntities` varlık veri modeli, sınıfında bağlam nesnesi. Aynı zamanda güncelleştirmeleri `InitializeService` hizmet okuma/yazma erişimi, istemcilerin yöntemi `SalesOrderHeader` varlık.

2. Projeyi oluşturmak ve hatasız oluşturulduğunu doğrulayın.

## <a name="create-the-wpf-client-application"></a>WPF istemci uygulaması oluşturma

WCF veri hizmeti verileri görüntülemek için hizmetini temel alan bir veri kaynağı ile yeni bir WPF uygulaması oluşturun. Bu kılavuzda daha sonra uygulamayı verilere bağlı denetimler ekleyeceksiniz.

1. İçinde **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın, **Ekle**seçip **yeni proje**.

2. İçinde **yeni proje** iletişim kutusunda Genişlet **Visual C#**  veya **Visual Basic**ve ardından **Windows**.

3. Seçin **WPF uygulaması** proje şablonu.

4. İçinde **adı** kutusuna `AdventureWorksSalesEditor`, tıklatıp **Tamam**.

   Visual Studio ekler `AdventureWorksSalesEditor` çözüme bir proje.

5. Üzerinde **veri** menüsünü tıklatın **veri kaynaklarını Göster**.

   **Veri kaynakları** penceresi açılır.

6. İçinde **veri kaynakları** penceresinde tıklayın **yeni veri kaynağı Ekle**.

   **Veri kaynağı yapılandırması** Sihirbazı açılır.

7. İçinde **bir veri kaynağı türü seçin** seçin sayfasında **hizmet**ve ardından **sonraki**.

8. İçinde **hizmet Başvurusu Ekle** iletişim kutusu, tıklayın **bulma**.

   Visual Studio sunulan hizmetler için geçerli çözüm arar ve ekler `AdventureWorksService.svc` kullanılabilir hizmetlerin listesini için **Hizmetleri** kutusu.

9. İçinde **Namespace** kutusuna **AdventureWorksService**.

10. İçinde **Hizmetleri** kutusunun **AdventureWorksService.svc**ve ardından **Tamam**.

    Visual Studio hizmet bilgilerini indirir ve ardından döndürür **veri kaynağı yapılandırması** Sihirbazı.

11. İçinde **hizmet Başvurusu Ekle** sayfasında **son**.

    Visual Studio hizmeti tarafından döndürülen verileri temsil eden düğümler ekler **veri kaynakları** penceresi.

## <a name="define-the-user-interface"></a>Kullanıcı arabirimi tanımlama

Çeşitli düğmeler, XAML içinde WPF Tasarımcısı değiştirerek pencereye ekleyin. Bu kılavuzda daha sonra kullanıcıların bu düğmeleri kullanarak satış kayıtları görüntüleyin ve olanak sağlayan bir kod ekleyeceksiniz.

1. İçinde **Çözüm Gezgini**, çift **MainWindow.xaml**.

   WPF Tasarımcısı'nda penceresi açılır.

2. İçinde [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] görüntülemek tasarımcısına, arasına aşağıdaki kodu ekleyin `<Grid>` etiketler:

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="525" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. Projeyi oluşturun.

## <a name="create-the-data-bound-controls"></a>Verilere bağlı denetimler oluşturma

Müşteri kayıtları sürükleyerek görüntüleyen denetimler oluşturma `SalesOrderHeaders` düğümünden **veri kaynakları** penceresinden tasarımcıya.

1. İçinde **veri kaynakları** penceresinde açılan menüsüne tıklayın **SalesOrderHeaders** düğüm ve select **ayrıntıları**.

2. Genişletin **SalesOrderHeaders** düğümü.

3. Bu örnekte, bazı alanlar görüntülenmez, bu nedenle aşağıdaki düğümler yanındaki açılır menüyü tıklayın ve seçin **hiçbiri**:

    - **CreditCardApprovalCode**

    - **ModifiedDate**

    - **OnlineOrderFlag**

    - **RevisionNumber**

    - **ROWGUID**

    Bu eylem, Visual Studio, bir sonraki adımda bu düğümler için verilere bağlı denetimler oluşturmanızı engeller. Bu kılavuz için son kullanıcı bu verileri görme gerekmez varsayılır.

4. Gelen **veri kaynakları** penceresinde Sürükle **SalesOrderHeaders** kılavuz satırı düğmeleri içeren satırı altında düğüm.

     Visual Studio, XAML ve verilere bağlı denetimler kümesini oluşturan kodu oluşturur **ürün** tablo. Oluşturulan XAML ve kod hakkında daha fazla bilgi için bkz. [Visual Studio'da veri bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

5. Tasarımcıda metin kutusunun yanındaki tıklatın **Müşteri Kimliği** etiketi.

6. İçinde **özellikleri** yanındaki onay kutusunu penceresinde **IsReadOnly** özelliği.

7. Ayarlama **IsReadOnly** özelliği her biri aşağıdaki metin kutuları için:

    - **Sipariş numarası**

    - **Satış siparişi kodu**

    - **Sipariş numarası**

## <a name="load-the-data-from-the-service"></a>Verileri hizmetten yükleme

Satış verileri hizmetten yükleme için hizmet proxy nesnesi kullanın. Veri kaynağı için döndürülen verileri atamak <xref:System.Windows.Data.CollectionViewSource> WPF penceresinde.

1. Oluşturulacak Tasarımcısı'nda `Window_Loaded` olay işleyicisi, yazan metnin çift: **MainWindow**.

2. Olay işleyicisi aşağıdaki kodla değiştirin. Değiştirdiğinizden emin olun *localhost* bu kodda adresi ile geliştirme bilgisayarınızda yerel ana bilgisayar adresi.

     [!code-csharp[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]

## <a name="navigate-sales-records"></a>Satış kayıtları gidin

Kullanıcıların kullanarak satış kayıtlarda gezinin olanak sağlayan bir kod ekleme **\<** ve **>** düğmeleri.

1. Tasarımcıda çift **<** penceresi yüzeyinde düğmesi.

     Visual Studio arka plan kod dosyasını açar ve yeni bir oluşturur `backButton_Click` için olay işleyicisi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.

2. Oluşturulan için aşağıdaki kodu ekleyin `backButton_Click` olay işleyicisi:

     [!code-csharp[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]

3. Tasarımcıya dönün ve çift **>** düğmesi.

     Visual Studio arka plan kod dosyasını açar ve yeni bir oluşturur `nextButton_Click` için olay işleyicisi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.

4. Oluşturulan için aşağıdaki kodu ekleyin `nextButton_Click` olay işleyicisi:

     [!code-csharp[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]

## <a name="save-changes-to-sales-records"></a>Değişiklikleri kaydetmek için satış kayıtları

Hem görüntüleme hem kullanarak satış kayıtları için değişiklikleri kaydedin açmasına sağlayan kodu ekleme **değişiklikleri kaydetmek** düğmesi:

1. Tasarımcıda çift **Değişiklikleri Kaydet** düğmesi.

     Visual Studio arka plan kod dosyasını açar ve yeni bir oluşturur `saveButton_Click` için olay işleyicisi <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.

2. Aşağıdaki kodu ekleyin `saveButton_Click` olay işleyicisi.

     [!code-csharp[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]

## <a name="test-the-application"></a>Uygulamayı test etme

Oluşturun ve görüntüleyin ve güncelleştirme Müşteri kayıtlarını doğrulamak için uygulamayı çalıştırın:

1. Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle**. Çözüm hatasız oluşturulduğunu doğrulayın.

2. Tuşuna **Ctrl**+**F5**.

     Visual Studio başlatır **AdventureWorksService** , hata ayıklama olmadan proje.

3. İçinde **Çözüm Gezgini**, sağ **AdventureWorksSalesEditor** proje.

4. Bağlam menüsünde altında **hata ayıklama**, tıklayın **yeni örnek Başlat**.

     Uygulama çalışır. Aşağıdakileri doğrulayın:

    - Metin kutuları satış siparişi kodu olan ilk satış kayıttan farklı veri alanlarını görüntüler **71774**.

    - Tıklayabilirsiniz **>** veya **<** diğer satış Kayıtlarda gezinmek için düğmeler.

5. Satış kayıtların her birinde, bir metin yazın **yorum** kutusuna ve ardından **değişiklikleri kaydetmek**.

6. Uygulamayı kapatın ve sonra uygulamayı Visual Studio'dan yeniden başlatın.

7. Değiştirdiğiniz satış kayda gidin ve sonra uygulamayı kapatıp değişikliği devam ettiğini doğrulayın.

8. Uygulamayı kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Bu kılavuzu tamamladıktan sonra aşağıdaki görevleri gerçekleştirebilirsiniz:

- Nasıl kullanacağınızı öğrenin **veri kaynakları** WPF bağlama için Visual Studio penceresinde başka türde veri kaynaklarını denetler. Daha fazla bilgi için [bağlama WPF denetimlerini bir veri kümesine](../data-tools/bind-wpf-controls-to-a-dataset.md).

- Nasıl kullanacağınızı öğrenin **veri kaynakları** Visual Studio'daki WPF denetimlerindeki ilgili verileri (diğer bir deyişle, bir üst-alt ilişkisi veri) görüntülenecek. Daha fazla bilgi için [izlenecek yol: WPF uygulamasında ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Bir veri kümesine WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [WCF genel bakış (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Entity Framework'e Genel Bakış (.NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [Veri bağlama genel bakış (.NET Framework)](/dotnet/framework/wpf/data/data-binding-overview)