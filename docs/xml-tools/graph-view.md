---
title: XML şema Tasarımcısı grafik görünümü
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: 5881afde-3f24-4eb9-bff8-6cb3fc8aade7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 603c0849d22f658800776e8a1e4cb1f429990e00
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894631"
---
# <a name="graph-view"></a>Graf görünümü

Bir grafik gösterimi genel şeması düğümlerin ve düğümler arasındaki ilişkileri grafik görünümü sağlar. Graf görünümünü tasarım yüzeyinde kümesi şeması düzenini değiştirmek için izin vermediğini unutmayın. Graf görünümünü de XML şema Tasarımcısı araç çubuğu ve içerik haritası çubuğu içerir.

 Aşağıdaki görüntüde, tasarım yüzeyindeki altı genel düğüme sahip graf görünümünü gösterir.

 ![XML şema Tasarımcısı grafik görünümü](../xml-tools/media/xsddesigner_graphview.gif)

## <a name="design-surface"></a>Tasarım yüzeyi

 Graf görünümünü tasarım yüzeyinin içeriğini görüntüler [XML şema Tasarımcısı çalışma alanı](../xml-tools/xml-schema-designer-workspace.md). Çalışma alanı şema kümesindeki herhangi bir genel düğüm içeriyorsa, graf görünümünü tasarım yüzeyinde düğümleri gösterilir ve ilişkileri olan düğümleri oklar çizilir.

 Grafik görünümündeki bir düğümünü çift XML Düzenleyicisi'ni getirir.

 XSD Tasarımcısı araç çubuğunda seçilen düğümleri çalışma alanından silmek için kullanın veya **Sil** anahtarı.

 Tasarım yüzeyine boşsa, XML Düzenleyicisi'ni **XML Şeması Gezgini**, ve eşik gösterilir. *Filigran* XSD Tasarımcısı görünümleri bağlantılar listesini içerir.

 ![XSD Tasarımcısı; Graf görünümü](../xml-tools/media/xsdgraphviewwatermark.gif)

 Şema kümesi hata varsa, listenin en sonunda aşağıdaki metni görüntülenir: "Görüntüleyip kümesindeki hataları düzeltmek için hata listesini kullanın."

## <a name="breadcrumb-bar"></a>İçerik haritası çubuğu

 Graf görünümünü alt kısmındaki içerik haritası çubuğu, seçili düğümü şema kümesinde nerede bulunduğunu gösterir. İçerik haritası çubuğu, birden çok öğe seçili ise, boş olarak görüntülenir.

## <a name="context-menu"></a>Bağlam menüsü

 Aşağıdaki tabloda, graf görünümünü tasarım yüzeyinde tüm düğümler için kullanılabilir seçenekleri açıklar.

|Seçenek|Açıklama|
|-|-----------------|
|**XML şema Gezgini'nde Göster**|Şema Gezgini'ni odak getirir ve şema kümesi düğümü vurgular.|
|**Graf görünümünde göster**|Graf görünümünü (gri) geçer.|
|**Örnek XML oluşturma**|Yalnızca genel öğeler için kullanılabilir. Genel öğe için bir örnek XML dosyası oluşturur.|
|**Çalışma alanını temizle**|Çalışma alanı ve tasarım yüzeyine temizler.|
|**Çalışma alanından kaldırma**|Çalışma alanını ve tasarım yüzeyinde seçilen düğümleri kaldırır.|
|**Çalışma alanı seçimi dışında tümünü Kaldır**|Çalışma alanını ve tasarım yüzeyinde seçili olmayan düğümleri kaldırır.|
|**Diyagramı görüntü olarak dışarı aktar**|Tasarım yüzeyi için XPS dosyası olarak kaydeder.|
|**Tümünü Seç**|Tasarım yüzeyinde tüm düğümleri seçer.|
|**Kodu Görüntüle**|XML Düzenleyicisi'nde seçili düğümü içeren dosyayı açar. Seçili öğeyi **XML Şeması Gezgini** XML Düzenleyicisi'nde da seçilir.|
|**Özellik Penceresi**|Açılır **özellikleri** penceresi (Bunu zaten açık değilse). Bu pencere, düğüm hakkında bilgi görüntüler.|

 Yukarıda açıklanan genel seçeneklerinin yanı sıra genel öğeler için bağlam menüsünü de aşağıdaki seçeneklere sahiptir:

