---
title: Gelişmiş derleme Ayarları iletişim kutusu (C#) | Microsoft Docs
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
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9f3d62f6cd393dfccdaeb9047bac4780546f0087
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811983"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Gelişmiş Derleme Ayarları İletişim Kutusu (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Kullanım **AdvancedBuild ayarları** iletişim kutusunun **Proje Tasarımcısı** Proje Gelişmiş yapı yapılandırması özelliklerini belirtmek için. Bu iletişim kutusunu uygulandığı [!INCLUDE[csprcs](../../includes/csprcs-md.md)] yalnızca projeleri.  
  
## <a name="general"></a>Genel  
 Aşağıdaki seçenekler, genel Gelişmiş ayarları ayarlamanızı sağlar.  
  
 **Dil sürümü**  
 Kullanılacak dilin sürümünü belirtir. Yalnızca bir alt uygulanan özelliklerin izin vermek için veya yalnızca mevcut bir standardı ile uyumlu özellikleri etkinleştirmek için zorlamak için bu seçeneği kullanabilmeniz özellik kümesi her sürümde farklıdır. Bu ayar, şu seçeneklere sahiptir:  
  
- **ISO-1**  
  
   ISO-1 standart özellikleri hedefler.  
  
- **default**  
  
   Geçerli sürümünü hedefler.  
  
  Daha fazla bilgi için [/langversion (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).  
  
  **İç derleyici hata bildirimi**  
  Derleyici hatalarını Microsoft'a belirtir. Varsa kümesine **istemi** derleyici iç hatası oluşursa (varsayılan), bir komut istemi bir hata raporu elektronik olarak Microsoft'a gönderme seçeneğini verir elde edersiniz. Varsa kümesine **Gönder**, bir hata raporu otomatik olarak gönderilir. Varsa kümesine **kuyruk**, hata raporlarını kuyruğa alınacak. Varsa kümesine **hiçbiri**, yalnızca derleyicinin metin çıktısında hata bildirilir. Daha fazla bilgi için [/errorreport (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).  
  
  **Aritmetik Taşma ve alttaşmayı denetle**  
  Bir tamsayı aritmetik ifadesi, kapsamı içinde olup olmadığını belirtir [kullanıma](http://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) veya [denetlenmeyen](http://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) anahtar sözcükleri ve veri türü aralık dışında bir değer sonuçları bir çalışma zamanı neden olur özel durum. Daha fazla bilgi için [/ checked (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).  
  
  **Mscorlib.dll dosyasına başvurma**  
  Mscorlib.dll programınıza tüm tanımlama içeri olup olmadığını belirtir <xref:System> ad alanı. Tanımlayın veya kendi oluşturmak istiyorsanız bu kutuyu <xref:System> ad alanı ve nesneler. Daha fazla bilgi için [/nostdlib (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).  
  
## <a name="output"></a>Çıkış  
 Aşağıdaki seçenekler Gelişmiş çıkış seçenekleri belirtmenize olanak verir.  
  
 **Hata ayıklama bilgileri**  
 Derleyici tarafından oluşturulan hata ayıklama bilgilerinin türünü belirtir. Bir uygulamanın hata ayıklama performansını yapılandırma hakkında daha fazla bilgi için bkz: [bir görüntü için hata ayıklama kolaylaştıracak](http://msdn.microsoft.com/library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3). Bu ayar, şu seçeneklere sahiptir:  
  
- **Yok**  
  
   Hata ayıklama bilgisi oluşturulacağını belirtir  
  
- **Tam**  
  
   Bir Haya ayıklayıcı çalışan programa etkinleştirir.  
  
- **pdbonly**  
  
   Kaynak kodu programın hata ayıklayıcıda başlatıldı ancak çalışan programa hata ayıklayıcıya bağlı olduğu assembler yalnızca görüntüler hata ayıklamasına izin verir.  
  
  Daha fazla bilgi için [/Debug (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).  
  
  **Dosya hizalama**  
  Bölüm boyutu, çıkış dosyasında belirtir. Geçerli değerler **512**, **1024**, **2048**, **4096**, ve **8192**. Bu değerler, bayt cinsinden ölçülür. Her bölümde, çıkış dosyasının boyutu etkileyen bu değer,'in katı bir sınır üzerinde hizalanır. Daha fazla bilgi için [/filealign (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).  
  
  **DLL temel adresi**  
  Bir DLL yüklemek için tercih edilen temel adresini belirtir. Bir DLL için varsayılan taban adresi belirlediği [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ortak dil çalışma zamanı. Daha fazla bilgi için [/baseaddress (C# Derleyici Seçenekleri)](http://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](http://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44)   
 [Derleme Sayfası, Proje Tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md)



