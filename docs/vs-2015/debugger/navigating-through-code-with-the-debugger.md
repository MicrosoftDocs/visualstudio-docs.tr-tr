---
title: Hata ayıklayıcısı ile kodlarda gezinme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43155bbd4236ea34d67058443e8814f7ccf00b1f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750574"
---
# <a name="navigating-through-code-with-the-debugger"></a>Hata Ayıklayıcısı ile Kodlarda gezinme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hata ayıklayıcısı koda gitmek için komutlar ve kısayolları hakkında bilgi edinin ve daha hızlı ve bulun ve uygulamanızdaki sorunları gidermek kolay hale getirir. Hata ayıklayıcı kodda gezinme, ancak yapabilecekleriniz [uygulamanızın durumunu incelemek](https://msdn.microsoft.com/library/mt243867.aspx#BKMK_Inspect_Variables) veya kendi yürütme akışı hakkında daha fazla bilgi edinin.  
  
## <a name="start-debugging"></a>Hata Ayıklamayı Başlat  
 Genellikle, kullanarak bir hata ayıklama oturumu başlatmak **F5** (**hata ayıklama** / **hata ayıklamayı Başlat**). Bu komut, uygulamanızı hata ayıklayıcısı ekli başlatır.  
  
 Yeşil ok, aynı zamanda hata ayıklayıcıyı başlatır (aynı **F5**).  
  
 ![DBG&#95;Temelleri&#95;Başlat&#95;hata ayıklama](../debugger/media/dbg-basics-start-debugging.png "DBG_Basics_Start_Debugging")  
  
 Hata ayıklayıcısı ekli uygulamanın başlatmak için birkaç yolu şunlardır **F11** ([kod içine Adımlama](#BKMK_Step_into__over__or_out_of_the_code)), **F10** ([kodu Adımlama](#BKMK_Step_over_Step_out)), veya kullanarak **imlece kadar Çalıştır**.  Ne Bu seçenekler hakkında bilgi için bu konudaki diğer bölümlere bakın.  
  
 Hata ayıklama seçtiğinizde sarı bir çizgi sonraki yürütülen kod gösterilir.  
  
 ![DBG&#95;Temelleri&#95;sonu&#95;modu](../debugger/media/dbg-basics-break-mode.png "DBG_Basics_Break_Mode")  
  
 Hata ayıklarken, komutları gibi arasında geçiş yapabilirsiniz **F5**, **F11** ve hızlıca bakmak için istediğiniz kodu almak için (örneğin, kesme noktaları) Bu konuda açıklanan diğer özelliklerini kullanabilirsiniz.  
  
 Hata ayıklayıcı yalnızca duraklatılmış durumdayken değişken değerleri Yereller penceresinde görüntüleme ya da ifadeleri İzleme penceresinde değerlendirme gibi çoğu hata ayıklama özellikleri kullanılabilir (olarak da adlandırılan *Kesme moduna*). Hata ayıklayıcı duraklatıldığı zaman, uygulama durumunu değişkenler, İşlevler sırasında askıya alındı ve nesneler bellekte kalır. Kesme modundayken, öğelerin konumlarını ve durumlarını ihlalleri ya da hatalar arayabilirsiniz inceleyebilirsiniz. Bazı proje türleri için kesme modundayken uygulamada ayarlamalar yapabilirsiniz.  
  
##  <a name="BKMK_Step_into__over__or_out_of_the_code"></a> Satır, kodda ilerleyebilmeniz  
 Hata ayıklarken kod (her deyim) her bir satırda durdurmak için kullanın **F11** klavye kısayolu (veya **hata ayıklama** / **içine adımla** menüsünde).  
  
> [!TIP]
>  Her kod satırının yürütürken, değerlerine bakın veya değişkenleri gelerek [Yereller](../debugger/autos-and-locals-windows.md) ve [Watch](../debugger/autos-and-locals-windows.md) değerlerini değiştirmek izlemek için windows.  
  
 Davranışı hakkında bazı Ayrıntılar **içine adımla**:  
  
- Bir iç içe geçmiş işlev çağrısında **içine adımla** en derin yuvalanmış işlevi adımlar. Kullanırsanız **içine adımla** gibi bir çağrıda `Func1(Func2())`, hata ayıklayıcı adımları işleve `Func2`.  
  
- Hata ayıklayıcı gerçekte fiziksel satırlar yerine kod deyimlerini adımlar. Örneğin bir `if` yan tümcesi bir satıra yazılabilir:  
  
  ```csharp  
  int x = 42;  
  string s = "Not answered";  
  if( int x == 42) s = "Answered!";  
  ```  
  
  ```vb  
  Dim x As Integer = 42  
  Dim s As String = "Not answered"  
  If x = 42 Then s = "Answered!"  
  ```  
  
   Bu satır adımladığınızda hata ayıklayıcı koşulu bir adım ve başka bir sonucu olarak değerlendirir. (Bu örnekte, koşul true olduğu).  
  
  İşlevlere adımlamayla girerken çağrı yığınını görsel olarak izlemek için bkz: [hata ayıklarken çağrı yığınında yöntemler harita](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
##  <a name="BKMK_Step_over_Step_out"></a> İşlevleri atlanıyor kodda adım adım  
 Hata ayıklayıcıda kod çalıştırma, genellikle, belirli bir işlevde ne olacağına bakalım gerekmez fark edeceksiniz (Bu konuda umursamaz veya biliyorsanız gibi çalışır, iyi sınanmış kitaplık kodu). Kod atlamak için bu komutları kullanmak (işlevler yine de, yürütme, ancak bunlar üzerinde hata ayıklayıcı atlar).  
  
|Klavye komutu|Menü komutu|Açıklama|  
|----------------------|------------------|-----------------|  
|**F10**|**Üzerinden adımla**|Geçerli satır bir işlev çağrısı içeriyorsa, **Step Over** kodu çalıştırır daha sonra ilk kod satırında, çağrılan işlev döndürdükten sonra yürütmeyi askıya alır.|  
|**Shift+F11**|**Dışına adımla**|**Step Out** kod çalışmaya devam eder ve geçerli işlev (hata ayıklayıcı atlar geçerli işlev aracılığıyla) döndüğünde yürütmeyi askıya alır.|  
  
> [!TIP]
>  Giriş noktası uygulamanızda bulmanız gerekiyorsa, başlayan **F10** veya **F11**. Uygulama durumunu incelemek veya çalışırken, yürütme akışı hakkında daha fazla bilgi şu komutları çoğunlukla yararlı olur.  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Belirli bir konuma veya işleve kadar çalıştırma  
 Tam olarak hangi kodun incelemek istediğiniz bildiğinizde genellikle kodda hata ayıklama, tercih edilen yöntem, bu yöntemleri yararlıdır ve hata ayıklamaya başlamak istediğiniz en az bildiğiniz.  
  
-   **Kod içinde kesme noktalarını belirleyin**  
  
     Kodunuza basit bir kesme noktası ayarlamak için kaynak dosyasını Visual Studio düzenleyicisinde açın. Yürütmeyi askıya almak ve içerik menüsünü görmek ve kod penceresinde sağ istediğiniz imleci kod satırına ayarlayın **kesme noktası / kesme noktası Ekle** (veya basın **F9**). Satırı yürütülmeden önce hata ayıklayıcı yürütme sağ askıya alır.  
  
     ![Bir kesme noktası ayarlamak](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Visual Studio'daki kesme noktaları, koşullu kesme noktaları ve izleme noktaları gibi ek işlevler zengin bir özellik kümesi sağlar. Bkz: [kesme noktalarını kullanma](../debugger/using-breakpoints.md).  
  
-   **İmleç konumuna çalıştırın**  
  
     İmlecin konumuna kadar yürütmek için bir kaynak penceresinde kod yürütülebilir bir satırda imleci yerleştirin. Düzenleyicinin bağlam menüsünden (Düzenleyicisi'nde sağ tıklama), **imlece kadar Çalıştır**. Geçici bir kesme noktası ayarlama gibi budur.  
  
-   **El ile break into code**  
  
     Çalışan bir uygulamada kod kullanılabilen bir sonraki satıra içine kesmek için seçin **hata ayıklama**, **tümünü Kes** (klavye: **Ctrl + Alt + Break**).  
  
     Kesme karşılık gelen kaynak kod yürütülürken veya sembol (.pdb) dosyaları), hata ayıklayıcı görüntüler bir **kaynak dosyaları bulunamadı** veya **semboller bulunamadı** yardımcı olabilecek sayfasında uygun bulun dosyaları. Bkz: [sembol (.pdb) belirtin ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Destekleyici dosyalara erişemiyorsanız, ayrıştırma penceresinde derleme yönergeleri yine de hata ayıklaması yapabilirsiniz.  
  
-   **Çağrı yığınındaki bir işleve çalıştırın**  
  
     İçinde **çağrı yığını** (hata ayıklama sırasında kullanılabilir) penceresinde işlevi seçin, sağ tıklayın ve seçin **imlece kadar Çalıştır**. Çağrı yığınını görsel olarak izlemek için bkz: [hata ayıklarken çağrı yığınında yöntemler harita](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
-   **Belirtilen ada göre bir işleve çalıştırın**  
  
     Belirli bir işleve ulaşıncaya kadar uygulamanızı çalıştırmak için hata ayıklayıcı söyleyebilirsiniz. İşlevi adıyla belirtebilir veya çağrı yığınından seçebilirsiniz.  
  
     Ada göre bir işlev belirtmek için **hata ayıklama**, **yeni kesme noktası**, **sonu işlevi**, ardından işlevin adını ve tanımlayıcı diğer bilgilerini girin.  
  
     ![Yeni kesme noktası iletişim kutusu](../debugger/media/dbg-execution-newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     İşlev aşırı yüklüyse ya da birden çok ad alanındaki, istediğiniz işlevleri seçebilirsiniz **kesme noktalarını Seç** iletişim kutusu.  
  
     ![Kesme noktaları iletişim kutusu seç](../debugger/media/dbg-execution-overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a> Yürütme akışı değiştirmek için işaretçiyi taşıyın  
 Hata Ayıklayıcı duraklatılmış durumdayken, kodda yürütülecek sonraki deyimi ayarlamak için yönerge işaretçisini taşıyabilirsiniz. Kaynak veya Ayrıştırılmış kod penceresinin kenar boşluğundaki bir sarı ok yürütülecek sonraki deyimin konumunu işaret eder. Bu Ok ucunu taşıyarak kodun bir kısmını atlayın veya önceden yürütülmüş bir satıra geri dönebilirsiniz. Bu bilinen bir hata içeren kod bölümünü atlama gibi durumlar için kullanabilirsiniz.  
  
 ![Örnek2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")  
  
 Yürütülecek sonraki deyimi ayarlamak için aşağıdaki yordamlardan birini kullanın:  
  
-   Bir kaynak penceresinde, sarı ok başını, aynı dosya içinde sonraki deyimi ayarlamak için istediğiniz bir konuma sürükleyin.  
  
-   Bir kaynak penceresinde, imleci sonraki yürütme, sağ tıklayın ve istediğiniz satırda ayarlamak **sonraki deyimi Ayarla**.  
  
-   Ayrıştırma penceresinde, imleci sağ tıklayın, sonraki yürütmek istediğiniz derleme talimatına bir seçip **sonraki deyimi Ayarla**.  
  
> [!CAUTION]
>  Sonraki deyimin ayarlanması program sayacının doğrudan yeni konuma atlamasına neden olur. Bu komutu dikkatli kullanın:  
> 
> - Eski ve yeni yürütme noktaları arasındaki talimatlar hariç tutulur.  
>   -   Yürütme noktasını geriye taşırsanız, müdahaleci talimatlar geri alınmaz.  
>   -   Sonraki deyimi başka bir işleve ya da kapsama taşınması genelde bir çalışma zamanı hatası ya da özel durum neden Çağrı Yığını Bozulması ile sonuçlanır. Sonraki deyimi başka bir kapsama geçmeden çalışırsanız, hata ayıklayıcı bir uyarı ile bir iletişim kutusu açılır ve işlemi iptal etmek için bir şans verir. Visual Basic'te sonraki deyimi başka bir kapsam ya da işleve taşıyamazsınız.  
>   -   Çalışma zamanı kontrolleriniz etkinse, yerel C++'da, sonraki deyimi ayarlamak bir özel yürütme yöntemin sonuna ulaştığında durum neden olabilir.  
>   -   Düzenle ve devam et etkinken, **sonraki deyimi Ayarla** , Düzenle ve devam et düzenlemeler yaptıysanız başarısız hemen yeniden eşleyemeyeceği. Bir catch bloğu içinde kod düzenlediyseniz, örneğin, ortaya çıkabilir. Bu durumda, bir işlem desteklenen söyleyen bir hata iletisi görürsünüz.  
> 
> [!NOTE]
>  Yönetilen kodda aşağıdaki koşullarda sonraki deyimi taşıyamazsınız:  
> 
> - Sonraki deyimi başka bir yöntem geçerli deyimden bileşenidir.  
>   -   Hata ayıklama başlatıldı Just-ın-Time kullanarak hata ayıklama.  
>   -   Geriye doğru bir callstack sürüyor.  
>   -   Bir System.StackOverflowException ya da System.Threading.ThreadAbortException özel durumu oluşturuldu.  
  
 Uygulamanız etkin olarak çalışırken sonraki deyimi ayarlayamazsınız. Sonraki deyimi ayarlamak için hata ayıklayıcının kesme modunda olması gerekir.  
  
## <a name="step-into-non-user-code"></a>Kullanıcı olmayan kod adımla  
 Varsayılan olarak, hata ayıklayıcı, hata ayıklayıcı çağrılan ayarı tarafından belirlenen hata ayıklarken, yalnızca, uygulama kodunuz göstermek çalışır *yalnızca kendi kodum*. (Bkz [yalnızca kendi kodum](../debugger/just-my-code.md) davranışını nasıl özelleştiririm ve bu farklı proje türleri ve diller için nasıl çalıştığını görmek için.) Ancak, bazen, hata ayıklama sırasında framework kodu, üçüncü taraf kitaplık kodu veya çağrıları bakmak isteyebilirsiniz işletim sistemine (sistem çağrıları).  
  
 Yalnızca benim kodum giderek kapatabilirsiniz **Araçları** / **seçenekleri** / **hata ayıklama** temizleyin **yalnızca benim kodumu etkinleştir** onay kutusu.  
  
 Just My Code'u devre dışı bırakıldığında, hata ayıklayıcı kullanıcı olmayan kod içinde adım ve kullanıcı olmayan kod hata ayıklayıcı pencerelerinde görünür.  
  
> [!NOTE]
>  Yalnızca benim kodum cihaz projeleri için desteklenmiyor.  
  
 **Sistem çağrılarına adımlamayla girme**  
  
 Başka herhangi bir çağrıda gibi sistem kodu için hata ayıklama sembolleri yüklediniz ve yalnızca kendi kodum etkin değil, bir Sistem çağrısına geçebilirsiniz.  
  
 Microsoft sembol dosyalarına erişmek için bkz: [yerel makinenizde olmayan sembol dosyalarını bulmak için Sembol sunucularını kullanın](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) içinde [belirtin sembol (.pdb) ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) konu.  
  
 Hata ayıklarken belirli bir sistem bileşeninin sembolleri için:  
  
1.  Modüller penceresini açın (klavye: **Ctrl + Alt + U**).  
  
2.  Sembolleri istediğiniz modülü seçin.  
  
     Bakarak hangi modüllerin yüklü simgeleri sahip söyleyebilirsiniz **sembol durumu** sütun.  
  
3.  Seçin **sembolleri Yükle** bağlam menüsünde.  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Yönetilen kod içindeki özellikler ve işleçlerin içine adımla  
 Varsayılan olarak hata ayıklama adımlarında yönetilen kod içindeki özellikler ve işleçlerin üzerinden. Çoğu durumda, bunu bir daha iyi hata ayıklama deneyimi sunar. Özellikleri veya işleçleri adımlamak için seçin **hata ayıklama** / **seçenekleri**. Üzerinde **hata ayıklama** / **genel** sayfasında, NET **özellikleri ve işleçleri (sadece yönetilen) üzerinden adımla** onay kutusu





