---
title: İşlev parametrelerini ve dönüş değerlerini açıklama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7886b7a49999890520aaeaf216159647cd9fdf27
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788400"
---
# <a name="annotating-function-parameters-and-return-values"></a>İşlev Parametrelerini ve Dönüş Değerlerini Açıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu makalede basit işlev parametreleri için ek açıklamaları tipik kullanımları — skalerler yanı sıra, yapılar ve sınıflar için işaretçiler — ve çoğu arabellek.  Bu makalede, ek açıklamalar için yaygın kullanım biçimlerini de gösterilir. İşlevlerle ilişkili ek açıklama için bkz: [işlev davranışını yorumlama](../code-quality/annotating-function-behavior.md)  
  
## <a name="pointer-parameters"></a>İşaretçi parametreleri  
 Bir işaretçi parametresi ek açıklama, aşağıdaki tabloda ek açıklamalar için null işaretçi ise Çözümleyicisi bir hata bildirir.  Bu, işaretçiler ve işaret edilen herhangi bir veri öğesini için geçerlidir.  
  
 **Ek açıklamalar ve açıklamaları**  
  
-   `_In_`  
  
     Skalerler, yapıları, yapılarına işaretçiler ve benzeri giriş parametrelerini açıklama ekler.  Üzerinde basit skalerler açıkça kullanılabilir.  Parametre öncesi durumda geçerli olması gerekir ve değiştirilmeyecek.  
  
-   `_Out_`  
  
     Skalerler, yapıları, yapılarına işaretçiler ve benzeri bir çıktı parametreleri açıklama ekler.  Bu bir değer döndürülemez bir nesne için geçerli değildir — Örneğin, bir değer olarak geçilemez skaler.  Parametre ön durumunda geçerli olması gerekmez ancak sonrası durumunda geçerli olması gerekir.  
  
-   `_Inout_`  
  
     İşlev tarafından değiştirilen bir parametre açıklama ekler.  Hem ön durumu hem de sonrası durumu geçerli olmalıdır, ancak önce ve sonra çağrı farklı değerlere sahip olduğu varsayılır. Değiştirilebilir bir değer için geçerli olmalıdır.  
  
-   `_In_z_`  
  
     Girdi olarak kullanılan boş sonlandırılmış dizeye bir işaretçi.  Dize öncesi durumda geçerli olmalıdır.  Türevleri `PSTR`, hangi zaten doğru ek açıklamalarına sahip, tercih edilir.  
  
-   `_Inout_z_`  
  
     Değiştirilecek bir null ile sonlandırılmış karakter dizisine bir işaretçi.  Önce ve sonra çağrı geçerli olmalıdır, ancak değiştirilmiş değer kabul edilir.  Null Sonlandırıcı taşınmış olabilir, ancak yalnızca özgün null Sonlandırıcı öğeleri erişilebilir.  
  
-   `_In_reads_(s)`  
  
     `_In_reads_bytes_(s)`  
  
     İşlev tarafından okunan bir dizisine bir işaretçi.  Dizinin boyutudur `s` öğeleri, her biri olmalıdır geçerli.  
  
     `_bytes_` Değişken öğeleri yerine bayt cinsinden boyutu sağlar. Yalnızca boyutu öğeleri olarak ifade, bunu kullanın.  Örneğin, `char` dizeleri kullandığınız `_bytes_` yalnızca benzer, işlev, değişken kullanan `wchar_t` gerekir.  
  
-   `_In_reads_z_(s)`  
  
     Null ile sonlandırılmış ve bilinen bir boyuta sahip bir dizi için bir işaretçi. Null Sonlandırıcı kadar olan öğeleri — veya `s` null Sonlandırıcı ise — öncesi durumda geçerli olması gerekir.  Bayt cinsinden boyut biliniyorsa, ölçeklendirme `s` öğesinin boyutu.  
  
-   `_In_reads_or_z_(s)`  
  
     Null ile sonlandırılmış veya bilinen bir boyuta ve her ikisi de bir dizi için bir işaretçi. Null Sonlandırıcı kadar olan öğeleri — veya `s` null Sonlandırıcı ise — öncesi durumda geçerli olması gerekir.  Bayt cinsinden boyut biliniyorsa, ölçeklendirme `s` öğesinin boyutu.  (Kullanılan `strn` ailesi.)  
  
