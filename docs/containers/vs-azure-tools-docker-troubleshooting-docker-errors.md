---
title: Windows Docker istemcisi hatalarında sorun giderme | Microsoft Docs
description: Visual Studio oluşturma ve Visual Studio 2017'yi kullanarak web uygulamaları Windows üzerindeki Docker dağıtma kullanırken karşılaştığınız sorunları giderin.
ms.technology: vs-azure
author: devinb
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: conceptual
ms.workload: multiple
ms.date: 10/13/2017
ms.author: devinb
ms.openlocfilehash: 396ad65835375c9c85bc3d67ca685f6270bbb7d3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58160426"
---
# <a name="troubleshoot-visual-studio-2017-development-with-docker"></a>Docker ile Visual Studio 2017 geliştirme sorunlarını giderme

Docker için Visual Studio Araçları ile çalışırken, oluşturma veya uygulamanızı hata ayıklama sırasında sorunlarla karşılaşabilirsiniz. Aşağıda bazı ortak adımlar giderirken.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Birim paylaşımı etkin değil. Birim, paylaşım için Docker CE Windows ayarları (yalnızca Linux kapsayıcıları) etkinleştir

Bu sorunu çözmek için:

1. Sağ **için Docker Windows** bildirim alanına tıklayın ve ardından içinde **ayarları**.
1. Seçin **paylaşılan sürücüleri** ve projenin bulunduğu sürücü yanı sıra sistem sürücüsünün paylaşın.

> [!NOTE]
> Dosyaları paylaşılan görünüyorsa, birimi paylaşan yeniden etkinleştirmek için iletişim kutusunun alt kısmındaki "... kimlik bilgilerini Sıfırla" bağlantısını tıklatın gerekebilir. Kimlik bilgilerini sıfırlama sonra devam etmek için Visual Studio'yu yeniden başlatmanız gerekebilir.

![Paylaşılan sürücüleri](media/vs-azure-tools-docker-troubleshooting-docker-errors/shareddrives.png)

> [!TIP]
> Visual Studio 2017 sürüm 15.6 ve daha sonra sor **paylaşılan sürücüleri** yapılandırılmamışlardır.

### <a name="container-type"></a>Kapsayıcı türü

Docker desteği bir projeye eklerken, bir Windows veya Linux kapsayıcısı seçin. Docker konağı aynı kapsayıcı türü çalıştırmalıdır. Çalışan Docker örneğinde kapsayıcı türü değiştirmek için sistem tepsisindeki'nın Docker simgesini sağ tıklatın ve seçin **Windows kapsayıcılarına geç...**  veya **geçiş Linux kapsayıcıları için...** .

## <a name="unable-to-start-debugging"></a>Hata ayıklama başlatılamıyor

Nedenlerinden biri, kullanıcı profili klasöründe eski hata ayıklama bileşenleri bulunması ilgili olabilir. En son hata ayıklama bileşenleri sonraki hata ayıklama oturumunda yüklenir, böylece bu klasörleri kaldırmak için aşağıdaki komutları yürütün.

- DEL %userprofile%\vsdbg
- DEL %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Uygulamanızı hata ayıklama sırasında ağ ile belirli hataları

Dan indirilebilir komut dosyası yürütme deneyin [temizleme kapsayıcı konağı ağ](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking), hangi ana makinenizde ağ ile ilgili bileşenler Yenile.

## <a name="mounts-denied"></a>Takar reddedildi

MacOS için Docker'ı kullanırken, klasör /usr/local/share/dotnet/sdk/NuGetFallbackFolder başvuran bir hatayla karşılaşabilir. Docker dosya paylaşımı sekmesine klasörü Ekle

## <a name="microsoftdockertools-github-repo"></a>Microsoft/DockerTools GitHub deposu

Karşılaştığınız başka herhangi bir sorun için bkz: [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues) sorunları.