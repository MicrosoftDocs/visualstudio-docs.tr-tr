---
title: Özellikler Penceresi
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- properties [Visual Studio], Properties Window
- handler functions, Properties window
- handlers, Properties window
- Windows messages
- properties [Visual Studio], setting at design time
- properties [Visual Studio], editing
- Property Browser
- Windows messages, adding message handlers
- Properties window, overrides
- virtual functions, Properties window
- Properties window
ms.assetid: e6e0fa4f-75c4-4a52-af15-281cd61876ca
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2848a8197dfe62836918de51ae6e7d01677dac6d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947306"
---
# <a name="properties-window"></a>Özellikler Penceresi
Tasarım zamanı özellikleri ve olayları düzenleyicileri ve tasarımcıları bulunan Seçili nesnelerin görüntülemek ve değiştirmek için bu pencereyi kullanın. Aynı zamanda **özellikleri** dosya, proje ve çözüm özelliklerini görüntülemek ve düzenlemek için penceresi. Bulabileceğiniz **özellikleri** penceresinde **Görünüm** menüsü. Ayrıca, F4 tuşuna basarak veya yazarak açabilirsiniz **özellikleri** içinde **hızlı başlatma** penceresi.

 **Özellikleri** penceresi belirli bir özellik gereksinimlerine bağlı olarak alanları düzenleme farklı türlerini görüntüler. Bu alanları düzenleme düzenleme kutularını, açılan listeleri ve özel Düzenleyici iletişim kutuları bağlantılar içerir. Gri gösterilen özellikleri salt okunurdur.

## <a name="uielement-list"></a>UIElement Listesi
 Nesne adı

 Seçili nesneyi ya da nesneleri listeler. Etkin Düzenleyicisi'ni veya Tasarımcısı nesneler yalnızca görünür. Birden çok nesne seçtiğinizde, yalnızca seçilen tüm nesneleri için ortak olan özellikleri görünür.

 Kategorilere

 Tüm özellikleri ve seçili nesne için özellik değerlerine kategoriye göre listeler. Görünür özellikleri sayısını azaltmak üzere bir kategori daraltabilirsiniz. Genişletmek veya daraltmak için bir kategori, gördüğünüz artı (+) veya eksi (-) sol tarafındaki kategori adı. Kategoriler alfabetik olarak listelenir.

 Alfabetik

 Alfabetik olarak tüm tasarım zamanı özellikleri ve olayları seçilen nesneler için sıralar. Undimmed özelliği düzenlemek için sağ tıklatın ve değişiklikleri girin.

 Özellik Sayfaları

 Görüntüler **özellik sayfaları** iletişim kutusu veya **Proje Tasarımcısı** seçili öğe için. Özellik sayfaları görüntüler veya bir alt kümesi, aynı bulunan özellikleri'nin bir üst **özellikleri** penceresi. Projenizin etkin yapılandırması ile ilgili özelliklerini görüntülemek ve düzenlemek için bu düğmeyi kullanın.

 Özellikler

 Bir nesne özelliklerini görüntüler. Birçok nesne kullanılarak görüntülenebilir olayları de **özellikleri** penceresi.

 Özellik kaynağını göre sırala

 Stilleri ve bağlamaları grupları özellikleri devralma gibi kaynak tarafından uygulanır. Yalnızca Tasarımcısı'nda XAML dosyaları düzenlerken kullanılabilir.

 Olaylar

 Bir nesne için olayları görüntüler.

> [!NOTE]
> Bu **özellikleri** penceresi araç çubuğu denetimi kullanılabilir yalnızca form veya denetimi Tasarımcısı bağlamında etkin olduğu bir [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projesi. XAML dosyaları düzenlerken, olayları penceresinin ayrı bir sekmesinde görünür.


 İletiler

 Tüm Windows iletilerini listeler. Ekleme veya silme seçilen sınıf için sağlanan iletileri için belirtilen işleyici işlevleri sağlar.

> [!NOTE]
> Bu **özellikleri** penceresi araç çubuğu denetimi yalnızca kullanılabilir olduğunda **sınıf görünümü** etkin pencere bağlamında bir [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projesi.


 Geçersiz Kılmalar

 Seçilen sınıf için tüm sanal işlevleri listeler ve ekleme veya silme geçersiz kılma işlevleri sağlar.

> [!NOTE]
> Bu **özellikleri** penceresi araç çubuğu denetimi yalnızca kullanılabilir olduğunda **sınıf görünümü** etkin pencere bağlamında bir [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projesi.


 Açıklama bölmesi

 Özellik türü ve özellik kısa bir açıklamasını gösterir. Kapatıp kısayol menüsünde Açıklama komutunu kullanarak özellik açıklaması kapatabilirsiniz.

> [!NOTE]
> Bu **özellikleri** penceresi araç çubuğu Denetimi kullanılamaz Tasarımcısı'nda XAML dosyaları düzenlerken.


 Küçük resim görünümü

 Seçili olan öğenin görsel gösterimi Tasarımcısı'nda XAML dosyaları düzenlerken gösterir.

 Ara

 Özellikler ve XAML dosyaları Tasarımcısı'nda düzenlerken olaylar için bir arama işlevini sağlar. Arama kutusuna kısmi sözcük aramaları için yanıt verir ve siz yazarken arama sonuçları güncelleştirmeler.

## <a name="see-also"></a>Ayrıca Bkz.

- [Proje Özellikleri Başvurusu](../../ide/reference/project-properties-reference.md)
- [Pencere düzenlerini özelleştirme](../../ide/customizing-window-layouts-in-visual-studio.md)