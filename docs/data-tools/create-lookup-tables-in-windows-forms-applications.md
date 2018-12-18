---
title: Windows Forms uygulamalarında arama tabloları oluşturma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c52e5f157dcbc6dcfeacf72df465bd3d8d9d172e
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304942"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Windows Forms uygulamalarında arama tabloları oluşturma

Terim *arama tablosu* iki ilgili veri tablolarına bağlı denetimler açıklar. Bu arama denetimleri, ikinci tabloda seçilen bir değere göre ilk tablosundan verileri görüntülemek.

Arama tabloları üst tablonun ana düğüm sürükleyerek oluşturabilirsiniz (gelen [veri kaynakları penceresi](add-new-data-sources.md#data-sources-window)) üzerine formunuzdaki ilgili alt tablo sütununda zaten bağlı bir denetim.

Örneğin, bir tablo düşünün `Orders` satış veritabanındaki. Her kayıtta `Orders` tablo içeren bir `CustomerID`, siparişi hangi müşterinin verdiğini gösteren. `CustomerID` Bir müşteri kaydı işaret eden bir yabancı anahtar `Customers` tablo. Bu senaryoda, genişletme `Orders` tablosundaki **veri kaynakları** penceresi ve ana düğüm kümesine **ayrıntıları**. Ardından, `CustomerID` kullanılacak sütunu bir <xref:System.Windows.Forms.ComboBox> (veya arama bağlamayı destekleyen başka bir denetimi) sürükleyin `Orders` formunuza düğümü. Son olarak, sürükleyin `Customers` ilgili sütuna bağlı denetim düğüme — bu durumda, <xref:System.Windows.Forms.ComboBox> bağlı `CustomerID` sütun.

## <a name="to-databind-a-lookup-control"></a>Veri bağlama için bir arama denetimi

1.  Projenizi açın, açın **veri kaynakları** penceresini seçerek **görünümü** > **diğer Windows** > **verikaynakları**.

    > [!NOTE]
    > Arama tabloları gerektiren iki ilişkili tablolar veya nesnelerin kullanılabilir olduğunu **veri kaynakları** penceresi. Daha fazla bilgi için [veri kümelerindeki ilişkiler](relationships-in-datasets.md).

2.  Ait düğümleri genişletebilirsiniz **veri kaynakları** üst tablo ve tüm alt sütunları ve ilgili alt tablo ve sütunları görene kadar penceresi.

    > [!NOTE]
    > Alt tablo düğümü üst tablo bir Genişletilebilir alt düğüm olarak görünen düğümüdür.

3.  Alt tablo için bırakma türünü değiştirme **ayrıntıları** seçerek **ayrıntıları** alt tablonun düğümde denetim listesinden. Daha fazla bilgi için [veri kaynakları penceresinden sürüklendiğinde oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4.  İki tablo ilişkili düğümü bulun ( `CustomerID` önceki örnekte düğümü). Bırakma türünü değiştirin bir <xref:System.Windows.Forms.ComboBox> seçerek **ComboBox** denetim listesinden.

5.  Ana alt tablo düğümünden sürükleyin **veri kaynakları** formunuza penceresi.

     Veriye bağlı denetimler (tanımlayıcı etiketlerle) ve bir aracı (<xref:System.Windows.Forms.BindingNavigator>) formda görünür. A [veri kümesi](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

6.  Artık, ana üst tablo düğümünden sürükleyin **veri kaynakları** penceresinden doğrudan arama denetimi ( <xref:System.Windows.Forms.ComboBox>).

     Arama bağlamaları artık oluşturulur. Denetimde ayarlanan belirli özellikleri için aşağıdaki tabloya bakın.

    |Özellik|Ayar açıklaması|
    |--------------| - |
    |**Veri kaynağı**|Visual Studio bu özelliği ayarlar <xref:System.Windows.Forms.BindingSource>, denetimin sürükleyin tablosu için oluşturulmuş (başlangıcı yerine sonundan <xref:System.Windows.Forms.BindingSource>, denetimin oluşturduğunuzda oluşturulan).<br /><br /> Ayarlama yapmanız gerekirse, bu ayar <xref:System.Windows.Forms.BindingSource> görüntülemek istediğiniz sütun içeren tablo.|
    |**DisplayMember**|Visual Studio bu özellik, bir dize veri türü denetimi sürükleyin tablosu için birincil anahtar sonra ilk sütuna ayarlar.<br /><br /> Bir düzeltme yapmak ihtiyacınız varsa, bu görüntülemek istediğiniz sütun adına ayarlayın.|
    |**ValueMember**|Visual Studio bu özellik anahtarı yok tanımlanmışsa, birincil anahtarda yer alan ilk sütunun veya tablonun ilk sütunda ayarlar.<br /><br /> Bir düzeltme yapmak ihtiyacınız varsa, bu görüntülemek istediğiniz sütunu tablonun birincil anahtarı ayarlayın.|
    |**SelectedValue**|Visual Studio düşürülmüştür özgün sütun için bu özelliği ayarlar **veri kaynakları** penceresi.<br /><br /> Bir düzeltme yapmak istiyorsanız, bunu ilgili tablosundaki yabancı anahtar sütunu ayarlayın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)