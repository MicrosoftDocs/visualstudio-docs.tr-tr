---
title: 'İzlenecek yol: Oluşturma, düzenleme ve kodlanmış UI testi bakımını yapma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c25ba7-5c9c-455b-9242-701cda56f90c
caps.latest.revision: 43
ms.author: gewarren
manager: douge
ms.openlocfilehash: aff0363b1fe554e55cae7b58d79cd8f765e76d68
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49257536"
---
# <a name="walkthrough-creating-editing-and-maintaining-a-coded-ui-test"></a>İzlenecek yol: Kodlanmış Bir UI Testi Oluşturmak Düzenlemek ve Sürdürmek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu yönergede kodlanmış UI testinin nasıl oluşturulduğunu, düzenlendiğini ve korunduğunu göstermek üzere basit bir Windows Presentation Foundation (WPF) oluşturacaksınız. İzlenecek yol çeşitli zamanlama sorunları ve yeniden düzenlemeyi denetleme tarafından kırılan testleri düzeltmeye ilişkin çözümler sağlar.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu örnek için şunlar gerekir:  
  
-   Visual Studio Enterprise  
  
### <a name="create-a-simple-wpf-application"></a>Basit WPF Uygulaması Oluşturma  
  
1.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje**.  
  
     **Yeni proje** iletişim kutusu görüntülenir.  
  
2.  İçinde **yüklü** bölmesini genişletin **Visual C#** ve ardından **Windows Masaüstü**.  
  
3.  Orta bölmede hedef çerçeve açılır listesinin değerine ayarlandığını doğrulayın **.NET Framework 4.5**.  
  
4.  Orta bölmede seçin **WPF uygulaması** şablonu.  
  
5.  İçinde **adı** metin kutusunda, **SimpleWPFApp**.  
  
6.  Projeyi kaydetmek için bir klasör seçin. İçinde **konumu** metin kutusuna, klasörün adını yazın.  
  
7.  Seçin **Tamam**.  
  
     Visual Studio için WPF Tasarımcısı açılır ve projenin MainWindow öğesini görüntüler.  
  
8.  Araç kutusu açık değilse, açın. Seçin **görünümü** menüsünü seçip **araç kutusu**.  
  
9. Altında **tüm WPF denetimleri** bölümü bir **düğmesi**, **onay kutusu** ve **ProgressBar** tasarım MainWindow üzerine denetimi Surface.  
  
10. Düğme denetimini seçin. Özellikler penceresinde değerini değiştirin **adı** özelliğinden \<No Name > button1 için. Ardından değerini değiştirin **içerik** özelliğini Başlat düğmesi.  
  
11. ProgressBar denetimini seçin. Özellikler penceresinde değer değeri için değiştirme **adı** özelliğinden \<No Name > den progressbar1'e. Ardından değerini değiştirin **maksimum** özelliğinden **100** için **10000**.  
  
12. Onay kutusu denetimini seçin. Özellikler penceresinde değerini değiştirin **adı** özelliğinden \<No Name > checkBox1 ve Temizle **IsEnabled** özelliği.  
  
     ![Basit WPF uygulaması](../test/media/codedui-wpfapp.png "CodedUI_WPFApp")  
  
13. Bir tıklama olayı işleyicisi eklemek için düğme denetimini çift tıklayın.  
  
     MainWindow.xmal.cs, yeni button1_Click yönteminde imleç ile Kod Düzenleyicisi'nde görüntülenir.  
  
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
  
### <a name="verify-the-wpf-application-runs-correctly"></a>WPF Uygulamasının Düzgün Çalıştığını Doğrulama  
  
1.  Üzerinde **hata ayıklama** menüsünde **hata ayıklamayı Başlat** veya basın **F5**.  
  
2.  Onay kutusu denetimi devre dışı olduğuna dikkat edin. Seçin **Başlat**.  
  
     Birkaç saniye içinde ilerleme çubuğu tam %100 bitmiş olmalıdır.  
  
3.  Onay kutusu denetimi şimdi seçebilirsiniz.  
  
4.  SimpleWPFApp Uygulamasını Kapatın.  
  
