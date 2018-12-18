---
title: SAL'ı Anlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 712d99f3839982632e54b622b3512eb611f2bf95
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792827"
---
# <a name="understanding-sal"></a>SAL'ı Anlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft kaynak kodu ek açıklama dili (SAL) bir işlev parametrelerini ve bunlarla ilgili kolaylaştıran varsayımların tamamlandığında kolaylaştıran garanti nasıl kullandığını tanımlamak için kullanabileceğiniz ek açıklamaları sunmaktadır. Ek açıklamalar üstbilgi dosyasında tanımlanan `<sal.h>`. C++ için Visual Studio kod analizi, kendi analiz işlevleri değiştirmek için SAL ek açıklamalarını kullanır. Windows Sürücü Geliştirme için SAL 2.0 hakkında daha fazla bilgi için bkz. [SAL 2.0 ek açıklamalar için Windows sürücüleri](http://go.microsoft.com/fwlink/?LinkId=250979).  
  
 Yerel olarak, C ve C++ geliştiricileri amacı ve değişmezlik terimlerinin tutarlı bir şekilde ifade etmek için yalnızca sınırlı yolları sağlayın. SAL ek açıklamalarını kullanarak bunları kullanan geliştiriciler, bunları nasıl kullanacağınızı daha iyi anlayabilmeniz işlevlerinizi daha ayrıntılı tanımlayabilirsiniz.  
  
## <a name="what-is-sal-and-why-should-you-use-it"></a>SAL nedir ve neden kullanmalısınız?  
 Kısacası, SAL kodunuzu iade derleyici izin vermek için bir Hesaplı yoludur.  
  
### <a name="sal-makes-code-more-valuable"></a>SAL kod daha değerli hale getirir  
 SAL insanlar hem kod çözümleme araçları kod tasarımınızı daha anlaşılır yapmanıza yardımcı olabilir. C çalışma zamanı işlevi gösteren Bu örnek göz önünde bulundurun `memcpy`:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 Bu işlevin ne yaptığını anlayabilirsiniz? Bir işlev uygulanan ya da adlı programı doğruluğunu sağlamak için belirli özellikleri korunmalıdır. Yalnızca bir örnekteki gibi bir bildirim bakarak, bunların ne olduğunu bilmiyorum. SAL ek açıklamalar olmadan, belge veya kod açıklamaları dayalı etmesi gerekir. İçin MSDN belgelerine işte `memcpy` söylüyor:  
  
> "Kopya kaynak hedefe kopyalanmaya bayt sayısı. Kaynak ve hedef çakışırsa, memcpy davranışı tanımsızdır. Çakışan bölgeleri işlemek için memcpy kullanın.   
> **Güvenlik Notu:** boyutta veya daha büyük kaynak arabelleği hedef arabellek aynı olduğundan emin olun. Daha fazla bilgi için arabellek taşmalarını bkz."  
  
 Belgeler, birkaç kodunuzu program doğruluğunu sağlamak için belirli özelliklerini korumak sahip Öner bit bilgi içerir:  
  
- `memcpy` kopya `count` hedef arabelleğinin kaynak arabellekteki bayt.  
  
- Hedef arabelleğinin en az kaynak arabelleği kadar büyük olmalıdır.  
  
  Ancak, derleyici belgeleri veya resmi olmayan yorumlar okunamıyor. İki arabellek arasında bir ilişki olduğunu bilmez ve `count`, ve bu da etkin bir ilişki hakkında tahmin edilemez. SAL burada gösterildiği gibi işlev uygulaması ve özellikleri hakkında daha fazla netlik sağlayabilir:  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 Bu ek açıklamalar MSDN belgelerinde benzer, ancak bunlar daha kısa ve bunlar bir anlam desenini izler dikkat edin. Bu kodu okuma, bu işlevin özelliklerine ve arabellek taşması güvenlik sorunlarını önlemek nasıl hızlı bir şekilde anlayabilirsiniz. Daha da iyi SAL sağlayan semantik desenleri otomatik kod analiz araçları olası hataların erken bulma, etkinliğini ve verimliliğini artırabilir. Birisi bu çalışmalarında uygulaması Yazar Imagine `wmemcpy`:  
  
