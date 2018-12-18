---
title: Katman diyagramlarına komut ve hareket ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams, adding custom commands
- layer diagrams, adding custom gestures
ms.assetid: ac9c417b-0b40-4a90-86f5-ee3cbdce030b
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ae57d950b20fc6e342056b8c89738fa895c48c28
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733384"
---
# <a name="add-commands-and-gestures-to-layer-diagrams"></a>Katman diyagramlarına komut ve hareket ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bağlam menüsü komutları tanımlayabilir ve hareket işleyicileri Visual Studio'da katman diyagramları üzerinde. Bu uzantıları içinde bir Visual Studio Tümleştirme Uzantısı (diğer Visual Studio kullanıcılarına dağıtabileceğiniz VSIX) paketleyebilirsiniz.  
  
 İsterseniz, aynı Visual Studio projesinde birkaç komut ve hareket işleyici tanımlayabilirsiniz. Ayrıca, gibi birçok projeyi bir VSIX içinde birleştirebilirsiniz. Örneğin, katman komutlarını, etki alanına özgü dili ve UML şemaları için komutları içeren tek bir VSIX tanımlayabilirsiniz.  
  
> [!NOTE]
>  Ayrıca, hangi kullanıcıların kaynak kodu katman diyagramları ile karşılaştırıldığı mimari doğrulamayı da özelleştirebilirsiniz. Mimari doğrulama ayrı bir Visual Studio projesinde tanımlamanız gerekir. Diğer uzantılarla aynı vsıx'e ekleyebilirsiniz. Daha fazla bilgi için [katman diyagramlarına özel mimari doğrulaması ekleme](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).  
  
