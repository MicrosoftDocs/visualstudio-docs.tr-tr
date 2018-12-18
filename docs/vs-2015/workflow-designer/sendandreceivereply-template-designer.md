---
title: SendAndReceiveReply şablon Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: e2b7ffb52979c0899949806ae97b562f76b0b3c9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884959"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply Şablon Tasarımcısı
**SendAndReceiveReply** şablon çifti oluşturmak için kullanılan önceden yapılandırılmış <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> içindeki etkinlikleri bir <xref:System.Activities.Statements.Sequence> istek/yanıt iletisi exchange bir parçası olarak bağıntılı olan etkinliği istemci üzerinde deseni.  

## <a name="the-sendandreceivereply-template"></a>SendAndReceiveReply şablon  
 Ekleme **SendAndReceiveReply** şablon oluşturma yanı sıra üç şeyi yapar <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> içindeki etkinlikleri bir <xref:System.Activities.Statements.Sequence> etkinlik:  

1.  Yapılandırır <xref:System.ServiceModel.Activities.Send.OperationName%2A>, <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> özelliklerini <xref:System.ServiceModel.Activities.Send> etkinlik.  

2.  Bağlar <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> özelliği <xref:System.ServiceModel.Activities.ReceiveReply> etkinliğini <xref:System.ServiceModel.Activities.Send> etkinlik.  

3.  Oluşturur bir <xref:System.ServiceModel.Activities.CorrelationHandle> üst etkinliği bir değişken olarak.  

### <a name="using-the-sendandreceivereply-template-designer"></a>SendAndReceiveReply şablon Tasarımcısı'nı kullanarak  
 **SendAndReceiveReply** etkinlik Tasarımcısı bulunabilir **Mesajlaşma** kategorisi **araç kutusu**, hangi erişilen tıklayarak **araç kutusu**  sekmesinde [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatif olarak, seçin **araç** gelen **görünümü** menüsünü veya CTRL + ALT + X.)  

 **SendAndReceiveReply** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve oturum bırakılan [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzey yerde etkinlikleri genellikle yerleştirilir. Bu, oluşturur bir <xref:System.ServiceModel.Activities.Send> ile yapılandırılmış etkinlik **Gönder** etkinlik Tasarımcısı ve ilişkili bir <xref:System.ServiceModel.Activities.ReceiveReply> ile yapılandırılabilir **ReceiveReplyForSend** Tasarımcısı.  

 [!INCLUDE[crabout](../includes/crabout-md.md)] kullanarak **Gönder** yapılandırmak için tasarımcı <xref:System.ServiceModel.Activities.Send> etkinliği bkz [Gönder](../workflow-designer/send-activity-designer.md) konu.  

 [!INCLUDE[crabout](../includes/crabout-md.md)] kullanarak **ReceiveReplyForSend** yapılandırmak için tasarımcı <xref:System.ServiceModel.Activities.ReceiveReply> etkinlik, aşağıdaki bölüme bakın.  

### <a name="properties-of-receivereply"></a>ReceiveReply özellikleri  
 Aşağıdaki tabloda <xref:System.ServiceModel.Activities.ReceiveReply> özellikleri Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. Bu özellikleri Özellikler Kılavuzu ' düzenlenebilir ve bazı şirket düzenlenebilir [!INCLUDE[wfd2](../includes/wfd2-md.md)]Tasarımcı yüzeyine bırakın.  


|                                 Özellik adı                                 | Gerekli |                                                                                                                                                                                                                                                                                                                                                        Kullanım                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            İsteğe bağlı kolay adı <xref:System.ServiceModel.Activities.ReceiveReply> etkinlik. ReceiveReplyForSend varsayılandır.<br /><br /> Ancak kolay için varsayılan olmayan bir değeri kullanımını <xref:System.Activities.Activity.DisplayName%2A> kati şekilde gerekli değil gibi bir değer kullanmak için en iyi bir uygulamadır.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   Doğru   | Başvuru <xref:System.ServiceModel.Activities.Send> etkinlik ile eşleştirilmiş <xref:System.ServiceModel.Activities.ReceiveReply> etkinlik. Bu özellik olmamalıdır **null**. <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikler birlikte istemcide bir istek/yanıt Mesajlaşma modeli model için kullanılır. Bu özellik belirten <xref:System.ServiceModel.Activities.Send> etkinlik eşleştirilmiştir. Tasarımcıda için otomatik olarak bağlı olduğundan bu özellik düzenlenemiyor <xref:System.ServiceModel.Activities.Send> oluşturduğunuz etkinlik <xref:System.ServiceModel.Activities.ReceiveReply> etkinlik. |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        İleti veya parametre içeriği almak için belirtir. Ya da olabilir bir <xref:System.ServiceModel.Activities.ReceiveMessageContent> etkinlik veya <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinlik. Yanındaki üç nokta düğmesine tıklayarak bu özellik düzenleme **içerik** özellik kılavuzu veya tıklayarak alanındaki **tanımla...** yanında düğmesini **içerik** üzerinde etiket **alma** etkinlik Tasarımcı yüzeyine bırakın. Her ikisini de görüntüle **içerik tanımı** iletişim. [!INCLUDE[crabout](../includes/crabout-md.md)] Bu kutuyu kullanmak üzere nasıl [içerik tanımı iletişim kutusunun](../workflow-designer/content-definition-dialog-box.md) konu.                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              Koleksiyonunu belirtir <xref:System.ServiceModel.Activities.CorrelationInitializer> birden çok başlatmak nesneleri <xref:System.ServiceModel.Activities.CorrelationHandle> bu yapılandırma nesneleri <xref:System.ServiceModel.Activities.Receive> etkinlik iş akışı içinde. Yanındaki üç nokta düğmesini tıklayın <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> özelliği açmak için özellikler kılavuzundaki **bağıntı başlatıcılar Ekle** iletişim kutusu. [!INCLUDE[crabout](../includes/crabout-md.md)] Bu kutuyu bkz [Correlationınitializer iletişim kutusunu](../workflow-designer/add-correlationinitializers-dialog-box.md) konu.               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               İletinin eylem üstbilgisini belirtir. Açıkça ayarlanmazsa, değeri varsayılan olarak:<br /><br /> <strong>https://tempuri.org/{service ad alanı sözleşme} / {hizmet sözleşmesi adı} / {işlem adı}.</strong>                                                                                                                                                                                                                                               |

## <a name="see-also"></a>Ayrıca Bkz.  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [Initializecorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Alma](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Gönder](../workflow-designer/send-activity-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)