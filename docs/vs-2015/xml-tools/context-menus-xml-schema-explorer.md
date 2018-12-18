---
title: Bağlam menüleri (XML Şeması Gezgini) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42ab17ca-b8c1-40d7-beda-d033f66fe874
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 854ea473f2f606b28052b093978253372b4fec59
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294629"
---
# <a name="context-menus-xml-schema-explorer"></a>Bağlam menüleri (XML Şeması Gezgini)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Aşağıdaki bağlam menüsü öğelerine, şema özel aramalar ve diğer işlemleri gerçekleştirmek için kullanılır.  
  
## <a name="node-type-schema-set"></a>Düğüm türü: Şema kümesi  
 Aşağıdaki tabloda, bir şema düğüm kümesi için kullanılabilen seçenekler açıklanmaktadır.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**En olası kök öğeleri göster**|Bulur ve kendisi dışında genel öğelerinden başvurulmayan tüm genel öğeler vurgulanır.|  
|**Genel türleri Göster**|Bulur ve şema kümesindeki tüm genel türleri vurgular.|  
|**Genel öğeler Göster**|Bulur ve şema kümesindeki tüm genel öğeler vurgulanır.|  
|**Özellik Penceresi**|Açılır **özellikleri** penceresi (Bunu zaten açık değilse). Bu pencere, düğüm hakkında bilgi görüntüler.|  
  
## <a name="node-type-namespace"></a>Düğüm türü: Namespace  
 Aşağıdaki tabloda, bir ad alanı düğümü için kullanılabilir seçenekleri açıklar.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**Tüm gelen başvuruları göster**|Bulur ve seçili ad alanı içe dosyaları vurgular.|  
|**Tüm giden başvuruları göster**|Seçili ad alanında her dosya için bulur ve şunları vurgular:<br /><br /> -Başvurulan tüm ad alanlarını içeri aktarma deyimleri olmadan bir `schemaLocation` özniteliği.<br />-Tüm dosyaları belirtilen seçili bir başka isim uzaylarında `schemaLocation` öznitelik alma ve ifadeleri içerir.|  
|**Genel türleri Göster**|Bulur ve seçili ad alanı içindeki tüm genel öğeler vurgulanır.|  
|**Genel öğeler Göster**|Bulur ve seçilen ad alanındaki tüm genel öğeler vurgulanır.|  
|**Özellik Penceresi**|Açılır **özellikleri** penceresi (Bunu zaten açık değilse). Bu pencere, düğüm hakkında bilgi görüntüler.|  
  
## <a name="node-type-file"></a>Düğüm türü: dosya  
 Aşağıdaki tabloda, bir dosya düğümü için kullanılabilir seçenekleri açıklar.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**Tüm gelen başvuruları göster**|Bulur ve seçili dosyayı belirtin. tüm dosyaları vurgular `schemaLocation` kendi dahil etme ve içeri aktarma deyimlerini öznitelikleri.|  
|**Tüm giden başvuruları göster**|Bulur ve aşağıdaki hususları vurgular:<br /><br /> -Tüm ad alanı özniteliklerinde belirtilen tüm ad alanlarını alma olmadığı deyimleri `schemaLocation` özniteliği.<br />-Tüm dosyaları belirtilen `schemaLocation` sınıflarının tüm öznitelikleri almak ve deyimleri ekleyin.|  
|**Genel türleri Göster**|Bulur ve bu dosyadaki tüm genel türlere vurgular.|  
|**Genel öğeler Göster**|Bulur ve bu dosyadaki tüm genel öğeler vurgulanır.|  
|**Kodu Görüntüle**|XML Düzenleyicisi'nde seçili düğümü içeren dosyayı açar. XML şema Gezgini içinde seçili öğenin XML Düzenleyicisi'nde da seçilir.|  
|**Özellik Penceresi**|Açılır **özellikleri** penceresi (Bunu zaten açık değilse). Bu pencere, düğüm hakkında bilgi görüntüler.|  
  
## <a name="all-global-node-types"></a>Tüm genel düğüm türleri  
 Aşağıdaki tabloda, genel tüm düğümler için kullanılabilir seçenekleri açıklar.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**Graf görünümünde göster**|Graf görünümünü açar. Seçili düğüm çalışma alanında değilse, çalışma alanına ekler ve düğümü seçer.|  
|**İçerik modeli görünümünde göster**|İçerik modeli görünümü açılır. Seçili düğüm çalışma alanında değilse, çalışma alanına ekler ve düğümü seçer.|  
|**Kodu Görüntüle**|XML Düzenleyicisi'nde seçili düğümü içeren dosyayı açar. XML şema Gezgini içinde seçili öğenin XML Düzenleyicisi'nde da seçilir.|  
|**Özellik Penceresi**|Açılır **özellikleri** penceresi (Bunu zaten açık değilse). Bu pencere, düğüm hakkında bilgi görüntüler.|  
  
