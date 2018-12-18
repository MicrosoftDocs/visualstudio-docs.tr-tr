---
title: Kodlanmış UI testi oluşturma
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: fe8bed9c1f1f8aee9ae8e6d1ba460bf226d7b818
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895528"
---
# <a name="walkthrough-create-edit-and-maintain-a-coded-ui-test"></a>İzlenecek yol: Oluşturma, düzenleme ve bir kodlanmış UI testinin

Bu kılavuzda, oluşturmak, düzenlemek ve bir kodlanmış UI sınamak için bir Windows Presentation Framework (WPF) uygulaması korumak öğreneceksiniz. İzlenecek yol çeşitli zamanlama sorunları tarafından Kırılan testleri düzeltmeye ve denetimleri yeniden düzenleme için çözümler sağlar.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-wpf-app"></a>Bir WPF uygulaması oluşturma

1.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.

     **Yeni proje** iletişim kutusu görüntülenir.

2.  İçinde **yüklü** bölmesini genişletin **Visual C#** ve ardından **Windows Masaüstü**.

3.  Orta bölmede hedef çerçeve açılır listesinin değerine ayarlandığını doğrulayın **.NET Framework 4.5**.

4.  Orta bölmede seçin **WPF uygulaması** şablonu.

5.  İçinde **adı** metin kutusunda, **SimpleWPFApp**.

6.  Projeyi kaydetmek için bir klasör seçin. İçinde **konumu** metin kutusuna, klasörün adını yazın.

7.  Seçin **Tamam**.

     **Visual Studio için WPF Tasarımcısı** açılır ve projenin MainWindow öğesini görüntüler.

8.  Araç kutusu açık değilse, açın. Seçin **görünümü** menüsünü seçip **araç kutusu**.

9. Altında **tüm WPF denetimleri** bölümü bir **düğmesi**, **onay kutusu** ve **ProgressBar** tasarım MainWindow üzerine denetimi Surface.

10. Seçin **düğmesi** denetimi. İçinde **özellikleri** penceresinde değerini **adı** özelliğinden \<No Name > button1 için. Ardından değerini değiştirin **içerik** özelliğini Başlat düğmesi.

11. Seçin **ProgressBar** denetimi. İçinde **özellikleri** penceresinde değerini **adı** özelliğinden \<No Name > den progressbar1'e. Ardından değerini değiştirin **maksimum** özelliğinden **100** için **10000**.

12. Seçin **onay kutusu** denetimi. İçinde **özellikleri** penceresinde değerini değiştirin **adı** özelliğinden \<No Name > checkBox1 ve Temizle **IsEnabled** özelliği.

     ![Basit WPF uygulaması](../test/media/codedui_wpfapp.png)

13. Bir tıklama olayı işleyicisi eklemek için düğme denetimini çift tıklayın.

     *MainWindow.xmal.cs* yeni button1_Click yönteminde imleç ile Kod Düzenleyicisi'nde görüntülenir.

14. MainWindow sınıfının en üstünde bir temsilci ekleyin. Temsilci ilerleme çubuğu için kullanılacaktır. Temsilci eklemek için aşağıdaki kodu ekleyin:

    ```csharp
    public partial class MainWindow : Window
    {
            private delegate void ProgressBarDelegate(System.Windows.DependencyProperty dp, Object value);

        public MainWindow()
        {

            InitializeComponent();
        }
    ```

15. button1_Click yöntemine aşağıdaki kodu ekleyin:

    ```csharp
    private void button1_Click(object sender, RoutedEventArgs e)
    {
        double progress = 0;

        ProgressBarDelegate updatePbDelegate =
            new ProgressBarDelegate(progressBar1.SetValue);

        do
        {
            progress ++;

            Dispatcher.Invoke(updatePbDelegate,
                System.Windows.Threading.DispatcherPriority.Background,
                new object[] { ProgressBar.ValueProperty, progress });
            progressBar1.Value = progress;
        }
        while (progressBar1.Value != progressBar1.Maximum);

        checkBox1.IsEnabled = true;
    }
    ```

16. Dosyayı kaydedin.

### <a name="run-the-wpf-app"></a>WPF uygulaması çalıştırma

1.  Üzerinde **hata ayıklama** menüsünde **hata ayıklamayı Başlat** veya basın **F5**.

