---
title: ARM ile desteklenen cihazlarda Visual Studio
description: ARM tabanlı işlemcilerle cihazlarda Visual Studio kullanımı için öneriler.
ms.date: 09/10/2020
ms.topic: conceptual
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 31fb209a3f19c052c19e98691b8643bb098887ee
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107295812"
---
# <a name="visual-studio-on-arm-powered-devices"></a>ARM destekli cihazlarda Visual Studio

> [!IMPORTANT]
> Visual Studio yalnızca x86 veya AMD64/x64 tabanlı işlemci kullanan cihazlarda desteklenir.

Visual Studio, x86 mimarisine göre hedef işlemciler için geliştirilmiştir ve ARM tabanlı işlemciler için Visual Studio 'nun hiçbir sürümü bulunmamaktadır. Ancak, Windows, Visual Studio 'Nun çalıştırabileceği [ARM üzerinde x86 öykünmesi](https://www.docs.microsoft.com/windows/uwp/porting/apps-on-arm-x86-emulation)sağlar. Visual Studio 'yu, x86 öykünmesi aracılığıyla bir ARM işlemcisinde çalıştırmak, Visual Studio 'nun performansını önemli ölçüde impairs ve Visual Studio 'daki çeşitli özellikler bu senaryoda çalışmak üzere tasarlanmamıştır. Bu nedenle, ARM tabanlı işlemciler kullanan cihazlarda Visual Studio 'Yu çalıştırmayı önermiyoruz ve bunun yerine uzaktan hedeflenen ARM cihazlarını öneririz.

## <a name="remote-targeting-arm-devices"></a>ARM cihazlarını uzaktan hedefleme
En iyi deneyim için, Visual Studio 'Yu ayrı, x86 ile desteklenen bir bilgisayarda kullanmanızı ve Visual Studio 'da ARM tabanlı cihazı hedeflemek için uzaktan dağıtım ve hata ayıklama özelliklerini kullanmanızı öneririz. Cihazda zaten yüklü olan Windows Evrensel uygulamalarında hata ayıklamak için bkz. [yüklü uygulama paketini hata ayıkla](../debugger/debug-installed-app-package.md) belgeleri. Yeni bir uygulama dağıtmak için bkz. [Windows Mağazası uygulaması uzak tley 'i çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md). Diğer tüm uygulama türleri için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md) belgeleri.

## <a name="tips-for-running-visual-studio-on-arm-devices"></a>ARM cihazlarda Visual Studio 'Yu çalıştırmaya yönelik ipuçları

### <a name="use-only-when-needed"></a>Yalnızca gerektiğinde kullanın
Yalnızca ARM 'e özgü çalışma için gerektiğinde Visual Studio 'Yu kullanarak zamandan en iyileştirin. ARM ile desteklenen herhangi bir cihazda performans kötü olur ve bu da normal kullanım için kabul edilemez olduğunu fark edersiniz.

### <a name="install-time"></a>Yükleme saati
Visual Studio 'nun yüklenmeye daha uzun sürmesini planlayın ve bir süre boyunca duraklamasını veya yeniden başlatmayı gerektir.
 
### <a name="remote-tools"></a>Uzak araçlar
Uzak cihazda çalışan bir uygulamada hata ayıklamak için, ARM için [Uzak araçları indirip yüklemeniz](../debugger/remote-debugging.md#download-and-install-the-remote-tools) gerekir.

### <a name="start-debugging-f5"></a>Hata ayıklamayı Başlat (F5)
Tüm Visual Studio projeleri, bir ARM cihazından hata ayıklamayı başlattığınızda (**F5**) projeleri yerel olarak başlatacak şekilde yapılandırılmamıştır. Uygulamanız yerel olarak çalışıyor olsa bile, Visual Studio 'Yu uzaktan hata ayıklama için yapılandırmanız gerekebilir. Daha fazla bilgi için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).

## <a name="we-need-your-help"></a>Yardımımız olması gerekir!
Visual Studio 'Nun ARM cihazlarda yerel olarak çalışmasını istiyorsanız, gerekli senaryolar ve destek hakkında bilgi almak istiyoruz. [Geliştirici topluluğu](https://developercommunity.visualstudio.com/idea/1161018/native-arm-support-for-visual-studio.html)' na giderek bizimle iletişime ulaşabilirsiniz.
