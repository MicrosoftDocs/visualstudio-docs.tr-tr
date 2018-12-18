---
title: Bağımlılık diyagramlarına özel özellikler ekleme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 368d1a794f51d827aa62cc913039edda59ae7ae6
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33864196"
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Bağımlılık diyagramlarına özel özellikler ekleme

Bağımlılık diyagramları için uzantı kodu yazarken, bir bağımlılık diyagramda herhangi bir öğe değerleriyle depolayabilirsiniz. Diyagram yeniden açılır ve kaydedildiğinde, değerleri korunur. Ayrıca bu özellikleri görünür olabilir **özellikleri** penceresi böylece kullanıcılar bakın ve bunları düzenleyebilir. Örneğin, her katman için normal bir ifade belirtin ve her katman sınıflarda adları kullanıcı tarafından belirtilen desenle uygun doğrulamak için doğrulama kodu yazma kullanıcıların izin.

## <a name="non-visible-properties"></a>Görünür olmayan özellikleri

Yalnızca bir bağımlılık diyagramda herhangi bir öğeye değerler eklemek için kodunuzu istiyorsanız, bir MEF Bileşeni tanımlamak gerekmez. Adlı bir sözlük yoktur `Properties` içinde <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>. Herhangi bir katman öğe sözlüğe sıralanabilir değerleri eklemeniz yeterlidir. Bağımlılık diyagramın bir parçası olarak kaydedilir. Daha fazla bilgi için bkz: [gidin ve güncelleştirme modelleri program kodunda katman](../modeling/navigate-and-update-layer-models-in-program-code.md).

## <a name="editable-properties"></a>Düzenlenebilir özellikler

**İlk hazırlama**

> [!IMPORTANT]
> Özellikleri görünür yapmak için katman özellikleri görünür olmasını istediğiniz her bilgisayarda aşağıdaki değişikliği yapın:
>
> 1. Not Defteri'ni kullanarak çalıştırın **yönetici olarak çalıştır**. Açık *%ProgramFiles%\Microsoft Visual Studio [sürüm] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest*.
> 2. İçinde **içerik** öğesini ekleyin:
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
> 3. Altında **Visual Studio Araçları** Visual Studio uygulama Başlat menüsünde açık bölümünü **Geliştirici komut istemi**. Girin:
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. Visual Studio'yu yeniden başlatın.

**Kodunuzu bir VSIX proje ile olduğundan emin olun**

Özelliğinizi komutu, hareketi veya doğrulama projesi parçası ise, herhangi bir şey eklemenize gerek yoktur. Özel özellik için kod MEF Bileşeni olarak tanımlanan bir Visual Studio genişletilebilirlik projesi tanımlanması gerekir. Daha fazla bilgi için bkz: [bağımlılık diyagramlarına komut ve hareket ekleme](../modeling/add-commands-and-gestures-to-layer-diagrams.md) veya [bağımlılık diyagramlarına özel mimari doğrulaması ekleme](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

**Özel özellik tanımlama**

Bir özel özellik oluşturmak için bu gibi bir sınıf tanımlayın:

```csharp
[Export(typeof(IPropertyExtension))]
public class MyProperty : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

Üzerinde özellikleri de tanımlayabilir <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> ya da dahil, türetilmiş sınıflarından herhangi biriyle:

-   `ILayerModel` -modeli

-   `ILayer` -her katman

-   `ILayerDependencyLink` -katmanları arasındaki bağlantıları

-   `ILayerComment`

-   `ILayerCommentLink`

## <a name="example"></a>Örnek

Tipik bir özel özellik tanımlayıcısı kodudur. Katman modeli üzerinde bir Boolean özelliği tanımlar (`ILayerModel`) bir özel doğrulama yöntemi için değerler sağlayın kullanıcının olanak tanır.

```csharp
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

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık diyagramlarını genişletme](../modeling/extend-layer-diagrams.md)
