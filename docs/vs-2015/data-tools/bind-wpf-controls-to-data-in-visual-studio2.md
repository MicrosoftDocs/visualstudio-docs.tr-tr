---
title: Verilere WPF denetimleri bağlama | Microsoft Docs
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
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6cf08391084fdcfd5236212d098b25130aadcda7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53054702"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Visual Studio'da verilere WPF denetimleri bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veri bağlama oluşturabilirsiniz [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] kullanarak denetimleri **veri kaynakları** penceresi. İlk olarak, bir veri kaynağına ekleme **veri kaynakları** penceresi. Ardından, öğeleri sürükleyin **veri kaynakları** penceresine**WPF Tasarımcısı**.

##  <a name="adding"></a> Bir veri kaynağı veri kaynakları penceresine ekleme
 Verilere bağlı denetimler oluşturabilmeniz için önce bir veri kaynağına eklemelisiniz **veri kaynakları** penceresi.

#### <a name="to-add-a-data-source-to-the-data-sources-window"></a>Veri kaynakları penceresine bir veri kaynağı eklemek için

1.  Üzerinde **görünümü** menüsünde **diğer Windows**ve ardından **veri kaynakları**.

2.  Tıklayın **yeni veri kaynağı Ekle**ve tamamlayın **veri kaynağı yapılandırması** Sihirbazı.

