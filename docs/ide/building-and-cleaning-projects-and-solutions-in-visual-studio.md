---
title: Projeler ve çözümler oluşturma ve temizleme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
f1_keywords:
- VS.BuildProjectPicker
- vs.batchbuild
helpviewer_keywords:
- Clean Solution command
- builds [Visual Studio], managing
- solution build configurations, starting
- Build Solution command
- project build configurations, starting
- build configurations, starting
- project build configurations, dependencies
- Rebuild Solution command
- solution build configurations, build order
- builds [Visual Studio], preparing
ms.assetid: 710891fd-379e-42c2-a84b-44a7af694ca0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c96a3b6699428b156a23ad643eb7958cb438b994
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349276"
---
# <a name="build-and-clean-projects-and-solutions-in-visual-studio"></a>Derleme ve temizleme projeleri ve Visual Studio çözümleri

Bu konudaki yordamları kullanarak, derleme, yeniden veya tüm veya bazı projeler veya bir çözümde proje öğeleri temizleyin. Adım adım bir öğretici için bkz [izlenecek yol: uygulama oluşturma](../ide/walkthrough-building-an-application.md).

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz: [derleme ve temizleme projeleri ve Visual Studio çözümleri için Mac](/visualstudio/mac/building-and-cleaning-projects-and-solutions).

> [!NOTE]
> Visual Studio sürümünüz kullanıcı Arabiriminde, bu konuda, etkin ayarlarınıza bağlı olarak açıklanmıştır öğesinden farklı olabilir. Ayarlarınızı, örneğin değiştirileceğini **genel** veya **Visual C++** ayarları seçebilirsiniz **Araçları** > **içeri ve dışarı aktarma ayarları**ve ardından **tüm ayarları Sıfırla**.

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Derleme, yeniden oluşturmanız veya bütün bir çözüm Temizle

1.  İçinde **Çözüm Gezgini**, seçin veya çözümü açın.

2.  Menü çubuğunda, **derleme**ve ardından aşağıdaki komutlardan birini seçin:

    -   Seçin **derleme** veya **Çözümü Derle** yalnızca bu dosyaları ve en son derlemeden sonra değiştirilen bileşenleri proje derlemek için.

        > [!NOTE]
        > **Derleme** komut olur **Çözümü Derle** ne zaman bir çözüm birden fazla proje içerir.

    -   Seçin **çözümü yeniden derle** "çözümü Temizle" ve sonra tüm proje dosyaları ve bileşenleri oluşturun.

    -   Seçin **çözümü Temizle** tüm ara ve Çıkış dosyalarını silmek için. Yalnızca proje ve bileşen dosyalarını sol yeni örneklerini Ara ve Çıkış dosyalarını sonra oluşturulabilir.

## <a name="to-build-or-rebuild-a-single-project"></a>Derleme veya tek projeyi yeniden derleyin

1.  İçinde **Çözüm Gezgini**, seçin veya projeyi açın.

2.  Menü çubuğunda, **derleme**seçin **derleme** *ProjectName* veya **yeniden** *ProjectName*.

    -   Seçin **derleme** *ProjectName* en son derlemeden sonra değiştirilen bileşenleri bu proje yalnızca oluşturulacak.

    -   Seçin **yeniden** *ProjectName* "projeyi Temizle" ve ardından Proje dosyalarını ve tüm proje bileşenler oluşturun.

## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Başlangıç projesi ve bağımlılıklarını oluşturma

1.  Menü çubuğunda, **Araçları** > **seçenekleri**.

2.  İçinde **seçenekleri** iletişim kutusunda **projeler ve çözümler** düğümünü seçip **derleme ve çalıştırma** sayfası.

     **Derleme ve çalıştırma** > **projeler ve çözümler** > **seçenekleri** iletişim kutusu açılır.

3.  Seçin **çalıştırıldığında yalnızca başlangıç projelerini ve bağımlılıkları derle** onay kutusu.

     Bu onay kutusu işaretli olduğunda, aşağıdaki adımlardan birini gerçekleştirdiğinizde yalnızca geçerli başlangıç projesi ve bağımlılıklarını oluşturulur:

    -   Menü çubuğunda, **hata ayıklama** > **Başlat** (**F5**).

    -   Menü çubuğunda, **derleme** > **Çözümü Derle** (**Ctrl**+**Shift** +  **B**).

    Bu onay kutusunun işareti kaldırıldığında, önceki komutlardan birini çalıştırdığınızda tüm projeler, bağımlılıklarını ve çözüm dosyaları oluşturulur. Varsayılan olarak, bu onay kutusu işaretli değildir.

## <a name="to-build-only-the-selected-visual-c-project"></a>Yalnızca seçilen Visual C++ projesi oluşturmak için

Seçin bir [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] proje ve ardından, menü çubuğunda, **derleme** > **yalnızca proje**ve aşağıdaki komutlardan birini:

- **Yalnızca derleme** *ProjectName*

- **Yalnızca yeniden** *ProjectName*

- **Temizleme yalnızca** *ProjectName*

- **Yalnızca bağlantı** *ProjectName*

Bu komutlar yalnızca uygulanacak [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] oluşturma, yeniden oluşturma, temizlenmesi veya herhangi bir proje bağımlılıkları veya çözüm dosyaları bağlama olmadan seçtiğiniz proje. Sürümünüze bağlı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], **yalnızca proje** alt daha fazla komut içerebilir.

## <a name="to-compile-multiple-c-project-items"></a>Birden çok C++ proje öğeleri derlemek için

İçinde **Çözüm Gezgini**, sahip birden çok dosya olabilir derlenmiş eylemleri seçin bu dosyalardan biri için kısayol menüsünü açın ve ardından **derleme**.

Dosyaları bağımlılıkları varsa, bağımlılık sırasına dosyaları derlenir. Derlediğinizde, kullanılabilir olmayan bir önceden derlenmiş üst bilgi dosyaları gereksiniminiz varsa, derleme işlemi başarısız olur. Derleme işlemi, geçerli etkin çözüm yapılandırmasını kullanır.

## <a name="to-stop-a-build"></a>Bir derlemeyi durdurmak için

Aşağıdaki adımlardan birini gerçekleştirin:

- Menü çubuğunda, seçin **derleme** > **iptal**.

- Tuşuna **Ctrl**+**sonu**.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: görüntüleme, kaydetme ve derleme günlüğü dosyalarını yapılandırma](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Derleme günlükleri alma](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
- [Derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md)
- [Nasıl yapılır: Hata ayıklama ve dağıtım yapılandırmalarını ayarlama](../debugger/how-to-set-debug-and-release-configurations.md)
- [C/C++ oluşturma başvurusu](/cpp/build/reference/c-cpp-building-reference)
- [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md)
- [Projeler ve çözümler](../ide/solutions-and-projects-in-visual-studio.md)
- [Derleme ve temizleme projeler ve çözümler (Mac için Visual Studio)](/visualstudio/mac/building-and-cleaning-projects-and-solutions)