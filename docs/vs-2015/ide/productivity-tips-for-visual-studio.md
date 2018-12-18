---
title: Üretkenlik ipuçları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ccc5e543-7dcf-465c-97dd-e133e869800c
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: db89bda465d1a4fc4da1b3066858b270ce50c5bb
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051036"
---
# <a name="productivity-tips-for-visual-studio"></a>Visual Studio için Üretkenlik İpuçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu ipuçlarını izleyerek, daha hızlı ve verimli bir şekilde yazma gidin ve kodunuzu Visual Studio'da hata ayıklama. Ortak klavye kısayolları hakkında daha fazla bilgi için bkz. [ipuçları ve püf noktaları](../ide/tips-and-tricks-for-visual-studio.md). Daha kapsamlı bir liste için bkz. [tanımlama ve özelleştirme klavye kısayolları](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) ve [varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md).

 Bu konu aşağıdaki bölümleri içermektedir:

 [Visual Studio araçlarına erişim](../ide/productivity-tips-for-visual-studio.md#BKMK_Access)

 [Kod Yazma](../ide/productivity-tips-for-visual-studio.md#BKMK_Writing)

 [Kodunuzun içinde gezinme](../ide/productivity-tips-for-visual-studio.md#BKMK_Navigating)

 [Öğeleri daha hızlı bulma](../ide/productivity-tips-for-visual-studio.md#BKMK_Finding)

 [Kodda hata ayıklama](../ide/productivity-tips-for-visual-studio.md#BKMK_Debugging)

 [Dosyaları araç çubuklarını ve Windows yönetme](../ide/productivity-tips-for-visual-studio.md#BKMK_Managing)

##  <a name="BKMK_Access"></a> Visual Studio araçlarına erişim
 Başlangıç ekranına veya göreve sabitlerseniz için sabitlerseniz Geliştirici komut istemi veya başka bir araca daha kolay erişebilirsiniz.

1.  Başlangıç ekranından girin `Visual Studio Tools`ve ardından Enter tuşuna basın.

2.  İçinde **dosya Gezgini**, istediğiniz öğe için kısayol menüsünü açın:

    -   Derleme bildirimleri

    -   Hata ayıklanabilir Paket Yöneticisi

    -   VS2013 için geliştirici komut istemi

    -   Microsoft geri bildirim istemcisi 2013

    -   VS2013 ARM çapraz Araçlar komut istemi

    -   VS2013 x64 çapraz Araçları komut istemi

    -   VS2013 x64 yerel Araçları komut istemi

    -   VS2013 x86 yerel Araçları komut istemi

3.  Seçin **Başlangıç ekranına Sabitle** veya **görev çubuğuna Sabitle**.

##  <a name="BKMK_Writing"></a> Kod yazma
 Aşağıdaki özellikleri kullanarak kod daha hızlı bir şekilde yazın.

-   **Örnek uygulamaları kullanın**. Karşıdan yükleme ve MSDN Kod Galerisinden örnek uygulamalar tarafından uygulama geliştirme sürecini hızlandırabilir. İndirerek ve örnek paketi o alan için keşfetmek, belirli bir teknoloji veya programlama konsepti öğrenebilirsiniz.

-   **IntelliSense kullanın**. Düzenleyiciye kod girerken, gibi üyeleri listeleme, parametre bilgisi, hızlı bilgi, imza Yardım ve tam sözcük IntelliSense bilgisi görüntülenir. Bu özellikler, metnin benzer öğe eşleştirmesi destekler; Örneğin, listesi üyeleri için sonuçları listelerini sadece girdiğiniz karakterlerle başlayan girdileri olmakla kalmayıp herhangi bir yerde karakter bileşimini içeren girdileri içerir. Daha fazla bilgi için [IntelliSense kullanarak](../ide/using-intellisense.md).

-   **Kod girerken IntelliSense seçeneklerini otomatik ekleme değiştirme**. IntelliSense Öneri moduna çevirirseniz, IntelliSense seçeneklerini sadece açıkça bunları seçerseniz eklenmiş olduğunu belirtebilirsiniz.

     Öneri modunu etkinleştirmek için Ctrl + Alt + Ara çubuğu seçin anahtarları veya menü çubuğunda, **Düzenle**, **IntelliSense**, **tamamlama modunu Değiştir**.

-   **Kod parçacıkları kullanma**. Yerleşik parçacıkları kullanabilir veya kendi parçacıklarınızı oluşturabilirsiniz.

     Menü çubuğunda bir parçacık eklemek için seçin **Düzenle**, **IntelliSense**, **parçacık Ekle** veya bir dosyada kısayol menüsünü açın ve seçin **kod parçacığı Ekle** . Daha fazla bilgi için [kod parçacıkları](../ide/code-snippets.md).

-   **Kod hatalarını satır içi düzeltme**. Akıllı etiketler bir kod satırı altında mavi veya kırmızı kutu olarak görünür. Bir kutular veya kod satırında imleci yerleştirerek ve Ctrl seçerek işaret ederek akıllı etiket seçeneklerini görüntüleyebilirsiniz +. (devir) tuşları.

     Mavi kutular kodunuzda hataları düzeltmek için yollar önerir.

     Şekil 1: Hata akıllı etiketleri

     ![Hata akıllı etiket önerileri](../ide/media/productivity-bluesmarttags.png "Productivity_BlueSmartTags")

     Kırmızı kutuları, kodunuzu yeniden değiştirmenin yollarını önerir.

     Şekil 2: Akıllı etiketleri yeniden düzenleme

     ![Akıllı etiket önerileri yeniden düzenleme](../ide/media/productivity-redsmarttags.png "Productivity_RedSmartTags")

-   **Gösterme ve bir kod öğesinin tanımını Düzenle**. Hızlı bir şekilde gösterebilir ve bir üyesi, bir değişken veya yerel olarak gibi bir kod öğe tanımlandığı modülü Düzenle.

     Açılır pencerede bir tanımı açmak için öğeyi vurgulayıp Alt + F12 tuşlarını seçin veya öğe için kısayol menüsünü açın ve ardından **Özet tanım**. Ayrı bir kod penceresinde bir tanımı açmak için öğe için kısayol menüsünü açın ve ardından **Tanıma Git**.

##  <a name="BKMK_Navigating"></a> Kodunuzun içinde gezinme
 Kodunuzda belirli konumları daha hızlı hareket ettirin ve bulmak için çeşitli teknikler kullanabilirsiniz.

-   **Kod satırlarını yer işareti**. Belirli bir dosyaya kod satırlarını hızla gitmek için yer işaretlerini kullanabilirsiniz.

     Menü çubuğunda bir yer işareti koymak için **Düzenle**, **yer işaretleri**, **yer işaretini Değiştir**. Tüm yer işaretlerini bir çözüm için görüntüleyebileceğiniz **yer işaretleri** penceresi. Daha fazla bilgi için [koddaki ayarı yer işaretlerini](../ide/setting-bookmarks-in-code.md).

-   **Bir dosyada sembol tanımlarını arama**. Bir çözüm içinde Sembol tanımlarını ve dosya adlarını konumlandırmak için arama yapabilirsiniz ancak arama sonuçları ad veya yerel değişkenleri içermez.

     Menü çubuğunda, bu özelliğe erişmek için seçin **Düzenle**, **gitmek için**.

-   **Kodunuzun genel yapısına gözatın**. İçinde **Çözüm Gezgini**, arama ve sınıfları ve türleri ve üyeleri, projelerinizde göz atın. Ayrıca arama, bir yöntemin çağrı hiyerarşisini görüntülemek simge başvurularını bulmak ve diğer görevleri gerçekleştirebilirsiniz. İçinde bir kod elemanını seçerseniz **Çözüm Gezgini**, ilişkili dosya açılır bir **Önizleme** sekmesi ve dosyanın içindeki öğeye işaretçi taşır. Daha fazla bilgi için [Structure of Code görüntüleme](../ide/viewing-the-structure-of-code.md).

##  <a name="BKMK_Finding"></a> Öğeleri daha hızlı bulma
 Komutlar, dosyalar ve Seçenekler, yalnızca geçerli görevinize ilgili bilgileri göstermek için araç pencerelerinin içeriğini filtre ek olarak IDE içinde arama yapabilirsiniz.

-   **Araç pencerelerinin içeriğini filtre**. Aşağıdakiler gibi birçok araç pencerelerinin içeriğini içinde arama yapabilirsiniz **araç kutusu**, **özellikleri** penceresinde ve **Çözüm Gezgini**, ancak görüntü yalnızca, adları öğeler Belirttiğiniz karakterler içeriyor.

-   **Yalnızca istediğiniz hataları görüntülemek adresine**. Seçerseniz **filtre** düğmesini **hata listesi** araç çubuğu içinde görünen hata sayısını azaltabilirsiniz **hata listesi** penceresi. Yalnızca hataları, düzenleyicide açık olan dosyalardaki yalnızca geçerli dosyadaki hataları veya yalnızca geçerli projedeki hataları görüntüleyebilirsiniz. Hata Listesi penceresi içinde belirli hataları bulmak için arama da yapabilirsiniz.

-   **İletişim kutularını, menü komutlarını ve seçenekleri bulun**. İçinde [hızlı başlatma, ortam, Seçenekler iletişim kutusu](../ide/reference/quick-launch-environment-options-dialog-box.md) kutusunda, bulmaya çalıştığınız öğeler için anahtar sözcükleri veya tümceleri girin. Girerseniz, örneğin, aşağıdaki seçenekler görünür `new project`:

     Şekil 3: Hızlı başlatma sonuçları listesi için `new project`

     !['Yeni project' hızlı başlatma sonuçları](../ide/media/productivity-quicklaunch.png "Productivity_QuickLaunch")

     **Hızlı başlatma** bağlantılarını gösterir **yeni proje** iletişim kutusu, **Yeni Öğe Ekle** iletişim kutusu ve projeler ve çözümler sayfanın **seçenekleri** iletişim kutusunda, diğerlerinin yanı sıra. Hızlı Başlatma sonuçları ayrıca proje dosyalarını ve araç pencerelerini de içerebilir.

##  <a name="BKMK_Debugging"></a> Kodda hata ayıklama
 Hata ayıklama çok zaman kullanabilir, ancak aşağıdaki ipuçları yardımcı olabilir sürecinize hız.

-   **Sayfa, uygulama veya siteyi farklı tarayıcılarda test etme**. Kodunuzdaki hataları ayıklamanıza gibi dahil olmak üzere yüklü web tarayıcıları arasında kolayca geçiş yapabilirsiniz [sayfa denetçisi (Visual Studio)](http://msdn.microsoft.com/library/65880969-1ad2-47be-85b9-bb12c81bf209), açmak zorunda kalmadan **şununla Gözat** iletişim kutusu. Kullanabileceğiniz **hata ayıklama hedefi** üzerinde olan liste **standart** yanındaki araç **hata ayıklamayı Başlat** düğme, hızlı bir şekilde hata ayıklama gibi kullanarak kullandığınız tarayıcıyı doğrulamak için veya sayfaları görüntüleyin.

     ![Web tarayıcı hata ayıklama seçeneklerini](../ide/media/webbrowserdropdowntoolbar.png "WebBrowserDropDownToolbar")

-   **Geçici kesme noktalarını ayarlayın**. Geçerli kod satırında geçici bir kesme noktası oluşturabilir ve aynı anda hata ayıklayıcıyı başlatın. Kodun o satırına isabet ettiğinde, hata ayıklayıcı kesme moduna girer. Daha fazla bilgi için [hata ayıklayıcısı ile kodlarda gezinme](../debugger/navigating-through-code-with-the-debugger.md).

     Bu özelliği kullanmak için Ctrl + F10 seçin anahtarları veya Kes ve ardından istediğiniz kod satırı için kısayol menüsünü açın **imlece**.

-   **Hata ayıklama sırasında yürütme noktasını taşımak**. Geçerli yürütme noktasını farklı bir bölüme taşımak ve hata ayıklamaya bu noktadan yeniden başlatın. Bu teknik, bu bölüme erişmek için gerekli tüm adımları yeniden oluşturmak zorunda kalmadan kodun bir bölümünü hata ayıklamak istiyorsanız kullanışlıdır. Daha fazla bilgi için [hata ayıklayıcısı ile kodlarda gezinme](../debugger/navigating-through-code-with-the-debugger.md).

     Yürütme noktasını taşımak, sarı ok başını, aynı dosya içinde sonraki deyimi ayarlamak istediğiniz bir konuma sürükleyin ve sonra hata ayıklamaya devam etmek için F5 tuşuna basın.

-   **Değişkenler için değer bilgilerini yakalama**. Kodunuzda bir değişkene bir DataTip eklemek ve hata ayıklama işlemini tamamladıktan sonra değişkenin son bilinen değerini erişebilmesi için sabitleyin. Daha fazla bilgi için [veri İpuçlarında veri değerlerini görüntüleme](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Bir DataTip eklemek için hata ayıklayıcının kesme modunda olması gerekir. Değişkenin üzerine imleci yerleştirin ve ardından görünen DataTip üzerinde görünen pin düğmesini seçin. Hata ayıklama durdurulduğunda, değişkeni içeren kod satırının yanındaki kaynak dosyada bir mavi iğne simgesi görüntülenir. Mavi işaret ederseniz, en son hata ayıklama oturumu değişkenin değeri görüntülenir.

-   **Anlık pencereyi temizleme**. İçeriklerini silebilirsiniz [komut penceresi](../ide/reference/immediate-window.md) girerek tasarım zamanında `>cls` veya `>Edit.ClearAll`

     Ek komutlar hakkında daha fazla bilgi için bkz. [Visual Studio komut diğer adları](../ide/reference/visual-studio-command-aliases.md).

##  <a name="BKMK_Managing"></a> Dosyaları araç çubuklarını ve Windows yönetme
 Herhangi bir anda, birden fazla kod dosyasında çalışma ve uygulama geliştirme gibi birçok araç pencereleri arasında taşınması. Aşağıdaki ipuçlarını kullanarak düzenli tutabilirsiniz.

-   **Sık kullandığınız dosyaları düzenleyicide görünür tutma**. İyi kaç dosya düzenleyicide açık olduğundan bağımsız olarak görünür kalır dosyaları sekmenin sol tarafına sabitleyebilirsiniz.

     Bir dosyayı sabitlemek için dosyanın sekmesini seçin ve ardından **Pin durumunu değiştir** düğmesi.

-   **Belgeleri ve dokümanları diğer monitörlere taşıma**. Uygulama geliştirirken birden fazla monitör kullanıyorsanız, başka bir monitöre düzenleyicide açık olan dosyaları taşıyarak uygulamanızın bölümleri üzerinde daha kolay çalışabilirsiniz. Başka bir izleme ve sekme için hata ayıklayıcı windows gibi araç pencereleri birlikte "rafts" oluşturmak için belge ve araç pencerelerini sabitlemek taşıyabilirsiniz Daha fazla bilgi için [nasıl yapılır: Düzenle ve Dock Windows](../misc/how-to-arrange-and-dock-windows.md).

     Ayrıca dosyaları daha kolay başka bir örneğini oluşturarak yönetebilirsiniz **Çözüm Gezgini** ve başka bir monitöre taşıyarak. Başka bir örneğini oluşturmak için **Çözüm Gezgini**, bir kısayol menüsünü açıp **Çözüm Gezgini**ve ardından **Yeni Çözüm Gezgini görünümü**.

-   **Visual Studio'da görünen yazı tiplerini özelleştirme**. Yazı tipi, boyutu ve IDE içindeki metin için kullanılan rengi değiştirebilirsiniz. Örneğin, düzenleyici ve araç pencerelerini veya IDE boyunca yazı tipini belirli kod öğelerinin rengini özelleştirebilirsiniz. Daha fazla bilgi için [nasıl yapılır: değişiklik yazı tipleri ve renkler](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) ve [nasıl yapılır: değişiklik yazı tipleri ve renkler Düzenleyicisi'nde](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Sık kullanılan komutlar için varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md) [nasıl yapılır: menüleri ve araç çubuklarını özelleştirme](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md) [izlenecek yol: basit bir uygulama oluşturma](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md) [erişilebilirlik ipuçları ve Püf noktaları](../ide/reference/accessibility-tips-and-tricks.md)
