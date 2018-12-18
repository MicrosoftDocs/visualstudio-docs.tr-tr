---
title: Visual Studio için Mac turu
description: Mac için Visual Studio, ASP.NET Core Web siteleri ve iOS, Android, Mac ve Xamarin.Forms için Xamarin projeleri dahil olmak üzere, macOS üzerinde .NET uygulama derlemek için bir tümleşik geliştirme ortamı sağlar.
zone_pivot_groups: mac-ide-version
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.openlocfilehash: e1787f6d396121263d91633a4ee6d4dd8ed2c35f
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895801"
---
# <a name="visual-studio-for-mac-tour"></a>Visual Studio için Mac turu

Mac için Visual Studio, Mac'te bir mobil öncelikli ve bulut öncelikli bir geliştirme ortamına Xamarin'in mobil odaklı IDE, Xamarin Studio geliştikçe. Bu Geliştirici odaklı bir araç kullanıcılarınıza gereken tüm platformlar için uygulama oluşturmak için .NET gücünü kullanmanıza olanak sağlar.

Kullanıcı Deneyimi (UX) Visual Studio Mac için Windows çözümlemesiyle, ancak yerel macOS kullanımında benzer. Windows üzerinde Visual Studio önceden kullanılmış herkes için tanıdık bir deneyim, oluşturma, açma ve uygulama geliştirme olacaktır. Ayrıca, Mac için Visual Studio, çok güçlü bir IDE Windows çözümlemesiyle olun güçlü araçları kullanır. Roslyn derleyici platformu, yeniden düzenleme ve IntelliSense için kullanılır. MSBuild proje sistemi ve yapı altyapısı kullanın ve kaynak düzenleyicisinin TextMate paketi gruplarını destekler. Aynı hata ayıklayıcı altyapıları için Xamarin ve .NET Core uygulamaları ve aynı tasarımcıları Xamarin.iOS ve Xamarin.Android için kullanır.

Bu makalede, bazı platformlar arası uygulamaları oluşturmak için güçlü bir araç hale getiren özellikler sağlayan Mac için Visual Studio çeşitli bölümlerini keşfediyor.

## <a name="ide-tour"></a>IDE turu

Mac için Visual Studio, uygulama dosyalarını ve ayarlarını yönetme, uygulama kodu oluşturma ve hata ayıklama için çeşitli bölümler halinde düzenlenmiştir.

::: zone pivot="vsmac2019"

## <a name="visual-studio-for-mac-2019-start-window"></a>Visual Studio Mac 2019 başlangıç penceresi

> [!TIP]
> Önizleme Mac için Visual Studio 2019 olan [indirilebilir](install-preview.md) ve test etme.

Mac 2019 Önizleme için Visual Studio'yu başlattığınızda, yeni kullanıcılar bir oturum açma penceresi görürsünüz. Microsoft hesabınızla (varsa) Ücretli lisansı veya Azure abonelikleri bağlantısını etkinleştirmek için oturum açın. Basabilirsiniz **atla** ve daha sonra aracılığıyla oturum açma **Visual Studio > oturum** menü öğesi:

![Microsoft hesabınızda oturum açın](media/ide-tour-2019-start-signin.png)

Oturum açmış kullanıcıların görebileceği yeni _başlangıç penceresi_son projeler listesi gösterilir ve varolan açmak için düğmeler, proje veya yeni bir tane oluşturun:

![Son projelerden seçin veya yeni bir şeyler oluşturun](media/ide-tour-2019-start-projects.png)

::: zone-end
::: zone pivot="vsmac2017"

## <a name="welcome-screen-in-visual-studio-for-mac-2017"></a>2017 Mac için Visual Studio'da Hoş Geldiniz ekranı

Mac için Visual Studio başlatıldığında, görüntüler bir *Hoş Geldiniz ekranı*:

![Hoş Geldiniz ekranı](media/ide-tour-image1.png)

Hoş Geldiniz ekranında aşağıdaki bölümleri içerir:

- **Araç çubuğu** -Arama çubuğuna hızlı erişim sağlar. Bir çözüm yüklendiğinde, araç, hata ayıklama ve hataları görüntülemek için uygulama yapılandırmaları ayarlamak için kullanılır.
- **Başlarken** -Mac için Visual Studio ile çalışmaya başlama geliştiriciler için yararlı konularını hızlı erişim sağlar
- **Son çözümleri** -açın veya projeleri oluşturmak için uygun düğmeleri yanı sıra, en son açılan çözümleri hızlı erişim sağlar.
- **Geliştirici Haberleri** -en son Microsoft Developer bilgiler, güncel tutar bir haber akışı.

::: zone-end

## <a name="solutions-and-projects"></a>Projeler ve Çözümler

