---
title: Parametreleştirilmiş TableAdapter sorguları oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 56e14d66275bd961829fc09e06f7d5e99dbcc2c4
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50218905"
---
# <a name="create-parameterized-tableadapter-queries"></a>Parametreleştirilmiş TableAdapter sorguları oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Parametreli bir sorgu, WHERE yan tümcesi içinde sorgu koşulları karşılayan verileri döndürür. Örneğin, yalnızca müşterilerin ekleyerek belirli bir şehirde görüntülemek için Müşteri listesini parametreleştirebilirsiniz `WHERE City = @City` Müşteri listesini döndüren SQL deyimini sonuna.  
  
 Parametreleştirilmiş TableAdapter sorguları oluşturma [veri kümesi Tasarımcısı](../data-tools/creating-and-editing-typed-datasets.md). Bir Windows uygulaması da oluşturabilirsiniz **Parametreleştirme veri kaynağı** komutunu **veri** menüsü. **Parametreleştirme veri kaynağı** komutu, parametre değerlerini girin ve sorguyu çalıştırın, form üzerindeki denetimleri oluşturur.  
  
> [!NOTE]
>  Parametreli sorgu oluşturulurken karşı kodlama veritabanına özgü parametre gösterimini kullanın. Örneğin, soru işareti Access ve OleDb veri kaynakları kullan '?' parametreleri belirtmek için bu nedenle WHERE yan tümcesi şuna benzeyecektir: `WHERE City = ?`.  
  
> [!NOTE]
>  İletişim kutuları ve menü komutları gördüğünüz Yardım menüsünde açıklanana içinde etkin ayarlarınıza ve kullandığınız sürüm bağlı olarak farklı olabilir. Ayarlarınızı değiştirmek için Git **Araçları** menü ve select **içeri ve dışarı aktarma ayarları**. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-parameterized-tableadapter-query"></a>Parametreleştirilmiş TableAdapter sorgu oluşturma  
  
#### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>Veri kümesi Tasarımcısı'nda parametreli bir sorgu oluşturmak için  
  
-   SQL deyimi için istenen parametrelere sahip bir WHERE yan tümcesi ekleyerek yeni bir TableAdapter'ı oluşturun. Daha fazla bilgi için [oluştur ve TableAdapter yapılandırma](../data-tools/create-and-configure-tableadapters.md).  
  
     veya  
  
-   Bir sorgu, WHERE yan tümcesi istenen parametrelerle SQL deyiminde ekleme, var olan bir TableAdapter ekleyin. Daha fazla bilgi için [nasıl yapılır: TableAdapter sorguları oluşturma](../data-tools/how-to-create-tableadapter-queries.md).  
  
#### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>Verilere bağlı bir form tasarlarken, parametreli bir sorgu oluşturmak için  
  
1.  Formunuzdaki bir veri kümesine zaten bağlı bir denetim seçin. Daha fazla bilgi için [Visual Studio'da verilere Windows Forms bağlama denetimleri](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
2.  Üzerinde **veri** menüsünde**Sorgu Ekle**.  
  
3.  Tamamlamak **arama ölçütü Oluşturucu** iletişim kutusunda, istenen parametrelere sahip bir WHERE yan tümcesi SQL deyiminde ekleme.  
  
### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>Varolan bir verilere bağlı forma bir sorgu ekleme  
  
1. Formda açın **Windows Form Tasarımcısı**.  
  
2. Üzerinde **veri** menüsünde **Sorgu Ekle** veya **veri akıllı etiketler**.  
  
   > [!NOTE]
   > Varsa **Sorgu Ekle** kullanılamaz **veri** menüsü, görüntüler veri kaynağı, formda bir denetim için Parametreleştirme eklemek için seçin. Form verileri görüntüler, örneğin, bir <xref:System.Windows.Forms.DataGridView> denetlemek, onu seçin. Form bireysel denetimlerinde verileri görüntülüyorsa, herhangi bir veriye bağlı denetim seçin.  
  
3. İçinde **Select veri kaynağı tablosu** alanı Ekle'yi seçin istediğiniz tablethat Parametreleştirme için.  
  
4. Bir ad yazın **yeni sorgu adı** yeni bir sorgu oluşturuyorsanız kutusu.  
  
    veya  
  
    Bir sorgu seçin **varolan sorgu adı** kutusu.  
  
5. İçinde **sorgu metni** parametreleri alan bir sorgu yazın.  
  
6. Seçin **Tamam**.  
  
    Bir giriş parametresi için Denetim ve bir **yük** düğmesi, formda eklenir bir <xref:System.Windows.Forms.ToolStrip> denetimi.  
  
   Hiçbir geçerli bir değere sahip kayıtları için sorgu istediğinizde TableAdapter parametreleri null değerler atanabilir. Örneğin, sahip şu sorguyu inceleyin bir `ShippedDate` parametresinde kendi `WHERE` yan tümcesi:  
  
   `SELECT CustomerID, OrderDate, ShippedDate`  
  
   `FROM Orders`  
  
   `WHERE (ShippedDate = @ShippedDate) OR`  
  
   `(ShippedDate IS NULL)`  
  
   Bu bir TableAdapter sorgu olsaydı, aşağıdaki kod ile birlikte gönderilmeyen tüm siparişleri için sorgu:  
  
   [!code-csharp[VbRaddataTableAdapters#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form2.cs#8)]
   [!code-vb[VbRaddataTableAdapters#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form2.vb#8)]  
  
#### <a name="to-enable-a-query-to-accept-null-values"></a>Null değerleri kabul etmek bir sorgu etkinleştirmek için  
  
1.  İçinde **veri kümesi Tasarımcısı**, null parametre değerlerini kabul etmesi gerekir TableAdapter sorgu seçin.  
  
2.  İçinde **özellikleri** penceresinde **parametreleri**. Ardından üç nokta simgesine basın (**...** ) açmak için düğmeyi **parametre koleksiyon Düzenleyicisi**.  
  
3.  Null değerlere izin verir parametreyi seçin ve ayarlayın **AllowDbNull** özelliğini `true`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)

