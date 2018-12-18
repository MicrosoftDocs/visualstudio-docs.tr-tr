---
title: Yönetilen Genişletilebilirlik Çerçevesi Düzenleyicisi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a5ea47032ed2c5e4fb9b99afb214e068ca39d692
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857529"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Genişletilebilirlik Çerçevesi Düzenleyicisi'nde yönetilen
Düzenleyici, Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşenleri kullanılarak oluşturulmuştur. Kod Düzenleyicisi bileşenleri kullanabilir ve kendi MEF bileşenlerini düzenleyicisini genişletmek için oluşturabilirsiniz.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Yönetilen Genişletilebilirlik Çerçevesi'ne genel bakış  
 MEF ekleyin ve bir uygulama veya bileşen MEF programlama modeli izleyen özelliklerini değiştirmenize olanak tanıyan bir .NET kitaplıktır. Visual Studio Düzenleyicisi sağlar hem MEF Bileşeni bölümleri kullanın.  
  
 .NET Framework sürüm 4 MEF yer alan *System.ComponentModel.Composition.dll* derleme.  
  
 MEF hakkında daha fazla bilgi için bkz: [Yönetilen Genişletilebilirlik Çerçevesi (MEF)](/dotnet/framework/mef/index).  
  
### <a name="component-parts-and-composition-containers"></a>Bileşen parçalarına ve kapsayıcıları oluşturma  
 Bir sınıf veya bir (veya her ikisi) birini yapmak için bir sınıf üyesi bir bileşenin bir parçasıdır:  
  
- Başka bir bileşeni kullanma  
  
- Başka bir bileşen tarafından tüketilen  
  
  Örneğin, bir ambar envanteri bileşeni tarafından sağlanan ürün kullanılabilirlik verileri bağlı olduğu bir giriş üretilmekte olan alışveriş bir uygulama düşünün. MEF bağlamında, Envanter bölümü için *dışarı* ürün kullanılabilirlik verileri ve sipariş girişi bölümü can *alma* veri. Sipariş girişi ve envanter bölümlerini diğer hakkında bilmeniz gerekmez; *kapsayıcının* (konak uygulama tarafından sağlanan) dışarı aktarmaları kümesi bakımını yapma ve dışarı aktarmaları çözümleme sorumludur ve içeri aktarır.  
  
  Kapsayıcının <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, genellikle ana bilgisayar tarafından sahiplenilir. Kapsayıcının tutan bir *Kataloğu* dışarı aktarılan bileşen bölümleri.  
  
### <a name="export-and-import-component-parts"></a>Bileşen parçalarına alma ve verme  
 Bir ortak sınıf ya da genel bir sınıf (özellik veya yöntem) üyesi uygulanan sürece, herhangi bir işlevi dışa aktarabilirsiniz. Bileşen Bölümü'nden türetilen gerekmez <xref:System.ComponentModel.Composition.Primitives.ComposablePart>. Bunun yerine, eklemelisiniz bir <xref:System.ComponentModel.Composition.ExportAttribute> özniteliği sınıf veya dışarı aktarmak istediğiniz sınıf üyesi. Bu öznitelik belirtir *sözleşme* hangi başka bir bileşen tarafından bölümü işlevinizi içeri aktarabilirsiniz.  
  
### <a name="the-export-contract"></a>Dışarı aktarma Sözleşmesi  
 <xref:System.ComponentModel.Composition.ExportAttribute> Dışarı aktarılan varlık (bir sınıf, arabirim veya yapısı) tanımlar. Genellikle, dışarı aktarma öznitelik verme türünü belirten bir parametre alır.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 Varsayılan olarak, <xref:System.ComponentModel.Composition.ExportAttribute> özniteliği verilirken sınıf türünde bir sözleşme tanımlar.  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 Örnekte, varsayılan `[Export]` özniteliktir eşdeğer `[Export(typeof(TestAdornmentLayerDefinition))]`.  
  
 Aşağıdaki örnekte gösterildiği gibi bir özellik veya yöntem de verebilirsiniz.  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="import-a-mef-export"></a>MEF dışarı aktarma  
 MEF dışarı aktarma kullanmasını istediğinizde, dışarı aktarılan ve ekleme sözleşmenin (genellikle türü) bilmeniz gerekir bir <xref:System.ComponentModel.Composition.ImportAttribute> bu değere sahip bir öznitelik. Varsayılan olarak, içeri aktarma öznitelik değiştirdiği sınıf türünde bir parametre alır. Kod alma aşağıdaki satırları <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> türü.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="get-editor-functionality-from-a-mef-component-part"></a>Düzenleyici işlevselliği bir MEF Bileşeni bölümünden alın  
 Mevcut kodunuzu bir MEF Bileşeni parçasıysa, düzenleyici bileşen parçalarına kullanmak için MEF meta verileri kullanabilirsiniz.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Bir MEF Bileşeni bölümünden Düzenleyici işlevselliği kullanmak için  
  
1.  Başvuruları Ekle *System.Composition.ComponentModel.dll*, genel derleme önbelleğinde (GAC) ve düzenleyici derlemelere olan.  
  
2.  İlgili ekleme using deyimleri.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  Ekleme `[Import]` hizmeti arabirimine özniteliğini aşağıdaki gibi.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  Hizmet edindiğinizde, bileşenlerinden herhangi birini kullanabilir.  
  
5.  Ne zaman, önceleri derlendiği böyle derlemenizi *... \Common7\IDE\Components\* Visual Studio yüklemenizin klasör.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Dil hizmeti ve düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md)