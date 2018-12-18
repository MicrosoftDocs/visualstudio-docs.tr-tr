---
title: UML öğelerin özelliklerini sıralı diyagramlar | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.properties
- vs.teamarch.sequencediagram.shapes.properties
helpviewer_keywords:
- UML sequence diagrams, properties
- sequence diagrams, properties
ms.assetid: 475c10f3-a2d2-4a1e-b366-dc28997d437e
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 01d63e39967df361d87ff0182b1c85b6ecd2fdb6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793905"
---
# <a name="properties-of-elements-on-uml-sequence-diagrams"></a>UML sıralı diyagramlarındaki öğelerin özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML sıralı diyagramı her öğe diyagram üzerindeki özellikleri vardır. Öğenin özelliklerini görmek için diyagram üzerinde veya öğeye sağ tıklayın **UML Model Gezgini** ve ardından **özellikleri**. Özellikleri görünür **özellikleri** penceresi.  
  
> [!NOTE]
>  Bu konu UML sıralı diyagramlarındaki öğelerin özellikleri hakkındadır. UML sıralı diyagramlar okuma hakkında daha fazla bilgi için bkz. [UML sıralı diyagramlar: başvuru](../modeling/uml-sequence-diagrams-reference.md). UML sıralı diyagramlar çizin hakkında daha fazla bilgi için bkz. [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Öğelerin özellikleri  
  
|Özellik|Varsayılan|Öğe|Açıklama|  
|--------------|-------------|-------------|-----------------|  
|**Ad**|Varsayılan bir ad|Tümü|Öğeyi tanımlar.|  
|**Tam adı**|Paket:: adı|Tümü|Öğeyi benzersiz şekilde tanımlar. İle içerdiği paket tam adı öneki.|  
|**İş öğeleri**|ilişkili 0|Tümü|Bu öğeyle ilişkili çalışma öğelerinin sayısı. İş öğelerini ilişkilendirmek için bkz: [bağlantı model öğelerini ve iş öğeleri](../modeling/link-model-elements-and-work-items.md).|  
|**Açıklama**|(boş)|Tümü|Öğeyi buraya hakkında genel bir not alabilirsiniz.|  
|**Renk**|(öğe türü için varsayılan)|İleti yaşam çizgisi|Şeklin rengi. Bu şeklin bir özelliği, öğe yerine gösterir.|  
|**Türü**|(boş)|Yaşam çizgisi|Yaşam çizgisi temsil eden örneği türü.<br /><br /> Yaşam çizgisi üst bilgisinde görüntülenen bir başvuru simge varsa, bu sınıf veya arabirim ayrı olarak UML Model Gezgini'nde var. sonra bir sınıf diyagramı üzerinde görüntülenebilir.|  
|**Aktör**|False|Yaşam çizgisi|Yaşam çizgisi, diyagram hakkında bileşeni için dış bir kullanıcı, cihaz veya yazılım bileşeni temsil edip etmediğini belirtir.|  
|**tür**|**Tam** -göndereni ve alıcısı içeren bir iletisi.<br /><br /> **Bulunan** -iletiye belirtilmeyen bir göndericisi vardır.<br /><br /> **Kayıp** -belirtilmeyen bir alıcı olan bir iletisi.|İleti|Bir iletinin biteceği çizgisine ekli gösterir.<br /><br /> Bu özellik değiştirilemez. İleti oluştururken ayarlanır.|  
|**Sıralama**|**AsynchCall** -zaman uyumsuz ileti.<br /><br /> **SynchCall** -zaman uyumlu bir ileti.<br /><br /> **Yanıt** -zaman uyumlu bir ileti dönüş parçası.<br /><br /> **CreateMessage nesne** -oluşturma iletisi.|İleti|İleti türü. Bu özellik değiştirilemez. İleti oluşturmak için kullandığınız araç tarafından belirlenir.|  
|**İşlemi**|(boş)|İleti|İleti alma yaşam çizgisine tarafından çağırılan yöntem.<br /><br /> Yalnızca alma yaşam çizgisine bir arabirim veya sınıfa bağlı olduğunda görünür.|  
|**İfade eder**|Sıralı diyagram|Etkileşim kullanımı|Sıralı diyagram, bu etkileşim kullanımı tarafından çağrılır.|  
|**Etkileşim işleci**|Kullandığınız ayarlanır **Surround With** komutu|Birleştirilmiş parça|Bu parça veya parçalar topluluğu tarafından temsil edilen işleci.|  
|**koruma**|(boş)|Birleştirilmiş parça etkileşim işleneni|Koruma true olduğu sürece parça dizisinde gerçekleşmez.<br /><br /> Herhangi bir birleştirilmiş parça ilk parçasını seçmek için parça başlığının altına tıklayın.|  
|**Min, maks**|(sınırsız)|Birleştirilmiş parça döngü|Döngü yürütüldükten kez minimum ve maksimum sayısı.|  
|**İletiler**|(boş)|Göz önünde bulundurun ve<br /><br /> Birleştirilmiş parçaları yoksay|Dikkate alınan veya bu parçada göz ardı iletiler.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML sıralı diyagramlar: başvuru](../modeling/uml-sequence-diagrams-reference.md)   
 [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Denetim akışını UML sıralı diyagramlarında parçalarla açıklama](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)



