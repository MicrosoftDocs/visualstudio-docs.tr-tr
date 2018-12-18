---
title: Tableadapter'lar oluşturma ve yapılandırma | Microsoft Docs
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
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 03cb6c67b4887762885a0cb920eb928359b4708b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917654"
---
# <a name="create-and-configure-tableadapters"></a>TableAdapter’lar oluşturma ve yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
TableAdapter, uygulamanızla veritabanı arasındaki iletişimi sağlar. Veritabanı, çalışma sorguları veya saklı yordamları bağlanmak ve ya da yeni bir veri döndürmeyen tablo veya mevcut bir dolgu <xref:System.Data.DataTable> döndürülen verilerle. TableAdapter ayrıca uygulamanızdan veritabanına güncelleştirilmiş veriler gönderebilirsiniz.  
  
 Aşağıdaki eylemlerden birini gerçekleştirdiğinizde TableAdapters sizin için oluşturulur:  
  
- Çalıştırma [veri kaynağı Yapılandırma Sihirbazı](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) seçin ya da **veritabanı** veya **Web hizmeti** veri kaynağı türü.  
  
- Veritabanı nesneleri sürükleyin [Sunucu Gezgini](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) içine **veri kümesi Tasarımcısı**.  
  
  Yeni bir TableAdapter oluşturmak ve boş bir bölge için araç kutusundan bir TableAdapter sürükleyerek bir veri kaynağı ile yapılandırma **veri kümesi Tasarımcısı** yüzeyi.  
  
  TableAdapter bağdaştırıcıları için bir giriş için bkz [TableAdapter kullanarak veri kümelerini dolgu](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="use-the-tableadapter-configuration-wizard"></a>TableAdapter Yapılandırma Sihirbazı'nı kullanma  
 Çalıştırma **TableAdapter Yapılandırma Sihirbazı'nı** oluşturmak veya TableAdapter'ları ve bunların ilişkili DataTable düzenlemek için. Mevcut bir TableAdapter içinde sağ tıklayarak yapılandırabileceğiniz **veri kümesi Tasarımcısı**.  
  
 ![Tablo bağdaştırıcısı Yapılandırma Sihirbazı'nı raddata](../data-tools/media/raddata-table-adapter-configuration-wizard.png "raddata tablo bağdaştırıcısı Yapılandırma Sihirbazı")  
  
 Araç kutusundan yeni bir TableAdapter sürüklerseniz, **veri kümesi Tasarımcısı** odağı, TableAdapter bağlanmak için veri kaynağını belirtmek için ve ne tür komutlarını kullanması gereken ile iletişim kurmak için sihirbaz yönergelerini yer Veritabanı, SQL deyimlerinin veya saklı yordamlar. Zaten bir veri kaynağı ile ilişkili olan bir TableAdapter yapılandırıyorsanız bu görmezsiniz.  
  
-   Kullanarak **güncelleştirmeleri doğrudan veritabanına göndermek için metotlar Oluştur** seçeneği ayarını eşdeğerdir `GenerateDBDirectMethods` özelliği true. Özgün SQL deyimi yeterli bilgi sağlamaz veya sorgu güncelleştirilebilen bir sorgu değil seçeneği kullanılamaz. Bu durum, örneğin, içinde ortaya çıkabilir **katılın** sorgular ve tek bir (sayı) değerini döndüren sorgular.  
  
-   Veritabanı için doğru izinlere sahip değilse temel alınan veritabanında yeni bir saklı yordam oluşturmak için bu seçeneği var. Bu izinlere sahip değilseniz, bu seçeneği olmayacaktır.  
  
-   İçin mevcut saklı yordamları çalıştırmak de seçebilirsiniz **seçin**, **Ekle**, **güncelleştirme**, ve **Sil** komutları TableAdapter. Atanan saklı yordamı **güncelleştirme** komutu, örneğin, çalıştığı zaman `TableAdapter.Update()` yöntemi çağrılır.  
  
     Seçilen saklı yordamın parametreleri veri tablosunda karşılık gelen sütunlara eşleyin. Örneğin, depolanmış yordamınızdaki adlı bir parametre kabul eder `@CompanyName` için geçen `CompanyName` tablodaki sütun kümesini **kaynak sütunu** , `@CompanyName` parametresi `CompanyName`.  
  
    > [!NOTE]
    >  SELECT komutu için atanan saklı yordamı, sihirbazın bir sonraki adımda isimlendirdiğiniz TableAdapter'ın yöntemi çağrılarak çalıştırılır. İçin varsayılan yöntemdir `Fill`, genellikle SELECT yordamı çalıştırmak için kullanılan kod, bu nedenle `TableAdapter.Fill(tableName)`. Varsayılan adı değiştirirseniz `Fill`, yedek `Fill` adıyla atayın ve "TableAdapter" TableAdapter'ın gerçek adıyla değiştirin (örneğin, `CustomersTableAdapter`).  
  
-   **Gelişmiş Seçenekler** sihirbazda göre tanımlanan bir SELECT deyimi INSERT, UPDATE ve DELETE deyimleri oluşturmasını sağlayan **oluşturmak SQL deyimleri** sayfası. İyimser eşzamanlılığı kullanın ve sonra INSERT ve UPDATE veri tablosunu yenilemek için deyimleri çalıştırılıp çalıştırılmayacağını belirtin.  
  
## <a name="configure-a-tableadapters-fill-method"></a>TableAdapter bağdaştırıcısının dolgu yöntemini yapılandırma  
 Bazen TableAdapter bağdaştırıcısının tablo şemasını değiştirmek isteyebilirsiniz. Bunu yapmak için TableAdapter bağdaştırıcısının birincil değiştirme `Fill` yöntemi. TableAdapter'ları ile birincil oluşturulan `Fill` ilişkili veri tablosunun şemasını tanımlayan yöntemi. Birincil `Fill` yöntemi sorgu veya saklı yordamı TableAdapter bağdaştırıcısının özgün yapılandırmasında, girdiğiniz dayanır. Veri tablosu veri kümesi Tasarımcısı'nda ilk (en üstte) yöntem var.  
  
 ![TableAdapter ile birden çok sorgu](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 TableAdapter bağdaştırıcısına yaptığınız tüm değişiklikler ana `Fill` yöntemi ilişkili veri tablosunun şemada yansıtılır. Örneğin, ana sorgudan bir sütun kaldırılması `Fill` yöntemi ilişkili veri tablosundan da sütunu kaldırır. Ayrıca, ana sütunu kaldırmak `Fill` yöntemi herhangi bir ek sorgularından sütunu için TableAdapter kaldırır.  
  
 Oluşturun ve ek sorgular için TableAdapter'ı düzenlemek için TableAdapter sorgu Yapılandırma Sihirbazı'nı kullanabilirsiniz. Sürece bir skalar değer döndürürler bu ek sorgular tablonun şemasına uygun olmalıdır.  Ek sorgular, belirttiğiniz bir adlara sahip (örneğin, `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`.)  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Yeni bir sorgu ile TableAdapter sorgu Yapılandırma Sihirbazı'nı başlatmak için  
  
1.  Kümenizde açın **veri kümesi Tasarımcısı**.  
  
2.  Yeni bir sorgu oluşturuyorsanız, sürükleyin bir **sorgu** nesnesinden **veri kümesi** sekmesinde **araç kutusu** üzerine bir <xref:System.Data.DataTable>, ya da seçin **Sorgu Ekle**TableAdapter bağdaştırıcısının kısayol menüsünden. Sürükleyebilirsiniz bir **sorgu** boş bir alanı nesneye **veri kümesi Tasarımcısı**, TableAdapter bağdaştırıcısının ilişkili bir olmadan oluşturan <xref:System.Data.DataTable>. Bu sorgular yalnızca tek (skaler) değerler ya da çalışma güncelleştirme, ekleme, döndürür veya veritabanı komutları SİLEBİLİRSİNİZ.  
  
3.  Üzerinde **veri bağlantınızı seçin** ekran, seçin veya sorguyu bir bağlantı oluşturun.  
  
    > [!NOTE]
    >  Bu ekran Tasarımcısı'nı kullanmak için uygun bağlantı belirleyemediğinde veya bağlantı kullanılabilir olduğunda yalnızca görünür.  
  
4.  Üzerinde **komut türü seçin** ekranında, verileri veritabanından getirmekten aşağıdaki yöntemleri arasından seçim:  
  
    -   **SQL deyimlerini** veritabanınızdan verileri seçmek için bir SQL deyimi yazabileceğiniz yeri sağlar.  
  
    -   **Yeni saklı yordam oluşturma** etkinleştirir, sihirbaz için oluşturduğunuz yeni bir saklı yordam'ı (veritabanında) belirtilen SELECT deyiminde göre.  
  
    -   **Mevcut saklı yordamlar kullanma** , varolan bir saklı yordam sorgu çalıştırırken çalıştırmanızı sağlar.  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Varolan bir sorguyu temel TableAdapter sorgu Yapılandırma Sihirbazı'nı başlatmak için  
  
-   Varolan bir TableAdapter sorgu düzenliyorsanız, sorguyu sağ tıklayın ve ardından **yapılandırma** kısayol menüsünden.  
  
    > [!NOTE]
    >  TableAdapter bağdaştırıcısının ana sorguda sağ TableAdapter yeniden yapılandırır ve <xref:System.Data.DataTable> şema. Bir TableAdapter üzerindeki ek bir sorgu sağ tıklayarak, ancak yalnızca seçilen sorgu yapılandırır. **TableAdapter Yapılandırma Sihirbazı'nı** TableAdapter sorgu Yapılandırma Sihirbazı'nı yalnızca seçili sorguyu yeniden yapılandırır. ancak TableAdapter tanımının yeniden yapılandırır.  
  
#### <a name="to-add-a-global--query-to-a-tableadapter"></a>Bir TableAdapter için genel bir sorgu eklemek için  
  
-   *Genel sorgular* tek bir (sayı) değerini veya herhangi bir değer döndüren SQL sorguları. Genellikle, ekleme, güncelleştirme siler gibi genel işlevleri veritabanı işlemleri gerçekleştirin. Bunlar ayrıca bir tablo ya da belirli bir sırada tüm öğeler için Toplam ücret müşterilerin sayısını gibi bilgileri toplayın.  
  
     Sürükleyerek genel sorgular ekleme bir **sorgu** nesnesinden **veri kümesi** sekmesinde **araç kutusu** boş bir alanı üzerine **veri kümesi Tasarımcısı**.  
  
-   Örneğin, istenen bir görevi gerçekleştiren bir sorgu sağlamanız `SELECT COUNT(*) AS CustomerCount FROM Customers`.  
  
    > [!NOTE]
    >  Sürükleyerek bir **sorgu** doğrudan nesne **veri kümesi Tasarımcısı** yalnızca skaler (tek) değer döndüren bir yöntem oluşturur. Sorgu veya saklı yordam seçtiğiniz birden çok tek bir değer döndürebilir sırasında sihirbaz tarafından oluşturulan yöntemi yalnızca tek bir değer döndürür. Örneğin, sorgu döndürülen verileri ilk satırının ilk sütununu döndürebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)

