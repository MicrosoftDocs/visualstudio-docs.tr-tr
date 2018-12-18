---
title: Yazı tipleri ve renkler kullanarak | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4415d00e5a1233bfdf14dbc86a3a7ed2f7b8e770
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31141216"
---
# <a name="using-fonts-and-colors"></a>Yazı tipleri ve renkler kullanarak
[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Metni görüntülemek için yazı tiplerini ve renkleri kullanmak için destek sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Yazı tipi ve renk genel bakış](../extensibility/font-and-color-overview.md)  
 Metin yazı tipi ve renk ayarları açıklanır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı (IDE). Ayrıca, kategoriler ve öğeleri görüntüleme kavramlar tanıtılır ve VSPackages ve çekirdek düzenleyici metin özniteliklerini kullanımını açıklar.  
  
 [Yazı tipi ve metin renklendirme için renk bilgilerini alma](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Metin renklendirme yönetmek VSPackages içinde uygulamak için kılavuz bilgiler verilmektedir **kategorileri** dışında **metin düzenleyici**.  
  
 [Saklı yazı tipi ve renk ayarlarını erişme](../extensibility/accessing-stored-font-and-color-settings.md)  
 Nasıl geçerli yazı tipi ve renk açıklayan ayarları depolanan, alınan ve uygulanır.  
  
 [Uygulama özel kategoriler ve öğeleri görüntüleme](../extensibility/implementing-custom-categories-and-display-items.md)  
 Tarafından bir pencere oluşturabilir ve kullanmak, kendi temel adımlar açıklanmıştır **öğeleri görüntüle** ve **kategorileri** metin görüntüleme desteklemek için.  
  
 Bu yaklaşımı uygulamak bir VSPackage gerektirir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> ve ilgili arabirim.  
  
 [Nasıl yapılır: yerleşik yazı tipleri ve renk düzenini erişim](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Tanımlamak ve yerleşik yazı tipleri ve renkler kullanarak bir kategori kaydedin ve sistem tarafından sağlanan yazı tiplerini ve renkleri kullanımını başlatmak nasıl ele alınmaktadır.  
  
## <a name="reference"></a>Başvuru  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Bir örneğini sağlar `IVsFontAndColorDefaults` veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> listelenen belirli bir öğeye karşılık gelen arabirim **Settings For Göster** listesinde **yazı tiplerini ve renkleri** sayfasının**Seçenekleri** iletişim kutusu.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 IDE desteklemek bir VSPackage etkinleştirir **yazı tiplerini ve renkleri** varsayılan yazı tipleri ve renkler penceresi veya UI bileşeni için tanımlayarak sayfası.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Bir mekanizma olarak sağlar, yazı tipi ve renk desteği, bir görüntü öğesi grubu - iki veya daha fazla kategoriye birleşimi temsil eden bir üst kategori belirtebilirsiniz sağlayan bir VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Yazı tipi ve renk veri almak veya kayıt defterine kaydetmek bir VSPackage sağlar.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Yazı tipi ve renk ayarlarında değişiklikler hakkında bilgi yazı tipi ve renk kullanmakta VSPackages bildirir.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Yöntemleri tarafından kullanılan giriş ve çıkış verilerle çalışmak için araçlar sağlar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **yazı tipi ve renk** mekanizması.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Önbelleğe alma yazı tipi ve renk ayarlarını denetler.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Eski Dil Hizmeti Geliştirme](../extensibility/internals/developing-a-legacy-language-service.md)  
 VSPackages özelleştirmek için dil hizmetleri nasıl kullanabileceğinizi anlatır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Düzenleyici.  
  
 [Özel Düzenleyicilerde Söz Dizimi Renklendirmesi](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries nasıl [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Düzenleyicisi sözdizimi renklendirmesi uygulamak için dil Hizmetleri kullanır.  
  
 [Visual Studio’nun Diğer Bölümlerini Genişletme](../extensibility/extending-other-parts-of-visual-studio.md)  
 Nasıl kullanılacağı açıklanmaktadır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kalan eşleşen kullanıcı Arabirimi öğeleri oluşturmak için Sertifika Hizmetleri'ni [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].