## <a name="node-type-element"></a>Düğüm türü: öğesi  
 Yukarıda açıklanan genel düğüm seçeneklerinin yanı sıra öğe düğümlerinin için bağlam menüsünü aşağıdaki seçeneklere sahiptir:  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**Tür tanımına Git**|Seçili öğenin tür tanımına gider. Bu öğe için kullanılan tür genel bir tür olduğunda geçerlidir.|  
|**Özgün öğeye git**|Öğesinin gerçek bir tanımı öğesi başvuruları için gider.|  
|**Tüm başvuruları göster**|Genel öğeler için bulur ve tüm başvuruları vurgular (olan öğeler `ref="selectedElement"`) seçili öğeye.|  
|**Değiştirme grubu üyelerini Göster**|Değiştirme grubu yöneticileri için bulur ve seçilen öğenin bir üyesi olan değiştirme grubunun üyesi olan tüm öğeleri vurgular. Bu, doğrudan ve dolaylı katılımcıları gösterir.|  
|**Show değiştirme grubu Heads**|Değiştirme grubu üyeleri, bulur ve aşağıdaki gibi seçilen öğe için doğrudan ve dolaylı heads vurgular genel öğeler için:<br /><br /> Seçilen öğede belirtilen değiştirme grubu baş.<br />-Bir değiştirme grubu kendi baş öğede belirtilen head.|  
|**Örnek XML oluşturma**|Yalnızca genel öğeler için kullanılabilir. Genel öğe için bir örnek XML dosyası oluşturur.|  
  
## <a name="node-type-global-types"></a>Düğüm türü: Genel türler  
 Yukarıda açıklanan genel düğüm seçeneklerinin yanı sıra, genel tür düğümleri için bağlam menüsünü aşağıdaki seçeneklere sahiptir:  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**Temel tür Göster**|Seçilen tür genel bir türden türetilirse seçili türün temel türü için gider.|  
|**Tüm başvuruları göster**|Bulur ve tüm başvuruları seçilen türe vurgular. Bu öğeler ve öznitelikler seçili türü ve seçilen türden türetilmiş türleri içerir.|  
|**Tüm türetilmiş türleri Göster**|Bulur ve doğrudan ve dolaylı olarak seçilen türünden türetilen tüm türler vurgular.|  
|**Tüm üst öğeleri göster**|Tüm (Temel) üst türleri gösterir.|  
  
## <a name="node-type-attribute"></a>Düğüm türü: özniteliği  
 Yukarıda açıklanan genel düğüm seçeneklerinin yanı sıra, öznitelik düğümleri için bağlam menüsünü aşağıdaki seçeneklere sahiptir:  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**Tür tanımına Git**|Öznitelik için kullanılan tür genel bir tür olduğunda, seçili öznitelik türü tanımına gider.|  
|**Özgün özniteliğe Git**|Öznitelik başvuruları için öznitelik gerçek tanımına gider.|  
|**Tüm başvuruları göster**|Genel öznitelikler için bulur ve tüm başvuruları vurgular (sahip diğer öznitelikleri `ref="selectedAttribute"`) seçilen öznitelik.|  
  
## <a name="node-type-attribute-group"></a>Düğüm türü: Öznitelik grubu  
 Yukarıda açıklanan genel düğüm seçeneklerinin yanı sıra, öznitelik düğümleri gruplandırma için bağlam menüsünü aşağıdaki seçeneklere sahiptir:  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**Tanıma Git**|Başvurular için öznitelik gerçek tanımına gider.|  
|**Tüm üyeleri Göster**|Bulur ve öznitelik grubunun tüm üyeleri vurgular.|  
|**Tüm başvuruları göster**|Bulur ve tüm başvuruları vurgular (öznitelik grupları `ref="selectedAttributeGroup"`) seçili öznitelik grubu için.|  
  
## <a name="node-type-named-group"></a>Düğüm türü: Adlandırılmış Grup  
 Yukarıda açıklanan genel düğüm seçeneklerinin yanı sıra, adlandırılmış Grup düğümleri için bağlam menüsünü aşağıdaki seçeneklere sahiptir:  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**Tanıma Git**|Başvurular için öznitelik gerçek tanımına gider.|  
|**Tüm üyeleri Göster**|Bulur ve adlandırılmış grubun tüm üyelerinin vurgular.|  
|**Tüm başvuruları göster**|Bulur ve tüm başvuruları vurgular (grupları `ref="selectedGroup"`) seçilen gruba.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML şema Gezgini](../xml-tools/xml-schema-explorer.md)   
 [Şema Kümesini Arama](../xml-tools/searching-the-schema-set.md)



