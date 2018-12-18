---
title: 'DA0026: Aşırı Çekirdek CPU süresi işleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9043b1dddcacc797c640252691d6bf393189cc4d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876613"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: Aşırı çekirdek CPU süresi işleme

|||  
|-|-|  
|Kural Kimliği|TODO|  
|Kategori|Profil oluşturma araçları kullanım|  
|Profil oluşturma yöntemi|Örnekleme|  
|İleti|Çekirdek modu CPU zamanı görece yüksek miktarda ölçülmüştür. Kaynağı etkin syscall örneklemesiyle incelemeyi dikkate alın.|  
|Kural türü|Bilgiler|  

 Örnekleme, .NET bellek ve kaynak çekişmesi yöntemleri kullanılarak profili, bu kural tetiklemek için en az 10 örnekleri toplamanız gerekir.  

## <a name="cause"></a>Sebep  
 Çekirdek modunda yürütülen oranda CPU süresi, kullanıcı modunda harcanan süreyi aştı. Yeniden profil oluşturmayı hem de örnekleme yüksek çekirdek modu yürütme sürelerini nedenini belirlemek için sistem çağrıları (syscalls) sayısını göz önünde bulundurun.  

## <a name="rule-description"></a>Kural açıklaması  
 Uygulama çekirdek modu yürütme için harcanan süre görece yüksek oranda daha fazla araştırma isteyebilirsiniz. Bir kullanıcı modu uygulaması için iş parçacığı veya işlem eşitleme temellerine bekleyin ya da sistem çağrıları yapmak için g/ç işlemleri gerçekleştirmek için çekirdek moduna geçer. Sistem çağrıları uygulama yapar ve sistem çağrıları örnek çağrı yığınlarını Topla seçeneğini belirlediğinizde, bunlardan sorumlu olan işlevleri temel tür araştırabilirsiniz.  

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?  
 Profili yeniden çalıştırın ve sistem çağrıları tabanlı örnekleri toplamak için seçeneğini uygulamanızı sağlayan sistem çağrıları tür araştırmak için. Bkz: [nasıl yapılır: örnekleme olayları seçin](../profiling/how-to-choose-sampling-events.md) daha fazla bilgi için IDE içinde profil oluşturma araçları çalıştırıyorsanız. Komut satırından profil oluşturma araçları çalıştırıyorsanız bkz **örnekleme aralığı seçenekleri** bölümünü [VSPerfCmd](../profiling/vsperfcmd.md) Profil Araçları komut satırı araçları başvurusu makalesinde.