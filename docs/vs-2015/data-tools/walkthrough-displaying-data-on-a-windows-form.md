---
title: 'İzlenecek yol: Bir Windows formunda veri görüntüleme | Microsoft Docs'
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
- displaying data on forms, walkthroughs
- Windows Forms, displaying data
- Windows applications, displaying data
- data binding, Windows Forms
- data [Visual Studio], displaying on Windows Forms
- forms, displaying data
ms.assetid: f6e08c2c-c792-43de-adf3-3e52c0100225
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f623f639458a9f5c9c055b5d6de384f6fd39cad1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201209"
---
# <a name="walkthrough-displaying-data-on-a-windows-form"></a>İzlenecek Yol: Bir Windows Formunda Veri Görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulama geliştirmede en sık karşılaşılan senaryolardan biri, veri Windows tabanlı bir uygulamada bir form üzerinde görüntülemektir. Verileri sürükleyerek bir formda görüntüleyebilirsiniz [veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) forma. Bu izlenecek yolda bireysel denetimlerinde Tek bir tablodan verileri görüntüleyen basit bir form oluşturur. Bu örnekte `Customers` Northwind örnek veritabanından tablo.  
  
 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:  
  
-   Yeni bir oluşturma **Windows uygulama** proje.  
  
-   Oluşturma ve yapılandırma ile dataset [veri kaynağı Yapılandırma Sihirbazı](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Form üzerinde öğelerinden sürüklendiğinde oluşturulacak denetimi seçerek **veri kaynakları** penceresi. Daha fazla bilgi için [veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Öğe sürükleyerek veriye bağlı denetim oluşturma **veri kaynakları** formunuza penceresi.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için şunlar gerekir:  
  
-   Northwind örnek veritabanına erişim. Daha fazla bilgi için [nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-the-windows-application"></a>Windows Uygulaması Oluşturma  
 İlk adım oluşturmaktır bir **Windows uygulama** proje.  
  
#### <a name="to-create-the-new-windows-application-project"></a>Yeni bir Windows Uygulaması projesi oluşturmak için  
  
1.  Gelen **dosya** menüsünden Yeni bir proje oluşturun.  
  
2.  Projeyi adlandırın `DisplayingDataonaWindowsForm`.  
  
3.  Seçin **Windows uygulama** tıklatıp **Tamam**. Daha fazla bilgi için [istemci uygulamaları](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **DisplayingDataonaWindowsForm** projesi oluşturulur ve eklenen **Çözüm Gezgini**.  
  
## <a name="creating-the-data-source"></a>Veri Kaynağı Oluşturma  
 Bu adımda, bir veri kaynağı kullanılarak oluşturulur **veri kaynağı Yapılandırma Sihirbazı** göre `Customers` Northwind örnek veritabanındaki tablo. Bağlantı oluşturmak için Northwind örnek veritabanına erişiminiz olmalıdır. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: örnek veritabanları yükleme](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için  
  
1.  Üzerinde **veri** menüsünü tıklatın **veri kaynaklarını Göster**.  
  
2.  İçinde **veri kaynakları** penceresinde **yeni veri kaynağı Ekle** başlatmak için **veri kaynağı Yapılandırma Sihirbazı**.  
  
3.  Seçin **veritabanı** üzerinde **bir veri kaynağı türü seçin** sayfasında ve ardından **sonraki**.  
  
4.  Üzerinde **veri bağlantınızı seçin** sayfasında aşağıdakilerden birini yapın:  
  
    -   Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.  
  
         veya  
  
    -   Seçin **yeni bağlantı** başlatmak için **Bağlantı Ekle/Değiştir** iletişim kutusu...  
  
5.  Veritabanınız parola gerektiriyorsa, hassas verileri eklemek ve ardından seçeneğini **sonraki**.  
  
6.  Tıklayın **sonraki** üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfası.  
  
7.  Genişletin **tabloları** düğümde **veritabanı nesnelerinizi seçin** sayfası.  
  
8.  Seçin **müşteriler** tablosunu ve ardından **son**.  
  
     **NorthwindDataSet** projenize eklenir ve **müşteriler** tablo görünür **veri kaynakları** penceresi.  
  
## <a name="setting-the-controls-to-be-created"></a>Oluşturulması için denetimleri ayarlama  
 Bu kılavuz için veriler olacaktır bir **ayrıntıları** veri görüntüleyen her denetim düzeni. (Alternatif bir yaklaşım varsayılandır **kılavuz** veri görüntüleyen, düzen bir <xref:System.Windows.Forms.DataGridView> denetim.)  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Veri kaynakları Penceresi'nde öğelerin bırakma türünü ayarlama  
  
1.  Genişletin **müşteriler** düğümünde **veri kaynakları** penceresi.  
  
2.  Bırakma türünü değiştirme **müşteriler** tablo **ayrıntıları** seçerek **ayrıntıları** aşağı açılan listeden **müşteriler** düğümü. Daha fazla bilgi için [veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Değişiklik **CustomerID** sütun bırakma türünü seçerek bir etikete **etiket** üzerinde denetim listesinden **CustomerID** düğümü.  
  
## <a name="creating-the-form"></a>Form Oluşturma  
 Öğe sürükleyerek veriye bağlı denetimler oluşturmak **veri kaynakları** formunuza penceresi.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Form üzerinde veri bağlama denetimleri oluşturmak için  
  
-   Ana sürükleyin **müşteriler** düğümünden **veri kaynakları** forma penceresi.  
  
     Araç şeridi yanı sıra form üzerindeki verilere bağlı denetimler, tanımlayıcı etiketlerle görünür (<xref:System.Windows.Forms.BindingNavigator>) Kayıtlarda gezinmek için. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
  
#### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için  
  
-   F5 tuşuna basın.  
  
-   Git kullanarak kayıtları <xref:System.Windows.Forms.BindingNavigator> denetimi.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Uygulama gereksinimlerinize bağlı olarak, bir veri bağlantılı Windows Form oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bu izlenecek yolda yapabileceğiniz bazı geliştirmeler şunlardır:  
  
-   Forma arama işlevselliği ekleme. Daha fazla bilgi için [nasıl yapılır: bir Windows Forms uygulamasına parametreli bir sorgu ekleme](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
-   Güncelleştirmeleri veritabanına geri göndermek için işlevsellik ekler. Daha fazla bilgi için [izlenecek yol: verileri bir veritabanına (tek tablo) kaydetme](http://msdn.microsoft.com/library/68befa96-7463-43e8-abcf-dc2f42ccd53d).  
  
-   Ekleme `Orders` seçerek veri kümesini tabloya **veri kümesini Yapılandırma Sihirbazı ile** içinden **veri kaynakları** penceresi. Sürükleyerek ilgili verileri görüntüleyen denetimler ekleyebilirsiniz **siparişler** düğümü (bir aşağıdaki **faks** sütunda **müşteriler** tablo) forma. Daha fazla bilgi için [nasıl yapılır: Windows Forms uygulamasında görüntü ilgili verileri](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri izlenecek yollar](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)   
 [TableAdapter genel bakış](../data-tools/tableadapter-overview.md)