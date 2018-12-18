---
title: Hata ayıklayıcı, kullanıcı arabirimi (XSLT) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 02ba962a3410b2e964e7653fcb6308b9209def44
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891862"
---
# <a name="debugger-user-interface-xslt"></a>Hata Ayıklayıcı Kullanıcı Arabirimi (XSLT)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
|----------|-----------------|  
|`last()`|İçerik boyutu.|  
|`position()`|Konumu veya dizin sayısı, bağlam düğümü göre içerik boyutu.|  
|`self::node()`|Bağlam düğümünün değeri.|  
  
 Daha fazla bilgi için [nasıl yapılır: hata ayıklayıcı bağlamını değiştirme](http://msdn.microsoft.com/library/8a69ea63-2ef0-4b4f-9521-cf8ad2e3ec5e).  
  
## <a name="output-window"></a>Çıktı Penceresi  
 Çıkış penceresi, herhangi bir hata iletileri veya hata ayıklama sırasında oluşan bir güvenlik özel durumları gösterir.  
  
 XSLT hata ayıklayıcı, hata ayıklayıcı çıkış görüntülemek için ayrı bir pencerede kullanır. Çıkışı görüntülemek için kullanılan aynı pencerede budur bir **Göster XSL çıkış** komutu.  
  
## <a name="task-list"></a>Görev Listesi  
 Görev listesi'stil sayfası tüm derleme hataları listeler. Hata çift hata satırı için imleç alır.  
  
 Görev listesi, komut dosyası blokları XSLT dosyasında oluşan hataları içerir.  
  
> [!NOTE]
>  Hiçbir zaman görev listesinde görünmesini XSLT hata ayıklayıcısı, uyarı var.  
  
## <a name="breakpoints-window"></a>Kesme noktaları penceresi  
 Kesme noktaları penceresi tüm kesme noktalarını ayarlayın geçerli projedeki gösterir. Pencerenin görünümde olduğu sürece bir kesme noktası eklenirse, pencerenin yeni kesme noktası gösterecek şekilde otomatik olarak güncelleştirilir.  
  
 Kesme noktaları penceresini diğer Visual Studio hata ayıklayıcıları aynı şekilde çalışacaktır.  
  
## <a name="command-windowimmediate-window"></a>Komut penceresi/komut penceresi  
 XSLT hata ayıklayıcı bu sürümde uygulanmadı.  
  
## <a name="watch-window"></a>İzleme penceresi  
 İzleme penceresi değişkenleri değerlendirmek için kullanılır. Değişkenlerin değerlerini de değiştirebilirsiniz.  
  
 İzleme penceresinde görüntülenen geçerli bağlam (çağrı yığınında en üst öğe) için değişkenlerdir. Bağlam değiştirirseniz, İzleme penceresinde güncelleştirir ve bu bağlam için ayarlanan değişkenler görüntüler.  
  
## <a name="call-stack-window"></a>Çağrı yığını penceresi  
 Çağrı yığını penceresinde işlev adlarını çağrı yığını, parametre türleri ve parametre değerlerini görüntülemek için kullanılır. Çağrı yığını bilgileri yalnızca ayıklanan programın bir kesme durumunda olduğunda gösterilir.  
  
 Çağrı yığınını XSLT yürütme oluşturulmak çeşitli bağlamı temsil eder. Örneğin, şablondan bir çağrı ise "a" Şablon "b", şablon "a" ve "b" şablonu görünür çok üst listenin geçerli bağlam ile çağrı yığını penceresindeki. Kullanıcı şu anda yürütülmekte olan sorgu görebilirsiniz.  
  
 Şablonlar XSLT dosyasında bir adı yoksa, XSLT işlemcisi tarafından oluşturulan adları kullanılır.  
  
 Bir listenin üst kısmındaki dışında bir öğeye tıklandığında Burada XSLT yürütme dal standart yeşil vurgu kullanarak oldu ve yeşil ok Görüntüleyicisi gösterir.  
  
## <a name="quickwatch-dialog-box"></a>QuickWatch iletişim kutusu  
 **QuickWatch** iletişim kutusu, XPath 1.0 ifade değerlendirmek için kullanılır. Bağlam düğümünün ( `self::node()` Yereller penceresinde düğüm) için XPath ifadesinin yürütme bağlamı sağlar. XPath ifadesini yürütmenin sonucu İzleme penceresinde görüntülenir.  
  
 Aşağıdaki listede, XPath ifadesi değerlendirmesi üzerinde bazı kısıtlamaları açıklamaktadır.  
  
- Yerleşik XPath işlevleri izin verilir.  
  
- Yerleşik XSLT işlevleri gibi `document()`, `key()`ve benzeri izin verilmez.  
  
- Kullanıcı tanımlı işlevlerde izin verilmez.  
  
  Daha fazla bilgi için [nasıl yapılır: bir XPath ifadesini değerlendirme](../xml-tools/how-to-evaluate-an-xpath-expression.md).  
  
## <a name="disassembly-window"></a>Ayrıştırma penceresi  
 Ayrıştırılmış kod penceresini XSLT derleyici tarafından oluşturulan bütünleştirilmiş kodu gösterir. Bu pencerede diğer Visual Studio çözümünü windows ile aynı şekilde kullanılabilir.  
  
 Daha fazla bilgi için [nasıl yapılır: Ayrıştırılmış kod penceresini kullanma](../debugger/how-to-use-the-disassembly-window.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XSLT hata ayıklama](../xml-tools/debugging-xslt.md)   
 [Hata ayıklayıcı temel bilgileri](../debugger/debugger-basics.md)   
 [Değişken Windows](http://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)

