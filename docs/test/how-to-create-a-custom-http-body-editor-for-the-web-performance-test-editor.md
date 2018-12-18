---
title: Bir Web Performans Testi Düzenleyicisi için özel HTTP Gövde Düzenleyicisi oluşturma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, custom HTTP body editor
ms.assetid: a0b2d8ff-3e2a-487e-9172-90047174f336
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 83ed50b5f242f5a869e1c0a69bf6a0674bdf4d69
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068415"
---
# <a name="how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor"></a>Nasıl yapılır: bir özel HTTP Gövde Düzenleyicisi için Web Performans Testi Düzenleyicisi oluşturma

Dize gövdesi içeriğini veya bir web hizmeti isteği, örneğin SOAP, REST, asmx, wcf, RIA ve diğer web hizmeti istek türlerinin ikili gövde içeriğini düzenlemenize olanak sağlayan özel bir içerik düzenleyici oluşturabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Bu tür düzenleyicileri uygulayabilirsiniz:

-   **Dize içerik Düzenleyicisi** bu kullanılarak uygulanan <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> arabirimi.

-   **İkili içerik Düzenleyicisi** bu kullanılarak uygulanan <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> arabirimi.

Bu arabirimler bulunan <xref:Microsoft.VisualStudio.TestTools.WebTesting> ad alanı.

## <a name="create-a-windows-control-library-project"></a>Bir Windows Denetim Kitaplığı projesi oluşturun

### <a name="create-a-user-control-by-using-a-windows-control-library-project"></a>Bir Windows Denetim Kitaplığı projesi kullanarak bir kullanıcı denetimi oluşturma

1. Visual Studio'da üzerinde **dosya** menüsünde seçin **yeni** seçip **proje**.

    **Yeni proje** iletişim kutusu görüntülenir.

2. Altında **yüklü şablonlar**, şunlardan birini seçin **Visual Basic** veya **Visual C#** programlama tercihinize göre ve ardından **Windows**.

   > [!NOTE]
   > Bu örnek, Visual C# kullanmaktadır.

3. Şablonlar listesinde seçin **Windows Forms Denetim Kitaplığı**.

4. İçinde **adı** metin kutusuna bir ad, örneğin, türü `MessageEditors`ve **Tamam**.

   > [!NOTE]
   > Bu örnek, MessageEditors kullanmaktadır.

    Proje yeni çözüme eklenir ve <xref:System.Windows.Forms.UserControl> adlı *UserControl1.cs* Tasarımcı içinde sunulur.

5. Gelen **araç kutusu**altında **ortak denetimleri** kategorisi bir <xref:System.Windows.Forms.RichTextBox> UserControl1 yüzeyine sürükleyin.

6. Eylem etiket karakterini seçin (![akıllı etiket karakterini](../test/media/vs_winformsmttagglyph.gif)) sağ üst köşesindeki <xref:System.Windows.Forms.RichTextBox> denetlemek ve ardından seçin ve **üst kapsayıcıya Yerleştir**.

7. İçinde **Çözüm Gezgini**, Windows Forms kitaplık projesini sağ tıklatın ve seçin **özellikleri**.

8. İçinde **özellikleri**seçin **uygulama** sekmesi.

9. İçinde **hedef Framework'ü** aşağı açılan listesinden **.NET Framework 4**.

10. **Hedef Framework değişikliği** iletişim kutusu görüntülenir.

11. Seçin **Evet**.

12. İçinde **Çözüm Gezgini**, sağ **başvuruları** düğümünü seçip alt **Başvuru Ekle**.

13. **Başvuru Ekle** iletişim kutusu görüntülenir.

14. Seçin. **NET** sekmesinde, aşağı kaydırın ve seçin **Microsoft.VisualStudio.QualityTools.WebTestFramework** seçip **Tamam**.

