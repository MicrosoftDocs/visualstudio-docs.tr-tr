---
title: En iyi yöntemler ve örnekler (SAL) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 666276fb-99c2-4dc9-8bac-d74861c203ea
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9327ab850bb5f62158e48abc4c8445d3f9b6fe9b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743742"
---
# <a name="best-practices-and-examples-sal"></a>En İyi Yöntemler ve Örnekler (SAL)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kaynak kod ek açıklama dili (SAL) dışında en iyi şekilde yararlanmak ve bazı yaygın sorunları önlemek için bazı yollar şunlardır.  
  
## <a name="in"></a>\_İçinde\_
 Öğesine yazılacak işlev beklenen kullanırsanız `_Inout_` yerine `_In_`. Bu, özellikle eski makroları otomatik dönüştürme SAL'ın durumlarda geçerlidir. SAL'ın önce birçok Programcı makroları yorum olarak kullanılan — adlandırılmıştı makroları `IN`, `OUT`, `IN_OUT`, veya türevleri bu adları. Bu makrolar için SAL dönüştürmenizi öneririz ancak biz de, kod özgün prototip yazılmıştır ve eski makrosu, artık ne yaptığını gösterebilir beri değiştirilmiş olabileceğinden dönüştürme yaparken dikkatli olun bağlantısını okumanızı tavsiye. Hakkında özellikle dikkat `OPTIONAL` sık yanlış yerleştirilir çünkü makrosu açıklama — Örneğin, tarafındaki yanlış virgül.  
  
```cpp  
  
// Incorrect  
void Func1(_In_ int *p1)  
{  
    if (p1 == NULL)   
        return;  
  
    *p1 = 1;  
}  
  
// Correct  
void Func2(_Inout_ PCHAR p1)  
{  
    if (p1 == NULL)   
        return;  
  
    *p1 = 1;  
}  
```  
  
## <a name="opt"></a>\_iyileştirilmiş\_  
 Arayan bir null işaretçi geçmesine izin verilmiyor kullanırsanız `_In_` veya `_Out_` yerine `_In_opt_` veya `_Out_opt_`. Bu parametreleri denetler ve olmamalıdır, NULL ise, bir hata döndürür bile bir işlev için geçerlidir. Bir işlev için beklenmeyen NULL parametresi denetleyin ve düzgün bir şekilde dönmek zorunda savunma kodlama iyi olsa da, bu ek açıklama parametresi isteğe bağlı bir türde olabilir gelmez (\_*Xxx*_opt\_).  
  
```cpp  
  
// Incorrect  
void Func1(_Out_opt_ int *p1)  
{  
    *p = 1;  
}  
  
// Correct  
void Func2(_Out_ int *p1)  
{  
    *p = 1;  
}  
  
```  
  
## <a name="predefensive-and-postdefensive"></a>\_Pre_defensive\_ ve \_Post_defensive\_  
 Bir işlev bir güven sınırı varsa, kullanmanızı öneririz `_Pre_defensive_` ek açıklama.  "Savunma" değiştiricisi, çağrısı noktasında belirtmek için bazı ek açıklamaları değiştirir, arabirimi tamamen denetlenmesi, ancak uygulama gövdesinde hatalı parametreler geçebilir, varsaymanız gerekir. Bu durumda, `_In_ _Pre_defensive_` çağıran NULL geçirmeye çalışırsa bir hata alırsınız olsa da, sanki parametresi NULL ve işaretçi olmayan XML'deki başvuru girişimleri olabilir işlev gövdesi analiz edilir olduğunu belirtmek için bir güven sınırında tercih edilir NULL denetimi işaretlenir.  A `_Post_defensive_` ek açıklama kullanılabilir Ayrıca, burada güvenilen taraf çağıran olduğu varsayılır ve güvenilmeyen kod çağrılan kodu geri çağırmaları kullanmak için.  
  
