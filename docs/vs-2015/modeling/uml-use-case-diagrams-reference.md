---
title: 'UML Kullanım durumu diyagramları: Başvuru | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.usecasediagram.toolbox
- vs.teamarch.usecasediagram.diagram
- vs.teamarch.UMLModelExplorer.usecasediagram
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: aa15772b-eb67-4366-b145-b559112817df
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 64eece28fc46fce799eff01e7ed1e7302e939dbc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791775"
---
# <a name="uml-use-case-diagrams-reference"></a>UML Kullanım Durumu Diyagramları: Başvuru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da bir *kullanım örneği diyagramı* kullanan uygulama ya da sistemin ve onunla neler özetler. Bir UML Kullanım durumu diyagramı oluşturmak için **mimarisi** menüsünü tıklatın **yeni UML veya katman diyagramı**.  
  
 Bir kullanım durumu diyagramı, kullanıcı gereksinimlerini açıklaması bir odak olarak görev yapar. Bu gereksinimler, kullanıcılar ve ana bileşenleri arasındaki ilişkileri açıklar. Ayrıntılı gereksinimler tanımlamaz; Bunlar ayrı diyagramları veya her kullanım örneğine bağlanabilen belgelerde açıklanabilir. Kullanım örneği diyagramları anlamanıza, tartışın ve kullanıcılarınızın ihtiyaçlarını nasıl yardımcı olabileceği hakkında daha fazla bilgi için bkz: [kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md).  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!NOTE]
>  Bu konu, kullanım örneği diyagramları kullanılabilir öğeleri açıklar. Kullanım örneği diyagramları çizmek hakkında daha fazla bilgi için bkz. [UML kullanma örneği diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md). Modelleme diyagramları çizmek ve oluşturma hakkında daha fazla bilgi için bkz. [Düzenle UML modellerini ve diyagramları](../modeling/edit-uml-models-and-diagrams.md).  
  
## <a name="reading-use-case-diagrams"></a>Kullanım örneği diyagramları okuma  
 Aşağıdaki bölümlerde tablolarında ana özellikleri ile birlikte bir kullanım durumu diyagramı üzerinde kullanılabilir olan öğeler açıklanmaktadır. Özelliklerinin tam listesi için bkz. [UML öğeleri özelliklerini kullanma örneği diyagramları](../modeling/properties-of-elements-on-uml-use-case-diagrams.md).  
  
### <a name="actors-use-cases-and-subsystems"></a>Aktörleri kullanım örnekleri ve alt sistemlerin  
 ![Bir kullanım durumu diyagramı öğeleri](../modeling/media/uml-ucovactor.png "UML_UCOvActor")  
  
|**Şekil**|**Öğe**|**Açıklama ve ana özellikleri**|  
|---------------|-----------------|-----------------------------------------|  
|1.|**Aktör**|Bir kullanıcı, kuruluş veya uygulama ya da sistemin ile etkileşime giren bir dış sistem temsil eder. Bir aktör türü türüdür.<br /><br /> -   **Görüntü yolu** -varsayılan aktör simge yerine kullanılması gereken bir görüntü dosyasının yolu. Simgesi, Visual Studio projesi içinde bir kaynak dosyası olmalıdır.|  
|2|**Kullanım örneği**|Belirli bir hedefin takip içinde bir veya daha fazla aktör tarafından gerçekleştirilen eylemleri gösterir. Kullanım örneği, türü türüdür.<br /><br /> -   **Konular** -alt kullanım örneği göründüğü.|  
|3|**İlişkilendirme**|Aktörün bir kullanım örneği, parça aldığını gösterir.|  
|4|**Alt sistemi veya bileşeni**|Sistem veya üzerinde çalıştığınız uygulama veya bir parçası. Bir uygulamada tek bir sınıf için geniş bir ağdan herhangi bir şey olabilir.<br /><br /> Bir sistem veya bileşen destekleyen kullanım örneklerini, kendi dikdörtgeni içinde görünür. Bazı dikdörtgen dışında sisteminizin kapsamını açıklamak için kullanım örnekleri göstermek işe faydalı olabilir.<br /><br /> Bir alt sistemini bir kullanım durumu diyagramı, temel bir bileşen diyagramında aynı türde bir bileşen olarak sahiptir.<br /><br /> -   **Dolaylı olarak Örneklendirilmiş olduğu** - yanlış yürütülen sisteminizin bir veya daha fazla nesne doğrudan bu alt sistemine karşılık gelir. TRUE ise alt bağlı parçalarının yalnızca aracılığıyla yürütme sistemi görünen tasarımınızda yapıdır.|  
  
