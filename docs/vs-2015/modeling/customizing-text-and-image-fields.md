---
title: Metin ve görüntü alanlarını özelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a7259fc0-5afa-4356-b27e-5641e01628a9
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c73f14e2b581ea5a9c0bd22f50c11ed205c0f804
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49271134"
---
# <a name="customizing-text-and-image-fields"></a>Metin ve Görüntü Alanlarını Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir şeklin metin dekoratör tanımladığınızda, bir TextField tarafından temsil edilir. Başlatma TextFields ve diğer ShapeFields örnekleri için DSL çözümünüzde Dsl\GeneratedCode\Shapes.cs inceleyin.  
  
 Bir TextField etiketine atanan alanı gibi bir şeklin içindeki alan yöneten bir nesnedir. TextField örneği aynı sınıfın birçok şekiller arasında paylaşılır. TextField örneği her örneği için ayrı ayrı etiketin metni depolamaz: bunun yerine, `GetDisplayText(ShapeElement)` yöntemi şekil bir parametre olarak alır ve geçerli durumunu şekli ve alt model öğesi üzerinde bağımlı metin arayabilirsiniz.  
  
## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Bir metin alanı görünümünü nasıl belirlenir  
 `DoPaint()` Yöntemi çağrıldığında görüntüler için alan ekranda. Varsayılan ya da geçersiz kılabilirsiniz `DoPaint(),` veya bazı çağırdığı yöntemleri geçersiz kılabilirsiniz. Varsayılan yöntemler aşağıdaki Basitleştirilmiş sürümü, varsayılan davranışı nasıl geçersiz kılacağınızı anlamanıza yardımcı olabilir:  
  
```  
// Simplified version:  
public override void DoPaint(DiagramPaintEventArgs e, ShapeElement parentShape)  
{   
  string text = GetDisplayText(shape);   
  StringFormat format = GetStringFormat(parentShape);  
  Brush brush = GetTextBrush(e.View, shape);  
  using (Font font = GetFont(shape))  
  {  
    e.Graphics.DrawString(text, font, brush, format);  
  }  
}  
// StringFormat determines whether the string is centered etc.  
// To customize statically for all instances of this shape field,   
// assign to DefaultStringFormat.  
// To customize dynamically or per shape, override this:    
public virtual StringFormat GetStringFormat(ShapeElement shape)  
{ return DefaultStringFormat; }  
  
// Override to customize the displayed string:  
public virtual string GetDisplayText(ShapeElement shape)  
{ return this.GetValue(shape).ToString(); }  
  
// Brush determines the text color.  
// To change the brush for every field, change the shape’s styleset.   
// To customize to a brush in the style set, override GetTextBrushId.  
// To change the brush to non-standard color, override this.  
// Should take account of whether selected.   
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)  
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }  
  
// Brush ID selects a brush from a StyleSet.  
// Either return a member of DiagramBrushes   
// or add your own brush to the shape or application’s styleset.  
// Override this to change dynamically or per instance.  
// To change statically, just assign to default values.   
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)  
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId  
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;  
}  
  
// Font determines the shape and size of the text.  
// To change the font for every field, change the shape’s styleset.   
// To customize to a font in the style set, override GetFontId.  
// To change the font to a non-standard font, override this.   
public virtual Font GetFont(ShapeElement shape)  
{ return shape.StyleSet.GetFont(GetFontId(shape)); }  
  
// Selects a font from a styleset.  
// Either return a member of DiagramFonts or   
// add your own font to the shape or application’s styleset.  
// To change statically for all instances of this field,   
// assign to DefaultFontId.  
// To change per shape or dynamically, override this.   
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)  
{ return DefaultFontId; }  
  
```  
  
 Diğer birçok çiftlerini vardır `Get` yöntemleri ve `Default` özellikleri gibi `DefaultMultipleLine/GetMultipleLine()`. Şekil alanı tüm örneklerini değerini değiştirmek için varsayılan özelliği için bir değer atayabilirsiniz. Başka bir ya da şekli veya kendi model öğesi durumu bağımlı bir şekil örneğinden farklı değeri için geçersiz kılın `Get` yöntemi.  
  
