---
title: CRT kitaplığı ile bellek sızıntılarını bulma | Microsoft Docs
ms.custom: ''
ms.date: 10/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, on memory allocation
- _CrtMemState
- _CrtMemCheckpoint
- memory leaks
- _CrtMemDifference
- memory leaks, detecting and isolating
- _CrtDumpMemoryLeaks
- _CrtSetBreakAlloc
- _crtBreakAlloc
- _CrtSetReportMode
- memory, debugging
- _CrtMemDumpStatistics
- debugging memory leaks
- _CRTDBG_MAP_ALLOC
- _CrtSetDbgFlag
ms.assetid: cf6dc7a6-cd12-4283-b1b6-ea53915f7ed1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b797e8c8068523b4c782c4d7f02a3853c1d37d1
ms.sourcegitcommit: 12d6398c02e818de4fbcb4371bae9e5db6cf9509
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050118"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>CRT kitaplığı ile bellek sızıntılarını bulma

Bellek sızıntıları, C/C++ uygulamalarında en zarif ve sabit algılamak hatalar arasındadır. Önceden ayrılmış olan belleği doğru şekilde serbest bırakmak başarısız sonuçtan bellek sızıntıları. Küçük bellek sızıntısı ilk başta fark edilmeyebilir, ancak zaman içinde uygulamanın bellek yetersiz belirtilere performansı arasında değişen belirtilere neden. Tüm kullanılabilir belleği kullanan diğer uygulamalar çökmesine neden neden olabilecek sızdıran bir uygulama için hangi uygulama konusunda karışıklık oluşturur sorumludur. Hatta zararsız bellek sızıntıları, düzeltilmesi gereken diğer sorunlar gösterebilir.  

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Hata ayıklayıcı ve C çalışma zamanı kitaplığı (CRT) yardımcı olabilir, algılamak ve bellek sızıntıları tanımlamak.  

## <a name="enable-memory-leak-detection"></a>Bellek sızıntısı algılamayı etkinleştirme  

Bellek sızıntıları C/C++ hata ayıklayıcı ve C çalışma zamanı kitaplığı (CRT) olan algılama için kullanılan birincil Araçlar, hata ayıklama yığın işlevleridir.  

Tüm hata ayıklama yığın işlevlerini etkinleştirmek için C++ programınızda, aşağıdaki sırayla aşağıdaki deyimleri ekleyin:  

```cpp
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  

`#define` Deyimi CRT yığın işlevlerinin temel sürümünü ilgili hata ayıklama sürümüyle eşler. Seçeneğini kullanmazsanız `#define` deyimi, bellek sızıntısı dökümü olacaktır [daha az ayrıntılı](#interpret-the-memory-leak-report).  

Dahil olmak üzere *crtdbg.h* eşler `malloc` ve `free` işlevleri için hata ayıklama sürümlerine [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) ve [_free_dbg](/cpp/c-runtime-library/reference/free-dbg), bellek izleme ayırmayı ve ayırmayı kaldırma. Bu eşleme olan yalnızca hata ayıklama yapılarında, oluşur `_DEBUG`. Sürüm yapıları sıradan kullanın `malloc` ve `free` işlevleri.  

Önceki ifadeleri kullanarak hata ayıklama yığın işlevlerini etkinleştirdikten sonra bir çağrı için [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) uygulama çıkış yaptığında bellek sızıntısı raporu görüntülemek için bir uygulama çıkış noktasından önce.  

```cpp
_CrtDumpMemoryLeaks();  
```  

Uygulamanızı birden çok çıkış varsa, el ile yerleştirmeniz gerekmez `_CrtDumpMemoryLeaks` her çıkış noktasında. Otomatik bir çağrıya neden `_CrtDumpMemoryLeaks` her çıkış noktasında çağrı `_CrtSetDbgFlag` burada gösterilen bit alanları uygulamanızla başında:

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  

Varsayılan olarak, `_CrtDumpMemoryLeaks` bellek sızıntısı raporunu çıkarır **hata ayıklama** bölmesinde **çıkış** penceresi. Bir kitaplık kullanıyorsanız, kitaplık çıktıyı başka bir konuma sıfırlayabilir. 

Kullanabileceğiniz `_CrtSetReportMode` raporu başka bir konuma yeniden yönlendirme veya yeniden **çıkış** burada gösterildiği gibi penceresi:  

```cpp
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  

## <a name="interpret-the-memory-leak-report"></a>Bellek sızıntısı raporunu yorumlama  

Uygulamanızı tanımlamıyorsa `_CRTDBG_MAP_ALLOC`, [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) gibi görünen bir bellek sızıntısı raporu görüntüler:  

```cmd
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  

Uygulamanız tanımlıyorsa `_CRTDBG_MAP_ALLOC`, bellek sızıntısı raporu aşağıdaki gibi görünür:  

