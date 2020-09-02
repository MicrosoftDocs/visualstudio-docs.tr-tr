---
title: İş Akışı Tasarımcısı 'de hata Iletileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d89c0dcad23a91ec6057311b9afde7d6d4702772
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656763"
---
# <a name="error-messages-in-workflow-designer"></a>İş Akışı Tasarımcısında Hata İletileri
Bu konu, ile çalışırken karşılaşılabilecek hata iletilerinin türlerini açıklar [!INCLUDE[wfd1](../includes/wfd1-md.md)] .

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>İş Akışı Tasarımcısı hatanın oluştuğu durumlar
 Hatalar [!INCLUDE[wfd2](../includes/wfd2-md.md)] aşağıdaki durumlarda oluşur:

1. İfadede bir hata var.

2. Etkinliğin doğrulama kısıtlamaları karşılanmadı.

3. XAML dosyasında bir etkinliğin yüklenmesine neden olan hatalar vardır.

4. XAML dosyasında iş akışının yükleme başarısız olmasına neden olan hatalar vardır.

   Geçersiz ifadeler ve karşılanmamış doğrulama kısıtlamaları iş akışının derlenmemesine neden olmaz. İş akışınızı oluşturma işlemi başarılı olur, ancak <xref:System.Activities.InvalidWorkflowException> çalışma zamanında bir oluşturulur. XAML dosyasında hatalar varsa, yapı başarısız olur.

   İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , bir iş akışı yüklendiğinde, hata **hata listesi**görüntülenir. Hatanın kaynağı olan etkinliğe gitmek için **hata listesi**hataya çift tıklayın.

### <a name="expression-errors"></a>İfade hataları
 Geçersiz bir ifade, ifadenin yanındaki beyaz ünlem işaretine sahip kırmızı bir daire ile belirtilir. Bu simgenin üzerine gelindiğinde, hatanın kaynağını açıklayan bir araç ipucu görüntülenir. İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , hata kaynağının altını çizili çizgiyi görüntülemek için ifadeye tıklayın. Çizgili metnin üzerine gelindiğinde, hatanın kaynağını açıklayan bir araç ipucu görüntülenir.

### <a name="activity-validation-errors"></a>Etkinlik doğrulama hataları
 Etkinliğin doğrulama kısıtlamaları karşılanmadığı zaman, etkinliğin sağ üst köşesinde beyaz ünlem işaretine sahip kırmızı bir daire görünür. Bu simgenin üzerine gelindiğinde, hatanın kaynağını açıklayan bir araç ipucu görüntülenir.

### <a name="xaml-load-errors"></a>XAML yükleme hataları
 Bir etkinlik yüklenemediğinde, "XAML içindeki hatalar nedeniyle etkinlik yüklenemedi" metnini içeren kırmızı bir kutu görünür. Bu genellikle etkinliğin türü çözümlenemediğinde oluşur. Geçersiz etkinlik, kırmızı kutuyu seçerek ve silerek tasarımcıda silinebilir.

### <a name="workflow-load-errors"></a>İş akışı yükleme hataları
 Bir iş akışı yüklemesi başarısız olduğunda, "İş Akışı Tasarımcısı metin, çalışma akışının hatasına neden olan özel durum bilgileri ve tasarımcı yüzeyinde" belgenizde sorunlarla karşılaştı "şeklinde görünür. Bu genellikle XAML dosyası ayrıştırılamadığınızda meydana gelir.