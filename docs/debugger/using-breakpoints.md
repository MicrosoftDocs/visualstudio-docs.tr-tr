---
title: Hata ayıklayıcıda kesme noktaları kullanma | Microsoft Docs
ms.custom: seodec18
ms.date: 10/15/2018
ms.technology: vs-ide-debug
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
helpviewer_keywords:
- breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 16bcb4bb12e852a8fa268998d0605b2ffc7471e5
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068454"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcıda kesme noktaları kullanma
Kesme noktaları, geliştirici araç kutusundaki en önemli hata ayıklama tekniklerinden biridir. Hata ayıklayıcı yürütme duraklatmak istediğiniz yere kesme noktalarını ayarlayın. Örneğin, belirli bir kesme noktası çağrı yığınına bakın veya kod değişkenleri durumunu görmek isteyebilirsiniz. Bu, kodda hata ayıklamak için girişimde ilk kez ise, okumak isteyebilirsiniz [yeni başlayanlar için hata ayıklama](../debugger/debugging-absolute-beginners.md) bu makalede geçmeden önce.
  
##  <a name="BKMK_Overview"></a> Kaynak kodunda kesme noktalarını belirleyin  
 Herhangi bir yürütülebilir kod satırında bir kesme noktası ayarlayabilirsiniz. Örneğin, aşağıdaki C# kodunda, size bir kesme noktası Değişken bildiriminde ayarlayabilirsiniz `for` döngü ya da herhangi bir kod içinde `for` döngü. Ad alanı veya sınıf bildirimlerinde ya da yöntem imzası bir kesme noktası ayarlanamıyor.  

 Kaynak kodunda bir kesme noktası ayarlamak için bir kod satırının yanındaki en sol kenar boşluğunda tıklayın. Çizgi ve ENTER tuşuna de seçebilirsiniz **F9**seçin **hata ayıklama** > **iki durumlu kesme noktası**, veya sağ tıklayıp **kesmenoktası**  >  **Kesme noktası Ekle**. Kesme noktası sol kenar boşluğunda kırmızı bir nokta olarak görünür.  

İçinde C# kod, kesme noktası ve geçerli yürütme satırları otomatik olarak vurgulanır. C++ kodu için kesme noktası geçerli satır ve seçerek vurgulamayı kapatabilirsiniz **Araçları** (veya **hata ayıklama**) > **seçenekleri**  >   **Hata ayıklama** >  **kesme noktaları ve geçerli deyim (yalnızca C++) için tüm kaynak satırını Vurgula**. 
  
 ![Bir kesme noktası ayarlamak](../debugger/media/basicbreakpoint.png "temel kesme noktası")  
  
 Hata ayıklama, kod bu satırı yürütülmeden önce yürütme kesme noktasında duraklatır. Kesme noktası simgesi sarı bir ok gösterir. 

 Aşağıdaki örnekte, değerini kesme noktasında `testInt` hala 1'dir.  
  
 ![Kesme noktası yürütme durduruldu](../debugger/media/breakpointexecution.png "kesme noktası yürütme")  
  
 Hata ayıklayıcı kesme noktasında durdurulduğunda, değişkeni değerlerini ve çağrı yığını da dahil olmak üzere uygulama geçerli durumda bakabilirsiniz. Çağrı yığını hakkında daha fazla bilgi için bkz: [nasıl yapılır: çağrı yığını penceresini kullanma](../debugger/how-to-use-the-call-stack-window.md).  

- Bir iki durumlu kesme noktası olur. Tıklatın, basın **F9**, veya **hata ayıklama** > **iki durumlu kesme noktası** silme veya yeniden.
  
- Bir kesme noktası silmeden devre dışı bırakmak için üzerine gelin veya sağ tıklatın ve seçin **devre dışı kesme noktası**. Devre dışı bırakılmış kesme noktaları görünür sol kenar boşluğunda boş noktaların veya **kesme noktaları** penceresi. Bir kesme noktası yeniden etkinleştirmek için üzerine gelin veya sağ tıklatın ve seçin **etkinleştirme kesme noktası**. 
  
