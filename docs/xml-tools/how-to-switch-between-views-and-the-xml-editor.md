---
title: 'Nasıl yapılır: görünümleri ve XML düzenleyicisini arasında geçiş yapma'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b0eb90f2ead313ce94d609d71385b595f3e964b
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2018
ms.locfileid: "34477736"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>Nasıl yapılır: görünümleri ve XML düzenleyicisini arasında geçiş yapma

Bu konu, XML şema Tasarımcısı (XSD Tasarımcı) görünümleri ve XML düzenleyicisini arasında geçiş yapma gösterir. Bu örnekte [satın alma siparişi şeması](../xml-tools/sample-xsd-file-simple-schema.md).

## <a name="to-switch-between-the-views-and-the-xml-editor"></a>XML Düzenleyicisi'ni ve görünümleri arasında geçiş yapmak için

1.  Oluşturun ve yeni bir XML şema dosyası düzenlemek için adımları [nasıl yapılır: oluşturma ve bir XSD şema dosyası düzenleme](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  XML şema Tasarımcısı için XML Düzenleyicisi'nden geçiş yapmak için herhangi bir yere XML Düzenleyicisi'nde sağ tıklatıp **Görünüm Tasarımcısı**.

3.  Filigran kullanılarak grafik görünümüne geçiş yapmak için tıklatın **düğümleri arasındaki ilişkiyi görmek için grafik görünümü kullanmak** Başlat görünümündeki bağlantı.

4.  Sürükleme `USAddress` düğümden **XML Şeması Explorer** grafik görünümü üzerine. Sağ `USAddress` seçin ve grafik görünümü düğümünde **Göster içerik modeli görünümünde** bağlam menüsünde.

     İçerik modeli görünümü ayrıntılarıyla `USAddress` düğümü görüntülenir.

5.  Araç çubuğunu kullanarak içerik modeli görünümünden başlatmak görünümüne geçiş yapmak için tıklatın **Başlangıç'ı** XSD araç çubuğunda.

6.  Kısayol tuşlarını kullanarak görünümleri arasında geçiş yapmak için basın **Ctrl**+**1** Başlat görünüm için **Ctrl**+**2** Grafik görünümü için ve **Ctrl**+**3** içerik modeli görünümü.

7.  İçerik modeli görünümünden XML Düzenleyici'ye gidin, düğümünü sağ tıklatın ve seçin **görünümü kodu** bağlam menüsünde.