---
title: Özellikler penceresi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a3faa4b9e0bf7d0ad59a33ed93f895a83e6ff8dc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282379"
---
# <a name="properties-window"></a>Özellikler Penceresi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Tasarım zamanı özelliklerini ve düzenleyicilerde ve tasarımcılarda bulunan seçilen nesnelerin olaylarını görüntülemek ve değiştirmek için bu pencereyi kullanın. Ayrıca **özellikleri** düzenlemek ve dosya, proje ve çözüm özelliklerini görüntülemek için penceresi. Bulabilirsiniz **özellikleri** penceresinde **görünümü** menüsü. Ayrıca, F4 tuşuna basarak veya yazarak açabileceğiniz **özellikleri** içinde **hızlı başlatma** penceresi.  
  
 **Özellikleri** farklı tür alanları, belirli bir özelliğin gereksinimlerine bağlı olarak düzenleme penceresinde görüntülenir. Bu düzenleme alanları düzenleme kutuları, açılan listeler ve özel Düzenleyici iletişim kutularına bağlantılar içerir. Gri renkle gösterilen özellikler salt okunurdur.  
  
## <a name="uielement-list"></a>UIElement Listesi  
 Nesne adı  
 Seçili nesneyi ya da nesneleri listeler. Sadece aktif Düzenleyici veya tasarımcı nesnelerden görülebilir. Birden çok nesne seçtiğinize, yalnızca seçilen tüm nesneler için ortak olan özellikler görünür.  
  
 Kategorilere ayrılmış  
 Kategoriye göre tüm özellikleri ve seçili nesne için özellik değerlerini listeler. Görünür özelliklerin sayısını azaltmak için bir kategoriyi daraltabilirsiniz. Genişlet veya daralt bir kategori artı görürsünüz (+) veya eksidir (–) sol tarafındaki kategori adı. Kategoriler alfabetik olarak listelenir.  
  
 Alfabetik  
 Tüm tasarım zamanı özelliklerini ve seçilen nesnelerin olaylarını alfabetik olarak sıralar. Soluklaşmamış bir özelliği düzenlemek için sağındaki hücreyi tıklatın ve değişiklikleri girin.  
  
 Özellik Sayfaları  
 Görüntüler **özellik sayfaları** iletişim kutusu veya **Proje Tasarımcısı** seçili öğe için. Özellik sayfaları görüntüler bir alt kümesini aynısını veya bulunan özelliklerin bir alt kümesi **özellikleri** penceresi. Projenizin etkin yapılandırması ile ilgili özellikleri görüntülemek ve düzenlemek için bu düğmeyi kullanın.  
  
 Özellikler  
 Bir nesne için özellikleri görüntüler. Çok sayıda nesne kullanılarak görüntülenebilen olayları de **özellikleri** penceresi.  
  
 Özellik kaynağına göre sırala  
 Stiller ve bağlamalar gibi devralma, bir kaynağa göre özellikleri gruplandırır uygulanır. Yalnızca tasarımcıdaki XAML dosyaları düzenlerken kullanılabilir.  
  
 Olaylar  
 Bir nesne için olayları görüntüler.  
  
> [!NOTE]
>  Bu **özellikleri** penceresi araç çubuğu denetimi yalnızca yok bir form veya Denetim Tasarımcısı olduğunda bağlamında etkin bir [!INCLUDE[csprcs](../../includes/csprcs-md.md)] proje. XAML dosyalarını düzenlerken, olaylar Özellikler penceresinin ayrı bir sekmede görünür.  
  
 İletiler  
 Tüm Windows iletilerini listeler. Ekleme veya silme seçilen sınıf için sağlanan iletilerin belirtilen işleyici işlevlerini sağlar.  
  
> [!NOTE]
>  Bu **özellikleri** penceresi araç çubuğu denetimi yalnızca kullanılabilir olduğunda **sınıf görünümü** bağlamında etkin pencere bir [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] proje.  
  
 Geçersiz Kılmalar  
 Seçilen sınıf için tüm sanal işlevleri listeler ve ekleme veya silmeyi geçersiz kılma işlevleri sağlar.  
  
> [!NOTE]
>  Bu **özellikleri** penceresi araç çubuğu denetimi yalnızca kullanılabilir olduğunda **sınıf görünümü** bağlamında etkin pencere bir [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] proje.  
  
 Açıklama bölmesi  
 Özellik türünü ve özelliğin kısa bir açıklamasını gösterir. Ve kısayol menüsünden Açıklama komutunu kullanarak özelliğin açıklamasını kapatabilirsiniz.  
  
> [!NOTE]
>  Bu **özellikleri** penceresi araç çubuğu denetimi kullanılamıyor tasarımcıdaki XAML dosyaları düzenlerken.  
  
 Küçük resim görünümü  
 Seçili olan öğenin görsel bir temsilini tasarımcıdaki XAML dosyaları düzenlerken gösterir.  
  
 Ara  
 Özellikler ve tasarımcıdaki XAML dosyaları düzenlerken olaylar için bir arama işlevi sağlar. Arama kutusuna, kısmi sözcük aramalarına yanıt verir ve siz yazarken arama sonuçlarını güncelleştirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje Özellikleri başvurusu](../../ide/reference/project-properties-reference.md)   
 [Pencere düzenlerini özelleştirme](../../ide/customizing-window-layouts-in-visual-studio.md)



