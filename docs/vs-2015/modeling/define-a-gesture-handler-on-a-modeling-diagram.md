---
title: Modelleme Diyagramında hareket işleyicisi tanımlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, double-click
- UML - extending, drag and drop
ms.assetid: e5e1d70a-3539-4321-a3b1-89e86e4d6430
caps.latest.revision: 36
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3e448b14a2a24994b9f03a569b0bb568d538bc69
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722179"
---
# <a name="define-a-gesture-handler-on-a-modeling-diagram"></a>Modelleme diyagramında hareket işleyicisi tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da, kullanıcı çift tıkladığında veya öğeleri bir UML diyagram üzerine sürüklediğinde gerçekleştirilen komutları tanımlayabilirsiniz. Bu uzantılar bir Visual Studio Tümleştirme Uzantısı'na paketini ([VSIX](http://go.microsoft.com/fwlink/?LinkId=160780)) ve diğer Visual Studio kullanıcılarına dağıtabilirsiniz.  
  
 Diyagram türü ve sürüklemek istediğiniz öğe türü için yerleşik davranış zaten yoksa ekleyin veya bu davranışı geçersiz kılmak mümkün olmayabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 Bkz: [gereksinimleri](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="creating-a-gesture-handler"></a>Hareket İşleyici oluşturma  
 Bir UML tasarımcısı için bir hareket işleyicisi tanımlama için hareket işleyicisinin davranışını tanımlayan bir sınıf oluşturun ve bu sınıfı bir Visual Studio Tümleştirme Uzantısı'na (VSIX) katıştırmanız gerekir. VSIX işleyiciyi yükleyebilecek bir kapsayıcı gibi davranır. Bir hareket işleyicisini tanımlamanın iki farklı yöntemi vardır:  
  
-   **Bir proje şablonunu kullanarak kendi VSIX'inde bir hareket işleyici oluşturun.** Bu daha hızlı bir yöntemdir. Uzantı doğrulama uzantıları, özel araç kutusu öğeleri veya menü komutları gibi diğer tür işleyicinizi birleştirmek istemiyorsanız, bunu kullanın.  
  
-   **Ayrı hareket işleyicisi ve VSIX projeleri oluşturun.** Aynı VSIX içinde kaç tür uzantıyı birleştirmek istiyorsanız bu yöntemi kullanın. Örneğin, hareket işleyiciniz modelin belirli kısıtlamalar ortaya koyacağını ön görüyorsa bunu bir doğrulama yöntemi olarak aynı VSIX içine katıştırabilirsiniz.  
  
#### <a name="to-create-a-gesture-handler-in-its-own-vsix"></a>Kendi VSIX'inde bir hareket işleyicisi oluşturmak için  
  
1. İçinde **yeni proje** iletişim kutusunun **modelleme projeleri**seçin **hareket uzantısı**.  
  
2. Açık **.cs** yeni projeye dosya ve değiştirme `GestureExtension` hareket işleyicinizi uygulamak için sınıfı.  
  
    Daha fazla bilgi için [jest işleyici uygulama](#Implementing).  
  
3. F5 tuşuna basarak hareket işleyicisini test edin. Daha fazla bilgi için [hareket işlecini yürütme](#Executing).  
  
4. Hareket işleyicisini dosyasını kopyalayarak başka bir bilgisayara yükleyin. **bin\\\*\\\*.vsix** projeniz tarafından oluşturulmuş. Daha fazla bilgi için [yükleme ve kaldırma uzantı](#Installing).  
  
   Alternatif yordam şöyledir:  
  
#### <a name="to-create-a-separate-class-library-dll-project-for-the-gesture-handler"></a>Hareket işleyicisi için ayrı bir sınıf kitaplığı (DLL) projesi oluşturmak için  
  
1. Bir sınıf kitaplığı projesini yeni bir oluşturma [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözümü ya da var olan bir çözümde.  
  
   1.  Üzerinde **dosya** menüsünde seçin **yeni**, **proje**.  
  
   2.  Altında **yüklü şablonlar**, genişletme **Visual C#** veya **Visual Basic**, ardından Orta sütundaki seçin **sınıf kitaplığı**.  
  
2. Projenize aşağıdaki başvuruları ekleyin.  
  
    `Microsoft.VisualStudio.Modeling.Sdk.[version]`  
  
    `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]`  
  
    `Microsoft.VisualStudio.ArchitectureTools.Extensibility`  
  
    `Microsoft.VisualStudio.Uml.Interfaces`  
  
    `System.ComponentModel.Composition`  
  
    `System.Windows.Forms`  
  
    `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer` Yalnızca katman diyagramlarını genişletirken – bu gereksinim. Daha fazla bilgi için [katman diyagramlarını genişletme](../modeling/extend-layer-diagrams.md).  
  
3. Projeye bir sınıf dosyası ekleyin ve içeriğini aşağıdaki koda göre ayarlayın.  
  
   > [!NOTE]
   >  Ad alanını ve sınıf adını tercihinize göre değiştirin.  
  
   ```  
   using System.ComponentModel.Composition;  
   using System.Linq;  
   using System.Collections.Generic;  
   using Microsoft.VisualStudio.Modeling.Diagrams;  
   using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;  
   using Microsoft.VisualStudio.Modeling;  
   using Microsoft.VisualStudio.Uml.Classes;  
   // ADD other UML namespaces if required  
  
   namespace MyGestureHandler // CHANGE  
   {  
     // DELETE any of these attributes if the handler  
     // should not work with some types of diagram.  
     [ClassDesignerExtension]  
     [ActivityDesignerExtension]  
     [ComponentDesignerExtension]  
     [SequenceDesignerExtension]  
     [UseCaseDesignerExtension]  
     // [LayerDesignerExtension]  
  
     // Gesture handlers must export IGestureExtension:  
     [Export(typeof(IGestureExtension))]  
     // CHANGE class name  
     public class MyGesture1 : IGestureExtension  
     {  
       [Import]  
       public IDiagramContext DiagramContext { get; set; }  
  
       /// <summary>  
       /// Called when the user double-clicks on the diagram  
       /// </summary>  
       /// <param name="targetElement"></param>  
       /// <param name="diagramPointEventArgs"></param>  
       public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)  
       {  
         // CHANGE THIS CODE FOR YOUR APPLICATION.  
  
         // Get the target shape, if any. Null if the target is the diagram.  
         IShape targetIShape = targetElement.CreateIShape();  
  
         // Do something...  
       }  
  
       /// <summary>  
       /// Called repeatedly when the user drags from anywhere on the screen.  
       /// Return value should indicate whether a drop here is allowed.  
       /// </summary>  
       /// <param name="targetMergeElement">References the element to be dropped on.</param>  
       /// <param name="diagramDragEventArgs">References the element to be dropped.</param>  
       /// <returns></returns>  
       public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)  
       {  
         // CHANGE THIS CODE FOR YOUR APPLICATION.  
  
         // Get the target element, if any. Null if the target is the diagram.  
         IShape targetIShape = targetMergeElement.CreateIShape();  
  
         // This example allows drag of any UML elements.  
         return GetModelElementsFromDragEvent(diagramDragEventArgs).Count() > 0;  
       }  
  
       /// <summary>  
       /// Execute the action to be performed on the drop.  
       /// </summary>  
       /// <param name="targetDropElement"></param>  
       /// <param name="diagramDragEventArgs"></param>  
       public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)  
       {  
         // CHANGE THIS CODE FOR YOUR APPLICATION.  
       }  
  
       /// <summary>  
       /// Retrieves UML IElements from drag arguments.  
       /// Works for drags from UML diagrams.  
       /// </summary>  
       private IEnumerable<IElement> GetModelElementsFromDragEvent  
               (DiagramDragEventArgs dragEvent)  
       {  
         //ElementGroupPrototype is the container for  
         //dragged and copied elements and toolbox items.  
         ElementGroupPrototype prototype =  
            dragEvent.Data.  
            GetData(typeof(ElementGroupPrototype))  
                 as ElementGroupPrototype;  
         // Locate the originals in the implementation store.  
         IElementDirectory implementationDirectory =  
            dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;  
  
         return prototype.ProtoElements.Select(  
           prototypeElement =>  
           {  
             ModelElement element = implementationDirectory  
               .FindElement(prototypeElement.ElementId);  
             ShapeElement shapeElement = element as ShapeElement;  
             if (shapeElement != null)  
             {  
               // Dragged from a diagram.  
               return shapeElement.ModelElement as IElement;  
             }  
             else  
             {  
               // Dragged from UML Model Explorer.  
               return element as IElement;  
             }  
           });  
       }  
  
     }  
   }  
  
   ```  
  
    Yöntemlere konulacaklar hakkında daha fazla bilgi için bkz. [jest işleyici uygulama](#Implementing).  
  
   Menü komutunuzu komutu yüklemek için bir kapsayıcı görevi gören bir VSIX projesine eklemeniz gerekir. İsterseniz, aynı VSIX içine diğer bileşenleri dahil edebilirsiniz.  
  
#### <a name="to-add-a-separate-gesture-handler-to-a-vsix-project"></a>Bir VSIX projesine ayrı bir hareket işleyici eklemek için  
  
1.  Kendi VSIX'i olan bir hareket işleyicisi oluşturduysanız, bu yordama ihtiyacınız yoktur.  
  
2.  Çözümünüz zaten içermiyorsa, bir VSIX projesi oluşturun.  
  
    1.  İçinde **Çözüm Gezgini**, çözümün kısayol menüsünde **Ekle**, **yeni proje**.  
  
    2.  Altında **yüklü şablonlar**, genişletme **Visual C#** veya **Visual Basic**, ardından **genişletilebilirlik**. Orta sütundaki seçin **VSIX projesi**.  
  
3.  VSIX projesinin çözümün başlangıç projesi olarak ayarlayın.  
  
    -   Çözüm Gezgini'nde VSIX projesinin kısayol menüsünde seçin **başlangıç projesi olarak ayarla**.  
  
4.  İçinde **source.extension.vsixmanifest**, hareket işleyicisi sınıf kitaplığı projesini MEF Bileşeni ekleyin:  
  
    1.  Üzerinde **meta verileri** sekmesinde, VSIX için bir ad belirleyin.  
  
    2.  Üzerinde **hedefleri Yükle** sekmesinde, hedefler olarak Visual Studio sürümleri ayarlayın.  
  
    3.  Üzerinde **varlıklar** sekmesini, bir **yeni**ve iletişim kutusunda şunu ayarlayın:  
  
         **Tür** = **MEF Bileşeni**  
  
         **Kaynak** = **mevcut çözümde bir proje**  
  
         **Proje** = *, sınıf kitaplığı projesi*  
  
##  <a name="Executing"></a> Hareket işlecini yürütme  
 Test amaçları için hareket işleyicinizi hata ayıklama modunda yürütün.  
  
#### <a name="to-test-the-gesture-handler"></a>Hareket işleyicisini test etmek için  
  
1. Tuşuna **F5**, veya **hata ayıklama** menüsünde tıklatın **hata ayıklamayı Başlat**.  
  
    Deneysel örneği [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] başlatır.  
  
    **Sorun giderme**: yeni [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] başlamıyor:  
  
   -   Birden fazla projeniz varsa, VSIX projesinin çözümün başlangıç projesi olarak ayarlandığından emin olun.  
  
   -   Çözüm Gezgini'nde başlatmanın veya yalnızca projenin kısayol menüsünde Özellikler'i seçin. Proje Özellikleri düzenleyicisinden seçin **hata ayıklama** sekmesi. Emin olun dizesinde **harici program Başlat** alandır tam yol adını [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], genellikle:  
  
        `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`  
  
2. Deneysel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], açın veya bir modelleme projesi oluşturmak ve açmak veya bir modelleme diyagramı oluşturun. Hareket işleyici sınıfınızın özniteliklerinde listelenen türlerden ait bir diyagram kullanın.  
  
3. Herhangi bir diyagram üzerine çift tıklayın. Çift tıklatma işleyiciniz çağrılmalıdır.  
  
4. Bir öğe, UML Gezgini'nde diyagram üzerine sürükleyin. Sürükleme işleyiciniz çağrılmalıdır.  
  
   **Sorun giderme**: hareket işleyicisi çalışmıyorsa emin olun:  
  
-   Hareket işleyicisi projesini MEF Bileşeni olarak listelenir **varlıklar** sekmesinde **source.extensions.manifest** VSIX projesinde.  
  
-   Tüm parametreleri `Import` ve `Export` öznitelikleri geçerlidir.  
  
-   `CanDragDrop` Yöntemi döndürmez `false`.  
  
-   Bir türü modelin diyagramı (UML sınıfı, dizisi ve benzeri) kullanıyorsanız bir hareket işleyicisi sınıfı öznitelikleri [ClassDesignerExtension], [SequenceDesignerExtension] vb. listelenir.  
  
-   Bu tür hedef ve bırakılan öğe için zaten tanımlanmış yerleşik işlevi yoktur.  
  
##  <a name="Implementing"></a> Hareket işlecini uygulama  
  
### <a name="the-gesture-handler-methods"></a>Hareket işleyici yöntemleri  
 Hareket işleyicisi sınıfı uygular ve dışarı aktarır <xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement.IGestureExtension>. Tanımlamanız gereken yöntemler aşağıdaki gibidir:  
  
|||  
|-|-|  
|`bool CanDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|Dönüş `true` içinde başvurulmuş kaynak öğeye izin vermek için `dragEvent` bu hedefte bırakılacak.<br /><br /> Bu yöntem, modele değişiklik yapmamalısınız. Kullanıcı fareyi hareket ettirdikçe okun durumunu belirlemek için kullanıldığından, hızlı çalışması.|  
|`void OnDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|İçinde başvurulmuş kaynak nesnesine dayalı modeli güncelleştirin `dragEvent`hem de hedef.<br /><br /> Kullanıcının fareyi sürükleyip ardından bıraktığında çağrılır.|  
|`void OnDoubleClick (ShapeElement target, DiagramPointEventArgs pointEvent)`|`target` kullanıcının çift tıklattığı şekildir.|  
  
 Bir .NET sınıf görünümü ve benzeri birçok farklı dosya gibi öğelerin, diğer düğümler sadece UML'i değil de kabul edebilen işleyiciler yazabilirsiniz. Kullanıcı bu öğelerden herhangi birinin yazmanızı bir UML diyagram üzerine sürükleyebilirsiniz bir `OnDragDrop` seri hale getirilmiş biçimlerini çözebilen yöntemi. Çözümleme yöntemleri bir öğe türünden diğerine farklılık gösterir.  
  
 Bu yöntemlerin parametreleri şunlardır:  
  
-   `ShapeElement target`. Şekil veya diyagram üzerine kullanıcı birşey sürüklediği.  
  
     `ShapeElement` bir sınıfta altını çizen UML modelleme araçları. UML model ve diyagramlarının tutarsız bir duruma koymanın riskini azaltmak için bu sınıfın yöntemlerini doğrudan kullanmamanızı öneririz. Bunun yerine öğenin kaydırma bir `IShape`ve sonra da açıklanmış yöntemleri kullanın [diyagramlar üzerinde bir UML modeli görüntüleme](../modeling/display-a-uml-model-on-diagrams.md).  
  
    -   Elde etmek için bir `IShape`:  
  
        ```  
        IShape targetIShape = target.CreateIShape(target);  
        ```  
  
    -   Sürükleme tarafından hedeflenen bir model öğesi elde etmek veya çift tıklama işlemleri için:  
  
        ```  
        IElement target = targetIShape.Element;  
        ```  
  
         Bu daha belirli bir öğe türüne çevirebilirsiniz.  
  
    -   UML modeli içeren bir UML model deposu elde etmek için:  
  
        ```  
        IModelStore modelStore =   
          targetIShape.Element.GetModelStore();   
        ```  
  
    -   Ana bilgisayar ve hizmet sağlayıcısına erişim elde etmek için:  
  
        ```  
        target.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE  
        ```  
  
-   `DiagramDragEventArgs eventArgs`. Bu parametre sürükleme işleminin kaynak nesnesinin seri hala getirilmiş biçimini taşır:  
  
    ```  
    System.Windows.Forms.IDataObject data = eventArgs.Data;    
    ```  
  
     Birçok farklı türdeki öğeleri, farklı bölümlerinden bir diyagram üzerine sürükleyebilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], veya Windows masaüstünden. Farklı türde öğe içinde farklı yollarda kodlanır `IDataObject`. Öğeleri buradan ayıklamak için nesnenin uygun türünü belgelerine bakın.  
  
     Eğer kaynak nesneniz UML Model Gezgini'nden veya başka bir UML diyagramından sürüklenen bir UML öğesi ise, başvurmak [alma UML model öğelerini bilgisine](../modeling/get-uml-model-elements-from-idataobject.md).  
  
### <a name="writing-the-code-of-the-methods"></a>Yöntemlerin kodunu yazma  
 Okuma ve modeli güncelleştirmek için kod yazma hakkında daha fazla bilgi için bkz. [UML API ile programlama](../modeling/programming-with-the-uml-api.md).  
  
 Bir sürükleme işleminde model bilgilerine erişme hakkında daha fazla bilgi için bkz: [alma UML model öğelerini bilgisine](../modeling/get-uml-model-elements-from-idataobject.md).  
  
 Sıra diyagram ile uğraşıyorsanız, ayrıca bkz: [UML API kullanarak Düzenle UML sıralı diyagramlar](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).  
  
 Yöntemlerin parametrelerinin yanı sıra sınıfınızda, geçerli diyagrama ve modele erişimi sağlayan içeri aktarılan özellik bildirebilirsiniz.  
  
```  
[Import] public IDiagramContext DiagramContext { get; set; }  
```  
  
 Bildirimi `IDiagramContext` diyagrama, geçerli seçime ve modele erişen yöntemlerinizde kod yazmanıza olanak sağlar:  
  
```  
IDiagram diagram = this.DiagramContext.CurrentDiagram;  
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>)  
{ IElement element = shape.Element; ... }  
IModelStore modelStore = diagram.ModelStore;  
IModel model = modelStore.Root;  
foreach (IDiagram diagram in modelStore.Diagrams) {...}  
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}  
```  
  
 Daha fazla bilgi için [UML modelini gezme](../modeling/navigate-the-uml-model.md).  
  
##  <a name="Installing"></a> Yükleme ve bir uzantıyı kaldırma  
 Yükleyebileceğiniz bir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] hem kendi bilgisayarınıza hem de diğer bilgisayarlara uzantısı.  
  
#### <a name="to-install-an-extension"></a>Bir uzantı yüklemek için  
  
1.  Bilgisayarınızda, bulma **.vsix** VSIX projeniz tarafından oluşturulan dosya.  
  
    1.  İçinde **Çözüm Gezgini**, VSIX projesinin kısayol menüsünde **klasörü Windows Gezgini'nde Aç**.  
  
    2.  Dosyayı bulmak **bin\\\*\\**_projeniz_**.vsix**  
  
2.  Kopyalama **.vsix** uzantıyı yüklemek istediğiniz hedef bilgisayarın bir dosyaya. Bu sizin kendi bilgisayarınız veya başka bir tane olabilir.  
  
     Hedef bilgisayarda sürümlerinden biri olmalıdır [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] belirttiğiniz **source.extension.vsixmanifest**.  
  
3.  Hedef bilgisayarda açın **.vsix** dosya.  
  
     **Visual Studio Uzantı Yükleyicisi** açılır ve uzantıyı yükler.  
  
4.  Başlatın veya yeniden [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
#### <a name="to-uninstall-an-extension"></a>Bir uzantıyı kaldırmak için  
  
1. Üzerinde **Araçları** menüsünde seçin **Uzantılar ve güncelleştirmeler**.  
  
2. Genişletin **yüklü uzantıları**.  
  
3. Uzantıyı seçin ve ardından **kaldırma**.  
  
   Nadiren, hatalı bir uzantı yüklemede başarısız olur ve hata penceresinde bir rapor oluşturur ancak Uzantı Yöneticisi'nde görünmez. Bu durumda, dosyayı şuradan silerek uzantıyı kaldırabilirsiniz:  
  
   *% LocalAppData %* **\Local\Microsoft\VisualStudio\\[sürüm] \Extensions**  
  
##  <a name="DragExample"></a> Örnek  
 Aşağıdaki örnek nasıl oluştuğunu bileşen diyagramdan sürüklenen bileşenin bağlantı noktalarını ve parçaları temel bir sıralı diyagramda yaşam çizgilerini oluşturulacağını gösterir.  
  
 Test etmek için F5 tuşuna basın. Visual Studio deneysel örneği açılır. Bu örnekte, bir UML modeli açın ve bir bileşen diyagramı üzerinde bir bileşen oluşturun. Bu bileşeni bazı arayüzlere ve iç bileşen parçalarına ekleyin. Arabirimleri ve bölümleri seçin. Sonra arabirimleri ve parçaları bir sıralama diyagramına sürükleyin. (Sıralı diyagram ve sonra aşağı için sekmesinde kadar bileşen diyagramından sıra diyagramının içine sürükleyin.) Her arabirim ve parça için bir yaşam çizgisi görünecektir.  
  
 Sıralı diyagramlara bağlama etkileşimleri hakkında daha fazla bilgi için bkz: [UML API kullanarak Düzenle UML sıralı diyagramlar](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).  
  
```  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.Uml.Interactions;  
using Microsoft.VisualStudio.Uml.CompositeStructures;  
using Microsoft.VisualStudio.Uml.Components;  
  
/// <summary>  
/// Creates lifelines from component ports and parts.  
/// </summary>  
[Export(typeof(IGestureExtension))]  
[SequenceDesignerExtension]  
public class CreateLifelinesFromComponentParts : IGestureExtension  
{  
  [Import]  
  public IDiagramContext Context { get; set; }  
  
  /// <summary>  
  /// Called by the modeling framework when  
  /// the user drops something on a target.  
  /// </summary>  
  /// <param name="target">The target shape or diagram </param>  
  /// <param name="dragEvent">The item being dragged</param>  
  public void OnDragDrop(ShapeElement target,  
           DiagramDragEventArgs dragEvent)  
  {  
    ISequenceDiagram diagram = Context.CurrentDiagram  
            as ISequenceDiagram;  
    IInteraction interaction = diagram.Interaction;  
    if (interaction == null)  
    {  
      // Sequence diagram is empty: create an interaction.  
      interaction = diagram.ModelStore.Root.CreateInteraction();  
      interaction.Name = Context.CurrentDiagram.Name;  
      diagram.Bind(interaction);  
    }  
    foreach (IConnectableElement connectable in  
       GetConnectablesFromDrag(dragEvent))  
    {  
      ILifeline lifeline = interaction.CreateLifeline();  
      lifeline.Represents = connectable;  
      lifeline.Name = connectable.Name;  
    }  
  }  
  
  /// <summary>  
  /// Called by the modeling framework to determine whether  
  /// the user can drop something on a target.  
  /// Must not change anything.  
  /// </summary>  
  /// <param name="target">The target shape or diagram</param>  
  /// <param name="dragEvent">The item being dragged</param>  
  /// <returns>true if this item can be dropped on this target</returns>  
  public bool CanDragDrop(ShapeElement target,  
           DiagramDragEventArgs dragEvent)  
  {  
    IEnumerable<IConnectableElement> connectables = GetConnectablesFromDrag(dragEvent);  
    return connectables.Count() > 0;  
  }  
  
  ///<summary>  
  /// Get dragged parts and ports of an IComponent.  
  ///</summary>  
  private IEnumerable<IConnectableElement>  
    GetConnectablesFromDrag(DiagramDragEventArgs dragEvent)  
  {  
    foreach (IElement element in  
      GetModelElementsFromDragEvent(dragEvent))  
    {  
      IConnectableElement part = element as IConnectableElement;  
      if (part != null)  
      {  
        yield return part;  
      }  
    }  
  }  
  
  /// <summary>  
  /// Retrieves UML IElements from drag arguments.  
  /// Works for drags from UML diagrams.  
  /// </summary>  
  private IEnumerable<IElement> GetModelElementsFromDragEvent  
          (DiagramDragEventArgs dragEvent)  
  {  
    //ElementGroupPrototype is the container for  
    //dragged and copied elements and toolbox items.  
    ElementGroupPrototype prototype =  
       dragEvent.Data.  
       GetData(typeof(ElementGroupPrototype))  
            as ElementGroupPrototype;  
    // Locate the originals in the implementation store.  
    IElementDirectory implementationDirectory =  
       dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;  
  
    return prototype.ProtoElements.Select(  
      prototypeElement =>  
      {  
        ModelElement element = implementationDirectory  
          .FindElement(prototypeElement.ElementId);  
        ShapeElement shapeElement = element as ShapeElement;  
        if (shapeElement != null)  
        {  
          // Dragged from a diagram.  
          return shapeElement.ModelElement as IElement;  
        }  
        else  
        {  
          // Dragged from UML Model Explorer.  
          return element as IElement;  
        }  
      });  
  }  
  
  public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)  
  {  
  }  
}  
  
```  
  
 Kodu `GetModelElementsFromDragEvent()` açıklanan [alma UML model öğelerini bilgisine](../modeling/get-uml-model-elements-from-idataobject.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Modelleme Uzantısı Tanımlama ve yükleme](../modeling/define-and-install-a-modeling-extension.md)   
 [UML modellerini ve diyagramları genişletme](../modeling/extend-uml-models-and-diagrams.md)   
 [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [UML modelleri için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md)   
 [UML API ile programlama](../modeling/programming-with-the-uml-api.md)



