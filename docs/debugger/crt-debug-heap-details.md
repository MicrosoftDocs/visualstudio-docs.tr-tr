---
title: CRT hata ayıklama öbeği ayrıntıları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug heap, accessing
- heap functions
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CrtMemDumpStatistics function
- debugging [C++], debug heap
- _CRT_BLOCK macro
- DBGINT.H file
- _CrtMemDumpAllObjectsSince function
- _crtBreakAlloc global variable
- _CrtMemState function
- _CLIENT_BLOCK macro
- _FREE_BLOCK block
- _CrtMemBlockHeader function
- heap state reporting functions
- _CRTDBG_ALLOC_MEM_DF macro
- _CrtSetBreakAlloc function
- memory blocks, allocation types on debug heap
- debugging [C++], CRT debug support
- debug heap, tracking heap allocation requests
- memory allocation, debug heap
- _NORMAL_BLOCK block
- crtBreakAlloc global variable
- _CrtDoForAllClientObjects function
- new operator, using debug heap from C++
- _CrtSetDumpClient function
- debugging [CRT], heap-related problems
- debug heap, solving memory allocation problems
- _CrtMemCheckpoint function
- debug builds, linking to debug heap
- _IGNORE_BLOCK block
- _crtDbgFlag function
- client blocks, specifying subtypes
- memory leaks, tracking
- _CrtSetDbgFlag function
- nBlockUse method
- memory leaks, CRT debug library functions
- _CRTDBG_DELAY_FREE_MEM_DF macro
- allocation request numbers
- _CRTDBG_LEAK_CHECK_DF macro
- debug heap
- memory, debugging
- _CrtReportBlockType function
- _CrtDumpMemoryLeaks function
- _CrtCheckMemory function
- debug heap, CRT
- memory blocks, free
- _BLOCK_TYPE macro
- debug heap, memory blocks
- heap allocation, debug
- debugging memory leaks
- _BLOCK_SUBTYPE macro
- debug heap, using from C++
- _CrtMemDifference function
- heap allocation, tracking requests
- debugging [Visual Studio], debug heap
- delete operator, using debug heap from C++
- blocks, types of on the debug heap
- _CRTDBG_CHECK_CRT_DF macro
- debug heap, reporting functions
ms.assetid: bf78ace6-28e4-4a04-97c6-39e0cdd00ba4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df3dbcd36bdb72bdd76972ff03a295ba9310f8f7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897088"
---
# <a name="crt-debug-heap-details"></a>CRT Hata Ayıklama Öbeği Ayrıntıları
Bu konu, CRT hata ayıklama yığınındaki ayrıntılı bilgi sağlar.  
  