### <a name="create-and-run-a-coded-ui-test-for-simplewpfapp"></a>SimpleWPFApp için Kodlanmış Kullanıcı Arabirimi Testi Oluşturma ve Çalıştırma  
  
1.  Daha önce oluşturduğunuz SimpleWPFApp uygulamasını bulun. Varsayılan olarak, uygulamanın C:\Users yer alacağı\\< kullanıcı adı\>\Documents\Visual Studio \<sürüm > \Projects\SimpleWPFApp\SimpleWPFApp\bin\Debug\SimpleWPFApp.exe  
  
2.  SimpleWPFApp uygulaması için bir masaüstü kısayolu oluşturun. SimpleWPFApp.exe sağ tıklatın ve seçin **kopyalama**. Masaüstünüzde sağ tıklatın ve seçin **kısayolu Yapıştır**.  
  
    > [!TIP]
    >  Uygulamaya bir kısayol eklenmesi, uygulamayı hızlıca başlatmanızı sağladığından uygulamanız açısından Kodlanmış UI testleri ekleyip değiştirmenizi kolaylaştırır.  
  
3.  Çözüm Gezgini'nde çözüme sağ tıklayın, seçin **Ekle** seçip **yeni proje**.  
  
     **Yeni Proje Ekle** iletişim kutusu görüntülenir.  
  
4.  İçinde **yüklü** bölmesini genişletin **Visual C#** ve ardından **Test**.  
  
5.  Orta bölmede seçin **kodlanmış UI Test projesi** şablonu.  
  
6.  Seçin **Tamam**.  
  
     Çözüm Gezgini içinde yeni kodlanmış UI test projesi adlı **Codeduıtestproject1** çözümünüze eklenir.  
  
     **Kodlanmış UI testi için kod üret** iletişim kutusu görüntülenir.  
  
