---
title: Seçenekler sayfası, metin düzenleyici düğümü özellikleri | Microsoft Docs
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
- Tools Options settings, Text Editor node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 19438302-0677-4f4d-9720-5667e6a22ab2
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 88ba9765e292d4f07a7e1392a64270ddf27e8f60
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49241910"
---
# <a name="options-page-text-editor-node-properties"></a>Seçenekler Sayfası, Metin Düzenleyici Düğümü Özellikleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Bu belgede, bazı sayfalar (veya özellik koleksiyonları) açıklanmaktadır ile ilişkili **metin düzenleyici** kategori `DTE.Properties("TextEditor", <Property Page>)`, biri **seçenekleri** iletişim kutusu. Her bir alt bölümünün başlığı kullanılan çağrıdır erişimi `Properties` toplama ve her bir alt bölümdeki tabloda koleksiyondaki özellikler listelenmektedir.  
  
 Visual Basic makrolarındaki [Controlling Options Settings](http://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) geçerli seçeneklerini ve her bir sayfası değerlerini görüntülemek nasıl **seçenekleri** iletişim kutusu.  
  
## <a name="general"></a>Genel  
 `DTE.Properties("TextEditor", "General")`  
  
|Özellik Öğesi Adı|Değer|Açıklama|  
|------------------------|-----------|-----------------|  
|GoToAnchorAfterEscape|Get/Set (Boole)|Varsa `True`, bir seçim varken ESC tuşuna basılması ekleme noktasını seçimi oluşturan eylemin başlatıldığı yere taşıyın. `False` ekleme noktasını seçimin diğer sonuna taşır.|  
|DragNDropTextEditing|Get/Set (Boole)|Seçilen bir metin bölümünü, kopyala veya kes/yapıştır işlemleri için belge içinde bir yerden başka bir yere sürükleyip sürükleyemeyeceğinizi belirler.|  
|HorizontalScrollBar|Get/Set (Boole)|Düzenleyici pencerelerinde yatay kaydırma çubuğu olup olmadığını belirler.|  
|VerticalScrollBar|Get/Set (Boole)|Düzenleyici pencerelerinde dikey kaydırma çubuğu olup olmadığını belirler.|  
|SelectionMargin|Get/Set (Boole)|Metin bölmesinin solunda özel seçim işlemleri, kesme noktası çizimleri vs. için boşluk olup olmadığını belirler.|  
|MarginIndicatorBar|Get/Set (Boole)|Metin bölmesinin sol kenar boşluğunu metin bölmesinin ana gövdesinden ayıran bir dikey çizgi olup olmadığını belirler.|  
|UndoCaretActions|Get/Set (Boole)|Varsa `True`. ekleme noktası hareketini, seçim komutlarını ve benzeri eylemleri önbelleği değiştiren düzenleme yanı sıra geri alma işlemleri içerir.|  
|AutoDelimiterHighlighting|Get/Set (Boole)|Kapanış sınırlayıcısı girmenin, düzenleyicinin açılış sınırlayıcısını vurgulamasına neden olup olmayacağını belirler. Bu özelliğin değerinden bağımsız olarak, düzenleyici açık sınırlayıcıyı her zaman kalın yapar.|  
|EditorEmulation|Get/Set (Enum)||  
|DetectUTF8WithoutSignature|Get/Set (Boole)|Bir dosyanın kodlama imzası olmadığında, UTF-8 kodlaması kullanıp kullanmadığını belirler.|  
|TrackChanges|Get/Set (Boole)||  
  
## <a name="plain-text"></a>Düz Metin  
 `DTE.Properties("TextEditor", "PlainText")`  
  
 `PlainText` Düzenleyici seçenekleri, metin dosyaları düzenlenirken Düzenleyici ayarlarını etkiler. Her programlama dilinin ve [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] paketi olan kendi özel **metin düzenleyici** ayarları. Örneğin, görüntüleme veya değiştirme için [!INCLUDE[csprcs](../../includes/csprcs-md.md)] Düzenleyici ayarları kullanmak `DTE.Properties("TextEditor", "CSharp") or DTE.Properties("TextEditor", "CSharp-Specific")`. İçin **SQL betiğini** Düzenleyici ayarları kullanmak `DTE.Properties("TextEditor", "SQL ")`.  
  
|Özellik Öğesi Adı|Değer|Açıklama|  
|------------------------|-----------|-----------------|  
|AutoListMembers|Get/Set (Boole)|Kullanıcı, bir değişken başvurusunun ardından nokta girdiğinde, kullanılabilir üye listesinin otomatik olarak görünüp görünmeyeceğini belirler.|  
|AutoListParams|Get/Set (Boole)|Kullanıcılar bir işlev adının ardından "(" girdiğinde, bağımsız değişken listesi açıklamasının otomatik olarak görüntülenip görüntülenmeyeceğini belirler.|  
|HideAdvancedMembers|Get/Set (Boole)|Deyim tamamlama özelliğinin tüm üyeleri mi, yoksa sadece sık kullanılanları mı listeleyeceğini belirler.|  
|VirtualSpace|Get/Set (Boole)|Boşluk karakterlerinin grafik olarak görüntülenip görüntülenmeyeceğini belirler. Bu ayar `true` neden `WordWrap` özellik ayarlamak için (Bu listede) öğesinin `false`.|  
|WordWrap|Get/Set (Boole)|Görünümün, uzun satırları sözcük sınırlarından kaydırıp kaydırmayacağını belirler. Bu ayar `true` neden `VirtualSpace` özellik ayarlamak için (Bu listede) öğesinin `false`.|  
|WordWrapGlyphs|Get/Set (Boole)|Satırın sonunda bir karakter (glif) görüntüler; bu da satırın bir sonraki satıra kaydırılacağını gösterir.|  
|EnableLeftClickForURLs|Get/Set (Boole)|Düzenleyicinin URL'lerin altını çizip çizmeyeceğini ve tek sol tıklamanın ilgili URL'yi sistemde kayıtlı Web tarayıcısında açmayı sağlayıp sağlamayacağını belirler.|  
|IndentStyle|Get/Set (<xref:EnvDTE.vsIndentStyle>)|Girintilendirme stilini belirler: Varsayılan, Akıllı veya Yok.|  
|TabSize|Get/Set (Long)|Bir sekmeye eşit gelen boşluk sayısını temsil eder. 1 ila 60 aralığı (sınırlar dahil) dışında bir tamsayı ayarlanması hata verir.|  
|InsertTabs|Get/Set (Boole)|Varsa `True`, girintilendirme yaparken sekme karakterleri kullanılır.|  
|IndentSize|Get/Set (Long)|Tek bir girinti düzeyine eşit boşluk sayısını temsil eder. 1 ila 60 aralığı (sınırlar dahil) dışında bir tamsayı değeri ayarlanması hata verir.|  
|ShowLineNumbers|Get/Set (Boole)|Çekirdek düzenleyici belge görünümünün, sol kenar boşluğu boyunca satır numaraları görüntüleyip görüntülemeyeceğini belirler.|  
|ShowNavigationBar|Get/Set (Boole)|Düzenleyici pencerelerinin en üstünde açılan listeler ve düğmeler görünüp görünmeyeceğini belirler.|  
|CutCopyBlankLines|Get/Set (Boole)|Seçildiklerinde, boş satırları keser veya kopyalar:|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Seçenek ayarlarını denetleme](http://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [Seçenekler sayfasında özellik öğelerinin adlarını belirleme](http://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [Seçenekler sayfası, ortam düğümü özellikleri](../../ide/reference/options-page-environment-node-properties.md)   
 [Seçenekler Sayfası, Yazı Tipleri ve Renkler Düğümü Özellikleri](../../ide/reference/options-page-fonts-and-colors-node-properties.md)