### <a name="structuring-use-cases"></a>Kullanım örnekleri yapılandırma  
 ![İle birlikte kullanım örnekleri, genişletme ve Genelleştirme](../modeling/media/uml-ucovstructure.png "UML_UCOvStructure")  
  
|Şekil|**Öğe**|Açıklama|  
|-----------|-----------------|-----------------|  
|5|**İçerir**|Dahil olmak üzere bir kullanım örneği çağrıları veya dahil edilen bir çağırır. Ekleme, bir kullanım durumu daha küçük adımlara nasıl ayrıldığını göstermek için kullanılır. Dahil olan kullanım ok ucu durumdur.<br /><br /> Diyagram adımlarının sırasını göstermez dikkat edin. Bu ayrıntıları açıklamak için bir etkinlik diyagramı, sıralı diyagram veya başka bir belgeye kullanabilirsiniz.|  
|6|**Genişletme**|Genişletme bir kullanım örneği, hedefler ve adımları genişletilmiş kullanım örneğine ekler. Uzantılar yalnızca belirli koşullar altında çalışır. Genişletilmiş kullanım örneğine ok ucu ' dir.<br /><br /> Diyagram uzantısı altında uygulandığı tam koşullar göstermez dikkat edin: bunları yorum veya diğer belge kaydedebilirsiniz.|  
|7|**Devralma**|Özelleştirilmiş ve genelleştirilmiş bir öğe ile ilgilidir. Ok ucu genelleştirilmiş öğesidir.<br /><br /> Özelleştirilmiş kullanım örneğine hedefleri ve kendi Genelleştirme aktörleri devralır ve daha belirli amaçlar ve onları elde etmek için kullanabileceğiniz adımlar ekleyebilirsiniz.<br /><br /> Özelleştirilmiş bir aktör, kullanım örnekleri, öznitelikleri ve kendi Genelleştirme ilişkilendirmelerini devralır ve daha fazlasını ekleyebilirsiniz.|  
|8|**Bağımlılık**|Kaynak tasarımını tasarımı hedefin bağlı olduğunu gösterir.|  
|9|**Yorum**|Genel notları diyagrama eklemek için kullanılır.|  
|10|**Yapıt**|Bir yapı, başka bir diyagrama veya belge bağlantısını sağlar. Çözüm Gezgini'nden bir dosya sürükleyerek oluşturabilirsiniz. Diyagram üzerindeki herhangi bir öğe için bir bağımlılık ile bağlanabilir. Bir yapı, genellikle bir kullanım örneği bir sıralı diyagram, OneNote sayfası, Word belgesi veya ayrıntılı olarak açıklayan bir PowerPoint sunusu bağlamak için kullanılır. Belge olabilir bir öğeyi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözümü ya da paylaşılan bir konumda bir SharePoint sitesi gibi bir belge.<br /><br /> -   **Köprü**. Diyagram veya belge URL veya dosya yolu.<br /><br /> Dosya veya web sayfasını, bağlantıları açmak için bir yapıya çift tıklayın.|  
|11 (gösterilmez)|**Paketleri**|Kullanım örnekleri, aktörler ve alt sistemlerin paketler içinde yer alabilir. Paket şekilleri diyagram üzerinde görünmez, ancak ayarlayabileceğiniz **LinkedPackage** diyagramın özelliği. Diyagram üzerinde daha sonra oluşturduğunuz öğeleri paket içine yerleştirilir. Daha fazla bilgi için [paketleri ve ad alanlarını tanımlama](../modeling/define-packages-and-namespaces.md).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML Kullanım durumu diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)   
 [UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md)   
 [UML sıralı diyagramlar: başvuru](../modeling/uml-sequence-diagrams-reference.md)   
 [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)   
 [UML Bileşen Diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md)   
 [UML Bileşen Diyagramları: Başvuru](../modeling/uml-component-diagrams-reference.md)



