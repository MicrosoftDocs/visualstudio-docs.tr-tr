---
title: Grafik tanılama | Microsoft Docs
description: Visual Studio Grafik Tanılama, Direct3D etkinliğini günlüğe kaydetmeye ve çözümlemeye yönelik bir araç kümesidir. İşleme ve performans sorunlarını gidermek için bunları kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b6b769131831a0f1f94aa4fcc8e94a9a88bf9890
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386130"
---
# <a name="visual-studio-graphics-diagnostics"></a>Visual Studio Grafik Tanılama
>[!NOTE]
> Visual Studio DirectX 12 oyunları için Windows'da PIX önerilir. [Windows'da PIX,](https://aka.ms/PIXonWindows) DirectX 12'yi tam olarak destekleyen bir performans ayarlama ve hata ayıklama aracıdır. [Daha fazla bilgi için buraya bakın](visual-studio-graphics-diagnostics-directx-12.md) veya [indirin.](https://aka.ms/downloadPIX)

Visual Studio *Grafik Tanılama,* Direct3D uygulamaları içinde işleme ve performans sorunlarını kaydetmeye ve analize yönelik bir araç kümesidir. Grafik Tanılama, Windows bilgisayarınızda yerel olarak çalışan uygulamalarda, bir Windows cihaz öykünücüsününde veya uzak bir bilgisayarda ya da cihazda kullanılabilir.

 Bu Grafik Tanılama iş akışı, davranışının hemen analiz, paylaşılan veya daha sonra kaydedilebilir olması için, uygulamanın Direct3D'yi (canlı, çalışırken) nasıl kullandığının bir kaydını yakalayarak başlar. Yakalama oturumları, Visual Studio'den veya komut satırı yakalama aracı ile el ile **başlatılabilir** dxcap.exe. Yakalama oturumları, yakalama API'leri kullanılarak program aracılığıyla başlat Grafik Tanılama denetlenerek de olabilir.

 Bir yakalama oturumu kaydedildikten sonra içeriği Visual Studio Graphics *Analyzer* tarafından herhangi bir zamanda geri çalınarak, yakalanan kareler tam olarak aynı kaynaklar kullanılarak yeniden oluşturma ve uygulamanın kullandığı komutları işleme. Ardından, Grafik Çözümleyicisi penceresinde sağlanan araçlar kullanılarak yakalanan çerçevelerden herhangi biri ayrıntılı olarak analiz edilir. Bu araçlar herhangi bir Direct3D API çağrısını, kaynağı, işlem hattı durumu nesnesini, işlem hattı aşamasını ve hatta yakalanan çerçevede herhangi bir pikselin tüm geçmişini incelemek için kullanılabilir. Bu araçlar birlikte kullanılarak, yakalanan bir çerçevede nasıl göründüğüne bakarak ve uygulamanın kaynak kodunda, gölgelendiricilerde veya grafik varlıklarında kök nedenine kadar inerek işleme sorunu sezgisel bir şekilde keşfedebilirsiniz.

 Performans sorunlarını tanılamak için, yakalanan bir çerçeve Çerçeve Analizi aracı *kullanılarak analiz* edilir. Bu araç, uygulamanın Direct3D kullanma yolunu otomatik olarak değiştirerek ve tüm varyasyonları sizin için kıyaslaarak olası performans iyileştirmelerini keşfeder. Geçmişte, yalnızca hangilerinin fark yaratmış olduğunu bulmak için bu tür değişiklikleri el ile yapmış ve kıyaslamış olabilirsiniz. Çerçeve Analizi ile yalnızca ödemesi olduğunu zaten biliyor olduğunu yaptığınız değişikliklere ihtiyacınız olur.

 Grafik Tanılama grafik açısından zengin Direct3D uygulamanıza en iyi şekilde bakmanıza ve çalıştırmanıza yardımcı olur.

 Neler sunduğu [hakkında daha](overview-of-visual-studio-graphics-diagnostics.md) fazla bilgi edinmek için Genel bakış Visual Studio Grafik Tanılama devam eder.

## <a name="in-this-section"></a>Bu Bölümde
 [Genel Bakış](overview-of-visual-studio-graphics-diagnostics.md) İş akışı Grafik Tanılama araçları hakkında bilgi sağlar.

 [Başlarken](getting-started-with-visual-studio-graphics-diagnostics.md) Bu bölümde, Direct3D uygulamanıza Visual Studio Grafik Tanılama ve Grafik Tanılama kullanmaya nasıl başlayacağınızı öğrenirsiniz.

 [Grafik Bilgilerini Yakalama](capturing-graphics-information.md) Uygulamanıza Grafik Tanılama bir işleme sorununu incelemek için, önce uygulamanın DirectX'i nasıl kullandığına ilişkin bilgileri kaydetmeniz gerekir. Kayıt oturumu sırasında, uygulamanız normal şekilde  çalıştırılana kadar ilgilendiğiniz kareleri yakalar (başka bir ifadeyle) seçersiniz. Yakalamalar, karelerin nasıl işlenecekleri hakkında ayrıntılı bilgiler içerir. Yakalanan bilgileri daha sonra incelemek veya takımınız diğer üyeleriyle paylaşmak için grafik günlüğü belgesi olarak kaydedebilirsiniz.

 [GPU Kullanımı](../../profiling/gpu-usage.md) Uygulama profilini Grafik Tanılama için GPU Kullanımı aracını kullanın. GPU kullanımı, uygulamanıza performans sorunlarına neden olan CPU ve GPU etkinliği arasında ilişki oluşturmak için CPU Kullanımı gibi diğer profil oluşturma araçlarıyla birlikte kullanılabilir.

 [Grafik Günlüğü Belgesi](graphics-log-document.md) Kayıtlı grafik günlüğünü incelemeye başlamak için Grafik Günlüğü belge penceresini kullanarak yakalanan bir çerçeveyi ve hatta belirli bir  pikseli seçersiniz. Böylece, onu etkileyen olayları (DirectX API çağrıları) ayrıntılı olarak incelersiniz.

 [Çerçeve Analizi](graphics-frame-analysis.md) Bir çerçeveyi seçmenizin ardından işleme performansınızı Grafik Çerçeve Çözümlemesi ayarlamak için çerçeveyi kullanırsiniz.

 [Olay Listesi](graphics-event-list.md) Bir çerçeveyi seçmenizin ardından  Grafik Olay Listesi'ne bakarak olayları inceler ve bunların işleme sorunuyla ilgili olup olmadığını belirlersiniz.

 [Durum](graphics-state.md) Durum penceresi, geçerli olay sırasında etkin olan grafik durumunu anlamanıza yardımcı olur.

 [İşlem Hattı Aşamaları](graphics-pipeline-stages.md) Grafik İşlem **Hattı Aşamaları** penceresinde, işleme sorununun ilk olarak nerede görüntülendiğinden emin olmak için seçili durumdaki olayın grafik işlem hattının her aşaması tarafından nasıl işlendiğinden araştırabilirsiniz. İşlem hattı aşamalarını incelemeniz, hatalı bir dönüştürme nedeniyle bir nesne görünmese veya aşamalardan biri bir sonraki aşamanın beklense bile çıkışını ürettiği zaman özellikle yararlı olur.

 [Olay Çağrı Yığını](graphics-event-call-stack.md) İşleme **sorunuyla ilgili uygulama koduna** gitmek üzere seçili durumdaki olayın çağrı yığınını incelemek için Grafik Olay Çağrı Yığını'yı kullanabilirsiniz.

 [Piksel Geçmişi](graphics-pixel-history.md) Seçili **pikselin** bu pikseli etkileyen olaylardan nasıl etkilendiğini analiz etmek için Grafik Piksel Geçmişi penceresini kullanarak, belirli türlerde işleme sorunlarına neden olan olayları veya olayların birleşimini tanımlayabilirsiniz. Piksel geçmişi, piksel gölgelendiricisi çıkışı yanlış olduğundan veya çerçeve arabelleğiyle yanlış bir şekilde birleştirilene veya pikselleri çerçeve arabelleğine ulaşmadan önce atılmış olduğu için bir nesne bile görünmeyse, yanlış şekilde işlenecekse piksel geçmişi özellikle yararlı olur.

 [Nesne Tablosu](graphics-object-table.md) Seçili durumdaki **olay için geçerli** olan belirli Direct3D nesnelerinin ve kaynaklarının özelliklerini ve içeriğini incelemek için Grafik Nesne Tablosu kullanırsınız. Nesne tablosu, bir olay sırasında etkin olan grafik cihazı bağlamını belirlemenize ve sabit arabellekler, köşe arabellekleri ve dokular gibi grafik kaynaklarının içeriğini incelemeye yardımcı olabilir.

 [HLSL Hata Ayıklayıcısı](hlsl-shader-debugger.md) O anda seçili olan olay ve grafik işlem hattı aşamasının gölgelendirici kodunun nasıl davrandığını incelemek için **HLSL Hata** Ayıklayıcısı'nın kodda adım adım ilerler, değişkenlerin içeriklerini inceler ve diğer tipik hata ayıklama görevlerini gerçekleştirebilirsiniz. Sonuçların grafik işlem hattı tarafından daha fazla işlendiğinden veya yalnızca uygulama tarafından geri okunduklarından bağımsız olarak işlem gölgelendirici kodunu incelemek için HLSL hata ayıklayıcısını da kullanabilirsiniz.

 [Komut Satırı Yakalama Aracı](command-line-capture-tool.md) Komut satırı yakalama aracını kullanarak grafik bilgilerini yakalama veya program aracılığıyla yakalama Visual Studio hızlı bir şekilde oynatın. Özellikle, otomasyon için veya bir test ortamında komut satırı yakalama aracını kullanabilirsiniz.

 [Örnekler](graphics-diagnostics-examples.md) Farklı tür işleme sorunlarını tanılamak için Grafik Tanılama araçları birlikte kullanmayı gösteren çeşitli örnekler.

## <a name="related-sections"></a>İlgili Bölümler

| Başlık | Açıklama |
| - | - |
| [Hata Ayıklayıcısı Özellik Turu](../debugger-feature-tour.md) | içinde hata ayıklama işlevini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tanıtıyor. |
| [DirectX Grafik ve Oyun](/windows/win32/directx) | DirectX grafik teknolojilerini tartışan makaleler sağlar. |
| [Visual Studio'de DirectX 12 desteği](visual-studio-graphics-diagnostics-directx-12.md) | Visual Studio'da DirectX 12 desteği hakkında Visual Studio |