-   `_Out_writes_(s)`  
  
     `_Out_writes_bytes_(s)`  
  
     Bir dizi işaretçi `s` işleviyle yazılacağı öğeleri (Sorum bayt).  Dizi öğelerine ön durumunda geçerli olması gerekmez ve sonrası durumda geçerli olan öğelerin sayısını belirtilmemiş.  Parametre türü ek açıklamalar varsa, bunlar sonrası durumunda uygulanır. Örneğin, aşağıdaki kodu düşünün.  
  
     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`  
  
     Bu örnekte, arayanın bir arabellek sağlar `size` için öğeleri `p1`.  `MyStringCopy` Bu öğelerin bazıları geçerli hale getirir. Daha da önemlisi, `_Null_terminated_` üzerindeki ek açıklama `PWSTR` anlamına `p1` sonrası durumda null sonlandırılmıştır.  Bu şekilde, geçerli öğe sayısını yine de iyi tanımlanmış, ancak belirli öğe sayısı gerekli değildir.  
  
     `_bytes_` Değişken öğeleri yerine bayt cinsinden boyutu sağlar. Yalnızca boyutu öğeleri olarak ifade, bunu kullanın.  Örneğin, `char` dizeleri kullandığınız `_bytes_` yalnızca benzer, işlev, değişken kullanan `wchar_t` gerekir.  
  
-   `_Out_writes_z_(s)`  
  
     Bir dizi işaretçi `s` öğeleri.  Öğeleri öncesi durumda geçerli olması gerekmez.  Sonrası durumundaki öğeleri null Sonlandırıcı aracılığıyla — mevcut olması gereken — geçerli olmalıdır.  Bayt cinsinden boyut biliniyorsa, ölçeklendirme `s` öğesinin boyutu.  
  
-   `_Inout_updates_(s)`  
  
     `_Inout_updates_bytes_(s)`  
  
     Hem okunur ve işlev yazılan bir dizi için bir işaretçi.  Boyutu olan `s` öğeleri ve geçerli durumu öncesi ve sonrası durumu.  
  
     `_bytes_` Değişken öğeleri yerine bayt cinsinden boyutu sağlar. Yalnızca boyutu öğeleri olarak ifade, bunu kullanın.  Örneğin, `char` dizeleri kullandığınız `_bytes_` yalnızca benzer, işlev, değişken kullanan `wchar_t` gerekir.  
  
-   `_Inout_updates_z_(s)`  
  
     Null ile sonlandırılmış ve bilinen bir boyuta sahip bir dizi için bir işaretçi. Öğeleri null Sonlandırıcı aracılığıyla — mevcut olması gereken — hem öncesi durumu hem de sonrası durumu geçerli olmalıdır.  Değerin sonrası durumunda öncesi durumda değerinden farklı olacak şekilde varsayılır; Bu, null Sonlandırıcı konumunu içerir. Bayt cinsinden boyut biliniyorsa, ölçeklendirme `s` öğesinin boyutu.  
  
-   `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Bir dizi işaretçi `s` öğeleri.  Öğeleri öncesi durumda geçerli olması gerekmez.  Sonrası durumundaki öğeleri kadar `c`- öğedeki geçerli olmalıdır.  Bayt cinsinden boyut biliniyorsa, ölçeklendirme `s` ve `c` kullanın ya da öğe boyutu `_bytes_` olarak tanımlanan değişken:  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     Diğer bir deyişle, arabellekteki kadar mevcut her öğe `s` ön sonrası durumunda geçerli durumda.  Örneğin:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
-   `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Hem okunur ve işlev tarafından yazılan bir dizi için bir işaretçi.  Boyutu olan `s` tümü olmalıdır geçerli öncesi durumda, öğeleri ve `c` öğeleri olmalıdır geçerli sonrası durumda.  
  
     `_bytes_` Değişken öğeleri yerine bayt cinsinden boyutu sağlar. Yalnızca boyutu öğeleri olarak ifade, bunu kullanın.  Örneğin, `char` dizeleri kullandığınız `_bytes_` yalnızca benzer, işlev, değişken kullanan `wchar_t` gerekir.  
  
-   `_Inout_updates_z_(s)`  
  
     Null ile sonlandırılmış ve bilinen bir boyuta sahip bir dizi için bir işaretçi. Öğeleri null Sonlandırıcı aracılığıyla — mevcut olması gereken — hem öncesi durumu hem de sonrası durumu geçerli olmalıdır.  Değerin sonrası durumunda öncesi durumda değerinden farklı olacak şekilde varsayılır; Bu, null Sonlandırıcı konumunu içerir. Bayt cinsinden boyut biliniyorsa, ölçeklendirme `s` öğesinin boyutu.  
  
-   `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Bir dizi işaretçi `s` öğeleri.  Öğeleri öncesi durumda geçerli olması gerekmez.  Sonrası durumundaki öğeleri kadar `c`- öğedeki geçerli olmalıdır.  Bayt cinsinden boyut biliniyorsa, ölçeklendirme `s` ve `c` kullanın ya da öğe boyutu `_bytes_` olarak tanımlanan değişken:  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     Diğer bir deyişle, arabellekteki kadar mevcut her öğe `s` ön sonrası durumunda geçerli durumda.  Örneğin:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
-   `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Hem okunur ve işlev tarafından yazılan bir dizi için bir işaretçi.  Boyutu olan `s` tümü olmalıdır geçerli öncesi durumda, öğeleri ve `c` öğeleri olmalıdır geçerli sonrası durumda.  
  
     `_bytes_` Değişken öğeleri yerine bayt cinsinden boyutu sağlar. Yalnızca boyutu öğeleri olarak ifade, bunu kullanın.  Örneğin, `char` dizeleri kullandığınız `_bytes_` yalnızca benzer, işlev, değişken kullanan `wchar_t` gerekir.  
  
-   `_Inout_updates_all_(s)`  
  
     `_Inout_updates_bytes_all_(s)`  
  
     Hem okunur ve boyutu işlevi tarafından yazılan bir dizi işaretçi `s` öğeleri. Eşdeğer olarak tanımlanır:  
  
     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`  
  
     Diğer bir deyişle, arabellekteki kadar mevcut her öğe `s` öncesi durumu öncesi ve sonrası durumu geçerli bir durumda.  
  
     `_bytes_` Değişken öğeleri yerine bayt cinsinden boyutu sağlar. Yalnızca boyutu öğeleri olarak ifade, bunu kullanın.  Örneğin, `char` dizeleri kullandığınız `_bytes_` yalnızca benzer, işlev, değişken kullanan `wchar_t` gerekir.  
  
