---
title: Visual Studio Öğreticisi 4. adım, Python hata ayıklama
titleSuffix: ''
description: Adım 4 çekirdek kılavuzun Visual Studio hata ayıklayıcıda Python kodu çalıştırmak nasıl yapılandırılacağını açıklayan, özelliklerin Python.
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
ms.openlocfilehash: 5facce6eff378586ece01b5774089e76058615f9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53060426"
---
# <a name="step-4-run-code-in-the-debugger"></a>4. adım: hata ayıklayıcıda kod çalıştırma

**Önceki adımda: [etkileşimli REPL penceresini kullanma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)**

Ek projeleri bir zengin düzenleme deneyimi, sağlama, yönetme ve **etkileşimli** penceresinde Visual Studio'nun sağladığı tam özellikli Python kodu için hata ayıklama. Hata ayıklayıcıda, her bir döngü yinelemesi dahil olmak üzere adım adım kodunuzu çalıştırabilirsiniz. Bazı koşullar doğru olduğunda da program duraklatabilirsiniz. Herhangi bir noktada hata ayıklayıcıda program duraklatıldığında tüm program durumunu inceleyebilir ve değişkenleri değiştirin. Bu tür eylemleri program hataları izlemek için gerekli olan ve dikkatli bir şekilde tam program akışını izlemek için çok yararlı yardımları de sağlar.

1. Değiştirin *PythonApplication1.py* aşağıdaki dosya. Bu farklılığa kodun genişletir `make_dot_string` böylece hata ayıklayıcısı ayrık adımları inceleyebilir. Ayrıca yerleştirir `for` içine döngü bir `main` işlevini ve bu işlevi çağrılarak açıkça çalıştırır:

    ```python
    from math import cos, radians

    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        rad = radians(x)                             # cos works with radians
        numspaces = int(20 * cos(radians(x)) + 20)   # scale to 0-40 spaces
        st = ' ' * numspaces + 'o'                   # place 'o' after the spaces
        return st

    def main():
        for i in range(0, 1800, 12):
            s = make_dot_string(i)
            print(s)

    main()
    ```

1. Kodun tuşlarına basarak düzgün çalıştığını onay **F5** veya seçerek **hata ayıklama** > **hata ayıklamayı Başlat** menü komutu. Bu komut, hata ayıklayıcıda kod çalışır ancak program çalışırken duraklatmak için herhangi bir şey yapmadınız olduğundan, birkaç yineleme için wave desen yalnızca yazdırır. Çıkış penceresini kapatmak için herhangi bir tuşa basın.

    > [!Tip]
    > Program tamamlandığında, çıkış penceresi otomatik olarak kapatmak için değiştirin `main()` aşağıdaki kod ile çağırın:
    >
    > ```python
    > if __name__ == "__main__":
    >     sys.exit(int(main() or 0))
    > ```

1. Bir kesme noktası ayarlamak `for` tıklayarak kez gri kenar boşluğunda, çizgi veya bu satırda düzeltme işareti yerleştirmek ve kullanarak deyimi **hata ayıklama** > **iki durumlu kesme noktası** (komutu **F9**). Kesme noktası (aşağı ok tarafından belirtildiği gibi) belirtmek için gri kenar kırmızı bir nokta belirir:

    ![Bir kesme noktası ayarlama](media/vs-getting-started-python-18-debugging1.png)

1. Hata ayıklayıcıyı yeniden başlatın (**F5**) ve kesme noktasını içeren satırda, kodunun durduğu çalıştıran bakın. Çağrı buradan inceleyebilirsiniz yığın ve değişkenleri inceleyebilirsiniz. Kapsamdaki değişkenler görünür **Otolar** bunların tanımlandığı zaman penceresi; anahtara ayrıca **Yereller** penceresinin Visual Studio tüm değişkenleri göstermek için alt kısımdaki görünümü bulur Geçerli kapsam (dahil olmak üzere işlevler), bunlar tanımlanan önce bile:

    ![Python için kesme noktası UI deneyimi](media/vs-getting-started-python-19-debugging2b.png)