2.  Onay kutusu denetimi devre dışı olduğuna dikkat edin. Seçin **Başlat**.

     Birkaç saniye içinde ilerleme çubuğu tam %100 bitmiş olmalıdır.

3.  Onay kutusu denetimi şimdi seçebilirsiniz.

4.  SimpleWPFApp Uygulamasını Kapatın.

## <a name="create-a-shortcut-to-the-wpf-app"></a>WPF uygulaması için bir kısayol oluşturma

1.  Daha önce oluşturduğunuz SimpleWPFApp uygulamasını bulun.

2.  SimpleWPFApp uygulaması için bir masaüstü kısayolu oluşturun. Sağ *SimpleWPFApp.exe* ve **kopyalama**. Masaüstünüzde sağ tıklatın ve seçin **kısayolu Yapıştır**.

    > [!TIP]
    > Uygulamaya bir kısayol eklemek veya uygulamanız için kodlanmış UI testleri uygulamayı hızlıca başlatmanızı sağlar çünkü değiştirmek kolaylaştırır.

## <a name="create-a-coded-ui-test-for-simplewpfapp"></a>SimpleWPFApp için kodlanmış UI testi oluşturma

1. İçinde **Çözüm Gezgini**, çözüme sağ tıklayın, seçin **Ekle** seçip **yeni proje**.

     **Yeni Proje Ekle** iletişim kutusu görüntülenir.

1. İçinde **yüklü** bölmesini genişletin **Visual C#** ve ardından **Test**.

