---
title: Dosyalar ve klasörler için ayarları güven
description: Visual Studio güvenli tutmak için dosyalar ve klasörler için güven ayarlarını değiştirmeyi öğrenin.
author: abuchholtzau
ms.author: allisb
ms.date: 09/05/2018
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
f1_keywords:
- VS.ToolsOptionsPages.Environment.PathTrustOptions
helpviewer_keywords:
- file security
- folder security
- mark of the web
- trusted files
- trusted folders
ms.openlocfilehash: 08c4b08c33cd954aa427f158158f29cfbe50df94
ms.sourcegitcommit: 4708f0ba09b540424efcc344f8438f25432e3d51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44384690"
---
# <a name="configure-trust-settings-for-files-and-folders"></a>Dosyalar ve klasörler için güven ayarlarını yapılandırma

Visual Studio ister projeleri açmadan önce kullanıcı onayı [web işareti](/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537628(v=vs.85)). Ek güvenlik için Visual Studio'nun herhangi bir dosya veya web öznitelik işareti olan veya bu değilse atanmış olarak klasör açmadan önce kullanıcının onayını iste de yapılandırabilirsiniz *güvenilen*. Dosya ve klasör denetimleri, varsayılan olarak devre dışıdır.

> [!WARNING]
> Yine de, dosya, klasör veya çözüm güvenilir bir kişi veya güvenilen bir konumdan onaylamadan önce geldiğinden emin olun.

## <a name="configure-trust-settings"></a>Güven ayarlarını yapılandırma

Güven ayarlarını değiştirmek için aşağıdaki adımları izleyin:

1. Açık **Araçları** > **seçenekleri** > **güven ayarları** seçip **güven ayarlarını yapılandır** bağlayın sağ bölme.

2. Dosya ve klasörler için istediğiniz denetimleri düzeyini seçin. Her biri için farklı denetimleri olabilir. Seçenekler şunlardır:

   * **Hiçbir doğrulama**: Visual Studio değil tüm denetimleri gerçekleştirin.

   * **Web özniteliğinin işareti doğrulayın**: dosya veya klasörün web öznitelik işareti varsa, Visual Studio engeller ve açmak için izin ister.

   * **Yol güvenilir olduğundan emin olun**: dosya veya klasör yolu parçası değilse **güvenilen yolları** listesi, Visual Studio engeller ve açmak için izin ister.

   ![Güven doğrulama seçenekleri](media/trust-settings.png)

## <a name="add-trusted-paths"></a>Güvenilir yollarını ekleyin

Güvenilir yollarını eklemek için aşağıdaki adımları izleyin:

1. Açık **Araçları** > **seçenekleri** > **güven ayarları** seçip **güven ayarlarını yapılandır** bağlayın sağ bölme.

2. Tıklayın **Ekle** içinde **güven ayarları** iletişim tıklayın ve ardından **dosya** veya **klasör**.

3. Gidin ve dosyayı veya güvenilir listeye eklemek istediğiniz klasörü seçin.

   Dosya veya klasör yolu görünür **güvenilen yolları** listesi.

   ![Güvenilen yolları eklendi](media/trusted-paths.png)

## <a name="remove-trusted-paths"></a>Güvenilen yolları Kaldır

Güvenilir yollarını kaldırmak için aşağıdaki adımları izleyin:

1. Açık **Araçları** > **seçenekleri** > **güven ayarları** seçip **güven ayarlarını yapılandır** bağlayın sağ bölme.

2. Kaldırmak istediğiniz yolu seçin **güvenilen yolları** listeleyin ve ardından **Kaldır**.

   > [!TIP]
   > Birden çok girişi seçmek için basılı **Shift** yolları seçerken.

   Seçilen yollar çıkarılır **güvenilen yolları** listesi.
