---
title: UML öğeleri özelliklerini örneği diyagramları kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties
- vs.teamarch.usecasediagram.shapes.properties
helpviewer_keywords:
- use case diagrams, properties
ms.assetid: 2728fb26-a275-4fce-8a2c-5a78af6bee04
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a81f7630a1a903af2f9c21aee3249ea6fe156af2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762819"
---
# <a name="properties-of-elements-on-uml-use-case-diagrams"></a>UML kullanım durumu diyagramlarındaki öğelerin özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML Kullanım durumu diyagramında, her öğe diyagram üzerindeki özellikleri vardır. Öğenin özelliklerini görmek için diyagram üzerinde veya öğeye sağ tıklayın **UML Model Gezgini** ve ardından **özellikleri**. Özellikleri görünür **özellikleri** penceresi.  
  
> [!NOTE]
>  Bu konu UML Kullanım durumu diyagramlarındaki öğelerin özellikleri hakkındadır. UML etkinlik diyagramları okuma hakkında daha fazla bilgi için bkz. [UML Kullanım durumu diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md). UML etkinlik diyagramları çizmek hakkında daha fazla bilgi için bkz. [UML Kullanım durumu diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Öğelerin özellikleri  
  
|Özellik|Varsayılan|Öğe|Açıklama|  
|--------------|-------------|-------------|-----------------|  
|**Ad**|Varsayılan bir ad|Tümü|Öğeyi tanımlar.|  
|**Tam adı**|Paket:: adı|Tümü|Öğeyi benzersiz şekilde tanımlar. İle içerdiği paket tam adı öneki.|  
|**İş öğeleri**|ilişkili 0|Tümü|Bu öğeyle ilişkili çalışma öğelerinin sayısı. İş öğelerini ilişkilendirmek için bkz: [bağlantı model öğelerini ve iş öğeleri](../modeling/link-model-elements-and-work-items.md).|  
|**Açıklama**|(hiçbiri)|Tümü|Burada bir öğeyle ilgili genel bir not alabilirsiniz.|  
|**Renk**|(varsayılan)|Tümü|Şeklin rengi. Diğer özelliklerin aksine, bu olmadığından, bir özellik öğesinin şeklini görüntüler.|  
|**Görüntü yolu**|(hiçbiri)|Aktör|Görüntünün varsayılan aktör simge yerine kullanılması gereken dosya yolu. Simgesi, Visual Studio projesi içinde bir kaynak dosyası olmalıdır.|  
|**Konuları**|(hiçbiri)|Kullanım örneği|Veya alt kullanım örneği başka bir türü.<br /><br /> Kullanım örneği diyagramındaki bir alt sisteminde yerleştirerek ayarlayabilirsiniz.|  
|**Görünürlük**|Ortak|Örneği, aktör, alt kullanın|**Genel** - Global olarak görünür.<br /><br /> **Paket** - paket içinde görünür.|  
|**IsAbstract**|False|Örneği, aktör, alt kullanın|TRUE ise, türü oluşturulamaz ve diğer tanımları tarafından özelleştirmesi için temel olarak tasarlanmıştır.|  
|**Dolaylı olarak Örneklendirilmiş**|Doğru|Alt sistem|Alt yalnızca bir tasarım yapıt bulunmaktadır. Çalışma zamanında, yalnızca bölümleri mevcuttur.|  
|**Köprü**|(hiçbiri)|Yapıt|Diyagram veya belge yapıt bağlantı sağlayan URL veya dosya yolu.|  
  
 İlişkilendirmelerin özelliklerinin bir listesi için bkz. [UML İlişkilendirmelerin Özellikleri sınıf diyagramları](../modeling/properties-of-associations-on-uml-class-diagrams.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML Kullanım durumu diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md)   
 [UML Kullanım Durumu Diyagramları: Yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)



