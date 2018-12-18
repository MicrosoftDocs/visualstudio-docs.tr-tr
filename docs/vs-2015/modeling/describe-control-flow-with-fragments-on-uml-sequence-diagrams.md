---
title: Denetim akışını UML sıralı diyagramlar üzerinde açıklayan | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.interactionoperand
- vs.teamarch.sequencediagram.combinedfragment
helpviewer_keywords:
- UML sequence diagrams, control flow
- UML sequence diagrams, fragments
- sequence diagrams, fragments
- sequence diagrams, control flow
ms.assetid: efcc0949-be7e-4cf4-99ef-47c36b3803ae
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4ab4c65e554e9eef75a1761719ce19f3312e07ce
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727657"
---
# <a name="describe-control-flow-with-fragments-on-uml-sequence-diagrams"></a>Denetim akışını UML sıralı diyagramlarında parçalarla açıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir UML sıralı diyagramda *Birleşik Parçalar* döngüleri, dalları ve başka alternatifler sağlar.  
  
 Bir veya daha fazla birleştirilmiş parça oluşur *etkileşim işlenenleri*, ve bunların her biri bir veya daha fazla iletiler, etkileşim kullanımları veya birleştirilmiş parçaları barındırır.  
  
> [!NOTE]
>  Bu konu, sıralı diyagramlar parçalarında hakkındadır. UML sıralı diyagramlar okuma hakkında daha fazla bilgi için bkz. [UML sıralı diyagramlar: başvuru](../modeling/uml-sequence-diagrams-reference.md). UML sıralı diyagramlar çizin hakkında daha fazla bilgi için bkz. [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md).  
  
 ![Birleşik iki Etkileşim İşleneniyle parça](../modeling/media/uml-seqfragments.png "UML_SeqFragments")  
  
 Aşağıdaki şekilde gösterilen öğeler aşağıdaki gibidir.  
  
1.  Birleştirilmiş parça. Birleştirilmiş parçaları birkaç türü vardır. Bu örnekte, bir Alt iletileri alternatif dizileri oluşabilir göstermek için kullanabileceğiniz birleştirilmiş parça.  
  
2.  Etkileşim işlenenleri. Her bir birleştirilmiş parça iletiler, etkileşim kullanımları ve birleştirilmiş parçaları daha küçük içerebilir en az bir etkileşim işleneni içerir. Bu örnekte, Alt birleştirilmiş parça iletilerin iki alternatif dizileri gösteren iki etkileşimi işlem vardır.  
  
3.  İçinde tıklayarak her etkileşim işlenen ayrı ayrı seçebilirsiniz. Alt sınır görülebilir böylece bu örnekte, üst etkileşim işlenen seçilir. Genellikle, yalnızca arasındaki çizgi etkileşim işlenenleri görülebilir.  
  
    > [!NOTE]
    >  Üst etkileşim işlenen seçmek için çok yakın birleştirilmiş parça üst kısmına tıklamanız gerekir değil.  
  
4.  Cf. Bir koruma her etkileşim işlenen verebilirsiniz. Bu, altında etkileşim işleneni içinde iletileri gerçekleştirilecek koşul açıklar.  
  
