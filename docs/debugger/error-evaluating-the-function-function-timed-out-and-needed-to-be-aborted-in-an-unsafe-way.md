---
title: 'Hata: işlevin değerlendirilmesi &#39;işlevi&#39; zaman aşımına uğradı ve güvenli bir şekilde iptal edilmesi gerekti | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1f36e56b2870d5f099a3b8ed95265fe7e2d688ff
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934450"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Hata: işlevin değerlendirilmesi &#39;işlevi&#39; zaman aşımına uğradı ve güvenli bir şekilde iptal edilmesi gerekti

Tam metin iletisi: ' % s'function 'işlevini değerlendirirken zaman aşımına uğradı ve güvenli bir şekilde iptal edilmesi gerekti. Bu hedef işlemi bozmuş olabilir. 

.NET nesnelerinin durumunu incelemek daha kolay hale getirmek için ek kod (genellikle özellik alıcı yöntemlere ve ToString işlevleri) çalıştırmak için hataları ayıklanan işlem otomatik olarak hata ayıklayıcı zorlar. Çoğu tüm senaryolarda, bu işlevler hızla tamamlayın ve çok daha kolay hata ayıklama yapın. Ancak, hata ayıklayıcı korumalı alanda uygulama çalışmaz. Sonuç olarak, özellik alıcısı veya yanıt vermemeye başlıyor yerel bir işleve çağrı ToString yöntemini kurtarılamayabilir uzun zaman aşımları için neden olabilir. Bu hata iletisiyle karşılaşırsanız, bu durum oluştu.
 
Bu sorun için yaygın nedenlerinden biri hata ayıklayıcı bir özellik değerlendirdiğinde, yalnızca yürütmek için denetlenen iş parçacığı olanak sağlamasıdır. Bu nedenle özelliği içinde hata ayıklanan uygulamayı çalıştırmak için diğer iş parçacıkları üzerinde bekleyen ve .NET çalışma zamanı kesme mümkün olmayan bir şekilde bekliyorsa, bu sorunu gerçekleşir.
 
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için
 
Bu sorun için üç olası çözümü vardır.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>#1 çözümü: özellik alıcısı veya ToString yöntemini çağırmasını hata ayıklayıcı engellemek
 
Hata iletisi, hata ayıklayıcı ulaşmaya çalıştık işlevin adını bildirir. Bu işlev değiştirebilir, özellik alıcısı veya ToString yöntemini çağırma, hata ayıklayıcı engelleyebilirsiniz. Aşağıdakilerden birini deneyin:
 
* Yöntem başka türde bir özellik alıcısı yanı sıra kodu değiştirin veya ToString yöntemi ve sorunu kaybolur.
    veya
* (ToString için) DebuggerDisplay özniteliği türüne tanımlayın ve ToString dışında bir şey değerlendirmek hata ayıklayıcı olabilir.
    veya
* (Özellik alıcısı için) PUT `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` özelliği özniteliği. Bu API Uyumluluk nedenleriyle bir özellik kalması gereken bir yöntem varsa yararlı olabilir, ancak gerçekten bir yöntemi olması gerekir.
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Çözüm #2: sahip değerlendirme iptal etmek için hata ayıklayıcı isteyin hedef kodu
 
Hata iletisi, hata ayıklayıcı ulaşmaya çalıştık işlevin adını bildirir. ToString yöntemi ve özellik alıcısı bazen düzgün çalışması başarısız sorunu olduğu, özellikle durumlarda kod kodu çalıştırmak için başka bir iş parçacığı gerekir ve ardından uygulama işlevi çağırabilir `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` işlevi iptal etmek için hata ayıklayıcı istemek için Değerlendirme. Bu çözüm ile açıkça bu işlevler değerlendirmek yine de mümkündür, ancak NotifyOfCrossThreadDependency çağrısı yapıldığında yürütmeyi durdurur varsayılan davranıştır.
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>#3. çözüm: tüm örtülü değerlendirme devre dışı bırak
 
Önceki çözümler sorunu yoksa, Git *Araçları* > *seçenekleri*, ayarı kaldırın *hata ayıklama*  >   *Genel* > *özellik değerlendirmesini ve diğer örtük işlev çağrılarını etkinleştir*. Bu, çoğu örtük İşlev değerlendirmesi devre dışı bırakır ve sorun çözülebilir.



  