```cpp  
  
wchar_t * wmemcpy(  
   _Out_writes_all_(count) wchar_t *dest,   
   _In_reads_(count) const wchar_t *src,   
   size_t count)  
{  
   size_t i;  
   for (i = 0; i <= count; i++) { // BUG: off-by-one error  
      dest[i] = src[i];  
   }  
   return dest;  
}  
  
```  
  
 Bu uygulama, ortak bir kapalı tek hata içeriyor. Neyse ki, kod yazar SAL arabellek boyutu ek açıklama eklenen — tek başına Bu işlev analiz ederek hataya bir kod çözümleme aracı catch.  
  
### <a name="sal-basics"></a>SAL temelleri  
 SAL dört temel tür kullanım desenine göre kategorize edilir parametreleri tanımlar.  
  
|Kategori|Parametre ek açıklaması|Açıklama|  
|--------------|--------------------------|-----------------|  
|**Giriş olarak çağrılan işlev**|`_In_`|Veriler çağrılan işleve geçirilir ve salt okunur olarak kabul edilir.|  
|**Giriş olarak çağrılan işlev ve çağırana çıkış**|`_Inout_`|Tüm dünyada kullanılabilir veriler işleve geçirilen ve potansiyel olarak değiştirilir.|  
|**Arayan çıkışı**|`_Out_`|Çağıran, yalnızca yazmak çağrılan işlev için alan sağlar. Çağrılan işlev, verileri alana yazar.|  
|**Arayan bir işaretçiye çıktısı**|`_Outptr_`|Gibi **çağırana çıkış**. Çağrılan işlev tarafından döndürülen değerin bir işaretçisidir.|  
  
 Bu dört temel ek açıklamaları daha açık olarak çeşitli şekillerde yapılabilir. Varsayılan olarak, ek açıklamalı işaretçi parametrelerini gerekli olarak kabul edilir — NULL olmayan olmaları gerekir başarılı olması işlev. En sık kullanılan temel ek açıklamalar çeşitlemesi işaretçi parametresi isteğe bağlı olduğunu gösterir; NULL ise, işlev yine de çalışmasını yaparak başarılı olabilir.  
  
 Bu tablo, gerekli ve isteğe bağlı parametreler arasında ayrım yapmak gösterilmektedir:  
  
||Parametreler gereklidir|Parametreler isteğe bağlıdır|  
|-|-----------------------------|-----------------------------|  
|**Giriş olarak çağrılan işlev**|`_In_`|`_In_opt_`|  
|**Giriş olarak çağrılan işlev ve çağırana çıkış**|`_Inout_`|`_Inout_opt_`|  
|**Arayan çıkışı**|`_Out_`|`_Out_opt_`|  
|**Arayan bir işaretçiye çıktısı**|`_Outptr_`|`_Outptr_opt_`|  
  
 Bu ek açıklamalar olası başlatılmamış değerleri belirlemek ve biçimsel ve doğru bir şekilde geçersiz null işaretçisi kullanır. Gerekli parametre için NULL geçirme Çökmeye neden veya döndürülecek bir "başarısız" hata kodu neden olabilir. Her iki durumda da, kendi iş yaparak işlevi başarılı olamaz.  
  
## <a name="sal-examples"></a>SAL örnekleri  
 Bu bölüm, kod örnekleri için temel SAL ek açıklamalarını gösterir.  
  
### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>Hataları bulmak için Visual Studio Kod Analizi aracını kullanma  
 Örneklerde, Visual Studio kod analizi aracı, kod hataları bulmak için SAL ek açıklamalarını ile birlikte kullanılır. Bunu nasıl yapacağınız aşağıda verilmiştir.  
  
##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>Visual Studio Kod Analizi araçları ve SAL'ı kullanmak için  
  
1. Visual Studio'da SAL ek açıklamaları içeren bir C++ projesini açın.  
  
2. Menü çubuğunda, **derleme**, **çözüm üzerinde kod analizini Çalıştır**.  
  
    Göz önünde bulundurun \_içinde\_ bu bölümdeki örnek. Kod Analizi üzerinde çalıştırıyorsanız, bu uyarı görüntülenir:  
  
   > **C6387 Geçersiz parametre değeri**   
   > 'pInt', '0' olabilir: Bu 'InCallee' işlevinin belirtimine bağlı kalmıyor.  
  
