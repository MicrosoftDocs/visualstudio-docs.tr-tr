---
title: 'Nasıl yapılır: performans veri dosyası adlandırma seçeneklerini ayarlama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f2f9d47107d8a5e0fb4c10e058c2fc4c7ca3ed5e
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844475"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Nasıl yapılır: performans veri dosyası adlandırma seçeneklerini ayarlama

Varsayılan olarak, bir profil oluşturma veri kaydetme (. *Vsp*) aşağıdaki söz dizimini kullanarak dosya:

*Path\VSP-File\YYMMDD(N)* **.vsp**

Herhangi bir adlandırma parametre değiştirebileceğiniz **genel** performans oturumu için Özellikler iletişim kutusunun sayfası.

|||
|-|-|
|*Yol*|Raporda dizin. Varsayılan konum çözüm klasör ya da kullanıcının projeler ve çözümler için varsayılan konum değil.|
|*VSP-File*|Profil oluşturma veri dosyası adı. Çözüm adı varsayılan addır veya yürütülebilir, profili.|
|*YYAAGG*|Yıl, ay ve profil oluşturma verileri toplanan gün gösterir ve tarih damgası.|
|*(N)*|Birden fazla profil oluşturma veri dosyası zaten varsa, ayraçlar arasında dosya adı artan bir sayı eklenir.|

## <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Profil oluşturma veri dosyaları bir performans oturumu adlandırma sözdizimi değiştirmek için

1. İçinde **performans Gezgini**, performans oturumunu adına sağ tıklayın ve ardından **özellikleri**.

2. Tıklatın **genel**.

3. Altında **rapor**, aşağıdaki ayarlardan birini değiştirin:

    |||
    |-|-|
    |**Rapor konumu**|Profil oluşturma veri dosyaları depolamak için bir dizin belirtin.|
    |**Rapor adı**|Dosyalar için bir veritabanı adı belirtin.|
    |**Yeni raporlar oturuma otomatik olarak Ekle**|Otomatik olarak veri dosyası performans oturumuna eklemek için bu onay kutusunu seçin.|
    |**Bir artacak numarası oluşturulan raporlar ekleme**|Aynı ada sahip birden fazla dosya varsa, dosya adına bir artacak numarası eklemek için bu onay kutusunu seçin. Varolan dosyanın üzerine yazmak için bu onay kutusunu temizleyin.|
    |**Bir zaman damgası numarasını kullanın**|Dosya adına bir tarih damgası eklemek için bu onay kutusunu seçin.|