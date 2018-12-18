---
title: Derleme sayfası, Proje Tasarımcısı (Visual Basic) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 65
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4b369b1aa8d9e6857b29a5c37d13169b2e21ea74
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924563"
---
# <a name="compile-page-project-designer-visual-basic"></a>Derleme Sayfası, Proje Tasarımcısı (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Kullanım **derleme** derleme yönergeleri belirtmek için Proje Tasarımcısı'nın sayfa. Bu sayfada Gelişmiş derleyici seçenekleri ve derleme öncesi veya derleme sonrası olay de belirtebilirsiniz.  
  
 Erişim için **derleme** sayfasında, bir proje düğümü seçin (değil **çözüm** düğümü) içinde **Çözüm Gezgini**. Ardından **proje**, **özellikleri** menü çubuğundaki. Proje Tasarımcısı göründüğünde tıklayın **derleme** sekmesi.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="configuration-and-platform"></a>Yapılandırma ve Platform  
 Aşağıdaki ayarlar, görüntülenecek veya değiştirilecek platform ve yapılandırmayı seçmenize olanak sağlar.  
  
> [!NOTE]
>  Basitleştirilmiş yapı yapılandırmaları ile proje sistemi bir hata ayıklama sürüm yayını mı belirler. Bu nedenle, **yapılandırma** ve **Platform** listeleri görüntülenmez. Daha fazla bilgi için [hata ayıklama ve dağıtım proje yapılandırmalarını](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 **Yapılandırma**  
 Hangi yapılandırma ayarlarının görüntüleneceğini veya değiştirileceğini belirtir. Ayarlar **hata ayıklama** (varsayılan), **yayın**, veya **yapılandırmalarında**. Daha fazla bilgi için [hata ayıklama ve dağıtım proje yapılandırmalarını](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e) ve [nasıl yapılır: yapılandırmaları oluşturma ve düzenleme](../../ide/how-to-create-and-edit-configurations.md).  
  
 **Platform**  
 Platform ayarlarının görüntüleneceğini veya değiştirileceğini belirtir. Belirtebileceğiniz **herhangi bir CPU** (varsayılan), **x64**, veya **x86**. Daha fazla bilgi için [hata ayıklama ve dağıtım proje yapılandırmalarını](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
## <a name="compiler-configuration-options"></a>Derleyici yapılandırma seçenekleri  
 Aşağıdaki ayarlar, derleyici yapılandırma seçenekleri ayarlamanızı sağlar.  
  
 **Yapı çıkış yolu**  
 Bu projenin yapılandırması için çıkış dosyalarının konumunu belirtir. Yapı çıkış yolunu bu kutuya yazın ya da tıklayın **Gözat** düğmesini bir yolu seçin. Yolun göreli olduğuna dikkat edin; mutlak bir yol girerseniz, göreli olarak kaydedilecektir. Varsayılan yol bin\Debug\ veya bin\Release olan\\. Daha fazla bilgi için [hata ayıklama ve dağıtım proje yapılandırmalarını](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 Basitleştirilmiş yapı yapılandırmaları ile proje sistemi bir hata ayıklama sürüm yayını mı belirler. **Derleme** komutunu **hata ayıklama** menüsündeki (F5) bağımsız olarak, hata ayıklama konumuna derleme koyacaktır **çıkış yolu** belirtirsiniz. Ancak, **derleme** komutunu **derleme** menü, belirttiğiniz konuma koyar. Daha fazla bilgi için [hata ayıklama ve dağıtım proje yapılandırmalarını](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 **Seçeneği açık**  
 Örtük bir değişken bildirimi izin verilip verilmeyeceğini belirtir. Seçin **üzerinde** değişkenleri açık bildirimini gerektiren. Bunlar kullanılmadan önce değişkenleri bildirilmedikçe derleyici hatalarını raporlamak için bu neden olur. Seçin **kapalı** örtük bir değişken bildirimi izin vermek için.  
  
 Bu ayar karşılık gelen [/optionexplicit](http://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7) derleyici seçeneği.  
  
 Bir kaynak kodu dosyası içeriyorsa bir [Option Explicit deyimi](http://msdn.microsoft.com/library/e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc), `On` veya `Off` deyiminde değerini geçersiz kılar **Option Explicit** ayarını **derleme Sayfa**.  
  
 Yeni bir proje oluşturduğunuzda **Option Explicit** ayarını **derleme sayfa** değerine ayarlanmış **Option Explicit** ayarı **seçenekleri**  iletişim kutusu. Görüntülemek veya bu iletişim kutusunda bir ayarı değiştirmek için **Araçları** menüsünü tıklatın **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda **projeler ve çözümler**ve ardından **VB varsayılanları**. İlk varsayılan ayarı **Option Explicit** içinde **VB varsayılanları** olduğu **üzerinde**.  
  
 Ayarı **Option Explicit** için `Off` genellikle iyi bir uygulama değildir. Bir değişken adı program çalıştırıldığında bu beklenmeyen sonuçlara neden olduğu bir veya daha fazla konumda yazsanız.  
  
 **Katı tanımlama seçeneği**  
 Kesin türü anlamları zorlanıp zorlanmayacağını belirtir. Zaman **Option Strict** olduğu **üzerinde**, bir derleme zamanı hatası aşağıdaki durumlar neden:  
  
- Örtük daraltma dönüşümleri  
  
- Geç bağlama  
  
- Örtük sonuçlanan yazarak bir `Object` türü  
  
  Bir daraltma dönüştürmesi olan bir örtük veri türü dönüştürme olduğunda daraltma örtük dönüştürme hataları oluşur. Daha fazla bilgi için [Option Strict deyimi](http://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), [örtük ve açık dönüştürmeler](http://msdn.microsoft.com/library/77de1659-af8a-492c-967e-e7ef60ccce66), ve [Widening ve daraltma dönüşümleri](http://msdn.microsoft.com/library/058c3152-6c28-4268-af44-2209e774f0bd).  
  
  Bir özellik veya yöntem türü olarak bildirilmiş bir değişken atandığında, nesnenin geç bağlama `Object`. Daha fazla bilgi için [Option Strict deyimi](http://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5) ve [erken ve geç bağlama](http://msdn.microsoft.com/library/d6ff7f1e-b94f-4205-ab8d-5cfa91758724).  
  
  Örtük nesne türü hatalar ortaya uygun bir tür olamaz bildirilmiş bir değişken için bu nedenle bir tür çıkarımı yapılan `Object` algılanır. Kullandığınızda öncelikle böyle bir `Dim` kullanmadan bir değişken bildirmek için deyimi bir `As` yan tümcesi ve `Option Infer` kapalıdır. Daha fazla bilgi için [Option Strict deyimi](http://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), [Option Infer deyimi](http://msdn.microsoft.com/library/4ad3e6e9-8f5b-4209-a248-de22ef6e4652)ve [Visual Basic dil belirtimi](http://msdn.microsoft.com/library/42c30017-19d0-442e-87a2-850b66ddc3df).  
  
  **Option Strict** ayarı karşılık gelen [/optionstrict](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) derleyici seçeneği.  
  
  Bir kaynak kodu dosyası içeriyorsa bir [Option Strict deyimi](http://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), `On` veya `Off` deyiminde değerini geçersiz kılar **Option Strict** ayarını **derle sayfası** .  
  
  Bir proje oluşturduğunuzda **Option Strict** ayarını **derleme sayfası** değerine ayarlanmış **Option Strict** ayarı **seçenekleri** iletişim kutusu. Görüntülemek veya bu iletişim kutusunda bir ayarı değiştirmek için **Araçları** menüsünü tıklatın **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda **projeler ve çözümler**ve ardından **VB varsayılanları**. İlk varsayılan ayarı **Option Strict** içinde **VB varsayılanları** olduğu **kapalı**.  
  
  **Bireysel uyarıları katı seçeneği.** **Uyarı yapılandırmaları** bölümünü **derleme sayfa** karşılık gelen bir derleme zamanı hatasına neden olan üç koşulları ayarlarına sahip olduğunda `Option Strict` açıktır. Bu ayarlar şunlardır:  
  
- **Örtük dönüştürme**  
  
- **Geç bağlama; Çağrı çalışma zamanında başarısız olabilir**  
  
- **Örtük tür; Nesne varsayıldı**  
  
  Ayarladığınızda **Option Strict** için **üzerinde**, bu uyarı yapılandırma ayarlarını üç kümesine **hata**. Ayarladığınızda **Option Strict** için **kapalı**, tüm üç ayarları kümesine **hiçbiri**.  
  
  Her uyarı yapılandırma ayarı ayrı ayrı değiştirebileceğiniz **hiçbiri**, **uyarı**, veya **hata**. Üç uyarı yapılandırma ayarlarını ayarlandıysa **hata**, `On` görünür `Option strict` kutusu. Üç ayarlandıysa **hiçbiri**, `Off` bu kutuda görünür. Bu ayarlar, diğer herhangi bir birleşimini için **(özel)** görünür.  
  
  **Karşılaştırma seçeneği**  
  Kullanılacak dize karşılaştırma türünü belirtir. Seçin **ikili** derleyicisinin ikili, büyük küçük harfe duyarlı dize karşılaştırmaları kullanın. Seçin **metin** metin yerel ayara özgü, büyük küçük harf duyarsız dize karşılaştırmalarını kullanmak için.  
  
  Bu ayar karşılık gelen [/optioncompare](http://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4) derleyici seçeneği.  
  
  Bir kaynak kodu dosyası içeriyorsa bir [seçenek karşılaştırma ifadesini](http://msdn.microsoft.com/library/54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e), `Binary` veya `Text` deyiminde değerini geçersiz kılar **Option Compare** ayarını **derleme Sayfa**.  
  
  Bir proje oluşturduğunuzda **Option Compare** ayarını **derleme sayfası** değerine ayarlanmış **Option Compare** ayarı **seçenekleri** iletişim kutusu. Görüntülemek veya bu iletişim kutusunda bir ayarı değiştirmek için **Araçları** menüsünü tıklatın **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda **projeler ve çözümler**ve ardından **VB varsayılanları**. İlk varsayılan ayarı **Option Compare** içinde **VB varsayılanları** olduğu **ikili**.  
  
  **Option Infer**  
  Yerel tür çıkarımı değişken bildirimlerinde izin verilip verilmeyeceğini belirtir. Seçin **üzerinde** yerel tür çıkarımı kullanımına izin vermek için. Seçin **kapalı** blok yerel tür çıkarımı için.  
  
  Bu ayar karşılık gelen [/optioninfer](http://msdn.microsoft.com/library/f6c09db1-0553-464a-abe3-d4510c61d6ed) derleyici seçeneği.  
  
  Bir kaynak kodu dosyası içeriyorsa bir [Option Infer deyimi](http://msdn.microsoft.com/library/4ad3e6e9-8f5b-4209-a248-de22ef6e4652), `On` veya `Off` deyiminde değerini geçersiz kılar **Option Infer** ayarını **derle sayfası** .  
  
  Bir proje oluşturduğunuzda **Option Infer** ayarını **derleme sayfa** değerine ayarlanmış **Option Infer** ayarı **seçenekleri**iletişim kutusu. Görüntülemek veya bu iletişim kutusunda bir ayarı değiştirmek için **Araçları** menüsünü tıklatın **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda **projeler ve çözümler**ve ardından **VB varsayılanları**. İlk varsayılan ayarı **Option Infer** içinde **VB varsayılanları** olduğu **üzerinde**.  
  
  **Hedef CPU**  
  Çıktı dosyası tarafından hedeflenecek işlemciyi belirtir. Belirtin **x86** herhangi bir 32 bit Intel uyumlu işlemci için **x64** herhangi bir 64-bit Intel uyumlu işlemci için **ARM** tüm ARM işlemci için veya **herhangi bir CPU**  tüm işlemcilerin kabul edilebilir olduğunu belirtmek için. **Herhangi bir CPU** uygulamanın en büyük sayısını donanım türleri üzerinde çalışmasına izin verdiğinden yeni projeler için varsayılan değerdir.  
  
  Daha fazla bilgi için [/Platform (Visual Basic)](http://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1).  
  
  **32 bit tercih edin**  
  Varsa **Prefer32-bit** onay kutusu seçildiğinde, uygulama bir 32 bit uygulama olarak, hem 32-bit hem de 64 bit Windows sürümlerinde çalışır. Aksi takdirde, uygulamanın Windows ve Windows 64 bit sürümlerinde 64 bit uygulama olarak 32-bit sürümleri 32-bit uygulama olarak çalışır.  
  
  64 bitlik bir uygulama işaretçi boyutu iki katına çıkar ve özellikle 32 bit kitaplıkları uyumluluk sorunlarına neden olabilir olarak çalışıyor. Yalnızca önemli ölçüde daha hızlı çalışır veya 4 GB'den daha fazla bellek gerekli bir uygulamayı 64-bit olarak çalıştırmak mantıklıdır.  
  
  Bu onay kutusu yalnızca aşağıdaki koşulların tümü doğruysa, kullanılabilir:  
  
- Üzerinde **derle sayfası**, **hedef CPU** listesinin **herhangi bir CPU**.  
  
- Üzerinde **uygulama sayfası**, **uygulama türü** listesi, projenin bir uygulama olduğunu belirtir.  
  
- Üzerinde **uygulama sayfası**, **hedef Framework'ü** listesi .NET Framework 4.5 belirtir.  
  
  **Uyarı yapılandırma**  
  Bu tabloda derleme koşullar ve karşılık gelen bildirim düzeyini **hiçbiri**, **uyarı**, veya **hata** her.  
  
  Varsayılan olarak, tüm Derleyici uyarılarını, derleme sırasında görev listesine eklenir. Seçin **tüm uyarıları devre dışı bırak** derleyicisinin sorunu uyarıları veya hataları. Seçin **tüm uyarıları hata olarak değerlendir** Derleyicinin uyarıları düzeltilmesi gereken hata olarak değerlendir istiyorsanız.  
  
  **Tüm uyarıları devre dışı bırak**  
  Sorunu bildirimleri belirtildiği gibi derleyici izin verilip verilmeyeceğini belirten **koşulu ve bildirim** bu belgenin önceki bölümlerinde açıklanan tablo. Varsayılan olarak, bu onay kutusu işaretli değildir. Derleyicisinin bir uyarı veya hata sorun değil, bu onay kutusunu seçin.  
  
  Bu ayar karşılık gelen [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) derleyici seçeneği.  
  
  **Tüm uyarıları hata olarak değerlendir**  
  Uyarıları nasıl belirtir. Tüm uyarı bildirimleri için ayarlanmış kalmaları için varsayılan olarak, bu onay kutusu, temizlenir **uyarı**. Tüm Uyarı bildirimlerinin postalanacağı değiştirmek için bu onay kutusunu işaretleyin **hata**.  
  
  Bu seçenek yalnızca **tüm uyarıları devre dışı bırak** temizlenir.  
  
  **XML belge dosyası oluşturma**  
  Belgelendirme bilgilerini oluşturulup oluşturulmayacağını belirtir. Varsayılan olarak, belgelendirme bilgilerini oluşturup bir XML dosyasına eklenecek derleyici söyleyen bu onay kutusu seçilidir. Belgeleri oluşturmamayı derleyicisinin bu onay kutusunu temizleyin.  
  
  Bu ayar karşılık gelen [/doc](http://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65) derleyici seçeneği.  
  
  **COM birlikte çalışması için kaydol**  
  Yönetilen uygulama ile etkileşim kurmak bir COM nesnesi sağlayan bir COM nesnesi (COM çağrılabilir sarmalayıcısı) açığa çıkarır olup olmadığını belirtir.  
  
  Varsayılan olarak, uygulama COM birlikte çalışma izin vermeyeceğini belirten bu onay kutusunu temizlenir. COM birlikte çalışma izin vermek için bu onay kutusunu seçin.  
  
  Bu seçenek Windows uygulama veya konsol uygulaması projelerinde kullanılamaz.  
  
  **Derleme olayları**  
  Erişim için bu düğmeye tıklayın **Build Events** iletişim kutusu. Derleme öncesi ve sonrası yapılandırma yönergeleri için projeyi belirtmek için bu iletişim kutusunu kullanın. Bu iletişim kutusu, yalnızca Visual Basic projeleri için geçerlidir. Daha fazla bilgi için [derleme olayları iletişim kutusu (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md).  
  
  **Gelişmiş derleme seçenekleri**  
  Erişim için bu düğmeye tıklayın **AdvancedCompiler ayarları** iletişim kutusu. Kullanım **AdvancedCompiler ayarları** Gelişmiş yapı yapılandırma özellikleri iletişim kutusu, bir projeyi belirtmek için. Bu iletişim kutusu, yalnızca Visual Basic projeleri için geçerlidir. Daha fazla bilgi için [Gelişmiş derleyici Ayarları iletişim kutusu (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama ve yayın proje yapılandırmaları](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e)   
 [Derleme özelliklerini yönetme](http://msdn.microsoft.com/en-us/94308881-f10f-4caf-a729-f1028e596a2c)   
 [Nasıl yapılır: derleme olayları belirtme (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Visual Basic komut satırı derleyicisi](http://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)   
 [Nasıl Yapılır: Yapılandırmaları Oluşturma ve Düzenleme](../../ide/how-to-create-and-edit-configurations.md)



