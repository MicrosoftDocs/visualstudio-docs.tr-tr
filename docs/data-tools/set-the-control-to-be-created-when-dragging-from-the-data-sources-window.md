---
title: Veri Kaynakları penceresinden sürüklendiğinde denetimin oluşturulmasını ayarlama
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: daceedd2709de7882ecff5b29a657f706c96175d
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305474"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Veri Kaynakları penceresinden sürüklendiğinde denetimin oluşturulmasını ayarlama

Öğe sürükleyerek veriye bağlı denetimler oluşturabilirsiniz **veri kaynakları** penceresinden WPF tasarımcısına veya Windows Form Tasarımcısı. Her öğe **veri kaynakları** penceresine sahip tasarımcıya sürüklediğinizde varsayılan denetim oluşturulur. Ancak, farklı bir denetim oluşturmak seçebilirsiniz.

## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Veri tabloları veya nesneler için oluşturulacak denetimleri ayarlayın

Veri tabloları veya nesneleri temsil eden bir öğe sürüklemeden önce **veri kaynakları** penceresinde tüm verileri bir denetimi görüntüleme ya da her bir sütun veya özelliği ayrı bir denetimde görüntülenecek seçebilirsiniz.

Bu bağlamda terimi *nesne* bir özel iş nesnesi, bir varlık (bir varlık veri modeli) veya bir hizmet tarafından döndürülen bir nesneye başvuruyor.

### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>Veri tabloları veya nesneler için oluşturulacak denetimleri ayarlamak için

1. Mutlaka **WPF** Tasarımcısı veya **Windows Forms** Tasarımcısı açıksa.

2. İçinde **veri kaynakları** penceresinde veri tablosunu temsil eden bir öğe seçin ya da ayarlamak istediğiniz nesne.

   > [!TIP]
   > Varsa **veri kaynakları** penceresi açık değilse, bunu seçerek açabilirsiniz **görünümü** > **diğer Windows** > **verikaynakları**.

3. Öğeyi aşağı açılan menüsüne tıklayın ve ardından menüde aşağıdaki öğeleri biri:

    - Her veri alanı ayrı bir denetimde görüntülemek için tıklatın **ayrıntıları**. Bu eylem, veri öğesi tasarımcıya sürüklediğinizde, her bir sütun veya üst veri tablosu veya nesnenin her denetim için etiket özelliği için farklı bir veriye bağlı denetim oluşturacaksınız.

    - Tüm verileri tek bir denetimde görüntülemek için farklı bir denetim listesinde, gibi seçin **DataGrid** veya **listesi** bir WPF uygulamasında veya **DataGridView** Windows Forms'ta uygulama.

    Mevcut denetimlerin listesinin hangi tasarımcıda sahip olduğunuz açık, .NET Framework'ün hangi sürümünün projenizin hedeflediği bağlıdır ve olup özel eklediğiniz bağlama söz konusu destek veri denetimleri **araç kutusu**. Oluşturmak istediğiniz denetimi kullanılabilir denetimleri listesinde değilse, denetim listesine ekleyebilirsiniz. Daha fazla bilgi için [veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md).

    Veri tabloları veya nesneleri için denetim listesini eklenebilen özel bir Windows Forms denetimi oluşturma hakkında bilgi edinmek için **veri kaynakları** penceresinde görmek [karmaşık veri destekleyen bir Windows Forms kullanıcı denetimi oluşturma Bağlama](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).

## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Veri sütunları veya özellikleri için oluşturulacak denetimleri ayarlayın

Bir sütun veya bir nesneyi bir özelliği temsil eden bir öğe sürüklemeden önce **veri kaynakları** penceresinden tasarımcıya, oluşturulacak denetimi ayarlayabilirsiniz.

### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>Sütun veya özellikleri için oluşturulacak denetimleri ayarlamak için

1. Mutlaka **WPF** Tasarımcısı veya **Windows Forms** Tasarımcısı açıksa.

2. İçinde **veri kaynakları** penceresinde istediğiniz tabloyu genişletin veya kendi sütunları veya özelliklerini görüntülemek için nesne.

3. Oluşturulacak denetimi ayarlamak istediğiniz her sütun veya özelliği seçin.

4. Sütun veya özellik açılan menüsüne tıklayın ve ardından öğeyi tasarımcıya sürüklediğinizde oluşturmak istediğiniz denetimi seçin.

     Projenizin hedeflediği açık, .NET Framework'ün hangi sürümünün sahip hangi tasarımcıda mevcut denetimlerin listesinin bağlıdır ve hangi özel denetimleri için veri bağlama, eklediğiniz destekleyen **araç kutusu**. Oluşturmak istediğiniz denetim mevcut denetimlerin listesinin içinde ise, denetim listesine ekleyebilirsiniz. Daha fazla bilgi için [veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md).

     Veri sütunları ya da özelliği için denetim listesini eklenebilen özel bir denetimin nasıl oluşturulacağını öğrenmek için **veri kaynakları** penceresinde görmek [BasitveribağlamayıdestekleyenbirWindowsFormskullanıcıdenetimioluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).

     Sütun veya özellik için bir denetim oluşturmak istemiyorsanız, seçin **hiçbiri** açılan menüsünde. Bu, üst tablo veya nesne tasarımcıya sürükleyerek istediğiniz, ancak belirli bir sütun veya özellik eklemek istiyor musunuz kullanışlıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)