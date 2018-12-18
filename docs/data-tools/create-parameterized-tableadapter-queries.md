---
title: Parametreleştirilmiş TableAdapter sorguları oluşturma
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9d344fdd444a46b3e0434e70850946ef242864b0
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388484"
---
# <a name="create-parameterized-tableadapter-queries"></a>Parametreleştirilmiş TableAdapter sorguları oluşturma

Parametreli bir sorgu, WHERE yan tümcesi içinde sorgu koşulları karşılayan verileri döndürür. Örneğin, yalnızca müşterilerin ekleyerek belirli bir şehirde görüntülemek için Müşteri listesini parametreleştirebilirsiniz `WHERE City = @City` Müşteri listesini döndüren SQL deyimini sonuna.

Parametreleştirilmiş TableAdapter sorguları oluşturma **veri kümesi Tasarımcısı**. Bir Windows uygulaması da oluşturabilirsiniz **Parametreleştirme veri kaynağı** komutunu **veri** menüsü. **Parametreleştirme veri kaynağı** komutu, parametre değerlerini girin ve sorguyu çalıştırın, form üzerindeki denetimleri oluşturur.

> [!NOTE]
> Parametreli sorgu oluşturulurken karşı kodlama veritabanına özgü parametre gösterimini kullanın. Örneğin, soru işareti Access ve OleDb veri kaynakları kullan '?' parametreleri belirtmek için bu nedenle WHERE yan tümcesi şuna benzeyecektir: `WHERE City = ?`.

## <a name="create-a-parameterized-tableadapter-query"></a>Parametreleştirilmiş TableAdapter sorgu oluşturma

### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>Veri kümesi Tasarımcısı'nda parametreli bir sorgu oluşturmak için

-   SQL deyimi için istenen parametrelere sahip bir WHERE yan tümcesi ekleyerek yeni bir TableAdapter'ı oluşturun. Daha fazla bilgi için [oluştur ve TableAdapter yapılandırma](../data-tools/create-and-configure-tableadapters.md).

     veya

-   Bir sorgu, WHERE yan tümcesi istenen parametrelerle SQL deyiminde ekleme, var olan bir TableAdapter ekleyin.

### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>Verilere bağlı bir form tasarlarken, parametreli bir sorgu oluşturmak için

1.  Formunuzdaki bir veri kümesine zaten bağlı bir denetim seçin. Daha fazla bilgi için [Visual Studio'da verilere Windows Forms bağlama denetimleri](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2.  Üzerinde **veri** menüsünde **Sorgu Ekle**.

3.  Tamamlamak **arama ölçütü Oluşturucu** iletişim kutusunda, istenen parametrelere sahip bir WHERE yan tümcesi SQL deyiminde ekleme.

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>Varolan bir verilere bağlı forma bir sorgu ekleme

1.  Formda açın **Windows Form Tasarımcısı**.

2.  Üzerinde **veri** menüsünde **Sorgu Ekle** veya **veri akıllı etiketler**.

    > [!NOTE]
    > Varsa **Sorgu Ekle** kullanılamaz **veri** menüsü, görüntüler veri kaynağı, formda bir denetim için Parametreleştirme eklemek için seçin. Form verileri görüntüler, örneğin, bir <xref:System.Windows.Forms.DataGridView> denetlemek, onu seçin. Form bireysel denetimlerinde verileri görüntülüyorsa, herhangi bir veriye bağlı denetim seçin.

3.  İçinde **Select veri kaynağı tablosu** alanında Parametreleştirme eklemek istediğiniz tabloyu seçin.

4.  Bir ad yazın **yeni sorgu adı** yeni bir sorgu oluşturuyorsanız kutusu.

     veya

     Bir sorgu seçin **varolan sorgu adı** kutusu.

5.  İçinde **sorgu metni** parametreleri alan bir sorgu yazın.

6.  Seçin **Tamam**.

     Bir giriş parametresi için Denetim ve bir **yük** düğmesi, formda eklenir bir <xref:System.Windows.Forms.ToolStrip> denetimi.

### <a name="query-for-null-values"></a>Null değerler için sorgu

Hiçbir geçerli bir değere sahip kayıtları için sorgu istediğinizde TableAdapter parametreleri null değerler atanabilir. Örneğin, sahip şu sorguyu inceleyin bir `ShippedDate` parametresinde kendi `WHERE` yan tümcesi:

 ```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

Bu bir TableAdapter sorgu olsaydı, aşağıdaki kod ile birlikte gönderilmeyen tüm siparişleri için sorgu:

[!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
[!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]

Null değerleri kabul etmek bir sorgu etkinleştirmek için:

1.  İçinde **veri kümesi Tasarımcısı**, null parametre değerlerini kabul etmesi gerekir TableAdapter sorgu seçin.

2.  İçinde **özellikleri** penceresinde **parametreleri**, sonra üç nokta simgesine tıklayın (**...** ) açmak için düğmeyi **parametre koleksiyon Düzenleyicisi**.

3.  Null değerlere izin verir parametreyi seçin ve ayarlayın **AllowDbNull** özelliğini `true`.

## <a name="see-also"></a>Ayrıca bkz.

- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)