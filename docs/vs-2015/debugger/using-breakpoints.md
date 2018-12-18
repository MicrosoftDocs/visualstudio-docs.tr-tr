---
title: Kesme noktalarını kullanma | Microsoft Docs
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
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
- vs.debug.breakpt.choose
- vs.debug.breakpt.location.address
- vs.debug.breakpt.constraints
- vs.debug.breakpoints.delete
- vs.debug.breakpt.location.data
- vc.breakpoints
- vs.debug.breakpt.condition
- vs.debug.breakpt.location.function
- vs.debug.breakpoints
- vs.debug.menu.insert
- vs.debug.filenames
- vs.debug.breakpt.action
- vs.debug.sourcewin.insert
- vs.debug.address
- vs.debug.data
- vs.debug.func
- vs.debug.breakpt.location.file
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
caps.latest.revision: 63
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d980fd2367545eb5c824bacc507d9ced9aa2d723
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765956"
---
# <a name="using-breakpoints"></a>Kesme Noktalarını Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Çağrı yığınına bakın veya belki de kod değişkenleri durumunu görmek için hata ayıklayıcı yürütmesini durdurmak istediğinizde, kesme noktaları ayarlayabilirsiniz. Bunlar, bir geliştirici araç kutusundaki en önemli hata ayıklama tekniklerinden biridir.
  
##  <a name="BKMK_Overview"></a> Kaynak kodunda bir işlev kesme noktası ayarlama  
 Bir işlev kesme noktasını bir kaynak kodu dosyasının sol kenar boşluğunda tıklatarak veya F9 tuşuna basarak ve imlecinizi bir kod satırına koyarak kaynak kodunda ayarlayın. Kesme noktası sol kenar boşluğunda kırmızı bir nokta olarak görünür ve kod satırının de renkli:  
  
 ![Bir kesme noktası ayarlamak](../debugger/media/basicbreakpoint.png "BasicBreakpoint")  
  
 Bu kod hata ayıklayıcıda çalıştırdığınızda, o satırdaki kod yürütülmeden önce kesme noktasına isabet her yürütmeyi durdurur. Kaynak kod satırının sarı renkli:  
  
 ![Kesme noktası yürütme durduruldu](../debugger/media/breakpointexecution.png "BreakpointExecution")  
  
 Bu noktada değerini `testInt` hala 1'dir.  
  
 Değişken değerleri ve çağrı yığını da dahil olmak üzere uygulama geçerli durumda bakabilirsiniz. Çağrı yığını hakkında daha fazla bilgi için bkz: [nasıl yapılır: çağrı yığını penceresinde kullanmak](../debugger/how-to-use-the-call-stack-window.md).  
  
 Herhangi bir yürütülebilir kod satırında bir kesme noktası ayarlayabilirsiniz. Örneğin, C# dilinde kod yukarıdaki bir kesme noktası Değişken bildiriminde ayarlayabilirsiniz `for` döngü ya da herhangi bir kod içinde `for` döngü, ancak ayarlayamıyor bir kesme noktası ad alanı veya sınıf bildirimlerine veya yöntem imzası.  
  
##  <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> Diğer türlerdeki kesme noktaları ayarlama  
 Kesme noktaları, çağrı yığınındaki, ayrıştırma penceresinde ve, yerel C++ kod, bir veri koşul veya bir bellek adresi de ayarlayabilirsiniz.  
  
## <a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a> Çağrı yığını penceresinde bir kesme noktası ayarlama  
 Yönerge ya da bir kesme noktası ayarlayarak için çağıran işlevin döndürdüğü satır yürütmeyi kesebilirsiniz **çağrı yığını** penceresi. Çağrı yığını hakkında daha fazla bilgi için bkz: [nasıl yapılır: çağrı yığını penceresinde kullanmak](../debugger/how-to-use-the-call-stack-window.md). Hata ayıklayıcı, yürütmeyi durdurdu.  
  
1. Uygulama hata ayıklamayı başlatmak ve (örneğin, bir kesme noktasında) bekleme yürütme durduruldu. Açık **çağrı yığını** penceresi (**hata ayıklama / Windows / çağrı yığını**, veya **CTRL + ALT + C**).  
  
2. Çağıran işlevin sağ tıklayın ve ardından **kesme noktası / kesme noktası Ekle**, veya kısayol tuşunu kullanmanız yeterlidir **F9**.  
  
