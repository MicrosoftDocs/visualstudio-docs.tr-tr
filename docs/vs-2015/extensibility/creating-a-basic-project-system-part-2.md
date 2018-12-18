---
title: Temel Proje sistemi oluşturma, bölüm 2 | Microsoft Docs
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
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 98cdcf426f2aeeb794e9e33754108c792f9725e5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753972"
---
# <a name="creating-a-basic-project-system-part-2"></a>Temel Proje Sistemi Oluşturma, Bölüm 2
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu serideki ilk izlenecek [1. bölüm bir temel proje sistemi oluşturma](../extensibility/creating-a-basic-project-system-part-1.md), temel proje sistemi oluşturma işlemi gösterilmektedir. Bu izlenecek yol, Visual Studio şablonu, bir özellik sayfası ve diğer özellikleri ekleyerek üzerinde temel proje sistemi oluşturur. Bu bir başlamadan önce ilk izlenecek yolu tamamlamanız gerekir.  
  
 Bu izlenecek yol, proje dosya adı uzantısı .myproj olan bir proje türü oluşturmak öğretir. İzlenecek yolu tamamlamak için izlenecek yol, mevcut Visual C# proje sistemi çözümümüz kendi dilinize oluşturulamıyor gerekmez.  
  
 Bu izlenecek yol aşağıdaki görevlerin nasıl yerine getirileceğini öğretir:  
  
-   Visual Studio şablonu oluşturun.  
  
-   Visual Studio şablonu dağıtın.  
  
-   Bir proje türü alt düğüm oluşturma **yeni proje** iletişim kutusu.  
  
-   Parametre değiştirme Visual Studio şablonunda etkinleştirin.  
  
-   Proje özellik sayfası oluşturun.  
  
> [!NOTE]
>  Bu kılavuzda açıklanan adımları bir C# projesini temel alıyor. Ancak, dosya adı uzantıları ve kod gibi özellikleri dışında bir Visual Basic projesi için aynı adımları kullanabilirsiniz.  
  
## <a name="creating-a-visual-studio-template"></a>Visual Studio şablon oluşturma  
 [1. bölüm bir temel proje sistemi oluşturma](../extensibility/creating-a-basic-project-system-part-1.md) temel proje şablonu oluşturma ve proje sisteme ekleme işlemi gösterilmektedir. Ayrıca bu şablonu kullanarak Visual Studio ile kaydetme işlemini gösterir <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> \Templates\Projects\SimpleProject\ klasörün tam yolunu sistem kayıt defterine yazma özniteliği.  
  
 Visual Studio şablonu (.vstemplate dosyası) yerine temel proje şablonunu kullanarak, şablonun nasıl görünür denetleyebilirsiniz **yeni proje** iletişim kutusu ve şablon parametreleri nasıl yerini alır.  .Vstemplate dosyası kaynak dosyaları proje sistemi şablonunu kullanarak bir proje oluşturulduğunda, dahil edilecek şeklini tanımlayan bir XML dosyasıdır. Proje sistemi, .vstemplate dosyası ve bir .zip dosyası kaynak dosyalarında toplayarak oluşturulan ve Visual Studio için bilinen bir konuma .zip dosyasını kopyalayarak dağıtılabilir. Bu işlem, bu kılavuzda daha sonra daha ayrıntılı açıklanmıştır.  
  
1. İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], izleyerek oluşturduğunuz SimpleProject çözümü açın [1. bölüm bir temel proje sistemi oluşturma](../extensibility/creating-a-basic-project-system-part-1.md).  
  
2. SimpleProjectPackage.cs dosyasında ProvideProjectFactory öznitelik bulunamadı. Null ile ikinci parametrenin (proje adı) ve dördüncü parametresinin (proje şablonu klasörüne yol) yerine ". \\\NullPath "gibi.  
  
   ```  
   [ProvideProjectFactory(typeof(SimpleProjectFactory), null,  
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",  
       ".\\NullPath",  
   LanguageVsTemplate = "SimpleProject")]  
   ```  
  