7.  Seçin **eylemleri Kaydet, UI haritasını Düzenle veya onaylama işlemleri Ekle** seçenek ve **Tamam**.  
  
     UIMap – Kodlanmış UI Test Oluşturucusu görünür ve Visual Studio penceresi simge durumuna küçültülür.  
  
     İletişim kutusundaki seçenekler hakkında daha fazla bilgi için bkz. [kodlanmış UI testleri](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
8.  Seçin **kaydı Başlat** UIMap – Kodlanmış UI Test Oluşturucusu.  
  
     ![Kaydı Başlat](../test/media/cuit-builder-record.png "CUIT_Builder_Record")  
  
     Gerekirse, gelen e-posta ile uğraşmak zorunda örneğin kayıt duraklatabilirsiniz.  
  
     ![Kaydı Duraklat](../test/media/cuit.png "CUIT_")  
  
    > [!WARNING]
    >  Masaüstü üzerinde gerçekleştirilen tüm eylemler kaydedilir. Hassas veriler kayda eklenmesini açabilir eylemleri gerçekleştiriyorsanız kaydı duraklatın.  
  
9. Masaüstü kısayolunu kullanarak SimpleWPFApp başlatın.  
  
     Önceki örneklerde olduğu gibi onay kutusu denetimi devre dışı bırakıldığını dikkat edin.  
  
10. SimpleWPFApp üzerinde seçin **Başlat**.  
  
     Birkaç saniye içinde ilerleme çubuğu tam %100 bitmiş olmalıdır.  
  
11. Artık etkin onay kutusu denetimini kontrol edin.  
  
12. SimpleWPFApp uygulamasını kapatın.  
  
13. UIMap - Kodlanmış UI Test Oluşturucusu seçin **kod üret**.  
  
14. Yöntem adı türü **SimpleAppTest** ve **Ekle ve Oluştur**. Birkaç saniye içinde Kodlanmış UI testi görünür ve Çözüm'e eklenir.  
  
15. UIMap – Kodlanmış Kullanıcı Arabirimi Test Oluşturucusu uygulamasını kapatın.  
  
     Kod Düzenleyicisi'nde CodedUITest1.cs dosyası görüntülenir.  
  
16. Projenizi kaydedin.  
  
### <a name="run-the-coded-ui-test"></a>Kodlanmış UI Testi Çalıştırma  
  
1.  Gelen **TEST** menüsünde seçin **Windows** seçip **Test Gezgini**.  
  
2.  Gelen **derleme** menüsünde seçin **Çözümü Derle**.  
  
3.  Codeduıtest1.cs dosyasında bulun **CodedUITestMethod** yöntemi, sütuna sağ tıklayıp **çalıştırmak testlerini**, veya Test Gezgini'nde testi çalıştırın.  
  
     Kodlanmış UI testi çalışırken, SimpleWPFApp görülebilir. Bir önceki yordamda yaptığınız adımları oluşturur. Ancak, onay kutusu denetimi için onay kutusunu seçmek test çalıştığında, Test Sonuçları penceresi testin başarısız olduğunu gösterir. Bu onay kutusunu seçmek test çalışmasından, ancak ilerleme çubuğu % 100 tamamlandı olana kadar onay kutusu denetimi devre dışı bırakıldığını ile uyumlu değildir. Bunu düzeltmek ve çeşitli kullanarak benzer sorunlar `UITestControl.WaitForControlXXX()` kullanılabilir yöntemleri kodlanmış UI testi. Sonraki yordamı `WaitForControlEnabled()` bu testin başarısız olmasına neden olan sorunu düzeltmek için yöntemi. Daha fazla bilgi için [yapmadan kodlanmış UI testleri beklemek için belirli olayları sırasında kayıttan yürütme](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).  
  
### <a name="edit-and-rerun-the-coded-ui-test"></a>Kodlanmış Kullanıcı Arabirimi Testini Düzenleme ve Yeniden Çalıştırma  
  
1.  Test Gezgini penceresinde başarısız testi seçin ve **StackTrace** bölümünde, ilk bağlantısını seçin **UIMap.SimpleAppTest()**.  
  
2.  Kodda vurgulanan hata noktasını içeren UIMap.Designer.cs dosyası açılır:  
  
    ```csharp  
  
    // Select 'CheckBox' check box  
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;  
    ```  
  
3.  Bu sorunu düzeltmek için kodlanmış UI testinin CheckBox denetiminin kullanarak devam etmeden önce etkin olmasını bekleyin yapabilir `WaitForControlEnabled()` yöntemi.  
  
    > [!WARNING]
    >  UIMap.Designer.cs dosyasını değiştirmeyin. UIMap - Kodlanmış UI Test Oluşturucusu kullanarak kodu her oluşturduğunuzda, UIMapDesigner.cs dosyasında yaptığınız herhangi bir kod değişikliğinin üzerine yazılır. Kayıtlı bir yöntemi değiştirmeniz gerekiyorsa, yöntemi UIMap.cs dosyasına kopyalayıp yeniden adlandırmanız gerekir. UIMap.cs dosyası, UIMapDesigner.cs dosyasındaki yöntemleri ve özellikleri geçersiz kılmak için kullanılabilir. Kodlanmış UITest.cs dosyasındaki orijinal yönteme başvuruyu kaldırıp yeniden adlandırılan yöntem adıyla değiştirmelisiniz.  
  
4.  Çözüm Gezgini'nde bulun **UIMap.uitest** kodlanmış UI test projenizdeki.  
  
5.  Kısayol menüsünü açın **UIMap.uitest** ve **açık**.  
  
     Kodlanmış UI testi kodlanmış UI Test Düzenleyicisi'nde görüntülenir. Şimdi, görüntüleyebilir ve kodlanmış UI testi düzenleyebilirsiniz.  
  
6.  İçinde **UI eylemi** , ne zaman üzerine olmayacaktır yazılmayacak kod işlevselliğini UIMap.cs veya UIMap.vb dosyasına test kodu taşımak istediğiniz test yöntemini (SimpleAppTest) yeniden bölmesinde seçin.  
  
7.  Seçin **kodu Taşı** kodlanmış UI Test Düzenleyicisi araç çubuğu düğmesi.  
  
8.  Microsoft Visual Studio iletişim kutusu görüntülenir. Yöntem UIMap.uitest dosyasından UIMap.cs dosyasına taşınması için ve artık kodlanmış UI Test Düzenleyicisi'ni kullanarak yöntemi düzenlemenin mümkün olmayacağı konusunda uyarır. Seçin **Evet**.  
  
     Test yöntemi UIMap.uitest dosyasından kaldırılır ve artık UI Eylemler bölmesinde görüntülenmez. Taşınan test dosyasını düzenlemek için Çözüm Gezgini'nden UIMap.cs dosyasını açın.  
  
9. Üzerinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] araç seçin **Kaydet**.  
  
     Test yöntemi güncelleştirmeleri UIMap.Designer dosyasında kaydedilir.  
  
    > [!CAUTION]
    >  Yöntemi taşıdığınızda Kodlanmış UI Test Düzenleyicisi'ni kullanarak artık düzenleyemezsiniz. Özel kodunuzu eklemeli ve Kod Düzenleyicisi'ni kullanarak korumalısınız.  
  
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
  