-   `_In_reads_to_ptr_(p)`  
  
     Kendisi için bir dizisine bir işaretçi ifadesi `p` – `_Curr_` (diğer bir deyişle, `p` eksi `_Curr_`) standart uygun dili tarafından tanımlanır.  Öğeleri öncesinde `p` öncesi durumda geçerli olması gerekir.  
  
-   `_In_reads_to_ptr_z_(p)`  
  
     Kendisi için null ile sonlandırılmış bir dizisine bir işaretçi ifadesi `p` – `_Curr_` (diğer bir deyişle, `p` eksi `_Curr_`) standart uygun dili tarafından tanımlanır.  Öğeleri öncesinde `p` öncesi durumda geçerli olması gerekir.  
  
-   `_Out_writes_to_ptr_(p)`  
  
     Kendisi için bir dizisine bir işaretçi ifadesi `p` – `_Curr_` (diğer bir deyişle, `p` eksi `_Curr_`) standart uygun dili tarafından tanımlanır.  Öğeleri öncesinde `p` öncesi durumda geçerli olması gerekmez ve sonrası durumunda geçerli olması gerekir.  
  
-   `_Out_writes_to_ptr_z_(p)`  
  
     Kendisi için null ile sonlandırılmış bir dizisine bir işaretçi ifadesi `p` – `_Curr_` (diğer bir deyişle, `p` eksi `_Curr_`) standart uygun dili tarafından tanımlanır.  Öğeleri öncesinde `p` öncesi durumda geçerli olması gerekmez ve sonrası durumunda geçerli olması gerekir.  
  
