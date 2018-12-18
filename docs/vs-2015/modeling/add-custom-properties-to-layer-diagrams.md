---
title: Katman diyagramlarına özel özellikler ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams, adding custom properties
ms.assetid: 52b3ac25-d10b-4507-a1fe-209ccb4d2777
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 9024ccda38e6b261b29d808e6fafb7837776fc8c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789284"
---
# <a name="add-custom-properties-to-layer-diagrams"></a>Katman diyagramlarına özel özellikler ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Katman diyagramları için uzantı kodu yazdığınızda, herhangi bir öğeyle değerleri Katman diyagramında saklayabilirsiniz. Diyagram kaydedildiğinde ve yeniden açıldığında, değerler kalır. Bu özellikler görünür bulundurabilirsiniz **özellikleri** penceresi böylece kullanıcıların görebilmesi ve düzenleyebilmesi. Örneğin, kullanıcıların her katman için normal bir ifade belirtin ve her katmanda sınıfların adlarını, kullanıcı tarafından belirtilen düzene uyan doğrulamak için doğrulama kodu yazmasına izin verebilirsiniz.  
  
## <a name="properties-not-visible-to-the-user"></a>Kullanıcının göremediği Özellikler  
 Yalnızca kodunuzun değerleri Katman diyagramında herhangi bir öğe eklemek istiyorsanız, bir MEF Bileşeni tanımlamanız gerekmez. Adlı bir sözlük var. `Properties` içinde <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>. Herhangi bir katman öğenin sözlüğe sıralanabilecek değerler eklemeniz yeterlidir. Katman diyagramının bir parçası olarak kaydedilir. Daha fazla bilgi için [erişin ve güncelleştirme modelleri program kodunda katman](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
## <a name="properties-that-the-user-can-edit"></a>Kullanıcının düzenleyebildiği Özellikler  
 **İlk Hazırlık**  
  
> [!IMPORTANT]
>  Özellikleri görünür yapmak için katman özellikleri görünür olmasını istediğiniz her bilgisayarda aşağıdaki değişikliği yapmanız gerekir.  
> 
> 1. Kullanarak Not Defteri'ni çalıştırma **yönetici olarak çalıştır**. açın `%ProgramFiles%\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest`  
>    2.  İçinde `Content` öğesini ekleyin:  
> 
>    ```xml  
>    <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>  
>    ```  
>    3.  Altında **Visual Studio Araçları** Visual Studio uygulama başlangıç menüsünde, açık bir bölümünü **Geliştirici komut istemi**.  
> 
>    Girin:  
> 
>    `devenv /rootSuffix /updateConfiguration`  
> 
>    `devenv /rootSuffix Exp /updateConfiguration`  
>    4.  Visual Studio'yu yeniden başlatın.  
  
 **Kodunuzun bir VSIX projesinde olduğundan emin olun**  
  
 Özelliğiniz komutun, hareket ya da doğrulama projesi parçasıysa, hiçbir şey eklemenize gerek yoktur. Özel özelliğinizin kodu, bir MEF Bileşeni olarak tanımlanmış bir Visual Studio genişletilebilirlik projesinde tanımlanmalıdır. Daha fazla bilgi için [katman diyagramlarına komutlar ve hareketler ekleme](../modeling/add-commands-and-gestures-to-layer-diagrams.md) veya [katman diyagramlarına özel mimari doğrulaması ekleme](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).  
  
 **Özel özelliği tanımla**  
  
 Özel bir özellik oluşturmak için şunun gibi bir sınıf tanımlayın:  
  
```  
[Export(typeof(IPropertyExtension))]  
public class MyProperty   
      : PropertyExtension<ILayerElement>  
{  
  // Implement the interface.  
}  
```  
  
 Özellikleri tanımlayabilirsiniz <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> veya içeren, ondan türetilen sınıflardan biri:  
  
-   `ILayerModel` -model  
  
-   `ILayer` -her katman  
  
-   `ILayerDependencyLink` -Katmanlar arasında bağlantılar  
  
-   `ILayerComment`  
  
-   `ILayerCommentLink`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod tipik bir özel özellik tanımlayıcısıdır. Katman modelinde bir Boolean özelliği tanımlar (`ILayerModel`) olanak tanıyan kullanıcının özel doğrulama yöntemi için değerler sağlayın.  
  
```  
using System;  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
  
namespace MyNamespace  
{  
  /// <summary>  
  /// Custom properties are added to the Layer Designer via a custom  
  /// Property Descriptor. We have to export this Property Descriptor  
  /// using MEF to make it available in the Layer Designer.  
  /// </summary>  
  [Export(typeof(IPropertyExtension))]  
  public class AllTypesMustBeReferencedProperty   
      : PropertyExtension<ILayerModel>  
  {  
    /// <summary>  
    /// Each custom property must have a unique name.   
    /// Usually we use the full name of this class.  
    /// </summary>  
    public static readonly string FullName =  
      typeof(AllTypesMustBeReferencedProperty).FullName;  
  
    /// <summary>  
    /// Construct the property. Notice the use of FullName.  
    /// </summary>  
    public AllTypesMustBeReferencedProperty()  
            : base(FullName)  
    {  }  
  
    /// <summary>  
    /// The display name is shown in the Properties window.  
    /// We therefore use a localizable resource.  
    /// </summary>  
    public override string DisplayName  
    {  
      get { return Strings.AllTypesMustBeReferencedDisplayName; }  
    }  
  
    /// <summary>  
    /// Description shown at the bottom of the Properties window.  
    /// We use a resource string for easier localization.  
    /// </summary>  
    public override string Description  
    {  
      get { return Strings.AllTypesMustBeReferencedDescription; }  
    }  
  
    /// <summary>  
    /// This is called to set a new value for this property. We must  
    /// throw an exception if the value is invalid.  
    /// </summary>  
    /// <param name="component">The target ILayerElement</param>  
    /// <param name="value">The new value</param>  
    public override void SetValue(object component, object value)  
    {  
      ValidateValue(value);  
      base.SetValue(component, value);  
    }  
    /// <summary>  
    /// Helper to validate the value.  
    /// </summary>  
    /// <param name="value">The value to validate</param>  
    private static void ValidateValue(object value)  
    {  }  
  
    public override Type PropertyType  
    { get { return typeof(bool); } }  
  
    /// <summary>  
    /// The segment label of the properties window.  
    /// </summary>  
    public override string Category  
    {   
      get  
      {  
        return Strings.AllTypesMustBeReferencedCategory;  
      }  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Katman diyagramlarını genişletme](../modeling/extend-layer-diagrams.md)



