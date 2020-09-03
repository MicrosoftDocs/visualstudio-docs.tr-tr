---
title: Işlev parametrelerine ve dönüş değerlerine açıklama ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Ouptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 71854388f3fb1c5eaea7d40ed2757af9cecacf1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543812"
---
# <a name="annotating-function-parameters-and-return-values"></a>İşlev Parametrelerini ve Dönüş Değerlerini Açıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu makalede basit işlev parametreleri için ek açıklamaların tipik kullanımları ve yapı ve sınıf işaretçileri ve birçok arabellek türü açıklanmaktadır.  Bu makalede ayrıca ek açıklamalar için ortak kullanım desenleri gösterilmektedir. İşlevlerle ilgili ek ek açıklamalar için bkz. [Işlev davranışına açıklama ekleme](../code-quality/annotating-function-behavior.md)  
  
## <a name="pointer-parameters"></a>İşaretçi parametreleri  
 Aşağıdaki tablodaki ek açıklamalar için, işaretçi parametresine açıklama eklendiğinde, işaretçi null ise çözümleyici bir hata bildirir.  Bu, işaretçiler için ve işaret edilen tüm veri öğeleri için geçerlidir.  
  
 **Ek açıklamalar ve açıklamalar**  
  
- `_In_`  
  
     Yapılar, yapılar, yapılara yönelik işaretçiler ve benzeri bir giriş parametresi olan annotates.  Açıkça basit dolandırıcıklar üzerinde kullanılabilir.  Parametrenin ön durumunda geçerli olması ve değiştirilmeyecektir.  
  
- `_Out_`  
  
     Yapıları, yapıları, yapılara yönelik işaretçileri ve benzeri bir çıkış parametresi olan annotates.  Bunu değer döndürmeyen bir nesneye uygulamayın — Örneğin, değere göre geçirilmiş bir skaler.  Parametrenin ön durumunda geçerli olması gerekmez, ancak durum sonrası için geçerli olmalıdır.  
  
- `_Inout_`  
  
     İşlev tarafından değiştirilecek bir parametreyi annotates.  Hem ön durum hem de durum durumunda geçerli olmalıdır, ancak çağrıdan önce ve sonra farklı değerlere sahip olduğu varsayılır. Değiştirilebilir bir değere uygulamanız gerekir.  
  
- `_In_z_`  
  
     Giriş olarak kullanılan null ile sonlandırılmış bir dize işaretçisi.  Dize, ön durumunda geçerli olmalıdır.  `PSTR`Zaten doğru ek açıklamaların bulunduğu varyantlar tercih edilir.  
  
- `_Inout_z_`  
  
     Değiştirilecek, null ile sonlandırılmış bir karakter dizisine yönelik bir işaretçi.  Çağrıdan önce ve sonra geçerli olmalıdır, ancak değer değişmiş olarak kabul edilir.  Null Sonlandırıcı taşınabilir, ancak yalnızca orijinal null sonlandırıcısına kadar olan öğelere erişilebilir.  
  
- `_In_reads_(s)`  
  
     `_In_reads_bytes_(s)`  
  
     İşlev tarafından okunan dizi için bir işaretçi.  Dizi `s` , hepsi geçerli olması gereken boyut öğeleridir.  
  
     `_bytes_`Değişken, boyutu öğeler yerine bayt olarak verir. Bunu yalnızca boyut öğe olarak ifade edilemez ' i kullanın.  Örneğin, `char` dizeler `_bytes_` yalnızca kullanan benzer bir işlev ise değişkeni kullanır `wchar_t` .  
  
- `_In_reads_z_(s)`  
  
     Null sonlandırılmış ve bilinen bir boyuta sahip dizi için bir işaretçi. Null sonlandırıcısına sahip öğeler — veya `s` null Sonlandırıcı yoksa, ön durumunda geçerli olmalıdır.  Boyut bayt olarak biliniyorsa `s` öğe boyutuna göre ölçeklendirin.  
  
- `_In_reads_or_z_(s)`  
  
     Null sonlandırılmış veya bilinen bir boyut veya her ikisi içeren bir dizi işaretçisi. Null sonlandırıcısına sahip öğeler — veya `s` null Sonlandırıcı yoksa, ön durumunda geçerli olmalıdır.  Boyut bayt olarak biliniyorsa `s` öğe boyutuna göre ölçeklendirin.  (Aile için kullanılır `strn` .)  
  
