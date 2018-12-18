---
title: Temel Proje sistemi oluşturma, bölüm 2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4f5a059562db2409dca8eca1fb53c007059456b9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928119"
---
# <a name="create-a-basic-project-system-part-2"></a>2. Bölüm temel proje sistemi oluşturma
Bu serideki ilk izlenecek [1. Bölüm temel proje sistemi oluşturma](../extensibility/creating-a-basic-project-system-part-1.md), temel proje sistemi oluşturma işlemi gösterilmektedir. Bu izlenecek yol, Visual Studio şablonu, bir özellik sayfası ve diğer özellikleri ekleyerek üzerinde temel proje sistemi oluşturur. Bu bir başlamadan önce ilk izlenecek yolu tamamlamanız gerekir.  
  
 Bu izlenecek yol, proje dosya adı uzantısına sahip bir proje türü oluşturmak öğretir *.myproj*. İzlenecek yolu tamamlamak için izlenecek yol, mevcut Visual C# proje sistemi çözümümüz kendi dilinize oluşturulamıyor gerekmez.  
  
 Bu izlenecek yol aşağıdaki görevlerin nasıl yerine getirileceğini öğretir:  
  
-   Visual Studio şablonu oluşturun.  
  
-   Visual Studio şablonu dağıtın.  
  
-   Bir proje türü alt düğüm oluşturma **yeni proje** iletişim kutusu.  
  
-   Parametre değiştirme Visual Studio şablonunda etkinleştirin.  
  
-   Proje özellik sayfası oluşturun.  
  
> [!NOTE]
>  Bu kılavuzda açıklanan adımları bir C# projesini temel alıyor. Ancak, dosya adı uzantıları ve kod gibi özellikleri dışında bir Visual Basic projesi için aynı adımları kullanabilirsiniz.  
  
## <a name="create-a-visual-studio-template"></a>Visual Studio şablon oluşturma  
 [1. Bölüm temel proje sistemi oluşturma](../extensibility/creating-a-basic-project-system-part-1.md) temel proje şablonu oluşturma ve proje sisteme ekleme işlemi gösterilmektedir. Ayrıca bu şablonu kullanarak Visual Studio ile kaydetme işlemini gösterir <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> tam yolunu yazan özniteliği *\\Templates\Projects\SimpleProject\\* sistem klasörü kayıt defteri.  
  
 Visual Studio şablonu kullanarak (*.vstemplate* dosya) yerine temel proje şablonu, şablonun nasıl görünür denetleyebilirsiniz **yeni proje** iletişim kutusu ve şablon parametreleri şeklini değiştirdi.  A *.vstemplate* kaynak dosyaları proje sistemi şablonunu kullanarak bir proje oluşturulduğunda, dahil edilecek şeklini açıklayan bir XML dosyasını bir dosyadır. Proje sistemi toplayarak oluşturulan *.vstemplate* dosya ve kaynak dosyalarında bir *.zip* dosya ve kopyalayarak dağıtılan *.zip* bir konuma dosya Visual Studio bilinen. Bu işlem, bu kılavuzda daha sonra daha ayrıntılı açıklanmıştır.  
  
1. İçinde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], izleyerek oluşturduğunuz SimpleProject çözümü açın [1. Bölüm temel proje sistemi oluşturma](../extensibility/creating-a-basic-project-system-part-1.md).  
  
2. İçinde *SimpleProjectPackage.cs* dosya, ProvideProjectFactory öznitelik bulunamadı. Null ile ikinci parametrenin (proje adı) ve dördüncü parametresinin (proje şablonu klasörüne yol) yerine ". \\\NullPath "gibi.  
  
   ```  
   [ProvideProjectFactory(typeof(SimpleProjectFactory), null,  
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",  
       ".\\NullPath",  
   LanguageVsTemplate = "SimpleProject")]  
   ```  
  
3. Adlı bir XML dosyası ekleyin *SimpleProject.vstemplate* için *\\Templates\Projects\SimpleProject\\* klasör.  
  
