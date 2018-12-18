---
title: LINQ to XML dinamik özellikleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 59eece0ffae18b72504c258fd3134c7dc8e952d2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894436"
---
# <a name="linq-to-xml-dynamic-properties"></a>LINQ to XML dinamik özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde, XML dinamik özellikleri LINQ hakkında başvuru bilgileri sağlar. Özellikle, bu özellikleri tarafından kullanıma sunulan <xref:System.Xml.Linq.XAttribute> ve <xref:System.Xml.Linq.XElement> bulunan sınıfları, <xref:System.Xml.Linq> ad alanı.  
  
 Konu başlığı altında açıklandığı gibi [genel bakış, WPF veri bağlama LINQ to XML ile](../designers/wpf-data-binding-with-linq-to-xml-overview.md), dinamik özelliklerin her birini bir standart genel özelliğin veya aynı sınıftaki yöntemi eşdeğerdir. Bu standart üyeleri birçok amaç için kullanılması gereken; Dinamik özellikler, LINQ to XML veri bağlama senaryoları için özel olarak sağlanır. Bu sınıfların standart üyeleri hakkında daha fazla bilgi için bkz. <xref:System.Xml.Linq.XAttribute> ve <xref:System.Xml.Linq.XElement> başvuru konuları.  
  
 Çözümlenen değerlerine göre dinamik özellikler bu bölümün iki kategoriye ayrılır:  
  
- Basit olanlar gibi `Value` özelliklerinde <xref:System.Xml.Linq.XAttribute> ve <xref:System.Xml.Linq.XElement> çözümlenmesi için tek bir değer sınıfları.  
  
- Değerleri gibi dizine [öğeleri](../designers/elements-xelement-dynamic-property.md) ve [alt öğeleri](../designers/descendants-xelement-dynamic-property.md) özelliklerini <xref:System.Xml.Linq.XElement>, bir dizin oluşturucu türüne çözün. Dizin oluşturucu türleri istediğiniz değeri veya koleksiyona çözülmesi için bir genişletilmiş adı parametresi geçirilmelidir.  
  
  Dizinli bir değer türü döndüren Dinamik Özellikler <xref:System.Collections.Generic.IEnumerable%601> deffered yürütme kullanın. Ertelenmiş yürütme hakkında daha fazla bilgi için bkz: [(C#) LINQ sorgularına giriş](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[XAttribute Sınıfı Dinamik Özellikleri](../designers/xattribute-class-dynamic-properties.md)|Tarafından kullanıma sunulan dinamik özellikleri hakkında ayrıntılı bilgi sağlayan <xref:System.Xml.Linq.XAttribute> sınıfı.|  
|[XElement Sınıfı Dinamik Özellikleri](../designers/xelement-class-dynamic-properties.md)|Tarafından kullanıma sunulan dinamik özellikleri hakkında ayrıntılı bilgi sağlayan <xref:System.Xml.Linq.XElement> sınıfı.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Xml.Linq>  
  
 <xref:System.Xml.Linq.XElement?displayProperty=fullName>  
  
 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to XML ile WPF verilerini bağlama](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [LINQ to XML genel bakış ile WPF verilerini bağlama](../designers/wpf-data-binding-with-linq-to-xml-overview.md)   
 [LINQ sorguları (C#) giriş](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)



