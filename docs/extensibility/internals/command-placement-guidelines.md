---
title: Komut yerleştirme yönergeleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bac09a361c885d866bf6a78e6fe7b49c246265ba
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511192"
---
# <a name="command-placement-guidelines"></a>Komut yerleştirme yönergeleri
Visual Studio tümleşik geliştirme ortamında (IDE) komutları konumlandırma için en iyi komut kümesi boyutuna bağlı olarak değişir. Komutları tanımlanır ve bilgileri göre yerleştirilmiş *.vsct* dosyaları.  
  
## <a name="best-practices-for-all-command-sets"></a>Tüm komut kümesi için en iyi uygulamalar  
 Her komut kümesi için aşağıdaki yönergeleri izleyin:  
  
-   Bir grafik komutu yapısı önceden hazırlayın. Komutlar, birleşik giriş kutuları, komut grupları ve birden fazla konumda kullanılacak kısayol menüleri belirleyin.  
  
-   Aynı grubu içinde görünen komutlar ilişkili olmalıdır.  
  
-   Tek bir komut içeren gruplar kabul edilir.  
  
-   Paketler için mevcut Visual Studio menü komutları çok sayıda eklememelisiniz. Bunun yerine, bunlar menülere veya yeni komutlar barındırmak için alt menülere oluşturmalısınız.  
  
-   Bir komut, komut adı gibi varolan bir menüye üzerinde amacı açıktır ve bunu mevcut komutları ile karıştırılmamalıdır böylece yerleştirdiğinizde.  
  
## <a name="best-practices-for-small-command-sets"></a>Küçük komut kümesi için en iyi uygulamalar  
 Ayrıca birkaç komutları içeren bir VSPackage geliştiriyorsanız aşağıdaki yönergeleri izleyin:  
  
-   Mümkün olduğunda, kullanın [üst](../../extensibility/parent-element.md) komutu, birleşik giriş kutusu, Grup veya alt menüsünü uygun gruba yerleştirmek için öğesi.  
  
-   VSPackage'ı tarafından görüntülenen menüler bu gruplara atayın.  
  
-   Üst öğesi bir alt menü veya bir komut olmalıdır bir [grubu](../../extensibility/group-element.md) öğesi. Komutlar ve menüler alt gruplara ve gruplar için üst menü atayın.  
  
-   Bir komutu ekleyerek ek gruplarında koyabilirsiniz bir [CommandPlacements](../../extensibility/commandplacements-element.md) komutunu ve ardından ekleyerek öğesi bölümü tanımı sonra `CommandPlacements` öğesi bir [CommandPlacement](../../extensibility/commandplacement-element.md) öğesi her ek grubun için.  
  
## <a name="best-practices-for-large-command-sets"></a>Büyük komut kümesi için en iyi uygulamalar  
 Ayrıca, VSPackage'ı birden çok bağlamlarda görünecek komutların çoğu varsa, aşağıdaki yönergeleri izleyin:  
  
-   Menüleri, gruplar ve komutlar Self bırakarak olun. Atama diğer bir deyişle, bir `Parent` öğesinin tanımındaki öğesi.  
  
-   Kullanım `CommandPlacement` öğesi girişleri `CommandPlacements` öğe bölümünü menüler, gruplar ve komutlar, ana menüler ve gruplar yerleştirmek için.  
  
-   İçinde `CommandPlacements` öğesi bölümünde, belirli bir menü veya grubu dolduran girişleri olmalıdır birbirine bitişik. Bu okunabilirliği kolaylık sağlar ve yapar `Priority` sıralamasına belirlemek daha kolay.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSPackage kullanıcı arabirimi öğelerini nasıl eklenir](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Visual Studio komut tablosu (.vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)