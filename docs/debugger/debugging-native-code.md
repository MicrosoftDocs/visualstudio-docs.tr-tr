---
title: Yerel kodda hata ayıklama | Microsoft Docs
description: Visual Studio 'daki yerel uygulamalar için ortak hata ayıklama sorunları ve üst düzey teknikler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 04/11/2017
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4fee3044e4eaa1e7dd3549923082f9b843951b28
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728323"
---
# <a name="debugging-native-code"></a>Yerel Kodda Hata Ayıklama
Bu bölümde, yerel uygulamalar için bazı yaygın hata ayıklama sorunları ve teknikleri ele alınmaktadır. Bu bölümde ele alınan teknikler, üst düzey tekniklerdir. Visual Studio hata ayıklayıcısını kullanmanın mekanizması için bkz. [ilk olarak hata ayıklayıcıya](../debugger/debugger-feature-tour.md)bakın.

## <a name="in-this-section"></a>Bu Bölümde
 [Nasıl yapılır: Iyileştirilmiş kodda hata ayıklama](../debugger/how-to-debug-optimized-code.md) En iyi duruma getirilmiş kodda hata ayıklama için ipuçları, özellikle de programın en iyi duruma getirilmiş bir sürümünde hata ayıklamanızın yanı sıra hata ayıklama ve sürüm yapılandırmalarının varsayılan iyileştirme ayarlarını ve yalnızca iyileştirilmiş kodda (bir hata ayıklama yapı yapılandırmasında en iyi duruma getirmeyi etkinleştirerek) görünen hataları bulmaya yönelik ipuçları verir.

 [DebugBreak ve __debugbreak](../debugger/debugbreak-and-debugbreak.md) Win32 işlevini açıklar `DebugBreak` ve Platform SDK 'sında başvuru konusuna bir bağlantı sağlar. Ayrıca, iç öğesini açıklar `__debugbreak` .

 [C/C++ Onayları](../debugger/c-cpp-assertions.md) Onaylama deyimlerini, bunların nasıl çalıştığını, bunları kullanmanın avantajlarını (mantık hatalarını yakalama, bir işlemin sonuçlarını kontrol etmeyi ve hata koşullarını test etmeyi), ile etkileşimini `_DEBUG` ve ' de desteklenen onayların türlerini açıklar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 [Nasıl yapılır: satır Içi derleme kodunda hata ayıklama](../debugger/how-to-debug-inline-assembly-code.md) Kayıt içeriğini görüntülemek ve bu pencereler hakkındaki konuların bağlantılarını sağlamak üzere derleme yönergelerini ve Yazmaçları penceresini görüntülemek için ayrıştırma penceresini kullanma hakkında kısa yönergeler sağlar.

 [MFC hata ayıklama teknikleri](../debugger/mfc-debugging-techniques.md) MFC programları için hata ayıklama tekniklerine bağlantı sağlar: afxDebugBreak, Izleme makrosu, MFC 'de bellek sızıntılarını algılama, MFC onayları ve MFC hata ayıklama derlemeleri boyutunu azaltma.

 [CRT hata ayıklama teknikleri](../debugger/crt-debugging-techniques.md) CRT hata ayıklama kitaplığı, raporlama için makrolar, malloc ve _malloc_dbg arasındaki farklılıklar, hata ayıklama kanca işlevleri yazma ve CRT hata ayıklama yığını gibi, C Run-Time kitaplığı için hata ayıklama tekniklerine bağlantı sağlar.

 [Yerel kod SSS hatalarını ayıklama](../debugger/debugging-native-code-faqs.md) C++ programlarında hata ayıklama hakkında sık sorulan soruların yanıtlarını sağlar

 [Com ve ActiveX hata ayıklaması](../debugger/com-and-activex-debugging.md) Com ve ActiveX hata ayıklaması için kullanabileceğiniz araçlar da dahil olmak üzere COM ve ActiveX uygulamalarının hatalarını ayıklama hakkında bilgi sağlar.

 [Nasıl yapılır: eklenen koddaki hataları ayıklama](../debugger/how-to-debug-injected-code.md) Öznitelikleri kullanan hata ayıklama kodu hakkında rehberlik sağlar. Kaynak ek açıklamanın nasıl kullanılacağı, eklenen kodun nasıl görüntüleneceği ve geçerli yürütme noktasındaki ayrıştırılmış kodu nasıl görüntüleneceği hakkında yönergeler içerir.

 [Izlenecek yol: paralel uygulamada hata ayıklama](../debugger/walkthrough-debugging-a-parallel-application.md) Paralel bir uygulamada hata ayıklamak için **paralel görevler** ve **Paralel Yığınlar** araç pencerelerinin nasıl kullanılacağını açıklar.

## <a name="related-sections"></a>İlgili Bölümler
 [C++ projelerinde hata ayıklamaya hazırlanma](../debugger/debugging-preparation-visual-cpp-project-types.md) C++ proje şablonları tarafından oluşturulan yerel proje türlerinde hata ayıklamanın nasıl yapılacağını betimleyen konuların bağlantılarını sağlar.

 [DLL projelerinde hata ayıklama](../debugger/debugging-dll-projects.md) Yerel ve yönetilen DLL 'Lerde hata ayıklama hakkında bilgi sağlar.

 [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md) Hata ayıklama belgelerinin daha büyük bölümlerine bağlantılar sağlar. Bilgiler hata ayıklayıcıdaki yenilikleri, ayarlar ve hazırlık, kesme noktaları, özel durumları işleme, düzenleme ve devam etme, yönetilen kod hatalarını ayıklama, yerel kodda hata ayıklama, SQL hata ayıklama ve Kullanıcı arabirimi başvurularına dahildir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)
- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)