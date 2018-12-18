---
title: Veri aramak için bir Windows formu oluşturma | Microsoft Docs
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
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e42c86cf94115d317eb20df66f4cef005e05eba9
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281803"
---
# <a name="create-a-windows-form-to-search-data"></a>Veri aramak için Windows Form oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Sık rastlanan bir uygulama senaryosu seçilen verileri form üzerinde görüntülemektir. Örneğin, belirli bir müşterinin siparişlerini veya belirli bir siparişin ayrıntılarını görüntülemek isteyebilirsiniz. Bu senaryoda, kullanıcı bilgileri forma girer ve sonra kullanıcının girişi parametre olarak kullanılarak bir sorgu yürütülür; diğer bir deyişle veriler parametreli bir sorgu temel alınarak seçilir. Sorgu sadece kullanıcı tarafından girilen ölçütleri karşılayan verileri getirir. Bu kılavuzda, belirli bir şehirdeki müşterileri getiren bir sorgu oluşturma ve kullanıcı arabirimini kullanıcıların şehir adı girip bir düğmeye basarak sorguyu çalıştırabilecekleri şekilde değiştirme işlemleri gösterilmiştir.  
  
 Parametreli sorgular kullanılması, veritabanının kayıtları hızla filtreleyerek işini en iyi şekilde yapmasını sağlayarak uygulamanızın verimli çalışmasına yardımcı olur. Buna karşılık, tüm veritabanı tablosunu istek, ağ üzerinden aktar ve ardından istediğiniz kayıtları bulmak için uygulama mantığı kullanmak, uygulamanızın yavaş ve verimli hale gelebilir.  
  
 Bir TableAdapter (ve denetimleri için parametre değerlerini kabul etmek ve sorguyu yürütmek için) kullanarak parametreli sorgular ekleyebilirsiniz **arama ölçütü Oluşturucu** iletişim kutusu. İletişim kutusunu seçerek açın **Sorgu Ekle** komutunu **veri** menü (veya herhangi bir TableAdapter akıllı etiketinde).  
  
 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:  
  
-   Yeni bir Windows Forms uygulaması projesi oluşturma.  
  
-   Oluşturma ve veri kaynağı ile uygulamanızda yapılandırma **veri kaynağı yapılandırması** Sihirbazı.  
  
-   İçindeki öğelerin bırakma türünü ayarlama **veri kaynakları** penceresi.  
  
-   Öğeleri sürükleyerek verileri görüntüleyen denetimler oluşturma **veri kaynakları** forma penceresi.  
  
-   Formdaki verileri görüntülemek için denetimler ekleme.  
  
-   Tamamlama **arama ölçütü Oluşturucu** iletişim kutusu.  
  
-   Parametreleri forma girme ve parametreli sorguyu yürütme.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için şunlar gerekir:  
  
-   Northwind örnek veritabanına erişim.  
  
## <a name="create-the-windows-application"></a>Windows uygulaması oluşturma  
 İlk adım oluşturmaktır bir **Windows uygulama**. Projeye bir ad atamak Bu adımda isteğe bağlıdır, ancak daha sonra kaydetmeniz çünkü Buraya bir ad vermeniz.  
  
#### <a name="to-create-the-new-windows-application-project"></a>Yeni bir Windows Uygulaması projesi oluşturmak için  
  
1.  Gelen **dosya** menüsünden Yeni bir proje oluşturun.  
  
2.  Projeyi adlandırın `WindowsSearchForm`.  
  
3.  Seçin **Windows uygulama** tıklatıp **Tamam**.  
  
     **WindowsSearchForm** projesi oluşturulur ve eklenen **Çözüm Gezgini**.  
  
