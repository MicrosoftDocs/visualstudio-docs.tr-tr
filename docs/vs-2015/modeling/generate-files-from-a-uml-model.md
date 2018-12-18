---
title: Bir UML modelinden dosyalar oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, generating files
ms.assetid: 4e28b0e6-ce8f-45ee-9e3a-e4d600a0ad81
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: afbb81a67d8d5f8f587979ab8adca4251562072a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51804553"
---
# <a name="generate-files-from-a-uml-model"></a>UML modeli aracılığıyla dosya oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir UML modelinden, program kodu, şemalar, belgelerin, kaynakları ve diğer yapılara hiçbir türde oluşturabilirsiniz. Bir UML modelinden metin dosyaları oluşturma kullanışlı bir yöntem ise [metin şablonlarını](../modeling/code-generation-and-t4-text-templates.md). Bu, program kodu içinde oluşturmak istediğiniz metni ekleme olanak tanır.  
  
 Başlıca üç senaryo vardır:  
  
- [Bir menü komut dosyaları oluşturma](#Command) veya hareket. Tanımladığınız bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] UML modellerinde kullanılabilir komutu.  
  
- [Dosyaları dosyasından bir uygulama oluşturma](#Application). UML modellerini okur ve dosyaları oluşturan bir uygulama yazmanız.  
  
- [Tasarım zamanında oluşturma](#Design). Uygulamanızın işlevselliğini bir kısmını tanımlamak için bir modeli kullanır ve kod, kaynak ve benzeri içinde oluşturmak, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözüm.  
  
  Bu konu hakkında ayrıntılı bilgi ile sona erer [metin oluşturma kullanmayı](#What). Daha fazla bilgi için [kod oluşturma ve T4 metin şablonları](../modeling/code-generation-and-t4-text-templates.md).  
  
##  <a name="Command"></a> Bir menü komut dosyaları oluşturma  
 Kullanabileceğiniz bir UML menü komutu metin şablonlarında önceden işlenir. Metin şablonunun veya ayrı bir kısmi sınıf içindeki kod, diyagram tarafından görüntülenen model okuyabilirsiniz.  
  
 Bu özellikler hakkında daha fazla bilgi için aşağıdaki konuları okuyun:  
  
- [Modelleme diyagramında menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)  
  
- [T4 Metin Şablonları İle Çalışma Süresi Metni Oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md)  
  
- [UML modelinde gezinme](../modeling/navigate-the-uml-model.md)  
  
  Aşağıdaki örnekte gösterilen yaklaşım işlem modeli diyagramları birinden başlattığınızda, metin tek bir modelden oluşturmak için uygundur. Ayrı bir bağlamda modeli işlemek için kullanmayı [Visual Studio Modelbus'ı](../modeling/integrate-uml-models-with-other-models-and-tools.md) modeli ve onun öğelerine erişmek için.  
  
### <a name="example"></a>Örnek  
 Bu örneği çalıştırmak için oluşturun bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısı (VSIX) projesi. Bu örnekte kullanılan proje adı `VdmGenerator`. İçinde **source.extension.vsixmanifest** dosyasına sağ tıklayıp **İçerik Ekle** ve tür alanı kümesine **MEF Bileşeni** ve geçerli projeye başvuran kaynak yolu. Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz. [modelleme diyagramında menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
 Aşağıdaki kodu içeren C# dosyası projeye ekleyin. Bu sınıf, bir UML sınıf diyagramında görünür bir menü komutu tanımlar.  
  
```  
using System;  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace VdmGenerator  
{  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  public class GenerateVdmFromClasses : ICommandExtension  
  {  
    [Import] public IDiagramContext DiagramContext { get; set; }  
    public void Execute(IMenuCommand command)  
    {  
      // Initialize the template with the Model Store.  
      VdmGen generator = new VdmGen(  
             DiagramContext.CurrentDiagram.ModelStore);  
      // Generate the text and write it.  
      System.IO.File.WriteAllText  
        (System.IO.Path.Combine(  
            Environment.GetFolderPath(  
                Environment.SpecialFolder.Desktop),  
            "Generated.txt")   
         , generator.TransformText());  
    }  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Enabled = command.Visible = true;  
    }  
    public string Text  
    { get { return "Generate VDM"; } }  
  }  
}  
```  
  
 Metin şablonu dosyasıdır. Bu modeldeki her UML sınıfı için metin satırı yanı sıra, her bir sınıf içindeki her bir öznitelik için bir satır oluşturur. Kod modeli tarafından ayrılmış metin gömüldüğü okumak için `<# ... #>`.  
  
 Bu dosyayı oluşturmak için Çözüm Gezgini'nde projeye sağ tıklatın, **Ekle**ve ardından **yeni öğe**. Seçin **önceden işlenmiş metin şablonu**. Bu örnek için dosya adı olmalıdır **VdmGen.tt**. **Özel araç** dosyasının özelliği olmalıdır **TextTemplatingFilePreprocessor**. Önceden işlenmiş metin şablonları hakkında daha fazla bilgi için bkz. [T4 metin şablonları ile çalışma süresi metni oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
```  
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>  
<#   
   foreach (IClass classElement in store.AllInstances<IClass>())   {  
#>  
Type <#= classElement.Name #> ::  
<#  
     foreach (IProperty attribute in classElement.OwnedAttributes)     {  
#>  
       <#= attribute.Name #> : <#=   
           attribute.Type == null ? ""  
                                  : attribute.Type.Name #>   
<#  
     }   }  
#>  
```  
  
 Metin şablonunun parçası olan bir C# kısmi sınıf oluşturur, uygulamanızın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proje. Ayrı bir dosyada aynı sınıfın başka bir partial bildirimi ekleyin. Bu kod, UML model deposu erişimi olan şablon sağlar:  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
namespace VdmGenerator  
{  
    public partial class VdmGen  
    {  
        private IModelStore store;  
        public VdmGen(IModelStore s)  
        { store = s; }  
    }  
}  
```  
  
 Projeyi test etmek için basın **F5**. Yeni bir örneğini [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] başlar. Bu örnekte, bir sınıf diyagramı içeren bir UML modeli oluşturun veya açın. Diyagrama bazı sınıfları eklemek ve bazı öznitelikler için her bir sınıf ekleyin. Diyagramda sağ tıkladıktan sonra örnek komut `Generate VDM`. Komut dosyası oluşturur `C:\Generated.txt`. Bu dosyayı inceleyin. İçeriğini aşağıdaki metne benzer olmalıdır, ancak kendi sınıflar ve öznitelikler listelenir:  
  
```  
Type Class1 ::  
          Attribute1 : int   
          Attribute2 : string   
Type Class2 ::   
          Attribute3 : string   
```  
  
##  <a name="Application"></a> Dosyaları dosyasından bir uygulama oluşturma  
 Bir UML modeli okuyan bir uygulamaya ait dosyaları oluşturabilirsiniz. Bu amaçla, model ve onun öğelerine erişmenin en esnek ve sağlam yöntemdir [Visual Studio Modelbus'ı](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
 Temel API modeli yüklemek için kullanın ve önceki bölümde olduğu gibi aynı teknikleri kullanarak metin şablonları için model geçirin. Bir model yükleme hakkında daha fazla bilgi için bkz. [program kodundaki UML modelini okuma](../modeling/read-a-uml-model-in-program-code.md).  
  
##  <a name="Design"></a> Tasarım zamanında dosyalar oluşturma  
 UML kod olarak yorumlanması için standart bir yöntem projeniz varsa, kodu projenizin içinde bir UML modelinden oluşturmanıza olanak tanıyan metin şablonları oluşturabilirsiniz. Genellikle UML model projesi ve uygulama kodu için bir veya daha fazla proje içeren bir çözüm yoktur. Her kod projesini modelin içeriğine göre program kodu, kaynakları ve yapılandırma dosyaları oluşturan çeşitli şablonlar içerebilir. Geliştirici tıklayarak tüm şablonları çalıştırabilir **tüm Şablonları Dönüştür** Çözüm Gezgini araç. Program kodu genellikle el ile yazılmış bölümleri tümleştirmeyi kolaylaştırmak için kısmi sınıflar, biçiminde oluşturulur.  
  
 A [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bu tür proje böylece her bir takım üyesi kod aynı şekilde modelden üreten projeler oluşturabilir, şablon biçiminde dağıtılabilir. Genellikle, şablon kod önkoşulları karşılandığından emin olmak için model üzerinde doğrulama kısıtlamalarını içeren bir uzantı paketi parçasıdır.  
  
### <a name="outline-procedure-for-generating-files"></a>Anahat dosyaları oluşturmak için yordamı  
  
-   Şablon için bir proje eklemek için seçin **metin şablonu** yeni dosya Ekle iletişim kutusunda. Çoğu proje ancak modelleme projelerine türleri için bir şablon ekleyebilirsiniz.  
  
-   Şablon dosyasının özel Araçlar özelliği olmalıdır **TextTemplatingFileGenerator**, ve dosya adı uzantısını .tt olmalıdır.  
  
-   En az bir çıkış yönergesi şablonu olmalıdır:  
  
     `<#@ output extension=".cs" #>`  
  
     Projenizin diline göre uzantı alanını ayarlayın.  
  
-   Kod modeli erişmek için şablonunuzda izin vermek için yazma `<#@ assembly #>` bir UML modeli okumak için gereken derlemeler için yönergeleri. Kullanım `ModelingProject.LoadReadOnly()` modeli açmak için. Daha fazla bilgi için [program kodundaki UML modelini okuma](../modeling/read-a-uml-model-in-program-code.md).  
  
-   Şablon ve tıkladığınızda kaydettiğinizde yürütülür **tüm Şablonları Dönüştür** Çözüm Gezgini araç.  
  
-   Bu tür bir şablon hakkında daha fazla bilgi için bkz. [T4 metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
-   Tipik bir projede farklı dosyalar aynı Modeli'nden çeşitli şablonlar olacaktır. Her şablon ilk bölümünü aynı olacaktır. Bu azaltmak için ortak bölümleri ayrı bir metin dosyasına taşıyın ve yönergesini kullanarak çağırma `<#@include file="common.txt"#>` her şablonda.  
  
-   Metin oluşturma işlemi parametreleri sağlamanıza olanak tanıyan özel bir yönerge işlemcisi de tanımlayabilirsiniz. Daha fazla bilgi için [T4 metin dönüştürmeyi özelleştirme](../modeling/customizing-t4-text-transformation.md).  
  
### <a name="example"></a>Örnek  
 Bu örnek, C# sınıfı her UML sınıfı için kaynak modeli oluşturur.  
  
##### <a name="to-set-up-a-visual-studio-solution-for-this-example"></a>Bu örnek için bir Visual Studio çözümünü ayarlamak için  
  
1. Yeni bir çözüm içindeki bir modelleme projesindeki UML sınıf diyagramı oluşturun.  
  
   1.  İçinde **mimarisi** menüsünü tıklatın **yeni diyagram**.  
  
   2.  Seçin **UML sınıf diyagramı**.  
  
   3.  Yeni bir çözüm ve modelleme projesi oluşturmak için istemleri izleyin.  
  
   4.  Bazı sınıflar diyagramda UML sınıf aracını Toolbox'tan sürükleyerek ekleyin.  
  
   5.  Dosyayı kaydedin.  
  
2. Aynı çözümdeki bir C# veya Visual Basic projesi oluşturun.  
  
   -   Çözüm Gezgini'nde çözüme sağ tıklayın, fareyle **Ekle**ve ardından **yeni proje**. Altında **yüklü şablonlar**, tıklayın **Visual Basic** veya **Visual C#** seçip bir proje türü gibi **konsol uygulaması**.  
  
3. C# veya Visual Basic projesi düz metin dosyası ekleyin. Bu dosya birkaç metin şablon yazmak istiyorsanız, paylaşılan kod içerir.  
  
   - Çözüm Gezgini'nde projeye sağ tıklayın, fareyle **Ekle**ve ardından **yeni öğe**. Seçin **metin dosyası**.  
  
     Aşağıdaki bölümde görüntülenen metin ekleyin.  
  
4. Metin şablonu dosyasını, C# veya Visual Basic projesi ekleyin.  
  
   - Çözüm Gezgini'nde projeye sağ tıklayın, fareyle **Ekle**ve ardından **yeni öğe**. Seçin **metin şablonu**.  
  
     Metin şablon dosyasına aşağıdaki kodu ekleyin.  
  
5. Metin şablonu dosyasını kaydedin.  
  
6. Paketinizle dosyasındaki kodu inceleyin. Bu modeldeki her UML sınıf için bir sınıf içermelidir.  
  
   1.  Bir Visual Basic projesinde tıklayın **tüm dosyaları göster** Çözüm Gezgini araç.  
  
   2.  Çözüm Gezgini'nde şablon dosyası düğümünü genişletin.  
  
#### <a name="content-of-the-shared-text-file"></a>Paylaşılan bir metin dosyasının içeriği  
 Bu örnekte, dosyanın SharedTemplateCode.txt adlandırılır ve metin şablonları ile aynı klasörde olan.  
  
```  
<# /* Common material for inclusion in my model templates */ #>  
<# /* hostspecific allows access to the Visual Studio API */ #>  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ assembly name="Microsoft.VisualStudio.Uml.Interfaces.dll"#>  
<#@ assembly name="Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll"#>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>  
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility" #>  
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>  
<#+  // Note this is a Class Feature Block  
///<summary>  
/// Text templates are run in a common AppDomain, so   
/// we can cache the model store that we find.  
///</summary>  
private IModelStore StoreCache  
{  
  get { return AppDomain.CurrentDomain.GetData("ModelStore") as IModelStore; }  
  set { AppDomain.CurrentDomain.SetData("ModelStore", value); }   
}  
private bool CacheIsOld()  
{  
    DateTime? dt = AppDomain.CurrentDomain  
           .GetData("latestAccessTime") as DateTime?;  
    DateTime t = dt.HasValue ? dt.Value : new DateTime();   
    DateTime now = DateTime.Now;  
    AppDomain.CurrentDomain.SetData("latestAccessTime", now);  
    return now.Subtract(t).Seconds > 3;  
}  
  
///<summary>  
/// Find the UML modeling project in this solution,  
/// and load the model.  
///</summary>  
private IModelStore ModelStore  
{  
  get   
  {  
    // Avoid loading the model for every template:  
    if (StoreCache == null || CacheIsOld())  
    {  
      // Use Visual Studio API to find modeling project:  
      EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
      EnvDTE.Project project = null;  
      foreach (EnvDTE.Project p in dte.Solution.Projects)  
      {  
        if (p.FullName.EndsWith(".modelproj"))  
        {  
          project = p;  
          break;  
        }              
      }  
      if (project == null) return null;  
  
      // Load UML model into this AppDomain  
      // and access model store:  
      IModelingProjectReader reader =   
           ModelingProject.LoadReadOnly(project.FullName);  
      StoreCache = reader.Store;  
    }  
    return StoreCache;  
  }  
}  
#>  
```  
  
#### <a name="content-of-the-text-template-file"></a>Metin şablonu dosyasının içeriği  
 Aşağıdaki metni yerleştirilir **.tt** dosya. Bu örnek, bir C# dosyasında UML model sınıflardan sınıflar oluşturur. Ancak, tüm dosya türlerini oluşturabilir. Oluşturulan dosyanın dili metin şablonunun kod yazıldığı dili ilişkili değil.  
  
```  
<#@include file="SharedTemplateCode.txt"#>  
<#@ output extension=".cs" #>  
namespace Test{  
<#  
      foreach (IClass c in ModelStore.AllInstances<IClass>())  
      {  
#>  
   public partial class <#=c.Name#>  
   {   }  
<#  
      }  
#>  
}  
```  
  
##  <a name="What"></a> Metin oluşturma kullanma  
 Modelleme gücü, gereksinimler veya mimari düzeyde tasarlamak için modelleri kullandığınızda elde edilir. Metin şablonları, üst düzey fikirlerinizi koda dönüştürme işinin bir kısmını yapmak için kullanabilirsiniz. Çoğu durumda, bu bire bir ilişkisi için UML modellerini ve sınıflar veya diğer bölümlerinde program kodu içinde olan öğeler arasında neden olmaz.  
  
 Ayrıca, dönüşümün sorun etki alanınızda bağlıdır; kod modelleri arasındaki evrensel eşlemesi yok.  
  
 Kod modelleri oluşturma bazı örnekleri aşağıda verilmiştir:  
  
-   **Ürün serileri**. Fabrikam, Inc. oluşturur ve havaalanı bagaj sistemleri işleme yükler. Yazılımın daha sonraki bir yüklemesi arasında çok benzer, ancak işleme hangi paketi yüklenir ve bu parça tarafından taşıyıcı bantları nasıl bağlandığına yazılım yapılandırmasına bağlıdır. Bir sözleşme başında, Fabrikam analistleri havaalanı yönetimi ile gereksinimleri görüşmek ve UML etkinlik diyagramı kullanarak donanım planını yakalayın. Yapılandırma dosyalarını, program kodu, planlar ve kullanıcı belgeleri, bu modelinden geliştirme ekibi oluşturur. Bunlar, el ile eklemeler ve kod ayarlamaları iş tamamlayın. Bunlar, bunlar sonraki deneyimi bir işten elde gibi oluşturulan malzeme kapsamını genişletin.  
  
-   **Desenler**. Contoso, Ltd geliştiriciler genellikle Web siteleri oluşturun ve UML sınıf diyagramları kullanarak gezinme düzenini tasarlama. Her Web sayfasını bir sınıfla temsil edilir ve ilişkilendirmeler gezinti bağlantılarını gösterir. Geliştiriciler kodu bir Web sitesinin çoğunu modelden oluşturur. Her Web sayfasını, çeşitli sınıflar ve kaynak dosyası girdileri karşılık gelir.  Bu yöntem, her sayfanın oluşumu daha güvenilir ve esnek elle yazılmış kod daha kolaylaştırır, tek bir desene uyar faydası vardır. Değişken yönlerini yakalamak için modeli kullanılırken şablon oluşturma modelidir.  
  
-   **Şemaları**. Bellek bilgisayar sistemleri binlerce dünya çapında sahiptir. Bu sistemler, farklı veritabanlarındaki, diller ve arabirimler kullanın. Merkezi mimari ekibi, iş kavramları ve işlemleri modelleri dahili olarak yayımlar. Bu modeller aracılığıyla yerel takımlar kendi veritabanı ve değişim şemaları program kodu bildirimlerinde bölümleri oluşturmak ve benzeri. Grafik sunumlarını modellerin önerileri tartışmak ekipleri yardımcı olur. Takımlar, farklı iş alanlarına uygulanan model kümelerine Göster birden çok diyagramları oluşturun. Bunlar rengi değiştirilebilir alanları vurgulamak için de kullanabilirsiniz.  
  
## <a name="important-techniques-for-generating-artifacts"></a>Yapıları oluşturmak için önemli teknikleri  
 Önceki örneklerde, modelleri farklı iş bağımlı amaçlar için kullanılır ve sınıflar ve etkinlikler gibi öğeleri modelleme yorumu bir uygulamadan diğerine farklılık gösterir. Modellerden yapıtları oluşturmak aşağıdaki teknikleri yararlıdır.  
  
-   **Profilleri**. Bir iş alanı içinde bile, bir öğe türü yorumunu farklılık gösterebilir. Örneğin bir Web sitesi diyagram üzerinde bazı sınıflar, Web sayfaları temsil ve diğer içerik bloklarını temsil etmek. Bu farklılıkları kaydedin açmasına kolaylaştırmak için stereotipleri tanımlayın. Stereotip Ayrıca, bu tür öğelere uygulanan ek özellikleri eklemek mümkün kılar. Stereotipler profillerinde paketlenir. Daha fazla bilgi için [UML genişletmek için profil tanımlama](../modeling/define-a-profile-to-extend-uml.md).  
  
     Şablon kodunda bir nesne üzerinde tanımlanan stereotipler erişmek kolaydır. Örneğin:  
  
    ```  
    public bool HasStereotype(IClass c, string profile, string stereo)  
    { return c.AppliedStereotypes.Any  
       (s => s.Profile == profile && s.Name == stereo ); }  
    ```  
  
-   **Kısıtlı modelleri**. Oluşturduğunuz tüm modelleri, her amaç için geçerlidir. Örneğin, Fabrikam'ın havaalanı bagaj modellerinde iade masanızın giden bir taşıyıcı olmadan da yanlış olur. Bu kısıtlamalar ortaya koyacağını ön kullanıcıların yardımcı olma doğrulama işlevleri tanımlayabilirsiniz. Daha fazla bilgi için [UML modelleri için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md).  
  
-   **El ile yapılan değişiklikler korumak**. Çözüm dosyalarını yalnızca bazılarını bir modelden oluşturulabilir. Çoğu durumda, ekleyin veya oluşturulan içerik el ile ayarlamanız gerekir. Ancak, bu el ile yapılan değişiklikler şablonu dönüştürme tekrar çalıştırıldığında korunmalıdır önemlidir.  
  
     Burada şablonlarınızın kodda [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] diller, geliştiriciler, yöntemler ve kod ekleyebilirsiniz. böylece kısmi sınıflar oluşturmak. Bir çift olarak her bir sınıf oluşturmak kullanışlıdır: yöntemleri içeren Özet temel sınıf ve türetilen bir sınıf yalnızca Oluşturucu içerir. Bu, geliştiricilerin yöntemleri geçersiz kılmasına olanak tanır. Geçersiz kılınacak başlatma için izin vermek için bunu ayrı bir yöntem yerine oluşturucularda gerçekleştirilir.  
  
     XML ve diğer türleri çıktının bir şablon oluşturur, el ile içerik oluşturulan içerikten ayrı tutmak daha zor olabilir. Bir yöntemi, iki dosyayı birleştirir yapı işleminde bir görev oluşturmaktır. Başka bir yöntem oluşturma şablonu yerel bir kopyasını ayarlamak geliştiriciler içindir.  
  
-   **Ayrı derlemeler kodu Taşı**. Kodun büyük gövdeleri şablonlarını yazma önermiyoruz. Oluşturulan içerik hesaplamadan ayrı tutmak için tercih edilir ve kod düzenleme için metin şablonları da desteklenmez.  
  
     Bunun yerine, metin oluşturmak için önemli ölçüde hesaplamalar gerçekleştirmek varsa, bu işlevlerde ayrı bir derleme oluşturmak ve metotlarını şablondan çağırın.



