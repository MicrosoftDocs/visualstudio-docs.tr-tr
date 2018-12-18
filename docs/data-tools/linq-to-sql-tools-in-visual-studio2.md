---
title: O/R Tasarımcısı genel bakış
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 68b19993448ed68520f267177ca760975cd4d4aa
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066815"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Visual Studio'da LINQ to SQL araçları

LINQ to SQL Microsoft tarafından yayınlanan ilk nesne ilişkisel eşleme teknoloji oluştu. Temel senaryolarında iyi çalışır ve Visual Studio'da desteklenmeye devam eder, ancak artık etkin geliştirilme aşamasındadır. LINQ zaten kullandığı eski bir uygulama korurken SQL veya SQL Server'ı kullanın ve birden çok tablo eşleme gerektirmeyen basit uygulamalar kullanın. Genel olarak, bir nesne ilişkisel eşleyicidir katmanı gerekli olduğunda yeni uygulamalar Entity Framework kullanmanız gerekir.

Visual Studio kullanarak SQL tablolarını temsil eden SQL sınıflarına LINQ oluşturma **Object Relational Designer** (**O/R Tasarımcısı**).

**O/R Tasarımcısı** tasarım yüzeyinde iki farklı alanlara sahiptir: varlıklar bölmesinde solda ve sağdaki yöntemler bölmesi. Varlıklar, varlık sınıfları, ilişkilerini ve devralma hiyerarşilerini görüntüler ana tasarım yüzeyi bölmesidir. Yöntemler bölmesini görüntüler tasarım yüzeyine olduğu <xref:System.Data.Linq.DataContext> saklı yordamları ve işlevleri için eşlenmiş yöntemleri.

**O/R Tasarımcısı** oluşturmak için bir görsel tasarım yüzeyi sağlar [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) varlık sınıfları ve ilişkileri (ilişki) bir veritabanındaki nesneleri temel alan. Diğer bir deyişle, **O/R Tasarımcısı** uygulamada veritabanındaki nesnelerle eşleşen bir nesne modeli oluşturur. Türü kesin belirlenmiş bir ayrıca oluşturur <xref:System.Data.Linq.DataContext> gönderir ve varlık sınıfları ve veritabanı arasında veri alır. **O/R Tasarımcısı** ayrıca saklı yordamlar eşlemek üzere işlevsellik sağlar ve yaramaz <xref:System.Data.Linq.DataContext> veriyor ve varlık sınıfları doldurma için kullanılan yöntemler. Son olarak, **O/R Tasarımcısı** tasarım varlık sınıfları arasındaki devralma ilişkileri olanağı sağlar.

## <a name="open-the-or-designer"></a>O/R Tasarımcısı'nı açın

LINQ to SQL varlık modeli projenize eklemek için seçin **proje** > **Yeni Öğe Ekle**ve ardından **LINQ to SQL sınıfları** proje öğeleri listesinden:

