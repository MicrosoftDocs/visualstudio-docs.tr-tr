---
title: Grafik tanılama | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e40a8ce0f2785aa606922d3f9c49f3aad48f7591
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058629"
---
# <a name="visual-studio-graphics-diagnostics"></a>Visual Studio Grafik Tanılama
Visual Studio*grafik tanılama* kaydetme ve ardından Direct3D uygulamalar oluşturma ve performans sorunları çözümleme araçları kümesidir. Grafik Tanılama, Windows PC, bir Windows cihaz öykünücüsü veya bir uzak bilgisayar veya cihaz üzerinde yerel olarak çalışan uygulamalarda kullanılabilir.  

 Grafik tanılama iş akışının nasıl Direct3D uygulamanızın kullandığı kaydını yakalayarak başlar — Canlı çalıştığı gibi — davranışını hemen çözümlenebilir böylece paylaşılan ya da daha sonra kullanmak üzere kaydedildi. Yakalama oturumu başlatılabilir ve Visual Studio'dan el ile veya komut satırı Yakalama aracı ile controled **dxcap.exe**. Yakalama oturumu da başlatılabilir ve grafik tanılama yakalama API'leri kullanarak programlı olarak controled.  

 Yakalama oturumu kaydettikten sonra içeriğini Visual Studio tarafından çalınabilecek *grafik Çözümleyicisi* tam aynı kaynakları kullanarak ve işleme komutları kullanılan uygulaması herhangi bir zamanda, yakalanan kareleri yeniden. Ardından, grafik Analyer penceresinde sağlanan araçları kullanarak, yakalanan kareleri birini ayrıntılı olarak çözümlenebilir. Bu araçlar, her Direct3D API çağrısı, kaynak, işlem hattı durum nesnesi, ardışık düzen aşamasını veya yakalanan çerçevede bir piksel bile tam geçmişini incelemek için kullanılabilir. Bu araçları birlikte kullanarak, bir işleme sorunuyla sezgisel, yakalanan çerçevede görüntülenme şeklini öğesinden başlayarak ve aşağı uygulamanın kaynak kodu, gölgelendiriciler veya grafik varlıklar, sorunun kök nedenini araştırıp bulma notebook'ta incelenebilir.  

 Performans sorunlarını tanılamak için yakalanan çerçeve kullanılarak çözümlenebilecek *çerçeve analizi* aracı. Bu araç, olası performans iyileştirmeleri otomatik olarak uygulama Direct3D nasıl kullanacağını değiştirip sizin için tüm çeşitlemeleri değerlendirmesi keşfediyor. Daha önce yapmış olabilirsiniz ve bu tür değişiklikler yalnızca el ile bulmak için benchmarked hangilerinin yapılan bir fark giden. Çerçeve Analizi ile yalnızca faydalı olur bildiğiniz değişiklikler yapmanız gerekir.  

 Grafik Tanılama'yı arayın ve en iyi şekilde çalıştırın, grafik açısından zengin Direct3D uygulaması yardımcı olur.  

 Devam [genel bakış](overview-of-visual-studio-graphics-diagnostics.md) ne sunan Visual Studio grafik Tanılama hakkında daha fazla bilgi edinmek için.  

