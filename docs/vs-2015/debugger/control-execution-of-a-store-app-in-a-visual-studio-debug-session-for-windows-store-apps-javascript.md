---
title: Denetleme (JavaScript) Windows Store uygulamaları için hata ayıklama oturumunda bir Store uygulamasının yürütülmesine | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 60159535-61ec-466a-a4a6-115ec72a8af5
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca8e2a584ff68786d22bd90ddd8827a70c66a557
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052216"
---
# <a name="control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript"></a>Bir Store uygulamasının yürütülmesini denetleme (JavaScript) Windows Store uygulamaları için Visual Studio hata ayıklama oturumunda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu hızlı başlangıçta, Visual Studio hata ayıklayıcıda gitme ve bir oturumda program durumunu görüntülemek nasıl gösterir.

 Bu hızlı başlangıçta, Visual Studio ile hata ayıklama için yenidir ve hata ayıklama oturumu Visual Studio'da gezinme hakkında daha fazla bilgi için isteyen geliştiriciler için geliştiriciler içindir. Kendi hata ayıklama resim öğretmek değildir. Örnek kodda işlevleri, yalnızca bu konuda açıklanan hata ayıklama yordamları göstermek için tasarlanmıştır. Uygulama veya işlev tasarımının en iyi işlevleri dağıtıyorsunuz değil. Aslında, İşlevler ve uygulama içinden her şeyin daha fazlasını yapmanız değil, hızlı bir şekilde keşfeder.

 Bu hızlı başlangıçta bölümlerini, zaten alışık olduğunuz bilgiler içeren herhangi bir bölümü atlayabilirsiniz olabildiğince bağımsız olarak tasarlanmıştır. Örnek bir uygulama oluşturmak için gerekli değildir. Ancak biz bunu tavsiye ve işlem mümkün olduğu kadar kolay yaptığınız.

 **Hata ayıklayıcı, klavye kısayolları.** Visual Studio hata ayıklayıcı gezintisi, hem fare ve klavye için optimize edilmiştir. Bu konu başlığı altındaki adımların birçok klavye kısayol tuşu veya kısayol tuşu parantez içinde bir açıklama içerir. Örneğin, (klavye: F5) yazarak F5 başlatır veya hata ayıklayıcı yürütme devam eder, anahtar gösterir.

> [!NOTE]
>  **Modül deseni**
>
>  Sık kullandığınız JavaScript Windows Store apps *modülü deseni* verileri ve işlevleri sayfasında yalıtılacak. Modül düzeni tek, kendi kendine çalışan ve anonim bir kapanış sayfa işlevselliği genel ad alanından ayrı tutmak için kullanır. Bu konuda, bu işlev diyoruz *Modülü*.

