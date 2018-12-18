---
title: Ipython REPL (etkileşimli pencere)
description: Paralel hesaplama etkileşimli özelliklere sahip bir kullanıcı dostu etkileşimli geliştirme ortamı için Visual Studio etkileşimli pencereye Ipython modu kullanın.
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 84e93d06e294ef11cc345eb4c443845421a8f834
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067809"
---
# <a name="use-ipython-in-the-interactive-window"></a>Etkileşimli pencerede Ipython kullanın

Visual Studio **etkileşimli** penceredir Ipython modunda etkileşimli paralel bilgi işlem özellikleri olan bir Gelişmiş henüz kullanımı kolay, etkileşimli geliştirme ortamı. Bu makalede Visual Studio'daki Ipython açıklanmaktadır **etkileşimli** penceresinde hangi tümü normal [etkileşimli pencere](python-interactive-repl-in-visual-studio.md) özellikleri de vardır.

Bu kılavuz için olmalıdır [Anaconda](https://www.continuum.io) Ipython ve gerekli kitaplıkları içeren yüklü, ortam.

> [!Note]
> IronPython desteklemiyor, Ipython üzerinde seçin olgu rağmen **etkileşimli seçenekleri** formu. Daha fazla bilgi için [özellik isteği](https://github.com/Microsoft/PTVS/issues/84).

1. Visual Studio'yu açın, geçiş **Python ortamları** penceresi (**görünümü** > **diğer Windows** > **Python ortamları** ) ve Anaconda ortamı seçin.

2. İncelemek **paketleri (Conda)** sekme (olarak görünür **pip** veya **paketleri**) emin olmak bu ortam için `ipython` ve `matplotlib` listelenir. Aksi durumda, buraya yükleyin. (Bkz [Python ortamları windows - paketleri sekmesinde](python-environments-window-tab-reference.md).)

3. Seçin **genel bakış** sekmenize **kullanım Ipython etkileşimli mod**. (Visual Studio 2015'te seçin **etkileşimli seçenekleri yapılandırın** açmak için **seçenekleri** iletişim kutusunda, ardından **etkileşimli mod** için **Ipython**seçip **Tamam**).

4. Seçin **açık etkileşimli pencere** ortaya çıkarmak için **etkileşimli** Ipython modunda penceresi. Etkileşimli mod yalnızca değişmişse penceresi sıfırlamanız gerekebilir; basmanız gerekebilir **Enter** yalnızca bir >>> istemi görünür, böylece bir komut istemi beğeni almak **[2]**.

    ![Etkileşimli pencerede Ipython modu](media/ipython-repl-03.png)

5. Aşağıdaki kodu girin:

   ```python
   import matplotlib.pyplot as plt
   import numpy as np
  
   x = np.linspace(0, 5, 10)
   y = x ** 2
   plt.plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
   ```

6. Son satırı girdikten sonra bir satır içi graf (Bu, isterseniz sağ alt köşesindeki üzerinde sürükleyerek yeniden boyutlandırabilirsiniz) görmeniz gerekir.

    ![Etkileşimli pencerede satır içi grafiği](media/ipython-repl-04.png)

7. Kod Düzenleyicisi'nde yazabilirsiniz REPL'de yazmak yerine seçin, sağ tıklatın ve seçin **etkileşime Gönder** komutu (veya basın **Ctrl**+**Enter**). Aşağıdaki kod düzenleyicisinde ile seçerek yeni bir dosyaya yapıştırmayı deneyin **Ctrl**+**A**, ardından gönderme **etkileşimli** penceresi. (Visual Studio kodu Ara ya da kısmi grafikleri vermeyi önlemek için bir birim olarak gönderir. Python projesi yoksa açıp seçili, farklı bir ortam ile Visual Studio açılır bir **etkileşimli** için hangi ortamı varsayılan olarak seçili penceresi **Python ortamları**penceresi.)

    ```python
    from mpl_toolkits.mplot3d import Axes3D
    import matplotlib.pyplot as plt
    import numpy as np
    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')
    for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):
        xs = np.arange(20)
        ys = np.random.rand(20)
        # You can provide either a single color or an array. To demonstrate this,
        # the first bar of each set is colored cyan.
        cs = [c] * len(xs)
        cs[0] = 'c'
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X')
    ax.set_ylabel('Y')
    ax.set_zlabel('Z')
    plt.show()
    ```

    ![Kod Düzenleyicisi'nden etkileşimli pencereye göndermek.](media/ipython-repl-05.png)

8. Dışında grafiklerini görmek için **etkileşimli** penceresi, bunun yerine kullanarak kod çalıştırın **hata ayıklama** > **hata ayıklama olmadan Başlat** komutu.

Ipython kaçış sistem Kabuk değişkeni değiştirme gibi başka birçok yararlı özellik yakalama çıkış, vb. vardır. Başvurmak [Ipython belgeleri](https://ipython.org/documentation.html) daha fazla bilgi için.

## <a name="see-also"></a>Ayrıca bkz.

- Jupyter kolayca ve yükleme olmadan kullanmak için ücretsiz deneyin [Azure not defterleri barındırılan hizmet](https://notebooks.azure.com/) olanak tanıyan tutun ve not defterlerinizi başkalarıyla paylaşın.

- [Azure veri bilimi sanal makinesi](/azure/machine-learning/data-science-virtual-machine/overview) ayrıca çok çeşitli diğer veri bilimi araçları ile birlikte Jupyter not defterlerini çalıştırmak için önceden yapılandırılmıştır.
