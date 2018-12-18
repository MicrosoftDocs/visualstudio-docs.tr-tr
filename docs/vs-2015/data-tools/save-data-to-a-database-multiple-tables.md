---
title: Verileri bir veritabanına (birden çok tablo) kaydetme | Microsoft Docs
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
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 986df2d58c9a8955c9de9b45edaa5276b2e68bfb
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50218434"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Bir veritabanına (birden çok tablo) veri kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Uygulama geliştirmede en sık karşılaşılan senaryolardan biri, bir Windows uygulamasındaki bir formdaki verileri görüntülemek, verileri düzenleme ve güncelleştirilmiş veriyi veritabanına geri gönder sağlamaktır. Bu izlenecek yolda kayıtlarını düzenleyin ve değişiklikleri veritabanına geri kaydedin gösterir ve ilgili iki tablodan verileri görüntüleyen bir form oluşturur. Bu örnekte `Customers` ve `Orders` Northwind örnek veritabanındaki tablolar.  
  
 Çağırarak veritabanına uygulamanızdaki verileri kaydedebilirsiniz `Update` TableAdapter bağdaştırıcısının yöntemi. Tablodan sürüklediğinizde **veri kaynakları** forma, verileri kaydetmek için gereken kod penceresi otomatik olarak eklenir. Bir forma eklenmiş herhangi bir ek tablolar bu kodu el ile eklenmesi gerekir. Bu izlenecek yol, birden fazla tablodan güncelleştirmeleri kaydetmek için kod ekleme işlemi gösterilmektedir.  
  
> [!NOTE]
>  İletişim kutuları ve menü komutları gördüğünüz Yardım menüsünde açıklanana etkin ayarlarınıza ve kullandığınız sürüm bağlı olarak farklı olabilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:  
  
-   Yeni bir oluşturma **Windows uygulama** proje.  
  
