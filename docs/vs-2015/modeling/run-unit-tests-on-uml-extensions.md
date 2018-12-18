---
title: Birim testlerini UML uzantılarında çalıştırma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 745d74ae-e48c-4fd9-a755-4354b81b9f8a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6ba485b40beb82db9ea8cfe573cb6d9e6742ecea
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817327"
---
# <a name="run-unit-tests-on-uml-extensions"></a>UML uzantılarında birim testleri çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodunuzu art arda gelen değişiklikler ile tutarlı olmasını sağlamak için birim testleri yazma ve normal yapı işleminin parçası olarak bunları gerçekleştirmek öneririz. Daha fazla bilgi için [Birim Test kodunuzu](../test/unit-test-your-code.md). Testleri Visual Studio modelleme uzantıları ayarlamak için bazı temel bilgi parçasını gerekir. Özet:  
  
- [VSIX uzantıları için bir birim testi ayarlama](#Host)  
  
   VS IDE ana bilgisayar bağdaştırıcısı ile testleri çalıştırın. Her test yönteminin önüne `[HostType("VS IDE")]`. Bu konak bağdaştırıcısı başlar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] testlerinizi çalıştırdığınızda.  
  
- [DTE ve ModelStore erişme](#DTE)  
  
   Genellikle, bir model ve diyagramları ve erişim açmak zorunda olacaksınız `IModelStore` test başlatma.  
  
- [Bir modeli diyagramı açma](#Opening)  
  
   Atayabilirsiniz `EnvDTE.ProjectItem` kitaplıklarından `IDiagramContext`.  
  
- [UI iş parçacığında değişikliklerini gerçekleştirme](#UiThread)  
  
   Model deposu için değişiklik testleri UI iş parçacığında gerçekleştirilmesi gerekir. Kullanabileceğiniz `Microsoft.VSSDK.Tools.VsIdeTesting.UIThreadInvoker` bu.  
  
- [Komutlar ve hareketler diğer MEF Bileşenleri test etme](#MEF)  
  
   MEF Bileşenleri test etmek için açıkça içeri aktarılan özellikleri için değerleri bağlanmanız gerekir.  
  
  Bu noktaları aşağıdaki bölümlerde ayrıntılandırılmıştır.  
  
  Birim test UML Uzantısı örnek kod Örnekler Galerisi bulunabilir [UML – hızlı kullanarak metin girişi](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a).  
  
## <a name="requirements"></a>Gereksinimler  
 Bkz: [gereksinimleri](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
##  <a name="Host"></a> VSIX uzantıları için bir birim testi ayarlama  
 Modelleme uzantılarınızı yöntemleri genellikle açık bir diyagram ile çalışır. MEF içeri aktarmalar gibi yöntemler kullanmanız **IDiagramContext** ve **ILinkedUndoContext**. Sınama ortamınızda, testleri çalıştırmadan önce bu bağlamı ayarlamanız gerekir.  
  
#### <a name="to-set-up-a-unit-test-that-executes-in-includevsprvsincludesvsprvs-mdmd"></a>Yürütülen bir birim testi ayarlamak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
1.  UML Uzantısı proje ve birim testi projesi oluşturun.  
  
    1.  **Bir UML Uzantısı projesi.** Genellikle, bu komut, hareket veya doğrulama proje şablonları kullanarak oluşturun. Örneğin, [modelleme diyagramında menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
    2.  **Birim testi projesi.** Daha fazla bilgi için [Birim Test kodunuzu](../test/unit-test-your-code.md).  
  
2.  Oluşturma bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] UML modelleme projesini içeren çözüm. Bu çözüm, testlerinizi ilk durumunu kullanır. UML Uzantısı ve birim testleri yazma çözümden ayrı olmalıdır. Daha fazla bilgi için [oluşturma UML modelleme projeleri ve diyagramları](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
3.  **UML Uzantısı projedeki**, .csproj dosyasını metin olarak düzenleyin ve aşağıdaki show satırları emin `true`:  
  
    ```  
    <CopyBuildOutputToOutputDirectory>true</CopyBuildOutputToOutputDirectory>  
        <CopyOutputSymbolsToOutputDirectory>true</CopyOutputSymbolsToOutputDirectory>  
    ```  
  
     Metin olarak .csproj dosyasını düzenlemek için seçin **projeyi** Çözüm Gezgini'nde projenin kısayol menüsünde. Ardından **Düzenle … .csproj**. Metni düzenledikten sonra seçin **projeyi**.  
  
4.  UML Uzantısı projenizde, aşağıdaki satırı ekleyin **properties\assemblyınfo.cs**. Bu, test etmek istediğiniz yöntemlere erişmek için birim testleri sağlar:  
  
    ```csharp  
    [assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.  
    ```  
  
5.  **Birim test projesinde**, aşağıdaki derleme başvurularını ekleyin:  
  
    -   *UML Uzantısı projesi*  
  
    -   **EnvDTE.dll**  
  
    -   **Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll**  
  
    -   **Microsoft.VisualStudio.ComponentModelHost.dll**  
  
    -   **Microsoft.VisualStudio.QualityTools.UnitTestFramework.dll**  
  
    -   **Microsoft.VisualStudio.UML.Interfaces.dll'yi**  
  
    -   **Microsoft.VSSDK.TestHostFramework.dll**  
  
6.  Öznitelik öneki `[HostType("VS IDE")]` her test yöntemi için başlatma yöntemleri dahil.  
  
     Bu, Visual Studio'nun deneysel örneğinde test çalışmasını garanti eder.  
  
##  <a name="DTE"></a> DTE ve ModelStore erişme  
 Bir modelleme projesinde açmak için bir yöntem yazmaktır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Genellikle, her test çalıştırmasında yalnızca bir kez çözümü açmak istediğiniz. Yöntemi yalnızca bir kez çalıştırmak için yönteminin önüne `[AssemblyInitialize]` özniteliği. Ayrıca her test yönteminin [HostType ("VS IDE")] özniteliğini gerektiğini unutmayın.  Örneğin:  
  
```csharp  
using EnvDTE;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
using Microsoft.VSSDK.Tools.VsIdeTesting;  
  
namespace UnitTests  
{  
  [TestClass]  
  public static class TestSetup  
  {  
  
    // Location of a VS Solution that defines an initial state for your tests:  
    private const string testSolutionFilePath = @"C:\MyTestFolder\TestModelSln\TestModel.sln";  
    // Name of a modeling project within the test solution:  
    private const string testModelingProjectName = "MyTestModel";  
  
    // Make Solution and IModelStore available to test methods:  
    public static Solution ModelSolution = null;  
    public static IModelingProject ModelingProject = null;  
    public static IModelStore ModelStore = null;  
  
    // This method will be performed once to initialize tests for this assembly:  
    [AssemblyInitialize]   
    [HostType("VS IDE")]  
    public static void OpenTestModelingProject(TestContext testContext)  
    {  
      // To make sure that we always start the tests in the same state,  
      // copy the test solution from a read-only directory:  
      // TODO: copy test solution folder.  
  
      // Open a solution that is the initial state for your tests:  
      ModelSolution = VsIdeTestHostContext.Dte.Solution;  
      ModelSolution.Open(testSolutionFilePath);  
  
      // Find the ModelingProject and IModelStore:  
      foreach (Project project in ModelSolution.Projects)  
      {  
        // http://msdn.microsoft.com/library/ee791691.aspx  
        ModelingProject = project as IModelingProject;  
        if (ModelingProject != null)  
        {  
          // This is a modeling project.  
          ModelStore = ModelingProject.Store;  
          break;  
        }  
        // else this is another kind of project.  
      }  
  
      Assert.IsNotNull(ModelSolution, "VS solution not found");  
      Assert.IsNotNull(ModelStore, "Modeling store not found");  
    }  
    [AssemblyCleanup]  
    public static void RemoveTestSolution ()  
    {  
      // TODO: Remove copied test solution directory.  
    }  
  }  
}  
  
```  
  
 Örneği, <xref:EnvDTE.Project?displayProperty=fullName> ve ondan çevirebilirsiniz sonra bir modelleme projesi temsil eden <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.IModelingProject>.  
  
##  <a name="Opening"></a> Bir modeli diyagramı açma  
 Her bir test veya test sınıfı için genellikle açık bir diyagramı ile çalışma istersiniz. Aşağıdaki örnekte `[ClassInitialize]` özniteliği bu test sınıfında diğer yöntemleri önce bu yöntemi yürütür. Yine de her test metodu özniteliği [HostType ("VS IDE")] gerektiğini unutmayın:  
  
```csharp  
//   
private IDiagram diagram;  
// This class contains unit tests:  
[TestClass]  
public class MyTestClass  
{  
  // Map filenames to open diagram files:  
  private static Dictionary<string, IDiagram> diagrams = new Dictionary<string, IDiagram>();  
  
  // This method will be called once for this test class:  
  [ClassInitialize]  
  [HostType("VS IDE")]  
  public static void TestClassInitialize(TestContext testContext)  
  {  
    // Open all the diagrams in the model:  
    foreach (ProjectItem item in (TestSetup.ModelingProject as Project).ProjectItems)  
    {  
      // Get the filename of the principal file (not the .layout subsidiary):  
      string fileName = item.FileNames[0];  
      // If this is a model diagram file, it can be cast to IDiagramContext:  
      IDiagramContext modelingItem = item as IDiagramContext;  
      if (modelingItem != null)  
      {  
        IDiagram diagram = modelingItem.CurrentDiagram;  
        if (diagram == null)  
        {  
          // Diagram is closed. Open it:  
          item.Open().Activate();  
          diagram = modelingItem.CurrentDiagram;  
        }  
        diagrams[fileName] = diagram;  
      }  
      // else item is not a model diagram.  
    }  
    Assert.IsTrue(diagrams.Count>0, "UML diagram not found");  
  }  
// Insert test methods here ...  
}  
  
```  
  
##  <a name="UiThread"></a> UI iş parçacığı modeli değişikliklerini gerçekleştirme  
 Daha sonra testlerinizi veya test yöntemlerine model deposu için değişiklik yaparsanız, bunlar kullanıcı arabirimi iş parçacığında yürütmelidir. Bunu yaparsanız görebileceğiniz bir `AccessViolationException`. Test yöntemi kodunda bir çağırma çağrısı içine alın:  
  
```  
using System.Windows.Forms;  
using Microsoft.VSSDK.Tools.VsIdeTesting;  
 ...  
    [TestMethod]  
    [HostType("VS IDE")]  
    public void MyTest1()  
    {  
      // Store operations must run in the UI thread:  
      UIThreadInvoker.Invoke((System.Action)delegate()  
      {  
        SetupTestState(TestSetup.ModelStore, diagram);  
        ExecuteMethodUnderTest(TestSetup.ModelStore, diagram);  
      });  
    }  
```  
  
##  <a name="MEF"></a> Komut, hareket ve diğer MEF Bileşenleri test etme  
 MEF Bileşenleri kullanan sahip özellik bildirimleri `[Import]` özniteliği ve değerlerinin konaklarının tarafından ayarlanır. Genellikle, IDiagramContext SVsServiceProvider ve ILinkedUndoContext gibi özellikleri içerir. Bu özelliklerden herhangi birini kullanan bir yöntem test ettiğinizde, test altındaki yöntemi yürütülmeden önce değerlerini ayarlamanız gerekir. Örneğin, bu kod benzeyen bir komut uzantısı yazdıysanız:  
  
```  
  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  class MyCommand : ICommandExtension  
  {  
    [Import] IDiagramContext context { get; set; }  
    [Import]   
Microsoft.VisualStudio.Shell.SVsServiceProvider  
serviceProvider {get;set;}  
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }  
    public void Execute(IMenuCommand command)  
    {  
      DoCommand();  
    }  
    private void DoCommand()  
    {  
      IDiagram diagram = context.CurrentDiagram;  
      using (ILinkedUndoTransaction t = linkedUndoContext.BeginTransaction("go"))  
      { ... }}}  
  
```  
  
 Daha sonra içeri aktarılan özelliklerini aşağıdaki gibi ayarlayabilirsiniz:  
  
```  
  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.ComponentModelHost;   
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
using Microsoft.VSSDK.Tools.VsIdeTesting;  
...  
    [TestMethod]   
    [HostType("VS IDE")]  
    public void Test1()  
    {  
      // Create an instance of the class under test:  
      MyCommand myCommand = new MyCommand();  
      // Get the components service:  
      IComponentModel components = VsIdeTestHostContext.ServiceProvider  
        .GetService(typeof(SComponentModel)) as IComponentModel;  
      // Set the imported properties of the instance under test:  
      // Extension requires "using System.ComponentModel.Composition;" :  
      components.DefaultCompositionService.SatisfyImportsOnce(myCommand);  
      // Call method(s) under test:  
      UIThreadInvoker.Invoke((System.Action)delegate()  
      {  
        myCommand.DoCommand();  
      });  
...}  
```  
  
 İçeri aktarılan özellik bir parametre olarak alan bir yöntem test etmek istediğiniz sonra test sınıfınıza özellik alma ve uygulama `SatisfyImportsOnce` test örneği. Örneğin:  
  
```  
  
using System.ComponentModel.Composition;  
...  
  [TestClass]  
  public class MyTestClass  
  {  
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }  
  
    // Called before each test method:  
    [TestInitialize, HostType("VS IDE")]   
    public void TestInitializer()  
    {  
      IComponentModel components = VsIdeTestHostContext.ServiceProvider  
            .GetService(typeof(SComponentModel)) as IComponentModel;  
      // Extension requires "using System.ComponentModel.Composition;" :  
      components.DefaultCompositionService.SatisfyImportsOnce(this);  
    }  
    [TestMethod, HostType("VS IDE")]  
    public void Test2()  
    {   
     UIThreadInvoker.Invoke((System.Action)delegate()  
      {  
      // Pass context items to class under test:  
      Class1 item1 = new Class1(this.linkedUndoContext);  
      item1.Method1(); // Can use linkedUndoContext  
     });  
   }  
}  
  
```  
  
 Bu örnekte, tek bir satır kolaylık sağlamak için her test yönteminin iki özniteliklerinde birleştirilir.  
  
## <a name="access-from-tests-to-private-methods-and-variables"></a>Testleri bir erişimden özel yöntemler ve değişkenler  
 Bazen bir yöntemi private, test etmek istediğiniz önce özel bir alan durumunu doğrulamak istediğiniz veya test altındaki yöntemi yürütmeden sonra. Testleri test sınıfları için ayrı bir derleme olduğundan bu bir güçlük sunar. Aşağıdakiler dahil olmak üzere, düşünebilirsiniz birkaç taktikleri vardır:  
  
 Yalnızca genel ve iç öğeleri kullanarak test etme  
 Testlerinizi yazın, böylece yalnızca genel (veya iç) sınıflar ve üyeler kullanın. Bu en iyi bir yaklaşımdır. Testlerinizi test edilmekte olan bütünleştirilmiş iç uygulamasını yeniden düzenleme bile çalışmaya devam eder. Değişikliklerden önceki ve sonraki aynı testler uygulayarak, değişikliklerinizi derleme davranışını değiştirilemez emin olabilirsiniz.  
  
 Bunu mümkün hale getirmek için kodunuzu yeniden yapılandırma gerekebilir. Örneğin, bazı yöntemler başka bir sınıf içinde ayırmak gerekebilir.  
  
 Bu yaklaşımın önemli göz önünde bulundurarak vererek, değişiklikler gerekli olduğunda kodunuzu prone hataları için okuma ve değiştirme ve daha az daha kolay, genellikle bulabilirsiniz.  
  
 Test derlemesi'özniteliği ekleyerek iç öğelere erişmek izin verebilirsiniz **properties\assemblyınfo.cs** projesinde, test edilecek:  
  
```csharp  
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.  
```  
  
 Bir test arabirimi tanımlayın  
 Hem bir sınıfın genel üyelerinin test edilecek ve ek özellikleri ve yöntemleri kullanabilmek için testleri istediğiniz özel üyeler içerir bir arabirim tanımlayın. Bu arabirim, test edilecek projeye ekleyin. Örneğin:  
  
```csharp  
internal interface MyClassTestInterface {  
  void PublicMethod1();  
  string PublicProperty1 { get; }  
  string privateField1_Accessor { get; }  
  int privateMethod1_Accessor (string p1);   
 }  
```  
  
 Test edilecek, açıkça erişimci yöntemlerini uygulamak için sınıfı yöntemleri ekleyin. Bu ek yöntemleri ana sınıftaki ayrı ayrı bir dosyada bir parçalı sınıf tanımında yazarak tutun. Örneğin:  
  
```csharp  
partial public class MyClass  
{  
  string MyClassTestInterface.privateField1_Accessor  
  { get { return privateField1; } }  
  int MyClassTestInterface.privateMethod1_Accessor (string p1)  
  { return privateMethod1(p1); }  
}  
  
```  
  
 Test derlemesi test derlemesi için bu öznitelik ekleyerek test arabirimleri kullanmak izin ver:  
  
```csharp  
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.  
```  
  
 Birim test yöntemlerinde, test kullanıcı arabirimini kullanın. Örneğin:  
  
```csharp  
MyClassTestInterface testInstance = new MyClass();  
testInstance.PublicMethod1();  
Assert.AreEqual("hello", testInstance.privateField1_Accessor);  
```  
  
 Yansıma kullanarak erişimcileri tanımlayın  
 Bu, en az öneririz yoludur. Eski sürümlerini [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sağlanan her bir yöntemin özel bir erişimci metot otomatik olarak oluşturulan bir yardımcı program. Bu kullanışlı olsa da, iç yapısını sınamakta olduğunuz uygulama için çok güçlü bağlı bir birim testleri neden eğilimindedir deneyimimizi önerir. Mimari ve gereksinimleri değiştiğinde testleri yanı sıra uygulama değiştirilmesi gerektiği için bu ek iş sonuçlanır. Ayrıca, böylece test hataları bulmaz tasarımında hatalı varsayımlar uygulamasının de testlere, oluşturulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir birim testinin anatomisi](http://msdn.microsoft.com/en-us/a03d1ee7-9999-4e7c-85df-7d9073976144)   
 [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [UML – metin kullanarak hızlı bir giriş](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a)



