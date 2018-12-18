---
title: Hızlı Başlangıç - Cookiecutter kullanarak Python projesi oluşturma
description: Bu hızlı başlangıçta, bir Cookiecutter şablonu kullanarak Python için bir Visual Studio projesi oluşturun.
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: b8ad6d53a337e6a2a0d879ff9637156fb3d6d791
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062709"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Hızlı Başlangıç: bir Cookiecutter şablonundan proje oluşturma

Kaydederler [Python desteği Visual Studio 2017'de yüklü](installing-python-support-in-visual-studio.md), Github'da yayımlanan birçok bir Cookiecutter şablonundan yeni bir proje oluşturmak kolaydır. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) şablonları keşfedin, şablon seçeneklerini giriş ve projeleri ve dosyaları oluşturmak için bir grafik kullanıcı arabirimi sağlar. Visual Studio 2017 ile eklemiştir ve Visual Studio'nun önceki sürümlerinde ayrı olarak yüklenebilir.

1. Bu hızlı başlangıçta, ilk burada gösterilen Cookiecutter şablonu için gerekli Python paketlerini içeren Anaconda3 Python dağıtım yükleyin. Visual Studio Yükleyicisi'ni çalıştırın, seçin **Değiştir**, seçeneklerini genişletip **Python geliştirme** seçin ve sağ tarafındaki **Anaconda3** (32 bit veya 64-bit). Yükleme, Internet hızına bağlı olarak biraz zaman alabilir, ancak bu, gerekli paketleri yüklemek için en basit yoludur unutmayın.

1. Visual Studio'yu başlatın.

1. Seçin **dosya** > **yeni** > **Cookiecutter gelen**. Bu komut şablonları burada göz atabilirsiniz Visual Studio'da bir pencere açılır. 

    ![Cookiecutter şablonundan yeni proje](media/projects-from-cookiecutter1.png)

1. Seçili **Microsoft/python-sklearn-sınıflandırıcı-cookiecutter** şablonu seçip **sonraki**. (İşlemi ilk kez Cookiecutter kullandığınızda birkaç dakika sürebilir.)

1. Sonraki adımda, yeni proje için bir konum kümesi **oluşturmak için** alan ve ardından seçin **Oluştur**.

    ![Cookiecutter kullanarak, proje özelliklerini ayarlama ikinci adım](media/projects-from-cookiecutter2.png)

1. İşlem tamamlandığında, ileti gördüğünüz **dosyaları başarıyla oluşturuldu.** Komutu seçin **Çözüm Gezgini'nde açın** projeyi açmak için.

1. Tuşuna **Ctrl**+**F5** veya **hata ayıklama** > **hata ayıklama olmadan Başlat** programı çalıştırmak için. 

    ![Python sklearn sınıflandırıcı cookiecutter şablonu projenin çıkışı](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Öğretici: Visual Studio'da Python ile çalışma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Cookiecutter uzantısını kullanma](using-python-cookiecutter-templates.md)
- [El ile var olan bir Python yorumlayıcısı tanımlayın](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Visual Studio 2015'te ve daha önce Python desteğini yükleme](installing-python-support-in-visual-studio.md)
- [Yükleme konumları](installing-python-support-in-visual-studio.md#install-locations)
