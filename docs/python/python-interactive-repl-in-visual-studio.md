---
title: Python etkileşimli penceresinde (REPL)
description: Visual Studio'da hızlı Python kodu geliştirmeye yönelik etkileşimli pencere (REPL) kullanın.
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
ms.openlocfilehash: 3c3a3a6cd3694a0affa6ca1d5cfabac58b124ec9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055721"
---
# <a name="work-with-the-python-interactive-window"></a>Python etkileşimli pencere ile çalışma

Visual Studio, her biri ile alma REPL üzerine artırır, Python ortamları için bir etkileşimli okuma değerlendirmek yazdırma döngü (REPL) penceresi sağlar *python.exe* komut satırında. **Etkileşimli** penceresi (açılmış **görünümü** > **diğer Windows** > **&lt;ortamı&gt; Etkileşimli** menü komutları) rastgele Python kodu girin ve sonuçlarını hemen görmek olanak sağlar. Öğrenin ve API'ları ve kitaplıkları ile etkileşimli çalışan kod projelerinizde geliştirmek için deneme bu şekilde kodlama yardımcı olur.

![Python etkileşimli penceresi](media/interactive-window.png)

Visual Studio Python REPL modları, aralarından seçim yapabileceğiniz birçok vardır:

| REPL | Açıklama | Düzenleme | Hata Ayıklama | Görüntüler |
| --- | --- | --- | --- | --- |
| Standart | Varsayılan REPL, doğrudan Python konuştuğunu | Standart düzenleme (çok satırlı, vb.). | Evet, aracılığıyla `$attach` | Hayır |
| Hata ayıklama | Varsayılan REPL, hataları ayıklanan Python işlem konuştuğunu | Standart düzenleme | Yalnızca hata ayıklama | Hayır |
| Ipython | REPL, Ipython arka ucuna hakkında konuşuyor | Ipython komutları Pylab kolaylığı | Hayır | Evet, satır içi olarak REPL |
| Ipython Pylab olmadan | REPL, Ipython arka ucuna hakkında konuşuyor | Standart Ipython | Hayır | Evet, pencere ayırın | 

Bu makalede **standart** ve **hata ayıklama** REPL modları. Ipython modları hakkında daha fazla bilgi için bkz: [Ipython REPL kullanma](interactive-repl-ipython.md).

Örnekleri içeren ayrıntılı bilgi için düzenleyici etkileşim aşağıdaki gibi **Ctrl**+**Enter**, bkz: [Öğreticisi 3. adım:etkileşimliREPLpenceresinikullanma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md). 

|   |   |
|---|---|
| ![video kamera simgesini film](../install/media/video-icon.png "bir video izleyin") | [(Microsoft Virtual Academy) videoyu](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Python-Interactive-Window-gJYKY5LWE_4605918567) üzerinde **etkileşimli** penceresi (2 dk. 22s).|

## <a name="open-an-interactive-window"></a>Etkileşimli bir pencere açın

Açmak için birkaç şekilde **etkileşimli** penceresi için bir ortam.