- `_Out_writes_(s)`  
  
     `_Out_writes_bytes_(s)`  
  
     `s`İşlev tarafından yazılacak öğe (yanıt. bayt) dizisine yönelik bir işaretçi.  Dizi öğelerinin ön durumunda geçerli olması gerekmez ve durum sonrası için geçerli olan öğe sayısı belirtilmemiş olur.  Parametre türünde ek açıklamalar varsa, bunlar durum sonrası ' a uygulanır. Örneğin, aşağıdaki kodu göz önünde bulundurun.  
  
     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`  
  
     Bu örnekte, çağıran öğesi için bir arabellek sağlar `size` `p1` .  `MyStringCopy` Bu öğelerin bazılarını geçerli hale getirir. Daha da önemlisi, `_Null_terminated_` üzerindeki ek açıklama, `PWSTR` `p1` durum sonrası için null olarak sonlandırılmış anlamına gelir.  Bu şekilde, geçerli öğe sayısı hala iyi tanımlanmış, ancak belirli bir öğe sayısı gerekli değildir.  
  
     `_bytes_`Değişken, boyutu öğeler yerine bayt olarak verir. Bunu yalnızca boyut öğe olarak ifade edilemez ' i kullanın.  Örneğin, `char` dizeler `_bytes_` yalnızca kullanan benzer bir işlev ise değişkeni kullanır `wchar_t` .  
  
- `_Out_writes_z_(s)`  
  
     Öğe dizisine yönelik bir işaretçi `s` .  Öğelerin ön durumunda geçerli olması gerekmez.  Durum sonrası 'de, mevcut olması gereken null Sonlandırıcı aracılığıyla bulunan öğeler geçerli olmalıdır.  Boyut bayt olarak biliniyorsa `s` öğe boyutuna göre ölçeklendirin.  
  
- `_Inout_updates_(s)`  
  
     `_Inout_updates_bytes_(s)`  
  
     Bir dizi için, hem okunan hem de işlevine yazılan bir işaretçi.  Bu, bir boyut `s` öğeleridir ve ön durum ve durum sonrası için geçerlidir.  
  
     `_bytes_`Değişken, boyutu öğeler yerine bayt olarak verir. Bunu yalnızca boyut öğe olarak ifade edilemez ' i kullanın.  Örneğin, `char` dizeler `_bytes_` yalnızca kullanan benzer bir işlev ise değişkeni kullanır `wchar_t` .  
  
- `_Inout_updates_z_(s)`  
  
     Null sonlandırılmış ve bilinen bir boyuta sahip dizi için bir işaretçi. Mevcut olması gereken null Sonlandırıcı aracılığıyla bulunan öğeler, hem ön durum hem de durum sonrası için geçerli olmalıdır.  Durum sonrası değeri, ön durumundaki değerden farklı olacak şekilde belirlenir; Bu, null Sonlandırıcı konumunu içerir. Boyut bayt olarak biliniyorsa `s` öğe boyutuna göre ölçeklendirin.  
  
- `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Öğe dizisine yönelik bir işaretçi `s` .  Öğelerin ön durumunda geçerli olması gerekmez.  Durum sonrası, `c` -TH öğesine kadar olan öğelerin geçerli olması gerekir.  Boyut bayt cinsinden bilindiğinde, `s` `c` öğe boyutuna göre ve, ölçeği kullanın veya şu `_bytes_` şekilde tanımlanan değişkeni kullanın:  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     Diğer bir deyişle, ön durumunda olan arabellekte bulunan her öğe, `s` son durum durumunda geçerlidir.  Örneğin:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
- `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     İşlev tarafından hem okunan hem yazılan dizi için bir işaretçi.  Bu, `s` tümünün ön durumunda geçerli olması gereken bir boyut öğeleridir ve `c` öğelerin durum sonrası geçerli olması gerekir.  
  
     `_bytes_`Değişken, boyutu öğeler yerine bayt olarak verir. Bunu yalnızca boyut öğe olarak ifade edilemez ' i kullanın.  Örneğin, `char` dizeler `_bytes_` yalnızca kullanan benzer bir işlev ise değişkeni kullanır `wchar_t` .  
  
- `_Inout_updates_z_(s)`  
  
     Null sonlandırılmış ve bilinen bir boyuta sahip dizi için bir işaretçi. Mevcut olması gereken null Sonlandırıcı aracılığıyla bulunan öğeler, hem ön durum hem de durum sonrası için geçerli olmalıdır.  Durum sonrası değeri, ön durumundaki değerden farklı olacak şekilde belirlenir; Bu, null Sonlandırıcı konumunu içerir. Boyut bayt olarak biliniyorsa `s` öğe boyutuna göre ölçeklendirin.  
  
- `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Öğe dizisine yönelik bir işaretçi `s` .  Öğelerin ön durumunda geçerli olması gerekmez.  Durum sonrası, `c` -TH öğesine kadar olan öğelerin geçerli olması gerekir.  Boyut bayt cinsinden bilindiğinde, `s` `c` öğe boyutuna göre ve, ölçeği kullanın veya şu `_bytes_` şekilde tanımlanan değişkeni kullanın:  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     Diğer bir deyişle, ön durumunda olan arabellekte bulunan her öğe, `s` son durum durumunda geçerlidir.  Örneğin:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
- `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     İşlev tarafından hem okunan hem yazılan dizi için bir işaretçi.  Bu, `s` tümünün ön durumunda geçerli olması gereken bir boyut öğeleridir ve `c` öğelerin durum sonrası geçerli olması gerekir.  
  
     `_bytes_`Değişken, boyutu öğeler yerine bayt olarak verir. Bunu yalnızca boyut öğe olarak ifade edilemez ' i kullanın.  Örneğin, `char` dizeler `_bytes_` yalnızca kullanan benzer bir işlev ise değişkeni kullanır `wchar_t` .  
  
- `_Inout_updates_all_(s)`  
  
     `_Inout_updates_bytes_all_(s)`  
  
     Boyut öğelerinin işlevi tarafından hem okunan hem yazılan dizi için bir işaretçi `s` . Eşdeğer olarak tanımlanan:  
  
     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`  
  
     Diğer bir deyişle, ön durumunda olan arabellekte bulunan her öğe, `s` ön durum ve sonrası durumunda geçerlidir.  
  
     `_bytes_`Değişken, boyutu öğeler yerine bayt olarak verir. Bunu yalnızca boyut öğe olarak ifade edilemez ' i kullanın.  Örneğin, `char` dizeler `_bytes_` yalnızca kullanan benzer bir işlev ise değişkeni kullanır `wchar_t` .  
  
