---
title: Bir işlemde veri kaydetme | Microsoft Docs
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
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b0912ffbe2a9a82ac5efbd3b2ca6ba3566ce5b02
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219308"
---
# <a name="save-data-in-a-transaction"></a>Bir işlemde veri kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Bu izlenecek yol kullanarak bir işlemde veri kaydetme gösterilmektedir <xref:System.Transactions> ad alanı. Bu örnekte `Customers` ve `Orders` Northwind örnek veritabanındaki tablolar.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yol, Northwind örnek veritabanına erişim gerektirir. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-a-windows-application"></a>Bir Windows uygulaması oluşturma  
 İlk adım oluşturmaktır bir **Windows uygulama**.  
  
#### <a name="to-create-the-new-windows-project"></a>Yeni Windows projesi oluşturmak için  
  
1.  Visual Studio'da üzerinde **dosya** menüsünden Yeni bir **proje**.  
  
2.  Projeyi adlandırın **SavingDataInATransactionWalkthrough**.  
  
3.  Seçin **Windows uygulama**ve ardından **Tamam**. Daha fazla bilgi için [istemci uygulamaları](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **SavingDataInATransactionWalkthrough** projesi oluşturulur ve eklenen **Çözüm Gezgini**.  
  
## <a name="create-a-database-data-source"></a>Veritabanı veri kaynağı oluşturma  
 Bu adımı kullanan [veri kaynağı Yapılandırma Sihirbazı](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) dayalı bir veri kaynağını oluşturmak için `Customers` ve `Orders` Northwind örnek veritabanındaki tablolar.  
  
#### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için  
  
1.  Üzerinde **veri** menüsünde**veri kaynaklarını Göster**.  
  
2.  İçinde **veri kaynakları** penceresinde **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı Yapılandırma Sihirbazı**.  
  
3.  Üzerinde **bir veri kaynağı türü seçin**ekranındayken **veritabanı**ve ardından **sonraki**.  
  
4.  Üzerinde **veri bağlantınızı seçin**aşağıdakilerden birini ekran yapın:  
  
    -   Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.  
  
         veya  
  
    -   Seçin **yeni bağlantı** başlatmak için **Bağlantı Ekle/Değiştir** iletişim kutusu ve Northwind veritabanına bağlantı oluşturun.  
  
5.  Veritabanınız parola gerektiriyorsa, hassas verileri eklemek ve ardından seçeneğini **sonraki**.  
  
6.  Üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** ekranındayken **sonraki**.  
  
7.  Üzerinde **veritabanı nesnelerinizi seçin** ekranında, **tabloları** düğümü.  
  
8.  Seçin `Customers` ve `Orders` tablolar ve ardından **son**.  
  
     **NorthwindDataSet** projenize eklenir ve `Customers` ve `Orders` tablolar görünür **veri kaynakları** penceresi.  
  
## <a name="addcontrols-to-the-form"></a>Forma Addcontrols  
 Öğe sürükleyerek veriye bağlı denetimler oluşturabilirsiniz **veri kaynakları** formunuza penceresi.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Windows form üzerinde denetimleri bağlı veri oluşturma  
  
-   İçinde **veri kaynakları** penceresini genişletin **müşteriler** düğümü.  
  
-   Ana sürükleyin **müşteriler** düğümünden **veri kaynakları** penceresinden **Form1**.  
  
     A <xref:System.Windows.Forms.DataGridView> denetim ve araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) Kayıtlarda gezinmek için formda görünür. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md),<xref:System.Windows.Forms.BindingSource>, ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.  
  
-   İlgili sürükleyin **siparişler** düğümü (ana **siparişler** düğümü ancak ilgili alt tablo düğümünün altındaki **faks** sütun) aşağıdaki forma  **CustomersDataGridView**.  
  
     A <xref:System.Windows.Forms.DataGridView> formda görünür. Bir [orderstableadapter bağdaştırıcısına](../data-tools/tableadapter-overview.md) ve <xref:System.Windows.Forms.BindingSource> bileşen tepsisinde görünür.  
  
## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>System.Transactions derlemesine bir başvuru ekleyin  
 İşlemleri kullanma <xref:System.Transactions> ad alanı. El ile eklemeniz gerekir. Bu nedenle varsayılan olarak, system.transactions derlemeye bir proje başvurusu eklenmedi.  
  
#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>System.Transactions DLL dosyasına bir başvuru eklemek için  
  
1.  Üzerinde **proje** menüsünde**Başvuru Ekle**.  
  
2.  Seçin **System.Transactions**(üzerinde **.NET** sekmesinde) ve ardından **Tamam**.  
  
     Bir başvuru **System.Transactions** projeye eklenir.  
  
## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>Farenin kodda BindingNavigator'ın saveItem düğmesi  
 Varsayılan olarak eklenen formunuza bırakılan ilk tablo için kod `click` olayını Kaydet düğmesine <xref:System.Windows.Forms.BindingNavigator>. Herhangi bir ek tablolar güncelleştirmek için kodu el ile eklemeniz gerekir. Bu kılavuz için biz varolan kaydetme kodunun kaydetme yeniden düzenleme düğmenin tıklama olay işleyicisi. Ayrıca belirli bir güncelleştirmeyi işlevi mi satır eklendiğinde veya silindiğinde uygun olarak sağlamak için birkaç hakkında daha fazla yöntem oluşturacağız.  
  
#### <a name="to-modify-the-auto-generated-save-code"></a>Otomatik olarak oluşturulan kodu Kaydet değiştirmek için  
  
1. Seçin **Kaydet** düğmesini **CustomersBindingNavigator** (düğme disket simgesi ile).  
  
2. Değiştirin `CustomersBindingNavigatorSaveItem_Click` yöntemini aşağıdaki kod ile:  
  
    [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
    [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]  
  
   İlgili veri değişiklikleri mutabık kılma sırasını aşağıdaki gibidir:  
  
-   Alt kayıtları silin. (Bu durumda, kayıtları silme `Orders` tablo.)  
  
-   Üst kayıtlar silin. (Bu durumda, kayıtları silme `Customers` tablo.)  
  
-   Üst kayıtlar ekler. (Bu durumda, kayıtları eklemek `Customers` tablo.)  
  
-   Alt kayıtları ekleyin. (Bu durumda, kayıtları eklemek `Orders` tablo.)  
  
#### <a name="to-delete-existing-orders"></a>Mevcut siparişlerin silmek için  
  
-   Aşağıdaki `DeleteOrders` yönteme **Form1**:  
  
     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]  
  
#### <a name="to-delete-existing-customers"></a>Mevcut müşteriler silmek için  
  
-   Aşağıdaki `DeleteCustomers` yönteme **Form1**:  
  
     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]  
  
#### <a name="to-add-new-customers"></a>Yeni müşteriler eklemek için  
  
-   Aşağıdaki `AddNewCustomers` yönteme **Form1**:  
  
     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]  
  
#### <a name="to-add-new-orders"></a>Yeni siparişler eklemek için  
  
-   Aşağıdaki `AddNewOrders` yönteme **Form1**:  
  
     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]  
  
## <a name="run-the-application"></a>Uygulamayı çalıştırın  
  
#### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için  
  
-   Seçin **F5** uygulamayı çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)

