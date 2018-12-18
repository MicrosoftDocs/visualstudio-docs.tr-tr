---
title: C/C++ onaylamaları | Microsoft Docs
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
- debugging [MFC], assertions
- results, checking
- result checking
- Call Stack window, assertion failures
- debugging [C++], assertions
- VERIFY macro
- assertions, side effects
- assertions
- ASSERT macro
- errors [C++], catching with assertions
- testing, error conditions with assertion statements
- _DEBUG macro
- Assertion Failed dialog box
- failures, finding locations
ms.assetid: 2d7b0121-71aa-414b-bbb6-ede1093d0bfc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: c91ff9d752e2043829b3ea310606a9d8b82b1e1e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845998"
---
# <a name="cc-assertions"></a>C/C++ Onayları
Bir onay deyimi programınızda herhangi bir noktada doğru olması beklenen bir koşulu belirtir. Bu koşul true değilse onaylama işlemi başarısızsa, programınızın yürütülmesini kesildiğinde ve [onaylama başarısız iletişim kutusu](../debugger/assertion-failed-dialog-box.md) görünür.  

 Visual C++, aşağıdaki yapılar üzerinde alan onaylama deyimleri destekler:  

- MFC programları için MFC onaylar.  

- [ATLASSERT](/cpp/atl/reference/debugging-and-error-reporting-macros#atlassert) ATL kullanan programlar  

- C Çalışma Zamanı Kitaplığı'nı kullanan programlar için CRT onaylar.  

- ANSI [assert işlevi](/cpp/c-runtime-library/reference/assert-macro-assert-wassert) diğer C/C++ programları için.  

  Onaylamalar mantık hataları catch, bir işlemin sonuçlarını denetleyin ve işlenen hata koşulları Test için kullanabilirsiniz.  

##  <a name="BKMK_In_this_topic"></a> Bu konudaki  
 [Onaylamalar nasıl çalışır?](#BKMK_How_assertions_work)  

 [Hata ayıklama ve yayın yapılarında onaylar](#BKMK_Assertions_in_Debug_and_Release_builds)  

 [Onayları kullanarak yan etkileri](#BKMK_Side_effects_of_using_assertions)  

 [CRT onaylar](#BKMK_CRT_assertions)  

 [MFC onaylar](#BKMK_MFC_assertions)  

- [MFC assert_valıd ve CObject::AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)  

- [AssertValid sınırlamaları](#BKMK_Limitations_of_AssertValid)  

  [Onaylamalar kullanma](#BKMK_Using_assertions)  

- [Mantık hatalarını yakalama](#BKMK_Catching_logic_errors)  

- [Sonuçları denetleniyor](#BKMK_Checking_results_)  

- [İşlenmemiş bulma hataları](#BKMK_Testing_error_conditions_)  

##  <a name="BKMK_How_assertions_work"></a> Onaylamalar nasıl çalışır?  
 Hata ayıklayıcı nedeniyle MFC veya C çalışma zamanı kitaplığı onaylama durdurduğunda kaynak kullanılabiliyorsa, ardından hata ayıklayıcı onaylama oluştuğu kaynak dosyadaki noktasına gider. Onaylama ileti hem de görünür [çıkış penceresine](../ide/reference/output-window.md) ve **onaylama işlemi başarısız oldu** iletişim kutusu. Onaylama ileti kopyalayabilirsiniz **çıkış** penceresinde bir metin penceresine başvurulmak üzere kaydetmek istiyorsanız. **Çıkış** penceresi, diğer hata iletileri de içerebilir. Hatanın nedenini onaylama için ipuçları sağlar çünkü bu iletiler dikkatlice inceleyin.  

 Onaylar, geliştirme sırasında hataları algılamak için kullanın. Bir kural olarak, bir onaylama için her bir varsayım kullanın. Örneğin, bir bağımsız değişken NULL değil olduğunu varsayarsak, onaylama bu varsayımı test etmek için kullanın.  

 [Bu konudaki](#BKMK_In_this_topic)  

##  <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> Hata ayıklama ve yayın yapılarında onaylar  
 Onaylama deyimleri yalnızca derleme `_DEBUG` tanımlanır. Aksi halde, derleyici onaylar boş deyimler değerlendirir. Bu nedenle onaylama deyimleri zahmetine zorunlu kılmadan veya performans maliyeti, son yayın programınızda ve kullanmaktan kaçınmak izin `#ifdef` yönergeleri.  

##  <a name="BKMK_Side_effects_of_using_assertions"></a> Onayları kullanarak yan etkileri  
 Onaylamalar kodunuza ekleyin, onaylamalar yan etkisi yok emin olun. Örneğin, aşağıdaki onay değiştiren düşünün `nM` değeri:  

```cpp
ASSERT(nM++ > 0); // Don't do this!  
```  

 Çünkü `ASSERT` programınızı yayın sürümünde ifade değerlendirilmez `nM` hata ayıklama ve yayın sürümleri farklı değerlere sahip. MFC içinde bu sorundan kaçınmak için kullanabileceğiniz [doğrulama](/cpp/mfc/reference/diagnostic-services#verify) yerine makrosu `ASSERT`.  `VERIFY` tüm sürümlerde ifade değerlendirilir, ancak sonuçta yayın sürümünü denetlemez.  

 Bir işlev değerlendirme olabileceğinden işlev çağrıları onaylama deyimleri içinde kullanırken özellikle dikkatli beklenmeyen yan etkiler.  

```cpp
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects  
VERIFY ( myFnctn(0)==1 ) // safe  
```  

 `VERIFY` çağrıları `myFnctn` hata ayıklama ve yayın sürümlerinde, bu nedenle, kullanmak için kabul edilebilir. Ancak, `VERIFY` bir yayın sürümünü gereksiz işlev çağrısında yükü getirir.  

 [Bu konudaki](#BKMK_In_this_topic)  

##  <a name="BKMK_CRT_assertions"></a> CRT onaylar  
 CRTDBG. H üstbilgi dosyası tanımlar [_ASSERT ve _ASSERTE makroları](/cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros) onaylama işlemi denetimi.  


| Makrosu | Sonuç |
|------------| - |
| `_ASSERT` | Belirtilen ifade FALSE olarak değerlendirilirse dosya adı ve satır sayısını `_ASSERT`. |
| `_ASSERTE` | Aynı `_ASSERT`, artı onaylanan ifade bir dize gösterimi. |

 `_ASSERTE` FALSE dönüştü olarak onaylanan ifade bildirmesi nedeniyle daha güçlüdür. Bu, kaynak koda başvuruda bulunmadan sorunu tanımlamak için yeterli olabilir. Ancak, uygulamanızın hata ayıklama sürümünü kullanarak onaylanan her ifade için bir dize sabitine içerecek `_ASSERTE`. Çoğu kullanırsanız `_ASSERTE` makroları, bu dize ifadeler olması önemli miktarda bellek. Bu sorun kanıtlar kullanırsanız `_ASSERT` bellekten tasarruf etmek.  

 Zaman `_DEBUG` tanımlanan `_ASSERTE` makrosu şu şekilde tanımlanır:  

```cpp
#define _ASSERTE(expr) \  
   do { \  
      if (!(expr) && (1 == _CrtDbgReport( \  
         _CRT_ASSERT, __FILE__, __LINE__, #expr))) \  
         _CrtDbgBreak(); \  
   } while (0)  
```  

 Olarak onaylanan ifade FALSE olarak değerlendirilirse [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) (varsayılan olarak bir ileti iletişim kutusu kullanılarak) onaylama işlemi hatası bildirmek için çağırılır. Seçerseniz **yeniden** iletisi iletişim kutusunda, `_CrtDbgReport` 1 döndürür ve `_CrtDbgBreak` aracılığıyla hata ayıklayıcı çağırır `DebugBreak`.  

### <a name="checking-for-heap-corruption"></a>Yığın bozulmasını denetleme  
 Aşağıdaki örnekte [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory) yığın bozulma olup olmadığını denetleyin:  

```cpp
_ASSERTE(_CrtCheckMemory());  
```  

### <a name="checking-pointer-validity"></a>İşaretçi geçerlilik denetimi  
 Aşağıdaki örnekte [_crtısvalidpointer](/cpp/c-runtime-library/reference/crtisvalidpointer) belirtilen bellek aralığının okuma veya yazma için geçerli olduğunu doğrulayın.  

```cpp
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );  
```  

 Aşağıdaki örnekte [_crtısvalidheappointer](/cpp/c-runtime-library/reference/crtisvalidheappointer) yerel yığın belleğini bir işaretçi işaret doğrulamak için (öbek oluşturulan ve C Çalışma Zamanı Kitaplığı'nın bu örneği tarafından yönetilen — bir DLL Kitaplığı kendi örneğini olabilir ve Bu nedenle kendi yığın, uygulama yığın dışında). Bu onay, yalnızca null yakalar değil veya işlemleri, ancak aynı zamanda işaretçileri statik değişkenler, yığın değişkenleri ve herhangi bir yerel olmayan bellek adresleri.  

```cpp
_ASSERTE(_CrtIsValidPointer( myData );  
```  

### <a name="checking-a-memory-block"></a>Bir bellek bloğunu denetleniyor  
 Aşağıdaki örnekte [_crtısmemoryblock](/cpp/c-runtime-library/reference/crtismemoryblock) bir bellek bloğunu yerel yığında ve geçerli blok türü olduğundan doğrulamak için.  

```cpp
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));  
```  

 [Bu konudaki](#BKMK_In_this_topic)  

##  <a name="BKMK_MFC_assertions"></a> MFC onaylar  
 MFC tanımlar [ASSERT](https://msdn.microsoft.com/Library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) onaylama işlemi denetimi makrosu. Ayrıca tanımlar `MFC ASSERT_VALID` ve `CObject::AssertValid` iç durumunu denetleme yöntemleri bir `CObject`-türetilmiş bir nesneye.  

 MFC bağımsız değişkeni `ASSERT` makrosu sıfır olarak değerlendirilen veya yanlış makro programın yürütülmesini durdurur ve kullanıcıyı uyarır, aksi takdirde, yürütme devam eder.  

 Bir onaylama işlemi, kaynak dosya ve satır numarası onaylama adı bir ileti iletişim kutusu gösterilir başarısız olduğunda. Yeniden deneme iletişim kutusunda seçerseniz kutusunda, bir çağrı [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) ayıklayıcıya geçmeye yürütülmesine neden olur. Bu noktada, çağrı yığınını inceleyebilir ve diğer hata ayıklayıcı tesislerini onaylama neden başarısız olduğunu belirlemek için kullanın. Etkinleştirdiyseniz [Just-ın-time hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)ve hata ayıklayıcı zaten yürütülmekte, iletişim kutusu, hata ayıklayıcıyı başlatabilirsiniz.  

 Aşağıdaki örnek nasıl kullanılacağını gösterir `ASSERT` işlevinin dönüş değerini denetlemek için:  

```cpp
int x = SomeFunc(y);  
ASSERT(x >= 0);   //  Assertion fails if x is negative  
```  

 ASSERT ile kullanabileceğiniz [Iskindof](https://docs.microsoft.com/cpp/mfc/reference/cobject-class#iskindof) işlevi türü işlev bağımsız değişkenleri denetimini sağlamak için:  

```cpp
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );  
```  

 `ASSERT` Makrosu yayın sürümünde kod üretir. Yayın sürümünü ifadesinde değerlendirilecek ihtiyacınız varsa [doğrulama](https://msdn.microsoft.com/library/s8c29sw2.aspx#verify) ASSERT yerine makrosu.  

###  <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> MFC assert_valıd ve CObject::AssertValid  
 [CObject::AssertValid](https://docs.microsoft.com/cpp/mfc/reference/cobject-class#assertvalid) yöntemi sağlar çalışma zamanı, bir nesnenin iç durumunu denetler. Geçersiz kılma gerekmez ancak `AssertValid` türetilen, sizin sınıfınızdan `CObject`, bunu yaparak, sınıfınıza daha güvenilir yapabilirsiniz. `AssertValid` Onaylamalar tüm geçerli değerleri içerdiğini doğrulamak için üye değişkenleri nesnenin gerçekleştirmeniz gerekir. Örneğin, işaretçi üye değişkenleri NULL olmadığını denetlemelisiniz.  

 Aşağıdaki örnek nasıl belirtileceğini gösteren bir `AssertValid` işlevi:  

```cpp
class CPerson : public CObject  
{  
protected:  
    CString m_strName;  
    float   m_salary;  
public:  
#ifdef _DEBUG  
    // Override  
    virtual void AssertValid() const;  
#endif  
    // ...  
};  
```  

 Ne zaman geçersiz kılmanız `AssertValid`, temel sınıf sürümü çağrı `AssertValid` kendi denetimleri gerçekleştirmeden önce. Ardından ASSERT makrosu, türetilmiş sınıf için benzersiz üye denetlemek için burada gösterildiği gibi kullanın:  

```cpp
#ifdef _DEBUG  
void CPerson::AssertValid() const  
{  
    // Call inherited AssertValid first.  
    CObject::AssertValid();  

    // Check CPerson members...  
    // Must have a name.  
    ASSERT( !m_strName.IsEmpty());  
    // Must have an income.  
    ASSERT( m_salary > 0 );  
}  
#endif  
```  

 Tüm üye değişkenleri nesneleri depolamak, kullanabileceğiniz `ASSERT_VALID` iç geçerliliği test etmek için makro (kendi sınıfları geçersiz kılarsanız `AssertValid`).  

 Örneğin, bir sınıf düşünün `CMyData`, hangi depoları bir [CObList](/cpp/mfc/reference/coblist-class) üye değişkenlerini birinde. `CObList` Değişken `m_DataList`, koleksiyonunu depolar `CPerson` nesneleri. Kısaltılmış bir bildirimi `CMyData` şöyle görünür:  

```cpp
class CMyData : public CObject  
{  
    // Constructor and other members ...  
    protected:  
        CObList* m_pDataList;  
    // Other declarations ...  
    public:  
#ifdef _DEBUG  
        // Override:  
        virtual void AssertValid( ) const;  
#endif  
    // And so on ...  
};  
```  

 `AssertValid` İçinde geçersiz kılma `CMyData` şöyle görünür:  

```cpp
#ifdef _DEBUG  
void CMyData::AssertValid( ) const  
{  
    // Call inherited AssertValid.  
    CObject::AssertValid( );  
    // Check validity of CMyData members.  
    ASSERT_VALID( m_pDataList );  
    // ...  
}  
#endif  
```  

 `CMyData` kullanan `AssertValid` veri üyesi içinde depolanan nesneleri geçerliliğini sınamak için bir mekanizma. Geçersiz kılma `AssertValid` , `CMyData` çağırır `ASSERT_VALID` kendi m_pDataList üye değişkeni makro.  

 Geçerlilik testleri değil durdurmak bu düzeyde olduğundan sınıfı `CObList` de geçersiz kılmalar `AssertValid`. Bu geçersiz kılma ek geçerlilik listenin iç durumuna sınama gerçekleştirir. Bu nedenle, geçerlilik test üzerinde bir `CMyData` nesne ek geçerlilik testleri için iç durumlarını depolanan müşteri adayları `CObList` liste nesnesi.  

 Daha fazla bazı çalışmak için geçerlilik testleri ekleyebilirsiniz `CPerson` nesneleri listesinde depolanır. Bir sınıf türetin `CPersonList` gelen `CObList` ve geçersiz kılma `AssertValid`. Geçersiz çağrı yapıyordu `CObject::AssertValid` ve ardından listesi boyunca yineleme çağırma `AssertValid` her `CPerson` listesinde depolanan nesne. `CPerson` Bu konunun başındaki zaten gösterilen sınıfı geçersiz kılan `AssertValid`.  

 Hata ayıklama için oluştururken güçlü bir mekanizma budur. Daha sonra için yayın oluşturma sırasında mekanizma otomatik olarak kapatılır.  

###  <a name="BKMK_Limitations_of_AssertValid"></a> AssertValid sınırlamaları  
 Tetiklenmiş bir onaylama işlemi kesinlikle hatalı bir nesnedir ve yürütmesi durdurulur gösterir. Ancak, onaylama işlemi eksikliği yalnızca hiçbir sorun bulunamadı, ancak nesne iyi olmasını garanti edilmez gösterir.  

 [Bu konudaki](#BKMK_In_this_topic)  

##  <a name="BKMK_Using_assertions"></a> Onaylamalar kullanma  

###  <a name="BKMK_Catching_logic_errors"></a> Mantık hatalarını yakalama  
 Onaylama programınızı mantığına göre true olması gereken bir koşul ayarlayabilirsiniz. Mantıksal bir hata gerçekleşmediği sürece onaylama bir etkisi yoktur.  

 Örneğin, bir kapsayıcı ve değişken gaz molecules benzetimi, varsayalım `numMols` molecules toplam sayısını temsil eder. Bu sayı kullanılamaz olması böyle bir MFC onay deyimi içerebilir. Bu nedenle, sıfırdan küçüktür:  

```cpp
ASSERT(numMols >= 0);  
```  

 Ya da böyle bir CRT onaylama şunlar olabilir:  

```cpp
_ASSERT(numMols >= 0);  
```  

 Bu deyimler, programınızı düzgün çalışıyorsa, hiçbir şey yapmayın. Bir mantık hatası neden olursa `numMols` değerinden küçük olması için sıfır ancak onaylama programınızın yürütülmesini durdurur ve görüntüler [onaylama başarısız iletişim kutusu](../debugger/assertion-failed-dialog-box.md).  

 [Bu konudaki](#BKMK_In_this_topic)  

###  <a name="BKMK_Checking_results_"></a> Sonuçları denetleniyor  
 Onaylar, test sonuçlarını hızlı görsel denetim belirgin olmayan operations değerlidir.  

 Örneğin, değişken güncelleştirmeleri aşağıdaki kodu düşünün `iMols` işaret ettiği bağlantılı listenin içeriğine göre `mols`:  

```cpp
/* This code assumes that type has overloaded the != operator  
 with const char *   
It also assumes that H2O is somewhere in that linked list.   
Otherwise we'll get an access violation... */  
while (mols->type != "H2O")  
{  
 iMols += mols->num;  
 mols = mols->next;  
}  
ASSERT(iMols<=numMols); // MFC version  
_ASSERT(iMols<=numMols); // CRT version  
```  

 Molecules sayısını sayılan tarafından `iMols` her zaman molecules, toplam sayısını küçük veya buna eşit olmalıdır `numMols`. Görsel denetim döngünün bir onay deyimi döngüsünden sonra test etmek için bu koşul için kullanılmak üzere bu mutlaka durumda olacağını göstermez.  

 [Bu konudaki](#BKMK_In_this_topic)  

###  <a name="BKMK_Testing_error_conditions_"></a> İşlenmemiş bulma hataları  
 Onaylar, burada herhangi bir hata işlenmiş olan bir noktada hata koşulları için kodunuzu test etmek için kullanabilirsiniz. Aşağıdaki örnekte, bir grafik yordamı bir hata kodu veya başarı için sıfır döndürür.  

```cpp
myErr = myGraphRoutine(a, b);  

/* Code to handle errors and  
   reset myErr if successful */  

ASSERT(!myErr); -- MFC version  
_ASSERT(!myErr); -- CRT version  
```  

 Hata işleme kodu düzgün çalışıyorsa, hata olarak işleneceğini ve `myErr` sıfırlama onaylama ulaşılmadan önce sıfır. Varsa `myErr` sahip başka bir değer, onaylama işlemi başarısız olursa, program durur ve [onaylama başarısız iletişim kutusu](../debugger/assertion-failed-dialog-box.md) görünür.  

 Onaylama deyimleri bir hata işleme kodu, ancak yerini alamayacak. Aşağıdaki örnekte, son yayın kodda sorunlara yol açabilecek bir onay deyimi gösterilmektedir:  

```cpp
myErr = myGraphRoutine(a, b);  

/* No Code to handle errors */  

ASSERT(!myErr); // Don't do this!  
_ASSERT(!myErr); // Don't do this, either!  
```  

 Bu kod, hata durumunu işlemek için onay deyimi kullanır. Sonuç olarak, herhangi bir hata kodu tarafından döndürülen `myGraphRoutine` son sürüm kodda işlenmemiş.  

 [Bu konudaki](#BKMK_In_this_topic)  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)   
 [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)   
 [Yönetilen Koddaki Onaylamalar](../debugger/assertions-in-managed-code.md)