- `_In_reads_to_ptr_(p)`  
  
     `p` `_Curr_` (Yani `p` eksi) ifadesi için `_Curr_` uygun dil standardı tarafından tanımlanan dizi için bir işaretçi.  Öncesindeki öğelerin `p` ön durumunda geçerli olması gerekir.  
  
- `_In_reads_to_ptr_z_(p)`  
  
     `p` `_Curr_` (Yani `p` eksi) ifadesi için `_Curr_` uygun dil standardı tarafından tanımlanan, null ile sonlandırılmış diziye yönelik bir işaretçi.  Öncesindeki öğelerin `p` ön durumunda geçerli olması gerekir.  
  
- `_Out_writes_to_ptr_(p)`  
  
     `p` `_Curr_` (Yani `p` eksi) ifadesi için `_Curr_` uygun dil standardı tarafından tanımlanan dizi için bir işaretçi.  ' Den önceki öğelerin `p` ön durumunda geçerli olması gerekmez ve durum sonrası için geçerli olmalıdır.  
  
- `_Out_writes_to_ptr_z_(p)`  
  
     `p` `_Curr_` (Yani `p` eksi) ifadesi için `_Curr_` uygun dil standardı tarafından tanımlanan, null ile sonlandırılmış diziye yönelik bir işaretçi.  ' Den önceki öğelerin `p` ön durumunda geçerli olması gerekmez ve durum sonrası için geçerli olmalıdır.  
  
## <a name="optional-pointer-parameters"></a>İsteğe bağlı Işaretçi parametreleri  
 Bir işaretçi parametresi ek açıklaması içerdiğinde `_opt_` , parametrenin null olabileceğini gösterir. Aksi takdirde, ek açıklama dahil olmayan sürümle aynı şekilde gerçekleştirilir `_opt_` . Bu, `_opt_` işaretçi parametresi ek açıklamaların türevlerini listeler:  
  
