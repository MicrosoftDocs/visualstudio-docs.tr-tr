---
title: Derleme sayfası, Proje Tasarımcısı (C#) | Microsoft Docs
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
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
caps.latest.revision: 47
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a377db0ac82b672d053e59c621714945fa9b515c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837190"
---
# <a name="build-page-project-designer-c"></a>Derleme Sayfası, Proje Tasarımcısı (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Kullanım **derleme** sayfasının **Proje Tasarımcısı** projenin yapı yapılandırması özelliklerini belirtmek için. Bu sayfa uygulandığı [!INCLUDE[csprcs](../../includes/csprcs-md.md)] yalnızca projeleri.  
  
 Erişim için **derleme** sayfasında, bir proje düğümü seçin (değil **çözüm** düğümü) içinde **Çözüm Gezgini**. Ardından **proje**, **özellikleri** menü çubuğundaki. Proje Tasarımcısı göründüğünde tıklayın **derleme** sekmesi.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="configuration-and-platform"></a>Yapılandırma ve Platform  
 Aşağıdaki seçenekler, görüntülenecek veya değiştirilecek platform ve yapılandırmayı seçmenize olanak sağlar.  
  
> [!NOTE]
>  Basitleştirilmiş yapı yapılandırmaları ile proje sistemi bir hata ayıklama sürüm yayını mı belirler. Bu nedenle, bu seçenekler görüntülenmez. Daha fazla bilgi için [hata ayıklama ve dağıtım proje yapılandırmalarını](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 **Yapılandırma**  
 Hangi yapılandırma ayarlarının görüntüleneceğini veya değiştirileceğini belirtir. Ayarları **etkin (hata ayıklama)** (varsayılan değer), **hata ayıklama**, **yayın**, veya **yapılandırmalarında**.  
  
 **Platform**  
 Platform ayarlarının görüntüleneceğini veya değiştirileceğini belirtir. Varsayılan ayar **etkin (herhangi bir CPU)**. Etkin platformu kullanarak değiştirebileceğiniz **Configuration Manager**. Daha fazla bilgi için [nasıl yapılır: yapılandırmaları oluşturma ve düzenleme](../../ide/how-to-create-and-edit-configurations.md).  
  
## <a name="general"></a>Genel  
 Aşağıdaki seçenekler bazı C# Derleyici ayarlarını yapılandırmanıza olanak sağlar.  
  
 **Koşullu derleme simgeleri**  
 Üzerinde koşullu derleme yapılacak olan sembolleri belirtir. Simgeleri bir noktalı virgül ile ayırın (";"). Daha fazla bilgi için [/ define (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e).  
  
 **DEBUG sabitini tanımlayın**  
 Uygulamanızdaki tüm kaynak kodu dosyalarında sembol olarak DEBUG tanımlar. Bu seçeneğin seçilmesi kullanmaya eşdeğerdir `/define:DEBUG` komut satırı seçeneği.  
  
 **TRACE sabitini tanımlayın**  
 Uygulamanızdaki tüm kaynak kodu dosyalarında sembol olarak TRACE tanımlar. Bu seçeneğin seçilmesi kullanmaya eşdeğerdir `/define:TRACE` komut satırı seçeneği.  
  
 **Hedef CPU**  
 Çıktı dosyası tarafından hedeflenecek işlemciyi belirtir. Seçin **x86** seçin tüm 32 bit Intel uyumlu işlemci için **x64** herhangi 64-bit Intel uyumlu işlemci için seçin **ARM** ARM işlemcileri için veya seçin **Herhangi bir CPU** tüm işlemcilerin kabul edilebilir olduğunu belirtmek için. **Herhangi bir CPU** uygulamanın çok çeşitli donanımlar üzerinde çalışmasına izin verdiğinden projeler için varsayılan değerdir.  
  
 Daha fazla bilgi için [/Platform (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04).  
  
 **32 bit tercih edin**  
 Varsa **Prefer32-bit** onay kutusu seçildiğinde, uygulama bir 32 bit uygulama olarak, hem 32-bit hem de 64 bit Windows sürümlerinde çalışır. Onay kutusu işaretli değilse uygulama Windows ve Windows 64 bit sürümlerinde 64 bit uygulama olarak 32-bit sürümleri 32-bit uygulama olarak çalışır.  
  
 64 bit uygulama olarak, işaretçi boyutu iki kat büyür, bir uygulamayı çalıştırmak ve özellikle 32 bit olan diğer kitaplıklarla uyumluluk sorunları ortaya çıkabilir. Yalnızca 4 GB'den daha fazla bellek ihtiyacı ya da 64 bitlik Yönergeleriniz önemli bir performans geliştirmesi sağlayan bir 64 bit uygulamayı çalıştırmak kullanışlıdır.  
  
 Bu onay kutusu yalnızca aşağıdaki koşulların tümü doğruysa, kullanılabilir:  
  
- Üzerinde **yapı sayfası**, **Platform hedefi** listesinin **herhangi bir CPU**.  
  
- Üzerinde **uygulama sayfası**, **çıkış türü** listesi, projenin bir uygulama olduğunu belirtir.  
  
- Üzerinde **uygulama sayfası**, **hedef Framework'ü** listesi .NET Framework 4.5 belirtir.  
  
  **Güvenli olmayan koda izin ver**  
  Kullanan koda izin verir [güvenli](http://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) derlemek için anahtar sözcüğü. Daha fazla bilgi için [/ unsafe (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc).  
  
  **Kodu En İyileştir**  
  Etkinleştirmek veya çıkış dosyanızı daha küçük, daha hızlı ve daha verimli yapmak için derleyici tarafından gerçekleştirilen iyileştirmeleri devre dışı bırakın. Daha fazla bilgi için [/ optimize (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0).  
  
## <a name="errors-and-warnings"></a>Hatalar ve uyarılar  
 Aşağıdaki ayarlar, hata ve uyarı yapı işlemi seçeneklerini yapılandırmak için kullanılır.  
  
 **Uyarı düzeyi**  
 Derleyici uyarılarını görüntüleme düzeyini belirtir. Daha fazla bilgi için [/ warn (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71).  
  
 **Uyarıları bastırma**  
 Derleyicinin bir veya daha fazla uyarı oluşturma yeteneğini engeller. Birden çok uyarı numaralarını virgülle veya noktalı virgül ile ayırın. Daha fazla bilgi için [/nowarn (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4).  
  
## <a name="treat-warnings-as-errors"></a>Uyarıları hata olarak değerlendir  
 Aşağıdaki ayarlar hangi uyarıların hata olarak kabul edileceğini belirtmek için kullanılır. Hangi koşullar altında yapı bir uyarı ile karşılaştığında, bir hata döndüreceğini belirtmek için aşağıdaki seçeneklerden birini seçin. Daha fazla bilgi için [/warnaserror (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).  
  
 **Yok**  
 Uyarı hata olarak değerlendirir.  
  
 **Belirli uyarıları**  
 Belirtilen uyarılara hata olarak değerlendirir. Birden çok uyarı numaralarını virgülle veya noktalı virgül ile ayırın.  
  
 **Tüm**  
 Tüm uyarıları hata olarak değerlendirir.  
  
## <a name="output"></a>Çıkış  
 Aşağıdaki ayarlar, yapı işlemine yönelik çıktı seçeneklerini yapılandırmak için kullanılır.  
  
 **Çıkış yolu**  
 Bu projenin yapılandırması için çıkış dosyalarının konumunu belirtir. Bu kutuya yapı çıkış yolunu girin veya seçin **Gözat** düğmesine bir yol belirtin. Yolun göreli olduğuna dikkat edin; mutlak bir yol girerseniz, göreli olarak kaydedilecektir. Varsayılan yol bin\Debug veya bin\Release olan\\. Daha fazla bilgi için [hata ayıklama ve dağıtım proje yapılandırmalarını](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 Basitleştirilmiş yapı yapılandırmaları ile proje sistemi bir hata ayıklama sürüm yayını mı belirler. **Derleme** komutunu **hata ayıklama** menüsündeki (F5) bağımsız olarak, hata ayıklama konumuna derleme koyacaktır **çıkış yolu** belirtirsiniz. Ancak, **derleme** komutunu **derleme** menü, belirttiğiniz konuma koyar. Daha fazla bilgi için [hata ayıklama ve dağıtım proje yapılandırmalarını](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 **XML belge dosyası**  
 Belgeleme açıklamalarının işleneceği dosyanın adını belirtir. Daha fazla bilgi için [/doc (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a).  
  
 **COM birlikte çalışması için kaydol**  
 Yönetilen uygulamanızın COM nesnesinin yönetilen uygulamanızla etkileşmesini sağlar bir COM nesnesi (COM çağrılabilir sarmalayıcısı) açığa çıkarır gösterir. **Çıkış türü** özelliğinde [uygulama sayfası](../../ide/reference/application-page-project-designer-visual-basic.md) , **Proje Tasarımcısı** bu uygulama kümesi için **sınıf kitaplığı** içinde için sipariş **kaydetme COM birlikte çalışması için** özelliği kullanılabilir. Dahil edebileceğiniz bir örnek sınıfı için [!INCLUDE[csprcs](../../includes/csprcs-md.md)] uygulama ve bir COM nesnesi olarak gösterebileceğiniz [örnek COM sınıfı](http://msdn.microsoft.com/library/6504dea9-ad1c-4993-a794-830fec5270af).  
  
 **Serileştirme derlemesi oluştur**  
 XML serileştirme derlemeleri oluşturmak için derleyicinin XML serileştiricisi Oluşturma Aracı (Sgen.exe) kullanıp kullanmayacağını belirtir. Serileştirme derlemeleri başlatma performansını geliştirebilir <xref:System.Xml.Serialization.XmlSerializer> kodunuzda türleri serileştirmek için bu sınıfı kullandıysanız. Varsayılan olarak, bu seçeneği ayarlamak **otomatik**, yalnızca kullandıysanız, serileştirme derlemelerinin oluşturulacağını belirten <xref:System.Xml.Serialization.XmlSerializer> kodunuzdaki XML kodlama. **Kapalı** serileştirme derlemelerinin hiçbir zaman, kodunuzun kullanıp bağımsız olarak oluşturulmamasını belirtir <xref:System.Xml.Serialization.XmlSerializer>. **Üzerinde** serileştirme derlemelerinin her zaman oluşturulacağını belirtir. Serileştirme derlemeleri yeniden adlandırılır `TypeName`. XmlSerializers.dll. Daha fazla bilgi için [XML serileştiricisi Oluşturma Aracı (Sgen.exe)](http://msdn.microsoft.com/library/cc1d1f1c-fb26-4be9-885a-3fe84c81cec6).  
  
 **Gelişmiş**  
 Görüntülemek için sonuçlara tıklayın [Gelişmiş derleme Ayarları iletişim kutusu (C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md) iletişim kutusu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje Özellikleri başvurusu](../../ide/reference/project-properties-reference.md)   
 [C# Derleyici Seçenekleri](http://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44)



