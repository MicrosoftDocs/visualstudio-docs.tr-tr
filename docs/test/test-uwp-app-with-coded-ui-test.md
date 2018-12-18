---
title: Kodlanmış UI testi ile bir UWP uygulaması test
ms.date: 05/31/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- uwp
ms.openlocfilehash: 3dcbd6065d45bf5350b80d555f335d3b8ec1cec7
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895970"
---
# <a name="create-a-coded-ui-test-to-test-a-uwp-app"></a>Kodlanmış UI testi için test UWP uygulaması oluşturma

Bu makalede, bir evrensel Windows Platformu (UWP) uygulaması için kodlanmış UI testi oluşturma açıklanmaktadır.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-uwp-app-to-test"></a>Test etmek için bir UWP uygulaması oluşturma

İlk adım, testi karşı çalıştırmak için basit bir UWP uygulaması oluşturmaktır.

1. Visual Studio kullanarak yeni bir proje oluşturma **boş uygulama (Evrensel Windows)** Visual C# veya Visual Basic şablonu.

     ![Boş uygulama Evrensel Windows şablonu](../test/media/blank-uwp-app-template.png)

1. İçinde **yeni evrensel Windows platformu projesi** iletişim kutusunda **Tamam** varsayılan platform sürümleri kabul etmek için.

1. Gelen **Çözüm Gezgini**açın *MainPage.xaml*.

   Dosya açılır **XAML Tasarımcısı**.

1. Bir düğme denetimi ve bir metin kutusu denetimi sürükleyin **araç kutusu** tasarım yüzeyine bırakın.

     ![UWP uygulaması tasarlama](../test/media/toolbox-controls.png)

1. Denetimlere adlar verin. Textbox denetimi seçin ve ardından **özellikleri** penceresinde girin **textBox** içinde **adı** alan. Düğme denetimini seçin ve ardından **özellikleri** penceresinde girin **düğmesi** içinde **adı** alan.

1. Düğme denetimini çift tıklayın ve gövdesi için aşağıdaki kodu ekleyin `Button_Click` yöntemi. Bu kod, metin yalnızca metin kutusuna daha sonra oluşturacağımız kodlanmış UI testi ile doğrulamak için bir şey bulunun yalnızca düğme denetimi, adını ayarlar.

   ```csharp
   this.textBox.Text = this.button.Name;
   ```

   ```vb
   Me.textBox.Text = Me.button.Name
   ```

1. Tuşuna **Ctrl**+**F5** uygulamayı çalıştırmak için. Aşağıdaki gibi görmeniz gerekir:

   ![UWP uygulamasında düğme ve metin kutusu](media/uwp-app.png)

## <a name="create-a-coded-ui-test"></a>Kodlanmış UI testi oluşturma

1. Bir test projesi çözüme eklemek için çözüme sağ **Çözüm Gezgini** ve **Ekle** > **yeni proje**.