`_In_opt_`, `_Out_opt_`, `_Inout_opt_`, `_In_opt_z_`, `_Inout_opt_z_`, `_In_reads_opt_`, `_In_reads_bytes_opt_`, `_In_reads_opt_z_`|`_Out_writes_opt_`, `_Out_writes_opt_z_`, `_Inout_updates_opt_`, `_Inout_updates_bytes_opt_`, `_Inout_updates_opt_z_`, `_Out_writes_to_opt_`, `_Out_writes_bytes_to_opt_`, `_Out_writes_all_opt_`, `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`, `_Inout_updates_bytes_to_opt_`, `_Inout_updates_all_opt_`, `_Inout_updates_bytes_all_opt_`, `_In_reads_to_ptr_opt_`, `_In_reads_to_ptr_opt_z_`, `_Out_writes_to_ptr_opt_`, `_Out_writes_to_ptr_opt_z_`|  
  
## <a name="output-pointer-parameters"></a>Çıkış Işaretçisi parametreleri  
 Çıkış işaretçisi parametreleri, parametre ve işaret konumu üzerinde null olma durumunu belirsizliğini ortadan kaldırmak için özel bir gösterim gerektirir.  
  
 **Ek açıklamalar ve açıklamalar**  
  
- `_Outptr_`  
  
   Parametre null olamaz ve durum son durumunda, işaret edilen konum null olamaz ve geçerli olmalıdır.  
  
- `_Outptr_opt_`  
  
   Parametre null olabilir, ancak durum sonrası, noktadan sonra gelen konum null olamaz ve geçerli olmalıdır.  
  
- `_Outptr_result_maybenull_`  
  
   Parametre null olamaz ve durum son durumunda, işaret edilen konum null olabilir.  
  
- `_Outptr_opt_result_maybenull_`  
  
   Parametre null olabilir ve durum son durumunda, işaret edilen konum null olabilir.  
  
  Aşağıdaki tabloda ek alt dizeler, ek açıklamanın anlamını daha fazla nitelemek için ek bir açıklama adına eklenir.  Çeşitli alt dizeler,,, ve ' dir `_z` `_COM_` `_buffer_` `_bytebuffer_` `_to_` .  
  
> [!IMPORTANT]
> Not ettiğiniz arabirim COM ise, bu ek açıklamaların COM formunu kullanın. Diğer tür arabirimlerle COM ek açıklamalarını kullanmayın.  
  
 **Ek açıklamalar ve açıklamalar**  
  
- `_Outptr_result_z_`  
  
   `_Outptr_opt_result_z_`  
  
   `_Outptr_result_maybenull_z_`  
  
   `_Ouptr_opt_result_maybenull_z_`  
  
   Döndürülen işaretçinin `_Null_terminated_` ek açıklaması vardır.  
  
- `_COM_Outptr_`  
  
   `_COM_Outptr_opt_`  
  
   `_COM_Outptr_result_maybenull_`  
  
   `_COM_Outptr_opt_result_maybenull_`  
  
   Döndürülen işaretçinin COM semantiği vardır ve bu nedenle `_On_failure_` döndürülen işaretçinin null olduğunu belirten bir koşul taşır.  
  
- `_Outptr_result_buffer_(s)`  
  
   `_Outptr_result_bytebuffer_(s)`  
  
   `_Outptr_opt_result_buffer_(s)`  
  
   `_Outptr_opt_result_bytebuffer_(s)`  
  
   Döndürülen işaretçi, öğe veya bayt boyutundaki geçerli bir arabelleğe işaret ediyor `s` .  
  
- `_Outptr_result_buffer_to_(s, c)`  
  
   `_Outptr_result_bytebuffer_to_(s, c)`  
  
   `_Outptr_opt_result_buffer_to_(s,c)`  
  
   `_Outptr_opt_result_bytebuffer_to_(s,c)`  
  
   Döndürülen işaretçi, öğe veya bayt boyutlu bir arabelleğe işaret eder `s` . Bu, ilki `c` geçerli olur.  
  
  Belirli arabirim kuralları, hata durumunda çıkış parametrelerinin null olduğunu varsayar.  Açık COM kodu hariç, aşağıdaki tablodaki formlar tercih edilir.  COM kodu için, önceki bölümde listelenen ilgili COM formlarını kullanın.  
  
  **Ek açıklamalar ve açıklamalar**  
  
- `_Result_nullonfailure_`  
  
   Diğer ek açıklamaları değiştirir. İşlev başarısız olursa sonuç null olarak ayarlanır.  
  
