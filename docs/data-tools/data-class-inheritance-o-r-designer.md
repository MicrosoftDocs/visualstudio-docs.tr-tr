---
title: Veri sınıf devralma (O R Tasarımcısı)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6c6b17ad38e9aae78975e43797931a326955712d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756743"
---
# <a name="data-class-inheritance-or-designer"></a>Veri sınıf devralma (O/R Tasarımcısı)

Diğer nesneleri gibi LINQ'ten SQL'e sınıflarını devralma kullanabilirsiniz ve diğer sınıflardan türetilmiş olmalıdır. Kod içinde bir sınıf diğerinden devralır bildirme tarafından nesneleri arasındaki ilişkiler devralma belirtebilirsiniz. Bir veritabanında, çeşitli yollarla devralma ilişkisi oluşturulur. **Nesne İlişkisel Tasarımcısı** (**O/R Tasarımcısı**) genellikle ilişkisel sistemlerinde gerçekleştirilir gibi tek Tablo Devralma kavramını destekler.

Tek Tablo Devralma temel ve türetilen sınıflar için sütun içeren bir tek veritabanı tablosu yok. İlişkisel veri ile ayrıştırıcı sütunun herhangi verilen kayıt ait hangi sınıfı belirleyen bir değer içerir. Örneğin, göz önünde bulundurun bir `Persons` herkes bir şirket tarafından işe içeren tablo. Bazı kişiler çalışanlar ve bazı kişiler yöneticileri. `Persons` Tablo adlı bir sütun içeren `Type` 1 değeri, yöneticileri ve 2 değerini için çalışanlar için sahip. `Type` Ayrıştırıcı sütunun bir sütundur. Bu senaryoda, çalışanların öğesinin bir alt kümesi oluşturmak ve yalnızca sahip kayıtları sınıfıyla doldurmak bir `Type` değeri 2.

Yapılandırdığınızda devralma varlık sınıflarını kullanarak [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], iki kez tasarımcıya devralma veri içeren tek tablo sürükleyin: devralma hiyerarşisinde her sınıf için bir kez. Tabloları Designer'a ekledikten sonra bunları bir devralma öğesinden bağlamak **Nesne İlişkisel Tasarımcısı** araç kutusunu ve ardından kümesi dört devralma özelliklerinde **özellikleri** penceresi.

## <a name="inheritance-properties"></a>Devralma Özellikleri

Aşağıdaki tabloda, devralma özellikleri ve açıklamaları listelenmektedir:

|Özellik|Açıklama|
|--------------|-----------------|
|**Ayrıştırıcı özelliği**|Hangi sınıfın belirler (sütuna eşlenen) özelliği geçerli kayıt ait.|
|**Taban sınıf Ayrıştırıcıyı değeri**|Değer (olarak tasarlanmış sütununda **Ayrıştırıcıyı özelliği**) bir kayıt temel sınıfını olup olmadığını belirler.|
|**Türetilmiş sınıf Ayrıştırıcıyı değeri**|Değer (olarak tasarlanmış özelliğinde **Ayrıştırıcıyı özelliği**) bir kayıt türetilen sınıfı olup olmadığını belirler.|
|**Devralma varsayılan**|Özellik değeri olarak tasarlanmış olduğunda doldurulur sınıfının **Ayrıştırıcıyı özelliği** ya da eşleşmiyor **temel sınıf Ayrıştırıcıyı değeri** veya **türetilen sınıfı Ayrıştırıcı değeri**.|

Devralma kullanan ve ilişkisel verilere karşılık gelen bir nesne modeli oluşturmak biraz kafa karıştırıcı olabilir. Bu konuda temel kavramları ve devralma yapılandırmak için gerekli olan özellikler hakkında bilgi sağlar. Devralma ile yapılandırma hakkında daha anlaşılır bir açıklama aşağıdaki konularda **O/R Tasarımcısı**.

|Konu|Açıklama|
|-----------|-----------------|
|[Nasıl yapılır: devralma O/R Tasarımcısı kullanarak yapılandırma](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Tek Tablo Devralma kullanarak varlık sınıfları yapılandırmayı açıklar **O/R Tasarımcısı**.|
|[İzlenecek yol: LINQ tek tablo devralma (O/R Tasarımcısı) kullanarak SQL sınıfları için oluşturma](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Tek Tablo Devralma kullanarak varlık sınıfları yapılandırma hakkında adım adım yönergeler sağlar **O/R Tasarımcısı**.|

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ-SQL Visual Studio Araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [İzlenecek yol: LINQ (O R Tasarımcısı) SQL sınıfları için oluşturma](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [İzlenecek yol: LINQ tek tablo devralma (O/R Tasarımcısı) kullanarak SQL sınıfları için oluşturma](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Başlarken](/dotnet/framework/data/adonet/sql/linq/getting-started)