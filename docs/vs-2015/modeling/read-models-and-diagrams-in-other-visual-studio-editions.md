---
title: Modelleri ve diyagramları diğer Visual Studio sürümlerinde okuma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6d104d8d92345ba56d390fdd7ad9b856432b4c92
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757362"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Diğer Visual Studio sürümlerindeki modelleri ve diyagramları okuma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir model oluşturmayı desteklemiyor Visual Studio sürümünde bir modeli açtığınızda, model salt okunur modunda açar. Bu modda, diyagram düzenini değiştirebilirsiniz, ancak modeli değiştiremezsiniz.  
  
 Visual Studio'nun hangi sürümlerinin modeli oluşturulmasını desteklemek için bkz [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="obtaining-access-to-a-model-and-diagrams"></a>Bir Model ve diyagramlarını erişim elde etme  
 Bir UML diyagram ya da bir katman diyagramı okumak için ilk modelleme projesini açmak için Visual Studio'yu kullanın ve ardından diyagramında açın.  
  
 Bir UML diyagram veya katman diyagramı, okumak istiyorsanız bu nedenle, ayrıca içinde oluşturulmuş bir modelleme projesine erişiminiz olmalıdır. Projeden erişerek ya da bunu yapabilirsiniz [!INCLUDE[esprscc](../includes/esprscc-md.md)], ya da proje dosyalarının bir kopyasını alma.  
  
> [!NOTE]
>  Bu kod için geçerli değildir haritaları ve .NET sınıf diyagramları koddan oluşturulan. Bu diyagramlar bir modelleme projesi bağımsız olarak görüntülenebilir.  
  
 Bir UML diyagram ya da bir katman diyagramı okumak için gereken dosyalar en düşük kümesini şu şekildedir:  
  
-   İki dosyaları okumak için örneğin, istediğiniz diyagram için diyagram **MyDiagram.classdiagram ve MyDiagram.classdiagram.layout**.  
  
    > [!NOTE]
    >  Katman diyagramları için adlı bir dosya da olmalıdır _Diyagramım_**. layerdiagram.suppressions**.  
  
-   Modelleme Proje dosyası (**MyModel.modelproj**)  
  
-   Kök model dosyası (**ModelDefinition\MyModel.uml**)  
  
-   Şemada başvurulan herhangi bir paket için paket dosyaları (**ModelDefinition\MyPackage.uml**)  
  
## <a name="changes-that-you-can-make-in-read-only-mode"></a>Salt okunur modunda yaptığınız değişiklikler  
 Bir model oluşturmayı desteklemiyor Visual Studio sürümünde bir model ve diyagramlarını açarsanız, modeli değiştiremezsiniz. Diğer bir deyişle, öğeleri ve ilişkileri diyagramlarda veya model Gezgini'nde görüntülenen değiştiremezsiniz. Ancak, diyagramların düzene bazı değişiklikler yapabilirsiniz:  
  
- Şekilleri ve bağlayıcıları diyagram üzerinde yeniden düzenleyin.  
  
- Şekilleri genişletme ve daraltma.  
  
  Bu değişiklikleri kaydedebilirsiniz. Değişikliklerinizi diğer kullanıcılarına görünür hale getirmek isterseniz, en az güncelleştirilmiş gönderdiğiniz gerekir **.layout** dosyaları.  
  
##  <a name="RelatedTopics"></a> İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Katman Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)|Bir katman diyagramı, mevcut ya da önerilen bir mimari yapısı gösterilmektedir. Kodu yazıldığında otomatik olarak bir katman diyagramına karşı doğrulanabilir.|  
|[UML Etkinlik Diyagramları: Başvuru](../modeling/uml-activity-diagrams-reference.md)|Etkinlik diyagramı, iş sürecini veya yazılım, iş akışı gösterir.|  
|[UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)|Türleri ve ilişkiler kod, veritabanı şemaları, protokolleri veya iş etki alanını tanımlamak için kullanılan terimler sözlüğü gibi birçok bağlamlarda kullanılan bir sınıf diyagramı gösterir.|  
|[UML Bileşen Diyagramları: Başvuru](../modeling/uml-component-diagrams-reference.md)|Bir bileşen diyagramı ayrılabilir parçaların bir yazılım tasarımı ve arabirimlerini gösterir.|  
|[UML Sıralı Diyagramlar: Başvuru](../modeling/uml-sequence-diagrams-reference.md)|Sıralı diyagram, yazılım tasarımı öğeler arasındaki etkileşimler gösterilmektedir.|  
|[UML Kullanım Durumu Diyagramları: Başvuru](../modeling/uml-use-case-diagrams-reference.md)|Bir kullanım durumu diyagramı, sistemi ve belirli hedeflere ulaşmak için gerçekleştirebileceği etkinlikleri kullanıcıları gösterir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)



