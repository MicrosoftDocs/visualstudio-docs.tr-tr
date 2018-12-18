---
title: 'UML etkinlik diyagramları: Başvuru | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.activitydiagram.diagram
- vs.teamarch.activitydiagram.toolbox
- vs.teamarch.UMLModelExplorer.activitydiagram
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
- behaviors, UML
ms.assetid: 07efcd17-2a96-4052-9957-6dcccbb725ee
caps.latest.revision: 50
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2dcfa13a7ac97a5afd3e315fcef13a706c5f4bce
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810474"
---
# <a name="uml-activity-diagrams-reference"></a>UML Etkinlik Diyagramları: Başvuru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir *etkinlik diyagramı* yazılım işlem veya iş sürecini, bir dizi eylem iş akışı olarak gösterilir. Kişiler, yazılım bileşenlerini veya bilgisayarların bu eylemleri gerçekleştirebilirsiniz.  
  
 Etkinlik diyagramı, aşağıdaki örneklerde gibi çeşitli türlerde işlemleri tanımlamak için kullanabilirsiniz:  
  
- Bir iş sürecini veya kullanıcıların sisteminizi arasındaki iş akışı. Daha fazla bilgi için [kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md).  
  
- Bir kullanım örneği, adımların. Daha fazla bilgi için [UML Kullanım durumu diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md).  
  
- Yazılım protokol, diğer bir deyişle, izin verilen dizileri bileşenleri arasındaki etkileşimler dizesi.  
  
- Bir yazılım algoritması.  
  
  Bu konuda, etkinlik diyagramlarını kullanabilirsiniz öğeleri açıklar. Daha ayrıntılı etkinlik çizim hakkında bilgi için bkz [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md). UML etkinlik diyagramı oluşturmak için **mimarisi** menüsünü tıklatın **yeni UML veya katman diyagramı**. Genel olarak modelleme diyagramları çizmek hakkında daha fazla bilgi için bkz. [Düzenle UML modellerini ve diyagramları](../modeling/edit-uml-models-and-diagrams.md).  
  
## <a name="reading-activity-diagrams"></a>Etkinlik diyagramları okuma  
 Aşağıdaki bölümlerde tablolar etkinlik diyagramı ve ana özelliklerini kullandığınız öğeleri açıklar. Öğelerin özelliklerinin tam listesi için bkz. [etkinlik diyagramlarındaki öğelerin özellikleri](../modeling/properties-of-elements-on-uml-activity-diagrams.md).  
  
 Eylemler ve etkinlik diyagramında görünen diğer öğelerin bir etkinlik oluşturur. Etkinlik UML Model Gezgini'nde görebilirsiniz. Diyagrama ilk öğeyi eklediğinizde, oluşturulur.  
  
 Bir diyagram okumak için bir belirteç veya iş parçacığı denetimin bağlayıcılar boyunca bir eylemden geçirir olduğunu hayal edin.  
  
### <a name="simple-control-flows"></a>Basit bir denetim akışı  
 Bir dizi eylem dallar ve döngüler ile gösterebilirsiniz. Akış denetimi açıklayan bölümüne burada açıklanan öğeleri kullanma hakkında daha fazla bilgi için bkz. [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md).  
  
 ![Basit bir iş akışı](../modeling/media/uml-actovsimple.png "UML_ActOvSimple")  
  
