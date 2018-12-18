---
title: Projeler veya çözümler olmadan kod geliştirme
ms.date: 02/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- open folder [Visual Studio]
- anycode [Visual Studio]
- projects and solutions, develop code without
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5885fc8c62b8da4213446601f37700cc077eda8c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062370"
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Kodu Visual Studio'da projeler veya çözümler olmadan geliştirme

Visual Studio 2017'de, kod neredeyse tüm dizin tabanlı proje türünden Visual Studio'ya bir çözüm veya proje dosyası gerek kalmadan açabilirsiniz. Bu,, örneğin, github'da bir depoyu kopyaladığınızda, doğrudan Visual Studio'da oturum açın ve bir çözüm veya projeyi oluşturmak zorunda kalmadan geliştirmeye başlamak anlamına gelir. Gerekirse, özel derleme görevleri belirtin ve basit JSON dosyalarıyla parametreleri başlatın.

Visual Studio'da kod dosyalarınızı açtıktan sonra **Çözüm Gezgini** klasöründe tüm dosyaları görüntüler. Düzenlemeye başlamak için herhangi bir dosyaya tıklayabilirsiniz. Arka planda, dosyaları, IntelliSense, gezinti ve yeniden düzenleme özellikleri etkinleştirmek için Visual Studio başlatılır. Düzenleme, oluşturma, taşıma veya dosyaları silmek gibi Visual Studio değişiklikleri otomatik olarak izler ve IntelliSense dizinini sürekli olarak güncelleştirir. Kod söz dizimi renklendirme ve çoğu durumda, görünür temel IntelliSense deyim tamamlamada içerir.

## <a name="open-any-code"></a>Herhangi bir kod açın

Kod aşağıdaki yollardan biriyle bir Visual Studio'da oturum açabilirsiniz:

- Visual Studio menü çubuğunda **dosya** > **açık** > **klasör**ve ardından kodu konumuna göz atın.
- Kodu içeren bir klasör (sağ tıklama) bağlam menüsünden **Visual Studio'da Aç** komutu.
- Seçin **Klasör Aç** bağlantı Visual Studio **başlangıç sayfası**.
- Klavye kullanıcısıysanız basın **Ctrl**+**Shift**+**Alt**+**O** görselde Studio.
- Kod, klonlanan bir GitHub deposundan açın.

### <a name="to-open-code-from-a-cloned-github-repo"></a>Kopyalanan bir GitHub deposundan kodunu açmak için

Aşağıdaki örnek, bir GitHub deposunu kopyalayın ve ardından, kodu Visual Studio'da açmak gösterilmektedir. Bu yordamı izlemek için bir GitHub hesabınız var ve Git için Windows sisteminizde yüklü. Bkz: [yeni bir GitHub hesabı için kaydolmadan](https://help.github.com/articles/signing-up-for-a-new-github-account/) ve [Git için Windows](https://git-for-windows.github.io/) daha fazla bilgi için.

1. Github'da kopyalamak istediğiniz depoya gidin.

1. Seçin **Kopyala veya indir** düğmesine ve ardından **Panoya Kopyala** güvenli URL'nin için GitHub deposunu kopyalamak için açılır menüdeki düğmesi.

   ![GitHub Kopyala düğmesini](./media/VSIDE_Code_Clone.png)

1. Visual Studio'da **Takım Gezgini** açmak için sekmesinde **Takım Gezgini**. Sekmeyi görmüyorsanız açın **görünümü** > **Takım Gezgini**.

1. Takım Gezgini altında **yerel Git depoları** bölümünde, seçin **kopya** komut ve GitHub sayfasının URL'si metin kutusuna yapıştırın.

   ![Projesini kopyalama](./media/VSIDE_Code_Clone2.png)

1. Seçin **kopya** projenin dosyalarını yerel bir Git deposuna kopyalamak için düğme. Depo boyutuna bağlı olarak, bu işlem birkaç dakika sürebilir.

1. Depo içinde sisteminize kopyalanmış olan sonra **Takım Gezgini**, seçin **açık** yeni kopyalanan deponun (sağ tıklama) bağlam menüsünde komutu.

   ![Kopyalanan deponun](./media/VSIDE_Code_Clone3.png)

1. Seçin **klasör görünümünü göster** dosyaları görüntülemek için komut **Çözüm Gezgini**.

   ![Klasör görünümünü göster](./media/VSIDE_Code_Clone3_show.png)

   Artık dosya ve klasörleri kopyalanan deponun içinde göz atın ve da görüntüleyebilir ve kod söz dizimi renklendirme ile tam Visual Studio Kod Düzenleyicisi ve diğer özelliklere arayın.

