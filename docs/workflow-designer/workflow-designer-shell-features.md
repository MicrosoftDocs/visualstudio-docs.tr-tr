---
title: İş Akışı Tasarımcısı Kabuk Özellikleri
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5d881a6c6e14983fd8537d8e78066ef9479b9633
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757216"
---
# <a name="workflow-designer-shell-features"></a>İş Akışı Tasarımcısı Kabuk Özellikleri

İş Akışı Tasarımcısı üç ana UI alandan oluşur: Tasarımcı yüzeyine, içerik haritası çubuğunun üstündeki ve altındaki Kabuk. Ekranın en üstünde konumlandırılmış içerik haritası çubuğunun üst geçerli kök etkinlik öğelerinin listesini görüntülemek için kullanılır. Daha fazla bilgi için bkz: [nasıl yapılır: kullanım içerik haritası Gezinti](../workflow-designer/how-to-use-breadcrumb-navigation.md). Tasarımcı yüzeyine konumlandırılmış ekran Merkezi'nde iş akışları oluşturmak için kullanılır. Ekranın alt kısmında konumlandırılmış Kabuk geçerli görünümü yönetme için düğmeler sayısını içerir.

## <a name="shell-features"></a>Kabuk özellikleri
 Kabuk düğmeleri yakınlaştırmak veya iş akışınızı dışında ekranınızın boyutu iş akışınıza içeriklerin sığması ve Göster veya gizle Genel İnceleme haritası için kullanabileceğiniz çubuğu sağ tarafta vardır. Ayrıca CTRL ++ ve CTRL + klavye kısayollarını kullanarak bir iş akışı dışında ya da yakınlaştırabilirsiniz-.

## <a name="overview-map"></a>Genel İnceleme Haritası
 Genel İnceleme Haritası tüm alt ve tüm genişletilmiş bunların alt öğeleri de dahil olmak üzere geçerli içerik haritası kökündeki tüm etkinlik küçük bir sürümünü görüntüler. Bir Görünüm penceresi, bir dikdörtgen içinde Düzenleyicisi görüntülenmekte etkinlik kısmı vurgular turuncu bir kenarlık yoktur. Genel İnceleme Haritası etrafında dikdörtgen sürükleyerek, iş akışı Tasarımcısı'nı birlikte kayar ve düzenleyici görünümünü değiştirir.

> [!NOTE]
> İş Akışı Tasarımcısı kullanıcı arabirimi sanallaştırılmış. Etkinlik tasarımcıları, yalnızca gerekli olduğunda işlenir. İş akışı bir kısmı hiçbir zaman Tasarımcı yüzeyine düzenlendi, söz konusu bölümü üzerinde genel bakış eşlemesi beyaz olarak görünür. Genel İnceleme Haritası tamamen kaydırma iş akışı çizer.

## <a name="copying-or-saving-workflows-as-images"></a>Kopyalama veya iş akışları görüntü olarak kaydetme
 İş akışları, bit eşlem biçiminde kopyaladığınız veya bitmap veya vektör biçiminde kaydedilmiş. Kopyalama veya görüntü kaydetme tüm alt öğelerini ve başka bir programa genişletilmiş kendi alt dahil olmak üzere geçerli içerik haritası kökündeki tüm etkinlik görünümünü dışa aktarmak için bir yol sağlar.

 Resim olarak kopyalamak için herhangi bir yere Tasarımcısı seçin sağ tıklayın ve **kopya görüntü olarak**. Resim olarak kaydetmek için herhangi bir yere Tasarımcısı seçin sağ tıklayın ve **resmi olarak kaydetmek**. İş akışları, JPG, GIF, PNG ya da XPS biçiminde kaydedilebilir. Biçimi seçili **Kaydet** iletişim kutusunda **farklı türde Kaydet:** liste kutusu pencerenin altındaki aşağı açılır.

## <a name="fonts-and-colors"></a>Yazı tipleri ve renkler

Visual Studio içinde iş akışı Tasarımcısı'nda kullanılan yazı tiplerini ortamı yazı tipi tarafından denetlenir. İşletim sistemi tema için yüksek karşıtlık renk düzenini kullanıyorsanız, iş akışı Tasarımcısı'nda görüntülenen renklerini değiştirin. Visual Studio iş akışı Tasarımcısı'nda değişikliklerin etkili olması bir yazı tipi veya renk ayarlarını değiştirdikten sonra yeniden başlatmanız gerekir.