3. SimpleProject.vstemplate \Templates\Projects\SimpleProject\ klasöre adlı bir XML dosyası ekleyin.  
  
4. SimpleProject.vstemplate içeriğini aşağıdaki kodla değiştirin.  
  
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
  
5. İçinde **özellikleri** penceresinde, seçin tüm beş dosyaları kümesi ve \Templates\Projects\SimpleProject\ klasörü içinde **derleme eylemi** için **ZipProject**.  
  
   ![](../extensibility/media/simpproj2.png "SimpProj2")  
  
   \<TemplateData > bölümü, SimpleProject proje türünde görünümünü ve konumunu belirler **yeni proje** iletişim kutusunda, aşağıdaki gibi:  
  
- \<Adı > öğesi adları SimpleProject uygulaması için proje şablonu.  
  
- \<Açıklaması > ögesinin görünen açıklama **yeni proje** proje şablonu seçildiğinde iletişim kutusu.  
  
- \<Simgesi > öğesi SimpleProject proje türü ile birlikte görüntülenen simgeyi belirtir.  
  
- \<ProjectType > öğesi içindeki proje türü adları **yeni proje** iletişim kutusu. Bu ad, proje adı parametresi ProvideProjectFactory özniteliğinin değiştirir.  
  
  > [!NOTE]
  >  \<ProjectType > öğesi eşleşmelidir `LanguageVsTemplate` bağımsız değişkeni `ProvideProjectFactory` SimpleProjectPackage.cs dosya özniteliği.  
  
  \<TemplateContent > bölümü, yeni bir proje oluşturulduğunda, oluşturulan bu dosyaları açıklar:  
  
- SimpleProject.myproj  
  
- Program.cs  
  
- AssemblyInfo.cs  
  
  Üç dosya sahip `ReplaceParameters` parametre değiştirme sağlayan true olarak ayarlayın.  Program.cs dosyasının `OpenInEditor` Kod Düzenleyicisi'nde bir proje oluşturulduğunda açılması dosyanın neden true olarak ayarlayın.  
  
  Visual Studio şablon şeması öğeleri hakkında daha fazla bilgi için bkz: [Visual Studio şablon şeması başvurusu](../extensibility/visual-studio-template-schema-reference.md).  
  
> [!NOTE]
>  Bir projenin birden fazla Visual Studio şablon varsa, her ayrı bir klasöre şablonudur. Klasördeki her bir dosya olmalıdır **derleme eylemi** kümesine **ZipProject**.  
  
## <a name="adding-a-minimal-vsct-file"></a>Bir Minimal .vsct dosyası ekleme  
 Visual Studio, yeni veya değiştirilmiş bir Visual Studio şablonu tanıyabilmesi için Kurulum modunda çalıştırılmalıdır. Kurulum modu .vsct dosyası mevcut olmasını gerektirir. Bu nedenle, en az .vsct dosyası projeye eklemeniz gerekir.  
  
1.  SimpleProject.vsct SimpleProject projeye adlı bir XML dosyası ekleyin.  
  
