---
title: MEF kullanarak DSL'nizi genişletme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e7be79a-53ab-4d79-863a-bef8d27839bd
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fd5e4727c4352ca27d905bad608c4a1c17284f9b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930652"
---
# <a name="extend-your-dsl-by-using-mef"></a>MEF kullanarak DSL'nizi genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yönetilen Genişletilebilirlik Çerçevesi (MEF) kullanarak, etki alanına özgü dil (DSL) genişletebilirsiniz. Sizin veya diğer geliştiriciler DSL tanımını ve program kodunu değiştirmeden DSL için uzantıları yazmak mümkün olacaktır. Bu tür uzantılar, menü komutlarını, sürükle ve bırak işleyicisi ve doğrulama içerir. Kullanıcılar DSL'nizi yükleyin ve ardından isteğe bağlı olarak uzantıları yükleyebilmek için mümkün olacaktır.  
  
 MEF DSL'nizi içinde etkinleştirdiğinizde, tüm DSL birlikte oluşturuldukları olsa bile ek olarak, bunu daha kolay bazı özellikler, DSL'nin, yazma için olabilir.  
  
 MEF hakkında daha fazla bilgi için bkz: [Yönetilen Genişletilebilirlik Çerçevesi (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>MEF tarafından genişletilmesi DSL'nizi etkinleştirmek için  
  
1. Adlı yeni bir klasör oluşturun **MefExtension** içinde **DslPackage** proje. Aşağıdaki dosyaları ekleyin:  
  
    Dosya adı: `CommandExtensionVSCT.tt`  
  
   > [!IMPORTANT]
   >  Bu dosyadaki DslPackage\GeneratedCode\Constants.tt içinde tanımlanan GUID CommandSetId aynı GUID'i ayarlayın  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#  
   // CmdSet Guid must be defined before master template is included  
   // This Guid must be kept synchronized with the CommandSetId Guid in Constants.tt  
   Guid guidCmdSet = new Guid ("00000000-0000-0000-0000-000000000000");  
   string menuidCommandsExtensionBaseId="0x4000";  
   #>  
   <#@ include file="DslPackage\CommandExtensionVSCT.tt" #>  
   ```  
  
    Dosya adı: `CommandExtensionRegistrar.tt`  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>  
   ```  
  
    Dosya adı: `ValidationExtensionEnablement.tt`  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>  
   ```  
  
    Dosya adı: `ValidationExtensionRegistrar.tt`  
  
    Bu dosya eklerseniz, doğrulama DSL'nizi anahtarları en az birini kullanarak etkinleştirmelisiniz **EditorValidation** DSL Gezgini içinde.  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>  
   ```  
  
    Dosya adı: `PackageExtensionEnablement.tt`  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>  
   ```  
  
2. Adlı yeni bir klasör oluşturun **MefExtension** içinde **Dsl** proje. Aşağıdaki dosyaları ekleyin:  
  
    Dosya adı: `DesignerExtensionMetaDataAttribute.tt`  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>  
   ```  
  
    Dosya adı: `GestureExtensionEnablement.tt`  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="Dsl\GestureExtensionEnablement.tt" #>  
   ```  
  
    Dosya adı: `GestureExtensionController.tt`  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="Dsl\GestureExtensionController.tt" #>  
   ```  
  
3. Adlı varolan dosyaya aşağıdaki satırı ekleyin **DslPackage\Commands.vsct**:  
  
   ```  
   <Include href="MefExtension\CommandExtensionVSCT.vsct"/>  
   ```  
  
    Var olan sonra satır Ekle `<Include>` yönergesi.  
  
4. `Open DslDefinition.dsl.`  
  
5. DSL Gezgini içinde seçin **Editor\Validation**.  
  
6. Özellikler penceresinde özelliklerinden en az birini adlı emin **kullanır...**  olduğu `true`.  
  
7. Çözüm Gezgini araç çubuğunda **tüm Şablonları Dönüştür**.  
  
    Paketinizle dosyalar her eklediğiniz dosyaların altında görünür.  
  
8. Derleme ve hala çalıştığından emin olmak için çözümü çalıştırın.  
  
   DSL'nizi MEF özellikli sunulmuştur. Menü komutları, hareket işleyicileri ve doğrulama kısıtlamalarını MEF uzantıları yazabilirsiniz. DSL çözümünüzdeki diğer özel kod ile birlikte bu uzantıları yazabilirsiniz. Ayrıca, sizin veya diğer geliştiriciler ayrı yazabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] DSL'nizi genişletme uzantıları.  
  
## <a name="creating-an-extension-for-a-mef-enabled-dsl"></a>MEF özellikli bir DSL için uzantı oluşturma  
 MEF özellikli kendinize veya başka bir kullanıcı tarafından oluşturulan bir DSL erişiminiz varsa, uzantıları için yazabilirsiniz. Uzantılar, menü komutlarını, hareket işleyicileri veya doğrulama kısıtlamalarını eklemek için kullanılabilir. Bu uzantıları yazmak için kullandığınız bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısı (VSIX) çözümü. Çözüm iki bölümden oluşur: bir sınıf kitaplığı projesi, kod derleme yapıları ve derleme paketleri bir VSIX projesi.  
  
#### <a name="to-create-a-dsl-extension-vsix"></a>Bir DSL uzantısı VSIX oluşturmak için  
  
1. Yeni bir sınıf kitaplığı projesi oluşturun. Bunu yapmak için **yeni proje** iletişim kutusunda **Visual Basic** veya **Visual C#** seçip **sınıf kitaplığı**.  
  
2. Yeni sınıf kitaplığı projesinde DSL derlemeye bir başvuru ekleyin.  
  
   - Bu derleme, genellikle ile biten bir ada sahip ". DSL.dll".  
  
   - DSL projesi erişiminiz varsa, derleme dosyası dizini altında bulabilirsiniz **Dsl\bin\\\\***  
  
   - DSL VSIX dosyasına erişimi varsa, derleme ".zip olarak" dosya adı uzantısı, VSIX dosyasını değiştirerek bulabilirsiniz. .Zip dosyasını açın.  
  
3. Aşağıdaki .NET derlemelere başvurular ekleyin:  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.11.0.dll  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll  
  
   -   System.ComponentModel.Composition.dll  
  
   -   System.Windows.Forms.dll  
  
4. Aynı çözüm içinde VSIX projesi oluşturun. Bunu yapmak için **yeni proje** iletişim kutusunda **Visual Basic** veya **Visual C#**, tıklayın **genişletilebilirlik**ve ardından seçin **VSIX projesi**.  
  
5. Çözüm Gezgini'nde VSIX projesini sağ tıklayın ve ardından **başlangıç projesi olarak ayarla**.  
  
6. Yeni projeyi **source.extension.vsixmanifest**.  
  
7. Tıklayın **içeriğinizi**. İletişim kutusunda ayarlanan **içerik türü** için **MEF Bileşeni**, ve **kaynak proje** sınıf kitaplığı projenize.  
  
8. Bir DSL VSIX başvuru ekleyin.  
  
   1. İçinde **source.extension.vsixmanifest**, tıklayın **Başvuru Ekle**  
  
   2. İletişim kutusunda **eklemek yükü** DSL VSIX dosyasını bulun. VSIX dosyasını DSL çözümde içinde yerleşik ** DslPackage\bin\\\\***.  
  
       Bu, kullanıcıların DSL ve uzantınızı aynı anda yüklemesine olanak sağlar. Uzantınızı yalnızca kullanıcı DSL yüklü değilse yüklenir.  
  
9. Gözden geçirmek ve güncelleştirmek, diğer alanları **source.extension.vsixmanifest**. Tıklayın **sürümleri seçin** doğrulayın doğru [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sürümleri ayarlanır.  
  
10. Sınıf kitaplığı projesi için kod ekleyin. Örnekler sonraki bölümde bir kılavuz olarak kullanın.  
  
     Komut ve hareket doğrulama sınıfları herhangi bir sayıda ekleyebilirsiniz.  
  
11. Uzantıyı test etmek için basın **F5**. Deneysel örneğinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]oluşturun veya bir örneğin DSL dosyası açın.  
  
## <a name="writing-mef-extensions-for-dsls"></a>MEF uzantıları için DSL'ler yazma  
 Ayrı bir DSL uzantısı çözümü derleme kod projesinde uzantıları yazabilirsiniz. DSL bir parçası olarak, komutlar ve hareketler doğrulama kodu yazmak için kullanışlı bir yol olarak DslPackage projenizde, MEF de kullanabilirsiniz.  
  
### <a name="menu-commands"></a>Menü Komutları  
 Bir menü komutu yazmak için uygulayan bir sınıf tanımlama <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> adlı DSL'nizi içinde tanımlanan özniteliğine sahip sınıf önek *YourDsl*`CommandExtension`. Birden fazla menü komutu sınıfı yazabilirsiniz.  
  
 `QueryStatus()` Kullanıcı diyagramda sağ tıkladığı zaman çağrılır. Geçerli seçimi inceleyin ve ayarlayın gerekir `command.Enabled` komutu geçerli olduğunda belirtmek için.  
  
```  
using System.ComponentModel.Composition;  
using System.Linq;  
using Company.MyDsl; // My DSL  
using Company.MyDsl.ExtensionEnablement; // My DSL  
using Microsoft.VisualStudio.Modeling; // Transactions  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement; // IVsSelectionContext  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement; // ICommandExtension  
  
namespace MyMefExtension  
{  
  // Defined in Dsl\MefExtension\DesignerExtensionMetaDataAttribute.cs:  
  [MyDslCommandExtension]   
  public class MyCommandClass : ICommandExtension  
  {   
    /// <summary>  
    /// Provides access to current document and selection.  
    /// </summary>  
    [Import]  
    IVsSelectionContext SelectionContext { get; set; }  
  
    /// <summary>  
    /// Called when the user selects this command.  
    /// </summary>  
    /// <param name="command"></param>  
    public void Execute(IMenuCommand command)  
    {  
      // Transaction is required if you want to update elements.  
      using (Transaction t = SelectionContext.CurrentStore  
              .TransactionManager.BeginTransaction("fix names"))  
      {  
        foreach (ExampleShape shape in SelectionContext.CurrentSelection)  
        {  
          ExampleElement element = shape.ModelElement as ExampleElement;  
          element.Name = element.Name + " !";  
        }  
        t.Commit();  
      }  
    }  
  
    /// <summary>  
    /// Called when the user right-clicks the diagram.  
    /// Determines whether the command should appear.  
    /// This method should set command.Enabled and command.Visible.  
    /// </summary>  
    /// <param name="command"></param>  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Enabled =  
        command.Visible = (SelectionContext.CurrentSelection.OfType<ExampleShape>().Count() > 0);  
    }  
  
    /// <summary>  
    /// Called when the user right-clicks the diagram.  
    /// Determines the text of the command in the menu.  
    /// </summary>  
    public string Text  
    {  
      get { return "My menu command"; }  
    }  
  }  
}  
  
```  
  
### <a name="gesture-handlers"></a>Hareket işleyicileri  
 Bir hareket işleyicisi içine veya dışına diyagram üzerine yerden sürüklediğiniz nesnelerle giderebilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Aşağıdaki örnek, dosyaları Windows Gezgini'nden diyagram üzerine sürükleyin. kullanıcının olanak sağlar. Dosya adlarını içeren öğeleri oluşturur.  
  
 Diğer DSL modelleri ve UML modelleri ile etkileyen dağıtılacak işleyiciler yazabilirsiniz. Daha fazla bilgi için [nasıl yapılır: sürükle ve bırak işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md).  
  
```  
  
using System.ComponentModel.Composition;  
using System.Linq;  
using Company.MyDsl;  
using Company.MyDsl.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling; // Transactions  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;   
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;   
  
namespace MefExtension  
{  
  [MyDslGestureExtension]  
  class MyGestureExtension : IGestureExtension  
  {  
    public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)  
    {  
      System.Windows.Forms.MessageBox.Show("double click!");  
    }  
  
    /// <summary>  
    /// Called when the user drags anything over the diagram.  
    /// Return true if the dragged object can be dropped on the current target.  
    /// </summary>  
    /// <param name="targetMergeElement">The shape or diagram that the mouse is currently over</param>  
    /// <param name="diagramDragEventArgs">Data about the dragged element.</param>  
    /// <returns></returns>  
    public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)  
    {  
      // This handler only allows items to be dropped onto the diagram:  
      return targetMergeElement is MefDsl2Diagram &&  
      // And only accepts files dragged from Windows Explorer:  
        diagramDragEventArgs.Data.GetFormats().Contains("FileNameW");  
    }  
  
    /// <summary>  
    /// Called when the user drops an item onto the diagram.  
    /// </summary>  
    /// <param name="targetDropElement"></param>  
    /// <param name="diagramDragEventArgs"></param>  
    public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)  
    {  
      MefDsl2Diagram diagram = targetDropElement as MefDsl2Diagram;  
      if (diagram == null) return;  
  
      // This handler only accepts files dragged from Windows Explorer:  
      string[] draggedFileNames = diagramDragEventArgs.Data.GetData("FileNameW") as string[];  
      if (draggedFileNames == null || draggedFileNames.Length == 0) return;   
  
      using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("file names"))  
      {  
        // Create an element to represent each file:  
        foreach (string fileName in draggedFileNames)  
        {  
          ExampleElement element = new ExampleElement(diagram.ModelElement.Partition);  
          element.Name = fileName;  
  
          // This method of adding the new element allows the position  
          // of the shape to be specified:            
          ElementGroup group = new ElementGroup(element);  
          diagram.ElementOperations.MergeElementGroupPrototype(  
            diagram, group.CreatePrototype(), PointD.ToPointF(diagramDragEventArgs.MousePosition));  
        }  
        t.Commit();  
      }  
    }  
  }  
}  
  
```  
  
### <a name="validation-constraints"></a>Doğrulama kısıtlamaları  
 Doğrulama yöntemlerinin işaretlenmiş `ValidationExtension` DSL ve ayrıca tarafından oluşturulan öznitelik <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute>. Yöntemi, bir öznitelik tarafından işaretlenmemiş herhangi bir sınıf içinde görünebilir.  
  
 Daha fazla bilgi için [etki alanına özgü bir dilde doğrulama](../modeling/validation-in-a-domain-specific-language.md).  
  
```  
using Company.MyDsl;  
using Company.MyDsl.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.Validation;  
  
namespace MefExtension  
{  
  class MyValidationExtension // Can be any class.  
  {  
    // SAMPLE VALIDATION METHOD.  
    // All validation methods have the following attributes.  
  
    // Specific to the extended DSL:  
    [MyDslValidationExtension]   
  
    // Determines when validation is applied:  
    [ValidationMethod(  
       ValidationCategories.Save  
     | ValidationCategories.Open  
     | ValidationCategories.Menu)]  
  
    /// <summary>  
    /// When validation is executed, this method is invoked  
    /// for every element in the model that is an instance  
    /// of the second parameter type.  
    /// </summary>  
    /// <param name="context">For reporting errors</param>  
    /// <param name="elementToValidate"></param>  
    private void ValidateClassNames  
      (ValidationContext context,  
       // Type determines to what elements this will be applied:  
       ExampleElement elementToValidate)  
    {   
      // Write code here to test values and links.  
      if (elementToValidate.Name.IndexOf(' ') >= 0)  
      {  
        // Log any unacceptable values:  
        context.LogError(  
          // Description:  
          "Name must not contain spaces"   
          // Error code unique to this type of error:  
          , "MyDsl001"   
          // Element to highlight when user double-clicks error:  
          , elementToValidate);   
} } } }  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio uzantıları gönderme](../extensibility/shipping-visual-studio-extensions.md)   
 [Yönetilen Genişletilebilirlik Çerçevesi (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)   
 [Nasıl yapılır: sürükle ve bırak işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Etki Alanına Özgü bir Dilde Doğrulama](../modeling/validation-in-a-domain-specific-language.md)



