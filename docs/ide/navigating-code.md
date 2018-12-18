---
title: Kod Gezinti komutları
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code editor, navigation
- code editor, go to
- code editor, go to definition
- code editor, go to line
- code editor, peek definition
- code editor, navigation bar
- go to definition
- peek definition
- go to line
- go to
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6ac6fb3ae1f8c4e7fb48c9cd9a0d2b77cb875094
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894475"
---
# <a name="navigate-code"></a>Kod gidin

Visual Studio Düzenleyicisi'nde koduna gitmek için çeşitli yollar sağlar. Bu konu, kodunuzu gidebilirsiniz farklı yollarını özetler ve daha fazla ayrıntıya konulara bağlantılar sağlar.

## <a name="navigate-backward-and-navigate-forward-commands"></a>Geriye git ve Navigate Forward komutları

Kullanabileceğiniz **Navigate Backward** (**Ctrl**+**-**) ve **Navigate Forward** ( **CTRL**+**Shift**+**-**) ekleme noktasını önceki konumlara taşımak ya da daha fazla şey bir döndürmek için araç çubuğundaki düğmeler bir önceki konumdan son konum. Bu düğmeler, ekleme noktasının son 20 konumunu korur. Bu komutlar da kullanılabilir **görünümü** menüsü altında **Navigate Backward** ve **Navigate Forward**.

![İleri ve geri gezinti düğmeleri](../ide/media/vs2017_nav_buttons.png)

## <a name="navigation-bar"></a>Gezinti çubuğu

Kullanabileceğiniz **gezinti çubuğu** (kod penceresinin üst kısmındaki açılır kutuları) bir kod temeli kodda gidin. Bir tür veya üye ona doğrudan gitmek için seçebilirsiniz. Bir Visual Basic, C# veya C++ kod temeli kodda düzenlerken gezinti çubuğu görünür. Kısmi class içinde geçerli kod dosyası dışında tanımlanan üyeler devre dışı bırakılabilir (bunlar gri renkte görüntülenir).

 ![Kod gezinti çubuğu](../ide/media/vside_navigation_bar.png)

Açılan kutu gibi gezinebilirsiniz:

- Geçerli dosyaya ait başka bir proje gitmek için soldaki aşağı açılan seçin.

- Bir sınıf veya türe gitmek için açılan ortadaki seçin.

- Bir yordam veya başka bir sınıfın üyesi doğrudan gitmek için sağ açılan menü seçin.

- Odağı kod penceresinden Gezinti çubuğuna geçirmek için kısayol tuş bileşimine basın **Ctrl**+**F2**.

- Odağı gezinti çubuğunda kutusu kutusu kaydırmak için basın **sekmesini** anahtarı.

- Odak ve dönüş kodu penceresine sahip bir gezinti çubuğu öğesini seçmek için basın **Enter** anahtarı.

- Odağı gezinti çubuğundan koda hiçbir şey seçmeden dönmek için basın **Esc** anahtarı.

Gezinti çubuğunu gizlemek için değiştirin **gezinti çubuğu** seçeneğini **metin düzenleyici tüm diller** ayarları (**Araçları** > **seçenekleri**  >  **Metin düzenleyici** > **tüm diller**), veya tek tek dil ayarlarını değiştirebilirsiniz.

## <a name="find-all-references"></a>Tüm başvuruları Bul

Çözümde seçilen öğenin tüm başvurularını bulur. Bu, olası yan-büyük bir yeniden düzenleme etkilerini kontrol etmek için ya da "etkin" kod doğrulamak için kullanabilirsiniz. Tuşuna **F8** výsledky mezi atlamak için. Daha fazla bilgi için [kodunuzdaki başvuruları bulma](finding-references.md).

Giriş | İşlev
------------ | ---
**Klavye** | Metin imlecinizi yere adını yazın ve ENTER tuşuna içinde **Shift**+**F12**
**Fare** | Seçin **tüm başvuruları Bul** bağlam menüsünden

## <a name="reference-highlighting"></a>Başvuru vurgulama

Kaynak koddaki bir simge tıkladığınızda, o simgenin tüm örnekleri belgede vurgulanır. Vurgulanan simgeler bildirimleri ve başvurular içerebilir ve diğer pek çok simgeyi **tüm başvuruları Bul** döndürür. Bu sınıf, nesneler, değişkenler, yöntemleri ve özellik adlarını içerir. Visual Basic kodu içinde birçok denetim yapıları için anahtar sözcükler ayrıca vurgulanır. Sonraki veya önceki vurgulanan simgeye gitmek için basın **Ctrl**+**Shift**+**aşağı ok** veya **Ctrl** + **Shift**+**yukarı ok**. Vurgulama rengini değiştirebilirsiniz **Araçları** > **seçenekleri** > **ortam** > **yazı tipleri ve Renkleri** > **vurgulanmış başvuru**.

## <a name="go-to-commands"></a>Git komutları

Gitmek için kullanılabilen aşağıdaki komutları sahip **Düzenle** menüsünün altında **Git**:

- **Satıra Git** (**Ctrl**+**G**): Etkin belgede belirtilen satır numarası taşıyın.

- **Tümüne Git** (**Ctrl**+**T** veya **Ctrl**+**,**): türü belirtilen satırına Taşı Dosya, üye veya simge.

- **Dosyaya Git** (**Ctrl**+**1**, **Ctrl**+**F**): belirtilen dosyaya Taşı Çözüm.

- **Son dosya** (**Ctrl**+**1**, **Ctrl**+**R**): belirtilen, Taşı en son ziyaret edilen çözümdeki (Visual Studio 2017 sürüm 15,8 yeni) dosyası.

