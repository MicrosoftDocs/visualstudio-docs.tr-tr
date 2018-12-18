---
title: Grafik Tanılama ile çalışmaya başlama | Microsoft Docs
ms.custom: seodec18
ms.date: 05/26/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 422a0fa4ea44cb3a605b8905282a5fe2a7e71e4c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055478"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Visual Studio Grafik Tanılama’ya Başlarken
Bu bölümde, grafik Tanılama'yı ilk kez kullanmak hazırlarsınız ve ardından bir Direct3D uygulamasından kareleri yakalayın ve grafik Çözümleyicisi'nde inceleyebilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 Visual Studio grafik tanılama kullanmak için Visual Studio Enterprise, Visual Studio Professional veya Visual Studio Community kullanmanız gerekir.  Visual Studio Code dahil olmak üzere diğer sürümleri, bu özelliği içermez.
 
 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]  
  
### <a name="windows-10-prerequisites"></a>Windows 10 önkoşulları  
 İsteğe bağlı bir Windows özelliği *grafik araçları* grafik tanılama Windows 10 tarafından gerekli yakalama ve kayıttan yürütme altyapısı sağlar.  
  
 Grafik Araçları'nı yükleme hakkında daha fazla bilgi için bkz. [yükleme grafik araçları Windows 10 için](#InstallGraphicsTools).  
  
##  <a name="InstallGraphicsTools"></a> Windows 10 için grafik araçları yükleme  
 Windows 10, grafik Tanılama Altyapısı isteğe bağlı bir adlı Windows özelliği tarafından sağlanan *grafik araçları*. Bu özellik, yakalama ve hedefleri olan uygulama olup olmadığını yakalanan ne olursa olsun, grafik bilgilerini Windows 10, windows veya kullandığı Direct3D'ın hangi sürümünün önceki bir sürümünü oynatmak için gereklidir. Grafik araçları özelliğinin önceden yüklemeyi seçebilirsiniz; Aksi durumda, Visual Studio'dan bir grafik Tanılama oturumu başlatın yüklü üzerine ilk zaman olur.  
  
#### <a name="to-install-graphics-tools-for-windows-10"></a>Windows 10 için grafik araçları yüklemek için  
  
1. Arama alanına yazın **uygulamalar ve Özellikler** açın **uygulamalar ve Özellikler** ayarları.
  
2. Sağ tarafındaki **uygulamalar ve Özellikler** iletişim kutusunda seçin **isteğe bağlı özellikleri Yönet** (altında **uygulamalar ve Özellikler**).

   **İsteğe bağlı özellikleri Yönet** iletişim kutusu görüntülenir.
  
3. İçinde **isteğe bağlı özellikleri Yönet** iletişim kutusunda seçin **özellik ekleme**. Yükleyebileceğiniz isteğe bağlı özelliklerin bir listesi görüntülenir.  
  
4. Seçin **grafik araçları** özellikler listesinden seçin **yükleme**.  
  
   Grafik araçları özelliğinin de, Windows 10 SDK'yı yüklediğinizde otomatik olarak yüklenir.  
  
> [!TIP]
>  Windows 10 'un isteğe bağlı grafik araçları özelliğinin basit yakalama ve kayıttan yürütme işlevlerini sağlar — komut satırı yakalama program gibi **dxcap.exe**— desteği, test etme ve tanılama senaryoları kullanılabilir makineler, geliştirici araçları yüklü değil. Daha fazla bilgi için [komut satırı Yakalama aracı](command-line-capture-tool.md) konu.  
  
## <a name="using-graphics-diagnostics-for-the-first-time"></a>İlk kez grafik tanılamayı kullanma  
 İhtiyacınız olan her şey sahip olduğunuza göre grafik Tanılama'yı kullanmaya başlamak hazırsınız. Şu adımları izlemeniz yeterlidir.  
  
