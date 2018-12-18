---
title: 'İş Akışı Tasarımcısı - nasıl yapılır: iş akışlarında kesme noktalarını ayarlama'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1d7dcb437a77bd91c8dbb3360a33c7260fabb91
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755245"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Nasıl yapılır: iş akışlarında kesme noktalarını ayarlama

İş Akışı Tasarımcısı kullandığınızda, Visual Basic veya C# kodunda yaptığınız gibi grafik iş akışlarında kesme noktaları ayarlayabilirsiniz. Beklendiği gibi iş akışı yürütme ayarladığınız her kesme noktasında durur.

Üç durumlu bir kesme noktası vardır: *bekleyen*, *bağlı*, ve *hata*. Bir kesme noktası ayarladığınızda, bekleyen ve düz bir kırmızı simgesiyle gösterilir. Çalışma zamanı iş akışı türü yüklendiğinde bağlı olur. Geçerli olmayan bir etkinlik adı gibi kesme için yanlış bir biçim belirtirseniz, bir hata penceresi görünür. Kesme noktası hala kesme noktası penceresine eklenen ancak küçük "x" ile işaretlenmiş.

> [!NOTE]
> Çağrılan iş akışlarında kesme noktalarını ayarlama desteklenmez.

> [!NOTE]
> Seçeneği belirlediğinizden emin olun **sadece kendi kodumu etkinleştir (sadece yönetilen)** gelen **Araçları** > **seçenekleri** > **hata ayıklama**  hata ayıklama önce menüsü. Seçeneği seçili değilse ve içinde başka bir sırayla iç içe geçmiş iki sıraları varsa ve ilk iç dizisi üzerinde bir kesme noktası ayarlayın, tuşuna basarak **F11** ikinci iç dizisi debug değil.

> [!NOTE]
> XAML dosya özelliği tam yolu doğru değilse, bir iş akışında kesme noktası isabet değil. Proje ve çözüm başka bir klasöre veya başka bir makine taşıdıktan sonra özelliği XAML dosyasının tam yolunu doğru değil. Seçin **Ctrl**+**S** kaydedin ve tam yolu özelliğini güncelleştirin.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Tasarım görünümünde bir etkinlikte bir kesme noktası ayarlamak için

1. Üzerinde ayırmak için hata ayıklayıcı istediğiniz etkinliği seçin.

2. Üzerinde **hata ayıklama** menüsünde, select **kesme**. Etkinlik sol üst kenarına kırmızı bir simge görüntülenir.

   Alternatif olarak, basabilirsiniz **F9** etkinlik veya seçerek etkinliğe sağ tıklayın ve da seçin sonra **kesme noktası** > **kesme noktası Ekle** bağlam menüsünden.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: İş Akışı Hata Ayıklayıcısını Çağırma](../workflow-designer/how-to-invoke-the-workflow-debugger.md)
- [İş Akışı Tasarımcısı ile İş Akışlarında Hata Ayıklama](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Nasıl Yapılır: İş Akışı Tasarımcısı ile XAML Hatalarını Ayıklama](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)