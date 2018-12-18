---
title: Bir ilişkilendirme - iki kez listelenen özellik oluşturulamıyor
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d508cc407087e481ff77e29956db7511bba81165
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916835"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Bir ilişki oluşturulamıyor &lt;ilişkilendirme adı&gt; -özelliği listelenen iki kez

Bir ilişki oluşturulamıyor \<ilişkilendirme adı >. Aynı özelliği birden çok kez listelenir: \<özellik adı >.

İlişkilendirmeleri tanımlanan seçili tarafından **ilişki özellikleri** içinde **ilişkilendirme Düzenleyicisi** iletişim kutusu. Özellikler ilişkisindeki her sınıf için yalnızca bir kez listelenebilir.

İleti özelliği üst veya alt sınıfın içinde birden fazla kez görünür **ilişki özellikleri**.

## <a name="to-resolve-this-condition"></a>Bu durumu gidermek için

- İleti inceleyin ve iletide belirtilen özellik unutmayın.

- Tıklatın **Tamam** ileti kutusu kapatılamadı.

- İnceleme **ilişki özellikleri** ve yinelenen girişleri kaldırın.

- **Tamam**'ı tıklatın.

## <a name="see-also"></a>Ayrıca bkz.

- [O/R Tasarımcısı iletileri](../data-tools/o-r-designer-messages.md)
- [LINQ-SQL Visual Studio Araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Nasıl yapılır: LINQ-SQL sınıfları (O/R Tasarımcısı) arasında bir ilişkilendirme oluşturun](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)