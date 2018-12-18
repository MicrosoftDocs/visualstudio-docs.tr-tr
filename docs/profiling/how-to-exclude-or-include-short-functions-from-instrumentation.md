---
title: 'Nasıl yapılır: Exclude veya kısa işlevleri izlemeden Include | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c6234db781925e8c0558513cb7e8bc608b5cfea
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814690"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Nasıl yapılır: hariç tutma veya kısa işlevleri izlemeden içerir
Profil oluşturma araçları varsayılan olarak, dışarıda *küçük işlevleri* izlemeden. İşlev çağrıları yapma kısa işlevleri küçük işlevlerdir. Bu kısa işlevleri dışlama araçları tarafından yükü daha azdır için sağlar ve bu nedenle araçları hızı geliştirilmiş. Kısa işlevleri dışlama ayrıca performans veri dosyası profil azaltır (. *Vsp*) boyutunu ve çözümleme için gereken süreyi. Küçük işlevler hariç, küçük işlevlerde geçen süre üst işlevleriyle özel ve kapsayıcı zaman karşı sayar. Küçük işlevler hariç veya Araçları'nda, aşağıdaki yordamda açıklandığı gibi dahil.  
  
### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Hariç tutma veya kısa işlevleri izlemeden eklemek için  
  
1.  İçinde **performans Gezgini**seçin **Performans oturumunu** ve ardından sağ tıklatın ve seçin **özellikleri**.  
  
     **Özellik sayfaları** iletişim kutusu görüntülenir.  
  
2.  İçinde **özellik sayfaları**, tıklatın **Araçları** özellikleri.  
  
3.  Kısa işlevleri izleme hariç tutmak için işaretleyin **araçları kısa işlevleri dışlama**. Varsayılan ayar budur.  
  
     veya  
  
     Kısa işlevleri de araçları içerecek şekilde temizleyin **araçları kısa işlevleri dışlama**.  
  
4.  **Tamam**'ı tıklatın.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Denetimin veri toplama](../profiling/controlling-data-collection.md)   
 [Performans oturumu özellikleri](../profiling/performance-session-properties.md)