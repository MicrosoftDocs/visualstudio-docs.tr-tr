---
title: Hata ayıklayıcısı koda gitmek | Microsoft Docs
ms.custom: seodec18
ms.date: 11/12/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f951732704b178c2726d60f20fc4fedcbd4cde90
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068279"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısı ile kodda gidin

Visual Studio hata ayıklayıcı bir uygulamanın durumunu inceleyebilir ve kendi yürütme akışını göstermek için kod gezinmenize yardımcı olabilir. Hızlı bir şekilde incelemek istediğiniz kodu almak için klavye kısayolları, hata ayıklama komutları, kesme noktaları ve diğer özellikleri kullanabilirsiniz. Hata ayıklayıcı Gezinti komutlarını ve kısayolları konusunda daha hızlı ve kolay bulmak ve uygulama sorunları gidermek yapar.  Bu, kodda hata ayıklamak için girişimde ilk kez ise, okumak isteyebilirsiniz [düzeltme hataları daha iyi yazarak C# kod](../debugger/write-better-code-with-visual-studio.md) ve [yeni başlayanlar için hata ayıklama](../debugger/debugging-absolute-beginners.md) bu makalede geçmeden önce.
  
## <a name="basic-debugging"></a>Temel hata ayıklama  

Hata ayıklayıcısı ekli uygulamanızı başlatmak için basın **F5**seçin **hata ayıklama** > **hata ayıklamayı Başlat**, veya Visual Studio araç çubuğunda yeşil oku seçin.  
  
 ![DBG&#95;Temelleri&#95;Başlat&#95;hata ayıklama](../debugger/media/dbg_basics_start_debugging.png "DBG_Basics_Start_Debugging")  
  
Hata ayıklarken, sonraki yürüten bir kod satırı sarı bir Vurgu gösterir.  
  
 ![DBG&#95;Temelleri&#95;sonu&#95;modu](../debugger/media/dbg_basics_break_mode.png "kesme modu")  
  
En çok hata ayıklayıcı, windows gibi **modülleri** ve **Watch** windows, yalnızca hata ayıklayıcı çalışırken kullanılabilir. Bazı değişken değerleri görüntüleme gibi özellikler, hata ayıklayıcı **Yereller** penceresi veya ifadeleri değerlendirme **Watch** penceresinde, hata ayıklayıcı bir kesme noktasında olarak da bilinir, yalnızca duraklatılmış durumdayken kullanılabilir *Kesme moduna*. 

Kesme modunda İşlevler, değişkenler, uygulama yürütmesi askıya alınır ve nesneler bellekte kalır. Öğelerin konumlarını ve durumlarını ihlalleri ya da hatalar arayabilirsiniz inceleyebilirsiniz. Bazı proje türleri için kesme modundayken uygulamada ayarlamalar yapabilirsiniz. Bu özellikleri gösteren bir video için bkz [hata ayıklayıcı ile çalışmaya başlama](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6).

Kaynak veya sembol yok kodda kesme durumunda (*.pdb*) hata ayıklayıcı yüklenen dosyaları, görüntüler bir **kaynak dosyaları bulunamadı** veya **semboller bulunamadı** yardımcı olabilecek sayfası bulun ve dosyaları yükleyin. Bkz: [belirtin, sembol (.pdb) ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Sembol veya kaynak dosyalarına yüklenemiyorsa, yine de derleme ayıklayabilirsiniz **ayrıştırılmış kodu** penceresi. 

Her zaman başında bir uygulamayı yeniden başlatarak hata ayıklamayı Başlat gerekmez. Tuşlarına da basabilirsiniz **F11** için [kod içine Adımlama](#BKMK_Step_into__over__or_out_of_the_code), basın **F10** için [kodu Adımlama](#BKMK_Step_over_Step_out), veya [belirli bir konuma yeniden çalıştırın veya işlev](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All).    

##  <a name="step-through-code"></a>Kodunuz içinde adım adım

Hata ayıklayıcı adım komutları, uygulama durumunu incelemek veya kendi yürütme akışı hakkında daha fazla bilgi edinin yardımcı olur. 

Giriş noktası uygulamanızda bulmanız gerekiyorsa, başlayan **F10** veya **F11**.  

### <a name="BKMK_Step_into__over__or_out_of_the_code"></a> Kodu satır satır içine adımla  

Kod veya hata ayıklama sırasında ifade her satırda durdurmak için kullanın **hata ayıklama** > **içine adımla**, veya basın **F11**.  

Kod deyimlerini, fiziksel satırlar hata ayıklayıcı adımları. Örneğin, bir `if` yan tümcesi bir satıra yazılabilir:  
  
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

Ancak, bu satır adımladığınızda hata ayıklayıcısı bir adım ve sonucu başka bir koşulu değerlendirir. Önceki örnekte koşul true'dur.  
  
Bir iç içe geçmiş işlev çağrısında **içine adımla** en derin yuvalanmış işlevi adımlar. Örneğin kullanırsanız **içine adımla** gibi bir çağrıda `Func1(Func2())`, hata ayıklayıcı adımları işleve `Func2`.  

>[!TIP]
>Her kod satırının yürütürken, değerlerine bakın veya değişkenleri gelerek [Yereller](autos-and-locals-windows.md) ve [Watch](watch-and-quickwatch-windows.md) değiştirme değerleri izlemek için windows. Ayrıca, işlevlere adımlamayla girerken çağrı yığınını görsel olarak da izleyebilirsiniz. Bkz: [hata ayıklarken çağrı yığınında yöntemler harita](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md). 

###  <a name="BKMK_Step_over_Step_out"></a> Kod içinde gezinebilmek ve bazı işlevler atla  

Bir işlev hakkında hata ayıklama sırasında önemsemez veya biliyorsanız gibi çalışır, iyi sınanmış kitaplık kodu. Kod üzerinden geçmek için aşağıdaki komutları kullanabilirsiniz. İşlevler yine de yürütme, ancak bunlar üzerinde hata ayıklayıcı atlar.  
  
|Klavye komutu|Menü komutu hata ayıklama|Açıklama|  
|----------------------|------------------|-----------------|  
|**F10**|**Üzerinden adımla**|Geçerli satır bir işlev çağrısı içeriyorsa, **Step Over** kodu çalıştırır ve ardından kod ilk satırında, çağrılan işlev döndürdükten sonra yürütmeyi askıya alır.|  
|**Shift**+**F11**|**Dışına adımla**|**Step Out** kod çalışmaya devam eder ve geçerli işlevi döndüğünde yürütmeyi askıya alır. Hata ayıklayıcı geçerli işlevin atlar.|  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Belirli bir konuma veya işleve kadar çalıştırma  

İncelemek istediğiniz hangi kodun tam olarak biliyorsanız, doğrudan bir belirli bir konuma veya işleve kadar çalıştırma tercih edebilirsiniz veya hata ayıklamaya başlamak istediğiniz bildirin.  
  
### <a name="run-to-a-breakpoint-in-code"></a>Kodda bir kesme noktası için çalıştırın  
  
Kodunuza basit bir kesme noktası ayarlamak için yürütmeyi askıya almak istediğiniz kod satırının yanındaki en sol kenar boşluğu tıklayın. Çizgi ve ENTER tuşuna de seçebilirsiniz **F9**seçin **hata ayıklama** > **iki durumlu kesme noktası**, veya sağ tıklayıp **kesmenoktası**  >  **Kesme noktası Ekle**. Kesme noktası sol kenar boşluğunda kod satırının yanında kırmızı bir nokta olarak görünür. Yalnızca satır yürütülmeden önce hata ayıklayıcı yürütmeyi askıya alır.
  
![Bir kesme noktası ayarlamak](../debugger/media/dbg_basics_setbreakpoint.png "bir kesme noktası ayarlayın")  
  
Visual Studio'daki kesme noktaları, koşullu kesme noktaları ve izleme noktaları gibi ek işlevler zengin bir özellik kümesi sağlar. Ayrıntılar için bkz [kesme noktalarını kullanma](../debugger/using-breakpoints.md).  
  
### <a name="run-to-a-function-breakpoint"></a>Bir işlev kesme noktasına Git  

Belirli bir işleve ulaşıncaya kadar çalıştırılacak hata ayıklayıcı söyleyebilirsiniz. İşlevi adıyla belirtebilir veya çağrı yığınından seçebilirsiniz.  
  
**Adıyla bir işlev kesme noktasını belirtmek için**

1. Seçin **hata ayıklama** > **yeni kesme noktası** > **işlev kesme noktası**
   
1. İçinde **yeni işlev kesme noktası** iletişim kutusunda, işlev adını yazın ve dili seçin.
   
   ![Yeni işlev kesme noktası iletişim kutusu](../debugger/media/dbg_execution_newbreakpoint.png "yeni işlev kesme noktası")  
   
1. Seçin **Tamam**. 

İşlev aşırı yüklüyse ya da birden fazla ad alanında, istediğiniz seçeneği tercih edebilir, **kesme noktaları** penceresi.  

![İşlev kesme noktaları aşırı](../debugger/media/dbg_execution_overloadedbreakpoints.png "aşırı yüklenmiş işlev kesme noktaları")  
  
**Bir işlev kesme noktası çağrı yığınından seçmek için** 
  
1. Hata ayıklama sırasında açın **çağrı yığını** penceresini seçerek **hata ayıklama** > **Windows** > **çağrı yığını**. 
   
1. İçinde **çağrı yığını** penceresindeki bir işlevi sağ tıklayıp **imlece**, veya basın **Ctrl**+**F10**.  

Çağrı yığınını görsel olarak izlemek için bkz: [hata ayıklarken çağrı yığınında yöntemler harita](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
### <a name="run-to-a-cursor-location"></a>İmleç konumuna çalıştırın  

İmleç konumu, kaynak kodu çalıştırmak için veya **çağrı yığını** penceresinde kesme, sağ tıklayıp istediğiniz satırı seçin **imlece**, veya basın **Ctrl** + **F10**. Seçme **imlece** geçici bir kesme noktası ayarlamak gibi.

### <a name="run-to-click"></a>Tıklanan Satıra Kadar Çalıştır 

Hata ayıklayıcısında duraklatıldıktan karşın, bir kaynak kodu deyiminde üzerine gelerek veya **ayrıştırılmış kodu** penceresi ve select **yürütme işlemini burada Çalıştır** yeşil ok simgesi. Kullanarak **tıklanan satıra kadar Çalıştır** geçici bir kesme noktası ayarlama gereğini ortadan kaldırır.

![Tıklanan satıra kadar Çalıştır](../debugger/media/dbg-run-to-click.png "tıklanan satıra kadar Çalıştır") 

> [!NOTE]
> **Tıklanan satıra kadar Çalıştır** de: [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].
  
### <a name="manually-break-into-code"></a>El ile break into code  
  
Çalışan bir uygulamanın kod kullanılabilir bir sonraki satırda kesmek için seçin **hata ayıklama** > **tümünü Kes**, veya basın **Ctrl**+**Alt**  + **Sonu**. 
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a> Yürütme akışı değiştirmek için işaretçiyi taşıyın  

Hata Ayıklayıcı duraklatılmış durumdayken, kaynak kodunun kenar boşluğundaki bir sarı ok veya **ayrıştırılmış kodu** penceresi yürütülecek sonraki deyimin konumunu işaretler. Bu Ok ucunu taşıyarak yürütülecek sonraki deyimi değiştirebilirsiniz. Kodun bir kısmını atlayın veya önceki bir satıra geri dönebilirsiniz. İşaretçiyi taşıma, bilinen bir hata içeren kod bölümünü atlama gibi durumlar için kullanışlıdır.  

 ![İşaretçiyi](../debugger/media/dbg_basics_example3.gif "işaretçiyi")
  
Yürütülecek sonraki deyimi değiştirmek için hata ayıklayıcının kesme modunda olması gerekir. Kaynak kodunda veya **ayrıştırılmış kodu** penceresinde, sarı ok başını farklı bir satıra sürükleyin veya sonraki seferde çalıştırmak ve seçmek için satırın sağ **sonraki deyimi Ayarla**. 

Program sayacının doğrudan yeni konuma ve yönergeler için noktaları yürütülen olmayan eski ve yeni yürütme arasında atlar. Ancak, yürütme noktasını geriye taşırsanız, müdahaleci talimatlar geri değildir.  

>[!CAUTION]
>- Sonraki deyimi başka bir işleve ya da kapsama taşınması genelde bir çalışma zamanı hatası ya da özel durum neden Çağrı Yığını Bozulması ile sonuçlanır. Sonraki deyimi başka bir kapsama geçmeden çalışırsanız, hata ayıklayıcı bir uyarı ile bir iletişim kutusu açılır ve işlemi iptal etmek için bir şans verir. 
>- Visual Basic'te sonraki deyimi başka bir kapsam ya da işleve taşıyamazsınız.  
>- Çalışma zamanı kontrolleriniz etkinse, yerel C++'da, sonraki deyimi ayarlamak bir özel yürütme yöntemin sonuna ulaştığında durum neden olabilir.  
>- Düzenle ve devam et etkinken, **sonraki deyimi Ayarla** , Düzenle ve devam et düzenlemeler yaptıysanız başarısız hemen yeniden eşleyemeyeceği. Bir catch bloğu içinde kod düzenlediyseniz, örneğin, ortaya çıkabilir. Bu durumda, bir hata iletisi işlemi desteklenmiyor söyler.  
>- Yönetilen kodda, sonraki deyimi taşıyamazsınız:  
>   - Sonraki deyimi başka bir yöntem geçerli deyimden bileşenidir.  
>   - Hata ayıklama Just-ın-Time tarafından başlatılmışsa hata ayıklama.  
>   - Çağrı yığını geriye doğru izleme işlemi devam ediyor.  
>   - Bir System.StackOverflowException ya da System.Threading.ThreadAbortException özel durumu oluşturuldu.  
  
## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Kullanıcı dışı kod hata ayıklama  

Adlı bir ayarı etkinleştirerek yalnızca uygulama kodunuzda hata ayıklamak hata ayıklayıcı varsayılan olarak, çalıştığında *yalnızca kendi kodum*. Bu özellik, farklı proje türleri ve diller için nasıl çalıştığını ve nasıl özelleştirebileceğiniz hakkında daha fazla ayrıntı için [yalnızca kendi kodum](../debugger/just-my-code.md). 

Hata ayıklama sırasında Framework kodu, üçüncü taraf kitaplık kodu veya sistem çağrıları aramak için Just My Code'u devre dışı bırakabilirsiniz. İçinde **Araçları** (veya **hata ayıklama**) > **seçenekleri** > **hata ayıklama**temizleyin **yalnızca benim kodumu etkinleştir** onay kutusu. Just My Code'u devre dışı bırakıldığında, kullanıcı dışı kod hata ayıklayıcı pencerelerinde görünür ve hata ayıklayıcının kullanıcı olmayan kodun içine geçebilirsiniz.  

> [!NOTE]
> Yalnızca benim kodum cihaz projeleri için desteklenmiyor.  
  
### <a name="debug-system-code"></a>Sistem kodu hatalarını ayıklama

Microsoft Sistem kodu için hata ayıklama yüklendi ve Just My Code'u devre dışı, başka herhangi bir çağrıda gibi bir Sistem çağrısına geçebilirsiniz.  
  
Microsoft simgeleri yüklemek için bkz: [sembol konumlarını yapılandırma ve yükleme seçenekleri](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).  
  
**Belirli bir sistem bileşeninin sembolleri için:**

1. Hata ayıklarken, açık **modülleri** penceresini seçerek **hata ayıklama** > **Windows** > **modülleri**, ya basarak **Ctrl**+**Alt**+**U**.  
  
1. İçinde **modülleri** penceresinde, öğrenebilirsiniz hangi modüllerinizin yüklenmiş semboller **sembol durumu** sütun. Sembolleri ve istediğiniz modülü sağ **yük sembolleri**.  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Yönetilen kod içindeki özellikler ve işleçlerin içine adımla  
 Varsayılan olarak hata ayıklama adımlarında yönetilen kod içindeki özellikler ve işleçlerin üzerinden. Çoğu durumda, bunu bir daha iyi hata ayıklama deneyimi sunar. Özellikleri veya işleçleri adımlamak için seçin **hata ayıklama** > **seçenekleri**. Üzerinde **hata ayıklama** > **genel** sayfasında, NET **özellikleri ve işleçleri (sadece yönetilen) üzerinden adımla** onay kutusu.

## <a name="see-also"></a>Ayrıca bkz.
 [Hata ayıklıyor?](../debugger/what-is-debugging.md)  
 [Daha iyi yazarak hataları düzeltmek C# kod](../debugger/write-better-code-with-visual-studio.md)  
 [Hata ayıklama ilk bakış](../debugger/debugger-feature-tour.md) 
