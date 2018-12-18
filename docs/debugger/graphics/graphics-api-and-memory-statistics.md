---
title: Grafik API'si ve bellek istatistikleri | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 48c8ed3c8c2ebffc57ac46e987dbc37950cba0fd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31481534"
---
# <a name="graphics-api-and-memory-statistics"></a>Grafik API'si ve bellek istatistikleri
<!-- VERSIONLESS -->
Visual Studio 2017 ve daha fazla destek grafik API'si istatistikleri ve bellek istatistikleri araçları.  Bu iki aracı GPU bellek tüketimi çeşitli kaynakların yanı sıra Direct3D API kullanımı hakkında bilgi çeşitli BITS görüntülemenize olanak sağlar.

## <a name="graphics-api-statistics"></a>Grafik API'si istatistikleri
Visual Studio grafik tanılama grafik API'si istatistiklerine yapılan Direct3D çağrıları tümüne ve her çağrı sayısı görüntülemenize olanak tanır.  Penceresini görüntülemek için seçin **Görünüm > API istatistikleri** menü öğesi.

![API istatistikleri](media/gfx_diag_api_statistics.png)

Bu araç, size bilmiyor olabilirler DirectX çağrıları yapıyorsanız bulmaya veya çok sık kuran çağrıları kullanışlı olabilir.

Excel gibi içine daha detaylı analizler için yapıştırılabilmesi için CSV olarak kopyalama tüm verileri penceresinde tıklayabilir.

## <a name="memory-statistics"></a>Bellek istatistikleri
Bu aracı, grafik sürücüsü için kaynakları ayırma ne kadar bellek oluşturduğunuz bir çerçevede görüntülenir.  Bu pencereyi görüntülemek için seçin **Görünüm > bellek istatistikleri** menü öğesi.

![Bellek istatistikleri](media/gfx_diag_memory_statistics.png)

**GPU ayırma** sütun görüntülenen olay tarafından kullanılan bellek miktarını görüntüler **olay** sütun.  İzleme simgesi öğesini de seçebilirsiniz ![izleme simgesi](media/gfx_watch.png) görüntülemek için [kaynak geçmiş](graphics-event-list.md#resource-history) seçili olay için.

API istatistikleri aracıyla olduğu gibi kopyalama tüm verileri penceresinde aşağıdakine benzer Excel içine daha detaylı analizler için yapıştırılabilmesi için CSV olarak sağ tıklatın.

## <a name="see-also"></a>Ayrıca Bkz.  
[Grafik tanılama (hata ayıklama DirectX grafik)](visual-studio-graphics-diagnostics.md)   
[Kaynak geçmişi](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->