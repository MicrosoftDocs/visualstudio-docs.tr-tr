---
title: Visual Basic'teki Uyarıları Yapılandırma
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Basic], warnings
- run-time errors, warnings
- warnings, configuring
ms.assetid: 99cf4781-bd4d-47b4-91b9-217933509f82
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8cb2cec8258813fa9c93c466afb607ce88acc7e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865972"
---
# <a name="configuring-warnings-in-visual-basic"></a>Visual Basic'teki uyarıları yapılandırma

[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Derleyici çalışma zamanı hatalarına neden olabilir kod hakkında uyarılar kümesi içerir. Temizleyici, daha hızlı, daha az hata ile daha iyi kod yazmak için bu bilgileri kullanabilirsiniz. Derleyici gibi veya kullanıcı, dönüş değeri olmadan bir işlevden dönüş atanmamış nesne değişkeninin bir üyeyi çağıran girişiminde bulunduğunda uyarı üreten yürütme bir `Try` hatalarla mantığında özel durumları yakalama bloğu.

 Bazen derleyicinin kullanıcı elinizdeki yerine olası hatalar öngörerek üzerinde odaklanabilmeniz için kullanıcı adına ek mantık sağlar. Önceki sürümlerinde [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], **Option Strict** ilave bir mantık sınırlamak için kullanılan, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] derleyici sağlar. Uyarıları yapılandırma bireysel uyarı düzeyinde daha ayrıntılı bir şekilde bu mantığı sınırlamanıza olanak sağlar.

 Bazı uyarıları değil ilgili hatalara diğer uyarıları kapatma sırasında uygulamanıza Kapat ve projenizi özelleştirmek isteyebilirsiniz. Bu sayfa, bireysel uyarıları açıp kapatmak açıklanmaktadır.

## <a name="turning-warnings-off-and-on"></a>Uyarıları ve kapatma
 Uyarıları yapılandırmak için iki farklı yolu vardır: bunları yapılandırabilirsiniz kullanarak **Proje Tasarımcısı**, ya da **/warnaserror** ve **/nowarn** derleyici seçenekleri .

 **Derleme** sekmesinde **Proje Tasarımcısı** sayfasını açıp uyarıları kapatmak olanak tanır. Seçin **tüm uyarıları devre dışı** tüm uyarıları devre dışı bırakmak için onay kutusunu işaretleyin; seçin **tüm uyarıları hata olarak değerlendir** tüm uyarıları hata olarak değerlendirilecek. Tek tek bazı uyarılar oluştu, hata veya uyarı açılıp kapatılabilir görüntülenen tabloda istediğiniz.

 Zaman **Option Strict** ayarlanır **kapalı**, **Option Strict** uyarıları kullanılamaz Kabul birbirinden ilgili. Zaman **Option Strict** ayarlanır **üzerinde**ilişkili uyarıları hata olarak kabul edilir, Hayır ne durumlarını önemli değildir. Zaman **Option Strict** ayarlanır **özel** belirterek `/optionstrict:custom` komut satırı derleyicisinde **Option Strict** uyarılar açılıp açıp bağımsız olarak.

 **/Warnaserror** derleyici komut satırı seçeneği de kullanılabilir uyarıları hata olarak kabul edileceğini belirtmek için. Hangi uyarıların hata veya uyarı kullanarak değerlendirilmesi gerektiğini belirtmek için bu seçeneği bir virgülle ayrılmış liste ekleyebileceğiniz + veya -. Aşağıdaki tabloda, olası seçeneklerin ayrıntıları.

|Komut satırı seçeneği|Belirler|
| - |---------------|
|`/warnaserror+`|Tüm uyarıları hata olarak değerlendir|
|`/warnsaserror`-|Uyarıları hata olarak olarak kabul. Bu varsayılandır.|
|`/warnaserror+:<warning list``>`|Belirli uyarıları hata, bir virgülle ayrılmış liste r hata kodu numarasına göre listelenmiş olarak kabul eder.|
|`/warnaserror-:<warning list>`|Belirli uyarıları hata, bir virgülle ayrılmış liste hata kodu numarasına göre listelenmiş olarak değerlendir değil.|
|`/nowarn`|Uyarıları bildirmez.|
|`/nowarn:<warning list>`|Bir virgülle ayrılmış liste hata kodu numarasına göre listelenen belirli uyarıları bildirmez.|

 Belirli uyarıları açmak veya kapatmak için komut satırı seçenekleriyle birlikte kullanılabilecek hata olarak değerlendirilip uyarıları kimlik numaraları hatası uyarısı listelenmiştir. Uyarı listesi geçersiz bir sayı içeriyorsa, bir hata bildirilir.