```cmd
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  

İkinci raporun dosya adı ve satır numarası sızdırılan belleğin ilk ayrıldığı gösterilir.  

Tanımladığınız olup olmadığını `_CRTDBG_MAP_ALLOC`, bellek sızıntısı raporu görüntüler:  

- Bellek ayırma numarası `18` örnekte  
- Blok türü `normal` örnekte.  
- Onaltılık bellek konumu `0x00780E80` örnekte.  
- Blok boyutu `64 bytes` örnekte.  
- Veri onaltılık biçiminde bloktaki ilk 16 bayt.  

Bellek bloğu türleri *normal*, *istemci*, veya *CRT*. A *normal blok* olan programınız tarafından ayrılan sıradan bellektir. A *istemci bloğu* özel bir yıkıcı gerektiren nesneler için MFC programları tarafından kullanılan bellek bloğu türüdür. MFC `new` işleci normal bir blok veya oluşturulan nesne için uygun bir istemci bloğu oluşturur. 

A *CRT bloğu* kendi kullanımı için CRT kitaplığı tarafından ayrılır. CRT kitaplığı ile ilgili önemli sorunlara olmadığı sürece bellek sızıntısı raporu CRT blokları görünmez şekilde CRT kitaplığı bu bloklar için ayırma kaldırma işler.  

Hiçbir zaman bellek sızıntısı raporlarında görünür bellek bloğu diğer iki türü vardır. A *boş blok* , tanımına göre sızmasına olmayan şekilde serbest bırakılan bellek. Bir *yoksayma bloğu* , bellek sızıntısı raporundan dışlamak için açıkça işaretlediğiniz bellektir.  

Bellek sızıntılarını standart CRT kullanılarak ayrılmış bellek için önceki teknikler tanımlamak `malloc` işlevi. Programınız, C++ kullanarak bellek ayırırsa `new` işleci, ancak yalnızca karşılaşabilirsiniz dosya adı ve satır numarasını nereden `operator new` çağrıları `_malloc_dbg` bellek sızıntısı raporunda. Daha kullanışlı bir bellek sızıntısı raporu oluşturmak için ayırma satır bildirmek için aşağıdakine benzer bir makro yazabilirsiniz: 

```cpp  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  

Artık, değiştirebileceğiniz `new` işleci kullanarak `DBG_NEW` kodunuzda makrosu. Hata ayıklama yapılarında `DBG_NEW` genel kullanmaktadır `operator new` , blok türü, dosya ve satır numarası için ek bir parametre alır. Aşırı yüklemesini `new` çağrıları `_malloc_dbg` ek bilgileri kaydetmek için. Bellek sızıntısı raporlarında, sızan nesne ayrıldığı dosya adı ve satır numarası gösterilir. Yayın derlemeleri hala kullanım varsayılan `new`. Teknik bir örneği aşağıda verilmiştir:  

```cpp  
// debug_new.cpp
// compile by using: cl /EHsc /W4 /D_DEBUG /MDd debug_new.cpp
#define _CRTDBG_MAP_ALLOC
#include <cstdlib>
#include <crtdbg.h>

#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif

struct Pod {
    int x;
};

void main() {
    Pod* pPod = DBG_NEW Pod;
    pPod = DBG_NEW Pod; // Oops, leaked the original pPod!
    delete pPod;

    _CrtDumpMemoryLeaks();
}
```  

Bu kod Visual Studio çalıştırdığınızda, hata ayıklayıcı, çağrı `_CrtDumpMemoryLeaks` bir rapor oluşturur **çıkış** e benzer penceresi:  

