---
title: CRT kitaplığını kullanarak bellek sızıntılarını bulma | Microsoft Docs
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
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eca7af1cb572714214f264cac35b488fba993bdd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726555"
---
# <a name="finding-memory-leaks-using-the-crt-library"></a>CRT Kitaplığını Kullanarak Bellek Sızıntılarını Bulma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Önceden ayrılmış olan belleği doğru şekilde serbest bırakmak başarısız tanımlanan bellek sızıntıları, C/C++ uygulamalarında en zarif ve algılamak zor hatalar arasındadır. Küçük bellek sızıntısı, ilk ancak zaman içinde fark edilmeyebilir, aşamalı bir bellek sızıntısı belirtileri, aralığı performansı azalan uygulama bellek yetersiz çalıştığında belirtilere neden olabilir. Daha da kötüsü, tüm kullanılabilir belleği kullanan sızdıran bir uygulama hangi uygulamanın sorumlu olduğu konusunda karışıklık oluşturur başka bir uygulamanın çökmesine neden neden olabilir. Görünüşte zararsız bellek sızıntıları, düzeltilmesi gereken başka sorunların belirtisi olabilir.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Hata ayıklayıcı ve C çalışma zamanı (CRT) kitaplıkları size sağlar algılama ve bellek sızıntıları tanımlayan anlamına gelir.  
  
## <a name="enabling-memory-leak-detection"></a>Bellek sızıntısı algılamayı etkinleştirme  
 Bellek sızıntılarını hata ayıklayıcı ve C çalışma zamanı kitaplıkları (CRT) olan algılama için kullanılan birincil Araçlar, hata ayıklama yığın işlevleridir.  
  
 Hata ayıklama yığın işlevlerini etkinleştirmek için aşağıdaki ifadeleri programınıza ekleyin:  
  
