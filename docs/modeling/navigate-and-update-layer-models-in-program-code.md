---
title: Program kodunda katman modellerini gezinme ve güncelleştirme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8ca10b8504dc4383ad6251e3819c14b7102d32d3
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566745"
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Program kodunda katman modellerini gezinme ve güncelleştirme

Bu makalede, öğeleri ve ilişkileri gidin ve program kodunu kullanarak katman modellerini açıklar. Kullanıcı açısından bağımlılık diyagramları hakkında daha fazla bilgi için bkz. [bağımlılık diyagramları: başvuru](../modeling/layer-diagrams-reference.md) ve [bağımlılık diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md).

<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer> Bu konuda açıklanan hakkında daha genel bir cephe modelidir <xref:Microsoft.VisualStudio.GraphModel> modeli. Yazıyorsanız bir [menü komut veya hareket uzantısı](../modeling/add-commands-and-gestures-to-layer-diagrams.md), kullanın `Layer` modeli. Yazıyorsanız bir [katman doğrulama uzantısı](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), kullanımı daha kolay olan `GraphModel`.

## <a name="transactions"></a>İşlemler

Bir modeli güncelleştirme, değişiklikleri kapsayan göz önünde bir `ILinkedUndoTransaction`, değişikliklerinizi bir hareket halinde gruplandırır. Değişikliklerden herhangi birini başarısız olursa, tüm işlem geri alınır. Kullanıcı bir değişikliği geri alır, tüm değişiklikleri birlikte geri alınır.

```csharp
using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("a name"))
{
    // Make changes here ....
    t.Commit(); // Don't forget this!
}
```

## <a name="containment"></a>Kapsama

![ILayer ve ILayerModel hem ILayers içerebilir.](../modeling/media/layerapi_containment.png)

Katmanları (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>) ve katman modeli (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>) yorumlar ve Katmanlar içerebilir.

Bir katman (`ILayer`) bir katman modeli içinde yer alabilir (`ILayerModel`) ya da başka yuvalanabilir `ILayer`.

Bir yorum veya bir katman oluşturmak için üzerinde uygun bir kapsayıcı oluşturma yöntemlerini kullanın.

## <a name="dependency-links"></a>Bağımlılık bağlantıları

Bir bağımlılık bağlantısı, bir nesne tarafından temsil edilir. Herhangi bir yönde çıkıldığında:

![Bir ILayerDependencyLink iki ILayers bağlanır.](../modeling/media/layerapi_dependency.png)

Bir bağımlılık bağlantısı oluşturmak için arama `source.CreateDependencyLink(target)`.

## <a name="comments"></a>Açıklamalar

Açıklamalar, katmanları veya katman modeli içinde yer alabilir ve herhangi bir katman öğeye bağlanabilir:

![Herhangi bir katman öğeye açıklamalar eklenebilir.](../modeling/media/layerapi_comments.png)

Bir yorum yok gibi öğeleri, herhangi bir sayıda bağlanabilir.

Bir katman öğesine eklenen açıklamalar almak için kullanın:

```csharp
ILayerModel model = diagram.GetLayerModel();
IEnumerable<ILayerComment> comments =
   model.Comments.Where(comment =>
      comment.Links.Any(link => link.Target == layerElement));
```

> [!CAUTION]
> `Comments` Özelliği bir `ILayer` içinde yer alan yorum alır `ILayer`. Kaynağa bağlı yorumlar almaz.

Çağırarak bir açıklama oluşturun `CreateComment()` üzerinde uygun bir kapsayıcı.

Bir bağlantıyı kullanarak oluşturursunuz `CreateLink()` açıklama üzerinde.

## <a name="layer-elements"></a>Katman öğeleri

Öğesinin bir modelde bulunan tüm türleri katman öğeler şunlardır:

![bağımlılık diyagram içeriği ILayerElements olduğundan.](../modeling/media/layerapi_layerelements.png)

## <a name="properties"></a>Özellikler

Her `ILayerElement` sahip adlandırılmış bir dize sözlük `Properties`. Bu sözlük, herhangi bir katman öğeye rastgele bilgi eklemek için kullanabilirsiniz.

## <a name="artifact-references"></a>Yapıt başvuruları

Bir yapı başvurusu (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>) bir katman ve bir proje öğesi dosya, sınıf veya klasör gibi arasındaki bağlantıyı temsil eder. Kullanıcı, bir katman oluşturma veya Çözüm Gezgini, sınıf görünümü veya nesne tarayıcısı bir bağımlılık diyagramına öğeleri sürükleyerek ekleyin yapıtları oluşturur. Yapıt başvuruları herhangi bir sayıda katmana bağlı.

Katman Gezgini her satırda bir yapı başvurusu görüntüler. Daha fazla bilgi için [kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md).

Asıl türleri ve yöntemleri yapıt başvurularla ilgili aşağıdaki gibidir:

<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>. Kategori özelliği, bir sınıf, yürütülebilir dosya veya derleme gibi ne tür bir yapı başvuruluyor gösterir. Nasıl hedef yapıt tanımlayıcısı tanımlar kategorilere özelliği belirler.

<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A> bir yapıt başvuru oluşturur bir <xref:EnvDTE.Project> veya <xref:EnvDTE.ProjectItem>. Bu zaman uyumsuz bir işlemdir. Bu nedenle, genellikle oluşturma tamamlandıktan sonra çağrılan bir geri çağırma sağlar.

Katman yapı başvuruları, kullanım örneği diyagramları Yapıtları için farklıdır.

## <a name="shapes-and-diagrams"></a>Şekilleri ve diyagramları

İki nesne, bir katman modeli içindeki her öğeyi temsil etmek için kullanılır: bir <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>ve bir <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>. `IShape` Şekli diyagram üzerinde boyutunu ve konumunu temsil eder. Katman modellerdeki her `ILayerElement` varsa `IShape`ve her `IShape` bağımlılık diyagram varsa `ILayerElement`. `IShape` UML modelleri için de kullanılır. Bu nedenle, her `IShape` katman öğesine sahip.

Aynı şekilde <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel> birinde görüntülenen <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram>.

Bir özel komut veya hareket işleyici kodda, geçerli diyagrama ve şekillerden oluşan geçerli seçimi alabilirsiniz `DiagramContext` içeri aktarın:

```csharp
public class ... {
[Import]
    public IDiagramContext DiagramContext { get; set; }
...
public void ... (...)
{ IDiagram diagram = this.DiagramContext.CurrentDiagram;
  ILayerModel model = diagram.GetLayerModel();
  if (model != null)
  { foreach (ILayer layer in model.Layers) { ... }}
  foreach (IShape selected in diagram.SelectedShapes)
  { ILayerElement element = selected.GetLayerElement();
    if (element != null) ... }}
```

![Her ILayerElement IShape tarafından sunulur.](../modeling/media/layerapi_shapes.png)

<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> ve <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> UML modelleri görüntülemek için de kullanılır.

## <a name="see-also"></a>Ayrıca Bkz.

- [Bağımlılık diyagramlarına komut ve hareket ekleme](../modeling/add-commands-and-gestures-to-layer-diagrams.md)
- [Bağımlılık diyagramlarına özel mimari doğrulaması ekleme](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
- [Bağımlılık diyagramlarına özel özellikler ekleme](../modeling/add-custom-properties-to-layer-diagrams.md)
- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)
- [Bağımlılık Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)
