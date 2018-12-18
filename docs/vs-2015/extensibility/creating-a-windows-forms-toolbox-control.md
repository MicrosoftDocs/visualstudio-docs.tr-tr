---
title: Oluşturma bir Windows Forms araç kutusu denetimi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 371fd4269cee5918bd0d0b623eb49e1f709a311d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781718"
---
# <a name="creating-a-windows-forms-toolbox-control"></a>Windows Forms Araç Kutusu Denetimi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio genişletilebilirlik Araçları (VS SDK) dahil Windows Forms araç kutusu denetimi öğe şablonu otomatik olarak eklenen bir denetim oluşturmanızı sağlar **araç kutusu** uzantısı yüklü olduğunda. Bu konuda, diğer kullanıcılarına dağıtabileceğiniz bir basit bir sayaç denetimi oluşturmak için şablonu kullanmayı gösterir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015'ten başlayarak, size Visual Studio SDK İndirme Merkezi'nden yüklemeyin. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yi daha sonra yükleyebilirsiniz. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-windows-forms-toolbox-control"></a>Windows Forms Araç Kutusu Denetimi Oluşturma  
 Windows Forms araç kutusu denetim şablonu tanımlanmamış kullanıcı denetimi oluşturur ve tüm denetime eklemek için gereken işlevselliği sağlayan **araç kutusu**.  
  
#### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Bir Windows Forms araç kutusu denetimi ile bir uzantı oluşturma  
  
1.  Adlı bir VSIX projesi oluşturun `MyWinFormsControl`. VSIX proje şablonunda bulabilirsiniz **yeni proje** iletişim altında **Visual C# / genişletilebilirlik**.  
  
2.  Projeyi açtığında, ekleme bir **Windows Forms araç kutusu denetimi** adlı öğe şablonu `Counter`. İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Ekle / yeni öğe**. İçinde **Yeni Öğe Ekle** iletişim kutusunda, Git **Visual C# / genişletilebilirlik** seçip **Windows Forms araç kutusu denetimi**  
  
