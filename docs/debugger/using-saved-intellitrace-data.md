---
title: Kayıtlı IntelliTrace verilerini kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.norepro
helpviewer_keywords:
- iTrace files
- IntelliTrace, log files
- IntelliTrace log files
- .iTrace files
ms.assetid: 9f2cce86-345a-4e22-84ba-91542d81e67a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad584ac350038ced460b42a4e63d2b140d8396d6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912974"
---
# <a name="using-saved-intellitrace-data"></a>Kayıtlı IntelliTrace verilerini kullanma
Bir IntelliTrace günlük (.iTrace) dosyasından hata ayıklamaya başladığınızda uygulamanızda yürütmesinde belirli noktaları gidin. Bu dosya, performans olayları, özel durumlar, iş parçacıkları, test adımları, modüller ve Intellitrace'in kaydettiği uygulamanız çalışırken, diğer sistem bilgileri içerebilir.

 Bilgisayarınızda yüklü olduğundan emin olun:

-   Eşleşen kaynak dosyaları ve sembol (.pdb) dosyalarını kullanarak uygulama kodunuz için. Aksi takdirde, Visual Studio kaynak konumları çözümleyemez ve "simgeler bulunamadı." iletisini gösterir Bkz: [belirtin sembol (.pdb) ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) ve [dağıtımdan sonra sorunları tanılama](../debugger/diagnose-problems-after-deployment.md).

-   Visual Studio .iTrace dosyalarını açmak için Kurumsal (ancak değil Professional veya Community sürümlerini) geliştirme bilgisayarınızda veya başka bir bilgisayar

