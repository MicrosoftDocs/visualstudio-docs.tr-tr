---
title: TableAdapters düzenleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.dbtablefunctionwizard
- vs.datasource.datacomponentquerywizard
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], data component queries
- data [Visual Studio], TableAdapters
- TableAdapter Query Configuration Wizard
- data [Visual Studio], table adapter queries
ms.assetid: 8c06b306-24d0-4521-948d-07e3b7badd95
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: b242f8154f31391d168f2a41bfd00c01f037d87e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877653"
---
# <a name="editing-tableadapters"></a>TableAdapters düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bazen bağdaştırıcının tablo şemasını değiştirmek isteyebilirsiniz. Bunu yapmak için bağdaştırıcının birincil değiştirme `Fill` yöntemi. TableAdapter'ları ile bir ana oluşturulan `Fill` ilişkili veri tablosunun şemasını tanımlayan yöntemi. Ana `Fill` yöntemi sorguya dayalı, veri tablosu altında (üst) ilk yöntem açıktır; veya, girdiğiniz saklı yordamı TableAdapter bağdaştırıcısının özgün olarak yapılandırıldığında [oluşturma ve yazılan veri kümelerini düzenleme](../data-tools/creating-and-editing-typed-datasets.md).  
  
 ![TableAdapter ile birden çok sorgu](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 TableAdapter bağdaştırıcısına yaptığınız tüm değişiklikler ana `Fill` yöntemi ilişkili veri tablosunun şemada yansıtılır. Örneğin, ana sorgudan bir sütun kaldırılması `Fill` yöntemi ilişkili veri tablosundan da sütunu kaldırır. Ayrıca, ana sütunu kaldırmak `Fill` yöntemi herhangi bir ek sorgularından sütunu için TableAdapter kaldırır.  
  
 Kullanabileceğiniz **TableAdapter sorgu Yapılandırma Sihirbazı'nı** oluşturmak ve ek sorgular için TableAdapter'ı düzenlemek için. Sürece bir skalar değer döndürürler bu ek sorgular tablonun şemasına uygun olmalıdır.  Ek sorgular, belirttiğiniz bir ada sahip (örneğin, `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`.)  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Yeni bir sorgu ile TableAdapter sorgu Yapılandırma Sihirbazı'nı başlatmak için  
  
1.  Kümenizde açın **veri kümesi Tasarımcısı**.  
  
2.  Yeni bir sorgu oluşturuyorsanız, sürükleyin bir **sorgu** nesnesinden **veri kümesi** sekmesinde **araç kutusu** üzerine bir <xref:System.Data.DataTable>, ya da seçin **Sorgu Ekle**TableAdapter bağdaştırıcısının kısayol menüsünden. Sürükleyebilirsiniz bir **sorgu** boş bir alanı nesneye **veri kümesi Tasarımcısı**, TableAdapter bağdaştırıcısının ilişkili bir olmadan oluşturan <xref:System.Data.DataTable>. Bu sorgular, tek değerler (sayısal) döndüren veya güncelleştirme, ekleme, çalıştırma sınırlı veya veritabanı komutları SİLİN. Daha fazla bilgi için [nasıl yapılır: bir TableAdapter genel sorgular ekleme](../data-tools/how-to-add-global-queries-to-a-tableadapter.md).  
  
3.  Üzerinde **veri bağlantınızı seçin** sayfa seçin veya sorguyu kullanacağı bir bağlantı oluşturun.  
  
    > [!NOTE]
    >  Bu sayfa tasarımcıyı kullanmak için uygun bağlantı belirleyemediğinde veya bağlantı kullanılabilir olduğunda yalnızca görünür.  
  
4.  Üzerinde **komut türü seçin** sayfasında, verileri veritabanından getirmekten aşağıdaki yöntemleri arasından seçim:  
  
    -   **SQL deyimlerini** veritabanınızdan verileri seçmek için bir SQL deyimi yazabileceğiniz yeri sağlar.  
  
    -   **Yeni saklı yordam oluşturma** — belirtilen SELECT deyimine dayalı yeni bir saklı yordam (veritabanında) Oluşturma Sihirbazı'nı için bu seçeneği belirleyin.  
  
    -   **Mevcut saklı yordamlar kullanma** — varolan bir saklı yordam sorgu çalıştırırken yürütmek için bu seçeneği belirleyin.  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Varolan bir sorguyu temel TableAdapter sorgu Yapılandırma Sihirbazı'nı başlatmak için  
  
-   Varolan bir TableAdapter sorgu düzenliyorsanız, sorguyu sağ tıklatın ve seçin **yapılandırma** kısayol menüsünden.  
  
    > [!NOTE]
    >  TableAdapter bağdaştırıcısının ana sorguda sağ TableAdapter yeniden yapılandırır ve <xref:System.Data.DataTable> şemasını, TableAdapter üzerindeki ek bir sorgu sağ ise yalnızca yapılandırır seçili sorgu. **TableAdapter Yapılandırma Sihirbazı'nı** TableAdapter tanımı yeniden yapılandırır; **TableAdapter sorgu Yapılandırma Sihirbazı'nı** yalnızca seçili sorguyu yeniden yapılandırır.  
  
## <a name="running-the-wizard"></a>Sihirbazı çalıştırma  
 Sorguları üzerine sürükleyin **veri kümesi Tasarımcısı**, veya var olan sorguları (herhangi bir sorgu ilk sorgu listelenen) yapılandırın.  
  
 Bir TableAdapter içinde ilk sorgu, TableAdapter bağdaştırıcısının ana sorgusunda gereklidir. Bu ana sorgu düzenleme açılır **TableAdapter Yapılandırma Sihirbazı'nı** ve TableAdapter bağdaştırıcısının veri tablosunu şemasını düzenler. Tüm sorgular ana sorguda listelenen ek sorgular ve kullanarak yapılandırılmış **TableAdapter sorgu Yapılandırma Sihirbazı'nı**. Sihirbazı çalıştırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: TableAdapter sorgu Yapılandırma Sihirbazı'nı Başlat](http://msdn.microsoft.com/library/fc7b468e-3417-48a4-a8aa-cace8f99c24a).  
  
## <a name="choose-your-data-connection"></a>Veri bağlantınızı seçin  
 Mevcut bir bağlantıyı bağlantılar listesinden seçin veya tıklatın **yeni bağlantı** veritabanına bir bağlantı oluşturmak için.  
  
 Tamamlanmasından sonra **bağlantı özellikleri** iletişim kutusu, **bağlantı ayrıntıları** alanı salt okunur bilgilerini ve seçilen sağlayıcıyı, hem de bağlantı dizesini görüntüler.  
  
## <a name="save-the-connection-string-to-the-application-configuration-file"></a>Bağlantı dizesini uygulama yapılandırma dosyasına kaydet  
 Seçin **Evet, bağlantıyı bu adla Kaydet** bağlantı dizesini uygulama yapılandırma dosyasında saklamak için. Bağlantı için bir ad yazın veya sağlanan varsayılan adı kullanın.  
  
 Uygulama yapılandırma dosyasında bağlantı dizelerini kaydetme veritabanı bağlantısı değişirse uygulamanızı koruma işlemini basitleştirir. Veritabanı bağlantısı bir değişiklik olması durumunda, bağlantı dizesini uygulama yapılandırma dosyasında düzenleyebilirsiniz. Böylece, kaynak kodunu düzenleyin ve uygulamanızı yeniden derlemeniz gerekmez. Uygulama yapılandırma dosyasında bir bağlantı dizesi düzenleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Kaydet ve bağlantı dizeleri düzenleme](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
> [!IMPORTANT]
>  Bilgiler, uygulama yapılandırma dosyasında düz metin olarak depolanır. Hassas bilgilere yetkisiz erişim olasılığını azaltmak için verilerinizi şifrelemek isteyebilirsiniz. Daha fazla bilgi için [şifreleme ve şifre çözme veri](http://msdn.microsoft.com/en-us/22812ae8-e082-4eb1-a29b-21b6ee00c6b5).  
  
## <a name="use-sql-statements"></a>SQL deyimleri kullan  
 Bu bölümde nasıl tamamlanacağını açıklayan **TableAdapter sorgu Yapılandırma Sihirbazı'nı** seçerken **SQL deyimi kullan** seçeneği.  
  
## <a name="choose-a-query-type"></a>Bir sorgu türü seçin  
 Sihirbaz, sorgu, uygulamanızın gereksinimlerine bağlı olarak çeşitli türleri oluşturur. (Bir veri tablosu) veri satırı döndüren SELECT sorgusu seçebilirsiniz veya seçin, dönüş skalar değer sorguları (gibi tek bir değer `Count` veya `Sum`).  
  
 Üzerinde **bir sorgu türü seçin** sayfasında, mevcut sorgular listesinden oluşturmak için sorgu türünü seçin.  
  
> [!NOTE]
>  Bir INSERT, UPDATE veya DELETE deyimi oluşturma, TableAdapter bağdaştırıcısının çağırırken kullanılan TableAdapter bağdaştırıcısının komutlarını değiştirmez `Update` yöntemi. Örneğin, bir sorgu türü güncelleştirme seçerek yeni bir sorgu daha sonra sihirbazda belirttiğiniz adla oluşturur. TableAdapter'ın adlandırılmış bu yöntemi çağırarak, bu sorguyu yürütün. TableAdapter bağdaştırıcısının `Update` yöntemi, özgün TableAdapter yapılandırıldığında oluşturulan deyimleri yürütülecek.  
  
## <a name="specify-a-sql-query-type-statement"></a>Bir SQL belirtin \<sorgu türü > deyimi  
 Üzerinde **bir SQL deyimi belirtin** sayfasında, sorguyu çağırırken yürütmek için SQL deyimi girin.  
  
> [!TIP]
>  Sihirbaz erişim sağlayan **Sorgu Oluşturucu**, SQL sorguları oluşturmak için bir araç. Bunu açmak için **Sorgu Oluşturucu** düğmesi.  
  
## <a name="choose-methods-to-generate"></a>Oluşturulacak metotları seçin  
 Bu sayfa sihirbaz oluşturur, sorgu için hangi yöntemlerin seçmek için seçenekleri sağlar.  
  
 **Bir DataTable Doldur**  
 Veri tablosunu doldurmak için bir yöntem oluşturur. Veri tablosu adı ile döndürülen verileri veri tablosunu doldurmak için bu yöntemi çağrılırken bir parametre olarak geçirirsiniz.  
  
 İsteğe bağlı olarak, varsayılan adı değiştirebilirsiniz **yöntem adı** kutusu. Anlamlı bir ad sağlayarak, bu sorgu kod ile çalışırken yararlı olabilir.  
  
 **Bir DataTable Döndür**  
 Doldurulmuş veri tablosunu döndüren bir yöntem oluşturur. Bazı uygulamalar, mevcut veri tablosu verilerle doldurma aksine doldurulmuş veri tablosu döndürülecek daha tercih edilen olabilir.  
  
 İsteğe bağlı olarak, varsayılan adı değiştirebilirsiniz **yöntem adı** kutusu.  
  
## <a name="choose-function-name"></a>İşlev adı seçin  
 İşlev için bir ad yazın. TableAdapter sorgu oluşturma yöntemi burada belirtilen adla TableAdapter bağdaştırıcısına ekler. Sorguyu yürütmek için bu yöntemi çağırın. Bu sorguda kod ile çalışırken, anlamlı bir ad sağlamayı yararlıdır.  
  
> [!NOTE]
>  Yeni saklı yordam oluşturma, için iki ad istenir. İlk adı veritabanında saklı yordamı adıdır; İkinci Ad yöntemi çağrıldığında saklı yordamı yürüten TableAdapter adıdır.  
  
## <a name="create-new-stored-procedures"></a>Yeni saklı yordamlar oluşturma  
 Bu bölümde nasıl tamamlanacağını açıklayan **TableAdapter sorgu Yapılandırma Sihirbazı'nı** seçerken **yeni saklı yordamlar oluşturma** seçeneği.  
  
1. İçinde **saklı yordamlar üretmesini** sayfasında, saklı yordamı çağrılırken yürütmek için SQL deyimi girin.  
  
   > [!NOTE]
   >  Sihirbaz erişim sağlayan **Sorgu Oluşturucu**, SQL sorguları oluşturmak için bir araç. Bunu açmak için **Sorgu Oluşturucu** düğmesi.  
  
2. İçinde **saklı yordamları oluştur** sayfasında, aşağıdakileri yapın:  
  
   1. Yeni saklı yordam için bir ad yazın.  
  
   2. Temel alınan veritabanında saklı yordamı oluşturulup oluşturulmayacağını belirtin.  
  
      > [!NOTE]
      >  Veritabanında bir saklı yordam oluşturma özelliği, belirli bir veritabanı için güvenlik ayarları tarafından belirlenir.  
  
      **Sihirbazı sonuçlarını görüntüle** sayfası TableAdapter sorgu oluşturma sonuçlarını gösterir. Bu sayfa, Sihirbazı bir sorunla karşılaşırsa, hata bilgilerini sağlar.  
  
## <a name="use-existing-stored-procedures"></a>Mevcut saklı yordamlar kullanma  
 Bu bölümde nasıl tamamlanacağını açıklayan **TableAdapter sorgu Yapılandırma Sihirbazı'nı** seçerken **mevcut saklı yordamlar kullanma** seçeneği.  
  
1.  Aşağı açılan listeden varolan bir saklı yordam seçin **varolan bir saklı yordam seçin** Sihirbazı sayfası.  
  
     **Parametreleri** ve **sonuçları** seçili saklanan yordam görüntülenir için başvuru.  
  
2.  **İleri**'ye tıklayın.  
  
## <a name="choose-the-shape-of-data-returned-by-the-stored-procedure"></a>Saklı yordam tarafından döndürülen verinin şeklini seçin  
 TableAdapter metotları nasıl Sihirbaz seçilen saklı yordam tarafından döndürülen veri türünü belirler.  
  
 Bu sorgu tarafından döndürülen veri türünü seçin.  
  
-   Seçme **tablo veri** açılır **oluşturmak için yöntemlerini seçin** yöntemleri, yöntem adlarını ve disk belleği desteği oluşturulacak türlerini belirtmek olanak tanıyan sayfa (daha önce bu Yardım sayfası üzerinde açıklanmıştır).  
  
-   Seçme **tek bir değer** tek bir değer döndüren türü belirtilmiş bir metot oluşturur. Bu seçenek açılır **işlev adı seçin** sayfa (daha önce bu Yardım sayfası üzerinde açıklanmıştır).  
  
-   Seçme **hiçbir değer** saklı yordamı yürütür ve döndürülecek veri yok bekliyor türü belirtilmiş bir metot oluşturur. Bu seçenek açılır **işlev adı seçin** sayfa (daha önce bu Yardım sayfası üzerinde açıklanmıştır).  
  
## <a name="view-wizards-results"></a>Sihirbazlar sonuçlarını görüntüle  
 **Sihirbazı sonuçlarını görüntüle** sayfası TableAdapter sorgu oluşturma sonuçlarını gösterir. Sihirbazı bir sorunla karşılaşırsa, ayrıntıları bu sayfada görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TableAdapter genel bakış](../data-tools/tableadapter-overview.md)   
 [Nasıl yapılır: TableAdapter sorgularını düzenleme](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Veri izlenecek yollar](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Veri uygulamaları Visual Studio'da genel bakış](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio'da verilere bağlanma](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Uygulamanızı veri almaya hazırlama](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Uygulamanıza veri getirme](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Uygulamanızdaki verileri düzenleme](../data-tools/editing-data-in-your-application.md)   
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Verileri Kaydetme](../data-tools/saving-data.md)