```  
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  
  
 CRT işlevlerinin düzgün çalışmaya `#include` deyimleri burada gösterilen sırayı izlemelidir.  
  
 Crtdbg.h eşlemeleri de dahil olmak üzere `malloc` ve [ücretsiz](http://msdn.microsoft.com/library/74ded9cf-1863-432e-9306-327a42080bb8) işlevleri için hata ayıklama sürümlerine [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb) ve `free`, bellek ayırmayı ve ayırmayı kaldırma izleyin. Bu eşleme olan yalnızca hata ayıklama yapılarında, oluşur `_DEBUG`. Sürüm yapıları sıradan kullanın `malloc` ve `free` işlevleri.  
  
 `#define` Deyimi CRT yığın işlevlerinin temel sürümünü ilgili hata ayıklama sürümüyle eşler. Atlarsanız `#define` deyimi, bellek sızıntısı dökümü daha az ayrıntılı olur.  
  
 Bu ifadeleri kullanarak hata ayıklama yığın işlevlerini etkinleştirdikten sonra bir çağrı yerleştirebilirsiniz `_CrtDumpMemoryLeaks` uygulamanız çıkış yaptığında bellek sızıntısı raporunu görüntülemek için bir uygulama çıkış noktasından önce:  
  
```  
_CrtDumpMemoryLeaks();  
```  
  
 Uygulamanızı birden çok çıkış varsa, el ile yapılan yerleştirmeniz gerekmez [_CrtDumpMemoryLeaks](http://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) her çıkış noktasında. Bir çağrı `_CrtSetDbgFlag` uygulamanızı başında otomatik bir çağrıya neden olacak `_CrtDumpMemoryLeaks` her çıkış noktasında. Burada gösterilen iki bit alanını ayarlamanız gerekir:  
  
```  
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  
  
 Varsayılan olarak, `_CrtDumpMemoryLeaks` bellek sızıntısı raporunu çıkarır **hata ayıklama** bölmesinde **çıkış** penceresi. Kullanabileceğiniz `_CrtSetReportMode` raporu başka bir konuma yeniden yönlendirmek için.  
  
 Bir kitaplık kullanıyorsanız, kitaplık çıktıyı başka bir konuma sıfırlayabilir. Bu durumda, çıkış konumunu ayarlayabilirsiniz geri **çıkış** penceresi, aşağıda gösterildiği gibi:  
  
```  
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  
  
## <a name="interpreting-the-memory-leak-report"></a>Bellek sızıntısı raporunu yorumlama  
 Uygulamanızı tanımlamazsa `_CRTDBG_MAP_ALLOC`, [_CrtDumpMemoryLeaks](http://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) aşağıdakine benzer bir bellek sızıntısı raporu görüntüler:  
  
```  
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 Uygulamanızın `_CRTDBG_MAP_ALLOC`, bellek sızıntısı raporu şöyle görünür:  
  
```  
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
 normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 İkinci rapor sızdırılan belleğin ilk ayrıldığı satır numarasını ve dosya adı gösterir farktır.  
  
 Olup `_CRTDBG_MAP_ALLOC` veya değil, bellek sızıntısı raporu olacak aşağıdaki bilgileri görüntüler:  
  
- Bellek ayırma numarası `18` Bu örnekte  
  
- [Blok türü](http://msdn.microsoft.com/en-us/e2f42faf-0687-49e7-aa1f-916038354f97), olduğu `normal` Bu örnekte.  
  
- Onaltılık bellek konumu olan `0x00780E80` Bu örnekte.  
  
- Blok boyutu `64 bytes` Bu örnekte.  
  
- Veri onaltılık biçiminde bloktaki ilk 16 bayt.  
  
  Bellek sızıntısı raporu bir blok bellek normal, istemci ya da CRT olarak tanımlar. A *normal blok* olan programınız tarafından ayrılan sıradan bellektir. A *istemci bloğu* özel bir yıkıcı gerektiren nesneler için MFC programları tarafından kullanılan bellek bloğu türüdür. MFC `new` işleci normal bir blok veya oluşturulan nesne için uygun bir istemci bloğu oluşturur. A *CRT bloğu* kendi kullanımı için CRT kitaplığı tarafından ayrılır. CRT kitaplığı bu bloklar için ayırma kaldırma işler. Bu nedenle, görürsünüz bir şey önemli ölçüde olmadığı sürece bellek sızıntısı raporunda bunları yanlış, örneğin CRT kitaplığının Bozulması düşüktür.  
  
  Hiçbir zaman bellek sızıntısı raporlarında görünür bellek bloğu diğer iki türü vardır. A *boş blok* , yayınlanan bellektir. Bu, tanım gereği sızdırmamış anlamına gelir. Bir *yoksayma bloğu* , bellek sızıntısı raporundan dışlamak için açıkça işaretlediğiniz bellektir.  
  
  Bu teknikler standart CRT kullanılarak ayrılmış bellek için iş `malloc` işlevi. Programınız, C++ kullanarak bellek ayırırsa `new` işleci, ancak yalnızca karşılaşabilirsiniz dosya ve satır numarası nerede genel uygulama `operator new` çağrıları `_malloc_dbg` bellek sızıntısı raporunda. Bu davranışı çok kullanışlı olmadığı için ayırma şuna benzer bir makro kullanarak yapılan satırı bildirmek için değiştirebilirsiniz: 
 
```cpp  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  
  
Artık, değiştirebileceğiniz `new` işleci kullanarak `DBG_NEW` kodunuzda makrosu. Hata ayıklama yapılarında, bu genel kullanmaktadır `operator new` , blok türü, dosya ve satır numarası için ek bir parametre alır. Bu aşırı yüklemesini `new` çağrıları `_malloc_dbg` ek bilgileri kaydetmek için. Kullanırken `DBG_NEW`, bellek sızıntısı raporları sızan nesne ayrıldığı dosya adı ve satır numarasını göster. Perakende sürümlerde varsayılan kullandığı `new`. (Adlı önişlemci makrosu oluşturduğunuz önermiyoruz `new`, veya diğer bir dil anahtar.) Teknik bir örneği aşağıda verilmiştir:  
  
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
  
Visual Studio'da çağrı hata ayıklayıcı bu kodu çalıştırdığınızda `_CrtDumpMemoryLeaks` bir rapor oluşturur **çıkış** şuna benzer penceresi:  
  
```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  
  
Bu durum size sızdırılan ayırma debug_new.cpp satır 20 olduğunu gösterir.  
  
## <a name="setting-breakpoints-on-a-memory-allocation-number"></a>Bellek ayırma numarası üzerinde kesme noktaları ayarlama  
 Bellek ayırma sayısı size bir sızdırılan bellek bloğunun ne zaman ayrıldığını söyler. Örneğin, bir bellek ayırma numarası 18 olan bir blok uygulama çalıştırması sırasında ayrılan belleğin 18 blok ' dir. CRT raporu çalışma sırasında tüm bellek bloğu ayırmalarını sayar. Bu, Tahsisatlar tarafından CRT kitaplık ve MFC gibi diğer kitaplıkları içerir. Bu nedenle, bir bellek ayırma numarası 18 olan bir blok, kodunuz tarafından ayrılan 18. bellek bloğu olmayabilir. Genellikle, bu olmayacaktır.  
  
 Bellek ayırmada bir kesme noktası ayarlamak için ayırma sayısını kullanabilirsiniz.  
  
#### <a name="to-set-a-memory-allocation-breakpoint-using-the-watch-window"></a>İzleme penceresini kullanarak bir bellek ayırma kesme noktası ayarlamak için  
  
1. Uygulamanızın başlangıç bir kesme noktası ayarlayın ve ardından uygulamanızı başlatın.  
  
2. Uygulama kesme noktasında kesildiğinde **Watch** penceresi.  
  
3. İçinde **Watch** penceresinde, tür `_crtBreakAlloc` içinde **adı** sütun.  
  
    (/MD seçeneği) CRT kitaplığının çok iş parçacıklı DLL sürümünü kullanıyorsanız, içerik işlecini dahil edin: `{,,ucrtbased.dll}_crtBreakAlloc`  
  
4. Tuşuna **dönüş**.  
  
    Hata ayıklayıcı çağrıyı değerlendirir ve sonucu yerleştirir **değer** sütun. Bellek ayırmalarında herhangi bir kesme noktası ayarlamadıysanız, bu değer – 1 olur.  
  
5. İçinde **değer** sütun, kesmek istediğiniz bellek ayırma ayırma sayısı ile gösterilen değerini değiştirin.  
  
   Bir bellek ayırma numarasında bir kesme noktası ayarladıktan sonra hata ayıklamaya devam. Böylece bellek ayırma sırasının önceki çalıştırmayla aynı koşullar altında programı çalıştırmayı dikkatli olun. Programınız belirtilen bellek ayırmada bölündüğünde, kullanabileceğiniz **çağrı yığını** penceresi ve diğer hata ayıklayıcı pencereleri altında bellek tahsis koşullarını belirlemek için. Ardından nesneye neler gözlemlemek için yürütmeye devam ve neden ayırmasının doğru şekilde belirleyin.  
  
   Nesnede veri kesme noktası ayarlamak da bu kadar yardımcı olabilir. Daha fazla bilgi için [kullanılarak kesme noktaları](../debugger/using-breakpoints.md).  
  
   Kodda bellek ayırma kesme noktaları da ayarlayabilirsiniz. Bunu yapmak için iki yol vardır:  
  
```  
_crtBreakAlloc = 18;  
```  
  
 veya:  
  
```  
_CrtSetBreakAlloc(18);  
```  
  
## <a name="comparing-memory-states"></a>Bellek durumlarını karşılaştırma  
 Bellek sızıntılarının bulunmasına yönelik başka bir teknik önemli anlarda uygulamanın bellek durumunun anlık görüntülerini almadan içerir. Uygulamanızda belirli bir noktada bellek durumunun anlık görüntüsünü almak için oluşturun bir **_CrtMemState** yapısı ve geçirin `_CrtMemCheckpoint` işlevi. Bu işlev, geçerli bellek durumunun bir anlık görüntüsüyle doldurur:  
  
```  
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
  
```  
  
 `_CrtMemCheckpoint` Geçerli bellek durumunun bir anlık görüntüsüyle doldurur.  
  
 İçeriğini çıkış olarak bir **_CrtMemState** yapısı, yapısı için geçirin `_ CrtMemDumpStatistics` işlevi:  
  
```  
_CrtMemDumpStatistics( &s1 );  
  
```  
  
 `_ CrtMemDumpStatistics` şuna benzer bir bellek durumu dökümü verir:  
  
```  
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
  
```  
  
 Bir kod bölümünde bellek sızıntısı oluşup oluşmadığını belirlemek için önceki ve sonraki bölümde bellek durumunun anlık görüntüsünü ve ardından `_ CrtMemDifference` iki durumu karşılaştırmak için:  
  
```  
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  
  
if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  
  
 `_CrtMemDifference` bellek durumlarını karşılaştırır `s1` ve `s2` ve içinde bir sonuç döndürür (`s3`) diğer bir deyişle fark `s1` ve `s2`.  
  
 Bellek sızıntılarını bulmanın bir yöntemi başlar yerleştirerek `_CrtMemCheckpoint` başlangıcına ve sonuna ardından kullanarak uygulamanızı çağrıları `_CrtMemDifference` sonuçları karşılaştırmak için. Varsa `_CrtMemDifference` daha ekleyebileceğiniz bir bellek sızıntısı gösterir `_CrtMemCheckpoint` sızıntı kaynağını yalıtıncaya kadar ikili dosya arama özelliğini kullanarak programınızı bölmek için çağırır.  
  
## <a name="false-positives"></a>Hatalı pozitif sonuçları  
 Bazı durumlarda, `_CrtDumpMemoryLeaks` bellek sızıntılarının yanlış göstergelerini verebilir. Yerine _NORMAL_BLOCKs olarak iç Tahsisatları işaretleyen bir kitaplık kullanıyorsanız bu durum ortaya çıkabilir `_CRT_BLOCK`s veya `_CLIENT_BLOCK`s. Bu durumda, `_CrtDumpMemoryLeaks` kullanıcı tahsisleri ve dahili kitaplık ayırmaları arasındaki farkı anlatamıyor. Kitaplık ayırmalarının genel yıkıcıları çağırdığınız noktadan sonra çalışırsa `_CrtDumpMemoryLeaks`, her iç kitaplık ayırması bir bellek sızıntısı olarak bildirilir. Standart Şablon kitaplığı, Visual Studio .NET, nedeni'den önceki eski sürümleri `_CrtDumpMemoryLeaks` böyle yanlış bildirmek için hatalı pozitif sonuçlar, ancak bu düzeltilmiştir son sürümlerde.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CRT hata ayıklama öbeği ayrıntıları](../debugger/crt-debug-heap-details.md)   
 [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)   
 [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)