-   Bu kaynaklardan birinden bir .iTrace dosyası:

    |**Kaynak**|**Bkz:**|
    |----------------|-------------|
    |Visual Studio Enterprise (ancak değil Professional veya Community sürümlerini) bir IntelliTrace oturumu|[IntelliTrace Özellikleri](../debugger/intellitrace-features.md)|
    |Microsoft Test Yöneticisi'nde bir sınama oturumu. Bu bir .iTrace dosyası bir Team Foundation Server iş nesnesine ekler.|[El ile testlerde daha fazla tanılama verisi toplama](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)|
    |Microsoft Monitoring Agent, ya da tek başına veya System Center 2012 R2 Operations Manager ile ASP.NET web uygulamaları ve SharePoint uygulamaları geliştirme sırasında çalışan|-   [Dağıtımdan sonra sorunları tanılama](../debugger/diagnose-problems-after-deployment.md)<br />-   [System Center 2012 R2 Operations Manager için yenilikler nelerdir?](http://technet.microsoft.com/library/dn249700.aspx)|

##  <a name="GetStarted"></a> Ne yapmak istiyorsunuz?

-   [IntelliTrace günlüğünü açın](#Open)

-   [IntelliTrace günlüğünün anlama](#Understand)

-   [Bir IntelliTrace günlüğünden hata ayıklamayı Başlat](#StartDebugging)

##  <a name="Open"></a> IntelliTrace günlüğünü açın
 Visual Studio Enterprise ile bir bilgisayara, .iTrace dosyasını açın.

-   Visual Studio dışında .iTrace dosyasına çift tıklayın veya dosya açma Visual Studio içinde.

     \- veya -

-   .İTrace dosyasını bir Team Foundation Server iş öğesine iliştirildiyse sonucu iş öğesi bu adımları izleyin:

    -   Altında **tüm bağlantıları**, .iTrace dosyasını bulun. Dosyayı açın.

         \- veya -

    -   Altında **yineleme adımları**, seçin **IntelliTrace** bağlantı.

> [!TIP]
>  Hata ayıklama sırasında IntelliTrace dosyasını kapattıysanız, kolayca yeniden açabilirsiniz. Git **hata ayıklama** menüsünde seçin **IntelliTrace**, **günlük özetini göster**. Ayrıca seçebilirsiniz **günlük özetini göster** içinde **IntelliTrace** penceresi. Yalnızca IntelliTrace ile hata ayıklama sırasında bu kullanılabilir.

##  <a name="Understand"></a> IntelliTrace günlüğünün anlama
 Yalnızca, belirli bir kaynaktan Örneğin, Test Yöneticisi'nden veya SharePoint uygulamalardan toplanan veriler, bazı .iTrace dosyasın içinde aşağıdaki bölümlerde görünür.

|**Bölüm**|**içerir**|**Koleksiyon kaynağı**|
|-----------------|------------------|---------------------------|
|[Performans ihlalleri](#Performance)|Yapılandırılan Eşiği aşan işlev çağrıları sahip performans olayları|Microsoft Monitoring Agent, ya da tek başına Toplayıcı veya System Center 2012 R2 Operations Manager için IIS'de barındırılan ASP.NET web uygulamaları|
|[Özel durum verileri](#ExceptionData)|Her özel durum için tam çağrı yığını da dahil olmak üzere özel durumlar|Tüm kaynakları|
|[Çözümleme](#Analysis)|Yalnızca SharePoint 2010 ve SharePoint 2013 uygulamaları için. Hata ayıklayıcı olayları, ULS olayları, İşlenmeyen özel durumları ve Microsoft Monitoring Agent kaydettiği diğer veriler gibi IntelliTrace ve SharePoint olaylarını tanılayın.|Microsoft Monitoring Agent, ya da tek başına Toplayıcı veya System Center 2012 R2 Operations Manager ile|
|[Sistem bilgisi](#SystemInfo)|Ayarları ve özellikleri ana sistemin|Tüm kaynakları|
|[İş parçacıkları listesi](#ThreadsList)|Koleksiyon süresince çalışan iş parçacıkları|Tüm kaynakları|
|[Test verileri](#TestData)|Test adımları ve bir test oturumundaki sonuçları|Test Yöneticisi|
|[Modüller](#Modules)|Yüklendikleri sırada hedef işlemin yüklediği modülleri.|Tüm kaynakları|
|[Web isteği](#Modules)|Üretim IIS için istek verileri Web uygulamaları ve SharePoint 2010 ve SharePoint 2013 web|Microsoft Monitoring Agent ve tek başına Toplayıcı|

 Aşağıda, her bölümde bilgileri bulmanıza yardımcı olabilecek bazı ipuçları verilmiştir:

-   Verileri sıralamak için sütun başlığını seçin.

-   Filtre verileri için arama kutusunu kullanın. Düz metin arama zaman sütunu dışındaki tüm sütunlarda çalışır. Sütun başına bir filtre ile ayrıca aramaları belirli bir sütuna filtreleyebilirsiniz. Sütun adı boşluk içermeyen, iki nokta (**:**) ve arama değeri. Noktalı virgül ile izleyin (**;**) başka bir sütun ve arama değeri eklemek için.

     Örneğin, bulunacak Word'ün performans olayları "içinde yavaş" **açıklama** sütun, türü:

     `Description:slow`

##  <a name="StartDebugging"></a> Bir IntelliTrace günlüğünden hata ayıklamayı Başlat

###  <a name="Performance"></a> Performans ihlalleri
 Uygulamanız için kaydedilen performans olaylarını gözden geçirin. Sık sık gerçekleşen olmayan olaylar gizleyebilirsiniz.

##### <a name="to-start-debugging-from-a-performance-event"></a>Bir performans olayından hata ayıklamasını başlatmak için

1.  Altında **performans ihlallerinin**, kaydedilen performans olaylarını, bunların toplam yürütme sürelerini ve diğer olay bilgilerini gözden geçirin. Sonra belirli performans olayı sırasında çağrılan yöntemlerde fazla araştırma yapın.

     ![Performans Olay Ayrıntıları Görüntüle](../debugger/media/ffr_itsummarypageperformance.png "FFR_ITSummaryPagePerformance")

     Ayrıca, olayı çift tıklatabilirsiniz.

2.  Olay sayfasında, bu çağrılar için yürütme zamanını gözden geçirin. Yürütme ağacında yavaş bir çağrı bulun.

     İç içe ya da başka şekilde birden fazla çağrınız varsa, en yavaş çağrılar kendi bölümünde görüntülenir.

3.  Çağrı gözden geçirmek için çağrıları ve o noktasında kaydedilmiş bir parametre değerlerini içe genişletin.

     (Klavye: göster veya gizle iç içe geçmiş bir çağrı için basın **sağ ok** veya **sol ok** sırasıyla anahtar. Gösterme ve gizleme iç içe geçmiş bir çağrı için parametre değerleri için basın **alanı** anahtarı.)

     Çağrıdan hata ayıklamayı başlatın.

     ![Yöntem çağrısından hata ayıklamayı Başlat](../debugger/media/ffr_itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")

     Ayrıca aramayı çift tıklatabilirsiniz veya basın **Enter** anahtarı.

     Yöntem uygulama kodunuzda ise, Visual Studio bu yönteme gider.

     ![Performans olayından uygulama koduna gidin](../debugger/media/ffr_itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")

     Kaydedilmiş diğer değerleri çağrı yığını gözden geçirebilir kodunuzda adım adım veya kullanın **IntelliTrace** penceresine [geriye veya ileten diğer yöntemler arasında "zamanda" taşıma](../debugger/intellitrace.md) sırasında çağırılan Bu performans olayı.

###  <a name="ExceptionData"></a> Özel durum verileri
 Durum ve uygulamanız için kayıtlı özel durumları gözden geçirin. Aynı türe sahip ve yalnızca en son özel durum görebilmesi için çağrı yığını özel durumları gruplandırabilirsiniz.

##### <a name="to-start-debugging-from-an-exception"></a>Bir özel durumdan hata ayıklamasını başlatmak için

1.  Altında **özel durum verileri**, kaydedilen özel durum olaylarını, türleri, iletileri gözden geçirin ve özel durumların ne zaman oluştuğunu. Kodu daha ayrıntılı incelemek için özel durumlar grubu içindeki en son olaydan başlayın.

     ![Özel durum bir olaydan hata ayıklamaya başlamak](../debugger/media/ffr_itsummarypageexception.png "FFR_ITSummaryPageException")

     Ayrıca, olayı çift tıklatabilirsiniz. Olayları gruplandırılmış değil ise seçin **hata ayıklama bu olay**.

     Uygulama kodunuzda bir özel durum oluştuysa, Visual Studio özel durumun olduğu yere gider.

     ![Gelen bir özel durum olayı uygulama koduna gidin](../debugger/media/ffr_itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")

     Kaydedilmiş diğer değerleri çağrı yığını gözden geçirin veya kullanmak artık **IntelliTrace** penceresine [geriye veya ileten diğer kaydedilen olaylar arasında "zamanda" taşıma](../debugger/intellitrace.md), ilgili kod ve sırasında kaydedilmiş değerler Bu zaman noktaları.

    |**Sütun**|**Gösterir**|
    |----------------|-------------------|
    |**Türü**|Özel durumun .NET türü|
    |**En yeni ileti** gruplandırılmış özel durumlar veya **ileti** gruplanmamış özel durumları|Özel durum tarafından sağlanan ileti|
    |**Sayısı** gruplandırılmış özel durumlar|Özel durumun oluştuğu sayısı|
    |**İş parçacığı kimliği** gruplanmamış özel durumları|Özel durum oluşturan iş parçacığının kimliği|
    |**En yeni olay saati** veya **olay saati**|Zaman damgası, özel durum oluştuğunda kaydedilen|
    |**Çağrı yığını**|Bir özel durum için çağrı yığını.<br /><br /> Çağrı yığınını görmek için listeden bir özel durum seçin. Çağrı yığını, özel durum listesinin altında görüntülenir.|

###  <a name="Analysis"></a> Çözümleme
 Bir SharePoint bağıntı kimliği'ni kullanarak SharePoint 2010 ve SharePoint 2013 uygulamaları ile sorunları tanılamak veya Microsoft Monitoring Agent bulduğu işlenmemiş özel durumlar gözden geçirin.

-   Bir SharePoint bağıntı kimliği, eşleşen web isteğini ve olaylarını bulmak için kullanın. Bir olay seçin ve ardından noktada hata ayıklamayı Başlat olayın gerçekleştiği yerde ve.

-   Microsoft Monitoring Agent, işlenmemiş özel durumlar, bir özel durum seçin ve ardından noktada hata ayıklamayı Başlat nerede ve ne zaman özel durum oluştu.

##### <a name="start-debugging-with-a-sharepoint-correlation-id"></a>SharePoint bağıntı kimliği ile hata ayıklamayı başlat

1. SharePoint bağıntı Kimliğini kaynağından kopyalayın.

    Örneğin:

    ![IntelliTrace &#45; SharePoint hatası &#45; bağıntı kimliği](../debugger/media/sharepointerror_intellitrace.png "SharePointError_IntelliTrace")

2. .İTrace dosyasını açın ve ardından Git **analiz** eşleşen web isteğini gözden geçirmek için SharePoint bağıntı Kimliğini girin ve kaydedilen olayları.

    ![IntelliTrace günlüğünü &#45; girin SharePoint bağıntı kimliği](../debugger/media/entersharepointcorrelationid.png "EnterSharePointCorrelationID")

3. Altında **istek olayları**, olayları inceleyin. Üstten başlayarak, olaylar gerçekleştiği sırada görüntülenir.

   1. Ayrıntılarını görmek için bir olay seçin.

   2. Seçin **hata ayıklamayı Başlat** olayın gerçekleştiği noktada hata ayıklama başlatılamıyor.

      ![IntelliTrace günlük dosyası &#45; web isteğini görüntüle &#43; olayları](../debugger/media/entersharepointcorrelationid2.png "EnterSharePointCorrelationID2")

   Bu tür SharePoint olaylarını IntelliTrace olayları ile birlikte görebilirsiniz:

-   **Kullanıcı profili olayları**

     Bu olaylar SharePoint bir kullanıcı profili yüklediğinde ve kullanıcı profili özellikleri okunduğunda ya da olduğunda gerçekleşir.

-   **Birleşik günlük kaydetme sistemi (ULS) olayları**

     Microsoft Monitoring Agent, SharePoint ULS olayları ve bu alanların bir alt kümesini kaydeder:

    |**IntelliTrace alanı**|**SharePoint ULS alanı**|
    |----------------------------|------------------------------|
    |**Kimliği**|**EventID**|
    |**düzeyi**|**düzeyi**|
    |**Kategori Kimliği**|**Kategori Kimliği**|
    |**Kategori**|**Kategori**|
    |**Alan**|**Ürün**|
    |**Output**|**İleti**|
    |**Bağıntı Kimliği**|**Bağıntı Kimliği**|

##### <a name="start-debugging-from-an-unhandled-exception"></a>İşlenmemiş bir özel durumdan hata ayıklamayı başlat

1. Bir özel durum için bir SharePoint bağıntı kimliği'ni seçin. Özel durum türüne göre gruplandırılır ve çağrı yığını.

2. (İsteğe bağlı) Genişletin **çağrı yığını** özel durumlar grubu için çağrı yığınını görmek için.

3. Seçin **özel durum hata ayıkla** noktada hata ayıklamayı başlatmak için nerede ve ne zaman bir özel durum oluştu.

    ![IntelliTrace günlüğünü &#45; SharePoint işlenmeyen özel durumları](../debugger/media/sharepointunhandledexceptions_intellitrace.png "SharePointUnhandledExceptions_IntelliTrace")

   Bir kılavuz için bkz. [izlenecek yol: bir SharePoint uygulaması tarafından IntelliTrace kullanarak hata ayıklama](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md). Aracı kayıtları görüntüle veri türleri için [IntelliTrace özellikleri](../debugger/intellitrace-features.md).

###  <a name="ThreadsList"></a> İş parçacıkları listesi
 Hedef işlemde çalışan kayıtlı iş parçacıklarını inceleyin. Seçili bir iş parçacığı içindeki ilk geçerli IntelliTrace olayından hata ayıklamasını başlayabilirsiniz.

##### <a name="to-start-debugging-from-a-specific-thread"></a>Belirli bir iş parçacığından hata ayıklamasını başlatmak için

1. Altında **iş parçacıkları listesi**, bir iş parçacığı seçin.

2. Sayfanın alt kısmında **iş parçacıkları listesi**, seçin **hata ayıklamayı Başlat**. Ayrıca, bir iş parçacığını çift tıklatabilirsiniz.

    Uygulamanın başladığı hata ayıklamayı başlatmak için çift tıklayın **ana iş parçacığı**. Bkz: [IntelliTrace özellikleri](../debugger/intellitrace-features.md).

   Kullanıcının oluşturduğu iş parçacığı verisi bir sunucunun oluşturur ve yönetir IIS'te barınan Web uygulamaları için iş parçacığı daha kullanışlı olabilir.

|**Sütun**|**Gösterir**|
|----------------|-------------------|
|**ID**|İş parçacığı kimliği numarası|
|**Ad**|İş parçacığı adı. Adlandırılmamış iş parçacıkları olarak görünür "\<adsız >".|
|**Başlangıç saati**|İş parçacığının oluşturulduğu saat|
|**Bitiş zamanı**|İş parçacığının tamamlandığı saat|

###  <a name="TestData"></a> Test verileri
 Test Yöneticisi'ni uygulamanızı test ederken kaydedilen IntelliTrace verilerini inceleyin.

##### <a name="to-start-debugging-from-a-specific-test-step"></a>Belirli bir sınama adımından hata ayıklamasını başlatmak için

1.  Genişletin **Test adımları kılavuz**. Bir test adımını seçin.

2.  Sayfanın alt kısmında **sınama adımları kılavuzunun**, seçin **hata ayıklamayı Başlat**. Ayrıca, bir test adımını çift tıklatabilirsiniz.

     Bu seçili sınama adımından sonraki ilk geçerli IntelliTrace olayından hata ayıklamayı başlatır.

     Sınama verisi varsa, IntelliTrace sınamanın çalışması için kullanılan ilişkili Team Foundation Server yapısını çözmeye çalışır. Yapı bulunduysa, uygulama ile ilişkili simgeler otomatik olarak çözümlenir.

|**Alan**|**Gösterir**|
|---------------|-------------------|
|**Test oturumu**|Kaydedilen sınama oturumları. Genellikle, var. yalnızca bir Test verilerini bir el ile araştırmacı sınama kullanılarak oluşturulmuşsa, bu liste boştur.|
|**Test çalışması**|Test çalışmaları seçili sınama oturumundan. Test verilerini bir el ile araştırmacı sınama kullanılarak oluşturulmuşsa, bu liste boştur.|
|**Sınama adımları Kılavuzu**|Test geçişi test sonucu ile kaydedilen sınama adımları veya başarısız|

###  <a name="SystemInfo"></a> Sistem bilgisi
 Bu bölümde, örnek uygulamayı barındırılan sistem, donanım, işletim sistemi, çevresel ve işlem özgü bilgileri hakkındaki ayrıntıları gösterir.

###  <a name="Modules"></a> Modüller
 Bu bölüm size hedef işlemin yüklediği modülleri gösterir. Modüller yüklendikleri sırada görünür.

|**Sütun**|**Gösterir**|
|----------------|-------------------|
|**Modül adı**|Modül dosya adı|
|**Modül yolu**|Burada modülün yüklendiğine disk konumu|
|**Modül kimliği**|Sürüme özgü olan ve eşleştirme simgesi (PDB) dosyalarına katkıda bulunan modülün benzersiz tanımlayıcısı. Bkz: [sembol (.pdb) dosyalarını ve kaynak dosyaları bulma](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).|

### <a name="where-can-i-get-more-information"></a>Daha fazla bilgiyi nereden bulabilirim?
 [IntelliTrace tek başına toplayıcısını kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md)

 [IntelliTrace Özellikleri](../debugger/intellitrace-features.md)

 [El ile testlerde daha fazla tanılama verisi toplama](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)

 [IntelliTrace](../debugger/intellitrace.md)

#### <a name="forums"></a>Forumlar
 [Visual Studio Debugger](http://go.microsoft.com/fwlink/?LinkId=262263)

#### <a name="guidance"></a>Kılavuz
 [Bölüm 6 - Visual Studio 2012 ile sürekli teslimat testi: sınama araç kutusu](http://go.microsoft.com/fwlink/?LinkID=255203)