15. Varsa **Görünüm Tasarımcısı** içinde hala açık değilse **Çözüm Gezgini**, sağ **UserControl1.cs** seçip **Görünüm Tasarımcısı**.

16. Tasarım yüzeyinde, sağ tıklayıp **kodu görüntüle**.

17. (İsteğe bağlı) Sınıf ve oluşturucu adını UserControl1'den, örneğin, MessageEditorControl gibi anlamlı bir ad ile değiştirin:

    > [!NOTE]
    > Örnek MessageEditorsControl kullanır.

    ```csharp
    namespace MessageEditors
    {
        public partial class MessageEditorControl : UserControl
        {
            public MessageEditorControl()
            {
                InitializeComponent();
            }
        }
    }
    ```

18. Alma ve RichTextBox1 metni ayarlama etkinleştirmek için aşağıdaki özellikleri ekleyin. <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> Arabirimi EditString ve <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> EditByteArray öğesini kullanır:

    ```csharp
    public String EditString
    {
       get
       {
           return this.richTextBox1.Text;
       }
       set
       {
           this.richTextBox1.Text = value;
       }
    }

    public byte[] EditByteArray
    {
       get
       {
           return System.Convert.FromBase64String(richTextBox1.Text);
       }
       set
       {
           richTextBox1.Text = System.Convert.ToBase64String(value, 0, value.Length);
       }
    }
    ```

## <a name="add-a-class-to-the-windows-control-library-project"></a>Windows Denetim Kitaplığı projesine bir sınıf ekleyin

Projeye bir sınıf ekleyin. Uygulamak için kullanılacak <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> ve <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> arabirimleri.

**Bu yordamdaki koda genel bakış**

MessageEditorControl <xref:System.Windows.Forms.UserControl> oluşturulan önceki yordamı messageEditorControl örneği olarak oluşturulur:

```csharp
private MessageEditorControl messageEditorControl
```

 MessageEditorControl örneği tarafından oluşturulan eklenti iletişiminin içinde barındırılır <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.CreateEditor*> yöntemi. Ayrıca, messageEditorControl'un <xref:System.Windows.Forms.RichTextBox> içerikle doldurulur <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>. Sürece eklentinin oluşumu ancak oluşamaz <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> döndürür `true`. Bu Düzenleyicide <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> döndürür `true` varsa <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> içinde <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> "xml" içerir.

 Dize gövdesinin düzenlenmesi tamamlandığında ve kullanıcı **Tamam** eklenti iletişim kutusundaki <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.GetNewValue*> düzenlenmiş metni bir dize ve güncelleştirme olarak almak için çağrılan **dize gövdesi** Web isteği Test performans Düzenleyicisi.

### <a name="to-create-a-class-and-implement-the-istringhttpbodyeditorplugin-interface-code"></a>Bir sınıf oluşturmak ve IStringHttpBodyEditorPlugin arabirimi kodunu uygulamak için

1.  İçinde **Çözüm Gezgini**, Windows Forms Denetim Kitaplığı projesini sağ tıklatın ve seçin **Yeni Öğe Ekle**.

2.  **Yeni Öğe Ekle** iletişim kutusu görüntülenir.

3.  Seçin **sınıfı**.

4.  İçinde **adı** metin kutusunda, sınıf için anlamlı bir ad yazın örneğin, `MessageEditorPlugins`.

5.  Seçin **ekleme**.

     Class1 projeye eklenir ve Kod Düzenleyicisi üzerinde sunulur.

6.  Kod Düzenleyicisi'nde, aşağıdaki ekleyin using deyimi:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    ```

