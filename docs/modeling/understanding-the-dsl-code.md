---
title: DSL Kodunu Anlama
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, generated code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 490c9c3fe5724373072b2857eb0ce3da7905b172
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813331"
---
# <a name="understanding-the-dsl-code"></a>DSL Kodunu Anlama
Bir etki alanına özgü dil (DSL) çözümü okumak ve Visual Studio DSL örneklerini güncellemek için kullanabileceğiniz bir API oluşturur. Bu API, DSL tanımını oluşturulan kodda tanımlanır. Bu konuda oluşturulan API açıklanmaktadır.

## <a name="the-example-solution-component-diagrams"></a>Örnek çözüm: Bileşen diyagramları
 Bu konudaki örnekler çoğu kaynağı olan çözümü oluşturmak için gelen bir DSL oluşturma **bileşeni modelleri** çözüm şablonu. Bu, yeni bir DSL çözümü oluşturduğunuzda görüntülenen standart şablonların biridir.

> [!NOTE]
>  Bileşen diyagramları DSL şablonu Visual Studio'da mimari menüsü kullanarak oluşturabileceğiniz UML Bileşen diyagramları ilgili değildir. İçinde **yeni proje** iletişim kutusunda **diğer proje Types\Extensibility** ve ardından **etki alanına özgü dil tasarımcısını**.

 Bu çözüm şablonu ile aşina değilseniz F5 ve deneyi tuşuna basın. Bir bağlantı noktası aracını bileşenin üzerine sürükleyerek bağlantı noktaları oluşturma ve bağlantı noktaları bağlanabildiğinizi özellikle dikkat edin.

 ![Bileşenleri ve birbirine bağlı bağlantı noktaları](../modeling/media/componentsample.png)

## <a name="the-structure-of-the-dsl-solution"></a>DSL Çözüm yapısı
 **Dsl** proje DSL'nizi için API tanımlar. **DslPackage** proje, Visual Studio ile nasıl tümleştiğine tanımlar. Modelden oluşturulan kodu da içerebilir kendi projeleriniz de ekleyebilirsiniz.

