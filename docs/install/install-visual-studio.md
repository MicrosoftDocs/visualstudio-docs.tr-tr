---
title: Visual Studio'yu yükleme
titleSuffix: ''
description: Visual Studio, adım adım yüklemeyi öğrenin.
ms.custom: seodec18
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9160a5ebca6efe2cca48a2b8832a51fab3c6ca5a
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159743"
---
# <a name="install-visual-studio-2017"></a>Visual Studio 2017'yi yükleyin

Visual Studio'yu yüklemek için yeni bir yolunu Hoş Geldiniz! Bizim en yeni sürüm, seçin ve yalnızca gereksinim duyduğunuz özellikleri yüklemek için daha kolay bir şekilde kolaylaştırdık. Daha hızlı ve daha önce hiç olmadığı kadar sistemi daha az etkileyerek yükler, böylece biz de Visual Studio'nun minimum ayak kısalttık.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz: [Mac için Visual Studio](/visualstudio/mac/installation).

Else bu sürümdeki yenilikler hakkında daha fazla bilgi edinmek istiyorsunuz? Bkz. bizim [sürüm notları](/visualstudio/releasenotes/vs2017-relnotes).

Yüklenmeye hazır? Biz, bunu, adım adım konusunda rehberlik edelim.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>1. adım: bilgisayarınızın Visual Studio'ya hazır olduğundan emin olun

Visual Studio yükleme başlamadan önce:

1. Denetleme [sistem gereksinimleri](/visualstudio/productinfo/vs2017-system-requirements-vs). Bu gereksinimleri bilgisayarınıza Visual Studio 2017 destekleyip desteklemediğini bilmenize yardımcı olur.
2. En son Windows güncelleştirmelerini uygulayın. Bu güncelleştirmeler, bilgisayarınızda Visual Studio için en son güvenlik güncelleştirmelerini hem gerekli sistem bileşenlerine sahip olun.
3. Yeniden başlatma. Yeniden başlatma bekleyen yükleme veya güncelleştirmelerin Visual Studio yüklemesini engellememesini sağlar.
4. Alan boşaltın. Gereksiz dosyaları ve uygulamalar, % SYSTEMDRIVE %, örneğin, Disk Temizleme uygulamayı çalıştıran kaldırın.

Visual Studio 2017 ile yan yana Visual Studio'nun önceki sürümlerini çalıştıran hakkında sorular için bkz [Visual Studio uyumluluk ayrıntıları](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

## <a name="step-2---download-visual-studio"></a>Adım 2 - Visual Studio indirme