7.  XmlMessageEditor sınıfını için aşağıdaki kodu yazın veya kopyalayın <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> arabirim ve gereken yöntemleri uygulamak:

    ```csharp
    /// <summary>
    /// Editor for generic text based hierarchical messages such as XML and JSON.
    /// </summary>
    public class XmlMessageEditor : IStringHttpBodyEditorPlugin
    {
        public XmlMessageEditor()
        {
        }

        /// <summary>
        /// Determine if this plugin supports the content type.
        /// </summary>
        /// <param name="contentType">The content type to test.</param>
        /// <returns>Returns true if the plugin supports the specified content type.</returns>
        public bool SupportsContentType(string contentType)
        {
            return contentType.ToLower().Contains("xml");
        }

        /// <summary>
        /// Create a UserControl to edit the specified bytes.
        /// This control will be hosted in the
        /// plugin dialog which provides OK and Cancel buttons.
        /// </summary>
        /// <param name="contentType">The content type of the BinaryHttpBody.</param>
        /// <param name="initialValue">The bytes to edit.  The bytes are the payload of a BinaryHttpBody.</param>
        /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
        public object CreateEditor(string contentType, string initialValue)
        {
            messageEditorControl = new MessageEditorControl();
            messageEditorControl.EditString = initialValue;
            return this.messageEditorControl;
        }

        /// <summary>
        /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
        /// </summary>
        public string GetNewValue()
        {
            return messageEditorControl.EditString;
        }

        private MessageEditorControl messageEditorControl;
    }
    ```

## <a name="add-a-ibinaryhttpbodyeditorplugin-to-the-class"></a>Sınıfa bir IBinaryHttpBodyEditorPlugin ekleyin

Uygulama <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> arabirimi.

**Bu yordamdaki koda genel bakış**

İçin kod uygulaması <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> arabirimi benzer <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> önceki yordamda işlenen. Ancak, ikili dosya sürümü bir dize yerine ikili verileri işlemek için bayt dizisini kullanır.

MessageEditorControl <xref:System.Windows.Forms.UserControl> oluşturulan MessageEditorControl örneği olarak ilk yordam örneği:

```csharp
private MessageEditorControl messageEditorControl
```

MessageEditorControl örneği tarafından oluşturulan eklenti iletişiminin içinde barındırılır <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.CreateEditor*> yöntemi. Ayrıca, messageEditorControl'un <xref:System.Windows.Forms.RichTextBox> içerikle doldurulur <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>. Sürece eklentinin oluşumu ancak oluşamaz <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> döndürür `true`. Bu Düzenleyicide <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> döndürür `true` varsa <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> içinde <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> "msbin1" içerir.

Dize gövdesinin düzenlenmesi tamamlandığında ve kullanıcı **Tamam** eklenti iletişim kutusundaki <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.GetNewValue*> düzenlenmiş metni bir dize ve güncelleştirme olarak almak için çağrılan **BinaryHttpBody.Data** istek Web Test performans Düzenleyicisi'nde.

### <a name="to-add-the-ibinaryhttpbodyeditorplugin-to-the-class"></a>IBinaryHttpBodyEditorPlugin'i sınıfa eklemek için

-   Msbin1MessageEditor sınıfını için önceki yordamda eklenen XmlMessageEditor sınıfının altına aşağıdaki kodu yazın veya kopyalayın <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> arabirim ve gereken yöntemleri uygulamak:

    ```csharp
    /// <summary>
        /// Editor for MSBin1 content type (WCF messages)
        /// </summary>
        public class Msbin1MessageEditor : IBinaryHttpBodyEditorPlugin
        {
            /// <summary>
            ///
            /// </summary>
            public Msbin1MessageEditor()
            {
            }

            /// <summary>
            /// Determine if this plugin supports a content type.
            /// </summary>
            /// <param name="contentType">The content type to test.</param>
            /// <returns>Returns true if the plugin supports the specified content type.</returns>
            public bool SupportsContentType(string contentType)
            {
                return contentType.ToLower().Contains("msbin1");
            }

            /// <summary>
            /// Create a UserControl to edit the specified bytes.  This control will be hosted in the
            /// plugin dialog which provides OK and Cancel buttons.
            /// </summary>
            /// <param name="contentType">The content type of the BinaryHttpBody.</param>
            /// <param name="initialValue">The bytes to edit.  The bytes are the payload of a BinaryHttpBody.</param>
            /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
            public object CreateEditor(string contentType, byte[] initialValue)
            {
                messageEditorControl = new MessageEditorControl();
                messageEditorControl.EditByteArray = initialValue;
                return messageEditorControl;
            }

            /// <summary>
            /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
            /// </summary>
            public byte[] GetNewValue()
            {
                return messageEditorControl.EditByteArray;
            }

            private MessageEditorControl messageEditorControl;
            private object originalMessage;
        }
    ```

