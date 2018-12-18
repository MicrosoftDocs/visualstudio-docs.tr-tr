---
title: 'Nasıl yapılır: Windows sayaç verileri toplama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ea074024e605d2dcc91500fb00fe0d7b6781692
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677243"
---
# <a name="how-to-collect-windows-counter-data"></a>Nasıl yapılır: Windows sayaç verileri toplama

Windows sayaçları profil oluşturma sırasında belirlenen aralıklarla toplanabilecek sistem performans sayaçları ' dir. Profil oluşturma araçları rapor işaretler görünümünde bir satır olarak etiketlenmiş **AutoMark** her koleksiyon aralığı. Satır o aralıkta performans sayaç değerlerini tanımlayan sütun içerir. Analizi iki belirli işaret arasındaki zaman dilimiyle sınırlamak için işaretleri, sağ tıklayın ve ardından seçin **filtre tarafından** > **işaretleri** kısayol menüsünden.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki Gelişmiş güvenlik özellikleri Visual Studio profil oluşturucu bu platformlarda veri toplayan bir şekilde önemli değişiklikler gerekmiştir. UWP uygulamaları, ayrıca yeni toplama teknikleri gerektirir. Bkz: [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-collect-windows-counter-data"></a>Windows sayaç verileri toplamak için

1. Performans Gezgini içinde Windows sayaçları yapılandırmak ve seçmek istediğiniz oturumu sağ **özellikleri**.

2. İçinde **özellik sayfaları**, tıklayın **Windows sayaçları**.

3. Seçin **Windows sayaçları toplamak** onay kutusu.

4. İçinde **toplama aralığı (milisaniye)** metin kutusunda, bir zaman aralığı yazın.

5. Bir kategori seçin **sayaç kategorisi** aşağı açılan listesi.

6. Bir örnekten seçin **örneği** aşağı açılan listesi.

7. Uygulamanızın profilini, kullanmak istediğiniz sayaçları seçin.

8. Tıklayın **uygulayın.**

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)  
[Performans oturumu özellikleri](../profiling/performance-session-properties.md)  
[CPU ve Windows sayaçları](../profiling/cpu-and-windows-counters.md)