### <a name="1---create-a-direct3d-app"></a>1 - bir Direct3D uygulaması oluşturma  
 Grafik Tanılama, harika keşfetmek için kendi Direct3D uygulaması zaten varsa! Aksi takdirde, aşağıdakilerden birini kullanın:

- **DirectX 11 uygulaması (Evrensel Windows)** veya **DirectX 12 uygulaması (Evrensel Windows)** Windows 10 için proje şablonları.
- [Direct3D 12 UAP örnek](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) Windows 10 için.  
  
  Geçmeden önce uygulamanın oluşturduğunuzdan emin olun.  
  
### <a name="2---start-a-graphics-diagnostics-session"></a>2 - bir grafik Tanılama oturumu başlatın  
 Artık ilk grafik tanılama oturumunuzu başlamak hazırsınız. Visual Studio'da ana menüde seçin **grafikler, grafik hata ayıklamayı Başlat hata ayıklama,**, veya tuşuna basarak **Alt + F5 tuşlarına**. Bu, uygulamanızı grafik tanılama altında başlar ve Visual Studio'da Tanılama oturumu windows görüntüler.  
  
> [!IMPORTANT]
>  Uygulamanızı Windows 10'da çalıştırıyorsanız ve isteğe bağlı grafik araçları özelliğinin henüz yüklemediyseniz, bunu şimdi yapmak istenir. Windows 10'da grafik tanılama kullanmadan önce yüklemeniz gerekir.  
  
### <a name="3---capture-frames"></a>3 - kareleri yakalayın  
 Uygulamanız başlar başlamaz kareleri yakalayın hazırsınız demektir.  
  
#### <a name="to-capture-single-frames"></a>Tek çerçeve yakalama  
  
-   Visual Studio'da **kare Yakala** Grafik araç çubuğu veya Tanılama oturumu penceresinden düğmesi. Ya da uygulamanızın odak varsa tuşuna basarak **Print Screen** klavyenizde anahtar.
  
#### <a name="to-capture-a-sequence-of-frames"></a>Bir dizi kare yakalamak için  
  
- Tanılama oturumu penceresinde, Visual Studio'da ayarlayın **Yakalanacak çerçeve** sonra istediğiniz sırayla Yakalanacak çerçeve sayısı için yukarıda açıklanan tek çerçeve yakalama için yöntemlerden birini kullanarak dizisi yakalayın.  
  
   Tek kare yeniden yakalamak için **Yakalanacak çerçeve** için *1*.  
  
  Çerçeve yakalamayı yalnızca işiniz bittiğinde, uygulamadan çıkmak veya tercih **Durdur** tanılama oturum penceresi ve Grafik araç çubuğu düğmesinden.  
  
### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4 - Grafik Çözümleyicisi yakalanan karelerde inceleyin  
 Artık yalnızca yakalanan çerçeveleri incelemek hazırsınız. Çerçeveyi analiz etmeye başlamak için tanılama oturumu penceresinden incelemek istediğiniz çerçeve çerçeve sayısını seçin. Bu çerçeve içinde açılır **grafik Çözümleyicisi**, Direct3D uygulamanızı işleme izlemek için nasıl kullandığını incelemek için grafik tanılama araçları kullanın, veya reddedebileceğiniz kullanın **çerçeve analizi** aracı performansını anlayın.  
  
 Tanılama oturumu penceresinden yanlış çerçeve seçtiğiniz ya da farklı bir çerçeveyi incelemek istediğiniz yeni bir grafik Çözümleyicisi'ni seçebilirsiniz. Üzerinde **hedef işleme** işleme hedef görüntü altında grafik günlüğü penceresinin sekmesini genişletin **çerçeve listesi** incelemek için farklı bir çerçeve seçin.  
  
 Grafik Çözümleyicisi araçları birlikte kullanma hakkında daha fazla bilgi için bkz. [örnekler](graphics-diagnostics-examples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Direct3D 12 grafik](/windows/desktop/direct3d12/direct3d-12-graphics)