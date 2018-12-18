---
title: 'UML sıralı diyagramlar: Başvuru | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.sequencediagram.diagram
- vs.teamarch.UMLModelExplorer.sequencediagram
- vs.teamarch.sequencediagram.toolbox
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- diagrams - modeling, UML sequence
- UML, sequence diagrams
ms.assetid: 366fc324-aeeb-4894-bd13-ec2e40754b8e
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5c92d9eb8ee7858a036fdbb8dfb621c269e3ed4c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797032"
---
# <a name="uml-sequence-diagrams-reference"></a>UML Sıralı Diyagramlar: Başvuru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da bir *sıralı diyagram* etkileşimi temsil eden sınıfları, bileşenleri, alt sistemler veya aktör örnekleri arasında iletiler dizisini gösterir. Zaman diyagram akar ve denetim akışını bir katılımcıdan diğerine gösterir. Nesneler ve sınıflar ve yöntemler yerine olayları görselleştirmek üzere sıralı diyagramlar kullanın. Aynı türde birden fazla örneği çok diyagramda görünebilir. Aynı mesajın birden fazla yinelenmiş de görünür.  
  
 UML sıralı diyagramlar bir UML modeli bir parçasıdır ve yalnızca UML modelleme projeleri içinde mevcuttur. Bir UML sıralı diyagramı oluşturmak için **mimarisi** menüsünde tıklatın **yeni UML veya katman diyagramı**. Oluşturma ve çizme hakkında daha fazla bilgi edinin [UML sıralı diyagramlar](../modeling/uml-sequence-diagrams-guidelines.md) veya [UML modelleme diyagramlarını](../modeling/edit-uml-models-and-diagrams.md) genel.  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="reading-sequence-diagrams"></a>Okuma sıralı diyagramlar  
 Aşağıdaki tabloda, sıralı diyagramda gördüğünüz öğeleri açıklar. Bunlar hakkında daha fazla bilgi edinin [öğeleri özellikleri](../modeling/properties-of-elements-on-uml-sequence-diagrams.md).  
  
 ![Sıralı Diyagram bölümlerini](../modeling/media/uml-sequence.png "UML_Sequence")  
  
|**Şekil**|**Öğe**|**Açıklama**|  
|---------------|-----------------|---------------------|  
|1.|**Yaşam çizgisi**|Bir satır aşağı zaman ilerlemesi sırasında etkileşim sırasında bir katılımcı gerçekleşen olayların sırasını temsil eden bir dikey çizgi. Bu katılımcı, bir sınıf, bileşen veya aktörün bir örneğini olabilir.|  
|2|**Aktör**|Geliştirmekte olduğunuz sisteme dış katılımcı.<br /><br /> Bir aktör simge yaşam çizgisinin üstünde ayarlayarak görünür yapabilirsiniz, **aktör** özelliği.|  
|3|**Zaman uyumlu iletisi**|Devam etmeden önce bir zaman uyumlu bir ileti yanıtı gönderen bekler. Çağrı hem dönüş diyagramda gösterilmektedir. Zaman uyumlu iletileri sıradan bir işlev çağrıları aynı şekilde davranan diğer ileti türlerinin yanı sıra, bir program içinde temsil etmek için kullanılır.|  
|4|**Zaman uyumsuz ileti**|Gönderen devam etmeden önce bir yanıt gerektirmeyen bir ileti. Zaman uyumsuz ileti gönderen yalnızca bir çağrıdan gösterir. Ayrı iş parçacıkları veya yeni bir iş parçacığı oluşturma arasındaki iletişimi temsil etmek için bu seçeneği kullanın.|  
|5|**Yürütme örneği**|Dikey gölgeli bir katılımcının yaşam çizgisinin üzerinde görünür ve katılımcı bir işlem olduğunda yürütme süresi temsil eden bir dikdörtgen.<br /><br /> Burada katılımcı bir ileti alır yürütmeyi başlatır. Başlatma iletisi yinelenen bir iletiyse, yürütme gönderene «return» bir ok ile sona erer.|  
|6|**İleti geri çağırma**|Daha önceki bir çağrıdan dönüş bekliyor katılımcı geri döndürür bir ileti. Elde edilen yürütme oluşumu varolanın üzerine görünür.|  
|7|**Kendi kendine iletisi**|Kendisi için bir ileti katılımcıdan. Elde edilen yürütme oluşumu gönderen yürütme üstünde görünür.|  
|8|**İleti oluşturma**|Katılımcı oluşturur bir ileti. Katılımcı bir oluşturma iletisi alırsa, bu aldığı ilk olmalıdır.|  
|9|**Bulundu iletisi**|Bilinmeyen veya belirtilmeyen bir katılımcı zaman uyumsuz bir ileti.|  
|10|**Kayıp iletisi**|Bilinmeyen veya belirtilmeyen bir katılımcı zaman uyumsuz bir ileti.|  
|11|**Yorum**|Bir yorum, bir yaşam çizgisi üzerinde herhangi bir noktaya eklenebilir.|  
|12|**Etkileşim kullanımı**|Başka bir şemada tanımlanan iletiler dizisini alır.<br /><br /> Oluşturmak için bir **etkileşim kullanımı**, Aracı'nı tıklatın ve sonra eklemek istediğiniz yaşam çizgileri arasında sürükleyin.|  
|13|**Birleştirilmiş parça**|Parçaların bir koleksiyonu. Her parça bir veya daha fazla iletiyi içine alır. Birleştirilmiş parçaları farklı tür vardır. Daha fazla bilgi için [açıklayın denetim akışını UML sıralı diyagramlarda parçalarla](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).<br /><br /> Bir parça oluşturmak için bir ileti sağ tıklatın, **Surround With**ve ardından parçanın türüne tıklayın.|  
|14|**Parça koruması**|Bir koşul parça meydana gelir için ilgili durum için kullanılabilir.<br /><br /> Ayarlamak için bir bölümünü seçin sonra guard'ı seçin ve bir değer yazın.|  
|**X**|**Yok etme olayı**|Nesne silinmiş veya erişilemez olduğu noktasını temsil eder. Her yaşam çizgisi altında görüntülenir.|  
||**Etkileşimi**|Sıralı Diyagramda gösterilen koleksiyonu yaşam çizgilerini ve iletileri. Etkileşim özelliklerini görüntülemek için projeyi seçmelisiniz **UML Model Gezgini**.|  
||**Sıralı diyagram**|Etkileşim gösteren diyagram. Özelliklerini görüntülemek için diyagramın boş bir bölümüne tıklatın. **Not:** adlarını sıralı diyagram, etkileşim görüntüler ve diyagramı içeren dosyanın farklı olabilir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)   
 [UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md)   
 [UML Kullanım durumu diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md)   
 [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)   
 [UML Bileşen Diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md)   
 [UML Bileşen Diyagramları: Başvuru](../modeling/uml-component-diagrams-reference.md)



