---
title: Dotfuscator Community Edition (CE) yükleyin
ms.date: 06/22/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive koruma, koruma, community edition, gizleme, .NET, ücretsiz, Visual Studio 2017, yükleme
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
- Dotfuscator installer
- Dotfuscator setup
- install Dotfuscator
- installing Dotfuscator
- set up Dotfuscator
description: Visual Studio 2017'de dahil edilen ücretsiz Dotfuscator Community Edition'ı yüklemeyi öğrenin.
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: douge
ms.openlocfilehash: d513588a7d00e874b38306150f896157906e2733
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880370"
---
# <a name="install-dotfuscator-community-edition-ce"></a>Dotfuscator Community Edition (CE) yükleyin

Visual Studio 2017, yeni bir low Impact yüklemesinde deneyim sağlanıyor.
Sonuç olarak, Dotfuscator Community Edition (Dotfuscator CE) varsayılan olarak yüklü değil.
Ancak, Visual Studio yüklü olsa bile Dotfuscator CE'yi yüklemeyi kolaydır.

> [!NOTE]
> Visual Studio sürümleriyle birlikte gelen Dotfuscator CE sürümleri yanı sıra, PreEmptive Solutions, güncelleştirilmiş sürümleri da düzenli aralıklarla ve Web sitesinde sağlar.
> Karşıdan yüklemek isterseniz **en son sürümü** Visual Studio'dan yüklemek yerine doğrudan **[Dotfuscator indirmeler sayfasına gitmek için buraya tıklayın] [ download]**.

## <a name="within-visual-studio"></a>Visual Studio içinden

Dotfuscator CE Visual Studio IDE içinden yükleyebilirsiniz:

1. İçinde **hızlı başlatma** (Ctrl + Q) arama çubuğunda, türü `dotfuscator`. <br/> <br/> ![Hızlı Başlatma](media/install_from_vs_12.png) <br/> <br/>
2. Hızlı Başlatma'altında gösterilen sonuçları *yükleme* başlığı seçin **PreEmptive koruma - Dotfuscator (ayrı ayrı bileşen)**.
   * Bunun yerine, altında görürseniz *menüleri* başlığı **araçları - PreEmptive koruma - Dotfuscator**, Dotfuscator CE zaten yüklü. Kullanım ayrıntıları için bkz. [tam Dotfuscator CE Kullanıcı Kılavuzu'nun Başlarken sayfası][get-started].
3. Bir Visual Studio yükleyicisi penceresi başlatılır, önceden yapılandırılmış Dotfuscator CE'yi yüklemeyi.
   * Devam etmek için yönetici kimlik bilgilerini sağlamanız gerekebilir.
4. Visual Studio IDE tüm örneklerini kapatın. <br/> <br/> ![Yükle'ye tıklayın](media/install_from_vs_345.png) <br/> <br/>
5. Visual Studio yükleyicisi penceresinde *yükleme*.

Yükleme tamamlandıktan sonra Dotfuscator CE kullanmaya başlayabilirsiniz. Ayrıntılar için bkz [tam Dotfuscator CE Kullanıcı Kılavuzu'nun Başlarken sayfası][get-started].

## <a name="during-visual-studio-installation"></a>Visual Studio yüklemesi sırasında

Visual Studio 2017 henüz yüklemediyseniz Yükleyicisi'nden edinebilirsiniz [Visual Studio Web][2017-install].
Çalıştırdığınızda, seçili Visual Studio sürümü için yükleme seçeneklerini görüntüler.

![Yükleme Seçenekleri](media/install_ui.png)

Ardından, Visual Studio 2017'in tek tek bir bileşen Dotfuscator CE yükleyebilirsiniz:

1. Seçin **tek tek bileşenler** sekmesi.
2. Altında *kod Araçları*, kontrol *PreEmptive koruma - Dotfuscator* öğesi.<br/> <br/> ![Bağımsız bileşenler](media/install_individually_12.png) <br/> <br/>
3. *Özeti* paneli görüntüler *PreEmptive koruma - Dotfuscator* altında *tek tek bileşenler* bölümü. <br/> <br/> ![Özet bölmesi](media/install_individually_3.png) <br/> <br/>
4. Ortamınız için uygun şekilde herhangi diğer yükleme ayarlarını yapılandırın.
5. Hazır olduğunuzda Visual Studio'yu yüklemek tıklayın *yükleme* düğmesi.

Yükleme tamamlandıktan sonra Dotfuscator CE kullanmaya başlayabilirsiniz. Ayrıntılar için bkz [tam Dotfuscator CE Kullanıcı Kılavuzu'nun Başlarken sayfası][get-started].

## <a name="see-also"></a>Ayrıca bkz.

[This topic in the full Dotfuscator CE User Guide]: https://www.preemptive.com/dotfuscator/ce/docs/help/

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[2017-install]:  https://visualstudio.microsoft.com/downloads/#vs-2017
[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html