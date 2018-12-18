---
title: 'Nasıl yapılır: belgeleri nesne verileriyle doldurma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- data [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ef3d1441f9587bceeca0c4aacdc054a4769a2369
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758118"
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>Nasıl yapılır: belgeleri nesne verileriyle doldurma

Windows Forms projelerindeki gibi bir veri nesnesi belirtilmemelidir verileri Microsoft Office Word için belge düzeyi projelerine aynı şekilde çalışır. Verileri bir nesneden çözümünüze getirmek için aynı araçları ve kod kullanmak ve verileri görüntülemek için Windows Forms denetimleri kullanabilirsiniz. Ayrıca, ana bilgisayar denetimleri kullanarak verileri görüntüleyebilirsiniz. Konak denetimleri, olaylar ve veri bağlama özelliğiyle geliştirilmiş yerel Microsoft Office Word nesneleridir. Daha fazla bilgi için bkz: [konak öğelerini ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

Belgeyi bir nesneden verilerle doldurmak için üç temel adımları tamamlamanız gerekir:

-   Veriye bağlayabilirsiniz belge için bir denetim ekleyin.

-   Bir veri nesnesi belgeye ekleyin.

-   Veri nesnesi BindingSource bağlayın.

## <a name="to-add-a-data-object"></a>Bir veri nesnesi eklemek için

Bir veri nesnesi eklemek için **veri kaynakları** penceresi ve bir nesneden bir veri kaynağı oluşturun. Daha fazla bilgi için bkz: [yeni veri kaynakları ekleyin](../data-tools/add-new-data-sources.md).

## <a name="connect-the-data-object-to-the-bindingsource"></a>Veri nesnesi BindingSource Bağlan

Belge düzeyi projelerine belgenize denetimleri ekleyebilir ve bunları tasarım zamanında verilere bağlayın.

VSTO eklentisi projelerine denetimleri oluşturmak ve çalışma zamanında bağlayın.

### <a name="document-level-projects"></a>Belge düzeyi projelerine

Veri nesnesi BindingSource bağlanmak için:

1.  İstediğiniz verileri alan sürükleyin **veri kaynakları** belgenizi penceresine. Bu denetim otomatik olarak oluşturur.

2.  Kodunuzda, veri kaynağı için seçtiğiniz nesnenin türü örneği oluşturun.

3.  Örneğine atadığınız <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliği <xref:System.Windows.Forms.BindingSource>.

### <a name="application-level-projects"></a>Uygulama düzeyi projeleri

Veri nesnesi BindingSource bağlanmak için:

1.  Kodunuzda, veri kaynağıyla ilişkilendirilmiş nesne türünün bir örneği oluşturun.

2.  Bir örneğini oluşturmak bir <xref:System.Windows.Forms.BindingSource>.

3.  Veri kaynağı örneği atayın <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliği <xref:System.Windows.Forms.BindingSource>.

4.  Veri kaynağı denetimine veri bağlama olarak ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeni veri kaynakları ekleyin](../data-tools/add-new-data-sources.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Nasıl yapılır: belgeleri veritabanı verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Nasıl yapılır: konak kontrolü verileriyle veri kaynağını güncelleme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [BindingSource bileşenine genel bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview)