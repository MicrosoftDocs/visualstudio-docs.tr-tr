---
title: 'Hata: işlev &#39;işlevi değerlendiriliyor&#39; zaman aşımına uğradı ve güvenli olmayan bir şekilde durdurulmak için gerekir | Microsoft Docs'
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.assetid: 0a9f70ed-21ad-4a10-8535-b9c5885ad8f4
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a27bf67770eef770fddef0301a804e6c45579539
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387128"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Hata: işlev &#39;işlevi değerlendiriliyor&#39; zaman aşımına uğradı ve güvenli olmayan bir şekilde durdurulmak için gerekiyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tam ileti metni: ' function ' işlevinin değerlendirilmesi zaman aşımına uğradı ve güvenli olmayan bir şekilde durdurulmak için gereklidir. Bu, hedef işlemi bozmuş olabilir. 

.NET nesnelerinin durumunu incelemeyi kolaylaştırmak için, hata ayıklama işlemini ek kod (genellikle özellik alıcı yöntemleri ve ToString işlevleri) çalıştırmaya otomatik olarak zorlar. Çoğu senaryoda, bu işlevler hızla tamamlanır ve hata ayıklamayı çok daha kolay hale getirir. Ancak, hata ayıklayıcı uygulamayı bir korumalı alana çalıştırmaz. Sonuç olarak, yanıt vermeyi durduran bir yerel işleve çağıran bir özellik alıcı veya ToString yöntemi, kurtarılamaz sürelere neden olabilir. Bu hata iletisiyle karşılaşırsanız, bu oluştu.
 
Bu sorunun yaygın bir nedeni, hata ayıklayıcı bir özelliği değerlendirirken yalnızca incelenen iş parçacığının çalışmasına izin verir. Bu nedenle, özellik diğer iş parçacıklarını hata ayıklanan uygulamanın içinde çalışacak şekilde bekleiyorsa ve .NET çalışma zamanının kesintiye uğramaması için bir yöntem bekliyorsa, bu sorun gerçekleşir.
 
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için
 
Bu soruna yönelik üç olası çözüm vardır.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Çözüm #1: hata ayıklayıcının alıcı özelliğini veya ToString metodunu aramasını engelleyin
 
Hata mesajı, hata ayıklayıcının çağrı gerçekleştirmeye çalıştığı işlevin adını bildirir. Bu işlevi değiştirebiliyorsanız, hata ayıklayıcının özellik alıcı veya ToString metodunu aramasını engelleyebilirsiniz. Aşağıdakilerden birini deneyin:
 
* Yöntemi bir özellik alıcı veya ToString yönteminin yanı sıra diğer kod türlerine de değiştirin ve sorun devam eder.
    -veya-
* (ToString için) Türde bir DebuggerDisplay özniteliği tanımlayın ve hata ayıklayıcının, ToString dışında bir şeyi değerlendirebilmeniz gerekir.
    -veya-
* (Bir özellik alıcısı için) `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` Özniteliği özelliğine yerleştirin. Bu, API uyumluluğu nedenleriyle bir özelliği kalması gereken bir yönteminiz varsa, ancak gerçekten bir yöntem olması gereken durumlarda yararlı olabilir.
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Çözüm #2: hedef kodun hata ayıklayıcıya değerlendirmeyi iptal etmesini isteyin
 
Hata mesajı, hata ayıklayıcının çağrı gerçekleştirmeye çalıştığı işlevin adını bildirir. Özellik alıcı veya ToString yöntemi bazen doğru bir şekilde çalışamazsa, özellikle sorunun kod çalıştırmak için başka bir iş parçacığına ihtiyacı olduğu durumlarda, uygulama işlevi `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` hata ayıklayıcıya işlev değerlendirmesini iptal etmesini istemek için çağırabilir. Bu çözümle, bu işlevleri açıkça değerlendirmek yine de mümkündür, ancak varsayılan davranış, NotifyOfCrossThreadDependency çağrısı gerçekleştiğinde yürütmenin durmasını sağlar.
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>Çözüm #3: tüm örtük değerlendirmeyi devre dışı bırak
 
Önceki çözümler sorunu gidermezse, *Araçlar*  /  *Seçenekler*' e gidin ve *hata ayıklama*  /  *genel*  /  *etkinleştirme özelliği değerlendirmesi ve diğer örtük işlev çağrıları*seçeneğinin işaretini kaldırın. Bu, çoğu örtük işlev değerlendirmesini devre dışı bırakır ve sorunu çözmelidir.
