---
title: 'DA0504: En büyük çalışma kümesinin profili oluşturuluyor işlem için bayt cinsinden | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0504
- vs.performance.504
- vs.performance.rules.DA0504
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a39171c8786f3b2149a50bd3c4a6915575f050ae
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800204"
---
# <a name="da0504-maximum-working-set-in-bytes-for-the-process-being-profiled"></a>DA0504: İşlem için izin verilen Bayt Cinsinden En Büyük Çalışma Kümesinin profili oluşturuluyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural Kimliği | DA0504 |  
| Kategori | Kaynak Yönetimi |  
| Profil oluşturma yöntemi | Tüm |  
| İleti | Bu bilgiler yalnızca bilgi toplanmıştır. İşlem çalışma kümesi sayacı profil bir işlem tarafından fiziksel bellek kullanımını ölçer. Bildirilen değer olan en yüksek tüm ölçüm aralıklarında gözlemlenen. |  
| Kural türü | Bilgi |  
  
 Örnekleme, .NET bellek ve kaynak çekişmesi yöntemleri kullanılarak profili, bu kural tetiklemek için en az 10 örnekleri toplamanız gerekir.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Bu ileti, en fazla işlem şu anda kullandığı bayt cinsinden fiziksel bellek miktarını bildirir. İşlem çalışma kümesi, işlemin adres alanından şu anda fiziksel bellekte bulunan sayfaları temsil eder. Bu kural, profil oluşturma etkinken işlem çalışma kümesi için maksimum değeri bildirir.  
  
 Bildirilen değeri yerleşik sayfalarından işlem başvurmuş paylaşılan bellek segmentler içerir. Paylaşılan dll işlem başvuruları sayılan paylaşılan bellek segmentler dahildir. Değer işlemin çalışma kümesi paylaşılan bellek kesimler nedeniyle işlemin ayırdığı sanal bellek miktarından daha yüksek olabilir.  
  
 İşlem çalışma kümesi boyutu işlemi etkin bir şekilde kullanarak ne kadar sanal bellek yansıtır. Fiziksel bellek (veya RAM) miktarı tarafından etkilenir uygulama ve fiziksel belleğin için Çekişme diğer çalışan işlemlerini çalıştırmak kullanılabilir. İşlem çalışma kümeleri hakkında daha fazla bilgi için bkz. [çalışma kümesi](http://go.microsoft.com/fwlink/?LinkId=177830) msdn'in Windows bellek yönetimi belgelerinde.  
  
## <a name="how-to-use-rule-data"></a>Kural verileri kullanma  
 Kural Windows performansı izleme olanağı Bu ölçüm verilerini toplar ve yalnızca bilgi bildirir. Bunu, farklı sürümlerin performans veya programın yapıları karşılaştırmak veya farklı test senaryoları altında uygulama performansını anlamak için kullanın.  
  
 Hata Listesi penceresindeki iletiyi gitmek için çift tıklatın [işaret görünümü](../profiling/marks-view.md) profil oluşturma verilerinin. Bulma **Process\Working ayarlamak** ve **Bellek\Sayfa/sn** sayaç sütun. Ardından en büyük değerini bulmak **Process\Working ayarlamak** ve karşılaştırmak için **Bellek\Sayfa/sn** değeri. Genellikle, özellikle makine bellek kısıtlı olduğunda maksimum küme çalışma azalan sayfalama g/ç etkinliğini olduğu zaman aralığı ile ilişkilidir.



