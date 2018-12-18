---
title: Uygulamanız için model oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.common.commentlink.properties
- vs.teamarch.UMLModelExplorer.dependency
- vs.teamarch.UMLModelExplorer.commentlink
- vs.teamarch.common.dependency.properties
- Microsoft.VisualStudio.Uml.Diagrams.CommentShape.IsTransparent
- vs.teamarch.common.comment.properties
- vs.teamarch.UMLModelExplorer.comment
helpviewer_keywords:
- diagrams - modeling, sequence
- software design
- diagrams - modeling, use case
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML model
- diagrams - modeling, UML use case
- diagrams - modeling, class
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- software modeling
- diagrams - modeling, UML sequence
- UML
- diagrams - modeling, UML
- diagrams - modeling, layer
- software, designing
- diagrams - modeling, UML class
- software, modeling
- UML diagrams
ms.assetid: b69d9d91-c7e7-4dee-8eb6-706076eecb85
caps.latest.revision: 60
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 9e3aa389441914121493148ecb8fa45b9f86beed
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745134"
---
# <a name="create-models-for-your-app"></a>Uygulamanız için model oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modelleme diyagramları kodunuz ve yazılım sisteminizin desteklemesi gereken kullanıcı gereksinimleri hakkında fikirleri anlamanıza, açıklamak ve yardımcı olur. Örneğin, tanımlamak ve kullanıcı gereksinimlerinden için Birleşik Modelleme Dili (UML) kullanım örneği, etkinlik, sınıf ve sıralı diyagramlar kullanabilirsiniz. Tanımlamak ve sisteminizin işlevselliğini iletişim kurmak için UML bileşeni, sınıf, etkinlik ve sıralı diyagramlar kullanabilirsiniz.  
  
 Bkz: [kanal 9 videosu: mimariyi modelleme aracılığıyla geliştirmek](http://go.microsoft.com/fwlink/?LinkID=252078).  
  
 Bu sürümde aşağıdaki UML diyagramları oluşturabilirsiniz:  
  
|**Diyagramı**|**Gösterir**|  
|-----------------|---------------|  
|[UML Etkinlik Diyagramları: Başvuru](../modeling/uml-activity-diagrams-reference.md)|Eylemler ve iş süreci içinde katılımcılar arasındaki iş akışı|  
|[UML Bileşen Diyagramları: Başvuru](../modeling/uml-component-diagrams-reference.md)|Bir sistem, arabirimler, bağlantı noktaları ve ilişkileri bileşenleri|  
|[UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)|Depolamak ve sistem ve aralarındaki ilişkiler veri değişimi için kullanılan türleri|  
|[UML Sıralı Diyagramlar: Başvuru](../modeling/uml-sequence-diagrams-reference.md)|Nesneleri, bileşenleri, sistemleri veya aktörler arasındaki etkileşimler dizesi dizileri|  
|[UML Kullanım Durumu Diyagramları: Başvuru](../modeling/uml-use-case-diagrams-reference.md)|Kullanıcı hedefleri ve sistemin desteklediği görevleri|  
  
 Visual Studio'nun hangi sürümlerinin her diyagram türü desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Bir sistem veya var olan kod mimarisini görselleştirmek için aşağıdaki diyagramları oluşturur:  
  
|**Diyagramı**|**Gösterir**|  
|-----------------|---------------|  
|[Katman Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)<br /><br /> [Katman Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)|Sistemin üst düzey mimarisi|  
|Kod haritaları<br /><br /> [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)<br /><br /> [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)|Bağımlılıklar ve diğer mevcut koddaki ilişkileri|  
|Kod tarafından oluşturulan sınıf diyagramları<br /><br /> [Sınıf Diyagramları ile Çalışma (Sınıf Tasarımcısı)](../ide/working-with-class-diagrams-class-designer.md)|Türlerini ve ilişkilerini .NET kod|  
  
## <a name="common-tasks"></a>Ortak Görevler  
  
|**Konu**|**Görev**|  
|---------------|--------------|  
|[UML modelleme projeleri ve diyagramları oluşturma](../modeling/create-uml-modeling-projects-and-diagrams.md)|**Model oluşturma** ve diyagramları ekleyin.|  
|[UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md)|**Diyagramlarının** modeli düzenlemek için.|  
|[Paketleri ve ad alanlarını tanımlama](../modeling/define-packages-and-namespaces.md)|**Paketleri oluşturma** bir modeli farklı takım üyeleri üzerinde çalışabilir birimlere bölmek için.|  
|[UML sınıf diyagramları aracılığıyla kod oluşturma](../modeling/generate-code-from-uml-class-diagrams.md)|**Sınıf diyagramlarından C# kodu oluşturabilir** uygulamanızı başlatmak için.|  
|[Modelinizi profiller ve stereotipler aracılığıyla özelleştirme](../modeling/customize-your-model-with-profiles-and-stereotypes.md)|**Model öğelerini özelleştirmek** stereotipler belirli amaçlar için standart UML model öğelerini genişletmek için kullanma.|  
|[Model öğelerini ve iş öğelerini bağlama](../modeling/link-model-elements-and-work-items.md)|**Model öğelerini ve iş öğeleri arasında bağlantılar oluşturmak** görevleri, test çalışmalarını, hataları, gereksinimleri, izlemenize yardımcı olmak için sorunları veya diğer tür çalışmalar, modelinizin belirli bir kısmı ile ilişkili.|  
|[Diyagramları görüntü olarak dışarı aktarma](../modeling/export-diagrams-as-images.md)|**Model ve diyagramlarını kaydetme** diğer kullanıcılarla paylaşmak üzere, kullanmayın olanlar dahil [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].|  
  
## <a name="related-tasks"></a>İlişkili görevler  
  
|**Konu**|**Görev**|  
|---------------|--------------|  
|[Kodu görselleştirme](../modeling/visualize-code.md)|Kod haritaları oluşturmak ve görselleştirerek tanımadıkları kodlarla katman diyagramlarına daha iyi anlayın.|  
|[Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)|Kullanıcıların ihtiyaçlarını açıklamak ve modelleri kullanır.|  
|[Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)|Genel yapısı ve sisteminizin davranışını tanımlamak ve kullanıcıların ihtiyaçlarını karşıladığından emin olmak için modelleri kullanır.|  
|[Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)|Yazılımınızı kullanıcılarınızın ihtiyaçlarını ve sisteminizin genel mimarisi ile tutarlı kalmasını sağlayın.|  
|[Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)<br /><br /> [Çevik Yazılım geliştirmede modeller kullanma](http://msdn.microsoft.com/en-us/592ac27c-3d3e-454a-9c38-b76658ed137f)|Anlama ve kendi geliştirme sırasında sisteminizi değiştirme yardımcı olması için modelleri kullanır.|  
|[Modelleme çözümünüzün yapısını oluşturma](../modeling/structure-your-modeling-solution.md)|Büyük ve orta ölçekli projelerde modelleri düzenleyin.|  
  
## <a name="external-resources"></a>Dış Kaynaklar  
  
|**Kategori**|**Bağlantılar**|  
|------------------|---------------|  
|**Forumları**|-   [Visual Studio Görselleştirme ve Modelleme Araçları](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Görselleştirme ve modelleme SDK'sını (DSL araçları)](http://go.microsoft.com/fwlink/?LinkId=184721)|