### <a name="example-the-in-annotation"></a>Örnek: \_içinde\_ ek açıklaması  
 `_In_` Ek açıklama gösterir:  
  
-   Parametresi, geçerli olması gerekir ve değiştirilmeyecek.  
  
-   İşlevi yalnızca tek öğeli arabelleğinden okur.  
  
-   Çağıranın arabellek sağlayın ve başlatmanız gerekir.  
  
-   `_In_` "salt okunur" belirtir. Sıkça uygulamaktır `_In_` olması gereken bir parametreye `_Inout_` ek açıklama yerine.  
  
-   `_In_` Ancak, işaretçi olmayan skalerler Çözümleyicisinde tarafından göz ardı izin verilir.  
  
```cpp  
void InCallee(_In_ int *pInt)  
{  
   int i = *pInt;  
}  
  
void GoodInCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
  
   InCallee(pInt);  
   delete pInt;     
}  
  
void BadInCaller()  
{  
   int *pInt = NULL;  
   InCallee(pInt); // pInt should not be NULL  
}  
  
```  
  
 Bu örneği temel Visual Studio Kod Analizi kullanırsanız arayanlar için başlatılmış olan bir arabellek için Null olmayan bir işaretçi geçtiğini doğrular `pInt`. Bu durumda, `pInt` işaretçisi, NULL olamaz.  
  
### <a name="example-the-inopt-annotation"></a>Örnek: \_In_opt\_ ek açıklaması  
 `_In_opt_` aynı `_In_`, giriş parametresinin NULL olmasına izin verilen ve bu nedenle, işlev bu denetlemelisiniz hariç.  
  
```cpp  
  
void GoodInOptCallee(_In_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
   }  
}  
  
void BadInOptCallee(_In_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
}  
  
void InOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOptCallee(pInt);  
   BadInOptCallee(pInt);  
}  
  
```  
  
 Visual Studio Kod Analizi arabellek erişmeden önce işlevi için NULL denetimleri doğrular.  
  
### <a name="example-the-out-annotation"></a>Örnek: \_kullanıma\_ ek açıklaması  
 `_Out_` bir öğeyi buffer'a işaret eden bir NULL olmayan işaretçi geçirilir ve işlev öğe başlatır sık karşılaşılan bir senaryodur destekler. Çağıranın çağırmadan önce arabellek başlatmak zorunda değildir; Çağrılan işlev döndürülmeden önce başlatmak üzere vaat eder.  
  
```cpp  
  
void GoodOutCallee(_Out_ int *pInt)  
{  
   *pInt = 5;  
}  
  
void BadOutCallee(_Out_ int *pInt)  
{  
   // Did not initialize pInt buffer before returning!  
}  
  
void OutCaller()  
{  
   int *pInt = new int;  
   GoodOutCallee(pInt);  
   BadOutCallee(pInt);  
   delete pInt;  
}  
  
```  
  
 Visual Studio kod analizi aracı doğrulama çağıran bir arabellek için NULL olmayan bir işaretçi geçirir `pInt` ve döndürülmeden önce arabellek işlevi tarafından başlatılır.  
  
### <a name="example-the-outopt-annotation"></a>Örnek: \_Out_opt\_ ek açıklaması  
 `_Out_opt_` aynı `_Out_`, parametresi NULL olmasına izin verilen ve bu nedenle, işlev bu denetlemelisiniz hariç.  
  
```cpp  
  
void GoodOutOptCallee(_Out_opt_ int *pInt)  
{  
   if (pInt != NULL) {  
      *pInt = 5;  
   }  
}  
  
void BadOutOptCallee(_Out_opt_ int *pInt)  
{  
   *pInt = 5; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutOptCaller()  
{  
   int *pInt = NULL;  
   GoodOutOptCallee(pInt);  
   BadOutOptCallee(pInt);  
}  
  
```  
  
 Visual Studio Kod Analizi doğrulama Bu işlev null önce denetler `pInt` referans edildi ve `pInt` döndürülmeden önce arabellek işlevi tarafından başlatılır, NULL değil.  
  