4. Öğesinin içeriğini değiştirin *SimpleProject.vstemplate* aşağıdaki kod ile.  
  
   ```xml  
   <VSTemplate Version="2.0.0" Type="Project"  
       xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
     <TemplateData>  
       <Name>SimpleProject Application</Name>  
       <Description>  
           A project for creating a SimpleProject application  
        </Description>  
        <Icon>SimpleProject.ico</Icon>  
        <ProjectType>SimpleProject</ProjectType>  
     </TemplateData>  
     <TemplateContent>  
       <Project File="SimpleProject.myproj" ReplaceParameters="true">  
         <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
             Program.cs  
         </ProjectItem>  
         <ProjectItem ReplaceParameters="true" OpenInEditor="false">  
            AssemblyInfo.cs  
         </ProjectItem>  
       </Project>  
     </TemplateContent>  
   </VSTemplate>  
   ```  
  
5. İçinde **özellikleri** penceresinde, seçin tüm beş dosyaları *\\Templates\Projects\SimpleProject\\* klasörü ve kümesi **derleme eylemi** için **ZipProject**.  
  
   ![Basit bir proje klasörü](../extensibility/media/simpproj2.png "SimpProj2")  
  
   \<TemplateData > bölümü, SimpleProject proje türünde görünümünü ve konumunu belirler **yeni proje** iletişim kutusunda, aşağıdaki gibi:  
  
- \<Adı > öğesi adları SimpleProject uygulaması için proje şablonu.  
  
- \<Açıklaması > ögesinin görünen açıklama **yeni proje** proje şablonu seçildiğinde iletişim kutusu.  
  
- \<Simgesi > öğesi SimpleProject proje türü ile birlikte görüntülenen simgeyi belirtir.  
  
- \<ProjectType > öğesi içindeki proje türü adları **yeni proje** iletişim kutusu. Bu ad, proje adı parametresi ProvideProjectFactory özniteliğinin değiştirir.  
  
  > [!NOTE]
  >  \<ProjectType > öğesi eşleşmelidir `LanguageVsTemplate` bağımsız değişkeni `ProvideProjectFactory` SimpleProjectPackage.cs dosya özniteliği.  
  
  \<TemplateContent > bölümü, yeni bir proje oluşturulduğunda, oluşturulan bu dosyaları açıklar:  
  
- *SimpleProject.myproj*  
  
- *Program.cs*  
  
- *AssemblyInfo.cs*  
  
  Üç dosya sahip `ReplaceParameters` parametre değiştirme sağlayan true olarak ayarlayın.  *Program.cs* dosyasının `OpenInEditor` Kod Düzenleyicisi'nde bir proje oluşturulduğunda açılması dosyanın neden true olarak ayarlayın.  
  
  Visual Studio şablon şeması öğeleri hakkında daha fazla bilgi için bkz: [Visual Studio şablon şeması başvurusu](../extensibility/visual-studio-template-schema-reference.md).  
  
> [!NOTE]
>  Bir projenin birden fazla Visual Studio şablon varsa, her ayrı bir klasöre şablonudur. Klasördeki her bir dosya olmalıdır **derleme eylemi** kümesine **ZipProject**.  
  
## <a name="adding-a-minimal-vsct-file"></a>Bir minimal .vsct dosyası ekleme  
 Visual Studio, yeni veya değiştirilmiş bir Visual Studio şablonu tanıyabilmesi için Kurulum modunda çalıştırılmalıdır. Kurulum modunu gerektiren bir *.vsct* mevcut olmasının dosya. Bu nedenle, en az eklemelisiniz *.vsct* projeye dosya.  
  
1.  Adlı bir XML dosyası ekleyin *SimpleProject.vsct* SimpleProject projeye.  
  
