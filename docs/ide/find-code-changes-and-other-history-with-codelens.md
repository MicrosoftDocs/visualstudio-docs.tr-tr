---
title: CodeLens ile kod değişikliklerini ve diğer geçmişi bulma
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.CodeLens
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e11b7458c5d26d56252b228522c53b00ebadb35b
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220306"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>CodeLens ile kod değişikliklerini ve diğer geçmişi bulma

CodeLens, kodunuzu ne olduğunu Bul sırada sayesinde yalnızca işinize odaklanmanıza olanak tanır&ndash;düzenleyicisinden çıkmadan. Başvurular bir parça kodu, kod, bağlı hataları, iş öğeleri, kod incelemeleri ve birim testleri değişiklikleri bulabilirsiniz.

> [!NOTE]
> CodeLens, yalnızca Visual Studio Enterprise ve Visual Studio Professional sürümlerinde kullanılabilir. Visual Studio Community Edition'da kullanılabilir değil.

Nerede ve nasıl kodunuzu ayrı bölümlerini çözümünüzde kullanılan bakın:

![Kod Düzenleyicisi'nde CodeLens göstergeleri](../ide/media/codelens-overview.png)

Düzenleyiciden çıkmadan kodunuzda yapılan değişiklikler hakkında takımınıza başvurun:

![CodeLens - takımınızın başvurun](../ide/media/codelens-contact-info.png)

Görmek için veya CodeLens kapatıp açmak istediğiniz göstergeleri seçmek için Git **Araçları** > **seçenekleri** > **metin düzenleyici**  >  **Tüm diller** > **CodeLens**.

## <a name="find-references-to-your-code"></a>Kodunuzda başvuruları Bul

C# veya Visual Basic kodu başvuruları bulabilirsiniz.

1. Seçin **başvuruları** göstergesi veya tuşuna **Alt**+**2**.

   ![CodeLens başvuruları](../ide/media/codelens-view-references.png)

   > [!NOTE]
   > Göstergenin gösteriliyorsa **0 başvuru**, C# veya Visual Basic kodundan başvurularınız. Ancak, olabilir başvuruları diğer öğeleri gibi *.xaml* ve *.aspx* dosyaları.

2. Başvuru kodu, fareyle üzerine başvuru listesinde görüntülenecek.

   ![CodeLens - Özet başvurusu](../ide/media/codelens-peek-reference.png)

3. Başvuruyu içeren dosyayı açmak için başvuruyu çift tıklayın.

### <a name="code-maps"></a>Kod haritaları

Kod ve başvuruları, arasındaki ilişkileri görmek için [bir kod Haritası oluşturun](../modeling/map-dependencies-across-your-solutions.md). Kod Haritası kısayol menüsünde seçin **tüm başvuruları göster**.

![CodeLens - kod haritasında başvuruları](../ide/media/codelensmappedreferences.png)

## <a name="a-namefind-code-historyfind-changes-in-your-code"></a><a name="find-code-history"/>Kodunuzda değişiklikler Bul

Kodunuzun geçmişini, kodunuzu ne olduğunu görmek için inceleyin. Ya da önce dala değişiklikleri kodunuzu nasıl etkileyeceğini daha iyi anlayabilmeniz için kodunuza birleştirilmiş değişiklikleri gözden geçirin.

İhtiyacın var:

- Visual Studio Enterprise veya Visual Studio Professional

- Team Foundation Server 2013 veya üzeri, Azure DevOps Services veya Git

- [Skype Kurumsal'a](/skypeforbusiness/) ekibinizin kod düzenleyicisinden başvurma

Team Foundation sürüm denetimi (TFVC) veya Git ile depolanan C# veya Visual Basic kodu için sınıf ve yöntem düzeylerinde CodeLens ayrıntıları alın (*kod öğe düzeyinde* göstergeleri). Git deponuzu TfGit içinde barındırılıyorsa, aynı zamanda TFS iş öğelerinin bağlantılarını alın.

![Code öğesi düzeyi göstergeleri](../ide/media/codelens-element-level-indicators.png)

İçin dosya türlerini dışında *.cs* veya *.vb*, CodeLens ayrıntıları için dosyanın tamamını tek bir yerde pencerenin alt kısmında aldığınız (*dosya düzeyinde* göstergeleri).

![Dosya düzeyinde CodeLens göstergeleri](../ide/media/almcodelensfilelevelindicators.png)

### <a name="code-element-level-indicators"></a>Code öğesi düzeyi göstergeleri

Yaptıkları kod öğe düzeyi göstergelerini kimin kodunuzu ve hangi değişiklikleri görmenize olanak tanır. C# ve Visual Basic kodu için kod öğesi düzeyi göstergelerini kullanılabilir.

Team Foundation Server veya Azure DevOps Hizmetleri'ndeki Team Foundation sürüm denetimi (TFVC) kullandığınızda gördüğünüz budur:

![CodeLens: Kodunuzu tfvc'de Get değişiklik geçmişi](../ide/media/codelens-code-changes.png)

Varsayılan süre son 12 ay değeridir. Team Foundation Server'da kodunuzu depolanmışsa çalıştırarak süreyi değiştirebilirsiniz [TFSConfig komut](/tfs/server/ref/command-line/tfsconfig-cmd) ile [Codeındex komutu](../ide/codeindex-command.md) ve **/indexHistoryPeriod**bayrağı.

Bir yıl önce bu da dahil olmak üzere tüm değişikliklerin, ayrıntılı bir geçmişini görmek için seçin **tüm dosya değişikliklerini göster**:

![Tüm kod değişiklikleri göster](../ide/media/codelens-show-all-file-changes.png)

**Geçmişi** penceresi açılır:

![Geçmiş penceresinde tüm kod değişiklikleri](../ide/media/codelenscodechangeshistory.png)

Dosyalarınızı Git deposunda ve kod öğe düzeyinde değişiklik göstergesini seçin gördüğünüz budur:

![CodeLens: Kodunuzu Git Get değişiklik geçmişi](../ide/media/codelens-code-changes-git.png)

### <a name="file-level-indicators"></a>Dosya düzeyi göstergelerini

Pencerenin alt kısmındaki dosya düzeyi göstergelerini tüm bir dosyayı değişiklikleri bulun:

![CodeLens: kod dosyası ayrıntıları alın.](../ide/media/codelens-file-level.png)

> [!NOTE]
> Dosya düzeyi göstergelerini C# ve Visual Basic dosyaları için kullanılabilir değil.

Bir değişiklik hakkında daha fazla bilgi almak için bu öğeye sağ tıklayın. TFVC veya Git kullanmanıza bağlı olarak, dosya sürümlerini karşılaştırın, ayrıntılarını görüntülemek ve değişiklik izleme, dosyanın seçili sürümünü almak ve bu değişikliği yazarı e-posta için seçenek vardır. Bu ayrıntılar bazıları görünür **Takım Gezgini**.

Ayrıca, zaman içinde kodu kimin değiştirdiğini görebilirsiniz. Bu, takımınızın değişiklikleri kalıpları bulmasına ve etkilerini değerlendirmenize yardımcı olabilir.

![CodeLens: kod değişiklikleri geçmişi grafik olarak bakın.](../ide/media/codelens.png)

### <a name="find-changes-in-your-current-branch"></a>Güncel dalınızda değişiklikler Bul

Takımınızın birden çok dal, ana dal ve kararlı kod bölme riskini azaltmak için bir alt geliştirme dalı olabilir.

![CodeLens: kodunuzun ne zaman dallandırılmış Bul](../ide/media/codelensfirstbranchconceptual.png)

Kodunuzu kaç kişinin değiştirdiğini ve kaç tane değişiklik tuşlarına basarak ana dalda yapılan bulabilirsiniz **Alt**+**6**:

![CodeLens: kaç tane değişiklik dalınızda bulun.](../ide/media/codelens-branch-changes.png)

### <a name="find-when-your-code-was-branched"></a>Kodunuzun ne zaman dallandırılmış Bul

Kodunuzu dallandırılmış zaman bulmak için alt öğe dalı kodunuzda gidin. Ardından, **değişiklikleri** göstergesi veya tuşuna **Alt**+**6**:

![CodeLens: kodunuzun ne zaman dallandırılmış Bul](../ide/media/codelens-first-branch.png)

### <a name="find-incoming-changes-from-other-branches"></a>Diğer dallardan değişiklikleri bulun

![CodeLens: kod değişikliklerini diğer dalları bulun.](../ide/media/codelensbranchchangecheckinconceptual.png)

Gelen değişiklikleri görüntüleyebilirsiniz. Aşağıdaki ekran görüntüsünde, "Dev" daldaki bir hata düzeltmesi yapıldı:

![CodeLens: Başka bir dalla değişikliği iade](../ide/media/codelens-branch-changes-dev.png)

Güncel dalı ("ana") çıkmadan değişiklik gözden geçirebilirsiniz:

![CodeLens: bkz. başka bir daldan gelen değiştirme](../ide/media/codelens-branch-changes-main.png)

### <a name="find-when-changes-got-merged"></a>Değişiklikleri birleştirdiğimde Bul

Böylece hangi değişikliklerin dalınızda bulunan belirleyebilir, ne zaman değişiklikleri birleştirilmiş, görebilirsiniz:

![CodeLens - dallar arasında birleştirilen değişiklikleri](../ide/media/codelensbranchmergedconceptual.png)

Örneğin, ana dalda kodunuz artık "Dev" dalından hata düzeltmesi sahiptir:

![CodeLens - dallar arasında birleştirilen değişiklikleri](../ide/media/codelens-branch-merged.png)

### <a name="compare-an-incoming-change-with-your-local-version"></a>Gelen bir değişiklik yerel sürüm ile Karşılaştır

Yerel sürümünüzle birlikte gelen bir değişikliği tuşlarına basarak karşılaştırma **Shift**+**F10**, veya değişiklik kümesini çift tıklayın.

![CodeLens: gelen değişiklik yerel ile Karşılaştır](../ide/media/codelens-branch-incoming-change-menu.png)

### <a name="branch-icons"></a>Dal simgeleri

Simge **dal** sütun bildirir dal nasıl ilişkili olduğunu içinde çalışmakta olduğunuz dalı için.

|**Simgesi**|**Değişiklik geldiği:**|
|--------------| - |
|![CodeLens: geçerli dal simgesini değiştirme](../ide/media/codelensbranchcurrenticon.png)|Geçerli dal|
|![CodeLens: üst dalı simgesini değiştirme](../ide/media/codelensbranchparenticon.png)|Üst dal|
|![CodeLens: alt öğe dalı simgesini değiştirme](../ide/media/codelensbranchchildicon.png)|Bir alt öğe dalı|
|![CodeLens: Eş dal simgesini değiştirme](../ide/media/codelensbranchpeericon.png)|Bir eş dal|
|![CodeLens: dal daha koyma simgesini değiştirme](../ide/media/codelensbranchfurtherawayicon.png)|Daha fazla dal parent, child veya eş daha kaldı|
|![CodeLens: üst simge Birleştir](../ide/media/codelensbranchmergefromparenticon.png)|Üst dalından bir alt öğe dalı birleştirme|
|![CodeLens: alt öğe dalı simgesinden Birleştir](../ide/media/codelensbranchmergefromchildicon.png)|Bir alt dalından ana dala birleştirme|
|![CodeLens: ilişkisiz dal simgesinden Birleştir](../ide/media/codelensbranchmergefromunrelatedicon.png)|İlişkisiz bir daldan (tabansız birleştirme) birleştirme|

## <a name="linked-work-items"></a>Bağlantılı iş öğeleri

Seçerek bağlantılı iş öğelerini bulma **iş öğelerini** göstergesi veya basarak **Alt**+**8**.

![CodeLens - belirli bir kod için çalışma öğeleri bulun](../ide/media/codelens-work-items.png)

## <a name="linked-code-reviews"></a>Bağlantılı kod incelemeleri

Bağlantılı kod incelemeleri seçerek bulmak **incelemeleri** göstergesi. Klavyeyi kullanmak için basılı **Alt** anahtar ve tuşuna **sol ok** veya **sağ ok** gösterge seçeneklerini gidin.

![CodeLens - kodu görüntüle isteklerini gözden geçirme](../ide/media/codelens-code-reviews.png)

## <a name="linked-bugs"></a>Bağlantılı hataları

Seçerek bağlantılı hataları bulun **hataları** göstergesi veya basarak **Alt**+**7**.

![CodeLens - bağlı değişiklik kümelerini Bul hataları](../ide/media/codelens-bugs-changesets.png)

## <a name="contact-the-owner-of-an-item"></a>Bir öğenin sahibiyle iletişime geçin

Öğeyi yazarı seçerek bulma **yazarlar** göstergesi veya basarak **Alt**+**5**.

![Bir öğenin sahibiyle iletişime geçin](../ide/media/codelens-contact-item-owner.png)

İlgili kişi seçeneklerini görmek için bir öğe için kısayol menüsünü açın. Lync veya Skype Kurumsal'a yüklü olan bu seçenekleri görürsünüz:

![Bir öğe için ilgili kişi seçeneklerini](../ide/media/codelens-item-contact-menu.png)

## <a name="associated-unit-tests"></a>İlişkili birim testleri

Mevcut birim testleri, C# veya Visual Basic kodunuzda açmadan bulabilir **Test Gezgini**.

1. İlişkili uygulama koduna gidin [birim testi kodu](../test/unit-test-your-code.md).

2. Zaten varsa, test CodeLens Göstergeleri yüklemek için uygulamanızı oluşturun. Emin [bulma tarafından derlenen bütünleştirilmiş kodlar](../test/test-explorer-faq.md#assembly-based-discovery) açıktır.

3. Kod için testleri tuşlarına basarak gözden **Alt**+**3**.

     ![CodeLens - seçin Kod Düzenleyicisi'nde test durumu](../ide/media/codelens-choose-test-indicator.png)

4. Bir uyarı simgesi görürseniz ![uyarı simgesi](../ide/media/codelenstestwarningicon.png), testleri henüz çalıştırmak henüz, bu nedenle bunları çalıştırın.

     ![CodeLens - görünüm birim testleri henüz Çalıştır](../ide/media/codelens-tests-not-yet-run.png)

5. Bir testin tanımını gözden geçirmek için düzenleyicide kod dosyasını açmak için CodeLens göstergesi penceresinde test öğesini çift tıklayın.

     ![CodeLens - birim testi tanımına Git](../ide/media/codelens-unit-test-definition.png)

6. Test sonuçlarını gözden geçirmek için test durumu göstergesini seçin (![başarısız test simgesini](../ide/media/codelenstestfailedicon.png) veya ![testi geçildi simgesi](../ide/media/codelenstestpassedicon.png)), veya basın **Alt**+**1**.

     ![CodeLens - bkz. birim testi sonucu](../ide/media/codelens-unit-test-result.png)

7. Bu testi kaç kişinin değiştirdiğini, bu testi kimin değiştirdiğini veya kaç değişiklik bu test ile yapılan görmek için [kodunuzun geçmişini bulun](#find-code-history) ve bağlantılı öğe.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

Göstergeleri seçmek için klavyeyi kullanmak için basılı tutun **Alt** seçmek istediğiniz anahtar ilgili sayı tuşlarını görüntülemek, ardından göstergesini karşılık gelen tuşuna basın.

![Klavye erişim numaraları](../ide/media/codelens-alt-keys.png)

> [!NOTE]
> Seçilecek **incelemeleri** göstergesi, basılı **Alt** gezinmek için sol ve sağ ok tuşlarını kullanarak.

## <a name="q--a"></a>Soru - Yanıt

### <a name="q-how-do-i-turn-codelens-off-or-on-or-choose-which-indicators-to-see"></a>S: CodeLens açma veya kapatma, veya nasıl görmek için hangi göstergelerini seçin?

**Y:** göstergeleri kapalı veya açık başvuru göstergesini dışında etkinleştirebilirsiniz. Git **Araçları** > **seçenekleri** > **metin düzenleyici** > **tüm diller**  >  **CodeLens**.

Göstergeler açık olduğunda, CodeLens seçeneklerini göstergelerden açabilirsiniz.

![CodeLens - veya devre dışı bırakma göstergeleri](../ide/media/codelensturnoffonindicatorsfromcode.png)

CodeLens dosya düzeyi göstergelerini açma ve kapatma köşeli çift ayraç simgelerini Düzenleyicisi penceresinin alt kısmında kullanarak etkinleştirin.

![Dosya düzeyi göstergelerini açıp kapatma](../ide/media/codelensfilelevelonandoff.png)

### <a name="q-where-is-codelens"></a>S: CodeLens nerede?

**Y:** yöntemi, sınıfı, dizin oluşturucu ve özellik düzeyinde C# ve Visual Basic kodu CodeLens görünür. CodeLens dosya düzeyi tüm dosya türleri için görünür.

- CodeLens açık olduğundan emin olun. Git **Araçları** > **seçenekleri** > **metin düzenleyici** > **tüm diller**  >  **CodeLens**.

- Kodunuzu TFS içinde depolanır, kod dizini oluşturma kullanarak açık olduğundan emin olun [Codeındex komutu](../ide/codeindex-command.md) ile [TFS Yapılandırma komut](/tfs/server/ref/command-line/tfsconfig-cmd).

- DevOps ile ilgili göstergeler, yalnızca bağlı iş öğesi için kod ve bağlı iş öğelerini açma izniniz olduğunda görünür. Sahip olduğunuzu onaylamak [takım üyesi izinlerine](/azure/devops/organizations/security/view-permissions?view=vsts).

- Birim test göstergeleri, uygulama kodu birim testlere sahip olmadığında görünmez. Test durumu göstergeleri test projesinde otomatik olarak görüntülenir. Uygulama kodunuzun birim testleri var, ancak test göstergeleri görünmüyorsa biliyorsanız, çözümü derlemeyi deneyin (**Ctrl**+**Shift**+**B**).

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>S: işleme iş öğesi ayrıntılarını neden göremiyorum?

**Y:** Azure panoları veya TFS iş öğeleri CodeLens bulamadığından gerçekleşebilir. Bu olan projesine bağlı değilseniz denetleyin, çalışma öğeleri ve bunları görme iznine sahip iş öğeleri. İş öğesi ayrıntıları, yürütme açıklama iş öğesi kimlikleri Azure panoları veya TFS yanlış bilgi olup olmadığını da göstermeyebilir.

### <a name="q-why-dont-i-see-the-skype-indicators"></a>S: neden Skype göstergeleri göremiyorum?

**Y:** Skype Kurumsal'a oturum açmadıysanız, Lync yüklü veya desteklenen bir yapılandırmaya sahip değilseniz, Skype göstergeleri görünmez. Bununla birlikte, e-posta göndermeye devam edebilir:

![CodeLens - posta yoluyla iletişim değişiklik kümesi sahibi](../ide/media/codelenscodesendmailchangesetnolync1.png)

**Hangi Skype ve Lync yapılandırmaları desteklenir?**

- Skype Kurumsal'a (32 bit veya 64-bit)

- Lync 2010 veya daha sonra tek başına (32 bit veya 64-bit), ancak değil, Lync Basic 2013 ile Windows 8.1

CodeLens, farklı Lync sürümlerine sahip desteklemiyor veya Skype yüklü. Bunlar, Visual Studio'nun tüm yerelleştirilmiş sürümleri için yerelleştirilmiş olmayabilir.

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>S: nasıl yazı tipi ve renk için CodeLens değiştirebilirim?

**Y:** Git **Araçları** > **seçenekleri** > **ortam** > **yazı tipleri ve renkler**.

![CodeLens - yazı tipi ve renk ayarlarını değiştir](../ide/media/codelensoptionsfontscolorssettings.png)

Klavyeyi kullanmak için:

1. Tuşuna **Alt**+**T**+**O** açmak için **seçenekleri** iletişim kutusu.

2. Basın **yukarı ok** veya **aşağı ok** gitmek için **ortam** düğümünü tuşuna **sol ok** düğümü genişletmek için.

3. Tuşuna **aşağı ok** gitmek için **yazı tipleri ve renkler**.

4. Basın **sekmesini** gitmek için **ayarlarını göster** listelemek ve tuşuna **aşağı ok** seçmek için **CodeLens**.

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>S: CodeLens ekran göstergesi görüntüsünü taşıyabilir miyim?

**Y:** Evet, seçin ![Dock simgesi](../ide/media/codelensdockwindow.png) Codelens'i pencere olarak yerleştirmek için.

![CodeLens göstergesi penceresinde Dock düğmesi](../ide/media/codelensselectdockwindow.png)

![Yerleşik CodeLens başvuruları pencere](../ide/media/codelensreferencesdockedwindow.png)

### <a name="q-how-do-i-refresh-the-indicators"></a>S: Göstergeleri nasıl yenileyebilirim?

**Y:** Bu gösterge üzerinde bağlıdır:

- **Başvuruları**: kod değiştiğinde bu gösterge otomatik olarak güncelleştirir. Varsa **başvuruları** göstergesi ayrı bir pencerede yerleştirilmiş, göstergenin Yenile'yi **Yenile**:

     ![Yenile düğmesi CodeLens başvurularda](../ide/media/codelensviewreferencesdocked.png)

- **Takım**: seçerek bu göstergelerini Yenile **CodeLens takım göstergelerini Yenile** sağ tıklatma menüsünden:

     ![CodeLens takım göstergeleri menü öğesi Yenile](../ide/media/codelensrefreshindicatorsfromcode.png)

- **Test**: [kodunuz için birim testleri bulmak](#associated-unit-tests) yenilemek için **Test** göstergesi.

### <a name="q-whats-local-version"></a>S: "Yerel sürüm" nedir?

**Y:** **yerel sürüm** ok yerel sürümünüzde bir dosyanın en son değişiklik kümesini işaret eder. Üstüne veya altına sunucunun daha yeni değişiklik kümeleri olduğunda, göründükleri **yerel sürüm** ok, değişiklik kümelerini sıralarken kullanılan düzene bağlı olarak.

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>CodeLens kod geçmişini ve ilişkili öğeleri göstermek için nasıl işlediği yönetebilir miyim?

**Y:** Evet. Kodunuzu TFS içinde ise, kullanın [Codeındex komutu](../ide/codeindex-command.md) ile [TFS Yapılandırma komut](/tfs/server/ref/command-line/tfsconfig-cmd).

### <a name="q-my-codelens-test-indicators-no-longer-appear-in-my-file-when-i-first-open-my-solution-how-can-i-load-them"></a>S: Alanım CodeLens test göstergeleri, artık çözümüm'ı ilk kez açtığınızda my dosyasında görünür. Bunları nasıl yüklenmesi miyim?

**Y:** dosyanıza yüklemek için CodeLens test göstergeleri almak için projenizi yeniden derleyin. Emin [bulma tarafından derlenen bütünleştirilmiş kodlar](../test/test-explorer-faq.md#assembly-based-discovery
) açıktır. Kod dosyalar yüklendiğinde performansını geliştirmek için Visual Studio artık test göstergeleri için kaynak bilgileri getirir. Test göstergeleri, bir derlemeden sonra veya bir testi içinde çift tıklayarak gittiğinizde yüklenir **Test Gezgini**.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Düzenleyicisi özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
