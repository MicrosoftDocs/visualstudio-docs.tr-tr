---
title: Initializecorrelation etkinlik Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 9dd9d622785fbfebd8560daf9bf459716381ddbf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49234032"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation Etkinlik Tasarımcısı
**Initializecorrelation** etkinlik Tasarımcısı oluşturmak ve yapılandırmak için kullanılan bir <xref:System.ServiceModel.Activities.InitializeCorrelation> gönderme veya alma bunları önce iletileri arasında bir bağıntı kurmak için kullanılan etkinlik.  
  
## <a name="the-initializecorrelation-activity"></a>Initializecorrelation etkinlik  
 Bir <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinliği gönderme veya bir mesaj bağıntılar başlatmak için kullanılır. Genellikle bağıntı veya bir mesaj gönderirken başlatılır. Bir ileti gönderildiğinde veya alındığında önce bağıntı oluşturulmalıdır kullanırsanız <xref:System.ServiceModel.Activities.InitializeCorrelation> bağıntı başlatılamadı.  
  
### <a name="using-the-initializecorrelation-activity-designer"></a>Initializecorrelation etkinlik Tasarımcısı kullanma  
 **Initializecorrelation** etkinlik Tasarımcısı bulunabilir **Mesajlaşma** kategorisi **araç kutusu**, hangi erişilen tıklayarak **araç kutusu**  sekmesinde [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatif olarak, seçin **araç** gelen **görünümü** menüsünden veya CTRL + ALT + X.)  
  
 **Initializecorrelation** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve oturum bırakılan [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyi. Bu, oluşturur bir <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinliği ile bir varsayılan <xref:System.Activities.Activity.DisplayName%2A> InitializeCorrelation.The, <xref:System.Activities.Activity.DisplayName%2A> üst bilgisinde düzenlenebilir **Initializecorrelation** etkinlik Tasarımcısı veya  **DisplayName** kutusunun **özellikleri** penceresi.  
  
 <xref:System.ServiceModel.Activities.CorrelationHandle> Olabilir belirtir **bağıntı** alanındaki **özellikleri** penceresinde **Initializecorrelation** etkinlik Tasarımcı yüzeyine bırakın.  
  
 Yanı sıra üç nokta düğmesini tıklatarak **CorrelationData** alanındaki **özellikleri** penceresi veya "Görünüm..." İpucu metni **Initializecorrelation** etkinlik tasarımcısının yüzeyine görüntüler **başlatmak bağıntı** içinde belirtebilirsiniz bağıntı tanıtıcısı ve anahtar-değer çiftleri için kullanılan iletişim kutusu Bunu başlatın. [!INCLUDE[crabout](../includes/crabout-md.md)] Bu iletişim kutusunu kullanarak bkz [türü koleksiyon Düzenleyicisi iletişim kutusu](../workflow-designer/type-collection-editor-dialog-box.md) konu.  
  
### <a name="the-initializecorrelation-properties"></a>Initializecorrelation özellikleri  
 Aşağıdaki tabloda <xref:System.ServiceModel.Activities.InitializeCorrelation> özellikleri Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. Bu özellikleri de düzenlenebilen **özellikleri** penceresi veya [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyi.  
  
|Özellik adı|Gerekli|Kullanım|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Kolay adı <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinlik. Initializecorrelation varsayılan değerdir.<br /><br /> Ancak kolay için varsayılan olmayan bir değeri kullanımını <xref:System.Activities.Activity.DisplayName%2A> kati şekilde gerekli değil gibi bir değer kullanmak için en iyi bir uygulamadır.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> İş akışı etkinliklerinde bağıntı ilişkilendirmek için kullanılır.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|İş akışı örneği için iletileri ilişkili bağıntı veri sözlüğü.<br /><br /> Kullanım **başlatmak bağıntı** yapılandırmak için iletişim kutusu <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. [!INCLUDE[crabout](../includes/crabout-md.md)] kullanımı bu iletişim kutusunu görmek [türü koleksiyon Düzenleyicisi iletişim kutusu](../workflow-designer/type-collection-editor-dialog-box.md) konu.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [Alma](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Gönder](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)