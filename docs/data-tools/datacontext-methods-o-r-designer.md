---
title: DataContext yöntemi (O R Tasarımcısı)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 95d84442b4aba74dbc44b7aacc97d0a965162150
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924973"
---
# <a name="datacontext-methods-or-designer"></a>DataContext yöntemi (O/R Tasarımcısı)

<xref:System.Data.Linq.DataContext> yöntemler (bağlamında [LINQ to SQL araçlarını Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md)), yöntemler <xref:System.Data.Linq.DataContext> saklı yordamları ve işlevleri bir veritabanında çalıştırılan bir sınıf.

<xref:System.Data.Linq.DataContext> Sınıfı bir [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] bir conduit arasında bir SQL Server veritabanı olarak davranan bir sınıf ve [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] veritabanına eşlenen varlık sınıfları. <xref:System.Data.Linq.DataContext> Sınıfı bağlantı dizesi bilgilerini ve bir veritabanına bağlanma ve veritabanındaki verileri işlemek için yöntemler içerir. Varsayılan olarak, <xref:System.Data.Linq.DataContext> sınıfı içerir, gibi çağırabileceğiniz birkaç yöntem <xref:System.Data.Linq.DataContext.SubmitChanges%2A> gönderen yöntemi güncelleştirilmiş verileri [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] veritabanına sınıfları. Ayrıca, ek oluşturabilirsiniz <xref:System.Data.Linq.DataContext> saklı yordamları ve işlevleri için eşleme yöntemleri. Diğer bir deyişle, bu özel metotları çağırma saklı yordamı veya işlevi veritabanında için çalıştığı <xref:System.Data.Linq.DataContext> yöntemi eşlenir. İçin yeni yöntemler ekleyebilirsiniz <xref:System.Data.Linq.DataContext> herhangi bir sınıf genişletmek için yöntemleri eklemek gibi sınıf. Hakkında tartışmalar, ancak <xref:System.Data.Linq.DataContext> bağlamında yöntemleri **O/R Tasarımcısı**, bu <xref:System.Data.Linq.DataContext> saklı yordamlar ve ele alınmıştır işlevlere eşleme yöntemleri.

## <a name="methods-pane"></a>Yöntemler bölmesi

<xref:System.Data.Linq.DataContext> saklı yordamları ve işlevleri için eşleme yöntemlerini görüntülenir **yöntemleri** bölmesinde **O/R Tasarımcısı**. **Yöntemleri** bölmesidir tarafında bölmesinde **varlıkları** bölmesinde (ana tasarım yüzeyi). **Yöntemleri** bölmesinde tümünü listeler <xref:System.Data.Linq.DataContext> kullanılarak oluşturulan yöntemler **O/R Tasarımcısı**. Varsayılan olarak, **yöntemleri** bölmesidir boş; Sürükle saklı yordamları veya işlevlerden **Sunucu Gezgini** veya **veritabanı Gezgini** üzerine **O/R Tasarımcısı**  oluşturmak için <xref:System.Data.Linq.DataContext> yöntemleri ve doldurma **yöntemleri** bölmesi. Daha fazla bilgi için [nasıl yapılır: saklı yordamları ve işlevleri (O/R Tasarımcısı) için eşlenen DataContext oluşturma yöntemleri](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Açın ve sağ tıklayarak yöntemler bölmesini kapatmak **O/R Tasarımcısı** tıklayıp **yöntemler Bölmesini Gizle** veya **yöntemler bölmesini göster**, veya klavyekısayolunukullanın **CTRL**+**1**.

## <a name="two-types-of-datacontext-methods"></a>İki tür DataContext yöntemi

DataContext yöntemi saklı yordamları ve işlevleri veritabanında eşleyen bu yöntemlerdir. Oluşturabilir ve DataContext yöntemi eklemek **yöntemleri** bölmesinde **O/R Tasarımcısı**. İki ayrı türü vardır <xref:System.Data.Linq.DataContext> yöntemleri; Bu, bir veya daha fazla sonuç kümesi döndüren ve desteklemeyenler:

- <xref:System.Data.Linq.DataContext> bir veya daha fazla sonuç kümesi döndüren yöntemler:

   Bu tür oluşturma <xref:System.Data.Linq.DataContext> saklı yordamları ve işlevleri veritabanında çalıştırın ve sonuçları döndürmek uygulamanızı yalnızca gerektiğinde yöntemi. Daha fazla bilgi için [nasıl yapılır: saklı yordamları ve işlevleri (O/R Tasarımcısı) için eşlenen DataContext oluşturma yöntemleri](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, ve <xref:System.Data.Linq.IMultipleResults>.

- <xref:System.Data.Linq.DataContext> Sonuç kümesi döndürmüyor yöntemleri: gibi ekler, güncelleştirmeler ve özel varlık sınıfı için siler.

   Bu tür oluşturma <xref:System.Data.Linq.DataContext> uygulamanızın varsayılan kullanmak yerine saklı yordamları çalıştırmak sahip olduğunda yöntemi [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] kaydetme davranışını değiştiren bir varlık sınıfı ve veritabanı arasında veri. Daha fazla bilgi için [nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atama](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>DataContext yöntemlerinin dönüş türleri

Saklı yordamları ve işlevleri sürüklediğinizde **Sunucu Gezgini** veya **veritabanı Gezgini** üzerine **O/R Tasarımcısı**, dönüş türü oluşturulan <xref:System.Data.Linq.DataContext> yöntemi, öğenin nereden bırakın bağlı olarak farklılık gösterir. Öğeleri doğrudan mevcut bir varlık sınıfı üzerine bırakarak oluşturur bir <xref:System.Data.Linq.DataContext> yöntemi varlık sınıfı dönüş türüne sahip; bırakma öğeleri boş bir alanı üzerine **O/R Tasarımcısı** oluşturur (ya da bölmesinde) bir <xref:System.Data.Linq.DataContext> yöntemi otomatik olarak oluşturulan bir tür döndürür. Otomatik olarak oluşturulan saklı yordam veya işlev adı ve saklı yordamı veya işlevi tarafından döndürülen alanlarla eşlemek özellikleri eşleşen ada sahiptir.

> [!NOTE]
> Dönüş türünü değiştirebilirsiniz bir <xref:System.Data.Linq.DataContext> yöntemleri bölmesine ekledikten sonra yöntemi. İnceleme veya dönüş türünü değiştirmek için bir <xref:System.Data.Linq.DataContext> yöntemi seçin ve İnceleme **dönüş türü** özelliğinde **özellikleri** penceresi. Daha fazla bilgi için [nasıl yapılır: bir DataContext yöntemi (O/R Tasarımcısı) dönüş türünü değiştirme](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

Nesneleri veritabanından O/R Tasarımcısı yüzeyine sürükleyin, veritabanındaki nesneleri adına göre otomatik olarak adlandırılır. Aynı nesne birden çok kez sürüklerseniz, bir sayı adlarını ayırır yeni adın sonuna eklenir. Veritabanı nesne adları, boşluk veya Visual Basic veya C# içinde desteklenmeyen karakterler içerdiğinde, boşluk veya geçersiz bir karakter bir alt çizgi ile değiştirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Saklı yordamlar](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Nasıl yapılır: Saklı yordamlarla eşlenen DataContext metotları oluşturma (O/R Tasarımcısı)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [İzlenecek yol: Varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [İzlenecek yol:, (O R Designer) SQL sınıflarına LINQ oluşturma](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)