- Koşullar ve Eylemler ayarlamak, ekleyin ve etiketleri düzenle veya sağ ve uygun komutu veya üzerine gelin ve seçerek bir kesme noktası dışarı **ayarları** simgesi.

##  <a name="BKMK_Set_a_breakpoint_in_a_function"></a> Windows Hata Ayıklayıcı'dan kesme noktaları ayarlama 

Gelen kesme noktaları da ayarlayabilirsiniz **çağrı yığını** ve **ayrıştırılmış kodu** hata ayıklayıcı, windows.  
  
### <a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a> Çağrı yığını penceresinde bir kesme noktası ayarlayın  

 Yönerge veya çağıran bir işlev döndürür satırı kesmek için bir kesme noktası ayarlayabilirsiniz **çağrı yığını** penceresi. 
  
**Çağrı yığını penceresinde bir kesme noktası ayarlamak için:**

1. Açmak için **çağrı yığını** penceresi, hata ayıklama sırasında duraklatılmış gerekir. Seçin **hata ayıklama** > **Windows** > **çağrı yığını**, veya basın **Ctrl** + **Alt**+**C**.  
   
2. İçinde **çağrı yığını** penceresinde çağıran işlevin sağ tıklayıp **kesme noktası** > **kesme noktası Ekle**, veya basın **F9**.  
   
   Kesme noktası sembolü işlev çağrı adının sol kenar boşluğunda çağrı yığınının yanında görünür.
   
Çağrı yığını kesme noktası görünür **kesme noktaları** işlevi bir sonraki yürütülebilir yönergeye karşılık gelen bir bellek konumuna sahip bir adres olarak penceresi. 

Hata ayıklayıcı yönerge olduğunda yürütmeyi keser.  

Çağrı yığını hakkında daha fazla bilgi için bkz: [nasıl yapılır: çağrı yığını penceresini kullanma](../debugger/how-to-use-the-call-stack-window.md). 

Görsel olarak kesme noktalarını izlemek için kod yürütme sırasında bkz: [hata ayıklarken çağrı yığınında yöntemler harita](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md). 
  
### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Ayrıştırma penceresinde bir kesme noktası ayarlayın  
   
1. Açmak için **ayrıştırılmış kodu** penceresi, hata ayıklama sırasında duraklatılmış gerekir. Seçin **hata ayıklama** > **Windows** > **ayrıştırılmış kodu**, veya basın **Alt** + **8**.  
   
2. İçinde **ayrıştırılmış kodu** penceresi, kesmek istediğiniz yönergenin sol kenar boşluğunda tıklayın. Ayrıca seçin ve basın **F9**, veya sağ tıklayıp **kesme noktası** > **kesme noktası Ekle**. 

##  <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> İşlev kesme noktaları belirleyin  

  Bir işlev çağrıldığında yürütmeyi kesebilirsiniz. 

**Bir işlev kesme noktası ayarlamak için:**
  
1. Seçin **hata ayıklama** > **yeni kesme noktası** > **işlev kesme noktası**, veya basın **Alt** + **F9** > **Ctrl**+**B**. 
   
   Belirleyebilirsiniz **yeni** > **işlev kesme noktası** içinde **kesme noktaları** penceresi.
   
1. İçinde **yeni işlev kesme noktası** iletişim kutusunda işlev adı girin **işlev adı** kutusu. 

   İşlev belirtimini daraltmak için:
   
   - Tam işlev adını kullanın. 
     
     Örnek:  `Namespace1.ClassX.MethodA()`
     
   - Aşırı yüklenmiş bir işlevi parametre türleri ekleyin. 
     
     Örnek:  `MethodA(int, string)`
     
   - Kullanım '!' modülü belirtmek için Sembol.
     
     Örnek: `App1.dll!MethodA`
     
   - Yerel C++'da şu içerik işlecini kullanın.
     
     `{function, , [module]} [+<line offset from start of method>]`
     
     Örnek: `{MethodA, , App1.dll}+2`
   
1. İçinde **dil** açılır listesinde, işlevin dili seçin.
   
1. Seçin **Tamam**.
  
### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Bir bellek adresi (yalnızca yerel C++'da) kullanarak bir işlev kesme noktası ayarlama  
 Bir sınıfın belirli bir örneği tarafından adlı bir yöntem bir işlev kesme noktası ayarlamak için bir nesnenin adresini kullanabilirsiniz.  Örneğin, türü adreslenebilir bir nesneyi belirtilen `my_class`, bir işlev kesme noktası ayarlayabilirsiniz `my_method` çağrıları örnek yöntemi. 
  
1.  Sınıfının örneğini örneği sonra herhangi bir yerde bir kesme noktası ayarlayın.  
    
2.  Örneğinin adresini bulun (örneğin, `0xcccccccc`). 
    
3.  Seçin **hata ayıklama** > **yeni kesme noktası** > **işlev kesme noktası**, veya basın **Alt** + **F9** > **Ctrl**+**B**.  
    
4.  Ekleyin **işlev adı** kutusunda ve seçin **C++** dili.  
    
    ```C++  
    ((my_class *) 0xcccccccc)->my_method  
    ```  

## <a name="BKMK_set_a_data_breakpoint_native_cplusplus_only"></a>Veri kesme noktaları (yalnızca yerel C++'da) ayarla 
 
 Veri kesme noktaları, belirtilen bellek adresi değişiklikleri depolanan değeri olduğunda yürütmeyi Kes. Değer okunur ancak değişmemiş ise yürütme sonu gelmez.  
  
**Veri kesme noktası ayarlamak için:**

1.  Bir C++ projesinde hata ayıklamayı başlatmak ve bir kesme noktası ulaşılana kadar bekleyin. Üzerinde **hata ayıklama** menüsünde seçin **yeni kesme noktası** > **veri kesme noktası** 

    Belirleyebilirsiniz **yeni** > **veri kesme noktası** içinde **kesme noktaları** penceresi.
  
2.  İçinde **adresi** bir bellek adresi ya da bir bellek adresini değerlendiren bir ifade yazın. Örneğin `&avar` değiştiğinde ayırmak için değişken içeriğini `avar` değişiklikler.  
  
3.  İçinde **bayt sayısı** açılır menüsünde, hata ayıklayıcının izlemesini istediğiniz bayt sayısını seçin. Örneğin, **4**, hata ayıklayıcı başlayan dört baytı izleyecek `&avar` ve bu baytlardan birini değeri değiştiğinde kesecektir.  

Veri kesme noktaları, aşağıdaki koşullar altında çalışmaz:  
-   Değil ayıklanmakta olan bir işlem bellek konumuna yazar.  
-   Bellek konumu iki veya daha fazla işlemler arasında paylaşılır.  
-   Bellek konumu çekirdek içinde güncelleştirilir. Örneğin bellek 32-bit Windows için iletilmezse `ReadFile` işlevi, güncelleştirmeyi hata ayıklayıcı kesme olmaz şekilde bellek çekirdek modundan güncelleştirilecek.  

>[!NOTE]
>- Veri kesme noktaları belirli bellek adreslerinde bağlıdır. Değişkenin adresini, bir hata ayıklama oturumundan yanında, değiştirir, böylece veri kesme noktaları her hata ayıklama oturumu sonunda otomatik olarak devre dışıdır.  
>  
>- Yerel bir değişkende veri kesme noktası ayarlarsanız, işlev sona erdiğinde, kesme noktası etkin kalır ancak kesme noktası davranışı tahmin edilemez şekilde bellek adresi artık geçerli değil. Yerel bir değişkende veri kesme noktası ayarlarsanız, delete ya da işlev sonlandırılmadan önce kesme noktasını devre dışı bırakın.  

##  <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Kesme noktaları penceresinde kesme noktalarını yönetin 

 Kullanabileceğiniz **kesme noktaları** penceresi görüp çözümünüzdeki tüm kesme noktalarını yönetin. Bu bir merkezi konumdan büyük bir çözümde veya kesme noktalarının kritik olduğu karmaşık hata ayıklama senaryoları için özellikle yararlı olur. 

İçinde **kesme noktaları** penceresinde, arama, sıralayabilir, filtre, etkinleştir/devre dışı bırak veya kesme noktalarını sil. Koşullar ve Eylemler ayarlayın veya yeni bir işlev veya veri kesme noktası ekleyin.
  