||||  
|-|-|-|  
|**Şekil**|**Öğe**|**Açıklama ve ana özellikleri**|  
|1.|**Eylem**|Bir etkinlikte adımda kullanıcılardan veya yazılımlardan bazı görevleri gerçekleştirir.<br /><br /> Bir belirteç tüm gelen akışlar sunuldu eylemi başlatabilirsiniz. Sona erdiğinde belirteçleri tüm giden akışlar gönderilir.<br /><br /> -   **Gövde** -ayrıntılı olarak eylemi belirtir.<br />-   **Dil** -gövdesi içindeki ifade dili.<br />-   **Yerel koşul Sonralarına** -yürütme sona erdiğinde karşılanması gereken kısıtlamaları. Eylem tarafından elde edilen hedefi.<br />-   **Yerel önkoşulları** -yürütme başlamadan önce karşılanması gereken kısıtlamaları.|  
|2|**Denetim Akışı**|Bir bağlayıcı Eylemler arasındaki denetim akışı gösterilmektedir. Diyagram yorumlamak için bir belirteç sonraki bir eylemden akışları düşünün.<br /><br /> Bir iş akışı oluşturmak için kullanın **bağlayıcı** aracı.|  
|3|**İlk düğüm**|İlk eylem veya eylem etkinliğindeki gösterir. Bir etkinlik başladığında, ilk düğümü aracılığıyla bir belirteç akar.|  
|4|**Etkinliğin son düğümü**|Etkinlik bitiş olayı. Bir belirteç geldiğinde etkinlik sona erer.|  
|5|**Karar düğümü**|Bir akışta koşullu bir dal. Bir giriş ve çıkışları iki veya daha fazla vardır. Gelen bir belirteci yalnızca bir çıkışları ortaya çıkar.|  
|6|**koruma**|Bir belirteç bağlayıcı boyunca akış olup olmadığını belirten bir koşul. Karar düğümünün giden akışlar üzerinde en sık kullanılan.<br /><br /> Bir koruma ayarlamak için bir akış sağ tıklayın, **özellikleri** ve ardından **koruyucu** özelliği.|  
|7|**Birleştirme düğümü**|Karar düğümüyle ayrılmış akışlar birleştirmek için gereklidir. İki veya daha fazla giriş ve bir çıktı. Çıkıştan herhangi bir giriş belirteç.|  
|8|**Yorum**|Bağlı öğeleri hakkında ek bilgi sağlar.|  
|9|**Davranış eylem çağrısı**|Başka bir etkinlik diyagramı'nda daha ayrıntılı bir şekilde tanımlanan bir eylem.<br /><br /> -   **IsSynchronous** - etkinlik kapsayıcınızın doğru eylemi bekler.<br />-   **Davranış** -etkinlik çağrılır.|  
|(gösterilmez)|**İşlem eylem çağrısı**|Bir sınıfın bir örneği üzerinde bir işlem çağıran eylem.|  
||**Etkinlik**|Bir etkinlik diyagramı tarafından düzenlenmiş iş akışı. Bir etkinlik özelliklerini görmek için bunu seçmelisiniz **UML Model Gezgini**.<br /><br /> -   **Salt okunur** - true ise etkinlik herhangi bir nesne durumunu değiştirmemesi gerekir.<br />-   **Tek yürütme** - true ise en fazla Bu diyagramda, tek bir yürütme birer birer.|  
||**UML etkinlik diyagramı**|Bir etkinlik gösteren diyagram. Özelliklerini görmek için diyagramın boş bir kısmına tıklayın. **Not:** adları etkinlik diyagramı, Diyagram ve diyagram tarafından görüntülenen etkinlik içeren dosyayı farklı olabilir.|  
  
### <a name="concurrent-flows"></a>Eşzamanlı Akışlar  
 Aynı anda yürütmek Eylemler dizisi tanımlayabilirsiniz. Çizim eşzamanlı akışlar daha fazla bilgi için bkz.  
  
 ![Eş zamanlı akışını gösteren bir etkinlik diyagramı](../modeling/media/uml-actovconcurrent.png "UML_ActovConcurrent")  
  
