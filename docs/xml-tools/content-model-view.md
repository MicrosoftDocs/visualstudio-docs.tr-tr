---
title: XML şema Tasarımcısı içerik modeli görünümü
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a151daa4419c24464aeeafd9a3b58d202a6e82b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942591"
---
# <a name="content-model-view"></a>İçerik Modeli Görünümü

Yerel ve genel şema düğümlerini ve basit ve karmaşık türler, öğe, model grupları, öznitelik ve öznitelik grupları dahil olmak üzere bileşenlerinin grafik gösterimi için içerik modeli görünümünü sağlar. XML açıklamaları ve işleme yönergeleri içerik modeli görünümünde görüntülenemez. İçerik modeli görünümü iki panel içerir: bir **çalışma** düğümlerin listesini içeren bir panel [XML şema Tasarımcısı çalışma alanı](../xml-tools/xml-schema-designer-workspace.md)ve içerik modeli şemasının görebileceğiniz tasarım yüzeyi Seçili düğümleri **çalışma** paneli. İçerik modeli görünümü, XML şema Tasarımcısı araç ve içerik haritası çubuğu de içerir.

 Aşağıdaki görüntüde, **çalışma** panelinde altı şema düğüm içeriyor. `purchaseOrder` Düğümü seçildiğinde, **çalışma** paneli ve tasarım yüzeyinde görüntülenir.

 ![XML şema Tasarımcısı içerik modeli görünümü](../xml-tools/media/xsddesigner_contentmodelview.gif)