1. Orta bölmede seçin **kodlanmış UI Test projesi** şablonu.

   > [!NOTE]
   > Görmüyorsanız **kodlanmış UI Test projesi** şablon gereken [kodlanmış UI test bileşeni](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

1. Seçin **Tamam**.

     Yeni kodlanmış UI test projesi adlı **Codeduıtestproject1** çözümünüze eklenir.

     **Kodlanmış UI testi için kod üret** iletişim kutusu görüntülenir.

1. Seçin **eylemleri Kaydet, UI haritasını Düzenle veya onaylama işlemleri Ekle** seçenek ve **Tamam**.

     **UIMap - Kodlanmış UI Test Oluşturucusu** iletişim kutusu açılır ve Visual Studio penceresi simge durumuna küçültülür.

     İletişim kutusundaki seçenekler hakkında daha fazla bilgi için bkz. [Oluştur kodlanmış UI testleri](../test/use-ui-automation-to-test-your-code.md).

1. Seçin **kaydı Başlat** üzerinde **UIMap - Kodlanmış UI Test Oluşturucusu** iletişim.

     ![Kaydı Başlat](../test/media/cuit_builder_record.png)

     Gerekirse, gelen e-posta ile uğraşmak zorunda örneğin kayıt duraklatabilirsiniz.

     ![Kaydı Duraklat](../test/media/cuit_.png)

    > [!WARNING]
    > Masaüstü üzerinde gerçekleştirilen tüm eylemler kaydedilir. Hassas veriler kayda eklenmesini açabilir eylemleri gerçekleştiriyorsanız kaydı duraklatın.

1. Masaüstü kısayolunu kullanarak SimpleWPFApp başlatın.

     Önceki örneklerde olduğu gibi onay kutusu denetimi devre dışı bırakıldığını dikkat edin.

1. SimpleWPFApp üzerinde seçin **Başlat**.

     Birkaç saniye içinde ilerleme çubuğu tam %100 bitmiş olmalıdır.

1. Artık etkin onay kutusu denetimini kontrol edin.

1. SimpleWPFApp uygulamasını kapatın.

1. Üzerinde **UIMap - Kodlanmış UI Test Oluşturucusu** iletişim kutusunda seçin **kod üret**.

1. İçinde **yöntem adı** kutusuna **SimpleAppTest** ve **Ekle ve Oluştur**. Birkaç saniye içinde kodlanmış UI testi görünür ve çözüme eklenir.

1. Kapat **UIMap - Kodlanmış UI Testi Oluşturucusu**.

     *Codeduıtest1.cs* dosyası Kod Düzenleyicisi'nde görünür.

1. Projenizi kaydedin.

### <a name="run-the-test"></a>Testi çalıştırın

1. Gelen **Test** menüsünde seçin **Windows** seçip **Test Gezgini**.

2. Gelen **derleme** menüsünde seçin **Çözümü Derle**.

3. İçinde *Codeduıtest1.cs* bulun, dosya **CodedUITestMethod** yöntemi, sütuna sağ tıklayıp **çalıştırmak testlerini**, veya test çalıştırmak **Test Gezgini**.

   Kodlanmış UI testi çalışırken, SimpleWPFApp görülebilir. Bir önceki yordamda yaptığınız adımları oluşturur. Ancak, test çalıştığında onay kutusu denetimi için onay kutusunu işaretleyin **Test sonuçları** penceresi testin başarısız olduğunu gösterir. Bu onay kutusunu seçmek test çalışmasından, ancak ilerleme çubuğu % 100 tamamlandı olana kadar onay kutusu denetimi devre dışı bırakıldığını ile uyumlu değildir. Bunu düzeltmek ve çeşitli kullanarak benzer sorunlar `UITestControl.WaitForControlXXX()` kullanılabilir yöntemleri kodlanmış UI testi. Sonraki yordamı `WaitForControlEnabled()` bu testin başarısız olmasına neden olan sorunu düzeltmek için yöntemi. Daha fazla bilgi için [olun kodlanmış UI testleri, kayıttan yürütme sırasında belirli olaylar için bekleyin](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

## <a name="edit-and-rerun-the-coded-ui-test"></a>Düzenle ve kodlanmış UI testi yeniden çalıştırın

1.  İçinde **Test Gezgini** penceresinde başarısız testi seçin ve **StackTrace** bölümünde, ilk bağlantısını seçin **UIMap.SimpleAppTest()**.

2.  *UIMap.Designer.cs* kodda vurgulanan hata noktasını içeren dosya açılır:

    ```csharp
    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3.  Bu sorunu düzeltmek için kodlanmış UI testinin CheckBox denetiminin kullanarak devam etmeden önce etkin olmasını bekleyin yapabilir `WaitForControlEnabled()` yöntemi.

    > [!WARNING]
    > Değişiklik yapmayın *UIMap.Designer.cs* dosya. Herhangi bir kod kod kullanarak oluşturduğunuz her üzerine olacak değişiklikler **UIMap - Kodlanmış UI Test Oluşturucusu**. Kayıtlı bir yöntemi değiştirmeniz gerekiyorsa, kopyalayın *UIMap.cs* dosya ve yeniden adlandırın. *UIMap.cs* dosya, yöntemleri ve özellikleri geçersiz kılmak için kullanılabilir *UIMapDesigner.cs* dosya. Orijinal yönteme başvuruyu kaldırmalısınız *CodedUITest.cs* dosya ve adlandırılan yöntem adıyla değiştirin.

4.  İçinde **Çözüm Gezgini**, bulun *UIMap.uitest* kodlanmış UI test projenizdeki.

5.  Kısayol menüsünü açın *UIMap.uitest* ve **açık**.

     Kodlanmış UI testi kodlanmış UI Test Düzenleyicisi'nde görüntülenir. Şimdi, görüntüleyebilir ve kodlanmış UI testi düzenleyebilirsiniz.

6.  İçinde **UI eylemi** bölmesinde, taşımak istediğiniz test yöntemini (SimpleAppTest) seçin *UIMap.cs* veya *UIMap.vb* dosya. Yöntemi, farklı bir dosyaya taşıma test kodu yeniden derlendiğinde üzerine olmaz eklenecek özel kod sağlar.

7.  Seçin **kodu Taşı** düğmesini **kodlanmış UI Test Düzenleyicisi** araç çubuğu.

8.  Microsoft Visual Studio iletişim kutusu görüntülenir. Yöntem öğesinden taşınacak sizi uyarır *UIMap.uitest* dosyasını *UIMap.cs* dosya ve, artık kodlanmış UI Test Düzenleyicisi'ni kullanarak yöntemi düzenlemenin mümkün olması. Seçin **Evet**.

     Test yöntemi kaldırılır *UIMap.uitest* dosya ve artık UI Eylemler bölmesinde görüntülenmez. Taşınan test dosyasını düzenlemek için açın *UIMap.cs* dosya **Çözüm Gezgini**.

9. Visual Studio araç çubuğunda **Kaydet**.

     Test yöntemi güncelleştirmeleri kaydedilir *UIMap.Designer* dosya.

    > [!WARNING]
    > Yöntemi taşıdığınızda Kodlanmış UI Test Düzenleyicisi'ni kullanarak artık düzenleyemezsiniz. Özel kodunuzu eklemeli ve Kod Düzenleyicisi'ni kullanarak korumalısınız.

10. Yöntemden Yeniden Adlandır `SimpleAppTest()` için `ModifiedSimpleAppTest()`

11. Aşağıdaki kullanım deyimini dosyaya ekleyin:

    ```csharp
    using Microsoft.VisualStudio.TestTools.UITesting.WpfControls;
    ```

12. Aşağıdaki `WaitForControlEnabled()` geçemediğinde daha önce tanımlanan kod önce yöntemi:

    ```csharp
    uICheckBoxCheckBox.WaitForControlEnabled();

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

13. İçinde *Codeduıtest1.cs* bulun, dosya **CodedUITestMethod** yöntemi ya da açıklama satırı yapın veya SimpleAppTest() yöntemine başvuruyu yeniden adlandırın ve ardından yeni değiştirin ModifiedSimpleAppTest():

    ```csharp
    [TestMethod]
            public void CodedUITestMethod1()
            {
                // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
                // For more information on generated code, see http://go.microsoft.com/fwlink/?LinkId=179463
                //this.UIMap.SimpleAppTest();
                this.UIMap.ModifiedSimpleAppTest();
            }
    ```

14. Üzerinde **derleme** menüsünde seçin **Çözümü Derle**.

15. Sağ **CodedUITestMethod** yöntemini seçip alt **çalıştırmak testlerini**.

16. Bu kez kodlanmış UI testi testteki tüm adımları başarıyla tamamlar ve **geçti** görüntülenen **Test Gezgini** penceresi.

## <a name="refactor-a-control-in-simplewpfapp"></a>SimpleWPFApp denetimi yeniden düzenleme

1.  İçinde *MainWindow.xaml* dosyasını Tasarımcısı'nda, düğme denetimini seçin.

2.  Üst kısmındaki **özellikleri** penceresinde değişiklik **adı** özellik değerinden **button1** için **buttonA**.

3.  Üzerinde **derleme** menüsünde seçin **Çözümü Derle**.

4.  İçinde **Test Gezgini**çalıştırın **Codeduıtestmethod1**.

     Kodlanmış UI testi button1 olarak UIMap öğesinde başlangıçta eşlenen düğme denetimini konumlandıramadığından test başarısız olur. Yeniden düzenleme kodlanmış UI testlerini bu anlamda etkileyebilir.

5.  İçinde **Test Gezgini**, **StackTrace** bölümünde, ilk bağlantıyı seçin **UIMpa.ModifiedSimpleAppTest ()**.

     *UIMap.cs* dosyasını açar. Hata noktası kodda vurgulanır:

    ```csharp
    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     Bu yordamda daha önce kod satırı kullanarak bildirim `UiStartButton`, yeniden düzenlenmeden önceki UIMap adı olan.

     Sorunu düzeltmek için UIMap'e yeniden işlenmiş denetimi Uımap'a kullanarak ekleyebileceğiniz **kodlanmış UI Test Oluşturucusu**. Testin kodunu kodu kullanmak için bir sonraki yordamda gösterildiği şekilde güncelleştirebilirsiniz.

## <a name="map-refactored-control-rerun-the-test"></a>Test UIMap'e yeniden işlenmiş denetimi yeniden eşleme

1.  İçinde *Codeduıtest1.cs* dosyasındaki **Codeduıtestmethod1()** yöntemi, sağ tıklayın, **kodlanmış UI testi için kod üret** seçip **kullanın Kodlanmış UI Testi Oluşturucusu**.

     **UIMap - Kodlanmış UI Test Oluşturucusu** görünür.

2.  Daha önce oluşturduğunuz masaüstü kısayolunu kullanarak, daha önce oluşturduğunuz SimpleWPFApp uygulamasını çalıştırın.

3.  Üzerinde **UIMap - Kodlanmış UI Test Oluşturucusu** iletişim kutusunda, artı aracını sürükleyin **Başlat** SimpleWPFApp düğmesi.

     **Başlat** düğmesi mavi bir kutu içine alınır. **Kodlanmış UI Testi Oluşturucusu** Seçili denetim için verileri işlemek ve denetimin özelliklerini görüntülemek için birkaç saniye sürer. Dikkat değerini **AutomationUId** olduğu **buttonA**.

4.  Denetimin özelliklerinden, UI Denetim Eşlemesi'ni genişletmek için sol üst köşedeki oku seçin. Dikkat **Uıstartbutton1** seçilir.

5.  Araç çubuğunda seçin **denetim UI kontrol Haritası'na ekleme**.

     Pencerenin altındaki durum görüntüleyerek eylemi doğrular **Seçili denetim UI kontrol haritasına eklendi**.

6.  Üzerinde **UIMap - Kodlanmış UI Test Oluşturucusu** iletişim kutusunda seçin **kod üret**.

     **Kodlanmış UI Test Oluşturucusu - kod üret** iletişim kutusu yeni bir yöntemi gerekli değildir ve bu kod yalnızca UI kontrol haritasında yapılan değişiklikler için oluşturulacak işaretlendiğine ile görünür.

7.  Seçin **oluşturmak**.

8.  SimpleWPFApp Uygulamasını Kapatın.

9. Kapat **UIMap - Kodlanmış UI Testi Oluşturucusu**.

10. İçinde **Çözüm Gezgini**açın *UIMap.Designer.cs* dosya.

11. İçinde *UIMap.Designer.cs* bulun, dosya **Uıstartbutton1** özelliği. Bildirim `SearchProperties` ayarlanır `"buttonA"`:

    ```csharp
    public WpfButton UIStartButton1
            {
                get
                {
                    if ((this.mUIStartButton1 == null))
                    {
                        this.mUIStartButton1 = new WpfButton(this);
                        #region Search Criteria
                        this.mUIStartButton1.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
                        this.mUIStartButton1.WindowTitles.Add("MainWindow");
                        #endregion
                    }
                    return this.mUIStartButton1;
                }
            }
    ```

     Şimdi yeni eşlenen denetimi kullanmak için kodlanmış kullanıcı arabirimini değiştirebilirsiniz. Herhangi bir yöntemi veya kodlanmış UI test özelliklerini geçersiz kılmak istiyorsanız önceki yordamda belirtildiği gibi bu nedenle de yapmalısınız *UIMap.cs* dosya.

12. İçinde *UIMap.cs* dosya, bir oluşturucu ekleyin ve belirtin `SearchProperties` özelliği `UIStartButton` kullanılacak özellik `AutomationID` özellik değerine sahip `"buttonA":`

    ```csharp
    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }
    ```

13. Üzerinde **derleme** menüsünde seçin **Çözümü Derle**.

14. İçinde **Test Gezgini**çalıştırın **Codeduıtestmethod1**.

     Bu kez, kodlanmış UI testi testteki tüm adımları başarıyla tamamlar. İçinde **Test sonuçlarını** penceresinde durumu görürsünüz **geçti**.

## <a name="videos"></a>Videolar

![video bağlantı](../data-tools/media/playvideo.gif) [kodlanmış UI testleri ile çalışmaya başlama](http://go.microsoft.com/fwlink/?LinkID=230573)

![video bağlantı](../data-tools/media/playvideo.gif) [kodlanmış UI testleri Bakım ve hata ayıklama](http://go.microsoft.com/fwlink/?LinkID=230574)

![video bağlantı](../data-tools/media/playvideo.gif) [kodlanmış UI testleri el kodlama](http://go.microsoft.com/fwlink/?LinkID=230575)

## <a name="faq"></a>SSS

[Kodlanmış UI testleri SSS](https://social.msdn.microsoft.com/Forums/vsautotest/3a74dd2c-cef8-4923-abbf-7a91f489e6c4/faqs)

## <a name="see-also"></a>Ayrıca bkz.

- [UI otomasyonunu kullanarak kodunuzu test etme](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Kodlanmış UI test düzenleyicisini kullanarak kodlanmış UI testlerini düzenleme](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