### <a name="example-the-inout-annotation"></a>Örnek: \_Inout\_ ek açıklaması  
 `_Inout_` işlev tarafından değiştirilebilir bir işaretçi parametresi açıklama eklemek için kullanılır. İşaretçi çağırmadan önce geçerli başlatılmış veriler işaret etmelidir ve değişiklik olsa bile, geçerli bir değer geri hala olmalıdır. Ek açıklama işlevi serbestçe okuma ve tek öğeli arabelleğe yazmak belirtir. Çağıranın arabellek sağlayın ve başlatmanız gerekir.  
  
> [!NOTE]
>  Gibi `_Out_`, `_Inout_` değiştirilebilir bir değer için uygulamanız gerekir.  
  
```cpp  
  
void InOutCallee(_Inout_ int *pInt)  
{  
   int i = *pInt;  
   *pInt = 6;  
}  
  
void InOutCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
   InOutCallee(pInt);  
   delete pInt;  
}  
  
void BadInOutCaller()  
{  
   int *pInt = NULL;  
   InOutCallee(pInt); // ‘pInt’ should not be NULL  
}  
  
```  
  
 Visual Studio Kod Analizi arayanlar için başlatılmış olan bir arabellek için NULL olmayan bir işaretçi geçtiğini doğrular `pInt`ve iade önce `pInt` hala NULL olmayan ve arabellek başlatılır.  
  
### <a name="example-the-inoutopt-annotation"></a>Örnek: \_Inout_opt\_ ek açıklaması  
 `_Inout_opt_` aynı `_Inout_`, giriş parametresinin NULL olmasına izin verilen ve bu nedenle, işlev bu denetlemelisiniz hariç.  
  
```cpp  
  
void GoodInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
      *pInt = 6;  
   }  
}  
  
void BadInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
   *pInt = 6;  
}  
  
void InOutOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOutOptCallee(pInt);  
   BadInOutOptCallee(pInt);  
}  
  
```  
  
 Visual Studio Kod Analizi doğrular arabellek erişmeden önce ve bu işlev için NULL denetimleri `pInt` döndürülmeden önce arabellek işlevi tarafından başlatılır, NULL değil.  
  
### <a name="example-the-outptr-annotation"></a>Örnek: \_Outptr\_ ek açıklaması  
 `_Outptr_` bir işaretçiyi döndürmek için hedeflenen bir parametreye açıklama eklemek için kullanılır.  Parametre NULL olmamalıdır ve çağrılan işlev NULL olmayan bir işaretçi döndürür ve başlatılmış veriler için bu işaretçi işaret eder.  
  
```cpp  
  
void GoodOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 5;  
  
   *pInt = pInt2;  
}  
  
void BadOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   // Did not initialize pInt buffer before returning!  
   *pInt = pInt2;  
}  
  
void OutPtrCaller()  
{  
   int *pInt = NULL;  
   GoodOutPtrCallee(&pInt);  
   BadOutPtrCallee(&pInt);  
}  
  
```  
  
 Visual Studio Kod Analizi doğrular çağıran bir NULL olmayan işaretçi geçtiği `*pInt`, ve döndürülmeden önce arabellek işlevi tarafından başlatılır.  
  
### <a name="example-the-outptropt-annotation"></a>Örnek: \_Outptr_opt\_ ek açıklaması  
 `_Outptr_opt_` aynı `_Outptr_`parametresi isteğe bağlıdır, ancak — çağıran parametresi için bir NULL işaretçi geçirebilirsiniz.  
  
```cpp  
  
void GoodOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
  
   if(pInt != NULL) {  
      *pInt = pInt2;  
   }  
}  
  
void BadOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
   *pInt = pInt2; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutPtrOptCaller()  
{  
   int **ppInt = NULL;  
   GoodOutPtrOptCallee(ppInt);  
   BadOutPtrOptCallee(ppInt);  
}  
  
```  
  
 Visual Studio Kod Analizi doğrulama Bu işlev null önce denetler `*pInt` referans edildi ve döndürülmeden önce arabellek işlevi tarafından başlatılır.  
  