## <a name="build-and-deploy-the-plug-ins"></a>Derleme ve eklentileri dağıtma

### <a name="to-build-and-deploy-the-resulting-dll-for-the-istringhttpbodyeditorplugin-and-ibinaryhttpbodyeditorplugin"></a>Oluşturmak ve IStringHttpBodyEditorPlugin ve IBinaryHttpBodyEditorPlugin için ortaya çıkan DLL'yi dağıtmak için

1.  Üzerinde **derleme** menüsünde seçin **derleme \<Windows Form Denetim Kitaplığı proje adı >**.

2.  Visual Studio'nun tüm örneklerini kapatın.

    > [!NOTE]
    > Visual Studio kapatıldıktan emin olur *.dll* kopyalamak denemeden önce dosya kilitli değil.

3.  Ortaya çıkan kopyalama *.dll* projelerinizi dosyasından *bin\debug* klasöre (örneğin, *MessageEditors.dll*) için *%ProgramFiles%\Microsoft Visual Studio\2017\\<edition>\Common7\IDE\PrivateAssemblies\WebTestPlugins*.

4.  Visual Studio'yu açın.

     *.Dll* artık Visual Studio ile kayıtlıdır.

## <a name="verify-the-plug-ins-using-a-web-performance-test"></a>Bir Web performans testi kullanarak eklentileri doğrulayın

### <a name="to-test-your-plug-ins"></a>Eklentilerinizi test etmek için

1.  Bir Test projesi oluşturun.

2.  Web performans testi oluşturma ve bir web hizmetine tarayıcıda bir URL girin.

3.  Kaydı bitirdikten sonra Web Performans Testi Düzenleyicisi'nde, web hizmeti isteğini genişletin ve seçin ya da bir **dize gövdesi** veya **ikili gövde**.

4.  Özellikler penceresinde, dize gövde veya İkili Gövde'ı seçin ve üç noktayı seçin **(...)** .

     **HTTP Gövde verisini Düzenle** iletişim kutusu görüntülenir.

5.  Artık verileri düzenleyebilir ve seçin **Tamam**. Bu içeriği güncelleştirmek için uygun GetNewValue yöntemini çağırır <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>.

## <a name="compile-the-code"></a>Kod derleme

Windows Denetim Kitaplığı projesi için hedeflenen çerçevenin .NET Framework 4.5 olduğunu doğrulayın. Varsayılan olarak, Windows Denetim Kitaplığı projeleri, eklenmesi, Microsoft.VisualStudio.QualityTools.WebTestFramework başvurusunun eklenmesine izin vermez .NET Framework 4.5 istemci çerçevesini hedefler.

Daha fazla bilgi için [uygulama sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.RichTextBox>
- [Özel kod ve yük testleri için eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Nasıl yapılır: istek düzeyi eklentisi oluşturma](../test/how-to-create-a-request-level-plug-in.md)
- [Kodu bir web performans testi için özel bir ayıklama kuralı](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kodu bir web performans testi için özel doğrulama kuralı](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Nasıl yapılır: bir yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md)
- [Oluşturma ve bir kodlanmış web performans testini çalıştırma](../test/generate-and-run-a-coded-web-performance-test.md)
- [Nasıl yapılır: Web Performans Test Sonuçları Görüntüleyicisi için bir Visual Studio eklentisi oluşturma](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)