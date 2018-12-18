---
title: Kod değişikliklerini ve CodeLens ile diğer geçmişi bulma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f697d7b4-704e-4cac-b13a-bc57d2ff8318
caps.latest.revision: 134
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: df4b435f791b066afda90ac9f5492a946d7e215c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825679"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>CodeLens ile kod değişikliklerini ve diğer geçmişi bulma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

-Kod düzenleyiciden çıkmadan ne olduğunu Bul sırada, çalışmasına odaklı kalmak. Başvuruları ve değişiklikleri kod, bağlı hataları, iş öğeleri, kod incelemeleri ve birim testlerini bulun.  
  
> [!NOTE]
>  CodeLens, yalnızca Visual Studio Enterprise ve Visual Studio Professional sürümlerinde kullanılabilir. Visual Studio Community Edition'da kullanılabilir değil.  
  
 Nerede ve nasıl kodunuzu ayrı bölümlerini çözümünüzde kullanılan bakın:  
  
 ![Kod Düzenleyicisi'nde CodeLens göstergeleri](../ide/media/codelensoverview.png "CodeLensOverview")  
  
 Düzenleyiciden çıkmadan kodunuzda yapılan değişiklikler hakkında takımınıza başvurun:  
  
 ![CodeLens &#45; ekibinize başvurun](../ide/media/codelensovervew2.png "CodeLensOvervew2")  
  
 Görmek için veya CodeLens kapatıp açmak istediğiniz göstergeleri seçmek için Git **Araçları**, **seçenekleri**, **metin düzenleyici**, **tüm diller** , **CodeLens**.  
  
##  <a name="FindReferences"></a> Kodunuzda başvuruları Bul  
 Şunları yapmanız gerekir:  
  
- Visual Studio Enterprise veya Visual Studio Professional  
  
- Visual C# .NET veya Visual Basic .NET kodunu  
  
  Seçin **başvuruları** göstergesi (**Alt + 2**). Görürseniz **0 başvuru**, Visual C# veya Visual Basic kodundan başvurularınız. Bu, XAML ve ASPX dosyaları gibi diğer öğelerdeki başvuruları içermez.  
  
  ![CodeLens &#45; başvuru göstergesini seçin](../ide/media/codelensviewreferenceslist.png "CodeLensViewReferencesList")  
  
  Başvuru kodu görmek için başvuru üzerinde fareyi hareket ettirin.  
  
  ![CodeLens &#45; Özet başvuru](../ide/media/codelensviewreferencespeekreference.png "CodeLensViewReferencesPeekReference")  
  
  Başvuruyu içeren dosyayı açmak için başvuruyu çift tıklayın.  
  
  Bu kod ve başvuruları, arasındaki ilişkileri görmek için [bir kod Haritası oluşturun](../modeling/map-dependencies-across-your-solutions.md) ve **tüm başvuruları göster** kod Haritası kısayol menüsünde.  
  
  ![CodeLens &#45; başvuruları kod haritasında](../ide/media/codelensmappedreferences.png "CodeLensMappedReferences")  
  
##  <a name="FindCodeHistory"></a> Kodunuzun geçmişini ve ilişkili öğeleri bulun  
 Kodunuzun geçmişini, kodunuzu ne olduğunu görmek için gözden geçirin. Ya da önce dala değişiklikleri kodunuzu nasıl etkileyeceğini daha iyi anlayabilmeniz için kodunuza birleştirilmiş değişiklikleri gözden geçirin.  
  
 Şunları yapmanız gerekir:  
  
- Visual Studio Enterprise veya Visual Studio Professional  
  
- Team Foundation Server 2013 veya üzeri, Visual Studio Team Services veya Git  
  
- [Lync 2010 veya üzeri ya da Skype Kurumsal'a](http://technet.microsoft.com/lync), takımınızın kod düzenleyicisinden başvurma  
  
  Team Foundation sürüm denetimi (TFVC) veya Git ile depolanan Visual C# .NET veya Visual Basic .NET kodu için sınıf ve yöntem düzeylerinde CodeLens ayrıntıları alın (*kod öğe düzeyinde* göstergeleri). Git deponuzu TfGit içinde barındırılıyorsa, aynı zamanda TFS iş öğelerinin bağlantılarını alın.  
  
  ![Kod öğesi&#45;düzey göstergeler](../ide/media/codelenselementlevelindicators.png "CodeLensElementLevelIndicators")  
  
  Tüm diğer Visual Studio düzenleyicisinde açabileceğiniz dosya türlerinde, CodeLens ayrıntıları dosyanın tamamını tek bir yerde pencerenin alt kısmında alın (*dosya düzeyinde* göstergeleri).  
  
  ![Dosya&#45;CodeLens göstergeleri düzey](../ide/media/almcodelensfilelevelindicators.png "ALMCodeLensFileLevelIndicators")  
  
  Göstergeleri seçmek için klavyeyi kullanmak için basılı tutun **ALT** ilgili sayı anahtarlarını görüntülemek için anahtar.  
  
  ![Klavye erişimi sayıları görmek için ALT tuşuna basın](../ide/media/codelensaltkeyindicators.png "CodeLensAltKeyIndicators")  
  
### <a name="find-changes-in-your-code"></a>Kodunuzda değişiklikler Bul  
 C# veya Visual Basic kodu kimin değiştirdiğini ve bunlar kod öğe düzeyi göstergelerini yapılan değişiklikleri bulun. Team Foundation Server veya Visual Studio Team Services, Team Foundation sürüm denetimi (TFVC) kullandığınızda gördüğünüz budur.  
  
 ![CodeLens: Get değişiklik geçmişi için kodunuzu tfvc'de](../ide/media/codelenscodechanges.png "CodeLensCodeChanges")  
  
 Varsayılan süre son 12 ay değeridir. Team Foundation Server'da kodunuzu depolanırsa, bu çalıştırarak değiştirebileceğiniz [TFSConfig komut](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62) ile [Codeındex komutu](../ide/codeindex-command.md) ve **/indexHistoryPeriod** bayrağı.  
  
 Bir yıl önce bu da dahil olmak üzere tüm değişikliklerin, ayrıntılı bir geçmişini görmek için seçin **tüm dosya değişikliklerini göster**.  
  
 ![Tüm kod değişiklikleri göster](../ide/media/codelensshowsallchanges.png "CodeLensShowsAllChanges")  
  
 Bu değişiklik kümesinin Geçmiş penceresinde açar.  
  
 ![Tüm kod değişiklikleri için Geçmiş penceresinde](../ide/media/codelenscodechangeshistory.png "CodeLensCodeChangesHistory")  
  
 Dosyalarınızı Git deposunda ve kod öğe düzeyinde değişiklik göstergesini seçin gördüğünüz budur.  
  
 ![CodeLens: Get değişiklik geçmişi için kodunuzu git'te](../ide/media/codelenscodechangesgit.png "CodeLensCodeChangesGit")  
  
 Pencerenin alt kısmındaki dosya düzeyi göstergelerini değişiklikleri (C# ve Visual Basic dosyaları) hariç tüm dosyayı bulun.  
  
 ![CodeLens: kod dosyası ayrıntılarınıza](../ide/media/codelensfilelevel.png "CodeLensFileLevel")  
  
 Bir değişiklik hakkında daha fazla bilgi almak için bu öğeye sağ tıklayın. TFVC veya Git kullanmanıza bağlı olarak, bir dizi seçenekleri dosya sürümlerini karşılaştırın, ayrıntılarını görüntülemek ve değişiklik izleme, dosyanın seçili sürümünü almak ve bu değişikliği yazarı e-posta alırsınız. Bu ayrıntılar bazıları, Takım Gezgini'nde görünür.  
  
 Ayrıca, zaman içinde kodu kimin değiştirdiğini görebilirsiniz. Bu, takımınızın değişiklikleri kalıpları bulmasına ve etkilerini değerlendirmenize yardımcı olabilir.  
  
 ![CodeLens: Bkz: kod değişikliklerini geçmişi grafik olarak](../ide/media/codelens.png "CodeLens")  
  
#### <a name="find-changes-in-your-current-branch"></a>Güncel dalınızda değişiklikler Bul  
 Birden çok dal - ana dal ve alt geliştirme - kararlı kod bölme riskini azaltmak için takımınızın sahip olduğunu varsayın:  
  
 ![CodeLens: kodunuzun ne zaman dallandırılmış Bul](../ide/media/codelensfirstbranchconceptual.png "CodeLensFirstBranchConceptual")  
  
 Kodunuzu kaç kişinin değiştirdiğini ve kaç tane değişiklik yapılmışsa bulun (**Alt + 6**) ana dalınızdaki:  
  
 ![CodeLens: kaç dalınızda değişiklikler Bul](../ide/media/codelensbranchchanges.png "CodeLensBranchChanges")  
  
#### <a name="find-when-your-code-was-branched"></a>Kodunuzun ne zaman dallandırılmış Bul  
 Kodunuzu alt dal gibi geliştirme dalını buraya gidin. Değişiklik göstergesini seçin (**Alt + 6**):  
  
 ![CodeLens: kodunuzun ne zaman dallandırılmış Bul](../ide/media/codelensfirstbranchscreenshot.png "CodeLensFirstBranchScreenshot")  
  
#### <a name="find-incoming-changes-from-other-branches"></a>Diğer dallardan değişiklikleri bulun  
 ![CodeLens: Kod değişikliklerini diğer dalları Bul](../ide/media/codelensbranchchangecheckinconceptual.png "CodeLensBranchChangeCheckinConceptual")  
  
 .. Bu hata düzeltmesi olarak Geliştirme dalında burada biçiminde yazarsınız:  
  
 ![CodeLens: Başka bir dalla değişikliği iade](../ide/media/codelensbranchchangedevscreenshot.png "CodeLensBranchChangeDevScreenshot")  
  
 Bu değişiklik, güncel dalı (ana) çıkmadan gözden geçirebilirsiniz:  
  
 ![CodeLens: bkz. başka bir daldan gelen değiştirme](../ide/media/codelensbranchchangemainscreenshot.png "CodeLensBranchChangeMainScreenshot")  
  
#### <a name="find-when-changes-got-merged"></a>Değişiklikleri birleştirdiğimde Bul  
 Bu nedenle, hangi değişikliklerin dalınızda bulunan görebilirsiniz:  
  
 ![CodeLens &#45; birleştirilen değişiklikleri dallar arasında](../ide/media/codelensbranchmergedconceptual.png "CodeLensBranchMergedConceptual")  
  
 Örneğin, ana dalda kodunuzu geliştirme dalındaki hata düzeltmesi artık sahiptir:  
  
 ![CodeLens &#45; chagnes dallar arasında birleştirilmiş](../ide/media/codelensbranchmergedscreenshot.png "CodeLensBranchMergedScreenshot")  
  
#### <a name="compare-an-incoming-change-with-your-local-version-shift--f10"></a>Yerel sürümünüz (Shift + F10) gelen bir değişiklikle karşılaştırın  
 ![CodeLens: yerel gelen değişikliğiyle karşılaştırma](../ide/media/codelensbranchincomingchangemenu.png "CodeLensBranchIncomingChangeMenu")  
  
 Ayrıca, değişiklik kümesini çift tıklatabilirsiniz.  
  
#### <a name="what-do-the-icons-mean"></a>Simgeleri ne anlama gelir?  
  
|**Simgesi**|**Nerede değişiklik nereden geldi?**|  
|--------------|-----------------------------------------|  
|![CodeLens: Geçerli dal simgesini değiştirme](../ide/media/codelensbranchcurrenticon.png "CodeLensBranchCurrentIcon")|Geçerli dal|  
|![CodeLens &#45; değiştirme üst dal simgesinden](../ide/media/codelensbranchparenticon.png "CodeLensBranchParentIcon")|Üst dal|  
|![CodeLens: Alt öğe dalı simgesini değiştirme](../ide/media/codelensbranchchildicon.png "CodeLensBranchChildIcon")|Bir alt öğe dalı|  
|![CodeLens &#45; eş dal simgesini değiştirme](../ide/media/codelensbranchpeericon.png "CodeLensBranchPeerIcon")|Bir eş dal|  
|![CodeLens &#45; dal daha koyma simgesini değiştirme](../ide/media/codelensbranchfurtherawayicon.png "CodeLensBranchFurtherAwayIcon")|Daha fazla dal parent, child veya eş daha kaldı|  
|![CodeLens: üst simge birleştirme](../ide/media/codelensbranchmergefromparenticon.png "CodeLensBranchMergeFromParentIcon")|Üst dalından bir alt öğe dalı birleştirme|  
|![CodeLens: alt öğe dalı simgesinden birleştirme](../ide/media/codelensbranchmergefromchildicon.png "CodeLensBranchMergeFromChildIcon")|Bir alt dalından ana dala birleştirme|  
|![CodeLens: ilişkisiz dal simgesinden birleştirme](../ide/media/codelensbranchmergefromunrelatedicon.png "CodeLensBranchMergeFromUnrelatedIcon")|İlişkisiz bir daldan (tabansız birleştirme) birleştirme|  
  
### <a name="find-linked-work-items"></a>Bağlantılı iş öğelerini bulma  
 ![CodeLens &#45; iş öğelerini bulmak için belirli kod](../ide/media/codelensworkitems.png "CodeLensWorkItems")  
  
### <a name="find-linked-code-reviews"></a>Bağlantılı kod incelemeleri bulma  
 ![CodeLens &#45; kod incelemesi isteklerini görüntülemek](../ide/media/codelenscodereviews.png "CodeLensCodeReviews")  
  
### <a name="find-linked-bugs"></a>Bağlantılı hataları bulun  
 ![CodeLens &#45; değişiklik kümelerini Bul hataları bağlı](../ide/media/codelensbugschangesets.png "CodeLensBugsChangesets")  
  
### <a name="contact-the-owner-of-an-item"></a>Bir öğenin sahibiyle iletişime geçin  
 ![Bir öğenin sahibiyle iletişime geçin](../ide/media/codelenscontactitemowner.png "CodeLensContactItemOwner")  
  
 İlgili kişi seçeneklerini görmek için bir öğe için kısayol menüsünü açın. Lync veya Skype Kurumsal'a yüklü olan bu seçenekleri görürsünüz:  
  
 ![Bir öğe için seçenekleri başvurun](../ide/media/codelensitemcontactmenu.png "CodeLensItemContactMenu")  
  
##  <a name="FindRunUnitTests"></a> Kodunuz için birim testleri bulma  
 Mevcut kodunuz için birim testleri hakkında daha fazla Test Gezgini açmaya gerek kalmadan bulun. Şunları yapmanız gerekir:  
  
-   Visual Studio Enterprise veya Visual Studio Professional  
  
-   Visual C# .NET veya Visual Basic .NET kodunu  
  
-   A [birim testi projesi](../test/unit-test-your-code.md) olan uygulama kodunuz için birim testleri  
  
1.  Birim testlerini içeren uygulama koduna gidin.  
  
2.  Bu kod için testleri gözden geçirin (**Alt + 3**).  
  
     ![CodeLens &#45; Kod Düzenleyicisi'nde test durumu seçin](../ide/media/codelenschoosetestindicator.png "CodeLensChooseTestIndicator")  
  
3.  Bir uyarı simgesi görürseniz ![CodeLens &#45; birim testleri, uyarı henüz çalıştırılmadı](../ide/media/codelenstestwarningicon.png "CodeLensTestWarningIcon"), testleri çalıştırın.  
  
     ![CodeLens &#45; görünümü birim testleri çalıştırma henüz](../ide/media/codelenstestsnotyetrun.png "CodeLensTestsNotYetRun")  
  
4.  Bir testin tanımını gözden geçirmek için düzenleyicide kod dosyasını açmak için CodeLens göstergesi penceresinde test öğesini çift tıklayın.  
  
     ![CodeLens &#45; birim test Tanıma Git](../ide/media/codelensunittestdefinition.png "CodeLensUnitTestDefinition")  
  
5.  Test sonuçlarını gözden geçirin Test durumu göstergesini seçin (![CodeLens &#45; birim testi başarısız oldu, simge](../ide/media/codelenstestfailedicon.png "CodeLensTestFailedIcon") veya ![CodeLens &#45; birim testi geçirilen simgesi](../ide/media/codelenstestpassedicon.png "CodeLensTestPassedIcon")), veya basın **Alt + 1**.  
  
     ![CodeLens &#45; bkz birim testi sonucu](../ide/media/codelensunittestresult.png "CodeLensUnitTestResult")  
  
6.  Bu testi kaç kişinin değiştirdiğini, bu testi kimin değiştirdiğini veya kaç değişiklik bu test ile yapılan görmek için [kodunuzun geçmişini ve ilişkili öğeleri bulun](#FindCodeHistory).  
  
##  <a name="QA"></a> SORU- CEVAP  
  
###  <a name="ChangeOrTurnOff"></a> CodeLens soru veya devre dışı bırakılsın mı? Veya görmek için hangi göstergelerini seçin?  
 **Y:** göstergeleri kapalı veya açık başvuru göstergesini dışında etkinleştirebilirsiniz. Git **Araçları**, **seçenekleri**, **metin düzenleyici**, **tüm diller**, **CodeLens**.  
  
 Göstergeler açık olduğunda, CodeLens seçeneklerini göstergelerden açabilirsiniz.  
  
 ![CodeLens &#45; etkinleştirmek veya devre dışı göstergeleri](../ide/media/codelensturnoffonindicatorsfromcode.png "CodeLensTurnOffOnIndicatorsFromCode")  
  
 CodeLens dosya düzeyi göstergelerini açma ve kapatma köşeli çift ayraç simgelerini Düzenleyicisi penceresinin alt kısmında kullanarak etkinleştirin.  
  
 ![Dosya Aç&#45;açıp düzey göstergeler](../ide/media/codelensfilelevelonandoff.png "CodeLensFileLevelOnAndOff")  
  
###  <a name="NoIndicators"></a> S: CodeLens nerede?  
 **Y:** yöntemi, sınıfı, dizin oluşturucu ve özellik düzeyinde Visual C# .NET ve Visual Basic .NET kodu CodeLens görünür. CodeLens dosya düzeyi tüm dosya türleri için görünür.  
  
-   CodeLens açık olduğundan emin olun. Git **Araçları**, **seçenekleri**, **metin düzenleyici**, **tüm diller**, **CodeLens**.  
  
-   Kodunuzu TFS içinde depolanır, kod dizini oluşturma kullanarak açık olduğundan emin olun [Codeındex komutu](../ide/codeindex-command.md) ile [TFS Yapılandırma komut](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62).  
  
-   TFS ilişkili göstergeler yalnızca iş öğeleri koda bağlandığında ve bağlantılı iş öğelerini açmak için izniniz olduğunda görünür. [Takım üyesi izinlerine sahip olduğunuzdan emin olun.](http://msdn.microsoft.com/en-us/f58805de-ba61-4d09-8f2d-d3ab9662ecfd)  
  
-   Birim test göstergeleri, uygulama kodu birim testlere sahip olmadığında görünmez. Test durumu göstergeleri test projesinde otomatik olarak görüntülenir. Uygulama kodunuzun birim testleri var, ancak test göstergeleri görünmüyorsa biliyorsanız, çözümü derlemeyi deneyin (**Ctrl + Shift + B**).  
  
### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>S: işleme iş öğesi ayrıntılarını neden göremiyorum?  
 **Y:** CodeLens TFS'de iş öğeleri bulamadığından gerçekleşebilir. Bu olan takım projesine bağlı değilseniz denetleyin iş öğeleri ve görme iznine sahip olan iş öğeleri. Yürütme açıklaması TFS'de iş öğesi kimlikleri hakkında yanlış bilgi varsa bu da gerçekleşebilir.  
  
###  <a name="NoLync"></a> S: neden Lync veya Skype göstergeleri göremiyorum?  
 **Y:** bunlar görünmez Lync veya Skype Kurumsal'a oturum açmadıysanız, bunlar yüklü birine sahip değilseniz veya desteklenen bir yapılandırma yok. Ancak yine de posta gönderebilirsiniz:  
  
 ![CodeLens &#45; kişi değişiklik kümesi sahibi tarafından posta](../ide/media/codelenscodesendmailchangesetnolync1.png "CodeLensCodeSendMailChangesetNoLync1")  
  
 **Hangi Lync ve Skype yapılandırmaları desteklenir?**  
  
- Skype Kurumsal'a (32 bit veya 64-bit)  
  
- Lync 2010 veya daha sonra tek başına (32 bit veya 64-bit), ancak değil, Lync Basic 2013 ile Windows 8.1  
  
  CodeLens, farklı Lync sürümlerine sahip desteklemiyor veya Skype yüklü. Bunlar, Visual Studio'nun tüm yerelleştirilmiş sürümleri için yerelleştirilmiş olmayabilir.  
  
### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>S: nasıl yazı tipi ve renk için CodeLens değiştirebilirim?  
 **Y:** Git **Araçları**, **seçenekleri**, **ortam**, **yazı tipleri ve renkler**.  
  
 ![CodeLens &#45; yazı tipi ve renk ayarlarını değiştir](../ide/media/codelensoptionsfontscolorssettings.png "CodeLensOptionsFontsColorsSettings")  
  
 Klavyeyi kullanmak için:  
  
1.  Tuşuna **Alt + T + O** açmak için **seçenekleri** kutusu.  
  
2.  Basın **yukarı ok** veya **aşağı ok** gitmek için **ortam** düğümünü tuşuna **sol ok** düğümü genişletmek için.  
  
3.  Tuşuna **aşağı ok** gitmek için **yazı tipleri ve renkler**.  
  
4.  Basın **sekmesini** gitmek için **ayarlarını göster** listelemek ve tuşuna **aşağı ok** seçmek için **CodeLens**.  
  
### <a name="q-can-i-move-the-codelens-heads-up-display"></a>S: CodeLens ekran göstergesi görüntüsünü taşıyabilir miyim?  
 **Y:** Evet, seçin ![CodeLens &#45; bir pencere olarak yerleştirmek](../ide/media/codelensdockwindow.png "CodeLensDockWindow") Codelens'i pencere olarak yerleştirmek için.  
  
 ![CodeLens göstergesi pencere sabitlemek](../ide/media/codelensselectdockwindow.png "CodeLensSelectDockWindow")  
  
 ![Yerleşik CodeLens başvuruları pencere](../ide/media/codelensreferencesdockedwindow.png "CodeLensReferencesDockedWindow")  
  
### <a name="q-how-do-i-refresh-the-indicators"></a>S: Göstergeleri nasıl yenileyebilirim?  
 **Y:** Bu gösterge üzerinde bağlıdır:  
  
-   **Başvuruları**: kod değiştiğinde bu gösterge otomatik olarak güncelleştirir. Bu gösterge ayrı bir pencerede yerleştirilmiş varsa, göstergenin el ile burada Yenile:  
  
     ![CodeLens &#45; penceresi olarak Yerleştir](../ide/media/codelensviewreferencesdocked.png "CodeLensViewReferencesDocked")  
  
-   **Takım**: Burada bu göstergeleri el ile yenileyin:  
  
     ![CodeLens &#45; göstergeleri yenileme](../ide/media/codelensrefreshindicatorsfromcode.png "CodeLensRefreshIndicatorsFromCode")  
  
-   **Test**: [kodunuz için birim testleri bulmak](#FindRunUnitTests) Bu belirteci yenilenemedi.  
  
###  <a name="LocalVersion"></a> S: "Yerel sürüm" nedir?  
 **Y:** **yerel sürüm** ok yerel sürümünüzde bu dosyanın en son değişiklik kümesini işaret eder. Üstüne veya altına sunucunun daha yeni değişiklik kümeleri olduğunda, göründükleri **yerel sürüm** ok, değişiklik kümelerini sıralarken kullanılan düzene bağlı olarak.  
  
### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>CodeLens kod geçmişini ve ilişkili öğeleri göstermek için nasıl işlediği yönetebilir miyim?  
 **Y:** Evet, kodunuzu TFS içinde ise, kullan [Codeındex komutu](../ide/codeindex-command.md) ile [TFS Yapılandırma komut](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62).




