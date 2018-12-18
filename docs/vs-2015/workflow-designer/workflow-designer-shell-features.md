---
title: İş Akışı Tasarımcısı Kabuk özellikleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 0f75d545055a4657ed4cefdbafe211ea2f34680f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49275307"
---
# <a name="workflow-designer-shell-features"></a>İş Akışı Tasarımcısı Kabuk Özellikleri
[!INCLUDE[wfd1](../includes/wfd1-md.md)] üç temel kullanıcı Arabirimi alanları oluşur: tasarım yüzeyinde, içerik haritası çubuğu üstünde ve altındaki Kabuk. Ekranın en üstünde konumlandırılmış içerik haritası çubuğu, geçerli bir kök etkinlik öncüleri listesini görüntülemek için kullanılır. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Nasıl yapılır: içerik haritası gezintisini kullanma](../workflow-designer/how-to-use-breadcrumb-navigation.md). Tasarımcı yüzeyine konumlandırılmış ekranın merkezinde, iş akışları oluşturmak için kullanılır. Ekranın alt kısmında konumlandırılmış Kabuk geçerli görünümü yönetme düğmelerini içerir.  
  
## <a name="shell-features"></a>Kabuk özellikleri  
 Kabuk düğmeleri yakınlaştırma veya uzaklaştırma iş akışınızı, iş akışınızın, ekran boyutuna içindekilere ve Göster veya gizle genel bakış haritasını için kullanabileceğiniz çubuğunun sağ tarafında vardır. İçine veya dışına CTRL ++ ve CTRL + klavye kısayollarını kullanarak iş akışı yakınlaştırma yapabilirsiniz-.  
  
## <a name="overview-map"></a>Genel Bakış haritasını  
 Genel Bakış haritasını, tüm alt öğelerini ve tüm genişletilmiş bunların alt öğeleri dahil olmak üzere geçerli içerik haritası kökündeki tüm etkinlik küçük bir sürümünü görüntüler. Görünüm penceresi, şu anda Düzenleyicisi içinde görüntülenen bir etkinlik kısmını vurgular turuncu bir kenarlık ile bir dikdörtgen yoktur. Genel Bakış haritasını çevresinde bir dikdörtgen sürükleyerek iş akışı Tasarımcısı kaydırılır ve düzenleyici görünümünü değiştirir.  
  
> [!NOTE]
>  [!INCLUDE[wfd2](../includes/wfd2-md.md)] Kullanıcı arabirimi sanallaştırılmış. Etkinlik tasarımcıları, yalnızca gerekli olduğunda işlenir. İş akışının bir kısmını hiçbir zaman Tasarımcı yüzeyinde düzenlendi, söz konusu bölümü genel bakış harita üzerinde beyaz olarak görünür. Genel Bakış haritasını tamamen kaydırma iş akışı çizer.  
  
## <a name="copying-or-saving-workflows-as-images"></a>Kopyalama veya görüntü olarak iş akışları kaydediliyor  
 İş akışları, bit eşlem biçiminde kopyalanamaz veya bit eşlem ya da vektör biçiminde kaydedilmiş. Kopyalama veya görüntü kaydetme kökünde tüm alt öğelerini ve tüm genişletilmiş alt öğelerini başka bir programa dahil olmak üzere geçerli içerik haritası, tüm etkinlik görünümünü dışarı aktarmak için bir yol sağlar.  
  
 Görüntü olarak Kopyala için herhangi bir yere Tasarımcısı seçin sağ tıklayıp **görüntü olarak Kopyala**. Görüntü olarak kaydetmek için her yerde Tasarımcısı seçin sağ tıklayın ve **görüntüyü farklı Kaydet**. İş akışları, JPG, GIF, PNG ya da XPS biçiminde kaydedilebilir. Biçimi seçildiğinde **Kaydet** iletişim kutusunda **farklı kaydetme türü:** pencerenin alt kısmındaki liste kutusunda aşağı açılır.  
  
## <a name="fonts-and-colors"></a>Yazı tipleri ve renkler  
 Kullanılan yazı tipleri [!INCLUDE[wfd2](../includes/wfd2-md.md)] içinde [!INCLUDE[vs2010](../includes/vs2010-md.md)] ortam yazı tipi tarafından denetlenir. Görüntülenen renkleri [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüksek karşıtlık renk şeması için işletim sistemi temanızı kullanıyorsanız değiştirin. Yeniden başlatmanız gerekir [!INCLUDE[vs2010](../includes/vs2010-md.md)] değişikliklerin etkili olabilmesi için yazı tipi veya renk ayarlarını değiştirdikten sonra [!INCLUDE[wfd2](../includes/wfd2-md.md)].