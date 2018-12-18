---
title: Unity için Visual Studio Araçları ile çalışmaya başlama | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 9d924ee92258e348d5ffee1551fcde7707d711cf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855215"
---
# <a name="get-started-with-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları ile çalışmaya başlama

## <a name="install-visual-studio"></a>Visual Studio'yu yükleme

### <a name="unity-bundled-installation"></a>Unity ile birlikte yükleme

Unity 2018.1 itibarıyla Visual Studio, Unity için varsayılan C# betik düzenleyicisidir ve Unity Hub yükleme aracının yanı sıra Unity Download Assistant'ta mevcuttur.

- [store.unity.com](https://store.unity.com/) adresinden Unity'yi indirin.

Yükleme sırasında Visual Studio'nun, Unity ile yüklenecek bileşenler listesinde işaretlendiğinden emin olun:

#### <a name="unity-hub"></a>Unity Hub

![Unity hub'ı yükleme](media/vstu_unity-hub.png)

#### <a name="unity-download-assistant"></a>Unity Yükleme Yardımcısı

![Unity Yükleme Yardımcısı'nı yükleme](media/vstu_download-assistant.png)

#### <a name="check-for-updates-to-visual-studio"></a>Visual Studio güncelleştirmelerini denetleme

Unity yüklemenize dahil olan Visual Studio sürümü, en son sürüm olmayabilir. En son araçlara ve özelliklere erişiminiz olduğundan emin olmak için güncelleştirmeleri denetlemeniz önerilir.

- [Visual Studio’yu güncelleştirme](../install/update-visual-studio.md)

### <a name="manual-installation"></a>El ile yükleme

Visual Studio 2017 zaten yüklüyse veya el ile yüklemeyi tercih ederseniz Visual Studio yükleyicisini çalıştırın.

1. [Visual Studio yükleyicisini indirin](/visualstudio/install/install-visual-studio) veya zaten yüklüyse açın.

1. İstediğiniz Visual Studio sürümü için **Değiştir**'e (zaten yüklüyse) veya **Yükle**'ye (yeni yüklemeler için) tıklayın.

1. **İş yükleri** sekmesinde **Mobil ve Oyun** bölümüne gidip **Game development with Unity** (Unity ile oyun geliştirme) iş yükünü seçin.

    ![Unity iş yükü](media/vstu_unity-workload.png)

1. Yükleyici penceresinin sağ alt köşesindeki **Değiştir**'e (zaten yüklüyse) veya **Yükle**'ye (yeni yüklemeler için) tıklayın.

## <a name="configure-unity-for-use-with-visual-studio"></a>Unity'yi Visual Studio ile kullanım için yapılandırma

Unity 2018.1 itibarıyla Visual Studio, Unity'de varsayılan dış kod düzenleyicisi olmalıdır. Bunu onaylayabilir veya dış betik düzenleyicisini Visual Studio'nun belirli bir sürümü olarak değiştirebilirsiniz:

1. **Edit** (Düzenle) menüsünde **Preferences** (Tercihler) seçeneğini belirleyin.

   ![Tercihler'i seçme](media/vstu_unity-preferences.png)

2. Tercihler iletişim kutusunda, **External Tools** (Dış Araçlar) sekmesini seçin.

3. **External Script Editor** (Dış Betik Düzenleyici) listesinde istediğiniz Visual Studio sürümü listelenmişse seçin, aksi takdirde **Browse...** (Gözat...) seçeneğini belirleyin.

   ![Visual Studio'yu seçme](media/vstu_unity-external-tools.png)

4. **Browse...** (Gözat...) seçili ise Visual Studio yükleme dizininizdeki **Common7/IDE** klasörüne gidin ve **devenv.exe** öğesini seçip **Aç**'a tıklayın.

   ![Aç'ı seçin](media/vstu_browse-for-application.png)

5. **External Script Editor** (Dış Betik Düzenleyici) listesinde Visual Studio seçildikten sonra, **Editor Attaching** (Düzenleyici Ekleme) onay kutusunun seçili olduğundan emin olun.

6. Yapılandırma işlemini tamamlamak için **Preferences** (Tercihler) iletişim kutusunu kapatın.

## <a name="support-for-older-versions"></a>Eski sürümler için destek

 Unity için Visual Studio Araçları'nı Visual Studio Market'ten indirip yükleyin. Visual Studio sürümünüz için doğru paketi yüklemeniz gerekir.

- Visual Studio 2015 Community, Visual Studio 2015 Professional veya Visual Studio 2015 Enterprise için:

   [Unity için Visual Studio 2015 Araçları'nı indirin](https://marketplace.visualstudio.com/items?itemName=SebastienLebreton.VisualStudio2015ToolsforUnity)

> [!NOTE]
> Unity için Visual Studio Araçları, Unity 5.2 veya sonraki bir sürümünün yanı sıra Visual Studio Community, Professional, Premium ya da Enterprise gibi uzantıları destekleyen bir Visual Studio sürümü gerektirir. Unity yüklemenizde Unity için Visual Studio Araçları'nın etkinleştirildiğini doğrulamak için **Yardım** menüsünde **Unity Hakkında**'yı seçin ve iletişim kutusunun sol alt kısmında "Unity için Microsoft Visual Studio Araçları etkin" ifadesinin yer alıp almadığını kontrol edin.
> ![Unity hakkında](media/vstu_about-unity.png)

## <a name="next-steps"></a>Sonraki adımlar

 Visual Studio'yu kullanarak Unity projenizde çalışma ve hata ayıklama hakkında bilgi edinmek için bkz. [Unity için Visual Studio Araçları](../cross-platform/using-visual-studio-tools-for-unity.md).