2.  SimpleProject.vsct dosyasının içeriğini aşağıdaki kodla değiştirin.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CommandTable  
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">  
    </CommandTable>  
    ```  
  
3.  Ayarlama **derleme eylemi** bu dosyanın **VSCTCompile**. Bu .csproj dosyasında yalnızca de yapabilirsiniz **özellikleri** penceresi. Emin olun **derleme eylemi** bu dosya kümesine **hiçbiri** bu noktada.  
  
    1.  SimpleProject düğümüne sağ tıklayın ve ardından **Düzenle SimpleProject.csproj**.  
  
    2.  .Csproj dosyasında SimpleProject.vsct öğeyi bulun.  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3.  Derleme eylemi değiştirme **VSCTCompile**.  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4.  Proje dosyası ve düzenleyiciyi kapatın.  
  
    5.  SimpleProject düğümü kaydedin ve sonra da **Çözüm Gezgini** tıklayın **projeyi**.  
  
## <a name="examining-the-visual-studio-template-build-steps"></a>Visual Studio şablon derleme adımlarını İnceleme  
 VSPackage Proje yapı sistemi genellikle Visual Studio Kurulum modunda .vstemplate dosyası değiştirildiğinde veya .vstemplate dosyasını içeren proje yeniden çalıştırır. Normal veya yüksek MSBuild ayrıntı düzeyini ayarlayarak izleyebilirsiniz.  
  
1. Üzerinde **Araçları** menüsünü tıklatın **seçenekleri**.  
  
2. Genişletin **projeler ve çözümler** düğümüne tıklayın ve ardından **derleme ve çalıştırma**.  
  
3. Ayarlama **MSBuild proje oluşturması çıkış ayrıntısı** için **Normal**. **Tamam**'ı tıklatın.  
  
4. SimpleProject projeyi yeniden derleyin.  
  
   Yapı adımının .zip proje dosyası oluşturmak için aşağıdaki örneğe benzer olmalıdır.  
  
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
  
## <a name="deploying-a-visual-studio-template"></a>Visual Studio şablonu dağıtma  
 Visual Studio şablonları yol bilgisi içermez. Bu nedenle, şablon .zip dosyasını Visual Studio'da bilinen bir konuma dağıtılması gerekir. Genellikle ProjectTemplates klasörünün konumu olan  **\<% LOCALAPPDATA % > \Microsoft\VisualStudio\14.0Exp\ProjectTemplates**.  
  
 Proje fabrikanızı dağıtmak için yükleme programını Yönetici ayrıcalıkları olmalıdır. Şablonları Visual Studio yükleme düğümünde dağıtır: **...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates**.  
  
## <a name="testing-a-visual-studio-template"></a>Visual Studio şablon testi  
 Visual Studio şablonu kullanarak bir proje hiyerarşisi oluşturur olup olmadığını görmek için proje fabrikanızı test edin.  
  
1. Visual Studio SDK Deneysel örneğini sıfırlama.  
  
    Üzerinde [!INCLUDE[win7](../includes/win7-md.md)]: Başlat menüsünde bulma **Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools** klasöre tıklayın ve ardından **Microsoft Visual Studio Deneysel örneğini sıfırlama**.  
  
    Sonraki Windows sürümlerinde: Başlangıç ekranında, türü **Microsoft Visual Studio sıfırlama \<sürüm > deneysel örneğinde**.  
  
2. Bir komut istemi penceresi görüntülenir. Sözcükleri gördüğünüzde `Press any key to continue`, ENTER'ı tıklatın. Pencere kapandıktan sonra Visual Studio'yu açın.  
  
3. SimpleProject projeyi yeniden derleyin ve hata ayıklamaya başlayın. Deneysel örneği açılır.  
  
4. Deneysel örneğinde bir SimpleProject projesi oluşturun. İçinde **yeni proje** iletişim kutusunda **SimpleProject**.  
  
5. SimpleProject yeni bir örneğini görmeniz gerekir.  
  
   ![](../extensibility/media/simpproj2-newproj.png "SimpProj2_NewProj")  
  
   ![](../extensibility/media/simpproj2-myproj.png "SimpProj2_MyProj")  
  
## <a name="creating-a-project-type-child-node"></a>Bir proje türü alt düğüm oluşturma  
 İçinde bir proje türü düğümü için bir alt düğüm ekleyin **yeni proje** iletişim kutusu.  Örneğin, SimpleProject proje türü için konsol uygulamaları, pencere uygulamaları, web uygulamaları ve benzeri için alt düğümleri olabilir.  
  
 Alt düğümler, proje dosyasını değiştirerek ve ekleyerek oluşturulur \<OutputSubPath > alt öğelere \<ZipProject > öğeleri. Derleme veya dağıtım sırasında bir şablon kopyalandığında, her alt düğümü proje şablonları klasörünün bir alt haline gelir.  
  
 Bu bölümde, bir konsol alt düğümü SimpleProject proje türü için oluşturma işlemi gösterilmektedir.  
  
1.  \Templates\Projects\SimpleProject\ klasörü yeniden adlandırmak için \Templates\Projects\ConsoleApp\\.  
  
2.  İçinde **özellikleri** penceresinde \Templates\Projects\ConsoleApp\ klasördeki tüm beş dosyayı seçin ve emin **derleme eylemi** ayarlanır **ZipProject**.  
  
3.  SimpleProject.vstemplate dosyanın sonuna aşağıdaki satırı ekleyin \<TemplateData > bölümü, kapanış etiketinin hemen önce.  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     Bu hem de konsol alt düğüm alt düğüm bir düzeyin SimpleProject üst düğümündeki görünmesini konsol uygulaması şablonu neden olur.  
  
4.  SimpleProject.vstemplate dosyayı kaydedin.  
  
5.  .Csproj dosyasında, ekleme \<OutputSubPath > ZipProject öğelerin her biri için. Önce olarak da projeyi kaldırmak ve proje dosyasını düzenleyin.  
  
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
  
## <a name="testing-the-project-type-child-node"></a>Proje türü alt düğüm sınaması  
 Değiştirilen proje dosyasını görmek için test olmadığını **konsol** alt düğüm görünür **yeni proje** iletişim kutusu.  
  
1. Çalıştırma **Microsoft Visual Studio Deneysel örneğini sıfırlama** aracı.  
  
2. SimpleProject projeyi yeniden derleyin ve hata ayıklamaya başlayın. Deneysel örneği görünmelidir  
  
3. İçinde **yeni proje** iletişim kutusunda, tıklayın **SimpleProject** düğümü. **Konsol uygulaması** şablon görüntülenmedir **şablonları** bölmesi.  
  
4. Genişletin **SimpleProject** düğümü. **Konsol** alt düğüm görüntülenmelidir. **SimpleProject uygulama** şablon devam görünmesini **şablonları** bölmesi.  
  
5. biçimindeki telefon numarasıdır. Tıklayın **iptal** ve hata ayıklamayı Durdur  
  
   ![](../extensibility/media/simpproj2-rollup.png "SimpProj2_Rollup")  
  
   ![](../extensibility/media/simpproj2-subfolder.png "SimpProj2_Subfolder")  
  
## <a name="substituting-project-template-parameters"></a>Proje şablonu parametrelerini değiştirme  
 [1. bölüm bir temel proje sistemi oluşturma](../extensibility/creating-a-basic-project-system-part-1.md) üzerine gösterildi `ProjectNode.AddFileFromTemplate` temel türde bir şablon parametre değiştirme yapmak için yöntemi. Bu bölümde daha karmaşık Visual Studio şablon parametreleri kullanmayı öğretir.  
  
 Bir Visual Studio şablonu kullanarak bir proje oluşturduğunuzda **yeni proje** iletişim kutusu, Parametreler yerine şablon dizeleri projenin özelleştirilmesi için. Şablon parametresi başlar ve bir dolar işareti, örneğin, $time$ biten özel bir belirteçtir. Aşağıdaki iki parametreyi şablonu temel alan projelerinde özelleştirme etkinleştirmek için kullanışlıdır:  
  
- 1-10 $GUID$ yeni GUID ile değiştirilir. En fazla 10 benzersiz GUID'ler, örneğin, guid1 $$ belirtebilirsiniz.  
  
- $safeprojectname$, bir kullanıcı tarafından sağlanan adıdır **yeni proje** iletişim kutusu, tüm güvenli olmayan karakterleri ve boşlukları kaldırmak için değiştirildi.  
  
  Şablon parametreleri tam bir listesi için bkz. [şablon parametreleri](../ide/template-parameters.md).  Kendi özel bir şablon parametresi oluşturmak istiyorsanız, bkz. [NIB: nasıl yapılır: özel parametreleri geçirmek şablonlarına](http://msdn.microsoft.com/en-us/5bc2ad11-84c7-4683-a276-e5e00d85d8fb).  
  
#### <a name="to-substitute-project-template-parameters"></a>Proje şablonu parametreleri değiştirmek için  
  
1.  SimpleProjectNode.cs dosyasında kaldırın `AddFileFromTemplate` yöntemi.  
  
2.  \Templates\Projects\ConsoleApp\SimpleProject.myproj dosyasında \<RootNamespace > özelliği ve değerini $safeprojectname$ olarak değiştirin.  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3.  \Templates\Projects\SimpleProject\Program.cs dosyasında, dosyanın içeriğini aşağıdaki kodla değiştirin:  
  
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
  
6.  Yeni oluşturulan projeye, program.cs dosyasını açın. Aşağıdaki gibi görünmelidir (dosyanızdaki GUID değerleri, farklı.):  
  
    ```  
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
  