### <a name="example-the-success-annotation-in-combination-with-out"></a>Örnek: \_başarı\_ birlikte ek açıklama \_çıkış\_  
 Ek açıklamalar, çoğu nesnelere uygulanabilir.  Özellikle, tam bir işlev açıklama ekleyebilirsiniz.  Bir işlev en belirgin özelliklerini, başarılı veya başarısız, biridir. Ancak bir arabellek boyutuna arasındaki ilişkiyi gibi C/C++ işlevi başarı veya başarısızlık express olamaz. Kullanarak `_Success_` ek açıklama, bir işlev için hangi başarının neye benzediğini söyleyebilirsiniz.  Parametre `_Success_` ek açıklama olduğunu da true olduğunda işlevi başarılı olduğunu belirten bir ifade. İfade, ek açıklama ayrıştırıcının işleyebilir herhangi bir şey olabilir. İşlev başarılı olduğunda işlev döndürdükten sonra ek açıklamalar etkilerini yalnızca geçerlidir. Bu örnek gösterir nasıl `_Success_` etkileşimde `_Out_` doğru şeyleri yapacakları konusunda. Anahtar sözcüğünü kullanabilirsiniz `return` dönüş değerini göstermek için.  
  
```cpp  
  
_Success_(return != false) // Can also be stated as _Success_(return)  
bool GetValue(_Out_ int *pInt, bool flag)  
{  
   if(flag) {  
      *pInt = 5;  
      return true;  
   } else {  
      return false;  
   }  
}  
  
```  
  
 `_Out_` Ek açıklama neden Visual Studio kodu doğrulamak için analiz çağıran bir arabellek için NULL olmayan bir işaretçi geçirir `pInt`, ve döndürülmeden önce arabellek işlevi tarafından başlatılır.  
  
## <a name="sal-best-practice"></a>SAL en iyi uygulama  
  
### <a name="adding-annotations-to-existing-code"></a>Ek açıklamalar için mevcut kod ekleme  
 SAL, güvenlik ve güvenilirlik kodunuzun geliştirmenize yardımcı olabilecek güçlü bir teknolojidir. SAL öğrendikten sonra günlük işleriniz için yeni yetenek uygulayabilirsiniz. Yeni kod içinde tasarıma SAL tabanlı özellikleri kullanabilirsiniz; eski kod içinde ek açıklamalar artımlı olarak ekleyebilir ve her güncelleştirdiğinizde, böylelikle avantajları artırabilirsiniz.  
  
 Microsoft ortak üst bilgileri zaten açıklama. Bu nedenle, projelerinizde, önce yaprak düğümü işlevlerini ve en çok faydayı almak için Win32 API'ları çağırma işlevlerini ek açıklama, öneririz.  
  
### <a name="when-do-i-annotate"></a>Ne zaman miyim açıklama?  
 Bazı Kılavuzlar şunlardır:  
  
- Tüm işaretçi parametrelerini açıklama ekleyin.  
  
- Değer aralığı ek açıklamaları, böylece Kod Analizi arabellek ve işaretçi güvenliği sağlamak açıklama ekleyin.  
  
- Kilitleme kuralları ve kilitleme yan etkileri açıklama ekleyin. Daha fazla bilgi için [kilitlenme davranışını yorumlama](../code-quality/annotating-locking-behavior.md).  
  
- Sürücü özellikleri ve diğer etki alanına özgü özellikleri açıklama ekleyin.  
  
  Veya tüm parametreleri boyunca hedefi, düz hale getirmek ve ek açıklamalar yapılmış denetlenecek kolaylaştırmak için açıklama ekleyebilirsiniz.  
  
## <a name="related-resources"></a>İlgili Kaynaklar  
 [Kod Analizi ekip blogu](http://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C/C++ kod hatalarını azaltmak için SAL ek açıklamalarını kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [İşlev parametrelerini ve dönüş değerlerini açıklama](../code-quality/annotating-function-parameters-and-return-values.md)   
 [İşlev davranışını yorumlama](../code-quality/annotating-function-behavior.md)   
 [Yapıları ve sınıfları yorumlama](../code-quality/annotating-structs-and-classes.md)   
 [Kilitlenme davranışını yorumlama](../code-quality/annotating-locking-behavior.md)   
 [Açıklamanın ne zaman ve nereye uygulanacağını belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [En İyi Yöntemler ve Örnekler](../code-quality/best-practices-and-examples-sal.md)