```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  

Bu raporlar sızdırılan ayırma satırında 20 olduğunu çıkış *debug_new.cpp*.  

>[!NOTE]
>Adlı bir önişlemci makrosu oluşturduğunuz önermemekteyiz `new`, veya diğer bir dil anahtar. 

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>Bellek ayırma numarası üzerinde kesme noktaları ayarlama  

Bellek ayırma sayısı size bir sızdırılan bellek bloğunun ne zaman ayrıldığını söyler. Örneğin, bir bellek ayırma numarası 18 olan bir blok uygulama çalıştırma sırasında ayrılan belleğin 18 blok ' dir. CRT raporu, Tahsisatlar tarafından CRT kitaplık ve MFC gibi diğer kitaplıkları dahil olmak üzere, çalışma sırasında tüm bellek bloğu ayırmalarını sayar. Bu nedenle, bellek ayırma blok numarası 18 büyük olasılıkla kodunuz tarafından ayrılan 18. bellek bloğu değildir. 

Bellek ayırmada bir kesme noktası ayarlamak için ayırma sayısını kullanabilirsiniz.  

**İzleme penceresini kullanarak bir bellek ayırma kesme noktası ayarlamak için:**  

1. Uygulamanızın başlangıç bir kesme noktası ayarlayın ve hata ayıklamaya başlayın.  
   
1. Uygulama kesme noktasında durakladığında açık bir **Watch** penceresini seçerek **hata ayıklama** > **Windows** > **Watch1** (veya **2 izleyin**, **3 izleyin**, veya **izleyin 4**).  
   
1. İçinde **Watch** penceresinde, tür `_crtBreakAlloc` içinde **adı** sütun.  
   
   Şu içerik işlecini (/MD seçeneği) CRT kitaplığının çok iş parçacıklı DLL sürümünü kullanıyorsanız, ekleyin: `{,,ucrtbased.dll}_crtBreakAlloc`  
   
1. Tuşuna **girin**.  
   
   Hata ayıklayıcı çağrıyı değerlendirir ve sonucu yerleştirir **değer** sütun. Bu değer olacaktır **-1** bellek ayırmalarında herhangi bir kesme noktası ayarlamadıysanız.  
   
1. İçinde **değer** sütun değeri, hata ayıklayıcının istediğiniz bellek ayırma ayırma sayısıyla değiştirin.  

Bir bellek ayırma numarasında bir kesme noktası ayarladıktan sonra hata ayıklamaya devam. Aynı koşullarda bellek ayırma numarası değişmez şekilde çalıştırıldığından emin olun. Programınız belirtilen bellek ayırmada bölündüğünde kullanın **çağrı yığını** penceresi ve diğer hata ayıklayıcı pencereleri altında bellek tahsis koşullarını belirlemek için. Ardından nesneye neler gözlemlemek için yürütmeye devam ve neden doğru şekilde serbest değil belirleyin.  

Nesnede veri kesme noktası ayarlamak da bu kadar yardımcı olabilir. Daha fazla bilgi için [kesme noktalarını kullanma](../debugger/using-breakpoints.md).  

Kodda bellek ayırma kesme noktaları da ayarlayabilirsiniz. Ayarlayabilirsiniz:  

```cpp
_crtBreakAlloc = 18;  
```  

 veya:  

```cpp
_CrtSetBreakAlloc(18);  
```  

## <a name="compare-memory-states"></a>Bellek durumlarını karşılaştırma  
 Bellek sızıntılarının bulunmasına yönelik başka bir teknik önemli anlarda uygulamanın bellek durumunun anlık görüntülerini almadan içerir. Uygulamanızda belirli bir noktada bellek durumunun anlık görüntüsünü almak için oluşturun bir `_CrtMemState` yapısı ve geçirin `_CrtMemCheckpoint` işlevi. 

```cpp
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
```  

`_CrtMemCheckpoint` İşlevi, geçerli bellek durumunun bir anlık görüntüsüyle doldurur.  

İçeriğini çıkış olarak bir `_CrtMemState` yapısı, yapısı için geçirin `_ CrtMemDumpStatistics` işlevi:  

```cpp
_CrtMemDumpStatistics( &s1 );  
```  

`_ CrtMemDumpStatistics` şuna benzer bir bellek durumu dökümü verir:  

```cmd
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
```  

Bir kod bölümünde bellek sızıntısı oluşup oluşmadığını belirlemek için önceki ve sonraki bölümde bellek durumunun anlık görüntüsünü ve ardından `_ CrtMemDifference` iki durumu karşılaştırmak için:  

```cpp
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  

if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  

`_CrtMemDifference` bellek durumlarını karşılaştırır `s1` ve `s2` ve içinde bir sonuç döndürür (`s3`) arasındaki farkı diğer bir deyişle `s1` ve `s2`.  

Bellek sızıntılarını bulmanın bir yöntemi başlar yerleştirerek `_CrtMemCheckpoint` başlangıcını ve bitişini ardından kullanarak uygulamanızın çağrıları `_CrtMemDifference` sonuçları karşılaştırmak için. Varsa `_CrtMemDifference` daha ekleyebileceğiniz bir bellek sızıntısı gösterir `_CrtMemCheckpoint` sızıntı kaynağını ayırdığınız kadar ikili dosya arama özelliğini kullanarak programınızı bölmek için çağırır.  

## <a name="false-positives"></a>Hatalı pozitif sonuçları  
 `_CrtDumpMemoryLeaks` bir kitaplık CRT blokları veya istemci bloklar yerine normal blokları olarak iç Tahsisatları işaretlerse bellek sızıntılarının yanlış göstergelerini verebilir. Bu durumda, `_CrtDumpMemoryLeaks` kullanıcı tahsisleri ve dahili kitaplık ayırmaları arasındaki farkı anlatamıyor. Kitaplık ayırmalarının genel yıkıcıları çağırdığınız noktadan sonra çalışırsa `_CrtDumpMemoryLeaks`, her iç kitaplık ayırması bir bellek sızıntısı olarak bildirilir. Standart Şablon Kitaplığı Visual Studio .NET neden'den önceki sürümleri `_CrtDumpMemoryLeaks` böyle yanlış pozitifleri bildirmek için.  

## <a name="see-also"></a>Ayrıca bkz.  
 [CRT hata ayıklama öbeği ayrıntıları](../debugger/crt-debug-heap-details.md)   
 [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)   
 [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)
