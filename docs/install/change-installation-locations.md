---
title: Yükleme konumlarını seçme
description: Sistem sürücünüzdeki yükleme ayak izini Visual Studio'nun konumunu indirme önbelleğini, paylaşılan bileşenler, SDK'ları ve araçları farklı sürücülere değiştirerek azaltmak öğrenin.
ms.date: 11/07/2018
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2acefee22976e061b3feff83b00891037a0f2bbd
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159847"
---
# <a name="select-the-installation-locations-in-visual-studio-2017"></a>Visual Studio 2017'de yükleme konumları seçin

**15.7 sürümündeki yeni**: Bazı dosyalar için konumun değiştirerek sistem sürücünüzde Visual Studio yükleme ayak izini azaltabilir. Özellikle, indirme önbelleğini, paylaşılan bileşenler, SDK'lar ve Araçlar dosyaları için farklı bir konum kullanabilirsiniz.

   > [!NOTE]
   > Bazı araçlar ve bunlar yüklenebileceği ile ilgili farklı kurallara sahip bir SDK'ları vardır. Başka bir konum seçin bile gibi araçları ve SDK'lar sistem sürücünüzde yüklenir.

Başlamaya hazır mısınız? İşte nasıl.

1. Visual Studio'yu yüklediğinizde seçin **yükleme konumlarını** sekmesi.

   ![Visual Studio 2017 - yükleme konumu seçin](media/vs-installation-locations.png "yükleme konumunu seçin.")

1. İçinde **Visual Studio IDE** bölümünde, varsayılanı kabul edin. Visual Studio temel ürünü yükler ve Visual Studio'nun bu sürümüne özgü dosyaları içerir.

   ![Yükleme konumlarını sekmesinde Visual Studio IDE bölümünü](media/vs-installation-locations-ide.png "yüklemeleri Konum sekmesini Visual Studio IDE bölümü için varsayılan değeri kabul edin.")

   > [!TIP]
   > Sistem sürücünüzdeki bir katı hal sürücüsü (SSD) ise, sistem sürücünüzde varsayılan konumu kabul etmenizi öneririz. Nedeni nedir? Visual Studio ile geliştirme yaptığınızda, okuma ve disk g/ç etkinliği artıran çok sayıda dosya, için yazma. Yükü işlemek için hızlı sürücünüze seçmek idealdir.

1. İçinde **indirme önbelleğini** bölümünde, indirme önbelleğini Tut ve kendi dosyalarını depolamak istediğiniz yere karar istediğinize karar verin.

     ![İndirme yükleme konumlarını sekmesinin önbellek bölümündeki](media/vs-installation-locations-cache.png "isteyip istemediğinizi belirleyin yüklemeden sonra indirme önbelleğini Tut ve ardından dosyaları depolamak istediğiniz sürücüyü belirtin.")

    1. İşaretleyin veya işaretini kaldırın **yüklemeden sonra indirme önbelleğini tut**.

       İndirme önbelleğini tutmamaya karar verirseniz, konum yalnızca geçici olarak kullanılır. Bu eylem kalmaz etkileyebilir veya önceki yüklemelerinden dosyaları silin.

    1. Yükleme dosyaları ve indirme önbelleğini bildirimlerinden depolamak istediğiniz sürücüyü belirtin.

        "C++ ile masaüstü geliştirme" iş yükünü seçin, örneğin, geçici olarak gereken boyut 1.58 yüklemesi tamamlandıktan hemen sonra serbest bırakılır sistem sürücüsünde GB'dir.

       > [!IMPORTANT]
       > Bu konum, ilk yükleme ile ayarlanır ve yükleyicisi kullanıcı arabirimini daha sonra değiştirilemez. Bunun yerine, şunları yapmalısınız [komut satırı parametrelerini](use-command-line-parameters-to-install-visual-studio.md) indirme önbelleğini taşınır.

1. İçinde **paylaşılan bileşenler, Araçlar ve SDK'lar** bölümünde, yan yana Visual Studio yüklemeleri tarafından paylaşılan dosyaları depolamak istediğiniz sürücüyü belirtin. SDK'lar ve araçlar da bu dizinde depolanır.

   ![Paylaşılan bileşenler, Araçlar ve SDK'lar bölümü yükleme konumlarını sekmesinin](media/vs-installation-locations-shared.png "paylaşılan bileşenler, Araçlar ve SDK'lar depolamak istediğiniz konumu belirtin.")

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 2017'yi Yükleme](install-visual-studio.md)
* [Visual Studio 2017 güncelleştirmesi](update-visual-studio.md)
* [Visual Studio 2017'yi Değiştirme](update-visual-studio.md)
* [Visual Studio 2017'yi kaldırın](uninstall-visual-studio.md)
