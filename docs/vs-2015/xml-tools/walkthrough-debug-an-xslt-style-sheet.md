---
title: 'İzlenecek yol: bir XSLT stil sayfasında hata ayıklama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 10dad7382a30800675c257a4e2c8219d20e5b18b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887706"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>İzlenecek Yol: XSLT Stil Sayfasında Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu kılavuzda açıklanan adımları XSLT hata ayıklayıcının kullanımını göstermektedir. Değişkenleri görüntüleme, kesme noktaları ayarlama ve kod içerisinde ilerlemeye adımlar içerir. Stil sayfası aşağıdaki ortalama kitap Fiyat Maliyet tüm kitaplar bulur.  
  
### <a name="to-prepare-for-this-walkthrough"></a>Bu adım adım izleme için hazırlanmak amacıyla  
  
1.  Herhangi bir açık çözümü kapatın.  
  
2.  İki örnek dosyaları yerel bilgisayarınıza kopyalayın.  
  
## <a name="start-debugging"></a>Hata Ayıklamayı Başlat  
  
#### <a name="to-start-debugging"></a>Hata ayıklamayı başlatmak için  
  
1. Gelen **dosya** menüsünde **açık**, tıklatıp **dosya**.  
  
2. BelowAvg.xsl dosyasını bulun ve tıklayın **açık**.  
  
    Stil sayfası XML Düzenleyicisi'nde açılır.  
  
3. Gözat düğmesine tıklayın (**...** ) üzerinde **giriş** belge penceresinin alan.  
  
4. Books.xml dosyasını bulun ve tıklatın **açık**.  
  
    Bu XSLT dönüşümü için kullanılan kaynak dosyanın ayarlar.  
  
5. Sağ `xsl:if` başlangıç etiketi, işaret **kesme noktası**, tıklatıp **kesme noktası Ekle**.  
  
6. Tıklayın **hata ayıklama XSL** XML Düzenleyicisi araç çubuğu düğmesi.  
  
   Bu, hata ayıklama işlemi başlar ve hata ayıklayıcı tarafından kullanılan birkaç yeni pencereler açılır.  
  
   Giriş belgesi ve stil sayfasını görüntülemek iki pencere vardır. Hata ayıklayıcı bu windows geçerli yürütme durumunu göstermek için kullanır. Hata ayıklayıcı konumlandırılıp `xsl:if` stil sayfası ve ilk books.xml dosyasını kitap düğümünde öğesi.  
  
   Yerel öğeler penceresi, tüm yerel değişkenlerin ve geçerli değerlerini görüntüler. Bu stil sayfası ve ayrıca hata ayıklayıcı şu anda bağlam içinde olan düğümleri izlemek için kullandığı değişkenleri tanımlanan değişkenler içerir.  
  
   **XSL çıkış** penceresi XSL Dönüştürme çıktısını görüntüler. Bu pencere ayrıdır **Visual Studio çıkış** penceresi.  
  
## <a name="watch-window"></a>İzleme penceresi  
  
#### <a name="to-use-the-watch-window"></a>İzleme penceresinde kullanmak için  
  
1.  Gelen **hata ayıklama** menüsünde **Windows**, işaret **Watch**, tıklatıp **Watch 1**.  
  
     Bu Watch 1 penceresi görünür hale getirir.  
  
2.  Tür `$bookAverage` içinde **adı** alanına girin ve ENTER tuşuna basın.  
  
     Değerini `$bookAverage` değişken penceresinde görüntülenir.  
  
3.  Tür `self::node()` içinde **adı** alanına girin ve ENTER tuşuna basın.  
  
     `self::node()` Geçerli bağlam düğümünün için değerlendirilen bir XPath ifadesidir. Değerini `self::node()` XPath ifadesidir ilk kitap düğümü. Bu dönüşüm ilerledikçe değiştirir.  
  
4.  Genişletin `self::node()` düğümünü ve ardından `price` düğümü.  
  
     Bu kitap Fiyat değeri görmenizi sağlar ve bunu kolayca karşılaştırabilirsiniz `$bookAverage` değeri. Kitap fiyat Ortalamanın altında olduğundan `xsl:if` koşul başarılı olması gerekir.  
  
## <a name="step-through-the-code"></a>Kodu adımlayın  
 Hata ayıklayıcı bir defada bir satır kod yürütmek sağlar.  
  
#### <a name="to-step-through-the-code"></a>Kodunuz içinde adım adım için  
  
1.  Tuşuna **F5** devam etmek için.  
  
     İlk kitap düğümün memnun çünkü `xsl:if` koşulu, kitap düğümün XSL çıkış penceresine eklenir. Hata ayıklayıcı üzerinde yeniden konumlandırılmış kadar yürütülmeye devam `xsl:if` stil sayfası öğesinde. Hata ayıklayıcı artık books.xml dosyasını ikinci kitap düğümde konumlandırılır.  
  
     Watch1 penceresinde `self::node()` için ikinci kitap düğümün değerini değiştirir. Fiyat öğenin değerini inceleyerek fiyat ortalamanın üstünde, bu nedenle olduğunu anlayabilirsiniz `xsl:if` koşul başarısız olmalıdır.  
  
2.  Tuşuna **F5** devam etmek için.  
  
     İkinci kitap düğümün karşılamıyorsa çünkü `xsl:if` koşulu, kitap düğümün XSL çıkış penceresinde eklenmez. Hata ayıklayıcı üzerinde yeniden konumlandırılmış kadar yürütülmeye devam `xsl:if` stil sayfası öğesinde. Hata ayıklayıcısı artık üçüncü konumlandırıldı `book` books.xml dosyasını düğümü.  
  
     Watch1 penceresinde `self::node()` üçüncü kitap düğümün değerini değiştirir. Değerini inceleme tarafından `price` öğesi, fiyat Ortalamanın altında bu nedenle olduğunu belirleyebilir `xsl:if` koşul başarılı olması gerekir.  
  
3.  Tuşuna **F5** devam etmek için.  
  
     Çünkü `xsl:if` koşulu karşılandı üçüncü kitap XSL çıkış penceresine eklenir. XML belgesi içindeki tüm kitaplar işlenen ve hata ayıklayıcıyı durdurur.  
  
## <a name="sample-files"></a>Örnek dosya  
 Aşağıdaki iki dosyada izlenecek yol tarafından kullanılır.  
  
### <a name="belowavgxsl"></a>belowAvg.xsl  
  
```  
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
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XSLT Hatalarını Ayıklama](../xml-tools/debugging-xslt.md)

