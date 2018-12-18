---
title: İş Akışı Tasarımcısı - Initializecorrelation etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7f72cb538018588ab11335be5a99fe86b5c474c3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879889"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation Etkinlik Tasarımcısı

**Initializecorrelation** etkinlik Tasarımcısı oluşturmak ve yapılandırmak için kullanılan bir <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinlik. <xref:System.ServiceModel.Activities.InitializeCorrelation> Etkinlik gönderme veya alma bunları önce iletileri arasında bir ilişki kurar.

## <a name="the-initializecorrelation-activity"></a>Initializecorrelation etkinlik

Bir <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinliği gönderme veya bir mesaj bağıntılar başlatmak için kullanılır. Genellikle bağıntı veya bir mesaj gönderirken başlatılır. Bir ileti gönderildiğinde veya alındığında önce bağıntı oluşturulmalıdır kullanırsanız <xref:System.ServiceModel.Activities.InitializeCorrelation> bağıntı başlatılamadı.

### <a name="using-the-initializecorrelation-activity-designer"></a>Initializecorrelation etkinlik Tasarımcısı kullanma

Erişim **Initializecorrelation** etkinlik Tasarımcısı'nda **Mesajlaşma** kategorisi **araç kutusu**.

**Initializecorrelation** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve iş akışı Tasarımcısı yüzeyine açın. Etkinlik Tasarımcısı bırakarak oluşturur bir <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinliği ile bir varsayılan <xref:System.Activities.Activity.DisplayName%2A> Initializecorrelation biri. <xref:System.Activities.Activity.DisplayName%2A> Üst bilgisinde düzenlenebilir **Initializecorrelation** etkinlik Tasarımcısı veya **DisplayName** kutusunun **özellikleri** penceresi.

<xref:System.ServiceModel.Activities.CorrelationHandle> Olabilir belirtir **bağıntı** alanındaki **özellikleri** penceresinde **Initializecorrelation** etkinlik Tasarımcı yüzeyine bırakın.

Görüntülenecek **başlatmak bağıntı** bağıntı tanıtıcı, başlatmak için kullanılan anahtar-değer çiftlerini seçin ve üç nokta düğmesini yanındaki belirleyebileceğiniz iletişim kutusu **CorrelationData** alanındaki **özellikleri** penceresi. Veya "Görünüm..." İpucu metnini seçin **Initializecorrelation** etkinlik Tasarımcı yüzeyine bırakın. Bu iletişim kutusunu kullanma hakkında daha fazla bilgi için bkz. [türü koleksiyon Düzenleyicisi iletişim kutusu](../workflow-designer/type-collection-editor-dialog-box.md) makalesi.

### <a name="the-initializecorrelation-properties"></a>Initializecorrelation özellikleri

Aşağıdaki tabloda <xref:System.ServiceModel.Activities.InitializeCorrelation> özelliklerini ve bunların Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. Bu özellikleri de düzenlenebilen **özellikleri** penceresi veya iş akışı Tasarımcısı yüzeyine.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Kolay adı <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinlik. Initializecorrelation varsayılan değerdir.<br /><br /> Ancak kolay için varsayılan olmayan bir değeri kullanımını <xref:System.Activities.Activity.DisplayName%2A> kesinlikle gerekli değildir, önerilir.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> İş akışı etkinliklerinde bağıntı ilişkilendirmek için kullanılır.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|İş akışı örneği için iletileri ilişkili bağıntı veri sözlüğü.<br /><br /> Kullanım **başlatmak bağıntı** yapılandırmak için iletişim kutusu <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Kullanımı hakkında daha fazla bilgi için bu iletişim kutusunu görmek [türü koleksiyon Düzenleyicisi iletişim kutusu](../workflow-designer/type-collection-editor-dialog-box.md) makalesi.|

## <a name="see-also"></a>Ayrıca bkz.

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)