## <a name="in-this-topic"></a>Bu konuda
 Bilgi edinmek nasıl yapılır:

 [Örnek uygulamayı oluşturma](#BKMK_Create_the_sample_app)

 [Ayarlayın ve program verileri incelemek için bir kesme noktası, bir işlevin içine Adımlama çalıştırın](#BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data)

 [İçine, üzerine ve dışına işlevleri adım](#BKMK_Step_into__over__and_out_of_functions)

 [Koşullu kesme noktası ayarlayın, imleci çalıştırmak ve bir değişken görselleştirin](#BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable)

 [Yerel öğeler penceresinde değişken veri görünümü](#BKMK_View_variable_data_in_the_Locals_window)

- [Değişken veri ve bir nesnenin prototip zincirini görüntüleyin](#BKMK_View_variable_data_and_the_prototype_chain_of_an_object)

- [Kapsam zinciri verilerini İnceleme](#BKMK_Examine_scope_chain_data)

  [Çağrı yığını penceresini kullanarak koda gidin](#BKMK_Navigate_to_code_by_using_the_Call_Stack_window)

##  <a name="BKMK_Create_the_sample_app"></a> Örnek uygulamayı oluşturma
 Örnek uygulama, yalnızca hata ayıklama oturumu gezinme nasıl çalıştığını ve programınızın durumunu incelemek nasıl görebilirsiniz bir kaynak dosyası oluşturmak için Windows Store uygulaması çerçevesini kullanır. Bu nedenle, hata ayıklama, kodla ilgilidir. Tüm harekete geçirecek kodun çağrılır `module` default.js dosyasını işlevi. Hiçbir denetim eklenir ve hiçbir olay işlenir.

1. **Boş bir JavaScript Windows Store uygulaması oluşturursunuz.** Visual Studio'yu açın. Giriş sayfasından Yeni'yi seçin **yeni proje** bağlantı. Üzerinde **yeni proje** iletişim kutusunda **JavaScript** içinde **yüklü** listeleyin ve ardından **Windows Store**. Proje şablonları listesinde seçin **boş uygulama**. Visual Studio yeni çözüm ve proje oluşturup default.htm dosyasını Kod düzenleyicisinde görüntüler.

    Sayfasına yüklenen komut dosyalarını unutmayın.

   -   `base.js` Ve `ui.js` dosyaları oluşturmak **JavaScript için Windows Kitaplığı**. JavaScript için Windows kitaplığı JavaScript kümesidir ve JavaScript kullanarak Windows Store uygulamaları daha kolay hale getirmek CSS dosyaları oluşturun. Size, HTML, CSS ve Windows çalışma zamanı ile birlikte uygulamanızı oluşturmak için kullanın.

   -   Kodunuzu başlar `default.js` dosya.

2. **Default.js kaynak dosyasını açın.** Çözüm Gezgini'nde açın **js** düğümünü seçip `default.js`.

3. **Sayfa içeriğini örnek kod ile değiştirin.** Tüm içeriğini silmek `default.js` dosya. Bu bağlantıyı izleyin: [hata ayıklayıcı gezintisi örnek kodu (JavaScript)](../debugger/debugger-navigation-sample-code-javascript.md)ve ardından panoya JavaScript bölümünde listelenen kodu kopyalayın. (Seçin **geri** tarayıcı veya Yardım Görüntüleyicisi bu hızlı başlangıç sayfasına geri dönün.) Visual Studio Düzenleyicisi'nde kod şimdi boş yapıştırın `default.js`. Seçin **Ctrl + S** dosyayı kaydetmek için.

   Şimdi, bu konudaki örnekleri birlikte izleyebilirsiniz.

##  <a name="BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data"></a> Ayarlayın ve program verileri incelemek için bir kesme noktası, bir işlevin içine Adımlama çalıştırın
 Hata ayıklama oturumu başlatmak için en yaygın yolu seçmektir **hata ayıklamayı Başlat** gelen **hata ayıklama** menü (klavye: F5). Uygulama başladığında ve bir kesme noktasına ulaşıldığında, el ile özel bir durum oluştuğunda, yürütme askıya veya uygulama sona kadar yürütmeye devam eder.

 Yürütme hata ayıklayıcıda askıya alındığında, bir değişken üzerinde fare duraklatarak bir veri ipucunda etkin bir değişkenin değerini görüntüleyebilirsiniz.

 (Hata ayıklayıcıya bozucu da adlandırılır) uygulamanın yürütülmesini askıya sonra program kodun geri kalanını yürütür şeklini denetlemek. Satır bir işlev çağrısında işlevin kendisi taşıma devam edebilir veya tek bir adımda çağrılan işlevi yürütebilir. Bu yordamlar uygulama üzerinden Adımlama çağrılır. Ayrıca, imlecinizi konumlandırılmış burada ayarladığınız sonraki kesme noktasına veya satırına çalıştıran uygulama standart yürütülmesi devam edebilir. Hata ayıklama oturumu istediğiniz zaman durdurabilirsiniz. Hata ayıklayıcı gerekli temizleme işlemlerini gerçekleştirmek ve yürütme çıkmak için tasarlanmıştır.

###  <a name="BKMK_Example_1"></a> Örnek 1
 Bu örnekte, gövdesinde bir kesme noktası ayarlamak `module` işlevi `default.js` kullanıcı bildirimlerimiz ilk çağrısı. Ardından işlevdeki adım, hata ayıklayıcı veri ipuçlarında değişken değerleri görüntülemek ve ardından hata ayıklamayı durdurun.

1. **Bir kesme noktası ayarlayın.** İfadede bir kesme noktası ayarlamak `callTrack = "module function";` çağrısının hemen sonra oluşan `app.start()`. Kaynak Kod Düzenleyicisi gölgeli kanalda satır seçin (klavye: İmleç satıra getirin ve seçin **F9** anahtar).

    ![Örnek1 bir kesme noktası ayarlamak](../debugger/media/dbg-jsnav-example1-breakpoint.png "DBG_JSNAV_example1_breakpoint")

    Kesme noktası simgesi kanalda görünür.

2. **Kesme noktasına kadar çalıştırın.** Hata ayıklama oturumu başlatın **hata ayıklamayı Başlat** üzerinde **hata ayıklama** menü (klavye: F5).

    Uygulama yürütülürken başlar ve kesme noktasını ayarlamanız deyiminden hemen önce yürütmeyi askıya alır. Geçerli satır simgesi cilt payını konumunuz tanımlar ve geçerli deyim vurgulanır.

    ![Kesme noktasına Git](../debugger/media/dbg-jsnav-example1-run-to-breakpoint.png "DBG_JSNAV_example1_run_to_breakpoint")

    Artık uygulamanın yürütülmesini denetimi sizdedir ve program ifadeleri ilerleyerek program durumunu inceleyebilir.

3. **İşleve adım.** Üzerinde **hata ayıklama** menüsünde seçin **içine adımla** (klavye: **F11**).

    ![Bir kod satırının içine Adımlama](../debugger/media/dbg-jsnav-example1-step-into.png "DBG_JSNAV_example1_step_into")

    Hata ayıklayıcı sonraki satıra taşır not için bir çağrı olduğu `example1` işlevi. Seçin **içine adımla** yeniden. Hata ayıklayıcıyı ilk kod satırına taşır `example1` işlevi. Vurgulanan satırın yürütülmedi, ancak işlev çağrı yığınındaki yüklendi ve yerel değişkenler için belleği ayrıldı.

4. Bir kod satırının içine adımladığınızda hata ayıklayıcısı aşağıdaki işlemlerden birini gerçekleştirir:

   - Sonraki deyim, çözümünüzün bir işlev çağrısı değilse, hata ayıklayıcısı deyimi yürütür, sonraki deyime geçer ve ardından yürütmeyi askıya alır.

   - Çözümünüzde bir işlev çağrısı ifadesi ise hata ayıklayıcısı çağrılan işlevin ilk satıra taşır ve ardından yürütmeyi askıya alır.

     Devam deyimleri adımlamak `example1` çıkış noktası ulaşıncaya kadar. Hata ayıklayıcı işlevin kapanış küme ayracı vurgulanır.

5. **Veri İpuçları'ndaki değişken değerlerini görüntüleme.** Devam deyimleri adımlamak `example1` çıkış noktası ulaşıncaya kadar. Hata ayıklayıcı işlevin kapanış küme ayracı vurgulanır. Bir değişken adı üzerinde fareyle geldiğinizde, bir veri ipucunda adını ve değişkeninin değeri görüntülenir.

    ![Değişken değerleri veri ipucunda görüntülemek](../debugger/media/dbg-jsnav-data-tip.png "DBG_JSNAV_data_tip")

6. **CallTrack değişken için bir izleme ekleyin.** `callTrack` Değişkeni bu hızlı başlangıç boyunca örneklerde çağrılan işlevler göstermek için kullanılır. Değişkenin değerini görüntülemek kolaylaştırmak için bir Watch pencere ekleyin. Düzenleyicide değişken adı seçin ve sonra **Gözcü Ekle** kısayol menüsünden.

    ![Bir değişken izleyin](../debugger/media/dbg-jsnav-watch-window.png "DBG_JSNAV_watch_window")

    Birden çok izleme penceresi değişkenleri izleyebilirsiniz. Veri ipucu pencerelerinde değerleri gibi izlenen değişkenlerin değerleri, her yürütme askıya alındığında güncelleştirilir. İzlenen değişkenlerinizi hata ayıklama oturumları arasında kaydedilir.

7. **Hata ayıklamayı durdurun.** Üzerinde **hata ayıklama** menüsünde seçin **hata ayıklamayı Durdur** (klavye: **Shift + F5**). Bu, hata ayıklama oturumunuzu sonlandırır.

##  <a name="BKMK_Step_into__over__and_out_of_functions"></a> İçine, üzerine ve dışına işlevleri adım
 Bir üst işlev tarafından çağrılan bir işlevin içine Adımlama, aksine bir işlevin Adımlama alt işlevi yürütür ve üst sürdürür olarak çağıran işlev yürütme bekletir. İşlevi çalışır ve yürütme göreceğiniz Araştırdığınız sorunun etkilemez eminseniz işlemleriyle ilgili bilgi sahibi olduğunda bir işlevin üzerine adım.

 Bir işlev çağrısı içermeyen bir kod satırı Adımlama, satır satır Adımlama gibi yürütür.

 Bir alt işlevi dışında işlev yürütmeye devam eder ve kendi çağıran işleve işlev döndürdükten sonra yürütmeyi askıya alır. İşlev diğer önemli değil belirlediğinizde uzun bir işlevden adım.

 Hem üzerinden Adımlama hem de bir işlev dışına Adımlama işlevi yürütme.

 ![Adım içine, üzerine ve dışına yöntemleri](../debugger/media/dbg-basics-stepintooverout.png "DBG_Basics_StepIntoOverOut")

###  <a name="BKMK_Example_2"></a> Örnek 2
 Bu örnekte, içine, üzerine ve dışına işlevleri adım.

1.  **Örnek2 işlev modülü işlev çağrısında.** Düzen `module` satırı aşağıdaki değiştirin ve işlev `var callTrack = "module function"` ile `example2();`.

     ![Örnek2 işlev çağrısı](../debugger/media/dbg-jsnav-example2.png "DBG_JSNAV_example2")

2.  **Kesme noktasına kadar çalıştırın.** Hata ayıklama oturumu başlatın **hata ayıklamayı Başlat** üzerinde **hata ayıklama** menü (klavye: F5). Hata ayıklayıcı yürütme kesme noktasında askıya alır.

3.  **Kod satırı adım.** Üzerinde **hata ayıklama** menüsünde seçin **Step Over** (klavye: F10). Hata ayıklayıcı yürütür `var callTrack = "module function"` deyimi deyim Adımlama olarak aynı şekilde.

4.  **Örnek2 ve example2_a adım.** Seçin **F11** içine Adımlama için anahtar `example2` işlevi. Adımla devam `example2` satır ulaşana kadar deyimleri `var x = example2_a();`. Yine, adım için giriş noktasını taşımak için bu satır içine `example2_a`. Her ifadesine adım devam `example2_a` dönene kadar `example2`.

     ![Bir işlevin üzerinden adımla](../debugger/media/dbg-jsnav-example2-a.png "DBG_JSNAV_example2_a")

5.  **Bir işlevin üzerine adım.** Sonraki satır içinde Not `example2`, `var y = example2_a();` önceki satıra temelde aynıdır. Bu satırı güvenli bir şekilde geçebilirsiniz. Seçin **F10** işlemin sürdürülmesini taşımak için anahtar `example2` bu ikinci çağrı için `example2_a`. Unutmayın `callTrack` dize gösterir `example2_a` işlevi iki kez yürütüldü.

6.  **Bir işlevden adım.** Seçin **F11** içine Adımlama için anahtar `example2_b` işlevi. Unutmayın `example2_b` çok farklı değildir `example2_a`. İşlev dışında adım tercih **Step Out** üzerinde **hata ayıklama** menü (klavye: **Shift + F11**). Unutmayın `callTrack` değişkeni gösterir `example2_b` yürütülmesi ve hata ayıklayıcı noktadan döndürülen olduğu `example2` sürdürür.

7.  **Hata ayıklamayı durdurun.** Üzerinde **hata ayıklama** menüsünde seçin **hata ayıklamayı Durdur** (klavye: **Shift + F5**). Bu, hata ayıklama oturumunuzu sonlandırır.

##  <a name="BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable"></a> Koşullu kesme noktası ayarlayın, imleci çalıştırmak ve bir değişken görselleştirin
 Koşullu kesme noktası yürütmeyi askıya almak hata ayıklayıcı neden olan bir koşulu belirtir. Koşul true veya false sonucu verebilen herhangi bir kod ifade belirtilir. Örneğin, yalnızca bir değişken belirli bir değere ulaştığında sıkça çağrılan bir işlevde programınızın durumunu incelemek için bir koşullu kesme noktası kullanabilirsiniz.

 İmlece gitme, tek seferlik bir kesme noktası ayarlama gibi ' dir. Yürütme askıya alındığında, kaynak olarak bir satır seçin ve seçilen satırın ulaşılana kadar yürütmeyi devam. Örneğin, olabileceğiniz olması bir işlev bir döngüde üzerinden adımlama ve döngü içinde kod doğru şekilde çalıştığını belirlemek. Döngünün her yinelemesinden Adımlama yerine, döngü yürütüldükten sonra konumlandırılmış bir imleç çalıştırabilirsiniz.

 Bazı durumlarda, bir veri ipucunda veya diğer veri penceresi satır içinde bir değişken değerini görüntülemek zordur. Hata ayıklayıcı, kaydırılabilir bir pencerede değeri biçimlendirilmiş bir görünümünü sunan metin Görselleştirici, dizeler, HTML ve Xml görüntüleyebilirsiniz.

###  <a name="BKMK_Example_3"></a> Örnek 3
 Bu örnekte, belirli bir döngü yinelemeyi kesme, ardından döngüsünden sonra konumlandırılmış imlece kadar Çalıştır koşullu kesme noktası ayarlayın. Ayrıca bir değişkenin değerini bir metin görselleştiricisi içinde görüntüleyin.

1.  **Örnek3 işlev modülü işlev çağrısında.** Düzen `module` satırı aşağıdaki değiştirin ve işlev `var callTrack = "module function";` satırı ile `example3();`.

     ![Örnek3 çağrı](../debugger/media/dbg-jsnav-example3.png "DBG_JSNAV_example3")

2.  **Kesme noktasına kadar çalıştırın.** Hata ayıklama oturumu başlatın **hata ayıklamayı Başlat** üzerinde **hata ayıklama** menü (klavye: **F5**). Hata ayıklayıcı kesme noktasında yürütmeyi askıya alır `module` işlevi.

3.  **Örnek3 işleve adım.** Seçin **içine adımla** üzerinde **hata ayıklama** menü (klavye: **F11**) için giriş noktasını taşımak `example3` işlevi. Bir veya iki döngüleri yinelendiğinde kadar işlevin Adımlama devam `for` blok. Bu, tüm 1000 yineleme boyunca adım uzun süreceğini unutmayın.

4.  **Koşullu kesme noktası ayarlayın.** Kod penceresinin sol kanalda satırın sağ `s += i.toString() + "\n";` seçip **koşul** kısayol menüsünde.

     Seçin **koşul** onay kutusunu işaretleyin ve ardından yazın `i == 500;` metin kutusuna. Seçin **true** seçenek ve **Tamam**. Kesme noktası 500th yinelemesini değerinde kontrol etmenize olanak `for` döngü. Koşullu kesme noktası simgesi, beyaz arası tarafından tespit edebilirsiniz.

     ![Koşullu kesme noktası simgesi](../debugger/media/dbg-jsnav-breakpoint-condition-icon.png "DBG_JSNAV_Breakpoint_Condition_icon")

5.  **Kesme noktasına kadar çalıştırın.** Üzerinde **hata ayıklama** menüsünde seçin **devam** (klavye: **F5**). Duraklatma `i` onaylamak için geçerli değerini `i` 500'dür. Ayrıca değişkeni `s` tek satır olarak ifade edilir ve veri ipucu penceresi daha çok uzun.

6.  **Bir dize değişkeni görselleştirin.** Veri ipucu Büyüteç simgesini `s`.

     Metin Görselleştirici penceresi görünür ve dize değeri çok satırlı dize olarak sunulur.

     ![Metin Görselleştirici hata ayıklama](../debugger/media/dbg-jsnav-text-visualizer.png "DBG_JSNAV_Text_Visualizer")

7.  **İmlece kadar çalıştırma.** Satırı seçin `callTrack += "->example3";` seçip **imlece kadar Çalıştır** kısayol menüsünde (klavye: **Ctrl + F10**). Hata ayıklayıcı, döngü yinelemesi tamamlar ve ardından satırında yürütmeyi askıya alır.

8.  **Hata ayıklamayı durdurun.** Üzerinde **hata ayıklama** menüsünde seçin **hata ayıklamayı Durdur** (klavye: **Shift + F5**). Bu, hata ayıklama oturumunuzu sonlandırır.

###  <a name="BKMK_Use_Run_to_Cursor_to_return_to_your_code_and_delete_a_breakpoint"></a> İmlece kadar Çalıştır kodunuza geri dönün ve bir kesme noktası silmek için kullanın
 Kitaplık kodu Microsoft'tan basamaklı veya bir üçüncü taraf imlece gitme çok kullanışlı olabilir. Kitaplık kod içerisinde ilerlemeye bilgilendirici olabilir, ancak genellikle uzun zaman alabilir. Ve genellikle kendi kodunuzda daha ilgilendiğiniz. Bu alıştırmada, nasıl yapılacağını gösterir.

1.  **App.start çağrıda bir kesme noktası ayarlayın.** İçinde `module` işlev, satırında bir kesme noktası ayarlayın `app.start()`

2.  **Kesme noktasına kadar çalıştırın ve kitaplık işleve.**

     İçine geçtiğinizde `app.start()`, Kod Düzenleyicisi'ni görüntüler `base.js`. Birden fazla satıra birkaç adım.

3.  **İçinde ve dışında işlevleri adım.** Üzerinden ilerleyerek (**F10**) ve / adım (**SHIFT + F11**) kod `base.js`, bu karmaşıklığı İnceleme için sonuç gelebilir ve uzunluğunda başlangıç işlevin ne yaptığını istediğiniz değil.

4.  **İmleç kodunuzda ayarlayın ve kendisine çalıştırın.** Dönmek `default.js` dosyasını Kod düzenleyicisinde. Koddan sonra ilk satırını seçin `app.start()` (açıklama ya da boş bir satır çalıştıramazsınız). Seçin **imlece kadar Çalıştır** kısayol menüsünden. Hata ayıklayıcı app.start işlev yürütmeye devam eder ve kesme noktasında yürütmeyi askıya alır.

##  <a name="BKMK_View_variable_data_in_the_Locals_window"></a> Yerel öğeler penceresinde değişken veri görünümü
 Yerel windows parametreler ve değişkenler yürütülmekte olan işlevin kapsamı zincirindeki ağaç görünümünü olur.

###  <a name="BKMK_View_variable_data_and_the_prototype_chain_of_an_object"></a> Değişken veri ve bir nesnenin prototip zincirini görüntüleyin

1.  **Bir dizi nesnesi modülü işlevi ekleyin.** Düzen `module` satırı aşağıdaki değiştirin ve işlev `var callTrack = "module function"` ile `var myArray = new Array(1, 2, 3);`

     ![myArray tanımı](../debugger/media/dbg-jsnav-myarray.png "DBG_JSNAV_myArray")

2.  **Kesme noktasına kadar çalıştırın.** Hata ayıklama oturumu başlatın **hata ayıklamayı Başlat** üzerinde **hata ayıklama** menü (klavye: **F5**). Hata ayıklayıcı yürütme kesme noktasında askıya alır. Çizginin Adımlama.

3.  **Yereller penceresini açın.** Üzerinde **hata ayıklama** menüsünde **Windows**ve ardından **Yereller**. (Klavye: Alt + 4).

4.  **Modül işlevinde yerel değişkenlerini inceleyin** Yereller windows yürütülmekte olan işlevin değişkenleri görüntüler ( `module` işlevi) ağacı üst düzey düğüm. JavaScript bir işleve girdiğiniz zaman, tüm değişkenler oluşturur ve bunları değerini verir `undefined`. İşlev içinde tanımlanan işlevleri kendi metin bir değere sahip.

     ![Yerel öğeler penceresinde](../debugger/media/dbg-jsnav-locals-window.png "DBG_JSNAV_Locals_window")

5.  **CallTrack ve myArray tanımları adım.** CallTrack ve myArray değişkenleri Yereller penceresinde bulabilirsiniz. Üzerinden adımla (**F10**) iki tanımları ve dikkat **değeri** ve **türü** alanları değiştirilir. Son kesme beri değiştirilen değişkenlerin değerleri Yereller penceresinde vurgular.

6.  **MyArray nesnesini inceler** genişletme `myArray` değişkeni. Dizinin her öğesi listelenen **[prototip]** içeren devralma hiyerarşisinde düğümü `Array` nesne. Bu düğümü genişletin.

     ![Prototip zinciri Yereller penceresinde](../debugger/media/dbg-jsnav-locals-proto-chain.png "DBG_JSNAV_Locals_proto_chain")

    -   **Yöntemleri** düğümü tüm yöntemleri listeler `Array` nesne.

    -   **[Prototip]** düğüm içeriyor prototipi `Object` nesnesi `Array` türetilir. **[prototip]**  düğümleri özyinelemeli olabilir. Her üst nesne bir nesne sıradüzeni içinde açıklanan **[prototip]** alt düğümü.

7.  **Hata ayıklamayı durdurun.** Üzerinde **hata ayıklama** menüsünde seçin **hata ayıklamayı Durdur** (klavye: Shift + F5). Bu, hata ayıklama oturumunuzu sonlandırır.

##  <a name="BKMK_Examine_scope_chain_data"></a> Kapsam zinciri verilerini İnceleme
 *Kapsam zinciri* etkin ve işlev tarafından erişilebilir olan tüm değişkenlere işlevi içerir. Yürütülmekte olan işlevin tanımlayan işlev tanımlanan tüm nesneleri (işlevler dahil olmak üzere) gibi genel değişkenler kapsam zincirinde bir parçasıdır. Örneğin, `callTrack` tanımlanan değişkeni `module` işlevi `default.js` tanımlanan herhangi bir işlev tarafından ulaşılabildiğinden `module` işlevi. Her kapsam ayrı olarak Yereller penceresinde listelenir.

- Yürütülmekte olan işlevin değişkenleri penceresinin en üstünde yer alır.

- Kapsam zincirindeki her işlev kapsamı değişkenleri altında listelenen bir **[kapsam]** düğümü için işlev. Kapsam işlevleri zincirindeki zincir en dıştaki işlev için geçerli işlevini tanımlayan işlevden sıralarına göre listelenir.

- **[Genel]** düğümü dışındaki herhangi bir işlev tanımlanan genel nesneleri listeler.

  Kapsam zincirleri kafa karıştırıcı olabilir ve en iyi örnekle gösterilmiştir. Aşağıdaki örnekte, gördüğünüz nasıl `module` işlevi oluşturur, kendi kapsamı ve diğerine nasıl oluşturabileceğinizi kapsamı düzeyi kapanım oluşturarak.

###  <a name="BKMK_Example_4"></a> Örnek 4

1.  **Örnek4 işlevi modül işlevini çağırın.** Düzen `module` satırı aşağıdaki değiştirin ve işlev `var callTrack = "module function"` ile `example4()`:

     ![Örnek4 çağrı](../debugger/media/dbg-jsnav-example4.png "DBG_JSNAV_example4")

2.  **Kesme noktasına kadar çalıştırın.** Hata ayıklama oturumu başlatın **hata ayıklamayı Başlat** üzerinde **hata ayıklama** menü (klavye: **F5**). Hata ayıklayıcı yürütme kesme noktasında askıya alır.

3.  **Yereller penceresini açın.** Üzerinde gerekirse **hata ayıklama** menüsünde **Windows**ve ardından **Yereller**. (Klavye: **Alt + 4**). Pencerenin tüm değişkenleri listeler ve içindeki işlevler unutmayın `module` işlev ve de içeren bir **[genel]** düğümü.

4.  **Genel değişkenler inceleyin.** Genişletin **[genel]** düğümü. Global değişkenler ve nesneler JavaScript için Windows kitaplığı tarafından ayarlandı. Kendi değişkenleri için genel kapsam ekleyebilirsiniz.

5.  **Adım örnek4 ve kendi yerel inceleyin ve kapsam değişkenleri** adımla (klavye: **F11**) `example4` işlevi. Çünkü `example4` tanımlanan `module` işlevi `module` işlevi üst kapsam haline gelir. `example4` işlevlerde birini çağırabilirsiniz `module` işlev ve değişkenlerini erişin. Genişletin **[kapsam]** düğüm Yereller penceresinde ve aynı ve değişkenler içeren Not `module` işlevi.

     ![Örnek4 yönteminin kapsam](../debugger/media/dbg-jsnav-locals-example4-scope.png "DBG_JSNAV_Locals_example4_scope")

6.  **Adım example4_a ve kendi yerel inceleyin ve kapsam değişkenleri** adımla devam `example4` ve çağrıya dönüştürür `example4_a`. Yerel değişkenler artık arasındadır Not `example4_a`ve **[kapsam]** düğüm devam değişkenleri tutacak `module` işlevi. Olsa da değişkenleri `example4` olan etkin, bunlar ulaşılamıyor tarafından `example4_a` ve kapsam zinciri artık parçasıdır.

7.  **Adım multipyByA ve kendi yerel inceleyin ve kapsam değişkenleri** adım kalanında `example4_a` ve satırına `var x = multilpyByA(b);`.

     İşlev değişkeni `multipyByA` ayarlanmış `multiplyClosure` olan işlevi bir *kapanış*. `multipyClosure` tanımlar ve bir iç işlevi döndürür `mulitplyXby`ve yakalar (üzerinden kapatır), parametre ve değişken. Bir kapanış döndürülen iç işlev dış işlevin veri erişimi ve bu nedenle kapsam düzeyini oluşturur.

     İçine geçtiğinizde `var x = multilpyByA(b);`, geçmeden `return a * b;` satırına `mulitplyXby` iç işlevi.

8.  Yerel öğeler penceresinde, yalnızca parametresini `b` yerel bir değişken olarak listelenen `multiplyXby`, ancak yeni bir **[kapsam]** düzeyi eklendi. Bu düğümü genişletmek, parametreleri, İşlevler ve değişkenler içerdiğini görürsünüz `multiplyClosure`de dahil olmak üzere `a` değişken adı ilk satırı `multiplyXby`. Hızlı bir ikinci denetimini **[kapsam]** düğüm modülü işlevi değişkenleri ortaya çıkarır, `multiplyXby` sonraki satıra erişir.

     ![Yerel öğeler penceresinde bir kapanış kapsamını](../debugger/media/dbg-jsnav-scope-mulitplyxby.png "DBG_JSNAV_scope_mulitplyXby")

9. **Hata ayıklamayı durdurun.** Üzerinde **hata ayıklama** menüsünde seçin **hata ayıklamayı Durdur** (klavye: **Shift + F5**). Bu, hata ayıklama oturumunuzu sonlandırır.

##  <a name="BKMK_Navigate_to_code_by_using_the_Call_Stack_window"></a> Çağrı yığını penceresini kullanarak koda gidin
 Çağrı yığınını uygulamanın geçerli iş parçacığında yürütülen işlevler hakkında bilgi içeren bir veri yapısıdır. Bir kesme noktasına ulaştığınızda, çağrı yığını penceresini yığın üzerinde etkin olan işlevlerin tümünün listesini görüntüler. Çağrı yığını penceresinde listenin en üstünde şu anda yürütülen işlevdir. İş parçacığı başlatan listesinin en altında işlevdir. İşlevleri arasındaki geçerli işlevin başlatma işlevi çağrısı yolunu gösterir.

 Şu anda yürütülen işleve çağrı yol göstermeye ek olarak, çağrı yığını penceresinde Kod düzenleyicisinde kod gitmek için kullanılabilir. Bu işlevselliği birden fazla dosyalarıyla çalışıyorsanız ve belirli bir işleve hızlıca taşımak istediğinizde yararlı olabilir.

###  <a name="BKMK_Example_5"></a> Örnek 5
 Bu örnekte, beş kullanıcı tarafından tanımlanan işlevler içeren bir çağrı yola adım.

1.  **Örneği5 işlev modülü işlev çağrısında.** Düzen `module` satırı aşağıdaki değiştirin ve işlev `var callTrack = "module function";` satırı ile `example5();`.

     ![Örneği5 çağrı](../debugger/media/dbg-jsnav-example5.png "DBG_JSNAV_example5")

2.  **Kesme noktasına kadar çalıştırın.** Hata ayıklama oturumu başlatın **hata ayıklamayı Başlat** üzerinde **hata ayıklama** menü (klavye: **F5**). Hata ayıklayıcı modül işlevdeki bir kesme noktasında yürütmeyi askıya alır.

3.  **Çağrı yığını penceresini açın.** Üzerinde **hata ayıklama** menüsünde seçin **Windows**ve ardından **çağrı yığını** (klavye: Alt + 7). Çağrı yığını penceresinde iki işlev gösterdiğine dikkat edin:

    -   **Genel kod** giriş noktası `module` çağrı yığınını alt kısmındaki işlevi.

    -   **Anonim işlev** satırda gösterir `module` yürütmesi askıya alındı burada işlevi. Çağrı yığınının başı budur.

4.  **İşlevlere example5_d işlevi ulaşmak için adım adım.** Seçin **içine adımla** üzerinde **hata ayıklama** menü (klavye: **F11**) example5_d işlev giriş noktası ulaşana kadar arama yolunda çağrılarını yürütmek için. Bir işlev bir işlevi çağırır, çağıran işlevin satır numarası kaydedilir ve çağrılan işlev, yığın üstüne yerleştirilen her zaman unutmayın. Çağıran işlevin satır numarası, çağıran işlevin yürütmesi askıya aldı noktasıdır. Sarı bir ok, o anda yürütülen işleve işaret eder.

     ![Çağrı yığını penceresi](../debugger/media/dbg-jsnav-callstack-windows.png "DBG_JSNAV_CallStack_windows")

5.  **Bir kesme noktası ayarlayın ve example5_a koduna gitmek için çağrı yığını penceresini kullanın.** Çağrı yığını penceresinde `example5_a` liste öğesi ve ardından **kaynağa Git** kısayol menüsünde. Kod Düzenleyicisi, imleç işlevin dönüş satırında ayarlar. Bu satıra bir kesme noktası ayarlayın. Geçerli yürütme satırını değiştirilmez unutmayın. Yalnızca Düzenleyici imleci taşınmıştır.

6.  **İşlevlere adım ve kesme noktasına kadar çalıştırın.** İçine Adımlama devam `example5_d`. İşlevden döndüğünüzde, çağrı yığını alınır unutmayın. Tuşuna **F5** programın yürütülmesi devam etmek için. Önceki adımda oluşturulan kesme noktasındaki durdur.

7.  **Hata ayıklamayı durdurun.** Üzerinde **hata ayıklama** menüsünde seçin **hata ayıklamayı Durdur** (klavye: **Shift + F5**). Bu, hata ayıklama oturumunuzu sonlandırır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Bir (JavaScript) hata ayıklama oturumunu başlatmada](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md) [hızlı başlangıç: hata ayıklayıcı gezintisi (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [hızlı başlangıç: hata ayıklama HTML ve CSS](../debugger/quickstart-debug-html-and-css.md) [tetikleyici askıya alma, sürdürme ve arka plan olayları Windows Store için)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [uygulamaları Visual Studio'da hata ayıklama](../debugger/debug-store-apps-in-visual-studio.md)
