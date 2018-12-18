---
title: Grafik Tanılama ile çalışmaya başlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59131181-1caa-4b7f-be4b-e84709634edf
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dde728b5617d50f672b67980c524e6d1d48e0b9a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049572"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Visual Studio Grafik Tanılama’ya Başlarken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde, grafik Tanılama'yı ilk kez kullanmak hazırlarsınız ve ardından bir Direct3D uygulamasından kareleri yakalayın ve grafik Çözümleyicisi'nde inceleyebilirsiniz.

## <a name="requirements"></a>Gereksinimler
 Visual Studio 2015'te grafik tanılama kullanmak için şu sürümlerden birine sahip olmalıdır:

- Visual Studio 2015 Enterprise

- Visual Studio 2015 Professional

- Visual Studio 2015 Community

  [!INCLUDE[downloadvs](../includes/downloadvs-md.md)]

### <a name="windows-10-prerequisites"></a>Windows 10 önkoşulları
 İsteğe bağlı bir Windows özelliği *grafik araçları* grafik tanılama Windows 10 tarafından gerekli yakalama ve kayıttan yürütme altyapısı sağlar.

 Grafik Araçları'nı yükleme hakkında daha fazla bilgi için bkz. [yükleme grafik araçları Windows 10 için](#InstallGraphicsTools).

