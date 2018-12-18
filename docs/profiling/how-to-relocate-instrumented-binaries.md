---
title: 'Nasıl yapılır: izleme eklenmiş ikili dosyaları yeniden konumlandırma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a060506f818ac000611fc0c29988ed324ae89226
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843659"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Nasıl yapılır: izleme eklenmiş ikili dosyaları yeniden konumlandırma

İzleme sırasında araştırmalar uygulama performansını ölçmek için ikili olarak eklenir. İzleme eklenmiş ikili taşıyabilir seçerek, özgün ikili bir kopyasını işaretlenir ve belirtilen konuma yerleştirin. Bu seçenek, özgün ikili dosyanız yeniden adlandırmak için profil oluşturucu istemiyorsanız yararlıdır. İkili yeniden konumlandırılmasını değil, ikili özgün sürümünün üzerine yazılır.

## <a name="to-relocate-instrumented-binary"></a>İzleme eklenmiş ikili konumunu değiştirmek için

1. İçinde **performans Gezgini**, performans oturumu sağ tıklatın ve ardından **özellikleri**.

2. İçinde **özellik sayfaları**, tıklatın **ikili** özellikleri.

3. Seçin **izleme eklenmiş ikili dosyaları yeniden konumlandırma** onay kutusu.

4. İzleme eklenmiş ikili dosya konumunu belirtin.

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)  
[VSInstr](../profiling/vsinstr.md)
