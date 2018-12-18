---
title: İş Akışı Tasarımcısı - CorrelationScope etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d1da881dfb7f7a8c063b94e49198d1b299b2e47b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942055"
---
# <a name="correlationscope-activity-designer"></a>CorrelationScope Etkinlik Tasarımcısı

**CorrelationScope** etkinlik Tasarımcısı oluşturmak ve yapılandırmak için kullanılan bir <xref:System.ServiceModel.Activities.CorrelationScope> alt Mesajlaşma etkinlikleri kullanarak örtük yönetimini sağlayan etkinlik bir <xref:System.ServiceModel.Activities.CorrelationHandle> nesne.

## <a name="the-correlationscope-activity"></a>CorrelationScope etkinlik

<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> Özellik belirtir <xref:System.ServiceModel.Activities.CorrelationHandle> alt Mesajlaşma etkinlikleri yönetmek için kullanılır. <xref:System.ServiceModel.Activities.Send> Ve <xref:System.ServiceModel.Activities.Receive> yer alan etkinlikleri <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> kullanmak üzere yapılandırılmış <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> içeren özellik <xref:System.ServiceModel.Activities.CorrelationScope> bağıntısı yapmak için etkinlik.

### <a name="use-the-correlationscope-activity-designer"></a>CorrelationScope etkinlik Tasarımcısı kullanma

**CorrelationScope** etkinlik Tasarımcısı bulunabilir **Mesajlaşma** kategorisi **araç kutusu**, hangi erişilen tıklayarak **araçkutusu** iş akışı Tasarımcısı'nın sol tarafındaki sekmesi. Alternatif olarak, seçin **araç kutusu** gelen **görünümü** tuşuna basın veya menü **Ctrl**+**Alt** + **X**.

**CorrelationScope** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve iş akışı Tasarımcısı yüzeyine açın. Bu, oluşturur bir <xref:System.ServiceModel.Activities.CorrelationScope> etkinliği ile bir varsayılan **DisplayName** CorrelationScope biri. <xref:System.Activities.Activity.DisplayName%2A> Üst bilgisinde düzenlenebilir **CorrelationScope** etkinlik Tasarımcısı veya **DisplayName** kutusunun **özellikleri** penceresi.

Belirtmek için <xref:System.ServiceModel.Activities.CorrelationHandle> Mesajlaşma etkinlikleriyle alt tarafından kullanılan, yanındaki üç nokta düğmesini seçin **CorrelatesWith** alanındaki **özellikleri** penceresini görüntülemek için **ifadesi Düzenleyici** iletişim kutusu. Bu özellik, etkinlik Tasarımcı yüzeyinde de ayarlanabilir.

İçinde tasarımcılar bırakarak içinde bağıntı kapsamlı etkinlikleri belirtilen **gövdesi** içinde kutusunda **CorrelationScope** Tasarımcısı.

### <a name="the-correlationscope-properties"></a>CorrelationScope özellikleri

Aşağıdaki tabloda <xref:System.ServiceModel.Activities.CorrelationScope> özellikleri Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. Bu özellikler olabilir ya da düzenlenebilir **özellikleri** penceresi veya iş akışı Tasarımcısı yüzeyine ve genellikle hem de.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|İsteğe bağlı kolay adı <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinlik.|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Belirtir <xref:System.ServiceModel.Activities.CorrelationHandle> alt Mesajlaşma etkinlikleri yönetmek için kullanılır. Bu özelliği ayarlamazsanız <xref:System.ServiceModel.Activities.CorrelationScope> örtük oluşturur <xref:System.ServiceModel.Activities.CorrelationHandle> otomatik olarak.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Bağıntı kapsamı içindeki belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)