### <a name="windows-81-prerequisites"></a>Windows 8.1 önkoşulları
 Windows Yazılım Geliştirme Seti (SDK) Windows 8.1 için Windows 8.1 grafik tanılamayı gereklidir ve Windows 8.1 ve Windows 8 için geliştirmeyi destekler yakalama ve kayıttan yürütme altyapısı sağlar.

 [Windows 8.1 Windows Yazılım Geliştirme Seti (SDK) indirin](https://msdn.microsoft.com/windows/desktop/bg162891.aspx)

 Windows 10, Windows 8.1 çalıştıran bir geliştirme makinesinden çalıştıran bir uzak kayıttan yürütme makinesi kullanmak için bir geliştirme makineniz ve kayıttan yürütme makinesi üzerinde isteğe bağlı grafik araçları özelliğinin Windows 10 SDK'yı yüklemeniz gerekir.

##  <a name="InstallGraphicsTools"></a> Windows 10 için grafik araçları yükleme
 Windows 10, grafik Tanılama Altyapısı isteğe bağlı bir adlı Windows özelliği tarafından sağlanan *grafik araçları*. Bu özellik, yakalama ve hedefleri olan uygulama olup olmadığını yakalanan ne olursa olsun, grafik bilgilerini Windows 10, windows veya kullandığı Direct3D'ın hangi sürümünün önceki bir sürümünü oynatmak için gereklidir. Grafik araçları özelliğinin önceden yüklemeyi seçebilirsiniz; Aksi durumda, Visual Studio'dan bir grafik Tanılama oturumu başlatın yüklü üzerine ilk zaman olur.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Windows 10 için grafik araçları yüklemek için

1. Üzerinde **Başlat** menüsünde seçin **ayarları**. **Ayarları** iletişim kutusu görüntülenir.

2. İçinde **ayarları** iletişim kutusunda seçin **sistem**, ardından **yüklenen uygulamalar** sistem ayarları listesinden.

3. Sağ tarafındaki **ayarları** iletişim kutusunda seçin **isteğe bağlı özellikleri Yönet** altında **yüklü uygulamalar ve Özellikler**. **İsteğe bağlı özellikleri Yönet** iletişim kutusu görüntülenir.

4. İçinde **isteğe bağlı özellikleri Yönet** iletişim kutusunda seçin **özellik ekleme**. Yükleyebileceğiniz isteğe bağlı özelliklerin bir listesi görüntülenir.

5. Seçin **grafik araçları** özellikler listesinden seçin **yükleme**.

   Grafik araçları özelliğinin de, Windows 10 SDK'yı yüklediğinizde otomatik olarak yüklenir.

> [!TIP]
>  Windows 10 'un isteğe bağlı grafik araçları özelliğinin basit yakalama ve kayıttan yürütme işlevlerini sağlar — komut satırı yakalama program gibi **dxcap.exe**— desteği, test etme ve tanılama senaryoları kullanılabilir makineler, geliştirici araçları yüklü değil. Daha fazla bilgi için [komut satırı Yakalama aracı](../debugger/command-line-capture-tool.md) konu.

## <a name="using-graphics-diagnostics-for-the-first-time"></a>İlk kez grafik tanılamayı kullanma
 İhtiyacınız olan her şey sahip olduğunuza göre grafik Tanılama'yı kullanmaya başlamak hazırsınız. Şu adımları izlemeniz yeterlidir.

### <a name="1---create-a-direct3d-app"></a>1 - bir Direct3D uygulaması oluşturma
 Grafik Tanılama, harika keşfetmek için kendi Direct3D uygulaması zaten var! Aksi durumda mevcut Direct3D örneklerden birini üzerinde kod Galerisi kullanabilirsiniz.

- Grafik tanılama Direct3D 12 Visual Studio 2015'i kullanarak Windows 10 ile denemek için deneyin [Direct3D 12 UAP örnek](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) Windows 10 için.

- Grafik tanılama Direct3D 11 Windows 10 veya Windows 8.1 ile denemek için kullanabileceğiniz **DirectX uygulaması (Evrensel Windows)** veya **DirectX uygulaması (Windows 8.1)** proje şablonları. Veya, bir şey daha ilgi çekici, deneyin [DirectX marble maze oyun örneği](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345) Windows 8.1 için.

  Geçmeden önce uygulamanın oluşturduğunuzdan emin olun.

### <a name="2---start-a-graphics-diagnostics-session"></a>2 - bir grafik Tanılama oturumu başlatın
 Artık ilk grafik tanılama oturumunuzu başlamak hazırsınız. Visual Studio'da ana menüde seçin **hata ayıklama, grafik tanılamayı Başlat**, veya tuşuna basarak **Alt + F5 tuşlarına**. Bu, uygulamanızı grafik tanılama altında başlar ve Visual Studio'da Tanılama oturumu windows görüntüler.

> [!IMPORTANT]
>  Uygulamanızı Windows 10'da çalıştırıyorsanız ve isteğe bağlı grafik araçları özelliğinin henüz yüklemediyseniz, bunu şimdi yapmak istenir. Windows 10'da grafik tanılama kullanmadan önce yüklemeniz gerekir.

### <a name="3---capture-frames"></a>3 - kareleri yakalayın
 Uygulamanız başlar başlamaz kareleri yakalayın hazırsınız demektir.

##### <a name="to-capture-single-frames"></a>Tek çerçeve yakalama

-   Visual Studio'da **kare Yakala** Grafik araç çubuğu veya Tanılama oturumu penceresinden düğmesi. Ya da uygulamanızın odak varsa tuşuna basarak **Print Screen**.

##### <a name="to-capture-a-sequence-of-frames"></a>Bir dizi kare yakalamak için

- Tanılama oturumu penceresinde, Visual Studio'da ayarlayın **Yakalanacak çerçeve** sonra istediğiniz sırayla Yakalanacak çerçeve sayısı için yukarıda açıklanan tek çerçeve yakalama için yöntemlerden birini kullanarak dizisi yakalayın.

   Tek kare yeniden yakalamak için **Yakalanacak çerçeve** için `1`.

  Çerçeve yakalamayı yalnızca işiniz bittiğinde, uygulamadan çıkmak veya tercih **Durdur** tanılama oturum penceresi ve Grafik araç çubuğu düğmesinden.

### <a name="4--examine-captured-frames-in-the-graphics-analyzer"></a>4 – Grafik Çözümleyicisi yakalanan karelerde inceleyin
 Artık yalnızca yakalanan çerçeveleri incelemek hazırsınız. Çerçeveyi analiz etmeye başlamak için tanılama oturumu penceresinden incelemek istediğiniz çerçeve çerçeve sayısını seçin. Bu çerçeve içinde açılır **grafik Çözümleyicisi**, Direct3D uygulamanızı işleme izlemek için nasıl kullandığını incelemek için grafik tanılama araçları kullanın, veya reddedebileceğiniz kullanın **çerçeve analizi** aracı performansını anlayın.

 Tanılama oturumu penceresinden yanlış çerçeve seçtiğiniz ya da farklı bir çerçeveyi incelemek istediğiniz yeni bir grafik Çözümleyicisi'ni seçebilirsiniz. Üzerinde **hedef işleme** işleme hedef görüntü altında grafik günlüğü penceresinin sekmesini genişletin **çerçeve listesi** incelemek için farklı bir çerçeve seçin.

 Grafik Çözümleyicisi araçları birlikte kullanma hakkında daha fazla bilgi için bkz. [örnekler](../debugger/graphics-diagnostics-examples.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Direct3D 12 grafik](http://msdn.microsoft.com/en-us/52094ae3-3b44-4689-9ee7-1ba1b3a779cb)
