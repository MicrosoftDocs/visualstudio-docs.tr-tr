---
title: Sorun bildir
description: Sorun raporu genel bir bakış sağlar ve sorun durumları ve tanımları içerir
ms.date: 11/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.custom: seodec18
ms.topic: conceptual
author: seaniyer
ms.author: seiyer
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b6d7605cffeca2797d47aa90c6f64a1aab0a6cb2
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159834"
---
# <a name="overview-report-a-problem"></a>Genel Bakış: Sorun bildir

Sorun raporu sorunları göndermek Visual Studio Geliştirici topluluğu sağlar. Her biri, sorun raporları, sistem tasarımı, etkili sorunlarını belirleyin ve çözün yardımcı olmak için doğrudan ürün ekiplerimiz ile etkileşim kurmak için güçlendirin bizim core'da bir iş öğesi olur. Visual Studio ürün ailesi geliştirmek için zengin tanılama bilgileriyle birlikte gönderilen Geri bildiriminiz önemlidir. Biz aslında, sorunları bildirmek zaman ayırdığınız için teşekkür ederiz.

Ayrıca, bir sorun daha fazla dikkatine için diğer topluluk üyelerinden geri bildirimi oy verin ve daha hızlı düzeltin yardımcı.

## <a name="problem-status"></a>Sorun durumu

Sorun bildir sonra gönderimlerinizi kendi yaşam döngüsünde nerede olduğunuza durumları gösterir. Microsoft teams'de Geri bildiriminizi gözden geçirirken, bunlar uygun bir durum ile ayarlayın.  Anlamı ve renk göstergelerini yanı sıra aşağıda listelenen durumları başvuru tarafından sorun raporları ilerlemesini izleyin.

![Geliştirici topluluğu üzerinde raporlama sorunu için yeni durum](../ide/media/ProblemStates/New.jpg)

**Yeni** yeni hata veya sorun bildirilir ve herhangi bir işlem üzerinde henüz alınmış gösterir.

- - -

![Geliştirici topluluğu üzerinde raporlama sorun Değerlendirilmiş ili](../ide/media/ProblemStates/Triaged.jpg)

**Değerlendirilmiş** denetimi, çeviri ve ilk yinelemeleri denetleme gibi ilk adımlar tamamlandı olduğunu gösterir. Anahtarınızı, göz önünde bulundurmanız gereken uygun mühendislik ekibine yönlendirilir.

- - -

![Geliştirici topluluğu üzerinde raporlama sorun için göz önünde bulundurarak durumu altında](../ide/media/ProblemStates/UnderConsideration.jpg)

**İncelenmekte** Microsoft sorununuzu topluluk etkiyi gözden geçirme ve buna göre sıralayacağını belirtir. Topluluk etkisi henüz açık ya da önemli değilse, ki bu durumda sorunu izlemek devam edeceğiz.

- - -

![Geliştirici topluluğu bildirdiği sorunun durumu araştırma altında](../ide/media/ProblemStates/UnderInvestigation.jpg)

**Araştırma altında** mühendisleri sorununuzu bir çözüm bulmak için sorun etkin olarak araştırılmaktadır gösterir.

- - -

![Geliştirici topluluğu üzerinde raporlama sorunla ilgili daha fazla bilgi durumu gerekir](../ide/media/ProblemStates/NeedMoreInfo.jpg)

