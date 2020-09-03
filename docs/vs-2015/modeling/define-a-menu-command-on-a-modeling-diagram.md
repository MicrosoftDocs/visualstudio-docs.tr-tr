---
title: Modelleme Diyagramında Menü komutu tanımlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, menu commands
ms.assetid: 79c277de-5871-4fc7-9701-55eec5c3cd46
caps.latest.revision: 63
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b6481a56b4cbc254baaee3ae087201df69c371b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534218"
---
# <a name="define-a-menu-command-on-a-modeling-diagram"></a>Modelleme diyagramında menü komutu tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da, UML diyagramının kısayol menülerinde ek menü öğeleri tanımlayabilirsiniz. Menü komutunun, Diyagram üzerindeki herhangi bir öğenin kısayol menüsünde görüntülenip görüntülenmeyeceğini ve etkin olduğunu denetleyebilir ve Kullanıcı menü öğesini seçtiğinde çalışan bir kod yazabilirsiniz. Bu uzantıları bir Visual Studio Tümleştirme Uzantısı 'na ([VSIX](https://msdn.microsoft.com/library/dd393694(VS.100).aspx)) paketleyebilir ve diğer Visual Studio kullanıcılarına dağıtabilirsiniz.

## <a name="requirements"></a>Gereksinimler
 [Gereksinimlere](../modeling/extend-uml-models-and-diagrams.md#Requirements)bakın.

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="defining-the-menu-command"></a>Menü komutunu tanımlama
 Bir UML tasarımcısı için bir menü komutu oluşturmak için, komutun davranışını tanımlayan bir sınıf oluşturmanız ve sınıfı bir Visual Studio Tümleştirme Uzantısı 'na (VSıX) katıştırmanız gerekir. VSıX, komutu yükleyen bir kapsayıcı görevi görür. Bir menü komutu tanımlamanın iki alternatif yöntemi vardır:

- **Proje şablonunu kullanarak kendi VSIX 'inde bir menü komutu oluşturun.** Bu daha hızlı bir yöntemdir. Menü komutlarınızı doğrulama uzantıları, özel araç kutusu öğeleri veya hareket işleyicileri gibi diğer tür uzantılarla birleştirmek istemiyorsanız, bunu kullanın.

- **Ayrı menü komutu ve VSıX projeleri oluşturun.** Aynı VSıX içinde birkaç uzantı türünü birleştirmek istiyorsanız bu yöntemi kullanın. Örneğin, menü komutunuz modelin belirli kısıtlamaları gözlemmesini bekliyorsa, bir doğrulama yöntemiyle aynı VSıX 'e katabilirsiniz.

#### <a name="to-create-a-menu-command-in-its-own-vsix"></a>Kendi VSIX 'inde bir menü komutu oluşturmak için

1. **Yeni proje** iletişim kutusunda, **modelleme projeleri**' nin altında, **komut uzantısı**' nı seçin.

2. Yeni projede **. cs** dosyasını açın ve `CommandExtension` komutunu uygulamak için sınıfını değiştirin.

    Daha fazla bilgi için, bkz. [menü komutunu uygulama](#Implementing).

3. Yeni sınıflar tanımlayarak bu projeye ek komutlar ekleyebilirsiniz.

4. F5 tuşuna basarak menü komutunu test edin. Daha fazla bilgi için, bkz. [menü komutunu yürütme](#Executing).

5. Menü komutunu, projeniz tarafından oluşturulan **bin \\ \* \\ \* . vsix** dosyasını kopyalayarak başka bir bilgisayara yükler. Daha fazla bilgi için bkz. [Uzantı yükleme ve kaldırma](#Installing).

   Alternatif yordam aşağıda verilmiştir:

#### <a name="to-create-a-menu-command-in-a-separate-class-library-dll-project"></a>Ayrı bir sınıf kitaplığı (DLL) projesinde bir menü komutu oluşturmak için

1. Yeni bir Visual Studio çözümünde ya da var olan bir çözümde bir sınıf kitaplığı projesi oluşturun.

   1. **Dosya** menüsünde, **Yeni**, **Proje**' yi seçin.

   2. **Yüklü şablonlar**altında **Visual C#** veya **Visual Basic**seçin. Orta sütundaki **sınıf kitaplığı**' nı seçin.

   3. Yeni bir çözüm oluşturmak mı yoksa zaten açtığınız bir VSıX çözümüne bir bileşen eklemek mi istediğinizi belirtmek için **çözüm** ayarlayın.

   4. Proje adını ve konumunu ayarlayıp Tamam ' a tıklayın.

2. Aşağıdaki başvuruları projenize ekleyin.

   |                                                                                                    Başvuru                                                                                                    |                                                                                                  Bunu yapmanıza izin verir                                                                                                  |
   |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                                                                                        System. ComponentModel. Composition                                                                                        |                                         [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)kullanarak bileşenleri tanımlayın.                                          |
   |                                                                                      Microsoft. VisualStudio. Uml. Interfaces                                                                                      |                                                                                        Model öğelerinin özelliklerini okuyun ve değiştirin.                                                                                         |
   |                                                                             Microsoft. VisualStudio. mimari Turetools. Extensibility                                                                              |                                                                                      Model öğeleri oluşturun, diyagramlarda şekilleri değiştirin.                                                                                       |
   |                                                                                  Microsoft. VisualStudio. model. SDK. sürümünüze                                                                                  | Model olay işleyicilerini tanımlayın.<br /><br /> Modelinizdeki değişiklikler serisini yalıtır. Daha fazla bilgi için bkz. [işlemleri kullanarak UML model güncelleştirmelerini bağlama](../modeling/link-uml-model-updates-by-using-transactions.md). |
   |                                                            Microsoft. VisualStudio. model. SDK. diyagramlar. sürümünüze<br /><br /> (her zaman gerekli değil)                                                             |                                                                                   Hareket işleyicileri için ek Diyagram öğelerine erişin.                                                                                   |
   | Microsoft. VisualStudio. mimari Turetools. Extensibility. Layer<br /><br /> Yalnızca Katman diyagramlarındaki komutlar için gereklidir. Daha fazla bilgi için bkz. [Katman diyagramlarını genişletme](../modeling/extend-layer-diagrams.md). |                                                                                             Bir katman diyagramında komutları tanımlayın.                                                                                              |

3. Projeye bir sınıf dosyası ekleyin ve içeriğini aşağıdaki koda ayarlayın.

   > [!NOTE]
   > Ad alanı, sınıf adı ve tarafından döndürülen değeri tercihinize göre değiştirin `Text` .
   >
   >  Birden çok komut tanımlarsanız, bunlar menüde sınıf adlarının alfabetik düzeninde görünürler.

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

    Yöntemlere yerleştirilecek hakkında daha fazla bilgi için, bkz. [menü komutunu uygulama](#Implementing).

   Menü komutunu bir VSıX projesine eklemeniz gerekir ve bu, komutu yüklemek için kapsayıcı olarak davranır. İsterseniz, diğer bileşenleri aynı VSıX 'e ekleyebilirsiniz.

#### <a name="to-add-a-menu-command-to-a-vsix-project"></a>Bir VSıX projesine bir menü komutu eklemek için

1. Kendi VSıX ile menü komutunu oluşturduysanız, bu yordama ihtiyacınız yoktur.

2. Çözümünüz bir tane içermiyorsa, bir VSıX projesi oluşturun.

    1. **Çözüm Gezgini**, çözümün kısayol menüsünde, **Ekle**, **Yeni proje**' yi seçin.

    2. **Yüklü şablonlar**altında **Visual C#** veya **Visual Basic**' i genişletin, ardından **genişletilebilirlik**' i seçin. Orta sütunda **VSIX projesi**' ni seçin.

3. Çözüm Gezgini, VSıX projesinin kısayol menüsünde **Başlangıç projesi olarak ayarla**' yı seçin.

4. Açık **kaynak. Extension. valtmanifest**.

    1. **Meta veriler** sekmesinde VSIX için bir ad belirleyin.

    2. **Hedefleri yüklensin** sekmesinde, Visual Studio sürümlerini hedef olarak ayarlayın.

    3. **Varlıklar** sekmesinde **Yeni**' yi seçin ve iletişim kutusunda, şunu ayarlayın:

         **Tür**  =  **MEF bileşeni**

         **Kaynak**  =  **Geçerli çözümdeki bir proje**

         **Proje**  =  *Sınıf kitaplığı projeniz*

## <a name="implementing-the-menu-command"></a><a name="Implementing"></a> Menü komutunu uygulama
 Menü komut sınıfı için gerekli yöntemleri uygular <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> .

|İmza|Description|
|-|-|
|`string Text { get; }`|Menü öğesinin etiketini döndürün.|
|`void QueryStatus(IMenuCommand command);`|Kullanıcı diyagramda sağ tıkladığında çağırılır.<br /><br /> Bu yöntem modeli değiştirmemelidir.<br /><br /> `DiagramContext.CurrentDiagram.SelectedShapes`Komutun görünmesini ve etkinleştirilmesini isteyip istemediğinizi öğrenmek için kullanın.<br /><br /> Kurmak<br /><br /> -   `command.Visible``true`Kullanıcı diyagramda sağ tıkladığında komutun menüde görünmesi gerekir<br />-   `command.Enabled``true`Kullanıcı menüdeki komutuna tıkladıysanız<br />-   `command.Text` Menü etiketini dinamik olarak ayarlamak için|
|`void Execute (IMenuCommand command);`|Görünür ve etkinse Kullanıcı menü öğesine tıkladığında çağırılır.|

### <a name="accessing-the-model-in-code"></a>Koddaki modele erişme
 Aşağıdaki bildirimi menü komut sınıfınıza dahil etme:

```
[Import] public IDiagramContext DiagramContext { get; set; }
```

 ...

 Bildirimi, `IDiagramContext` metotlarda diyagrama, geçerli seçime ve modele erişen kod yazmanıza izin verir:

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())
{ IElement element = shape.Element; ... }
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IElement element in modelStore.AllInstances<IUseCase>()) {...}
```

### <a name="navigating-and-updating-the-model"></a>Model gezinme ve güncelleştirme
 UML modelinin öğeleri API aracılığıyla kullanılabilir. Geçerli seçimden veya modelin kökünden diğer tüm öğelere erişebilirsiniz. Daha fazla bilgi için bkz [. UML](../modeling/navigate-the-uml-model.md) [API Ile programlama ve programlama](../modeling/programming-with-the-uml-api.md).

 Bir sıralı diyagram ile uğraşıyorsanız [UML API 'sini kullanarak UML sıra diyagramlarını da düzenleme](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)bölümüne bakın.

 Ayrıca API, öğelerin özelliklerini değiştirmenizi, öğeleri ve ilişkileri silmenizi ve yeni öğeler ve ilişkiler oluşturmanızı sağlar.

 Varsayılan olarak, Execute yönteminde yaptığınız her değişiklik ayrı bir işlemde gerçekleştirilir. Kullanıcı her değişikliği ayrı olarak geri alabilir. Değişiklikleri tek bir işlemde gruplandırmak isterseniz, <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoTransaction> [Işlem kullanarak UML model güncelleştirmelerini bağlama](../modeling/link-uml-model-updates-by-using-transactions.md)bölümünde açıklandığı gibi bir kullanın.

### <a name="use-the-ui-thread-for-updates"></a>Güncelleştirmeler için UI Iş parçacığını kullanma
 Bazı durumlarda, bir arka plan iş parçacığından modelde güncelleştirme yapmak yararlı olabilir. Örneğin, komutunuz yavaş bir kaynaktaki verileri yüklerse, kullanıcının sürmekte olan değişiklikleri görebilmesi ve gerekirse işlemi iptal edebilmesi için bir parantez içine bir iş parçacığında yüklemeyi yapabilirsiniz.

 Ancak, model deposunun iş parçacığı güvenli olmadığı farkında olmalısınız. Güncelleştirme yapmak için Kullanıcı arabirimi (UI) iş parçacığını her zaman kullanmanız gerekir ve mümkünse arka plan işlemi devam ederken kullanıcının düzenlemeler yapmasını önleyin. Bir örnek için bkz. [arka plan iş parçacığından UML modelini güncelleştirme](../modeling/update-a-uml-model-from-a-background-thread.md).

## <a name="executing-the-menu-command"></a><a name="Executing"></a> Menü komutu yürütülüyor
 Test amaçları için, komut hata ayıklama modunda komutunu yürütün.

#### <a name="to-test-the-menu-command"></a>Menü komutunu test etmek için

1. **F5**tuşuna basın veya **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat**' ı seçin.

     Deneysel bir örneği [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] başlar.

     **Sorun giderme**: yeni bir başlamazsa [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :

    - Birden çok projeniz varsa, VSıX projesinin çözümün başlangıç projesi olarak ayarlandığından emin olun.

    - Çözüm Gezgini, başlangıç veya yalnızca projenin kısayol menüsünde **Özellikler**' i seçin. Proje özellikleri düzenleyicisinde **Hata Ayıkla** sekmesini seçin. **Dış program Başlat** alanındaki dizenin, genellikle tam yol adı olduğundan emin olun [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :

         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. Deneysel içinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , bir modelleme projesi açın veya oluşturun ve bir modelleme diyagramı açın veya oluşturun. Menü komut sınıfınızın özniteliklerinde listelenen türlerden birine ait bir diyagram kullanın.

3. Diyagram üzerinde herhangi bir yerde kısayol menüsünü açın. Komutunuz menüde görünmelidir.

     **Sorun giderme**: komut menüde görünmezse şunları yaptığınızdan emin olun:

    - Menü komut projesi, VSıX projesindeki **kaynak. Extensions. manifest** içindeki **VARLıKLAR** sekmesinde bir MEF bileşeni olarak listelenir.

    - `Import`Ve `Export` özniteliklerinin parametreleri geçerlidir.

    - Yöntemi ' i `QueryStatus` ayarlamadır `command` .`Enabled` veya `Visible` alanları `false` .

    - Kullandığınız model diyagramın türü (UML sınıfı, sırası, vb.) menü komut sınıfı özniteliklerinden biri olarak listelenir `[ClassDesignerExtension]` `[SequenceDesignerExtension]` ve bu şekilde devam eder.

## <a name="installing-and-uninstalling-an-extension"></a><a name="Installing"></a> Uzantı yükleme ve kaldırma
 Bir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] uzantıyı, hem kendi bilgisayarınıza hem de diğer bilgisayarlara yükleyebilirsiniz.

#### <a name="to-install-an-extension"></a>Uzantı yüklemek için

1. Bilgisayarınızda, VSıX projeniz tarafından oluşturulan **. vsix** dosyasını bulun.

    1. **Çözüm Gezgini**, VSIX projesinin kısayol menüsünde **klasörü Windows Gezgini 'nde aç**' ı seçin.

    2. Dosya ** \\ \* bin \\ **' i_Proje_**. vsix** ' i bulun

2. **. Vsix** dosyasını, uzantıyı yüklemek istediğiniz hedef bilgisayara kopyalayın. Bu, kendi bilgisayarınız veya başka bir tane olabilir.

     Hedef bilgisayar, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **kaynak. Extension. valtmanifest**içinde belirttiğiniz sürümlerden birine sahip olmalıdır.

3. Hedef bilgisayarda, örneğin çift tıklayarak **. vsix** dosyasını açın.

     **Visual Studio Uzantı Yükleyicisi** açılır ve uzantıyı yüklüyor.

4. Başlatın veya yeniden başlatın [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] .

#### <a name="to-uninstall-an-extension"></a>Bir uzantıyı kaldırmak için

1. **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler**' i seçin.

2. **Yüklü uzantıları**genişletin.

3. Uzantıyı seçin ve ardından **Kaldır**' ı seçin.

   Nadiren, hatalı bir uzantı yükleme başarısız olur ve hata penceresinde bir rapor oluşturur, ancak Uzantı Yöneticisi 'nde görünmez. Bu durumda, dosyayı öğesinden silerek uzantıyı kaldırabilirsiniz:

   *% LocalAppData%* **\Local\microsoft\visualstudio \\ [sürüm] \Extensions**

## <a name="example"></a><a name="MenuExample"></a> Örneğinde
 Aşağıdaki örnek, bir sınıf diyagramında iki öğenin adlarını değiş tokuş edecek bir menü komutu için kodu gösterir. Bu kodun bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantı projesinde oluşturulması ve önceki bölümlerde açıklandığı gibi yüklenmesi gerekir.

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
 [Modelleme uzantısı tanımlama ve](../modeling/define-and-install-a-modeling-extension.md) [oluşturma UML modellerini ve Diyagramları Genişletme](../modeling/extend-uml-models-and-diagrams.md) [Modelleme diyagramında bir hareket işleyicisi tanımlama bir model oluşturma diyagramı](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) tanımlama [Özel Modelleme Araç kutusu Öğesı](../modeling/define-a-custom-modeling-toolbox-item.md) tanımlama UML [modelleriyle ilgili](../modeling/define-validation-constraints-for-uml-models.md) [olarak UML API](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md) [programlama](../modeling/programming-with-the-uml-api.md)
 