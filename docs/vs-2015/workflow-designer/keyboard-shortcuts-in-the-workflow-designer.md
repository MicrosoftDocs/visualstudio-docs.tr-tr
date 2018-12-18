---
title: Klavye kısayolları iş akışı tasarımcısında | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 409a39dc889970ee7ad0eff3354fa43de15b7dbe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895346"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>İş Akışı Tasarımcısında Klavye Kısayolları
Tüm temel işlevlerini [!INCLUDE[wfd1](../includes/wfd1-md.md)] klavye tarafından erişilebilir.  
  
## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Klavyeyi kullanarak iş akışı Tasarımcısı gezinme  
 İçinde [!INCLUDE[vs2010](../includes/vs2010-md.md)], genel kısayolları ve hata ayıklama kısayolları uygulamak [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Ayrıca, bir dizi [!INCLUDE[wfd2](../includes/wfd2-md.md)] özel klavye kısayollarını oluşturuldu. İçinde [!INCLUDE[vs2010](../includes/vs2010-md.md)], tüm klavye kısayollarını uri'lerini. Ancak, yeniden barındırılan bir uygulamada şu klavye kısayollarını sabittir.  
  
### <a name="workflow-designer-keyboard-shortcuts"></a>İş Akışı Tasarımcısı klavye kısayolları  
 Atanan varsayılan klavye kısayolları aşağıdaki tabloda özetlenmiştir [!INCLUDE[wfd2](../includes/wfd2-md.md)] komutları.  
  
|Kısayol|Amaç|  
|--------------|-------------|  
|CTRL + E, A|Bağımsız değişken tasarımcısını gizler veya gösterir.|  
|CTRL+E, C|Seçili etkinlik yerinde daraltır.|  
|CTRL + E, E|Seçili etkinlik yerinde genişletir.|  
|CTRL + E, F|Bir akış grafiğindeki seçili etkinlikler bağlanır.|  
|CTRL + E, I|İçe Aktarılanlar tasarımcısını gizler veya gösterir.|  
|CTRL + E, M|Klavye odağını sekme sırasında bir sonraki öğeye taşır.|  
|CTRL+E, N|Seçili etkinlik (veya en yakın) kapsamında yeni bir değişken oluşturur.|  
|CTRL + E, O|Genel Bakış haritasını gizler veya gösterir.|  
|CTRL + E, P|Seçilen etkinliğin üst gider. Bu içerik haritası gezintisini bir düzey yukarı gider ve tasarımcı yüzeyinde Kök etkinlik değiştirir.|  
|CTRL + E, S|Klavye odağı sahip öğe geçerli seçime ekler.|  
|CTRL+E, V|Değişken tasarımcısını gizler veya gösterir.|  
|CTRL+E, X|İş akışındaki tüm etkinlikler genişletir.|  
|CTRL+ALT+F6|Klavye odağı geçerli kullanıcı Arabirimi alanından dizideki sonraki alanına taşır. Sırayla aşağıdaki gibidir:<br /><br /> 1.  İçerik haritası gezinme çubuğu.<br />2.  Tasarımcı yüzeyi<br />3.  Bağımsız değişkenler/değişkenler/içe Aktarılanlar tasarımcısını açıksa<br />4.  Kabuk|  
  
### <a name="flowchart"></a>Akış Çizelgesi  
 Aşağıdaki liste, bir akış oluşturmak için klavye tarafından kullanılan hareketlerini gösterir. Kalan olduğu gibi [!INCLUDE[wfd2](../includes/wfd2-md.md)], etkinlikleri ile sağlanan genel araç kısayolları kullanılarak Tasarımcı yüzeyine eklenir [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
- Bir etkinlik taşımak için etkinliği seçin ve bunu yeniden konumlandırmak için ok tuşlarını kullanın.  
  
- Bir akış yeniden boyutlandırmak için ok tuşlarını kullanarak akış geçerli kenarlığını geçmiş etkinlik taşıyın. Akış otomatik olarak yeniden boyutlandırılır.  
  
- Etkinlik Başlangıç düğümü olarak ayarlamak için kullanın **BaşlangıçDüğümü ayarlamak** bağlam menüsündeki komutu.  
  
- Etkinlikleri bağlanmak için:  
  
  1.  Kaynak etkinliği için etkinlik sekmelerle seçin.  
  
  2.  CTRL + E, hedef etkinliğe klavye odağı taşımak için gerekli sayıda M tuşuna basın.  
  
  3.  CTRL + E, seçime hedef etkinlik eklemek için S tuşuna basın.  
  
  4.  CTRL + E, bağlayıcı kaynaktan hedefe eklemek için F tuşuna basın.  
  
  Etkinlikleri tarafından klavye bağlama hakkında notlar:  
  
- CTRL + E, f tuşuna basarak önce seçime daha fazla etkinlikler ekleyerek aynı anda birden çok bağlantı yapabilirsiniz Bağlantılar, etkinlikleri seçimi eklendiğini sırada yapılır.  
  
- Kaynak etkinliği giden bir bağlantı zaten varsa, örneğin bir çift etkinlikleri bağlanamaz, seçimdeki etkinlikler arasında diğer bağlantılar hala mümkün olduğunca yapılır.  
  
- Olduğunda bir **FlowDecision** seçime dahil ve **FlowDecision** giden bağlayıcı yok, bağlayıcı yerleştirildiği **True** dal.  
  
### <a name="expression-editing"></a>İfade düzenleme  
 Varsayılan olarak, varsayılan klavye kısayolları [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ifade Düzenleyicisi'nde içinde uygulama metni düzenleme [!INCLUDE[wfd2](../includes/wfd2-md.md)], aşağıdaki kısıtlamalarla:  
  
-   Aşağıdaki komutlar için klavye kısayolları yeniden eşleme, hiçbir etkisi olmaz. Bir ifade düzenlerken bu komutlara erişmek için yalnızca klavye kısayolları kullanabilirsiniz.  
  
    1.  Kes  
  
    2.  Kopyala  
  
    3.  Yapıştır  
  
    4.  Tümünü Seç  
  
    5.  Geri alma  
  
    6.  Yinele  
  
-   İfade içindeki komutları düzenlemek için klavye kısayolları yeniden eşlemek için [!INCLUDE[wfd2](../includes/wfd2-md.md)] içinde [!INCLUDE[vs2010](../includes/vs2010-md.md)], kısayolları Düzenle [!INCLUDE[wfd2](../includes/wfd2-md.md)] kapsam. Metin Düzenleyici kapsamı içinde yapılan değişiklikleri otomatik olarak geçerli olmayan [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Her iki yerde kısayolları eşlemek isterseniz değişiklikleri iki kez uygulamanız gerekir (her kapsam için bir kez).