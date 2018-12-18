---
title: 'Nasıl yapılır: sihirbazları proje şablonlarıyla kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 650b9c360013d06216e607269f77afd24f3cc22c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783766"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Nasıl Yapılır: Sihirbazları Proje Şablonlarıyla Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio sağlar <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> uygulandığında, arabirim, kullanıcı bir şablondan proje oluşturduğu zaman özel kod çalıştırmanıza olanak sağlar.  
  
 Proje şablonu özelleştirmesi, kullanıcı girişi şablonu özelleştirmek için şablona ek dosyalar ekleyin veya izin verilen herhangi bir işlem, bir proje üzerinde toplayan özel kullanıcı arabirimini görüntülemek için kullanılabilir.  
  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Arabirim yöntemleri proje, bir kullanıcı tıkladığında başlayarak oluşturulurken çeşitli zamanlarda çağrılır **Tamam** üzerinde **yeni proje** iletişim kutusu. Her arabirim yöntemi çağrıldığı noktası tanımlamak için adlandırılır. Örneğin, Visual Studio çağırır <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> projeyi oluşturmak başladığında hemen, kullanıcı girişini toplamak için özel kod yazmak için iyi bir konum haline getirir.  
  
## <a name="creating-a-project-template-project-with-a-vsix-project"></a>Bir VSIX projesi ile bir proje şablonu projesi oluşturma  
 Bir özel şablonu proje şablonu proje Visual Studio SDK'ın bir parçası. ile oluşturmaya başlayın. Bu yordamda bir C# proje şablonu projesi kullanacağız, ancak Visual Basic proje şablonu projesi de mevcuttur. Ardından bir VSIX projesi içeren proje şablonu projesi çözüme ekleyin.  
  
1.  Bir C# proje şablonu projesi oluşturma (Visual Studio'da **dosya / yeni / Project / Visual C# / genişletilebilirlik / C# proje şablonu**). Adlandırın **MyProjectTemplate**.  
  
    > [!NOTE]
    >  Visual Studio SDK'yı yüklemeyi istenebilir. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  Yeni projeye VSIX ekleme (**dosya / yeni / Project / Visual C# / genişletilebilirlik / VSIX projesi**) proje şablonu projesi olarak aynı çözüm içindeki (içinde **Çözüm Gezgini**, çözüm düğümü seçin sağ tıklatın ve seçin **Ekle / yeni proje**). Adlandırın **MyProjectWizard.**  
  
3.  VSIX projesini başlangıç projesi olarak ayarlayın. İçinde **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın ve Seç'i seçin **başlangıç projesi olarak ayarla**.  
  
4.  Şablonu projesi VSIX projesinin bir varlık ekleyin. İçinde **Çözüm Gezgini**, VSIX proje düğümü altında bulun **source.extension.vsixmanifest** dosya. Bildirim Düzenleyicisi'nde açmak için çift tıklayın.  
  
5.  Bildirim düzenleyicisinde **varlıklar** pencerenin sol tarafındaki sekmesi.  
  
6.  İçinde **varlıklar** sekmesinde **yeni**. İçinde **yeni varlık Ekle** türü alanı, Seç penceresinde **Microsoft.VisualStudio.ProjectTemplate**. İçinde **kaynak** alanın, Seç **mevcut çözümde bir proje**. İçinde **proje** alanın, Seç **MyProjectTemplate**. Sonra **Tamam**'a tıklayın.  
  
7.  Çözümü derleyin ve hata ayıklamaya başlayın. Visual Studio ikinci bir örneğini görünür. (Bu işlem birkaç dakika sürebilir.)  
  
8.  Yeni şablonunuzu yeni bir proje oluşturmak Visual Studio'nun ikinci örneğini deneyin. (**Dosya / yeni / Project / Visual C# / MyProject şablon**). Yeni Proje adlı bir sınıf ile görünmelidir **Class1**. Özel proje şablonu oluşturdunuz! Şimdi hata ayıklamayı durdurun.  
  
## <a name="creating-a-custom-template-wizard"></a>Bir özel şablon Sihirbazı oluşturma  
 Bu konuda, proje oluşturulmadan önce bir Windows formu açan özel bir sihirbazın nasıl oluşturulacağını gösterir. Form, kullanıcıların proje oluşturma sırasında kaynak koduna eklenen bir özel parametre değeri eklemesine olanak sağlar.  
  
1. Bir derleme oluşturmak izin vermek için VSIX projesi ayarlayın.  
  