13. Codeduıtest1.cs dosyasında **CodedUITestMethod** yöntemi ya da açıklama satırı yapın veya SimpleAppTest() yöntemine başvuruyu yeniden adlandırın ve sonra yeni ModifiedSimpleAppTest() ile değiştirin:  
  
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
  
16. Bu kez kodlanmış UI testi başarıyla testteki tüm adımları tamamlandıktan ve **geçti** Test Gezgini penceresinde görüntülenir.  
  
### <a name="refactor-a-control-in-the-simplewpfapp"></a>SimpleWPFApp içinde Denetimi Yeniden Düzenleme  
  
1.  MainWindow.xaml dosyasındaki Tasarımcı'da düğme denetimini seçin.  
  
2.  Özellikler penceresinin en üstünde değiştirme **adı** button1 özellik değerini buttonA.  
  
3.  Üzerinde **derleme** menüsünde seçin **Çözümü Derle**.  
  
4.  Test Gezgini'nde çalıştırma **Codeduıtestmethod1**.  
  
     Kodlanmış UI testi button1 olarak UIMap öğesinde başlangıçta eşlenen düğme denetimini konumlandıramadığından test başarısız olur. Yeniden düzenleme kodlanmış UI testlerini bu anlamda etkileyebilir.  
  
5.  Test Gezgini penceresinde de **StackTrace** bölümünde, ilk bağlantıyı seçin **UIMpa.ModifiedSimpleAppTest ()**.  
  
     UIMap.cs dosyası açılır. Hata noktası kodda vurgulanır:  
  
    ```csharp  
  
    // Click 'Start' button  
    Mouse.Click(uIStartButton, new Point(27, 10));  
    ```  
  
     Bu yordamda daha önce kod satırı kullanarak bildirim `UiStartButton`, yeniden düzenlenmeden önceki UIMap adı olan.  
  
     Sorunu düzeltmek için UIMap'e yeniden işlenmiş denetimi Kodlanmış UI Test Oluşturucusu kullanarak ekleyebilirsiniz. Testin kodunu, kodu kullanmak için sonraki yordamda gösterildiği şekilde güncelleştirebilirsiniz.  
  
### <a name="map-refactored-control-and-edit-and-rerun-the-coded-ui-test"></a>Yeniden Düzenlenmiş Denetimi Eşleme ve Kodlanmış UI Testini Düzenleme ve Yeniden Çalıştırma  
  
1.  Codeduıtest1.cs dosyasında içinde **Codeduıtestmethod1()** yöntemi, sağ tıklayın, **kodlanmış UI testi için kod üret** seçip **kullanım kodlanmış UI Test Oluşturucusu**.  
  
     UIMap – Kodlanmış UI Test Oluşturucusu görünür.  
  
2.  Daha önce oluşturduğunuz masaüstü kısayolunu kullanarak, daha önce oluşturduğunuz SimpleWPFApp uygulamasını çalıştırın.  
  
3.  UIMap – Kodlanmış UI Test Oluşturucusu üzerinde artı aracını sürükleyin **Başlat** SimpleWPFApp düğmesi.  
  
     **Başlat** düğmesi mavi bir kutu içine alınır ve kodlanmış UI Test Oluşturucusu'nu Seçili denetim için verileri işlemek için birkaç saniye sürer ve denetim özelliklerini görüntüler. Dikkat **AutomationUId** adlı **buttonA**.  
  
