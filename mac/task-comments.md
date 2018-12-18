---
title: Görev açıklamaları
description: Kodunuza Görev açıklamalarını ekleme
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 3caef73ba46afd8eaf90826540248cb2d5c4efef
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294285"
---
# <a name="task-comments"></a>Görev açıklamaları

Kod yazarken, tamamlanmamış veya şüpheli kod veya uyarılar ile Hızlı çözümler açıkça açıklama standart bir uygulamadır. Mac için Visual Studio tarafından sağlanan varsayılan sinyal TODO, HACK, FIXME ve UNDONE belirteçleridir. Kişiselleştirilmiş belirteçleri altında tanımlanabilir **Visual Studio > Tercihler > ortam > görevleri**aşağıdaki görüntüde gösterildiği gibi:

![Görev listesi tercihleri](media/source-editor-image10.png)

Yeni görev açıklama eklemek için görev anahtar sözcüğü içeren bir açıklama ekleyin. Örneğin:

```csharp
//TODO: Finish this for all properties.
```

Mac için Visual Studio bunları vurgulayarak bu işaretleyicileri dikkat çizer **görev listesi** giderek görüntülenebilen paneli **Görüntüle > doldurmalar > görev**:

![Görev listesi paneli](media/source-editor-image11.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Görev listesi (Windows için Visual Studio) kullanın](/visualstudio/ide/using-the-task-list)