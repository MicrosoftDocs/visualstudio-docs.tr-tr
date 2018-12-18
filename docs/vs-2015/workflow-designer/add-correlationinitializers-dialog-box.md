---
title: Correlationınitializer Ekle iletişim kutusu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 4d4d69185bef36ab514c984716cc6606f6068fb4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49275697"
---
# <a name="add-correlationinitializers-dialog-box"></a>CorrelationInitializer Ekle İletişim Kutusu
**Bağıntı başlatıcılar Ekle** iletişim kutusu kullanılan [!INCLUDE[wfd1](../includes/wfd1-md.md)] yapılandırmak için **Correlationınitializer** özelliklerini <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikler. [!INCLUDE[crabout](../includes/crabout-md.md)] Bu kutuyu kullanan etkinlik tasarımcıları bkz [Gönder](../workflow-designer/send-activity-designer.md), [alma](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), ve [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) konuları.  
  
 Bu iletişim kutusu ile belirtilen koleksiyondaki bağıntı başlatıcılar, sorgu tabanlı başlatabilirsiniz bağlam, içerik geri çağırma ve istek-yanıt bağıntılar Mesajlaşma etkinlikler arasında.  
  
 Aşağıdaki tabloda kullanıcı arabirimi (UI) öğelerini açıklar **bağıntı başlatıcılar Ekle** iletişim kutusu.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Başlatıcı Ekle**|Tıklayın **Ekle başlatma** kutusunu ek bir başlatıcı koleksiyona ekleyin.|  
|**Typ korelace**|Bağıntı başlatıcı türünü belirtir. Aralarından seçim yapabileceğiniz dört tür vardır:<br /><br /> 1.  Belirtmek için bir geri çağırma bağıntı başlatıcı bir <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2.  Belirtmek için bir bağlam bağıntı başlatıcı bir <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3.  Belirtmek için bir istek-yanıt bağıntısı Başlatıcı bir <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4.  Belirtmek için bir sorgu bağıntı başlatıcı bir <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Düzenlenecek **CorrelationType**<br /><br /> 1.  Belirli bir satırda için sekmesinde **ekleme Başlatıcı** DataGrid.<br />2.  Odağı ayarlamak için CTRL + Tab tuşuna basın **CorrelationTypeComboBox**<br />3.  Açılır kutu için alt + aşağı ok tuşlarına basın **ComboBox** ve düzenleyin.|  
|**XPath sorguları**|Gelen ve giden iletilerden bağıntı verileri ayıklamak için kullanılan sorguları içeren bir anahtar/değer çifti. Bu liste yalnızca geçerli kullanıldığında <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> türleri.|  
  
## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Bağıntı başlatıcılar Ekle iletişim kutusunu başlatmak için  
 **Bağıntı başlatıcılar Ekle** iletişim kutusu tarafından kullanılan **Gönder**, **alma**, **ReceiveAndSendReply**, ve  **SendAndReceiveReply** tasarımcıları. Bunlara erişmek her durumda ve içerir durumda benzer **alma** Tasarımcısı kullanıldığı burada yordamı göstermek için.  
  
 **Alma** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve oturum bırakılan [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzey yerde etkinlikleri genellikle yerleştirilir. Bu, oluşturur bir <xref:System.ServiceModel.Activities.Receive> etkinliği ile bir varsayılan <xref:System.Activities.Activity.DisplayName%2A> alma. Seçin **alma** etkinlik Tasarımcısı ve üç nokta düğmesini (koleksiyon) metnin yanında tıklatın **Correlationınitializer** özelliği için özellik kılavuzunda **Ekle Bağıntı başlatıcılar** iletişim kutusu görünür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağıntı iletişim kutusu Ekle](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [Bağıntıyı Başlat İletişim Kutusu](../workflow-designer/initialize-correlation-dialog-box.md)