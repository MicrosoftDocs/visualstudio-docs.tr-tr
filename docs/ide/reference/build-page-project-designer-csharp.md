---
title: Derleme Sayfası, Proje Tasarımcısı (C#)
ms.date: 06/20/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b003b3f965ab4f3857e2a532ae715d99533aa8e7
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38783824"
---
# <a name="build-page-project-designer-c"></a>Derleme Sayfası, Proje Tasarımcısı (C#)
Kullanım **derleme** sayfasının **Proje Tasarımcısı** projenin yapı yapılandırması özelliklerini belirtmek için. Bu sayfa uygulandığı [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] yalnızca projeleri.

Erişim için **derleme** sayfasında, bir proje düğümü seçin (değil **çözüm** düğümü) içinde **Çözüm Gezgini**. Ardından **görünümü**, **özellik sayfaları** menüsünde. Proje Tasarımcısı göründüğünde **derleme** sekmesi.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Yapılandırma ve Platform
Aşağıdaki seçenekler, görüntülenecek veya değiştirilecek platform ve yapılandırmayı seçmenize olanak sağlar.

> [!NOTE]
> Basitleştirilmiş yapı yapılandırmaları ile proje sistemi bir hata ayıklama sürüm yayını mı belirler. Bu nedenle, bu seçenekler görüntülenmez. Daha fazla bilgi için [nasıl yapılır: ayarlama hata ayıklama ve dağıtım yapılandırmalarını](../../debugger/how-to-set-debug-and-release-configurations.md).

**Yapılandırma** hangi yapılandırma ayarlarının görüntüleneceğini veya değiştirileceğini belirtir. Ayarları **etkin (hata ayıklama)** (varsayılan değer), **hata ayıklama**, **yayın**, veya **yapılandırmalarında**.

**Platform** platform ayarlarının görüntüleneceğini veya değiştirileceğini belirtir. Varsayılan ayar **etkin (herhangi bir CPU)**. Etkin platformu kullanarak değiştirebileceğiniz **Configuration Manager**. Daha fazla bilgi için [nasıl yapılır: yapılandırmaları oluşturma ve düzenleme](../../ide/how-to-create-and-edit-configurations.md).

## <a name="general"></a>Genel
Aşağıdaki seçenekler bazı C# Derleyici ayarlarını yapılandırmanıza olanak sağlar.

**Koşullu derleme simgeleri** üzerinde koşullu derleme yapılacak olan sembolleri belirtir. Simgeleri bir noktalı virgül ile ayırın (";"). Daha fazla bilgi için [/ define (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).

**DEBUG sabitini tanımlama** dosyaları uygulamanızdaki tüm kaynak kodu sembol olarak DEBUG tanımlar. Bu seçeneğin seçilmesi kullanmaya eşdeğerdir `/define:DEBUG` komut satırı seçeneği.

**TRACE sabitini tanımlama** dosyaları uygulamanızdaki tüm kaynak kodu sembol olarak TRACE tanımlar. Bu seçeneğin seçilmesi kullanmaya eşdeğerdir `/define:TRACE` komut satırı seçeneği.

**Platform hedefi** çıktı dosyası tarafından hedeflenecek işlemciyi belirtir. Seçin **x86** seçin tüm 32 bit Intel uyumlu işlemci için **x64** herhangi 64-bit Intel uyumlu işlemci için seçin **ARM** ARM işlemcileri için veya seçin **Herhangi bir CPU** tüm işlemcilerin kabul edilebilir olduğunu belirtmek için. **Herhangi bir CPU** uygulamanın çok çeşitli donanımlar üzerinde çalışmasına izin verdiğinden projeler için varsayılan değerdir.

Daha fazla bilgi için [/Platform (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).

**32 bit tercih** varsa **Prefer32-bit** onay kutusu seçildiğinde, uygulama bir 32 bit uygulama olarak, hem 32-bit hem de 64 bit Windows sürümlerinde çalışır. Onay kutusu işaretli değilse uygulama Windows ve Windows 64 bit sürümlerinde 64 bit uygulama olarak 32-bit sürümleri 32-bit uygulama olarak çalışır.

64 bit uygulama olarak, işaretçi boyutu iki kat büyür, bir uygulamayı çalıştırmak ve özellikle 32 bit olan diğer kitaplıklarla uyumluluk sorunları ortaya çıkabilir. Yalnızca 4 GB'den daha fazla bellek ihtiyacı ya da 64 bitlik Yönergeleriniz önemli bir performans geliştirmesi sağlayan bir 64 bit uygulamayı çalıştırmak kullanışlıdır.

Bu onay kutusu yalnızca aşağıdaki koşulların tümü doğruysa, kullanılabilir:

-   Üzerinde **yapı sayfası**, **Platform hedefi** listesinin **herhangi bir CPU**.

-   Üzerinde **uygulama sayfası**, **çıkış türü** listesi, projenin bir uygulama olduğunu belirtir.

-   Üzerinde **uygulama sayfası**, **hedef Framework'ü** listesi .NET Framework 4.5 belirtir.


**Güvenli olmayan koda izin ver** kullanan verir kod [güvenli](/dotnet/csharp/language-reference/keywords/unsafe) derlemek için anahtar sözcüğü. Daha fazla bilgi için [/ unsafe (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).

**Kodu En İyileştir** etkinleştirmek veya çıkış dosyanızı daha küçük, daha hızlı ve daha verimli yapmak için derleyici tarafından gerçekleştirilen iyileştirmeleri devre dışı bırakın. Daha fazla bilgi için [/ optimize (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).

## <a name="errors-and-warnings"></a>Hatalar ve uyarılar
Aşağıdaki ayarlar, hata ve uyarı yapı işlemi seçeneklerini yapılandırmak için kullanılır.

**Uyarı düzeyi** Derleyici uyarılarını görüntüleme düzeyini belirtir. Daha fazla bilgi için [/ warn (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).

**Uyarıları bastır** derleyicinin bir veya daha fazla uyarı oluşturma yeteneğini engeller. Birden çok uyarı numaralarını virgülle veya noktalı virgül ile ayırın. Daha fazla bilgi için [/nowarn (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).

## <a name="treat-warnings-as-errors"></a>Uyarıları hata olarak değerlendir
Aşağıdaki ayarlar hangi uyarıların hata olarak kabul edileceğini belirtmek için kullanılır. Hangi koşullar altında yapı bir uyarı ile karşılaştığında, bir hata döndüreceğini belirtmek için aşağıdaki seçeneklerden birini seçin. Daha fazla bilgi için [/warnaserror (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).

**Hiçbiri** uyarı hata olarak değerlendirir.

**Belirli uyarıları** belirtilen uyarılara hata olarak değerlendirir. Birden çok uyarı numaralarını virgülle veya noktalı virgül ile ayırın.

**Tüm** tüm uyarıları hata olarak değerlendirir.

## <a name="output"></a>Çıkış
Aşağıdaki ayarlar, yapı işlemine yönelik çıktı seçeneklerini yapılandırmak için kullanılır.

**Çıkış yolu** bu projenin yapılandırması için çıkış dosyalarının konumunu belirtir. Bu kutuya yapı çıkış yolunu girin veya seçin **Gözat** düğmesine bir yol belirtin. Yolun göreli olduğuna dikkat edin; mutlak bir yol girerseniz, göreli olarak kaydedilecektir. Varsayılan yol bin\Debug veya bin\Release olan\\.

Basitleştirilmiş yapı yapılandırmaları ile proje sistemi bir hata ayıklama sürüm yayını mı belirler. **Derleme** komutunu **hata ayıklama** menüsündeki (F5) bağımsız olarak, hata ayıklama konumuna derleme koyacaktır **çıkış yolu** belirtirsiniz. Ancak, **derleme** komutunu **derleme** menü, belirttiğiniz konuma koyar. Daha fazla bilgi için [derleme yapılandırmalarını anlama](../../ide/understanding-build-configurations.md).

**XML belge dosyası** belgeleme açıklamalarının işleneceği dosyanın adını belirtir. Daha fazla bilgi için [/doc (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).

**COM birlikte çalışması için kayıt** yönetilen uygulamanız COM nesnesinin yönetilen uygulamanızla etkileşmesini sağlar bir COM nesnesi (COM çağrılabilir sarmalayıcısı) açığa çıkarır gösterir. **Çıkış türü** özelliğinde [uygulama sayfası](../../ide/reference/application-page-project-designer-visual-basic.md) , **Proje Tasarımcısı** bu uygulama kümesi için **sınıf kitaplığı** içinde için sipariş **kaydetme COM birlikte çalışması için** özelliği kullanılabilir. Dahil edebileceğiniz bir örnek sınıfı için [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] uygulama ve bir COM nesnesi olarak gösterebileceğiniz [örnek COM sınıfı](/dotnet/csharp/programming-guide/interop/example-com-class).

**Serileştirme derlemesi oluştur** XML serileştirme derlemeleri oluşturmak için derleyicinin XML serileştiricisi Oluşturma Aracı (Sgen.exe) kullanıp kullanmayacağını belirtir. Serileştirme derlemeleri başlatma performansını geliştirebilir <xref:System.Xml.Serialization.XmlSerializer> kodunuzda türleri serileştirmek için bu sınıfı kullandıysanız. Varsayılan olarak, bu seçeneği ayarlamak **otomatik**, yalnızca kullandıysanız, serileştirme derlemelerinin oluşturulacağını belirten <xref:System.Xml.Serialization.XmlSerializer> kodunuzdaki XML kodlama. **Kapalı** serileştirme derlemelerinin hiçbir zaman, kodunuzun kullanıp bağımsız olarak oluşturulmamasını belirtir <xref:System.Xml.Serialization.XmlSerializer>. **Üzerinde** serileştirme derlemelerinin her zaman oluşturulacağını belirtir. Serileştirme derlemeleri yeniden adlandırılır `TypeName`. XmlSerializers.dll. Daha fazla bilgi için [XML serileştiricisi Oluşturma Aracı (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

**Gelişmiş** görüntülemek için sonuçlara tıklayın [Gelişmiş derleme Ayarları iletişim kutusu (C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md) iletişim kutusu.

## <a name="see-also"></a>Ayrıca Bkz.

- [Proje Özellikleri Başvurusu](../../ide/reference/project-properties-reference.md)
- [C# Derleyici Seçenekleri](/dotnet/csharp/language-reference/compiler-options/index)