- `_Result_zeroonfailure_`  
  
   Diğer ek açıklamaları değiştirir. İşlev başarısız olursa sonuç sıfır olarak ayarlanır.  
  
- `_Outptr_result_nullonfailure_`  
  
   Döndürülen işaretçi, işlev başarılı olursa geçerli bir arabelleğe işaret eder veya işlev başarısız olursa null olur. Bu ek açıklama isteğe bağlı olmayan bir parametre içindir.  
  
- `_Outptr_opt_result_nullonfailure_`  
  
   Döndürülen işaretçi, işlev başarılı olursa geçerli bir arabelleğe işaret eder veya işlev başarısız olursa null olur. Bu ek açıklama isteğe bağlı bir parametre içindir.  
  
- `_Outref_result_nullonfailure_`  
  
   Döndürülen işaretçi, işlev başarılı olursa geçerli bir arabelleğe işaret eder veya işlev başarısız olursa null olur. Bu ek açıklama bir başvuru parametresi içindir.  
  
## <a name="output-reference-parameters"></a>Çıkış başvurusu parametreleri  
 Başvuru parametresinin ortak kullanımı çıkış parametrelerine yöneliktir.  Basit çıkış başvuru parametreleri için — örneğin, `int&` — `_Out_` doğru semantiği sağlar.  Ancak, çıkış değeri bir işaretçisiyse — Örneğin, `int *&` benzer işaretçi ek açıklamaları `_Outptr_ int **` doğru anlambilimi sağlamaz.  İşaretçi türleri için çıkış başvurusu parametrelerinin semantiğini öz için, bu bileşik ek açıklamaları kullanın:  
  
 **Ek açıklamalar ve açıklamalar**  
  
- `_Outref_`  
  
     Sonuç, durum sonrası için geçerli olmalıdır ve null olamaz.  
  
- `_Outref_result_maybenull_`  
  
     Sonuç, durum sonrası için geçerli olmalıdır, ancak durum sonrası null olabilir.  
  
- `_Outref_result_buffer_(s)`  
  
     Sonuç, durum sonrası için geçerli olmalıdır ve null olamaz. Geçerli boyut öğeleri arabelleğini işaret eder `s` .  
  
- `_Outref_result_bytebuffer_(s)`  
  
     Sonuç, durum sonrası için geçerli olmalıdır ve null olamaz. Geçerli boyut baytları arabelleğini işaret eder `s` .  
  
- `_Outref_result_buffer_to_(s, c)`  
  
     Sonuç, durum sonrası için geçerli olmalıdır ve null olamaz. İlk geçerli olan öğe arabelleğini işaret eder `s` `c` .  
  
- `_Outref_result_bytebuffer_to_(s, c)`  
  
     Sonuç, durum sonrası için geçerli olmalıdır ve null olamaz. `s`İlk geçerli olan bayt arabelleğini işaret eder `c` .  
  
- `_Outref_result_buffer_all_(s)`  
  
     Sonuç, durum sonrası için geçerli olmalıdır ve null olamaz. Geçerli öğelerin boyutunu geçerli arabelleğe işaret eder `s` .  
  
- `_Outref_result_bytebuffer_all_(s)`  
  
     Sonuç, durum sonrası için geçerli olmalıdır ve null olamaz. Geçerli öğe baytlarının geçerli arabelleğini işaret eder `s` .  
  
- `_Outref_result_buffer_maybenull_(s)`  
  
     Sonuç, durum sonrası için geçerli olmalıdır, ancak durum sonrası null olabilir. Geçerli boyut öğeleri arabelleğini işaret eder `s` .  
  
- `_Outref_result_bytebuffer_maybenull_(s)`  
  
     Sonuç, durum sonrası için geçerli olmalıdır, ancak durum sonrası null olabilir. Geçerli boyut baytları arabelleğini işaret eder `s` .  
  
- `_Outref_result_buffer_to_maybenull_(s, c)`  
  
     Sonuç, durum sonrası için geçerli olmalıdır, ancak durum sonrası null olabilir. İlk geçerli olan öğe arabelleğini işaret eder `s` `c` .  
  
- `_Outref_result_bytebuffer_to_maybenull_(s,c)`  
  
     Sonuç, durum sonrası için geçerli olmalıdır, ancak post durumunda null olabilir. `s`İlk geçerli olan bayt arabelleğini işaret eder `c` .  
  
