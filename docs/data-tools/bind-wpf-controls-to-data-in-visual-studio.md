---
title: -1. Bölüm verilere WPF denetimleri bağlama
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
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4fa8ddf42cad6ad613846ceff2b49739b7dc1c18
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305344"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Visual Studio'da verilere WPF denetimleri bağlama

Bağlayarak uygulamanızın kullanıcılarına veri gösterebilirsiniz [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] kontrol eder. Bu verilere bağlı denetimler oluşturmak için öğeleri sürükleyebilirsiniz **veri kaynakları** penceresinden [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] Visual Studio'da. Bu konuda en yaygın görevleri, araçları ve verilere bağlı oluşturmak için kullanabileceğiniz sınıfların bazılarını açıklar [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] uygulamalar.

Visual Studio'da verilere bağlı denetimler oluşturma hakkında genel bilgi için bkz. [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md). Hakkında daha fazla bilgi için [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] veri bağlaması bkz [Data Binding Overview](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>WPF denetimlerini verilere bağlamada kullanılan görevler

Aşağıdaki tabloda sürükleyerek gerçekleştirilebilir görevleri listeler **veri kaynakları** penceresine [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].

|Görev|Daha fazla bilgi|
|----------| - |
|Yeni verilere bağlı denetimler oluşturun.<br /><br /> Varolan denetimleri verilere bağlayın.|[Bir veri kümesine WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Bir üst-alt ilişkisinde ilgili verileri görüntüleyen denetimler oluşturma: Kullanıcı bir denetimde üst veri kaydını seçtiğinde, bir diğer denetim seçili kayıt ile ilgili alt verileri görüntüler.|[WPF uygulamalarındaki ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md)|
|Oluşturma bir *arama tablosu* bir tablodaki başka bir tablodaki bir yabancı anahtar alanının değere göre görüntüler.|[WPF uygulamalarında arama tabloları oluşturma](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Veritabanında bir denetimi görüntüye bağlayın.|[Bir veritabanından resimlere denetim bağlama](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Geçerli bırakma hedefleri

Öğeleri sürükleyebilirsiniz **veri kaynakları** içindeki geçerli bırakma hedeflerine yalnızca penceresine [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]. İki tür geçerli bırakma hedefi vardır: kapsayıcılar ve denetimler. Kapsayıcı, genellikle denetimleri içeren bir kullanıcı arabirimi öğesidir. Örneğin, bir kılavuz bir kapsayıcıdır ve dolasıyla da bir penceredir.

## <a name="generated-xaml-and-code"></a>Oluşturulan XAML ve kod

Bir öğeyi sürüklediğinizde **veri kaynakları** penceresine [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)], Visual Studio'nun oluşturduğu [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] , yeni bir veri bağlı denetim tanımlayan (veya varolan bir denetimi veri kaynağına bağlar). Bazı veri kaynakları için Visual Studio kod veri kaynağını verilerle dolduran arka plan kod dosyasında da oluşturur.

Aşağıdaki tabloda [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] ve Visual Studio'nun her veri kaynağı türü için oluşturduğu kod **veri kaynakları** penceresi.

| Veri kaynağı | Bir denetimi veri kaynağına bağlayan XAML oluşturma | Veri kaynağını verilerle dolduran kod oluşturma |
| - | - | - |
| Veri kümesi | Evet | Evet |
| [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] | Evet | Evet |
| Hizmet | Evet | Hayır |
| Nesne | Evet | Hayır |

### <a name="datasets"></a>Veri kümeleri

Bir tabloyu veya sütunu sürüklediğinizde **veri kaynakları** Tasarımcı, Visual Studio penceresine oluşturur [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] aşağıdakileri yapar:

-   Veri kümesi ve yeni bir ekler <xref:System.Windows.Data.CollectionViewSource> öğeyi sürüklediğiniz kapsayıcının kaynaklarına için. <xref:System.Windows.Data.CollectionViewSource> Gidin ve veri kümesindeki verileri görüntülemek için kullanılan bir nesnedir.

-   Denetim için bir veri bağlama oluşturur. Öğeyi tasarımcıda varolan bir denetime sürüklerseniz, XAML denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz, XAML sürüklenen öğe için seçilmiş olan denetimi oluşturur ve denetimi öğeye bağlar. Denetim içinde yeni oluşturulan <xref:System.Windows.Controls.Grid>.

Visual Studio arka plan kod dosyasında aşağıdaki değişiklikleri de yapar:

- Oluşturur bir <xref:System.Windows.FrameworkElement.Loaded> için olay işleyicisi [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] denetimi içeren öğe. Olay işleyicisi tabloyu verilerle alır doldurur <xref:System.Windows.Data.CollectionViewSource> kapsayıcının kaynakları ve yapar sonra ilk veri öğesini geçerli öğe. Varsa bir <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi zaten varsa, Visual Studio bu kodu varolan olay işleyicisine ekler.

### <a name="entity-data-models"></a>Varlık veri modelleri

Bir varlığı veya varlık özelliğini sürüklediğinizde **veri kaynakları** Tasarımcı, Visual Studio penceresine oluşturur [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] aşağıdakileri yapar:

- Yeni bir ekler <xref:System.Windows.Data.CollectionViewSource> öğeyi sürüklediğiniz kapsayıcının kaynaklarına için. <xref:System.Windows.Data.CollectionViewSource> Gidin ve varlıktaki verileri görüntülemek için kullanılan bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi tasarımcıda varolan bir denetime sürüklerseniz [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] denetimi oluşturur sürüklenen öğe için seçilmiş ve denetimi öğeye bağlar. Denetim içinde yeni oluşturulan <xref:System.Windows.Controls.Grid>.

Visual Studio arka plan kod dosyasında aşağıdaki değişiklikleri de yapar:

- Tasarımcıya sürüklediğiniz varlık (veya tasarımcıya sürüklediğiniz özelliği içeren varlık) için bir sorgu döndüren yeni bir yöntem ekler. Yeni yöntem adına sahip `Get<EntityName>Query`burada `\<EntityName>` varlığın adıdır.

- Oluşturur bir <xref:System.Windows.FrameworkElement.Loaded> için olay işleyicisi [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] denetimi içeren öğe. Olay işleyicisi çağrılarını `Get<EntityName>Query` varlığı verilerle doldurmak için yöntemi alır <xref:System.Windows.Data.CollectionViewSource> kapsayıcının kaynakları ve yapar sonra ilk veri öğesini geçerli öğe. Varsa bir <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi zaten varsa, Visual Studio bu kodu varolan olay işleyicisine ekler.

### <a name="services"></a>Hizmetler

Bir hizmet nesnesini veya özelliği sürüklediğinizde **veri kaynakları** Tasarımcı, Visual Studio penceresine oluşturur [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] verilere bağlı bir denetim oluşturur (veya varolan bir denetimi nesneye veya özelliğe bağlar). Ancak, Visual Studio proxy hizmeti nesnesini verilerle dolduran kod oluşturmaz. Bu kodu kendiniz yazmalısınız. Bunun nasıl yapılacağını gösteren bir örnek için bkz: [denetimleri bir WCF veri hizmetine WPF bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

Visual Studio aşağıdakileri yapan XAML oluşturur:

- Yeni bir ekler <xref:System.Windows.Data.CollectionViewSource> öğeyi sürüklediğiniz kapsayıcının kaynaklarına. <xref:System.Windows.Data.CollectionViewSource> Gidin ve hizmet tarafından döndürülen nesnedeki verileri görüntülemek için kullanılan bir nesnedir.

- Denetim için bir veri bağlama oluşturur. Öğeyi tasarımcıda varolan bir denetime sürüklerseniz [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] denetimi oluşturur sürüklenen öğe için seçilmiş ve denetimi öğeye bağlar. Denetim içinde yeni oluşturulan <xref:System.Windows.Controls.Grid>.

### <a name="objects"></a>Nesneler

Bir nesneyi veya özelliği sürüklediğinizde **veri kaynakları** Tasarımcı, Visual Studio penceresine oluşturur [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] verilere bağlı bir denetim oluşturur (veya varolan bir denetimi nesneye veya özelliğe bağlar). Ancak, Visual Studio nesneyi verilerle doldurmak için kod oluşturmaz. Bu kodu kendiniz yazmalısınız.

> [!NOTE]
> Özel sınıflar genel olmalıdır ve, varsayılan olarak, parametresiz bir oluşturucusu vardır. Bunlar sözdizimlerinde "dot" sahip iç içe geçmiş can'tbe sınıflar. Daha fazla bilgi için [XAML ve özel sınıflar için WPF](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf).

Visual Studio'nun oluşturduğu [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] aşağıdakileri yapar:

-   Yeni bir ekler <xref:System.Windows.Data.CollectionViewSource> öğeyi sürüklediğiniz kapsayıcının kaynaklarına. <xref:System.Windows.Data.CollectionViewSource> Gidip nesnedeki verileri görüntülemek için kullanılan bir nesnedir.

-   Denetim için bir veri bağlama oluşturur. Öğeyi tasarımcıda varolan bir denetime sürüklerseniz, XAML denetimi öğeye bağlar. Öğeyi bir kapsayıcıya sürüklerseniz, XAML sürüklenen öğe için seçilmiş olan denetimi oluşturur ve denetimi öğeye bağlar. Denetim içinde yeni oluşturulan <xref:System.Windows.Controls.Grid>.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)