---
title: UML API ile programlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, API
- UML model, extending
ms.assetid: c5937139-49d0-4439-8a9f-89f5e0474618
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d5670b0c0806d59119e1a1af87bae5642255c5a9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793184"
---
# <a name="programming-with-the-uml-api"></a>UML API ile Programlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML API Visual Studio'nun oluşturmak, okumak ve UML modellerini ve diyagramları güncelleştirmek için kod yazmanıza olanak sağlar. Visual Studio'nun hangi sürümlerinin UML modellerini desteklemek için bkz [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 API başvuru sayfalarına ek olarak aşağıdaki konular API'yi açıklar.  
  
|Konu|Örnek türleri ve yöntemleri açıklanmaktadır|Açıklanan özellikler|  
|-----------|-----------------------------------------|------------------------|  
|[UML API ile ilişkilerde gezinme](../modeling/navigate-relationships-with-the-uml-api.md)|UML öğeleri ve bunların özelliklerini ve ilişkileri. Örneğin, IElement ve alt öğeleri dahil olmak üzere,: IClass, IActivity, IUseCase, IComponent, IInteraction, IModel, IPackage|Visual Studio'da UML modelleri UML adresindeki alınabilen belirtimi sürüm 2.1.2'ye, uygun [UML kaynak sayfası](http://go.microsoft.com/fwlink/?LinkId=160796). Her tür "I" önekli UML türü, aynı ada sahip bir arayüzdür.|  
|[UML modellerinde öğe ve ilişki oluşturma](../modeling/create-elements-and-relationships-in-uml-models.md)|IPackage.CreateClass()<br /><br /> IClass.CreateOperation()|Her öğe türünün alt öğelerini oluşturmak için yöntemleri vardır.|  
|[Diyagramlar üzerinde model görüntüleme](../modeling/display-a-uml-model-on-diagrams.md)|IShape, IDiagram<br /><br /> IShape.Move()|Modeldeki her öğe diyagram üzerindeki bir şekil olarak gösterilebilir. Bazı durumlarda, her nesne için yeni şekiller oluşturabilirsiniz. Taşıma, renklendirebilir ve daraltabilir veya bu şekilleri genişletin.|  
|[UML modelinde gezinme](../modeling/navigate-the-uml-model.md)|IModelStore<br /><br /> IDiagramContext|Model Store modeli depolar.<br /><br /> Diyagram bağlamı, geçerli diyagrama ve depoya erişiminizi erişmenizi sağlar.|  
|[İşlemleri kullanarak UML model güncelleştirmelerini bağlama](../modeling/link-uml-model-updates-by-using-transactions.md)|ILinkedUndoContext|Bir dizi değişikliği tek bir işleme bağlayabilirsiniz.|  
|[Modelleme diyagramında menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|IMenuCommand<br /><br /> IGestureExtension<br /><br /> ICommandExtension|Diyagramın işlevselliğini, çift tıklayarak ve diyagram üzerine sürükleyip çağrılan komutları tanımlayarak genişletebilirsiniz.|  
|[UML modelleri için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md)|ValidationContext|Doğrulama yardımcı kurallar, bir model, belirtilen kısıtlamalara uyduğundan emin tanımlayabilirsiniz.|  
|[IDataObject nesnesinden UML model öğelerini alma](../modeling/get-uml-model-elements-from-idataobject.md)|IElement, IShape|Bir öğe UML Model Gezgini veya UML diyagram başka bir diyagrama veya uygulamaya sürüklendiğinde, IDataObject olarak seri hale getirilir.|  
|[UML API kullanarak sıralama diyagramlarını düzenleme](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)|IInteraction, ILifeline, IMessage|Oluşturma ve etkileşim diyagramı güncelleştirme diğer diyagram türleri ile çalışmaktan biraz farklıdır.|  
|[Katman diyagramlarını genişletme](../modeling/extend-layer-diagrams.md)|ILayer, ILayerDiagram|Oluşturun ve katman diyagramları düzenlemek için kod yazma ve ayrıca program kodunu bunlara karşı doğrulayın.|  
  
## <a name="about-the-implementation"></a>Uygulama hakkında  
 UML modelleme araçları üzerine kuruludur [!INCLUDE[dsl](../includes/dsl-md.md)]. Her paket ve her diyagram tarafından temsil edilen bir [!INCLUDE[dsl](../includes/dsl-md.md)] modeli ve kural koleksiyonunu ve diğer yöntemleri onlar arasındaki tutarlılığı korur.  
  
 Bu platform üzerinden türler, UML uzantıları yazmak üzere başvurduğunuz derlemelerin bazılarında görünürdür. UML araçlarına erişerek uzantılar yapabilmenize rağmen [!INCLUDE[dsl](../includes/dsl-md.md)] API, aşağıdaki konuları göz önünde bulundurmalısınız:  
  
-   Bazı görünürde çok basit değişikliklerin tutarsızlıklar ve beklenmeyen etkilere neden olduğunu bulabilirsiniz.  
  
-   Böylece kullanarak yaptığınız uyarlamalar uygulama gelecekte değişebilir [!INCLUDE[dsl](../includes/dsl-md.md)] API artık çalışmıyor.  
  
## <a name="the-api-assemblies"></a>API derlemeleri  
 Bu tablo, UML araçları ve kullanmak için önerilen ad alanları için genişletilebilirlik sağlayan derlemeleri özetler.  
  
|Derleme|Ad Alanları|Erişim sağlar:|  
|--------------|----------------|-------------------------|  
|Microsoft.VisualStudio.Uml.Interfaces|(Tümü)|UML türleri.|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility|<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml>|[Oluşturma yöntemleri](../modeling/create-elements-and-relationships-in-uml-models.md)|  
||<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation>|[Diyagramlar ve şekiller](../modeling/display-a-uml-model-on-diagrams.md)|  
||<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility>|[Modelleme projesi](../modeling/read-a-uml-model-in-program-code.md)|  
|Microsoft.VisualStudio.Modeling.Sdk.[version]|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement>|[Menü komut uzantısı](../modeling/define-a-menu-command-on-a-modeling-diagram.md).<br /><br /> [Geri alınan işlemleri bağlama](../modeling/link-uml-model-updates-by-using-transactions.md).|  
||<xref:Microsoft.VisualStudio.Modeling.Validation>|[Doğrulama](../modeling/define-validation-constraints-for-uml-models.md)|  
||(diğer ad uzayları)|Yalnızca Gelişmiş kullanım önerilir.|  
|Microsoft.VisualStudio.Modeling.Sdk.Diagrams. [sürüm]|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement>|[Hareket işleyicileri](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).|  
||(diğer ad uzayları)|Yalnızca Gelişmiş kullanım önerilir.|  
|Microsoft.VisualStudio.TeamFoundation.WorkItemTracking|<xref:Microsoft.VisualStudio.TeamFoundation.WorkItemTracking>|[İş öğelerinin bağlantılarını](../modeling/define-a-work-item-link-handler.md).|  
|Microsoft.TeamFoundation.WorkItemTracking.Client|<xref:Microsoft.TeamFoundation.WorkItemTracking.Client>|[İş öğelerini ve onların alanları](../modeling/define-a-work-item-link-handler.md).|  
|Microsoft.TeamFoundation.Client|<xref:Microsoft.TeamFoundation.Client>|[İş öğelerini ve onların alanları](../modeling/define-a-work-item-link-handler.md).|  
|System.ComponentModel.Composition|<xref:System.ComponentModel.Composition>|[Dışarı ve içeri aktarma MEF Bileşenleri](../modeling/define-and-install-a-modeling-extension.md)|  
|System.Linq|<xref:System.Linq>|[Koleksiyonların özellikle ilişkilerle ilgili olduğunda kolay düzenlemesi](../modeling/navigate-relationships-with-the-uml-api.md).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML modellerini ve diyagramları genişletme](../modeling/extend-uml-models-and-diagrams.md)   
 [UML Genişletilebilirlik Modellemesi için API Başvurusu](../modeling/api-reference-for-uml-modeling-extensibility.md)



