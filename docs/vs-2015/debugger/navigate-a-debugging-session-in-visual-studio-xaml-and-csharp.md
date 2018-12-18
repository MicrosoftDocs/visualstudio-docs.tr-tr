---
title: Hata ayıklama oturumunda gezinme (Xaml ve C#) | Microsoft Docs
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
ms.assetid: 1da33203-333f-4a05-b4e2-8d407c497233
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a3dc5236d47450cb755ff8abbffd5b6497ff145
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052244"
---
# <a name="navigate-a-debugging-session-in-visual-studio-xaml-and-c"></a>Visual Studio’da (Xaml ve C#) bir hata ayıklama oturumunda gezinme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu hızlı başlangıçta, Visual Studio hata ayıklama oturumları gitmek ve görüntülemek ve bir oturumda program durumunu değiştirmek gösterir.

 Bu hızlı başlangıçta, Visual Studio ile hata ayıklama için yenidir ve hata ayıklama oturumu Visual Studio'da gezinme hakkında daha fazla bilgi için isteyen geliştiriciler için geliştiriciler içindir. Kendi hata ayıklama resim öğretmek değildir. Örnek kodda yöntemleri, yalnızca bu konuda açıklanan hata ayıklama yordamları göstermek için tasarlanmıştır. Uygulama veya işlev tasarımının en iyi yöntemleri dağıtıyorsunuz değil. Aslında, yöntemleri ve uygulama içinden her şeyin daha fazlasını yapmanız değil, hızlı bir şekilde keşfeder.

 Bu hızlı başlangıçta bölümlerini, zaten alışık olduğunuz bilgiler içeren herhangi bir bölümü atlayabilirsiniz olabildiğince bağımsız olarak tasarlanmıştır. Örnek bir uygulama oluşturmak için gerekli değildir; ancak biz bunu tavsiye ve işlem mümkün olduğu kadar kolay yaptığınız.

 **Hata ayıklayıcı, klavye kısayolları.** Visual Studio hata ayıklayıcı gezintisi, hem fare ve klavye için optimize edilmiştir. Bu konu başlığı altındaki adımların birçok klavye kısayol tuşu veya kısayol tuşu parantez içinde bir açıklama içerir. Örneğin, (klavye: F5) yazarak F5 başlatır veya hata ayıklayıcı yürütme devam eder, anahtar gösterir.

## <a name="in-this-topic"></a>Bu konuda
 Bilgi edinmek nasıl yapılır:

-   [Örnek uygulamayı oluşturma](#BKMK_CreateTheApplication)

-   [Ayarlayın ve program verileri incelemek için bir kesme noktası, bir yöntem adımla çalıştırın](#BKMK_StepInto)

-   [İçine, üzerine ve dışına yöntemleri adım](#BKMK_StepIntoOverOut)

-   [Koşullu kesme noktası ayarlayın, imleci çalıştırmak ve bir değişken görselleştirin](#BKMK_ConditionCursorVisualize)

-   [Düzenle ve devam etmek için bir özel durumdan kurtarma](#BKMK_EditContinueRecoverExceptions)

##  <a name="BKMK_CreateTheApplication"></a> Örnek uygulamayı oluşturma
 Örnek uygulama, yalnızca hata ayıklama oturumu gezinme nasıl çalıştığı ve nasıl program durumunu inceleyebilir ve görebilirsiniz bir kaynak dosyası oluşturmak için Windows Store uygulaması çerçevesini kullanır. Bu nedenle, hata ayıklama, kodla ilgilidir. Tüm çağırır, kodun ana sayfasında oluşturucudan çağrılır; Hiçbir denetim eklenir ve hiçbir olay işlenir.

 **Bir varsayılan C# Windows Store uygulaması oluşturacaksınız.** Visual Studio'yu açın. Giriş sayfasından Yeni'yi seçin **yeni proje** bağlantı. Yeni Proje iletişim kutusunda, seçmek **Visual C#** içinde **yüklü** listeleyin ve ardından **Windows Store**. Proje şablonları listesinde seçin **uygulama**. Visual Studio yeni çözüm ve proje oluşturur ve MainPage.xaml Tasarımcısı ve XAML Kod düzenleyicisinde görüntüler.

 **MainPage.xaml.cs kaynak dosyasını açın.** XAML Düzenleyicisi'nde herhangi bir yere sağ tıklayın ve seçin **kodu görüntüle**. MainPage.xaml.cs arka plan kod dosyası görüntülenir. Bu yalnızca bir yöntem Not `MainPage()` oluşturucusu, dosyada listelenmektedir.

 **MainPage Oluşturucusu örnek kod ile değiştirin.** MainPage() yöntemi silin. Bu bağlantıyı izleyin: [hata ayıklayıcı gezintisi örnek kodu (Xaml ve C#)](../debugger/debugger-navigation-sample-code-xaml-and-csharp.md)ve ardından Pano için C# bölümünde listelenen kodu kopyalayın. (Seçin **geri** tarayıcı veya Yardım Görüntüleyicisi bu hızlı başlangıç sayfasına geri dönün.) Visual Studio Düzenleyicisi'nde koda yapıştırın `partial class MainPage` blok. Dosyayı kaydetmek için CTRL + s seçin.

 Şimdi, bu konudaki örnekleri birlikte izleyebilirsiniz.

##  <a name="BKMK_StepInto"></a> Ayarlayın ve program verileri incelemek için bir kesme noktası, bir yöntem adımla çalıştırın
 Bir hata ayıklama oturumu başlatabilirsiniz en yaygın yolu seçmektir **hata ayıklamayı Başlat** gelen **hata ayıklama** menü (klavye: F5). Yürütme başlar ve bir kesme noktasına ulaşıldığında, el ile özel bir durum oluştuğunda, yürütme askıya veya uygulama sona kadar devam eder.

 Yürütme hata ayıklayıcıda askıya alındığında, değişkenin fare gelerek bir veri ipucunda etkin bir değişkenin değerini görüntüleyebilirsiniz. Etkin değişkenleri ve geçerli değerlerini listesini görmek için Yereller ve Arabalar'da windows da açabilirsiniz. Bir veya daha fazla değişkenleri uygulama yürütme devam ettikçe değişkenlerinin değere odaklanmak bir Gözcü penceresi imkan tanır ekleniyor.

 (Hata ayıklayıcıya bozucu da adlandırılır) uygulamanın yürütülmesini askıya sonra program kodun geri kalanını yürütülür şeklini denetlemek. Yöntemin kendisi, yöntem çağrısından taşıma satır devam edebilirsiniz ya da çağrılan yöntem tek bir adımda yürütebilirsiniz. Bu yordamlar uygulama üzerinden Adımlama çağrılır. Ayrıca, imlecinizi konumlandırılmış burada ayarladığınız sonraki kesme noktasına veya satırına çalıştıran uygulama standart yürütülmesi devam edebilir. Hata ayıklama oturumu istediğiniz zaman durdurabilirsiniz. Hata ayıklayıcı gerekli temizleme işlemlerini gerçekleştirmek ve yürütme çıkmak için tasarlanmıştır.

### <a name="example-1"></a>Örnek 1
 Bu örnekte, MainPage.xaml.cs dosyanın MainPage oluşturucuda bir kesme noktası ayarlayın, ilk metodun içine, değişken değerlerini görüntülemek ve ardından hata ayıklamayı durdurun.

 **Bir kesme noktası ayarlayın.** İfadede bir kesme noktası ayarlamak `methodTrack = "Main Page";` MainPage oluşturucuda. Kaynak Kod Düzenleyicisi gölgeli kanalda satır seçin (klavye: F9 tuşuna basın ve imleci satıra getirin).

 ![Adımlama](../debugger/media/dbg-basics-stepinto.png "DBG_Basics_StepInto")

 Kesme noktası simgesi kanalda görünür.

 **Kesme noktasına kadar çalıştırın.** Hata ayıklama oturumu başlatın **hata ayıklamayı Başlat** üzerinde **hata ayıklama** menü (klavye: F5).

 Uygulama yürütülürken başlar ve kesme noktasını ayarlamanız deyiminden hemen önce yürütmeyi askıya alır. Geçerli satır simgesi cilt payını konumunuz tanımlar ve geçerli deyim vurgulanır.

 ![Bir kesme noktası ayarlamak](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")

 Artık uygulamanın yürütülmesini denetimi sizdedir ve program ifadeleri ilerleyerek program durumunu inceleyebilir.

 **Yönteme adım.** Üzerinde **hata ayıklama** menüsünde seçin **içine adımla** (klavye: F11).

 ![Geçerli satırı](../debugger/media/dbg-basics-currentline.png "DBG_Basics_CurrentLine")

 Hata ayıklayıcı örnek1 yönteme bir çağrı sonraki satıra taşır unutmayın. İçine adımla yeniden seçin. Hata ayıklayıcı örnek1 yöntemi Giriş noktasına taşır. Bu yöntem, çağrı yığınındaki yüklendi ve yerel değişkenler için belleği tahsis gösterir.

 Bir kod satırının içine adımladığınızda hata ayıklayıcısı aşağıdaki işlemlerden birini gerçekleştirir:

- Sonraki deyim, çözümünüzün bir işlev çağrısı değilse, hata ayıklayıcısı deyimi yürütür, sonraki deyime geçer ve ardından yürütmeyi askıya alır.

- Çözümünüzde bir işlev çağrısı ifadesi ise hata ayıklayıcısı çağrılan işlevin Giriş noktasına taşır ve ardından yürütmeyi askıya alır.

  Çıkış noktası ulaşıncaya kadar örnek1 açıklamaalarını adımla devam edin. Hata ayıklayıcı yöntemin kapanış küme ayracı vurgulanır.

  **Veri ipuçları değişken değerleri inceleyin.** Fare bir değişken adının üzerine geldiğinizde, bir veri ipucunda ada, değere ve değişken türü görüntülenir.

  ![Hata ayıklayıcı veri İpucu](../debugger/media/dbg-basics-datatip.png "DBG_Basics_DataTip")

  Değişkenin fare gelin `a`. Ada, değere ve veri türünü not alın. Değişkenin fare gelin `methodTrack`. Yeniden ada, değere ve veri türünü not alın.

  **Değişken değerleri Yereller penceresinde inceleyin.** Üzerinde **hata ayıklama** menüsünde **Windows**ve ardından **Yereller**. (Klavye: Alt + 4).

  ![Yerel öğeler penceresinde](../debugger/media/dbg-basics-localswindow.png "DBG_Basics_LocalsWindow")

  Yerel windows, ağaç görünümünde parametrelerinin ve işlevin değişkenleri gereklidir. Nesnenin alt düğümleri bir nesne değişkeninin özelliklerdir. `this` Değişkendir nesnesini temsil eden her nesne yöntemi gizli parametre. Bu durumda, MainPage sınıfı temsil eder. Çünkü `methodTrack` MainPage sınıfının, değer ve veri türünün bir üyesi bir satırda altında listelenen olan `this`. Genişletin `this` görüntülemek için düğümü `methodTrack` bilgileri.

  **MethodTrack değişken için bir izleme ekleyin.** `methodWatch` Değişkeni bu hızlı başlangıç boyunca örneklerde çağrılan yöntemler göstermek için kullanılır. Değişkenin değerini görüntülemek kolaylaştırmak için bir watch pencere ekleyin. Yerel öğeler penceresinde değişken adına sağ tıklayın ve ardından **Gözcü Ekle**.

  ![İzleme penceresi](../debugger/media/dbg-basics-watchwindow.png "DBG_Basics_WatchWindow")

  Birden çok izleme penceresi değişkenleri izleyebilirsiniz. Değerleri Yereller ve veri ipucu windows gibi izlenen değişkenlerin değerleri, her yürütme askıya alındığında güncelleştirilir. Kod düzenleyicisinden İzle penceresine değişkenler de ekleyebilirsiniz. İzlemek için değişkeni seçin, sağ tıklatın ve ardından **Gözcü Ekle**.

##  <a name="BKMK_StepIntoOverOut"></a> İçine, üzerine ve dışına yöntemleri adım
 Üst yöntemi tarafından adlı bir yöntem içine Adımlama, aksine bir yöntem Adımlama alt yöntemini yürütür ve üst sürdürür olarak çağıran yöntem yürütme bekletir. Yöntem çalışır ve yürütme göreceğiniz Araştırdığınız sorunun etkilemez eminseniz işlemleriyle ilgili bilgi sahibi olduğunda bir yöntem adım.

 Bir yöntem çağrısı içermiyor kod satırı Adımlama, satır satır Adımlama gibi yürütür.

 Alt yöntemi dışına Adımlama, yöntemin yürütülmesi devam eder ve kendi yöntemi çağrılırken yöntemin dönüşünün ardından yürütmeyi askıya alır. İşlev diğer önemli değil belirlediğinizde uzun bir işlevden adım.

 Hem üzerinden Adımlama hem de bir işlev dışına Adımlama işlevi yürütme.

 ![Adım içine, üzerine ve dışına yöntemleri](../debugger/media/dbg-basics-stepintooverout.png "DBG_Basics_StepIntoOverOut")

### <a name="example-2"></a>Örnek 2
 Bu örnekte, içine, üzerine ve dışına yöntemleri adım.

 **MainPage oluşturucuda örnek2 yöntemi çağırın.** MainPage Oluşturucusu düzenleyebilir ve aşağıdaki satırı değiştirin `methodTrack = String.Empty;` ile `Example2();`.

 ![Tanıtım örnek2 yöntemi çağırın](../debugger/media/dbg-basics-callexample2.png "DBG_Basics_CallExample2")

 **Kesme noktasına kadar çalıştırın.** Hata ayıklama oturumu başlatın **hata ayıklamayı Başlat** üzerinde **hata ayıklama** menü (klavye: F5). Hata ayıklayıcı yürütme kesme noktasında askıya alır.

 **Kod satırı adım.** Üzerinde **hata ayıklama** menüsünde seçin **Step Over** (klavye: F10). Hata ayıklayıcı yürütür `methodTrack = "MainPage";` deyimi deyim Adımlama olarak aynı şekilde.

 **Örnek2 ve Example2_A içine Adımlama.** Örnek 2 metodun içine F11 tuşuna basın. Satır ulaşana kadar örnek2 açıklamaalarını adım devam `int x = Example2_A();`. Yeniden, giriş noktası Example2_A taşımak için bu satır içine Adımlama. Örnek2 için dönene kadar her Example2_A deyiminin adımlamak devam edin.

 ![Örnek2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")

 **Bir işlevin üzerine adım.** Sonraki satır örnek2 içinde Not `int y = Example2_A();` önceki satıra temelde aynıdır. Bu satırı güvenli bir şekilde geçebilirsiniz. Bu ikinci çağrı Example2_A örnek2 işlemin sürdürülmesini taşımayı F10 tuşuna basın. Bu yöntem adımlamak için F10 seçin. Unutmayın `methodTrack` dize gösterir Example2_A yöntemi iki kez yürütüldü. Ayrıca, hata ayıklayıcının hemen sonraki satıra taşır fark edeceksiniz. Bu yürütme noktası örnek2 sürdürür askıya almaz.

 **Bir işlevden adım.** Example2_B metodun içine F11 tuşuna basın. Example2_B Example2_A çok farklı olduğunu unutmayın. Yöntemi dışında adım tercih **Step Out** üzerinde **hata ayıklama** menü (klavye: Shift + F11). Unutmayın `methodTrack` değişkeni Example2_B yürütülmesi ve hata ayıklayıcı burada örnek2 sürdürür noktasına döndürdüğünü gösterir.

 **Hata ayıklamayı durdurun.** Hata Ayıklama menüsünde, hata ayıklamayı Durdur seçin (klavye: Shift + F5). Bu, hata ayıklama oturumunuzu sonlandırır.

##  <a name="BKMK_ConditionCursorVisualize"></a> Koşullu kesme noktası ayarlayın, imleci çalıştırmak ve bir değişken görselleştirin
 Koşullu kesme noktası yürütmeyi askıya almak hata ayıklayıcı neden olan bir koşulu belirtir. Koşul true veya false sonucu verebilen herhangi bir kod ifade belirtilir. Örneğin, yalnızca bir değişken belirli bir değere ulaştığında sıkça çağrılan yöntemde programınızın durumunu incelemek için bir koşullu kesme noktası kullanabilirsiniz.

 İmlece gitme, tek seferlik bir kesme noktası ayarlama gibi ' dir. Yürütme askıya alındığında, kaynak olarak bir satır seçin ve seçilen satırın ulaşılana kadar yürütmeyi devam. Örneğin, olabileceğiniz olması bir yöntem bir döngüde üzerinden adımlama ve döngü içinde kod doğru şekilde çalıştığını belirlemek. Döngünün her yinelemesinden Adımlama yerine, döngü yürütüldükten sonra konumlandırılmış bir imleç çalıştırabilirsiniz.

 Bazen bir değişken değeri satır veri ipucu veya değişken penceresinde görüntülemek zordur. Hata ayıklayıcı, kaydırılabilir bir pencerede değeri biçimlendirilmiş bir görünümünü sunan metin Görselleştirici, dizeler, HTML ve Xml görüntüleyebilirsiniz.

### <a name="example-3"></a>Örnek 3
 Bu örnekte, belirli bir döngü yinelemeyi kesme, ardından döngüsünden sonra konumlandırılmış imlece kadar Çalıştır koşullu kesme noktası ayarlayın. Ayrıca bir değişkenin değerini bir metin görselleştiricisi içinde görüntüleyin.

 **MainPage oluşturucuda örnek3 yöntemi çağırın.** MainPage Oluşturucusu düzenleyebilir ve aşağıdaki satırı değiştirin `methodTrack = String.Empty;` satırı ile `Example3();`.

 ![Tanıtım örnek3 çağırın](../debugger/media/dbg-basics-callexample3.png "DBG_Basics_CallExample3")

 **Kesme noktasına kadar çalıştırın.** Hata ayıklama oturumu başlatın **hata ayıklamayı Başlat** üzerinde **hata ayıklama** menü (klavye: F5). Hata ayıklayıcı MainPage yöntemde bir kesme noktasında yürütmeyi askıya alır.

 **Örnek3 yöntemi içine Adımlama.** Seçin **içine adımla** üzerinde **hata ayıklama** menü (klavye: F11) örnek3 yöntemi Giriş noktasına taşınır. Bir veya iki döngüleri yinelendiğinde kadar metodun Metoda atlama devam `for` blok. Bu, tüm 1000 yineleme boyunca adım uzun süreceğini unutmayın.

 **Koşullu kesme noktası ayarlayın.** Kod penceresinin sol kanalda satırın sağ `x += i;` seçip **koşul**. Seçin **koşul** onay kutusunu işaretleyin ve ardından yazın `i == 500;` metin kutusuna. Seçin **true** seçenek ve **Tamam**. Kesme noktası 500th yinelemesini değerinde kontrol etmenize olanak `for` döngü.

 ![Kesme noktası koşulu iletişim kutusu](../debugger/media/dbg-basics-breakpointcondition.png "DBG_Basics_BreakpointCondition")

 Koşullu kesme noktası simgesi, beyaz arası tarafından tespit edebilirsiniz.

 ![Koşullu kesme noktası](../debugger/media/dbg-basics-conditionalbreakpoint.png "DBG_Basics_ConditionalBreakpoint")

 **Kesme noktasına kadar çalıştırın.** Hata ayıklama menüsünden devam'ı seçin (klavye: F5). Yerel öğeler penceresinde onaylayın geçerli değerini `i` 500'dür. Unutmayın değişkeni `s` penceresinden daha uzunsa ve tek bir satır olarak gösterilir.

 **Görsel bir string değişkeni.** Büyüteç simgesini **değer** sütununun `s`.

 Metin Görselleştirici penceresi görünür ve dize değeri çok satırlı dize olarak sunulur.

 **İmlece kadar çalıştırma.** Satırın sağ `methodTrack += "->Example3";` seçip **imlece kadar Çalıştır** (klavye: satır; imleci taşıma CTRL + F10). Hata ayıklayıcı, döngü yinelemesi tamamlar ve ardından satırında yürütmeyi askıya alır.

 **Hata ayıklamayı durdurun.** Hata Ayıklama menüsünde, hata ayıklamayı Durdur seçin (klavye: Shift + F5). Bu, hata ayıklama oturumunuzu sonlandırır.

##  <a name="BKMK_EditContinueRecoverExceptions"></a> Düzenle ve devam etmek için bir özel durumdan kurtarma
 Visual Studio hata ayıklayıcısı koda böldüğünüzde bazı durumlarda, değişkenlerin değerini ve hatta deyimlerinin logics değiştirme olanağına sahiptir. Bu işlev, düzen olarak adlandırılır ve devam edin.

 Düzenle ve devam et sırasında bir özel durum böldüğünüzde özellikle kullanışlı olabilir. Özel durumdan kaçınmak için bir uzun ve ilgili yordam hata ayıklamayı yeniden başlatmak ve durdurmak zorunda kalmak yerine, "hemen özel durum oluşmadan önceki yürütme noktasına taşımak için özel durumu geriye doğru İzle" ve sorunlu değişken veya deyimi değiştirin ve Geçerli hata ayıklama oturumu ile bir özel durum oluşturmaz durumda devam edin.

 Düzenle ve devam etmek çok çeşitli durumlarda kullanabilirsiniz ancak düzenleme desteği ve devam et yoksa belirli koşulları koşullar geçerli durumu program yığının programlama dili bağımlı olduğundan belirtmeyi zor olan ve Durum işlem bozan olmadan değiştirme olanağı hata ayıklayıcının. Bir düzen değişiklik desteklenip desteklenmediğini belirlemek için en iyi yolu denemektir sağlamaktır; hata ayıklayıcı, hemen değişiklik desteklenmemesi durumunda'ı bilmenizi sağlar.

### <a name="example-4"></a>Örnek 4
 Bu örnekte, bir özel durum hata ayıklayıcıyı çalıştırmak, özel durum geri, yöntemin mantığını düzeltin ve yöntemini yürütmenin devam edebilmesi için sonra bir değişkenin değerini değiştirin.

 **MainPage oluşturucuda örnek4 yöntemi çağırın.** MainPage() Oluşturucusu düzenleyebilir ve aşağıdaki satırı değiştirin `methodTrack = String.Empty;` satırı ile `Example4();`.

 ![Tanıtım örnek4 çağırın](../debugger/media/dbg-basics-callexample4.png "DBG_Basics_CallExample4")

 **Özel durum çalıştırın.** Hata ayıklama oturumu başlatın **hata ayıklamayı Başlat** üzerinde **hata ayıklama** menü (klavye: F5). Yeniden yürütme sürdürmek için F5 tuşuna basın. Hata ayıklayıcı özel durumda örnek4 yönteminin yürütmeyi askıya alır ve bir özel durum iletişim kutusunu görüntüler.

 ![Özel durum iletişim kutusunda](../debugger/media/dbg-basics-exceptiondlg.png "DBG_Basics_ExceptionDlg")

 **Program mantığını değiştirin.** Hata olduğunu açıktır `if` koşul: değerini `x` ne zaman değiştirilmelidir `x` 0 değerine eşittir; belirtilmediğinde `x` sıfıra eşit değil. Seçin **sonu** yöntemin mantığını düzeltmek için. Satır düzenlemeye çalıştığınızda, başka bir iletişim kutusu görüntülenir.

 ![Düzenle ve devam et iletişim kutusu](../debugger/media/dbg-basics-editandcontinuedlg.png "DBG_Basics_EditAndContinueDlg")

 Seçin **Düzenle** değiştirip ardından satır `if (x != 0)` için `if (x == 0)`. Hata ayıklayıcı kaynak dosyasının program mantığına değişiklikler devam ettirir.

 **Değişken değerini değiştirin.** Değerini incelemek `x` bir veri ipucunda veya yerel öğeler penceresinde. Hala 0 (sıfır). Özgün özel duruma neden deyimi çalıştırmayı denerseniz, bu yalnızca yeniden oluşturmaz. Değerini değiştirebilir `x`. Yerel öğeler penceresinde, **değer** sütununun **x** satır. Değer 0 ile 1 olarak değiştirin.

 ![Yerel öğeler penceresinde bir değeri düzenledikten](../debugger/media/dbg-basics-editandcontinuefix.png "DBG_Basics_EditAndContinueFix")

 Daha önce bir özel durum oluşturdu. deyimi adımlamak için F11 tuşuna basın. Satır bir hata çalışacağını unutmayın. F11 yeniden seçin.

 **Hata ayıklamayı durdurun.** Üzerinde **hata ayıklama** menüsünde seçin **hata ayıklamayı Durdur** (klavye: Shift + F5). Bu, hata ayıklama oturumunuzu sonlandırır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Hata ayıklama oturumu başlatma (VB, C#, C++ ve XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) [tetikleyici askıya alma, sürdürme ve arka plan olaylarını Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [uygulamaları Visual Studio'da hata ayıklama](../debugger/debug-store-apps-in-visual-studio.md)