3.  Bu bir kullanıcı denetimi ekler bir `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> denetiminde yerleştirmek için **araç kutusu**ve **Microsoft.VisualStudio.ToolboxControl** dağıtım için VSIX bildirimi varlık girişi.  
  
### <a name="building-a-user-interface-for-the-control"></a>Denetim için bir kullanıcı arabirimi oluşturma  
 `Counter` Denetim gerektiren iki alt denetimleri: bir <xref:System.Windows.Forms.Label> geçerli sayısını görüntülemek için ve bir <xref:System.Windows.Forms.Button> sayısı 0 olarak ayarlamak için. Çağıranlar sayacı programlı olarak artırır çünkü başka bir alt denetimler gereklidir.  
  
##### <a name="to-build-the-user-interface"></a>Kullanıcı arabirimini oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, Counter.cs tasarımcıda açmak için çift tıklayın.  
  
2.  "Buraya tıklayın!" Kaldır **Düğme** dahil edilmiş varsayılan olarak, Windows Forms araç kutusu denetimi öğe şablonu eklediğinizde.  
  
3.  Gelen **araç kutusu**, sürükleyin bir `Label` denetimi ve ardından bir `Button` altındaki denetimi tasarım yüzeyine bırakın.  
  
4.  Genel kullanıcı denetimine 150 yeniden boyutlandırma, 50 piksel ve yeniden boyutlandırma düğme denetimi 50'ye 20 piksel.  
  
5.  İçinde **özellikleri** penceresinde tasarım yüzeyinde denetimler için aşağıdaki değerleri ayarlayın.  
  
    |Denetim|Özellik|Değer|  
    |-------------|--------------|-----------|  
    |`Label1`|**Metin**|""|  
    |`Button1`|**Ad**|btnReset|  
    |`Button1`|**Metin**|Sıfırlama|  
  
### <a name="coding-the-user-control"></a>Kullanıcı denetimi kodlama  
 `Counter` Denetim kullanıma sunma sayacın sayaç artırılır her oluşturulması için bir olay için bir yöntem bir `Reset` düğmesi ve geçerli sayı, görüntülenecek metni ve Göster veya gizle depolamakiçinüçözellik`Reset`düğmesi. `ProvideToolboxControl` Özniteliği belirler nerede **araç kutusu** `Counter` denetimi görünür.  
  
##### <a name="to-code-the-user-control"></a>Kullanıcı denetimi kod  
  
1.  Form, kendi yük olay işleyicisine kod penceresinde açmak için çift tıklayın.  
  
2.  Olay işleyicisi yöntemi ', sayaç değeri ve aşağıdaki örnekte gösterildiği gibi görünen metin depolamak için bir dize depolamak için bir tamsayı denetimi sınıfta oluşturun.  
  
    ```csharp  
    int currentValue;  
    string displayText;  
    ```  
  
3.  Aşağıdaki ortak özelliği bildirimleri oluşturun.  
  
    ```csharp  
    public int Value {  
        get { return currentValue; }   
    }  
  
    public string Message {  
        get { return displayText; }  
        set { displayText = value; }  
    }  
  
    public bool ShowReset {  
        get { return btnReset.Visible; }  
        set { btnReset.Visible = value; }  
    }  
  
    ```  
  
     Çağıranlar almak ve sayaç görüntü metnini ayarlamak için ve göstermek veya gizlemek için bu özellikleri erişebilir `Reset` düğmesi. Çağıranlar, salt okunur geçerli değerini elde edebilirsiniz `Value` özelliği ancak ayarlayamıyor değeri doğrudan.  
  
4.  Aşağıdaki kod koymak `Load` Olay denetimi.  
  
    ```csharp  
    private void Counter_Load(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = Message + Value;  
    }  
  
    ```  
  
     Ayarı **etiket** metinde <xref:System.Windows.Forms.UserControl.Load> olay değerlerine uygulanmadan önce yüklemek hedef özellikleri sağlar. Ayarı **etiket** metin Oluşturucu bir boş sonuçlanır **etiket**.  
  
5.  Sayaç artırmak için aşağıdaki genel yöntem oluşturun.  
  
    ```csharp  
    public void Increment()  
    {  
        currentValue++;  
        label1.Text = displayText + Value;  
        Incremented(this, EventArgs.Empty);  
    }  
  
    ```  
  
6.  Eklemek için bir bildirim `Incremented` olaya control sınıfı.  
  
    ```csharp  
    public event EventHandler Incremented;  
    ```  
  
     Çağıranlar, sayaç değeri değişikliklere yanıt vermek için bu olay işleyicileri ekleyebilirsiniz.  
  
7.  Çift tıklayın ve Tasarım görünümüne dön `Reset` oluşturmak için düğme `btnReset_Click` olay işleyicisi ve ardından buna aşağıdaki örnekte gösterildiği gibi doldurun.  
  
    ```csharp  
    private void btnReset_Click(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = displayText + Value;  
    }  
  
    ```  
  
8.  Hemen üzerinde sınıf tanımının içinde `ProvideToolboxControl` özniteliği bildirimi, ilk parametresinden değiştirin `"MyWinFormsControl.Counter"` için `"General"`. Bu denetimde barındıracak öğesi grubunun adını ayarlar **araç kutusu**.  
  
     Aşağıdaki örnekte gösterildiği `ProvideToolboxControl` özniteliği ve ayarlanmış bir sınıf tanımı.  
  
    ```csharp  
    [ProvideToolboxControl("General", false)]  
    public partial class Counter : UserControl  
    ```  
  
### <a name="testing-the-control"></a>Denetimini test etme  
 Test etmek için bir **araç kutusu** denetlemek, ilk geliştirme ortamında test edin ve içinde derlenen bir uygulamayı test edin.  
  
##### <a name="to-test-the-control"></a>Denetimi'ni sınamak için  
  
1.  F5 tuşuna basın.  
  
     Bu projeyi derler ve Visual Studio'nun yüklü denetimi olan ikinci bir deneysel örneği açılır.  
  
2.  Visual Studio'nun deneysel örneğinde oluşturma bir **Windows Forms uygulaması** proje.  
  
3.  İçinde **Çözüm Gezgini**, Form1.cs zaten açık değilse, tasarımcıda açmak için çift tıklayın.  
  
4.  İçinde **araç kutusu**, `Counter` denetim görüntüleneceğine **genel** bölümü.  
  
5.  Sürükleme bir `Counter` Formunuza denetim ve ardından bu seçeneği belirleyin. `Value`, `Message`, Ve `ShowReset` özellikleri içinde görüntülenecektir **özellikleri** birlikte öğesinden devralınan Özellikler penceresinde <xref:System.Windows.Forms.UserControl>.  
  
6.  Ayarlama `Message` özelliğini `Count:`.  
  
7.  Sürükleme bir <xref:System.Windows.Forms.Button> forma denetim ve ardından düğmeyi adını ve metin özelliklerini `Test`.  
  
8.  Form1.cs kod Görünümü'nde açın ve bir tıklama işleyicisi oluşturmak için düğmeyi çift tıklatın.  
  
9. Tıklama işleyicisi arama `counter1.Increment()`.  
  
10. Oluşturucu işlevi çağırdıktan sonra içinde `InitializeComponent`, türü `counter1``.``Incremented +=` ve sonra SEKME tuşuna iki kez basın.  
  
     Visual Studio için bir form düzeyinde işleyici oluşturur `counter1.Incremented` olay.  
  
11. Vurgulayın `Throw` olay işleyicisi, türü deyiminde `mbox`, ardından iki kez mbox kod parçacığı bir ileti kutusu oluşturmak için TAB tuşuna basın.  
  
12. Aşağıdakileri sonraki satırda ekleyin `if` / `else` görünürlüğünü ayarlamak için blok `Reset` düğmesi.  
  
    ```csharp  
    if (counter1.Value < 5) counter1.ShowReset = false;  
    else counter1.ShowReset = true;  
    ```  
  
13. F5 tuşuna basın.  
  
     Form açılır. `Counter` Denetimi, aşağıdaki metni görüntüler.  
  
     **Sayı: 0**  
  
14. Tıklayın **Test**.  
  
     Sayacını artırır ve Visual Studio, bir ileti kutusu görüntüler.  
  
15. İleti kutusunu kapatın.  
  
     **Sıfırlama** düğme kaybolur.  
  
16. Tıklayın **Test** sayaç ulaşana kadar **5** kutuları her iletiyi kapattıktan.  
  
     **Sıfırlama** düğme yeniden görünür.  
  
17. Tıklayın **sıfırlama**.  
  
     Sayaç sıfırlanır için **0**.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Yapı kurarken bir **araç kutusu** denetimi, Visual Studio, adlı bir dosya oluşturur *ProjectName*projenizin \bin\debug\ klasöründe .vsix. Bir ağ veya Web sitesine .vsix dosyasını karşıya yükleyerek denetim dağıtabilirsiniz. .Vsix dosyasını bir kullanıcı oturum açtığında, denetimin yüklenir ve Visual Studio için eklenen **araç kutusu** kullanıcının bilgisayarında. Alternatif olarak, .vsix dosyasına yükleyebilirsiniz [Visual Studio Galerisi](http://go.microsoft.com/fwlink/?LinkID=123847) Web sitesi kullanıcılar bunu göz atarak bulabilirsiniz **araçları / uzantı ve güncelleştirmeler** iletişim.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araç kutusu genişletme](../misc/extending-the-toolbox.md)   
 [WPF araç kutusu denetimi oluşturma](../extensibility/creating-a-wpf-toolbox-control.md)   
 [Visual Studio'nun diğer bölümlerini genişletme](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Windows Forms Denetimi Geliştirmenin Esasları](http://msdn.microsoft.com/library/6277bb81-90f7-4c5b-9f4b-b02bb42dd316)