Açmak için **kesme noktaları** penceresinde **hata ayıklama** > **Windows** > **kesme noktaları**, veya tuşunabasın **Alt**+**F9** veya **Ctrl**+**Alt**+**B**.
  
![Kesme noktaları penceresi](../debugger/media/breakpointswindow.png "kesme noktaları penceresi")  
  
Görüntülenecek sütunları seçmek için **kesme noktaları** penceresinde **sütunları göster**. Kesme noktaları listesinde sütuna göre sıralamak için sütun başlığını seçin. 

###  <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Kesme noktası etiketleri  
Etiketleri kesme noktaları listesini filtrelemek ve sıralamak için kullanabileceğiniz **kesme noktaları** penceresi. 

1. Bir kesme noktasına bir etiket eklemek için kaynak kodunda kesme noktasına sağ tıklayın veya **kesme noktaları** penceresi tıklayın ve ardından **etiketleri Düzenle**. Yeni bir etiket ekleyin veya mevcut bir seçin ve ardından **Tamam**.
2. Kesme noktası sıralamak **kesme noktaları** penceresini seçerek **etiketleri**, **koşullar**, ya da diğer sütun başlıkları. Görüntülenecek sütunları seçebilir **sütunları göster** araç. 
  
### <a name="export-and-import-breakpoints"></a>Kesme noktalarını içeri ve dışarı  
 Kaydetmek veya kesme noktalarınız konumunu ve durumunu paylaşmak için dışarı aktarma veya aktarın. 

- Tek bir kesme noktası bir XML dosyasına dışa aktarmak için kaynak kodunda kesme noktasına sağ tıklayın veya **kesme noktaları** penceresi ve select **dışarı** veya **seçili dışarı aktarma**. Bir dışarı aktarma konumunu seçin ve ardından **Kaydet**. Çözüm klasörü varsayılan konumdur. 
- Birkaç kesme noktaları olarak dışa aktarmayı **kesme noktaları** penceresinde, kesme noktaları yanındaki kutuları işaretleyin veya arama ölçütlerini girin **arama** alan. Seçin **geçerli arama ölçütüyle eşleşen tüm kesme noktalarını dışarı** simgesini ve dosyayı kaydedin. 
- Tüm kesme noktalarını dışarı aktarmak için tüm kutularının işaretini kaldırın ve bırakın **arama** alanını boş bırakın. Seçin **geçerli arama ölçütüyle eşleşen tüm kesme noktalarını dışarı** simgesini ve dosyayı kaydedin.  
- İçinde kesme noktaları, içeri aktarmak için **kesme noktaları** penceresinde **bir dosyadan kesme noktalarını içe** simgesi, XML dosyasının konumuna gidin ve seçin **açık**. 

##  <a name="breakpoint-conditions"></a>Kesme noktası koşulları  
 Ne zaman ve nerede kesme noktası koşulları ayarlayarak yürütür denetleyebilirsiniz. Koşul, hata ayıklayıcı tanıdığı herhangi bir geçerli ifade olabilir. Geçerli ifadeler hakkında daha fazla bilgi için bkz. [hata ayıklayıcısındaki ifadeler](../debugger/expressions-in-the-debugger.md).  

**Bir kesme noktası koşulu ayarlamak için:**

1. Kesme noktası sembolü sağ tıklayıp **koşullar**. Veya select kesme noktası simgenin üzerine geldiğinizde **ayarları** simgesine tıklayın ve ardından **koşullar** içinde **kesme noktası ayarları** penceresi.  

   De koşulları ayarlayabilirsiniz **kesme noktaları** penceresinde bir kesme noktasına sağ tıklayıp seçerek **ayarları**seçip **koşullar**. 
  
   ![Kesme noktası ayarları](../debugger/media/breakpointsettings.png "BreakpointSettings")  
  
2. Açılır menüden seçin **koşullu ifade**, **Hit Count**, veya **filtre**ve buna göre ayarlayın. 
  
3. Seçin **kapatmak** veya basın **Ctrl**+**Enter** kapatmak için **kesme noktası ayarları** penceresi. Veya **kesme noktaları** penceresinde **Tamam** iletişim kutusunu kapatmak için. 

