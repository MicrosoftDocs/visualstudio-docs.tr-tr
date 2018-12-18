---
title: Temiz projeleri çözümleri oluşturun
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 05e8d13454ab9698ae855f1e937e85eb287a3a35
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057645"
---
# <a name="building-and-cleaning-projects-and-solutions-in-visual-studio"></a>Visual Studio'da Projeler ve Çözümler Oluşturma ve Temizleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konudaki yordamları kullanarak, derleme, yeniden veya tüm veya bazı projeler veya bir çözümde proje öğeleri temizleyin. Adım adım bir öğretici için bkz [izlenecek yol: uygulama oluşturma](../ide/walkthrough-building-an-application.md).

> [!NOTE]
>  Visual Studio sürümünüz kullanıcı Arabiriminde, bu konuda, etkin ayarlarınıza bağlı olarak açıklanmıştır öğesinden farklı olabilir. Ayarlarınızı değiştirmek için **Araçları** menüsünü seçip **içeri ve dışarı aktarma ayarları**. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

### <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Derleme, yeniden oluşturmanız veya bütün bir çözüm Temizle

1.  İçinde **Çözüm Gezgini**, seçin veya çözümü açın.

2.  Menü çubuğunda, **derleme**ve ardından aşağıdaki komutlardan birini seçin:

    -   Seçin **derleme** veya **Çözümü Derle** yalnızca bu dosyaları ve en son derlemeden sonra değiştirilen bileşenleri proje derlemek için.

        > [!NOTE]
        >  **Derleme** komut olur **Çözümü Derle** ne zaman bir çözüm birden fazla proje içerir.

    -   Seçin **çözümü yeniden derle** "çözümü Temizle" ve sonra tüm proje dosyaları ve bileşenleri oluşturun.

    -   Seçin **çözümü Temizle** tüm ara ve Çıkış dosyalarını silmek için. Yalnızca proje ve bileşen dosyalarını sol yeni örneklerini Ara ve Çıkış dosyalarını sonra oluşturulabilir.

### <a name="to-build-or-rebuild-a-single-project"></a>Derleme veya tek projeyi yeniden derleyin

1.  İçinde **Çözüm Gezgini**, seçin veya projeyi açın.

2.  Menü çubuğunda, **derleme**seçin **derleme**_ProjectName_ veya **yeniden**_ProjectName_.

    -   Seçin **derleme**_ProjectName_ en son derlemeden sonra değiştirilen bileşenleri bu proje yalnızca oluşturulacak.

    -   Seçin **yeniden**_ProjectName_ "projeyi Temizle" ve ardından Proje dosyalarını ve tüm proje bileşenler oluşturun.

### <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Başlangıç projesi ve bağımlılıklarını oluşturma

1. Menü çubuğunda, **Araçları**, **seçenekleri**.

2. İçinde **seçenekleri** iletişim kutusunda **projeler ve çözümler** düğümünü seçip **derleme ve çalıştırma** sayfası.

    **Derleme ve çalıştırma, projeler ve çözümler, Seçenekler** iletişim kutusu açılır.

3. Seçin **çalıştırıldığında yalnızca başlangıç projelerini ve bağımlılıkları derle** onay kutusu.

    Bu onay kutusu işaretli olduğunda, aşağıdaki adımlardan birini gerçekleştirdiğinizde yalnızca geçerli başlangıç projesi ve bağımlılıklarını oluşturulur:

   - Menü çubuğunda, **hata ayıklama**, **Başlat** (F5).

   - Menü çubuğunda, **derleme**, **Çözümü Derle** (CTRL + SHIFT + B).

     Bu onay kutusunun işareti kaldırıldığında, önceki komutlardan birini çalıştırdığınızda tüm projeler, bağımlılıklarını ve çözüm dosyaları oluşturulur. Varsayılan olarak, bu onay kutusu işaretli değildir.

### <a name="to-build-only-the-selected-visual-c-project"></a>Yalnızca seçilen Visual C++ projesi oluşturmak için

1. Seçin bir [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] proje ve ardından, menü çubuğunda, **derleme**, **yalnızca proje**ve aşağıdaki komutlardan birini:

   - **Yalnızca derleme** *ProjectName*

   - **Yalnızca yeniden** *ProjectName*

   - **Temizleme yalnızca** *ProjectName*

   - **Yalnızca bağlantı** *ProjectName*

     Bu komutlar yalnızca uygulanacak [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] oluşturma, yeniden oluşturma, temizlenmesi veya herhangi bir proje bağımlılıkları veya çözüm dosyaları bağlama olmadan seçtiğiniz proje. Sürümünüze bağlı [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], **yalnızca proje** alt daha fazla komut içerebilir.

### <a name="to-compile-multiple-c-project-items"></a>Birden çok C++ proje öğeleri derlemek için

1.  İçinde **Çözüm Gezgini**, sahip birden çok dosya olabilir derlenmiş eylemleri seçin bu dosyalardan biri için kısayol menüsünü açın ve ardından **derleme**.

     Dosyaları bağımlılıkları varsa, bağımlılık sırasına dosyaları derlenir. Derlediğinizde, kullanılabilir olmayan bir önceden derlenmiş üst bilgi dosyaları gereksiniminiz varsa, derleme işlemi başarısız olur. Derleme işlemi, geçerli etkin çözüm yapılandırmasını kullanır.

### <a name="to-stop-a-build"></a>Bir derlemeyi durdurmak için

1.  Aşağıdaki adımlardan birini gerçekleştirin:

    -   Menü çubuğunda, **derleme**, **iptal**.

    -   Seç Ctrl + Break anahtarları.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: görüntüleme, kaydetme ve yapılandırma derleme günlüğü dosyalarını](../ide/how-to-view-save-and-configure-build-log-files.md) [derleme günlükleri alma](../msbuild/obtaining-build-logs-with-msbuild.md) [derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md) [anlama derleme yapılandırmaları](../ide/understanding-build-configurations.md) [ Hata ayıklama ve dağıtım proje yapılandırmalarını](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e) [C/C++ oluşturma başvurusu](http://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d) [Devenv komut satırı anahtarları](../ide/reference/devenv-command-line-switches.md) [projeler ve çözümler](../ide/solutions-and-projects-in-visual-studio.md)