## <a name="creating-combined-fragments"></a>Birleşik parçaları oluşturma  
 Oluşturabileceğiniz parça türlerinin bir listesi için bkz. [oluşturabileceğiniz](#KindsOfFragment).  
  
#### <a name="to-create-a-combined-fragment"></a>Birleştirilmiş parça oluşturmak için  
  
1. Bir iletiyi veya iletileri tümü aynı yaşam çizgisinin veya yürütme oluşması başlatmak, bir dizi seçin.  
  
   > [!NOTE]
   >  Birden fazla ileti seçerseniz, kesintisiz bir dizi oluşturması gerekir.  
  
2. İletileri birine sağ tıklayın, fareyle **Surround With**ve gibi istediğiniz birleştirilmiş parça türü ardından **Alt birleştirilmiş parça**.  
  
    Yeni bir birleştirilmiş parça görünür. Başlık gibi seçtiğiniz birleştirilmiş parça türü belirtir **Alt**.  
  
    Birleştirilmiş parça seçtiğiniz iletileri içeren bir parça yoktur.  
  
   Daha fazla etkileşim işlenenleri birleştirilmiş parça için bazı türleri ekleyebilirsiniz.  
  
   İletileri birleştirilmiş parça içinde yeniden sonra seçin **düzeni yeniden Düzenle** birleştirilmiş parça çerçeve yeniden boyutlandırmak için kısayol menüsünde.  
  
#### <a name="to-add-a-new-interaction-operand-to-a-combined-fragment"></a>Yeni bir etkileşim işleneni için birleştirilmiş bir parça eklemek için  
  
1. Etkileşim işleneni (2) dışında herhangi bir kapsanan parça ve birleştirilmiş parça başlığının altına içinde boş bir alana sağ tıklayın.  
  
2. İşaret **ekleme**.  
  
3. Tıklayın **önce etkileşim işleneni**, veya **sonra etkileşim işleneni**.  
  
4. İleti araçları kullanarak yeni etkileşim işleneni içinde veya var olan iletileri yapıştırarak iletileri ekleyebilirsiniz.  
  
   Ayarlayabileceğiniz **Guard** iletilerin içinde gerçekleştirilir koşulları tanımlamak için etkileşim işleneninin özelliği. Örneğin, bir **döngü** birleştirilmiş parça, bu sırada döngünün devam koşulu belirtmek için koruma kullanabilirsiniz. İçinde bir **Alt** birleşik parça, her etkileşimi işlenen için ayrı bir koşul belirtebilirsiniz.  
  
#### <a name="to-set-the-guard-of-an-interaction-operand"></a>Etkileşim işleneninin ayarlamak için  
  
1. Etkileşim işleneni (2) dışında herhangi bir kapsanan parça içinde boş bir alana tıklayın.  
  
    Etkileşim işleneni ve koruma koşulu etrafında bir seçim kenarlığı görüntülenir.  
  
    Başlıkta **özellikleri** penceresi şunu gösterir **etkileşim işleneni**.  
  
2. Koruma koşulunu yazın.  
  
    Koşul, parça (4) en görünür.  
  
   Birleştirilmiş parçaları bazı tür özelliklerini ayarlayabilirsiniz.  
  
#### <a name="to-set-or-view-the-properties-of-a-combined-fragment"></a>Ayarlamak veya birleştirilmiş parça özelliklerini görüntülemek için  
  
-   Birleştirilmiş parça başlığında sağ tıklayın ve ardından **özellikleri**.  
  
    > [!NOTE]
    >  Birleştirilmiş parça farklı türlerde farklı özelliklere sahiptir.  
  
##  <a name="KindsOfFragment"></a> Birleştirilmiş parça türü  
  
### <a name="fragments-describing-control-flow"></a>Denetim akışı açıklayan parçaları  
 Basit sıralı diyagram, tek bir genel sıra gösterir. Birleştirilmiş parçaları aşağıdaki türde farklı anlarda da oluşabilir farklılıkları açıklamak için kullanabilirsiniz.  
  
|Parça türü|Açıklama|  
|-------------------|-----------------|  
|**iyileştirilmiş**|İsteğe bağlı. Olabilir veya olmayacak bir dizisini alır. Korumada altında oluştuğu koşul belirtebilirsiniz.|  
|**Alt**|İletilerin alternatif dizileri içeren parçaları listesini içerir. Herhangi bir anda yalnızca bir sıralı gerçekleşir.<br /><br /> Bir koruma hangi koşullar altında çalıştığını göstermek için her parça koyabilirsiniz. İn **başka** başka bir koruma doğru ise bir parça çalışması gerektiğini belirtir. Tüm cf false ve yoksa hiçbir **başka**, parçalar hiçbiri yürütülmez.|  
|**döngü**|Parça bazı sayıda yineler. Korumada koşul yinelenmesi gerektiğini belirtebilirsiniz.<br /><br /> Döngü birleştirilmiş parçaları özelliklerine sahip **Min** ve **Max**, parça yinelenebilen bir kez minimum ve maksimum sayısını belirtin. Varsayılan değer kısıtlaması yoktur.|  
|**sonu**|Bu parçasını yürütülürse, dizinin kalan terk edilir. Koruma, kesme oluşur koşulu belirtmek için kullanabilirsiniz.|  
|**Par**|Paralel. Olaylar aralıklı olabilir.|  
|**Kritik**|Par veya Seq parçası içinde kullanılır. Bu parçadaki iletileri diğer iletilerle aralıklı olabilir gerekir değil olduğunu gösterir.|  
|**Seq**|İki veya daha fazla işlenen parçası vardır. Aynı yaşam çizgisini içeren iletileri sırasına göre parçaları gerçekleşmelidir. Aynı yaşam çizgilerini içermeyen yerlerde, iletileri farklı parçaları paralel olarak aralıklı olabilir.|  
|**Katı**|İki veya daha fazla işlenen parçası vardır. Parçalar, verilen sırada olmalıdır.|  
  
### <a name="fragments-about-how-to-interpret-the-sequence"></a>Parçaları dizisi yorumlama hakkında  
 Varsayılan olarak, sıralı diyagram oluşabilir ileti serilerinden birini belirtir. Çalışan sistemindeki diğer iletiler, diyagram üzerinde gösterilecek seçmediniz oluşabilir.  
  
 Bu yorumu değiştirmek için aşağıdaki parça türleri kullanılabilir.  
  
|Parça türü|Açıklama|  
|-------------------|-----------------|  
|**Göz önünde bulundurun**|Bu parçaların açıkladığı iletilerinin listesini belirtir. Diğer iletiler çalışan sistemde ortaya çıkabilir, ancak bu açıklama amaçları doğrultusunda önemli değildir.<br /><br /> Listedeki **iletileri** özelliği.|  
|**Yoksay**|Bu parça açıklanmayan iletilerin listesi. Çalışan sistemindeki oluşabilir, ancak bu açıklama amaçları doğrultusunda önemli değildir.<br /><br /> Listedeki **iletileri** özelliği.|  
|**Assert**|İşlenen parça yalnızca geçerli dizileri belirtir. Genellikle, bir veya Ignore parça içinde kullanılır.|  
|**Neg**|Bu parçasında gösterilen dizisi olmaması gerekir. Genellikle, bir veya Ignore parça içinde kullanılır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)   
 [UML sıralı diyagramlar: başvuru](../modeling/uml-sequence-diagrams-reference.md)   
 [UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md)



