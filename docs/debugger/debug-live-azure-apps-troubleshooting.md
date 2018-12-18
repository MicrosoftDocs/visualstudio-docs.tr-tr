---
title: Anlık görüntü hata ayıklama sorunlarını giderme | Microsoft Docs
ms.custom: seodec18
ms.date: 11/07/2017
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 82d8a310b86d5dc3c776243293a91f176025f897
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059833"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Visual Studio'da anlık görüntü hata ayıklama için sorun giderme ve bilinen sorunlar

Bu makalede açıklanan adımlar sorunu çözmezse, kişi snaphelp@microsoft.com.

## <a name="issue-snappoint-does-not-turn-on"></a>Sorun: Anlık görüntü noktası açılmıyor

Bir uyarı simgesi görürseniz ![anlık görüntü noktası uyarı simgesi](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "anlık görüntü noktası uyarı simgesi") , anlık görüntü noktası ile yerine normal bir anlık görüntü noktası simgesi, sonra anlık görüntü noktası açık değil.

![Anlık görüntü noktası olmayan açma](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "anlık görüntü noktası olmayan Aç")

Aşağıdaki adımları gerçekleştirin:

1. Derleme ve dağıtma, app.isua1 için kullanılan kaynak kodu aynı sürümüne sahip olduğunuzdan emin olun. Dağıtımınız için doğru semboller yükleniyor emin olun. Bunu yapmak için görüntüleme **modülleri** penceresi açıkken anlık görüntü hata ayıklama ve sembol dosyası sütun .pdb dosyasını ayıkladığınız modül için yüklenmiş görüntülendiğini doğrulama. Snapshot Debugger otomatik olarak indirmeyi ve dağıtımınız için semboller kullanın dener.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Sorun: bir anlık görüntü açtığımda sembolleri yüklenmiyor

Pencere görürseniz, semboller yüklenmedi.

![Sembolleri yükleme](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "sembolleri yükleme")

Aşağıdaki adımları gerçekleştirin:

- Tıklayın **sembol ayarlarını değiştir...** Bu sayfada bağlayın. İçinde **hata ayıklama > Sembol** ayarları, sembol önbellek dizini ekleyin. Sembol yolu ayarladıktan sonra anlık görüntü hata ayıklamayı yeniden başlatın.

   App Service dağıtımınızda simgeleri veya .pdb dosyaları, projenizde kullanılabilen eşleşmelidir. Çoğu dağıtım (Visual Studio, Kudu, ya da Azure işlem hatları ile CI/CD ile dağıtım vb.) sembol dosyalarınızı boyunca uygulama hizmetinize yayımlar. Sembol önbellek dizini ayarlamak, bu sembolleri kullanmak Visual Studio sağlar.

   ![Sembol ayarları](../debugger/media/snapshot-troubleshooting-symbol-settings.png "sembol ayarları")

- Kuruluşunuz bir sembol sunucusu kullanıyorsa ya da farklı bir yolda sembolleri bıraktığı alternatif olarak, dağıtımınız için doğru sembolleri yüklemek üzere sembol Ayarları'nı kullanın.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Sorun: "Snapshot Debugger Ekle" seçeneğini bulut Gezgini'nde göremiyorum

Aşağıdaki adımları gerçekleştirin:

- Anlık görüntü hata ayıklayıcı bileşeni yüklü olduğundan emin olun. Visual Studio Yükleyicisi'ni açın ve kontrol **Snapshot Debugger** Azure iş yükü bileşeni.
- Uygulamanızın desteklenen emin olun. Şu anda, yalnızca ASP.NET (4.6.1+) ve ASP.NET Core (2.0 +) uygulamalarını Azure App Services'a dağıtılmış desteklenir.

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Sorun: yalnızca tanılama araçları kısıtlanmış anlık görüntü görüyorum

![Kısıtlı anlık görüntü noktası](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "kısıtlanmış anlık görüntü noktası")

Aşağıdaki adımları gerçekleştirin:

- Anlık görüntüleri küçük bellek alanı dolduracaktır, ancak bir işleme ücrete tabi. Snapshot Debugger, yoğun bellek yükü altında sunucunuzdur algılarsa, anlık görüntüler olmayacaktır. Snapshot Debugger oturumu durdurma ve yeniden deneyerek zaten yakalanan anlık görüntülerini silebilirsiniz.

## <a name="known-issues"></a>Bilinen Sorunlar

- Aynı App Service karşı birden fazla Visual Studio istemcilerle anlık görüntü hata ayıklama şu anda desteklenmiyor.
- Roslyn IL en iyi duruma getirme, tam olarak ASP.NET Core projelerinde desteklenmez. Bazı ASP.NET Core projeleri için bkz. bazı değişkenleri veya bazı değişkenler koşullu Deyimlerinizde kullanın mümkün olmayabilir. 
- Özel değişkenler gibi *$FUNCTION* veya *$CALLER*, günlüğe kaydetme noktaları ASP.NET Core projeleri için de koşullu ifadeler değerlendirilemez.
- Anlık görüntü hata ayıklama sahip uygulama hizmetleri çalışmıyor [yerel önbelleğe alma](/azure/app-service/app-service-local-cache) açık.
- API Apps hata ayıklama anlık görüntü şu anda desteklenmiyor.

## <a name="site-extension-upgrade"></a>Site uzantısı yükseltme

Anlık görüntü hata ayıklama ve Application Insights site işleme yükler ve dosya kilitleme sorunları yükseltme sırasında neden olan bir ICorProfiler bağlıdır. Üretim sitenizi hiç kapalı kalma süresini olduğundan emin olmak için bu işlemi öneririz.

- Oluşturma bir [dağıtım yuvası](/azure/app-service/web-sites-staged-publishing) , App Service içinde ve sitenizi yuvaya dağıtın.
- Visual Studio'daki bulut Gezgini'nde veya Azure portalından üretim yuvasıyla takas.
- Yuva sitesini durdurun. Bu site w3wp.exe işlemi kaldırılarak devre dışı sonlandırmak için birkaç saniye sürer.
- Yuva site uzantısı Kudu sitesi veya Azure portalından yükseltme (*App Service dikey penceresi > Geliştirme araçları > uzantılar > güncelleştirme*).
- Yuva sitesini başlatın. Yeniden Isınma sitesinden öneririz.
- Üretim yuvasıyla takas etme.

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio’da hata ayıklama](../debugger/index.md)  
[Snapshot Debugger'ı kullanarak canlı ASP.NET uygulamalarının hatalarını ayıklama](../debugger/debug-live-azure-applications.md)  
[Anlık görüntü hatalarını ayıklama hakkında SSS](../debugger/debug-live-azure-apps-faq.md)  
