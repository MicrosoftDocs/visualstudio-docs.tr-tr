---
title: Windows Forms denetimleri verilere bağlayın | Microsoft Docs
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
- displaying data, Windows Forms controls
- Windows Forms, displaying data
- data sources, displaying
- data [Windows Forms], displaying
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d1d8710ef98339c0cf4b44ddd3fa41cca8676570
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237477"
---
# <a name="bind-windows-forms-controls-to-data"></a>Verilere Windows Forms denetimleri bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Nesnelerden sürükleyerek veri kaynakları denetimlerine bağlayabilirsiniz **veri kaynakları** Windows forma veya varolan bir denetimi form üzerinde oturum penceresi. Öğeleri sürükleme önce bağlamak istediğiniz denetim türünü ayarlayabilirsiniz. Tablo kendisi veya bir bireysel sütunda seçmenize bağlı olarak farklı değerler görüntülenir.  Özel değerler de ayarlayabilirsiniz. Bir tablo için her sütun için ayrı bir denetim bağlıdır "Details" anlamına gelir.  
  
 ![Veri kaynağına bağlamak için DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata DataGridView veri kaynağına bağlama")  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="bind-to--data-in-a-datagridview-control"></a>DataGridView denetimine veri bağlama  
 DataGridView için tablonun tamamını tek bir denetim için bağlıdır. Bir DataGridView'in forma sürüklediğinizde, bir aracı Şerit Kayıtlarda gezinmek için (<xref:System.Windows.Forms.BindingNavigator>) de görünür. A [veri kümesi](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür. Müşteriler tablosunda Siparişler tablosu için bir ilişkisi olduğundan, aşağıdaki çizimde, bir TableAdapterManager de eklenir. Bu değişkenler tüm otomatik olarak oluşturulan kodda form sınıfında özel üyeler olarak bildirilir. DataGridView doldurmak için otomatik olarak oluşturulan kodu Page_Load olay işleyicisi bulunur. Veritabanını güncellemek için verileri kaydetmek için kod Kaydet olay işleyicisi için BindingNavigator bulunur. Geçiş yapabilir veya bu kodu gerektiği gibi değiştirin.  
  
 ![BindingNavigator GridView](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata BindingNavigator GridView")  
  
 Akıllı etiket her sağ üst köşedeki tıklayarak DataGridView ve BindingNavigator davranışını özelleştirebilirsiniz:  
  
 ![Akıllı etiketler DataGridView ve bağlama Gezgin](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView ve bağlama Gezgin akıllı etiketler")  
  
 Denetimler, uygulamanızın ihtiyaçlarını içinde kullanılabilir değilse, **veri kaynakları** penceresinde denetimler ekleyebilirsiniz. Daha fazla bilgi için [veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 Öğeleri sürükleyerek de **veri kaynakları** penceresinden denetimin veriye bağlamak için zaten bir form üzerinde denetimleri. En son sürüklediğinizde sürüklenen öğe için bağlamaları sıfırlama verilerini verilere zaten bağlı bir denetim vardır. Geçerli bırakma hedefleri olması için denetimleri temel alınan veri türünü buradan oturum sürüklenen öğe görüntüleyebilen olmalıdır **veri kaynakları** penceresi. Örneğin, bir veri türüne sahip bir öğe sürüklemek için geçerli değil <xref:System.DateTime> üzerine bir <xref:System.Windows.Forms.CheckBox>, çünkü <xref:System.Windows.Forms.CheckBox> tarih görüntüleme yeteneğine sahip değil.  
  
## <a name="bind-to--data-in-individual-controls"></a>Tek denetimleri verilere bağlayın  
 "Ayrıntılar" bir veri kaynağına bağlandığınızda her sütun kümesindeki ayrı bir denetime bağlı.  
  
 ![Veri kaynağı ayrıntıları bağlama](../data-tools/media/raddata-bind-data-source-to-details.png "raddata bağlama veri kaynağı ayrıntıları")  
  
> [!IMPORTANT]
>  Önceki resimde unutmayın, Siparişler tablosundan Müşteriler tablosundaki siparişler özelliğinden sürükleyin. Customer.Orders özelliğine bağlama tarafından yaptığınız Datagrindview'daki Gezinti komutları hemen ayrıntıları denetimlerinde yansıtılır. Siparişler tablosundan Sürüklediyseniz, denetimleri yine de veri kümesine bağlı, ancak bunlar değil DataGridView ile eşitlenmemiş.  
  
 Aşağıda varsayılan siparişler Müşteriler tablosunda "Ayrıntılar" özelliğe sonra forma eklenen verilere bağlı denetimler gösterilir **veri kaynakları** penceresi.  
  
 ![Siparişler tablosu için ayrıntıları bağlı](../data-tools/media/raddata-orders-table-bound-to-details.png "raddata tablosuna bağlı ayrıntıları")  
  
 Ayrıca, her denetimi akıllı etiket olduğuna dikkat edin. Bu etiket yalnızca bu denetime uygulamak özelleştirmeleri sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