## <a name="in-this-section"></a>Bu Bölümde  
 [Genel bakış](overview-of-visual-studio-graphics-diagnostics.md)  
 Grafik tanılama iş akışı ve araçları sunar.  

 [Başlarken](getting-started-with-visual-studio-graphics-diagnostics.md)  
 Bu bölümde, Visual Studio grafik Tanılama'yı yükleme ve grafik tanılama Direct3D uygulamanızla kullanmaya başlamak nasıl öğreneceksiniz.  

 [Grafik Bilgilerini Yakalama](capturing-graphics-information.md)  
 Uygulamanızda bir işleme sorunuyla incelemek için grafik tanılama kullanmak için öncelikle uygulamayı DirectX nasıl kullandığı hakkında bilgi kaydedin. Kayıt oturumu sırasında uygulamanız çalışırken normalde, *yakalama* (diğer bir deyişle, seçin), ilgilendiğiniz çerçeveleri. Yakalamalar çerçeveleri nasıl işlendiğini hakkında ayrıntılı bilgi içerir. Yakalanan bilgiler grafik olarak kaydedebilirsiniz daha sonra incelemek veya takımınızın diğer üyeleriyle paylaşmak için günlük belgesi.  

 [GPU Kullanımı](gpu-usage.md)  
 Uygulamanızın profilini çıkarmak için grafik tanılama kullanmak için GPU kullanımı aracı kullanın. GPU kullanımı, CPU kullanımı gibi diğer profil oluşturma araçları ile uyumlu bir şekilde uygulamanızdaki performans sorunlarını katkıda bulunabilir CPU ve GPU etkinliği ilişkilendirmek için kullanılabilir.  

 [Grafik Günlük Belgesi](graphics-log-document.md)  
 Kaydedilen grafik günlüğü incelenmesi başlatmak için grafik günlüğü belge penceresinde bir yakalanan çerçeve seçmek için kullandığınız — ve hatta belirli bir pikseli — böylece ayrıntılı olarak inceleyebilir *olayları* (diğer bir deyişle, DirectX API onu etkileyen çağrıları) .  

 [Çerçeve Analizi](graphics-frame-analysis.md)  
 Bir çerçeveyi seçtikten sonra işleme performansını ayarlamak ve incelemek için grafik çerçeve çözümlemesi kullanın.  

 [Olay Listesi](graphics-event-list.md)  
 Bir çerçeveyi seçtikten sonra kullandığınız **grafik olay listesi** işleme sorunuyla ilgili olup olmadığını belirlemek için olaylarını incelemek için.  

 [State](graphics-state.md)  
 Durum Penceresi'ni geçerli olay sırasında etkin olan grafik durumu anlamanıza yardımcı olur.  

 [Ardışık Düzen Aşamaları](graphics-pipeline-stages.md)  
 İçinde **grafik ardışık düzen aşamaları** penceresinde işleme sorunun ilk göründüğü belirleyebilir seçili olan olay grafik ardışık düzeninin her aşamasında tarafından nasıl işlendiğini araştırın. Ardışık Düzen aşamaları İnceleme nesneyi nedeniyle yanlış bir dönüştürme görünmez yaklaştığında veya aşamalar birini ne sonraki aşamasına bekliyor eşleşmeyen bir çıktı üretir özellikle yararlı olur.  

 [Olay Çağırma Yığını](graphics-event-call-stack.md)  
 Kullandığınız **grafik olay çağrı yığını** , işleme sorunuyla ilişkili uygulama koduna gidebilmeniz şu anda seçili olayın çağrı yığınını incelemek için.  

 [Piksel Geçmişi](graphics-pixel-history.md)  
 Kullanarak **grafik piksel geçmişi** penceresi şu anda seçilen piksel, etkileyen olaylar tarafından nasıl etkilendiğini analiz etmek için olay veya belirli tür işleme sorunları neden olan olaylar birleşimi tanımlayabilirsiniz. Piksel gölgelendirici çıkışı olduğundan nesne yanlış işlendiğinde piksel geçmişi özellikle yararlıdır hatalı veya yanlış çerçeve arabelleği veya piksellerinin atıldı çünkü nesne bile görünmediği zaman birleştirilmiştir çerçeve arabelleği ulaşmadan önce.  

 [Nesne Tablosu](graphics-object-table.md)  
 Kullandığınız **Graphics Object Table** özelliklerini ve belirli Direct3D nesneleri ve şu anda seçili olayı için geçerli olan kaynakların içeriğini incelemek için. Nesne tablosu, bir olayı sırasında etkin olan grafik cihaz bağlamı belirlemek ve sabit arabellekler köşe arabellekleri ve dokular gibi grafik kaynakları içeriğini incelemek yardımcı olabilir.  

 [HLSL Hata Ayıklayıcısı](hlsl-shader-debugger.md)  
 Seçili olan olay ve grafik aşama işlem hattı için gölgelendirici kodu nasıl davranacağını incelemek için kullandığınız **HLSL hata ayıklayıcısı** kodda adım adım için değişkenlerin içeriğini inceleyebilir ve tipik diğer hata ayıklama görevleri. HLSL hata ayıklayıcısı, compute gölgelendirici kodu sonuçlarını grafik ardışık düzen tarafından daha fazla işlenebilir veya yalnızca, uygulamanız tarafından okunur bağımsız olarak incelemek için de kullanabilirsiniz.  

 [Komut satırı Yakalama Aracı](command-line-capture-tool.md)  
 Hızlı bir şekilde yakalayıp Visual Studio ya da programlı yakalama kullanmadan grafik bilgilerini kayıttan yürütmek için komut satırı yakalama Aracı'nı kullanın. Özellikle, bir test ortamında veya, otomasyon için komut satırı Yakalama aracı kullanabilirsiniz.  

 [Örnekler](graphics-diagnostics-examples.md)  
 Birkaç örnek grafik tanılama araçları birlikte farklı türde işleme sorunlarını tanılamak için nasıl kullanılacağını gösterir.  

## <a name="related-sections"></a>İlgili Bölümler  

| Başlık | Açıklama |
| - | - |
| [Hata ayıklayıcısı özellik turu](../debugging-in-visual-studio.md) | Hata ayıklama işlevleri tanıtır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| [DirectX grafik ve oyun](http://go.microsoft.com/fwlink/?LinkId=256498) | DirectX grafik teknolojilerini açıklayan makaleleri sağlar. |

