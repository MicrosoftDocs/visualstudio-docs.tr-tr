---
title: Web Performans Test Sonuçları Görüntüleyicisi eklenti oluşturma
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, Visual Studio Add-in
- Visual Studio Add-in, Web performance tests
ms.assetid: 1118c604-4b1b-4b21-a04e-45995b676fa8
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 6672bd1e38dee5b27d350b9d2e12626cef122115
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068347"
---
# <a name="how-to-create-a-visual-studio-add-in-for-the-web-performance-test-results-viewer"></a>Nasıl yapılır: Web Performans Test Sonuçları Görüntüleyicisi için bir Visual Studio eklentisi oluşturma

Kullanıcı Arabiriminde genişletebileceğiniz **Web Performans Test Sonuçları Görüntüleyicisi** aşağıdaki ad alanlarını kullanarak:

-   <xref:Microsoft.VisualStudio.TestTools.LoadTesting>

-   <xref:Microsoft.VisualStudio.TestTools.WebTesting>

Ayrıca, bulunan LoadTestPackage DLL'ye bir başvuru eklemeniz gerekir *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies* klasör.

Genişletmek için **Web Performans Test Sonuçları Görüntüleyicisi**'s UI, Visual Studio eklentisi ve bir kullanıcı denetimi oluşturmalısınız. Aşağıdaki yordamlar eklenti, kullanıcı denetimi oluşturma işlemleri açıklanmaktadır ve nasıl uygulanacağını genişletmek gereken sınıfların **Web Performans Test Sonuçları Görüntüleyicisi**ait kullanıcı Arabirimi.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="create-or-open-a-solution-that-contains-an-aspnet-web-application-and-a-web-performance-and-load-test-project"></a>Bir ASP.NET web uygulaması ve web performansı ve yük testi projesi içeren bir çözüm açın veya oluşturun

### <a name="to-prepare-for-extending-the-web-performance-test-results-viewer"></a>Web Performans Test Sonuçları Görüntüleyicisi'ni genişletmek üzere hazırlanmak için

Oluşturabilir veya ASP.NET web uygulaması içeren deneme yapabileceğiniz ve bir web performansı ve yük proje ASP.NET web uygulaması için bir veya daha fazla web performans testleri test üretim dışı çözümü açın.

