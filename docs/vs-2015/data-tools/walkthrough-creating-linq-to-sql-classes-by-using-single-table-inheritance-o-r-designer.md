---
title: 'İzlenecek yol: Tek tablolu devralma (O R Designer) kullanarak LINQ to SQL sınıfları oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cd8572900e181da1b33b26638f15aa04845008e3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260734"
---
# <a name="walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>İzlenecek yol: Tek tablolu devralma (O/R Tasarımcısı) kullanarak LINQ to SQL sınıfları oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[LINQ to SQL araçlarını Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md) ilişkisel sistemlerde genellikle uygulandığı şekilde tek tablolu devralmayı destekler. Bu kılavuzda sağlanan genel adımları sırasında genişletir [nasıl yapılır: O/R Tasarımcısı kullanarak devralmayı yapılandırma](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) konu ve devralma kullanımını göstermek için gerçek bazı veriler sağlar [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
 Bu kılavuz boyunca aşağıdaki görevleri gerçekleştireceksiniz:  
  
-   Bir veritabanı tablosu oluşturun ve verilerini ekleyin.  
  
-   Bir Windows Forms uygulaması oluşturun.  
  
-   Ekleme bir [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] bir projeye.  
  
-   Yeni varlık sınıfları oluşturun.  
  
-   Varlık sınıflarının devralma kullanmak için yapılandırın.  
  
-   Devralınan sınıf sorgulayın.  
  
-   Bir Windows formunda veri görüntüleme.  
  
## <a name="create-a-table-to-inherit-from"></a>Verileri devralmak için tablo oluşturma  
 Devralma nasıl çalıştığını görmek için küçük bir kişi tablo oluşturma, temel sınıf olarak kullanın ve sonra da bundan devralan çalışan nesne oluşturmak.  
  
#### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Devralma göstermek için temel bir tablo oluşturmak için  
  
1.  İçinde **Sunucu Gezgini**/**veritabanı Gezgini**, sağ **tabloları** düğüm ve tıklatın **Yeni Tablo Ekle**.  
  
    > [!NOTE]
    >  Northwind veritabanına veya tabloya eklediğiniz herhangi bir veritabanını kullanabilirsiniz.  
  
2.  Tablo Tasarımcısı'nda tabloda aşağıdaki sütunları ekleyin:  
  
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
  
#### <a name="to-add-data-to-the-table"></a>Tabloya veri eklemek için  
  
1.  Tablo Veri Görünümü'nde açın. (Sağ **kişi** tablosundaki **Sunucu Gezgini**/**veritabanı Gezgini** tıklatıp **tablo verilerini Göster**.)  
  
2.  Aşağıdaki veriler, tabloya kopyalayın. (Kopyalayın ve ardından sonuçlar bölmesinde tüm satırı seçerek tablosuna Yapıştır.)  
  
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
  
## <a name="create-a-new-project"></a>Yeni bir proje oluşturun  
 Tablo oluşturduğunuza göre yapılandırma devralma göstermek için yeni bir proje oluşturun.  
  
#### <a name="to-create-the-new-windows-application"></a>Yeni bir Windows uygulaması oluşturmak için  
  
1.  Gelen **dosya** menüsünden Yeni bir proje oluşturun.  
  
2.  Projeyi adlandırın **InheritanceWalkthrough**.  
  
    > [!NOTE]
    >  [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Visual Basic ve C# projelerinde desteklenir. Yeni projeyi bu dillerden birinde oluşturun.  
  
3.  Tıklayın **Windows Forms uygulaması** şablonu ve ardından **Tamam**. Daha fazla bilgi için [istemci uygulamaları](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
4.  InheritanceWalkthrough projesi oluşturulur ve eklenen **Çözüm Gezgini**.  
  
## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>LINQ to SQL ekleme projeye dosya sınıfları  
  
#### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>LINQ to SQL dosyası projeye eklemek için  
  
1.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.  
  
2.  Tıklayın **LINQ to SQL sınıfları** şablonu ve ardından **Ekle**.  
  
     Bir .dbml dosyası projenize eklenir ve [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] açılır.  
  
## <a name="create-the-inheritance-by-using-the-or-designer"></a>O/R Tasarımcısı kullanarak devralmayı oluşturma  
 Devralma sürükleyerek yapılandırma bir **devralma** nesnesinden **araç kutusu** tasarım yüzeyine.  
  
#### <a name="to-create-the-inheritance"></a>Devralma oluşturmak için  
  
1.  İçinde **Sunucu Gezgini**/**veritabanı Gezgini**, gitmek **kişi** daha önce oluşturduğunuz bir tablo.  
  
2.  Sürükleme **kişi** üzerine tablo [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] tasarım yüzeyi.  
  
3.  İkinci sürükleyin **kişi** üzerine tablo [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] adını değiştirip **çalışan**.  
  
4.  Silme **Manager** özelliğinden **kişi** nesne.  
  
5.  Silme **türü**, **kimliği**, **FirstName**, ve **LastName** özelliklerinden **çalışan** nesne. (Diğer bir deyişle, dışındaki tüm özellikleri Sil **Manager**.)  
  
6.  Gelen **Object Relational Designer** sekmesinde **araç kutusu**, oluşturun bir **devralma** arasında **kişi** ve  **Çalışan** nesneleri. Bunu yapmak için tıklatın **devralma** öğesi **araç kutusu** ve fare düğmesini bırakın. Ardından, **çalışan** nesnesi ve ardından **kişi** nesnesine [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Devralım çizgisi üzerindeki oku işaret edecek **kişi** nesne.  
  
7.  Tıklayın **devralma** tasarım yüzeyinde satır.  
  
8.  Ayarlama **ayrıştırıcı özelliği** özelliğini **türü**.  
  
9. Ayarlama **türetilen sınıf ayrıştırıcısı değerinin** özelliğini **2**.  
  
10. Ayarlama **temel sınıf ayrıştırıcı değeri** özelliğini **1**.  
  
11. Ayarlama **devralma varsayılan** özelliğini **kişi**.  
  
12. Projeyi oluşturun.  
  
## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Devralınan sınıf sorgulamak ve formdaki verileri görüntüleme  
 Artık, belirli bir sınıfın nesne modelinde sorgular formun bazı kod ekleyeceksiniz.  
  
#### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>LINQ sorgusu oluşturun ve sonuçları formunda görüntülemek için  
  
1.  Sürükleme bir **ListBox** Form1.  
  
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
 Uygulamayı çalıştırmak ve liste kutusunda görüntülenen kayıt tüm çalışanlar (kendi Türü sütununda 2 değerine sahip kayıtları) olduğundan emin olun.  
  
#### <a name="to-test-the-application"></a>Uygulamayı test etmek için  
  
1.  F5 tuşuna basın.  
  
2.  Yalnızca kendi Türü sütununda 2 değerine sahip kayıtların görüntülendiğini doğrulayın.  
  
3.  Formu kapatın. (Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Durdur**.)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL araçlarını Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Nasıl yapılır: LINQ to SQL sınıfları (O R Designer) projeye Ekle](http://msdn.microsoft.com/library/7bb184ab-ec54-4cda-b706-604b2b4a3ed6)   
 [İzlenecek yol: LINQ to SQL sınıfları (O R Designer) oluşturma](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atama](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Nasıl yapılır: Visual Basic veya C# içinde Nesne Modeli Oluşturma](http://msdn.microsoft.com/library/a0c73b33-5650-420c-b9dc-f49310c201ee)

