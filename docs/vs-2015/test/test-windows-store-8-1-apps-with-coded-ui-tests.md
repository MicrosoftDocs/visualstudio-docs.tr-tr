---
title: Kodlanmış UI testleriyle Windows UWP ve 8.1 Store uygulamaları test | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c8d9c15e-ce3c-401a-86ec-c5c124a239d8
caps.latest.revision: 26
ms.author: gewarren
manager: douge
ms.openlocfilehash: 70973305764319ecb8ebf902945c92eb4723af7a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934307"
---
# <a name="test-windows-uwp-and-81-store-apps-with-coded-ui-tests"></a>Kodlanmış UI testleriyle Windows UWP ve 8.1 Store uygulamaları test etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, UWP uygulamaları ve XAML tabanlı Store 8.1 uygulamaları için kullanıcı Arabirimi testleri oluşturmak için kullanın.
  
## <a name="create-a-simple-windows-store-app"></a>Basit bir Windows Store uygulaması oluşturun  
  
1.  XAML tabanlı Windows Store uygulaması için kodlanmış UI testlerini çalıştırmak istiyorsanız, şunları yapmalısınız [her denetimi tanımlayan benzersiz Otomasyon özelliği ayarlama](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md).  
  
     Üzerinde **Araçları** menüsünde **seçenekleri** seçip **metin düzenleyici**, ardından **XAML**ve son olarak **çeşitli** .  
  
     Otomatik olarak ad oluşumda etkileşimli öğeleri için onay kutusunu seçin.  
  
     ![XAML çeşitli seçenekleri](../test/media/cuit-windowsstoreapp-b.png "CUIT_WindowsStoreApp_B")  
  
