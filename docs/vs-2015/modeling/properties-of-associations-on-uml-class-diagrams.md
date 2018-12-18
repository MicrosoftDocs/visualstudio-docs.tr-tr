---
title: Sınıf diyagramları UML İlişkilendirmelerin Özellikleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.common.association.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: f82bcd34-7903-4c00-8da1-613efa07d223
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: b132ee2aa0f67662fcfcad92b8ae945c2d66c680
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810314"
---
# <a name="properties-of-associations-on-uml-class-diagrams"></a>UML sınıf diyagramlarındaki ilişkilendirmelerin özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir UML sınıf diyagramı çizebilirsiniz *ilişkilendirmeleri* herhangi bir tür çifti arasında. Bir sınıf, arabirim veya numaralandırma türüdür.  

 Bir ilişkilendirme geliştirdiğiniz sistem ilgili türlerinin örnekleri arasında tür bağlantılar içerdiğini gösterir. Genellikle, bu bağlantıları uygulanmasıyla ilgili herhangi bir şey göstermez. Örneğin, bunlar işaretçileri, bir tablodaki satırlar XML adlarında çapraz başvuru olması ve benzeri.  

 Bir ilişkilendirme özniteliğini veya özniteliklerini çifti gösteren grafiksel bir yöntemdir. Örneğin, menü türünde bir öznitelik için Restoran sınıfı tanımladıysanız, Restoran menüsü arasındaki ilişkilendirmeyi çizerek aynı tanımı durumu.  

 Bir ilişkilendirme çizmek için tıklayın **ilişkilendirme** araç kutusunda, ilk tür, ikinci tıklatın. Örnekleri aynı türdeki diğer örneklerle bağlanabilir göstermek için iki kez aynı türüne tıklayın.  

## <a name="properties"></a>Özellikler  
 Bir UML sınıf diyagramında bir ilişkilendirmenin özellikleri şunlardır.  

 Bir ilişkilendirmenin özellikleri görmek için ilişkilendirme sağ tıklayın ve ardından **özellikleri**. Özellikler, Özellikler penceresinde görünür.  

 Bazı özellikleri de aşağıdaki çizimde gösterildiği gibi diyagramda görülebilir.  

 ![İlişkilerdeki Özellikler](../modeling/media/uml-classprop.png "UML_ClassProp")  

|**Özelliği**|Açıklama|  
|------------------|-----------------|  
|**Ad (1)**|İlişkiyi tanımlar. De Orta noktasında ilişki diyagramda görünür.|  
|**Tam adı**|İlişkilendirmeyi benzersiz şekilde tanımlar. İle ilişkilendirmenin ilk rol içeren paket tam adı öneki.|  
|**İş öğeleri**|Bu ilişki için bağlı iş öğelerinin sayısı. İş öğeleri bağlamak için bkz [bağlantı model öğelerini ve iş öğeleri](../modeling/link-model-elements-and-work-items.md).|  
|**Renk**|Bağlayıcının rengi. Diğer özelliklerin aksine, bu ilişki, modeli temel ilişki özelliği bu görünüm özelliğidir.|  
|**İlk rol**<br /><br /> **İkinci Rol**|İlişkilendirmenin her ucundaki rol olarak adlandırılır. Her rol ilişkilendirmenin karşı ucunda sınıfı eşdeğer bir öznitelik özelliklerini açıklar.<br /><br /> Örnek diyagramında menü ve menü öğesi arasındaki ilişki menü ve içeriği adlı rol yok.<br /><br /> Menü sınıfı üzerinde bir öznitelik adı içeriğidir.|  

### <a name="properties-of-each-role"></a>Her rol özellikleri  
 Her bir rolün özelliklerini görmek için genişletin **ilk rol** veya **ikinci rol** özelliği.  