|Seçenek|Açıklama|
|-|-----------------|
|**Tür tanımı Ekle**|Temel türü diyagrama ekler.|
|**Tüm başvuruları Ekle**|Öğeye başvurmak ve bunlar arasındaki ilişkileri göstermek için okları çizer tüm düğümleri ekler.|
|**Değiştirme grubu üyeleri Ekle**|Tüm değiştirme grubu üyelerini ekler. Öğesi head veya değiştirme grubu üyesi ise, bu seçenek Görünümü'nde görüntülenir.|
|**Örnek XML oluşturma**|Genel öğe için bir örnek XML dosyası oluşturur.|

 Yukarıda açıklanan genel seçeneklerinin yanı sıra genel basit ve genel karmaşık türler için bağlam menüsünü de aşağıdaki seçeneklere sahiptir:

|Seçenek|Açıklama|
|-|-----------------|
|**Temel tür ekleyin**|Seçilen tür genel bir türden türetilirse seçili türün temel türünü ekler.|
|**Tüm başvuruları Ekle**|Seçili türdeki tüm başvuruları ekler. Bu öğeler ve öznitelikler seçili türü ve seçilen türden türetilmiş türleri içerir.|
|**Tüm türetilen türleri Ekle**|Doğrudan ve dolaylı olarak seçilen türünden türetilen tüm türler ekler.|
|**Tüm üst öğeleri Ekle**|Tüm üst (Temel) türleri ekler.|

 Yukarıda açıklanan genel seçeneklerinin yanı sıra hem genel öznitelik grupları için bağlam menüsünü de aşağıdaki seçeneklere sahiptir:

|Seçenek|Açıklama|
|-|-----------------|
|**Tüm başvuruları Ekle**|Gruba bakın ve bunlar arasındaki ilişkileri göstermek için okları çizer tüm düğümleri ekler.|
|**Tüm üyeleri Ekle**|Grubun tüm üyelerinin ekler ve bunlar arasındaki ilişkileri göstermek için okları çizer.|

 Yukarıda açıklanan genel seçenekleri gateway'e ek olarak, genel öznitelikler için bağlam menüsünü de aşağıdaki seçeneklere sahiptir:

|Seçenek|Açıklama|
|-|-----------------|
|**Tüm başvuruları Ekle**|Gruba bakın ve bunlar arasındaki ilişkileri göstermek için okları çizer tüm düğümleri ekler.|

## <a name="properties-window"></a>Özellik penceresi

 Başlangıçta açmak için bağlam menüsünü kullanın **özellikleri** penceresi. Varsayılan olarak, **özellikleri** penceresi Visual Studio'nun sağ alt köşesinde görüntülenir. İçerik modeli Görünümü'nde işlenen bir düğümüne tıkladığınızda, o düğümde özelliklerini görüntülenmesi **özellikleri** penceresi.

## <a name="xsd-toolbar"></a>XSD araç çubuğu

 Graf görünümü etkin olduğunda, aşağıdaki XSD araç çubuğu düğmeleri etkinleştirilir.

 ![XML şema Tasarımcısı araç çubuğu](../xml-tools/media/xsdgraphviewtoolbar.gif)

