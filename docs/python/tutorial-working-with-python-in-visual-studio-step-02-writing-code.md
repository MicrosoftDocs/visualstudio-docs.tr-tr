---
title: Python 2. adımda Visual Studio Öğreticisi, yazma ve kod çalıştırma
titleSuffix: ''
description: 2. adımı çekirdek kılavuzun Visual Studio'da kod düzenleme ve bir proje çalıştırma dahil olmak üzere, Python özellikleri.
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
ms.openlocfilehash: 9b2f1c4743652f0925ef083d0ca62a34485c219b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53054806"
---
# <a name="step-2-write-and-run-code"></a>2. adım: Yazma ve kod çalıştırma

**Önceki adımda: [yeni Python projesi oluşturma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)**

Ancak **Çözüm Gezgini** proje dosyaları, yönettiği yerdir *Düzenleyicisi* penceredir genellikle birlikte çalıştığınız *içeriği* dosyalarının kaynak kod gibi. Düzenleyici bağlam düzenlediğiniz, programlama dili (dosya uzantısına göre) gibi dosya türünü farkındadır ve teklifler özellikleri uygun söz dizimi renklendirme ve otomatik tamamlama gibi bu dil için IntelliSense kullanma.

1. Yeni bir "Python uygulaması" proje oluşturduktan sonra varsayılan boş adlı dosya *PythonApplication1.py* Visual Studio Düzenleyicisi'nde açık.

1. Düzenleyici'de yazmaya başlayın `print("Hello, Visual Studio")` ve Visual Studio IntelliSense otomatik tamamlama seçenekleri yol boyunca nasıl görüntülendiğine dikkat edin. Aşağı açılan listede anahatları belirlenmiş seçeneği tuşuna bastığınızda, kullanılan varsayılan tamamlanmadan **sekmesini** anahtarı. Tamamlamalar, en uzun ifadeleri veya tanımlayıcıları söz konusu olduğunda yararlıdır.

    ![IntelliSense otomatik tamamlama açılan menüsü](media/vs-getting-started-python-04-IntelliSense1b.png)

1. IntelliSense, kullanmakta olduğunuz deyimi, çağırdığınız işlev ve benzeri bağlı olarak farklı bilgi gösterir. İle `print` yazarak, işlev `(` sonra `print` çağrısı bir işlev belirtmek için bu işlevi tam kullanım bilgilerini görüntüler. IntelliSense açılanı kalın yazı tipinde geçerli bağımsız değişkeni de gösterir. (**değer** burada gösterildiği gibi):

    ![Bir işlev için IntelliSense otomatik tamamlama açılır](media/vs-getting-started-python-05-IntelliSense2b.png)

1. Deyim, aşağıdaki eşleşecek şekilde tamamlayın:

    ```python
    print("Hello, Visual Studio")
    ```

1. Deyim ayırır söz dizimi coloration fark `print` bağımsız `"Hello Visual Studio"`. Ayrıca, son geçici olarak silme `"` dize ve bildirim sözdizimi hataları içeren Visual Studio kod için kırmızı alt çizgi, gösterilmektedir. Ardından değiştirin `"` kodu düzeltmek için.

    ![IntelliSense söz dizimi renklendirme ve hata vurgulama](media/vs-getting-started-python-06-IntelliSense3b.png)

    > [!Tip]
    > Birinin geliştirme ortamı çok kişisel bir konudur çünkü Visual Studio, Visual Studio'nun görünümünü ve davranışını üzerinde tam denetim sağlar. Seçin **Araçları** > **seçenekleri** menü komutu ve ayarları keşfedin **ortam** ve **metin düzenleyici** Sekmeler. Varsayılan olarak yalnızca sınırlı sayıda seçenekleri görebilirsiniz; her programlama dili için tüm seçenekleri görmek için seçin **tüm ayarları göster** iletişim kutusunun alt kısmındaki. 

1. Kodu, yazılan bu noktada tuşuna basarak çalıştırın **Ctrl**+**F5** veya seçerek **hata ayıklama** > **hata ayıklama olmadan Başlat**  menü öğesi. Visual Studio, kodunuzdaki hataları hala olup olmadığını sizi uyarır.

1. Çalıştırıldığında programın sonuçlarını görüntüleyen bir konsol penceresi görünür alacağı bir Python yorumlayıcısı ile çalıştırın *PythonApplication1.py* komut satırından. Pencereyi kapatın ve Visual Studio Düzenleyicisi'ne dönmek için bir tuşa basın.

    ![İlk çalıştırma programının çıktısı](media/vs-getting-started-python-07-output.png)

1. İfadeler ve İşlevler için tamamlamalar ek olarak, IntelliSense sağlamak için Python tamamlamaları `import` ve `from` deyimleri. Bu tamamlamaları ortamınıza ve modüller üyelerinin hangi modüllerin kullanılabilen kolayca keşfetmenize yardımcı olur. Düzenleyici'de Sil `print` yazmaya başlayın ve satır `import `. Boşluk modüllerin listesini görünür:

    ![İçeri aktarma deyimi için kullanılabilir modüllerin gösteren IntellSense](media/vs-getting-started-python-08-import1.png)

1. Yazarak veya seçerek satır tamamlamak `sys`.

1. Sonraki satıra yazın `from` yeniden modüllerin listesini görmek için:

    ![IntellSense için kullanılabilir modüllerin gösteren bir deyiminden](media/vs-getting-started-python-09-import2.png)

1. Seçin veya yazın `math`, sonra bir boşluk ile yazmaya devam edin ve `import`, modül üyelerini görüntüler:

    ![IntellSense gösteren modülü üyeleri](media/vs-getting-started-python-10-import3.png)

1. Son içeri aktararak `sin`, `cos`, ve `radians` üyeleri, her biri için otomatik tamamlama kullanılabilir fark. İşiniz bittiğinde, kodunuz aşağıdaki gibi görünmelidir:

    ```python
    import sys
    from math import cos, radians
    ```

    > [!Tip]
    > Sözcükler, sözcük başlangıcında harf bölümlerini eşleşen yazın ve hatta karakter atlandı tamamlamaları alt dizeler ile çalışır. Bkz: [kod - tamamlamaları Düzenle](editing-python-code-in-visual-studio.md#completions) Ayrıntılar için.

1. 360 derece Kosinüs değerlerini yazdırmak için biraz daha fazla kod ekleyin:

    ```python
    for i in range(360):
        print(cos(radians(i)))
    ```

1. Programı yeniden çalıştırın **Ctrl**+**F5** veya **hata ayıklama** > **hata ayıklama olmadan Başlat**. İşiniz bittiğinde çıktı penceresini kapatın.

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Etkileşimli REPL penceresini kullanma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="go-deeper"></a>Daha ayrıntılı şekilde inceleyin

- [Kodu düzenleme](editing-python-code-in-visual-studio.md)
- [Biçim Kodu](formatting-python-code.md)
- [Kodu yeniden düzenleme](refactoring-python-code.md)
- [PyLint kullanma](linting-python-code.md)
