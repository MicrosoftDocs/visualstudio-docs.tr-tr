---
title: İş Akışı Tasarımcısı - TransactedReceiveScope etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a42c1cc9dac8e71bfe71f684232fdbf67fadb710
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929549"
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope Etkinlik Tasarımcısı

**TransactedReceiveScope** Tasarımcısı oluşturmak ve yapılandırmak için kullanılan bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik.

## <a name="the-transactedreceivescope-activity"></a>TransactedReceiveScope etkinlik

<xref:System.ServiceModel.Activities.TransactedReceiveScope> Etkinliğini bir iş akışı veya dağıtıcı tarafından oluşturulan sunucu işlemleri harekete akış olanak sağlar.

### <a name="using-the-transactedreceivescope-activity-designer"></a>TransactedReceiveScope etkinlik Tasarımcısı kullanma

Erişim **TransactedReceiveScope** etkinlik Tasarımcısı'nda **Mesajlaşma** kategorisi **araç kutusu**. **TransactedReceiveScope** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve etkinlikleri genellikle yerleştirilen her yerde iş akışı Tasarımcısı yüzeyine açın. Bu, oluşturur bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinliği ile bir varsayılan **DisplayName** TransactedReceiveScope kullanımı. <xref:System.Activities.Activity.DisplayName%2A> Üst bilgisinde düzenlenebilir **TransactedReceiveScope** etkinlik Tasarımcısı veya **DisplayName** özellik kılavuzunda kutusu.

**TransactedReceiveScope** Tasarımcısı içerir **istek** ve **gövdesi** kutuları. Bu yapılandırma için kullanılan <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> belirten özellik bir <xref:System.ServiceModel.Activities.Receive> etkinlik ve <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> başka belirten özellik <xref:System.Activities.Activity>. <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> Bir işlem oluşturur. Daha sonra işlem kapsamı için ortam yapılan <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> böylece bu işlem içinde bu kapsam içinde herhangi bir etkinliği yürütür.

### <a name="the-transactedreceivescope-properties"></a>TransactedReceiveScope özellikleri

Aşağıdaki tabloda <xref:System.ServiceModel.Activities.TransactedReceiveScope> özellikleri Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. Bunlar <xref:System.Activities.Activity.DisplayName%2A> özelliği, özellik kılavuzu veya iş akışı Tasarımcısı yüzeyine düzenlenebilir, ancak diğerleri tasarım yüzeyinde düzenlenmesi gerekir.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|İsteğe bağlı kolay adı <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik. TransactedReceiveScope varsayılandır.<br /><br /> Ancak <xref:System.Activities.Activity.DisplayName%2A> adı kesinlikle gerekli değil, görünen adı kullanmak için en iyi bir uygulamadır.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|Doğru|Bırakılanlar bir <xref:System.ServiceModel.Activities.Receive> etkinliğini **istek** etkinlik tasarımcısının yüzeyine blok.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Bırakılanlar bir <xref:System.Activities.Activity> içine **gövdesi** etkinlik tasarımcısının yüzeyine blok.|

## <a name="see-also"></a>Ayrıca bkz.

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)