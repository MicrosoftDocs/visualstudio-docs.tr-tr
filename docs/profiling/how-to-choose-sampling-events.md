---
title: 'Nasıl yapılır: örnekleme olayları seçme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.sampling
helpviewer_keywords:
- clock cycles sample event
- sample events, choosing
- profiling tools, sample events
- page faults sample event
- system calls sample event
- performance counter sample event
- performance tools, sample events
ms.assetid: ce7cb734-80ac-4930-a4ef-e24395e1cc07
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8af903abb15d06d8d76d73cca4a9c337d45ee45
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765638"
---
# <a name="how-to-choose-sampling-events"></a>Nasıl yapılır: örnekleme olayları seçme
Varsayılan olarak, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profil oluşturma araçları profili işlem tarafından kullanılan işlemci döngülerinin sayısı olarak belirtilen bir aralıkta performans verilerini toplar. Varsayılan döngüleri bir aralık içinde 10,000,000, yaklaşık 1 GH bilgisayarda 0,01 saniye olan sayısıdır. Bir aralık içinde döngüsü sayısını değiştirebilirsiniz ve örnek olay değiştirebilirsiniz. Aşağıdaki örnek olayları kullanılabilir:  
  
-   Saat döngüleri - CPU bağımlı sorunları için.  
  
-   Sayfa hataları - bellek ile ilgili sorunlar için.  
  
-   Sistem çağrıları - g/Ç ile ilgili sorunlar için.  
  
-   Performans sayacı - alt düzey performans sorunları için CPU sayaçları.  
  
> [!IMPORTANT]
>  .NET bellek verisi (ayırmaları veya nesne yaşam süresi veya her ikisi de) örnekleme yöntemini kullanarak topluyorsanız, tüm kullanıcı tarafından belirtilen örnekleme olayları göz ardı edilir ve uygun bellek ayırma veya çöp toplama olayları veya her ikisi de, verileri toplamak için kullanılır.  
  
### <a name="to-select-a-sample-event"></a>Örnek olay seçmek için  
  
1.  İçinde **performans Gezgini**, performans oturumu sağ tıklatın ve ardından **özellikleri**.  
  
2.  İçinde **özellik sayfaları**, tıklatın **örnekleme** özellikleri.  
  
3.  Gelen **örnek olayı** aşağı açılan listesinde, uygulamanıza profil için kullanmak istediğiniz örnek olayı seçin.  
  
    > [!NOTE]
    >  **Kullanılabilir performans sayaçları** yalnızca seçerseniz etkin **performans sayacı** gelen **örnek olayı** aşağı açılan liste.  
  
4.  Seçerseniz **performans sayacı**, belirli bir CPU sayacından seçin **kullanılabilir performans sayaçları** ağaç görünümü denetimi.  
  
    -   İçinde sayaçları **taşınabilir olayları** düğüm işlemci tüm türleri kullanılabilir.  
  
    -   İçinde sayaçları **Platform olayları** düğüm işlemci geçerli bilgisayarda özgüdür ve diğer türde işlemci kullanılamaz durumda olabilir.  
  
5.  Örnek olay seçtiğinizde, bir varsayılan aralık değeri örnekleme görüntülenen **örnekleme aralığı** metin kutusu. Gerekirse, metin kutusuna istediğiniz değeri girebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [Nasıl yapılır: Koleksiyon yöntemleri seçme](../profiling/how-to-choose-collection-methods.md)   
 [CPU ve Windows sayaçları](../profiling/cpu-and-windows-counters.md)   
 [Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)   
 [Komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md)