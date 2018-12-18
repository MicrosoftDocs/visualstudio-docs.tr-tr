---
title: İş Akışı Tasarımcısı - SendAndReceiveReply şablon Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22cdd114a11ff9d1b3b162009cc77d83aec1fd83
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858972"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply Şablon Tasarımcısı

**SendAndReceiveReply** şablon çifti oluşturmak için kullanılan önceden yapılandırılmış <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikler. Etkinlikleri parçası olan bir <xref:System.Activities.Statements.Sequence> çalıştırdığınız ve etkinlik bağıntılı istek/yanıt ileti değişim deseni istemcide bir parçası olarak.

## <a name="the-sendandreceivereply-template"></a>SendAndReceiveReply şablon

Ekleme **SendAndReceiveReply** şablon oluşturma yanı sıra üç şeyi yapar <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> içindeki etkinlikleri bir <xref:System.Activities.Statements.Sequence> etkinlik:

- Yapılandırır <xref:System.ServiceModel.Activities.Send.OperationName%2A> ve <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> özelliklerini <xref:System.ServiceModel.Activities.Send> etkinlik.

- Bağlar <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> özelliği <xref:System.ServiceModel.Activities.ReceiveReply> etkinliğini <xref:System.ServiceModel.Activities.Send> etkinlik.

- Oluşturur bir <xref:System.ServiceModel.Activities.CorrelationHandle> üst etkinliği bir değişken olarak.

### <a name="use-the-sendandreceivereply-template-designer"></a>SendAndReceiveReply şablon Tasarımcısı'nı kullanın

Erişim **SendAndReceiveReply** etkinlik Tasarımcısı'nda **Mesajlaşma** kategorisi **araç kutusu**. **SendAndReceiveReply** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve etkinlikleri genellikle yerleştirilen her yerde iş akışı Tasarımcısı yüzeyine açın. Etkinlik Tasarımcısı bırakarak oluşturur bir <xref:System.ServiceModel.Activities.Send> ile yapılandırılmış etkinlik **Gönder** etkinlik Tasarımcısı ve ilişkili bir <xref:System.ServiceModel.Activities.ReceiveReply> ile yapılandırılabilir **ReceiveReplyForSend** Tasarımcısı.

Kullanma hakkında daha fazla bilgi için **Gönder** yapılandırmak için tasarımcı <xref:System.ServiceModel.Activities.Send> etkinliği bkz [Gönder](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>ReceiveReply özellikleri

Aşağıdaki tabloda <xref:System.ServiceModel.Activities.ReceiveReply> özelliklerini ve bunların Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. Bu özellikleri Özellikler Kılavuzu ' düzenlenebilir ve bazı iş akışı Tasarımcısı yüzeyine düzenlenebilir.


| Özellik adı | Gerekli | Kullanım |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | İsteğe bağlı kolay adı <xref:System.ServiceModel.Activities.ReceiveReply> etkinlik. ReceiveReplyForSend varsayılandır.<br /><br /> Ancak varsayılan olmayan bir değeri kullanımı kolay için <xref:System.Activities.Activity.DisplayName%2A> kesinlikle gerekli değildir, bu tür bir değer kullanmak en iyisidir. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | Doğru | Başvuru <xref:System.ServiceModel.Activities.Send> etkinlik ile eşleştirilmiş <xref:System.ServiceModel.Activities.ReceiveReply> etkinlik. Bu özellik olmamalıdır **null**. <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikler birlikte istemcide bir istek/yanıt Mesajlaşma modeli model için kullanılır. Bu özellik belirten <xref:System.ServiceModel.Activities.Send> etkinlik eşleştirilmiştir. Tasarımcıda için otomatik olarak bağlı olduğundan bu özellik düzenlenemiyor <xref:System.ServiceModel.Activities.Send> oluşturduğunuz etkinlik <xref:System.ServiceModel.Activities.ReceiveReply> etkinlik. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | İleti veya parametre içeriği almak için belirtir. Ya da olabilir bir <xref:System.ServiceModel.Activities.ReceiveMessageContent> etkinlik veya <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinlik. Bu özelliğin yanındaki üç nokta düğmesine tıklayarak düzenleme **içerik** özellik kılavuzunda veya tıklayarak alan **tanımlayın** düğmesinin yanındaki **içerik** üzerindeki etiket **Alma** etkinlik Tasarımcı yüzeyine bırakın. Her ikisini de görüntüle **içerik tanımı** iletişim. Bu kutuyu kullanma hakkında daha fazla bilgi için bkz. [içerik tanımı iletişim kutusunun](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Koleksiyonunu belirtir <xref:System.ServiceModel.Activities.CorrelationInitializer> birden çok başlatmak nesneleri <xref:System.ServiceModel.Activities.CorrelationHandle> bu yapılandırma nesneleri <xref:System.ServiceModel.Activities.Receive> etkinlik iş akışı içinde. Yanındaki üç nokta düğmesini tıklayın <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> özelliği açmak için özellikler kılavuzundaki **bağıntı başlatıcılar Ekle** iletişim kutusu. Bu kutuyu kullanma hakkında daha fazla bilgi için bkz. [Correlationınitializer iletişim kutusunu](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | İletinin eylem üstbilgisini belirtir. Açıkça ayarlanmış ise, değeri varsayılan olarak:<br /><br /> <strong>https://tempuri.org/{service ad alanı sözleşme} / {hizmet sözleşmesi adı} / {işlem adı}.</strong> |

## <a name="see-also"></a>Ayrıca bkz.

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)