## <a name="creating-a-project-property-page"></a>Proje özellik sayfası oluşturma  
 Böylece kullanıcıların görüntüleyebileceği ve projelerinde, şablonunuzu temel alan özelliklerini değiştirmek, proje türü için özellik sayfası oluşturabilirsiniz. Bu bölümde bağımsız yapılandırma özellik sayfası oluşturma işlemini gösterir. Bu temel özellik sayfası özellikler Kılavuzu, özellik sayfası sınıfının içinde kullanıma sunan genel özelliklerini görüntülemek için kullanır.  
  
 Özellik sayfasında sınıfından türetilir `SettingsPage` temel sınıfı. Tarafından sağlanan özellikler Kılavuzu `SettingsPage` sınıfı en temel veri türlerini farkındadır ve bunları görüntülemek nasıl bilir.  Ayrıca, `SettingsPage` sınıfı özellik değerleri proje dosyasına kalıcı hale getirmek nasıl bilir.  
  
 Bu bölümde oluşturduğunuz özellik sayfasını, alter ve bu proje özelliklerini kaydetmek olanak sağlar:  
  
-   AssemblyName  
  
-   OutputType  
  
-   RootNamespace.  
  
1. Bu SimpleProjectPackage.cs dosyasına ekleyin `ProvideObject` özniteliğini `SimpleProjectPackage` sınıfı:  
  
   ```  
   [ProvideObject(typeof(GeneralPropertyPage))]  
   public sealed class SimpleProjectPackage : ProjectPackage  
   ```  
  
    Bu özellik sayfası sınıfının kaydeder `GeneralPropertyPage` com ile  
  