3. Kesme noktası sembolü işlev çağrı adının yanında çağrı yığını, sol kenar boşluğunda görünür.  
  
   İçinde **kesme noktaları** penceresi, çağrı yığını kesme noktası işlevdeki bir sonraki yürütülebilir yönergeye karşılık gelen bir bellek konumuna sahip bir adres olarak görünür. Hata ayıklayıcı yönerge yürütmeyi keser.  
  
   Görsel olarak kesme noktalarını izlemek için kod yürütme sırasında bkz: [hata ayıklarken çağrı yığınında yöntemler harita](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="setting-a-breakpoint-in-the-disassembly-window"></a>Ayrıştırma penceresinde bir kesme noktası ayarlama  
 Bir derleme yönergesinde kesme noktası ayarlamak için hata ayıklayıcının kesme modunda olması gerekir.  
  
1.  Uygulama hata ayıklamayı başlatmak ve (örneğin, bir kesme noktasında) bekleme yürütme durduruldu. Açık **ayrıştırılmış kodu** penceresi (**hata ayıklama / Windows / ayrıştırılmış kodu**, veya **Ctrl + Alt + D**).  
  
2.  Sol kenar boşluğunda kesmek veya imlecinizi yönerge ve ENTER tuşuna ayarlamak istediğiniz yönerge tıklatın **F9**.  
  
## <a name="BKMK_set_a_data_breakpoint_native_cplusplus_only"></a> (Yalnızca yerel C++'da) veri kesme noktası ayarlama  
 Veri kesme noktaları, belirtilen bellek adresi değişiklikleri depolanan değeri olduğunda yürütmeyi Kes. Değer okunur ancak değişmemiş ise yürütme sonu gelmez. Veri kesme noktaları ayarlamak için hata ayıklayıcının kesme modunda olması gerekir.  
  
1. Uygulama hata ayıklamayı başlatmak ve bir kesme noktası ulaşılana kadar bekleyin. Üzerinde **hata ayıklama** menüsünde seçin **yeni kesme noktası / veri kesme noktası** (veya **kesme noktaları** penceresi ve **yeni / veri kesme noktası**.  
  
2. İçinde **adresi** bir bellek adresi ya da bir bellek adresini değerlendiren bir ifade yazın. Örneğin `&avar` değiştiğinde ayırmak için değişken içeriğini `avar` değişiklikler.  
  
3. İçinde **bayt sayısı** açılır menüsünde, hata ayıklayıcının izlemesini istediğiniz bayt sayısını seçin. Örneğin, **4**, hata ayıklayıcı başlayan dört baytı izleyecek `&avar` ve bu baytlardan birini değeri değiştiğinde kesecektir.  
  
   Belirli bellek adresleri uygulanabilirliğini üzerinde veri kesme noktaları bağımlı aklınızda bulundurun.  
  
- Değişkenin adresini, bir hata ayıklama oturumundan diğerine değiştirir. Veri kesme noktaları her hata ayıklama oturumu sonunda otomatik olarak devre dışıdır.  
  
- Üzerinde veri kesme noktası ayarlarsanız, yerel bir değişken, işlev sona erdiğinde etkinleştirilmiş kesme noktası kalır, ancak bellek adresini artık ilgili ve kesme noktası davranışı tahmin edilemez. Yerel bir değişkende veri kesme noktası ayarlarsanız, kaldırın ya da işlev sonlandırılmadan önce kesme noktasını devre dışı bırakın.  
  
  Veri kesme noktaları bu koşullar altında çalışmaz:  
  
- Değil ayıklanmakta olan bir işlem bellek konumuna yazma  
  
- Bellek konumu iki veya daha fazla işlemler arasında paylaşılır.  
  
- Bellek konumu çekirdek içinde güncelleştirilir. Örneğin bellek 32-bit Windows için iletilmezse `ReadFile` işlevi, bellek çekirdek modundan güncelleştirilecek ve hata ayıklayıcı belleğe yazma sonu gelmez.  
  
## <a name="setting-a-breakpoint-with-a-memory-address-native-c-only"></a>Bir bellek adresi (yalnızca yerel C++'da) ile bir kesme noktası ayarlama  
 Bir sınıfın belirli bir örneği olarak adlandırılan bir yöntemde bir kesme noktası ayarlamak için bir nesnenin adresini de kullanabilirsiniz.  Örnek buradadır:  
  
 Örneğin, bir nesne türü belirtilen `my_class` adresiyle adlı bir yöntem bir işlev kesme noktası ayarlayabilirsiniz `my_method` bu örneğinden çağrılır.  
  
1.  Bu sınıf örneği örneği sonra bir kesme noktası yere ayarlayın.  
  
2.  Örneğinin adresini bulun (sahip dediğimiz `0xcccccccc`).  
  
3.  Tıklayın **hata ayıklama / yeni kesme noktası / işlev kesme noktası** (veya **ALT + F9'a, B**).  
  
4.  Aşağıdaki metni ekleyin **işlev adı** kutusunda:  
  
    ```cpp  
    ((my_class *) 0xcccccccc)->my_method  
    ```  
  
##  <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Kesme noktaları yönetme  
 Kullanabileceğiniz **kesme noktaları** penceresi (**hata ayıklama / Windows / kesme noktaları**, veya **CTRL + ALT + B**) tüm kesme noktalarını görmek için çözümünüzde ayarladığınız:  
  
 ![Kesme noktaları penceresi](../debugger/media/breakpointswindow.png "BreakpointsWindow")  
  
 **Kesme noktaları** penceresi tüm kesme noktalarınızı, özellikle büyük bir çözümde veya kesme noktalarının kritik olduğu karmaşık bir hata ayıklama senaryosuna yardımcı olabilen yönetmek için merkezi bir konum sağlar. Kesme noktaları kümesinin konumunu ve durumunu kaydedin veya gerekiyorsa, dışarı aktarma ve kesme noktaları yalnızca içeri aktarma **kesme noktaları** penceresi.  
  
##  <a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a> Gelişmiş kesme noktaları  
  
## <a name="breakpoint-conditions"></a>Kesme noktası koşulları  
 Ne zaman ve nerede kesme noktası koşulları ayarlayarak yürütür denetleyebilirsiniz.  
  
1. Kesme noktasına sağ tıklatın, kesme noktası gelin ve Ayarlar simgesini seçin.  
  
2. Bağlam menüsünde seçin **koşullar**. Bu açılır **kesme noktası ayarları** penceresi:  
  
   ![Kesme noktası ayarları](../debugger/media/breakpointsettings.png "BreakpointSettings")  
  
   İade **koşullar** penceresi kutusunu genişletir çeşitli koşullar göstermek için.  
  
   **Koşullu ifade:** koşullu ifade seçtiğinizde, iki koşuldan sonra seçebilirsiniz: **true** ve **değiştirildiğinde**. Seçin **true** kesmek istiyorsanız ne zaman ifadesi karşılanmadı veya seçin **değiştirildiğinde** ifade değeri değiştiğinde kesmek istiyorsanız.  
  
   Aşağıdaki örnekte biz yalnızca isabet kesme noktasını ayarlamanız değerini `testInt` olduğu **4**:  
  
   ![Kesme noktası koşulu true ise](../debugger/media/breakpointconditionistrue.png "BreakpointConditionIsTrue")  
  
   Aşağıdaki örnekte biz yalnızca isabet kesme noktasını ayarlamanız değerini `testInt` değişiklikler:  
  
   ![Değiştirilme zamanı kesme noktası](../debugger/media/breakpointwhenchanged.png "BreakpointWhenChanged")  
  
   Davranışı ne zaman değiştirilen alan farklı programlama dili için farklıdır. Seçerseniz **değiştirildiğinde** yerel kod için hata ayıklayıcı kesme noktası ilk değerlendirmeye yakalayamazsınız bir değişiklik olması için koşulun ilk değerlendirmesinin dikkate almaz. Seçerseniz **değiştirildiğinde** yönetilen kod için kesme noktası üzerinde sonraki ilk değerlendirmede isabet **değiştirildiğinde** seçilir.  
  
   Geçersiz söz dizimi ile bir kesme noktası koşulu ayarlarsanız, bir uyarı iletisi görüntülenir. Geçerli sözdizimi, ancak geçersiz semantiği ile bir kesme noktası koşulu belirtirseniz kesme noktasına ilk kez bir uyarı iletisi görüntülenir. Her iki durumda da, geçersiz kesme noktasına gelindiğinde hata ayıklayıcı yürütmeyi keser. Kesme noktası yalnızca koşul geçerliyse ve değerlendirilir atlanır `false`.  
  
   Koşul, hata ayıklayıcı tarafından tanınan herhangi bir geçerli ifade olabilir. Geçerli ifadeler hakkında daha fazla bilgi için bkz. [hata ayıklayıcısındaki ifadeler](../debugger/expressions-in-the-debugger.md).  
  
## <a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>Kesme noktası koşulları nesne kimlikleri kullanarak (C# ve F#)  
 Belirli bir nesneyi davranışını gözlemlemek istediğiniz zaman zamanlar vardır; Örneğin, neden bir nesne birden çok kez bir koleksiyona eklenmiş kullanıma bulmak isteyebilirsiniz. İçinde C# ve F#, belirli örneklerini nesne kimlikleri oluşturabilirsiniz [başvuru türleri](http://msdn.microsoft.com/library/801cf030-6e2d-4a0d-9daf-1431b0c31f47) ve kesme noktası koşulları kullanabilirsiniz. Nesne Kimliği hizmetlerinde hata ayıklama ortak dil çalışma zamanı tarafından (CLR) oluşturulan ve nesnesiyle ilişkili.  Bir nesne kimliği oluşturmak için aşağıdakileri yapın:  
  
1. Bir kesme noktası kodda nesne oluşturulduktan sonra biraz zaman ayarlayın.  
  
2. Hata ayıklamayı başlatmak ve kesme yürütme sona erdiğinde, kesme noktasına Bul **Yereller** penceresinde sağ tıklatın ve seçin **nesne kimliği yap**.  
  
    Görmelisiniz bir **$** bir sayıyı artı **Yereller** penceresi. Bu nesne kimliğidir.  
  
3. Araştırmak, örneğin koleksiyona eklenecek nesne olduğunda istediğiniz noktada yeni bir koşullu kesme noktası ekleyin.  
  
4. Nesne Kimliği koşullu ifade alanında kullanın. Örneğin, bir değişken ise `item` koleksiyona eklenecek nesneye başvuran, size koyabilirsiniz **öğesi $n ==** burada **n** nesne kimliği bir sayıdır.  
  
    Bu nesne koleksiyona eklenecek olduğunda noktada yürütmeyi keser.  
  
   Daha sonra nesne Kimliğini silmek istiyorsanız, değişkeni sağ tıklayabilirsiniz **Yereller** penceresi ve select **Nesne Kimliği Sil**.  
  
   Nesne kimlikleri zayıf başvuru oluşturmak ve nesnenin çöp olarak toplanacak yüklenmesini engellemez unutmayın. Bunlar, yalnızca geçerli hata ayıklama oturumu için geçerli olur.  
  
## <a name="hit-count"></a>İsabet sayısı  
 Kodunuzdaki döngünün belirli sayıda yinelemeden sonra yanlış davranış başlattığından şüpheleniyorsanız, bir kesme noktası isabet sayısı için belirtilen sayıda yürütmeyi durdurmak için ayarlayabileceğiniz ilişkili kod satırına, art arda zorunda yerine basın  **F5** yineleme düzeyine ulaşmak için.  
  
 İçinde **kesme noktası ayarları** penceresinde ayarlanmış koşul **Hit Count**. Ardından, yineleme sayısını belirtebilirsiniz. Aşağıdaki örnekte, size her bir yineleme üzerinde isabet kesme noktası ayarlayın:  
  
 ![Kesme noktası isabet sayısı](../debugger/media/breakpointhitcount.png "BreakpointHitCount")  
  
## <a name="filter"></a>Filtrele  
 Yalnızca belirtilen cihazlarda veya belirli süreçleri ve iş parçacığı için bir kesme noktası kısıtlayabilirsiniz.  
  
 İçinde **kesme noktası ayarı**s penceresinde ayarlanmış koşul **filtre**. Bir veya daha fazla aşağıdaki ifadeler girin.  
  
- MachineName = "name"  
  
- ProcessID = değer  
  
- ProcessName "name" =  
  
- ThreadID = değer  
  
- ThreadName = "name"  
  
  Dize değerleri çift tırnak içine alın. Kullanarak ifadeleri birleştirebilirsiniz `&` (AND) `||` (veya) `!` (NOT) ve parantez.  
  
##  <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Kesme noktası eylemleri ve izleme noktaları  
 İzleme noktası çıkış penceresine ileti yazdıran kesme noktasıdır. İzleme noktası programlama dilinde geçici trace deyimi gibi davranabilir.  
  
 İçinde **kesme noktası ayarları** onay penceresinde **eylemleri** kutusu. Seçin **çıkış penceresinde bir ileti Kaydet** içinde **eylem** grubu. Genel bir dize gibi yazdırabilir **bu bir sınamadır**. Bir değişkenin veya ifadenin değerini dahil etmek için küme ayraçlarının içine alın.  
  
 İzleme noktasına gelindiğinde yürütmeyi kesmek için Temizle **yürütmeye devam et** onay kutusu. Zaman **yürütmeye devam et** denetlenir yürütme durdurulmaz. Her iki durumda da ileti yazdırılır.  
  
 Aşağıdaki özel anahtar sözcükler kullanabilirsiniz **ileti**.  
  
|||  
|-|-|  
|**$ADDRESS**|Geçerli yönergesi|  
|**$CALLER**|Arama işlev adı|  
|**$CALLSTACK**|Çağrı yığını|  
|**$FUNCTION**|Geçerli işlev adı|  
|**$PID**|işlem kimliği|  
|**$PNAME**|İşlem adı|  
|**$TID**|iş parçacığı kimliği|  
|**$TNAME**|İş parçacığı adı|  
|**$TICK**||  
|**$TNAME**||  
  
##  <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Kesme noktası etiketleri  
 Kesme noktası etiketleri yalnızca kullanılan **kesme noktaları** sıralamak ve kesme noktaları listesini filtrelemek için penceresi. Bir kesme noktasına bir etiket eklemek için kesme noktası satırını seçin ve ardından **etiket** bağlam menüsünde.  
  
## <a name="export-and-import-breakpoints"></a>Dışarı aktarma ve içeri aktarma kesme noktaları  
 Bir kesme noktasına kesme noktasına sağ tıklatıp seçerek bir XML dosyasına aktarabilirsiniz **dışarı**. Dosya, varsayılan çözüm dizini olarak kaydedilir. Kesme noktalarını içeri aktarmak için açık **kesme noktaları** penceresi (**CTRL + ALT + B**) ve sağ ok simgesini (Araç İpucu **bir dosyadan kesme noktalarını içe**) .  
  
## <a name="troubleshoot-breakpoints"></a>Kesme noktaları sorunlarını giderme  
  
### <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Bir kesme noktası sildim ama hata ayıklamayı yeniden başlattığınızda, isabet devam  
 Hata ayıklarken bir kesme noktası silinirse, bazı durumlarda, hata ayıklama yeniden başlattığınızda kesme noktası karşılaşabilirsiniz. Bu kesme noktasına ulaşma durdurmak için kesme noktası örneklerini kaldırılma tüm emin **kesme noktaları** penceresi.  
  
### <a name="the-debugger-cant-locate-the-correct-version-of-the-source-file-for-a-breakpoint"></a>Hata ayıklayıcı bir kesme noktası için kaynak dosyanın doğru sürümünü bulamıyor  
 Kaynak dosyası mevcut olsa bile kaynak dosyası değiştirilirse ve kaynak artık ayıkladığınız kod ile eşlenmiyorsa, hata ayıklayıcı bir kesme noktasına karşılık gelen kaynak dosyasını bulabilirsiniz.  
  
1.  Visual Studio sürümle eşleşmeyen kaynak kodunu görüntülemesini isterseniz, hata ayıklama, seçin **Hata Ayıkla / seçenekler ve ayarlar**. Üzerinde **hata ayıklama/genel** sayfasında, NET **özgün sürümle tam eşleşen kaynak dosyaları gerekiyor** seçeneği.  
  
2.  Ayrıca, kesme noktasına kaynak dosyaya bağlayabilirsiniz. Kesme noktası seçip **koşullar** bağlam menüsünde. Denetleme **kaynak kodun özgün sürümden farklı olmasına izin ver** içinde **kesme noktası ayarları** penceresi.  
  
### <a name="breakpoints-dont-work-in-a-dll"></a>Kesme noktaları DLL içinde çalışmaz  
 Hata ayıklayıcı bir modül için hata ayıklama bilgileri yüklemediğinde kodun bulunduğu bir kaynak dosyasında bir kesme noktası ayarlanamıyor. Belirtiler iletileri içerebilir gibi **kesme noktası ayarlanmadı**. Uyarı kesme karakteri kesme noktası konumunda görünür. Ancak, bu uyarı kesme noktaları kod yüklendiğinde gerçek kesme noktaları haline gelir. Sembolleri yükleme hakkında daha fazla bilgi için bkz. [belirtin sembol (.pdb) ve kaynak dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı ile Kodlarda gezinme](../debugger/navigating-through-code-with-the-debugger.md)