## <a name="static-customizations"></a>Statik özelleştirmeleri  
 Bu şekil alanı her örneğini değiştirmek istiyorsanız, önce mi özelliği DSL tanımındaki ayarlayabileceğiniz bulun. Örneğin, yazı tipi boyutu ve stilini Özellikler penceresinde ayarlayabilirsiniz.  
  
 Aksi takdirde, daha sonra geçersiz `InitializeShapeFields` şekli sınıfı ve atama için uygun bir değer yöntemi `Default...` metin alanının özelliği.  
  
> [!WARNING]
>  Geçersiz kılınacak `InitializeShapeFields()`, ayarlamalısınız **Generates Double Derived** için Şekil sınıfın özelliği `true` DSL tanımındaki.  
  
 Bu örnekte, bir şekil kullanıcı yorumları için kullanılacak bir metin alanı vardır. Standart bir yorum yazı tipi kullanılacak istiyoruz. Standart bir yazı tipi stili kümesinde olduğundan, biz varsayılan yazı tipi kimliği ayarlayabilirsiniz:  
  
```  
  
 partial class ExampleShape  
{   protected override void InitializeShapeFields(IList<ShapeField> shapeFields)  
    {  
      // Fields set up according to DSL Definition:  
      base.InitializeShapeFields(shapeFields);  
      // Find and update comment field:  
      TextField commentField = ShapeElement.FindShapeField(shapeFields, "CommentDecorator") as TextField;  
      // Use the standard font for comments:  
      commentField.DefaultFontId = DiagramFonts.CommentText;  
  
```  
  
## <a name="dynamic-customizations"></a>Dinamik özelleştirmeleri  
 Değişiklik görünümünü bir şekil veya model öğesi kendi durumunu bağımlı hale getirmek için kendi öğesinin türetilen `TextField` ve bir veya daha fazla geçersiz kılma `Get...` yöntemleri. Ayrıca, şeklin InitializeShapeFields yöntemi yok sayın ve TextField örneğini kendi sınıfının bir örneğiyle değiştirin gerekir.  
  
 Aşağıdaki örnek bir metin alanı yazı tipi şeklin model öğesinin Boolean etki alanı özelliği durumunu bağımlı hale getirir.  
  
 Bu kod örneği çalıştırmak için en az bir dil şablonu kullanarak yeni bir DSL çözüm oluşturun. Bir Boolean etki alanı özelliği Ekle `AlternateState` ExampleElement alan sınıfına. Bir simge dekoratör ExampleShape sınıfa ekleyin ve bir bit eşlem dosyasına görüntüsünü ayarlayın. Tıklayın **tüm şablonları dönüştürme**. DSL projesinde yeni bir kod dosyası ekleyin ve aşağıdaki kodu ekleyin.  
  
 Kodu test etmek için F5 tuşuna basın ve hata ayıklama çözümü bir örnek diyagramı açın. Varsayılan durum simgesinin görünmesi gerekir. Şekli seçin ve Özellikler penceresinde değiştirin **AlternateState** özelliği. Yazı tipini öğe adını değiştirmeniz gerekir.  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