## <a name="examples"></a>Örnekler
 Komut satırı bağımsız değişkenleri örnekleri, bu tablo, her bağımsız değişken ne yaptığını açıklar.

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`vbc /warnaserror`|Tüm uyarıların hata sayılması gerektiğini belirtir.|
|`vbc /warnaserror:42024`|Bu uyarı belirtir 42024 hata olarak kabul.|
|`vbc /warnaserror:42024,42025`|42024 ve 42025 uyarıların hata sayılması gerektiğini belirtir.|
|`vbc /nowarn`|Uyarı bildirilmeden olduğunu belirtir.|
|`vbc /nowarn:42024`|Bu uyarı belirtir 42024 bildirilmedi.|
|`vbc /nowarn:42024,42025`|Uyarılar 42024 ve 42025 bildirilmedi belirtir.|

## <a name="types-of-warnings"></a>Uyarı türleri
 Uyarıları hata olarak değerlendirilecek isteyebileceğiniz listesi aşağıda verilmiştir.

### <a name="implicit-conversion-warning"></a>Örtük dönüştürme Uyarısı
 İçin oluşturulan örnekleri örtük dönüştürme. Bunlar iç bir sayısal tür örtük dönüştürmelerine bir dizeye kullanırken içermez `&` işleci. Yeni projeler kapatmak için varsayılan.

 ID: 42016

### <a name="late-bound-method-invocation-and-overload-resolution-warning"></a>Geç yöntemi çağırma bağlı ve aşırı yükleme çözünürlüğü Uyarısı
 İçin oluşturulan örnekleri, geç bağlama. Yeni projeler kapatmak için varsayılan.

 ID: 42017

### <a name="operands-of-type-object-warnings"></a>İşlenen türü 'Nesnesi' uyarıları
 Oluşturulan türündeki işlenenler `Object` oluşan bir hata ile oluşturmak **Option Strict On**. Yeni projeler üzerinde için varsayılan.

 ID: 42018 ve 42019

### <a name="declarations-require-as-clause-warnings"></a>'As' yan tümcesi uyarı bildirimleri gerektirir
 Bir değişken, işlev veya özellik bildirimi eksik olduğunda oluşturulan bir `As` yan tümcesi, bir hata ile oluşturulan **Option Strict On**. Atanmış bir türleri olmadığı değişkenleri olduğu varsayılır türü `Object`. Yeni projeler üzerinde için varsayılan.

 ID: 42020 (değişken bildirimi), 42021 (işlev bildirimi) ve 42022 (özellik bildiriminde).

### <a name="possible-null-reference-exception-warnings"></a>Olası bir null başvurusu özel durumu uyarıları
 Bir değer atanmadan önce değişken kullanıldığında oluşturulur. Yeni projeler üzerinde için varsayılan.

 ID: 42104, 42030

### <a name="unused-local-variable-warning"></a>Kullanılmayan yerel değişken Uyarısı
 Yerel bir değişken bildirildi ancak hiç başvurulan oluşturulur. Varsayılan açıktır.

 ID: 42024

### <a name="access-of-shared-member-through-instance-variable-warning"></a>Paylaşılan üyeye değişken uyarı örnek üzerinden erişim
 Örneği paylaşılan bir üyeye erişme yan etkileri olabilir veya bir örnek değişkeni paylaşılan bir üyeye erişme sağ tarafında bir ifade değil veya bir parametre olarak geçirilen zaman oluşturulur. Yeni projeler üzerinde için varsayılan.

 ID: 42025

### <a name="recursive-operator-or-property-access-warnings"></a>Özyinelemeli işleci veya özellik erişimi uyarıları
 Bir yordamın gövdesi aynı işleci veya içinde tanımlanan bir özellik kullanır oluşturulur. Yeni projeler üzerinde için varsayılan.

 ID: 42004 (işleç), 42026 (özellik)

### <a name="function-or-operator-without-return-value-warning"></a>İşlev veya işleci olmadan dönüş değeri Uyarısı
 İşlev veya işleci belirtilen dönüş değerine sahip olmadığı durumlarda oluşturulur. Bu atlama içerir bir `Set` örtük yerel değişkene işlevi olarak aynı ada sahip. Yeni projeler üzerinde için varsayılan.

 ID: 42105 (işlev), 42016 (işleç)

### <a name="overloads-modifier-used-in-a-module-warning"></a>Bir modül uyarıda kullanılan aşırı değiştiricisi
 Oluşturulan `Overloads` kullanılan bir `Module`. Yeni projeler üzerinde için varsayılan.

 ID: 42028

### <a name="duplicate-or-overlapping-catch-blocks-warnings"></a>Yinelenen veya örtüşen blokları uyarıları yakalayın
 Oluşturulan bir `Catch` bloğu diğer ilişkisi nedeniyle hiçbir zaman ulaşıldığında `Catch` tanımlanmış engeller. Yeni projeler üzerinde için varsayılan.

 ID: 42029, 42031

## <a name="see-also"></a>Ayrıca bkz.

- [Hata türleri](/dotnet/visual-basic/programming-guide/language-features/error-types)
- [Deneyin... Catch... Finally deyimi](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)
- [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)
- [/ warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)
- [Derleme sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Varsayılan olarak kapalı olan derleyici uyarıları](/cpp/preprocessor/compiler-warnings-that-are-off-by-default)