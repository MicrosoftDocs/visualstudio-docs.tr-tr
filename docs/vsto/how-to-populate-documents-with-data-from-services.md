---
title: 'Nasıl yapılır: belgeleri hizmet verileriyle doldurma'
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
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4ac901b524818086d6dbf23b7b55487054170b3e
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758548"
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Nasıl yapılır: belgeleri hizmet verileriyle doldurma

Windows Forms projelerindeki gibi veri erişimi için Microsoft Office belge düzeyi projelerine aynı şekilde çalışır. Çözümünüze verileri getirmek için aynı araçları ve kod kullanmak ve verileri görüntülemek için bile Windows Forms denetimleri kullanabilirsiniz. Ayrıca, Microsoft Office Excel ve Microsoft Office Word olayları ve veri bağlama özelliğiyle geliştirilmiş yerel nesneler olan konak kontrollerinden yararlanabilir. Daha fazla bilgi için bkz: [konak öğelerini ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

Aşağıdaki örnek, verilere bağlı denetimler tasarım zamanında belgelere ekleme gösterilmektedir. Verilere bağlı denetimler çalışma zamanında VSTO eklentiler ekleme konusunda bir örneği için bkz [izlenecek yol: VSTO eklenti projesindeki hizmetinden verilere bağlama](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).

![video bağlantı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz: [nasıl I: etkileşim web Hizmetleri ile Microsoft Excel'den musunuz?](http://go.microsoft.com/fwlink/?LinkID=130284).

## <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Belge düzeyi proje bir web hizmeti verilerle doldurmak için

1.  Açık **veri kaynakları** penceresi ve projeniz için bir veri kaynağı hizmeti oluşturun. Daha fazla bilgi için bkz: [yeni veri kaynakları ekleyin](../data-tools/add-new-data-sources.md).

2.  Tablo veya istediğiniz alanı sürükleyin **veri kaynakları** belgenizi penceresine.

     Bir denetim belge üzerinde oluşturulan bir <xref:System.Windows.Forms.BindingSource> oluşturulur projenizi nesne sınıfında bağlanır ve sınıflar, hizmet için oluşturulur.

3.  Kodunuzda, 1. adımda bağlı web hizmeti sınıfının bir örneğini oluşturun.

4.  Web hizmeti ile iletişim için gerekli olan özellikleri varsa, bu özelliklerin örneklerini oluşturun.

5.  Oluşturun ve 4. adımda oluşturduğunuz Web hizmeti ve hiç özelliği örneği tarafından kullanıma sunulan yöntemleri kullanarak veri isteği gönderin.

     Kullandığınız yöntem, web hizmetini sunar bağlıdır.

6.  Web hizmetine veri yanıtını atayın <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliği <xref:System.Windows.Forms.BindingSource>.

Projeyi çalıştırdığınızda denetimleri veri kaynağındaki ilk kaydı görüntüler. Nesneleri kullanarak para birimi olayları işleyerek kayıtlarda kaydırma etkinleştirebilirsiniz <xref:System.Windows.Forms.BindingSource>.

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Yeni veri kaynakları ekleyin](../data-tools/add-new-data-sources.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Nasıl yapılır: çalışma sayfalarını veritabanı verileriyle doldurma](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Nasıl yapılır: belgeleri nesne verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Nasıl yapılır: belgeleri veritabanı verileriyle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Nasıl yapılır: konak kontrolü verileriyle veri kaynağını güncelleme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)