3.  Verilere bağlı denetimler oluşturmak için aşağıdaki görevlerden birini gerçekleştirin:

    -   [Denetim oluşturma tek bir veri alanı için bağlı](#simple).

    -   [Denetim oluşturma birden fazla veri alanlarına bağlı](#complex).

    -   [Bir dizi denetimi oluşturma birden fazla veri alanlarına bağlı](#details).

    -   [Tasarımcıda varolan denetimlere veri bağlama](#existing).

##  <a name="simple"></a> Tek bir veri alanı için bağlı bir denetim oluşturma
 Bir veri kaynağına ekledikten sonra **veri kaynakları** penceresinde gibi tek bir alan veri görüntüleyen yeni bir verilere bağlı denetim oluşturabileceğiniz bir <xref:System.Windows.Controls.ComboBox> veya <xref:System.Windows.Controls.TextBox>.

#### <a name="to-create-a-control-that-is-bound-to-a-single-field-of-data"></a>Tek bir veri alanı için bağlı bir denetim oluşturmak için

1.  İçinde **veri kaynakları** penceresinde bir tablo veya bir nesneyi temsil eden bir öğeyi genişletin. Sütun veya bağlamak istediğiniz bir özellik temsil eden alt öğeyi bulun. Görsel bir örnek için bkz: [veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2.  İsteğe bağlı olarak oluşturmak için denetimi seçin. Her öğe **veri kaynakları** penceresine sahip öğeyi tasarımcıya sürüklediğinizde varsayılan denetim oluşturulur. Varsayılan Denetim öğesi temel alınan veri türüne göre değişir.

     Farklı bir denetimi seçmek için öğesinin yanındaki açılan oka tıklayın ve bir denetim seçin. Daha fazla bilgi için [veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

3.  Geçerli bir kapsayıcıya Tasarımcısı'nda öğeyi sürükleyin. Geçerli kapsayıcıları hakkında daha fazla bilgi için bkz. [Visual Studio'da veri bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Yeni veri bağlı denetim ve uygun şekilde başlıklı oluşturur <xref:System.Windows.Controls.Label> kapsayıcısında. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ayrıca oluşturur [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] ve denetimini verilere bağlama için kod. Daha fazla bilgi için [Visual Studio'da veri bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

##  <a name="complex"></a> Birden fazla veri alanlarına bağlı bir denetim oluşturma
 Bir veri kaynağına ekledikten sonra **veri kaynakları** penceresinde oluşturabileceğiniz gibi verilerin birden çok alan görüntüleyen yeni bir verilere bağlı denetim bir <xref:System.Windows.Controls.DataGrid> veya <xref:System.Windows.Controls.ListView>.

#### <a name="to-create-a-control-that-is-bound-to-multiple-fields-of-data"></a>Birden fazla veri alanlarına bağlı bir denetim oluşturmak için

1.  İçinde **veri kaynakları** penceresinde, bir tablo veya nesne temsil eden öğeyi seçin. Görsel bir örnek için bkz: [veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2.  İsteğe bağlı olarak oluşturmak için denetimi seçin. Varsayılan olarak, her öğesi **veri kaynakları** veri tablosu veya nesneyi temsil eden pencere oluşturmak için ayarlanmış bir <xref:System.Windows.Controls.DataGrid> (projeniz .NET Framework 4 hedefliyse) veya <xref:System.Windows.Controls.ListView> (için .NET Framework'ün önceki sürümler).

     Farklı bir denetimi seçmek için öğesinin yanındaki açılan oka tıklayın ve bir denetim seçin. Daha fazla bilgi için [veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    > [!NOTE]
    >  Belirli bir sütun veya özellik görüntülenecek istemiyorsanız, alt öğelerini görüntülemek için öğeyi genişletin. Sütun veya görüntüler ve ardından istemediğiniz özelliğin yanındaki açılan oka tıklayın **hiçbiri**.

3.  Öğeyi Tasarımcısı'nda geçerli bir kapsayıcı gibi sürüklemek bir <xref:System.Windows.Controls.Grid>. Geçerli kapsayıcıları hakkında daha fazla bilgi için bkz. [Visual Studio'da veri bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Yeni veri bağlı denetim kapsayıcıda oluşturur. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ayrıca oluşturur [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] ve denetimini verilere bağlama için kod. Daha fazla bilgi için [Visual Studio'da veri bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

##  <a name="details"></a> Birden fazla veri alanlarına bağlı denetimler kümesi oluşturma
 Bir veri kaynağına ekledikten sonra **veri kaynakları** penceresinde bir dizi denetimi için bir veri tablosu veya nesne bağlayabilirsiniz. Her bir sütun veya tablo veya nesne özelliği için farklı bir denetim oluşturulur.

#### <a name="to-create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a>Birden fazla veri alanlarına bağlı denetimler oluşturmak için

1.  İçinde **veri kaynakları** penceresinde, bir tablo veya nesne temsil eden öğeyi seçin. Görsel bir örnek için bkz: [veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2.  Seçin ve öğe yanındaki açılan oka tıklayın **ayrıntıları**.

    > [!NOTE]
    >  Belirli bir sütun veya özellik görüntülenecek istemiyorsanız, alt öğelerini görüntülemek için öğeyi genişletin. Sütun veya görüntüler ve ardından istemediğiniz özelliğin yanındaki açılan oka tıklayın **hiçbiri**.

3.  Öğeyi Tasarımcısı'nda geçerli bir kapsayıcı gibi sürüklemek bir <xref:System.Windows.Controls.Grid>. Geçerli kapsayıcıları hakkında daha fazla bilgi için bkz. [Visual Studio'da veri bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yeni verilere bağlı denetimler kapsayıcıda oluşturur. Her denetim, farklı bir sütun veya özelliğe bağlıdır ve her bir denetimin eşlik uygun şekilde başlıklı tarafından <xref:System.Windows.Controls.Label> denetimi. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ayrıca oluşturur [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] ve denetimleri verilere bağlamak için kodu. Daha fazla bilgi için [Visual Studio'da veri bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

##  <a name="existing"></a> Binddata Tasarımcısı'nda mevcut denetimleri için
 Bir veri kaynağına ekledikten sonra **veri kaynakları** penceresinde bir veri tasarımcıda varolan bir denetime bağlama ekleyebilirsiniz.

#### <a name="to-bind-data-to-an-existing-control-in-the-designer"></a>Veri Tasarımcısı'nda varolan bir denetime bağlamak için

1.  İçinde **veri kaynakları** penceresinde, aşağıdaki yordamlardan birini kullanın:

    -   Veri bağlama gibi birden çok alan verileri görüntüleyen varolan bir denetime eklemek için bir <xref:System.Windows.Controls.DataGrid> veya <xref:System.Windows.Controls.ListView>, tabloyu temsil eden öğeyi seçin veya denetime bağlamak istediğiniz nesne.

    -   Veri bağlama gibi tek bir alan veri görüntüleyen varolan bir denetime eklemek için bir <xref:System.Windows.Controls.ComboBox> veya <xref:System.Windows.Controls.TextBox>, tabloyu veya verileri içeren bir nesneyi temsil eden öğesini genişletin ve ardından istediğiniz verileri temsil eden öğeyi seçin denetime bağlama.

2.  Seçili öğe sürüklemeden **veri kaynakları** tasarımcıda varolan bir denetime penceresinden. Denetim geçerli bırakma hedefi olması gerekir. Daha fazla bilgi için [Visual Studio'da veri bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oluşturur [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] ve denetimini verilere bağlama için kod. Daha fazla bilgi için [Visual Studio'da veri bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

    > [!NOTE]
    >  Denetim verileri zaten bağlıysa, veri bağlama denetimi için denetimin en son sürüklenen öğeye sıfırlanır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [WPF uygulamalarında arama tabloları oluşturma](../data-tools/create-lookup-tables-in-wpf-applications.md) [WPF uygulamalarında ilgili verileri görüntüleyen](../data-tools/display-related-data-in-wpf-applications.md) [denetimleriverikümesineWPFbağlama](../data-tools/bind-wpf-controls-to-a-dataset.md) [Denetimleri bir WCF veri hizmetine WPF bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) [izlenecek yol: WPF uygulamasında ilgili verileri görüntüleme](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
