---
title: Web dağıtımı kullanarak dağıtma
description: Visual Studio Web Dağıtımı'nı kullanarak uygulama dağıtma
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 4ef232e64f308699c73c60cbe5b155f1d4ebb725
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38811928"
---
Web Platformu Yükleyicisi'ni kullanarak Web Dağıtımı'nı yüklediyseniz, doğrudan Visual Studio'dan bir uygulama dağıtabilirsiniz.

1. Visual Studio'yu yönetici ayrıcalıklarıyla başlatın ve projeyi yeniden açın.

    Web dağıtımı kullanarak uygulamanızı dağıtmak için yönetici ayrıcalıkları gerekir.

1. İçinde **Çözüm Gezgini**, proje düğümüne sağ tıklayıp **Yayımla**.

    Tüm yayımlama profilleri, daha önce yapılandırdıysanız **Yayımla** bölmesi görünür. Tıklayın **yeni profili**.

1. İçin **yayımlama hedefi seçin**seçin **IIS, FTP, vb.** tıklatıp **Yayımla**.

    ![RemoteDBG_Publish_IISl](../../debugger/media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

1. Düzeltme yapılandırma parametrelerini IIS ayarlarınızı girin.

    ![RemoteDBG_Publish_WebDeployl](../../debugger/media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Bir ana bilgisayar adı doğrulamak çalıştığınızda çözmezse sonraki adımları **sunucu** metin kutusunda, IP adresi deneyin. Dahil `http://` ön eki olarak **sunucu** alan.  Bağlantı noktası 80 kullandığınızdan emin olun **sunucu** metin kutusu ve bağlantı noktası 80 ve 8172 bağlantı noktası Güvenlik Duvarı'nda açık olduğundan emin olun.

1. Seçin **doğrulama**. Bağlantı kurma doğrulanırsa yayımlamayı deneyebilirsiniz.

1. Tıklayın **Yayımla** uygulama yayımlama.

    Çıktı sekmesi, yayımlama başarılı olduktan ve tarayıcınızı ardından uygulamayı açan gösterir.

    Web dağıtımı bahseden bir hata alırsanız, Web dağıtımı yükleme adımlarını yeniden denetleyin ve doğru bağlantı noktalarının açık olduğundan emin olun (Web dağıtımı da gerektirir bağlantı noktası 8172 sunucuda açık olması için).

    Uygulama başarıyla dağıtılır, ancak düzgün çalışmıyorsa, IIS yapılandırmanızı, ASP.NET yüklemenizi veya Web sitesi yapılandırmanızın bir sorun olabilir. Windows Server'da daha açıklayıcı hata iletileri için IIS Web sitesini açın ve ardından önceki adımlarda'yeniden denetle.
