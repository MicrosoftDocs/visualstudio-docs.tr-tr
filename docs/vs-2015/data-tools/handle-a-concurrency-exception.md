---
title: Bir eşzamanlılık özel durumunu işleme | Microsoft Docs
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
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a3141f2480aabc2ce6aa7b10f99991fc5cba0d05
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220423"
---
# <a name="handle-a-concurrency-exception"></a>Bir eşzamanlılık özel durumunu işleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Eşzamanlılık özel durumları (<xref:System.Data.DBConcurrencyException>) iki kullanıcı, bir veritabanında aynı verileri aynı anda değiştirme girişiminde oluşturulur. Bu kılavuzda, catch gösterilmektedir bir Windows uygulaması oluşturma bir <xref:System.Data.DBConcurrencyException>hataya neden satırı bulun ve nasıl işleyeceğini bir stratejisi öğrenin.  
  
 Bu izlenecek yol aşağıdaki süreci alır:  
  
1.  Yeni bir **Windows uygulama** proje.  
  
2.  Northwind üzerinde dayalı yeni bir veri kümesi oluşturma `Customers` tablo.  
  
3.  Bir formla oluşturma bir <xref:System.Windows.Forms.DataGridView> verileri görüntülemek için.  
  
4.  Bir veri kümesini verilerle doldurmak `Customers` Northwind veritabanındaki tablo.  
  
5.  Kullanım [Visual veritabanı araçları](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1) doğrudan erişmek için Visual Studio'da `Customers` veri tablosu ve bir kaydı değiştirin.  
  
6.  Aynı kaydı başka bir değerle değiştirmek, veri kümesini güncelleştirin ve değişiklikleri gerçekleştirilen bir eşzamanlılık hatası sonuçları veritabanına yazma girişimi.  
  
7.  Hata catch ve ardından devam etmek ve veritabanını güncellemek için veya güncelleştirmeyi iptal etmek için karar vermek kullanıcıya kayıt farklı sürümlerini görüntüler.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için şunlar gerekir:  
  
-   Güncelleştirmeleri gerçekleştirmek için izne sahip Northwind örnek veritabanına erişim. Daha fazla bilgi için [nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md).  
  
> [!NOTE]
>  İletişim kutuları ve menü komutları gördüğünüz Yardım menüsünde açıklanana etkin ayarlarınıza ve kullandığınız sürüm bağlı olarak farklı olabilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-new-project"></a>Yeni bir proje oluşturma  
 İzlenecek yol, yeni bir Windows uygulaması oluşturarak başlayın.  
  
#### <a name="to-create-a-new-windows-application-project"></a>Yeni bir Windows uygulaması projesi oluşturmak için  
  
1.  Üzerinde **dosya** menüsünden Yeni bir proje oluşturun.  
  
2.  İçinde **proje türleri** bölmesinde bir programlama dili seçin.  
  
3.  İçinde **şablonları** bölmesinde **Windows uygulama**.  
  
4.  Projeyi adlandırın `ConcurrencyWalkthrough`ve ardından **Tamam**.  
  
     Visual Studio projeyi ekler **Çözüm Gezgini** ve tasarımcıda yeni bir form görüntüler.  
  
## <a name="create-the-northwind-dataset"></a>Northwind veri kümesi oluşturma  
 Bu bölümde, adlı bir veri kümesi oluşturma `NorthwindDataSet`.  
  
#### <a name="to-create-the-northwinddataset"></a>NorthwindDataSet oluşturmak için  
  
1.  Üzerinde **veri** menüsünde seçin **ekleme yeni veri kaynağı**.  
  
     [Veri kaynağı Yapılandırma Sihirbazı](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) açılır.  
  
2.  Üzerinde **bir veri kaynağı türü seçin**ekranındayken **veritabanı**.  
  
3.  Bir bağlantı, Northwind örnek veritabanına kullanılabilir bağlantılar listesinden seçin. Bağlantı bağlantılar listesinde kullanılabilir durumda değilse, seçin**yeni bağlantı**  
  
    > [!NOTE]
    >  Bir yerel veritabanı dosyasına bağlanıyorsanız seçin **Hayır** sorulduğunda isterseniz ister dosyayı projenize ekleyin.  
  
4.  Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet**ekranındayken **sonraki**.  
  
