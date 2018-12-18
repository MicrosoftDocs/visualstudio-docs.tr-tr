---
title: Hata Ayıklayıcı Kullanıcı Arabirimi (XSLT)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c2cedf1a07307b8494e6a6b810e9590f347c9f1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847389"
---
# <a name="debugger-user-interface-xslt"></a>Hata ayıklayıcı kullanıcı arabirimi (XSLT)

Bu konu, hata ayıklayıcı pencereleri ve iletişim kutuları açıklar. Yalnızca özel XSLT hata ayıklama davranışa sahip kullanıcı arabirimi parçaları ele alınmaktadır.

Daha fazla bilgi için [kullanıcı arabirim başvurusunda hata ayıklama](../debugger/debugging-user-interface-reference.md).

## <a name="locals-window"></a>Yerel öğeler penceresi
 Stil sayfasında tanımlanan tüm değişkenler hakkında bilgi için Yereller penceresine görüntüler. Yerel öğeler penceresinde üç sütun bilgileri içerir:

 **Ad**

 Bu sütun, geçerli kapsamdaki tüm yerel değişkenlerin adlarını içerir. Bu, alt klasörlerinde görmek için detaya gitme bir ağaç denetimi düğümü vardır.

 **Değer**

 Bu sütunda yer alan her bir değişken değeri görüntülenir. Öznitelik, işlem yönergesi, yorum, metin ve CData düğümler, düğümün metin değerini görüntüler. Ad alanı URI Namespace düğümleri görüntüleyin.

 **Türü**

 Bu sütunda listelenen her bir değişken veri türünü tanımlayan **adı** sütun.

 Yerel öğeler penceresinde de XSLT dönüşümü bağlamında izleyen önceden tanımlanmış bağlam değişkenlerini görüntüler. XSLT hata ayıklayıcısı tarafından kullanılan önceden tanımlanmış bağlam değişkenleri aşağıdaki tabloda açıklanmaktadır.

|Ad|Açıklama|
|-|-----------------|
|`last()`|İçerik boyutu.|
|`position()`|Konumu veya dizin sayısı, bağlam düğümü göre içerik boyutu.|
|`self::node()`|Bağlam düğümünün değeri.|

## <a name="output-window"></a>Çıktı penceresi
 Çıkış penceresi, herhangi bir hata iletileri veya hata ayıklama sırasında oluşan bir güvenlik özel durumları gösterir.

 XSLT hata ayıklayıcı, hata ayıklayıcı çıkış görüntülemek için ayrı bir pencerede kullanır. Çıkışı görüntülemek için kullanılan aynı pencerede budur bir **Göster XSL çıkış** komutu.

## <a name="task-list"></a>Görev Listesi
 **Görev listesi** stil sayfası tüm derleme hataları listeler. Hata çift hata satırı için imleç alır.

 **Görev listesi** komut dosyası blokları XSLT dosyasında oluşan hataları içerir.

> [!NOTE]
> XSLT hata ayıklayıcısı hiçbir zaman görünürler, uyarı olduğundan **görev listesi**.

## <a name="breakpoints-window"></a>Kesme Noktaları penceresi
 Kesme noktaları penceresi tüm kesme noktalarını ayarlayın geçerli projedeki gösterir. Pencerenin görünümde olduğu sürece bir kesme noktası eklenirse, pencerenin yeni kesme noktası gösterecek şekilde otomatik olarak güncelleştirilir.

 Kesme noktaları penceresini diğer Visual Studio hata ayıklayıcıları aynı şekilde çalışacaktır.

## <a name="command-windowimmediate-window"></a>Komut penceresi/hemen penceresi
 XSLT hata ayıklayıcı bu sürümde uygulanmadı.

## <a name="watch-window"></a>Gözcü penceresi
 İzleme penceresi değişkenleri değerlendirmek için kullanılır. Değişkenlerin değerlerini de değiştirebilirsiniz.

 İzleme penceresinde görüntülenen geçerli bağlam (çağrı yığınında en üst öğe) için değişkenlerdir. Bağlam değiştirirseniz, İzleme penceresinde güncelleştirir ve bu bağlam için ayarlanan değişkenler görüntüler.

## <a name="call-stack-window"></a>Çağrı Yığını penceresi
 **Çağrı yığını** penceresinin, çağrı yığını, parametre türleri ve parametre değerlerini işlevlerin adları görüntülemek için kullanılır. Çağrı yığını bilgileri yalnızca ayıklanan programın bir kesme durumunda olduğunda gösterilir.

 Çağrı yığınını XSLT yürütme oluşturulmak çeşitli bağlamı temsil eder. Örneğin, şablondan bir çağrı ise "a" Şablon "b", şablon "a" ve "b" şablonu görünür **çağrı yığını** penceresi çok üst listenin geçerli bağlam ile. Kullanıcı şu anda yürütülmekte olan sorgu görebilirsiniz.

 Şablonlar XSLT dosyasında bir adı yoksa, XSLT işlemcisi tarafından oluşturulan adları kullanılır.

 Bir listenin üst kısmındaki dışında bir öğeye tıklandığında Burada XSLT yürütme dal standart yeşil vurgu kullanarak oldu ve yeşil ok Görüntüleyicisi gösterir.

## <a name="quickwatch-dialog-box"></a>QuickWatch iletişim kutusu
 **QuickWatch** iletişim kutusu, XPath 1.0 ifade değerlendirmek için kullanılır. Bağlam düğümünün ( `self::node()` Yereller penceresinde düğüm) için XPath ifadesinin yürütme bağlamı sağlar. XPath ifadesini yürütmenin sonucu İzleme penceresinde görüntülenir.

 Aşağıdaki listede, XPath ifadesi değerlendirmesi üzerinde bazı kısıtlamaları açıklamaktadır.

-   Yerleşik XPath işlevleri izin verilir.

-   Yerleşik XSLT işlevleri gibi `document()`, `key()`ve benzeri izin verilmez.

-   Kullanıcı tanımlı işlevlerde izin verilmez.

Daha fazla bilgi için [nasıl yapılır: bir XPath ifadesini değerlendirme](../xml-tools/how-to-evaluate-an-xpath-expression.md).

## <a name="disassembly-window"></a>Ayrıştırma penceresi
 Ayrıştırılmış kod penceresini XSLT derleyici tarafından oluşturulan bütünleştirilmiş kodu gösterir. Bu pencerede diğer Visual Studio çözümünü windows ile aynı şekilde kullanılabilir.

 Daha fazla bilgi için [nasıl yapılır: Ayrıştırılmış kod penceresini kullanma](../debugger/how-to-use-the-disassembly-window.md).

## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Hatalarını Ayıklama](../xml-tools/debugging-xslt.md)
- [Hata ayıklayıcısı temel bilgileri](../debugger/getting-started-with-the-debugger.md)
- [Visual Studio'da otolar ve yerel öğeler pencerelerinde değişkenleri denetleyin](../debugger/autos-and-locals-windows.md)