Ardından, Visual Studio önyükleyicisi dosyasını indirin. Bunu yapmak için aşağıdaki düğmeye tıklayın, Visual Studio 2017'ye tıklayın, istediğiniz sürümü seçin **Kaydet**ve ardından **Klasör Aç**.

 > [!div class="button"]
 > [Visual Studio 2017 İndir](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
<br/>

|         |         |
|---------|---------|
|  ![video kamera simgesini film](media/video-icon.png "bir video izleyin")  |    [Bir video izleyin](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Download-the-Visual-Studio-Installer-GgrESHD6D_3311787171) Visual Studio önyükleyicisi dosyasını indirin ve sizin için uygun olan Visual Studio sürümünü seçin. |

## <a name="step-3---install-the-visual-studio-installer"></a>3. adım - Visual Studio Yükleyicisi'ni yükleme

Ardından, Visual Studio Yükleyicisi'ni yüklemek için önyükleyici dosyasını çalıştırın. Yeni Basit yükleyicinin hem yüklemek ve Visual Studio 2017'yi özelleştirmek için ihtiyacınız olan her şeyi içerir.

1. Öğesinden, **indirir** klasöründe eşleşen veya benzer bir aşağıdaki dosyalar önyükleyici çift tıklayın:

   * **vs_enterprise.exe** için Visual Studio Enterprise
   * **vs_professional.exe** Visual Studio Professional
   * **vs_community.exe** Visual Studio Community için  <br><br>

   Bir kullanıcı hesabı denetimi bildirim alırsanız tıklayın **Evet**.

2. Microsoft onaylamak için isteriz [lisans koşulları](https://visualstudio.microsoft.com/license-terms/) ve Microsoft [gizlilik bildirimi](https://privacy.microsoft.com/privacystatement). **Devam**'a tıklayın.

   ![Lisans koşullarını ve gizlilik bildirimini](media/vs2017-privacy-and-license-terms.PNG "Microsoft lisans koşulları ve gizlilik bildirimi")

## <a name="step-4---select-workloads"></a>Adım 4 - Select iş yükleri

Yükleyici yüklendikten sonra bu özellik kümeleri seçerek yüklemenizi özelleştirmek için kullanabilirsiniz — veya iş yükleriniz — istediğiniz. İşte nasıl.

1. Bulmak istediğiniz iş yükünü **Visual Studio'yu** ekran.

   ![Visual Studio 2017 Kurulum iletişim kutusundan bir iş yükünü seçme](../install/media/install-visual-studio-community.png)

     Örneğin, ".NET masaüstü geliştirme" iş yükünü seçin. Bu, temel kod düzenleme açın ve projeye gerek kalmadan herhangi bir klasörden kodu düzenleme olanağı 20'den dil için destek içerir ve tümleşik kaynak kod denetimi varsayılan çekirdek Düzenleyicisi ile birlikte gelir.

2. İstediğiniz workload(s) seçtikten sonra tıklayın **yükleme**.

    Ardından, durum ekranları, Visual Studio yüklemenizin ilerleme durumunu gösteren görünür.

3. Yeni iş yükleri ve bileşenler yüklendikten sonra tıklayın **başlatma**.

> [!TIP]
> Yüklemeden sonra herhangi bir zamanda iş yükleri veya başlangıçta yüklenmedi bileşenleri yükleyebilirsiniz. Visual Studio'nun varsa **Araçları** > **araçları ve özellikleri Al...**  Visual Studio yükleyicisi açılır. Veya açık **Visual Studio yükleyicisi** Başlat menüsünden. Buradan yükleyin ve ardından istediğiniz bileşenleri ve iş yüklerini seçebileceğiniz **Değiştir**.

|         |         |
|---------|---------|
|  ![video kamera simgesini film](media/video-icon.png "bir video izleyin")  |    [Bir video izleyin](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Workloads-in-Visual-Studio-2017-jHE19HD6D_1611787171) Visual Studio Yükleyicisi'ni yükleyin ve ardından bir iş yükünü yükleyin. |

## <a name="step-5---select-individual-components-optional"></a>Adım 5 - tek bileşen seçin (isteğe bağlı)

Visual Studio yüklemenizi özelleştirmek için iş yüklerini özelliği kullanmayı istemiyorsanız, tek tek bileşenler yükleyerek bunu yapabilirsiniz. Tek tek bileşenleri seçmek için tıklatın **tek tek bileşenler** seçeneğini Visual Studio Yükleyicisi'nden, neleri istediğiniz ve daha sonra izleyin seçin yönergeleri.

  ![Visual Studio 2017 - tek tek bileşenleri yükle](media/vs2017-components.PNG "tek tek bileşenler Visual Studio'yu yükleyin")

  |         |         |
  |---------|---------|
  |  ![video kamera simgesini film](media/video-icon.png "bir video izleyin")  |   [Bir video izleyin](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Components-in-Visual-Studio-2017-ZMfaVID6D_7411787171) ayrı ayrı bir bileşen Visual Studio Yükleyicisi'ni kullanarak yükleme hakkında. |

## <a name="step-6---install-language-packs-optional"></a>6. adım - yükleme dil paketleri (isteğe bağlı)

Varsayılan olarak, yükleyici programı ilk kez çalıştığında işletim sisteminin dilini eşleştirmeye çalışır. Visual Studio 2017 bir dilde yüklemek için tıklayın **dil paketlerini** seçeneğini Visual Studio Yükleyicisi'nden ve yönergeleri izleyin.

  ![Visual Studio 2017 - yükleme dil paketlerini](media/vs2017-languages.PNG "Visual Studio'yu yükleyin dil paketleri")

  |         |         |
  |---------|---------|
  |  ![video kamera simgesini film](media/video-icon.png "bir video izleyin")  |   [Bir video izleyin](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Language-Packs-in-Visual-Studio-2017-ByT7yID6D_9011787171) dil paketi, Visual Studio Yükleyicisi'ni kullanarak yükleme hakkında. |

### <a name="change-the-installer-language-from-the-command-line"></a>Komut satırından yükleyici dilini değiştirme

Varsayılan dilini değiştirme başka bir komut satırından yükleyiciyi çalıştırarak yoludur. Örneğin, aşağıdaki komutu kullanarak İngilizce olarak çalıştırmak için yükleyici zorlayabilirsiniz: `vs_installer.exe --locale en-US`. Yükleyici, sonraki açışınızda çalıştırdığınızda bu ayar hatırlanır. Aşağıdaki Dil belirteçler yükleyici destekler: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-IT, ja-jp, ko-kr, pl-pl, pt-br, ru-ru ve tr-tr.

## <a name="step-7---change-the-installation-location-optional"></a>7. adım - (isteğe bağlı) yükleme konumunu değiştirme

**15.7 sürümündeki yeni**: Artık, Visual Studio yükleme ayak izini sistem sürücünüzde azaltabilir. İndirme önbelleğini, paylaşılan bileşenler, SDK'ları ve araçları farklı sürücülere taşıma ve Visual Studio en hızlı çalışan sürücüde korumak seçebilirsiniz.

  ![2017 - Visual Studio yükleme konumunu değiştirmek](media/installation-options-by-location.png "yükleme konumunu değiştirme")

Daha fazla bilgi için [Visual Studio yükleme konumlarını değiştirme](change-installation-locations.md) sayfası.

## <a name="step-8---start-developing"></a>8. adım - geliştirmeye başlayın

1. Visual Studio yüklemesi tamamlandıktan sonra tıklayın **başlatma** Visual Studio ile geliştirmeye başlamak için düğme.

2. Tıklayın **dosya**ve ardından **yeni proje**.

3. Bir proje türü seçin.

   Örneğin, [bir C++ uygulaması derleme](../ide/getting-started-with-cpp-in-visual-studio.md), tıklayın **yüklü**, genişletme **Visual C++** ve sonra oluşturmak istediğiniz C++ proje türü seçin.

   İçin [yapı bir C# uygulama](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md), tıklayın **yüklü**, genişletme **Visual C#** ve ardından C# proje derlemek istediğiniz türü.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 2017 güncelleştirmesi](update-visual-studio.md)
* [Visual Studio 2017'yi Değiştirme](modify-visual-studio.md)
* [Visual Studio 2017'yi kaldırın](uninstall-visual-studio.md)
* [Visual Studio 2017'in çevrimdışı yüklemesini oluşturma](create-an-offline-installation-of-visual-studio.md)
* [Visual Studio 2017'yi yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md)
* [Mac için Visual Studio'yu yükleyin](/visualstudio/mac/installation)