- **Tür Git** (**Ctrl**+**1**, **Ctrl**+**T**): Belirtilen türüne Taşı Çözüm.

- **Üye Git** (**Ctrl**+**1**, **Ctrl**+**M**): Belirtilen üye taşıyın Çözüm.

- **Sembole Git** (**Ctrl**+**1**, **Ctrl**+**S**): Belirtilen sembolü taşıyın Çözüm.

Visual Studio 2017 sürüm 15,8 ve daha sonra aşağıdaki **Git** Gezinti komutları de mevcuttur:

- **Dosyadaki sonraki sorun gider** (**Alt**+**PgDn**) ve **dosyadaki önceki sorun Git** (**Alt** + **PgUp**)

- **Son konumu düzenlemek için Git** (**Ctrl**+**Shift**+**geri**)

Bu komutları hakkında daha fazla bilgi bkz [Git komutlarını kullanarak kod bulma](../ide/go-to.md) konu.

## <a name="go-to-definition"></a>Tanıma Git

Tanıma Git için seçilen öğenin açıklamasını alır. Daha fazla bilgi için [tanıma ve Özet tanım](../ide/go-to-and-peek-definition.md).

Giriş | İşlev
------------ | ---
**Klavye** | Metin imlecinizi yere adını yazın ve ENTER tuşuna içinde **F12**
**Fare** | Tür adına sağ tıklayıp **tanıma** veya basın **Ctrl** (Visual Studio 2017 sürüm 15.4 için yeni) tür adı'e tıklayın

## <a name="peek-definition"></a>Tanıma göz at

Tanımı görüntüler, Kod düzenleyicisinde, konumunuzu uzağa gitmeden pencerede seçili öğenin tanıma göz at. Daha fazla bilgi için [nasıl yapılır: Özet tanım'ı kullanarak kodu görüntüleme ve düzenleme](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) ve [tanıma ve Özet tanım](../ide/go-to-and-peek-definition.md).

Giriş | İşlev
------------ | ---
**Klavye** | Metin imlecinizi yere adını yazın ve ENTER tuşuna içinde **Alt**+**F12**
**Fare** | Tür adına sağ tıklayıp **Özet tanımı** veya basın **Ctrl** ve türü adına tıklayın (varsa **tanımı Özet Görünümü'nde açın** teslim seçeneği)

## <a name="go-to-implementation"></a>Uygulamaya Git

Uygulamaya Git kullanarak, bir taban sınıftan gidin veya tür, uygulamaları için. Birden fazla uygulaması varsa, bunları listelenen görürsünüz **sembol sonuçları Bul** penceresi:

Giriş | İşlev
------------ | ---
**Klavye** | Metin imlecinizi yere adını yazın ve ENTER tuşuna içinde **Ctrl**+**F12**
**Fare** | Tür adına sağ tıklayıp **uygulamaya Git**

## <a name="call-hierarchy"></a>Çağrı Hiyerarşisi

Bir yöntemde gelen ve giden çağrıları görüntüleyebileceğiniz [çağrı hiyerarşisi penceresi](../ide/reference/call-hierarchy.md):

Giriş | İşlev
------------ | ---
**Klavye** | Metin imlecinizi yere adını yazın ve ENTER tuşuna içinde **Ctrl**+**K**, **Ctrl**+**T**
**Fare** | Üye adının üzerine sağ tıklayın ve **çağrı hiyerarşisini görüntüle**

## <a name="next-method-and-previous-method-commands-visual-basic"></a>Sonraki önceki yöntem komutları (Visual Basic)

Visual Basic kod dosyalarında bu komutları ekleme noktasını farklı yöntemlere taşımak için kullanın. Seçin **Düzenle** > **sonraki yöntemi** veya **Düzenle** > **önceki yöntem**.

## <a name="structure-visualizer"></a>Yapı Görselleştirici

Kod Düzenleyicisi gösterilmektedir yapı Görselleştirici özelliği *yapı kılavuz çizgileri* -dikey gösteren küme ayraçları içine kod temelinizde eşleşen satırları kesik. Bu mantıksal blokları nerede başlaması görmeyi kolaylaştırır ve son kolaylaştırır.

![Yapı Görselleştirici](../ide/media/vside_structure_visualizer.png)

Yapı kılavuz çizgileri devre dışı bırakmak için Git **Araçları** > **seçenekleri** > **metin düzenleyici** > **genel** temizleyin **yapı kılavuz çizgilerini göster** kutusu.

## <a name="enhanced-scroll-bar"></a>Gelişmiş kaydırma çubuğu

Kodunuzun kuş bakışı görünümünü almak için bir kod penceresinde Gelişmiş kaydırma çubuğunu kullanın. İmleç kaydırma çubuğu yukarı ve aşağı taşıdığınızda, eşleme modunda önizlemeler kodun görebilirsiniz. Daha fazla bilgi için [nasıl yapılır: kaydırma çubuğunu özelleştirerek kodunuzu izleme](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).

## <a name="codelens-information"></a>CodeLens bilgileri

Değişiklikleri ve bu değişiklikler, başvurular, hatalar, iş öğeleri, kod incelemeleri ve birim test durumu, Kod Düzenleyicisi'nde CodeLens kullandığınızda kimin yaptığını gibi belirli kod hakkında bilgi bulabilirsiniz. Team Foundation Server ile Visual Studio Enterprise kullandığınızda CodeLens ekran gibi çalışır. Bkz: [kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Düzenleyicisi özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
- [Çağrı hiyerarşisini görüntüle](../ide/reference/call-hierarchy.md)
