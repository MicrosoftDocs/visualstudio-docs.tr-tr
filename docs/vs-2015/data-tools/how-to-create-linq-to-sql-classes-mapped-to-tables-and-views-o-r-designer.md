---
title: 'Nasıl yapılır: LINQ to SQL sınıfları tablolar ve görünümler (O R Designer) ile eşlenmiş oluşturun | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 550fc362cf1652df48e029461a4d5fbdc6f04006
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269550"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Nasıl yapılır: LINQ to SQL sınıfları tablolar ve görünümler (O/R Tasarımcısı) ile eşlenmiş oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Veritabanını tablolar ve görünümler ile eşlenen SQL sınıflarına LINQ çağrılır *varlık sınıfları*. Bir varlık sınıfı özelliklerini bireysel kaydı oluşturan tek tek sütunlara yapılan oluştururken varlık sınıfı bir kayda eşler. Tabloları veya görünümleri sürükleyerek veritabanı tabloları veya görünümleri temel alan bir varlık sınıfları oluşturma **Sunucu Gezgini**/**veritabanı Gezgini** üzerine [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Sınıflar oluşturur ve belirli uygular [! Etkinleştirmek için LINQ SQL öznitelikleri [! LINQ to SQL işlevleri (veri iletişimi ve özelliklerini düzenleme <xref:System.Data.Linq.DataContext>). İlgili ayrıntılı bilgi için [! LINQ to SQL sınıfları Bkz [LINQ to SQL nesne modeli](http://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810).

> [!NOTE]
> [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Yalnızca 1:1 eşleme ilişkileri desteklediğinden, bir Basit Nesne İlişkisel eşleyicisidir. Diğer bir deyişle, bir varlık sınıfı yalnızca 1:1 eşleme ilişkisi olan bir veritabanı tablosu veya görünümü olabilir. Bir varlık sınıfı birden çok tablolara eşleme gibi karmaşık eşleme desteklenmez. Bununla birlikte, birden çok ilişkili tabloyla birleştiren bir görünüm için bir varlık sınıfı eşleyebilirsiniz.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Veritabanı tabloları veya görünümleri için eşlenen SQL sınıflarına LINQ oluşturma
 Sürükleme, tabloları veya gelen görünümleri **Sunucu Gezgini**/**veritabanı Gezgini** üzerine [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] varlık sınıflarının yanı sıra oluşturur <xref:System.Data.Linq.DataContext> için kullanılan yöntemleri güncelleştirmeler gerçekleştirme.

 Varsayılan olarak, [! LINQ to SQL çalışma zamanı değişiklikleri veritabanına geri güncelleştirilebilir varlık sınıfından kaydetmek için mantıksal oluşturur. Bu mantık, şemanın tablo (sütun tanımları ve birincil anahtar bilgileri) temel alır. Bu davranışı istemiyorsanız, ekleme, güncelleştirme gerçekleştirmek için saklı yordamları kullanmak için bir varlık sınıfı yapılandırabilirsiniz ve varsayılan kullanmak yerine siler. [! LINQ to SQL çalışma zamanı davranışı. Daha fazla bilgi için [nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atama](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Veritabanı tabloları veya görünümleri için eşlenen SQL sınıflarına LINQ oluşturmak için

1.  İçinde **sunucu**/**veritabanı Gezgini**, genişletme **tabloları** veya **görünümleri** veritabanı tablosunu bulun ve istediğiniz görüntülemek uygulamanızda kullanılacak.

2.  Tabloyu sürükleyin veya üzerine görüntülemek [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Bir varlık sınıfı oluşturulur ve tasarım yüzeyinde görünür. Varlık sınıfı için Seçili tabloyu veya görünümü sütunları eşlemek özelliğe sahiptir.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Formdaki verileri görüntülemek ve bir nesne veri kaynağı oluştur
 Kullanarak varlık sınıflarını oluşturduktan sonra [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], bir nesne veri kaynağı oluşturma ve doldurma [veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) varlık sınıfları ile.

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>LINQ to SQL varlık sınıflarını temel bir nesne veri kaynağı oluşturmak için

1.  Üzerinde **derleme** menüsünde tıklatın **Çözümü Derle** projenizi yapılandırmak için.

2.  Üzerinde **veri** menüsünü tıklatın **veri kaynaklarını Göster**.

3.  İçinde **veri kaynakları** penceresinde tıklayın **yeni veri kaynağı Ekle**.

4.  Tıklayın **nesne** üzerinde **bir veri kaynağı türü seçin** sayfasında ve ardından **sonraki**.

5.  Düğümleri genişletin ve bulun ve sonra da, sınıf seçin.

    > [!NOTE]
    > Varsa **müşteri** sınıf kullanılabilir değil, Sihirbazı iptal etmeniz, projeyi derleyin ve sihirbazı yeniden çalıştırın.

6.  Tıklayın **son** veri kaynağı oluşturma ve ekleme **müşteri** varlık sınıfı için **veri kaynakları** penceresi.

7.  Öğeleri sürükleme **veri kaynakları** forma penceresi.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki LINQ to SQL Araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [İzlenecek yol: LINQ to SQL sınıfları (O R Designer) oluşturma](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
- [DataContext Metotları (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md)
- [Nasıl yapılır: Saklı yordamlarla eşlenen DataContext metotları oluşturma (O/R Tasarımcısı)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [LINQ to SQL Nesne Modeli](http://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)
- [İzlenecek yol: Varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [İzlenecek yol: Varlık sınıflarına doğrulama ekleme](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
- [Nasıl yapılır: LINQ to SQL sınıfları arasında ilişkilendirme (ilişki) oluşturma (O/R Tasarımcısı)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)