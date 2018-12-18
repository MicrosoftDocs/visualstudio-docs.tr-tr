---
title: 'Nasıl yapılır: bir DataContext yöntemi (O R Tasarımcısı) dönüş türünü değiştirme'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5c67d6dea4c64e858acdab25ecc4a6cede6bf262
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089363"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Nasıl yapılır: bir DataContext yöntemi (O/R Tasarımcısı) dönüş türünü değiştirme
Dönüş türü bir <xref:System.Data.Linq.DataContext> yöntemi (bir saklı yordam veya işlevi temel alınarak oluşturulan) farklı olduğu saklı yordamı veya işlevi bağlı olarak **O/R Tasarımcısı**. Bir öğenin varolan bir varlık sınıfı doğrudan üzerine bırakın, bir <xref:System.Data.Linq.DataContext> varlık sınıfı dönüş türüne sahip yöntemi (saklı yordam veya işlev tarafından döndürülen veri şeması ve varlık sınıfı şeklini eşleşirse) oluşturulur. Boş bir alanı bir öğe bırakma durumunda **O/R Tasarımcısı**, <xref:System.Data.Linq.DataContext> otomatik olarak oluşturulan bir tür döndüren yöntem oluşturulur. Dönüş türünü değiştirebilirsiniz bir <xref:System.Data.Linq.DataContext> yöntemleri bölmesine ekledikten sonra yöntemi. İnceleme veya dönüş türünü değiştirmek için bir <xref:System.Data.Linq.DataContext> yöntemi seçin ve **dönüş türü** özelliğinde **özellikleri** penceresi.

> [!NOTE]
>  Geri alınamaz <xref:System.Data.Linq.DataContext> kullanarak otomatik olarak oluşturulan türünü döndürmek için bir varlık sınıfı olarak ayarlanan bir dönüş türüne sahip yöntemleri **özellikleri** penceresi. Geri almak için bir <xref:System.Data.Linq.DataContext> bir otomatik olarak oluşturulan türü döndürülecek yöntemi özgün veritabanı nesnesi üzerine sürükleyin **O/R Tasarımcısı** yeniden.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Bir varlık sınıfı için otomatik olarak oluşturulan türünden DataContext yöntemin dönüş türünü değiştirmek için

1.  Seçin <xref:System.Data.Linq.DataContext> yöntemleri bölmesinde yöntemi.

2.  Seçin **dönüş türü** içinde **özellikleri** penceresini açın ve ardından kullanılabilir varlık sınıfı içinde **dönüş türü** listesi. İstenen varlık sınıfı listede değilse, ekleyin veya içinde oluşturma **O/R Tasarımcısı** listesine eklemek için.

3.  Kaydet *.dbml* dosya.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Otomatik olarak oluşturulan türü geri varlık sınıfından DataContext yöntemin dönüş türünü değiştirmek için

1.  Seçin <xref:System.Data.Linq.DataContext> yönteminde **yöntemleri** bölmesi ve silin.

2.  Veritabanı nesnesinden sürükleyin **Sunucu Gezgini** veya **Database Explorer** boş bir alanı üzerine **O/R Tasarımcısı**.

3.  Kaydet *.dbml* dosya.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ-SQL Visual Studio Araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext yöntemleri (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md)
- [Nasıl yapılır: saklı yordamları ve işlevleri (O/R Tasarımcısı) eşlenen DataContext yöntemleri oluşturma](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)