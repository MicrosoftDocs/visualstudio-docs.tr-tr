---
title: Kodlanmış UI testleriyle Windows UWP ve 8.1 Phone uygulamalarını test | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b866776-f2d5-4823-8d15-919f889db26f
caps.latest.revision: 31
ms.author: gewarren
manager: douge
ms.openlocfilehash: 808482fdd7599adb270fe7634d61d4b88acb0d80
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890152"
---
# <a name="test-windows-uwp-and-81-phone-apps-with-coded-ui-tests"></a>Kodlanmış UI Testleriyle Windows UWP ve 8.1 Phone Uygulamalarını Test Etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu kılavuz, mobil cihaz veya öykünücü üzerinde çalışan UWP uygulamaları ve XAML tabanlı Phone 8.1 uygulamaları için kullanıcı Arabirimi testleri oluşturmak için kullanın.   
  
## <a name="create-a-simple-windows-phone-app"></a>Basit bir Windows Phone uygulaması oluşturun  
  
1.  Visual C# veya Visual Basic şablonu kullanarak boş bir Windows Phone uygulaması için yeni bir proje oluşturun.  
  
     ![Yeni bir Windows Phone uygulaması oluşturma](../test/media/cuit-phone-app-newproject.png "CUIT_Phone_App_NewProject")  
  
2.  Solution Explorer'da mainpage.XAML dosyasını açın. Araç kutusundan tasarım yüzeyine bir düğme denetimi ve bir metin kutusu denetimi sürükleyin.  
  
     ![MainPage.xaml için metinse ekleme](../test/media/cuit-phone-app-addcontrols.png "CUIT_Phone_App_AddControls")  
  
3.  Özellikler penceresinde düğme denetimini adlandırın.  
  
     ![Düğme denetimini ad](../test/media/cuit-phone-namebutton.png "CUIT_Phone_NameButton")  
  
4.  Ad metin kutusu denetimi.  
  
     ![Textbox denetimi adı](../test/media/cuit-phone-nametesxtbox.png "CUIT_Phone_NameTesxtBox")  
  
5.  Tasarımcı yüzeyinde düğme denetimini çift tıklayın ve aşağıdaki kodu ekleyin:  
  
    ```csharp  
    private void button_Click_1(object sender, RoutedEventArgs e)  
    {  
        this.textBox.Text = this.button.Name;  
    }  
  
    ```  
  
    ```vb  
    Public NotInheritable Class MainPage  
        Inherits Page  
  
        Private Sub button_Click(sender As Object, e As RoutedEventArgs) Handles Button.Click  
            Me.textBox.Text = Me.button.Name  
        End Sub  
    End Class  
    ```  
  
6.  Windows Phone uygulamanızı öykünücüde çalıştırma ve çalıştığını doğrulamak için F5 tuşuna basın.  
  
     ![Windows Phone çalıştıran uygulama](../test/media/cuit-phone-runapp.png "CUIt_Phone_RunApp")  
  
7.  Öykünücü çıkın.  
  
## <a name="deploy-the-windows-phone-app"></a>Windows Phone dağıtma uygulama  
  
1.  Kodlanmış UI testi uygulamanın denetimleri eşleyebilmeniz için önce uygulamayı dağıtmak zorunda.  
  
     ![Windows Phone dağıtma uygulama](../test/media/cuit-phone-deploy.png "CUIT_Phone_Deploy")  
  
     Öykünücü başlatılır. Uygulamayı test etmek için kullanıma sunulmuştur.  
  
     ![Öykünücü üzerinde dağıtılan uygulama](../test/media/cuit-phone-deployed.png "CUIT_Phone_Deployed")  
  
     Kodlanmış UI testleri oluşturma sırasında çalışan öykünücüyü tutun.  
  
## <a name="create-a-coded-ui-test-for-the-windows-phone-app"></a>Windows Phone uygulaması için kodlanmış UI testi oluşturma  

