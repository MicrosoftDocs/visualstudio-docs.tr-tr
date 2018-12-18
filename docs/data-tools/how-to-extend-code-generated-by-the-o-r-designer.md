---
title: 'Nasıl yapılır: O-R tasarımcısı tarafından oluşturulan kod genişletme'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9da4dca31043104c58122c2eed7aa55ae44ef07e
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089795"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Nasıl yapılır: O/R tasarımcısı tarafından oluşturulan kod genişletme
Tarafından oluşturulan kodu **O/R Tasarımcısı** sınıflar ve diğer nesnelere Tasarımcı yüzey üzerinde değişiklik yapıldığında yeniden oluşturur. Tasarımcı kodu yeniden oluşturur, bu kod yeniden oluşturma işlemi nedeniyle, oluşturulan kod eklediğiniz herhangi bir kod genellikle üzerine yazılır. **O/R Tasarımcısı** yazılmaz kodu parçalı sınıf dosyaları Ekle oluşturma yeteneği sağlar. Bir örneği tarafından oluşturulan kodu kendi kodunuzu ekleme **O/R Tasarımcısı** veri doğrulama LINQ-SQL (varlık) sınıfları için ekleme. Daha fazla bilgi için bkz: [nasıl yapılır: sınıflar için doğrulama ekleme](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>Bir varlık sınıfı için kod ekleme

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Bir parçalı sınıf oluşturun ve kod bir varlık sınıfı eklemek için

1.  Açın veya yeni bir LINQ to SQL sınıfları dosyası oluşturun (**.dbml** dosyası) içinde **O/R Tasarımcısı**. (Çift **.dbml** dosyasını **Çözüm Gezgini** veya **Database Explorer**.)

2.  İçinde **O/R Tasarımcısı**, doğrulama ekleyin ve ardından istediğiniz sınıfı sağ **görünümü kodu**.

     Seçilen varlık sınıfı için bir parçalı sınıf ile Kod Düzenleyicisi açılır.

3.  Varlık sınıfı için kısmi sınıf bildirimindeki kodunuzu ekleyin.

## <a name="add-code-to-a-datacontext"></a>DataContext için kod ekleme

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Bir parçalı sınıf oluşturun ve bir DataContext kodu eklemek için

1.  Açın veya yeni bir LINQ to SQL sınıfları dosyası oluşturun (**.dbml** dosyası) içinde **O/R Tasarımcısı**. (Çift **.dbml** dosyasını **Çözüm Gezgini** veya **Database Explorer**.)

2.  İçinde **O/R Tasarımcısı**, Tasarımcı üzerinde boş bir alana sağ tıklayın ve ardından **görünümü kodu**.

     Kod Düzenleyicisi DataContext için bir parçalı sınıf ile açılır.

3.  Kodunuzu DataContext parçalı sınıf bildirimi ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ-SQL Visual Studio Araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [İzlenecek yol: LINQ (O R Tasarımcısı) SQL sınıfları için oluşturma](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)