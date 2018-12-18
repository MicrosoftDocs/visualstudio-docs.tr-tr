---
title: Unity için Araçlar Mac için Visual Studio Kurulumu
description: Ayarlama ve kullanmak için Unity araçları, Mac için Visual Studio yükleme
author: therealjohn
ms.author: johmil
ms.date: 05/25/2018
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: 9a661e3cae151e4d6199fd2a588ebd62e098de6c
ms.sourcegitcommit: 5c049194fa256b876ad303f491af11edd505756c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53027334"
---
# <a name="set-up-visual-studio-for-mac-tools-for-unity"></a>Unity için Mac araçları için Visual Studio'yu ayarlama

Bu bölümde, Visual Studio için Unity için Mac araçları ile çalışmaya başlamak açıklanmaktadır.

## <a name="install-visual-studio-for-mac"></a>Mac için Visual Studio'yu yükleyin

### <a name="unity-bundled-installation"></a>Unity paket yükleme

Unity 2018.1 ile başlayarak, Mac için Visual Studio varsayılan değer C# Unity için tümleşik geliştirme ortamı (IDE) ve Unity indirme Yardımcısı'nın yanı sıra Unity hub'ı yükleme aracı dahil edilir. [store.unity.com](https://store.unity.com/) adresinden Unity'yi indirin.

Yükleme sırasında Mac için Visual Studio ile Unity yüklenecek bileşenlerin listesini işaretlendiğinden emin olun:

#### <a name="unity-hub"></a>Unity Hub

![Unity hub'ı yükleme](media/setup-vsmac-tools-unity-image7.png)

#### <a name="unity-download-assistant"></a>Unity Yükleme Yardımcısı

![Unity Yükleme Yardımcısı'nı yükleme](media/setup-vsmac-tools-unity-image8.png)

#### <a name="check-for-updates-to-visual-studio-for-mac"></a>Mac için Visual Studio Güncelleştirmeleri denetle

Unity yükleme işlemine dahil Mac için Visual Studio sürümü, en son olmayabilir. En son araçlara ve özelliklere erişiminiz olduğundan emin olmak için güncelleştirmeleri denetlemeniz önerilir.

* [Mac için Visual Studio güncelleştiriliyor](update.md)

### <a name="manual-installation"></a>El ile yükleme

Unity 5.6.1 zaten varsa veya yukarıdaki ancak Mac için Visual Studio yüklü, Mac için Visual Studio el ile yükleyebilirsiniz. Mac için Visual Studio'nun tüm sürümlerinde Visual Studio ile ücretsiz Community sürümü dahil olmak üzere, Unity için Mac araçları paketlendi:

* Mac için Visual Studio'yu indirin [visualstudio.microsoft.com](https://visualstudio.microsoft.com/).
* Unity için Araçlar Mac için Visual Studio yükleme işlemi sırasında otomatik olarak yüklenir.
* Bağlantısındaki [Yükleme Kılavuzu](installation.md) ek yükleme Yardımı.

> [!NOTE]
> Unity için Mac araçları Visual Studio Unity sürüm 5.6.1 gerektirir veya üzeri. Unity için Visual Studio Araçları sürümünüz Unity etkinleştirildiğini doğrulamak için **hakkında Unity** metni ara ve Unity menüden "Microsoft Visual Studio etkin Unity için iletişim kutusunun sol içinde Araçları".
>
> ![Unity hakkında](media/setup-vsmac-tools-unity-image3.png)

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Visual Studio için Unity uzantısı Mac araçları etkinleştirilmiş olduğunu doğrulayın

Visual Studio için Unity uzantısı Mac araçları varsayılan olarak etkinleştirilmesi gerekir, ancak bunu doğrulamak ve yüklü sürüm numarasını kontrol edin:

1. Visual Studio menüden **uzantıları...** .

   ![Uzantıları seçin](media/setup-vsmac-tools-unity-image1.png)

2. Oyun Geliştirme bölümü genişletin ve Visual Studio için Unity girişi için Mac araçları onaylayın.

   ![Unity girişi görünümü](media/setup-vsmac-tools-unity-image2.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Unity Mac için Visual Studio ile kullanılacak şekilde yapılandırma

Unity 2018.1 itibarıyla Visual Studio, Unity'de varsayılan dış kod düzenleyicisi olmalıdır. Bunu doğrulamak veya Visual Studio için dış Kod Düzenleyicisi'ni değiştirin:

1. Seçin **tercihleri...**  Unity menüsünde.

   ![Tercihler'i seçme](media/setup-vsmac-tools-unity-image4.png)

2. Tercihler iletişim kutusunda, **External Tools** (Dış Araçlar) sekmesini seçin.

3. Dış betik Düzenleyicisi açılır listeden seçin **Visual Studio** listeleniyorsa, aksi takdirde seçin **Gözat...** .

   ![Visual Studio'yu seçme](media/setup-vsmac-tools-unity-image5.png)

4. Varsa **Gözat...**  olduğu belirlenirse, uygulamaları dizine gidin ve Visual Studio seçin ve ardından **açık**.

   ![Aç'ı seçin](media/setup-vsmac-tools-unity-image6.png)

5. Visual Studio içinde seçildikten sonra **dış betik Düzenleyicisi** listesinde, yapılandırma işlemini tamamlamak için Tercihler iletişim kutusunu kapatın.