2. Bu iki geçersiz kılınan yöntemlerin SimpleProjectNode.cs dosyasına ekleyin `SimpleProjectNode` sınıfı:  
  
   ```  
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
  
3. GeneralPropertyPage.cs SimpleProject projeye adlı bir sınıf dosyası ekleyin.  
  
4. Bu dosyanın içeriğini aşağıdaki kodla değiştirin:  
  
   ```  
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
  
7. Visual Studio, Visual Studio şablonu kullanarak bir proje oluşturmak için proje fabrikanızı çağırır. Yeni Program.cs dosyasını Kod düzenleyicisinde açılır.  
  
8. ' Nde proje düğümüne sağ **Çözüm Gezgini**ve ardından **özellikleri**. **Özellik sayfaları** iletişim kutusu görüntülenir.  
  
   ![](../extensibility/media/simpproj2-proppage.png "SimpProj2_PropPage")  
  
## <a name="testing-the-project-property-page"></a>Proje özellik sayfasını test etme  
 Artık değiştirebilir ve özellik değerlerini değiştirmek olup olmadığını sınayabilirsiniz.  
  
1. İçinde **KonsolUygulamam özellik sayfaları** iletişim kutusunda, değişiklik **DefaultNamespace** için **MyApplication**.  
  
2. Seçin **OutputType** özelliği tıklayın ve ardından **sınıf kitaplığı**.  
  
3. Tıklayın **Uygula**ve ardından **Tamam**.  
  
4. Yeniden **özellik sayfaları** iletişim kutusu ve yaptığınız değişiklikleri kalıcı olun.  
  
5. Visual Studio'nun deneysel örneği kapatın.  
  
6. Deneysel örneğinde yeniden açın.  
  
7. Yeniden **özellik sayfaları** iletişim kutusu ve yaptığınız değişiklikleri kalıcı olun.  
  
8. Visual Studio'nun deneysel örneği kapatın.  
  
   ![](../extensibility/media/simpproj2-proppage2.png "SimpProj2_PropPage2")