2.  Boş bir XAML tabanlı Visual C# veya Visual Basic şablonu kullanarak Windows Store uygulaması için yeni bir proje oluşturun.  
  
     ![Boş bir Windows Store uygulaması oluşturma &#40;XAML&#41;](../test/media/cuit-windowsstoreapp-newproject-blankstoreapp.png "CUIT_WindowsStoreApp_NewProject_BlankStoreApp")  
  
3.  Solution Explorer'da mainpage.XAML dosyasını açın. Araç kutusundan tasarım yüzeyine bir düğme denetimi ve bir metin kutusu denetimi sürükleyin.  
  
     ![Windows Store uygulaması tasarım](../test/media/cuit-windowsstoreapp-design.png "CUIT_WindowsStoreApp_Design")  
  
4.  Düğme denetimini çift tıklayın ve aşağıdaki kodu ekleyin:  
  
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
  
5.  Windows Store uygulamanızı çalıştırmak için F5 tuşuna basın.  
  
## <a name="create-and-run-a-coded-ui-test-for-the-windows-store-app"></a>Oluşturma ve Windows Store uygulaması için kodlanmış UI testi çalıştırma  

[Evrensel Windows Platformu (UWP) uygulamaları için kodlanmış UI testleri nasıl oluşturulur?](#uwpapps)
  
1. Windows Store uygulaması için yeni kodlanmış UI test projesi oluşturun.  
  
    ![Yeni kodlanmış UI tet projesi &#40;Windows Store Apps&#41;](../test/media/cuit-windowsstore-newproject.png "CUIT_WindowsStore_NewProject")  
  
2. İnce artı aracını kullanarak UI eşlemini düzenlemek için seçin.  
  
    ![Seçin UI haritasını Düzenle veya onaylama işlemleri Ekle](../test/media/cuit-windowsstoreapp-createproject-gencodedialog.png "CUIT_WindowsStoreApp_CreateProject_GenCodeDialog")  
  
3. Kodlanmış UI Test Oluşturucusu'nda ince artı aracını uygulama kutucuğunu seçin, sağ tıklatın **Automationıd** ve **değeri Panoya Kopyala**. Panodaki değer daha sonra eylem yazmada test etmek üzere uygulamayı başlatmak için kullanılır.  
  
    ![Automationıd Panoya Kopyala](../test/media/cuit-windows-store-tileautomationid.png "CUIT_Windows_Store_TileAutomationID")  
  
4. Çalışan Windows Store uygulamasında düğme ve metin kutusu denetimini seçmek için artı işareti aracını kullanın. Her denetimi ekledikten sonra seçin **denetim UI kontrol Haritası'na ekleme** kodlanmış UI Test Oluşturucusu araç çubuğu düğmesi.  
  
    ![UI haritasına denetim Ekle](../test/media/cuit-windowsstoreapp-uimap.png "CUIT_WindowsStoreApp_UIMap")  
  
5. Seçin **kod üret** kodlanmış UI Test Oluşturucusu araç çubuğunda düğmesine ve ardından **Oluştur** UI kontrol haritasında değişiklikler için kod oluşturmak için.  
  
    ![UI haritasında kod üretmek](../test/media/cuit-windowsstoreapp-generate.png "CUIT_WindowsStoreApp_Generate")  
  
6. Metin kutusunda bir değer ayarlamak için bu düğmeyi seçin.  
  
    ![TextBox değeri ayarlamak için düğme denetimi](../test/media/cuit-windowsstoreapp-clickbutton.png "CUIT_WindowsStoreApp_ClickButton")  
  
7. Textbox denetimi seçin ve ardından seçmek için artı işareti aracını kullanın **metin** özelliği.  
  
    ![Metin özelliği seçin](../test/media/cuit-windowsstoreapp-selecttextproperty.png "CUIT_WindowsStoreApp_SelectTextProperty")  
  
8. Onaylama Ekle. Bu testte değerin doğru olduğunu doğrulamak için kullanılır.  
  
    ![Çapraz ile testbox seçin&#45;artı ve onaylama Ekle](../test/media/cuit-windowsstoreapp-textbox-addassertion.png "CUIT_WindowsStoreApp_Textbox_AddAssertion")  
  
9. Ekleyin ve onay için kod oluşturur.  
  
     ![Textbox onaylama için kod oluşturmak](../test/media/cuit-windowsstoreapp-textbox-generate-assertion.png "CUIT_WindowsStoreApp_Textbox_Generate_Assertion")  
  
10. **Visual C#**  
  
     Çözüm Gezgini'nde onay yöntemi ve denetimler için eklenen kodu görüntülemek için UIMap.Designer.cs dosyasını açın.  
  
     **Visual Basic**  
  
     Solution Explorer'da Codeduıtest1.vb dosyasını açın ve sonra Codeduıtestmethod1() test yöntemi kodunda otomatik olarak eklenen onay yöntemi çağrısını sağ `Me.UIMap.AssertMethod1()` ve **tanıma**. Bu görünümü onay yöntemi ve denetimler için eklenen kodu görüntüleyebilmeniz için UIMap.Designer.vb dosyasını Kod düzenleyicisinde açar.  
  
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
        Assert.AreEqual(this.AssertMethod3ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text);  
    }  
    ```  
  
    ```vb  
    Public Sub AssertMethod1()  
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit  
  
        'Verify that the 'Text' property of 'textBox' text box equals 'button'  
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text)  
    End Sub  
    ```  
  
     **Denetimler**  
  
    ```csharp  
    #region Properties  
    public XamlButton UIButtonButton  
    {  
        get  
        {  
            if ((this.mUIButtonButton == null))  
            {  
                this.mUIButtonButton = new XamlButton(this);  
                #region Search Criteria  
                this.mUIButtonButton.SearchProperties[XamlButton.PropertyNames.AutomationId] = "button";  
                this.mUIButtonButton.WindowTitles.Add("App1");  
                #endregion  
            }  
            return this.mUIButtonButton;  
        }  
    }  
  
    public XamlEdit UITextBoxEdit  
    {  
        get  
        {  
            if ((this.mUITextBoxEdit == null))  
            {  
                this.mUITextBoxEdit = new XamlEdit(this);  
                #region Search Criteria  
                this.mUITextBoxEdit.SearchProperties[XamlEdit.PropertyNames.AutomationId] = "textBox";  
                this.mUITextBoxEdit.WindowTitles.Add("App1");  
                #endregion  
            }  
            return this.mUITextBoxEdit;  
        }  
    }  
    #endregion  
  
    #region Fields  
    private XamlButton mUIButtonButton;  
  
    private XamlEdit mUITextBoxEdit;  
    #endregion  
    ```  
  
    ```vb  
    #Region "Properties"  
    Public ReadOnly Property UIButtonButton() As XamlButton  
        Get  
            If (Me.mUIButtonButton Is Nothing) Then  
                Me.mUIButtonButton = New XamlButton(Me)  
                Me.mUIButtonButton.SearchProperties(XamlButton.PropertyNames.AutomationId) = "button"  
                Me.mUIButtonButton.WindowTitles.Add("App2")  
            End If  
            Return Me.mUIButtonButton  
        End Get  
    End Property  
  
    Public ReadOnly Property UITextBoxEdit() As XamlEdit  
        Get  
            If (Me.mUITextBoxEdit Is Nothing) Then  
                Me.mUITextBoxEdit = New XamlEdit(Me)  
                Me.mUITextBoxEdit.SearchProperties(XamlEdit.PropertyNames.AutomationId) = "textBox"  
                Me.mUITextBoxEdit.WindowTitles.Add("App2")  
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
  
11. Çözüm Gezgini'nde Codeduıtest1.cs veya Codeduıtest1.vb dosyasını açın. Kodu artık CodedUTTestMethod1 yöntemine Uımap'a eklenen denetimleri kullanarak çalıştırılması gereken eylemler içir ekleyebilirsiniz:  
  
    1. Daha önce panoya kopyaladığınız Otomasyon kimliği özelliğini kullanarak Windows Store uygulamasını Başlat:  
  
       ```csharp  
       XamlWindow.Launch("8ebca7c4-effe-4c86-9998-068daccee452_cyrqexqw8cc7c!App")  
       ```  
  
       ```vb  
       XamlWindow myAppWindow = XamlWindow.Launch("7254db3e-20a7-424e-8e05-7c4dabf4f28d_cyrqexqw8cc7c!App");  
       ```  
  
    2. Düğme denetimine dokunma hareketi ekleyin:  
  
       ```csharp  
       Gesture.Tap(this.UIMap.UIApp1Window. UIButtonButton);  
       ```  
  
       ```vb  
       Gesture.Tap(Me.UIMap.UIApp2Window. UIButtonButton)  
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
        XamlWindow myAppWindow = XamlWindow.Launch("7254db3e-20a7-424e-8e05-7c4dabf4f28d_cyrqexqw8cc7c!App");  
  
        // Tap the button.  
        Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);  
  
        this.UIMap.AssertMethod1();  
    }  
    ```  
  
    ```vb  
    <CodedUITest(CodedUITestType.WindowsStore)>  
    Public Class CodedUITest1  
  
        <TestMethod()>  
        Public Sub CodedUITestMethod1()  
            '              
            ' To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
            '  
  
            ' Launch the app.  
            XamlWindow.Launch("8ebca7c4-effe-4c86-9998-068daccee452_cyrqexqw8cc7c!App")  
  
            '// Tap the button.  
            Gesture.Tap(Me.UIMap.UIApp2Window.UIButtonButton)  
  
            Me.UIMap.AssertMethod1()  
        End Sub  
    ```  
  
12. Testinizi oluşturun ve sonra test Gezginini kullanarak testi çalıştırın.  
  
     ![Çalıştırma kodlanmış UI testi Test Gezgini'nden](../test/media/cuit-windowsstoreapp-runtest.png "CUIT_WindowsStoreApp_RunTest")  
  
     Windows Store uygulaması başlar, eyleme düğme tamamlandı dokunun ve metin kutusunun metin özelliği doldurulur ve onay yöntemi kullanılarak doğrulandı.  
  
     ![Çalışan Kodlanmış UI testi](../test/media/cuit-windowsstoreapp-running.png "CUIT_WindowsStoreApp_Running")  
  
     Test tamamlandıktan sonra test Gezgini geçilen testleri görüntüler.  
  
     ![Test Gezgini'nde testi görüntüler geçirilen](../test/media/cuit-windowsstorapp-passedtest.png "CUIT_WindowsStorApp_PassedTest")  
  
## <a name="q--a"></a>Soru - Yanıt  
  
-   **Kodlanmış UI testi iletişim kutusu için kod üret içinde kodlanmış UI testimi kaydetme seçeneğini neden görmüyorum?**  
  
     **A**: kaydedilecek seçenek Windows Store uygulamaları için desteklenmez.  
  
-   **Kodlanmış UI testi için Windows Store uygulamalarım üzerinde WinJS oluşturabilirim miyim?**  
  
     **A**: Hayır, yalnızca XAML tabanlı uygulamalar desteklenir.  
  
-   **Kodlanmış UI testleri için Windows 8.1 veya Windows 10 çalıştırmayan bir sistemde Windows Store uygulamalarım oluşturabilirim miyim?**  
  
     **A**: Hayır, kodlanmış UI Test projesi şablonlar yalnızca Windows 8.1 ve Windows 10'da kullanılabilir. Otomasyon için evrensel Windows Platformu (UWP) uygulamaları oluşturmak için Windows 10 gerekir.  

<a name="uwpapps"></a>
- **S: Evrensel Windows Platformu (UWP) uygulamaları için kodlanmış UI testleri nasıl oluşturulur?**  
  
   **A**: Burada test UWP uygulamanızın platforma bağlı olarak, aşağıdaki yöntemlerden biriyle kodlanmış UI test projesi oluşturun:  
  
  - Yerel makine üzerinde çalışan UWP uygulaması bir Store uygulaması olarak çalışır. Bu test için kullanmanız gerekir **kodlanmış UI Test projesi (Windows)** şablonu. Yeni bir proje oluşturduğunuzda, bu şablonu bulmak için Git **Windows**, **Evrensel** düğümü. Veya Git **Windows**, **Windows 8**, **Windows** düğümü.  
  
  - Mobil cihaz veya öykünücü üzerinde çalışan bir UWP uygulaması, bir telefon uygulaması çalışır. Bu test için kullanmanız gerekir **kodlanmış UI Test projesi (Windows Phone)** şablonu. Yeni bir proje oluşturduğunuzda, bu şablonu bulmak için Git **Windows**, **Evrensel** düğümü. Veya Git **Windows**, **Windows 8**, **Windows Phone** düğümü.  
  
    Projeyi oluşturduktan sonra bir test yazma önceki ile aynı kalır.  
  
- **UIMap.Designer dosyasındaki kodu neden değiştiremiyorum?**  
  
   **A**: UIMap - Kodlanmış UI Test Oluşturucusu kullanarak kodu üretmek her zaman UIMapDesigner.cs dosyasında yaptığınız herhangi bir kod değişikliği üzerine yazılır. Kayıtlı bir yöntemi değiştirmeniz gerekiyorsa, yöntemi UIMap.cs dosyasına kopyalayıp yeniden adlandırmanız gerekir. UIMap.cs dosyası, UIMapDesigner.cs dosyasındaki yöntemleri ve özellikleri geçersiz kılmak için kullanılabilir. Kodlanmış UITest.cs dosyasındaki orijinal yönteme başvuruyu kaldırıp yeniden adlandırılan yöntem adıyla değiştirmelisiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)   
 [Test yapma amacıyla Windows Mağazası Denetimleri için Benzersiz Otomasyon Özelliği ayarlama](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)



