---
title: Depo Görüntüleyiciyi Kullanarak Hata Ayıklama
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: d26c66b6bcbab2eafe2ae8b01597ef09985dcfa8
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47858658"
---
# <a name="debugging-by-using-the-store-viewer"></a>Depo Görüntüleyiciyi Kullanarak Hata Ayıklama
Store Görüntüleyici ile durumunu inceleyebilirsiniz bir *depolamak* tarafından kullanılan [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. Store Görüntüleyici öğesi özellikleri ve öğeleri arasında bağlantılar ile birlikte, belirli bir depolama alanında bulunan tüm etki alanı model öğeleri görüntüler.

## <a name="opening-store-viewer"></a>Açılış Store Görüntüleyicisi
 Visual Studio deneysel yapı olduğunda, kodunuz bir kesme noktasında burada depolama örneği model bilgileri içeren durdurun. Ardından, aşağıdaki komutu yazarak Store Görüntüleyicisi'ni açın **hemen** penceresi:

```csharp
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);
```

> [!NOTE]
>  Değiştirmeniz gereken `mystore` deposu örneğinizin adı. Ayrıca, ad alanı kodunuza ekleyin, tam nitelikli ad Store Görüntüleyicisi'ni görüntülemek için komutu yazabilirsiniz:
>
>  `using Microsoft.VisualStudio.Modeling.Diagnostics;`
>
>  `...`
>
>  `StoreViewer.Show(mystore);`

 `Show` Yöntemi olan çeşitli aşırı yükler. Bir mağaza veya bir bölümleme örneği parametre olarak belirtebilirsiniz.

 Alternatif olarak, Store Görüntüleyicisi kodunuzdaki herhangi bir yere görüntüler kod satırının koyabilirsiniz burada geçirdiğiniz parametre `Show` kapsamda bir yöntemdir. Bu eylem, kod satırının bir anlık görüntüsünü deposunun içeriğini yürütüldüğünde Store Görüntüleyicisi'ni görüntüler.

### <a name="using-store-viewer"></a>Store Görüntüleyicisi'ni kullanma
 Store Görüntüleyicisi oturum açtığında, engelleyici olmayan bir Windows Forms pencere, aşağıdaki çizimde gösterildiği gibi görünür.

 ![](../modeling/media/storeviewer2.png) Store Görüntüleyicisi

 Store Görüntüleyicisi üç bölme vardır: sol bölmesinde, sağ üst bölmesi ve sağ alt bölmesi. Sol bölmede türlerini ağaç görünümünde olduğunu `DomainDataDirectory` mağaza üyesi. Ve bölüm düğümünü genişletin ve bir öğeyi tıklatın, öğenin özellikler sağ üst bölmede görünür. Öğenin diğer öğelere bağlı ise, ek öğeler sağ alt bölmede görünür. Öğesi, öğenin sağ alt bölmede çift tıklarsanız, sol bölmede vurgulanır.

## <a name="see-also"></a>Ayrıca Bkz.

- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)