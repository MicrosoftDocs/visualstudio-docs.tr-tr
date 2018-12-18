---
title: Python 3. adımda Visual Studio öğretici etkileşimli REPL
titleSuffix: ''
description: Adım 3 / Çekirdek izlenecek Python etkileşimli REPL penceresini kapsayan Visual Studio'da Python özellikleri.
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
ms.openlocfilehash: 7f237dde510ad9fd65416ae7521ebeed705781c2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066125"
---
# <a name="step-3-use-the-interactive-repl-window"></a>3. adım: etkileşimli REPL penceresini kullanma

**Önceki adımda: [yazma ve kod çalıştırma](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

Visual Studio **etkileşimli** penceresi Python için normal düzenleme-oluşturma-hata ayıklama döngüsü önemli ölçüde kısaltır bir zengin okuma-değerlendirme-print-loop (REPL) deneyimi sağlar. **Etkileşimli** penceresinde Python komut satırı REPL deneyiminin tüm özellikleri sağlar. Ayrıca, çok kaynak dosyaları Visual Studio'da kod değişimi Düzenleyici, aksi takdirde komut satırından yavaşlatan bir yöntemdir kolaylaştırır.

1. Açık **etkileşimli** projenin Python ortamında sağ tıklanarak penceresi **Çözüm Gezgini** (gibi **Python 3.6 (32-bit)** bir önceki grafikte gösterilen) ve seçme **açık etkileşimli pencere**. Alternatif olarak seçebileceğiniz **görünümü** > **diğer Windows** > **Python etkileşimli Windows** ana Visual Studio menüsünde.

1. **Etkileşimli** penceresi açılır standart düzenleyiciyle aşağıda **>>>** Python REPL istemi. **Ortam** aşağı açılan listesi ile çalışmak için belirli bir yorumlayıcıyı seçme olanak tanır. Önerilmesine de yapmak istediğiniz **etkileşimli** iki pencere ayırıcının sürükleyerek yapabileceğiniz daha büyük penceresi:

    ![Python etkileşimli penceresinde ve yeniden boyutlandırmak için sürükleme](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > Tüm Visual Studio windows bordering ayırıcılar sürükleyerek boyutlandırabilirsiniz. Bağımsız olarak Visual Studio çerçeve pencereleri Taşı ve çerçevesinde istiyor ancak bunları yeniden düzenleyebilir. Tüm Ayrıntılar için bkz. [pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md).

1. Gibi birkaç deyim girin `print("Hello, Visual Studio")` ifadeler gibi `123/456` sonuçlarını hemen görmek için:

    ![Python etkileşimli penceresinde sonuçlarını hemen](media/vs-getting-started-python-12-interactive2.png)

1. Bir işlev tanımı gibi çok satırlı bir deyim yazmaya başladığınızda **etkileşimli** penceresi gösterir Python'un **...**  satırları sağlayan, komut satırı REPL otomatik girintili yazma devam etmesini istemi:

    ![Python etkileşimli penceresinde deyimi devamlılık ile](media/vs-getting-started-python-13-interactive3.png)

1. **Etkileşimli** penceresi girdiğinizden ve çok satırlı geçmişi maddeler ile komut satırı REPL üzerine artırır her şeyin tam geçmişini sağlar. Örneğin, kolayca tüm tanımını çağırabilirsiniz `f` işlev tek bir birim olarak ve kolayca adla değiştirin `make_double`, yerine ' % s'işlevi satır yeniden oluşturuluyor.

1. Visual Studio için bir düzenleyici penceresinde birden çok kod satırlarını gönderebilir **etkileşimli** penceresi. Bu özellik, kaynak dosyada kod bakımı ve select bölümleri için kolayca gönderir tanır **etkileşimli** penceresi. Bu tür kod parçalarını bütün program çalıştırmak zorunda yerine hızlı REPL ortamı ile çalışabilirsiniz. Bu özelliği görmek için önce değiştirin `for` içinde döngü *PythonApplication1.py* aşağıdaki dosya:

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. Yalnızca belirli `import` ve `from` deyimlerinde *.py* dosyasını sağ tıklatın ve seçin **etkileşime Gönder** (veya basın **Ctrl** + **Girin**). Kod parçasını hemen yapıştırılır **etkileşimli** penceresi ve çalıştırın. Şimdi seçtiğiniz `make_dot_string` işlev ve söz konusu kod parçasını yeniden çalıştırır aynı komutu yineleyin. Kodu bir işlev tanımladığından hızlıca bu işlev birkaç kez çağırarak test edebilirsiniz:

    ![Kod etkileşimli pencereye göndermek ve test](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > Kullanarak **Ctrl**+**Enter** Düzenleyicisi'nde *olmadan* seçimi satıra kod çalıştıran **etkileşimli** Pencere ve giriş işaretini bir sonraki satırında otomatik olarak geçirir. Bu özellik ile tuşuna basarak **Ctrl**+**Enter** art arda yalnızca Python komut satırı ile mümkün olmayan kod adım adım için kullanışlı bir yol sağlar. Ayrıca sağlar hata ayıklayıcıyı çalıştıran ve mutlaka programınızı en baştan başlatmayı olmadan kodunuzda adım adım.

1. Ayrıca kopyalayın ve çok satırlı kod içine yapıştırabilirsiniz **etkileşimli** ile Python komut satırı REPL. yapmak zor olan penceresi aşağıdaki kod parçacığı gibi herhangi bir kaynaktan Yapıştırıldığında, **etkileşimli** penceresi içinde yazmış olarak varsa bu kod çalışır:

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Birden çok gönderme etkileşimli kullanarak kod satırlarını yapıştırma](media/vs-getting-started-python-15-interactive5.png)

1. Gördüğünüz gibi bu kodu düzgün çalışır ancak çıktısını çok liderlerini değil. Farklı adım değerinde `for` döngü cosine wave birkaçını göstermek. Neyse ki, çünkü tüm `for` döngü olduğu tek bir birim olarak REPL geçmişi, geri dönmek kolaydır ve hangi değişiklikler yapın, istediğiniz ve ardından test işlevi yeniden. İlk geri çağırma için yukarı ok tuşlarına basın `for` döngü. (Bunu yukarı yapmak ve okları geçmişinde döngüsü devam kadar) kodda gezinme başlatmak için sol veya sağ ok tuşuna basın. Gidin ve değiştirme `range` belirtimine `range(0, 360, 12)`. Tuşuna basarak **Ctrl**+**Enter** (kodda herhangi bir yere) tüm deyimi yeniden çalıştırmak için:

    ![Etkileşimli pencerede önceki bir deyim düzenleme](media/vs-getting-started-python-16-interactive6.png)

1. En iyi gibi bir değer bulana kadar farklı adım ayarları ile denemeler için işlemi tekrarlayın. Ayrıca wave aralığı, örneğin, uzatma tarafından tekrar yapabileceğiniz `range(0, 1800, 12)`.
 
1. Yazılmış kod memnun olduğunuzda **etkileşimli** penceresinde, sağ tıklatın ve seçin seçin **kopyalama kod** (**Ctrl** + **Shift**+**C**) ve ardından düzenleyiciye yapıştırın. Bu özelliği, Visual Studio'nun herhangi bir çıktı otomatik olarak atlar nasıl fark yanı sıra `>>>` ve `...` ister. Örneğin, kullanarak aşağıdaki resimde gösterilmektedir **kopyalama kod** komut istemleri ve çıkış içeren Seçimi:

    ![Etkileşimli pencere kopyalama kod komut istemleri ve çıkış seçimi](media/vs-getting-started-python-17-interactive7.png)

    Düzenleyiciye yapıştırın, yalnızca kod alın:

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    Tam içeriğini kopyalamak istiyorsanız **etkileşimli** pencere, çıktıyı ve istekleri dahil olmak üzere standart kullanmanız yeterlidir **kopyalama** komutu.

1. Hızlı REPL ortamı kullanmak olan ne yalnızca yaptığınızı **etkileşimli** rahatça projenizin kaynak dosyaya kod eklemek için küçük bir parça kodu, ayrıntılara çalışmak için penceresi. Artık çalıştırdığınızda, kod ile yeniden **Ctrl**+**F5** (veya **hata ayıklama** > **hata ayıklama olmadan Başlat**), siz istediğiniz tam sonuçları bakın.

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Hata ayıklayıcıda kod çalıştırma](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>Daha ayrıntılı şekilde inceleyin

- [Etkileşimli penceresini kullanma](python-interactive-repl-in-visual-studio.md)
- [Ipython REPL kullanma](interactive-repl-ipython.md)
