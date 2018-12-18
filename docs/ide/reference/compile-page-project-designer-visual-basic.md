---
title: Derleme Sayfası, Proje Tasarımcısı (Visual Basic)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesCompile
helpviewer_keywords:
- compilation, Visual Basic projects
- compilation, options [Visual Basic]
- compilers, Visual Basic options
- compilation, instructions [Visual Basic]
- compiler options, Visual Basic
- Project Designer, Compile page
- Compile page in Project Designer
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d1b5c55c3bc1732d0b394473f25c0b103c917f4
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808380"
---
# <a name="compile-page-project-designer-visual-basic"></a>Derleme Sayfası, Proje Tasarımcısı (Visual Basic)

Kullanım **derleme** derleme yönergeleri belirtmek için Proje Tasarımcısı'nın sayfa. Bu sayfada Gelişmiş derleyici seçenekleri ve derleme öncesi veya derleme sonrası olay de belirtebilirsiniz.

Erişim için **derleme** sayfasında, bir proje düğümü seçin (değil **çözüm** düğümü) içinde **Çözüm Gezgini**. Ardından **proje**, **özellikleri** menü çubuğundaki. Proje Tasarımcısı göründüğünde tıklayın **derleme** sekmesi.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Yapılandırma ve Platform

Aşağıdaki ayarlar, görüntülenecek veya değiştirilecek platform ve yapılandırmayı seçmenize olanak sağlar.

> [!NOTE]
> Basitleştirilmiş yapı yapılandırmaları ile proje sistemi bir hata ayıklama sürüm yayını mı belirler. Bu nedenle, **yapılandırma** ve **Platform** listeleri görüntülenmez.

 **Yapılandırma**

 Hangi yapılandırma ayarlarının görüntüleneceğini veya değiştirileceğini belirtir. Ayarlar **hata ayıklama** (varsayılan), **yayın**, veya **yapılandırmalarında**. Daha fazla bilgi için [derleme yapılandırmalarını anlama](../../ide/understanding-build-configurations.md) ve [nasıl yapılır: yapılandırmaları oluşturma ve düzenleme](../../ide/how-to-create-and-edit-configurations.md).

 **Platform**

 Platform ayarlarının görüntüleneceğini veya değiştirileceğini belirtir. Belirtebileceğiniz **herhangi bir CPU** (varsayılan), **x64**, veya **x86**.

## <a name="compiler-configuration-options"></a>Derleyici yapılandırma seçenekleri

Aşağıdaki ayarlar, derleyici yapılandırma seçenekleri ayarlamanızı sağlar.

 **Yapı çıkış yolu**

 Bu projenin yapılandırması için çıkış dosyalarının konumunu belirtir. Yapı çıkış yolunu bu kutuya yazın ya da tıklayın **Gözat** düğmesini bir yolu seçin. Yolun göreli olduğuna dikkat edin; mutlak bir yol girerseniz, göreli olarak kaydedilecektir. Varsayılan yol bin\Debug\ veya bin\Release olan\\.

 Basitleştirilmiş yapı yapılandırmaları ile proje sistemi bir hata ayıklama sürüm yayını mı belirler. **Derleme** komutunu **hata ayıklama** menüsündeki (F5) bağımsız olarak, hata ayıklama konumuna derleme koyacaktır **çıkış yolu** belirtirsiniz. Ancak, **derleme** komutunu **derleme** menü, belirttiğiniz konuma koyar.
  
 **Seçeneği açık**  
 Örtük bir değişken bildirimi izin verilip verilmeyeceğini belirtir. Seçin **üzerinde** değişkenleri açık bildirimini gerektiren. Bunlar kullanılmadan önce değişkenleri bildirilmedikçe derleyici hatalarını raporlamak için bu neden olur. Seçin **kapalı** örtük bir değişken bildirimi izin vermek için.  
  
 Bu ayar karşılık gelen [/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) derleyici seçeneği.  
  
 Bir kaynak kodu dosyası içeriyorsa bir [Option Explicit deyimi](/dotnet/visual-basic/language-reference/statements/option-explicit-statement), `On` veya `Off` deyiminde değerini geçersiz kılar **Option Explicit** ayarını **derleme Sayfa**.  
  
 Yeni bir proje oluşturduğunuzda **Option Explicit** ayarını **derleme sayfa** değerine ayarlanmış **Option Explicit** ayarı **seçenekleri**  iletişim kutusu. Görüntülemek veya bu iletişim kutusunda bir ayarı değiştirmek için **Araçları** menüsünü tıklatın **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda **projeler ve çözümler**ve ardından **VB varsayılanları**. İlk varsayılan ayarı **Option Explicit** içinde **VB varsayılanları** olduğu **üzerinde**.  
  
 Ayarı **Option Explicit** için `Off` genellikle iyi bir uygulama değildir. Bir değişken adı program çalıştırıldığında bu beklenmeyen sonuçlara neden olduğu bir veya daha fazla konumda yazsanız.  
  
 **Katı tanımlama seçeneği**  
