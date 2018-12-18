---
title: Visual Studio Öğreticisi Adım 6'da, Python, Git ile çalışma
titleSuffix: ''
description: 6. adımını bir çekirdek kılavuzun Visual Studio'nun Git ile ilgili özellikleri kapsayan Visual Studio'da Python.
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6c23a1d9835b7b065f24536c89a8f0befb03717c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53054482"
---
# <a name="step-6-work-with-git"></a>6. adım: Git ile çalışma

**Önceki adımda: [paketleri yükleyin ve Python ortamınızı yönetme](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Visual Studio, GitHub ve Azure depoları gibi hizmetleri yerel Git depoları ve uzak depolar ile doğrudan tümleştirme sağlar. Bir depo kopyalama, değişiklikleri yaptıktan ve dalların yönetiminin tümleştirmeyi içerir.

Bu makalede, var olan bir proje için yerel bir Git deposu oluşturma ve kendiniz Visual Studio'nun Git ilgili özelliklerin bazıları hakkında bilgi edinme, temel bir genel bakış sağlar.

1. Visual Studio'da projeden gibi açık bir projeyle [önceki adımda](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md), çözümü sağ tıklatın ve seçin **kaynak denetimine Çözüm Ekle**. Visual Studio Proje kodunuzu içeren yerel bir Git deposu oluşturur.

1. Visual Studio projesi Git ile ilgili bir Git deposu denetimlerinde yönetilir algıladığında Visual Studio penceresinin alt sağ köşesinde görüntülenir. Denetimler, işlemeler, değişiklik, depo ve dal adını gösterir. Ek bilgileri görmek için denetimlerin üzerine gelin.

    ![Visual Studio penceresine Git denetimde üzerine gelindiğinde ek bilgiler görüntülenir.](media/working-with-git-01.png)

1. Yeni bir depo oluşturun veya Git denetimleri seçin, Visual Studio açılır **Takım Gezgini** penceresi. (İle dilediğiniz zaman penceresini açabilirsiniz **görünümü** > **Takım Gezgini** menü komutu.) Açılan listeyi kullanarak arasında geçiş yapmak için üç ana bölme, penceresine sahip **Takım Gezgini** başlığı. **Eşitleme** yayımlama işlemleri sağlayan bölmesinde de seçmeniz halinde görünür **anında iletme** denetimi (yukarı ok simgesi):

    ![Yerel bir depo oluşturduktan sonra Visual Studio Takım Gezgini](media/working-with-git-02.png)

1. Seçin **değişiklikleri** (veya kalem simgesine Git denetimiyle) kaydedilmemiş değişiklikleri gözden geçirin ve bunları istediğiniz zaman uygulamak için.

    ![Kaydedilmemiş değişiklikler gösteren Visual Studio Takım Gezgini](media/working-with-git-03.png)

    Bir dosyasına çift tıklayarak **değişiklikleri** söz konusu dosya için bir fark görünümü açmak listesi:

    ![Bir dosyada yapılan değişiklikler için farkı görüntüle](media/working-with-git-05.png)

1. Seçin **dalları** (veya bir dal adı ile Git denetimi) dalları inceleyin ve birleştirme ve yeniden Temellendirme işlemleri gerçekleştirmek için:

    ![Takım Gezgini Visual Studio'da dal gösteriliyor](media/working-with-git-04.png)

1. Depo adı ile Git denetimi seçerek (**CosineWave** bir önceki resimde), **Takım Gezgini** gösterir bir **Connect** ile kolayca geçirebilirsiniz için arabirimi başka bir havuz tamamen.

1. Yerel bir depo kullanırken, yapılan değişiklikleri doğrudan depoya gidin. Uzak bir depoya bağlı değilseniz aşağı açılan üst bilgisinde seçin **Takım Gezgini**, seçin **eşitleme** geçmek **eşitleme** bölümünde ve ile çalışma **Çekme** ve **Fetch** komutları sunulan vardır.

## <a name="go-deeper"></a>Daha ayrıntılı şekilde inceleyin

Uzak bir Git deposundan proje oluşturma kısa kılavuzu için bkz [hızlı başlangıç: Python kodu Visual Studio'da bir depoyu kopyalamak](quickstart-03-python-in-visual-studio-project-from-repository.md).

Çekme istekleri, yeniden Temellendirme ve tek tek seçme değişiklikleri dallar arasındaki kod gözden geçirme, birleştirme çakışmalarını işleme dahil olmak üzere daha kapsamlı bir öğretici için bkz. [Azure depoları ve Git ile çalışmaya başlama](/azure/devops/repos/git/gitquickstart?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json&view=vsts&tabs=visual-studio).

## <a name="tutorial-review"></a>Öğretici gözden geçirme

Visual Studio'da Python üzerinde bu öğreticiyi tamamlamak tebrikler. Bu öğreticide öğrendiğinize göre nasıl yapılır:

- Projeler oluşturmak ve bir projenin içeriğini görüntüleyin.
- Kod Düzenleyicisi'ni kullanın ve bir projeyi çalıştırın.
- Kullanım **etkileşimli** penceresini yeni kod geliştirme ve kolayca kod düzenleyicisine kopyalayın.
- Visual Studio hata ayıklayıcıda tamamlanmış bir program çalıştırın.
- Paketleri yükleme ve Python ortamlarını yönetin.
- Bir Git deposunda kod ile çalışır.

Buradan, kavramlar ve nasıl yapılır kılavuzları, aşağıdaki makaleleri keşfedin:

- [Python için C++ uzantısı oluşturma](working-with-c-cpp-python-in-visual-studio.md)
- [Azure App Service’e yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Profil Oluşturma](profiling-python-code-in-visual-studio.md)
- [Birim testi](unit-testing-python-in-visual-studio.md)
