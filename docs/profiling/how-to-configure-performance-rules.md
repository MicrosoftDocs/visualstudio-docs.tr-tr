---
title: 'Nasıl yapılır: performans kurallarını yapılandırma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfe6e10c42188cab23c75262d947c7deb9c28ea5
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34816035"
---
# <a name="how-to-configure-performance-rules"></a>Nasıl yapılır: performans kurallarını yapılandırma
Th Visual Studio profil oluşturma araçları için performans uyarıları program yürütme yavaşlatabilir profili uygulamasında sorunları gösterir. Uyarılar, daha kullanışlı verileri toplamak için koleksiyon yöntemleri değiştirmeniz gerekebilir de belirtebilirsiniz. Performans uyarıları bir profil oluşturma oturumu otomatik olarak oluşturulur ve görüntülenir **hata listesi** bir profil oluşturma veri dosyası açıldığında penceresi [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Belirli uyarılar ilgilendiğiniz ve bazı uyarılar yanlış olarak yükseltilmiş senaryoları için geçerli olmayabilir. Performans uyarıları göstermek veya belirli uyarıları gizlemek için yapılandırabilirsiniz.  
  
### <a name="to-configure-profiler-performance-warnings"></a>Profil Oluşturucu performans uyarıları yapılandırmak için  
  
1.  Üzerinde **Araçları** menüsünde tıklatın **seçenekleri**.  
  
2.  Genişletme **performans araçları**ve ardından **kuralları**.  
  
3.  Etkinleştirmek veya devre dışı bir uyarı için seçin veya uyarı yanındaki onay kutusunu temizleyin **kimliği** ve adı.  
  
4.  Bir kural hanedan arasındaki düzeyini belirtmek için tıklatın **eylem** hücre yanındaki kuralı ve uyarı düzeyi'ye tıklayın.  
  
    -   **Devre dışı** -(Bu, kural kimliği yanındaki onay kutusunu temizleyerek ile aynı) kuralı devre dışı bırakır.  
  
    -   **Uyarı** -görüntüler kural bir uyarı olarak.  
  
    -   **Hata** - oluşturma yürütmesi durdurur ve kural hata olarak görüntüler.  
  
    -   **Bilgi** -görüntüler kural yalnızca bilgi olarak.