---
title: 'Nasıl yapılır: devralma O R Tasarımcısı kullanarak yapılandırma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: bb0be89627f5e7e95d7d45ebfb938bca3e4a982b
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089270"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Nasıl yapılır: devralma O/R Tasarımcısı kullanarak yapılandırma
**Nesne İlişkisel Tasarımcısı** (**O/R Tasarımcısı**) genellikle ilişkisel sistemlerinde gerçekleştirilir gibi tek Tablo Devralma kavramını destekler. Tek Tablo Devralma üst bilgi ve alt bilgi alanları içeren bir tek veritabanı tablo yok. İlişkisel veri ile ayrıştırıcı sütunun herhangi bir kaydın ait hangi sınıfı belirleyen bir değer içerir.

Örneğin, göz önünde bulundurun bir `Persons` herkes bir şirket tarafından işe içeren tablo. Bazı kişiler çalışanlar ve bazı kişiler yöneticileri. `Persons` Tablo adlı bir sütun içeren `EmployeeType` 1 değeri, yöneticileri ve 2 değerini için çalışanlar için olan; ayrıştırıcı sütunun budur. Bu senaryoda, çalışanların öğesinin bir alt kümesi oluşturmak ve yalnızca sahip kayıtları sınıfıyla doldurmak bir `EmployeeType` değeri 2. Ayrıca her sınıfları uygulanmaz sütunları kaldırabilirsiniz.

Devralma kullanır (ve ilişkisel verilere karşılık gelir) nesne modeli oluşturma biraz kafa karıştırıcı olabilir. Aşağıdaki yordam kalıtım yapılandırmak için gereken adımları özetler **O/R Tasarımcısı**. Veri kullanan bir kılavuz sağlanan için var olan bir tablo ve sütun başvuran olmadan aşağıdaki genel adımları zor olabilir. Devralma kullanarak yapılandırma için ayrıntılı adım adım yönergeler için **O/R Tasarımcısı**, bkz: [izlenecek yol: oluşturma LINQ'ten SQL'e sınıflarını tek tablo devralma (O/R Tasarımcısı) kullanarak](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

## <a name="to-create-inherited-data-classes"></a>Devralınan veri sınıfları oluşturmak için

1.  Açık **O/R Tasarımcısı** ekleyerek bir **LINQ'ten SQL'e sınıflarını** varolan bir Visual Basic veya C# proje öğesi.

2.  Temel sınıf olarak kullanmak istediğiniz tabloyu sürükleyin **O/R Tasarımcısı**.

3.  Tablo ikinci bir kopyası sürükleyin **O/R Tasarımcısı** ve yeniden adlandırın. Bu, türetilmiş sınıf veya bir alt kümesi değil.

4.  ' I tıklatın **devralma** içinde **Nesne İlişkisel Tasarımcısı** sekmesinde **araç**, alt kümesi (adlandırdığınız tablosu) ve ardından için temel sınıf bağlanın.

    > [!NOTE]
    >  Tıklatın **devralma** öğesi **araç** ve fare düğmesini bırakın, 3. adımda oluşturduğunuz sınıfı ikinci bir kopyası tıklayın ve ardından 2. adımda oluşturduğunuz ilk sınıfı'ı tıklatın. Devralma Satırı Oku ilk sınıfa işaret eder.

5.  Her sınıfında görünmesini istediğiniz değil ve ilişkilendirmeler için kullanılmayan tüm nesne özellikleri silin. İlişkilendirmeler için kullanılan nesne özellikleri silmeye çalışırsanız bir hata alıyorsunuz: [özelliği \<özellik adı > ilişkiye katılan olduğundan silinemez \<ilişkilendirme adı >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    >  Türetilmiş bir sınıf kendi taban sınıf içinde tanımlanan özellikleri devraldığı için aynı sütun her sınıfında tanımlanamaz. (Sütun özellikleri olarak uygulanır.) Türetilmiş sınıf sütunlarında oluşturulmasını temel sınıf özelliği üzerinde devralma değiştiricisi ayarlayarak etkinleştirebilirsiniz. Daha fazla bilgi için bkz: [devralma temelleri (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics).

6.  Devralma satırda seçin **O/R Tasarımcısı**.

7.  İçinde **özellikleri** penceresindeki ayarlayın **Ayrıştırıcıyı özelliği** sınıflarınızı kayıtları ayırt sütun adı.

8.  Ayarlama **türetilmiş sınıf Ayrıştırıcıyı değeri** kayıt devralınan türü olarak belirler veritabanındaki değerle özelliğine. (Ayrıştırıcıyı sütununda depolanır ve devralınan sınıfı belirlemek için kullanılan değer budur.)

9. Ayarlama **temel sınıf Ayrıştırıcıyı değeri** özellik değerine kaydı temel tür olarak atar. (Ayrıştırıcıyı sütununda depolanır ve temel sınıfı belirlemek için kullanılan değer budur.)

10. İsteğe bağlı olarak da ayarlayabilirsiniz **devralma varsayılan** herhangi eşleşmeyen satırları yüklenirken devralma kod tanımlandığında kullanılan bir devralma hiyerarşisinde bir tür belirleme özelliği. Bir kayıt kendi Ayrıştırıcıyı sütununda bir değer varsa, diğer bir deyişle, ya da değeri eşleşmiyor **türetilmiş sınıf Ayrıştırıcıyı değeri** veya **temel sınıf Ayrıştırıcıyı değeri** özellikleri, kayıt yükler olarak tasarlanmış türü **devralma varsayılan**.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ-SQL Visual Studio Araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [İzlenecek yol: LINQ (O R Tasarımcısı) SQL sınıfları için oluşturma](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [İzlenecek yol: LINQ tek tablo devralma (O/R Tasarımcısı) kullanarak SQL sınıfları için oluşturma](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Devralma temelleri (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Devralma](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)