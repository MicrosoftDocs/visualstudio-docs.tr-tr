---
title: Evrensel Windows Platformu (UWP) uygulamaları geliştirin | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
caps.latest.revision: 50
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 24dfca5d4ac8432cbe659bb42ca54d0398c47c04
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766480"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Evrensel Windows Platformu (UWP) için uygulama geliştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Evrensel Windows platformu ve bizim bir Windows çekirdek ile aynı uygulama tüm Windows 10 cihazlarda phone'lardan masaüstlerine çalıştırabilirsiniz. Visual Studio 2015 ile Evrensel Windows uygulaması geliştirme araçları bu evrensel Windows uygulamaları oluşturun.  
  
 ![Evrensel Windows platformu](../cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")  
  
 Uygulamanızı Windows 10 telefonda, Windows 10 Masaüstü veya Xbox üzerinde çalıştırın. Bu, aynı uygulama paketi kullanılır! Windows 10 tek, birleştirilmiş çekirdek sunulmasıyla birlikte, tüm platformlardaki bir uygulama paketini çalıştırabilecek. Çeşitli platformları platform belirli davranışlardan faydalanmak için uygulamanızı ekleyebileceğiniz olan uzantı Sdk'lerine vardır. Örneğin, mobil cihazlar için bir uzantı SDK'sı, Windows phone'da basıldığında geri düğmesini işler. Projenizde bir uzantı SDK'sına başvuran, yalnızca, SDK bu platform üzerinde kullanılabilir olup olmadığını test etmek için çalışma zamanı denetimleri ekleyin. Her platform için aynı uygulama paketi nasıl sahip olmasıdır!  
  
 **Windows Çekirdek nedir?**  
  
 İlk kez Windows tüm Windows 10 platformlardaki ortak bir çekirdek için düzenlendi. Bir ortak kaynak, bir ortak Windows çekirdek, bir dosya g/ç yığını ve bir uygulama modeli yoktur. Kullanıcı Arabirimi için yalnızca bir XAML kullanıcı Arabirimi çerçevesi ve bir HTML kullanıcı Arabirimi çerçevesi yoktur. Bu nedenle uygulamanızın farklı Windows 10 cihazlarda çalıştırmak kolay kolaylaştırdık için harika bir uygulama oluşturmaya odaklanabilirsiniz.  
  
 **Evrensel Windows platformu tam olarak nedir?**  
  
 Bu yalnızca, sözleşmeler ve sürümleri koleksiyonudur. Bunlar, uygulamanızın çalıştırdığı hedef izin verir. Artık bir işletim sistemini hedef. Şimdi uygulamanıza bir veya daha fazla cihaz aileleri hedefleyin. Bu daha ayrıntılı bilgi edinin [platform Kılavuzu](http://msdn.microsoft.com/library/windows/apps/dn894631.aspx).  
  
## <a name="requirements"></a>Gereksinimler  
 Evrensel Windows uygulaması geliştirme araçları, uygulamanızın farklı cihazlarda nasıl göründüğünü görmek için kullanabileceğiniz öykünücü ile birlikte gelir. Bu öykünücü kullanmak istiyorsanız, bu yazılımın bir fiziksel makineye yüklemeniz gerekir. Fiziksel makinenin Windows 8.1 (x64) Professional sürümü çalıştırmalıdır veya sonraki bir sürümünü ve istemci Hyper-V ve ikinci düzey adres çevirisi (SLAT) destekleyen bir işlemci. Visual Studio bir sanal makinede yüklü olduğunda öykünücüleri kullanılamaz.  
  
 Gereken yazılım listesi aşağıda verilmiştir:  
  
- [Windows 10](http://windows.microsoft.com/windows/downloads)  
  
- [Visual Studio 2015](http://go.microsoft.com/fwlink/p/?LinkId=526725). Evrensel Windows uygulama geliştirme araçları isteğe bağlı özellikler listesinden seçili olduğundan emin olun. Bu araçlar olmasaydı, Evrensel uygulamaları oluşturmak mümkün olmayacaktır.  
  
  Bu yazılımı yükledikten sonra yapmanız [Windows 10 Cihazınızı etkinleştirme](https://msdn.microsoft.com/library/windows/apps/xaml/dn706236.aspx) geliştirme için. (Artık bir geliştirici lisansı her Windows 10 cihaz için ihtiyacınız.)  
  
  **Windows 8.1 ve Windows 7 desteği**  
  
  Windows 10 dışındaki bir platformda Visual Studio 2015 ile Evrensel Windows uygulamaları geliştirme kullanmayı tercih ederseniz kısıtlamaları şunlardır:  
  
- Windows 8.1: Uygulamayı yerel olarak (yalnızca bir uzak Windows 10 cihazında) çalıştıramazsınız. Visual Studio, ancak simülatörü değil öykünücüleri kullanabilirsiniz.  
  
- Windows 7: Uygulamayı yerel olarak (yalnızca bir uzak Windows 10 cihazında) çalıştıramazsınız. Visual Studio öykünücü veya simülatör ya da kullanamazsınız.  
  
  Geliştirme platformunuzu Windows 10 ise yalnızca XAML Tasarımcısı'nı kullanabilirsiniz.  
  
## <a name="universal-windows-apps"></a>Evrensel Windows uygulamaları  
 Tercih edilen geliştirme dilini C#, Visual Basic, C++ veya JavaScript arasından [Windows 10 cihazları için bir evrensel Windows uygulaması oluşturma](http://msdn.microsoft.com/library/windows/apps/xaml/dn609832.aspx#target_win10). Veya, watch [bu başlangıç videosu](http://channel9.msdn.com/Series/ConnectOn-Demand/229).  
  
 Mevcut Windows Store 8.1 uygulamaları, Windows Phone 8.1 uygulamaları ve evrensel Windows uygulamaları Visual Studio 2015 RC ile oluşturulmuş varsa [mevcut uygulamaları bu bağlantı noktası](http://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) en yeni evrensel Windows platformu kullanılacak.  
  
 Evrensel Windows uygulamanızı oluşturduktan sonra yapmanız gerekenler [uygulamanızı paketleme](https://msdn.microsoft.com/library/windows/apps/hh454036.aspx) bir Windows 10 cihazına yükleyebiliyorum veya Windows Store için gönderin.

