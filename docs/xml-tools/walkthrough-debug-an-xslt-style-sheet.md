---
title: 'İzlenecek Yol: XSLT Stil Sayfasında Hata Ayıklama'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ebc8e8f8700690a2ae74fcc91384fb77b238ea33
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693402"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>İzlenecek yol: bir XSLT stil sayfası hata ayıklama

Bu izlenecek adımları XSLT hata ayıklayıcı kullanımını göstermektedir. Değişkenleri görüntüleme, kesme noktalarını ayarlama ve kod atlama adımları içerir. Stil sayfası maliyet ortalama kitap fiyatı tüm books bulur.

## <a name="to-prepare-for-this-walkthrough"></a>Bu adım adım izleme için hazırlanmak amacıyla

1.  Tüm açık çözümleri kapatın.

2.  İki örnek dosyalarını yerel bilgisayarınıza kopyalayın.

## <a name="start-debugging"></a>Hata ayıklama başlatılamıyor

### <a name="to-start-debugging"></a>Hata ayıklama başlatılamıyor

1.  Gelen **dosya** menüsündeki **açık**, tıklatıp **dosya**.

2.  Bulun *belowAvg.xsl* dosya ve tıklayın **açık**.

     Stil sayfası XML Düzenleyicisi'nde açılır.

3.  Gözat düğmesine (**...** ) üzerinde **giriş** belge penceresinin alan.

4.  Bulun *books.xml* dosya ve tıklayın **açık**.

     XSLT dönüşümü için kullanılan kaynak belge dosyasını ayarlar.

5.  Sağ `xsl:if` başlangıç etiketi, fareyle **kesme noktası**, tıklatıp **kesme noktası Ekle**.

6.  Tıklatın **hata ayıklama XSL** XML Düzenleyicisi araç çubuğunda.

Bu hata ayıklama işlemi başlatır ve hata ayıklayıcı tarafından kullanılan birkaç yeni pencereler açılır.

Giriş belgesi ve stil sayfasını görüntülemek iki windows vardır. Hata ayıklayıcı bu windows geçerli yürütme durumunu göstermek için kullanır. Hata ayıklayıcı üzerinde konumlandırılmış `xsl:if` öğesi stil sayfasının ve ilk kitap düğümünde *books.xml* dosya.

**Yereller** penceresi, tüm yerel değişkenleri ve geçerli değerlerini görüntüler. Bu, stil sayfası ve ayrıca hata ayıklayıcı bağlamda düğümlerini izlemek için kullandığı değişkenleri tanımlanan değişkenler içerir.

**XSL çıkış** penceresi XSL dönüşümün çıktısını görüntüler. Bu pencere ayrıdır **Visual Studio çıkış** penceresi.

## <a name="watch-window"></a>Gözcü penceresi

### <a name="to-use-the-watch-window"></a>Gözcü penceresi kullanmak için

1.  Gelen **hata ayıklama** menüsündeki **Windows**, işaret **izleme**, tıklatıp **izleme 1**.

     Böylece **izleme 1** penceresi görünür.

2.  Tür `$bookAverage` içinde **adı** alan ve tuşuna **Enter**.

     Değeri `$bookAverage` değişken penceresinde görüntülenir.

3.  Tür `self::node()` içinde **adı** alan ve tuşuna **Enter**.

     `self::node()` Geçerli bağlam düğüme değerlendiren bir XPath ifadesidir. Değeri `self::node()` XPath ifadesi ilk kitap düğümü. Bu biz dönüştürme ilerledikçe değiştirir.

4.  Genişletme `self::node()` düğümünü genişletin ve ardından `price` düğümü.

     Bu kitap Fiyat değerini görmenize olanak sağlar ve kendisine kolayca karşılaştırabilirsiniz `$bookAverage` değeri. Kitap fiyat Ortalamanın altında olduğundan `xsl:if` koşul başarılı olması gerekir.

## <a name="step-through-the-code"></a>Kod üzerinden adım
 Hata ayıklayıcı aynı anda bir satır kod yürütmek sağlar.

### <a name="to-step-through-the-code"></a>Kod arasında

1.  Tuşuna **F5** devam etmek için.

     İlk kitap düğümü memnun çünkü `xsl:if` koşul, kitap düğüm eklenmiş olup **XSL çıkış** penceresi. Hata ayıklayıcı üzerinde yeniden konumlandırılmış kadar yürütmeye devam eder `xsl:if` stil sayfası öğesinde. Hata ayıklayıcı Şimdi ikinci kitap düğümünde konumlandırılmış *books.xml* dosya.

     İçinde **izleme 1** penceresi `self::node()` değeri ikinci kitap düğüme değiştirir. Fiyat öğenin değerini inceleyerek, fiyat üzerinde ortalama, böylece olduğunu anlayabilirsiniz `xsl:if` koşulu başarısız olmalıdır.

2.  Tuşuna **F5** devam etmek için.

     İkinci kitap düğümü karşılamadığı için `xsl:if` koşul, kitap düğümü eklenmez **XSL çıkış** penceresi. Hata ayıklayıcı üzerinde yeniden konumlandırılmış kadar yürütmeye devam eder `xsl:if` stil sayfası öğesinde. Hata ayıklayıcı artık üçüncü konumlandırılmış `book` düğümünde *books.xml* dosya.

     İçinde **izleme 1** penceresi `self::node()` değeri üçüncü kitap düğüme değiştirir. Değerini inceleyerek tarafından `price` öğesi, fiyat ortalama, böylece olduğunu belirleyebilir `xsl:if` koşul başarılı olması gerekir.

3.  Tuşuna **F5** devam etmek için.

     Çünkü `xsl:if` koşulu karşılandı üçüncü kitap eklenen **XSL çıkış** penceresi. XML belgesi tüm kitapları işlenir ve hata ayıklayıcısı durdurur.

## <a name="sample-files"></a>Örnek dosyaları

Aşağıdaki iki dosyaları izlenecek yol tarafından kullanılır.

### <a name="belowavgxsl"></a>belowAvg.xsl

```xml
<?xml version='1.0'?>
<xsl:stylesheet version="1.0"
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="xml" encoding="utf-8"/>
  <xsl:template match="/">
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>
    <books>
      <!--Books That Cost Below Average-->
      <xsl:for-each select="/bookstore/book">
        <xsl:if test="price < $bookAverage">
          <xsl:copy-of select="."/>
        </xsl:if>
      </xsl:for-each>
    </books>
  </xsl:template>
</xsl:stylesheet>
```

### <a name="booksxml"></a>Books.XML

```xml
<?xml version='1.0'?>
<!-- This file represents a fragment of a book store inventory database -->
<bookstore>
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">
    <title>The Autobiography of Benjamin Franklin</title>
    <author>
      <first-name>Benjamin</first-name>
      <last-name>Franklin</last-name>
    </author>
    <price>8.99</price>
  </book>
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">
    <title>The Confidence Man</title>
    <author>
      <first-name>Herman</first-name>
      <last-name>Melville</last-name>
    </author>
    <price>11.99</price>
  </book>
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">
    <title>The Gorgias</title>
    <author>
      <name>Plato</name>
    </author>
    <price>9.99</price>
  </book>
</bookstore>
```

## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Hatalarını Ayıklama](../xml-tools/debugging-xslt.md)