2.  Öğesinin içeriğini değiştirin *SimpleProject.vsct* dosyasındaki kodu aşağıdaki kodla.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CommandTable  
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">  
    </CommandTable>  
    ```  
  
3.  Ayarlama **derleme eylemi** bu dosyanın **VSCTCompile**. Yalnızca yapabileceğiniz *.csproj* de dosya **özellikleri** penceresi. Emin olun **derleme eylemi** bu dosya kümesine **hiçbiri** bu noktada.  
  
    1.  SimpleProject düğümüne sağ tıklayın ve ardından **Düzenle SimpleProject.csproj**.  
  
    2.  İçinde *.csproj* bulun, dosya *SimpleProject.vsct* öğesi.  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3.  Derleme eylemi değiştirme **VSCTCompile**.  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4.  Proje dosyası ve düzenleyiciyi kapatın.  
  
    5.  SimpleProject düğümü kaydedin ve sonra da **Çözüm Gezgini** tıklayın **projeyi**.  
  
## <a name="examine-the-visual-studio-template-build-steps"></a>Visual Studio şablon derleme adımları inceleyin  
 VSPackage Proje yapı sistemi, genellikle Visual Studio Kurulum modunda çalıştırır, *.vstemplate* dosya değiştirildiğinde veya projeyi içeren *.vstemplate* dosya yeniden. Normal veya yüksek MSBuild ayrıntı düzeyini ayarlayarak izleyebilirsiniz.  
  
1. Üzerinde **Araçları** menüsünü tıklatın **seçenekleri**.  
  
2. Genişletin **projeler ve çözümler** düğümüne tıklayın ve ardından **derleme ve çalıştırma**.  
  
3. Ayarlama **MSBuild proje oluşturması çıkış ayrıntısı** için **Normal**. **Tamam**'ı tıklatın.  
  
4. SimpleProject projeyi yeniden derleyin.  
  
   Oluşturmak için yapı adımının *.zip* proje dosyası, aşağıdaki örnekte benzemesi gerekir.  
  
```  
ZipProjects:  
1>  Zipping ProjectTemplates  
1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip...  
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip".  
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip".  
1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip  
1>ZipItems:  
1>  Zipping ItemTemplates  
1>  SimpleProject ->  
```  
  
## <a name="deploy-a-visual-studio-template"></a>Visual Studio şablon dağıtma  
 Visual Studio şablonları yol bilgisi içermez. Bu nedenle, şablon *.zip* dosya, Visual Studio için bilinen bir konuma dağıtılmalıdır. Genellikle ProjectTemplates klasörünün konumu olan *< % LOCALAPPDATA % > \Microsoft\VisualStudio\14.0Exp\ProjectTemplates*.  
  
 Proje fabrikanızı dağıtmak için yükleme programını Yönetici ayrıcalıkları olmalıdır. Şablonları Visual Studio yükleme düğümünde dağıtır: *...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates*.  
  
## <a name="test-a-visual-studio-template"></a>Visual Studio şablonu test  
 Visual Studio şablonu kullanarak bir proje hiyerarşisi oluşturur olup olmadığını görmek için proje fabrikanızı test edin.  
  
1. Visual Studio SDK Deneysel örneğini sıfırlama.  
  
    Üzerinde [!INCLUDE[win7](../debugger/includes/win7_md.md)]: üzerinde **Başlat** menüsünde bulmak **Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools** klasöre tıklayın ve ardından **Microsoft Visual Studio Deneysel Sıfırla örnek**.  
  
    Sonraki Windows sürümlerinde: üzerinde **Başlat** ekranında, yazın **Microsoft Visual Studio sıfırlama \<sürüm > deneysel örneğinde**.  
  
2. Bir komut istemi penceresi görüntülenir. Sözcükleri gördüğünüzde **devam etmek için herhangi bir tuşa basın**, tıklayın **ENTER**. Pencere kapandıktan sonra Visual Studio'yu açın.  
  
3. SimpleProject projeyi yeniden derleyin ve hata ayıklamaya başlayın. Deneysel örneği açılır.  
  
4. Deneysel örneğinde bir SimpleProject projesi oluşturun. İçinde **yeni proje** iletişim kutusunda **SimpleProject**.  
  
5. SimpleProject yeni bir örneğini görmeniz gerekir.  
  
   ![Basit bir proje yeni örneği](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")  
  
   ![Yeni Proje Örneğim](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")  
  
## <a name="create-a-project-type-child-node"></a>Bir proje türü alt düğüm oluşturma  
 İçinde bir proje türü düğümü için bir alt düğüm ekleyin **yeni proje** iletişim kutusu.  Örneğin, SimpleProject proje türü için konsol uygulamaları, pencere uygulamaları, web uygulamaları ve benzeri için alt düğümleri olabilir.  
  
 Alt düğümler, proje dosyasını değiştirerek ve ekleyerek oluşturulur \<OutputSubPath > alt öğelere \<ZipProject > öğeleri. Derleme veya dağıtım sırasında bir şablon kopyalandığında, her alt düğümü proje şablonları klasörünün bir alt haline gelir.  
  
 Bu bölümde, bir konsol alt düğümü SimpleProject proje türü için oluşturma işlemi gösterilmektedir.  
  
1.  Yeniden adlandırma *\\Templates\Projects\SimpleProject\\* klasörüne  *\\Templates\Projects\ConsoleApp\\*.  
  
2.  İçinde **özellikleri** penceresinde, seçin tüm beş dosyaları *\\Templates\Projects\ConsoleApp\\* klasörü ve emin **derleme eylemi**ayarlanır **ZipProject**.  
  
3.  SimpleProject.vstemplate dosyanın sonuna aşağıdaki satırı ekleyin \<TemplateData > bölümü, kapanış etiketinin hemen önce.  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     Bu hem de konsol alt düğüm alt düğüm bir düzeyin SimpleProject üst düğümündeki görünmesini konsol uygulaması şablonu neden olur.  
  
4.  Kaydet *SimpleProject.vstemplate* dosya.  
  
5.  İçinde *.csproj* ekleyin \<OutputSubPath > ZipProject öğelerin her biri için. Önce olarak da projeyi kaldırmak ve proje dosyasını düzenleyin.  
  
6.  Bulun \<ZipProject > öğeleri. Her \<ZipProject > öğesini ekleyin bir \<OutputSubPath > öğesi ve bu değeri konsol verin. ZipProject  
  
    ```  
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>   
        <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico">  
          <OutputSubPath>Console</OutputSubPath>  
        </ZipProject>  
    ```  
  
7.  Bu ekleme \<PropertyGroup > Proje dosyasına:  
  
    ```  
    <PropertyGroup>  
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>  
    </PropertyGroup>  
    ```  
  
8.  Proje dosyasını kaydedin ve projeyi yeniden yükleyin.  
  
## <a name="test-the-project-type-child-node"></a>Test proje türü alt düğümü  
 Değiştirilen proje dosyasını görmek için test olmadığını **konsol** alt düğüm görünür **yeni proje** iletişim kutusu.  
  
1. Çalıştırma **Microsoft Visual Studio Deneysel örneğini sıfırlama** aracı.  
  
2. SimpleProject projeyi yeniden derleyin ve hata ayıklamaya başlayın. Deneysel örneği görünmelidir  
  
3. İçinde **yeni proje** iletişim kutusunda, tıklayın **SimpleProject** düğümü. **Konsol uygulaması** şablon görüntülenmedir **şablonları** bölmesi.  
  
4. Genişletin **SimpleProject** düğümü. **Konsol** alt düğüm görüntülenmelidir. **SimpleProject uygulama** şablon devam görünmesini **şablonları** bölmesi.  
  
5. Tıklayın **iptal** ve hata ayıklamayı durdurun.  
  
   ![Basit bir proje paketi](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")  
  
   ![Basit bir proje konsol düğümü](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")  
  
## <a name="substitute-project-template-parameters"></a>Proje şablonu parametreleri değiştirin  
 [Temel Proje sistemi oluşturma, bölüm 1](../extensibility/creating-a-basic-project-system-part-1.md) üzerine gösterildi `ProjectNode.AddFileFromTemplate` temel türde bir şablon parametre değiştirme yapmak için yöntemi. Bu bölümde daha karmaşık Visual Studio şablon parametreleri kullanmayı öğretir.  
  
 Bir Visual Studio şablonu kullanarak bir proje oluşturduğunuzda **yeni proje** iletişim kutusu, Parametreler yerine şablon dizeleri projenin özelleştirilmesi için. Şablon parametresi başlar ve bir dolar işareti, örneğin, $time$ biten özel bir belirteçtir. Aşağıdaki iki parametreyi şablonu temel alan projelerinde özelleştirme etkinleştirmek için kullanışlıdır:  
  
- 1-10 $GUID$ yeni GUID ile değiştirilir. En fazla 10 benzersiz GUID'ler, örneğin, guid1 $$ belirtebilirsiniz.  
  
- $safeprojectname$, bir kullanıcı tarafından sağlanan adıdır **yeni proje** iletişim kutusu, tüm güvenli olmayan karakterleri ve boşlukları kaldırmak için değiştirildi.  
  
  Şablon parametreleri tam bir listesi için bkz. [şablon parametreleri](../ide/template-parameters.md).  
  
### <a name="to-substitute-project-template-parameters"></a>Proje şablonu parametreleri değiştirmek için  
  
1.  İçinde *SimpleProjectNode.cs* dosya, kaldırma `AddFileFromTemplate` yöntemi.  
  
2.  İçinde  *\\Templates\Projects\ConsoleApp\SimpleProject.myproj* bulun, dosya \<RootNamespace > özelliği ve değerini $safeprojectname$ olarak değiştirin.  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3.  İçinde  *\\Templates\Projects\SimpleProject\Program.cs* dosyasında, dosyanın içeriğini aşağıdaki kodla değiştirin:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Runtime.InteropServices;    // Guid  
  
    namespace $safeprojectname$  
    {  
        [Guid("$guid1$")]  
        public class $safeprojectname$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
4.  SimpleProject projeyi yeniden derleyin ve hata ayıklamaya başlayın. Deneysel örneği görüntülenmesi gerekir.  
  
5.  Yeni bir SimpleProject konsol uygulaması oluşturun. (İçinde **proje türleri** bölmesinde **SimpleProject**. Altında **Visual Studio yüklenmiş şablonlar**seçin **konsol uygulaması**.)  
  
6.  Yeni oluşturulan projeyi açın *Program.cs*. Aşağıdaki gibi görünmelidir (dosyanızdaki GUID değerleri, farklı.):  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using System.Runtime.InteropServices;    // Guid  
  
    namespace Console_Application1  
    {  
        [Guid("00000000-0000-0000-00000000-00000000)"]  
        public class Console_Application1  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
## <a name="creatr-a-project-property-page"></a>Creatr proje özellik sayfası  
 Böylece kullanıcıların görüntüleyebileceği ve projelerinde, şablonunuzu temel alan özelliklerini değiştirmek, proje türü için özellik sayfası oluşturabilirsiniz. Bu bölümde bağımsız yapılandırma özellik sayfası oluşturma işlemini gösterir. Bu temel özellik sayfası özellikler Kılavuzu, özellik sayfası sınıfının içinde kullanıma sunan genel özelliklerini görüntülemek için kullanır.  
  
 Özellik sayfasında sınıfından türetilir `SettingsPage` temel sınıfı. Tarafından sağlanan özellikler Kılavuzu `SettingsPage` sınıfı en temel veri türlerini farkındadır ve bunları görüntülemek nasıl bilir.  Ayrıca, `SettingsPage` sınıfı özellik değerleri proje dosyasına kalıcı hale getirmek nasıl bilir.  
  
 Bu bölümde oluşturduğunuz özellik sayfasını, alter ve bu proje özelliklerini kaydetmek olanak sağlar:  
  
-   AssemblyName  
  
-   OutputType  
  
-   RootNamespace.  
  
1. İçinde *SimpleProjectPackage.cs* bu ekleyin `ProvideObject` özniteliğini `SimpleProjectPackage` sınıfı:  
  
   ```  
   [ProvideObject(typeof(GeneralPropertyPage))]  
   public sealed class SimpleProjectPackage : ProjectPackage  
   ```  
  
    Bu özellik sayfası sınıfının kaydeder `GeneralPropertyPage` com ile  
  
2. İçinde *SimpleProjectNode.cs* dosya, bu iki geçersiz kılınan yöntemler uygun `SimpleProjectNode` sınıfı:  
  
   ```csharp  
   protected override Guid[] GetConfigurationIndependentPropertyPages()  
   {  
       Guid[] result = new Guid[1];  
       result[0] = typeof(GeneralPropertyPage).GUID;  
       return result;  
   }  
   protected override Guid[] GetPriorityProjectDesignerPages()  
   {  
       Guid[] result = new Guid[1];  
       result[0] = typeof(GeneralPropertyPage).GUID;  
        return result;  
   }  
   ```  
  
    Bu yöntemlerin ikisi de, GUID'leri özellik sayfasının bir dizi döndürür.  GeneralPropertyPage GUID, dizi içindeki tek öğe ise böylece **özellik sayfaları** iletişim kutusu, yalnızca bir sayfa gösterilir.  
  
3. Adlı bir sınıf dosyası ekleyin *GeneralPropertyPage.cs* SimpleProject projeye.  
  
4. Bu dosyanın içeriğini aşağıdaki kodla değiştirin:  
  
   ```csharp  
   using System;  
   using System.Runtime.InteropServices;  
   using Microsoft.VisualStudio;  
   using Microsoft.VisualStudio.Project;  
   using System.ComponentModel;  
  
   namespace SimpleProject  
   {  
       [ComVisible(true)]  
       [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")]  
       public class GeneralPropertyPage : SettingsPage  
       {  
           private string assemblyName;  
           private OutputType outputType;  
           private string defaultNamespace;  
  
           public GeneralPropertyPage()  
           {  
               this.Name = "General";  
           }  
  
           [Category("AssemblyName")]  
           [DisplayName("AssemblyName")]  
           [Description("The output file holding assembly metadata.")]  
           public string AssemblyName  
           {  
               get { return this.assemblyName; }  
           }  
           [Category("Application")]  
           [DisplayName("OutputType")]  
           [Description("The type of application to build.")]  
           public OutputType OutputType  
           {  
               get { return this.outputType; }  
               set { this.outputType = value; this.IsDirty = true; }  
           }  
           [Category("Application")]  
           [DisplayName("DefaultNamespace")]  
           [Description("Specifies the default namespace for added items.")]  
           public string DefaultNamespace  
           {  
               get { return this.defaultNamespace; }  
               set { this.defaultNamespace = value; this.IsDirty = true; }  
           }  
  
           protected override void BindProperties()  
           {  
               this.assemblyName = this.ProjectMgr.GetProjectProperty(  
   "AssemblyName", true);  
               this.defaultNamespace = this.ProjectMgr.GetProjectProperty(  
   "RootNamespace", false);  
  
               string outputType = this.ProjectMgr.GetProjectProperty(  
   "OutputType", false);  
               this.outputType =   
   (OutputType)Enum.Parse(typeof(OutputType), outputType);  
           }  
  
           protected override int ApplyChanges()  
           {  
               this.ProjectMgr.SetProjectProperty(  
   "AssemblyName", this.assemblyName);  
               this.ProjectMgr.SetProjectProperty(  
   "OutputType", this.outputType.ToString());  
               this.ProjectMgr.SetProjectProperty(  
   "RootNamespace", this.defaultNamespace);  
               this.IsDirty = false;  
  
               return VSConstants.S_OK;  
           }  
       }  
   }  
   ```  
  
    `GeneralPropertyPage` Sınıfı AssemblyName, OutputType ve RootNamespace üç genel özelliklerini gösterir. Set metodu yok AssemblyName sahip olduğundan, bu salt okunur bir özellik olarak görüntülenir. OutputType numaralandırılmış bir sabit olduğundan, açılan liste olarak görünür.  
  
    `SettingsPage` Taban sınıfı sağlar `ProjectMgr` özelliklerini kalıcı hale getirmek için. `BindProperties` Yöntemi kullanan `ProjectMgr` kalıcı özellik değerlerini almak ve ilgili özellikleri ayarlayın.  `ApplyChanges` Yöntemi kullanan `ProjectMgr` özelliklerin değerlerini almak ve bunları proje dosyasına kalıcı hale getirmek için. Özelliği ayarlanmış yöntemi kümeleri `IsDirty` özelliklerini kalıcı olduğunu belirtmek için true.  Kalıcılık, proje veya çözüm kaydettiğinizde gerçekleşir.  
  
5. SimpleProject çözümü yeniden oluşturun ve hata ayıklamaya başlayın. Deneysel örneği görüntülenmesi gerekir.  
  
6. Deneysel örneğinde yeni bir SimpleProject uygulaması oluşturun.  
  
7. Visual Studio, Visual Studio şablonu kullanarak bir proje oluşturmak için proje fabrikanızı çağırır. Yeni *Program.cs* dosyası Kod Düzenleyicisi'nde açılır.  
  
8. ' Nde proje düğümüne sağ **Çözüm Gezgini**ve ardından **özellikleri**. **Özellik sayfaları** iletişim kutusu görüntülenir.  
  
   ![Basit bir proje özellik sayfası](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")  
  
## <a name="test-the-project-property-page"></a>Test projesi özellik sayfası
 Artık değiştirebilir ve özellik değerlerini değiştirmek olup olmadığını sınayabilirsiniz.  
  
1. İçinde **KonsolUygulamam özellik sayfaları** iletişim kutusunda, değişiklik **DefaultNamespace** için **MyApplication**.  
  
2. Seçin **OutputType** özelliği tıklayın ve ardından **sınıf kitaplığı**.  
  
3. Tıklayın **Uygula**ve ardından **Tamam**.  
  
4. Yeniden **özellik sayfaları** iletişim kutusu ve yaptığınız değişiklikleri kalıcı olun.  
  
5. Visual Studio'nun deneysel örneği kapatın.  
  
6. Deneysel örneğinde yeniden açın.  
  
7. Yeniden **özellik sayfaları** iletişim kutusu ve yaptığınız değişiklikleri kalıcı olun.  
  
8. Visual Studio'nun deneysel örneği kapatın.  
  
   ![Deneysel örneği kapatın](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")