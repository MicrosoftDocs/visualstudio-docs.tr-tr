---
title: MFC hata ayıklama tekniklerine | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AfxEnableMemoryTracking
- CMemoryState
- delayFreeMemDF
- checkAlwaysMemDF
- vs.debug.mfc
- vs.debug.objects.dump
- vs.debug.memory.dump
- allocMemDF
- afxMemDF
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [MFC]
ms.assetid: b154fc31-5e90-4734-8cbd-58dd9fe1f750
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1e7a1ea69da1cafa38ae2a7bfa4551d3d40a8d4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745115"
---
# <a name="mfc-debugging-techniques"></a>MFC Hata Ayıklama Teknikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MFC programı hata ayıklaması yapıyorsanız, bu hata ayıklama teknikleri yararlı olabilir.  
  
##  <a name="BKMK_In_this_topic"></a> Bu konudaki  
 [AfxDebugBreak](#BKMK_AfxDebugBreak)  
  
 [TRACE makrosu](#BKMK_The_TRACE_macro)  
  
 [Bellek MFC'de sızıntılarını algılama](#BKMK_Memory_leak_detection_in_MFC)  
  
- [Bellek ayırma izleme](#BKMK_Tracking_memory_allocations)  
  
- [Bellek tanılamayı etkinleştirme](#BKMK_Enabling_memory_diagnostics)  
  
- [Bellek anlık görüntü alma](#BKMK_Taking_memory_snapshots)  
  
- [Bellek istatistikleri görüntüleme](#BKMK_Viewing_memory_statistics)  
  
- [Alma nesne dökümünü yapar](#BKMK_Taking_object_dumps)  
  
  - [Bellek yorumlama dökümünü yapar](#BKMK_Interpreting_memory_dumps)  
  
  - [Özelleştirme nesnenin dökümünü yapar](#BKMK_Customizing_object_dumps)  
  
    [Bir MFC hata ayıklama derleme boyutunu küçültme](#BKMK_Reducing_the_size_of_an_MFC_Debug_build)  
  
  - [Seçili modüller için hata ayıklama bilgileri içeren bir MFC uygulaması oluşturma](#BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules)  
  
##  <a name="BKMK_AfxDebugBreak"></a> AfxDebugBreak  
 MFC sağlayan özel bir [AfxDebugBreak](http://msdn.microsoft.com/library/c4cd79b9-9327-4db5-a9d6-c4004a92aa30) işlevi kaynak kodunda kesme kodlamak için:  
  
```  
AfxDebugBreak( );  
  
```  
  
 Intel platformlarda `AfxDebugBreak` hangi sonlarını kaynak kod çekirdek kodu yerine aşağıdaki kodu üretir:  
  
```  
_asm int 3  
```  
  
 Diğer platformlarda `AfxDebugBreak` yalnızca çağıran `DebugBreak`.  
  
 Kaldırdığınızdan emin olun `AfxDebugBreak` deyimleri, bir yayın oluştururken oluşturun veya kullanın `#ifdef _DEBUG` bunları kapsamak için.  
  
 [Bu konudaki](#BKMK_In_this_topic)  
  
##  <a name="BKMK_The_TRACE_macro"></a> TRACE makrosu  
 Hata ayıklayıcıda programınızı alınan iletileri görüntülemek için [çıkış penceresine](../ide/reference/output-window.md), kullanabileceğiniz [ATLTRACE](http://msdn.microsoft.com/library/c796baa5-e2b9-4814-a27d-d800590b102e) makro veya MFC [izleme](http://msdn.microsoft.com/library/7b6f42d8-b55a-4bba-ab04-c46251778e6f) makrosu. Gibi [onaylar](../debugger/c-cpp-assertions.md), izleme makroları yalnızca programınızın hata ayıklama sürümü etkin ve sürümde derlendiğinde kaybolur.  
  
 Aşağıdaki örnekler kullanabileceğiniz yollardan bazılarını gösterir **izleme** makrosu. Gibi `printf`, **izleme** makrosu sayıda bağımsız değişken işleyebilir.  
  
```  
int x = 1;  
int y = 16;  
float z = 32.0;  
TRACE( "This is a TRACE statement\n" );  
  
TRACE( "The value of x is %d\n", x );  
  
TRACE( "x = %d and y = %d\n", x, y );  
  
TRACE( "x = %d and y = %x and z = %f\n", x, y, z );  
```  
  
 TRACE makrosu uygun şekilde char * hem wchar_t işleme\* parametreleri. Aşağıdaki örnekler, farklı dize parametre türleri ile birlikte izleme makrosu kullanımını göstermektedir.  
  
```  
TRACE( "This is a test of the TRACE macro that uses an ANSI string: %s %d\n", "The number is:", 2);  
  
TRACE( L"This is a test of the TRACE macro that uses a UNICODE string: %s %d\n", L"The number is:", 2);  
  
TRACE( _T("This is a test of the TRACE macro that uses a TCHAR string: %s %d\n"), _T("The number is:"), 2);  
  
```  
  
 Daha fazla bilgi için **izleme** makro bkz [tanı Hizmetleri](http://msdn.microsoft.com/library/8d78454f-9fae-49c2-88c9-d3fabd5393e8).  
  
 [Bu konudaki](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Memory_leak_detection_in_MFC"></a> Bellek MFC'de sızıntılarını algılama  
 Ayrılmış olan, ancak hiçbir zaman serbest bellek algılamak için MFC sınıfları ve işlevleri sağlar.  
  
###  <a name="BKMK_Tracking_memory_allocations"></a> Bellek ayırma izleme  
 MFC içinde makro kullanabilirsiniz [DEBUG_NEW](http://msdn.microsoft.com/library/9b379344-4093-4bec-a3eb-e0d8a63ada9d) yerine **yeni** sızıntıları bellek bulmak için işleci. Programınızın hata ayıklama sürümünde `DEBUG_NEW` ayırdığı her nesne için dosya adı ve satır numarası izler. Programınızı sürümünü derlediğinizde `DEBUG_NEW` çözümler için basit bir **yeni** dosya adı ve satır numarası bilgileri olmadan işlem. Bu nedenle, programınızı yayın sürümünde hiçbir hız ceza öder.  
  
 Yeniden kullanmak için tüm programınızı istemiyorsanız `DEBUG_NEW` yerine **yeni**, kaynak dosyalarınızda Bu makroyu tanımlayabilirsiniz:  
  
```  
#define new DEBUG_NEW  
```  
  
 Bunu yaptığınızda bir [nesne döküm](#BKMK_Taking_object_dumps), her bir nesne ile ayrılan `DEBUG_NEW` burada ayrıldı, dosya ve satır numarasını gösterir bellek sızıntılarının kaynağı belirlemenize olanak sağlar.  
  
 MFC çerçevesi hata ayıklama sürümünü kullanan `DEBUG_NEW` otomatik olarak, ancak kodunuz yoktur. Avantajlarını istiyorsanız `DEBUG_NEW`, kullanmalısınız `DEBUG_NEW` açıkça veya **#define yeni** yukarıda da gösterildiği gibi.  
  
 [Bu konudaki](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Enabling_memory_diagnostics"></a> Bellek tanılamayı etkinleştirme  
 Bellek Tanılama özelliklerini kullanabilmeniz için Tanılama izleme etkinleştirmeniz gerekir.  
  
 **Etkinleştirme veya devre dışı Bellek Tanılama**  
  
- Genel işlev çağrısı [AfxEnableMemoryTracking](http://msdn.microsoft.com/library/0a40e0c4-855d-46e2-9577-a8f2346f47db) etkinleştirme veya devre dışı tanılama bellek ayırıcısı. Bellek Tanılama üzerinde varsayılan olarak hata ayıklama kitaplığı olduğundan, genellikle programı yürütme hızını artırır ve tanılama çıkışı azaltan geçici olarak devre dışı kapatmak için bu işlevi kullanın.  
  
  **AfxMemDF ile özel bellek tanılama özellikleri seçmek için**  
  
- Bellek Tanılama özellikleri üzerinde daha kesin denetim istiyorsanız, seçmeli olarak tek tek Bellek Tanılama özellikleri açıp MFC genel değişkeninin değerini ayarlayarak kapatabilirsiniz [afxMemDF](http://msdn.microsoft.com/library/cf117501-5446-4fce-81b3-f7194bc95086). Bu değişken bir listeden seçimli türü tarafından belirtilen aşağıdaki değerleri içerebilir **afxMemDF**.  
  
  |Değer|Açıklama|  
  |-----------|-----------------|  
  |**allocMemDF**|Tanılama bellek ayırıcısı (varsayılan) üzerinde açın.|  
  |**delayFreeMemDF**|Gecikme çağırırken bellek boşaltma `delete` veya `free` kadar programdan çıkılır. Bu, olası maksimum bellek miktarı ayrılacak programınızı neden olur.|  
  |**checkAlwaysMemDF**|Çağrı [AfxCheckMemory](http://msdn.microsoft.com/library/4644da71-7d14-41dc-adc0-ee9558fd7a28) bellek tahsis veya serbest her zaman.|  
  
   Bu değerleri birlikte bir mantıksal OR işlemi gerçekleştirerek burada gösterildiği gibi kullanılabilir:  
  
  ```cpp  
  afxMemDF = allocMemDF | delayFreeMemDF | checkAlwaysMemDF;  
  ```  
  
  [Bu konudaki](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Taking_memory_snapshots"></a> Bellek anlık görüntü alma  
  
1. Oluşturma bir [CMemoryState](http://msdn.microsoft.com/en-us/8fade6e9-c6fb-4b2a-8565-184a912d26d2) nesne ve çağrı [CMemoryState::Checkpoint](http://msdn.microsoft.com/library/b2d80fea-3d21-457e-816d-b035909bf21a) üye işlevi. Bu ilk bellek anlık görüntüsünü oluşturur.  
  
2. Programınızı bellek ayırmayı ve ayırmayı kaldırma işlemlerini gerçekleştirdikten sonra başka bir oluşturma `CMemoryState` nesne ve çağrı `Checkpoint` bu nesne. Bu, ikinci bir bellek kullanımı anlık görüntüsünü alır.  
  
3. Bir üçüncü oluşturma `CMemoryState` nesne ve çağrı kendi [CMemoryState::Difference](http://msdn.microsoft.com/library/aba69e2f-71dd-4255-99b5-3da2e56a0c9c) üye işlevi, önceki iki bağımsız değişken olarak sağlama `CMemoryState` nesneleri. İki bellek durumu arasında bir fark varsa `Difference` işlevi sıfır olmayan bir değer döndürür. Bu, bazı bellek blokları serbest olduğunu gösterir.  
  
    Bu örnek kodu nasıl göründüğünü gösterir:  
  
   ```  
   // Declare the variables needed  
   #ifdef _DEBUG  
       CMemoryState oldMemState, newMemState, diffMemState;  
       oldMemState.Checkpoint();  
   #endif  
  
       // Do your memory allocations and deallocations.  
       CString s("This is a frame variable");  
       // The next object is a heap object.  
      CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
  
   #ifdef _DEBUG  
       newMemState.Checkpoint();  
       if( diffMemState.Difference( oldMemState, newMemState ) )  
       {  
           TRACE( "Memory leaked!\n" );  
       }  
   #endif  
   ```  
  
    Bellek denetimi deyimleri tarafından köşeli parantez içindeki bildirimi `#ifdef` [_DEBUG](http://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a)/ **#endif** yalnızca programınızın hata ayıklama sürümleri derlenmiş engeller.  
  
    Bir bellek sızıntısı olduğunu bildiğiniz, başka bir üye işlevi kullanabilirsiniz [CMemoryState::DumpStatistics](http://msdn.microsoft.com/library/90d5f281-b92f-4725-a996-23ab94cf4b5d) yardımcı olacak bulun.  
  
   [Bu konudaki](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Viewing_memory_statistics"></a> Bellek istatistikleri görüntüleme  
 [CMemoryState::Difference](http://msdn.microsoft.com/library/aba69e2f-71dd-4255-99b5-3da2e56a0c9c) işlevi iki bellek durumu nesnede arar ve yığın başlangıcını ve bitişini durumlar arasında öğesinden serbest değil herhangi bir nesne algılar. Bellek anlık görüntüler ve bunları karşılaştırıldığında sonra kullanarak `CMemoryState::Difference`, çağırabilirsiniz [CMemoryState::DumpStatistics](http://msdn.microsoft.com/library/90d5f281-b92f-4725-a996-23ab94cf4b5d) serbest nesneler hakkında bilgi almak için.  
  
 Aşağıdaki örnek göz önünde bulundurun:  
  
```  
if( diffMemState.Difference( oldMemState, newMemState ) )  
{  
   TRACE( "Memory leaked!\n" );  
   diffMemState.DumpStatistics();  
}  
```  
  
 Bir örnek dökümü örnek şöyle görünür:  
  
```  
0 bytes in 0 Free Blocks  
22 bytes in 1 Object Blocks  
45 bytes in 4 Non-Object Blocks  
Largest number used: 67 bytes  
Total allocations: 67 bytes  
```  
  
 Ücretsiz taşlarıdır olan ayırmayı kaldırma durumunda gecikir blokları `afxMemDF` ayarlandı `delayFreeMemDF`.  
  
 Sıradan nesne blokları, ikinci satırda gösterilen yığında ayrılmış şekilde kalır.  
  
 Nesne olmayan blokları içerecek diziler ve yapılar ile ayrılmış `new`. Bu durumda, nesne olmayan bloklar dört yığın üzerinde ayrılan ancak serbest.  
  
 `Largest number used` herhangi bir zamanda program tarafından kullanılan en fazla belleği sunar.  
  
 `Total allocations` Toplam program tarafından kullanılan bellek miktarı sağlar.  
  
 [Bu konudaki](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Taking_object_dumps"></a> Alma nesne dökümünü yapar  
 Bir MFC programında kullanabilirsiniz [CMemoryState::DumpAllObjectsSince](http://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2) açıklamasını serbest yığınındaki tüm nesnelerin dökümünü almak için. `DumpAllObjectsSince` en son ayrılan tüm nesneler dökümleri [CMemoryState::Checkpoint](http://msdn.microsoft.com/library/b2d80fea-3d21-457e-816d-b035909bf21a). Hayır ise `Checkpoint` çağrısı bir yerde harcanan `DumpAllObjectsSince` tüm nesneleri ve bellekte bulunan nonobjects dökümünü yapar.  
  
> [!NOTE]
>  MFC nesne dökme kullanabilmeniz için önce şunları yapmalısınız [tanılama izlemeyi etkinleştirme](../debugger/mfc-debugging-techniques.md#BKMK_Enabling_Memory_Diagnostics).  
  
> [!NOTE]
>  MFC programınızı çıktığında, otomatik olarak tüm sızan nesne dökümleri, dökümünü almak için kod oluşturmaya gerek kalmayacak şekilde bu noktada nesneleri.  
  
 Aşağıdaki kod, iki bellek durumlarını karşılaştırma tarafından bir bellek sızıntısı için test eder ve sızıntı algılanması durumunda tüm nesnelerin dökümünü alır.  
  
```  
if( diffMemState.Difference( oldMemState, newMemState ) )  
{  
   TRACE( "Memory leaked!\n" );  
   diffMemState.DumpAllObjectsSince();  
}  
```  
  
 Döküm içeriğini şöyle görünür:  
  
```  
Dumping objects ->  
  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
  
{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long  
```  
  
 Satırların çoğu sayıda başına köşeli ayraçlar içinde nesnelere ayrılan sırasını belirtin. En son ayrılmış nesne en yüksek sayıyı ve döküm üstünde görünür.  
  
 Bir nesne döküm dışında en çok bilgi almak için kılabilirsiniz `Dump` üye işlevi herhangi `CObject`-türetilmiş bir nesneye nesne döküm özelleştirmek için.  
  
 Genel değişkeni ayarlayarak, belirli bellek ayırmada bir kesme noktası ayarlayabilirsiniz `_afxBreakAlloc` küme ayraçları içinde gösterilen sayıya. Programı yeniden çalıştırın, bu ayırma gerçekleştiğinde, hata ayıklayıcı yürütmeyi keser. Ardından, programınızın o noktaya nasıl alındı görmek için çağrı yığınını da bakabilirsiniz.  
  
 C çalışma zamanı kitaplığı benzer bir işlev olan [_CrtSetBreakAlloc](http://msdn.microsoft.com/library/33bfc6af-a9ea-405b-a29f-1c2d4d9880a1), C çalışma zamanı ayırmalar için kullanabilirsiniz.  
  
 [Bu konudaki](#BKMK_In_this_topic)  
  
####  <a name="BKMK_Interpreting_memory_dumps"></a> Bellek yorumlama dökümünü yapar  
 Bu nesne döküm daha ayrıntılı bakın:  
  
```  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
  
{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long  
```  
  
 Bu döküm oluşturulan programı yalnızca iki açık ayırmaları vardı — bir yığın ve yığındaki:  
  
```  
// Do your memory allocations and deallocations.  
CString s("This is a frame variable");  
// The next object is a heap object.  
CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
```  
  
 `CPerson` Oluşturucusu işaretçileri olan üç bağımsız değişken alır `char`, başlatmak için kullanılan `CString` üye değişkenleri. Bellek dökümü gördüğünüz `CPerson` nonobject blokları üç (3, 4 ve 5) ile birlikte bir nesne. Bu karakterler için tutmak `CString` üye değişkenleri ve ne zaman silinmeyecek `CPerson` nesne yok Edicisi çağrılır.  
  
 2 blok sayıdır `CPerson` nesnenin kendisi. `$51A4` Blok adresini temsil eder ve tarafından çıkarılan nesne içeriğini arkasından `CPerson`::`Dump` çağrıldığında [DumpAllObjectsSince](http://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2).  
  
 Blok numarası 1 ile ilişkili olduğunu tahmin `CString` çerçeve değişkeni, sıra numarası ve çerçeve karakter sayısı ile eşleşen boyutu nedeniyle `CString` değişkeni. Çerçeve kapsam dışına çıktığında karesinde ayırma değişkenlerinde otomatik olarak serbest bırakılır.  
  
 **Çerçeve değişkenleri**  
  
 Genel olarak, çerçeve değişkenlerin kapsam dışına olduğunuzda, bunlar otomatik olarak serbest olmadığından çerçeveyi değişkenlerle ilişkili yığın nesnelerini hususlara değil. Bellek Tanılama bilgi dökümleri dağınıklığı önlemek için aramalarınız konumlandırma `Checkpoint` çerçeve değişkenleri kapsamında olmasını sağlamak. Örneğin, burada gösterildiği gibi önceki ayırma kod kapsamı ayraç koyun:  
  
```  
oldMemState.Checkpoint();  
{  
    // Do your memory allocations and deallocations ...  
    CString s("This is a frame variable");  
    // The next object is a heap object.  
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
}  
newMemState.Checkpoint();  
```  
  
 Kapsam köşeli parantez ile yerinde, bu örnek için bellek dökümü aşağıdaki gibidir:  
  
```  
Dumping objects ->  
  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
```  
  
 **Nonobject ayırmalar**  
  
 Bazı ayırmaları nesneleri olduğuna dikkat edin (gibi `CPerson`) ve nonobject ayırmaları bazılarıdır. Nesneleri türetilmemiş için "Nonobject ayırmaları" olan ayırmaları `CObject` veya ayırmaları gibi basit C türlerin `char`, `int`, veya **uzun**. Varsa **CObject -** türetilmiş sınıf iç arabellek için nesneleri ayırmaların hem nesne hem de nonobject gösterecektir gibi ek alan ayırır.  
  
 **Bellek sızıntılarını önleme**  
  
 Yukarıdaki kodda bellek bloğu ile ilişkili fark `CString` çerçeve değişken otomatik olarak serbest ve bir bellek sızıntısı olarak görünmez. Kapsama kuralları ile ilişkili otomatik ayırmayı kaldırma çerçeve değişkenleri ile ilişkili en fazla bellek sızıntılarının üstlenir.  
  
 Yığında ayrılmış nesneler için ancak, açıkça bir bellek sızıntısı önlemek için nesne silmeniz gerekir. Önceki örnekte son bellek sızıntısı temizlemek için silme `CPerson` gibi yığında ayrılmış nesne:  
  
```  
{  
    // Do your memory allocations and deallocations.  
    CString s("This is a frame variable");  
    // The next object is a heap object.  
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
    delete p;  
}  
```  
  
 [Bu konudaki](#BKMK_In_this_topic)  
  
####  <a name="BKMK_Customizing_object_dumps"></a> Özelleştirme nesnenin dökümünü yapar  
 Türetilen bir sınıftan zaman [CObject](http://msdn.microsoft.com/library/95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a), geçersiz kılabilirsiniz `Dump` kullandığınızda, ek bilgi sağlamak için üye işlevi [DumpAllObjectsSince](http://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2) döküm nesnelere [Çıkış penceresine](../ide/reference/output-window.md).  
  
 `Dump` İşlevi için bir döküm bağlam değişkenleri nesnenin üye değerinin metinsel bir gösterimini yazar ([CDumpContext](http://msdn.microsoft.com/library/98c52b2d-14b5-48ed-b423-479a4d1c60fa)). Döküm bağlamı bir g/ç akışına benzerdir. Append işlecini kullanabilirsiniz (**<<**) veri göndermesini bir `CDumpContext`.  
  
 Ne zaman geçersiz kılmanız `Dump` işlevi, temel sınıf sürümü ilk çağırmalıdır `Dump` temel sınıf nesnenin içeriğini dökümünü almak için. Ardından bir metinsel ve türetilmiş sınıfınızın her üye değişkeni için değer çıktı.  
  
 Bildirimi `Dump` işlevi şu şekilde görünür:  
  
```  
class CPerson : public CObject  
{  
public:  
#ifdef _DEBUG  
    virtual void Dump( CDumpContext& dc ) const;  
#endif  
  
    CString m_firstName;  
    CString m_lastName;  
    // And so on...  
};  
```  
  
 Bildirimi, programınızın hata ayıklama işlemi yaparken nesne dökme yalnızca anlamlı olduğundan `Dump` ile işlevi ayraçlı bir **#ifdef _DEBUG / #endif** blok.  
  
 Aşağıdaki örnekte, `Dump` işlev çağrılarında ilk `Dump` işlevi için temel sınıfı. Ardından üyenin değeri yanı sıra her bir üye değişkeni kısa bir açıklamasını tanılama akışa yazar.  
  
```  
#ifdef _DEBUG  
void CPerson::Dump( CDumpContext& dc ) const  
{  
    // Call the base class function first.  
    CObject::Dump( dc );  
  
    // Now do the stuff for our specific class.  
    dc << "last name: " << m_lastName << "\n"  
        << "first name: " << m_firstName << "\n";  
}  
#endif  
```  
  
 Siz sağlamalısınız bir `CDumpContext` dökümünün çıkışını gidecekleri belirtmek için bağımsız değişken. MFC hata ayıklama sürümünü önceden tanımlanmış bir sağlayan `CDumpContext` adlı nesne `afxDump` hata ayıklayıcıya çıktı gönderen.  
  
```  
CPerson* pMyPerson = new CPerson;  
// Set some fields of the CPerson object.  
//...  
// Now dump the contents.  
#ifdef _DEBUG  
pMyPerson->Dump( afxDump );  
#endif  
```  
  
 [Bu konudaki](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Reducing_the_size_of_an_MFC_Debug_build"></a> Bir MFC hata ayıklama derleme boyutunu küçültme  
 Büyük bir MFC uygulaması için hata ayıklama bilgileri bir çok disk alanı kaplar. Boyutunu azaltmak için aşağıdaki yordamlardan birini kullanabilirsiniz:  
  
1. MFC kitaplıklarını kullanarak yeniden [/z7, / zi, /zı (hata ayıklama bilgileri biçimi)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) seçeneği yerine **/z7**. Bu seçenekler, tüm kitaplığı yedeklilik azaltarak ve alanından tasarruf etme, hata ayıklama bilgilerini içeren tek bir program veritabanı (PDB) dosyası oluşturun.  
  
2. Hata ayıklama bilgileri olmadan MFC kitaplıkları yeniden (hiçbir [/z7, / zi, /zı (hata ayıklama bilgileri biçimi)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) seçeneği). Bu durumda, hata ayıklama bilgileri eksikliği MFC kitaplık kodu içinde birçok hata ayıklayıcı tesislerini kullanmanızı engeller ancak MFC kitaplıklarını hata ayıklama zaten kapsamlı olduğundan, bu bir sorun olmayabilir.  
  
3. Seçili modüller için hata ayıklama bilgileri ile kendi uygulamanızı yalnızca aşağıda açıklandığı gibi oluşturun.  
  
   [Bu konudaki](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules"></a> Seçili modüller için hata ayıklama bilgileri içeren bir MFC uygulaması oluşturma  
 MFC hata ayıklama kitaplıkları ile seçilen modüllerini oluşturmak, Adımlama kullanmanıza ve bu modüllerdeki diğer hata ayıklama özellikleri sağlar. Bu yordam hem bir hata ayıklama yararlanır ve bu nedenle aşağıdaki adımları (ve tam bir yayın yapısı gerekli olduğunda, gerekli yapmayı bir "tümünü yeniden derle" da) açıklanan değişiklikleri araya Visual C++ derleme görevleri modları bırakın.  
  
1. Çözüm Gezgini'nde projeyi seçin.  
  
2. Gelen **görünümü** menüsünde **özellik sayfaları**.  
  
3. İlk olarak, yeni bir proje yapılandırması oluşturur.  
  
   1.  İçinde  **\<Proje > özellik sayfaları** iletişim kutusu, tıklayın **Configuration Manager** düğmesi.  
  
   2.  İçinde [Configuration Manager iletişim kutusu](http://msdn.microsoft.com/en-us/fa182dca-282e-4ae5-bf37-e155344ca18b), kılavuz projenizi bulun. İçinde **yapılandırma** sütunundaki  **\<yeni … >**.  
  
   3.  İçinde [yeni proje yapılandırması iletişim kutusu](http://msdn.microsoft.com/en-us/cca616dc-05a6-4fe3-bdc1-40c72a66f2be), "Kısmi Debug" gibi yeni yapılandırma için bir ad yazın **proje yapılandırması adı** kutusu.  
  
   4.  İçinde **Ayarları Şuradan Kopyala:** listesinde **yayın**.  
  
   5.  Tıklayın **Tamam** kapatmak için **yeni proje yapılandırması**iletişim kutusu.  
  
   6.  Kapat **Configuration Manager** iletişim kutusu.  
  
4. Şimdi, seçenekleri tüm proje için ayarlanır.  
  
   1.  İçinde **özellik sayfaları** iletişim kutusunun **yapılandırma özellikleri** klasörüne **genel** kategorisi.  
  
   2.  Proje ayarları kılavuzunda genişletin **Proje Varsayılanları** (gerekirse).  
  
   3.  Altında **Proje Varsayılanları**, bulma **MFC kullanımı**. Geçerli ayarı kılavuz sağ sütunda görüntülenir. Geçerli ayarını'a tıklayın ve değiştirmek için **MFC'yi statik kitaplıkta**.  
  
   4.  Sol bölmesinde **özellikler sayfaları** açık iletişim kutusunu **C/C++** klasörü ve select **önişlemci**. Özellik kılavuzunda Bul **önişlemci tanımları** ve "NDEBUG" "_DEBUG" ile değiştirin.  
  
   5.  Sol bölmesinde **özellikler sayfaları** açık iletişim kutusunu **bağlayıcı** klasörü ve select **giriş** kategorisi. Özellik kılavuzunda Bul **ek bağımlılıklar**. İçinde **ek bağımlılıklar** ayarını "NAFXCWD. yazın LIB"ve"LIBCMT."  
  
   6.  Tıklayın **Tamam** yeni derleme seçenekleri kaydedip kapatmak için **özellik sayfaları** iletişim kutusu.  
  
5. Gelen **derleme** menüsünde **yeniden**. Bu, tüm hata ayıklama bilgileri, modüllerden kaldırır ancak MFC Kitaplığı etkilemez.  
  
6. Artık, hata ayıklama bilgileri geri seçili modüller için uygulamanıza eklemeniz gerekir. Kesme noktaları ayarlayın ve yalnızca hata ayıklama bilgileri ile derlenmiş modülleri'nde diğer hata ayıklayıcı işlevleri gerçekleştirmek unutmayın. Dahil etmek istediğiniz her proje dosyası için hata ayıklama bilgileri, aşağıdaki adımları izleyin:  
  
   1.  Çözüm Gezgini'nde açın **kaynak dosyaları** klasörünün altında projenizin.  
  
   2.  Hata ayıklama bilgileri için ayarlamak istediğiniz dosyayı seçin.  
  
   3.  Gelen **görünümü** menüsünde **özellik sayfaları**.  
  
   4.  İçinde **özellik sayfaları** iletişim kutusunun **yapılandırma ayarlarını** açık klasör **C/C++** klasör seçip **genel** Kategori.  
  
   5.  Özellik kılavuzunda Bul **hata ayıklama bilgi biçimi.**  
  
   6.  Tıklayın **hata ayıklama bilgi biçimi** ayarları ve istediğiniz seçeneği işaretleyin (genellikle **/zi**) için hata ayıklama bilgileri.  
  
   7.  Bir uygulama Sihirbazı tarafından oluşturulan bir uygulama kullanarak veya önceden derlenmiş üst bilgiler, önceden derlenmiş üstbilgileri devre dışı bırakın veya diğer modüller derlenmeden önce yeniden derlemeniz gerekir. Aksi takdirde, uyarı C4650 ve C2855 hata iletisi alırsınız. Önceden derlenmiş üst bilgiler değiştirerek etkinleştirebilirsiniz **önceden derlenmiş üst bilgi Oluştur/Kullan** ayarı  **\<Proje > Özellikleri** iletişim kutusu (**yapılandırma özellikleri**  klasöründe **C/C++** alt, **önceden derlenmiş üst bilgiler** kategorisi).  
  
7. Gelen **derleme** menüsünde **derleme** eski proje dosyalarını yeniden oluşturmak için.  
  
   Alternatif yöntem için bu konuda açıklandığı gibi her dosya için tek tek seçenek tanımlamak için dış bir derleme görevleri dosyası kullanabilirsiniz. Bu durumda, MFC hata ayıklama kitaplıklarıyla bağlamak için tanımlamalısınız [_DEBUG](http://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) her bir modül için bayrak. MFC sürüm kitaplıkları kullanmak istiyorsanız, NDEBUG tanımlamanız gerekir. Dış derleme görevleri dosyası yazma ile ilgili daha fazla bilgi için bkz: [NMAKE başvurusu](http://msdn.microsoft.com/library/0421104d-8b7b-4bf3-86c1-928d9b7c1a8c).  
  
   [Bu konudaki](#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual C++ hata ayıklama](../debugger/debugging-native-code.md)