1. Hata ayıklama araç çubuğu (aşağıda gösterilmiştir), Visual Studio penceresinin üst kısmında gözlemleyin. Bu araç yaygın hata ayıklama komutlara hızlı erişim sağlar (Ayrıca bulunabilir üzerinde **hata ayıklama** menüsü):

    ![Önemli hata ayıklama araç çubuğu düğmeleri](media/vs-getting-started-python-20-debugging3.png)

    Düğmeleri soldan sağa doğru şekilde:
    - **Devam** (**F5**) sonraki kesme noktasına kadar veya program tamamlama kadar programı çalıştırır.
    - **Tümünü Kes** (**Ctrl**+**Alt**+**sonu**) uzun süre çalışan bir program duraklatılır.
    - **Hata ayıklama Durdur** (**Shift**+**F5**) olduğu ve hata ayıklayıcı sonlandırılır her yerde programı durdurur.
    - **Yeniden** (**Ctrl**+**Shift**+**F5**) olduğu ve içinde baştan yeniden her yerde programı durdurur. hata ayıklayıcı.
    - **Sonraki bildirimi Göster** (**Alt**+**Num** **&#42;**) çalıştırmak için kod sonraki satıra geçer. Bu, en geçici bir hata ayıklama oturumu sırasında kodunuz içinden gidin ve burada hata ayıklayıcı duraklatıldı noktasına hızla döndürülecek istediğinizde yararlıdır.
    - **İçine adımla** (**F11**) sonraki satıra çağrılan işlevlerin girme, kodu çalıştırır.
    - **Step Over** (**F10**) sonraki kod satırına çağrılan işlevlere girmeye gerek kalmadan çalışır.
    - **Step Out** (**Shift**+**F11**) geçerli işlevin geri kalanında çalıştırır ve çağıran kodu duraklatır.

1. Atla `for` using deyimi **Step Over**. *Adımlama* hata ayıklayıcı herhangi bir işlev çağrıları dahil olmak üzere kod, geçerli satırı çalıştırır ve ardından hemen yeniden duraklatır anlamına gelir. Bildirim nasıl değişkeni `i` artık tanımlanan **Yereller** ve **Otolar** windows.

1. Çağıran kodun sonraki satırına üzerinden adımla `make_dot_string` ve duraklatır. **Step Over** Burada özellikle hata ayıklayıcı, tüm çalışmasını da anlamına gelir `make_dot_string` ve onu döndürdüğünde duraklatır. Ayrı bir kesme noktası var. mevcut değilse, hata ayıklayıcı bu işlevin içinde durdurmaz.

1. Kod içinde birkaç kez daha Adımlama devam etmek ve gözlemleyin nasıl değerleri **Yereller** veya **Otolar** penceresinde değişiklik.

1. İçinde **Yereller** veya **Otolar** penceresinde de çift **değer** ya da sütun `i` veya `s` değerini düzenlemek için değişkenleri. Tuşuna **Enter** veya değişiklikleri uygulamak için bu değeri tıklayın.

1. Kod kullanarak üzerinden Adımlama devam **içine adımla**. **İçine adımla** işlev çağrısı içinde bulunan gibi hata ayıklama bilgileri, hata ayıklayıcı girer anlamına gelir `make_dot_string`. Bir kez iç `make_dot_string` yerel değişkenlerini inceleyin ve kendi kodunuz içinde özellikle adım adım.

1. İle Adımlama devam **içine adımla** sonuna ulaştığında dikkat `make_dot_string`, sonraki adıma döndürür `for` yeni dönüş değeri ile döngüsü `s` değişkeni. Yeniden ilerleyerek `print` deyimi, dikkat **içine adımla** üzerinde `print` bu işleve geçmiyor. Bunun nedeni, `print` Python'da yazılmış değil ancak bunun yerine yerel kodu Python çalışma zamanını içinde.

1. Kullanmaya devam **içine adımla** , yeniden kadar içine oluncaya kadar `make_dot_string`. Ardından **Step Out** ve geri bildirim `for` döngü. İle **Step Out**, hata ayıklayıcı geri kalanında işlevi çalıştırır ve çağıran kodu otomatik olarak duraklatır. Hata ayıklamak istediğiniz uzun bir işlev bölümü basamaklı çok kullanışlıdır ancak rest üzerinden adım ve gerekmeyen çağıran kodu açık bir kesme noktası ayarlamak istiyor.

1. Sonraki kesme noktasına ulaşılana kadar programı çalıştırmaya devam etmek için kullanmak **devam** (**F5**). Bir kesme noktası olduğundan `for` döngüsünün sonraki yinelemesinde bölün.

1. Döngü yinelemesi yüzlerce Adımlama sağlamak can sıkıcı olabilir, böylece Visual Studio eklemenize olanak sağlayan bir *koşul* bir kesme noktası için. Yalnızca koşul karşılandığında hata ayıklayıcı kesme noktasında program ardından duraklatılır. Örneğin, üzerinde bir kesme noktası koşulla kullanabilirsiniz `for` BT'nin yalnızca duraklatır şekilde deyimi zaman değerini `i` 1600 aşıyor. Bu durum ayarlamak için kırmızı kesme noktası nokta sağ tıklayıp **koşullar** (**Alt**+**F9** > **C**). İçinde **kesme noktası ayarları** görünen açılan girin `i > 1600` ifade olarak **Kapat**. Tuşuna **F5** devam etmek ve programı bir sonraki kesme önce birçok yineleme çalıştırır gözlemleyin.

    ![Bir kesme noktası koşulu ayarlama](media/vs-getting-started-python-21-debugging4.png)

1. Program tamamlanana kadar çalıştırmak için kesme noktasına sağ tıklayıp seçme devre dışı **devre dışı kesme noktası** (**Ctrl**+**F9**). Ardından **devam** (veya basın **F5**) programı çalıştırmak için. Program sona erdiğinde, Visual Studio hata ayıklama oturumunu durdurur ve kendi düzenleme moduna döner. Kendi nokta tıklayarak kesme noktası silebilirsiniz, ancak bu, ayarlamış olduğunuz herhangi bir koşul da siler unutmayın.

> [!Tip]
> Python yorumlayıcısı kendisini başlatmak için bir hata gibi bazı durumlarda çıkış penceresi yalnızca kısa bir süre görünür ve tüm hata iletilerini görmek için bir fırsat vermeden otomatik olarak kapat. Bu durumda, projeye sağ **Çözüm Gezgini**seçin **özellikleri**seçin **hata ayıklama** sekmesine ve ardından eklemek `-i` için  **Yorumlayıcı bağımsız değişkenleri** alan. Bu bağımsız değişken neden olur, böylece girdiğiniz kadar penceresi açık tutulması bir program tamamlandıktan sonra etkileşimli moduna geçin yorumlayıcı **Ctrl**+**Z**  >  **Enter** çıkmak için.

## <a name="next-step"></a>Sonraki adım

> [!div class="nextstepaction"]
> [Python ortamınızda paketleri yükleme](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)

## <a name="go-deeper"></a>Daha ayrıntılı şekilde inceleyin

- [Hata Ayıklama](debugging-python-in-visual-studio.md)
- [Visual Studio'da hata ayıklama](../debugger/debugger-feature-tour.md) Visual Studio'nun tüm belgeler hata ayıklama özellikleri sağlar.
