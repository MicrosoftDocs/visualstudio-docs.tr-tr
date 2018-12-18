---
title: Mac için Visual Studio'yu kaldırın
description: Mac ve ilgili araçlar için Visual Studio kaldırma yönergeleri.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.openlocfilehash: 4a0ecef49d8c3493ff6094be66f1d05ad588077c
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295676"
---
# <a name="uninstalling-visual-studio-for-mac"></a>Mac için Visual Studio'yu kaldırma

Mac için Visual Studio gibi tek başına uygulamalar dahil olmak üzere, platformlar arası uygulama geliştirmeyi sağlayan Xamarin ürünlerin birçok

İlgili bölüme gidilerek ayrı ayrı her ürün kaldırmak için bu kılavuzu kullanabilirsiniz veya sağlanan betikleri kullanabilir [kaldırma betiği](#uninstall-script) her şeyi kaldırmak için bölümü.

Xamarin Studio makinenizde yüklü vardı, ayrıca yönergeleri gerekebilir [kullanıcının Xamarin kaldırma](/xamarin/cross-platform/get-started/installation/uninstalling-xamarin#uninstall-xamarin-studio-on-mac) Kılavuzu, aşağıdaki adımları yanı sıra.

## <a name="uninstall-script"></a>Betik kaldırma

Mac için Visual Studio'yu kaldırmak için kullanılan iki komut dosyası ve makineniz için tüm bileşenler vardır:

- [Visual Studio ve Xamarin betiği](#visual-studio-for-mac-and-xamarin-script)
- [.NET core komut dosyası](#net-core-script)

Aşağıdaki bölümlerde, indirme ve betikleri kullanarak bilgi sağlar.

### <a name="visual-studio-for-mac-and-xamarin-script"></a>Betik, Mac ve Xamarin için Visual Studio

Visual Studio yüklemesini kaldırabilir ve Xamarin bileşenleri bir Git kullanarak [betik kaldırma](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh).

Makalede bulabilirsiniz komutların çoğu bu kaldırma betiğini içerir. Komut dosyası iki ana atlamalar vardır ve olası dış bağımlılıklar nedeniyle dahil edilmez:

- **Mono kaldırma**
- **Android AVD kaldırma**

Betiği çalıştırmak için aşağıdaki adımları uygulayın:

1. Sağ tıklatın ve betik **Kaydet** mac'inizde dosyayı kaydetmek için
2. Terminali açın ve komut dosyasını indirdiğiniz için çalışma dizinini değiştirin:

    ```bash
    $ cd /location/of/file
    ```
3. Yürütülebilir kod ve çalışma ile **sudo**:

    ```bash
    $ chmod +x ./uninstall-vsmac.sh
    $ sudo ./uninstall-vsmac.sh
    ```
4. Son olarak, kaldırma betiğini silin.

### <a name="net-core-script"></a>.NET core komut dosyası

.NET Core için kaldırma betiğini bulunan [dotnet CLI depo](https://raw.githubusercontent.com/dotnet/cli/master/scripts/obtain/uninstall/dotnet-uninstall-pkgs.sh)

Betiği çalıştırmak için aşağıdaki adımları uygulayın:

1. Sağ tıklatın ve betik **Kaydet** mac'inizde dosyayı kaydetmek için
2. Terminali açın ve komut dosyasını indirdiğiniz için çalışma dizinini değiştirin:

    ```bash
    $ cd /location/of/file
    ```
3. Yürütülebilir kod ve çalışma ile **sudo**:

    ```bash
    $ chmod +x ./dotnet-uninstall-pkgs.sh
    $ sudo ./dotnet-uninstall-pkgs.sh
    ```
4. Son olarak, .NET Core kaldırma betiğini silin.

## <a name="uninstall-visual-studio-for-mac"></a>Mac için Visual Studio'yu kaldırın

Visual Studio'yu bir Mac bilgisayardan kaldırmak ilk adımı bulmaktır **Visual Studio.app** içinde **/Applications** dizin sürükleyin **çöp kutusu**. Alternatif olarak, sağ tıklayın ve **çöp kutusuna Taşı** aşağıdaki görüntüde gösterildiği gibi:

![Visual Studio uygulamaya çöp Taşı](media/uninstall-image1.png)

Olabilir yine de dosya sisteminde Xamarin için ilgili diğer dosyaları rağmen bu uygulama paketi grubu silme, Mac için Visual Studio kaldırır.

Mac için Visual Studio'nun tüm izlemeleri kaldırmak için terminalde aşağıdaki komutları çalıştırın:

```bash
sudo rm -rf "/Applications/Visual Studio.app"
rm -rf ~/Library/Caches/VisualStudio
rm -rf ~/Library/Preferences/VisualStudio
rm -rf ~/Library/Preferences/Visual\ Studio
rm -rf ~/Library/Logs/VisualStudio
rm -rf ~/Library/VisualStudio
rm -rf ~/Library/Preferences/Xamarin/
rm -rf ~/Library/Developer/Xamarin
rm -rf ~/Library/Application\ Support/VisualStudio
rm -rf ~/Library/Application\ Support/VisualStudio/7.0/LocalInstall/Addins/
```

## <a name="uninstall-mono-sdk-mdk"></a>Mono SDK'sı (MDK) kaldırma

Mono, Microsoft .NET Framework'ün açık kaynak uygulamasıdır ve tüm Xamarin Products—Xamarin.iOS, Xamarin.Android ve Xamarin.Mac bu platformlarda geliştirme C# ' ta izin vermek için kullanılır.

> [!WARNING]
> Mono, Unity gibi kullanan diğer uygulamalar Visual Studio dışında Mac için vardır.
> Başka bir bağımlılık üzerinde Mono kaldırmadan önce emin olun.

Mono Framework bir makineden kaldırmak için terminalde aşağıdaki komutları çalıştırın:

```bash
sudo rm -rf /Library/Frameworks/Mono.framework
sudo pkgutil --forget com.xamarin.mono-MDK.pkg
sudo rm -rf /etc/paths.d/mono-commands
```

## <a name="uninstall-xamarinandroid"></a>Xamarin.Android kaldırma

Xamarin.Android, Java SDK'sı ve Android SDK gibi kullanımını ve yükleme için gerekli öğeler vardır.

Xamarin.Android kaldırmak için aşağıdaki komutları kullanın:

```bash
sudo rm -rf /Developer/MonoDroid
rm -rf ~/Library/MonoAndroid
sudo pkgutil --forget com.xamarin.android.pkg
sudo rm -rf /Library/Frameworks/Xamarin.Android.framework
```

### <a name="uninstall-android-sdk-and-java-sdk"></a>Android SDK ve Java SDK kaldırma

Android SDK'sı, Android uygulamalarının geliştirilmesini için gereklidir. Android SDK'sı tüm parçalarını tamamen kaldırmak için dosyayı bulun **~/Library/Developer/Xamarin/** ve taşımak **çöp**.

Bunu zaten Mac OS X bir parçası olarak önceden paketlenmiş olarak Java SDK (JDK) kaldırılması, gerekmez / macOS.

### <a name="uninstall-android-avd"></a>Android AVD kaldırma

> [!WARNING]
> Ayrıca Android AVD ve Android projeleri Android Studio'da ayırmak bu dizin neden Studio.Removing gibi ek bu android bileşenlerini kullanan diğer uygulamalar Visual Studio dışında Mac için vardır.

Herhangi bir ek Android ve Android AVDs kaldırmak için bileşenleri aşağıdaki komutu kullanın:

```bash
rm -rf ~/.android
```

Kaldırmak için yalnızca Android AVDs aşağıdaki komutu kullanın:

```bash
rm -rf ~/.android/avd
```

## <a name="uninstall-xamarinios"></a>Xamarin.iOS kaldırma

Xamarin.iOS sağlayan iOS kullanarak uygulama geliştirme C# veya F# Mac için Visual Studio ile

Tüm Xamarin.iOS dosyaları dosya sisteminden kaldırmak için terminalde aşağıdaki komutları kullanın:

```bash
rm -rf ~/Library/MonoTouch
sudo rm -rf /Library/Frameworks/Xamarin.iOS.framework
sudo rm -rf /Developer/MonoTouch
sudo pkgutil --forget com.xamarin.monotouch.pkg
sudo pkgutil --forget com.xamarin.xamarin-ios-build-host.pkg
sudo pkgutil --forget com.xamarin.xamarin.ios.pkg
```

## <a name="uninstall-xamarinmac"></a>Xamarin.Mac kaldırma

Xamarin.Mac makinenizden Mac Cihazınızda lisans ve ürün sırasıyla yok etmek aşağıdaki iki komutu kullanılarak kaldırılabilir:

```bash
sudo rm -rf /Library/Frameworks/Xamarin.Mac.framework
rm -rf ~/Library/Xamarin.Mac
```

## <a name="uninstall-workbooks-and-inspector"></a>Çalışma kitapları ve denetçisi kaldırma

1.2.2 ile başlayarak, Xamarin Workbooks & Denetçisi terminalden çalıştırılarak kaldırılabilir:

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

Eski sürümler için aşağıdaki yapılar kaldırmanız gerekir:

* Çalışma kitapları uygulamaya Sil `"/Applications/Xamarin Workbooks.app"`
* Inspector uygulamaya Sil `"Applications/Xamarin Inspector.app"`
* Add-INS Sil: `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` ve `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"`
* Inspector silin ve destek dosyaları burada: `/Library/Frameworks/Xamarin.Interactive.framework` ve `/Library/Frameworks/Xamarin.Inspector.framework`

## <a name="uninstall-the-xamarin-profiler"></a>Xamarin Profiler'ı kaldırma

```bash
sudo rm -rf "/Applications/Xamarin Profiler.app"
```

## <a name="uninstall-the-visual-studio-installer"></a>Visual Studio yükleyicisini Kaldır

Xamarin için evrensel Yükleyicisi'nin tüm izlemeleri kaldırmak için aşağıdaki komutları kullanın:

```bash
rm -rf ~/Library/Caches/XamarinInstaller/
rm -rf ~/Library/Caches/VisualStudioInstaller/
rm -rf ~/Library/Logs/XamarinInstaller/
rm -rf ~/Library/Logs/VisualStudioInstaller/
rm -rf ~/Library/Preferences/Xamarin/
rm -rf "~/Library/Preferences/Visual Studio/"
```

## <a name="see-also"></a>Ayrıca bkz.

- [(Windows üzerinde) Visual Studio'yu kaldırın](/visualstudio/install/uninstall-visual-studio)