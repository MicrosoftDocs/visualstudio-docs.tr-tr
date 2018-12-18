---
title: Yerel Yardım belgeleri yükleyin
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- hv_manage
helpviewer_keywords:
- changing content installation source [Help Viewer]
- updating local content [Help Viewer]
- Help Viewer, content installation source
- Help Viewer, updating local content
- Help Viewer, changing content installation source
- installing local content [Help Viewer]
- content installation source [Help Viewer]
- downloading content [Help Viewer]
- removing local content [Help Viewer]
- Help Viewer, removing local content
- Help Viewer, installing local content
- Help Viewer, downloading content
ms.assetid: efd9df4c-2e69-4c50-992c-9678a8d8cf19
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fab06fee0dadd28d6b8feb793d29fb1e22e0b00b
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53378139"
---
# <a name="install-and-manage-local-content"></a>Yerel içeriği yükleme ve yönetme

Microsoft Yardım Görüntüleyicisi'ni kullanarak, ekleme, kaldırma, güncelleştirme ve yazılım geliştirme ihtiyaçlarınıza uygun şekilde bilgisayarınızda yüklü olan Yardım içeriğini taşımak.

Yerel bilgisayarınızdaki içeriği yönetmek için yönetici izinlerine sahip bir hesapla oturum açmalısınız. Ayrıca, bir Kurumsal ortamda çalışıyorsanız, sistem yöneticileri bu kararları kuruluşunuz için yapabileceğiniz çünkü yerel içeriği yönetmek mümkün olmayabilir. Daha fazla bilgi için [Yardım Görüntüleyicisi Yönetici Kılavuzu](../help-viewer/administrator-guide.md).

## <a name="change-the-content-installation-source"></a>İçerik yükleme kaynağını değiştirme

Varsayılan olarak, Yardım Görüntüleyici, içerik kaynak olarak bir Microsoft online service kullanarak yükler. Kendisi için bir sistem yöneticisinin içeriği başka bir konumda yüklü bir Kurumsal ortamda çalışmıyorsanız genellikle içerik kaynağını değiştirmeniz gerekmez.

### <a name="to-change-the-content-installation-source"></a>İçerik yükleme kaynağını değiştirmek için

1.  Üzerinde **içeriği Yönet** sekmesini, **Disk** seçenek düğmesini.

    > [!NOTE]
    > **Disk** seçenek yöneticinize, içerik yükleme kaynağını değiştirmenizi engellerse kullanılabilir değildir. Daha fazla bilgi için [Yardım Görüntüleyicisi Yönetici Kılavuzu](../help-viewer/administrator-guide.md).

2.  Aşağıdaki adımlardan birini uygulayın:

    -   Yolunu girin bir *.msha* dosya veya bir hizmet uç noktasının URL'si.

    -   Gözat düğmesini seçin (**...** ) düğmesine gitmek için bir *.msha* dosya.

    -   Listeden en son kullanılan girdiyi seçin.

## <a name="download-and-install-content-locally"></a>Yerel olarak içeriği indir ve yükle

İndirme ve içeriği yerel bilgisayarınıza yükleyin, internet bağlantısı olmadığında konuları görüntüleyebilirsiniz.

> [!IMPORTANT]
> İçeriği yüklemek için yönetici izinleri olan bir hesapla oturum açmalısınız.

> [!NOTE]
> Visual Studio IDE İngilizce dışında bir dile ayarlanmışsa İngilizce içeriği, yerelleştirilmiş içeriği veya her ikisini de yükleyebilirsiniz. Yalnızca İngilizce sürümü yüklerseniz, ancak içerik görünür ve **İngilizceyi dahil et içerik tüm gezinme sekmelerine ve F1 isteklerine dahil** onay kutusuna **Görüntüleyici seçenekleri** iletişim kutusu temizlenir.

### <a name="to-download-and-install-content"></a>İçeriği indirmek ve yüklemek için

