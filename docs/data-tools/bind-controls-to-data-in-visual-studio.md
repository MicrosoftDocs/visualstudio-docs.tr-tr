---
title: Verilere denetimler bağlama
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- dislaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c4e27f5ce9536e7128330ebe932709a9be408b7e
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305269"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Visual Studio'da verilere denetimler bağlama

Denetimlere veri bağlama ile uygulamanızın kullanıcılarına verileri görüntüleyebilirsiniz. Öğeleri sürükleyerek bu verilere bağlı denetimler oluşturabilirsiniz **veri kaynakları** penceresinden bir tasarım yüzeyine veya Visual Studio'da bir yüzeydeki denetimleri.

Bu konu, veriye bağlı denetimler oluşturmak için kullanabileceğiniz veri kaynaklarını anlatmaktadır. Ayrıca veri bağlamaya dahil edilen genel görevlerden bazılarını açıklar. Verilere bağlı denetimler oluşturma hakkında daha özel ayrıntılar için bkz [Visual Studio'da verilere Windows Forms bağlama denetimleri](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) ve [Visual Studio'da veri bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

## <a name="data-sources"></a>Veri kaynakları

Veri bağlama bağlamında Kullanıcı Arabiriminizin bağlı bellek verileri bir veri kaynağını temsil eder. Pratikte, bir veri kaynağı bir varlık çerçevesi sınıfı, bir veri kümesi, bir .NET proxy nesnesi, bir LINQ to SQL sınıfı veya herhangi bir .NET nesne veya koleksiyon kapsüllenir bir hizmet uç noktası olabilir. Öğe sürükleyerek veriye bağlı denetimler oluşturmak bazı veri kaynakları etkinleştirmeniz **veri kaynakları** desteklerken diğer veri kaynakları penceresi. Aşağıdaki tabloda, hangi veri kaynaklarının desteklendiğini göstermektedir.

| Veri kaynağı | Sürükle ve bırak desteği **Windows Form Tasarımcısı** | Sürükle ve bırak desteği **WPF Tasarımcısı** | Sürükle ve bırak desteği **Silverlight Tasarımcısı** |
| - | - | - | - |
| Veri kümesi | Evet | Evet | Hayır |
| Varlık Veri Modeli | Evet<sup>1</sup> | Evet | Evet |
| LINQ to SQL sınıfları | Hayır<sup>2</sup> | Hayır<sup>2</sup> | Hayır<sup>2</sup> |
| Hizmetler (dahil olmak üzere [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], WCF hizmetleri ve web Hizmetleri) | Evet | Evet | Evet |
| Nesne | Evet | Evet | Evet |
| SharePoint | Evet | Evet | Evet |

1. Kullanarak modeli oluşturma **varlık veri modeli** Sihirbazı'nı, ardından bu nesneleri tasarımcıya sürükleyebilirsiniz.

2. LINQ to SQL sınıfları görünmez **veri kaynakları** penceresi. Ancak LINQ to SQL sınıflarını temel alan yeni bir nesne veri kaynağı ekleyin ve ardından bu nesneleri tasarımcıya verilere bağlı denetimler oluşturmak için sürükleyin. Daha fazla bilgi için [izlenecek yol: oluşturma LINQ to SQL sınıfları (O R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="data-sources-window"></a>Veri Kaynakları penceresi

Veri kaynakları projenize kullanılabilir öğeleri olarak **veri kaynakları** penceresi. Bir form Tasarım yüzeyine projesinde etkin pencere veya bunu (bir proje açıkken) seçerek açabilirsiniz bu pencerenin görünür olup **görünümü** > **diğer Windows**  >   **Veri kaynakları**. Temel alınan verilere bağlı denetimler oluşturmak için bu pencereden öğe sürükleyebilirsiniz ve sağ tıklayarak veri kaynakları da yapılandırabilirsiniz.

![Veri Kaynakları penceresi](../data-tools/media/raddata-data-sources-window.png)

Görüntülenen her bir veri türü için **veri kaynakları** penceresinde varsayılan denetim öğeyi tasarımcıya sürüklediğinizde oluşturulur. Bir öğe sürüklemeden önce **veri kaynakları** penceresinde oluşturulan denetimi değiştirebilirsiniz. Daha fazla bilgi için [veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="tasks-involved-in-binding-controls-to-data"></a>Denetimleri verilere bağlamada kullanılan görevler

Aşağıdaki tablo bazı listeler denetimleri verilere bağlamak için gerçekleştirdiğiniz en yaygın görevleri.

|Görev|Daha fazla bilgi|
|----------| - |
|Açık **veri kaynakları** penceresi.|Bir tasarım yüzeyine Düzenleyicisi'nde açın ve seçin **görünümü** > **veri kaynakları**.|
|Bir veri kaynağını projenize ekleyin.|[Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)|
|Bir öğe sürüklerken oluşturulan denetimi ayarlama **veri kaynakları** penceresinden tasarımcıya.|[Deneti veri kaynakları penceresinden sürüklendiğinde oluşturulacak şekilde ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|Öğelerle ilişkili denetimlerin listesini değiştirin **veri kaynakları** penceresi.|[Veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|Verilere bağlı denetimler oluşturun.|[Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)|
|Bir nesnede veya koleksiyonda bağlayın.|[Visual Studio'da nesne bağlama](../data-tools/bind-objects-in-visual-studio.md)|
|Kullanıcı Arabiriminde görüntülenen verileri filtreleyin.|[Bir Windows Forms uygulamasındaki verileri filtreleme ve sıralama](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|Açıklamalı alt yazılar denetimleri için özelleştirin.|[Visual Studio'nun verilere bağlı denetimler için başlık oluşturma biçimini özelleştirme](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Windows Forms veri bağlama](/dotnet/framework/winforms/windows-forms-data-binding)