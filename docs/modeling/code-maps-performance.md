---
title: Kod haritaları yavaş
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 2dece1e63fffdba67678422ad9241babc63b7abd
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34267705"
---
# <a name="improve-performance-for-code-maps"></a>Kod haritaları performansını

İlk kez bir harita oluşturduğunuzda, Visual Studio bulduğu tüm bağımlılıkları dizinler. Bu işlem özellikle büyük çözümler için biraz zaman alabilir ancak sonraki performansını artırır. Kodunuzu değişirse, Visual Studio yalnızca güncelleştirilmiş kod reindexes. Harita işleme tamamlamak geçen süre en aza indirmek için aşağıdaki önerileri göz önünde bulundurun:

- [Sizi ilgilendiren bağımlılıkları eşleme.](#create-a-code-map-to-see-specific-dependencies)

- Çözümün tamamında harita oluşturmadan önce çözüm kapsamını azaltır.

- Seçerek otomatik derleme çözümü için devre dışı bırakma **Atla yapı** kod Haritası araç.

- Otomatik üst öğelerinin seçerek eklemek devre dışı bırakma **dahil üst** kod Haritası araç.

   ![Derleme ve dahil üst düğmeleri atla](../modeling/media/codemapsfilterskipbuildicons.png)

- Doğrudan düğümleri ve gerekli olmayan bağlantıları kaldırmak için kod Haritası dosyasını düzenleyin. Harita değiştirme, arka plandaki kod etkilemez. Bkz: [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

Eşlemeleri oluşturmak veya bir eşlemesinden öğeler eklemek için daha fazla zaman alabilir **Çözüm Gezgini** bir proje öğesi, kullanıcının **çıktı dizinine Kopyala** özelliği ayarlanmış **her zaman Kopyala**. Performansı artırmak için bu özelliği değiştirmek **yeniyse Kopyala** veya `PreserveNewest`. Bkz: [artımlı derlemeler](../msbuild/incremental-builds.md).

Tamamlanan eşlemesini yalnızca başarıyla yerleşik kod bağımlılıkları gösterir. Derleme hataları belirli bileşenler meydana gelirse, bu hataları harita üzerinde görünür. Bir bileşenin gerçekten oluşturur ve haritada temel mimari kararlar önce bağımlılıkları olduğundan emin olun.