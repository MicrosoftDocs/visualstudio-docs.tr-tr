---
title: İş Akışı Tasarımcısı ile İş Akışlarında Hata Ayıklama
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- Visual Studio Workflow Designer [WFD], debugging workflows
- Workflow Designer [WFD], debugging workflows
ms.assetid: d71308cf-d464-4536-8711-0d0a8eadb255
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 482e13a91513151d7c4595e0a622f223751ae553
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755320"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>İş Akışı Tasarımcısı ile hata ayıklama

**İş akışı Tasarımcısı** iş akışları ve özel etkinlikler hata ayıklama olanağı sağlar. İşlem ve davranışı, varsayılan Visual Studio hata ayıklayıcısı benzerdir.

## <a name="invoke-the-workflow-debugger"></a>İş akışı hata ayıklayıcı çağırma

Genellikle, diğer Visual Studio programlama dilinde yazılmış programları yalnızca hata ayıklama gibi iş akışları hata ayıklama. İş akışı hata ayıklayıcı aşağıdaki yollarla başlatabilirsiniz:

- Seçin **ekleme işlemi için** üzerinde **hata ayıklama** menüsü, iş akışı örneği için çalışan ana bilgisayar işlemi seçin. Bu yordam bir ana bilgisayar işlemi yönetilen kod ekleme aynıdır.

- Tuşuna **F5** iş akışı örneği çalıştırma başlatın ya da bir kesme noktası isabet sonra çalışmaya devam eder.

- Uzaktan hata ayıklama kullanın. Uzaktan hata ayıklama kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: uzaktan hata ayıklamayı etkinleştirme](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100)).

   > [!NOTE]
   > İş akışı uygulaması x86 hedefliyorsa mimarisi ve uzaktan hata ayıklama Visual Studio uzak makinede yüklü veya iş akışı uygulaması için hedef içindeğiştirildiğindesüreceçalışmazsonrabir64bitişletimsistemiçalıştıranbirmakinedebarındırıldığı **Tüm CPU**.

## <a name="step-through-code"></a>Kod üzerinden adım

- **Adım içinde**: basarak adım etkinliğe **F11**. Hata ayıklayıcı adımları tanımlanan işleyicisine. Hiçbir işleyici tanımlanmışsa, etkinlik adım veya diğer etkinlikler içeren bileşik etkinliklerle ilk yürütülen etkinliğe adım.

- **Adım çıkışı:** adım bir etkinlik dışında tuşlarına basarak **Shift**+**F11**. Bir etkinlik dışına Adımlama geçerli etkinliği ve tüm eşdüzey tamamlanıncaya kadar etkinlikleri çalıştırır. Hata ayıklayıcı sonra geçerli etkinliğin üst öğede keser. Kod işleyicisinden atlama, hata ayıklayıcı işleyici ilişkilendirildiği faaliyete keser.

- **Step Over**: basarak bir etkinlik Adımlama **F10**. Bileşik etkinlik Adımlama, hata ayıklayıcı bileşik etkinlik ilk yürütülebilir alt keser. Bir olmayan-bileşik gibi adımlarken bir <xref:System.Activities.Statements.Assign> etkinlik, hata ayıklayıcı sonraki faaliyete etkinliği ve ilişkili işleyicileri ve sonları yürütür. Ardından, yürütülen etkinliği son alt bileşik etkinlikte etkinlikse, yürütme sonrasında hata ayıklayıcı üst faaliyete keser.

## <a name="debug-with-f5"></a>F5 ile hata ayıklama

Bir iş akışı konsol uygulaması oluşturuyorsanız tuşuna basmanız yeterlidir **F5** uygulama ve iş akışı hata ayıklamayı başlatmak için. Bir etkinlik kitaplığı, kendi oluşturuyorsanız, yürütülebilir konak uygulamanın başlangıç projesi olarak belirtmeniz gerekir. Başlangıç projesi ayarlama **Çözüm Gezgini**, ana proje adına sağ tıklayın ve seçin **başlangıç projesi olarak ayarla**.