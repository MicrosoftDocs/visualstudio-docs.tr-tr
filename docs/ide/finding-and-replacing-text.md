---
title: Metin ve birden çok giriş işaretini seçimi bulma ve değiştirme
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- Find in Files dialog box
- text searches, finding and replacing text
- text, finding and replacing
- find and replace
- find text
- replace text
- multi-caret selection
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6120d1ece56e24712fd1217090159ec627f88d61
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349107"
---
# <a name="find-and-replace-text"></a>Metin bulma ve değiştirme

Bul ve Visual Studio düzenleyicisinde metin değiştirmek [Bul ve Değiştir](#find-and-replace-control) veya [dosyalarda Bul/Değiştir](#find-in-files-and-replace-in-files). Yeni Visual Studio 2017 sürüm 15,8, bulma değiştirin ve *bazı* kullanarak bir desen örneklerini  *[birden çok giriş işaretini seçimi](#multi-caret-selection)*.

> [!TIP]
> Değişkenler ve yöntemler gibi kod simgeleri yeniden adlandırma, daha iyi *[yeniden düzenleme](../ide/reference/rename.md)* Bul ve Değiştir kullanımı çok bunları. Yeniden düzenleme, akıllı ve Bul ve Değiştir körüne tüm örnekleri değiştirir ancak kapsam anlar.

Bul ve değiştir işlevselliği belirli diğer metin tabanlı Windows Düzenleyicisi'nde gibi **sonuçları Bul** windows, XAML Tasarımcısı ve Windows Forms Tasarımcısı gibi tasarımcı pencerelerinde ve araç pencereleri.

Geçerli belgede, geçerli çözüm veya özel bir klasör kümesi için arama kapsamını belirleyebilirsiniz. Ayrıca, bir çoklu dosya aramaları için dosya adı uzantıları kümesi de belirtebilirsiniz. .NET kullanarak arama sözdizimini özelleştirebilirsiniz [normal ifadeler](../ide/using-regular-expressions-in-visual-studio.md).

> [!TIP]
> [Bul/komut](../ide/find-command-box.md) kutusu araç çubuğu denetimi olarak kullanılabilir, ancak varsayılan olarak görünmez. Görüntülenecek **Bul/komut** kutusunda **Düğme Ekle veya Kaldır** üzerinde **standart** araç ve ardından **Bul**.

## <a name="find-and-replace-control"></a>Bul ve Değiştir denetimi

**Bul ve Değiştir** denetimi kod düzenleyici penceresinin sağ alt köşesinde görünür. **Bul ve Değiştir** denetimi belirtilen arama dizesinin geçerli belgede her geçtiği yeri hemen vurgular. Seçim yaparak başka bir oluşumdan diğerine gidebilirsiniz **Sonrakini Bul** düğmesini veya **Öncekini Bul** arama denetimin üzerindeki düğme.

![Bul ve Visual Studio'da Değiştir](media/find-and-replace-box.png)

Yanındaki düğmeyi seçerek değiştirme seçeneklerine erişebilirsiniz **Bul** metin kutusu. Aynı anda bir tane değişiklik yapmaya karar **Değiştir** düğmesinin yanındaki **değiştirin** metin kutusu. Tüm eşleşmeleri değiştirmek için seçin **Tümünü Değiştir** düğmesi.

Eşleşmeler için vurgulama rengini değiştirmek için seçin **Araçları** menüsünde **seçenekleri**ve ardından **ortam**seçip **yazı tipleri ve renkler** . İçinde **ayarlarını göster** listesinden **metin düzenleyici**ve ardından **görüntü öğeleri** listesinden **Vurgu Bul (uzantı)**.

### <a name="search-tool-windows"></a>Arama Araç pencereleri

Kullanabileceğiniz **bulmak** kod veya metin pencerelerinde denetimini **çıkış** windows ve **sonuçları Bul** seçerek windows **Düzenle**  >  **Bul ve Değiştir** ya basarak **Ctrl + F**.

Bir sürümünü **Bul** denetim kullanılabilir ayrıca bazı araç pencerelerinde de. Örneğin, denetim listesini filtreleyebilirsiniz **araç kutusu** arama kutusuna metin girerek penceresi. Bunların içeriğini aramanıza olanak veren diğer araç pencereleri dahil **Çözüm Gezgini**, **özellikleri** penceresinde ve **Takım Gezgini**.

## <a name="find-in-files-and-replace-in-files"></a>Find dosyalar ve dosyalarda Değiştir

**Dosyalarda Bul/Değiştir** gibi çalışır **Bul ve Değiştir** denetimi aramanız için bir kapsam tanımlayabilmenizdir. Yalnızca geçerli açık dosya Düzenleyicisi'nde arama yapabilirsiniz, ancak aynı zamanda tüm açık belgeleri, tüm çözümü, geçerli proje ve seçili klasör kümelerini. Dosya adı uzantısına göre de arayabilirsiniz. Erişim için **dosyalarda Bul/Değiştir** iletişim kutusunda **Bul ve Değiştir** üzerinde **Düzenle** menü veya basın **Ctrl + SHIFT + F**.

![Visual Studio dosyalarda Bul](media/find-in-files-box.png)

### <a name="find-results"></a>Sonuçları Bul

Seçeneğini belirlediğinizde **Tümünü Bul**, **sonuçları Bul** penceresi açılır ve aramanız için eşleşmeleri listeler. Listede bir sonuç seçerek ilişkili dosyayı görüntüler ve eşleşmeyi vurgular. Dosyayı düzenlemek için açık değilse, bunu sekmenin sağ tarafındaki bir önizleme sekmesinde de açılır. Kullanabileceğiniz **Bul** arama denetimi **sonuçları Bul** listesi.

### <a name="create-custom-search-folder-sets"></a>Özel arama klasörü kümeleri oluşturma

Seçerek bir arama kapsamı tanımlayabilirsiniz **arama klasörlerini Seç** düğmesine (gibi görünüyor **...** ) yanındaki **konum** kutusu. İçinde **arama klasörlerini Seç** iletişim kutusunda, aranacak klasörler kümesi belirtebilirsiniz ve daha sonra yeniden belirtim kaydedebilirsiniz.

> [!TIP]
> Uzak makinenin sürücü yerel makinenize eşleştirdik uzak makinede aramak için klasörler belirtebilirsiniz.

### <a name="create-custom-component-sets"></a>Özel bileşen kümeleri oluşturma

Seçerek bileşen kümelerini arama Kapsamınız olarak tanımlayabilirsiniz **özel bileşen kümesini Düzenle** düğmesinin yanındaki **konum** kutusu. Yüklü .NET veya COM bileşenlerini, çözümünüze veya herhangi bir derleme veya tür kitaplığı dahil Visual Studio projeleri belirtebilirsiniz (*.dll*, *.tlb*, *.olb*, *.exe*, veya *.ocx*). Başvurular aramak için seçin **başvurularda bak** kutusu.

## <a name="multi-caret-selection"></a>Birden çok giriş işaretini seçimi

> [!NOTE]
> Bu bölüm, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz: [Blok seçimi](/visualstudio/mac/block-selection).

**Yeni Visual Studio 2017 sürüm 15,8**

Kullanım *birden çok giriş işaretini seçimi* aynı anda iki veya daha fazla yerde aynı düzenleme yapma. Örneğin, aynı metni ekleyin veya aynı anda birden fazla konumda mevcut metni değiştirme.

Aşağıdaki ekran görüntüsünde `-0000` üç konumda; kullanıcının bastığında seçilir **Sil**, tüm üç seçimleri silinir:

![Visual Studio'da bir XML dosyasında birden çok giriş işaretini seçimi](media/multi-caret-selection.png)

Birden çok düzeltme işaretleri seçmek için tıklayın veya zamanki ilk metin seçimi yapın ve tuşuna **Alt** tıklayın ya da ek her konumda metin seçin. Da otomatik olarak, eşleşen metin ek seçimleri ekleyebilir veya bir her satırında aynı şekilde düzenlemek için metin kutusunu seçin.

> [!TIP]
> Seçtiyseniz, **Alt** fare tıklatın değiştiricisi anahtar olarak tanımında Git **Araçları** > **seçenekleri**, birden çok giriş işaretini seçin devre dışı bırakıldı.

### <a name="commands"></a>Komutlar

Birden çok giriş işaretini seçme davranışları için aşağıdaki anahtar ve eylemleri kullanın:

|Kısayol|Eylem|
|-|-|
|**CTRL**+**Alt** + tıklayın|İkincil şapka işareti Ekle|
|**CTRL**+**Alt** + çift tıklayın|İkincil sözcük seçimi Ekle|
|**CTRL**+**Alt** +'a tıklayın ve sürükleyin|İkincil bir seçim ekleyin|
|**Shift**+**Alt**+**.**|Sonraki eşleşen metnin bir seçimi olarak Ekle|
|**CTRL**+**Shift**+**Alt**+**,**|Seçimlerin tüm eşleşen metni Ekle|
|**Shift**+**Alt**+**,**|Son seçilen oluşum Kaldır|
|**CTRL**+**Shift**+**Alt**+**.**|Sonraki eşleşen atla|
|**Alt** + tıklayın|Seçim kutusu Ekle|
|**ESC** veya tıklayın|Tüm seçimleri Temizle|

Bazı komutlar da kullanılabilir **Düzenle** menüsü altında **birden çok düzeltme işaretleri**:

![Visual Studio'da birden çok düzeltme işaretleri açılan menüsü](media/edit-menu-multiple-carets.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da normal ifadeler kullanma](../ide/using-regular-expressions-in-visual-studio.md)
- [Visual Studio'da kodu yeniden düzenleyin](../ide/refactoring-in-visual-studio.md)
- [Blok seçimi (Mac için Visual Studio)](/visualstudio/mac/block-selection)