-   Oluşturma ve bir veri kaynağı ile uygulamanızda yapılandırma [veri kaynağı Yapılandırma Sihirbazı](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Ayarı'ndeki öğelerin kullanımını denetler [veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992). Daha fazla bilgi için [veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Öğe sürükleyerek veriye bağlı denetimler oluşturma **veri kaynakları** formunuza penceresi.  
  
-   Birkaç kayıt kümesindeki her bir tablodaki değiştirme.  
  
-   Güncelleştirilmiş veri kümesinde veritabanına geri göndermek için kod değiştirme.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için şunlar gerekir:  
  
-   Northwind örnek veritabanına erişim.  Daha fazla bilgi için [nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-the-windows-application"></a>Windows uygulaması oluşturma  
 İlk adım oluşturmaktır bir **Windows uygulama**. Projeye bir ad atamak Bu adımda isteğe bağlıdır, ancak daha sonra kaydetmeyi planlıyoruz çünkü biz bunu bir ad verin.  
  
#### <a name="to-create-the-new-windows-application-project"></a>Yeni bir Windows uygulaması projesi oluşturmak için  
  
1.  Üzerinde **dosya** menüsünden Yeni bir proje oluşturun.  
  
2.  Projeyi adlandırın `UpdateMultipleTablesWalkthrough`.  
  
3.  Seçin **Windows uygulama**ve ardından **Tamam**. Daha fazla bilgi için [istemci uygulamaları](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **UpdateMultipleTablesWalkthrough** projesi oluşturulur ve eklenen **Çözüm Gezgini**.  
  
## <a name="create-the-data-source"></a>Veri kaynağı oluşturma  
 Bu adımı kullanarak Northwind veritabanına bir veri kaynağı oluşturur. **veri kaynağı Yapılandırma Sihirbazı**. Bağlantı oluşturmak için Northwind örnek veritabanına erişiminiz olmalıdır. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için  
  
1.  Üzerinde **veri** menüsünde**veri kaynaklarını Göster**.  
  
2.  İçinde **veri kaynakları** penceresinde**yeni veri kaynağı Ekle** başlatmak için **veri kaynağı Yapılandırma Sihirbazı**.  
  
3.  Üzerinde **bir veri kaynağı türü seçin**ekranındayken **veritabanı**ve ardından **sonraki**.  
  
4.  Üzerinde **veri bağlantınızı seçin**aşağıdakilerden birini ekran yapın:  
  
    -   Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.  
  
         veya  
  
    -   Seçin **yeni bağlantı** açmak için **Bağlantı Ekle/Değiştir** iletişim kutusu.  
  
5.  Veritabanınız parola gerektiriyorsa, hassas verileri eklemek ve ardından seçeneğini **sonraki**.  
  
6.  Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet**seçin **sonraki**.  
  
7.  Üzerinde **veritabanı nesnelerinizi seçin**ekranında, **tabloları** düğümü.  
  
8.  Seçin **müşteriler** ve **siparişler** tablolar ve ardından **son**.  
  
     **NorthwindDataSet** projenize eklenir ve tablolar görünür **veri kaynakları** penceresi.  
  
## <a name="set-the-controls-to-be-created"></a>Oluşturulacak denetimleri ayarlayın  
 Bu izlenecek yolda, verileri için `Customers` tablo bir **ayrıntıları** veri görüntüleyen her denetim düzeni. Verilerden `Orders` tablo bir **kılavuz** görüntülenen düzeni bir <xref:System.Windows.Forms.DataGridView> denetimi.  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Veri kaynakları Penceresi'nde öğelerin bırakma türünü ayarlama  
  
1.  İçinde **veri kaynakları** penceresini genişletin **müşteriler** düğümü.  
  
2.  Üzerinde **müşteriler** düğümünü **ayrıntıları** denetimi değiştirmek için Denetim listesinden **müşteriler** tek denetimleri için tablo. Daha fazla bilgi için [veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## <a name="create-the-data-bound-form"></a>Verilere bağlı formu oluşturma  
 Öğe sürükleyerek veriye bağlı denetimler oluşturabilirsiniz **veri kaynakları** formunuza penceresi.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Form üzerinde veri bağlama denetimleri oluşturmak için  
  
1.  Ana sürükleyin **müşteriler** düğümünden **veri kaynakları** penceresinden **Form1**.  
  
     Araç şeridi yanı sıra form üzerindeki verilere bağlı denetimler, tanımlayıcı etiketlerle görünür (<xref:System.Windows.Forms.BindingNavigator>) Kayıtlarda gezinmek için. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.  
  
2.  İlgili sürükleyin **siparişler** düğümünden **veri kaynakları** penceresinden **Form1**.  
  
    > [!NOTE]
    >  İlgili **siparişler** düğümü altında bulunan **faks** sütun ve bir alt düğüm **müşteriler** düğümü.  
  
     A <xref:System.Windows.Forms.DataGridView> denetim ve araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) Kayıtlarda gezinmek için formda görünür. Bir [orderstableadapter bağdaştırıcısına](../data-tools/tableadapter-overview.md) ve <xref:System.Windows.Forms.BindingSource> bileşen tepsisinde görünür.  
  
## <a name="addcode-to-update-the-database"></a>Veritabanını güncellemek için Addcode  
 Çağırarak veritabanı güncelleştirebilirsiniz `Update` yöntemlerinin **müşteriler** ve **siparişler** TableAdapter bağdaştırıcıları. Varsayılan olarak, bir olay işleyicisi için **Kaydet** düğmesini<xref:System.Windows.Forms.BindingNavigator> veritabanına güncelleştirmeleri göndermek için formun koduna eklenir. Bu yordamı doğru sırayla güncelleştirmeleri göndermek için kod değiştirir. Bu bilgi tutarlılığını hataları oluşturma olanağına ortadan kaldırır. Kod ayrıca hata güncelleştirme çağrısında bir try-catch bloğu içinde sarmalama tarafından işleme uygular. Kod, uygulamanızın ihtiyaçlarına uyacak şekilde değiştirebilirsiniz.  
  
> [!NOTE]
>  Anlaşılsın diye, bu izlenecek yol, bir işlem kullanmaz. Ancak, iki güncelleştirilmiyor ya da tabloları ilgili daha fazla işlem içindeki tüm güncelleştirme mantığı içerir. Bir işlem değişiklikleri uygulanmadan önce bir veritabanındaki tüm ilgili değişiklikler başarılı olduğunu garantiler bir işlemdir. Daha fazla bilgi için [işlemler ve eşzamanlılık](http://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).  
  
#### <a name="to-add-update-logic-to-the-application"></a>Uygulama güncelleştirme mantığı eklemek için  
  
1.  Seçin **Kaydet** düğmesini <xref:System.Windows.Forms.BindingNavigator>. Kod Düzenleyicisi açılır `bindingNavigatorSaveItem_Click` olay işleyicisi.  
  
2.  Çağrılacak olay işleyicisinde kodu değiştirin `Update` ilgili TableAdapter yöntemleri. Aşağıdaki kod önce her kullanıcının güncelleştirilmiş bilgilerini tutmak için üç geçici veri tabloları oluşturur <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, ve <xref:System.Data.DataRowState>). Ardından güncelleştirmeleri doğru sırayla çalıştırılır. Kod aşağıdaki gibi görünmelidir:  
  
     [!code-csharp[VbRaddataSaving#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form4.cs#10)]
     [!code-vb[VbRaddataSaving#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form4.vb#10)]  
  
## <a name="test-the-application"></a>Uygulamayı test etme  
  
#### <a name="to-test-the-application"></a>Uygulamayı test etmek için  
  
1.  Seçin **F5**.  
  
2.  Veriler her tabloda bir veya daha fazla kayıt için birkaç değişiklik yapalım.  
  
3.  Seçin **Kaydet** düğmesi.  
  
4.  Değişiklikler kaydedildi doğrulamak için veritabanında değerleri kontrol edin.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Uygulama gereksinimlerinize bağlı olarak, Windows uygulamanıza veriye bağlı form oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bu izlenecek yolda yapabileceğiniz bazı geliştirmeler şunlardır:  
  
-   Forma arama işlevselliği ekleme. Daha fazla bilgi için [nasıl yapılır: bir Windows Forms uygulamasına parametreli bir sorgu ekleme](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
-   Veri kaynağı eklemek veya veritabanı nesnelerini kaldırmak için düzenleme. Daha fazla bilgi için [nasıl yapılır: bir veri kümesini düzenleme](http://msdn.microsoft.com/library/f2dade5f-9c7a-4ddb-96a8-e0a39e50bfd3).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)

