---
title: Mac için Visual Studio 2019 'yi yükler
description: Mac için Visual Studio 2019 ' i ve platformlar arası geliştirme için gereken ek bileşenleri yüklemek için yönergeler.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 03/04/2021
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: 653e653a0574da52c0030b06c7a8c13b436ed686
ms.sourcegitcommit: 4bf7d82eb3a837ad5d1ae5c110039cbf74258f18
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2021
ms.locfileid: "106273420"
---
# <a name="install-visual-studio-2019-for-mac"></a>Mac için Visual Studio 2019 'yi yükler

MacOS 'ta yerel, platformlar arası .NET uygulamaları geliştirmeye başlamak için aşağıdaki adımları izleyerek Mac için Visual Studio 2019 ' yi yüklemelisiniz.

 > [!div class="button"]
 > [Mac için Visual Studio’yu indirin](https://visualstudio.microsoft.com/vs/mac/)

## <a name="requirements"></a>Gereksinimler

- MacOS High Sierra 10,13 veya üzeri bir Mac.

İOS veya macOS için Xamarin uygulamaları oluşturmak üzere şunları da yapmanız gerekir:

- En son Xcode sürümüyle uyumlu bir Mac. Apple 'ın [En düşük gereksinimleri belgelerine](https://developer.apple.com/support/xcode/) bakın
- [Xcode](https://developer.apple.com/xcode)'un en son sürümü. Mac 'niz en son sürümle uyumlu değilse, [Xcode 'un eski bir sürümünü kullanmak](https://docs.microsoft.com/xamarin/ios/troubleshooting/questions/old-version-xcode) mümkün olabilir.
- Bir Apple KIMLIĞI. Zaten bir Apple KIMLIĞINIZ yoksa, üzerinde yeni bir tane oluşturabilirsiniz https://appleid.apple.com . Xcode 'a yükleme ve oturum açma için bir Apple KIMLIĞI olması gerekir.

## <a name="installation-instructions"></a>Yükleme yönergeleri

1. Yükleyiciyi [Mac için Visual Studio indirme sayfasından](https://visualstudio.microsoft.com/vs/mac/)indirin.
2. İndirme işlemi tamamlandıktan sonra, yükleyiciyi bağlamak için **VisualStudioforMacInstaller. dmg** ' ye tıklayın ve ardından ok logosunu çift tıklayarak çalıştırın:

    [![Yüklemeyi başlatmak için büyük oka tıklayın](media/install-installer-sml.png)](media/install-installer.png#lightbox)

3. Internet 'ten indirilen uygulamayla ilgili bir uyarı alabilirsiniz. **Aç**’a tıklayın.
4. Yükleyici sisteminizi denetlerken bekleyin:

    [![Yükleyici, sisteminizde yüklü bileşenleri denetler](media/install-checking-sml.png)](media/install-checking.png#lightbox)

5. Gizlilik ve lisans şartlarını doğrulamanızı isteyen bir uyarı görüntülenir. Bunları okumak için bağlantıları izleyin ve kabul ediyorsanız **devam** ' a basın:

    [![Gizlilik ve koşullara ilişkin bağlantıları izleyin, ardından kabul ediyorsanız devam edin](media/install-privacy.png)](media/install-privacy.png#lightbox)

6. Kullanılabilir iş yüklerinin listesi görüntülenir. Kullanmak istediğiniz bileşenleri seçin:

    [![Visual Studio Mac yükleyicisinde, yükleme için kullanılabilen bileşenlerin bir listesini gösteren "ne yüklemek istiyorsunuz?" ekranının ekran görüntüsü.](media/install-selection.png)](media/install-selection.png#lightbox)

   Tüm platformları yüklemek istemiyorsanız, hangi platformları yükleyeceğinize karar vermenize yardımcı olması için aşağıdaki kılavuzu kullanın:

   |Uygulama türü  |Hedef  |Seçim  |Notlar  |
   |---------|---------|---------|---------|
   |**Xamarin kullanan uygulamalar**| Xamarin.Forms|**Android** ve **iOS** platformlarını seçin |[ **Xcode** 'u yüklemeniz gerekecektir](https://developer.apple.com/xcode/) |
   ||Yalnızca iOS|**İOS** platformunu seçin|[ **Xcode** 'u yüklemeniz gerekecektir](https://developer.apple.com/xcode/)|
   ||Yalnızca Android|**Android** platformunu seçin|Ayrıca ilgili bağımlılıkları da seçmeniz gerektiğini unutmayın|
   ||Yalnızca Mac|**MacOS (Cocoa)** platformunu seçin|[ **Xcode** 'u yüklemeniz gerekecektir](https://developer.apple.com/xcode/)|
   |**.NET Core Uygulamaları**|         |**.NET Core** platformunu seçin.|         |
   |**ASP.NET Core Web Uygulamaları**|         |**.NET Core** platformunu seçin.|         |
   |**Azure İşlevleri**|         |**.NET Core** platformunu seçin.|         |
   |**Platformlar arası Unity oyun geliştirme**|         |Mac için Visual Studio ötesinde ek platform yüklenmesi gerekmez.| Unity uzantısını yükleme hakkında daha fazla bilgi için [Unity kurulum kılavuzuna](./setup-vsmac-tools-unity.md) bakın.|

7. Seçimlerinizi yaptıktan sonra, **Install** düğmesine basın.
8. Yükleyici, Mac için Visual Studio ve seçilen iş yüklerini indirdiği ve yükleyen ilerlemeyi görüntüler. Yükleme için gerekli ayrıcalıkları vermek üzere parolanızı girmeniz istenir.:

    [![Mac için .NET Geliştirici araç seti için bir yükleme ilerleme ekranı gösteren Visual Studio Mac yükleyicisi 'nin ekran görüntüsü.](media/installation-progress.png)](media/installation-progress.png#lightbox)

9. Mac için Visual Studio, yükledikten sonra oturum açarak ve kullanmak istediğiniz anahtar bağlamalarını seçerek yüklemenizi kişiselleştirmenizi ister:

    [![IDE 'de oturum açın](media/ide-tour-2019-start-signin.png)](media/ide-tour-2019-start-signin.png#lightbox)

    [![Kullanmak istediğiniz klavye kısayollarını seçin](media/ide-tour-2019-keyboard-shortcut.png)](media/ide-tour-2019-keyboard-shortcut.png#lightbox)

Şirket ortamında yükleme sırasında ağ sorununuz varsa, [bir güvenlik duvarı veya proxy yönergeleri arkasındaki yüklemeyi](#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server) inceleyin.

[Sürüm notlarındaki](/visualstudio/releasenotes/vs2019-mac-relnotes)değişiklikler hakkında daha fazla bilgi edinin.

> [!NOTE]
> Özgün yükleme sırasında bir platform veya araç yüklememeyi seçtiyseniz (#6 adımında bunu seçerek), bileşenleri daha sonra eklemek istiyorsanız yükleyiciyi yeniden çalıştırmalısınız.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Bir güvenlik duvarı veya proxy sunucusunun arkasında Mac için Visual Studio yüklemesi

Bir güvenlik duvarının arkasında Mac için Visual Studio yüklemek için, yazılım için gerekli araçların ve güncelleştirmelerin indirilmelerine izin vermek üzere belirli uç noktalara erişilebilir hale gelmelidir.

Ağınızı aşağıdaki konumlara erişime izin verecek şekilde yapılandırın:

- [Visual Studio uç noktaları](./install-behind-a-firewall-or-proxy-server.md)

## <a name="next-steps"></a>Sonraki adımlar

Mac için Visual Studio yükleme, uygulamalarınız için kod yazmaya başlayabilmeniz için izin verir. Aşağıdaki kılavuzlar, projelerinizi yazmanın ve dağıtmanın sonraki adımlarında size yol gösterecek şekilde sunulmaktadır.

### <a name="ios"></a>iOS

1. [Hello, iOS](https://docs.microsoft.com//xamarin/ios/get-started/hello-ios/)
2. [Cihaz sağlama](https://docs.microsoft.com/xamarin/ios/get-started/installation/device-provisioning/)(uygulamanızı cihazda çalıştırmak için).

### <a name="android"></a>Android

1. [Hello, Android](https://docs.microsoft.com/xamarin/android/get-started/hello-android/)
2. [Xamarin Android SDK Manager 'ı kullanma](https://docs.microsoft.com/xamarin/android/get-started/installation/android-sdk?tabs=macos)
3. [Android SDK Emulator](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/)
4. [Cihazı Dağıtım için Ayarlama](https://docs.microsoft.com/xamarin/android/get-started/installation/set-up-device-for-development)

### <a name="xamarinforms"></a>Xamarin.Forms

Xamarin. Forms ile yerel platformlar arası uygulamalar oluşturun:

1. [Xamarin.Forms Hızlı Başlangıçları](https://docs.microsoft.com/xamarin/get-started/quickstarts/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>.NET Core Uygulamaları, ASP.NET Core Web Apps, Unity oyun geliştirme

Diğer Iş yükleri için [Iş yükleri](workloads.md) sayfasına bakın.

## <a name="related-video"></a>İlgili video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'Yu (Windows 'a) yükler](/visualstudio/install/install-visual-studio)