**Daha fazla bilgi gerekiyor** biz araştırmaya İleri gidip gidemeyeceğini emin ediyoruz sizden daha fazla tanılama bilgisi gerektiğini belirtir.  [Daha fazla bilgi gerekiyor isteklerine yanıt öğrenin.](./how-to-report-a-problem-with-visual-studio-2017.md#when-further-information-is-needed-need-more-info)

- - -

![Düzeltildi - Yayınlanmayı bekliyor Geliştirici topluluğu üzerinde raporlama sorun için durum](../ide/media/ProblemStates/FixedPendingRelease.jpg)

**-Release bekleyen sabit** sorunu için düzeltme sunuyoruz ve bir sonraki Önizleme veya sürüm kullanılabilir olacaktır gösterir.  Düzeltme Önizleme aşamasında kullanıma sunulduğunda, sorun, önizleme sürümünü belirtme 'sürümünde düzeltilen' etiketiyle etiketlenir.

- - -

![Kapalı - Geliştirici topluluğu üzerinde raporlama sorun düzeltildi durumu](../ide/media/ProblemStates/ClosedFixed.jpg) 

**Kapatıldı - düzeltildi** sorunu için düzeltme yayımladık gösterir. Sorunun artık ile etiketlenmiş bir "sürümünde düzeltilen:" yayın sürümünü belirtme etiketi.

- - -

![Kapatıldı - yinelenen Geliştirici topluluğu bildirdiği sorunun durumu](../ide/media/ProblemStates/ClosedDuplicate.jpg)

**Kapatıldı - yinelenen** sorununuzu aracılığıyla başka bir geri bildirim zaten bildirildi gösterir. Burada, özgün sorun raporunda izleyebilirsiniz bağlantıyla sağlarız.

- - -

![Geliştirici topluluğu üzerinde raporlama sorun önceliği durumunu Kapalı - düşük](../ide/media/ProblemStates/ClosedLowerPriority.jpg)

**Kapalı - düşük öncelik** en iyi değeri Geliştirici topluluğumuz yürütüyoruz her biri, odaklanmak için size yüksek müşteri etkisi olan sorunları önceliklendirin. Şu anda bu sorunu çözmek üzere alamıyoruz olsa da, tüm Geri bildiriminiz önemlidir ve yardımcı olan Visual Studio geliştirmek yararlandığından emin.

- - -

![Kapalı - Geliştirici topluluğu üzerinde raporlama sorun için bir hata durumu değil](../ide/media/ProblemStates/ClosedNotaBug.jpg)

**Kapatıldı - hata değil** biz bildirilen işlevler tarafından geçerli tasarım olduğunu saptadıktan gösterir.

- - -

![Kapalı - yeterli bilgi durumu sorunun Geliştirici topluluğu üzerinde raporlama](../ide/media/ProblemStates/ClosedNotEnoughInfo.jpg)

**Kapalı - yeterli bilgi** biz sizin için bunu araştırmak için yeterli bilgimiz yok gösterir. Geri bildirim gerekli bilgileri kullanılabilir olduktan sonra yeniden gözden geçir mutluluk duyarız.

- - -

![Kapalı - diğer Geliştirici topluluğu üzerinde raporlama sorun için ürün durumu](../ide/media/ProblemStates/ClosedOtherProduct.jpg)

**Kapalı - diğer ürün** biz belirlenen sorununuzu başka bir ürün için geçerli olduğunu gösterir. Bağlantılar için dış ürün ve tüm ilgili Microsoft yorumu bakın.

- - -

![Kapatıldı - Geliştirici topluluğu üzerinde raporlama sorun durumu Düzeltilmeyecek](../ide/media/ProblemStates/ClosedWontFix.jpg)

**Kapatıldı - Düzeltilmeyecek** Biz bu sorun nedeniyle ürün yönü hizalama veya topluluk etkisi olmaması gibi faktörlere sürdürdüğünü olmayan gösterir. Microsoft herhangi bir ek açıklama için yorum bakın.  Bu sorunu çözmek için tüm geri bildirim için önemlidir ve yardımcı olabilirsiniz alamıyoruz olsa da Visual Studio geliştirin.

- - -

## <a name="faq"></a>SSS

### <a name="how-can-i-increase-the-chance-of-my-problem-getting-resolved-quickly"></a>Sorunumu hızlıca çözülebilmesi alma olasılığını nasıl artırabilirim?

Arama olduğunuz için rapor sorun zaten bildirilmiş taşınmadığından emin olmak için kullanmanızı öneririz. Sorununuzu eşleşen var olan bir öğeye bulursanız, izleyin ve bu sorun anahtar oy verin.

 Ekiplerimiz ne karşılaştığınız yeniden oluşturmak için mümkün olan tüm bilgileri sağlar.  Bu bilgiler gerekli yineleme adımları, kod parçalarını, ekran görüntüleri, yineleme Kayıtları, günlük dosyaları ve diğer yapıtları içerir.  İşte [Visual Studio'daki sorun bildirme](./how-to-report-a-problem-with-visual-studio-2017.md).

### <a name="how-is-my-feedback-prioritized"></a>Nasıl geri bildirimimi kurtarılmasına öncelik verilir?

Çok sayıda önemli sorunları müşterilerimizden aldığımız. En iyi değeri her biriniz Geliştirici topluluğumuz taşıyoruz emin olmak için size yüksek topluluk etkisi geri bildirim eylemi öncelik verin.

Sizi kişisel olarak geri bildirimlerinize yanıt açamıyorsanız, tam olarak girdi veriyoruz bildirin. Tüm geri bildirim doğru ekibe alır yararlandığından emin.

Biz, Visual Studio'nun daha iyi kolaylaştırmaya yönelik Yatırımlar zaman gerçek anlamda değer.

### <a name="what-actions-can-i-take-if-im-not-satisfied-with-the-resolution"></a>Çözünürlükten memnun değilim, hangi eylemlerin ben yararlanabilir miyim?

Karşılaştığınız sorunları tanılayıp en iyi şekilde ekiplerimiz yapın, ancak Bizim önerimiz ile tam olarak memnun olduğunuzda olmayan zamanlar olabilir. Yorum, geribildirim ve tam olarak ne bize bildirin memnun değilseniz ve gereksinimlerinizi karşıladığından emin olmak üzere size en uygun denenir.

### <a name="how-will-i-get-notified-of-progress-on-my-feedback"></a>Nasıl ilerleme durumunu bildirimim hakkında bildirim?

Microsoft mühendislik ekipleri size geri bildirim anahtar yorum ve bunların ilerleme yaparken, bilet durumunu değiştirme iletişim kurar. Bilet durum değişikliklerini veya yorum gönderildiğinde, gönderilen e-posta bildirimleri izleyin.  Geliştirici topluluğu sitesini profili ve Tercihleri ayarlarını Bildirimlerde sıklığını yönetebilirsiniz.

### <a name="why-cant-i-add-a-problem-for-visual-studio-ide-on-the-developer-community-website"></a>Neden bir sorun için Visual Studio IDE Geliştirici topluluğu Web sitesinde ekleyemiyorum?

Visual Studio aracılığıyla bir sorun bildirme raporda otomatik olarak dahil edilecek tanılama bilgileri sağlar. Bunu mühendislerimize sorun ve bu sorunu çözmek için iş tam olarak anlamak için ihtiyaç duydukları içerik sunan temel bilgilerdir.

Visual Studio aracılığıyla bildirdiğinde gibi büyük günlük dosyaları, kilitlenme bilgi, ekran görüntüleri, yineleme kaydı ve bize yardımcı olan diğer yapıtlar, daha kaliteli çözümler daha hızlı sunun, kolayca zengin tanılama bilgileri bizimle paylaşabilirsiniz.