---
title: Daralt ve bölgeleri genişletin
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b39e9613e36b45f812738ab4eab6b945727b196b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064711"
---
# <a name="outlining"></a>Anahat Oluşturma

Artı işareti altında görünmesi bir bölge kodu daraltarak bazı kod görünümden gizlemeyi seçebilirsiniz (**+**). Daraltılmış bölgeye, artı işaretine tıklayarak genişletin. Klavye kullanıcısıysanız seçebileceğiniz **Ctrl**+**M**+**M** daraltmak ve genişletmek için. Ayrıca, herhangi bir satırda bölge kodu yalnızca solunda görünür anahat Kenar çubuğunda çift tıklayarak bir anahat oluşturma bölgesi daraltabilirsiniz. Daraltılmış bölgeye geldiğinizde, araç ipucu olarak daraltılmış bölgeye içeriğini görebilirsiniz.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz: [Kaynak Düzenleyicisi (Mac için Visual Studio)](/visualstudio/mac/source-editor).

Kenar boşlukları fare ile üzerine geldiğinizde anahat kenar bölgelerde ayrıca vurgulanır. Varsayılan renk vurgulama renk bazı yapılandırmalarda yerine soluk görünebilir. İçinde değiştirebilirsiniz **Araçları** > **seçenekleri** > **ortam** > **yazı tipleri ve renkler**  >  **Genişletilebilir**.

Anahatları belirlenmiş kodunda çalışırken, üzerinde çalışma, yapılması ve sonra diğer bölümleri için taşıma bunları Daralt istediğiniz bölümleri genişletebilirsiniz. Olmasını istemediğiniz anahat oluşturma görüntülenen, kullanabileceğiniz **Durdur anahat oluşturma** , temel kodu etkilemeden anahat bilgileri kaldırmak için komutu.

**Geri** ve **Yinele** komutlarını **Düzenle** bu Eylemler menüsü etkiler. **Kopyalama**, **Kes**, **Yapıştır**, ve sürükle ve bırak işlemleri korumak anahat oluşturma bilgileri, ancak Genişletilebilir durumunda. Örneğin, daraltılmış durumda bir bölge kopyaladığınızda **yapıştırın** işlem bir genişletilmiş bölge olarak kopyalanan metni yapıştırın.

> [!CAUTION]
> Anahatları belirlenmiş bir bölge değiştirdiğinizde, anahat oluşturma kaybolabilir. Örneğin, silme veya bulma ve değiştirme işlemlerini bölge sonuna silme.

Aşağıdaki komutları bulunabilir **Düzenle** > **anahat** alt.

|||
|-|-|
|Seçimi Gizle|(**Ctrl**+**M**, **Ctrl**+**H**)-seçili değil normalde olabilecek kod bloğu daraltır Örneğin, anahat için kullanılabilir bir `if` blok. Özel bölge kaldırmak için **geçerli gizlemeyi Durdur** (veya **Ctrl**+**M**, **Ctrl** + **U**). Visual Basic'te kullanılabilir değil.|
|Anahat genişlemesini Değiştir|-Bölüm içinde iç içe geçmiş bir daraltılmış bölümü imleç gerektiği zaman Anahat en içteki geçerli gizli veya genişletilmiş durumunu tersine çevirir.|
|Tüm ana hattı Değiştir|(**Ctrl**+**M**, **Ctrl**+**L**)-tüm bölgeler için aynı durum genişletilmiş veya daraltılmış ayarlar. Bazı bölgelerde genişletilir ve bazı daraltılmış, ardından daraltılmış genişletilmiş bölge.|
|Ana Hat Oluşturmayı Durdur|(**Ctrl**+**M**, **Ctrl**+**P**)-tüm belgeyi tüm ana hat oluşturma bilgilerini kaldırır.|
|Geçerliyi gizlemeyi Durdur|(**Ctrl**+**M**, **Ctrl**+**U**)-şu anda seçili anahat oluşturma bilgilerini kaldırır Kullanıcı tanımlı bölge. Visual Basic'te kullanılabilir değil.|
|Tanımlara Daralt|(**Ctrl**+**M**, **Ctrl**+**O**)-tüm türlerin üyelerini daraltır.|
|Bloğu Daralt:\<mantıksal sınır >|(Visual C++) Ekleme noktasını içeren işlevi bir bölgede daraltır. Örneğin, ekleme noktasını bir döngü içinde yer alıyorsa, döngü gizlenir.|
|Tümünü Daralt: \<mantıksal yapıları >|(Visual C++) İşlevin içindeki tüm yapıları daraltır.|

Visual Studio SDK'sı, genişletmek veya daraltmak için istediğiniz metin bölgeleri tanımlamak için de kullanabilirsiniz. Bkz: [izlenecek yol: ana hat oluşturmayı](../extensibility/walkthrough-outlining.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Düzenleyicisi özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
- [Kaynak Düzenleyicisi (Mac için Visual Studio)](/visualstudio/mac/source-editor)