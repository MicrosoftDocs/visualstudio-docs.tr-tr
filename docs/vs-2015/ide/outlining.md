---
title: Anahat oluşturma | Microsoft Docs
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
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
ms.assetid: d1476758-9d35-4d74-b63c-310661932ecd
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: af7f854f6e097471cdd744537a4be4cbd1646400
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282522"
---
# <a name="outlining"></a>Anahat Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Artı işareti (+) altında görünmesi bir bölge kodu daraltarak bazı kod görünümden gizlemek seçebilirsiniz. Daraltılmış bölgeye, artı işaretine tıklayarak genişletin. (Veya basabilirsiniz için CTRL + M + M bir bölge daraltmak için ve CTRL + M + M yeniden genişletin.) Ayrıca, herhangi bir satırda bölge kodu yalnızca solunda görünür anahat Kenar çubuğunda çift tıklayarak bir anahat oluşturma bölgesi daraltabilirsiniz. Daraltılmış bölgeye geldiğinizde, araç ipucu olarak daraltılmış bölgeye içeriğini görebilirsiniz.  
  
 Kenar boşlukları fare ile üzerine geldiğinizde anahat kenar bölgelerde ayrıca vurgulanır. Varsayılan renk vurgulama renk bazı yapılandırmalarda yerine soluk görünebilir. İçinde değiştirebilirsiniz **Araçlar/Seçenekler/ortam/yazı tipi ve renkler/Collapsible bölge**.  
  
 Anahatları belirlenmiş kodunda çalışırken, üzerinde çalışma, yapılması ve sonra diğer bölümleri için taşıma bunları Daralt istediğiniz bölümleri genişletebilirsiniz. Olmasını istemediğiniz anahat oluşturma görüntülenen, kullanabileceğiniz **Durdur anahat oluşturma** , temel kodu etkilemeden anahat bilgileri kaldırmak için komutu.  
  
 **Geri** ve **Yinele** komutlarını **Düzenle** bu Eylemler menüsü etkiler. **Kopyalama**, **Kes**, **Yapıştır**, ve sürükle ve bırak işlemleri korumak anahat oluşturma bilgileri, ancak Genişletilebilir durumunda. Örneğin, daraltılmış durumda bir bölge kopyaladığınızda **yapıştırın** işlem bir genişletilmiş bölge olarak kopyalanan metni yapıştırın.  
  
> [!CAUTION]
>  Anahatları belirlenmiş bir bölge değiştirdiğinizde, anahat oluşturma kaybolabilir. Örneğin, silme veya bulma ve değiştirme işlemlerini bölge sonuna silme.  
  
 Aşağıdaki komutları bulunabilir **düzenleme/anahat** alt.  
  
|||  
|-|-|  
|Seçimi Gizle|(CTRL + M, CTRL + H) - bir seçili normalde örneğin anahat oluşturma için kullanılabilir olmayacaktır kod bloğu daraltır bir `if` blok. Özel bölge kaldırmak için **geçerli gizlemeyi Durdur** (veya CTRL + M, CTRL + U). Visual Basic'te kullanılabilir değil.|  
|Anahat genişlemesini Değiştir|-Bölüm içinde iç içe geçmiş bir daraltılmış bölümü imleç gerektiği zaman Anahat en içteki geçerli gizli veya genişletilmiş durumunu tersine çevirir.|  
|Tüm ana hattı Değiştir|(CTRL + M, CTRL + L) - tüm bölgeler için aynı durum genişletilmiş veya daraltılmış ayarlar. Bazı bölgelerde genişletilir ve bazı daraltılmış, ardından daraltılmış genişletilmiş bölge.|  
|Ana Hat Oluşturmayı Durdur|(CTRL + M, CTRL + P) - tüm belgeyi tüm ana hat oluşturma bilgilerini kaldırır.|  
|Geçerliyi gizlemeyi Durdur|(CTRL + M, CTRL + U) - şu anda seçili kullanıcı tanımlı bölge için ana hat oluşturma bilgilerini kaldırır. Visual Basic'te kullanılabilir değil.|  
|Tanımlara Daralt|(CTRL + M, CTRL + O) - tüm türlerin üyelerini daraltır.|  
|Bloğu Daralt:\<mantıksal sınır >|(Visual C++) Ekleme noktasını içeren işlevi bir bölgede daraltır. Örneğin, ekleme noktasını bir döngü içinde yer alıyorsa, döngü gizlenir.|  
|Tümünü Daralt: \<mantıksal yapıları >|(Visual C++) İşlevin içindeki tüm yapıları daraltır.|  
  
 Visual Studio SDK'sı, genişletmek veya daraltmak için istediğiniz metin bölgeleri tanımlamak için de kullanabilirsiniz. Bkz: [izlenecek yol: ana hat oluşturmayı](../extensibility/walkthrough-outlining.md).



