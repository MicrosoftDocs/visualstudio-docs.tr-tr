---
title: 'Nasıl yapılır: bir XPath ifadesini değerlendirme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 05758034c0228f0efd7fb3ae63bd3b7e0d5e3095
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210437"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Nasıl yapılır: bir XPath ifadesini değerlendirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XPath ifadeleri ile değerlendirebilirsiniz **QuickWatch** iletişim kutusu. XPath ifadesi W3C XPath 1.0 öneri göre geçerli olmalıdır. Geçerli XSLT bağlam — diğer bir deyişle, `self::node()` düğümünde **Yereller** penceresi — için XPath ifadesini değerlendirme bağlamı sağlar.  
  
 Aşağıdaki listede, hangi işlevlerin bir XPath ifadesi değerlendirilirken desteklenen açıklanmaktadır:  
  
-   Yerleşik XPath işlevleri desteklenir.  
  
-   Yerleşik XSLT işlevleri desteklenmez.  
  
-   Kullanıcı tanımlı işlevleri desteklenmez.  
  
> [!NOTE]
>  Aşağıdaki yordam belowAvg.xsl ve books.xml dosyalarından kullanır [izlenecek yol: bir XSLT stil sayfasında hata ayıklama](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) konu.  
  
### <a name="to-evaluate-an-xpath-expression"></a>Bir XPath ifadesini değerlendirme  
  
1.  Bir kesme noktasında Ekle `xsl:if` başlangıç etiketi.  
  
2.  Tıklayın **hata ayıklama XSL** XML Düzenleyicisi araç çubuğu düğmesi.  
  
     Hata ayıklayıcıyı başlatır ve üzerinde sonları `xsl:if` etiketi.  
  
3.  Sağ tıklayıp **QuickWatch**.  
  
     **QuickWatch** iletişim kutusu görüntülenir.  
  
4.  Girin `./price/text()` içinde **ifade** alanını **QuickWatch** iletişim kutusu ve tıklatın **yeniden değerlendir**.  
  
     Geçerli kitap düğümün fiyatı görünür **değer** kutusu.  
  
5.  XPath ifadesi değiştirme `./price/text() < $bookAverage` tıklatıp **yeniden değerlendir**.  
  
     **Değer** kutusu gösterir XPath ifadesi olarak değerlendirilen `true`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XSLT Hatalarını Ayıklama](../xml-tools/debugging-xslt.md)

