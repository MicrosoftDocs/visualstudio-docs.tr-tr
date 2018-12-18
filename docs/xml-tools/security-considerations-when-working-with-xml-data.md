---
title: XML Verileriyle Çalışırken Dikkat Edilecek Güvenlik Konuları
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6db64424e1b503f4835f268fad9fdc5b8648b150
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572611"
---
# <a name="security-considerations-when-working-with-xml-data"></a>XML verileriyle çalışırken güvenlik konuları

Bu konuda XML Düzenleyicisi'ni veya XSLT hata ayıklayıcısı ile çalışırken hakkında bilmeniz gereken güvenlik konuları anlatılmaktadır.

## <a name="xml-editor"></a>XML Düzenleyicisi

 XML Düzenleyicisi'ni üzerinde Visual Studio Metin Düzenleyicisi'ni temel alır. Kullanır. <xref:System.Xml> ve <xref:System.Xml.Xsl> XML işlemlerin çoğunu işlemek için sınıflar.

-   XSLT dönüştürmeleri yeni bir uygulama etki alanında çalıştırılır. XSLT dönüştürmeleri olan *korumalı*; diğer bir deyişle, bilgisayarınızın kod erişimi güvenlik ilkesi XSLT stil sayfası bulunduğu üzerinde göre kısıtlı izinleri belirlemek için kullanılır. Örneğin, tam güven ile çalışacak sabit diskinize stil sayfaları kopyalanmasını ancak bir Internet konumdan stil sayfaları en kısıtlı izinlere sahip.

-   <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı, Microsoft Ara dile yürütme sırasında daha hızlı performans için XSLT derlemek için kullanılır.

-   XML Düzenleyicisi'ni ilk kez yüklediğinde Katalog dosyasındaki bir dış konuma noktası şemaları otomatik olarak yüklenir. <xref:System.Xml.Schema.XmlSchemaSet> Sınıfı şemaları derlemek için kullanılır. Tüm dış şemaları bağlantılar XML Düzenleyicisi ile birlikte gelen katalog dosyası yok. Şema dosyası XML Düzenleyicisi'ni indirir önce açıkça dış şeması başvuru eklemek kullanıcının vardır. HTTP indirmeyi devre dışı bırakılabilir aracılığıyla **çeşitli Araçlar Seçenekler** sayfa XML Düzenleyicisi için.

-   XML Düzenleyicisi'ni kullanan <xref:System.Net> şemaları indirmek için sınıflar

## <a name="xslt-debugger"></a>XSLT hata ayıklayıcı

 XSLT hata ayıklayıcı Visual Studio yönetilen hata ayıklama motorunu kullanır ve gelen sınıfları <xref:System.Xml> ve <xref:System.Xml.Xsl> ad alanı.

-   XSLT hata ayıklayıcı her XSLT dönüşümü korumalı uygulama etki alanında çalışır. Kod erişimi güvenlik ilkesi bilgisayarınızın XSLT stil sayfası bulunduğu üzerinde göre kısıtlı izinleri belirlemek için kullanılır. Örneğin, tam güven ile çalışacak sabit diskinize stil sayfaları kopyalanmasını ancak bir Internet konumdan stil sayfaları en kısıtlı izinlere sahip.

-   XSLT stil sayfası derlenip <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.

-   XSLT ifade değerlendiricisi yönetilen hata ayıklama altyapısı tarafından yüklenir. Yönetilen hata ayıklama altyapısı tüm kod kullanıcının yerel bilgisayardan çalıştırıldığını varsayar. Buna göre <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı XSLT dosyasını kullanıcının yerel bilgisayara yükler. Sınırlı izinlere sahip yeni bir uygulama etki alanındaki tüm XSLT dönüştürmeleri yürüterek yürütme ayrıcalık içinde bir ayrıcalık oluşabilir olasılığı azalır

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama etki alanları](/dotnet/framework/app-domains/application-domains)