## <a name="requirements"></a>Gereksinimler  
 Bkz: [gereksinimleri](../modeling/extend-layer-diagrams.md#prereqs).  
  
## <a name="defining-a-command-or-gesture-in-a-new-vsix"></a>Yeni VSIX'de komut veya hareket tanımlama  
 Bir uzantı oluşturmanın en hızlı yolu, proje şablonu kullanmaktır. Bu seçenek, kodu ve VSIX bildirimini aynı projeye yerleştirir.  
  
#### <a name="to-define-an-extension-by-using-a-project-template"></a>Bir proje şablonunu kullanarak bir uzantısı tanımlamak için  
  
1. Kullanarak yeni çözümde bir proje oluşturma **yeni proje** komutunu **dosya** menüsü.  
  
2. İçinde **yeni proje** iletişim kutusunun **modelleme projeleri**, şunlardan birini seçin **katman Tasarımcı komut uzantısı** veya **katman Tasarımcı hareket uzantısı** .  
  
    Şablon, küçük bir iş örneği içeren bir proje oluşturur.  
  
3. Uzantıyı test etmek için basın **CTRL + F5** veya **F5**.  
  
    Deneysel örneği [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] başlatır. Bu örnekte, bir katman diyagramı oluşturun. Komut veya hareket uzantınızın Bu diyagramda çalışması gerekir.  
  
4. Deneysel örneği kapatın ve örnek kodu değiştirin. Daha fazla bilgi için [erişin ve güncelleştirme modelleri program kodunda katman](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
5. Aynı projeye daha fazla komut veya hareket işleyicileri ekleyebilirsiniz. Daha fazla bilgi için aşağıdaki bölümlerden birine bakın:  
  
    [Bir menü komutunu tanımlama](#command)  
  
    [Bir hareket işleyicisi tanımlama](#gesture)  
  
6. Ana örneğine uzantıyı yüklemek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], veya başka bir bilgisayarda Bul **.vsix** dosyası *bin\\*. Yüklemek istediğiniz bilgisayara kopyalayın ve ardından çift tıklayın. Kaldırmak için kullanın **Uzantılar ve güncelleştirmeler** üzerinde **Araçları** menüsü.  
  
## <a name="adding-a-command-or-gesture-to-a-separate-vsix"></a>Ayrı bir VSIX'e komut veya hareket ekleme  
 Komutların, katman doğrulayıcılarının ve diğer uzantıların bulunduğu bir VSIX oluşturmak istiyorsanız, VSIX tanımlamak için bir proje ve işleyiciler için ayrı projeler oluşturmanızı öneririz. Diğer modelleme uzantısı türleri hakkında daha fazla bilgi için bkz: [genişletmek UML modellerini ve diyagramları](../modeling/extend-uml-models-and-diagrams.md).  
  
#### <a name="to-add-layer-extensions-to-a-separate-vsix"></a>Ayrı bir VSIX'e katman uzantıları eklemek için  
  
1.  Yeni veya mevcut bir Visual Studio çözümünde bir sınıf kitaplığı projesi oluşturun. İçinde **yeni proje** iletişim kutusu, tıklayın **Visual C#** ve ardından **sınıf kitaplığı**. Bu projeyi içeren komut veya hareket işleyici sınıflarını.  
  
    > [!NOTE]
    >  Bir sınıf kitaplığında birden fazla komut veya hareket işleyici sınıf tanımlayabilirsiniz, ancak katman doğrulama sınıflarını ayrı sınıf kitaplığında tanımlamanız gerekir.  
  
2.  Çözümünüzde bir VSIX projesi oluşturun veya tanımlayın. Adlı bir dosyaya bir VSIX projesi içeren **source.extension.vsixmanifest**. Bir VSIX projesine eklemek için:  
  
    1.  İçinde **yeni proje** iletişim kutusunda **Visual C#**, ardından **genişletilebilirlik**ve ardından **VSIX projesi**.  
  
    2.  Çözüm Gezgini'nde VSIX projesini sağ tıklayın ve ardından **başlangıç projesi olarak ayarla**.  
  
    3.  Tıklayın **sürümleri seçin** emin olun **Visual Studio** denetlenir.  
  
3.  İçinde **source.extension.vsixmanifest**altında **varlıklar**Ekle komut veya hareket işleyicisi projesini MEF Bileşeni olarak.  
  
    1.  İçinde **varlıklar***.tab, seçin **yeni**.  
  
    2.  Konumunda **türü**seçin **Microsoft.VisualStudio.MefComponent**.  
  
    3.  Konumunda **kaynak**seçin **geçerli çözümde proje** ve komut veya hareket işleyici projenizin adını seçin.  
  
    4.  Dosyayı kaydedin.  
  
4.  Komut veya hareket işleyici projesine dönün ve aşağıdaki proje başvurularını ekleyin.  
  
|**Başvuru**|**Bunu yapmak sağlar**|  
|-------------------|------------------------------------|  
|Program Files\Microsoft Visual Studio [sürüm] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Katmanları oluşturma ve düzenleme|  
|Microsoft.VisualStudio.Uml.Interfaces|Katmanları oluşturma ve düzenleme|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility|Diyagramdaki şekilleri değiştirme|  
|System.ComponentModel.Composition|Yönetilen Genişletilebilirlik Çerçevesi (MEF) kullanarak bileşenleri tanımlayın|  
|Microsoft.VisualStudio.Modeling.Sdk.[version]|Modelleme uzantılarını tanımla|  
|Microsoft.VisualStudio.Modeling.Sdk.Diagrams. [sürüm]|Şekilleri ve diyagramları güncelleyin|  
  
1.  Uzantınız için kodu içermesi için C# sınıf kitaplığı projesi sınıfı dosyayı düzenleyin. Daha fazla bilgi için aşağıdaki bölümlerden birine bakın:  
  
     [Bir menü komutunu tanımlama](#command)  
  
     [Bir hareket işleyicisi tanımlama](#gesture)  
  
     Ayrıca bkz: [erişin ve güncelleştirme modelleri program kodunda katman](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
2.  Özelliği test etmek için CTRL + F5 veya F5 tuşuna basın. Deneysel örneği [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] açılır. Bu örnekte, oluşturma veya bir katman diyagramı açın.  
  
3.  Ana örneğine VSIX'i yüklemek [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], veya başka bir bilgisayarda Bul **.vsix** dosyası **bin** VSIX projesinin dizin. VSIX'i yüklemek istediğiniz bilgisayara kopyalayın. Windows Gezgini'nde (Windows 8'de dosya Gezgini) VSIX dosyasını çift tıklayın.  
  
     Kaldırmak için kullanın **Uzantılar ve güncelleştirmeler** üzerinde **Araçları** menüsü.  
  
##  <a name="command"></a> Bir menü komutunu tanımlama  
 Varolan bir hareket ya da komut projesine daha fazla menü komutu tanımları ekleyebilirsiniz. Her komut aşağıdaki özelliklere sahip bir sınıf tarafından tanımlanır:  
  
- Sınıf şu şekilde bildirilir:  
  
   `[LayerDesignerExtension]`  
  
   `[Export(typeof(ICommandExtension))]`  
  
   `public class`  *MyLayerCommand*  `: ICommandExtension { ... }`  
  
- Ad alanı ve sınıfın adı önemli değildir.  
  
- Uygulayan yöntemler `ICommandExtension` aşağıdaki gibidir:  
  
  -   `string Text {get;}` -Menüde görüntülenen etiketi.  
  
  -   `void QueryStatus(IMenuCommand command)` -Kullanıcı diyagrama ve komutun kullanıcının geçerli seçimi için görünür ve etkin olup olmayacağını belirler çağrılır.  
  
  -   `void Execute(IMenuCommand command)` -Kullanıcı komutu seçtiğinde çağrılır.  
  
- Geçerli seçimi belirlemek için alabilirsiniz `IDiagramContext`:  
  
   `[Import]`  
  
   `public IDiagramContext DiagramContext { get; set; }`  
  
   `...`  
  
   `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`  
  
  Daha fazla bilgi için [erişin ve güncelleştirme modelleri program kodunda katman](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
  Yeni bir komut eklemek için aşağıdaki örneği içeren yeni bir kod dosyası oluşturun. Ardından test edin ve düzenleyin.  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using System.ComponentModel.Composition;  
using System.Linq;  
  
namespace MyLayerExtension // Change to your preference.  
{  
  // This is a feature for Layer diagrams:  
  [LayerDesignerExtension]  
  // This feature is a menu command:  
  [Export(typeof(ICommandExtension))]  
  // Change the class name to your preference:  
  public class MyLayerCommand : ICommandExtension  
  {  
    [Import]  
    public IDiagramContext DiagramContext { get; set; }  
  
    [Import]  
    public ILinkedUndoContext LinkedUndoContext { get; set; }  
  
    // Menu command label:  
    public string Text  
    {  
      get { return "Duplicate layers"; }  
    }  
  
    // Called when the user right-clicks the diagram.  
    // Defines whether the command is visible and enabled.  
    public void QueryStatus(IMenuCommand command)  
    {   
      command.Visible =   
      command.Enabled = DiagramContext.CurrentDiagram  
        .SelectedShapes.Count() > 0;  
    }  
  
    // Called when the user selects the command.  
    public void Execute(IMenuCommand command)  
    {  
      // A selection of starting points:  
      IDiagram diagram = this.DiagramContext.CurrentDiagram;  
      ILayerModel lmodel = diagram.GetLayerModel();  
      foreach (ILayer layer in lmodel.Layers)  
      { // All layers in model.  
      }  
      // Updates should be performed in a transaction:  
      using (ILinkedUndoTransaction t =  
        LinkedUndoContext.BeginTransaction("copy selection"))  
      {  
        foreach (ILayer layer in   
          diagram.SelectedShapes  
            .Select(shape=>shape.GetLayerElement())  
            .Where(element => element is ILayer))  
        {  
          ILayer copy = lmodel.CreateLayer(layer.Name + "+");  
          // Position the shapes:  
          IShape originalShape = layer.GetShape();  
          copy.GetShape().Move(  
            originalShape.XPosition + originalShape.Width * 1.2,  
            originalShape.YPosition);  
        }  
        t.Commit();  
      }  
    }  
  }  
}  
```  
  
##  <a name="gesture"></a> Bir hareket işleyicisi tanımlama  
 Kullanıcı katman diyagramına öğeleri sürüklediğinde ve diyagramdaki kullanıcı herhangi bir yere tıkladığında bir hareket işleyicisi yanıt.  
  
 Mevcut komut veya hareket işleyicisi VSIX projeniz için bir hareket işleyicisi tanımlayan bir kod dosyası ekleyebilirsiniz:  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using System.ComponentModel.Composition;  
using System.Linq;  
namespace MyLayerExtensions // change to your preference  
{  
  [LayerDesignerExtension]  
  [Export(typeof(IGestureExtension))]  
  public class MyLayerGestureHandler : IGestureExtension  
  {  
  }  
}  
```  
  
 Hareket işleyicilerle ilgili aşağıdaki noktalara dikkat edin:  
  
- Üyeleri `IGestureExtension` aşağıdaki gibidir:  
  
   **OnDoubleClick** -kullanıcı diyagrama herhangi bir yeri çift tıkladığında çağrılır.  
  
   **CanDragDrop** - art arda kullanıcı bir öğeyi diyagram üzerine sürüklerken fareyi hareket ettirdikçe denir. Hızlı çalışması gerekir.  
  
   **OnDragDrop** -kullanıcı diyagrama bir öğe bıraktığında çağrılır.  
  
- Her yöntem için ilk bağımsız değişken bir `IShape`, öğesinden, katman öğesini elde edebilirsiniz. Örneğin:  
  
  ```  
  public void OnDragDrop(IShape target, IDataObject data)  
  {  
      ILayerElement element = target.GetLayerElement();  
      if (element is ILayer)  
      {  
          // ...  
      }  
  }  
  ```  
  
- Bazı sürüklenen öğe türlerine ilişkin işleyiciler zaten tanımlanmış. Örneğin, kullanıcı öğeleri Çözüm Gezgini'nden bir katman diyagramına sürükleyebilirsiniz. Bu öğe türleri için sürükleme işleyicisi tanımlayamazsınız. Bu gibi durumlarda, `DragDrop` yöntemleri çağrılmaz.  
  
  Diyagram üzerine sürüklediğinizde, diğer öğelerin kodunu çözme hakkında daha fazla bilgi için bkz. [modelleme diyagramında hareket işleyicisi tanımlama](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Program kodunda katman modellerini gezinme ve güncelleştirme](../modeling/navigate-and-update-layer-models-in-program-code.md)   
 [Katman diyagramlarına özel mimari doğrulaması ekleme](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
 [Modelleme uzantısı tanımlama ve yükleme](../modeling/define-and-install-a-modeling-extension.md)