##  <a name="BKMK_Contents"></a> İçeriği  
 [Arabellek taşmaları ile hata ayıklama Kaçağı bulma](#BKMK_Find_buffer_overruns_with_debug_heap)  
  
 [Hata ayıklama öbek üzerindeki blokları türleri](#BKMK_Types_of_blocks_on_the_debug_heap)  
  
 [Yığın bütünlüğü ve bellek sızıntıları denetle](#BKMK_Check_for_heap_integrity_and_memory_leaks)  
  
 [Hata ayıklama yığınını yapılandırma](#BKMK_Configure_the_debug_heap)  
  
 [Yeni, silme ve _clıent_blocks C++ hata ayıklama yığını](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)  
  
 [Öbek durumu raporlama işlevleri](#BKMK_Heap_State_Reporting_Functions)  
  
 [Parça yığın ayırma istekleri](#BKMK_Track_Heap_Allocation_Requests)  
  
##  <a name="BKMK_Find_buffer_overruns_with_debug_heap"></a> Arabellek taşmaları ile hata ayıklama Kaçağı bulma  
 Programcıların karşılaştığı en yaygın ve izlenebilir sorunların ikisi (artık gerekli olmayan ayırmalar serbest bırakılamıyor) ayrılan bir arabellek ve bellek sızıntıları sonuna üzerine yazıyor. Hata ayıklama öbeği bu tür bellek ayırma sorunlarını çözmek için güçlü araçlar sağlar.  
  
 Hata ayıklama yığın işlevlerin sürümleri sürümde kullanılan standart veya temel sürümleri çağırır oluşturur. Bir bellek bloğunu istediğinizde, hata ayıklama yığını Yöneticisi temel yığından biraz daha büyük bir, o blok kısmı için bir işaretçi döndürür ve istenen bellek bloğu ayırır. Örneğin, uygulamanızın çağrısını içerdiğini varsayın: `malloc( 10 )`. Derleme, [malloc](/cpp/c-runtime-library/reference/malloc) 10 bayt ayırma isteyen temel yığın ayırma rutinin çağırın. Ancak, bir hata ayıklama derlemesinde `malloc` çağıracak [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg), hangi ' ı çağırın yanı sıra yaklaşık 36 bayt bellek ek bir 10 bayt ayırma isteyen temel yığın ayırma rutinin. Hata ayıklama yığınında sonuçta elde edilen tüm bellek blokları, ayrıldığı göre sıralanmış tek bir bağlantılı listede bağlanır.  
  
 Hata ayıklama yığın yordamları tarafından ayrılmış ek bellek bağlantısı hata ayıklama bellek bloklarını birlikte ve yakalamak için verilerinizin her iki tarafındaki küçük arabellekler için yazıldığını ve ayrılan bölgenin işaretçileri, muhasebe bilgileri kullanılır.  
  
 Şu anda, hata ayıklama yığınının muhasebe bilgilerini depolamak için kullanılan blok üstbilgisi yapısı içinde DBGINT şu şekilde bildirilir. H üst bilgi dosyası:  
  
```cpp
typedef struct _CrtMemBlockHeader  
{  
// Pointer to the block allocated just before this one:  
    struct _CrtMemBlockHeader *pBlockHeaderNext;  
// Pointer to the block allocated just after this one:  
    struct _CrtMemBlockHeader *pBlockHeaderPrev;  
    char *szFileName;    // File name  
    int nLine;           // Line number  
    size_t nDataSize;    // Size of user block  
    int nBlockUse;       // Type of block  
    long lRequest;       // Allocation number  
// Buffer just before (lower than) the user's memory:  
    unsigned char gap[nNoMansLandSize];  
} _CrtMemBlockHeader;  
  
/* In an actual memory block in the debug heap,  
 * this structure is followed by:  
 *   unsigned char data[nDataSize];  
 *   unsigned char anotherGap[nNoMansLandSize];  
 */  
```  
  
 `NoMansLand` Blok kullanıcı veri alanının her iki tarafındaki arabellekleri şu anda 4 bayt boyutundadır ve sınırları kullanıcının bellek bloğu sınırlarının üzerine yazılmadığını olduğunu doğrulamak için hata ayıklama yığın rutinleri tarafından kullanılan bilinen bayt değeri ile doldurulur. Hata ayıklama öbeği ayrıca yeni bellek bloklarını bilinen bir değerle doldurur. Bırakılmış blokları yığının bağlantılı listesinde aşağıda açıklandığı gibi tutmayı seçerseniz, bu bırakılmış bloklar da bilinen bir değerle doldurulur. Şu anda kullanılan gerçek bayt değerleri şunlardır:  
  
 NoMansLand (0xFD)  
 Bir uygulama tarafından kullanılan belleğin her iki tarafındaki "NoMansLand" arabellekler, şu anda 0xFD ile doludur.  
  
 Boşaltılmış bloklar (0xDD)  
 Tutulan bırakılmış bloklar hata ayıklama yığınının bağlantılı listesinde `_CRTDBG_DELAY_FREE_MEM_DF` bayrağı ayarlandığında şu anda 0xDD ile doldurulur.  
  
 Yeni nesneler (0xCD)  
 Yeni nesneler ayrıldıkları zaman 0xCD ile doldurulmuştur.  
  
 ![Başa dön](../debugger/media/pcs_backtotop.png "PCS_BackToTop")  
  
 ![Başa dön](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_Types_of_blocks_on_the_debug_heap"></a> Hata ayıklama öbek üzerindeki blokları türleri  
 Hata ayıklama yığınındaki her bellek bloğu, beş ayırma türünden birine atanır. Bu tür izlenir ve sızıntı algılaması ve durum raporlama amaçları için farklı bildirdi. Hata ayıklama yığın ayırma işlevlerinden birine doğrudan çağrı aşağıdaki gibi kullanarak ayırarak bir bloğu ayırıp, türünü belirtebilirsiniz [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). Bellek bloklarını hata ayıklama yığınındaki beş tip (kümesinde **nBlockUse** üyesi **_CrtMemBlockHeader** yapısı) aşağıdaki gibidir:  
  
 **_NORMAL_BLOCK**  
 Bir çağrı [malloc](/cpp/c-runtime-library/reference/malloc) veya [calloc](/cpp/c-runtime-library/reference/calloc) Normal bir blok oluşturur. Yalnızca Normal blokları kullanmaya ve istemci blokları gerek sahip olmasını istiyorsanız, tanımlamak isteyebilirsiniz [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), hangi tüm yığın ayırma çağrılarına neden hata ayıklama yapılarında hata ayıklama eşdeğerleriyle eşlenmiş. Bu dosya adı ve satır numarası bilgilerinin ilgili öbek üstbilgisinde depolanması için her bir ayırma çağrısıyla ilgili olanak tanır.  
  
 `_CRT_BLOCK`  
 Bunlar ayrı olarak işlenebilmeleri birçok çalışma zamanı kitaplığı işlevleri tarafından dahili olarak ayrılan bellek blokları blokları CRT işaretlenir. Sonuç olarak, sızıntı algılama ve diğer işlemler tarafından bunları etkilenmemesi gerekir. Ayırma gerekir hiçbir zaman ayırın, yeniden tahsis veya herhangi bir bloğu ayırmamalı ücretsiz.  
  
 `_CLIENT_BLOCK`  
 Bir uygulama belirli bir grupta bellek bloğu, hata ayıklama yığın işlevlerine yapılan açık çağrıları kullanarak bu türü olarak ayırarak hata ayıklama amacıyla ayırma grubunun özel izini tutabilir. MFC, örneğin, ayırdığı tüm **CObjects** istemci bloklar olarak; diğer uygulamalar istemci bloklarda farklı bellek nesneleri tutabilir. İstemci blokların alt türleri de büyük parçalı yapı izleme için belirtilebilir. İstemci blokların alt türleri belirtmek için kaç kaydırma 16 sola ve `OR` kendisiyle `_CLIENT_BLOCK`. Örneğin:  
  
```cpp
#define MYSUBTYPE 4  
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));  
```  
  
 İstemci bloklarında depolanan nesnelerin dökümünü almak için bir istemci tarafından sağlanan bir kanca işlevi kullanılarak yüklenebilir [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient)ve ardından her bir hata ayıklama işlevi tarafından istemci bloğunun dökümü yapıldığında çağrılır. Ayrıca, [_CrtDoForAllClientObjects](/cpp/c-runtime-library/reference/crtdoforallclientobjects) hata ayıklama yığınındaki her istemci bloğu için uygulama tarafından sağlanan belirli bir işlevi çağırmak için kullanılabilir.  
  
 **_FREE_BLOCK**  
 Normalde, serbest bırakılan bloklar listeden kaldırılır. Denetlemek için serbest bırakılan belleğe hala yazılmakta olmadığını veya yetersiz bellek durumları benzetimini yapmak için serbest bırakılan bloklar bağlantılı listede serbest olarak işaretli ve bilinen bir bayt değeriyle (şu anda 0xDD) doldurulmuş tutmak seçebilirsiniz.  
  
 **_IGNORE_BLOCK**  
 Hata ayıklama yığın işlemleri bir süre devre dışı bırakmak mümkündür. Bu süre boyunca bellek blokları listede tutulur, ancak blokları Yoksay olarak işaretlenir.  
  
 Türünü ve belirli bir bloğu alt belirlemek için bu işlevi kullanın [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) ve makroları **_BLOCK_TYPE** ve **_BLOCK_SUBTYPE**. Makrolar (crtdbg.h) aşağıdaki gibi tanımlanır:  
  
```cpp
#define _BLOCK_TYPE(block)          (block & 0xFFFF)  
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)  
```  
  
 ![Başa dön](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a> Yığın bütünlüğü ve bellek sızıntıları denetle  
 Hata ayıklama öbek özelliklerin çoğu gelen kodunuz içinden erişilmelidir. Aşağıdaki bölümde bazı özellikler ve bunların nasıl kullanılacağı açıklanmaktadır.  
  
 `_CrtCheckMemory`  
 Bir çağrı kullanabileceğiniz [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory), örneğin, herhangi bir noktada yığının bütünlüğünü kontrol etmek için. Bu işlev yığınındaki her bellek bloğu inceler, bellek bloğu üst bilgi bilgileri geçerli olduğunu ve arabelleklerin değiştirilmemiş olduğunu doğrular.  
  
 `_CrtSetDbgFlag`  
 Nasıl hata ayıklama yığınının ayırmaları bir iç bayrağını kullanarak izler denetleyebilirsiniz [_crtDbgFlag](/cpp/c-runtime-library/crtdbgflag), hangi okunabilir ve kullanılarak ayarlanan [_CrtSetDbgFlag](/cpp/c-runtime-library/reference/crtsetdbgflag) işlevi. Bu bayrağı değiştirerek hata ayıklama yığınına program çıkış yaptığı andaki bellek sızıntılarını denetlemesini ve algılanan sızıntıları raporlamasını bildirebilirsiniz. Benzer şekilde, bırakılmış bellek bloklarının düşük bellek durumları benzetimini yapmak için bağlantılı listesinden Kaldırılmamasını belirtebilirsiniz. Yığın denetlendiğinde, rahatsız verilmemiş emin olmak için bu bırakılmış bloklar incelenir.  
  
 **_CrtDbgFlag** bayrak aşağıdaki bit alanlarını içerir:  
  
|Bit alanı|Varsayılan<br /><br /> value|Açıklama|  
|---------------|-----------------------|-----------------|  
|**_CRTDBG_ALLOC_MEM_DF**|Açık|Hata ayıklama ayırmayı etkinleştirir. Birbirine zincirlenmiş bu bit olduğunda kapalı, ayırmaları kalır ancak kendi blok türü **_ıgnore_block**.|  
|**_CRTDBG_DELAY_FREE_MEM_DF**|Kapalı|Bellek, aslında, düşük bellek koşulları benzetimi için olduğu gibi belleğin bırakılmasını engeller. Bu bit açık olduğunda, serbest bırakılan bloklar hata ayıklama yığının bağlantılı listesinde saklanır ancak olarak işaretlenmiş **_FREE_BLOCK** ve özel bir bayt değeriyle doldurulur.|  
|**_CRTDBG_CHECK_ALWAYS_DF**|Kapalı|Neden **_CrtCheckMemory** her ayırmayı ve ayırmayı kaldırma sırasında çağrılabilir. Bu yürütmeyi yavaşlatır, ancak hataları hızlı bir şekilde yakalar.|  
|**_CRTDBG_CHECK_CRT_DF**|Kapalı|Neden türü olarak işaretlenmiş blokların **_CRT_BLOCK** sızıntı algılama ve durum işlemlerinde dahil edilecek. Bu bit kapalıyken, çalışma zamanı kitaplığı tarafından dahili olarak kullanılan bellek bu tür işlemler sırasında yoksayılır.|  
|**_CRTDBG_LEAK_CHECK_DF**|Kapalı|Sızıntı denetlemesinin bir çağrı aracılığıyla program çıkışında gerçekleştirilmesine neden neden **_CrtDumpMemoryLeaks**. Uygulama, ayırdığı tüm belleği boşaltamazsa bir hata raporu oluşturulur.|  
  
 ![Başa dön](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_Configure_the_debug_heap"></a> Hata ayıklama yığınını yapılandırma  
 Gibi yığın işlevlerine yapılan tüm çağrılar `malloc`, `free`, `calloc`, `realloc`, `new`, ve `delete` hata ayıklama yığınında bu işlevleri hata ayıklama sürümleri çözümlenemiyor. Bir bellek öbeğini serbest bıraktığınızda, hata ayıklama yığınını otomatik olarak ayrılan alanınızın her iki tarafındaki arabelleklerin bütünlüğünü denetler ve üzerine yazma olduysa bir hata raporu yayınlar.  
  
 **Hata ayıklama yığınını kullanmak için**  
  
- Uygulamanızı hata ayıklama yapısını C çalışma zamanı kitaplığı hata ayıklama sürümü ile bağlayın.  
  
  **Bir veya birden çok _crtDbgFlag bit alanını değiştirmek ve yeni bir bayrak durumu oluşturmak için**  
  
1. Çağrı `_CrtSetDbgFlag` ile `newFlag` parametresini `_CRTDBG_REPORT_FLAG` (geçerli edinme `_crtDbgFlag` durumu) ve döndürülen değer, geçici bir değişkende depolayın.  
  
2. Tüm kapatma `OR`- ing (bit düzeyinde &#124; sembol) (uygulama kodunda bildirim sabitleriyle gösterilir) karşılık gelen bit maskesi ile geçici değişken.  
  
3. Diğer bitleri tarafından devre dışı bırakın `AND`- ing (bit düzeyinde & sembol) değişkenle bir `NOT` (bit düzeyinde ~ sembol), uygun bir bit maskesi.  
  
4. Çağrı `_CrtSetDbgFlag` ile `newFlag` yeni durumu oluşturmak üzere parametre ayarlamak geçici değişkende depolanan değere `_crtDbgFlag`.  
  
   Örneğin, aşağıdaki kod satırları otomatik sızıntı algılamayı açar ve tür bloklarının denetimini kapatır `_CRT_BLOCK`:  
  
```cpp
// Get current flag  
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );  
  
// Turn on leak-checking bit.  
tmpFlag |= _CRTDBG_LEAK_CHECK_DF;  
  
// Turn off CRT block checking bit.  
tmpFlag &= ~_CRTDBG_CHECK_CRT_DF;  
  
// Set flag to the new value.  
_CrtSetDbgFlag( tmpFlag );  
```  
  
 ![Başa dön](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a> Yeni, silme ve _clıent_blocks C++ hata ayıklama yığını  
 C++ hata ayıklama sürümü C çalışma zamanı kitaplığı hata ayıklama sürümlerini içeren `new` ve `delete` işleçleri. Kullanırsanız `_CLIENT_BLOCK` ayırma türü, hata ayıklama sürümünü çağırmalıdır `new` doğrudan işleci veya değiştiren makroları `new` aşağıdaki örnekte gösterildiği gibi hata ayıklama modunda, işleç:  
  
```cpp
/* MyDbgNew.h  
 Defines global operator new to allocate from  
 client blocks  
*/  
  
#ifdef _DEBUG  
   #define DEBUG_CLIENTBLOCK   new( _CLIENT_BLOCK, __FILE__, __LINE__)  
#else  
   #define DEBUG_CLIENTBLOCK  
#endif // _DEBUG  
  
/* MyApp.cpp  
        Use a default workspace for a Console Application to  
 *      build a Debug version of this code  
*/  
  
#include "crtdbg.h"  
#include "mydbgnew.h"  
  
#ifdef _DEBUG  
#define new DEBUG_CLIENTBLOCK  
#endif  
  
int main( )   {  
    char *p1;  
    p1 =  new char[40];  
    _CrtMemDumpAllObjectsSince( NULL );  
}  
```  
  
 Hata ayıklama sürümünü `delete` tüm blok işleç çalışır türleri ve bir yayım sürümünü derlediğinizde programınızda herhangi bir değişiklik gerektirmez.  
  
 ![Başa dön](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_Heap_State_Reporting_Functions"></a> Öbek durumu raporlama işlevleri  
 **_CrtMemState**  
  
 Belirli bir zamanda yığının durumunun Özet anlık görüntüsünü yakalamak için CRTDBG içinde tanımlanan _CrtMemState yapısını kullanın. Y:  
  
```cpp
typedef struct _CrtMemState  
{  
    // Pointer to the most recently allocated block:  
    struct _CrtMemBlockHeader * pBlockHeader;  
    // A counter for each of the 5 types of block:  
    size_t lCounts[_MAX_BLOCKS];  
    // Total bytes allocated in each block type:  
    size_t lSizes[_MAX_BLOCKS];  
    // The most bytes allocated at a time up to now:  
    size_t lHighWaterCount;  
    // The total bytes allocated at present:  
    size_t lTotalCount;  
} _CrtMemState;  
```  
  
 Bu yapı bir işaretçiyi hata ayıklama yığının bağlantılı listesinde ilk (en son ayrılmış) bloğa kaydeder. Daha sonra iki dizide onu her tür bellek kaç block kaydeder (_NORMAL_BLOCK, `_CLIENT_BLOCK`, _FREE_BLOCK, vb.) listesini ve her tür blokta ayrılan bayt sayısı. Son olarak, en fazla o noktaya kadar bir bütün olarak yığında ayrılan bayt sayısı ve şu anda ayrılan bayt sayısını kaydeder.  
  
 **Diğer CRT raporlama işlevleri**  
  
 Aşağıdaki işlevler yığının içeriği ve durumu raporu ve bellek sızıntıları ve diğer sorunların algılanmasına yardımcı olmak için bilgileri kullanın.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|[_CrtMemCheckpoint](/cpp/c-runtime-library/reference/crtmemcheckpoint)|Yığının anlık görüntüsünü kaydeder bir **_CrtMemState** uygulama tarafından sağlanan yapı.|  
|[_CrtMemDifference](/cpp/c-runtime-library/reference/crtmemdifference)|İki bellek durumu yapısını karşılaştırır, bunların üçüncü bir durum yapısına arasındaki farkı kaydeder ve iki durum farklıysa TRUE değerini döndürür.|  
|[_CrtMemDumpStatistics](/cpp/c-runtime-library/reference/crtmemdumpstatistics)|Dökümleri bir verilen **_CrtMemState** yapısı. Yapısı bir anlık görüntü hata ayıklama yığının durumunun belirli bir anda veya iki anlık görüntü arasındaki farkı içerebilir.|  
|[_CrtMemDumpAllObjectsSince](/cpp/c-runtime-library/reference/crtmemdumpallobjectssince)|Belirli bir anlık görüntü, yürütme başından itibaren veya yığının alındıktan sonra ayrılan tüm nesneler hakkında bilgi dökümünü yapar. Bunu dökümleri her zaman bir **_clıent_block** bloğu biri kullanılarak yüklenmişse, uygulama tarafından sağlanan bir kanca işlevini çağırır **_CrtSetDumpClient**.|  
|[_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)|Herhangi bir bellek sızıntısı program yürütme başlangıcından ve bu durumda, tüm ayrılan nesnelerin dökümünü alır olup olmadığını belirler. Her zaman **_CrtDumpMemoryLeaks** dökümleri bir **_clıent_block** bloğu biri kullanılarak yüklenmişse, uygulama tarafından sağlanan bir kanca işlevini çağırır **_CrtSetDumpClient**.|  
  
 ![Başa dön](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
##  <a name="BKMK_Track_Heap_Allocation_Requests"></a> Parça yığın ayırma istekleri  
 Kaynak dosya adı ve satır numarasının yerinin bir onay veya Raporlama makrosunun yürütüldüğü genellikle bir sorunun nedenini bulmak için de faydalı olan, aynı yığın ayırma işlevleri doğru olarak olası değildir. Makrolar, bir uygulamanın mantık ağacında uygun birçok noktalarında eklenebilir, ancak bir ayırma genellikle birçok farklı zamanlarda pek çok farklı yerden çağrılan özel bir yordama içinde gömülü. Soru genellikle hangi kod satırında bozuk bir ayırma olduğu değil, ancak bunun yerine bu kod satırı tarafından yapılan ayırmaları binlerce birinin bozulduğu ve bunun neden oluyordu.  
  
 **Benzersiz ayırma isteği numaraları ve _crtBreakAlloc**  
  
 Bozuk gitti belirli bir yığın ayırma çağrısını tanımlamak için en basit yolu, hata ayıklama yığınındaki her blokla ilişkili benzersiz ayırma isteği numarasından yararlanmak sağlamaktır. Bir öbekle ilgili bilgiler döküm işlevlerinden biri tarafından raporlandığında, bu ayırma isteği numarası parantez içine alınır (örneğin, "{36}").  
  
 Yanlış ayrılmış bir blok ayırma isteği sayısını öğrendikten sonra bu numarayı geçirebilirsiniz [_CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc) bir kesme noktası oluşturmak için. Yürütme blok ayrılmadan hemen önce kesilecek ve hangi yordamın hatalı çağrıdan sorumlu olduğunu belirlemek için geri izleme. Yeniden derlemeden kaçınmak için aynı şeyi hata ayıklayıcıda ayarlayarak gerçekleştirebilirsiniz **_crtBreakAlloc** ilgilendiğiniz ayırma isteği numarası.  
  
 **Ayırma yordamlarınızın hata ayıklama sürümlerini oluşturma**  
  
 Daha karmaşık bir yaklaşım, kendi ayırma yordamlarınızın hata ayıklama sürümlerini oluşturmaktır **_dbg** sürümlerini [yığın ayırma işlevleri](../debugger/debug-versions-of-heap-allocation-functions.md). Ardından kaynak dosya ve satır numarası bağımsız değişkenlerini temel yığın ayırma yordamlarını geçirebilirsiniz ve hemen kötü bir ayırmanın nereden geldiğini görmek mümkün olacaktır.  
  
 Örneğin, uygulamanızın aşağıdakine benzer bir sık kullanılan yordamı içerdiğini varsayın:  
  
```cpp
int addNewRecord(struct RecStruct * prevRecord,  
                 int recType, int recAccess)  
{  
    // ...code omitted through actual allocation...   
    if ((newRec = malloc(recSize)) == NULL)  
    // ... rest of routine omitted too ...   
}  
```  
  
 Bir üstbilgi dosyasında şunun gibi kod ekleyebilirsiniz:  
  
```cpp
#ifdef _DEBUG  
#define  addNewRecord(p, t, a) \  
            addNewRecord(p, t, a, __FILE__, __LINE__)  
#endif  
```  
  
 Ardından, bunu ayırma, kayıt oluşturma yordamı şu şekilde değiştirebilirsiniz:  
  
```cpp
int addNewRecord(struct RecStruct *prevRecord,  
                int recType, int recAccess  
#ifdef _DEBUG  
               , const char *srcFile, int srcLine  
#endif  
    )  
{  
    /* ... code omitted through actual allocation ... */  
    if ((newRec = _malloc_dbg(recSize, _NORMAL_BLOCK,  
            srcFile, scrLine)) == NULL)  
    /* ... rest of routine omitted too ... */  
}  
```  
  
 Artık kaynak dosyanın adı ve satır numarası nerede `addNewRecord` çağrıldı hata ayıklama yığınında sonuçta elde edilen her blok içinde saklanacak ve o blok incelendiği zaman raporlanacaktır.  
  
 ![Başa dön](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [içeriği](#BKMK_Contents)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