Kesin türü anlamları zorlanıp zorlanmayacağını belirtir. Zaman **Option Strict** olduğu **üzerinde**, bir derleme zamanı hatası aşağıdaki durumlar neden:  
  
-   Örtük daraltma dönüşümleri  
  
-   Geç bağlama  
  
-   Örtük sonuçlanan yazarak bir `Object` türü  
  
Bir daraltma dönüştürmesi olan bir örtük veri türü dönüştürme olduğunda daraltma örtük dönüştürme hataları oluşur. Daha fazla bilgi için [Option Strict deyimi](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [örtük ve açık dönüştürmeler](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions), ve [Widening ve daraltma dönüşümleri](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions).  
  
Bir özellik veya yöntem türü olarak bildirilmiş bir değişken atandığında, nesnenin geç bağlama `Object`. Daha fazla bilgi için [Option Strict deyimi](/dotnet/visual-basic/language-reference/statements/option-strict-statement) ve [erken ve geç bağlama](/dotnet/visual-basic/programming-guide/language-features/early-late-binding).
  
Örtük nesne türü hatalar ortaya uygun bir tür olamaz bildirilmiş bir değişken için bu nedenle bir tür çıkarımı yapılan `Object` algılanır. Kullandığınızda öncelikle böyle bir `Dim` kullanmadan bir değişken bildirmek için deyimi bir `As` yan tümcesi ve `Option Infer` kapalıdır. Daha fazla bilgi için [Option Strict deyimi](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Option Infer deyimi](/dotnet/visual-basic/language-reference/statements/option-infer-statement)ve [Visual Basic dil belirtimi](/dotnet/visual-basic/reference/language-specification).  
  
**Option Strict** ayarı karşılık gelen [/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) derleyici seçeneği.  
  
Bir kaynak kodu dosyası içeriyorsa bir [Option Strict deyimi](/dotnet/visual-basic/language-reference/statements/option-strict-statement), `On` veya `Off` deyiminde değerini geçersiz kılar **Option Strict** ayarını **derle sayfası** .  
  
Bir proje oluşturduğunuzda **Option Strict** ayarını **derleme sayfası** değerine ayarlanmış **Option Strict** ayarı **seçenekleri** iletişim kutusu. Görüntülemek veya bu iletişim kutusunda bir ayarı değiştirmek için **Araçları** menüsünü tıklatın **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda **projeler ve çözümler**ve ardından **VB varsayılanları**. İlk varsayılan ayarı **Option Strict** içinde **VB varsayılanları** olduğu **kapalı**.  
  
**Bireysel uyarıları katı seçeneği.** **Uyarı yapılandırmaları** bölümünü **derleme sayfa** karşılık gelen bir derleme zamanı hatasına neden olan üç koşulları ayarlarına sahip olduğunda `Option Strict` açıktır. Bu ayarlar şunlardır:  
  
-   **Örtük dönüştürme**  
  
-   **Geç bağlama; Çağrı çalışma zamanında başarısız olabilir**  
  
-   **Örtük tür; Nesne varsayıldı**  
  
Ayarladığınızda **Option Strict** için **üzerinde**, bu uyarı yapılandırma ayarlarını üç kümesine **hata**. Ayarladığınızda **Option Strict** için **kapalı**, tüm üç ayarları kümesine **hiçbiri**.  
  
Her uyarı yapılandırma ayarı ayrı ayrı değiştirebileceğiniz **hiçbiri**, **uyarı**, veya **hata**. Üç uyarı yapılandırma ayarlarını ayarlandıysa **hata**, `On` görünür `Option strict` kutusu. Üç ayarlandıysa **hiçbiri**, `Off` bu kutuda görünür. Bu ayarlar, diğer herhangi bir birleşimini için **(özel)** görünür.  
  
**Karşılaştırma seçeneği**  
Kullanılacak dize karşılaştırma türünü belirtir. Seçin **ikili** derleyicisinin ikili, büyük küçük harfe duyarlı dize karşılaştırmaları kullanın. Seçin **metin** metin yerel ayara özgü, büyük küçük harf duyarsız dize karşılaştırmalarını kullanmak için.  
  
Bu ayar karşılık gelen [/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) derleyici seçeneği.  
  
Bir kaynak kodu dosyası içeriyorsa bir [seçenek karşılaştırma ifadesini](/dotnet/visual-basic/language-reference/statements/option-compare-statement), `Binary` veya `Text` deyiminde değerini geçersiz kılar **Option Compare** ayarını **derleme Sayfa**.  
  
Bir proje oluşturduğunuzda **Option Compare** ayarını **derleme sayfası** değerine ayarlanmış **Option Compare** ayarı **seçenekleri** iletişim kutusu. Görüntülemek veya bu iletişim kutusunda bir ayarı değiştirmek için **Araçları** menüsünü tıklatın **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda **projeler ve çözümler**ve ardından **VB varsayılanları**. İlk varsayılan ayarı **Option Compare** içinde **VB varsayılanları** olduğu **ikili**.  
  
**Option Infer**  
Yerel tür çıkarımı değişken bildirimlerinde izin verilip verilmeyeceğini belirtir. Seçin **üzerinde** yerel tür çıkarımı kullanımına izin vermek için. Seçin **kapalı** blok yerel tür çıkarımı için.  
  
Bu ayar karşılık gelen [/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer) derleyici seçeneği.  
  
Bir kaynak kodu dosyası içeriyorsa bir [Option Infer deyimi](/dotnet/visual-basic/language-reference/statements/option-infer-statement), `On` veya `Off` deyiminde değerini geçersiz kılar **Option Infer** ayarını **derle sayfası** .  
  
Bir proje oluşturduğunuzda **Option Infer** ayarını **derleme sayfa** değerine ayarlanmış **Option Infer** ayarı **seçenekleri**iletişim kutusu. Görüntülemek veya bu iletişim kutusunda bir ayarı değiştirmek için **Araçları** menüsünü tıklatın **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda **projeler ve çözümler**ve ardından **VB varsayılanları**. İlk varsayılan ayarı **Option Infer** içinde **VB varsayılanları** olduğu **üzerinde**.  
  
**Hedef CPU**  
Çıktı dosyası tarafından hedeflenecek işlemciyi belirtir. Belirtin **x86** herhangi bir 32 bit Intel uyumlu işlemci için **x64** herhangi bir 64-bit Intel uyumlu işlemci için **ARM** tüm ARM işlemci için veya **herhangi bir CPU**  tüm işlemcilerin kabul edilebilir olduğunu belirtmek için. **Herhangi bir CPU** uygulamanın en büyük sayısını donanım türleri üzerinde çalışmasına izin verdiğinden yeni projeler için varsayılan değerdir.  
  
Daha fazla bilgi için [/Platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).  
  
**32 bit tercih edin**  
Varsa **Prefer32-bit** onay kutusu seçildiğinde, uygulama bir 32 bit uygulama olarak, hem 32-bit hem de 64 bit Windows sürümlerinde çalışır. Aksi takdirde, uygulamanın Windows ve Windows 64 bit sürümlerinde 64 bit uygulama olarak 32-bit sürümleri 32-bit uygulama olarak çalışır.  
  
64 bitlik bir uygulama işaretçi boyutu iki katına çıkar ve özellikle 32 bit kitaplıkları uyumluluk sorunlarına neden olabilir olarak çalışıyor. Yalnızca önemli ölçüde daha hızlı çalışır veya 4 GB'den daha fazla bellek gerekli bir uygulamayı 64-bit olarak çalıştırmak mantıklıdır.  
  
Bu onay kutusu yalnızca aşağıdaki koşulların tümü doğruysa, kullanılabilir:  
  
-   Üzerinde **derle sayfası**, **hedef CPU** listesinin **herhangi bir CPU**.  
  
-   Üzerinde **uygulama sayfası**, **uygulama türü** listesi, projenin bir uygulama olduğunu belirtir.  
  
-   Üzerinde **uygulama sayfası**, **hedef Framework'ü** listesi .NET Framework 4.5 belirtir.  
  
**Uyarı yapılandırma**  
Bu tabloda derleme koşullar ve karşılık gelen bildirim düzeyini **hiçbiri**, **uyarı**, veya **hata** her.  
  
Varsayılan olarak, tüm Derleyici uyarılarını, derleme sırasında görev listesine eklenir. Seçin **tüm uyarıları devre dışı bırak** derleyicisinin sorunu uyarıları veya hataları. Seçin **tüm uyarıları hata olarak değerlendir** Derleyicinin uyarıları düzeltilmesi gereken hata olarak değerlendir istiyorsanız.  
  
**Tüm uyarıları devre dışı bırak**  
Sorunu bildirimleri belirtildiği gibi derleyici izin verilip verilmeyeceğini belirten **koşulu ve bildirim** bu belgenin önceki bölümlerinde açıklanan tablo. Varsayılan olarak, bu onay kutusu işaretli değildir. Derleyicisinin bir uyarı veya hata sorun değil, bu onay kutusunu seçin.  
  
Bu ayar karşılık gelen [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) derleyici seçeneği.  
  
**Tüm uyarıları hata olarak değerlendir**  
Uyarıları nasıl belirtir. Tüm uyarı bildirimleri için ayarlanmış kalmaları için varsayılan olarak, bu onay kutusu, temizlenir **uyarı**. Tüm Uyarı bildirimlerinin postalanacağı değiştirmek için bu onay kutusunu işaretleyin **hata**.  
  
Bu seçenek yalnızca **tüm uyarıları devre dışı bırak** temizlenir.  
  
**XML belge dosyası oluşturma**  
Belgelendirme bilgilerini oluşturulup oluşturulmayacağını belirtir. Varsayılan olarak, belgelendirme bilgilerini oluşturup bir XML dosyasına eklenecek derleyici söyleyen bu onay kutusu seçilidir. Belgeleri oluşturmamayı derleyicisinin bu onay kutusunu temizleyin.  
  
Bu ayar karşılık gelen [/doc](/dotnet/visual-basic/reference/command-line-compiler/doc) derleyici seçeneği.  
  
**COM birlikte çalışması için kaydol**  
Yönetilen uygulama ile etkileşim kurmak bir COM nesnesi sağlayan bir COM nesnesi (COM çağrılabilir sarmalayıcısı) açığa çıkarır olup olmadığını belirtir.  
  
Varsayılan olarak, uygulama COM birlikte çalışma izin vermeyeceğini belirten bu onay kutusunu temizlenir. COM birlikte çalışma izin vermek için bu onay kutusunu seçin.  
  
Bu seçenek Windows uygulama veya konsol uygulaması projelerinde kullanılamaz.  
  
**Derleme olayları**  
Erişim için bu düğmeye tıklayın **Build Events** iletişim kutusu. Derleme öncesi ve sonrası yapılandırma yönergeleri için projeyi belirtmek için bu iletişim kutusunu kullanın. Bu iletişim kutusu, yalnızca Visual Basic projeleri için geçerlidir. Daha fazla bilgi için [derleme olayları iletişim kutusu (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md).  
  
**Gelişmiş derleme seçenekleri**  
Erişim için bu düğmeye tıklayın **AdvancedCompiler ayarları** iletişim kutusu. Kullanım **AdvancedCompiler ayarları** Gelişmiş yapı yapılandırma özellikleri iletişim kutusu, bir projeyi belirtmek için. Bu iletişim kutusu, yalnızca Visual Basic projeleri için geçerlidir. Daha fazla bilgi için [Gelişmiş derleyici Ayarları iletişim kutusu (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).  


## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Derleme Olayları Belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Visual Basic komut satırı derleyicisi](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Nasıl Yapılır: Yapılandırmaları Oluşturma ve Düzenleme](../../ide/how-to-create-and-edit-configurations.md)