## <a name="create-the-data-source"></a>Veri kaynağı oluşturma  
 Bu adımda veri kaynağı kullanarak bir veritabanı oluşturulur **veri kaynağı yapılandırması** Sihirbazı. Bağlantı oluşturmak için Northwind örnek veritabanına erişiminiz olmalıdır. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz. [yüklemek SQL Server örnek veritabanları](../data-tools/install-sql-server-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için  
  
1.  Üzerinde **veri** menüsünü tıklatın **veri kaynaklarını Göster**.  
  
2.  İçinde **veri kaynakları** penceresinde **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı yapılandırması** Sihirbazı.  
  
3.  Seçin **veritabanı** üzerinde **bir veri kaynağı türü seçin** sayfasında ve ardından **sonraki**.  
  
4.  Üzerinde **veri bağlantınızı seçin** sayfasında aşağıdakilerden birini yapın:  
  
    -   Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.  
  
    -   Seçin **yeni bağlantı** başlatmak için **Bağlantı Ekle/Değiştir** iletişim kutusu.  
  
5.  Veritabanınız parola gerektiriyorsa, hassas verileri eklemek ve ardından seçeneğini **sonraki**.  
  
6.  Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfasında **sonraki**.  
  
7.  Üzerinde **veritabanı nesnelerinizi seçin** sayfasında **tabloları** düğümü.  
  
8.  Seçin **müşteriler** tablosunu ve ardından **son**.  
  
     **NorthwindDataSet** projenize eklenir ve **müşteriler** tablo görünür **veri kaynakları** penceresi.  
  
## <a name="create-the-form"></a>Form oluşturma  
 Öğe sürükleyerek veriye bağlı denetimler oluşturabilirsiniz **veri kaynakları** formunuza penceresi.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Form üzerinde veri bağlama denetimleri oluşturmak için  
  
1.  Genişletin **müşteriler** düğümünde **veri kaynakları** penceresi.  
  
2.  Sürükleme **müşteriler** düğümünden **veri kaynakları** penceresinden formunuza.  
  
     A <xref:System.Windows.Forms.DataGridView> ve araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) Kayıtlarda gezinmek için formda görünür. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.  
  
## <a name="addparameterization-search-functionality-to-the-query"></a>Sorgulanacak Addparameterization (arama işlevselliği)  
 Özgün kullanarak sorgu, WHERE yan tümcesi ekleyebilirsiniz **arama ölçütü Oluşturucu** iletişim kutusu.  
  
#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>Parametreleri girmek üzere parametreli sorgu ve denetimler oluşturmak için  
  
1.  Seçin <xref:System.Windows.Forms.DataGridView> denetlemek ve ardından **Sorgu Ekle** üzerinde **veri** menüsü.  
  
2.  Tür `FillByCity` içinde **yeni sorgu adı** alanı **arama ölçütü Oluşturucu** iletişim kutusu.  
  
3.  Ekleme `WHERE City = @City` sorguya **sorgu metni** alan.  
  
     Sorgu aşağıdakine benzemelidir:  
  
     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`  
  
     `FROM Customers`  
  
     `WHERE City = @City`  
  
    > [!NOTE]
    >  Erişim ve OLE DB veri kaynakları, soru işareti kullanın ('? ') parametreleri belirtmek için bu nedenle WHERE yan tümcesi şuna benzeyecektir: `WHERE City = ?`.  
  
4.  Tıklayın **Tamam** kapatmak için **arama ölçütü Oluşturucu** iletişim kutusu.  
  
     A **FillByCityToolStrip** formuna eklenir.  
  
## <a name="testing-the-application"></a>Uygulamayı test etme  
 Uygulamanın çalıştırılması formunuzu giriş olarak parametreyi almaya hazır olarak açar.  
  
#### <a name="to-test-the-application"></a>Uygulamayı test etmek için  
  
1.  Uygulamayı çalıştırmak için F5 tuşuna basın.  
  
2.  Tür **Londra** içine **Şehir** metin kutusuna ve ardından **FillByCity**.  
  
     Veri Kılavuzu ölçütlere uyan müşterilerle doldurulur. Bu örnekte, veri kılavuzu yalnızca değeri olan müşterileri görüntüler **Londra** içinde kendi **Şehir** sütun.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Uygulama gereksinimlerinize bağlı olarak, parametreli form oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bu izlenecek yolda yapabileceğiniz bazı geliştirmeler şunlardır:  
  
-   İlgili verileri görüntüleyen denetimler ekleme. Daha fazla bilgi için [nasıl yapılır: Windows Forms uygulamasında görüntü ilgili verileri](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
-   Veritabanı nesneleri eklemek veya çıkarmak için veri kümesini düzenleme. Daha fazla bilgi için [oluşturun ve veri kümeleri yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

