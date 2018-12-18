---
title: Yerel içeriği yükleme ve yönetme | Microsoft Docs
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
- hv_manage
helpviewer_keywords:
- changing content installation source [Help Viewer 2.0]
- updating local content [Help Viewer 2.0]
- Help Viewer 2.0, content installation source
- Help Viewer 2.0, updating local content
- Help Viewer 2.0, changing content installation source
- installing local content [Help Viewer 2.0]
- content installation source [Help Viewer 2.0]
- downloading content [Help Viewer 2.0]
- removing local content [Help Viewer 2.0]
- Help Viewer 2.0, removing local content
- Help Viewer 2.0, installing local content
- Help Viewer 2.0, downloading content
ms.assetid: efd9df4c-2e69-4c50-992c-9678a8d8cf19
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7b8a67a9105314ad73076d3a8b12d51c23f83097
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832738"
---
# <a name="install-and-manage-local-content"></a>Yerel İçeriği Yükleme ve Yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft Yardım Görüntüleyicisi'ni kullanarak, ekleme, kaldırma, güncelleştirme ve yazılım geliştirme ihtiyaçlarınıza uygun şekilde bilgisayarınızda yüklü olan Yardım içeriğini taşımak.  
  
 Yerel bilgisayarınızdaki içeriği yönetmek için yönetici izinleri olan bir hesapla oturum açmalısınız. Ayrıca, sistem yöneticileri bu kararları kuruluşunuz için yapabileceğiniz çünkü bir Kurumsal ortamda çalışıyorsanız, yerel içeriği yönetmek mümkün olmayabilir. Daha fazla bilgi için [Yardım Görüntüleyicisi Yönetici Kılavuzu'na](../ide/help-viewer-administrator-guide.md).  
  
## <a name="changing-the-content-installation-source"></a>İçerik yükleme kaynağını değiştirme  
 Varsayılan olarak, Yardım Görüntüleyici, içerik kaynak olarak bir Microsoft online service kullanarak yükler. Kendisi için bir sistem yöneticisinin içeriği başka bir konumda yüklü bir Kurumsal ortamda çalışmıyorsanız genellikle içerik kaynağını değiştirmeniz gerekmez.  
  
#### <a name="to-change-the-content-installation-source"></a>İçerik yükleme kaynağını değiştirmek için  
  
1.  Üzerinde **içeriği Yönet** sekmesini, **Disk** seçenek düğmesini.  
  
    > [!NOTE]
    >  **Disk** seçeneği yöneticinize, içerik yükleme kaynağını değiştirmenizi engellerse kullanılabilir olmayacak. Daha fazla bilgi için [Yardım Görüntüleyicisi Yönetici Kılavuzu'na](../ide/help-viewer-administrator-guide.md).  
  
2.  Aşağıdaki adımlardan birini uygulayın:  
  
    -   .Msha dosya yolunu veya hizmet uç noktası URL'sini girin.  
  
    -   Gözat düğmesini seçin (**...** ) .msha dosyasına gitmek için düğme.  
  
    -   Listeden en son kullanılan girdiyi seçin.  
  
## <a name="download-and-install-content-locally"></a>Yerel olarak içeriği indir ve yükle  
 İndirme ve içeriği yerel bilgisayarınıza yükleyin, Internet bağlantısı olmadan konuları görüntüleyebilirsiniz.  
  
> [!IMPORTANT]
>  İçeriği yüklemek için yönetici izinleri olan bir hesapla oturum açmalısınız.  
  
 Visual Studio IDE İngilizce dışında bir dile ayarlanmışsa İngilizce içeriği, yerelleştirilmiş içeriği veya her ikisini de yükleyebilirsiniz. Ancak, içerik yalnızca İngilizce sürümü yüklerseniz görünür ve **İngilizceyi dahil et içerik tüm gezinme sekmelerine ve F1 isteklerine dahil** onay kutusuna **Görüntüleyici seçenekleri** iletişim kutusu temizlenir.  
  
#### <a name="to-download-and-install-content"></a>İçeriği indirmek ve yüklemek için  
  
1.  Seçin **içeriği Yönet** sekmesi.  
  
2.  İçerik listesinde **Ekle** kitabın veya kitapların indirmek ve yüklemek için istediğiniz yanındaki bağlantı.  
  
     Kitap eklenir **bekleyen değişiklikler** listesi ve tahmini boyutunu belirttiğiniz kitap veya kitaplar bu listenin altında görünür. Bazı kitaplar konuları paylaştığından birden çok kitap toplam yükleme boyutu, belirttiğiniz her kitabın boyutlarını birlikte eklemenin sonucunu küçük olabilir.  
  
3.  Seçin **güncelleştirme** düğmesi.  
  
     Belirttiğiniz kitap veya kitaplar, bilgisayarınızda zaten yüklü Kitaplar için tüm güncelleştirmelerle birlikte yüklenir. Yükleme süreleri değişebilir ancak durum çubuğundan ilerlemeyi görüntüleyebilirsiniz.  
  
## <a name="removing-local-content"></a>Yerel içeriği kaldırma  
 İstenmeyen içeriği bilgisayarınızdan kaldırarak disk alanından kazanabilirsiniz.  
  
> [!IMPORTANT]
>  İçeriği kaldırmak için yönetici izinleri olmalıdır.  
  
 İçerik, Visual Studio IDE İngilizce dışında bir dile ayarlanırsa, yerelleştirilmiş içeriği kaldırmak görünür ve **İngilizceyi dahil et içerik tüm gezinme sekmesindeki ve F1 isteklerine dahil** onay kutusuna **Görüntüleyici seçenekleri**  iletişim kutusu temizlenir.  
  
#### <a name="to-remove-content"></a>İçeriği kaldırmak için  
  
1.  Seçin **içeriği Yönet** sekmesi.  
  
2.  İçerik listesinde **Kaldır** kitabın veya kitapların kaldırmak istediğiniz yanındaki bağlantı.  
  
     Kitap eklenir **bekleyen değişiklikler** listesi.  
  
3.  Seçin **güncelleştirme** düğmesi.  
  
     Belirttiğiniz kitap veya kitaplar bilgisayarınızdan kaldırılır.  
  
## <a name="updating-local-content"></a>Yerel içeriği güncelleştirme  
 Durum çubuğu yüklü içeriğinizle güncelleştirmelerinin ne zaman kullanılabilir olduğunu gösterir.  
  
> [!IMPORTANT]
>  Çevrimiçi güncelleştirmeleri otomatik olarak denetlemek için Yardım Görüntüleyicisi istiyorsanız açmalısınız **Görüntüleyici seçenekleri** iletişim kutusunu ve ardından **içerik güncelleştirmelerini denetlemek için çevrimiçi ol** onay kutusu.  
  
#### <a name="to-update-local-content"></a>Yerel içeriği güncelleştirmek için  
  
- Durum çubuğunun sağ alt köşesinde seçin **şimdi indirmek için buraya tıklayın** bağlantı.  
  
  Güncelleştirme süreleri değişebilir ancak durum çubuğunda güncelleştirme ilerleme durumunu görüntüleyebilirsiniz.  
  
## <a name="moving-local-content"></a>Yerel içeriği taşıma  
 Yüklü içeriği yerel bilgisayarınızdan bir ağ paylaşımına veya başka bir bölüme, yerel bilgisayarınızda taşıyarak disk alanından kazanabilirsiniz.  
  
> [!IMPORTANT]
>  İçeriği taşımak için yönetici izinleri olan bir hesapla oturum açmalısınız.  
  
#### <a name="to-move-local-content"></a>Yerel içeriği taşımak için  
  
1.  Üzerinde **içeriği Yönet** sekmesini, **taşıma** düğmesini **yerel Store yol**.  
  
     **İçeriği Taşı** iletişim kutusu açılır.  
  
2.  İçinde **için** metin kutusuna içerik için farklı bir konum girin ve ardından **Tamam** düğmesi.  
  
3.  Seçin **Kapat** içerik taşındıktan sonra düğme.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Microsoft Yardım Görüntüleyicisi](../ide/microsoft-help-viewer.md)