## <a name="optional-pointer-parameters"></a>İsteğe bağlı işaretçi parametreleri  
 Ne zaman bir işaretçi parametresi ek açıklaması içerir `_opt_`, bu parametre null olabilir gösterir. Aksi takdirde, ek açıklama içermeyen sürümüyle aynı gerçekleştirir `_opt_`. Bir listesine buradan ulaşabilirsiniz `_opt_` çeşitleri işaretçi parametresi ek açıklamaları:  
  
||||  
|-|-|-|  
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|  
  
## <a name="output-pointer-parameters"></a>Çıkış işaretçi parametreleri  
 Çıkış işaretçi parametreleri null-ness parametresi ve işaret edilen konumun ayırt etmek için özel gösterimi gerektirir.  
  
 **Ek açıklamalar ve açıklamaları**  
  
- `_Outptr_`  
  
   Parametresi null olamaz ve sonrası durumunda, işaret edilen konumu null olamaz ve geçerli olmalıdır.  
  
- `_Outptr_opt_`  
  
   Parametre null olabilir, ancak sonrası durumunda, işaret edilen konumu null olamaz ve geçerli olmalıdır.  
  
- `_Outptr_result_maybenull_`  
  
   Parametresi null olamaz ve sonrası durumda işaret edilen konumu null olabilir.  
  
- `_Outptr_opt_result_maybenull_`  
  
   Parametre null olabilir ve sonrası durumda işaret edilen konumu null olabilir.  
  
  Aşağıdaki tabloda, ek alt dizeler daha fazla ek açıklama anlamını nitelemek için ek açıklama adı eklenir.  Çeşitli alt dizeler olan `_z`, `_COM_`, `_buffer_`, `_bytebuffer_`, ve `_to_`.  
  
> [!IMPORTANT]
>  COM yorumlama arabirimi ise bu ek açıklamalar COM biçimini kullanın. COM ek açıklamalar, başka bir tür arabirimiyle kullanmayın.  
  
 **Ek açıklamalar ve açıklamaları**  
  
- `_Outptr_result_z_`  
  
   `_Outptr_opt_result_z_`  
  
   `_Outptr_result_maybenull_z_`  
  
   `_Ouptr_opt_result_maybenull_z_`  
  
   Döndürülen işaretçiyle `_Null_terminated_` ek açıklama.  
  
- `_COM_Outptr_`  
  
   `_COM_Outptr_opt_`  
  
   `_COM_Outptr_result_maybenull_`  
  
   `_COM_Outptr_opt_result_maybenull_`  
  
   Döndürülen işaretçi COM semantiği vardır ve bu nedenle taşıyan bir `_On_failure_` sonrası koşul döndürülen işaretçi null.  
  
- `_Outptr_result_buffer_(s)`  
  
   `_Outptr_result_bytebuffer_(s)`  
  
   `_Outptr_opt_result_buffer_(s)`  
  
   `_Outptr_opt_result_bytebuffer_(s)`  
  
   Döndürülen işaretçi işaret için geçerli bir arabellek boyutunu `s` öğeleri veya bayt sayısı.  
  
- `_Outptr_result_buffer_to_(s, c)`  
  
   `_Outptr_result_bytebuffer_to_(s, c)`  
  
   `_Outptr_opt_result_buffer_to_(s,c)`  
  
   `_Outptr_opt_result_bytebuffer_to_(s,c)`  
  
   Döndürülen işaretçi işaret eden bir arabellek boyutunu `s` öğeleri veya bayt cinsinden, ilk `c` geçerlidir.  
  
  Belirli bir arabirim kuralları, çıktı parametreleri hatasında nullified olduğunu varsayar.  Açıkça COM kodu hariç, aşağıdaki tabloda formlar tercih edilir.  COM kodu için önceki bölümde listelenen karşılık gelen bir COM forms kullanın.  
  
  **Ek açıklamalar ve açıklamaları**  
  
- `_Result_nullonfailure_`  
  
   Diğer ek açıklamalar değiştirir. Sonuç, işlev başarısız olursa null olarak ayarlanır.  
  