1. İçinde **yeni proje** iletişim kutusunda, **kodlanmış UI Test projesi (Evrensel Windows)** şablonu. Şablon altında bulabilirsiniz **Windows Evrensel** kategorisi altında **Visual C#** veya **Visual Basic**.

     ![Yeni kodlanmış UI test projesi](../test/media/coded-ui-test-project-uwp-template.png)

   > [!NOTE]
   > Görmüyorsanız **kodlanmış UI Test projesi (Evrensel Windows)** şablon gereken [kodlanmış UI test bileşeni](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

1. İçinde **kodlanmış UI testi için kod üret** iletişim kutusunda **el ile testi düzenlemek**.

     ![Kodlanmış UI testi iletişim kutusu için kod oluşturma](../test/media/manually-edit-the-test.png)

1. UWP uygulamanız zaten çalışmıyorsa başlatın tuşlarına basarak **Ctrl**+**F5**.

1. Açık **kodlanmış UI Test Oluşturucusu** imleci yerleştirerek iletişim `CodedUITestMethod1` yöntemi ve seçerek **Test** > **KodlanmışUItestiiçinkodüret**  >  **Kullanım kodlanmış UI Testi Oluşturucusu**.

1. Denetim UI kontrol Haritası'na ekleyin. Kullanım **kodlanmış UI Test Oluşturucusu** ince artı aracını UWP uygulamasında düğme denetimini seçin. İçinde **onaylama Ekle** iletişim kutusunda genişletin **UI kontrol haritasını** bölmesinde gerekli ve ardından **denetim UI kontrol Haritası'na ekleme**.

     ![UI haritasına denetim Ekle](../test/media/add-control-to-ui-control-map.png)

1. Textbox denetimi UI kontrol Haritası'na eklemek için önceki adımı yineleyin.

1. İçinde **kodlanmış UI Test Oluşturucusu** iletişim kutusunda **kod üret** veya basın **Ctrl**+**G**. Ardından **Oluştur** UI kontrol haritasında değişiklikler için kod oluşturmak için.

     ![UI haritasında için kod oluşturma](../test/media/generate-code-dialog.png)

1. Metin metin kutusuna değiştiğini doğrulamak için **düğmesi** düğmesine tıklandığında, düğmeye tıklayın.

     ![Düğme denetimi TextBox değeri ayarlamak için tıklayın](../test/media/uwp-app-button-textbox.png)

1. Textbox denetiminde metni doğrulamak için bir onay ekleyin. Textbox denetimi seçin ve ardından seçmek için artı işareti aracını kullanın **metin** özelliğinde **onaylama Ekle** iletişim. Ardından, **onaylama Ekle** veya basın **Alt**+**A**. İçinde **onaylama başarısız iletisi** kutusuna **Textbox değeri olması beklenmiyor.** ve ardından **Tamam**.

     ![TextBox ile artı seçin ve onaylama Ekle](../test/media/add-assertion-for-text.png)

1. Onay için test kod oluşturur. İçinde **kodlanmış UI Test Oluşturucusu** iletişim kutusunda **kod üret**. İçinde **kod üret** iletişim kutusunda **Ekle ve Oluştur**.

     ![Textbox onaylama için kod oluşturma](../test/media/add-and-generate-assert-method.png)

   İçinde **Çözüm Gezgini**açın *UIMap.Designer.cs* onay yöntemi ve denetimler için eklenen kodu görüntülemek için.

   > [!TIP]
   > Visual Basic kullanıyorsanız açın *Codeduıtest1.vb*. Ardından `CodedUITestMethod1()` test yöntemi kodu, onay yöntemi çağrısını sağ `Me.UIMap.AssertMethod1()` ve **tanıma**. *UIMap.Designer.vb* açılarak Kod Düzenleyicisi ve onay yöntemi ve denetimler için eklenen kodu görüntüleyebilirsiniz.

    > [!WARNING]
    > Değişiklik yapmayın *UIMap.Designer.cs* veya *UIMap.Designer.vb* dosyalarını doğrudan. Bunu yaparsanız, testi oluşturulduğunda, değişikliklerin üzerine yazılır.

    Assert yöntemini şöyle görünür:

    ```csharp
    public void AssertMethod1()
    {
        #region Variable Declarations
        XamlEdit uITextBoxEdit = this.UIUWPAppWindow.UITextBoxEdit;
        #endregion

        // Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(this.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.");
    }
    ```

    ```vb
    Public Sub AssertMethod1()
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit

        'Verify that the 'Text' property of 'textBox' text box equals 'button'
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text, "Textbox value is unexpected.")
    End Sub
    ```
1. Ardından, elde etmek ihtiyacımız **Automationıd** UWP, [uygulama](#create-a-uwp-app-to-test) , test etmek istiyoruz. Windows açın **Başlat** menüsünde uygulama kutucuğuna bakın. Ardından, ince artı aracını sürükleyin ![hedef simgesine](media/target-icon.png) gelen **kodlanmış UI Test Oluşturucusu** uygulamanız için bir kutucuk için iletişim. Kutucuk mavi bir kutu çevreleyen, farenizi serbest bırakın.

   ![İnce artı aracını](media/cross-hair-tool.png)

   **Onaylama Ekle** iletişim kutusu açılır ve görüntüler **Automationıd** uygulamanız için. Sağ **Automationıd** ve **değeri Panoya Kopyala**.

   ![Onaylama Ekle iletişim kutusunda Automationıd](../test/media/automation-id.png)

1. UWP uygulamasını başlatmak için test yöntemi için kod ekleyin. İçinde **Çözüm Gezgini**açın *Codeduıtest1.cs* veya *Codeduıtest1.vb*. Yukarıdaki çağrı `AssertMethod1`, UWP uygulamasını başlatmak için kodu ekleyin:

   ```csharp
   XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")
   ```

   ```vb
   XamlWindow myAppWindow = XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");
   ```

   Otomasyon kimliği örnek kod, önceki adımda panoya kopyaladığınız değeriyle değiştirin.

   > [!IMPORTANT]
   > Karakterleri gibi kaldırmak için Otomasyon kimliği başına kesim **P ~**. Bu karakterleri kırpma yoksa, test oluşturur. bir `Microsoft.VisualStudio.TestTools.UITest.Extension.PlaybackFailureException` olduğunda çalışır uygulamayı başlatmak.

1. Ardından, düğmesine tıklamanız test yöntemi için kod ekleyin. Sonra satırında `XamlWindow.Launch`, düğme denetimine dokunma hareketi ekleyin:

   ```csharp
   Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);
   ```

   ```vb
   Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)
   ```

   Tam kod ekledikten sonra `CodedUITestMethod1` test yöntemi şu şekilde görünmelidir:

   ```csharp
   [TestMethod]
   public void CodedUITestMethod1()
   {
       XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App");

       Gesture.Tap(this.UIMap.UIUWPAppWindow.UIButtonButton);

       // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
       this.UIMap.AssertMethod1();
   }
   ```

   ```vb
   <CodedUITest(CodedUITestType.WindowsStore)>
   Public Class CodedUITest1

       <TestMethod()>
       Public Sub CodedUITestMethod1()

           ' Launch the app.
           XamlWindow.Launch("af5ecd75-f252-45a1-9e7e-c6f1d8f054ff_0q1pp7qrjexbp!App")

           '// Tap the button.
           Gesture.Tap(Me.UIMap.UIUWPAppWindow.UIButtonButton)

           Me.UIMap.AssertMethod1()
       End Sub
   ```

1. Test projesi oluşturmak ve ardından açın **Test Gezgini** seçerek **Test** > **Windows** > **Test Gezgini**.

1. Seçin **tümünü Çalıştır** testi çalıştırmak için.

   Uygulama açılır, düğmeye dokunulduğunda ve metin kutusunun **metin** özelliği doldurulur. Assert yöntemini metin kutusunun doğrular **metin** özelliği.

   Test tamamlandıktan sonra **Test Gezgini** geçilen testleri gösterir.

   ![Geçen test Test Gezgini'nde görüntüler.](../test/media/test-explorer-coded-ui-test-passed.png)

## <a name="q--a"></a>Soru - Yanıt

### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>Kodlanmış UI testi iletişim kutusu için kod üret içinde kodlanmış UI testimi kaydetme seçeneğini neden görmüyorum?

**A**: kaydedilecek seçenek UWP uygulamaları için desteklenmez.

### <a name="q-can-i-create-a-coded-ui-test-for-my-uwp-apps-based-on-winjs"></a>Kodlanmış UI testi için UWP uygulamalarım WinJS üzerinde oluşturabilirim miyim?

**A**: Hayır, yalnızca XAML tabanlı uygulamalar desteklenir.

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>UIMap.Designer dosyasındaki kodu neden değiştiremiyorum?

**A**: herhangi bir kod, yaptığınız değişiklikler *UIMapDesigner.cs* dosyanın üzerine kod kullanarak oluşturduğunuz her zaman **kodlanmış UI Test Oluşturucusu**. Kayıtlı bir yöntemi değiştirmeniz gerekiyorsa, kopyalayın *UIMap.cs* dosya ve yeniden adlandırın. *UIMap.cs* dosya, yöntemleri ve özellikleri geçersiz kılmak için kullanılabilir *UIMapDesigner.cs* dosya. Orijinal yönteme başvuruyu kaldırmak *CodedUITest.cs* dosya ve adlandırılan yöntem adıyla değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [UI otomasyonunu kullanarak kodunuzu test etme](../test/use-ui-automation-to-test-your-code.md)
- [UWP denetimleri için benzersiz Otomasyon özelliklerini ayarlama](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)