- `_Outref_result_buffer_all_maybenull_(s)`  
  
     Sonuç, durum sonrası için geçerli olmalıdır, ancak post durumunda null olabilir. Geçerli öğelerin boyutunu geçerli arabelleğe işaret eder `s` .  
  
- `_Outref_result_bytebuffer_all_maybenull_(s)`  
  
     Sonuç, durum sonrası için geçerli olmalıdır, ancak post durumunda null olabilir. Geçerli öğe baytlarının geçerli arabelleğini işaret eder `s` .  
  
## <a name="return-values"></a>Dönüş Değerleri  
 Bir işlevin dönüş değeri `_Out_` parametreye benzer, ancak farklı bir de başvuru düzeyindedir ve işaretçi kavramını sonuca düşünmek zorunda kalmazsınız.  Aşağıdaki ek açıklamalar için, dönüş değeri, bir skalar, bir struct işaretçisi veya bir arabelleğin işaretçisi olan açıklamalı nesnedir. Bu ek açıklamalar, ilgili ek açıklamayla aynı semantiğe sahiptir `_Out_` .  
  
`_Ret_z_`, `_Ret_writes_(s)`, `_Ret_writes_bytes_(s)`, `_Ret_writes_z_(s)`, `_Ret_writes_to_(s,c)`, `_Ret_writes_maybenull_(s)`, `_Ret_writes_to_maybenull_(s)`, `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`, `_Ret_maybenull_z_`, `_Ret_null_`, `_Ret_notnull_`, `_Ret_writes_bytes_to_`, `_Ret_writes_bytes_maybenull_`, `_Ret_writes_bytes_to_maybenull_`
  
## <a name="other-common-annotations"></a>Diğer yaygın ek açıklamalar  
 **Ek açıklamalar ve açıklamalar**  
  
- `_In_range_(low, hi)`  
  
     `_Out_range_(low, hi)`  
  
     `_Ret_range_(low, hi)`  
  
     `_Deref_in_range_(low, hi)`  
  
     `_Deref_out_range_(low, hi)`  
  
     `_Deref_inout_range_(low, hi)`  
  
     `_Field_range_(low, hi)`  
  
     Parametresi, alanı veya sonucu, ile arasında (dahil) aralığıdır `low` `hi` .  Buna eşdeğer, `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` ilgili bir ön durum veya durum sonrası koşulları ile birlikte açıklamalı nesneye uygulanır.  
  
    > [!IMPORTANT]
    > Adlar "ın" ve "Out" içerse de, `_In_` ve anlamları `_Out_` Bu ek açıklamalar için **not** geçerlidir.  
  
- `_Pre_equal_to_(expr)`  
  
     `_Post_equal_to_(expr)`  
  
     Açıklamalı değer tam olarak `expr` .  Buna eşdeğer, `_Satisfies_(_Curr_ == expr)` ilgili bir ön durum veya durum sonrası koşulları ile birlikte açıklamalı nesneye uygulanır.  
  
- `_Struct_size_bytes_(size)`  
  
     Bir struct veya Class bildirimi için geçerlidir.  Bu türdeki geçerli bir nesnenin, tarafından verilen bayt sayısıyla, belirtilen tür ile daha büyük olabileceğini gösterir `size` .  Örneğin:  
  
     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`  
  
     Daha sonra, türündeki bir parametrenin bayt cinsinden arabellek boyutu `pM` `MyStruct *` Şu şekilde alınır:  
  
     `min(pM->nSize, sizeof(MyStruct))`  
  
## <a name="related-resources"></a>İlgili Kaynaklar  
 [Kod Analizi ekip blogu](https://blogs.msdn.com/b/codeanalysis/)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C/C++ kod hatalarını azaltmak için SAL ek açıklamalarını kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL 'ı anlama](../code-quality/understanding-sal.md)   
 [Işlev davranışına açıklama ekleme](../code-quality/annotating-function-behavior.md)   
 [Yapı ve sınıflara açıklama ekleme](../code-quality/annotating-structs-and-classes.md)   
 [Kilitleme davranışına açıklama ekleme](../code-quality/annotating-locking-behavior.md)   
 [Ek açıklamanın ne zaman ve nereye uygulanacağını belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [İç Işlevler](../code-quality/intrinsic-functions.md)   
 [En İyi Yöntemler ve Örnekler](../code-quality/best-practices-and-examples-sal.md)