Koşullar kümesiyle kesme noktaları ile görünür bir **+** sembol kaynak kodunda ve **kesme noktaları** windows. 

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="conditional-expression"></a>Koşullu ifade

Seçtiğinizde, **koşullu ifade**, iki koşul arasında seçim yapabilirsiniz: **true** veya **değiştirildiğinde**. Seçin **true** ifade karşılandığında, kesmek veya **değiştirildiğinde** ifade değeri değiştiğinde kesmek için.  
  
 Aşağıdaki örnekte, kesme noktasına erişildiğinde yalnızca değerini `testInt` olduğu **4**:  
  
 ![Kesme noktası koşulu true ise](../debugger/media/breakpointconditionistrue.png "true kesme noktası")  
  
 Aşağıdaki örnekte, kesme noktasına erişildiğinde yalnızca değerini `testInt` değişiklikler:  
  
 ![Değiştirilme zamanı kesme noktası](../debugger/media/breakpointwhenchanged.png "kesme noktası değiştirildiğinde")  
  
 Geçersiz söz dizimi ile bir kesme noktası koşulu ayarlarsanız, bir uyarı iletisi görüntülenir. Geçerli sözdizimi, ancak geçersiz semantiği ile bir kesme noktası koşulu belirtirseniz kesme noktasına ilk kez bir uyarı iletisi görüntülenir. Geçersiz kesme noktasına ulaştığında her iki durumda da hata ayıklayıcı keser. Kesme noktası yalnızca koşul geçerliyse ve değerlendirilir atlanır `false`.  
  
 >[!NOTE]
 >Davranışını **değiştirildiğinde** alan farklı programlama dili için farklıdır. 
 >- Yerel kod için hata ayıklayıcı, kesme noktasına ilk değerlendirmede isabet etmez şekilde bir değişiklik, koşulun ilk değerlendirmesinin dikkate almaz. 
 >- Yönetilen kod için hata ayıklayıcı kesme noktasına sonraki ilk değerlendirmede isabet **değiştirildiğinde** seçilir.  
  
### <a name="using-object-ids-in-conditional-expressions-c-and-f-only"></a>Nesne kimlikleri koşullu ifadeler kullanma (C# ve F# yalnızca)  
 Belirli bir nesneyi davranışını gözlemlemek istediğiniz zaman zamanlar vardır. Örneğin, neden bir nesne bir koleksiyona birden fazla kez eklendi kullanıma bulmak isteyebilirsiniz. İçinde C# ve F#, belirli örneklerini nesne kimlikleri oluşturabilirsiniz [başvuru türleri](/dotnet/csharp/language-reference/keywords/reference-types)ve kesme noktası koşulları kullanabilirsiniz. Nesne Kimliği hizmetlerinde hata ayıklama ortak dil çalışma zamanı tarafından (CLR) oluşturulan ve nesnesiyle ilişkili.  

**Bir nesne kimliği oluşturmak için:** 
  
1. Nesne oluşturulduktan sonra bir kesme noktası kodda bir yere ayarlayın.  
   
2. Hata ayıklamayı başlatmak ve yürütme kesme noktasında durakladığında seçin **hata ayıklama** > **Windows** > **Yereller** veya **Alt** + **4** açmak için **Yereller** penceresi.
   
   Kesme noktasına Bul **Yereller** penceresinde sağ tıklatın ve seçin **nesne kimliği yap**.  
   
   Görmelisiniz bir **$** bir sayıyı artı **Yereller** penceresi. Bu nesne kimliğidir.  
   
3. Yeni bir kesme noktası araştırmak istediğiniz yere ekleyin; Örneğin, nesne koleksiyona eklenecek olduğunda. Kesme noktasına sağ tıklayıp **koşullar**.  
   
4. Nesne kimliği kullanan **koşullu ifade** alan. Örneğin, varsa değişkeni `item` koleksiyonuna select eklenecek nesne **true** ve türü **öğesi == $\<n >** burada \<n > nesne kimliği numarası .  
   
   Bu nesne koleksiyona eklenecek olduğunda noktada yürütmeyi keser.  
   
   Nesne Kimliğini silmek için değişkeni sağ **Yereller** penceresi ve select **Nesne Kimliği Sil**.  