2. İçinde **Çözüm Gezgini**, VSIX proje düğümünü seçin. Çözüm Gezgini görmelisiniz **özellikleri** penceresi. Bunu yapmazsanız seçin **görünüm / Özellikler penceresi**, veya basın **F4**. Özellikler penceresinde, aşağıdaki alanları seçin `true`:  
  
   -   **IncludeAssemblyInVSIXContainer**  
  
   -   **IncludeDebugSymbolsInVSIXContainer**  
  
   -   **IncludeDebugSymbolsInLocalVSIXDeployment**  
  
3. Bütünleştirilmiş kod bir varlık VSIX projesine ekleyin. Source.extension.vsixmanifest dosyasını açın ve seçin **varlıklar** sekmesi. İçinde **yeni varlık Ekle** penceresinde için **türü** seçin **Microsoft.VisualStudio.Assembly**, için **kaynak** seçin **A Geçerli çözümde proje**ve **proje** seçin **MyTemplateWizard**.  
  
4. VSIX projesinde aşağıdaki başvuruları ekleyin. (İçinde **Çözüm Gezgini**, VSIX altında düğüm seçin proje **başvuruları**, sağ tıklatın ve seçin **Başvuru Ekle**.) İçinde **Başvuru Ekle** iletişim, **Framework** sekmesinde, bulmak **System.Windows Forms** derlemesi ve bu seçeneği belirleyin. Şimdi seçtiğiniz **uzantıları** sekmesini Bul **EnvDTE** derleme ve bu seçeneği belirleyin. Ayrıca **Microsoft.VisualStudio.TemplateWizardInterface** derlemesi ve bu seçeneği belirleyin. **Tamam**'ı tıklatın.  
  