### <a name="the-code-directories"></a>Kodu dizinleri
 Bu projelerin her biri kodda çoğunu oluşturulduğu **Dsl\DslDefinition.dsl**. Oluşturulan kodu **oluşturulan kodu** klasör. Oluşturulan dosyanın görmek için tıklayın **[+]** oluşturma yanındaki **.tt** dosya.

 DSL anlamanıza yardımcı olması için oluşturulan kod incelemenizi öneririz. Oluşturulan dosyaları görmek için Çözüm Gezgini'nde *.tt dosyaları genişletin.

 \*.Tt dosyaları çok az kod içerir. Bunun yerine, kullandıkları `<#include>` paylaşılan şablon dosyaları eklemek için yönergeleri. Paylaşılan dosyalar bulunabilir **\Program Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates**

 DSL çözümü kendi program kodu eklediğinizde, oluşturulan kod klasörü dışında ayrı bir dosya ekleyin. Oluşturmak istediğiniz bir **özel kod** klasör. (Özel bir klasöre yeni bir kod dosyası eklediğinizde, ad alanı'başlangıç kodunu çatıda düzeltmek unutmayın.)

 Çözümü yeniden derlediğinizde, yaptığınız düzenlemeleri kaybolacağı için oluşturulan kodun doğrudan düzenlemenizi öneririz. Bunun yerine, DSL'nizi özelleştirmek için:

-   DSL tanımındaki birçok parametreleri ayarlayın.

-   Kısmi sınıflar ayrı kod dosyalarında tanımlanan veya devralınan tarafından üretilen sınıfları geçersiz kılma yöntemleri yazın. Bazı durumlarda ayarlamak zorunda **Generates Double Derived** oluşturulan bir yöntemi geçersiz kılmak için DSL tanımındaki bir sınıfın seçeneği.

-   DSL tanımındaki 'kancaları' için kendi kodunuzu sağlamak oluşturulan kodu neden seçeneklerini ayarlayın.

     Örneğin ayarlarsanız, **sahip özel Oluşturucu** alan sınıfının seçeneğini ve ardından Çözümü derleyin, hata iletisi görürsünüz. Bu hata iletilerinden biri çift tıkladığınızda, özel kodunuz sağlamanız açıklayan oluşturulan kod açıklamaları görürsünüz.

-   Uygulamanıza özgü kodu oluşturmak için kendi metin şablonlarınızı yazın. Kullanım birçok projelerinde ortak olan şablonları parçalarını paylaşmak için dosyalar içerebilir ve kendi dosya yapısı ile başlatılır projeler kurmak için Visual Studio Proje şablonları oluşturabilirsiniz.

## <a name="generated-files-in-dsl"></a>Dsl içinde oluşturulan dosyalar
 Aşağıdaki oluşturulan dosyalar görünür **Dsl** proje.

 *YourDsl* `Schema.xsd`

 DSL'nizi örneklerini içeren şema dosyaları için. Bu dosya için derleme kopyalanır (**bin**) dizin. DSL'nizi yüklediğinizde, bu dosyaya kopyalayın **\Program Visual Studio 11.0\Xml\Schemas** böylece model dosyaları doğrulanabilir. Daha fazla bilgi için [etki alanına özgü dil çözümlerini dağıtma](../modeling/deploying-domain-specific-language-solutions.md).

 DSL Gezgini içinde seçeneklerini ayarlayarak serileştirme özelleştirirseniz, şema uygun şekilde değiştirir. Ancak, bu dosya artık kendi serileştirme kod yazma, gerçek şema temsil edebilir. Daha fazla bilgi için [özelleştirme dosya depolamayı ve XML serileştirmeyi](../modeling/customizing-file-storage-and-xml-serialization.md).

 `ConnectionBuilders.cs`

 Bir bağlantı Oluşturucu ilişkileri oluşturan bir sınıftır. Bağlantı aracını arkasında kodudur. Bu dosya, bir çift her bağlantı aracı için sınıflar içerir. Adları etki alanı ilişkisi ve bağlantı aracını adlarından türetilir: *ilişki*oluşturucusu ve *ConnectorTool*ConnectAction.

 (Bileşen çözüm örnekte, bağlantı oluşturucular birini ConnectionBuilder çağrılır, etki alanı ilişkisi bağlantısı adında bir rastlantı olmasıdır.)

 İlişki oluşturulur *ilişki* `Builder.Connect()` yöntemi. Varsayılan sürüm doğrular: kaynak ve hedef model öğeleri kabul edilir ve ardından ilişkinin örneğini oluşturur. Örneğin:

 `CommentReferencesSubject(sourceAccepted, targetAccepted);`

 Her Oluşturucu sınıfı bir düğümden oluşturulan **bağlantı oluşturucular** DSL Gezgini bölümünde. Bir `Connect` yöntemi, etki alanı sınıflarının bir veya daha fazla çiftleri arasındaki ilişkileri oluşturabilir. Her bir bağlantı bağlanma Oluşturucu düğümünde DSL Gezgini içinde bulabileceğiniz yönergesi tarafından tanımlanır.

 Örneğin, üç DSL örneği'nde ilişki türlerinin her biri için bir bağlantı Oluşturucu bağlantı bağlama yönergeleri ekleyebilirsiniz. Bu kullanıcı tek bir bağlantı aracıyla sağlar. İlişki örneği türü kullanıcı tarafından seçilen kaynak ve hedef öğe türlerine bağlıdır.  Bağlantı bağlama yönergesi eklemek için bir Oluşturucu'da DSL Gezgini sağ tıklayın.

 Belirli türde bir etki alanı ilişkisi oluşturulduğunda çalışan özel kod yazmak için uygun bağlantı bağlama yönergesi Oluşturucusu düğümü altında seçin. Özellikler penceresinde ayarlayın **zel bağlanma kullanır**. Çözümü yeniden oluşturun ve sonra ortaya çıkan hataları düzeltmek için kodu girin.

 Kullanıcı Bu bağlantı aracı kullandığında çalışan özel kod yazmak için ayarlanmış **olan özel** bağlantı oluşturucunun özelliği. Bir kaynak öğesi, belirli bir kaynak bileşimini olmadığını izin verilir ve hedef izin verilir ve hangi güncelleştirmelerin bir bağlantı yapıldığında modele yapılması gereken olup olmadığını karar kodu sağlayabilir. Örneğin, yalnızca bir döngü diyagramda oluşturulduğu değil, bir bağlantı izin verebilir. Tek ilişkisi bağlantı yerine, kaynak ve hedef arasında birden fazla arası ilgili öğelerin daha karmaşık bir desen örneği oluşturulamadı.

 `Connectors.cs`

 Genellikle başvuru ilişkileri gösteren diyagram öğeleri bağlayıcılar için sınıflar içerir. Tek bir bağlayıcıyı DSL tanımındaki her sınıf oluşturulur. Her bağlayıcı sınıfın türetilmiş <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 Renk ve diğer stil özellikleri değişken, çalışma zamanında yapmak için sınıf DSL tanım diyagramı üzerinde sağ tıklayın ve fareyle **ekleme kullanıma sunulan**.

 Çalışma zamanında ek stil özellikleri değişkeni gerçekleştirmek için örneğin bkz <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> ve <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>.

 `Diagram.cs`

 Diyagramı tanımlayan bir sınıf içerir. Öğesinden türetilen <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>.

 Renk ve diğer stil özellikleri değişken, çalışma zamanında yapmak için sınıf DSL tanım diyagramı üzerinde sağ tıklayın ve fareyle **ekleme kullanıma sunulan**.

 Ayrıca, bu dosyayı içeren `FixupDiagram` modele yeni bir öğe eklendiğinde, yanıt veren bir kural. Kural yeni bir şekil ekler ve şekli model öğesine bağlar.

 `DirectiveProcessor.cs`

 Bu yönerge işlemcisi, DSL'nin bir örneği okuma metin şablonları yazma, kullanıcılara yardımcı olur. Yönerge işlemcisini DSL'nizi için (DLL'ler) derlemeleri yükler ve etkili bir şekilde ekler `using` deyimleri ad alanınız için. Bu kod içinde DSL'nizi tanımladığınız ilişkileri ve sınıfların kullanmak için metin şablonları sağlar.

 Daha fazla bilgi için [bir etki alanına özgü dilden kod oluşturma](../modeling/generating-code-from-a-domain-specific-language.md) ve [özel T4 metin şablonu yönerge işlemcileri oluşturma](../modeling/creating-custom-t4-text-template-directive-processors.md).

 `DomainClasses.cs`

 Uygulamaları, soyut sınıflar ve model kök sınıfı dahil olmak üzere, tanımladığınız bir etki alanı sınıflarının. Öğesinden türetilen <xref:Microsoft.VisualStudio.Modeling.ModelElement>.

 Her etki alanı sınıfı içerir:

- Bir özellik tanımı ve her bir etki alanı özellik için bir iç içe geçmiş bir işleyici sınıfı. OnValueChanging() ve OnValueChanged() geçersiz kılabilirsiniz. Daha fazla bilgi için [etki alanı özellik değeri değişiklik işleyicileri](../modeling/domain-property-value-change-handlers.md).

   DSL, örnekte `Comment` sınıfı içeren bir özellik `Text` ve bir işleyici sınıfı `TextPropertyHandler`.

- Bu etki alanı sınıfı, yer aldığı ilişkileri için erişimci özellikleri. (Rol özellikleri için hiç iç içe geçmiş sınıf yoktur.)

   DSL, örnekte `Comment` sınıfına sahip gömme ilişkisi, üst modeline erişme erişimcileri `ComponentModelHasComments`.

- Oluşturucular. Bu geçersiz kılmak istediğiniz verilirse **sahip özel Oluşturucu** şirket etki alanı sınıfı.

- Öğe grubu prototip (EGP) işleyici yöntemleri. Bu kullanıcı, gerekli olan *birleştirme* (Ekle) bu sınıfın örneklerinin üzerine başka bir öğe. Genellikle kullanıcının bu öğe aracına ya da başka bir şekil sürükleyerek veya yapıştırarak yapar.

   Örnekte DSL, bir giriş veya çıkış bağlantı noktasına bir bileşen üzerine birleştirilebilir. Ayrıca, bileşenler ve açıklamaları modeline birleştirilebilir. Bu

   Bileşen sınıfı EGP işleyici yöntemleri bağlantı noktaları, ancak değil açıklamaları kabul etmek bir bileşenine izin verin. Kök model sınıfı EGP işleyicisinde yorumlar ve bileşenleri, ancak olmayan bağlantı noktalarını kabul eder.

  `DomainModel.cs`

  Etki alanı modeli temsil eden sınıf. Öğesinden türetilen <xref:Microsoft.VisualStudio.Modeling.DomainModel>.

> [!NOTE]
>  Bu modelin kök sınıfı ile aynı değildir.

 Kopyalama ve Sil kapanışlar tanımlamak diğer öğeleri olması gereken bir öğe kopyalandığında veya dahil. Ayarlayarak bu davranışı denetleyebilirsiniz **yayar kopyalama** ve **yayar Sil** rollerinin her ilişkinin her iki tarafındaki özellikleri. Değerleri dinamik olarak belirlendiği istiyorsanız, kapanış sınıflarının yöntemleri geçersiz kılmak için kod yazabilirsiniz.

 `DomainModelResx.resx`

 Bu, etki alanı sınıfları ve özellikleri, özellik adları, araç kutusu etiketleri, standart hata iletileri ve kullanıcıya görüntülenen diğer dizeleri açıklamaları gibi dizeler içerir. Ayrıca, araç simgelerle ve görüntülerle resim şekilleri için de içerir.

 Bu dosya, derlenen bütünleştirilmiş koda bağlı olduğu ve bu kaynaklar için varsayılan değerleri sağlar. Kaynakları yerelleştirilmiş bir sürümünü içeren bir uydu derlemesine oluşturarak DSL'nizi yerelleştirebilirsiniz. Bu sürüm, DSL bir kültürde yerelleştirilmiş kaynaklar eşleşen yüklü olduğunda kullanılır. Daha fazla bilgi için [etki alanına özgü dil çözümlerini dağıtma](../modeling/deploying-domain-specific-language-solutions.md).

 `DomainRelationships.cs`

 Modeldeki iki öğe arasındaki her bağlantı, bir etki alanı ilişki sınıfı örneği tarafından temsil edilir. Tüm ilişkisi sınıflarını türetilmiştir <xref:Microsoft.VisualStudio.Modeling.ElementLink>, hangi sırayla türetilmiş olan <xref:Microsoft.VisualStudio.Modeling.ModelElement>. Bir ModelElement olduğundan, bir ilişkinin örneğini özelliklere sahip olabileceğini ve kaynak veya hedef bir ilişkinin olabilir.

 `HelpKeywordHelper.cs`

 Kullanıcı F1 tuşuna bastığında kullanılan işlevler sağlar.

 `MultiplicityValidation.cs`

 İlişki rollerindeki 1..1 ya da 1 Çokluk belirttiğiniz.. *, kullanıcı uyarı, en az bir ilişkinin örneğini gereklidir. Bu dosya bu uyarılar uygulayan doğrulama kısıtlamaları sağlar. 1..1 katıştırma üst bağlantı doğrulanamadı.

 Bu kısıtlamalar yürütülecek birine ayarlamalısınız **kullanır...**  seçeneklerini **Editor\Validation** DSL Gezgininde. Daha fazla bilgi için [etki alanına özgü bir dilde doğrulama](../modeling/validation-in-a-domain-specific-language.md).

 `PropertiesGrid.cs`

 Bu dosya, yalnızca bir alan özelliği için bir özel tür tanımlayıcı eklediyseniz, kod içerir. Daha fazla bilgi için [Özellikler penceresini özelleştirme](../modeling/customizing-the-properties-window.md).

 `SerializationHelper.cs`

- İki öğe aynı ad tarafından başvurulan emin olmak için bir doğrulama yöntemi. Daha fazla bilgi için [özelleştirme dosya depolamayı ve XML serileştirmeyi](../modeling/customizing-file-storage-and-xml-serialization.md).

- SerializationHelper sınıf seri hale getirme sınıfları tarafından kullanılan ortak işlevleri sağlar.

  `Serializer.cs`

  Her etki alanı sınıfı, ilişki, şekil, bağlayıcı, Diyagram ve model için seri hale getirici sınıfı.

  Bu sınıfların özelliklerin çoğu, DSL Gezgini altında ayarlar tarafından denetlenebilir **Xml serileştirme davranışı**.

  `Shapes.cs`

  DSL tanımındaki her şekil sınıfı için bir sınıf. Şekiller türetilir <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>. Daha fazla bilgi için [özelleştirme dosya depolamayı ve XML serileştirmeyi](../modeling/customizing-file-storage-and-xml-serialization.md).

  Kısmi bir sınıf kendi yöntemleri ile oluşturulan yöntemleri geçersiz kılmak için ayarlanmış **Generates Double Derived** DSL tanımındaki Bağlayıcısı. Bir Oluşturucu ile kendi kodunuzu değiştirmek için **sahip özel Oluşturucu**.

  Renk ve diğer stil özellikleri değişken, çalışma zamanında yapmak için sınıf DSL tanım diyagramı üzerinde sağ tıklayın ve fareyle **ekleme kullanıma sunulan**.

  Çalışma zamanında ek stil özellikleri değişkeni gerçekleştirmek için örneğin bkz <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField> ve <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

  `ToolboxHelper.cs`

  Araç kutusu öğe grubu prototipleri öğesi araçları yükleyerek ayarlar. Kullanıcı Aracı'nı çalıştırdığında bu prototipleri kopyalarını hedef öğeleri ile birleştirilir.

  Geçersiz kılma `CreateElementPrototype()` birkaç nesnelerin bir grup oluşturur. bir araç kutusu öğesi tanımlama. Örneğin, alt bileşenlerine sahip nesneleri temsil etmek için bir öğe tanımlayabilirsiniz. Kod değiştirdikten sonra araç kutusu önbelleği temizlemek için Visual Studio'nun deneysel örneğinde sıfırlayın.

## <a name="generated-files-in-the-dslpackage-project"></a>DslPackage projesindeki oluşturulan dosyalar
 DslPackage Yönetme penceresi, araç kutusu ve menü komutları, Visual Studio Kabuğu için DSL model couples. Böylece herhangi birini kendi yöntemlerini geçersiz kılabilirsiniz sınıflar türetilmiş, çift çoğu.

 `CommandSet.cs`

 Diyagramda görünür olan bağlam menüsü komutları. Uyum veya bu kümeye ekleyebilirsiniz. Bu dosya, komutlar için kod içerir. Menü komutlarını konumunu Commands.vsct dosyası tarafından belirlenir. Daha fazla bilgi için [kullanıcı komutları ve eylemleri yazma](../modeling/writing-user-commands-and-actions.md).

 `Constants.cs`

 GUID.

 `DocData.cs`

 *YourDsl* `DocData` yükleme ve bir model dosyasını kaydetme yönetir ve Store örneği oluşturur.

 Örneğin, bir dosya yerine bir veritabanında DSL'nizi kaydetmek istiyorsanız, geçersiz kılmanız `Load` ve `Save` yöntemleri.

 `DocView.cs`

 *YourDsl* `DocView` diyagramda görünme penceresi yönetir. Örneğin, bir windows Form içinde diyagram katıştırabilirsiniz:

 Bir kullanıcı denetimi dosyası DslPackage projeye ekleyin. Diyagramda görüntülenebilir bir Panel ekleyin. Düğme ve diğer denetimleri ekleyin. Formun kod görünümünde DSL'nizi adlar ayarlamayı aşağıdaki kodu ekleyin:

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Drawing;
using System.Data;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Shell;

namespace Company.EmbedInForm
{
  public partial class UserControl1 : UserControl
  {
    public UserControl1()
    {
      InitializeComponent();
    }

    private DiagramDocView docView;

    public UserControl1(DiagramDocView docView, Control content)
      : this()
    {
      this.docView = docView;
      panel1.Controls.Add(content);
    }

    private void button1_Click(object sender, EventArgs e)
    {
      ExampleModel modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;
      foreach (ExampleElement element in modelRoot.Elements)
      {
       listBox1.Items.Add(element.Name);
      }
    }
  }
  internal partial class EmbedInFormDocView
  {

    private ContainerControl container;

    /// <summary>
    /// Return a User Control instead of the DSL window.
    /// The user control will contain the DSL window.
    /// </summary>

    public override System.Windows.Forms.IWin32Window Window
    {
      get
      {
        if (container == null)
        {
          // Put the normal DSL Window inside our control
          container = new UserControl1(this, (Control)base.Window);
        }
        return container;
      }
    }
  }

}
```

 `EditorFactory.cs`

 Başlatır `DocData` ve `DocView`. Visual Studio DSL paketinizi başlatıldığında bir Düzenleyicisi'ni açmak için kullandığı standart bir arabirimi karşıladığı. İçinde başvurulan `ProvideEditorFactory` Package.cs özniteliği

 `GeneratedVSCT.vsct`

 Standart menü komutlarını, menü, diyagram bağlam menüsü gibi bulur **Düzenle** menü ve benzeri. Komutları için CommandSet.cs kodudur. Yerini değiştirmek veya standart komutları değiştirebilir ve kendi komutlar ekleyebilirsiniz. Daha fazla bilgi için [kullanıcı komutları ve eylemleri yazma](../modeling/writing-user-commands-and-actions.md).

 `ModelExplorer.cs`

 Model Gezginini DSL'nizi için tanımlar. Ağaç görünümü diyagramda yanı sıra kullanıcının gördüğü modelin budur.

 Örneğin, geçersiz `InsertTreeView()` öğeleri Model Gezgini'nde görüntülenme sırasını değiştirmek için.

 Seçimi model Gezgini'nde diyagram seçimi ile eşitlenmiş tutmak istiyorsanız, aşağıdaki kodu kullanabilirsiniz:

```
protected override void OnSelectionChanged(global::System.EventArgs e)
{
base.OnSelectionChanged(e);
// get the selected element
DslModeling::ModelElement selectedElement =
this.PrimarySelection as DslModeling::ModelElement;
// Select in the model explorer
SelectInModelExplorer<YOURLANGUAGEExplorerToolWindow>(selectedElement);
}
private void SelectInModelExplorer<T>(DslModeling::ModelElement modelElement)
where T : DslShell.ModelExplorerToolWindow
{
DslShell::ModelingPackage package =
this.GetService(typeof(VSShell.Package)) as DslShell::ModelingPackage;

if (package != null)
{
// find the model explorer window
T explorerWindow = package.GetToolWindow(typeof(T), true) as T;
if (explorerWindow != null)
{
// get the tree container
DslShell.ModelExplorerTreeContainer treeContainer =
explorerWindow.TreeContainer;
// find the tree node
DslShell.ExplorerTreeNode treeNode =
treeContainer.FindNodeForElement(modelElement);
// select the node
explorerWindow.TreeContainer.ObjectModelBrowser.SelectedNode = treeNode;
}
}
}
```

 `ModelExplorerToolWindow.cs`

 Model gezginini görüntülendiği penceresini tanımlar. Explorer'da öğelerinin seçimini işler.

 `Package.cs`

 Bu dosya, DSL Visual Studio'ya nasıl tümleştirildiğini tanımlar. Paket sınıfı özniteliklerinde DSL işleyici, dosya uzantısına sahip, kendi araç kutusu tanımlayın ve yeni bir pencere açmak nasıl tanımlama dosyaları olarak kaydedin. Initialize() yöntemi ilk DSL bir Visual Studio örneğine yüklenen ne zaman bir kez çağrılır.

 `Source.extension.vsixmanifest`

 Bu dosyayı özelleştirmek için düzenleme `.tt` dosya.

> [!WARNING]
>  Simgeler veya görüntü gibi kaynakları içerecek şekilde .tt dosyayı düzenlerseniz, kaynak dahil olduğundan emin olun. VSIX derleme. Çözüm Gezgini'nde dosyayı seçin ve emin **VSIX Ekle** özelliği `True`.

 Bu dosya, bir Visual Studio Tümleştirme Uzantısı (VSIX) DSL nasıl paketlenmiştir denetler. Daha fazla bilgi için [etki alanına özgü dil çözümlerini dağıtma](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Ayrıca Bkz.

- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
- [Modelleri, Sınıfları ve İlişkileri Anlama](../modeling/understanding-models-classes-and-relationships.md)
- [Etki Alanına Özgü Dili Özelleştirme ve Genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md)
- [Etki Alanına Özgü Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