5.  Genişletin **tabloları** düğümünü seçip alt `Customers` tablo. Veri kümesi için varsayılan adı olması gereken `NorthwindDataSet`.  
  
6.  Seçin **son** veri kümesini projeye eklenecek.  
  
## <a name="create-a-data-bound-datagridview-control"></a>DataGridView denetimine veri bağlama oluşturun  
 Bu bölümde, oluşturduğunuz bir <xref:System.Windows.Forms.DataGridView> sürükleyerek **müşteriler** öğesini **veri kaynakları** Windows formunuza penceresi.  
  
#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Müşteriler tablosu için bağlı bir DataGridView denetimi oluşturmak için  
  
1.  Üzerinde **veri** menüsünde seçin **veri kaynaklarını Göster** açmak için **veri kaynakları penceresi**.  
  
2.  İçinde **veri kaynakları** penceresini genişletin **NorthwindDataSet** düğümüne tıklayın ve ardından **müşteriler** tablo.  
  
3.  Tablo düğümü aşağı oku seçip ardından **DataGridView** aşağı açılan listesinde.  
  
4.  Tablo boş bir alana formunuzu sürükleyin.  
  
     A <xref:System.Windows.Forms.DataGridView> adlı Denetim `CustomersDataGridView` ve <xref:System.Windows.Forms.BindingNavigator> adlı `CustomersBindingNavigator` bağlı forma eklenen <xref:System.Windows.Forms.BindingSource>. Bu, kullanıma bağlı `Customers` tablosundaki `NorthwindDataSet`.  
  
## <a name="test-the-form"></a>Form test  
 Artık bu noktaya kadar beklendiği gibi davrandığından emin olmak için form test edebilirsiniz.  
  
#### <a name="to-test-the-form"></a>Formu sınamak için  
  
1.  Seçin **F5** uygulamayı çalıştırmak için  
  
     Form görünür bir <xref:System.Windows.Forms.DataGridView> verilerle doldurulmuş denetim üzerindeki `Customers` tablo.  
  
2.  Üzerinde **hata ayıklama** menüsünde**hata ayıklamayı Durdur**.  
  
## <a name="handleconcurrency-errors"></a>Handleconcurrency hataları  
 Hataların nasıl işleneceğini olduğundan uygulamanız yöneten belirli iş kurallarına bağlıdır. Bu kılavuz için aşağıdaki stratejisi örnek için nasıl kullanıyoruz işlemek eşzamanlılık hatası.  
  
 Kullanıcı kaydı üç sürümleriyle applicationpresents:  
  
- Veritabanı geçerli kayıt  
  
- Veri kümesine yüklenmesidir özgün kaydı  
  
- Önerilen değişikliklerin veri kümesi  
  
  Kullanıcı daha sonra önerilen sürümü, veritabanı üzerine veya güncelleştirmeyi iptal eder ve yeni değerlerle veritabanından veri kümelerini yenileme mümkün değil.  
  
#### <a name="to-enable-the-handling-of-concurrency-errors"></a>Eşzamanlılık hata işlemesini etkinleştirmek için  
  
1.  Özel hata işleyicisi oluşturun.  
  
2.  Kullanıcı için seçenekleri görüntüler.  
  
3.  Kullanıcının yanıt işler.  
  
4.  Güncelleştirmenin yeniden ya da veri kümesindeki verileri sıfırlayın.  
  
### <a name="addcode-to-handle-the-concurrency-exception"></a>Eşzamanlılık özel durumu işlemek üzere Addcode  
 Bir güncelleştirme gerçekleştirmeyi denedi ve bir özel durum, genellikle özel durumu tarafından sağlanan bilgilerle bir şey yapmak istersiniz.  
  
 Bu bölümde, veritabanını güncellemek için çalışan kod ekleyin. Tüm de ele <xref:System.Data.DBConcurrencyException> , yükseltilmiş, yanı sıra diğer tüm özel durumlar.  
  
> [!NOTE]
>  `CreateMessage` Ve `ProcessDialogResults` yöntemi bu izlenecek yolda eklenir.  
  
##### <a name="to-add-error-handling-for-the-concurrency-error"></a>Hata işleme için eşzamanlılık hatası eklemek için  
  
