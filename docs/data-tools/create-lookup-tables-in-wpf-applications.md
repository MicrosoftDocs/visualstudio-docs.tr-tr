---
title: WPF uygulamalarında arama tabloları oluşturma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c76f769234d8b8c14ccd44d8c2cf4c669bf48ffd
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305487"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>WPF uygulamalarında arama tabloları oluşturma

Terim *arama tablosu* (olarak da adlandırılan bir *arama bağlama*) bir veri tablosundaki başka bir tablodaki bir yabancı anahtar alanının değeri temel bilgileri görüntüleyen bir denetimi açıklar. Bir üst tablonun ana düğüm sürükleyerek arama tablosu oluşturma veya nesnesine **veri kaynakları** penceresinden bir sütun veya ilgili alt tabloda özelliği zaten bağlı bir denetim.

Örneğin, bir tablo düşünün `Orders` satış veritabanındaki. Her kayıtta `Orders` tablo içeren bir `CustomerID` siparişi hangi müşterinin verdiğini gösterir. `CustomerID` Bir müşteri kaydı işaret eden bir yabancı anahtar `Customers` tablo. Sipariş listesini görüntülerken `Orders` tablosu yerine gerçek müşteri adı görüntülemek isteyebilirsiniz `CustomerID`. Müşteri adı olduğundan `Customers` tablosu, müşteri adına görüntülemek için arama tablosu oluşturmanız gerekir. Arama tablosu kullandığı `CustomerID` değerini `Orders` ilişki gitmek için kayıt ve müşteri adı döndürür.

## <a name="to-create-a-lookup-table"></a>Arama tablosu oluşturma

1.  Veri kaynakları ile ilgili verileri aşağıdaki türlerden biri, projenize ekleyin:

    -   Veri kümesi veya varlık veri modeli.

    -   WCF veri hizmeti, WCF hizmeti veya web hizmeti. Daha fazla bilgi için [nasıl yapılır: bir hizmetteki verilere bağlanma](../data-tools/how-to-connect-to-data-in-a-service.md).

    -   Nesneleri. Daha fazla bilgi için [Visual Studio'da nesne bağlama](bind-objects-in-visual-studio.md).

    > [!NOTE]
    > Arama tablosu oluşturmadan önce iki ilişkili tablolar veya nesneleri projesi için veri kaynağı olarak mevcut olmalıdır.

2.  Açık **WPF Tasarımcısı**ve tasarımcı geçerli bırakma hedefi öğeleri için bir kapsayıcı içerdiğinden emin olun **veri kaynakları** penceresi.

     Geçerli bırakma hedefleri hakkında daha fazla bilgi için bkz. [Visual Studio'da veri bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

3.  Üzerinde **veri** menüsünde tıklatın **veri kaynaklarını Göster** açmak için **veri kaynakları** penceresi.

4.  Ait düğümleri genişletebilirsiniz **veri kaynakları** üst tablo veya nesne ve ilgili alt tablo veya nesne görene kadar penceresi.

    > [!NOTE]
    > İlgili alt tablo veya nesne olarak üst tablo veya nesne Genişletilebilir alt düğümünde görüntülenen düğümüdür.

5.  Alt düğümü için aşağı açılan menüsünü tıklatın ve seçin **ayrıntıları**.

6.  Alt düğümü genişletin.

7.  Alt düğümünde, alt ve üst veri ilişkili öğeyi aşağı açılan menüsüne tıklayın. (Önceki örnekte budur **CustomerID** düğümü.) Arama bağlamayı destekleyen denetimlerin aşağıdaki türlerinden birini seçin:

    -   **ComboBox**

    -   **ListBox**

    -   **ListView**

        > [!NOTE]
        > Varsa **ListBox** veya **ListView** denetimi görünmez listesinde, bu denetimleri listesine ekleyebilirsiniz. Bilgi için [veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    -   Öğesinden türetilen herhangi bir özel denetimin <xref:System.Windows.Controls.Primitives.Selector>.

        > [!NOTE]
        > Öğe denetimleri listesine özel denetimleri ekleme hakkında bilgi seçebilirsiniz **veri kaynakları** penceresinde görmek [veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md).

8.  Alt düğümünden sürükleyin **veri kaynakları** penceresinden WPF tasarımcısına bir kapsayıcıda. (Önceki örnekte, alt düğümüdür **siparişler** düğümü.)

     Visual Studio her sürüklediğiniz öğeleri için yeni verilere bağlı denetimler oluşturan XAML oluşturur. XAML ayrıca yeni bir ekler <xref:System.Windows.Data.CollectionViewSource> alt tablo veya bırakma hedefi kaynaklarına nesnesi. Bazı veri kaynakları için Visual Studio ayrıca tablo veya nesne verilerini yüklemek için kod oluşturur. Daha fazla bilgi için [Visual Studio'da veri bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

9. Sürükleyin üst düğümden **veri kaynakları** penceresinden daha önce oluşturduğunuz arama bağlama denetimi. (Önceki örnekte, üst düğümdür **müşteriler** düğümü).

     Visual Studio arama yapılandırmak için Denetim bazı özelliklerini ayarlar. Aşağıdaki tabloda, Visual Studio değiştirir özellikleri listeler. Gerekirse, bu özellikler, XAML veya değiştirebileceğiniz, **özellikleri** penceresi.

    |Özellik|Ayar açıklaması|
    |--------------| - |
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Bu özellik, koleksiyon veya denetimde görüntülenen verileri almak için kullanılan bağlama belirtir. Visual Studio bu özelliği ayarlar <xref:System.Windows.Data.CollectionViewSource> denetime sürüklediğiniz üst veriler için.|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Bu özellik, veri öğesi denetiminde görüntülenen yolunu belirtir. Visual Studio bu özellik bir dize veri türü olan birincil anahtar sonra ilk sütuna veya üst veri özelliğini ayarlar.<br /><br /> Farklı bir sütun veya özellik üst verileri görüntülemek istiyorsanız, bu özellik için farklı bir özellik yolunu değiştirin.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio bu özellik sütun veya alt verilerin tasarımcıya sürüklediğiniz özelliği bağlar. Üst verileri için yabancı anahtarı budur.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio bu özellik sütunu yolunu veya üst veri yabancı anahtar alt veri özelliğini ayarlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [WPF uygulamalarındaki ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md)
- [İzlenecek yol: WPF uygulamasında ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md)