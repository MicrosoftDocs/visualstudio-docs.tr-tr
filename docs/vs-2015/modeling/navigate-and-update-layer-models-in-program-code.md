---
title: Program kodunda katman modellerini gezinme ve güncelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ec36aa78ce5ed90098587092207806444681146a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734724"
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Program kodunda katman modellerini gezinme ve güncelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, öğeleri ve ilişkileri gidin ve program kodunu kullanarak katman modellerini açıklar. Kullanıcı açısından katman diyagramları hakkında daha fazla bilgi için bkz: [katman diyagramları: başvuru](../modeling/layer-diagrams-reference.md) ve [katman diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md).  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer> Bu konuda açıklanan hakkında daha genel bir cephe modelidir <xref:Microsoft.VisualStudio.GraphModel> modeli. Yazıyorsanız bir [menü komut veya hareket uzantısı](../modeling/add-commands-and-gestures-to-layer-diagrams.md), kullanın `Layer` modeli. Yazıyorsanız bir [katman doğrulama uzantısı](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), kullanımı daha kolay olan `GraphModel`.  
  
## <a name="transactions"></a>İşlemler  
 Bir modeli güncelleştirme, değişiklikleri kapsayan göz önünde bir `ILinkedUndoTransaction`. Bu, değişikliklerinizi bir hareket halinde gruplandırır. Değişikliklerden herhangi birini başarısız olursa, tüm işlem geri alınacaktır. Kullanıcı bir değişikliği geri alır, tüm değişiklikleri birlikte geri alınacak.  
  
 Daha fazla bilgi için [işlemleri kullanarak bağlantı UML model güncelleştirmelerini](../modeling/link-uml-model-updates-by-using-transactions.md).  
  
```  
using (ILinkedUndoTransaction t =  
        LinkedUndoContext.BeginTransaction("a name"))  
{   
    // Make changes here ....  
    t.Commit(); // Don't forget this!  
}  
```  
  
## <a name="containment"></a>Kapsama  
 ![ILayer ve ILayerModel hem ILayers içerebilir. ](../modeling/media/layerapi-containment.png "LayerApi_Containment")  
  
 Katmanları (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>) ve katman modeli (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>) yorumlar ve Katmanlar içerebilir.  
  
 Bir katman (`ILayer`) bir katman modeli içinde yer alabilir (`ILayerModel`) ya da başka yuvalanabilir `ILayer`.  
  
 Bir yorum veya bir katman oluşturmak için üzerinde uygun bir kapsayıcı oluşturma yöntemlerini kullanın.  
  
## <a name="dependency-links"></a>Bağımlılık bağlantıları  
 Bir bağımlılık bağlantısı, bir nesne tarafından temsil edilir. Herhangi bir yönde çıkıldığında:  
  
 ![Bir ILayerDependencyLink iki ILayers bağlanır. ](../modeling/media/layerapi-dependency.png "LayerApi_Dependency")  
  
 Bir bağımlılık bağlantısı oluşturmak için arama `source.CreateDependencyLink(target)`.  
  
## <a name="comments"></a>Açıklamalar  
 Açıklamalar, katmanları veya katman modeli içinde yer alabilir ve herhangi bir katman öğeye bağlanabilir:  
  
 ![Herhangi bir katman öğeye açıklamalar eklenebilir. ](../modeling/media/layerapi-comments.png "LayerApi_Comments")  
  
 Bir yorum yok gibi öğeleri, herhangi bir sayıda bağlanabilir.  
  
 Bir katman öğesine eklenen açıklamalar almak için kullanın:  
  
```csharp  
ILayerModel model = diagram.GetLayerModel();   
IEnumerable<ILayerComment> comments =   
   model.Comments.Where(comment =>   
      comment.Links.Any(link => link.Target == layerElement));  
  
```  
  
> [!CAUTION]
>  `Comments` Özelliği bir `ILayer` içinde yer alan yorum alır `ILayer`. Kaynağa bağlı yorumlar almaz.  
  
 Çağırarak bir açıklama oluşturun `CreateComment()` üzerinde uygun bir kapsayıcı.  
  
 Bir bağlantıyı kullanarak oluşturursunuz `CreateLink()` açıklama üzerinde.  
  