1.  Aşağıdaki kodu ekleyin `Form1_Load` yöntemi:  
  
     [!code-csharp[VbRaddataConcurrency#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#1)]
     [!code-vb[VbRaddataConcurrency#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#1)]  
  
2.  Değiştirin `CustomersBindingNavigatorSaveItem_Click` çağrılacak yöntem `UpdateDatabase` yöntemi aşağıdaki gibi görünür:  
  
     [!code-csharp[VbRaddataConcurrency#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#2)]
     [!code-vb[VbRaddataConcurrency#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#2)]  
  
### <a name="displaychoices-to-the-user"></a>Kullanıcıya Displaychoices  
 Yeni kod yazdığınız çağrıları `CreateMessage` kullanıcıya hata bilgilerini görüntülemek için yordamı. Bu kılavuz için kaydın farklı sürümlerine kullanıcıya görüntülenecek bir ileti kutusu kullanın. Bu, kullanıcının kaydı değişikliklerle değiştirmek ya da düzenlemeyi iptal etmek isteyip istemediğinizi seçin sağlar. Kullanıcı ileti kutusunda (bir düğmeye tıkladığında) seçeneği seçtikten sonra yanıt geçirilen `ProcessDialogResult` yöntemi.  
  
##### <a name="to-create-the-message-to-display-to-the-user"></a>Kullanıcıya görüntülenecek iletiyi oluşturmak için  
  
-   Aşağıdaki kodu ekleyerek iletiyi oluşturmak **Kod Düzenleyicisi**. Bu aşağıdaki kodu girin `UpdateDatabase` yöntemi.  
  
     [!code-csharp[VbRaddataConcurrency#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#4)]
     [!code-vb[VbRaddataConcurrency#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#4)]  
  
### <a name="process-the-users-response"></a>Kullanıcının yanıt işleme  
 İleti kutusunda kullanıcının yanıta işlemek için kod da gerekir. Önerilen değişiklik, veritabanındaki geçerli kaydın üzerine veya yerel değişiklikleri iptal ve yenilemek veri tablosu veritabanında şu anda var olan kayıtla seçeneklerdir. Evet, kullanıcı seçerse <xref:System.Data.DataTable.Merge%2A> yöntemi çağrıldığında *preserveChanges* değişkenini `true`. Bu, kaydın orijinal sürümünü artık veritabanında kayıt eşleştiği için başarılı olması güncelleştirme girişimi neden olur.  
  
##### <a name="to-process-the-user-input-from-the-message-box"></a>Kullanıcı işlenecek ileti kutusunda giriş  
  
-   Önceki bölümde eklenen kodun altına aşağıdaki kodu ekleyin.  
  
     [!code-csharp[VbRaddataConcurrency#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#3)]
     [!code-vb[VbRaddataConcurrency#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#3)]  
  
## <a name="test-the-form"></a>Form test  
 Şimdi beklendiği gibi davrandığından emin olmak için form test edebilirsiniz. Bir eşzamanlılık ihlali benzetimini yapmak için NorthwindDataSet doldurduktan sonra veritabanındaki verileri değiştirmeniz gerekir.  
  
#### <a name="to-test-the-form"></a>Formu sınamak için  
  
1.  Seçin **F5** uygulamayı çalıştırın.  
  
2.  Form göründükten sonra çalışan bırakın ve geçiş yapmak için Visual Studio IDE.  
  
3.  Üzerinde **görünümü** menüsünde seçin **Sunucu Gezgini**.  
  
4.  İçinde **Sunucu Gezgini**, uygulamanızı kullanma ve ardından bağlantıyı genişletin **tabloları** düğümü.  
  
5.  Sağ **müşteriler** tablosuna sağ tıklayıp ardından **tablo verilerini Göster**.  
  
6.  İlk kayda (`ALFKI`) değiştirmek `ContactName` için `Maria Anders2`.  
  
    > [!NOTE]
    >  Değişikliği kaydetmek için farklı bir satıra gidin.  
  
7.  Geçiş `ConcurrencyWalkthrough`form çalıştıran kullanıcının.  
  
8.  Formdaki ilk kayda (`ALFKI`), değiştirme`ContactName` için `Maria Anders1`.  
  
9. Seçin **Kaydet** düğmesi.  
  
     Eşzamanlılık hatası tetiklenir ve ileti kutusu görünür.  
  
10. Seçme **Hayır** güncelleştirmeyi iptal eder ve veri kümesini veritabanında şu anda değerlerini güncelleştirir. Seçme **Evet** önerilen değeri veritabanına yazar.
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)