4.  Denetimin özelliklerinden, UI Denetim Eşlemesi'ni genişletmek için sol üst köşedeki oku seçin. Dikkat **Uıstartbutton1** seçilir.  
  
5.  Araç çubuğunda seçin **denetim UI kontrol Haritası'na ekleme**.  
  
     Pencerenin altındaki durum görüntüleyerek eylemi doğrular **Seçili denetim UI kontrol haritasına eklendi**.  
  
6.  UIMap – Kodlanmış UI Test Oluşturucusu'nü seçin **kod üret**.  
  
     Kodlanmış UI Test Oluşturucu – Kod Oluştur yeni bir yönteme gerek olmadığı notuyla görüntülenir ve bu kod yalnızca UI kontrol haritasında değişiklikler olduğunda oluşturulacaktır.  
  
7.  Seçin **oluşturmak**.  
  
8.  SimpleWPFApp.exe uygulamasını kapatın.  
  
9. UIMap – Kodlanmış Kullanıcı Arabirimi Test Oluşturucusu uygulamasını kapatın.  
  
     UIMap – Kodlanmış UI Test Oluşturucusunun UI kontrol eşlemesi değişikliklerini işlemesi bir kaç saniye alır.  
  
10. Çözüm Gezgini'nde, UIMap.Designer.cs dosyasını açın.  
  
11. UIMap.Designer.cs dosyasında Uıstartbutton1 özelliği bulun. Bildirim `SearchProperties` ayarlanır `"buttonA"`:  
  
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
  
     Şimdi yeni eşlenen denetimi kullanmak için kodlanmış kullanıcı arabirimini değiştirebilirsiniz. Önceki yordamda işaret edildiği gibi, kodlanmış UI testindeki herhangi bir yöntemi ya da özelliği geçersiz kılmak istiyorsanız, bunu UIMap.cs dosyasında yapmalısınız.  
  
12. UIMap.cs dosyasına bir oluşturucu ekleyin ve belirtin `SearchProperties` özelliği `UIStartButton` kullanılacak özellik `AutomationID` özellik değerine sahip `"buttonA":`  
  
    ```csharp  
  
    public UIMap()  
            {  
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";  
            }  
  
    ```  
  
13. Üzerinde **derleme** menüsünde seçin **Çözümü Derle**.  
  
14. Test Gezgini'nde Codeduıtestmethod1 çalıştırın.  
  
     Bu kez, kodlanmış UI testi testteki tüm adımları başarıyla tamamlar.  Test Sonuçları penceresinde durumu görürsünüz **geçti**.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
  
### <a name="videos"></a>Videolar  
 ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") [kodlanmış UI testleri-DeepDive-Episode1-GettingStarted](http://go.microsoft.com/fwlink/?LinkID=230573)  
  
 ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") [kodlanmış UI testleri-DeepDive-Episode2-MaintainenceAndDebugging](http://go.microsoft.com/fwlink/?LinkID=230574)  
  
 ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") [kodlanmış UI testleri-DeepDive-Episode3-HandCoding](http://go.microsoft.com/fwlink/?LinkID=230575)  
  
### <a name="hands-on-lab"></a>Laboratuvarda eller  
 [MSDN sanal Laboratuvar: Visual Studio 2010 ile kodlanmış UI testleri oluşturmaya giriş](http://go.microsoft.com/fwlink/?LinkID=22508)  
  
### <a name="faq"></a>SSS  
 [Kodlanmış UI testleri SSS - 1](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Kodlanmış UI testleri SSS -2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### <a name="forum"></a>Forum  
 [(Visual Studio UI Otomasyon Codeduı dahil) test etme](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)   
 [WPF Tasarımcısı ile çalışmaya başlama](http://msdn.microsoft.com/en-us/18e61d03-b96a-4058-a166-8ec6b3f6116b)   
 [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Kodlanmış UI Test Düzenleyicisi'ni Kullanarak Kodlanmış UI Testlerini Düzenleme](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)