1.  Seçin **içeriği Yönet** sekmesi.

2.  İçerik listesinde **Ekle** kitabın veya kitapların indirmek ve yüklemek için istediğiniz yanındaki bağlantı.

     Kitap eklenir **bekleyen değişiklikler** listesi ve tahmini boyutunu belirttiğiniz kitap veya kitaplar bu listenin altında görünür. Bazı kitaplar konuları paylaştığından birden çok kitap toplam yükleme boyutu, belirttiğiniz her kitabın boyutlarını birlikte eklemenin sonucunu küçük olabilir.

3.  Seçin **güncelleştirme** düğmesi.

     Belirttiğiniz kitap veya kitaplar, bilgisayarınızda zaten yüklü Kitaplar için tüm güncelleştirmelerle birlikte yüklenir. Yükleme süreleri değişebilir ancak durum çubuğundan ilerlemeyi görüntüleyebilirsiniz.

## <a name="remove-local-content"></a>Yerel içeriği kaldırma

İstenmeyen içeriği bilgisayarınızdan kaldırarak disk alanından kazanabilirsiniz.

> [!IMPORTANT]
> İçeriği kaldırmak için yönetici izinleri olmalıdır.

> [!NOTE]
> İçerik, Visual Studio IDE İngilizce dışında bir dile ayarlanırsa, yerelleştirilmiş içeriği kaldırmak görünür ve **İngilizceyi dahil et içerik tüm gezinme sekmesindeki ve F1 isteklerine dahil** onay kutusuna **Görüntüleyiciseçenekleri** iletişim kutusu temizlenir.

### <a name="to-remove-content"></a>İçeriği kaldırmak için

1.  Seçin **içeriği Yönet** sekmesi.

2.  İçerik listesinde **Kaldır** kitabın veya kitapların kaldırmak istediğiniz yanındaki bağlantı.

     Kitap eklenir **bekleyen değişiklikler** listesi.

3.  Seçin **güncelleştirme** düğmesi.

     Belirttiğiniz kitap veya kitaplar bilgisayarınızdan kaldırılır.

## <a name="update-local-content"></a>Yerel içeriği güncelleştirme

Durum çubuğu yüklü içeriğinizle güncelleştirmelerinin ne zaman kullanılabilir olduğunu gösterir.

> [!IMPORTANT]
> İsterseniz **Yardım Görüntüleyici** çevrimiçi güncelleştirmeleri otomatik olarak denetlemek için açmalısınız **Görüntüleyici seçenekleri** iletişim kutusunu ve ardından **içerikgüncelleştirmelerinidenetlemekiçinçevrimiçiol**onay kutusu.

### <a name="to-update-local-content"></a>Yerel içeriği güncelleştirmek için

- Durum çubuğunun sağ alt köşesinde seçin **şimdi indirmek için buraya tıklayın** bağlantı.

Güncelleştirme süreleri değişebilir ancak durum çubuğunda güncelleştirme ilerleme durumunu görüntüleyebilirsiniz.

## <a name="move-local-content"></a>Yerel içeriği taşıma

Yüklü içeriği yerel bilgisayarınızdan bir ağ paylaşımına veya başka bir bölüme, yerel bilgisayarınızda taşıyarak disk alanından kazanabilirsiniz.

> [!IMPORTANT]
> İçeriği taşımak için yönetici izinleri olan bir hesapla oturum açmalısınız.

### <a name="to-move-local-content"></a>Yerel içeriği taşımak için

1.  Üzerinde **içeriği Yönet** sekmesini, **taşıma** düğmesini **yerel Store yol**.

     **İçeriği Taşı** iletişim kutusu açılır.

2.  İçinde **için** metin kutusuna içerik için farklı bir konum girin ve ardından **Tamam** düğmesi.

3.  Seçin **Kapat** içerik taşındıktan sonra düğme.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Yardım Görüntüleyicisi](../help-viewer/overview.md)