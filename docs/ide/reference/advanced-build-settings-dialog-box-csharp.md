---
title: Gelişmiş Derleme Ayarları İletişim Kutusu (C#)
ms.date: 06/20/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: cf4fd5b48dc3bfcfbfe1809eebe656a5b8f2079d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928288"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Gelişmiş Derleme Ayarları İletişim Kutusu (C#)

Kullanım **Gelişmiş derleme ayarları** iletişim kutusunun **Proje Tasarımcısı** Proje Gelişmiş yapı yapılandırması özelliklerini belirtmek için. Bu iletişim kutusunu uygulandığı [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] yalnızca projeleri.

## <a name="general"></a>Genel

Aşağıdaki seçenekler, genel Gelişmiş ayarları ayarlamanızı sağlar.

**Dil sürümü**

Kullanılacak dilin sürümünü belirtir. Yalnızca bir alt uygulanan özelliklerin izin vermek için veya yalnızca mevcut bir standardı ile uyumlu özellikleri etkinleştirmek için zorlamak için bu seçeneği kullanabilmeniz özellik kümesi her sürümde farklıdır. Bu ayar, şu seçeneklere sahiptir:

- **default**

   Geçerli sürümünü hedefler.

- **ISO-1** ve **ISO-2**

   ISO-1 ve 2 ISO standart özellikleri sırasıyla hedefler.

- **C#[sürüm numarası]**

   Belirli bir sürümünü hedefleyen C#. Daha fazla bilgi için [/langversion (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).

**İç derleyici hata bildirimi**

Derleyici hatalarını Microsoft'a belirtir. Varsa kümesine **istemi** derleyici iç hatası oluşursa (varsayılan), bir komut istemi bir hata raporu elektronik olarak Microsoft'a gönderme seçeneğini verir elde edersiniz. Varsa kümesine **Gönder**, bir hata raporu otomatik olarak gönderilir. Varsa kümesine **kuyruk**, hata raporlarını kuyruğa alınacak. Varsa kümesine **hiçbiri**, yalnızca derleyicinin metin çıktısında hata bildirilir. Daha fazla bilgi için [/errorreport (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).

**Aritmetik Taşma ve alttaşmayı denetle**

Bir tamsayı aritmetik ifadesi, kapsamı içinde olup olmadığını belirtir [kullanıma](/dotnet/csharp/language-reference/keywords/checked) veya [denetlenmeyen](/dotnet/csharp/language-reference/keywords/unchecked) anahtar sözcükleri ve veri türü aralık dışında bir değer sonuçları bir çalışma zamanı neden olur özel durum. Daha fazla bilgi için [/ checked (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).

**Mscorlib.dll dosyasına başvurma**

Mscorlib.dll programınıza tüm tanımlama içeri olup olmadığını belirtir <xref:System> ad alanı. Tanımlayın veya kendi oluşturmak istiyorsanız bu kutuyu <xref:System> ad alanı ve nesneler. Daha fazla bilgi için [/nostdlib (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).

## <a name="output"></a>Çıkış

Aşağıdaki seçenekler Gelişmiş çıkış seçenekleri belirtmenize olanak verir.

**Hata ayıklama bilgileri**

Derleyici tarafından oluşturulan hata ayıklama bilgilerinin türünü belirtir. Bir uygulamanın hata ayıklama performansını yapılandırma hakkında daha fazla bilgi için bkz: [bir görüntü için hata ayıklama kolaylaştıracak](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug). Bu ayar, şu seçeneklere sahiptir:

- **Yok**

   Hata ayıklama bilgisi oluşturulacağını belirtir.

- **Tam**

   Bir Haya ayıklayıcı çalışan programa etkinleştirir.

- **pdbonly**

   Kaynak kodu programın hata ayıklayıcıda başlatıldı ancak çalışan programa hata ayıklayıcıya bağlı olduğu assembler yalnızca görüntüler hata ayıklamasına izin verir.

-  **Taşınabilir**

   Üreten bir. PDB dosyası, diğer araçlar sağlayan bir platforma özgü olmayan ve taşınabilir sembol dosyası özellikle hata ayıklayıcıları, hakkında bilgi ana yürütülebilir dosyanın ve nasıl üretilmiştir. Bkz: [taşınabilir PDB](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) daha fazla bilgi için.

- **Katıştırılmış**

   Taşınabilir sembol bilgilerini derlemesine katıştırır. Dış yok. PDB dosyası oluşturulur.

Daha fazla bilgi için [/Debug (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).

**Dosya hizalama**

Bölüm boyutu, çıkış dosyasında belirtir. Geçerli değerler **512**, **1024**, **2048**, **4096**, ve **8192**. Bu değerler, bayt cinsinden ölçülür. Her bölümde, çıkış dosyasının boyutu etkileyen bu değer,'in katı bir sınır üzerinde hizalanır. Daha fazla bilgi için [/filealign (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).

**Kitaplık temel adres**

Bir DLL yüklemek için tercih edilen temel adresini belirtir. Bir DLL için varsayılan taban adresi belirlediği [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] ortak dil çalışma zamanı. Daha fazla bilgi için [/baseaddress (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).

## <a name="see-also"></a>Ayrıca Bkz.

- [C# Derleyici Seçenekleri](/dotnet/csharp/language-reference/compiler-options/index)
- [Derleme Sayfası, Proje Tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md)