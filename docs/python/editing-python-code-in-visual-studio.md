---
title: Python kodunu düzenleme
description: Python için Visual Studio, zengin IntelliSense kod parçacıkları ve biçimlendirme, linting ve yeniden düzenleme ile birlikte Gezinti özellikleri sağlar.
ms.date: 11/19/2018
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
ms.openlocfilehash: 15020111702d68c8c35fb09655018215e3a11d3b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062822"
---
# <a name="edit-python-code"></a>Python kodunu düzenleme

Kod düzenleyicisinde, geliştirme zamanınızın harcadığınız çünkü [Visual Studio'da Python desteği](installing-python-support-in-visual-studio.md) daha üretken olmanıza yardımcı olmak için işlevsellik sağlar. IntelliSense söz dizimi vurgulama, otomatik tamamlama, imza Yardımı, yöntemi geçersiz kılmalar, arama ve gezinti özellikleri içerir.

Düzenleyici ile de tümleştirilen **etkileşimli** Visual Studio'daki kod ikisi arasındaki değişimi kolaylaştırın,. Bkz: [Öğreticisi 3. adım: etkileşimli REPL penceresini kullanma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md) ve [etkileşimli penceresini - gönderme etkileşimli komutunu kullanma](python-interactive-repl-in-visual-studio.md#send-to-interactive-command) Ayrıntılar için.

|   |   |
|---|---|
| ![video kamera simgesini film](../install/media/video-icon.png "bir video izleyin") | [(Microsoft Virtual Academy) videoyu](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Editing-Python-Code-r2iQH5LWE_4605918567) Python kod (2 dk. 30 saniye) düzenleme, tanıtım için.|

Visual Studio'da kod düzenleme genel belgeler için bkz: [Kod Düzenleyicisi özellikleri](../ide/writing-code-in-the-code-and-text-editor.md). Ayrıca bkz: [anahat](../ide/outlining.md), kodunuzun belirli bölümleri odaklı kalmanıza yardımcı olur.

Visual Studio ayrıca kullanabileceğiniz **Nesne Tarayıcısı** (**görünümü** > **diğer Windows** > **Nesne Tarayıcısı**veya **Ctrl**+**W** > **J**) her modülde tanımlanmış Python sınıfların ve içinde tanımlanan işlevleri incelemek için sınıflar.

## <a name="intellisense"></a>IntelliSense

IntelliSense sağlar [tamamlamaları](#completions), [imza Yardımı](#signature-help), [hızlı bilgi](#quick-info), ve [kod renklendirme](#code-coloring). Visual Studio 2017 sürüm 15.7 ve üzeri da destek [tür ipuçlarını](#type-hints).

IntelliSense, performansı artırmak için **Visual Studio 2017 sürüm 15.5** ve daha önce projenizdeki her Python ortamı için oluşturulan bir tamamlanma veritabanı bağlıdır. Veritabanları eklemek, kaldırmak veya güncelleştirme paketleri yenileme gerekebilir. Veritabanı durumu gösterilir **Python ortamları** penceresi (bir eşdüzeyi **Çözüm Gezgini**) üzerinde **IntelliSense** sekme (bkz [ortamları penceresi başvuru](python-environments-window-tab-reference.md#intellisense-tab)).

**Visual Studio 2017 sürüm 15.6** ve daha sonra veritabanına bağımlı olmayan IntelliSense tamamlamaları sağlamak için farklı bir yol kullanır.

### <a name="completions"></a>Tamamlamaları

Tamamlamalar deyimleri, tanımlayıcıların ve düzenleyicide geçerli konumda uygun şekilde girilebilir başka bir deyişle olarak görünür. Listede gösterilen bağlama göre ve hatalı veya dikkat dağıtıcı seçenekleri atlamak için filtrelenir. Tamamlamalar, farklı ifadeler yazarak genellikle tetiklenir (gibi `import`) ve işleçler (nokta dahil), ancak olabilir bunları dilediğiniz zaman yazarak görünür **Ctrl**+**J**  >  **Alanı**.

![Visual Studio düzenleyicisinde üye tamamlama](media/code-editing-completions-simple.png)

Tamamlanma listesi açıkken, fare ok tuşlarını kullanarak istediğiniz tamamlama veya yazmaya devam etmek arama yapabilirsiniz. Daha fazla harf yazarken liste daha büyük olasılıkla tamamlamaları göstermek için filtrelenir. Kısayolları gibi kullanabilirsiniz:

- Başında 'argparse' bulmak için 'parse' gibi bir adı olmayan bir harf yazarak
- 'AbstractBaseClass' veya 'hava' 'as_integer_ratio' bulmak için bulmayı 'abc' gibi bir sözcük başlangıcında olan mektup yazmaya
- Harf, '' base64' bulmak için b64' gibi atlanıyor

Bazı örnekler:

![Visual Studio Düzenleyicisi'nde filtre ile üye tamamlama](media/code-editing-completion-filtering.png)

Bir süre sonra bir değişken veya yöntemleri ve olası türlerinin öznitelikleri ile birlikte bir değer yazdığınızda, üye tamamlamaları otomatik olarak görünür. Bir değişkeni birden fazla tür olabilir, listenin tüm olasılıkları hangi türlerin her tamamlama desteği göstermek için ek bilgilerle, tüm türlerden içerir. Bir tamamlama tüm olası türleri tarafından destekleniyorsa, ek açıklama gösterilmektedir.

![Visual Studio düzenleyicisinde birden çok türlerinde üye tamamlama](media/code-editing-completion-types.png)

Varsayılan olarak, "dunder" üyeleri (başlayan ve bir çift alt çizgi ile biten üyeler) gösterilmez. Genel olarak, bu tür üyelerin doğrudan erişilmemelidir. Bir tane gerekir, ancak başlarında çift alt çizgi yazarak bu tamamlamaları listeye ekler:

![Visual Studio düzenleyicisinde özel üye tamamlama](media/code-editing-completion-dunder.png)

`import` Ve `from ... import` ifadeler aktarılabilen modüllerin listesini görüntüler. İle `from ... import`, liste belirtilen modülünden içeri aktarılabilir üyeleri içerir.

![Visual Studio düzenleyicisinde tamamlama içeri aktarma](media/code-editing-completion-import.png)

`raise` Ve `except` ifadeler sınıfları hata türleri için olası bir listesini görüntüler. Listenin tüm kullanıcı tanımlı özel durumlar içermiyor olabilir, ancak uygun yerleşik özel durumlar hızlı bir şekilde bulmanıza yardımcı olur:

![Visual Studio düzenleyicisinde özel durum tamamlama](media/code-editing-completion-exception.png)

Yazarak bir dekoratör başlar ve olası dekoratörler gösterir. Bu öğelerin birçoğunu dekoratörler kullanışlı değildir; hangisini kullanacağınızı belirlemek için kitaplık belgelerine bakın.

![Visual Studio düzenleyicisinde dekoratör tamamlama](media/code-editing-completion-decorator.png)

> [!Tip]
> Tamamlamalar davranışını yapılandırabilirsiniz **Araçları** > **seçenekleri** > **metin düzenleyici**  >   **Python** > **Gelişmiş**. Bunlar arasında **filtresi listesi, arama dizesi tabanlı** yazdığınız sırada tamamlama önerileri ve filtreleme uygular (varsayılan denetlenir) ve **üye tamamlama üyelerini kesişimi görüntüler** yalnızca gösterir (varsayılan olarak işaretli değildir) tüm olası türleri tarafından desteklenen tamamlamalar. Bkz: [seçenekleri - tamamlama sonuçları](python-support-options-and-settings-in-visual-studio.md#completion-results).

### <a name="type-hints"></a>Tür ipuçları

*Visual Studio 2017 sürüm 15.7 ve üzeri.*

"Tür ipuçlarını" Python 3.5 + ([CESARETLENDİRİCİ 484](https://www.python.org/dev/peps/pep-0484/) (python.org) olan işlevler için bir ek açıklama söz dizimi ve bağımsız değişken türlerini belirten sınıflar dönüş değerleri ve sınıf öznitelikleri. İşlev çağrıları, bağımsız değişkenleri ve bu ek açıklamalarına sahip değişkenler geldiğinizde IntelliSense tür ipuçlarını görüntüler.

Aşağıdaki örnekte `Vector` sınıfı olarak bildirilen `List[float]`ve `scale` işlevi, bağımsız değişkenler ve dönüş değeri için tür ipuçları içerir. Bu işleve yapılan bir çağrı geldiğinizde tür ipuçlarını gösterir:

![Tür ipuçlarını görüntülemek için işlev çağrısının üzerinden vurgulama](media/code-editing-type-hints1.png)

Aşağıdaki örnekte, gördüğünüz nasıl özniteliklerini açıklamalı `Employee` sınıfı IntelliSense tamamlanma açılan bir öznitelik için görünür:

![IntelliSense tamamlanma gösteren türü ipuçları](media/code-editing-type-hints2.png)

Hataları çalışma zamanına kadar normal olarak görünmez olduğundan da tür ipuçlarına, proje boyunca doğrulamak yararlıdır. Bu amaç için bağlam menüsü komutu aracılığıyla sektörde standart MyPy aracı Visual Studio'yu tümleştirir **Python** > **Run Mypy** içinde **Çözüm Gezgini**:

![Çözüm Gezgini'nde MyPy bağlam menüsü komutu Çalıştır](media/code-editing-type-hints-run-mypy.png)

Komut istemlerini çalıştıran, mypy paketini yüklemek için gerekli. Visual Studio projesinde her bir Python dosyasında tür ipuçlarını doğrulamak için mypy sonra çalışır. Visual Studio'da hata görünür **hata listesi** penceresi. Bir öğenin seçilmesi pencerenin kodunuzdaki uygun satırına gider.

Basit bir örnek olarak, aşağıdaki işlev tanımı belirtmek için bir tür ipucu içeren `input` bağımsız değişken türü ise `str`bilgileriyse söz konusu işleve yapılan çağrı, bir tamsayı geçirin dener:

```python
def commas_to_colons(input: str):
    items = input.split(',')
    items = [x.strip() for x in items]
    return ':'.join(items)

commas_to_colons(1)
```

Kullanarak **Run Mypy** komutu bu kodda şu hata oluşturur:

![Tür ipuçlarını doğrulama mypy örnek sonucu](media/code-editing-type-hints-validation-error.png)

> [!Tip]
> Python 3.5 önce sürümleri için Visual Studio aracılığıyla sağladığınız tür ipuçları da görüntüler *saplama dosyalarını* (*.pyi*). Saplama dosyalarını doğrudan kodunuzu tür ipuçları dahil etmek istemediğiniz her ya da bunları doğrudan kullanmayan kitaplığı için tür ipuçlarını oluşturmak istediğinizde kullanabilirsiniz. Daha fazla bilgi için [oluşturmak için Python modüllerini saplamalar](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) mypy proje Wiki'de.
>
> Şu anda, Visual Studio açıklamalarda tür ipuçlarını desteklemez.

### <a name="signature-help"></a>İmza Yardımı

Açılış yazdığınızda, bir işlev çağıran kod yazarken, imza Yardımı görünür `(` ve mevcut belgeler ve parametre bilgileri görüntüler. Ayrıca, görünür zorlaştırabilir **Ctrl**+**Shift**+**alanı** içinde bir işlev çağrısı. Görüntülenen bilgiler, işlevin kaynak kodunu belgeleri dizelerde bağlıdır, ancak varsayılan değerler içerir.

![Visual Studio düzenleyicisinde imza Yardımı](media/code-editing-signature-help.png)

> [!Tip]
> İmza Yardımı devre dışı bırakmak için Git **Araçları** > **seçenekleri** > **metin düzenleyici** > **Python**  >  **Genel** temizleyin **deyim tamamlama** > **parametre bilgileri**.

### <a name="quick-info"></a>Hızlı bilgi

Fare işaretçisi bir tanımlayıcının geldiğinizde, hızlı bilgi araç ipucu görüntülenir. Tanımlayıcı bağlı olarak, hızlı bilgi olası değerleri veya türleri, tüm kullanılabilir belgelere, dönüş türleri ve tanımı konumları görüntüleyebilir:

![Visual Studio düzenleyicisinde hızlı bilgi](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Kod renklendirme

Kod renklendirme rengi değişkenler, ifadeler ve kodunuzun diğer bölümlerine Kod Analizi bilgileriyle kullanır. Örneğin, modülleri veya sınıflar için başvuru değişkenleri işlevleri veya diğer değerlere daha farklı bir renkte gösterilebilir ve parametre adları yerel veya genel değişkenleri farklı bir renkte görünür. (Varsayılan olarak, İşlevler kalın olarak gösterilmez):

![Kod ve söz dizimi renklendirme Visual Studio Düzenleyicisi'nde](media/code-editing-code-coloring.png)

Renkleri özelleştirmek için Git **Araçları** > **seçenekleri** > **ortam** > **yazı tipleri ve renkler** ve değiştirme **Python** girişleri **görüntü öğeleri** listesi:

![Visual Studio'da yazı tiplerini ve renkleri seçenekleri](media/code-editing-customize-colors.png)

> [!Tip]
> Renklendirme kodu devre dışı bırakmak için Git **Araçları** > **seçenekleri** > **metin düzenleyici** > **Python**  >  **Gelişmiş** temizleyin **çeşitli seçenekleri** > **renk türüne göre adları**. Bkz: [seçenekleri - çeşitli seçenekleri](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

## <a name="code-snippets"></a>Kod parçacıkları

Kod parçacıkları, dosyalarınızı bir kısayol yazıp tuşuna basarak eklenebilir kod parçalarını **sekmesini**, veya bu adı kullanıyor **Düzenle** > **IntelliSense**  >  **Kod parçacığı Ekle** ve **Surround With** seçme komutlarını **Python**, istenen kod parçacığı seçildikten sonra.

Örneğin, `class` bir sınıf tanımı ekleyen bir kod parçacığı bir kısayol bulunur. Yazarken otomatik tamamlama listede görüntülenen kod parçacığının gördüğünüz `class`:

![Sınıf kısayol için kod parçacığı](media/code-editing-code-snippet-class.png)

Tuşuna basarak **sekmesini** rest sınıfı oluşturur. Vurgulu alanlar arasında hareket sonra adı ve tabanlar liste üzerinde yazabilirsiniz **sekmesini**, tuşuna **Enter** gövdesi yazmaya başlamak için.

![Öne çıkan özellikleri alanlara tamamlayabilmeniz için bir kod parçacığı](media/code-editing-code-snippets.png)

### <a name="menu-commands"></a>Menü komutları

Kullanırken **Düzenle** > **IntelliSense** > **kod parçacığı Ekle** menü komutu, siz ilk select **Python**, ardından bir kod parçacığı seçin:

![Kod parçacığı Ekle komutu aracılığıyla kod parçacığı seçme](media/code-editing-code-snippet-insert.png)

**Düzenle** > **IntelliSense** > **Surround With** komut, benzer şekilde, yerleştirir geçerli seçimi içinde seçili bir metin düzenleyicisinde Yapısal öğesi. Örneğin, biraz kod aşağıdaki gibi olan varsayalım:

```python
sum = 0
for x in range(1, 100):
    sum = sum + x
```

Bu kod ve seçerek **Surround With** komutu kullanılabilir kod parçacıkları bir listesini görüntüler. Seçme **def** seçili kod içinde bir işlev tanımı ve liste yerlerden **sekmesini** anahtar vurgulanan işlev adı ve bağımsız değişkenleri arasında gezinmek için:

![Surround With komutu için kod parçacıkları kullanma](media/code-editing-code-snippet-surround-with.png)

### <a name="examine-available-snippets"></a>Kullanılabilir kod parçacıkları inceleyin

Kullanılabilir kod parçacıkları görebilirsiniz **kod parçacıkları Yöneticisi**, kullanılarak açılmış **Araçları** > **kod parçacıkları Yöneticisi** menü komutu ve seçme **Python** dili olarak:

![Visual Studio'da kod parçacıkları Yöneticisi](media/code-editing-code-snippets-manager.png)

Kendi parçacıklarınızı oluşturmak için bkz [izlenecek yol: bir kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md).

Paylaşmak istediğiniz bir harika bir kod parçacığı yazarsanız, içinde bir gist göndermekten çekinmeyin ve [bize bildirin](https://github.com/Microsoft/PTVS/issues). Visual Studio'nun gelecekteki bir sürümde eklemek mümkün olabilir.

## <a name="navigate-your-code"></a>Kodunuzda gezinme

Visual Studio'da Python desteği için hangi kaynak kodu kullanılabilir kitaplıklar gibi kodunuzu içinde hızlıca gezinmek için birkaç yol sağlar: [gezinti çubuğu](#navigation-bar), [ **Tanıma Git** ](#go-to-definition), [ **Gidin**](#navigate-to), ve [ **tüm başvuruları Bul**](#find-all-references). Visual Studio ayrıca kullanabileceğiniz [ **Nesne Tarayıcısı**](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser).

### <a name="navigation-bar"></a>Gezinti çubuğu

Gezinti çubuğunda, her Düzenleyicisi penceresinin üst kısmında görüntülenir ve iki düzeyli listesini tanımları içerir. Soldaki aşağı açılan, üst düzey bir sınıf ve işlev tanımları geçerli dosyadaki içerir. doğru açılan sola gösterilen kapsamındaki tanımlarını listesini görüntüler. Düzenleyicide yerleri gibi geçerli Bağlamınızı gösterilecek listelerini güncelleştirmek ve bir giriş doğrudan atlamak için bu listeleri de seçebilirsiniz.

! [Gezinti çubuğu] Visual Studio editor(media/code-editing-navigation-bar.png) içinde

> [!Tip]
> Gezinti çubuğunu gizlemek için şuraya gidin: **Araçları** > **seçenekleri** > **metin düzenleyici** > **Python**  >  **Genel** temizleyin **ayarları** > **gezinti çubuğu**.

### <a name="go-to-definition"></a>Tanıma Git

**Tanıma Git** hızlı bir şekilde (örneğin, bir işlev adı, sınıf veya değişken), bir tanımlayıcının kullanıma karşı kaynak koduna tanımlandığı atlar. Bir tanımlayıcı sağ tıklatıp seçerek çağırma **tanıma** veya giriş işaretini tanımlayıcısı ve tuşlarına basarak yerleştirerek **F12**. Kaynak kodu kullanılabilir olması koşuluyla, kod ve dış kitaplıkları çalışır. Kitaplığı kaynak kodunu kullanılamıyorsa **tanıma** atlar ilgili `import` deyim için bir modül başvurusu veya bir hata gösterir.

![Visual Studio'da Tanıma Git komutu](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Gidin

**Düzenle** > **gitmek için** komut (**Ctrl**+**,**) bir arama kutusu Düzenleyicisi'nde görüntüler. Burada, herhangi bir dizesini yazın ve kodunuzda bir işlev, sınıf veya o dizeyi içeren bir değişkeni tanımlar olası eşleşmeleri görmek kullanabilirsiniz. Bu özellik, benzer bir özellik olarak sağlar. **tanıma** ancak tanımlayıcının kullanımını bulmak zorunda kalmadan.

Herhangi bir ad çift veya ok tuşlarını seçerek ve **Enter**, bu tanımlayıcının tanımına gider.

![Visual Studio komut gidin](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Tüm Başvuruları Bul

**Tüm başvuruları Bul** herhangi bir tanımlayıcı hem olduğu bulmak için kullanışlı bir yol tanımlanır ve içeri aktarmalar ve atamaları dahil olmak üzere kullanılır. Bir tanımlayıcı sağ tıklatıp seçerek çağırma **tüm başvuruları Bul**, ya da giriş işaretini tanımlayıcısı ve tuşlarına basarak yerleştirerek **Shift**+**F12**. Listedeki bir öğeye çift tıklatarak konumuna gider.

![Tüm başvuruları sonuçları bulma](media/code-editing-find-all-references.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme](formatting-python-code.md)
- [Yeniden Düzenleme](refactoring-python-code.md)
- [Bir lint kullanın](linting-python-code.md)
