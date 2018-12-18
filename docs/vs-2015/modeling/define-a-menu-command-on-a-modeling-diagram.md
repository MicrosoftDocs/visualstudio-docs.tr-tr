---
title: Modelleme Diyagramında Menü komutu tanımlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, menu commands
ms.assetid: 79c277de-5871-4fc7-9701-55eec5c3cd46
caps.latest.revision: 63
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c211c37817ba996105d7496dc49e91db9fa9298e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809109"
---
# <a name="define-a-menu-command-on-a-modeling-diagram"></a>Modelleme diyagramında menü komutu tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da UML diyagramının kısayol menülerindeki ek menü öğelerini tanımlayabilirsiniz. Menü komutunu görünür ve diyagram üzerindeki herhangi bir öğenin kısayol menüsünün etkinleştirilip ve kullanıcı menü öğesi seçtiğinde çalışan kod yazabileceğiniz olup olmadığını kontrol edebilirsiniz. Bu uzantılar bir Visual Studio Tümleştirme Uzantısı'na paketini ([VSIX](http://go.microsoft.com/fwlink/?LinkId=160780)) ve diğer Visual Studio kullanıcılarına dağıtabilirsiniz.  

## <a name="requirements"></a>Gereksinimler  
 Bkz: [gereksinimleri](../modeling/extend-uml-models-and-diagrams.md#Requirements).  

 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  

## <a name="defining-the-menu-command"></a>Menü komutunu tanımlama  
 Bir UML tasarımcısı için bir menü komutu oluşturmak için komutun davranışını tanımlayan bir sınıf oluşturmanız ve sınıfı bir Visual Studio Tümleştirme Uzantısı'na (VSIX) katıştırmanız gerekir. VSIX komutu yükleyebilecek bir kapsayıcı gibi davranır. Bir menü komutunu tanımlamanın iki farklı yöntemi vardır:  

-   **Bir proje şablonunu kullanarak kendi VSIX'inde bir menü komutu oluşturun.** Bu daha hızlı bir yöntemdir. Menü komutlarınızı uzantı doğrulama uzantıları, özel araç kutusu öğeleri veya hareket işleyicileri gibi diğer tür birleştirmek istemiyorsanız, bunu kullanın.  

-   **Ayrı menü komutu ve VSIX projeleri oluşturun.** Aynı VSIX içinde kaç tür uzantıyı birleştirmek istiyorsanız bu yöntemi kullanın. Örneğin, menü komutunuz modelin belirli kısıtlamalar ortaya koyacağını ön görüyorsa bunu bir doğrulama yöntemi olarak aynı VSIX içine katıştırabilirsiniz.  

#### <a name="to-create-a-menu-command-in-its-own-vsix"></a>Kendi VSIX'inde bir menü komutu oluşturmak için  

1. İçinde **yeni proje** iletişim kutusunun **modelleme projeleri**seçin **komut uzantısı**.  

2. Açık **.cs** yeni projeye dosya ve değiştirme `CommandExtension` komutunuzu uygulamak için sınıfı.  

    Daha fazla bilgi için [menü komutunu uygulama](#Implementing).  

3. Yeni sınıflar tanımlayarak bu projeye ek komutlar ekleyebilirsiniz.  

4. F5 tuşuna basarak menü komutunu test edin. Daha fazla bilgi için [menü komutunu yürütme](#Executing).  

5. Menü komut dosyasını kopyalayarak başka bir bilgisayara yükleyin. **bin\\\*\\\*.vsix** projeniz tarafından oluşturulmuş. Daha fazla bilgi için [yükleme ve kaldırma uzantı](#Installing).  

   Alternatif yordam şöyledir:  

#### <a name="to-create-a-menu-command-in-a-separate-class-library-dll-project"></a>Bir ayrı bir sınıf kitaplığı (DLL) projesinde bir menü komutu oluşturmak için  

1. Bir sınıf kitaplığı projesini yeni bir Visual Studio çözüm veya varolan bir çözüm içerisinde oluşturun.  

   1.  Üzerinde **dosya** menüsünde seçin **yeni**, **proje**.  

   2.  Altında **yüklü şablonlar**seçin **Visual C#** veya **Visual Basic**. Orta sütundaki seçin **sınıf kitaplığı**.  

   3.  Ayarlama **çözüm** yeni bir çözüm oluşturmak veya önceden açmış olduğunuz VSIX çözümüne bir bileşen eklemek isteyip istemediğinizi belirtmek için.  

   4.  Proje kümesi adını ve konumunu ve Tamam'a tıklayın.  

2. Projenize aşağıdaki başvuruları ekleyin.  


   |                                                                                                    Başvuru                                                                                                    |                                                                                                  Bunu yapmak sağlar                                                                                                  |
   |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                                                                                        System.ComponentModel.Composition                                                                                        |                                         Kullanarak bileşenleri tanımlayın [Yönetilen Genişletilebilirlik Çerçevesi (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).                                          |
   |                                                                                      Microsoft.VisualStudio.Uml.Interfaces                                                                                      |                                                                                        Okuma ve model öğelerinin özellikleri değiştirin.                                                                                         |
   |                                                                             Microsoft.VisualStudio.ArchitectureTools.Extensibility                                                                              |                                                                                      Model öğeleri oluşturun, diyagramdaki şekilleri değiştirin.                                                                                       |
   |                                                                                  Microsoft.VisualStudio.Modeling.Sdk.[version]                                                                                  | Model öğe işleyicilerini tanımlar.<br /><br /> Modeldeki değişiklikler dizisini yalıtır. Daha fazla bilgi için [işlemleri kullanarak bağlantı UML model güncelleştirmelerini](../modeling/link-uml-model-updates-by-using-transactions.md). |
   |                                                            Microsoft.VisualStudio.Modeling.Sdk.Diagrams. [sürüm]<br /><br /> (her zaman gerekli)                                                             |                                                                                   Hareket işleyicileri için ek diyagram öğelerine erişir.                                                                                   |
   | Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer<br /><br /> Yalnızca Katman diyagramlarındaki komutlar için gereklidir. Daha fazla bilgi için [katman diyagramlarını genişletme](../modeling/extend-layer-diagrams.md). |                                                                                             Katman diyagramları üzerinde komutlar tanımlayın.                                                                                              |


3. Projeye bir sınıf dosyası ekleyin ve içeriğini aşağıdaki koda göre ayarlayın.  

   > [!NOTE]
   >  Ad alanı, sınıf adı ve tarafından döndürülen değer değiştirme `Text` tercihinize.  
   >   
   >  Birden çok komut tanımlarsanız, sınıf adları alfabetik sırada menüsünde görünür.  

   ```  
   using System.ComponentModel.Composition;     
   using System.Linq;  
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;  
   using Microsoft.VisualStudio.Uml.Classes;   
       // ADD other UML namespaces if required  

   namespace UMLmenu1 // CHANGE  
   {  
     // DELETE any of these attributes if the command  
     // should not appear in some types of diagram.  
     [ClassDesignerExtension]  
     [ActivityDesignerExtension]  
     [ComponentDesignerExtension]  
     [SequenceDesignerExtension]  
     [UseCaseDesignerExtension]   
     // [LayerDesignerExtension]  

     // All menu commands must export ICommandExtension:  
     [Export (typeof(ICommandExtension))]  
     // CHANGE class name – determines order of appearance on menu:  
     public class Menu1 : ICommandExtension  
     {  
       [Import]  
       public IDiagramContext DiagramContext { get; set; }  

       public void QueryStatus(IMenuCommand command)  
       { // Set command.Visible or command.Enabled to false  
         // to disable the menu command.  
         command.Visible = command.Enabled = true;  
       }  

       public string Text  
       {  
         get { return "MENU COMMAND LABEL"; }  
       }  

       public void Execute(IMenuCommand command)  
       {  
         // A selection of starting points:  
         IDiagram diagram = this.DiagramContext.CurrentDiagram;  
         foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())  
         { IElement element = shape.Element; }  
         IModelStore modelStore = diagram.ModelStore;  
         IModel model = modelStore.Root;  
         foreach (IElement element in modelStore.AllInstances<IClass>())   
         { }  
       }  
     }  
   }  
   ```  

    Yöntemlere konulacaklar hakkında daha fazla bilgi için bkz. [menü komutunu uygulama](#Implementing).  

   Menü komutunuzu komutu yüklemek için bir kapsayıcı görevi gören bir VSIX projesine eklemeniz gerekir. İsterseniz, aynı VSIX içine diğer bileşenleri dahil edebilirsiniz.  

#### <a name="to-add-a-menu-command-to-a-vsix-project"></a>Bir menü komutu bir VSIX projesine eklemek için  

1.  Kendi VSIX'i olan bir menü komutu oluşturduysanız, bu yordama ihtiyacınız yoktur.  

2.  Çözümünüz zaten içermiyorsa, bir VSIX projesi oluşturun.  

    1.  İçinde **Çözüm Gezgini**, çözümün kısayol menüsünde **Ekle**, **yeni proje**.  

    2.  Altında **yüklü şablonlar**, genişletme **Visual C#** veya **Visual Basic**, ardından **genişletilebilirlik**. Orta sütundaki seçin **VSIX projesi**.  

3.  Çözüm Gezgini'nde VSIX projesinin kısayol menüsünden seçin **başlangıç projesi olarak ayarla**.  

4.  Açık **source.extension.vsixmanifest**.  

    1.  Üzerinde **meta verileri** sekmesinde, VSIX için bir ad belirleyin.  

    2.  Üzerinde **hedefleri Yükle** sekmesinde, hedefler olarak Visual Studio sürümleri ayarlayın.  

    3.  Üzerinde **varlıklar** sekmesini, bir **yeni**ve iletişim kutusunda şunu ayarlayın:  

         **Tür** = **MEF Bileşeni**  

         **Kaynak** = **mevcut çözümde bir proje**  

         **Proje** = *, sınıf kitaplığı projesi*  

##  <a name="Implementing"></a> Menü komutunu uygulama  
 Menü komut sınıfı için gerekli yöntemleri uygular <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension>.  

|||  
|-|-|  
|`string Text { get; }`|Menü öğenizin etiketini döndürün.|  
|`void QueryStatus(IMenuCommand command);`|Kullanıcı diyagramda sağ tıkladığı zaman çağrılır.<br /><br /> Bu yöntemin modeli değiştirmemesi gerekir.<br /><br /> Kullanım `DiagramContext.CurrentDiagram.SelectedShapes` komutu görünür ve etkin olmasını isteyip istemediğinize karar vermek için.<br /><br /> Ayarlayın:<br /><br /> -   `command.Visible` için `true` komutu kullanıcı diyagramda sağ tıkladığı zaman menüde görünmeliyse<br />-   `command.Enabled` için `true` kullanıcı menüde komuta tıklayabilir,<br />-   `command.Text` Menü etiketini dinamik olarak ayarlamak için|  
|`void Execute (IMenuCommand command);`|Görünür ve etkin olması durumunda, kullanıcı menü öğesine tıkladığı zaman çağrılır.|  

### <a name="accessing-the-model-in-code"></a>Kod içinde modele erişme  
 Menü komut sınıfına aşağıdaki bildirimi dahil edin:  

```  
[Import] public IDiagramContext DiagramContext { get; set; }  
```  

 ...  

 Bildirimi `IDiagramContext` diyagrama, geçerli seçime ve modele erişen yöntemlerinizde kod yazmanıza olanak sağlar:  

```  
IDiagram diagram = this.DiagramContext.CurrentDiagram;  
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())  
{ IElement element = shape.Element; ... }  
IModelStore modelStore = diagram.ModelStore;  
IModel model = modelStore.Root;  
foreach (IElement element in modelStore.AllInstances<IUseCase>()) {...}  
```  

### <a name="navigating-and-updating-the-model"></a>Gezinme ve modeli güncelleştirme  
 UML modeli öğelerinin tümü API aracılığıyla kullanılabilirdir. Geçerli seçimden veya modelin kökünden diğer tüm öğelere erişebilirsiniz. Daha fazla bilgi için [UML modelini gezme](../modeling/navigate-the-uml-model.md) ve [UML API ile programlama](../modeling/programming-with-the-uml-api.md).  

 Sıra diyagram ile uğraşıyorsanız, ayrıca bkz: [UML API kullanarak Düzenle UML sıralı diyagramlar](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).  

 API, öğelerin özelliklerini değiştirmenizi, öğeleri ve ilişkileri silmenizi ve yeni öğeler ve ilişkiler oluşturmanızı sağlar.  

 Varsayılan olarak, yürütme yönteminde yaptığınız her değişikliği ayrı bir işlemde gerçekleştirilecektir. Kullanıcı, her değişikliği ayrı ayrı geri mümkün olacaktır. Değişiklikleri tek bir işlemde gruplandırmak istiyorsanız kullanan bir <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoTransaction> açıklandığı [işlemleri kullanarak bağlantı UML model güncelleştirmelerini](../modeling/link-uml-model-updates-by-using-transactions.md).  

### <a name="use-the-ui-thread-for-updates"></a>Güncelleştirmeler için UI iş parçacığı kullanımı  
 Bazı durumlarda modele güncelleştirmeleri bir arka plan iş parçacığından yapmak kullanışlı olabilir. Örneğin, komutunuz bir yavaş kaynaktan veri yüklerse, yükleme komutunuz iş parçacığında gerçekleştirebilir, böylece kullanıcı devam ederken değişiklikleri görebilirsiniz ve gerekirse işlemi iptal.  

 Ancak, model depolamasının bir iş parçacığı güvenli olmadığını bilmeniz gerekir. Her zaman kullanıcı arabirimini (UI) iş parçacığı güncelleştirmeleri yapma ve mümkünse, kullanıcının arka plandaki işlem devam ederken kullanıcıların düzenlemeler yapmasını önlemek gerekir. Bir örnek için bkz. [arka plan iş parçacığı'ndan bir UML modeli güncelleştirme](../modeling/update-a-uml-model-from-a-background-thread.md).  

##  <a name="Executing"></a> Menü komutunu yürütme  
 Test amaçları için komutunuzu hata ayıklama modunda yürütün.  

#### <a name="to-test-the-menu-command"></a>Menü komutunu test etmek için  

1.  Tuşuna **F5**, veya **hata ayıklama** menüsünde seçin **hata ayıklamayı Başlat**.  

     Deneysel örneği [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] başlatır.  

     **Sorun giderme**: yeni [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] başlamıyor:  

    -   Birden fazla projeniz varsa, VSIX projesinin çözümün başlangıç projesi olarak ayarlandığından emin olun.  

    -   Çözüm Gezgini'nde başlatmanın veya yalnızca projenin kısayol menüsünde seçin **özellikleri**. Proje özellik Düzenleyicisi'ndeki **hata ayıklama** sekmesi. Emin olun dizesinde **harici program Başlat** alandır tam yol adını [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], genellikle:  

         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`  

2.  Deneysel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], açın veya bir modelleme projesi oluşturmak ve açmak veya bir modelleme diyagramı oluşturun. Menü komutu sınıfınızın özniteliklerinde listelenen türlerden birine ait bir diyagram kullanın.  

3.  Diyagram üzerindeki herhangi bir yerde kısayol menüsünü açın. Komutunuz menüde görünmeli.  

     **Sorun giderme**: Komut menüsünde görünmüyorsa, emin olun:  

    -   Menü komut projesi, bir MEF Bileşeni olarak listelenir **varlıklar** sekmesinde **source.extensions.manifest** VSIX projesinde.  

    -   Parametreleri `Import` ve `Export` öznitelikleri geçerlidir.  

    -   `QueryStatus` Yöntemi `command`.`Enabled` veya `Visible` alanlarını `false`.  

    -   Menü komut sınıfı özniteliklerinden biri olarak listelenir (UML sınıfı, dizisi ve benzeri) kullandığınız model diyagramın türü `[ClassDesignerExtension]`, `[SequenceDesignerExtension]` ve benzeri.  

##  <a name="Installing"></a> Yükleme ve bir uzantıyı kaldırma  
 Yükleyebileceğiniz bir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] hem kendi bilgisayarınıza hem de diğer bilgisayarlara uzantısı.  

#### <a name="to-install-an-extension"></a>Bir uzantı yüklemek için  

1.  Bilgisayarınızda, bulma **.vsix** VSIX projeniz tarafından oluşturulan dosya.  

    1.  İçinde **Çözüm Gezgini**, VSIX projesinin kısayol menüsünde **klasörü Windows Gezgini'nde Aç**.  

    2.  Dosyayı bulmak **bin\\\*\\**_projeniz_**.vsix**  

2.  Kopyalama **.vsix** uzantıyı yüklemek istediğiniz hedef bilgisayarın bir dosyaya. Bu sizin kendi bilgisayarınız veya başka bir tane olabilir.  

     Hedef bilgisayarda sürümlerinden biri olmalıdır [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] belirttiğiniz **source.extension.vsixmanifest**.  

3.  Hedef bilgisayarda açın **.vsix** örneğin çift tıklayarak dosyayı.  

     **Visual Studio Uzantı Yükleyicisi** açılır ve uzantıyı yükler.  

4.  Başlatın veya yeniden [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  

#### <a name="to-uninstall-an-extension"></a>Bir uzantıyı kaldırmak için  

1. Üzerinde **Araçları** menüsünde seçin **Uzantılar ve güncelleştirmeler**.  

2. Genişletin **yüklü uzantıları**.  

3. Uzantıyı seçin ve ardından **kaldırma**.  

   Nadiren, hatalı bir uzantı yüklemede başarısız olur ve hata penceresinde bir rapor oluşturur ancak Uzantı Yöneticisi'nde görünmez. Bu durumda, dosyayı şuradan silerek uzantıyı kaldırabilirsiniz:  

   *% LocalAppData %* **\Local\Microsoft\VisualStudio\\[sürüm] \Extensions**  

##  <a name="MenuExample"></a> Örnek  
 Aşağıdaki örnek, bir sınıf diyagramı üzerindeki iki öğenin adlarını değiştirecek menü komutu için kod gösterir. Bu kod yerleşik olarak bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantı projesi ve önceki bölümlerde açıklandığı gibi yüklenmelidir.  

```  
using System.Collections.Generic; // for IEnumerable  
using System.ComponentModel.Composition;  
  // for [Import], [Export]  
using System.Linq; // for IEnumerable extensions  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
  // for IDiagramContext  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
  // for designer extension attributes  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  // for ShapeElement  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  // for IGestureExtension, ICommandExtension, ILinkedUndoContext  
using Microsoft.VisualStudio.Uml.Classes;  
  // for class diagrams, packages  

/// <summary>  
/// Extension to swap names of classes in a class diagram.  
/// </summary>  
namespace SwapClassNames  
{  
  // Declare the class as an MEF component:  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  // Add more ExportMetadata attributes to make  
  // the command appear on diagrams of other types.  
  public class NameSwapper : ICommandExtension  
  {  
  // MEF required interfaces:  
  [Import]  
  public IDiagramContext Context { get; set; }  
  [Import]  
  public ILinkedUndoContext LinkedUndoContext { get; set; }  

  /// <summary>  
  /// Swap the names of the currently selected elements.  
  /// </summary>  
  /// <param name="command"></param>  
  public void Execute(IMenuCommand command)  
  {  
    // Get selected shapes that are IClassifiers -  
    // IClasses, IInterfaces, IEnumerators.  
    var selectedShapes = Context.CurrentDiagram  
     .GetSelectedShapes<IClassifier>();  
    if (selectedShapes.Count() < 2) return;  

    // Get model elements displayed by shapes.  
    IClassifier firstElement = selectedShapes.First().Element;  
    IClassifier lastElement = selectedShapes.Last().Element;  

    // Do the swap in a transaction so that user  
    // cannot undo one change without the other.  
    using (ILinkedUndoTransaction transaction =  
    LinkedUndoContext.BeginTransaction("Swap names"))  
    {  
    string firstName = firstElement.Name;  
    firstElement.Name = lastElement.Name;  
    lastElement.Name = firstName;  
    transaction.Commit();  
    }  
  }  

  /// <summary>  
  /// Called by Visual Studio to determine whether  
  /// menu item should be visible and enabled.  
  /// </summary>  
  public void QueryStatus(IMenuCommand command)  
  {   
    int selectedClassifiers = Context.CurrentDiagram  
     .GetSelectedShapes<IClassifier>().Count();  
    command.Visible = selectedClassifiers > 0;  
    command.Enabled = selectedClassifiers == 2;  
  }  

  /// <summary>  
  /// Name of the menu command.  
  /// </summary>  
  public string Text  
  {  
    get { return "Swap Names"; }  
  }  
  }  

}  
```  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Modelleme Uzantısı Tanımlama ve yükleme](../modeling/define-and-install-a-modeling-extension.md)   
 [UML modellerini ve diyagramları genişletme](../modeling/extend-uml-models-and-diagrams.md)   
 [Modelleme Diyagramında hareket işleyicisi tanımlama](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)   
 [Özel tanımlama Modelleme araç kutusu öğesi](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [UML modelleri için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md)   
 [UML API kullanarak UML sıralı diyagramlar Düzenle](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)   
 [UML API ile programlama](../modeling/programming-with-the-uml-api.md)   
 [Örnek: UML diyagramında şekilleri hizalamak için komutu](http://go.microsoft.com/fwlink/?LinkID=213809)