>[!NOTE]
>Nesne kimlikleri, zayıf başvuru oluşturmak ve nesnenin çöp olarak toplanacak yüklenmesini engellemez. Bunlar, yalnızca geçerli hata ayıklama oturumu için geçerli olur.  
  
### <a name="hit-count"></a>İsabet sayısı  
 Kodunuzdaki döngünün belirli sayıda yinelemeden sonra yanlış davranış başlattığından şüpheleniyorsanız, bu art arda basmak yerine isabet sayısı sonra yürütmeyi durdurmak için bir kesme noktası ayarlayabilirsiniz **F5** bu yineleme ulaşmak için.  
  
 Altında **koşullar** içinde **kesme noktası ayarları** penceresinde **Hit Count**, yineleme sayısını belirtin. Aşağıdaki örnekte, kesme noktasına isabet her bir yineleme üzerinde ayarlanır:  
  
 ![Kesme noktası isabet sayısı](../debugger/media/breakpointhitcount.png "BreakpointHitCount")  
  
### <a name="filter"></a>Filtrele  
Yalnızca belirtilen cihazlarda veya belirli süreçleri ve iş parçacığı için bir kesme noktası kısıtlayabilirsiniz.  
  
Altında **koşullar** içinde **kesme noktası ayarları** penceresinde **filtre**ve ardından bir veya daha fazla aşağıdaki ifadeler girin:  
  
-   MachineName = "name"  
-   ProcessID = değer  
-   ProcessName "name" =  
-   ThreadID = değer  
-   ThreadName = "name"  

Dize değerleri çift tırnak içine alın. Kullanarak ifadeleri birleştirebilirsiniz `&` (AND) `||` (veya) `!` (NOT) ve parantez.  
  
##  <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Kesme noktası eylemleri ve izleme noktaları  
 A *İzleme noktası* ileti yazdıran kesme noktasıdır **çıkış** penceresi. İzleme noktası programlama dilinde geçici trace deyimi gibi davranabilir.  
  
**İzleme noktası ayarlamak için:**

1. Bir kesme noktasına sağ tıklayıp **eylemleri**. Veya **kesme noktası ayarları** penceresinde kesme noktası üzerine geldiğinizde seçin **ayarları** simgesine tıklayın ve ardından **eylemleri**.  
   
1. Bir ileti girin **çıkış penceresinde bir ileti Kaydet** alan. İleti genel metin dizelerini, değerleri değişkenlere veya küme ayraçları ve biçim belirticileri içine ifadeleri içerebilir ([C#](../debugger/format-specifiers-in-csharp.md) ve [C++](../debugger/format-specifiers-in-cpp.md)) değerleri için.
   
   Aşağıdaki özel anahtar sözcükler iletisinde de kullanabilirsiniz:  
   
   - **$ADDRESS** -geçerli yönergesi  
   - **$CALLER** -arama işlev adı  
   - **$CALLSTACK** -çağrı yığını 
   - **$FUNCTION** -geçerli işlev adı  
   - **$PID** -işlem kimliği  
   - **$PNAME** -işlem adı  
   - **$TID** -iş parçacığı kimliği  
   - **$TNAME** -iş parçacığı adı  
   - **$TICK** -değer sayısı (Windows gelen `GetTickCount`)  
   
1. İletiyi yazdırmak için **çıkış** olmadan, Seç penceresi **yürütmeye devam et** onay kutusu. İzleme noktası iletisi ve sonu yürütmeyi yazdırmak için onay kutusunu temizleyin. 

İzleme noktaları görünür olarak kaynak kodunun sol kenar boşluğunda kırmızı Karo ve **kesme noktaları** windows. 
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Hata ayıklıyor?](../debugger/what-is-debugging.md)  
 [Daha iyi yazma C# kullanarak Visual Studio code](../debugger/write-better-code-with-visual-studio.md)  
 [Hata ayıklama ilk bakış](../debugger/debugger-feature-tour.md)  
 [Visual Studio hata ayıklayıcısında kesme noktaları sorunlarını giderme](../debugger/troubleshooting-breakpoints.md)  