|Seçenek|Açıklama|
|-|-----------------|
|**Başlangıç görünümü göster**|Ağınızdan [başlangıç görünümü](../xml-tools/start-view.md). Bu görünüm, klavye kısayolunu kullanarak erişilebilir: **Ctrl**+**1**.|
|**İçerik modeli görünümünü göster**|Ağınızdan [içerik modeli görünümünü](../xml-tools/content-model-view.md). Bu görünüm, klavye kısayolunu kullanarak erişilebilir: **Ctrl**+**2**.|
|**Graf görünümünü göster**|Ağınızdan [grafik görünümü](../xml-tools/graph-view.md). Bu görünüm, klavye kısayolunu kullanarak erişilebilir: **Ctrl**+**3**.|
|**Çalışma alanını temizle**|Çalışma alanı ve tasarım yüzeyine temizler.|
|**Çalışma alanından kaldırma**|Çalışma alanını ve tasarım yüzeyinde seçilen düğümleri kaldırır.|
|**Çalışma alanı seçimi dışında tümünü Kaldır**|Çalışma alanını ve tasarım yüzeyinde seçili olmayan düğümleri kaldırır. Bu seçenek, graf görünümünden ve içerik modeli görünümünü etkindir.|
|**Soldan sağa**|Soldan sağa hiyerarşik bir sunumunu düğümleri için graf görünümünü, düzenini değiştirir. Bu seçenek, klavye kısayolunu kullanarak erişilebilir: **Alt**+**sağ ok**.|
|**Sağdan sola**|Sağdan sola hiyerarşik bir sunumunu düğümleri için graf görünümünü, düzenini değiştirir. Bu seçenek, klavye kısayolunu kullanarak erişilebilir: **Alt**+**sol ok**.|
|**Üstten alta**|Üst-alt hiyerarşik bir sunumunu düğümleri için graf görünümünü, düzenini değiştirir. Bu seçenek, klavye kısayolunu kullanarak erişilebilir: **Alt**+**aşağı ok**.|
|**Aşağıdan yukarıya**|Alt-üst hiyerarşik bir sunumunu düğümleri için graf görünümünü, düzenini değiştirir. Bu seçenek, klavye kısayolunu kullanarak erişilebilir: **Alt**+**yukarı ok**.|

## <a name="panscroll"></a>PAN/kaydırma

 Kaydırma çubuklarını kullanarak veya bulunduran tasarım yüzeyine kaydırabilirsiniz **Ctrl** tıklayın ve fareyle sürükleyin anahtar. ' A tıklayın ve sürükleyin kullanarak tasarım yüzeyine PAN imleç dört yönde çapraz dört oklar değişir.

## <a name="undoredo"></a>Geri Al/Yinele

 Aşağıdaki eylemler için graf görünümünü geri al/Yinele özelliği etkin:

-   Tek bir düğüm sürükleme ve bırakma ekleniyor.

-   Şema Gezgini veya başlangıç görünümünde sorgular arama sonuçları penceresinde birden çok düğüm ekleme.

-   Tek veya birden çok düğüm siliniyor.

## <a name="zoom"></a>Yakınlaştır

 Graf görünümünü sağ alt köşesindeki Yakınlaştır kullanılabilir.

 Yakınlaştırma, aşağıdaki yollarla denetlenebilir:

-   Basılı tutarak **Ctrl** anahtar ve fare dönen Tekerlek fare graf görünümünü yüzeyi gelindiğinde.

-   Kaydırıcı denetimi kullanarak. Kaydırıcı geçerli yakınlaştırma düzeyini gösterir.

Bunu seçtiğinizde, üzerine gelin veya kullanın yakınlaştırma kaydırıcısı donuktur **Ctrl** yakınlaştırma için fare tekerleğini ile; her zaman saydamdır.

## <a name="xml-editor-integration"></a>XML Düzenleyicisi tümleştirme

 Bir düğüm tıklayarak ve kodu görüntüle bağlam menüsünü kullanarak graf görünümünden ve XML Düzenleyicisi arasında ileri ve geri geçebilirsiniz.

 XML Düzenleyicisi'nde ayarlamak şema değişiklik yaparsanız, değişiklikleri grafik görünümde eşitlenecektir. Daha fazla bilgi için [XML Düzenleyicisi ile tümleştirme](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Tasarım yüzeyi](../xml-tools/xml-schema-designer-workspace.md)