|     **Özelliği**     |          **Default**          |                                                                                                                                                                                                                                                                                                                                        Açıklama                                                                                                                                                                                                                                                                                                                                         |
|----------------------|-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Rol adı (2)**   | Bu roldeki türü adı |                                                                                                                                                                                                                                                                                                       Rolün adı. Diyagramda ilişkilendirmenin sonunun yakınında görünür.                                                                                                                                                                                                                                                                                                        |
|   **Toplama**    |             Yok.              |                                                                        **Hiçbiri** (4) - sınıf örnekleri arasındaki genel bir ilişkiyi temsil eder.<br /><br /> **Bileşik** (5) - Bu rol nesne karşıt rolü nesne içerir. Kullanabileceğiniz **bileşik** Bileşik toplama ile bir ilişki oluşturmak için aracı.<br /><br /> **Paylaşılan** (6) - bu rolün nesnede başka bir rolle nesne başvurular içerir. Kullanabileceğiniz **toplama** paylaşılan toplama ile ilişkilendirme oluşturmak için aracı.<br /><br /> Yerel kurala tam yorumu açıktır.                                                                         |
|    **Türetilmiş**    |             False             |                                                                                                                                                                                                                          TRUE ise bu bağlantının sonunda nesne diğer öznitelikler ve ilişkilendirmeler hesaplanır. Örneğin, MyWorkPlace MyEmployer.WorkPlace'den hesaplanır. Ayrıntılar veya açıklama eklenmiş bir yorum yazılmalıdır.                                                                                                                                                                                                                           |
| **Olan birleşim türetilmiş** |             False             |                                                                                                                                                                                                                                                                                                             TRUE ise bir türetilen türlerin roller kümesini birleşimi rolüdür.                                                                                                                                                                                                                                                                                                             |
|   **Gezinebilir**   |             Doğru              |                                                 Bu yönde ilişkilendirme okuyabilirsiniz. Karşı rol örneği göz önünde bulundurulduğunda, tanımlamakta olduğunuz yazılım bu rolün ilişkili örnek verimli bir şekilde belirleyebilirsiniz.<br /><br /> Bir ok (7) bir rol gezinebilir ve diğer değil, gezinebilir yönde ilişkilendirme görünür.<br /><br /> Varsayılan olarak, bir yönde gezilebilir ilişkilendirme ilişkilendirme aracı oluşturur. Çift yönlü bir ilişkilendirmeye dönüştürmek için ilişkisini seçin, görünür ve ardından eylem etiketine **olun çift yönlü**.                                                 |
|   **Salt okunur**   |             False             |                                                                                                                                                                                                                                                                                   True ise ilişki örneği oluşturulduktan sonra değiştirilemez. Her zaman aynı nesneye bağlantıdır.                                                                                                                                                                                                                                                                                    |
| **Çoğulluk (3)** |               1.               | **1** -ilişki her zaman bu sonuna bir nesneye bağlar. Şekilde, bir menü her menü öğesi vardır.<br /><br /> **0..1** - ya da bu ilişki sonu bir nesneye bağlantı veya bağlantı yoktur.<br /><br /> **\\**\* -ilişkinin diğer ucundaki her nesne bu sonunda nesneler koleksiyonunu bağlanır ve koleksiyon boş olabilir.<br /><br /> **1..\\**  \* -ilişkinin diğer ucundaki her nesne bu uçtaki en az bir nesneye bağlıdır. Şekilde, her menüye en az bir menü öğesi vardır.<br /><br /> *n* **...** *m* -diğer ucundaki her nesne koleksiyonu arasında vardır *n* ve *m* bu sonunda nesnelerine giden bağlantıları. |
|    **Sıralı**    |             False             |                                                                                                                                                                                                                                                                                                  TRUE ise döndürülen koleksiyon sıralı bir liste oluşturur. 1'den daha çok çeşitlilik için.                                                                                                                                                                                                                                                                                                   |
|    **Benzersiz**     |             False             |                                                                                                                                                                                                                                                                                              TRUE ise döndürülen koleksiyonda yinelenen değerler yoktur. 1'den daha çok çeşitlilik için.                                                                                                                                                                                                                                                                                              |
|    **Görünürlük**    |            Ortak             |                                                                                                                                                                                                                                 Genel - görünür genel<br /><br /> Özel - türü dışında görünür değil<br /><br /> Korumalı - sahibinden türetilen türler görünür<br /><br /> Package - aynı paket içindeki diğer türlere görünür.                                                                                                                                                                                                                                  |

## <a name="see-also"></a>Ayrıca Bkz.  
 [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)   
 [UML sınıf diyagramlarındaki türlerin özellikleri](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [UML sınıf diyagramlarındaki özniteliklerin özellikleri](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [UML sınıf diyagramlarındaki işlemlerin özellikleri](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)



