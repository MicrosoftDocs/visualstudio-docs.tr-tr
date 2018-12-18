---
title: Yönetilen Genişletilebilirlik Çerçevesi Düzenleyicisi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41d5768c8cfddc3474616d7a2eee16b84cd24d56
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754694"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Düzenleyicide Managed Extensibility Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Düzenleyici, Yönetilen Genişletilebilirlik Çerçevesi (MEF) bileşenleri kullanılarak oluşturulmuştur. Kod Düzenleyicisi bileşenleri kullanabilir ve kendi MEF bileşenlerini düzenleyicisini genişletmek için oluşturabilirsiniz.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Yönetilen Genişletilebilirlik Çerçevesi'ne genel bakış  
 MEF ekleyin ve bir uygulama veya bileşen MEF programlama modeli izleyen özelliklerini değiştirmenize olanak tanıyan bir .NET kitaplıktır. Visual Studio Düzenleyicisi sağlar hem MEF Bileşeni bölümleri kullanın.  
  
 MEF, .NET Framework sürüm 4 System.ComponentModel.Composition.dll derlemede yer alır.  
  
 MEF hakkında daha fazla bilgi için bkz: [Yönetilen Genişletilebilirlik Çerçevesi (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
### <a name="component-parts-and-composition-containers"></a>Bileşen parçalarına ve kapsayıcıları oluşturma  
 Bir sınıf veya bir (veya her ikisi) birini yapmak için bir sınıf üyesi bir bileşenin bir parçasıdır:  
  
- Başka bir bileşeni kullanma  
  
- Başka bir bileşen tarafından tüketilen  
  
  Örneğin, bir ambar envanteri bileşeni tarafından sağlanan ürün kullanılabilirlik verileri bağlı olduğu bir giriş üretilmekte olan alışveriş bir uygulama düşünün. MEF bağlamında, Envanter bölümü için *dışarı* ürün kullanılabilirlik verileri ve sipariş girişi bölümü can *alma* veri. Sipariş girişi ve envanter bölümlerini diğer hakkında bilmeniz gerekmez; *kapsayıcının* (konak uygulama tarafından sağlanan) dışarı aktarmaları kümesi bakımını yapma ve dışarı aktarmaları çözümleme sorumludur ve içeri aktarır.  
  
  Kapsayıcının <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>, genellikle ana bilgisayar tarafından sahiplenilir. Kapsayıcının tutan bir *Kataloğu* dışarı aktarılan bileşen bölümleri.  
  
### <a name="exporting-and-importing-component-parts"></a>Bileşen parçalarına alma ve verme  
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
  
### <a name="importing-a-mef-export"></a>MEF dışarı aktarma  
 MEF dışarı aktarma kullanmasını istediğinizde, dışarı aktarılan ve ekleme sözleşmenin (genellikle türü) bilmeniz gerekir bir <xref:System.ComponentModel.Composition.ImportAttribute> bu değere sahip bir öznitelik. Varsayılan olarak, içeri aktarma öznitelik değiştirdiği sınıf türünde bir parametre alır. Kod alma aşağıdaki satırları <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> türü.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>Düzenleyici işlevselliği bir MEF Bileşeni bölümünden alma  
 Mevcut kodunuzu bir MEF Bileşeni parçasıysa, düzenleyici bileşen parçalarına kullanmak için MEF meta verileri kullanabilirsiniz.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Bir MEF Bileşeni bölümünden Düzenleyici işlevselliği kullanmak için  
  
1.  Genel derleme önbelleğinde (GAC) olan System.Composition.ComponentModel.dll ve düzenleyici derlemelere başvurular ekleyin.  
  
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
  
5.  Ne zaman, önceleri derlendiği böyle derlemenizi... Visual Studio yüklemenizin \Common7\IDE\Components\ klasör.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dil Hizmeti ve Düzenleyici Uzantı Noktaları](../extensibility/language-service-and-editor-extension-points.md)