[Evrensel Windows Platformu (UWP) uygulamaları için kodlanmış UI testleri nasıl oluşturulur?](#uwpapps)
  
1. Windows Phone uygulaması ile çözüme yeni bir kodlanmış UI test projesi ekleyin.  
  
    ![Windows Phone için yeni kodlanmış UI testi oluşturma](../test/media/cuit-phone-newproject.png "CUIT_Phone_NewProject")  
  
2. İnce artı aracını kullanarak UI eşlemini düzenlemek için seçin.  
  
    ![Kodlanmış UI çapraz kullanarak test oluşturma&#45;artı aracını. ](../test/media/cuit-phone-howgencodedialog.png "CUIT_Phone_HowGenCodeDialog")  
  
3. Uygulamayı seçmek için artı işareti aracını kullanın ve ardından uygulamanın değerini kopyalayın **Automationıd** daha sonra test uygulamasını başlatmak için kullanılacak özelliği.  
  
    ![Uygulamanın Automationıd değerini kopyalayın](../test/media/cuit-phone-getautomationid.png "CUIT_Phone_GetAutomationId")  
  
4. Öykünücüsünde uygulamayı başlatın ve düğme denetimini seçmek için artı işareti aracını kullanın. Düğme denetimini UI kontrol haritasına eklersiniz.  
  
    ![Çapraz kullanın&#45;eşleme denetimleri için artı aracını](../test/media/cuit-phone-mapbuttoncontrol.png "CUIT_Phone_MapButtonControl")  
  
5. Textbox denetimi UI kontrol Haritası'na eklemek için önceki adımı yineleyin.  
  
    ![Çapraz kullanın&#45;artı aracını ve harita textbox denetimi](../test/media/cuit-phone-maptextboxcontrol.png "CUIT_Phone_MapTextBoxControl")  
  
6. UI kontrol haritasında değişiklikler için kod oluşturmak için kod oluşturur.  
  
    ![Kod oluşturma Oluşturucusu'ndan](../test/media/cuit-phone-generatecode.png "CUIT_Phone_GenerateCode")  
  
7. Textbox denetimi seçin ve ardından seçmek için artı işareti aracını kullanın **metin** özelliği.  
  
    ![Metin özelliği seçin](../test/media/cuit-phone-textproperty.png "CUIT_Phone_TextProperty")  
  
8. Onaylama Ekle. Bu testte değerin doğru olduğunu doğrulamak için kullanılır.  
  
    ![Test için onaylama Ekle](../test/media/cuit-phone-addassertion.png "CUIT_Phone_AddAssertion")  
  
9. Ekleyin ve onay yöntemi için kod oluşturur.  
  
     ![Onay için kod oluşturmak](../test/media/cuit-phone-generatecodeassertion.png "CUIT_Phone_GenerateCodeAssertion")  
  
10. **Visual C#**  
  
     Çözüm Gezgini'nde UIMap.Designer.cs dosyasını yeni onay yöntemi ve denetimler için eklenen kodu görüntüleyin açın.  
  
     **Visual Basic**  
  
     Solution Explorer'da, Codeduıtest1.vb dosyasını açın. Codeduıtestmethod1() test yöntemi kodu, otomatik olarak eklenen onay yöntemi çağrısını sağ `Me.UIMap.AssertMethod1()` ve **tanıma**. Bu onay yöntemi ve denetimler için eklenen kodu görüntüleyebilmeniz için UIMap.Designer.vb dosyasını Kod düzenleyicisinde açar.  
  
    > [!WARNING]
    >  UIMap.Designer.cs veya UIMap.Designer.vb dosyasını doğrudan değiştirmeyin. Bunu yaparsanız, dosyadaki değişikliklerin testin üretildiği her seferinde üzerine yazılır.  
  
     **Assert yöntemi**  
  
    ```csharp  
    public void AssertMethod1()  
    {  
        #region Variable Declarations  
        XamlEdit uITextBoxEdit = this.UIApp1Window.UITextBoxEdit;  
        #endregion  
  
        // Verify that the 'Text' property of 'textBox' text box equals 'button'  
        Assert.AreEqual(this.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text);  
    }  
    ```  
  
    ```vb  
    Public Sub AssertMethod1()  
        Dim uITextBoxEdit As XamlEdit = Me.UIApp1Window.UITextBoxEdit  
  
        'Verify that the 'Text' property of 'textBox' text box equals 'button'  
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text)  
    End Sub  
    ```  
  
     **Denetimler**  
  
    ```csharp  
    #region Properties  
    public virtual AssertMethod1ExpectedValues AssertMethod1ExpectedValues  
    {  
        get  
        {  
            if ((this.mAssertMethod1ExpectedValues == null))  
            {  
                this.mAssertMethod1ExpectedValues = new AssertMethod1ExpectedValues();  
            }  
            return this.mAssertMethod1ExpectedValues;  
        }  
    }  
  
    public UIApp1Window UIApp1Window  
    {  
        get  
        {  
            if ((this.mUIApp1Window == null))  
            {  
                this.mUIApp1Window = new UIApp1Window();  
            }  
            return this.mUIApp1Window;  
        }  
    }  
    #endregion  
  
    #region Fields  
    private AssertMethod1ExpectedValues mAssertMethod1ExpectedValues;  
  
    private UIApp1Window mUIApp1Window;  
    #endregion  
    ```  
  
    ```vb  
    #Region "Properties"  
    Public ReadOnly Property UIButtonButton() As XamlButton  
        Get  
            If (Me.mUIButtonButton Is Nothing) Then  
                Me.mUIButtonButton = New XamlButton(Me)  
                Me.mUIButtonButton.SearchProperties(XamlButton.PropertyNames.AutomationId) = "button"  
            End If  
            Return Me.mUIButtonButton  
        End Get  
    End Property  
  
    Public ReadOnly Property UITextBoxEdit() As XamlEdit  
        Get  
            If (Me.mUITextBoxEdit Is Nothing) Then  
                Me.mUITextBoxEdit = New XamlEdit(Me)  
                Me.mUITextBoxEdit.SearchProperties(XamlEdit.PropertyNames.AutomationId) = "textBox"  
            End If  
            Return Me.mUITextBoxEdit  
        End Get  
    End Property  
    #End Region  
  
    #Region "Fields"  
    Private mUIButtonButton As XamlButton  
  
    Private mUITextBoxEdit As XamlEdit  
    #End Region  
    ```  
  
11. Çözüm Gezgini'nde Codeduıtest1.cs veya Codeduıtest1.vb dosyasını açın. Şimdi, test çalıştırmak için gerekli eylemleri CodedUTTestMethod1 yöntemine kod ekleyebilirsiniz. Kod eklemek için Uımap'a eklenen denetimleri kullanın:  
  
    1. Daha önce panoya kopyaladığınız Otomasyon kimliği özelliğini kullanarak Windows Phone uygulamasını Başlat:  
  
       ```csharp  
       XamlWindow myAppWindow = XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");  
       ```  
  
       ```vb  
       XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");  
       ```  
  
    2. Düğme denetimine dokunma hareketi ekleyin:  
  
       ```csharp  
       Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);  
       ```  
  
       ```vb  
       Gesture.Tap(Me.UIMap.UIApp1Window.UIButtonButton)  
       ```  
  
    3. Otomatik olarak oluşturulan izin yöntemine çağrı uygulama başlatıldıktan sonra geldiğini doğrulamak ve düğme üzerinde hareket dokunun:  
  
       ```csharp  
       this.UIMap.AssertMethod1();  
       ```  
  
       ```vb  
       Me.UIMap.AssertMethod1()  
       ```  
  
       Kod ekledikten sonra Codeduıtestmethod1 test yöntemi şu şekilde görünmelidir:  
  
    ```csharp  
    [TestMethod]  
    public void CodedUITestMethod1()  
    {  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
  
        // Launch the app.  
        XamlWindow myAppWindow = XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");  
  
        // Tap the button.  
        Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);  
  
        this.UIMap.AssertMethod1();  
    }  
    ```  
  
    ```vb  
    <CodedUITest>  
    Public Class CodedUITest1  
  
        <TestMethod()>  
        Public Sub CodedUITestMethod1()  
            '              
            ' To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
            '  
            ' Launch the app.  
            XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App")  
  
            '// Tap the button.  
            Gesture.Tap(Me.UIMap.UIApp1Window.UIButtonButton)  
  
            Me.UIMap.AssertMethod1()  
        End Sub  
    ```  
  
## <a name="run-the-coded-ui-test"></a>Kodlanmış UI testi Çalıştır  
  
1.  Testinizi oluşturun ve sonra test Gezginini kullanarak testi çalıştırın.  
  
     ![Derleme ve Test Gezgini'ni kullanarak test çalıştırma](../test/media/cuit-phone-runtestexplorer.png "CUIT_Phone_RunTestExplorer")  
  
     Windows Phone uygulaması başlar, eyleme düğme tamamlandı dokunun ve metin kutusunun metin özelliği doldurulur ve onay yöntemi kullanılarak doğrulandı.  
  
     ![Çalışan Windows Phone test](../test/media/cuit-phone-runtestexplorerrunning.png "CUIT_Phone_RunTestExplorerRunning")  
  
     Test tamamlandıktan sonra test Gezgini geçilen testleri onaylar.  
  
     ![Test Explorer sonuçları](../test/media/cuit-phone-runtestexplorerresults.png "CUIT_Phone_RunTestExplorerResults")  
  
##  <a name="TestingPhoneAppsCodedUI_DataDriven"></a> Kullanım veri tabanlı kodlanmış UI testleri Windows Phone uygulamalarını  
 Farklı koşulları test etmeye yönelik bir kodlanmış UI testi birden çok kez farklı veri kümelerini çalıştırılabilir.  
  
 Windows Phone için verilerle çalışan kodlanmış UI testleri bir test yönteminde DataRow özniteliği kullanılarak tanımlanır. Aşağıdaki örnek, x ve y ilk yineleme ve -1 -2 için ikinci bir test yinelemesini için 1 ve 2 değerlerini kullanın.  
  
```  
[DataRow(1, 2, DisplayName = "Add positive numbers")]  
[DataRow(-1, -2, DisplayName = "Add negative numbers")]  
[TestMethod]  
public void DataDrivingDemo_MyTestMethod(int x, int y)  
  
```  
  
## <a name="q--a"></a>Soru - Yanıt  
  
### <a name="q-do-i-have-to-deploy-the-windows-phone-app-in-the-emulator-in-order-to-map-ui-controls"></a>UI denetimine eşlemek için Windows Phone öykünücüsünde uygulamayı dağıtmak zorunda s:?  
 **A**: Evet, kodlanmış UI test Oluşturucusu bir öykünücü çalışıyor olmalıdır ve uygulama için dağıtılabilir gerektirir. Aksi takdirde, hiçbir çalışan öykünücüsü bulunamadı hata mesajını durum oluşturur.  
  
###  <a name="TestingPhoneAppsCodedUI_EmulatorDevice"></a> Testleri yalnızca öykünücü üzerinde yürütülen miyim ya da fiziksel bir cihaz kullanabilir miyim?  
 **A**: her iki seçenek desteklenir. Test yürütmesi için hedef öykünücü türünü değiştirme veya cihaz cihaz araç çubuğunda seçerek seçilir. Cihaz seçiliyse, telefon mavi bir cihaz makinenin USB bağlantı noktalarından birine bağlanması gerekir.  
  
 ![Physcial cihaz veya öykünücü sürümü seçin](../test/media/cuit-phone-testtarget.png "CUIT_Phone_TestTarget")  
  
### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>Kodlanmış UI testi iletişim kutusu için kod üret içinde kodlanmış UI testimi kaydetme seçeneğini neden görmüyorum?  
 **A**: kaydedilecek seçenek Windows Phone uygulamaları için desteklenmez.  
  
### <a name="q-can-i-create-a-coded-ui-test-for-my-windows-phone-apps-based-on-winjs-silverlight-or-html5"></a>Kodlanmış UI testi için Windows Phone uygulamalarım WinJS, Silverlight veya HTML5 tabanlı oluşturabilirim miyim?  
 **A**: Hayır, yalnızca XAML tabanlı uygulamalar desteklenir.  
  
### <a name="q-can-i-create-coded-ui-tests-for-my-windows-phone-apps-on-a-system-that-is-not-running-windows-81-or-windows-10"></a>Kodlanmış UI testleri, Windows 8.1 veya Windows 10 çalıştırmayan bir sistemde Windows Phone uygulamalarım için oluşturabilirim miyim?  
 **A**: Hayır, kodlanmış UI Test projesi şablonlar yalnızca Windows 8.1 ve Windows 10'da kullanılabilir. Otomasyon için evrensel Windows Platformu (UWP) uygulamaları oluşturmak için Windows 10 gerekir.  

<a name="uwpapps"></a>  
### <a name="q-how-do-i-create-coded-ui-tests-for-universal-windows-platform-uwp-apps"></a>S: Evrensel Windows Platformu (UWP) uygulamaları için kodlanmış UI testleri nasıl oluşturulur?  
 **A**: Burada test UWP uygulamanızın platforma bağlı olarak, aşağıdaki yöntemlerden biriyle kodlanmış UI test projesi oluşturun:  
  
- Yerel makine üzerinde çalışan UWP uygulaması bir Store uygulaması olarak çalışır. Bu test için kullanmanız gerekir **kodlanmış UI Test projesi (Windows)** şablonu. Yeni bir proje oluşturduğunuzda, bu şablonu bulmak için Git **Windows**, **Evrensel** düğümü. Veya Git **Windows**, **Windows 8**, **Windows** düğümü.  
  
- Mobil cihaz veya öykünücü üzerinde çalışan bir UWP uygulaması, bir telefon uygulaması çalışır. Bu test için kullanmanız gerekir **kodlanmış UI Test projesi (Windows Phone)** şablonu. Yeni bir proje oluşturduğunuzda, bu şablonu bulmak için Git **Windows**, **Evrensel** düğümü. Veya Git **Windows**, **Windows 8**, **Windows Phone** düğümü.  
  
  Projeyi oluşturduktan sonra bir test yazma önceki ile aynı kalır.  
  
### <a name="q-can-i-select-controls-that-are-outside-the-emulator"></a>Öykünücü dışında olan denetimler seçtiğim miyim?  
 **A**: Hayır, oluşturucu bunları algılamaz.  
  
### <a name="q-can-i-use-the-coded-ui-test-builder-to-map-controls-using-a-physical-phone-device"></a>S: kodlanmış UI test Oluşturucusu'nu fiziksel phone cihazı kullanarak denetimleri eşlemek için kullanabilir miyim?  
 **A**: uygulamanızı öykünücüde dağıttıysanız Hayır, oluşturucu yalnızca kullanıcı Arabirimi öğeleri eşleyebilirsiniz.  
  
### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>UIMap.Designer dosyasındaki kodu neden değiştiremiyorum?  
 **A**: UIMap - Kodlanmış UI Test Oluşturucusu kullanarak kodu üretmek her zaman UIMapDesigner.cs dosyasında yaptığınız herhangi bir kod değişikliği üzerine yazılır. Kayıtlı bir yöntemi değiştirmeniz gerekiyorsa, yöntemi UIMap.cs dosyasına kopyalayıp yeniden adlandırmanız gerekir. UIMap.cs dosyası, UIMapDesigner.cs dosyasındaki yöntemleri ve özellikleri geçersiz kılmak için kullanılabilir. Kodlanmış UITest.cs dosyasındaki orijinal yönteme başvuruyu kaldırıp yeniden adlandırılan yöntem adıyla değiştirmelisiniz.  
  
### <a name="q-can-i-run-a-coded-ui-test-on-my-windows-phone-app-from-the-command-line"></a>Kodlanmış UI testi Windows Phone uygulamamı komut satırından çalıştırabilir miyim?  
 **A**: Evet, siz runsettings dosyası test yürütmesi için hedef cihazla belirtmek için kullanın. Örneğin:  
  
 **vstest.Console.exe "pathToYourCodedUITestDll" /settings:devicetarget.runsettings**  
  
 Örnek runsettings dosyası:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<RunSettings>  
<MSPhoneTest>  
<!--to specify test execution on device, use a TargetDevice option as follows-->  
<TargetDevice>Device</TargetDevice>  
<!--to specify an emulator instead, use a TargetDevice option like below-->  
<!--<TargetDevice>Emulator 8.1 WVGA 4 inch 512MB</TargetDevice>-->  
</MSPhoneTest>  
</RunSettings>  
```  
  
### <a name="q-what-are-the-differences-between-coded-ui-tests-for-xaml-based-windows-store-apps-and-windows-phone-apps"></a>S: XAML tabanlı Windows Store uygulamaları için kodlanmış UI testleri ve Windows Phone uygulamaları arasındaki farklar nelerdir?  
 **A**: bazı temel farklar şunlardır:  
  
|Özellik|Windows Mağazası uygulamaları|Windows Phone uygulamaları|  
|-------------|------------------------|------------------------|  
|Testleri çalıştırmak için hedef|Yerel veya uzak bilgisayar. Testleri çalıştırmak için otomatikleştirilmiş test çalışmasına kullandığınızda, uzak bilgisayarlara belirtilebilir. Bkz: [Microsoft Test Yöneticisi'nde bir test çalışmasını otomatikleştirme](http://msdn.microsoft.com/library/4e02568b-9cde-47cc-b41c-82726c177e42).|Öykünücü veya cihaz. Bkz, [s: testleri yalnızca öykünücü üzerinde yürütülebilir veya fiziksel bir cihaz ayrıca kullanabilirim?](#TestingPhoneAppsCodedUI_EmulatorDevice) bu konuda.|  
|Komut satırından yürütmek|Ayarlar dosyası hedef belirtmek için gerekli değildir.|Runsettings dosyası hedef belirtmek için gereklidir.|  
|Kabuk denetimleri için özel sınıflar|<xref:Microsoft.VisualStudio.TestTools.UITesting.DirectUIControls.DirectUIControl>|<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl>|  
|WebView denetiminde XAML uygulama|Html * kullanırsanız desteklenen özel HTML öğeleri ile etkileşim kurmak için sınıflar. Bkz. <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>.|Desteklenmez.|  
|MTM'den otomatik testler yürütme|Desteklenen.|Desteklenmez.|  
|Veri tabanlı testler|Bkz: [veri tabanlı testler](../test/creating-a-data-driven-coded-ui-test.md) dış veri kaynakları kullanarak ve veri kaynağı kullanma hakkında bilgi için bir test yönteminde öznitelik.|Verileri, bir test metodunda DataRow özniteliğini kullanarak, belirtilen içindedir. Bkz: [kullanım verilerle çalışan kodlanmış UI testleri Windows Phone uygulamalarını](#TestingPhoneAppsCodedUI_DataDriven) bu konuda.|  
  
## <a name="external-resources"></a>Dış kaynaklar  
 Microsoft Visual Studio uygulama yaşam döngüsü yönetimi blogunda: [XAML tabanlı Windows Phone uygulamalarını test etmek için kodlanmış UI kullanarak](http://blogs.msdn.com/b/visualstudioalm/archive/2014/04/05/using-coded-ui-to-test-xaml-based-windows-phone-apps.aspx?PageIndex=2#comments)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kodunuzu Test Etmek için UI Otomasyonunu Kullanma](../test/use-ui-automation-to-test-your-code.md)