Python ortamları penceresine geçin (**görünümü** > **diğer Windows** > **Python ortamları** veya **Ctrl** + **K** > **Ctrl**+**`**) seçip **açık etkileşimli Pencere** komutu veya seçilen ortam düğmesi.

![Python ortamları penceresinde etkileşimli penceresi bağlantı](media/interactive-window-opening.png)

İkinci olarak, yakınlarında **görünümü** > **diğer Windows** menüsünde yoktur bir **Python etkileşimli penceresinde** olarak da, varsayılan ortamınız için komutu bir geçmek için komut **ortamları** penceresi:

![Etkileşimli pencere menüsü öğelerini Görünüm > diğer Windows](media/interactive-window-menu.png)

Üçüncü olarak, açık bir **etkileşimli** penceresi projenizdeki veya seçerek bir tek başına dosya için bir başlangıç dosyası üzerinde **hata ayıklama** > **yürütme \<proje | Dosya > Python etkileşimli** menü komutu (**Shift**+**Alt**+**F5**):

![Python etkileşimli menüde proje yürütülemiyor](media/interactive-execute-project.png)

Son olarak, kod dosyasını seçin ve kullanmak [ **etkileşime Gönder** komut](#send-to-interactive-command) aşağıda açıklanmıştır.

## <a name="interactive-window-options"></a>Etkileşimli pencere seçenekleri

Çeşitli yönlerini denetleyebilirsiniz **etkileşimli** penceresinden **Araçları** > **seçenekleri** > **Pythonaraçları**  >  **Etkileşimli Windows** (bkz [seçenekleri](python-support-options-and-settings-in-visual-studio.md)):

![Python etkileşimli penceresinde seçenekleri](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>Etkileşimli penceresini kullanma

Bir kez **etkileşimli** penceresi açıksa, kodu satır satır adresindeki girme başlayabilirsiniz **\> \> \>** istemi. **Etkileşimli** penceresi, modüller, içeri içeren değişkenleri tanımlayan girin ve benzeri gibi her satırı yürütür:

![Python etkileşimli penceresi](media/interactive-window.png)

Ne zaman gibi tam bir deyim hale getirmek için ek kod satırı gerektiğinde istisnadır bir `for` deyimi yukarıda da gösterildiği gibi iki nokta üst üste sona erer. Bu gibi durumlarda satırı istemi değişikliklerini **...**  yukarıdaki grafikte dördüncü ve beşinci satırda gösterildiği bloğu için ek satırlar girmenize gerek gösteren. Bastığınızda **Enter** boş bir satıra **etkileşimli** penceresi blok kapatır ve yorumlayıcıda çalıştırır.

> [!Tip]
> **Etkileşimli** penceresi artırır komut satırı REPL deneyimi çevreleyen kapsama ait deyimleri girintileme tarafından otomatik olarak normal Python bağlı. Komut satırı REPL yalnızca tek satır sağlar (yukarı ok ile geri) buna ait geçmişi çok satırlı öğeleri de sağlar.

<a name="meta-commands"></a> **Etkileşimli** penceresi çeşitli meta-komutları da destekler. Tüm meta-komutları başlayın `$`, ve yazabileceğiniz `$help` meta komutlarının listesini almak için ve `$help <command>` kullanım ayrıntıları için belirli bir komut almak için.

| Meta komutu | Açıklama |
| --- | --- |
| `$$` | Oturumunuz boyunca açıklama kodu için yardımcı olan bir yorum ekler. |
| `$attach` | Visual Studio hata ayıklayıcı, hata ayıklamayı etkinleştirmek için REPL penceresi işleme ekler. |
| `$cls`, `$clear` | Geçmiş ve yürütme bağlamı dokunmadan Düzenleyicisi penceresinin içeriğini temizler. |
| `$help` | Komutların bir listesini görüntülemek veya belirli bir komut hakkında Yardım. |
| `$load` | Komut dosyasını yükler ve tamamlanana kadar yürütür. |
| `$mod` | Geçerli kapsam için belirtilen modül adı geçer. |
| `$reset` | Yürütme ortamını ilk durumuna sıfırlar, ancak geçmişini tutar. |
| `$wait` | En az belirtilen sayıda milisaniye bekler. |

Komut ayrıca Visual Studio uzantıları tarafından Genişletilebilir uygulama ve dışarı aktarma `IInteractiveWindowCommand` ([örnek](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)).

## <a name="switch-scopes"></a>Kapsamları geçiş

Varsayılan olarak, **etkileşimli** penceresini bir projenin Komut İstemi'nden çalıştırdıysanız olarak projenin başlangıç dosyası için kapsamlı. Tek başına bir dosya için dosya kapsamları. Herhangi bir noktada REPL oturumunuz sırasında üst kısmındaki açılır menü ancak zaman **etkileşimli** pencere kapsam değiştirmenize olanak sağlar:

![Etkileşimli pencere kapsamları](media/interactive-scopes.png)

Yazarak gibi bir modülü içeri aktardığınızda `import importlib`, bu modüldeki herhangi bir kapsama geçiş yapmak için açılan seçenekleri görünür. Bir ileti **etkileşimli** penceresinde belirli bir duruma oturumunuz sırasında nasıl aldığınız izleyebilmek yeni kapsam de gösterir.

Girme `dir()` bir kapsamda işlev adlarını, sınıflar ve değişkenleri de dahil olmak üzere bu kapsamda geçerli tanımlayıcıları görüntüler. Örneğin, kullanarak `import importlib` ardından `dir()` şunları gösterir:

![Etkileşimli pencerede importlib kapsamı](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>Etkileşimli komutu Gönder

İçinde yanı sıra **etkileşimli** penceresi doğrudan Kod Düzenleyicisi'nde seçebilirsiniz sağ tıklatın ve seçin **etkileşime Gönder** veya basın **Ctrl** + **Girin**.

![Etkileşimli bir menü komutu için Gönder](media/interactive-send-to.png)

Bu komut, geliştirirken kodunuzu test de dahil olmak üzere, yinelemeli veya gelişime kod geliştirme için yararlıdır. Örneğin, bir kez gönderdiğiniz için kod parçasını **etkileşimli** penceresi çıktısı, söz konusu hızlıca tuşlarına basarak test kodu gösterme ve değiştirmek için yukarı ok tuşlarına basabilirsiniz **Ctrl** + **Girin**. (Tuşuna basarak **Enter** giriş sonunda yürütür, ancak tuşuna basarak **Enter** giriş ortasında yeni bir satır ekler.) İstediğiniz kodu aldıktan sonra kolayca geri proje dosyanız kopyalayabilirsiniz.

> [!Tip]
> Varsayılan olarak, Visual Studio kaldırır **>>>** ve **...** REPL ister koddan yapıştırırken **etkileşimli** Düzenleyici penceresine. Bu davranışı değiştirebilirsiniz **Araçları** > **seçenekleri** > **metin düzenleyici** > **Python**  >  **Gelişmiş** kullanarak sekmesinde **Yapıştır kaldırır REPL istemleri** seçeneği. Bkz: [seçenekleri - çeşitli seçenekleri](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

Bir kod dosyası bir karalama defteri kullanırken, genellikle küçük tamamını aynı anda göndermek istediğiniz bir kod bloğunu sahiptir. Kod gruplamak için kod olarak işaretlemek bir *kodu hücreyi* ile başlayan bir açıklama ekleyerek `#%%` hücre başlangıcına sona erdiği Öncekine. Daraltılmış ve genişletilmiş ve kullanarak kod hücreleri olabilir **Ctrl**+**Enter** içindeki kodu hücreyi tüm hücreyi gönderir. **etkileşimli** penceresi ve taşır bir sonraki.

Visual Studio gibi yorumlar ile başlayan kod hücreleri de algılar `# In[1]:`, Jupyter not defteri bir Python dosyası olarak dışarı aktarılırken aldığınız biçim. Bu algılama not defterinden çalıştırmayı kolaylaştırır [Azure not defterleri](https://notebooks.azure.com/) bir Python dosyası olarak indirme, Visual Studio'da açarak ve kullanarak **Ctrl**+**Enter**her hücresini çalıştırmak için.

![Etkileşimli kod hücreleri](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>IntelliSense davranışı

**Etkileşimli** penceresinde IntelliSense yalnızca kaynak kod çözümlemeyi dayanır Kod Düzenleyicisi'ni aksine Canlı nesneler dayalı IntelliSense'i içerir. Bu öneriler daha doğru **etkileşimli** penceresiyle, özellikle dinamik olarak üretilen kod. (Örneğin, günlük iletilerini) yan etkileri olan işlevlere geliştirme deneyiminizi etkileyebilir dezavantajı olmasıdır.

Bu davranış bir sorun varsa altındaki ayarları değiştirin **Araçları** > **seçenekleri** > **Python Araçları**  >   **Etkileşimli Windows** içinde **tamamlama modunu** grup üzerinde açıklandığı [seçenekleri - etkileşimli pencere](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options).