![LINQ to SQL sınıfları](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio oluşturur bir *.dbml* dosya ve çözümünüze ekler. XML eşleme dosyası ve ilgili kod dosyaları budur.

![LINQ to SQL sınıfları Çözüm Gezgini](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Seçtiğinizde, *.dbml* dosya, Visual Studio gösterir **O/R Tasarımcısı** yüzey model görsel olarak oluşturmanıza olanak sağlar. Aşağıdaki çizimde, sonra Northwind Tasarımcı gösterir `Customers` ve `Orders` tabloları sürüklediğiniz gelen **Sunucu Gezgini**. Tablolar arasında ilişki unutmayın.

![LINQ to SQL Tasarımcı](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> **O/R Tasarımcısı** yalnızca 1:1 eşleme ilişkileri desteklediğinden, bir Basit Nesne İlişkisel eşleyicisidir. Diğer bir deyişle, bir varlık sınıfı yalnızca 1:1 eşleme ilişkisi olan bir veritabanı tablosu veya görünümü olabilir. Birleştirilmiş bir tabloya bir varlık sınıfı eşleme gibi karmaşık eşleme desteklenmiyor; Entity Framework için karmaşık eşleme kullanın. Ayrıca, bir tek yönlü bir kod oluşturucuyu Tasarımcısı olur. Başka bir deyişle, Tasarımcı yüzeyine yaptığınız değişiklikleri kod dosyasında yansıtılır. El ile yapılan kod dosyası değil yansıtılır **O/R Tasarımcısı**. Kod dosyasında el ile yaptığınız tüm değişiklikler Tasarımcı kaydedilir ve kod yeniden oluşturulursa üzerine yazılır. Kullanıcı kodu ekleyin ve tarafından oluşturulan sınıflar genişletme hakkında daha fazla bilgi için **O/R Tasarımcısı**, bkz: [nasıl yapılır: bir O/R tasarımcısı tarafından oluşturulan kodu genişletme](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>Oluşturma ve DataContext yapılandırma

Siz ekledikten sonra bir **LINQ to SQL sınıfları** öğesi projeye ve açık **O/R Tasarımcısı**, boş bir tasarım yüzeyinde boş bir temsil eden <xref:System.Data.Linq.DataContext> yapılandırılması hazır. <xref:System.Data.Linq.DataContext> tasarım yüzeyine sürüklediğiniz ilk öğesi tarafından sağlanan bağlantı bilgileriyle yapılandırılır. Bu nedenle, <xref:System.Data.Linq.DataContext> ilk öğesinden tasarım yüzeyine bırakılan bağlantı bilgilerini kullanarak yapılandırılır. Hakkında daha fazla bilgi için <xref:System.Data.Linq.DataContext> sınıfı bakın [DataContext yöntemi (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Veritabanı tabloları ve görünümleri eşleştiren varlık sınıfları oluşturma

Veritabanı tabloları ve görünümleri sürükleyerek, tablolar ve görünümler ile eşlenen varlık sınıfları oluşturabilirsiniz **Sunucu Gezgini** veya **veritabanı Gezgini** üzerine **O/R Tasarımcısı**. Önceki bölümde belirtildiği gibi <xref:System.Data.Linq.DataContext> tasarım yüzeyine sürüklediğiniz ilk öğesi tarafından sağlanan bağlantı bilgileriyle yapılandırılır. Farklı bir bağlantı kullanan bir sonraki öğe için eklenip eklenmediğini **O/R Tasarımcısı**, bağlantı için değiştirebileceğiniz <xref:System.Data.Linq.DataContext>. Daha fazla bilgi için [nasıl yapılır: tablolar ve görünümler (O/R Tasarımcısı) ile eşlenen SQL sınıflarına LINQ oluşturma](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Saklı yordamları ve işlevleri çağırma DataContext-metotları oluşturma

Oluşturabileceğiniz <xref:System.Data.Linq.DataContext> çağıran yöntemleri (eşleştirilmiş) saklı yordamları ve işlevleri sürükleyerek **Sunucu Gezgini** veya **veritabanı Gezgini** üzerine **O/R Tasarımcısı** . Saklı yordamları ve işlevleri eklenir **O/R Tasarımcısı** yöntemleri olarak <xref:System.Data.Linq.DataContext>.

> [!NOTE]
> Saklı yordamları ve işlevleri sürüklediğinizde **Sunucu Gezgini** veya **veritabanı Gezgini** üzerine **O/R Tasarımcısı**, dönüş türü oluşturulan <xref:System.Data.Linq.DataContext> yöntemi, öğenin nereden bırakın bağlı olarak farklılık gösterir. Daha fazla bilgi için [DataContext yöntemi (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Bir DataContext varlık sınıfları ve veritabanı arasında veri kaydetmek için saklı yordamları kullanmak için yapılandırma

Daha önce belirtildiği gibi oluşturabileceğiniz <xref:System.Data.Linq.DataContext> saklı yordamları ve işlevleri çağıran yöntemleri. Ayrıca, LINQ to SQL çalışma zamanı davranışı gerçekleştirir, güncelleştirmeler, ekler ve siler varsayılan için kullanılan saklı yordamlar da atayabilirsiniz. Daha fazla bilgi için [nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atama](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Devralma ve O/R Tasarımcısı

Diğer nesneleri gibi LINQ to SQL sınıfları devralma kullanabilirsiniz ve diğer sınıflarından türetilmiş. Bir veritabanında kalıtım ilişkileri çeşitli yollarla oluşturulur. **O/R Tasarımcısı** ilişkisel sistemlerde sık uygulandığı şekilde tek tablolu devralma kavramını destekler. Daha fazla bilgi için [nasıl yapılır: O/R Tasarımcısı kullanarak devralmayı yapılandırma](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>LINQ to SQL sorguları

Tarafından oluşturulan varlık sınıfları **O/R Tasarımcısı** ile kullanılmak üzere tasarlanmış [dil ile tümleşik sorgu (LINQ)](/dotnet/csharp/linq/). Daha fazla bilgi için [nasıl yapılır: bilgi sorgulama](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Üretilen DataContext ve varlık sınıf kodunu farklı ad alanında ayrı

**O/R Tasarımcısı** sağlar **bağlam Namespace** ve **varlık Namespace** özellikleri <xref:System.Data.Linq.DataContext>. Bu özellikler ne ad alanı belirlemek <xref:System.Data.Linq.DataContext> ve varlık sınıfı kod içinde oluşturulur. Bu özellikler varsayılan olarak, boş olur ve <xref:System.Data.Linq.DataContext> ve varlık sınıfları, uygulamanın ad alanına oluşturulur. Uygulamanın ad alanı başka bir ad alanı içinde kod üretmek için bir değer olarak girin. **bağlam Namespace** ve/veya **varlık Namespace** özellikleri.

## <a name="reference-content"></a>Başvuru içeriği

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Sık sorulan sorular (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)