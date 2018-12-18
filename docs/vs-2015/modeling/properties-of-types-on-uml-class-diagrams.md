---
title: Özellik türleri UML sınıf diyagramları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 6e1ef2d0-d67a-401a-bd64-d5e034decd2c
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e8baad41658cc6144f08d0b6b4d415aa4ff6e499
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750107"
---
# <a name="properties-of-types-on-uml-class-diagrams"></a>UML sınıf diyagramlarındaki türlerin özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML sınıf diyagramında bir *türü* bir sınıf, arabirim veya numaralandırma.  
  
> [!NOTE]
>  Bu konu UML sınıf diyagramlarındaki türlerin özellikleri hakkındadır. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)  
  
-   [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)  
  
-   [UML sınıf diyagramlarındaki özniteliklerin özellikleri](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
-   [UML sınıf diyagramlarındaki işlemlerin özellikleri](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
-   [UML sınıf diyagramlarındaki ilişkilendirmelerin özellikleri](../modeling/properties-of-associations-on-uml-class-diagrams.md)  
  
## <a name="properties"></a>Özellikler  
 Bu sınıf, arabirim veya numaralandırma özellikleridir.  
  
 Bir tür özelliklerini görmek için diyagram veya türe sağ **UML Model Gezgini**ve ardından **özellikleri**. Özellikleri görünür **özellikleri** penceresi.  
  
|**Özelliği**|**Default**|Görünür|Açıklama|  
|------------------|-----------------|----------------|-----------------|  
|**Ad**|Varsayılan bir ad|Tüm öğeleri|Öğeyi tanımlar.|  
|**Tam adı**|İçeren paketi:: Tür adı|Tüm öğeleri|Öğeyi benzersiz şekilde tanımlar. İle içerdiği paket tam adı öneki.|  
|**Renk**|Türünü için varsayılan|Tüm öğeleri|Bu şeklin rengi. Diğer özelliklerin aksine, bu temel alınan model öğesinin bir özellik değil. Aynı türde farklı görünümleri farklı renkler olabilir.|  
|**Özet**|False|örneği|TRUE ise, sınıf oluşturulamaz ve bir temel sınıf olarak kullanıma yöneliktir.|  
|**Yaprak**|False|Sınıf, arabirim|TRUE ise, türü türetilmiş türleri için tasarlanmamıştır.|  
|**Etkin**|False|örneği|TRUE ise, her türden iş parçacığı denetimi ile ilişkilidir.|  
|**Görünürlük**|Ortak|Sınıf, arayüz, sabit listesi|-Public - Global olarak görünür.<br />-Özel - bu tür sahip bir paket içinde görülebilir.<br />-Package - paket içinde görünür.|  
|**İş öğeleri**|ilişkili 0|Tüm öğeleri|Bu öğeyle ilişkili çalışma öğelerinin sayısı. İş öğelerini ilişkilendirmek için bkz: [bağlantı model öğelerini ve iş öğeleri](../modeling/link-model-elements-and-work-items.md).|  
|**Açıklama**|(boş)|Tüm öğeleri|Öğeyi buraya hakkında genel bir not alabilirsiniz.|  
|**Şablon Bağlama**|(hiçbiri)|Sınıf, arayüz, sabit listesi|Aksi halde boş, bu tür parametre değerleri için bu şablon sınıfının bağlama tarafından tanımlanır. Şablon parametrelerinin bağlamaları görmek için özelliğini genişletin.|  
|**Şablon Parametreleri**|(hiçbiri)|Sınıf, arayüz, sabit listesi|Aksi halde boş, bunu burada listelenen parametrelere sahip bir şablon sınıfıdır. Parametre Ekle ya da bağımsız parametreleri özelliklerini görüntülemek için tıklayın **[...]** .|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UML sınıf diyagramlarındaki özniteliklerin özellikleri](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [UML sınıf diyagramlarındaki işlemlerin özellikleri](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [UML sınıf diyagramlarındaki İlişkilendirmelerin Özellikleri](../modeling/properties-of-associations-on-uml-class-diagrams.md)   
 [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)