| | |
|---------|---------|
| ![video kamera simgesini film](../install/media/video-icon.png)| [Bir video izleyin](https://mva.microsoft.com/en-us/training-courses/getting-started-with-visual-studio-2017-17798?l=lp3TOKD6D_6711787171) kopyalayın ve kodu bir GitHub deposundan Visual Studio'da açın. |

## <a name="run-and-debug-your-code"></a>Kodunuzdaki hataları ayıklamanıza ve çalıştırma

Kodunuzu Visual Studio'da bir proje veya çözüm olmadan hata ayıklaması yapabilirsiniz! Bazı diller hata ayıklamak için geçerli bir belirtmeniz gerekebilir *başlangıç dosyası* komut dosyası, yürütülebilir dosya veya proje gibi kod tabanındaki. Yanındaki aşağı açılan liste kutusunda **Başlat** araç çubuğunda tüm öğeleri özellikle belirlediğiniz yanı sıra algılar, Visual Studio başlangıç öğelerini listeler. Kod hata ayıklaması yaparken, visual Studio bu kod önce çalışır.

Kodunuzu Visual Studio içinde çalıştırmak için yapılandırma olduğu ne tür bir kod ve derleme araçları nelerdir bağlı olarak farklılık gösterir.

### <a name="codebases-that-use-msbuild"></a>MSBuild kullanan kod tabanlarında

MSBuild tabanlı kod tabanlarında görünen birden çok oluşturma yapılandırmasında olabilir **Başlat** düğmenin aşağı açılan listesi. Başlangıç öğesi olarak kullanın ve ardından istediğiniz dosyayı seçin **Başlat** hata ayıklamayı başlatmak için düğme.

> [!NOTE]
> İçin C# ve Visual Basic kod tabanlarında, olmalıdır **.NET masaüstü geliştirme** iş yükü yüklenmiş. C++ kod tabanlarında için olmalıdır **C++ ile masaüstü geliştirme** iş yükü yüklenmiş.

### <a name="codebases-that-use-custom-build-tools"></a>Kod tabanlarında özel derleme araçlarını kullanın

Derleme araçları, özel bir kod temelinde kullanılan sonra Visual Studio kullanarak kod oluşturma söylemelisiniz *derleme görevleri* içinde tanımlanan bir *.json* dosya. Daha fazla bilgi için [yapı özelleştirme ve hata ayıklama görevleri](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

### <a name="codebases-that-contain-python-or-javascript-code"></a>Bu kod tabanlarında Python veya JavaScript kodu içerir

Kod temelinizde Python veya JavaScript kodu içeriyorsa, tüm yapılandırmanız gerekmez *.json* dosyaları, ancak karşılık gelen iş yükünü yüklemek sahip. Başlangıç betiği de yapılandırmanız gerekir:

1. Yükleme [Node.js geliştirme](https://visualstudio.microsoft.com/vs/node-js/) veya [Python geliştirme](https://visualstudio.microsoft.com/vs/python/) seçerek iş yükü **Araçları** > **araçları ve özellikleriAl**, veya Visual Studio kapatıldıktan ve Visual Studio Yükleyicisi'ni çalıştırarak.

   ![Node.js ve Python geliştirme iş yükleri](media/python_nodejs_workloads.png)

1. İçinde **Çözüm Gezgini**, JavaScript veya Python dosyasını sağ tıklayın veya bağlam menüsünde **başlangıç öğesi olarak ayarla** komutu.

1. Seçin **Başlat** hata ayıklamayı başlatmak için düğme.

### <a name="codebases-that-contain-c-code"></a>Bu kod tabanlarında C++ kodu içerir

Visual Studio'da C++ kodu çözümlerin veya projelerin olmadan açma hakkında daha fazla bilgi için bkz: [C++ açık klasörü projelerde](/cpp/ide/non-msbuild-projects).

### <a name="codebases-that-contain-a-visual-studio-project"></a>Kod tabanlarında içeren bir Visual Studio projesi

Kod klasörünüz Visual Studio projesi içeriyorsa, projeyi başlangıç öğesi olarak belirleyebilirsiniz.

![Başlangıç öğesi olarak ayarla proje](media/customize-set-project-as-startup-item.png)

**Başlat** proje başlangıç öğesi olduğunu yansıtmak için düğmenin metin değişiklikleri.

![Başlat düğmesine proje](media/customize-start-button-project.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yapı özelleştirme ve hata ayıklama görevleri](../ide/customize-build-and-debug-tasks-in-visual-studio.md)
- [C++ için klasör Proje Aç](/cpp/ide/non-msbuild-projects)
- [C++'da CMake projeleri](/cpp/ide/cmake-tools-for-visual-cpp)
- [Kod ve metin düzenleyicide kod yazma](../ide/writing-code-in-the-code-and-text-editor.md)