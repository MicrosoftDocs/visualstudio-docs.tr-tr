---
title: 'Nasıl yapılır: çalışma sayfalarını veritabanı verileriyle doldurma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 25e73eaa3cdd0655a51711ddd30996915f984213
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758475"
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Nasıl yapılır: çalışma sayfalarını veritabanı verileriyle doldurma

Windows Forms projelerindeki veri erişim aynı şekilde belge düzeyi Office projelerinde verilere erişebilirsiniz. Çözümünüze verileri getirmek için aynı araçları ve kod kullanmak ve verileri görüntülemek için bile Windows Forms denetimleri kullanabilirsiniz. Ayrıca, Microsoft Office Excel olayları ve veri bağlama özelliğiyle geliştirilmiş yerel nesneler olan konak kontrollerinden yararlanabilir. Daha fazla bilgi için bkz: [konak öğelerini ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

Aşağıdaki örnek bir tasarımcı kullanarak belge düzeyi projelerine verilere bağlı denetimler ekleme gösterir. Verilere bağlı denetimler çalışma zamanında uygulama düzeyi projelerine ekleme konusunda bir örnek için bkz: [izlenecek yol: karmaşık veri bağlama VSTO eklenti projesindeki](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).

![video bağlantı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz [I: Aktarım verileri bir Excel çalışma sayfasına nasıl yapılacağı?](http://go.microsoft.com/fwlink/?LinkID=130277), ve [nasıl Excel'de veritabanı verisi I: tüketen musunuz?](http://go.microsoft.com/fwlink/?LinkID=130287).

## <a name="add-a-data-bound-control-to-a-worksheet-at-design-time"></a>Veri bağlama denetimi çalışma sayfasına tasarım zamanında ekleme

### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Bir veritabanından verilerle çalışma doldurmak için

1.  Excel belge düzeyi projesindeki Tasarımcısı'nda çalışma açıkken Visual Studio'da açın.

2.  Açık **veri kaynakları** penceresi ve projeniz için bir veri kaynağı oluşturun. Daha fazla bilgi için bkz: [yeni bağlantılar eklemek](../data-tools/add-new-connections.md).

3.  Alan veya istediğiniz tablo sürükleyin **veri kaynakları** çalışma penceresine.

Aşağıdaki denetimleri biri çalışma sayfası üzerinde oluşturulur:

-   Bir alan sürüklediğinizde bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi çalışma sayfası üzerinde oluşturulur. Daha fazla bilgi için bkz: [NamedRange denetimi](../vsto/namedrange-control.md).

-   Bir tablo sürüklediğinizde bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi çalışma sayfası üzerinde oluşturulur. Daha fazla bilgi için bkz: [ListObject denetimi](../vsto/listobject-control.md).

Farklı bir denetim tablo seçerek eklemek veya içinde alan **veri kaynakları** penceresini açın ve ardından farklı bir denetim aşağı açılan listeden seçerek.

## <a name="objects-in-the-project"></a>Projesindeki nesneleri

Denetim ek olarak aşağıdaki verilerle ilgili nesnelerle projenize otomatik olarak eklenir:

-   Veritabanında bağlı veri tabloları yalıtır türü belirtilmiş veri kümesi. Daha fazla bilgi için bkz: [Visual Studio'da veri kümesi Araçları](/visualstudio/data-tools/dataset-tools-in-visual-studio).

-   A <xref:System.Windows.Forms.BindingSource> , Denetim türü belirtilmiş veri kümesine bağlanır. Daha fazla bilgi için bkz: [BindingSource bileşenine genel bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview).

-   Türü belirtilmiş veri kümesi veritabanına bağlanan bir TableAdapter. Daha fazla bilgi için bkz: [TableAdapter genel bakışı](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

-   Hiyerarşik güncelleştirmeleri etkinleştirmek için tablo bağdaştırıcıları kümesindeki koordine etmek için kullanılan bir TableAdapterManager. Daha fazla bilgi için bkz: [hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md) ve [TableAdapterManager başvuru](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Projeyi çalıştırdığınızda, denetimi veri kaynağındaki ilk kaydı görüntüler. Kullanabileceğiniz <xref:System.Windows.Forms.BindingSource> kullanıcıların kayıtlar arasında gezinmek.

### <a name="to-scroll-through-the-records"></a>Kayıtlar arasında gezinmek için

-   Kullanım <xref:System.Windows.Forms.BindingSource> gibi yöntemler <xref:System.Windows.Forms.BindingSource.MoveNext%2A> ve <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Türü belirtilmiş veri kümesi ve veritabanı güncellemelerin hakkında daha fazla bilgi için bkz: [nasıl yapılır: konak kontrolü verileriyle veri kaynağını güncelleme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Yeni veri kaynakları ekleyin](../data-tools/add-new-data-sources.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Nasıl yapılır: belgeleri nesne verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Nasıl yapılır: belgeleri veritabanı verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Nasıl yapılır: belgeleri hizmet verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Nasıl yapılır: konak kontrolü verileriyle veri kaynağını güncelleme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Nasıl I: Aktarım verileri bir Excel çalışma sayfasına?](http://go.microsoft.com/fwlink/?LinkID=130277)
- [Nasıl Excel'de veritabanı verisi I: kullanabilir?](http://go.microsoft.com/fwlink/?LinkID=130287)