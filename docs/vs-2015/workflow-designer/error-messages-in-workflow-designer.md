---
title: İş akışı tasarımcısında hata iletileri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: efd6bc680be42f1074da8d2313b1a4b8e9307580
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894852"
---
# <a name="error-messages-in-workflow-designer"></a>İş Akışı Tasarımcısında Hata İletileri
Bu konu ile çalışırken karşılaşılan hata iletileri türlerini açıklar [!INCLUDE[wfd1](../includes/wfd1-md.md)].  
  
## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>İş akışı tasarımcısında hatalar oluşabilen durumları  
 Hataları [!INCLUDE[wfd2](../includes/wfd2-md.md)] aşağıdaki durumlarda oluşur:  
  
1. Bir ifadede bir hata var.  
  
2. Bir etkinliğin doğrulama kısıtlamaları karşılanmadı.  
  
3. Bir etkinlik yüklenemedi neden XAML dosyasındaki hataları vardır.  
  
4. Neden yüklenmesi başarısız iş akışı XAML dosyasındaki hataları vardır.  
  
   Geçersiz ifade ve hizmetlerinizden doğrulama kısıtlamalarını iş akışı oluşturmak başarısız olmasına neden olmaz. İş akışınızı oluşturma başarılı, ancak bir <xref:System.Activities.InvalidWorkflowException> çalışma zamanında oluşturulur. XAML dosyasında hatalar varsa derleme başarısız oluyor.  
  
   İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], bir iş akışı yüklendiğinde, hatalar görüntülenir **hata listesi**. Hata kaynağı olan etkinliğin gitmek için hataya çift **hata listesi**.  
  
### <a name="expression-errors"></a>İfade hataları  
 Geçersiz bir ifade, kırmızı bir daire ifade yanındaki beyaz bir ünlem işaretiyle gösterilir. Bu simgenin üzerine geldiğinizde, hatanın kaynağını tanımlayan bir araç ipucu görüntülenir. İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ifade hatanın kaynağını çizip çizmeyeceğini satırı görüntülemek için tıklayın. Hatanın kaynağını tanımlayan bir araç ipucu çizgili metin görüntüler geldiğinizde.  
  
### <a name="activity-validation-errors"></a>Etkinlik doğrulama hataları  
 Bir etkinliğin doğrulama kısıtlamaları karşılanmadı etkinliğin sağ üst köşesindeki kırmızı bir daire beyaz bir ünlem işaretiyle görünür. Bu simgenin üzerine geldiğinizde, hatanın kaynağını tanımlayan bir araç ipucu görüntülenir.  
  
### <a name="xaml-load-errors"></a>XAML yükleme hataları  
 Bir etkinlik yük devrettiğinde metniyle "etkinlik XAML içindeki hatalar nedeniyle yüklenemedi" kırmızı kutu görünür. Bu genellikle, etkinliğin türü çözümlenemiyor oluşur. Geçersiz Etkinlik Tasarımcısı'nda kırmızı kutu seçip silerek silinebilir.  
  
### <a name="workflow-load-errors"></a>İş akışı yükleme hataları  
 Yüklenecek bir iş akışı başarısız olduğunda, "Belgenizi sorunlarla karşılaştı iş akışı Tasarımcısı" metin Tasarımcı yüzeyinde yüklemek iş akışının başarısızlığa neden özel durum bilgilerinin yanında görünür. Bu genellikle, XAML dosyası ayrıştırılamıyor oluşur.