---
title: Bir veritabanından resimlere denetim bağlama
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d93ca95a67bc3816d8d65a799282dc6c7969e093
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304929"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Bir veritabanından resimlere denetim bağlama

Kullanabileceğiniz **veri kaynakları** görüntü uygulamanızda bir denetimin bir veritabanına bağlamak için penceresi. Örneğin, bir görüntüye bağlayabilirsiniz bir <xref:System.Windows.Controls.Image> WPF uygulamasında veya çok denetleyen bir <xref:System.Windows.Forms.PictureBox> denetimini Windows Forms uygulamasında.

Bir veritabanı resimleri genellikle bayt dizisi depolanır. Öğeler **veri kaynakları** bayt dizileri türü denetimi gibi depolanmış penceresini ayarlamak **hiçbiri** varsayılan olarak, her şey basit bir yürütülebilir dosyanın bir bayt dizisi bayt dizileri içerebileceğinden büyük bir uygulama. Bir bayt dizisi öğesinde veriye bağlı denetim oluşturmak için **veri kaynakları** bir resmi temsil eden pencere oluşturmak için denetimi seçmesi gerekir.

Aşağıdaki yordam olduğunu varsayar **veri kaynakları** penceresi görüntüye bağlı bir öğe ile önceden doldurulur.

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Resim denetimi bir veritabanına bağlamak için

1.  Tasarım yüzeyinde denetime eklemek istediğiniz WPF Tasarımcısı veya Windows Forms Tasarımcısı'nda açık olduğundan emin olun.

2.  İçinde **veri kaynakları** penceresinde istediğiniz tabloyu genişletin veya kendi sütunları veya özelliklerini görüntülemek için nesne.

   > [!TIP]
   > Varsa **veri kaynakları** penceresi açık değilse, seçerek açın **görünümü** > **diğer Windows** > **veri kaynakları**.

3.  Sütun veya görüntü verilerinizi içeren bir özellik seçin ve kendi denetimi aşağı açılan listeden aşağıdaki denetimlerden birini seçin:

    - WPF Tasarımcısı açıksa seçin **görüntü**.

    - Windows Forms Tasarımcısı açıksa seçin **PictureBox**.

    - Alternatif olarak, veri bağlamayı destekleyen ve resimleri görüntülemek farklı bir denetimi seçebilirsiniz. Kullanmak istediğiniz denetim kullanılabilir denetimleri listesinde değilse, listeye ekleyin ve ardından bu seçeneği belirleyin. Daha fazla bilgi için [veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)