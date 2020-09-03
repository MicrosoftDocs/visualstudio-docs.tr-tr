---
title: Özellik &lt; özelliği adı &gt; silinemiyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aca36919cb4c82d6ca76e0f3eecbbacd48cde768
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667248"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>Özellik &lt; özelliği adı &gt; silinemiyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

\<property name>Ve arasında devralmanın ayrıştırıcı özelliği olarak ayarlandığı için özellik silinemiyor \<class name>\<class name>

 Seçilen özellik, hata iletisinde belirtilen sınıflar arasındaki devralma için **ayrıştırıcı özelliği** olarak ayarlanır. Veri sınıfları arasında devralma yapılandırmasına katılımları halinde Özellikler silinemez.

 İstenen özelliğin başarıyla silinmesini sağlamak için, **ayrıştırıcı özelliğini** veri sınıfının farklı bir özelliğine ayarlayın.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. O/R tasarımcısında, hata iletisinde belirtilen veri sınıflarını bağlayan devralma satırını seçin.

2. **Ayrıştırıcı** özelliğini farklı bir özelliğe ayarlayın.

3. Özelliği silmeyi yeniden deneyin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: o/r Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) [veri sınıfı devralmayı (o/r Designer)](../data-tools/data-class-inheritance-o-r-designer.md) kullanarak devralmayı yapılandırma [Izlenecek yol: tek tablo devralma (o/r Tasarımcısı) kullanarak LINQ to SQL sınıfları oluşturma](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
