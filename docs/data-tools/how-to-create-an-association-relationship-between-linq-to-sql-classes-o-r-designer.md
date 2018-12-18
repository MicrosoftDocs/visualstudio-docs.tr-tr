---
title: LINQ-SQL sınıfları O/R Tasarımcısı kullanarak arasında bir ilişki oluşturma
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d247603e14f431e44aa7c1589ba2ecd7463fac02
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089535"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Nasıl yapılır: LINQ-SQL sınıfları (O/R Tasarımcısı) arasında bir ilişkilendirme oluşturun
Varlık sınıflar arasındaki ilişkileri [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] veritabanındaki tablolar arasında ilişkiler benzer. Kullanarak sınıflar arasındaki ilişkileri oluşturabilirsiniz **ilişkilendirme Düzenleyicisi** iletişim kutusu.

Kullandığınızda, bir üst ve alt sınıf seçmelisiniz **ilişkilendirme Düzenleyicisi** iletişim kutusu bir ilişki oluşturun. Birincil anahtarı içeren varlık sınıfı üst sınıftır; yabancı anahtar içeren varlık sınıfı alt sınıfıdır. Örneğin, sınıflar eşlenen oluşturulmuşsa `Northwind Customers` ve `Orders` tabloları, `Customer` sınıfı, üst sınıf olacaktır ve `Order` sınıf alt sınıfı olması.

> [!NOTE]
>  Tablodan sürüklediğinizde **Sunucu Gezgini** veya **Database Explorer** üzerine **Nesne İlişkisel Tasarımcısı** (**O/R Tasarımcısı**), ilişkileri, veritabanında varolan yabancı anahtar ilişkileri temel alarak otomatik olarak oluşturulur.

## <a name="association-properties"></a>İlişki özellikleri
Association'ında seçtiğinizde bir ilişkilendirme oluşturduktan sonra **O/R Tasarımcısı**, bazı yapılandırılabilir özellik **özellikleri** penceresi. (Satırın ilgili sınıflar arasındaki ilişkidir.) Aşağıdaki tabloda bir ilişkilendirmenin özellikleri için açıklamalar sağlanır.

|Özellik|Açıklama|
|--------------|-----------------|
|**Önem düzeyi**|İlişki bire çok veya birebir olup olmadığını denetler.|
|**Alt özelliği**|Bir koleksiyon veya başvuru ilişki yabancı anahtar taraftaki alt kayıtlarına olan üst bir özellik oluşturulup oluşturulmayacağını belirtir. Arasındaki ilişki, örneğin, `Customer` ve `Order`, **alt özelliği** ayarlanır **True**, adında bir özellik `Orders` üst sınıf üzerinde oluşturulur.|
|**Üst özelliği**|İlişkili üst sınıfın başvuran alt sınıf özelliği. Örneğin, arasında ilişki içinde `Customer` ve `Order`, adlı bir özellik `Customer` sipariş üzerinde oluşturulan için ilişkili müşteri başvuran `Order` sınıfı.|
|**Katılımcı özellikleri**|İlişki özellikleri görüntüler ve sağlayan bir **üç nokta** yeniden açar (...) düğmesini **ilişkilendirme Düzenleyicisi** iletişim kutusu.|
|**Benzersiz**|Yabancı hedef sütunlar benzersizlik kısıtlamasını sahip olup olmadığını belirtir.|

## <a name="to-create-an-association-between-entity-classes"></a>Sınıflar arasında bir ilişki oluşturmak için

1.  Birleşimdeki üst sınıfın temsil ettiği varlık sınıfı sağ tıklayın, fareyle **Ekle**ve ardından **ilişkilendirme**.

2.  Doğrulayın doğru **üst sınıf** seçildiyse **ilişkilendirme Düzenleyicisi** iletişim kutusu.

3.  Seçin **alt sınıf** açılan kutuya.

4.  Seçin **ilişki özellikleri** sınıfları ilişkilidir. Genellikle, bu veritabanında tanımlı yabancı anahtar ilişkisi eşler. Örneğin, `Customers` ve `Orders` association **ilişki özellikleri** olan `CustomerID` her sınıf için.

5.  Tıklatın **Tamam** bir ilişki oluşturmak için.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ-SQL Visual Studio Araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [İzlenecek yol: LINQ SQL sınıfları için oluşturma](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext yöntemleri (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md)
- [Nasıl yapılır: birincil anahtarlar temsil eder](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)