- `_Result_zeroonfailure_`  
  
   Diğer ek açıklamalar değiştirir. Sonuç, işlev başarısız olursa sıfır olarak ayarlanır.  
  
- `_Outptr_result_nullonfailure_`  
  
   İşlev başarısız olursa, döndürülen işaretçi işlev başarılı olursa geçerli bir arabellek veya null gösterir. Bu ek açıklama için isteğe bağlı olmayan bir parametredir.  
  
- `_Outptr_opt_result_nullonfailure_`  
  
   İşlev başarısız olursa, döndürülen işaretçi işlev başarılı olursa geçerli bir arabellek veya null gösterir. Bu ek açıklama için isteğe bağlı bir parametredir.  
  
- `_Outref_result_nullonfailure_`  
  
   İşlev başarısız olursa, döndürülen işaretçi işlev başarılı olursa geçerli bir arabellek veya null gösterir. Bu ek açıklama bir başvuru parametresi olmalıdır.  
  
## <a name="output-reference-parameters"></a>Çıkış başvuru parametreleri  
 Bir ortak başvuru parametresi uygulanacağı çıktı parametreleri için kullanılır.  Basit çıkış başvuru parametreleri için — örneğin, `int&`—`_Out_` doğru semantikler sağlar.  Ancak, çıkış değeri olduğunda bir işaretçi — örneğin `int *&`— eşdeğer işaretçi ek açıklamalar ister `_Outptr_ int **` doğru semantiği sağlaması gerekmez.  İşaretçi türleri için çıktı başvuru parametreleri semantiği kısaca ifade etmek için bu bileşik ek açıklamaları kullanın:  
  
 **Ek açıklamalar ve açıklamaları**  
  
-   `_Outref_`  
  
     Sonuç sonrası durumda geçerli olmalıdır ve null olamaz.  
  
-   `_Outref_result_maybenull_`  
  
     Sonuç sonrası durumunda geçerli olması gerekir, ancak sonrası durumda null olabilir.  
  
-   `_Outref_result_buffer_(s)`  
  
     Sonuç sonrası durumda geçerli olmalıdır ve null olamaz. İşaret boyutu geçerli arabelleğinin `s` öğeleri.  
  
-   `_Outref_result_bytebuffer_(s)`  
  
     Sonuç sonrası durumda geçerli olmalıdır ve null olamaz. İşaret boyutu geçerli arabelleğinin `s` bayt.  
  
-   `_Outref_result_buffer_to_(s, c)`  
  
     Sonuç sonrası durumda geçerli olmalıdır ve null olamaz. İşaret arabelleğe `s` biri öğeleri ilk `c` geçerlidir.  
  
-   `_Outref_result_bytebuffer_to_(s, c)`  
  
     Sonuç sonrası durumda geçerli olmalıdır ve null olamaz. İşaret arabelleğe `s` bayt olan ilk `c` geçerlidir.  
  
-   `_Outref_result_buffer_all_(s)`  
  
     Sonuç sonrası durumda geçerli olmalıdır ve null olamaz. İşaret boyutu geçerli arabelleğinin `s` geçerli öğeleri.  
  
-   `_Outref_result_bytebuffer_all_(s)`  
  
     Sonuç sonrası durumda geçerli olmalıdır ve null olamaz. İşaret geçerli arabelleğe `s` geçerli öğe bayt.  
  
-   `_Outref_result_buffer_maybenull_(s)`  
  
     Sonuç sonrası durumunda geçerli olması gerekir, ancak sonrası durumda null olabilir. İşaret boyutu geçerli arabelleğinin `s` öğeleri.  
  
-   `_Outref_result_bytebuffer_maybenull_(s)`  
  
     Sonuç sonrası durumunda geçerli olması gerekir, ancak sonrası durumda null olabilir. İşaret boyutu geçerli arabelleğinin `s` bayt.  
  
-   `_Outref_result_buffer_to_maybenull_(s, c)`  
  
     Sonuç sonrası durumunda geçerli olması gerekir, ancak sonrası durumda null olabilir. İşaret arabelleğe `s` biri öğeleri ilk `c` geçerlidir.  
  