Aşağıdaki görüntüde, Mac için Visual Studio ile yüklenen bir uygulama gösterilmektedir:

![Yüklü bir uygulama ile Mac için Visual Studio](media/ide-tour-image17.png)

Aşağıdaki bölümler, Mac için Visual Studio temel alanları genel bir bakış sağlar

## <a name="solution-pad"></a>Çözüm bölmesi

Çözüm panelinde bir çözümdeki projelerin düzenler:

![Çözüm panelinde düzenlenmiş projeleri](media/ide-tour-image18.png)

Dosya kaynak kodu, kaynakları, kullanıcı arabirimi ve bağımlılıkları için platforma özgü projelere burada düzenlenir budur.

Projeler ve çözümler, Mac için Visual Studio kullanarak daha fazla bilgi için bkz: [projeler ve çözümler](projects-and-solutions.md) makalesi.

## <a name="assembly-references"></a>Derleme başvuruları

Her proje için derleme başvuruları, başvuruları klasörünün altında mevcuttur:

![Çözüm Bölmesi'nde başvurular klasörünün](media/ide-tour-image19.png)

Ek başvurular kullanarak eklenir **başvuruları Düzenle** başvuruları klasörü çift tıklayarak ya da seçerek görüntülenen iletişim kutusunda **başvuruları Düzenle** kendi bağlam menüsünde eylemleri:

![Başvurular iletişim Düzenle](media/ide-tour-image20.png)

Başvurular, Mac için Visual Studio kullanarak daha fazla bilgi için bkz: [bir projedeki başvuruları yönetme](managing-references-in-a-project.md) makalesi.

## <a name="dependencies--packages"></a>Bağımlılıkları / paketleri

Uygulamanızda kullanılan tüm dış bağımlılıkları içinde bir.Net Core olmanıza bağlı olarak bağımlılıklar veya paketler klasöründe depolanır veya Xamarin.iOS/Xamarin.Android projesi. Bunlar, genellikle bir NuGet biçiminde sağlanır.

NuGet, .NET geliştirme için en popüler paket yöneticisidir. Visual Studio'nun NuGet desteği ile kolayca arayabilir ve paketleri uygulaması projenize ekleyin.

Uygulamanıza bir bağımlılık eklemek için bağımlı sağ / paketleri klasörünü açın ve seçin **paketleri Ekle**:

![Bir NuGet paketi ekleme](media/ide-tour-image21.png)

Bir uygulamada bir NuGet paketi kullanarak bilgi bulunabilir [projenizdeki bir NuGet dahil olmak üzere proje](nuget-walkthrough.md) makalesi.

## <a name="refactoring"></a>Yeniden Düzenle

Mac için Visual Studio, kodunuzu yeniden değiştirmenin iki yararlı yol sağlar: bağlam Eylemler ve kaynak çözümleme. Daha fazla ilgili [yeniden düzenleme](refactoring.md) makalesi.

## <a name="debugging"></a>Hata Ayıklama

Mac için Visual Studio yerel hata ayıklayıcı bir izin verme hata ayıklama desteği Xamarin.iOS ve Xamarin.Mac Xamarin.Android uygulamaları için sahiptir. Mac için Visual Studio, Mono yazılım Mono çalışma zamanına uygulanan, IDE, tüm platformlar arasında hata ayıklama yönetilen kodu izin verme hata ayıklayıcıyı kullanır. Hata ayıklama hakkında ek bilgi için ziyaret edin [hata ayıklama](debugging.md) makalesi.

Hata ayıklayıcısı dizeleri, renkler, URL'ler, hem de boyutları, ortak ordinates ve bézier eğriler gibi özel türler için zengin görselleştiriciler içerir.

Hata Ayıklayıcı'nın veri görselleştirmeleri hakkında daha fazla bilgi için ziyaret [veri görselleştirmeleri](data-visualizations.md) makalesi.

## <a name="version-control"></a>Sürüm Denetimi

Mac için Visual Studio, Git, Subversion kaynak denetimi sistemleriyle tümleştirilir. Kaynak denetimi altında proje, çözüm adının yanında listelenen dal ile belirtilir:

![Kaynak denetimi altında proje belirtmek için dal adı](media/ide-tour-image22.png)

Dosyaları kaydedilmemiş değişikliklerle bir ek açıklama simgelerine çözüm bölmesinde üzerinde aşağıdaki görüntüde gösterildiği gibi sahiptir:

![Çözüm panelinde kaydedilmemiş dosyaları](media/ide-tour-image23.png)

Visual Studio'da sürüm denetimini kullanma ile ilgili daha fazla bilgi için bkz: [sürüm denetimi](version-control.md) makalesi.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE (üzerinde Windows)](/visualstudio/ide/visual-studio-ide)