...  
  
  partial class ExampleShape  
  {  
    /// <summary>  
    /// Compose a list of the fields in this shape.  
    /// Called once for each shape class.  
    /// </summary>  
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)  
    {  
      // Fields set up according to DSL Definition:  
      base.InitializeShapeFields(shapeFields);  
      // Replace the text field for NameDecorator:  
      TextField oldField = ShapeElement.FindShapeField(shapeFields, "NameDecorator") as TextField;  
      shapeFields.Remove(oldField);  
      // Replace with my text field based on DSL Definition values:  
      MyTextField newField = new MyTextField(oldField);  
      shapeFields.Add(newField);  
    }  
  }  
  /// <summary>  
  /// Dynamic font depends on state of model element.  
  /// </summary>  
  public class MyTextField : TextField  
  {  
    public MyTextField(TextField prototype)  
      : base(prototype.Name)  
    {  
      DefaultText = prototype.DefaultText;  
      DefaultFocusable = prototype.DefaultFocusable;  
      DefaultAutoSize = prototype.DefaultAutoSize;  
      AnchoringBehavior.MinimumHeightInLines = prototype.AnchoringBehavior.MinimumHeightInLines;  
      AnchoringBehavior.MinimumWidthInCharacters = prototype.AnchoringBehavior.MinimumWidthInCharacters;  
      DefaultAccessibleState = prototype.DefaultAccessibleState;  
    }  
  
    public override System.Drawing.Font GetFont(ShapeElement parentShape)  
    {  
      // Access the Boolean domain property of the model element:  
      if ((parentShape.ModelElement as ExampleElement).AlternateState)  
        return new System.Drawing.Font("Callisto", 14.0f,  
               System.Drawing.FontStyle.Italic |   
               System.Drawing.FontStyle.Bold);  
      else  
        return base.GetFont(parentShape);  
    }  
  
  }  
  
