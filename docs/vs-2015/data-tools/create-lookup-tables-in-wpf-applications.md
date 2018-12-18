---
title: WPF uygulamalarında arama tabloları oluşturma | Microsoft Docs
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
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6ce3b1cb07256c35949591b4d6ea012f56e432c6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303348"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>WPF uygulamalarında arama tabloları oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Terim *arama tablosu* (olarak da adlandırılan bir *arama bağlama*) bir veri tablosundaki başka bir tablodaki bir yabancı anahtar alanının değeri temel bilgileri görüntüleyen bir denetimi açıklar. Bir üst tablonun ana düğüm sürükleyerek arama tablosu oluşturma veya nesnesine **veri kaynakları** penceresinden bir sütun veya ilgili alt tabloda özelliği zaten bağlı bir denetim.  
  
 Örneğin, bir tablo düşünün `Orders` satış veritabanındaki. Her kayıtta `Orders` tablo içeren bir `CustomerID` siparişi hangi müşterinin verdiğini gösterir. `CustomerID` Bir müşteri kaydı işaret eden bir yabancı anahtar `Customers` tablo. Sipariş listesini görüntülerken `Orders` tablosu yerine gerçek müşteri adı görüntülemek isteyebilirsiniz `CustomerID`. Müşteri adı olduğundan `Customers` tablosu, müşteri adına görüntülemek için arama tablosu oluşturmanız gerekir. Arama tablosu kullandığı `CustomerID` değerini `Orders` ilişki gitmek için kayıt ve müşteri adı döndürür.  
  
## <a name="to-create-a-lookup-table"></a>Arama tablosu oluşturma  
  
1.  Veri kaynakları ile ilgili verileri aşağıdaki türlerden biri, projenize ekleyin:  
  
    -   Veri kümesi veya varlık veri modeli. Daha fazla bilgi için [nasıl yapılır: bir veritabanındaki verilere bağlanma](../data-tools/how-to-connect-to-data-in-a-database.md).  
  
    -   WCF veri hizmeti, WCF hizmeti veya Web hizmeti. Daha fazla bilgi için [nasıl yapılır: bir hizmetteki verilere bağlanma](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
    -   Nesneleri. Daha fazla bilgi için [nasıl yapılır: nesnelerdeki verilere bağlanma](http://msdn.microsoft.com/library/862fd351-0f4d-4220-9743-6103b87dc24b).  
  
    > [!NOTE]
    >  Arama tablosu oluşturmadan önce iki ilişkili tablolar veya nesneleri projesi için veri kaynağı olarak mevcut olmalıdır.  
  
2.  Açık**WPF Tasarımcısı**ve tasarımcı geçerli bırakma hedefi öğeleri için bir kapsayıcı içerdiğinden emin olun **veri kaynakları** penceresi.  
  
     Geçerli bırakma hedefleri hakkında daha fazla bilgi için bkz. [Visual Studio'da veri bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
3.  Üzerinde **veri** menüsünde tıklatın **veri kaynaklarını Göster** açmak için **veri kaynakları** penceresi.  
  
4.  Ait düğümleri genişletebilirsiniz **veri kaynakları** üst tablo veya nesne ve ilgili alt tablo veya nesne görene kadar penceresi.  
  
    > [!NOTE]
    >  İlgili alt tablo veya nesne olarak üst tablo veya nesne Genişletilebilir alt düğümünde görüntülenen düğümüdür.  
  
5.  Alt düğümü için aşağı açılan menüsünü tıklatın ve seçin **ayrıntıları**.  
  
6.  Alt düğümü genişletin.  
  
7.  Alt düğümünde, alt ve üst veri ilişkili öğeyi aşağı açılan menüsüne tıklayın. (Önceki örnekte budur **CustomerID** düğümü.) Arama bağlamayı destekleyen denetimlerin aşağıdaki türlerinden birini seçin:  
  
    -   **ComboBox**  
  
    -   **ListBox**  
  
    -   **ListView**  
  
        > [!NOTE]
        >  Varsa **ListBox** veya **ListView** denetimi görünmez listesinde, bu denetimleri listesine ekleyebilirsiniz. Bilgi için [veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
    -   Öğesinden türetilen herhangi bir özel denetimin <xref:System.Windows.Controls.Primitives.Selector>.  
  
        > [!NOTE]
        >  Öğe denetimleri listesine özel denetimleri ekleme hakkında bilgi seçebilirsiniz **veri kaynakları** penceresinde görmek [veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
8.  Alt düğümünden sürükleyin **veri kaynakları** penceresinden WPF tasarımcısına bir kapsayıcıda. (Önceki örnekte, alt düğümüdür **siparişler** düğümü.)  
  
     Visual Studio her sürüklediğiniz öğeleri için yeni verilere bağlı denetimler oluşturan XAML oluşturur. XAML ayrıca yeni bir ekler <xref:System.Windows.Data.CollectionViewSource> alt tablo veya bırakma hedefi kaynaklarına nesnesi. Bazı veri kaynakları için Visual Studio ayrıca tablo veya nesne verilerini yüklemek için kod oluşturur. Daha fazla bilgi için [Visual Studio'da veri bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
9. Sürükleyin üst düğümden **veri kaynakları** penceresinden daha önce oluşturduğunuz arama bağlama denetimi. (Önceki örnekte, üst düğümdür **müşteriler** düğümü).  
  
     Visual Studio arama yapılandırmak için Denetim bazı özelliklerini ayarlar. Aşağıdaki tabloda, Visual Studio değiştirir özellikleri listeler. Gerekirse, bu özellikler, XAML veya değiştirebileceğiniz, **özellikleri** penceresi.  
  
    |Özellik|Ayar açıklaması|  
    |--------------|----------------------------|  
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Bu özellik, koleksiyon veya denetimde görüntülenen verileri almak için kullanılan bağlama belirtir. Visual Studio bu özelliği ayarlar <xref:System.Windows.Data.CollectionViewSource> denetime sürüklediğiniz üst veriler için.|  
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Bu özellik, veri öğesi denetiminde görüntülenen yolunu belirtir. Visual Studio bu özellik bir dize veri türü olan birincil anahtar sonra ilk sütuna veya üst veri özelliğini ayarlar.<br /><br /> Farklı bir sütun veya özellik üst verileri görüntülemek istiyorsanız, bu özellik için farklı bir özellik yolunu değiştirin.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio bu özellik sütun veya alt verilerin tasarımcıya sürüklediğiniz özelliği bağlar. Üst verileri için yabancı anahtarı budur.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio bu özellik sütunu yolunu veya üst veri yabancı anahtar alt veri özelliğini ayarlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [WPF uygulamalarında ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md)   
 [İzlenecek yol: WPF uygulamasında ilgili verileri görüntüleme](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)

