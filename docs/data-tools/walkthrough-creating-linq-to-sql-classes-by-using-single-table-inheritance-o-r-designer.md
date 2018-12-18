---
title: 'İzlenecek yol: Tek tablolu devralma (O R Designer) kullanarak LINQ to SQL sınıfları oluşturma'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 943b75c9c5f9c0c32ab02b5e73c07282728e0beb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49864737"
---
# <a name="walkthrough-create-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>İzlenecek yol: LINQ tek tablolu devralma (O/R Tasarımcısı) kullanarak SQL sınıfları oluşturma
[LINQ to SQL araçları Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md) ilişkisel sistemlerde genellikle uygulandığı şekilde tek tablolu devralmayı destekler. Bu kılavuzda sağlanan genel adımları sırasında genişletir [nasıl yapılır: O/R Tasarımcısı kullanarak devralmayı yapılandırma](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) konu ve devralma kullanımını göstermek için gerçek bazı veriler sağlar [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

 Bu kılavuz boyunca aşağıdaki görevleri gerçekleştirin:

- Bir veritabanı tablosu oluşturun ve verilerini ekleyin.

- Bir Windows Forms uygulaması oluşturun.

- Ekleme bir [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] bir projeye.

- Yeni varlık sınıfları oluşturun.

- Varlık sınıflarının devralma kullanmak için yapılandırın.

- Devralınan sınıf sorgulayın.

- Bir Windows formunda veri görüntüleme.

## <a name="create-a-table-to-inherit-from"></a>Verileri devralmak için tablo oluşturma
 Devralma nasıl çalıştığını görmek için küçük bir oluşturma `Person` tablo, bir temel sınıf olarak kullanın ve ardından oluşturmak bir `Employee` devralan bir nesne.

### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Devralma göstermek için temel bir tablo oluşturmak için

1.  İçinde **Sunucu Gezgini** veya **veritabanı Gezgini**, sağ **tabloları** düğüm ve tıklatın **Yeni Tablo Ekle**.

    > [!NOTE]
    >  Northwind veritabanına veya tabloya eklediğiniz herhangi bir veritabanını kullanabilirsiniz.

2.  İçinde **Tablo Tasarımcısı**, tabloda aşağıdaki sütunları ekleyin:

    |Sütun adı|Veri Türü|Null değerlere izin ver|
    |-----------------|---------------|-----------------|
    |**ID**|**int**|**False**|
    |**Türü**|**int**|**TRUE**|
    |**FirstName**|**Nvarchar(200)**|**False**|
    |**Soyadı**|**Nvarchar(200)**|**False**|
    |**Yöneticisi**|**int**|**TRUE**|

3.  Kimlik sütunu birincil anahtar olarak ayarlayın.

4.  Tabloyu kaydettikten ve adlandırın **kişi**.

## <a name="add-data-to-the-table"></a>Tabloya veri ekleme
 Devralma doğru yapılandırdığınızı onaylayın, böylece tabloya bazı veriler tek tablolu devralma her sınıf için gerekir.

### <a name="to-add-data-to-the-table"></a>Tabloya veri eklemek için

1.  Tablo Veri Görünümü'nde açın. (Sağ **kişi** tablosundaki **Sunucu Gezgini** veya **veritabanı Gezgini** tıklatıp **tablo verilerini Göster**.)

2.  Aşağıdaki veriler, tabloya kopyalayın. (Kopyalayın ve sonra tüm satır seçerek tablosuna Yapıştır **sonuçları** bölmesinde.)

    ||||||
    |-|-|-|-|-|
    |**ID**|**Türü**|**FirstName**|**Soyadı**|**Yöneticisi**|
    |**1**|**1**|**Anne**|**Wallace**|**NULL**|
    |**2**|**1**|**Carlos**|**Grilo**|**NULL**|
    |**3**|**1**|**Yael**|**Peled**|**NULL**|
    |**4**|**2**|**Gatis**|**Ozolins**|**1**|
    |**5**|**2**|**Andreas**|**Hauser**|**1**|
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|
    |**7**|**2**|**Alexey**|**Orekhov**|**2**|
    |**8**|**2**|**Michał**|**Poliszkiewicz**|**2**|
    |**9**|**2**|**Tai**|**N**|**2**|
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|
    |**11**|**2**|**Kemal**|**Martin**|**3**|
    |**12**|**2**|**Ken**|**Kwok**|**3**|

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma
 Tablo oluşturduğunuza göre yapılandırma devralma göstermek için yeni bir proje oluşturun.

### <a name="to-create-the-new-windows-forms-application"></a>Yeni bir Windows Forms uygulaması oluşturma

1. Visual Studio'da üzerinde **dosya** menüsünde **yeni** > **proje**.

2. Ya da genişletin **Visual C#** veya **Visual Basic** seçip sol bölmedeki **Windows Masaüstü**.

3. Orta bölmede seçin **Windows Forms uygulaması** proje türü.

4. Projeyi adlandırın **InheritanceWalkthrough**ve ardından **Tamam**.

     **InheritanceWalkthrough** projesi oluşturulur ve eklenen **Çözüm Gezgini**.

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Bir LINQ to SQL sınıfları dosyası projeye Ekle

### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Bir LINQ to SQL dosyası projeye eklemek için

1.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.

2.  Tıklayın **LINQ to SQL sınıfları** şablonu ve ardından **Ekle**.

     *.Dbml* dosya projeye eklenir ve **O/R Tasarımcısı** açılır.

## <a name="create-the-inheritance-by-using-the-or-designer"></a>O/R Tasarımcısı kullanarak devralmayı oluşturma
 Devralma sürükleyerek yapılandırma bir **devralma** nesnesinden **araç kutusu** tasarım yüzeyine.

### <a name="to-create-the-inheritance"></a>Devralma oluşturmak için

1.  İçinde **Sunucu Gezgini** veya **veritabanı Gezgini**, gitmek **kişi** daha önce oluşturduğunuz bir tablo.

2.  Sürükleme **kişi** üzerine tablo **O/R Tasarımcısı** tasarım yüzeyi.

3.  İkinci sürükleyin **kişi** üzerine tablo **O/R Tasarımcısı** adını değiştirip **çalışan**.

4.  Silme **Manager** özelliğinden **kişi** nesne.

5.  Silme **türü**, **kimliği**, **FirstName**, ve **LastName** özelliklerinden **çalışan** nesne. (Diğer bir deyişle, dışındaki tüm özellikleri Sil **Manager**.)

6.  Gelen **Object Relational Designer** sekmesinde **araç kutusu**, oluşturun bir **devralma** arasında **kişi** ve  **Çalışan** nesneleri. Bunu yapmak için tıklatın **devralma** öğesi **araç kutusu** ve fare düğmesini bırakın. Ardından, **çalışan** nesnesi ve ardından **kişi** nesnesine **O/R Tasarımcısı**. Devralım çizgisi üzerindeki oku ardından işaret **kişi** nesne.

7.  Tıklayın **devralma** tasarım yüzeyinde satır.

8.  Ayarlama **ayrıştırıcı özelliği** özelliğini **türü**.

9. Ayarlama **türetilen sınıf ayrıştırıcısı değerinin** özelliğini **2**.

10. Ayarlama **temel sınıf ayrıştırıcı değeri** özelliğini **1**.

11. Ayarlama **devralma varsayılan** özelliğini **kişi**.

12. Projeyi oluşturun.

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Devralınan sınıf sorgulamak ve formdaki verileri görüntüleme
 Şimdi, belirli bir sınıfın nesne modelinde sorgular forma bazı kod ekleyin.

### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>LINQ sorgusu oluşturun ve sonuçları formunda görüntülemek için

1.  Sürükleme bir **ListBox** üzerine **Form1**.

2.  Formu oluşturmak için bir `Form1_Load` olay işleyicisi.

3.  Aşağıdaki kodu ekleyin `Form1_Load` olay işleyicisi:

    ```vb
    Dim dc As New DataClasses1DataContext
    Dim results = From emp In dc.Persons _
        Where TypeOf emp Is Employee _
        Select emp

    For Each Emp As Employee In results
        ListBox1.Items.Add(Emp.LastName)
    Next
    ```

    ```csharp
    NorthwindDataContext dc = new DataClasses1DataContext();
    var results = from emp in dc.Persons
                  where emp is Employee
                  select emp;

    foreach(Employee Emp in results)
    {
        listBox1.Items.Add(Emp.LastName)
    }
    ```

## <a name="test-the-application"></a>Uygulamayı test etme
 Uygulamayı çalıştırmak ve liste kutusunda görüntülenen kayıt tüm çalışanlar olduğunu doğrulayın (2'de bir değere sahip kayıtları kendi **türü** sütunu).

### <a name="to-test-the-application"></a>Uygulamayı test etmek için

1.  Tuşuna **F5**.

2.  Yalnızca kaydı, 2'de bir değere sahip olun, **türü** sütununda görüntülenir.

3.  Formu kapatın. (Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Durdur**.)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [İzlenecek yol:, (O R Designer) SQL sınıflarına LINQ oluşturma](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Nasıl yapılır: Visual Basic veya C# içinde nesne modeli oluşturma](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)