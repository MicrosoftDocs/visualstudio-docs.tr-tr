---
title: 'Nasıl yapılır: LINQ to SQL sınıfları tablolar ve görünümler (O R Designer) ile eşlenmiş oluşturma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b66559061f0d66699a7505c71541b237814812c4
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305604"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Nasıl yapılır: LINQ to SQL sınıfları tablolar ve görünümler (O/R Tasarımcısı) ile eşlenmiş oluşturma

[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] veritabanını tablolar ve görünümler ile eşlenen sınıfları çağrılır *varlık sınıfları*. Bir varlık sınıfı özelliklerini bireysel kaydı oluşturan tek tek sütunlara yapılan oluştururken varlık sınıfı bir kayda eşler. Tabloları veya görünümleri sürükleyerek veritabanı tabloları veya görünümleri temel alan bir varlık sınıfları oluşturma **Sunucu Gezgini** veya **veritabanı Gezgini** üzerine [LINQ to SQL araçları Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md). **O/R Tasarımcısı** sınıflar oluşturur ve belirli uygular [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] etkinleştirmek için öznitelikleri [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] işlevleri (veri iletişimi ve özelliklerini düzenleme <xref:System.Data.Linq.DataContext>). İlgili ayrıntılı bilgi için [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] sınıfları için bkz [LINQ to SQL nesne modeli](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).

> [!NOTE]
> **O/R Tasarımcısı** yalnızca 1:1 eşleme ilişkileri desteklediğinden, bir Basit Nesne İlişkisel eşleyicisidir. Diğer bir deyişle, bir varlık sınıfı yalnızca 1:1 eşleme ilişkisi olan bir veritabanı tablosu veya görünümü olabilir. Bir varlık sınıfı birden çok tablolara eşleme gibi karmaşık eşleme desteklenmez. Bununla birlikte, birden çok ilişkili tabloyla birleştiren bir görünüm için bir varlık sınıfı eşleyebilirsiniz.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Veritabanı tabloları veya görünümleri için eşlenen SQL sınıflarına LINQ oluşturma

Sürükleme, tabloları veya gelen görünümleri **Sunucu Gezgini** veya **veritabanı Gezgini** üzerine **O/R Tasarımcısı** varlık sınıflarının yanı sıra oluşturur <xref:System.Data.Linq.DataContext> yöntemleri, güncelleştirmeleri gerçekleştirmek için kullanılır.

Varsayılan olarak, [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] çalışma zamanı değişiklikleri veritabanına geri güncelleştirilebilir varlık sınıfından kaydetmek için mantıksal oluşturur. Bu mantık, şemanın tablo (sütun tanımları ve birincil anahtar bilgileri) temel alır. Bu davranışı istemiyorsanız, ekleme, güncelleştirme ve silme varsayılan kullanmak yerine gerçekleştirmek için saklı yordamları kullanmak için bir varlık sınıfı yapılandırabileceğiniz [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] çalışma zamanı davranışı. Daha fazla bilgi için [nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atama](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Veritabanı tabloları veya görünümleri için eşlenen SQL sınıflarına LINQ oluşturmak için

1.  İçinde **sunucu** veya **veritabanı Gezgini**, genişletme **tabloları** veya **görünümleri** veritabanı tablosunu bulun ve kullanmak istediğiniz görüntülemek, uygulama.

2.  Tabloyu sürükleyin veya üzerine görüntülemek **O/R Tasarımcısı**.

     Bir varlık sınıfı oluşturulur ve tasarım yüzeyinde görünür. Varlık sınıfı için Seçili tabloyu veya görünümü sütunları eşlemek özelliğe sahiptir.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Formdaki verileri görüntülemek ve bir nesne veri kaynağı oluştur

Kullanarak varlık sınıflarını oluşturduktan sonra **O/R Tasarımcısı**, bir nesne veri kaynağı oluşturma ve doldurma [veri kaynakları penceresi](add-new-data-sources.md#data-sources-window) varlık sınıfları ile.

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>LINQ to SQL varlık sınıflarını temel bir nesne veri kaynağı oluşturmak için

1.  Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle** projenizi yapılandırmak için.

2.  Açmak için **veri kaynakları** penceresi, **veri** menüsünde tıklatın **veri kaynaklarını Göster**.

3.  İçinde **veri kaynakları** penceresinde tıklayın **yeni veri kaynağı Ekle**.

4.  Tıklayın **nesne** üzerinde **bir veri kaynağı türü seçin** sayfasında ve ardından **sonraki**.

5.  Düğümleri genişletin ve bulun ve sonra da, sınıf seçin.

    > [!NOTE]
    > Varsa **müşteri** sınıf kullanılabilir değil, Sihirbazı iptal etmeniz, projeyi derleyin ve sihirbazı yeniden çalıştırın.

6.  Tıklayın **son** veri kaynağı oluşturma ve ekleme **müşteri** varlık sınıfı için **veri kaynakları** penceresi.

7.  Öğeleri sürükleme **veri kaynakları** forma penceresi.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [İzlenecek yol:, (O R Designer) SQL sınıflarına LINQ oluşturma](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [DataContext yöntemi (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md)
- [Nasıl yapılır: Saklı yordamlarla eşlenen DataContext metotları oluşturma (O/R Tasarımcısı)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [LINQ to SQL nesne modeli](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [İzlenecek yol: Varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Nasıl yapılır: LINQ to SQL sınıfları arasında ilişkilendirme (ilişki) oluşturma (O/R Tasarımcısı)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)