-   `_Outref_result_bytebuffer_to_maybenull_(s,c)`  
  
     Sonuç sonrası durumunda geçerli olması gerekir, ancak posta durumda null olabilir. İşaret arabelleğe `s` bayt olan ilk `c` geçerlidir.  
  
-   `_Outref_result_buffer_all_maybenull_(s)`  
  
     Sonuç sonrası durumunda geçerli olması gerekir, ancak posta durumda null olabilir. İşaret boyutu geçerli arabelleğinin `s` geçerli öğeleri.  
  
-   `_Outref_result_bytebuffer_all_maybenull_(s)`  
  
     Sonuç sonrası durumunda geçerli olması gerekir, ancak posta durumda null olabilir. İşaret geçerli arabelleğe `s` geçerli öğe bayt.  
  
## <a name="return-values"></a>Dönüş Değerleri  
 Bir işlevin dönüş değerini benzer bir `_Out_` parametresi, ancak farklı bir de-reference düzeyinde ve sonucu işaretçisi kavramını göz önünde bulundurun gerekmez.  Aşağıdaki ek açıklamalar için dönüş değeri açıklamalı nesnedir — bir skaler, bir yapı için bir işaretçi veya arabellek için işaretçi. Bu ek açıklamalar ilgili olarak aynı semantiğe sahip `_Out_` ek açıklama.  
  
|||  
|-|-|  
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|  
  
## <a name="other-common-annotations"></a>Diğer genel ek açıklamalar  
 **Ek açıklamalar ve açıklamaları**  
  
-   `_In_range_(low, hi)`  
  
     `_Out_range_(low, hi)`  
  
     `_Ret_range_(low, hi)`  
  
     `_Deref_in_range_(low, hi)`  
  
     `_Deref_out_range_(low, hi)`  
  
     `_Deref_inout_range_(low, hi)`  
  
     `_Field_range_(low, hi)`  
  
     Aralık (dahil) gelen parametre, alan veya sonuç bulunduğu `low` için `hi`.  Eşdeğer `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` uygun önceden eyalet veya il sonrası koşulları birlikte açıklamalı nesneye uygulanır.  
  
    > [!IMPORTANT]
    >  "İçinde" ve "dışarı" olmak semantiği adlarını içerse de `_In_` ve `_Out_` yapmak **değil** bu ek açıklamalar için geçerlidir.  
  
-   `_Pre_equal_to_(expr)`  
  
     `_Post_equal_to_(expr)`  
  
     Ek açıklamalı tam değerdir `expr`.  Eşdeğer `_Satisfies_(_Curr_ == expr)` uygun önceden eyalet veya il sonrası koşulları birlikte açıklamalı nesneye uygulanır.  
  
-   `_Struct_size_bytes_(size)`  
  
     Bir yapı ya da sınıf bildirimi geçerlidir.  Bu türün geçerli bir nesne tarafından verilen bayt sayısı ile bildirilen türünden daha büyük olabileceğini gösterir `size`.  Örneğin:  
  
     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`  
  
     Arabellek boyutu parametresinin bayt `pM` türü `MyStruct *` olmasını alınır:  
  
     `min(pM->nSize, sizeof(MyStruct))`  
  
## <a name="related-resources"></a>İlgili Kaynaklar  
 [Kod Analizi ekip blogu](http://go.microsoft.com/fwlink/?LinkId=251197)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C/C++ kod hatalarını azaltmak için SAL ek açıklamalarını kullanma](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL'yi anlama](../code-quality/understanding-sal.md)   
 [İşlev davranışını yorumlama](../code-quality/annotating-function-behavior.md)   
 [Yapıları ve sınıfları yorumlama](../code-quality/annotating-structs-and-classes.md)   
 [Kilitlenme davranışını yorumlama](../code-quality/annotating-locking-behavior.md)   
 [Açıklamanın ne zaman ve nereye uygulanacağını belirtme](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [İç işlevleri](../code-quality/intrinsic-functions.md)   
 [En İyi Yöntemler ve Örnekler](../code-quality/best-practices-and-examples-sal.md)