## <a name="workspace-panel"></a>Çalışma alanı panelini

 Çalışma alanına düğüm ekleme sonra düğüm listesi görünür **çalışma** içerik modeli görünümünü panelini. Düğümleri seçtiğinizde, **çalışma** paneli, içerik modeli görünümünü tasarım yüzeyinde görünürler. Düğümleri çalışma alanından silmek için XSD Tasarımcısı araç kullanmak **çalışma** paneli bağlam menüsünden veya **Sil** anahtarı.

 Düğüm ekleme hakkında daha fazla bilgi için "bir çalışma için düğümleri ekleme" bölümüne bakın. [XML şema Tasarımcısı çalışma alanı](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>Tasarım yüzeyi

 İçinde bir düğümü seçildiğinde **çalışma** paneli, düğümün ayrıntılarını görüntüleyebileceğiniz içerik modeli görünümünü tasarım yüzeyine eklenir.

 İçerik modeli, bir düğüm, Genişletilebilir bir grafik ağacı öğeleri ve özniteliklerinin ağaç düğümleri olarak görünen ile temsil edilir. Varsayılan olarak, yalnızca bir düzey genişletilir. Oluşturucuları, tür adları, grupları ve diğer kapsayıcı gibi diğer bilgileri öğeleri ve bunların içine öznitelikleri (genişletildiğinde) dikey bir çubuk yerleştirilir. Dikey çubuk çift tıkladığınızda, yatay hale gelir ve ağaç daraltır. Yatay bir çubuk çift tıkladığınızda, dikey haline gelir ve ağaç genişletir. Dikey çubuk seçerek kapsayıcısında tüm düğümleri seçer. Bir öğenin genişletilmiş veya daraltılmış Genişleticileri bir düğümü sağ tarafta görünür.

 Tasarım yüzeyine boşsa, XML Düzenleyicisi'ni **XML Şeması Gezgini**, ve eşik gösterilir. *Filigran* XSD Tasarımcısı görünümleri bağlantılar listesini içerir. Şema kümesi hata varsa, listenin en sonunda aşağıdaki metni görüntülenir: "Görüntüleyip kümesindeki hataları düzeltmek için hata listesini kullanın."

## <a name="breadcrumb-bar"></a>İçerik haritası çubuğu

 İçerik modeli görünümünü alt kısmındaki içerik haritası çubuğu, seçili düğümü şema kümesinde nerede bulunduğunu gösterir.

## <a name="context-menus"></a>Bağlam menüleri

 Tasarım yüzeyinde bir öğeye sağ tıkladığınızda veya **çalışma** panelinde, bir bağlam menüsü görüntülenir. Aşağıdaki tablo, içerik modeli görünümünü tasarım yüzeyi için kullanılabilir seçenekleri açıklar.

|Seçenek|Açıklama|
|-|-----------------|
|**XML şema Gezgini'nde Göster**|Şema Gezgini'ni odak getirir ve şema kümesi düğümü vurgular.|
|**Graf görünümünde göster**|Graf görünümünü geçer.|
|**Örnek XML oluşturma**|Yalnızca genel öğeler için kullanılabilir. Genel öğe için bir örnek XML dosyası oluşturur.|
|**Belgeleri göster**|Ek açıklama/belge düğümü içeriği gizler veya gösterir.|
|**Diyagramı görüntü olarak dışarı aktar**|Tasarım yüzeyi için XPS dosyası olarak kaydeder.|
|**Kodu Görüntüle**|XML Düzenleyicisi'nde seçili düğümü içeren dosyayı açar. Seçili öğeyi **XML Şeması Gezgini** XML Düzenleyicisi'nde da seçilir.|
|**Özellik Penceresi**|Açılır **özellikleri** penceresi (Bunu zaten açık değilse). Bu pencere, düğüm hakkında bilgi görüntüler.|

 Aşağıdaki tabloda kullanılabilir seçenekler açıklanmaktadır **çalışma** paneli.

|Seçenek|Açıklama|
|-|-----------------|
|**XML şema Gezgini'nde Göster**|Şema Gezgini'ni odak getirir ve şema kümesi düğümü vurgular.|
|**Graf görünümünde göster**|Graf görünümünde geçer.|
|**Çalışma alanını temizle**|Çalışma alanı ve tasarım yüzeyine temizler.|
|**Çalışma alanından kaldırma**|Çalışma alanını ve tasarım yüzeyinde seçilen düğümleri kaldırır.|
|**Çalışma alanı seçimi dışında tümünü Kaldır**|Çalışma alanını ve tasarım yüzeyinde seçili olmayan düğümleri kaldırır.|
|**Örnek XML oluşturma**|Yalnızca genel öğeler için kullanılabilir. Genel öğe için bir örnek XML dosyası oluşturur.|
|**Tümünü Seç**|Tüm düğümleri seçer **çalışma** paneli.|
|**Kodu Görüntüle**|XML Düzenleyicisi'nde seçili düğümü içeren dosyayı açar. Seçili öğeyi **XML Şeması Gezgini** XML Düzenleyicisi'nde da seçilir.|
|**Özellik Penceresi**|Açılır **özellikleri** penceresi (Bunu zaten açık değilse). Bu pencere, düğüm hakkında bilgi görüntüler.|

## <a name="properties-window"></a>Özellik penceresi

 Başlangıçta açmak için bağlam menüsünü kullanın **özellikleri** penceresi. Varsayılan olarak, **özellikleri** penceresi Visual Studio'nun sağ alt köşesinde görüntülenir. İçerik modeli Görünümü'nde işlenen bir düğümüne tıkladığınızda, o düğümde özelliklerini görüntülenir **özellikleri** penceresi.

## <a name="xsd-designer-toolbar"></a>XSD Tasarımcısı araç çubuğu

 İçerik modeli görünümü etkin olduğunda, aşağıdaki XSD Tasarımcısı araç çubuğu düğmeleri etkinleştirilir.

 ![XML şema Tasarımcısı araç çubuğu](../xml-tools/media/xsdcontentmodelviewtoolbar.gif)

|Seçenek|Açıklama|
|-|-----------------|
|**Başlangıç görünümü göster**|Ağınızdan [başlangıç görünümü](../xml-tools/start-view.md). Bu görünüm, klavye kısayolunu kullanarak erişilebilir: **Ctrl**+**1**.|
|**İçerik modeli görünümünü göster**|Ağınızdan [içerik modeli görünümünü](../xml-tools/content-model-view.md). Bu görünüm, klavye kısayolunu kullanarak erişilebilir: **Ctrl**+**2**.|
|**Graf görünümünü göster**|Ağınızdan [grafik görünümü](../xml-tools/graph-view.md). Bu görünüm, klavye kısayolunu kullanarak erişilebilir: **Ctrl**+**3**.|
|**Çalışma alanını temizle**|Çalışma alanı ve tasarım yüzeyine temizler.|
|**Çalışma alanından kaldırma**|Çalışma alanını ve tasarım yüzeyinde seçilen düğümleri kaldırır.|
|**Çalışma alanı seçimi dışında tümünü Kaldır**|Çalışma alanını ve tasarım yüzeyinde seçili olmayan düğümleri kaldırır.|
|**Belgeleri göster**|Ek açıklama/belge düğümü içeriği gizler veya gösterir.|

## <a name="panscroll"></a>PAN/kaydırma

 Kaydırma çubuklarını kullanarak veya bulunduran tasarım yüzeyine kaydırabilirsiniz **Ctrl** tıklayın ve fareyle sürükleyin anahtar. ' A tıklayın ve sürükleyin kullanarak tasarım yüzeyine PAN imleç dört yönde çapraz dört oklar değiştirir.

## <a name="undoredo"></a>Geri Al/Yinele

 Aşağıdaki eylemler için içerik modeli görünümünü geri al/Yinele özelliği etkin:

-   Tek bir düğüm sürükleme ve bırakma ekleniyor.

-   Şema Gezgini arama sonuçları penceresinde birden çok düğüm ekleme.

-   Düğüm başlangıç görünümünden ekleme.

-   Tek veya birden çok düğüm siliniyor.

## <a name="zoom"></a>Yakınlaştır

 İçerik modeli görünümünü sağ alt köşesindeki Yakınlaştır kullanılabilir.

 Yakınlaştırma, aşağıdaki yollarla denetlenebilir:

-   Basılı tutarak **Ctrl** anahtar ve fare dönen Tekerlek fare içerik modeli görünümünü yüzeyi gelindiğinde.

-   Kaydırıcı denetimi kullanarak. Kaydırıcı geçerli yakınlaştırma düzeyini gösterir.

Bunu seçtiğinizde, üzerine gelin veya kullanın yakınlaştırma kaydırıcısı donuktur **Ctrl** yakınlaştırma için fare tekerleğini ile; her zaman saydamdır.

## <a name="xml-editor-integration"></a>XML Düzenleyicisi tümleştirme

 İleri ve geri arasında geçiş yapabilirsiniz **XSD Tasarımcısı** ile XML Düzenleyicisi bağlam menüsünü kullanarak.

 XML Düzenleyicisi'nde ayarlamak şema değişiklik yaparsanız, değişiklikleri içerik modeli Görünümü'nde eşitlenir. Daha fazla bilgi için [XML Düzenleyicisi ile tümleştirme](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Tasarımcısı Çalışma Alanı](../xml-tools/xml-schema-designer-workspace.md)