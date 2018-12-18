---
title: Yazı tipi ve metin renklendirmesi için renk bilgisi alma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1b9d5aa4c3f649f7be44db2e18f67884acd23201
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370672"
---
# <a name="get-font-and-color-information-for-text-colorization"></a>Metin renklendirmesi yazı tipi ve renk bilgilerini al
İşler veya kullanıcı arabirimi (UI) öğeleri renklendirildi metni görüntüler işlem, proje, teknoloji ve geliştirici tercihleri türüne bağlıdır. **Yazı tipleri ve renkler** özellik sayfası ayarları depolar.

 Renklendirilmiş metnini uygulamalarının çoğu gereksinim <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> ve arabirimleri sunma, almaya ve metin depolama ayarlarını görüntülemek için ilişkili.

> [!NOTE]
>  Çekirdek Düzenleyici özelleştirirken (destekleyen **metin EditorCategory**), renklendirme teknoloji dil hizmeti kullanmanız önerilir. Daha fazla bilgi için [yazı tipi ve renk genel bakış](../extensibility/font-and-color-overview.md).

## <a name="get-default-font-and-color-information"></a>Varsayılan yazı tipi ve renk bilgilerini al
 Tüm **yazı tipleri ve renkler** metin görüntüleme herhangi bir pencerenin ayarları belirtilmelidir **görünen öğeler** birinin **kategori**. Daha fazla bilgi için [yazı tipleri ve renkler, ortam, Seçenekler iletişim kutusu](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).

VSPackage renklendirmeye geçerli edinmeniz gerekir **yazı tipleri ve renkler** ayarları. VSPackage geçerli ayarlarını kendi gereksinimlerinize bağlı olarak aşağıdaki yollarla elde edebilirsiniz:

-   Yazı tipi ve renk Kalıcılık mekanizması depolanmış veya geçerli durumunu almak için kullanın. Daha fazla bilgi için [erişim depolanan yazı tipi ve renk ayarlarını](../extensibility/accessing-stored-font-and-color-settings.md).

-   Kullanım <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> örneğini almak için yazı tipi ve renk veri sağlayan bir hizmet arabiriminin <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, VSPackage'ı da yazı tipini ve rengini sağlayıcısı değil.

-   Uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> arabirimi.

Emin olmak için yoklama işlemi tarafından elde edilen sonucu güncel olan, kullanılacak yararlı olabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> alma yöntemleri çağrılmadan önce bir güncelleştirme gerekip gerekmediğini belirlemek için arabirimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> arabirimi.

Yazı tipi ve renk bilgilerini sonra aldıysanız, renklendirme gerektiren öğeleri tanımlamak için görüntülenecek metni ayrıştırın. Metin uygun yazı tipleri ve renkler kullanarak pencerede görüntülemektir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- [Kullanım yazı tipleri ve metin](/dotnet/framework/winforms/advanced/using-fonts-and-text)
- [Renklerle çalışma](/cpp/windows/working-with-color-image-editor-for-icons)
- [GDI (grafik cihaz arabirimi)](https://msdn.microsoft.com/library/7e1d4540-bb2e-4257-8eee-eee376acba83)