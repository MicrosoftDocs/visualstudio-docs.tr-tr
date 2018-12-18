---
title: Bir önizleme sürümünü yükle
description: Önizleme sürümleri, önizlemeleri Mac için Visual Studio 2019'dahil olmak üzere Mac için Visual Studio yükseltildikten ve bunlara erişmek için yönergeleri.
zone_pivot_groups: mac-ide-version
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 0E1EF257-9DE4-4653-9DF4-805CE007A1A1
ms.openlocfilehash: b5eea8c2c894b7eeaa13c83ae6698d1297de9297
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896763"
---
# <a name="install-a-preview-release"></a>Bir önizleme sürümünü yükle

::: zone pivot="vsmac2019"

> [!TIP]
> Visual Studio 2019 Mac Önizleme için kullanıma sunulmuştur. İlk kez, Mac için Visual Studio'nun en son kararlı sürüm ile yan yana yüklenebilir

## <a name="requirements-for-the-visual-studio-2019-for-mac-preview"></a>Mac için Visual Studio 2019 gereksinimleri Önizleme

* Mac ile macOS Sierra 10.13 yüksek veya üzeri.

İOS veya Mac OS x için Xamarin uygulamaları oluşturmak için ayrıca gerekir:

* Xcode 10.0 veya üzeri. En son kararlı sürüme genellikle önerilir.
* Bir Apple kimliği Bir Apple kimliği yoksa, yeni bir hesap oluşturabilirsiniz https://appleid.apple.com. Yükleme ve Xcode ile imzalamak için bir Apple Kimliği gereklidir.

## <a name="installing-the-preview"></a>Önizleme Yükleniyor

1. Önizleme Yükleyicisi'nden indirin [Önizleme sayfası Mac için Visual Studio](https://aka.ms/vs4mac-preview).
2. İndirme tamamlandıktan sonra tıklayın **VisualStudioforMacPreviewInstaller.dmg** yükleyici bağlamak için çalıştırın ve ok logosu çift tıklayarak:

    [![Yüklemeye başlamak için büyük oku](media/install-preview-installer-sml.png)](media/install-preview-installer.png#lightbox)

3. Internet'ten yüklenen uygulama hakkında bir uyarı ile sunulan. Tıklayın **açık**.
4. Yükleyicinin sisteminizi denetlerken bekleyin:

    [![Sisteminiz yüklü bileşenleri için yükleyici denetler](media/install-preview-checking-sml.png)](media/install-preview-checking.png#lightbox)

5. Gizlilik ve lisans koşullarını kabul etmek isteyen bir uyarı görüntülenir. Bunları okuyun ve sonra basın için bağlantıları izleyin **devam** kabul ediyorsanız:

    [![Koşulları ve gizlilik için bağlantıları izleyin, sonra kabul etmiyorsanız devam edin](media/install-preview-privacy-sml.png)](media/install-preview-privacy.png#lightbox)

6. Kullanılabilir iş yüklerinin listesi görüntülenir. Kullanmak için istediklerinizi seçin:

    [![İsteğe bağlı bir iş yükü özellikleri yüklemek istediğiniz seçin](media/install-preview-selection-sml.png)](media/install-preview-selection.png#lightbox)

    Geçerli Visual Studio 2017 Mac için 7.7 sürümden daha eski ise, (Bu, yan yana yükleme desteklemek için gerekli olan) en son kararlı sürüme yükseltme onaylamanız istenir. Tuşuna **devam** yükseltmeyi onaylamak için:

    ![Kararlı bir sürüm 7.7 için yükseltme gerekiyor](media/install-preview-older-upgrade.png)

7. Seçimlerinizi yaptıktan sonra basın **yükleme** düğmesi.
8. İndirir ve Mac ve seçilen iş yükleri için Visual Studio'yu yükler yükleyici ilerleme durumunu görüntüler. Yükleme için gerekli ayrıcalıklara vermek için parolanızı girmeniz istenebilir.
9. Kullanım **Visual Studio (Önizleme)** Önizleme sürümü test edebilir veya en son sürüme geçiş yapmak istediğiniz zaman üretim çalışmanız için Visual Studio kararlı. İki simgeyi burada gösterilir:

    ![Kararlı ve önizleme simgesinin farklılıklar](media/install-preview-icons-sml.png)

Bir Kurumsal ortamda yüklenirken ağ bulmakta güçlük çekiyorsanız, gözden [bir güvenlik duvarı veya proxy yüklemeye](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server) yönergeleri.

Değişiklikleri hakkında daha fazla bilgi [sürüm notları](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-preview-relnotes).

::: zone-end
::: zone pivot="vsmac2017"

## <a name="install-an-update-for-visual-studio-2017-for-mac"></a>Mac için Visual Studio 2017 için bir güncelleştirmeyi yüklemek

Mac için Visual Studio'nun yeni bir sürüm resmi olarak yayımlanmadan önce önizleme olarak kullanılabilir. Önizleme sürümü, yeni özellikleri denemek ve tam olarak bir üründe dahil önce en son hata düzeltmeleri almak için bir fırsat sağlar.

Mac için Visual Studio Preview sürümlerinde, bir güncelleştirme olarak yerine ayrı bir indirme aracılığıyla dağıtılır. Mac için Visual Studio sahip üç güncelleştirici kanalları açıklandığı [güncelleştirme](update.md) makale: kararlı, Beta ve alfa.

Çoğu Önizleme sürümleri hem de kullanılabilir olacak **Beta** ve **alfa** Kanallar, ancak her zaman denetleyin [Preview sürüm notları](/visualstudio/releasenotes/vs2017-mac-preview-relnotes) en doğru bilgi.

Mac için Visual Studio'nun Önizleme yüklemek için aşağıdaki adımları kullanın:

1. Git **Visual Studio > Güncelleştirmeleri denetle**.
2. Güncelleştirme kanalı birleşik giriş kutusunda seçin **Beta**.
3. Seçin **anahtar kanal** seçili kanala geçin ve yeni bir güncelleştirme yüklemeyi Başlat düğmesi.
4. Seçin **yeniden başlat ve güncelleştirmeleri yükle** güncelleştirmeleri yüklemeye başlamak için düğme.

Mac için Visual Studio güncelleştirme hakkında daha fazla bilgi için bkz. [güncelleştirme](update.md) makalesi.

::: zone-end