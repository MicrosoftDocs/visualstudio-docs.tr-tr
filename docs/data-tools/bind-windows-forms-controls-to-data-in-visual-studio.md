---
title: Verilere Windows Forms denetimleri bağlama
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 596475ed3a5e1cac535ca0cdf43980af44bd4bf1
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304642"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Visual Studio'da verilere Windows Forms denetimleri bağlama

Windows Forms veri bağlama ile uygulamanızın kullanıcılarına verileri görüntüleyebilirsiniz. Bu verilere bağlı denetimler oluşturmak için öğeleri sürükleyin **veri kaynakları** penceresinden Windows Form Tasarımcısı'nda Visual Studio.

![Veri kaynağı sürükleme işlemi](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> Varsa **veri kaynakları** penceresi görünür değilse, bunu seçerek açabilirsiniz **görünümü** > **diğer Windows** > **veri kaynakları** , veya basarak **Shift**+**Alt**+**D**. Visual Studio'da görmek için açık bir projeniz olmalıdır **veri kaynakları** penceresi.

Öğeleri sürükleme önce bağlamak istediğiniz denetim türünü ayarlayabilirsiniz. Tablo kendisi veya bir bireysel sütunda seçmenize bağlı olarak farklı değerler görüntülenir.  Özel değerler de ayarlayabilirsiniz. Bir tablo için **ayrıntıları** her sütun için ayrı bir denetim bağlı olduğu anlamına gelir.

![DataGridView için veri kaynağına bağlama](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>BindingSource ve BindingNavigator denetimleri

<xref:System.Windows.Forms.BindingSource> Bileşen iki amaca hizmet eder. İlk olarak denetimlere veri bağlama sırasında bir soyutlama katmanı sağlar. Form üzerinde denetimleri için ilişkili <xref:System.Windows.Forms.BindingSource> bir veri kaynağına doğrudan yerine bileşen. İkinci olarak, bu nesnelerin bir koleksiyonunu yönetebilirsiniz. Bir türe eklemek <xref:System.Windows.Forms.BindingSource> o türün bir liste oluşturur.

Hakkında daha fazla bilgi için <xref:System.Windows.Forms.BindingSource> bileşeni için bkz:

- [BindingSource bileşeni](/dotnet/framework/winforms/controls/bindingsource-component)

- [BindingSource bileşenine genel bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [BindingSource bileşeni mimarisi](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

[BindingNavigator denetimine](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) bir Windows uygulaması tarafından görüntülenen veriler aracılığıyla gezinmek için bir kullanıcı arabirimi sağlar.

## <a name="bind-to-data-in-a-datagridview-control"></a>DataGridView denetimine veri bağlama

İçin bir [DataGridView denetiminde](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), tablonun tamamını tek bir denetim için bağlıdır. Sürüklediğinizde bir **DataGridView** forma bir aracı Şerit Kayıtlarda gezinmek için (<xref:System.Windows.Forms.BindingNavigator>) de görünür. A [veri kümesi](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür. Aşağıdaki çizimde, bir [TableAdapterManager](https://msdn.microsoft.com/library/bb384426.aspx) Müşteriler tablosunda Siparişler tablosu için bir ilişkisi olduğundan de eklenir. Bu değişkenler tüm otomatik olarak oluşturulan kodda form sınıfında özel üyeler olarak bildirilir. Doldurma için otomatik olarak oluşturulan kod **DataGridView** bulunan `Form_Load` olay işleyicisi. Veritabanını güncellemek için verileri kaydetmek için kod bulunan `Save` için olay işleyicisi **BindingNavigator**. Geçiş yapabilir veya bu kodu gerektiği gibi değiştirin.

![BindingNavigator GridView](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

Davranışını özelleştirebilirsiniz **DataGridView** ve **BindingNavigator** her sağ üst köşedeki akıllı etiket tıklayın:

![DataGridView ve bağlama Gezgin akıllı etiketler](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Denetimler, uygulamanızın ihtiyaçlarını içinde kullanılabilir değilse, **veri kaynakları** penceresinde denetimler ekleyebilirsiniz. Daha fazla bilgi için [veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md).

Öğeleri sürükleyerek de **veri kaynakları** penceresinden denetimin veriye bağlamak için zaten bir form üzerinde denetimleri. En son sürüklediğinizde sürüklenen öğe için bağlamaları sıfırlama verilerini verilere zaten bağlı bir denetim vardır. Geçerli bırakma hedefleri olması için denetimleri temel alınan veri türünü buradan oturum sürüklenen öğe görüntüleyebilen olmalıdır **veri kaynakları** penceresi. Örneğin, bir veri türüne sahip bir öğe sürüklemek için geçerli değil <xref:System.DateTime> üzerine bir <xref:System.Windows.Forms.CheckBox>, çünkü <xref:System.Windows.Forms.CheckBox> tarih görüntüleme yeteneğine sahip değil.

## <a name="bind-to-data-in-individual-controls"></a>Tek denetimleri verilere bağlayın

Bir veri kaynağına bağladığınızda **ayrıntıları**, her sütun kümesindeki ayrı bir denetime bağlı.

![Ayrıntılar için veri kaynağına bağlama](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Önceki resimde unutmayın, Siparişler tablosundan Müşteriler tablosundaki siparişler özelliğinden sürükleyin. Bağlama tarafından `Customer.Orders` özellik, Gezinti komutları içinde yapılan **DataGridView** ayrıntıları denetimlerinde anında yansıtılır. Siparişler tablosundan sürüklediğiniz denetimler hala veri kümesine bağlı, ancak bunlar değil ile eşitlenmemiş **DataGridView**.

Müşteriler tablosundaki siparişler özelliği bağlı sonra forma eklenen verilere bağlı denetimler varsayılan aşağıda gösterilmiştir **ayrıntıları** içinde **veri kaynakları** penceresi.

![Siparişler tablosu için ayrıntıları bağlı](../data-tools/media/raddata-orders-table-bound-to-details.png)

Ayrıca, her denetimi akıllı etiket olduğuna dikkat edin. Bu etiket yalnızca bu denetime uygulamak özelleştirmeleri sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Windows Forms (.NET Framework) veri bağlama](/dotnet/framework/winforms/windows-forms-data-binding)