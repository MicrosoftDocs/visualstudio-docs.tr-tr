---
title: Visual Studio Öğreticisi 1. adım, Python'da bir proje oluşturun
titleSuffix: ''
description: Genel bakış ve adım 1 / Visual Studio'da yeni Python projesi oluşturma ve önkoşulları de dahil olmak üzere, Python özelliklerine ilişkin bir çekirdek kılavuz.
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
ms.openlocfilehash: 1aaf0c0258d502693b771cad66f9347dd60f80e8
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049861"
---
# <a name="tutorial-work-with-python-in-visual-studio"></a>Öğretici: Visual Studio'da Python ile çalışma

Python güvenilir, esnek, öğrenin, tüm işletim sistemlerinde kullanmak için ücretsiz daha kolay ve güçlü Geliştirici topluluğu ve çoğu ücretsiz kitaplıkları tarafından desteklenen yaygın bir programlama dilidir. Dil, geliştirme, web uygulamaları, web Hizmetleri, Masaüstü uygulamaları, komut dosyası ve bilimsel bilgi işleme dahil olmak üzere tüm yolla destekler ve birçok üniversiteler, uzmanları, sıradan geliştiriciler ve aynı şekilde profesyonel geliştiriciler tarafından kullanılır.

Visual Studio, Python için birinci sınıf dil desteği sağlar. Bu öğreticide, aşağıdaki adımlarla size yol gösterir:

- [0. adım: yükleme](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [1. adım: (Bu makale) bir Python projesi oluşturma](#step-1-create-a-new-python-project)
- [2. adım: Yazma ve Visual Studio IntelliSense nasıl çalıştığını görürsünüz kodu çalıştırın](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [3. adım: etkileşimli REPL penceresinde daha fazla kod oluşturma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [4. adım: Visual Studio hata ayıklayıcıda tamamlanmış program çalıştırma](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [5. adım: paketleri yükleyin ve Python ortamlarını yönetme](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [6. adım: Git ile çalışma](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

[!INCLUDE[tutorial-prereqs](includes/tutorial-prereqs.md)]

## <a name="step-1-create-a-new-python-project"></a>1. adım: yeni Python projesi oluşturma

A *proje* Visual Studio kaynak kodu, kaynaklar, yapılandırmaları vb. dahil olmak üzere tek bir uygulama oluşturmak için birlikte gelen tüm dosyaları nasıl yönettiği. Bir proje testini biçimlendirir ve tüm proje dosyaları yanı sıra birden çok proje arasında paylaşılan, dış kaynaklara arasındaki ilişkiyi tutar. Bu nedenle, uygulamanızı kolayca genişletin ve yalnızca geçici klasör, bir projenin ilişkileri yönetme komutlar daha çok daha kolay büyütün, metin dosyaları ve hatta kendi fikrinizi projeleri sağlar.

Bu öğreticide tek ve boş bir kod dosyasını içeren basit bir projeyle başlayın.

1. Visual Studio'da **dosya** > **yeni** > **proje** (**Ctrl** + **Shift**+**N**), hangi getirir **yeni proje** iletişim. Burada da şablonlara göz atın farklı diller arasında sonra projeniz için bir tane seçin ve Visual Studio'nun dosyaları nereye yerleştirir belirtin.

1. Python şablonları görüntülemek için seçin **yüklü** > **Python** sola veya "Python" arayın. Arama'yı kullanarak diller ağaç konumunda hatırlayamıyorsunuz olduğunda bir şablon bulmak için harika bir yoludur.

    ![Yeni Proje iletişim kutusunda gösterilen Python projeleri](media/vs-getting-started-python-01-new-project.png)

    Nasıl Visual Studio'da Python desteği proje şablonları, Bottle, Flask ve Django çerçeveleri kullanarak web uygulamaları da dahil olmak üzere çeşitli içerir dikkat edin. Bu izlenecek yolda amacı doğrultusunda, ancak boş bir proje ile başlayalım.

1. Seçin **Python uygulaması** şablon, proje için bir ad belirtin ve seçin **Tamam**.

1. Birkaç dakika sonra Visual Studio içinde proje yapısını gösterir. **Çözüm Gezgini** penceresi (1). Varsayılan kod dosyası (2) düzenleyicide açık durumdadır. **Özellikleri** penceresi (3) seçili herhangi bir öğe için ek bilgileri görüntülemek için de görünür **Çözüm Gezgini**, diskteki tam konumuna dahil.

    ![Çözüm Gezgini ile Python projesi](media/vs-getting-started-python-02-windows.png)

1. İle kendinizi alıştırın için birkaç dakikanızı **Çözüm Gezgini**, olduğu projenizde burada dosya ve klasörleri bulun.

    ![Genişletilmiş çeşitli özelliklerini göstermek için Çözüm Gezgini](media/vs-getting-started-python-03-solution-explorer.png)

    (1) kalın olarak vurgulanmış olduğu içinde verdiğiniz ad kullanarak projenize **yeni proje** iletişim. Disk üzerinde bu proje tarafından temsil edilen bir *.pyproj* proje klasörünüzdeki dosya.

    (2 üst düzey) bir *çözüm*, varsayılan olarak, projenizin aynı ada sahip. Tarafından temsil edilen bir çözüm, bir *.sln* dosya diskte, bir veya daha fazla ilgili proje için bir kapsayıcıdır. Örneğin, Python uygulamanız için C++ uzantısı yazıyorsanız, C++ proje aynı çözüm içinde bulunan. Çözüm projeleri için ayrılmış test programlar ile birlikte bir web hizmeti için bir proje de içerebilir. 

    (3) altında projenizin kaynak dosyalarına bakın, bu durumda tek bir *.py* dosya. Bir dosya seçmek özelliklerini görüntüler **özellikleri** penceresi. Bir dosyayı çift bu dosya için uygun yolu açılır.

    (4) de altında projedir **Python ortamları** düğümü. Genişletildiğinde, kullanabileceğiniz Python yorumlayıcılarını bakın. (5) bu ortama yüklenen kitaplıklar görmek için bir yorumlayıcı düğümünü genişletin.

    Herhangi bir düğüme sağ tıklayın veya öğesi **Çözüm Gezgini** geçerli komutları menüsüne erişmek için. Örneğin, **Yeniden Adlandır** komutu herhangi bir düğüm veya öğeyi proje ve çözüm de dahil olmak üzere, adını değiştirmenizi sağlar.

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Yazma ve kod çalıştırma](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="go-deeper"></a>Daha ayrıntılı şekilde inceleyin

- [Visual Studio'da Python projeleri](managing-python-projects-in-visual-studio.md).
- [Python.org Python dil hakkında bilgi edinin](https://www.python.org)
- [Yeni başlayanlar için Python](https://www.python.org/about/gettingstarted/) (python.org)
- [Microsoft Virtual Academy ücretsiz Python kursları](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Microsoft sanal Akademi üst Python sorular](https://aka.ms/mva-top-python-questions)