## <a name="outwrites"></a>\_Out_writes\_  
 Aşağıdaki örnek, bir ortak kötüye kullanımı gösterir `_Out_writes_`.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_writes_(size) CHAR *pb,   
    DWORD size  
);  
  
```  
  
 Ek açıklama `_Out_writes_` arabellek olduğunu gösterir. Sahip `cb` Çıkışta başlatılan ilk bayt ile ayrılan bayt sayısı. Bu ek açıklama kesinlikle yanlış değil ve ayrılmış boyutu ifade etmek yararlı olabilir. Bununla birlikte, işlev tarafından kaç öğeleri başlatılır söylemez.  
  
 Sonraki örnek, tam olarak başlatılmış bölümü arabellek tam boyutunu belirtmek için üç doğru şekilde gösterir.  
  
```cpp  
  
// Correct  
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,   
    DWORD size,  
    PDWORD pCount  
);  
  
void Func2(_Out_writes_all_(size) CHAR *pb,   
    DWORD size  
);  
  
void Func3(_Out_writes_(size) PSTR pb,   
    DWORD size  
);  
  
```  
  
## <a name="out-pstr"></a>\_Çıkış\_ PSTR  
 Kullanımını `_Out_ PSTR` neredeyse her zaman yanlış. Bu sahip için bir karakter arabelleği işaret eden bir output parametresi olarak yorumlanır ve NULL ile sonlandırılmış.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_ PSTR pFileName, size_t n);  
  
// Correct  
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);  
  
```  
  
 Ek açıklamanın ister `_In_ PCSTR` ortak ve kullanışlıdır. NULL sonlandırma sahip bir Giriş dizesinin işaret önkoşulu `_In_` NULL ile sonlandırılmış bir dize tanınmasını sağlar.  
  
## <a name="in-wchar-p"></a>\_İçinde\_ WCHAR * p  
 `_In_ WCHAR* p` Giriş bir işaretçi olduğunu söylüyor `p` işaret eden bir karakter. Ancak, çoğu durumda, kullanılmaya belirtimi budur olmayabilir. Bunun yerine, amaçlanan büyük olasılıkla NULL ile sonlandırılmış bir dizinin özelliğidir; Bunu yapmak için kullanın `_In_ PWSTR`.  
  
```cpp  
  
// Incorrect  
void Func1(_In_ WCHAR* wszFileName);  
  
// Correct  
void Func2(_In_ PWSTR wszFileName);  
  
```  
  
 NULL sonlandırma uygun belirtimi eksik yaygındır. Uygun kullanın `STR` sürüme türü, aşağıdaki örnekte gösterildiği gibi değiştirin.  
  
```cpp  
  
// Incorrect  
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)  
{  
    return strcmp(p1, p2) == 0;  
}  
  
// Correct  
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)  
{  
    return strcmp(p1, p2) == 0;  
}  
  
```  
  
## <a name="outrange"></a>\_Out_range\_  
 Parametre bir işaretçi ise ve aralığı işaretçi tarafından kullanılacak işaret ettiği öğenin değerini ifade etmek istiyorsanız `_Deref_out_range_` yerine `_Out_range_`. Aşağıdaki örnekte, dizi * pcbFilled ifade edilir, pcbFilled değil.  
  
```cpp  
  
// Incorrect  
void Func1(  
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,   
    DWORD cbSize,   
    _Out_range_(0, cbSize) DWORD *pcbFilled  
);  
  
// Correct  
void Func2(  
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,   
    DWORD cbSize,   
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled   
);  
  
```  
  
 `_Deref_out_range_(0, cbSize)` içinden gösterilen çünkü bazı araçları için kesinlikle gerekli değil `_Out_writes_to_(cbSize,*pcbFilled)`, ancak bütünlük açısından buraya gösterilir.  
  
