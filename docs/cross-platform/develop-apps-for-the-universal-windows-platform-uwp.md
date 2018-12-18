---
title: Evrensel Windows Platformu (UWP) uygulamaları geliştirin | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2017
ms.technology:
- tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
author: stevehoag
ms.author: shoag
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: de4306b2fa56bf00fd51a741441395b90ed314e5
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280811"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Evrensel Windows Platformu (UWP) için uygulama geliştirme
Evrensel Windows platformu ve bizim bir Windows çekirdek ile masaüstlerine telefonlardan tüm Windows 10 cihazlarda aynı uygulamayı çalıştırabilirsiniz. Visual Studio ve evrensel Windows uygulaması geliştirme araçları ile bu evrensel Windows uygulamaları oluşturun.

 ![Evrensel Windows platformu](../cross-platform/media/uwp_coreextensions.png "UWP_CoreExtensions")

 Uygulamanızı Windows 10 telefonda, Windows 10 Masaüstü veya Xbox üzerinde çalıştırın. Bu, aynı uygulama paketi kullanılır! Windows 10 tek, birleştirilmiş çekirdek sunulmasıyla birlikte, tüm platformlardaki bir uygulama paketini çalıştırabilecek. Çeşitli platformları, platforma özgü davranışlardan faydalanmak için uygulamanızı ekleyebilirsiniz SDK'ları uzantılıdır. Örneğin, mobil cihazlar için bir uzantı SDK'sı, Windows phone'da basıldığında geri düğmesini işler. Projenizde bir uzantı SDK'sı başvuruda bulunursanız, yalnızca, SDK bu platform üzerinde kullanılabilir olup olmadığını test etmek için çalışma zamanı denetimleri ekleyin. Her platform için aynı uygulama paketi nasıl sahip olmasıdır!

 **Windows Çekirdek nedir?**

 İlk kez Windows tüm Windows 10 platformlardaki ortak bir çekirdek için düzenlendi. Bir ortak kaynak, bir ortak Windows çekirdek, bir dosya g/ç yığını ve bir uygulama modeli yoktur. Kullanıcı Arabirimi için yalnızca bir XAML kullanıcı Arabirimi çerçevesi ve bir HTML kullanıcı Arabirimi çerçevesi yoktur. Uygulamanızı farklı Windows 10 cihazlarda çalıştırmak kolay kolaylaştırdık için harika bir uygulama oluşturmaya odaklanabilirsiniz.

 **Evrensel Windows platformu tam olarak nedir?**

Evrensel Windows platformu yeterlidir, sözleşmeler ve sürümleri koleksiyonudur. Bunlar, uygulamanızın çalıştırdığı hedef izin verir. Artık bir işletim sistemini hedef; artık bir veya daha fazla cihaz aileleri hedefleyin. Daha ayrıntılı bilgi edinin okuyarak [Evrensel Windows platformu giriş](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="requirements"></a>Gereksinimler
 Evrensel Windows uygulaması geliştirme araçları, uygulamanızın farklı cihazlarda nasıl göründüğünü görmek için kullanabileceğiniz öykünücü ile gelir. Bu öykünücü kullanmak istiyorsanız, bu yazılımın bir fiziksel makineye yüklemeniz gerekir. Fiziksel makinenin Windows 8.1 (x64) Professional sürümü çalıştırmalıdır veya sonraki bir sürümünü ve istemci Hyper-V ve ikinci düzey adres çevirisi (SLAT) destekleyen bir işlemci. Visual Studio bir sanal makinede yüklü olduğunda öykünücüleri kullanılamaz.

 Gereken yazılım listesi aşağıda verilmiştir:

-   [Windows 10](http://windows.microsoft.com/windows/downloads). Visual Studio 2017 UWP geliştirme yalnızca Windows 10'da destekler. Daha fazla ayrıntı için bkz. Visual Studio [Platform hedefleme](/visualstudio/productinfo/vs2017-compatibility-vs) ve [sistem gereksinimleri](/visualstudio/productinfo/vs2017-system-requirements-vs).

-   [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017). İsteğe bağlı Evrensel Windows platformu geliştirme iş yükü de gerekir.

     ![UWP iş yükü](media/uwp_workload.png)

Bu yazılımı yükledikten sonra Windows 10 Cihazınızı geliştirme için etkinleştirmeniz gerekir. Bkz: [Cihazınızı geliştirme için etkinleştirme](/windows/uwp/get-started/enable-your-device-for-development). Artık her Windows 10 cihaz için bir geliştirici lisansı gereklidir.

## <a name="universal-windows-apps"></a>Evrensel Windows uygulamaları
C#, Visual Basic, C++ veya JavaScript Windows 10 cihazları için bir evrensel Windows platformu uygulaması oluşturmak için tercih edilen geliştirme dilini seçin. Okuma [ilk uygulamanızı oluşturma](/windows/uwp/get-started/your-first-app) veya izleme [araçları için Windows 10 genel bakış](https://channel9.msdn.com/Series/ConnectOn-Demand/229) video.

Mevcut Windows Store 8.1 uygulamaları, Windows Phone 8.1 uygulamaları veya Visual Studio 2015 ile oluşturulan Evrensel Windows uygulamalarını varsa, bu uygulamalar en son Evrensel Windows Platformu'nu kullanmak için bağlantı noktası gerekir. Bkz: [Windows çalışma zamanını şuradan taşımak için UWP 8.x](/windows/uwp/porting/w8x-to-uwp-root).

Evrensel Windows uygulamanızı oluşturduktan sonra bir Windows 10 cihazına yükleyebiliyorum veya Windows Store için göndermek için uygulamanızı paketleme gerekir. Bkz: [paketleme uygulamaları](/windows/uwp/packaging/index).

## <a name="see-also"></a>Ayrıca bkz.
[Visual Studio'da platformlar arası Mobil Geliştirme](../cross-platform/cross-platform-mobile-development-in-visual-studio.md)