||||  
|-|-|-|  
|**Şekil**|**Öğe**|**Açıklama**|  
|11|**Çatal düğümü**|Tek bir akış eşzamanlı akışlara böler. Gelen her belirteç, her giden bağlayıcıdaki bir belirteç oluşturur.|  
|12|**Düğüm katılın**|Eşzamanlı akışlara akar tek bir akış birleştirir. Bekleyen bir belirteci her gelen akış sahip olduğunda, bir belirteç çıktı oluşturulur.|  
|13|**Sinyal eylemi Gönder**|Başka bir etkinlik veya eş zamanlı bir iş parçacığı aynı etkinlik için bir mesaj ya da sinyal gönderen bir eylem. İleti içeriği ve tür eyleme ait başlık tarafından kapsanan veya ek açıklamalarda belirlenir.<br /><br /> Eylem, bir nesne akışı veya giriş PIN (16) eyleme geçirilebilir sinyal içinde veri gönderebilirsiniz.|  
|14|**Olay eylemi kabul edin**|Eylem devam etmeden önce bir ileti ya da sinyal bekleyen bir eylem. Eylem alabilir iletisinin türü başlık tarafından kapsanan veya ek açıklamalarda belirlenir.<br /><br /> Gelen denetim akışı eylem varsa her bir ileti aldığında bir belirteç oluşturur.<br /><br /> Eylem, bir nesne akışı veya çıkış PIN'i (17) geçirilebilir sinyal içinde veri alabilir.<br /><br /> -   **IsUnmarshall türde** - true ise birden çok çıktı pini olabilir ve veri açtığına unmarshalled ise. False ise, tüm veriler tek bir PIN'in görünür.|  
  
###  <a name="DataFlow"></a> Bir veri akışı  
 Bir eylem veri akışını tanımlayabilir. Bu bölümde kullanılan öğeleri hakkında daha fazla bilgi için etkinlik diyagramı çizmek için yönergeler çizim veri akışları bölümüne bakın.  
  
 ![Etkinlik diyagramı veri akışını gösteren](../modeling/media/uml-actovdata.png "UML_ActOvData")  
  
||||  
|-|-|-|  
|**Şekil**|**Öğe**|**Açıklama**|  
|15|**Nesne düğümü**|Akış boyunca geçen verileri temsil eder.<br /><br /> -   **Sıralama** - nasıl birden çok belirteç depolanır.<br />-   **Seçimi** -verilere filtre başka bir şemada tanımlanan bir işlem başlatır.<br />-   **Üst sınır** -0 verileri doğrudan akış boyunca; geçmesi gerektiğini gösterir \* veri akışı depolanabileceğini belirtir.<br />-   **Tür** -nesnelerin türü depolanan ve aktarılan.|  
|16|**Giriş PIN**|Yürütüldüğünde bir eylemi alıp verileri temsil eder.<br /><br /> -   **Tür** -aktarılan nesnelerin türü.|  
|17|**Çıkış PIN**|Yürütüldüğünde bir eylem üretir verileri temsil eder.<br /><br /> -   **Tür** -aktarılan nesnelerin türü.|  
|18|**Etkinlik parametre düğümü**|Üzerinden veri alınabilmesi veya etkinlik tarafından oluşturulan bir nesne düğümü.<br /><br /> Diyagram tarafından temsil edilen etkinlik başka bir etkinlik tarafından çağrıldığında ya da diyagramda bir işlemi ya da işlevin açıkladığında kullanılır.<br /><br /> -   **Tür** -aktarılan nesnelerin türü.|  
|(gösterilmez)|**Nesne akışı**|Eylemler ve nesne düğümleri arasındaki veri akışını gösteren bir bağlayıcı.<br /><br /> Bir nesne akışı oluşturmak için kullanın **bağlayıcı** giriş veya çıkış PIN ya da bir nesne düğümü başka bir öğeye bağlamak için aracı.<br /><br /> -   **Seçimi** -verilere filtre başka bir şemada tanımlanan bir işlem başlatır.<br />-   **Dönüştürme** -verileri dönüştüren başka bir şemada tanımlanan bir işlem başlatır.<br />-   **IsMulticast** -birden çok alıcı nesneleri veya bileşenleri olabileceğini gösterir.<br />-   **IsMultiReceive girdilerin** -çeşitli nesneleri veya bileşenleri alınabileceğini gösterir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md)   
 [UML Etkinlik Diyagramları: Yönergeler](../modeling/uml-activity-diagrams-guidelines.md)



