---
title: Veri TableAdapter DBDirect yöntemleri kaydedin. | Microsoft Docs
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
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6b7a7ec1d244f8bf711f0d1aaf4726c910846357
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219724"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>TableAdapter DBDirect metotlarıyla veri kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bu izlenecek yol, bir TableAdapter DBDirect yöntemleri kullanılarak doğrudan veritabanına karşı SQL deyimleri çalıştırmaya yönelik ayrıntılı yönergeler sağlar. Veritabanı güncelleştirmelerinizi denetime ayrıntılı bir düzeyde bir TableAdapter DBDirect yöntemleri sağlar. Bunları ayrı ayrı çağrı yaparak belirli SQL deyimlerini ve depolanan yordamları çalıştırmak için kullanabileceğiniz `Insert`, `Update`, ve `Delete` uygulamanızın ihtiyaç duyduğu gibi yöntemleri (aşırı yüklenmiş'ın aksine `Update` güncelleştirme gerçekleştirir yöntemi INSERT ve DELETE deyimleri bir çağrıda tüm).  
  
 Bu kılavuz boyunca, öğreneceksiniz nasıl yapılır:  
  
-   Yeni bir **Windows uygulama**.  
  
-   Oluşturma ve yapılandırma ile dataset [veri kaynağı Yapılandırma Sihirbazı](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Denetimin formda öğelerinden sürüklendiğinde oluşturulacak seçin **veri kaynakları** penceresi. Daha fazla bilgi için [veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Öğe sürükleyerek veriye bağlı form oluşturma **veri kaynakları** forma penceresi.  
  
-   Doğrudan veritabanına erişmek ve ekleme, güncelleştirme ve silme işlemleri gerçekleştirmek için yöntemler Ekle...  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için şunlar gerekir:  
  
-   Northwind örnek veritabanına erişim. Daha fazla bilgi için [nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-a-windows-application"></a>Bir Windows uygulaması oluşturma  
 İlk adım oluşturmaktır bir **Windows uygulama**.  
  
#### <a name="to-create-the-new-windows-project"></a>Yeni Windows projesi oluşturmak için  
  
1.  Visual Studio'da üzerinde **dosya** menüsünden Yeni bir **proje**.  
  
2.  Projeyi adlandırın **TableAdapterDbDirectMethodsWalkthrough**.  
  
3.  Seçin **Windows uygulama**ve ardından **Tamam**. Daha fazla bilgi için [istemci uygulamaları](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **TableAdapterDbDirectMethodsWalkthrough** projesi oluşturulur ve eklenen **Çözüm Gezgini**.  
  
## <a name="create-a-data-source-from-your-database"></a>Veritabanından bir veri kaynağı oluşturun  
 Bu adımı kullanan **veri kaynağı Yapılandırma Sihirbazı** dayalı bir veri kaynağını oluşturmak için `Region` Northwind örnek veritabanındaki tablo. Bağlantı oluşturmak için Northwind örnek veritabanına erişiminiz olmalıdır. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için  
  
1.  Üzerinde **veri** menüsünde **veri kaynaklarını Göster**.  
  
2.  İçinde **veri kaynakları** penceresinde **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı Yapılandırma Sihirbazı**.  
  
3.  Üzerinde **bir veri kaynağı türü seçin** ekranındayken **veritabanı**ve ardından **sonraki**.  
  
4.  Üzerinde **veri bağlantınızı seçin** ekranında, aşağıdakilerden birini yapın:  
  
    -   Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.  
  
         veya  
  
    -   Seçin **yeni bağlantı** başlatmak için **Bağlantı Ekle/Değiştir** iletişim kutusu.  
  
5.  Veritabanınız parola gerektiriyorsa, hassas verileri eklemek ve ardından seçeneğini **sonraki**.  
  
6.  Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** ekranındayken **sonraki**.  
  
7.  Üzerinde **veritabanı nesnelerinizi seçin** ekranında, **tabloları** düğümü.  
  
8.  Seçin `Region` tablosuna sağ tıklayıp ardından **son**.  
  
     **NorthwindDataSet** projenize eklenir ve `Region` tablo görünür **veri kaynakları** penceresi.  
  
## <a name="addcontrols-to-the-form-to-display-the-data"></a>Verileri görüntülemek için forma Addcontrols  
 Öğe sürükleyerek veriye bağlı denetimler oluşturmak **veri kaynakları** formunuza penceresi.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Windows form üzerinde denetimleri bağlı veri oluşturma  
  
-   Ana sürükleyin **bölge** düğümünden **veri kaynakları** forma penceresi.  
  
     A <xref:System.Windows.Forms.DataGridView> denetim ve araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) Kayıtlarda gezinmek için formda görünür. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [RegionTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.  
  
#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Tek tek TableAdapter DbDirect yöntemleri çağıran düğme eklemek için  
  
1.  Üç sürükleyin <xref:System.Windows.Forms.Button> denetimler **araç kutusu** üzerine **Form1** (aşağıda **RegionDataGridView**).  
  
2.  Aşağıdakileri ayarlayın **adı** ve **metin** her düğmesine özellikleri.  
  
    |Ad|Metin|  
    |----------|----------|  
    |`InsertButton`|**Ekle**|  
    |`UpdateButton`|**Güncelleştir**|  
    |`DeleteButton`|**Delete**|  
  
#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Veritabanına yeni kayıtlar eklemek için kod eklemek için  
  
1.  Seçin **InsertButton** click olayı için olay işleyicisi oluşturmak ve formunuza Kod Düzenleyicisi'nde açın.  
  
2.  Değiştirin `InsertButton_Click` olay işleyicisi aşağıdaki kod ile:  
  
     [!code-csharp[VbRaddataSaving#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#1)]
     [!code-vb[VbRaddataSaving#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#1)]  
  
#### <a name="to-add-code-to-update-records-in-the-database"></a>Veritabanındaki kayıtları güncelleştirmek için kod eklemek için  
  
1.  Çift **UpdateButton** click olayı için olay işleyicisi oluşturmak ve formunuza Kod Düzenleyicisi'nde açın.  
  
2.  Değiştirin `UpdateButton_Click` olay işleyicisi aşağıdaki kod ile:  
  
     [!code-csharp[VbRaddataSaving#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#2)]
     [!code-vb[VbRaddataSaving#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#2)]  
  
#### <a name="to-add-code-to-delete-records-from-the-database"></a>Kayıtlarını veritabanından silmek için kod eklemek için  
  
1.  Seçin **DeleteButton** click olayı için olay işleyicisi oluşturmak ve formunuza Kod Düzenleyicisi'nde açın.  
  
2.  Değiştirin `DeleteButton_Click` olay işleyicisi aşağıdaki kod ile:  
  
     [!code-csharp[VbRaddataSaving#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#3)]
     [!code-vb[VbRaddataSaving#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#3)]  
  
## <a name="run-the-application"></a>Uygulamayı çalıştırın  
  
#### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için  
  
-   Seçin **F5** uygulamayı çalıştırın.  
  
-   Seçin **Ekle** düğmesini ve yeni kayıt kılavuzda göründüğünü doğrulayın.  
  
-   Seçin **güncelleştirme** düğmesini ve kayıt kılavuzda güncelleştirildiğini doğrulayın.  
  
-   Seçin **Sil** düğmesini ve kayıt kılavuzdan kaldırıldığını doğrulayın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Uygulama gereksinimlerinize bağlı olarak, veri bağlama form oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bu izlenecek yolda yapabileceğiniz bazı geliştirmeler şunlardır:  
  
-   Forma arama işlevselliği ekleme. Daha fazla bilgi için [nasıl yapılır: bir Windows Forms uygulamasına parametreli bir sorgu ekleme](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
-   Seçerek veri kümesine ek tablolar ilave **veri kümesini Yapılandırma Sihirbazı ile** içinden **veri kaynakları** penceresi. İlgili düğümlerin form üzerine sürükleyerek ilgili verileri görüntüleyen denetimler ekleyebilirsiniz. Daha fazla bilgi için [nasıl yapılır: Windows Forms uygulamasında görüntü ilgili verileri](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)

