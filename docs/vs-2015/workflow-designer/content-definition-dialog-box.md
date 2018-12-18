---
title: İçerik tanımı iletişim kutusu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 0c0fffed6bbb8d9690f96679d910d5ac4a3b631e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176130"
---
# <a name="content-definition-dialog-box"></a>İçerik Tanımı İletişim Kutusu
**İçerik tanımı** iletişim kutusu kullanılan [!INCLUDE[wfd1](../includes/wfd1-md.md)] yapılandırmak için **içerik** özelliklerini <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikler. [!INCLUDE[crabout](../includes/crabout-md.md)] Bu kutuyu kullanan etkinlik tasarımcıları bkz [Gönder](../workflow-designer/send-activity-designer.md), [alma](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), ve [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) konuları.  
  
 Aşağıdaki tabloda kullanıcı arabirimi (UI) öğelerini açıklar **başlatmak bağıntı** iletişim kutusu.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**İleti**|İleti içeriği belirtir **ileti veri** ifade metin kutusu ve türünü kullanarak **ileti türü** aşağı açılan liste kutusu. Varsayılan olarak, **içerik tanımı** kullanan <xref:System.ServiceModel.Activities.ReceiveMessageContent>, hangi bekliyor bir <xref:System.ServiceModel.Channels.Message> veya sözleşme türü iş akışı hizmet tanımı içinde bir ileti.|  
|**Parametreler**|Tıklayın **parametreleri** kullanmak için bir radyo düğmesi <xref:System.ServiceModel.Activities.ReceiveParametersContent>, bir veri anlaşması bekliyor. Veri Kılavuzu Genel koleksiyonu ayarlamak için kullanın <xref:System.Activities.OutArgument> anahtar/değer çiftleri değerleri geçerli iş akışında değişken parametreleri atanır.|  
  
 **İçerik tanımı** iletişim kutusu tarafından kullanılan **Gönder**, **alma**, **ReceiveAndSendReply**, ve  **SendAndReceiveReply** tasarımcıları. Her durumda bunları erişme benzer ve alma durum burada yordamı göstermek için kullanılır.  
  
 **Alma** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve oturum bırakılan [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzey yerde etkinlikleri genellikle yerleştirilir. Bu, oluşturur bir <xref:System.ServiceModel.Activities.Receive> etkinliği ile bir varsayılan <xref:System.Activities.Activity.DisplayName%2A> alma. Seçin **alma** etkinlik Tasarımcısı ve üç nokta düğmesini (içerik) metnin yanında tıklatın **içerik** özelliği için özellik kılavuzunda **içerik tanımı**iletişim kutusu görünür.  
  
 İçerik içinde belirtilen **ileti** bölümü bir <xref:System.ServiceModel.Activities.ReceiveMessageContent> etkinlik veya içinde **parametre** bölümü bir <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinlik.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı Tasarımcısı Kullanıcı Arabirimi Yardımı](../workflow-designer/workflow-designer-ui-help.md)