5. Sihirbaz uygulamasını için bir sınıf, VSIX projesine ekleyin. (Çözüm Gezgini'nde VSIX proje düğümünü sağ tıklatın ve seçin **Ekle**, ardından **yeni öğe**, ardından **sınıfı**.) Sınıf adı **WizardImplementation**.  
  
6. Değiştirin **WizardImplementationClass.cs** dosyasındaki kodu aşağıdaki kodla:  
  
   ```csharp  
   using System;  
   using System.Collections.Generic;  
   using Microsoft.VisualStudio.TemplateWizard;  
   using System.Windows.Forms;  
   using EnvDTE;  
  
   namespace MyProjectWizard  
   {  
       public class WizardImplementation:IWizard  
       {  
           private UserInputForm inputForm;  
           private string customMessage;  
  
           // This method is called before opening any item that   
           // has the OpenInEditor attribute.  
           public void BeforeOpeningFile(ProjectItem projectItem)  
           {  
           }  
  
           public void ProjectFinishedGenerating(Project project)  
           {  
           }  
  
           // This method is only called for item templates,  
           // not for project templates.  
           public void ProjectItemFinishedGenerating(ProjectItem   
               projectItem)  
           {  
           }  
  
           // This method is called after the project is created.  
           public void RunFinished()  
           {  
           }  
  
           public void RunStarted(object automationObject,  
               Dictionary<string, string> replacementsDictionary,  
               WizardRunKind runKind, object[] customParams)  
           {  
               try  
               {  
                   // Display a form to the user. The form collects   
                   // input for the custom message.  
                   inputForm = new UserInputForm();  
                   inputForm.ShowDialog();  
  
                   customMessage = UserInputForm.CustomMessage;  
  
                   // Add custom parameters.  
                   replacementsDictionary.Add("$custommessage$",   
                       customMessage);  
               }  
               catch (Exception ex)  
               {  
                   MessageBox.Show(ex.ToString());  
               }  
           }  
  
           // This method is only called for item templates,  
           // not for project templates.  
           public bool ShouldAddProjectItem(string filePath)  
           {  
               return true;  
           }          
       }  
   }  
   ```  
  
    **Userınputform** bu başvurulan kod uygulanmasını daha sonra.  
  
    `WizardImplementation` Sınıfı her üyesi için yöntem uygulamaları içermektedir <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>. Bu örnekte, yalnızca <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> yöntemi bir görev gerçekleştirir. Tüm diğer yöntemler birşey yapmazlar veya dönüş `true`.  
  
    <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> Yöntemi dört parametre kabul eder:  
  
   - Bir <xref:System.Object> kök dönüştürülebilen parametresi <xref:EnvDTE._DTE> sizi projeyi özelleştirmek üzere etkinleştirmek için nesne.  
  
   - A <xref:System.Collections.Generic.Dictionary%602> şablonda tüm önceden tanımlanan parametrelerin bir koleksiyonunu içeren bir parametre. Şablon parametreleri hakkında daha fazla bilgi için bkz. [şablon parametreleri](../ide/template-parameters.md).  
  
   - A <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> ne tür şablon kullanıldığına bilgi içeren bir parametre.  
  
   - Bir <xref:System.Object> parametreler kümesi içeren bir dizi için Sihirbazı'nı Visual Studio tarafından geçirilen.  
  
     Bu örnek için kullanıcı giriş formundan bir parametre değeri ekler <xref:System.Collections.Generic.Dictionary%602> parametresi. Her bir örneğini `$custommessage$` projedeki parametresi, kullanıcı tarafından girilen metinle değiştirilecektir. Aşağıdaki derlemeleri projenize eklemelisiniz:  
  
7. Şimdi oluşturmak **Userınputform**. İçinde **WizardImplementation.cs** sonunda aşağıdaki kodu ekleyin **WizardImplementation** sınıfı.  
  
   ```csharp  
   public partial class UserInputForm : Form  
       {  
           private static string customMessage;  
           private TextBox textBox1;  
           private Button button1;  
  
           public UserInputForm()  
           {  
               this.Size = new System.Drawing.Size(155, 265);   
  
               button1 = new Button();  
               button1.Location = new System.Drawing.Point(90, 25);  
               button1.Size = new System.Drawing.Size(50, 25);  
               button1.Click += button1_Click;  
               this.Controls.Add(button1);  
  
               textBox1 = new TextBox();  
               textBox1.Location = new System.Drawing.Point(10, 25);  
               textBox1.Size = new System.Drawing.Size(70, 20);  
               this.Controls.Add(textBox1);  
           }  
           public static string CustomMessage  
           {  
               get  
               {  
                   return customMessage;  
               }  
               set  
               {  
                   customMessage = value;  
               }     
           }  
           private void button1_Click(object sender, EventArgs e)  
           {  
               customMessage = textBox1.Text;  
           }  
       }  
   ```  
  
    Kullanıcı giriş formu, bir özel parametre girmek için basit bir form sağlar. Adlı bir metin kutusu formu içeren `textBox1` adlı bir düğme `button1`. Düğme tıklandığında metin kutusundaki metin depolanan `customMessage` parametresi.  
  
## <a name="connect-the-wizard-to-the-custom-template"></a>Sihirbaz özel şablonuna Bağla  
 Özel Sihirbazı kullanmak, özel bir proje şablonu Sihirbazı derlemeyi imzalamak ve sihirbaz uygulamasını yeni bir proje oluşturulduğunda nerede bulacağını biliyor izin vermek için özel Proje şablonunuza bazı satırlar eklemek gerekir.  
  
1. Derlemeyi imzalayın. İçinde **Çözüm Gezgini**, VSIX projesi, sağ tıklatın ve seçin seçin **proje özellikleri**.  
  
2. İçinde **proje özellikleri** penceresinde **imzalama** sekmesindeki **imzalama** sekmesinde, onay **derlemeyi imzalamayı**. İçinde **bir tanımlayıcı ad anahtar dosyası seç** alanın, Seç  **\<yeni >**. İçinde **katı ad anahtarı oluştur** penceresi içinde **anahtar dosya adı** alanına **key.snk**. Onay kutusunu temizleyin **anahtar dosyamı bir parolayla korumak** alan.  
  
3. İçinde **Çözüm Gezgini**, VSIX projesini seçin ve bulma **özellikleri** penceresi.  
  
4. Ayarlama **kopyalama çıkış için çıktı dizinine** alanı **true**. Bu çözümü yeniden oluşturulduğunda çıkış dizinine kopyalanacak derleme sağlar. Hala .vsix dosyasında yer alır. Derleme imza anahtarıyla bulmak amacıyla görmek gerekir.  
  
5. Çözümü yeniden derleyin.  
  
6. Artık key.snk dosya MyProjectWizard proje dizininde bulabilirsiniz (**\<disk konumunuz > \MyProjectTemplate\MyProjectWizard\key.snk**). Key.snk dosyasını kopyalayın.  
  
7. Çıkış dizinine gidin ve derleme bulunamadı (**\<disk konumunuz > \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll**). Key.snk dosyayı buraya yapıştırın. (Bu kesinlikle gerekli değildir, ancak aşağıdaki adımları daha kolay hale getirir.)  
  
8. Bir komut penceresi açın ve derleme oluşturulduktan dizine geçin.  
  
9. Bulma **sn.exe** imzalama aracı. Örneğin, bir Windows 10 64-bit işletim sisteminde tipik bir yol şu olacaktır:  
  
     **C:\Program dosyaları (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 araçları**  
  
     Aracı bulamazsanız çalıştırmayı deneyin **burada /R.  sn.exe** komut penceresinde. Yolunu not edin.  
  
10. Ortak anahtarı key.snk dosyasından ayıklayın. Komut penceresinde şunu yazın  
  
     **\<sn.exe konumunu > \sn.exe - p key.snk outfile.key.**  
  
     Dizin adlarındaki boşluklar varsa tırnak işaretleri ile sn.exe yolunu çevreleyen unutmayın!  
  
11. Ortak anahtar ÇıkışDosyası belirteci alın:  
  
     **\<sn.exe konumunu > \sn.exe - t outfile.key.**  
  
     Tırnak işaretleri yeniden unutmayın. Bir satırda şunun gibi bir çıktı görmeniz gerekir  
  
     **Ortak anahtar belirteci <token>**  
  
     Bu değeri not edin.  
  
12. Özel Sihirbazı başvuru proje şablonu için .vstemplate dosyası ekleyin. Çözüm Gezgini'nde MyProjectTemplate.vstemplate adlı dosyayı bulun ve açın. Sonunda \<TemplateContent > bölümünde, aşağıdaki bölümü ekleyin:  
  
    ```xml  
    <WizardExtension>  
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>  
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
     Burada **MyProjectWizard** derlemenin adıdır ve **belirteci** önceki adımda kopyaladığınız belirtecidir.  
  
13. Projedeki tüm dosyaları kaydedin ve yeniden derleyin.  
  
## <a name="adding-the-custom-parameter-to-the-template"></a>Özel parametre şablonuna ekleme  
 Bu örnekte, şablon olarak kullanılan proje özel sihirbazın kullanıcı giriş formunda belirtilen iletiyi görüntüler.  
  
1. Çözüm Gezgini'nde Git **MyProjectTemplate** açın ve proje **Class1.cs**.  
  
2. İçinde `Main` uygulama yöntemini aşağıdaki kod satırını ekleyin.  
  
   ```  
   Console.WriteLine("$custommessage$");  
   ```  
  
    Parametre `$custommessage$` bir proje şablondan oluşturulduğunda kullanıcı giriş formuna girilen metin ile değiştirilir.  
  
   Bir şablona aktarılmadan önce tam kod dosyasını aşağıdadır.  
  
```csharp  
using System;  
using System.Collections.Generic;  
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;  
$endif$using System.Text;  
  
namespace $safeprojectname$  
{  
    public class Class1  
    {  
          static void Main(string[] args)  
          {  
               Console.WriteLine("$custommessage$");  
          }  
    }  
}  
```  
  
## <a name="using-the-custom-wizard"></a>Özel Sihirbazı'nı kullanma  
 Şimdi şablonunuzdan proje oluşturabilir ve özel Sihirbazı'nı kullanın.  
  
1.  Çözümü yeniden oluşturun ve hata ayıklamaya başlayın. Visual Studio ikinci bir örneğini görüntülenmesi gerekir.  
  
2.  Yeni bir MyProjectTemplate projesi oluşturun. (**Dosya / yeni / Project / Visual C# / MyProjectTemplate**)  
  
3.  İçinde **yeni proje** iletişim kutusunda, şablonunuzu bulup bir ad yazın ve tıklayın **Tamam**.  
  
     Sihirbaz kullanıcı giriş formu açılır.  
  
4.  Özel parametre için bir değer yazın ve düğmeye tıklayın.  
  
     Sihirbaz kullanıcı giriş formu kapanır ve şablondan bir Proje oluşturulur.  
  
5.  İçinde **Çözüm Gezgini**, kaynak kod dosyasını sağ tıklatıp **kodu görüntüle**.  
  
     Dikkat `$custommessage$` Sihirbaz kullanıcı giriş formuna girilen metin ile değiştirilmiştir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
 [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)   
 [WizardExtension Öğesi (Visual Studio Şablonları)](../extensibility/wizardextension-element-visual-studio-templates.md)