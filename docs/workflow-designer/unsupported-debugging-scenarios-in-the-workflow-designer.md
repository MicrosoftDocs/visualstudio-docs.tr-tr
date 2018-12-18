---
title: İş Akışı Tasarımcısı'nda hata ayıklama desteklenmeyen senaryolar
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 2b876df1b7d997f3999c119d02abd593a88e6d5e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973076"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>İş Akışı Tasarımcısı'nda hata ayıklama desteklenmeyen senaryolar

İş Akışı Tasarımcısı'nda .NET Framework 4 birçok yeni özellik eklendi ancak hala desteği olmayan hata ayıklama bazı senaryolar vardır.

Hata ayıklama senaryoları desteklenmeyen İş Akışı Tasarımcısı şunlardır:

-   Kodu düzenlenmiş sonra yürütme devam edemiyor.

-   Yürütme (sonraki ayarlayın) iş akışı içindeki rastgele bir noktadan devam edemiyor.

-   İmleç (imleç çalışmaya) ulaşılana kadar yürütme devam edemiyor.

-   İş Akışı Tasarımcısı'nı, iş akışı Tasarımcısı'nın kullanmadan kodda oluşturulan hata ayıklamak için kullanılamaz.

-   Önceki sürümlerinde Windows Workflow Foundation (WF) oluşturulan iş akışı .NET Framework 4 Tasarımcısı'nda hata ayıklaması olamaz.

-   Kesme noktaları, etkinlikler arasındaki bağlantılarında tanımlanamıyor veya <xref:System.Activities.Statements.Flowchart> düğümleri.

-   Pano hata ayıklama sırasında kullanılamaz.

-   Etkinlikler kopyalandığında veya yapıştırılan kesme noktaları korunmaz.

-   İş akışı kesme noktaları, çağrı yığını penceresinde olacak şekilde ayarlanamaz.

-   Kesme noktaları Tasarımcısı'nda oluştururken **satır** ve **karakter** ayarlarında **yeni kesme noktası** iletişim kullanılmaz.

-   Kesme noktası penceresi veya kısayol menüsünden aşağıdaki sütunları veya seçenekleri iş akışı hata ayıklama için desteklemez:

    -   Koşul

    -   İsabet sayısı

    -   Ne zaman ulaştı.

    -   İşlev

    -   Veri

    -   İşlem

    -   Çözüme Git