```  
  
## <a name="style-sets"></a>Stilini ayarlar  
 Yukarıdaki örnekte, metin alanı kullanılabilir olan herhangi bir yazı tipi için nasıl değiştirebileceğiniz gösterir. Ancak, şekli veya uygulama ile ilişkili olan bir stil kümesi birini değiştirmek için tercih edilen bir yöntem olduğundan. Bunu yapmak için geçersiz kılma <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> veya GetTextBrushId().  
  
 Alternatif olarak, şekliniz stil kümesi geçersiz kılarak değiştirmeyi göz önünde bulundurun <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A>. Bu yazı tiplerini ve tüm şekil alanlarının Fırçalar değiştirme etkisi vardır.  
  
## <a name="customizing-image-fields"></a>Görüntü alanlarını özelleştirme  
 Bir şekli görüntü dekoratör tanımladığınızda ve bir resim şekli tanımlarken, alanın şekli görüntülendiği bir ImageField tarafından yönetilir. Başlatma ImageFields ve diğer ShapeFields örnekleri için DSL çözümünüzde Dsl\GeneratedCode\Shapes.cs inceleyin.  
  
 Bir ImageField dekoratör için atanan alanı gibi bir şeklin içindeki alan yöneten bir nesnedir. Bir ImageField örneği aynı şekli sınıfın birçok şekiller arasında paylaşılır. ImageField örneği ayrı bir görüntü her bir şeklin depolamaz: bunun yerine, `GetDisplayImage(ShapeElement)` yöntemi şekil bir parametre olarak alır ve geçerli durumunu şekli ve alt model öğesi üzerinde bağımlı görüntü arayabilirsiniz.  
  
 Özel davranış gibi bir değişken görüntüsü isterseniz, kendi sınıfınızı ImageField'dan türetilmiş oluşturabilirsiniz.  
  
#### <a name="to-create-a-subclass-of-imagefield"></a>ImageField öğesinin oluşturmak için  
  
1.  Ayarlama **Generates Double Derived** , DSL tanımındaki üst şeklin sınıfın özelliği.  
  
2.  Geçersiz kılma `InitializeShapeFields` şekli sınıfınızın yöntemi.  
  
    -   DSL projede yeni bir kod dosyası oluşturun ve Şekil sınıfı için bir parçalı sınıf tanımı yazın. Yöntem tanımı geçersiz.  
  
3.  Kodu incelemek `InitializeShapeFields` DSL\GeneratedCode\Shapes.cs içinde.  
  
     Geçersiz kılma yönteminizde taban yöntemini çağırın ve ardından kendi görüntü alan sınıfının bir örneğini oluşturun. Bu normal görüntü alanını değiştirmek için kullanın `shapeFields` listesi.  
  
## <a name="dynamic-icons"></a>Dinamik simgeleri  
 Bu örnek, bir simge Değiştir şeklin model öğesi durumu bağımlı hale getirir.  
  
> [!WARNING]
>  Bu örnek, dinamik görüntü dekoratör yapmak nasıl gösterir. Ancak yalnızca bir model değişken durumunu bağlı olarak bir veya iki görüntü arasında geçiş yapmak istiyorsanız, daha basit birkaç görüntü dekoratörler oluşturun, bunları şekli üzerinde aynı konumda bulun ve ardından modelin belirli değerlerine bağımlı görünürlük filtresini ayarlayın değişken. Bu filtre ayarlamak için DSL tanımındaki şekil eşlemesi seçin, DSL Ayrıntıları penceresi açın ve dekoratörler sekmesine tıklayın.  
  
 Bu kod örneği çalıştırmak için en az bir dil şablonu kullanarak yeni bir DSL çözüm oluşturun. Bir Boolean etki alanı özelliği Ekle `AlternateState` ExampleElement alan sınıfına. Bir simge dekoratör ExampleShape sınıfa ekleyin ve bir bit eşlem dosyasına görüntüsünü ayarlayın. Tıklayın **tüm şablonları dönüştürme**. DSL projesinde yeni bir kod dosyası ekleyin ve aşağıdaki kodu ekleyin.  
  
 Kodu test etmek için F5 tuşuna basın ve hata ayıklama çözümü bir örnek diyagramı açın. Varsayılan durum simgesinin görünmesi gerekir. Şekli seçin ve Özellikler penceresinde değiştirin **AlternateState** özelliği. Ardından simgesi aracılığıyla bu şekli üzerinde 90 derece döndürülmüş görünmelidir.  
  
```csharp  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
...  
partial class ExampleShape  
{  
    /// <summary>  
    /// Compose a list of the fields in this shape.  
    /// Called once for each shape class.  
    /// </summary>  
    /// <param name="shapeFields"></param>  
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)  
    {  
      // Fields set up according to DSL Definition:  
      base.InitializeShapeFields(shapeFields);  
  
      // Replace the image field:  
      ShapeField oldField = ShapeElement.FindShapeField(shapeFields, "IconDecorator");  
      shapeFields.Remove(oldField);  
      // Must keep the same name:  
      MyImageField newField = new MyImageField(oldField.Name);  
      shapeFields.Add(newField);  
      newField.DefaultImage = (oldField as ImageField).DefaultImage.Clone() as System.Drawing.Image;  
    }  
  }  
  
  public class MyImageField : ImageField  
  {  
    public MyImageField(string tag) : base(tag) { }  
  
    /// <summary>  
    /// Get the image for this field in the given shape.  
    /// </summary>  
    public override System.Drawing.Image GetDisplayImage(ShapeElement parentShape)  
    {  
      ExampleElement element = parentShape.ModelElement as ExampleElement;  
      if (element.AlternateState == true)  
        return AlternateImage;  
      else  
        return base.GetDisplayImage(parentShape);  
    }  
  
    private System.Drawing.Image alternateImage;  
    public System.Drawing.Image AlternateImage  
    {  
      get  
      {  
        if (alternateImage == null)  
        {  
          // Alternate image is a copy of the default, rotated by 90 degrees:  
          alternateImage = this.DefaultImage.Clone() as System.Drawing.Image;  
          alternateImage.RotateFlip(System.Drawing.RotateFlipType.Rotate90FlipNone);  
        }  
        return alternateImage;  
      }  
    }  
  }  
}  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şekiller ve bağlayıcıları tanımlama](../modeling/defining-shapes-and-connectors.md)   
 [Diyagram üzerinde arka plan görüntüsü ayarlama](../modeling/setting-a-background-image-on-a-diagram.md)   
 [Gezinme ve Program kodundaki modeli güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Etki Alanına Özgü Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)