## <a name="layer-elements"></a>Katman öğeleri  
 Öğesinin bir modelde bulunan tüm türleri katman öğeler şunlardır:  
  
 ![Katman diyagramı içeriği ILayerElements olduğundan. ](../modeling/media/layerapi-layerelements.png "LayerApi_LayerElements")  
  
## <a name="properties"></a>Özellikler  
 Her `ILayerElement` sahip adlandırılmış bir dize sözlük `Properties`. Bu sözlük, herhangi bir katman öğeye rastgele bilgi eklemek için kullanabilirsiniz.  
  
## <a name="artifact-references"></a>Yapıt başvuruları  
 Bir yapı başvurusu (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>) bir katman ve bir proje öğesi dosya, sınıf veya klasör gibi arasındaki bağlantıyı temsil eder. Kullanıcı, bir katman oluşturma veya Çözüm Gezgini, sınıf görünümü veya nesne tarayıcısı bir katman diyagramına öğeleri sürükleyerek ekleyin yapıtları oluşturur. Yapıt başvuruları herhangi bir sayıda katmana bağlı.  
  
 Katman Gezgini her satırda bir yapı başvurusu görüntüler. Daha fazla bilgi için [kodunuz aracılığıyla katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md).  
  
 Asıl türleri ve yöntemleri yapıt başvurularla ilgili aşağıdaki gibidir:  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>. Kategori özelliği, bir sınıf, yürütülebilir dosya veya derleme gibi ne tür bir yapı başvuruluyor gösterir. Kategorileri belirler nasıl hedef yapıt tanımlayıcısı tanımlar.  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A> bir yapıt başvuru oluşturur bir <xref:EnvDTE.Project> veya <xref:EnvDTE.ProjectItem>. Bu zaman uyumsuz bir işlemdir. Bu nedenle, genellikle oluşturma işlemi tamamlandıktan sonra çağrılan bir geri çağırma sağlar.  
  
 Katman yapı başvuruları kullanım örneği diyagramları yapılar ile karıştırılmamalıdır.  
  
## <a name="shapes-and-diagrams"></a>Şekilleri ve diyagramları  
 İki nesne, bir katman modeli içindeki her öğeyi temsil etmek için kullanılır: bir <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>ve bir <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>. `IShape` Şekli diyagram üzerinde boyutunu ve konumunu temsil eder. Katman modellerdeki her `ILayerElement` varsa `IShape`ve her `IShape` üzerinde bir katman diyagramı varsa `ILayerElement`. `IShape` UML modelleri için de kullanılır. Bu nedenle, her `IShape` katman öğesine sahip.  
  
 Aynı şekilde <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel> birinde görüntülenen <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram>.  
  
 Bir özel komut veya hareket işleyici kodda, geçerli diyagrama ve şekillerden oluşan geçerli seçimi alabilirsiniz `DiagramContext` içeri aktarın:  
  
```  
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
  
 ![Her ILayerElement IShape tarafından sunulur. ](../modeling/media/layerapi-shapes.png "LayerApi_Shapes")  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> ve <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> UML modelleri görüntülemek için de kullanılır. Daha fazla bilgi için [diyagramlar üzerinde bir UML modeli görüntüleme](../modeling/display-a-uml-model-on-diagrams.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Katman diyagramlarına komut ve hareket ekleme](../modeling/add-commands-and-gestures-to-layer-diagrams.md)   
 [Katman diyagramlarına özel mimari doğrulaması ekleme](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
 [Katman diyagramlarına özel özellikler ekleme](../modeling/add-custom-properties-to-layer-diagrams.md)   
 [Katman diyagramları: başvuru](../modeling/layer-diagrams-reference.md)   
 [Katman diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)   
 [UML modellerini ve diyagramları genişletme](../modeling/extend-uml-models-and-diagrams.md)