> [!NOTE]
> Bir ASP.NET web uygulamasını oluşturabilir ve web performansı ve yük testi içindeki yordamları izleyerek web performans testleri içeren proje [nasıl yapılır: web hizmeti testi oluşturma](../test/how-to-create-a-web-service-test.md) ve [oluştur ve Çalıştır kodlanmış web performans testi](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="create-a-visual-studio-add-in"></a>Visual Studio eklenti oluşturma

Bir Visual Studio tümleşik geliştirme ortamında (IDE) çalışan derlenmiş DLL eklentidir. Derleme fikri mülkiyetinizi korur ve performansı geliştirir. Eklentileri elle oluşturabilseniz de bunu kullanmayı daha kolay bulabilirsiniz **Eklenti Sihirbazı**. Bu sihirbaz bir işlevsel fakat basit oluşturduktan sonra hemen çalıştırabilirsiniz eklenti oluşturur. Sonra **Eklenti Sihirbazı** temel programı oluşturduktan kodu ekleyin ve özelleştirin.

 **Eklenti Sihirbazı** bir görünen ad ve açıklama eklentiniz için sağlamanıza olanak tanır. Her ikisi de görünür **Eklenti Yöneticisi**. İsteğe bağlı olarak, ekleyen Sihirbazı kodu oluşturmasını sağlayabilirsiniz **Araçları** menüsünde eklentiyi açmak için bir komutu. Ayrıca özel görüntülemeyi seçebilirsiniz **hakkında** eklentiniz için iletişim kutusu. Sihirbaz tamamlandığında, eklentiyi uygulayan yalnızca bir sınıfı olan yeni bir proje vardır. Bu sınıf, Bağlan olarak adlandırılır.

 Kullanacağınız **Eklenti Yöneticisi** bu makalenin sonunda.

### <a name="to-create-an-add-in-by-using-the-add-in-wizard"></a>Eklenti Sihirbazı'nı kullanarak bir eklenti oluşturmak için

1. İçinde **Çözüm Gezgini**, çözüme sağ tıklayın, seçin **Ekle**ve ardından **yeni proje**.

    **Yeni proje** iletişim kutusu görüntülenir.

2. Altında **yüklü şablonlar**, genişletme **diğer proje türleri** seçip **genişletilebilirlik**.

3. Şablonlar listesinde seçin **Visual Studio eklentisini**.

4. Altında **adı**, eklenti için bir ad yazın. Örneğin, **WebPerfTestResultsViewerAddin**.

5. Seçin **Tamam**.

    Visual Studio **Eklenti Sihirbazı** başlatır.

6. Seçin **sonraki**.

7. Üzerinde **bir programlama dili seçin** sayfasında, eklentiyi yazmak için kullanmak istediğiniz programlama dilini seçin.

   > [!NOTE]
   > Bu konu Visual C# örnek kodunu kullanır.

8. Üzerinde **seçin, bir uygulama ana bilgisayarı** sayfasında **Visual Studio** temizleyin **Visual Studio Macros**.

9. Seçin **sonraki**.

10. Bir ad ve eklentiniz için bir açıklama yazın **bir ad ve açıklama girin** sayfası.

     Eklentiyi oluşturduktan sonra adını ve açıklamasını görüntülenen **kullanılabilir eklentiler** listesinde **Eklenti Yöneticisi**. Eklentinizin açıklamasına yeterli ayrıntı kullanıcıların hangi eklentinizi edinebilirsiniz işe yaradığını, nasıl çalıştığını ve benzeri ekleyin.

11. Seçin **sonraki**.

12. Üzerinde **eklenti seçeneklerini seçin** sayfasında **my ana bilgisayar uygulaması başladığında yüklenmesini eklenti istiyorum**.

13. Kalan onay kutularını temizleyin.

14. Üzerinde **'Yardım konusu' bilgilerini seçme** sayfasında, görüntülenecek eklentinizi hakkında bilgi isteyip istemediğinizi belirtebilirsiniz bir **hakkında** iletişim kutusu. Görüntülenecek bilgi istiyorsanız seçin **my 'Hakkında' kutusu bilgi sunmak için eklenti Evet, istiyorum** onay kutusu.

     Visual Studio için eklenebilir bilgi **hakkında** iletişim kutusunda, sürüm numarası, destek ayrıntıları, lisans verisi vb. içerir.

15. Seçin **sonraki**.

16. Seçtiğiniz seçenekler görüntülenir **özeti** sayfasını gözden geçirmenizi sağlar. Memnun kaldığınızda **son** eklenti oluşturmak için. Bir şey değiştirmek istiyorsanız, seçin **geri** düğmesi.

     Yeni çözüm ve Proje oluşturulur ve *Connect.cs* yeni eklenti görüntülenir dosya **Kod Düzenleyicisi**.

     Kod ekleyeceksiniz *Connect.cs* bu WebPerfTestResultsViewerAddin projesi tarafından başvurulacak olan bir kullanıcı denetimi oluşturur aşağıdaki yordamda sonra dosya.

    Bir eklenti oluşturulduktan sonra etkinleştirilmeden önce Visual Studio ile kaydetmelisiniz **Eklenti Yöneticisi**. Sahip bir XML dosyası kullanarak bunu bir *.addin* dosya adı uzantısı.

    *.Addin* dosya içinde görüntülemek için Visual Studio gerektiren bilgilerin açıklar **Eklenti Yöneticisi**. Visual Studio başladığında bakar *.addin* dosya konumu için tüm kullanılabilir *.addin* dosyaları. Herhangi birini bulursa, XML dosyasını okur ve verir **Eklenti Yöneticisi** eklenti tıklatıldığında başlatmak için gerekli bilgileri.

    *.Addin* dosyası, eklenti kullanarak oluşturduğunuzda otomatik olarak oluşturulursa **Eklenti Sihirbazı**.

### <a name="add-in-file-locations"></a>Eklenti dosyası konumları

İki kopyalar *.addin* dosyaları tarafından otomatik olarak oluşturulur **Eklenti Sihirbazı**gibi:

|**. Eklenti dosyası**|**Açıklama**|
|-|----------------------------|-|
|Kök proje klasörü|Eklenti projesinin dağıtımı için kullanılır. Projeye düzenleme kolaylığı dahil ve XCopy tarzı dağıtımının yerel yolu vardır.|
|Eklenti klasörü|Eklentinin hata ayıklama ortamında çalıştırılması için kullanılır. Her zaman geçerli yapı yapılandırmasının çıktı yolunu göstermelidir.|

## <a name="create-a-windows-form-control-library-project"></a>Bir Windows Form denetim kitaplığı projesi oluşturun

Önceki yordamda oluşturduğunuz Visual Studio eklentisi bir örneğini oluşturmak için bir Windows Forms Denetim Kitaplığı projesine başvuran bir <xref:System.Windows.Forms.UserControl> sınıfı.

### <a name="to-create-a-control-to-be-used-in-the-web-test-results-viewer"></a>Web Test Sonuçları Görüntüleyicisi'nde kullanılmak üzere bir denetim oluşturmak için

1.  İçinde **Çözüm Gezgini**, çözüme sağ tıklayın, seçin **Ekle**ve ardından **yeni proje**.

     **Yeni proje** iletişim kutusu görüntülenir.

2.  Altında **yüklü şablonlar**, genişletme **Visual Basic** veya **Visual C#** seçip **Windows**.

    > [!NOTE]
    > Bu konu Visual C# örnek kodunu kullanır.

3.  Şablonlar listesinde seçin **Windows Forms Denetim Kitaplığı**.

4.  Altında **adı**, eklenti için bir ad yazın. Örneğin, **WebPerfTestResultsViewerControl**.

5.  Seçin **Tamam**.

     Windows forms denetim kitaplığı projesi WebPerfTestResultsViewerControl eklenir **Çözüm Gezgini** ve *UserControl1.cs* Tasarım modunda görüntülenir.

6.  Gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.DataGridView> userControl1 yüzeyine sürükleyin.

7.  Eylem etiket karakterini tıklayın (![akıllı etiket karakterini](../test/media/vs_winformsmttagglyph.gif)) sağ üst köşesindeki <xref:System.Windows.Forms.DataGridView> ve aşağıdaki adımları izleyin:

    1.  Seçin **üst kapsayıcıya Yerleştir**.

    2.  Onay kutularını temizleyin **eklemeyi etkinleştir**, **düzenlemeyi etkinleştir**, **silmeyi etkinleştir** ve **sütun yeniden sıralamayı etkinleştir**.

    3.  Seçin **sütun ekleme**.

         **Sütun Ekle** iletişim kutusu görüntülenir.

    4.  İçinde **türü** aşağı açılan listesinden **DataGridViewTextBoxColumn**.

    5.  "Column1" metnini temizleyin **üst bilgi metni**.

    6.  Seçin **ekleme**.

    7.  Seçin **Kapat**.

8.  İçinde **özellikleri** penceresinde değişiklik **(ad)** özelliği <xref:System.Windows.Forms.DataGridView> için **resultControlDataGridView**.

9. Tasarım yüzeyi ve select sağ **kodu görüntüle**.

     *UserControl1.cs* dosya görüntülendiği **Kod Düzenleyicisi**.

10. Örneklenen adını değiştirmek <xref:System.Windows.Forms.UserControl> UserContro1'dan resultControl sınıfına:

    ```csharp
    namespace WebPerfTestResultsViewerControl
    {
        public partial class resultControl : UserControl
        {
            public resultControl()
            {
                InitializeComponent();
            }
    ```

     Sonraki yordamda, WebPerfTestResultsViewerAddin proje için kod ekleyeceksiniz *Connect.cs* resultControl sınıfına başvuracak dosyası.

     İçin bazı ek kod ekleme *Connect.cs* daha sonra dosya.

## <a name="add-code-to-the-webperftestresultsvieweraddin"></a>Webperftestresultsvieweraddin'e kod ekleyin

### <a name="to-add-code-to-the-visual-studio-add-in-to-extend-the-web-test-results-viewer"></a>Visual Studio Web Test Sonuçları Görüntüleyicisi'ni genişletmek için eklenti için kod eklemek için

1.  İçinde **Çözüm Gezgini**, sağ **başvuruları** seçip WebPerfTestResultsViewerAddin proje düğümünü **Başvuru Ekle**.

2.  İçinde **Başvuru Ekle** iletişim kutusunda **.NET** sekmesi.

3.  Aşağı kaydırın ve select **Microsoft.VisualStudio.QualityTools.WebTestFramework** ve **System.Windows.Forms**.

4.  Seçin **Tamam**.

5.  Sağ **başvuruları** düğümünü tekrar ve select **Başvuru Ekle**.

6.  İçinde **Başvuru Ekle** iletişim kutusunda **Gözat** sekmesi.

7.  Seçmek için açılan **konum** gidin *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies* seçip  *Microsoft.VisualStudio.QualityTools.LoadTestPackage.dll* dosya.

8.  Seçin **Tamam**.

9. WebPerfTestResultsViewerAddin proje düğümünü sağ tıklatın ve seçin **Başvuru Ekle**.

10. İçinde **Başvuru Ekle** iletişim kutusunda **projeleri** sekmesi.

11. Altında **proje adı**seçin **WebPerfTestResultsViewerControl** projesini ve ardından **Tamam**.

12. Varsa *Connect.cs* dosya içinde hala açık değilse **Çözüm Gezgini**, sağ **Connect.cs** dosya WebPerfTestResultsViewerAddin projesindeki ve seçin **Kod**.

13. İçinde *Connect.cs* dosyasında, aşağıdaki kullanım deyimlerini ekleyin:

    ```csharp
    using System.IO;
    using System.Windows.Forms;
    using System.Collections.Generic;
    using Microsoft.VisualStudio.TestTools.LoadTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using WebPerfTestResultsViewerControl;
    ```

14. Listenin sonuna kaydırın *Connect.cs* dosya. İçin bir GUID'ler listesi eklemeniz <xref:System.Windows.Forms.UserControl> olasılığına karşı birden fazla örneğini **Web Performans Test Sonuçları Görüntüleyicisi** açıktır. Bu liste kullanan kodu ekleyeceksiniz.

     Daha sonra kod OnDiscconection yönteminde ikinci bir dize listesi kullanılır.

    ```csharp
    private DTE2 _applicationObject;
    private AddIn _addInInstance;

    private Dictionary<Guid, List<UserControl>> m_controls = new Dictionary<Guid, List<UserControl>>();        private List<string> temporaryFilePaths = new List<string>();
    ```

15. *Connect.cs* dosya Bağlan adında bir sınıf oluşturur <xref:Extensibility.IDTExtensibility2> sınıfı ve ayrıca Visual Studio eklentisi uygulanması için bazı yöntemler içerir. Yöntemlerden biri eklentinin yüklenmekte olduğuna dair bildirim alan OnConnection yöntemine var. OnConnection yöntemine için genişletilebilirlik paketinizi oluşturmak için LoadTestPackageExt sınıfını kullanacağı **Web Performans Test Sonuçları Görüntüleyicisi**. Aşağıdaki kodu OnConnection yöntemine ekleyin:

    ```csharp
    public void OnConnection(object application, ext_ConnectMode connectMode, object addInInst, ref Array custom)
                {
                _applicationObject = (DTE2)application;
                _addInInstance = (AddIn)addInInst;

                // Create a load test packge extensibility class.            LoadTestPackageExt loadTestPackageExt = _applicationObject.GetObject("Microsoft.VisualStudio.TestTools.LoadTesting.LoadTestPackageExt") as LoadTestPackageExt;            // Process open windows.            foreach (WebTestResultViewer webTestResultViewer in loadTestPackageExt.WebTestResultViewerExt.ResultWindows)            {                WindowCreated(webTestResultViewer);            }            // Create event handlers.            loadTestPackageExt.WebTestResultViewerExt.WindowCreated += new EventHandler<WebTestResultViewerExt.WindowCreatedEventArgs>(WebTestResultViewerExt_WindowCreated);            loadTestPackageExt.WebTestResultViewerExt.WindowClosed += new EventHandler<WebTestResultViewerExt.WindowClosedEventArgs>(WebTesResultViewer_WindowClosed);            loadTestPackageExt.WebTestResultViewerExt.SelectionChanged += new EventHandler<WebTestResultViewerExt.SelectionChangedEventArgs>(WebTestResultViewer_SelectedChanged);
            }
    ```

16. OnConnection yöntemine eklediğiniz loadTestPackageExt.WebTestResultViewerExt.WindowCreated olay işleyicisi ve Webtestresultviewerext_windowcreated yöntemi WebTestResultViewerExt_WindowCreated yöntemi oluşturmak için bağlan sınıfına aşağıdaki kodu ekleyin, WebTestResultViewerExt_WindowCreated yöntemi çağırır.

    ```csharp
            void WebTestResultViewerExt_WindowCreated(object sender, WebTestResultViewerExt.WindowCreatedEventArgs e)
            {
                // New control added to new result viewer window.
                WindowCreated(e.WebTestResultViewer);
            }

    private void WindowCreated(WebTestResultViewer viewer)        {            // Instantiate an instance of the resultControl referenced in the WebPerfTestResultsViewerControl project.
                resultControl resultControl = new resultControl();            // Add to the dictionary of open playback windows.            System.Diagnostics.Debug.Assert(!m_controls.ContainsKey(viewer.TestResultId));            List<UserControl> userControls = new List<UserControl>();            userControls.Add(resultControl);            // Add Guid to the m_control List to manage Result viewers and controls.            m_controls.Add(viewer.TestResultId, userControls);            // Add tabs to the playback control.            resultControl.Dock = DockStyle.Fill;            viewer.AddResultPage(new Guid(), "Sample", resultControl);        }
    ```

17. OnConnection yöntemine eklediğiniz loadTestPackageExt.WebTestResultViewerExt.SelectionChanged olay işleyicisine yönelik WebTestResultViewer_SelectedChanged yöntemi oluşturmak için bağlan sınıfına aşağıdaki kodu ekleyin:

    ```csharp
    void WebTestResultViewer_SelectedChanged(object sender, WebTestResultViewerExt.SelectionChangedEventArgs e)
    {
        foreach (UserControl userControl in m_controls[e.TestResultId])            {                // Update the userControl in each result viewer.                resultControl resultControl = userControl as resultControl;                if (resultControl != null)                    // Call the resultControl's Update method (This will be added in the next procedure).                    resultControl.Update(e.WebTestRequestResult);            }
    }
    ```

18. OnConnection yöntemine eklediğiniz loadTestPackageExt.WebTestResultViewerExt.WindowClosed olay işleyicisi WebTesResultViewer_WindowClosed yöntemi oluşturmak için bağlan sınıfına aşağıdaki kodu ekleyin:

    ```csharp
    void WebTesResultViewer_WindowClosed(object sender, WebTestResultViewerExt.WindowClosedEventArgs e)
    {
        if (m_controls.ContainsKey(e.WebTestResultViewer.TestResultId))
        {
            m_controls.Remove(e.WebTestResultViewer.TestResultId);
        }
    }
    ```

     Visual Studio eklentisi için kod tamamlandıktan sonra WebPerfTestResultsViewerControl projesindeki resultControl güncelleştirme yöntemi eklemeniz gerekir.

## <a name="add-code-to-the-webperftestresultsviewercontrol"></a>WebPerfTestResultsViewerControl'a kod ekleyin

### <a name="to-add-code-to-the-user-control"></a>Kullanıcı denetimine kod eklemek için

1.  İçinde **Çözüm Gezgini**, WebPerfTestResultsViewerControl proje düğümünü sağ tıklatın ve seçin **özellikleri**.

2.  Seçin **uygulama** sekmesine ve ardından **hedef Framework'ü** aşağı açılan listesinden **.NET Framework 4** kapatın **özellikleri**.

     Bu genişletmek için gerekli DLL başvurularını desteklemek için gerekli **Web Performans Test Sonuçları Görüntüleyicisi**.

3.  İçinde **Çözüm Gezgini**, WebPerfTestResultsViewerControl projesindeki **başvuruları** düğümünü seçip alt **Başvuru Ekle**.

4.  İçinde **Başvuru Ekle** iletişim kutusu, tıklayın **.NET** sekmesi.

5.  Aşağı kaydırın ve select **Microsoft.VisualStudio.QualityTools.WebTestFramework**.

6.  Seçin **Tamam**.

7.  İçinde *UserControl1.cs* dosyasında, aşağıdaki kullanım deyimlerini ekleyin:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting.Rules;
    ```

8.  Çağrılan ve WebTestRequestResult WebPerfTestResultsViewerAddin WebTestResultViewer_SelectedChanged yöntemini'dan geçirilen güncelleştirme yöntemi eklemeniz *Connect.cs* dosya. Güncelleştirme yöntemi, DataGridView öğesini WebTestRequestResult öğesi içinden geçirilen çeşitli özelliklerle doldurur.

    ```csharp
    public void Update(WebTestRequestResult WebTestResults)
            {
                // Clear the DataGridView when a request is selected.
                resultControlDataGridView.Rows.Clear();
                // Populate the DataGridControl with properties from the WebTestResults.
                this.resultControlDataGridView.Rows.Add("Request: " + WebTestResults.Request.Url.ToString());
                this.resultControlDataGridView.Rows.Add("Response: " + WebTestResults.Response.ResponseUri.ToString());
                foreach (RuleResult ruleResult in WebTestResults.ExtractionRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Extraction rule results: " + ruleResult.Message.ToString());
                }
                foreach (RuleResult ruleResult in WebTestResults.ValidationRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Validation rule results: " + ruleResult.Message.ToString());
                }
                foreach (WebTestError webTestError in WebTestResults.Errors)
                {
                    this.resultControlDataGridView.Rows.Add("Error: " + webTestError.ErrorType.ToString() + " " + webTestError.ErrorSubtype.ToString() + " " + webTestError.ExceptionText.ToString());
                }
            }
    ```

## <a name="build-the-webperftestresultsvieweraddin-solution"></a>WebPerfTestResultsViewerAddin çözümünü oluşturun

### <a name="to-build-the-solution"></a>Çözümü derlemek için

-   Üzerinde **derleme** menüsünde **Çözümü Derle**.

## <a name="register-the-webperftestresultsvieweraddin-add-in"></a>WebPerfTestResultsViewerAddin Eklentisini Kaydet

### <a name="to-register-the-add-in-using-the-add-in-manager"></a>Eklenti Yöneticisi'ni kullanarak eklentiyi kaydetmek için

1.  Üzerinde **Araçları** menüsünde **Eklenti Yöneticisi**.

2.  **Eklenti Yöneticisi** iletişim kutusu görüntülenir.

3.  İçinde WebPerfTestResultsViewerAddin eklentisi onay kutusunu seçin **kullanılabilir eklentiler** sütun ve clear altındaki onay kutularını **başlangıç** ve **komut satırı**sütunları.

4.  Seçin **Tamam**.

## <a name="run-the-web-performance-test-using-the-build-the-webperftestresultsvieweraddin-add-in"></a>WebPerfTestResultsViewerAddin eklentisi yapıyı kullanarak web performans testini çalıştırma

### <a name="to-run-the-new-vs-add-in-for-the-web-test-results-viewer"></a>Web Testi Sonuçları Görüntüleyicisi için yeni VS eklentiyi çalıştırmak için

1.  Web performans testinizi çalıştırın ve görüntülenen Örnek başlıklı WebPerfTestResultsViewerAddin eklentisi yeni sekmesini göreceksiniz **Web Performans Testi Sonuçları Görüntüleyicisi**.

2.  DataGridView üzerinde sunulan özellikleri görüntülemek için sekmeyi seçin.

## <a name="net-framework-security"></a>.NET Framework Güvenliği

Kötü niyetli eklentilerin otomatik olarak etkinleşmesini engelleyerek güvenliği geliştirmek için Visual Studio ayarları sunar bir **Araçlar Seçenekler** sayfası **/makro güvenliği**.

Ayrıca, bu seçenekler sayfası, Visual Studio arar klasörleri belirtmenizi sağlar *. Eklenti* kayıt dosyaları. Bu, konumları sınırlandırmanıza olanak tanıyarak güvenliği artırır burada *. Eklenti* kayıt dosyaları okuyabilir. Bu kötü amaçlı *. Eklenti* istemeden kullanılmasını dosyaları.

 **Eklenti güvenlik ayarları**

 Seçenekler sayfası için ayarlar güvenlik şu şekildedir Eklentisi:

-   **Yüklenecek eklenti bileşenlerine izin ver.** Varsayılan olarak seçilidir. Bu onay kutusu seçildiğinde, eklentileri Visual Studio yüklemesine izin verilir. Seçili değilse, eklentileri Visual Studio içerisine yüklenmeleri yasaktır.

-   **Bir URL'den yüklenecek eklenti bileşenlerine izin ver.** Varsayılan olarak seçili değildir. Bu onay kutusu seçildiğinde, eklentiler dış Web sitelerinden yüklenebilir. Seçili değilse, uzak eklentilerin Visual Studio içerisine yüklenmeleri yasaktır. Ardından herhangi bir nedenle bir eklenti yüklenemiyor, Web'den yüklenemez. Bu ayar yalnızca yüklenmesini denetler eklenti DLL'in. *. Eklenti* kayıt dosyalarının yerel sistemde her zaman bulunmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.UserControl>
- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.DataGrid>
- [Özel kod ve yük testleri için eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)