## <a name="wrong-context-in-when"></a>Yanlış bağlamda \_olduğunda\_  
 Başka bir yaygın hata sonrası durum değerlendirmesi için önkoşulları kullanmaktır. Aşağıdaki örnekte, `_Requires_lock_held_` koşuludur.  
  
```cpp  
  
// Incorrect  
_When_(return == 0, _Requires_lock_held_(p->cs))  
int Func1(_In_ MyData *p, int flag);  
  
// Correct  
_When_(flag == 0, _Requires_lock_held_(p->cs))  
int Func2(_In_ MyData *p, int flag);  
  
```  
  
 İfade `result` öncesi durumda kullanılabilir değil bir son durum değeri belirtir.  
  
## <a name="true-in-success"></a>TRUE olarak \_başarılı\_  
 İşlev dönüş değeri, sıfır dışında olduğunda başarılı kullanırsanız `return != 0` yerine başarı koşulu olarak `return == TRUE`. NonZero derleyici sağlayan gerçek değerine denklik mutlaka gelmez `TRUE`. Parametre `_Success_` ifade olan ve aşağıdaki ifadeler eşdeğer olarak değerlendirilir: `return != 0`, `return != false`, `return != FALSE`, ve `return` parametreleri veya karşılaştırmalar.  
  
```cpp  
  
// Incorrect  
_Success_(return == TRUE, _Acquires_lock_(*lpCriticalSection))  
BOOL WINAPI TryEnterCriticalSection(  
  _Inout_ LPCRITICAL_SECTION lpCriticalSection  
);  
  
// Correct  
_Success_(return != 0, _Acquires_lock_(*lpCriticalSection))  
BOOL WINAPI TryEnterCriticalSection(  
  _Inout_ LPCRITICAL_SECTION lpCriticalSection  
);  
  
```  
  
## <a name="reference-variable"></a>Başvuru değişkenini  
 Bir başvuru değişkenini SAL'ın önceki sürümünü örtük işaretçi ek açıklama hedefi olarak kullanılan ve eklenmesi gereken bir `__deref` başvuru değişkenine bağlı ek açıklamalara. Bu sürüm nesnenin kendisini kullanır ve ek gerektirmez `_Deref_`.  
  
```cpp  
  
// Incorrect  
void Func1(  
    _Out_writes_bytes_all_(cbSize) BYTE *pb,   
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize  
);  
  
// Correct  
void Func2(  
    _Out_writes_bytes_all_(cbSize) BYTE *pb,   
    _Out_range_(0, 2) _Out_ DWORD &cbSize  
);  
  
```  
  
## <a name="annotations-on-return-values"></a>Ek açıklamalar dönüş değerleri  
 Aşağıdaki örnek, dönüş değeri ek açıklamalarda ortak bir sorunu gösterir.  
  
```cpp  
  
// Incorrect  
_Out_opt_ void *MightReturnNullPtr1();  
  
// Correct  
_Ret_maybenull_ void *MightReturnNullPtr2();  
  
```  
  
 Bu örnekte, `_Out_opt_` diyor işaretçi önkoşuluna bir parçası olarak NULL olabilir. Ancak, dönüş değeri için önkoşulları uygulanamaz. Bu durumda, doğru ek açıklama olup `_Ret_maybenull_`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C/C++ kod hatalarını azaltmak için SAL ek açıklamalarını kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL'yi anlama](../code-quality/understanding-sal.md)   
 [İşlev parametrelerini ve dönüş değerlerini açıklama](../code-quality/annotating-function-parameters-and-return-values.md)   
 [İşlev davranışını yorumlama](../code-quality/annotating-function-behavior.md)   
 [Yapıları ve sınıfları yorumlama](../code-quality/annotating-structs-and-classes.md)   
 [Kilitlenme davranışını yorumlama](../code-quality/annotating-locking-behavior.md)   
 [Açıklamanın ne zaman ve nereye uygulanacağını belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [İç İşlevler](../code-quality/intrinsic-functions.md)



