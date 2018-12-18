---
title: İş Akışı Tasarımcısı - ReceiveAndSendReply şablon Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c6b5a12b37509e6e5113c704ef2c3ff931ea32e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886415"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply Şablon Tasarımcısı

**ReceiveAndSendReply** şablon çifti oluşturmak için kullanılan önceden yapılandırılmış <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler. Etkinlikleri parçası olan bir <xref:System.Activities.Statements.Sequence> çalıştırdığınız ve etkinlik bağıntılı istek/yanıt ileti değişim deseni sunucudaki bir parçası olarak.

## <a name="the-receiveandsendreply-template"></a>ReceiveAndSendReply şablon

Ekleme bir **ReceiveAndSendReply** şablon oluşturma yanı sıra üç şeyi yapar <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinliklerle bir <xref:System.Activities.Statements.Sequence> etkinlik:

- Yapılandırır <xref:System.ServiceModel.Activities.Receive.OperationName%2A> ve <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> özelliklerini <xref:System.ServiceModel.Activities.Receive> etkinlik.

- Bağlar <xref:System.ServiceModel.Activities.SendReply.Request%2A> özelliği <xref:System.ServiceModel.Activities.Receive> etkinliğini <xref:System.ServiceModel.Activities.Send> etkinlik.

- Oluşturur bir <xref:System.ServiceModel.Activities.CorrelationHandle> üst etkinliği bir değişken olarak.

### <a name="use-the-receiveandsendreply-template-designer"></a>Kullanma ReceiveAndSendReply şablon Tasarımcısı

Erişim **ReceiveAndSendReply** etkinlik Tasarımcısı'nda **Mesajlaşma** kategorisi **araç kutusu**. **ReceiveAndSendReply** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve etkinlikleri genellikle yerleştirilen her yerde iş akışı Tasarımcısı yüzeyine açın. Etkinlik Tasarımcısı bırakarak oluşturur bir <xref:System.ServiceModel.Activities.Receive> ile yapılandırılmış etkinlik **Gönder** etkinlik Tasarımcısı ve ilişkili bir <xref:System.ServiceModel.Activities.SendReply> SendReplyToReceive tasarımcı ile yapılandırılabilir.

Kullanma hakkında daha fazla bilgi için **alma** yapılandırmak için tasarımcı <xref:System.ServiceModel.Activities.Receive> etkinliğine bakın [alma etkinlik Tasarımcısı](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>SendReply özellikleri

Aşağıdaki tabloda <xref:System.ServiceModel.Activities.SendReply> özellikleri Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. Bu özellikleri Özellikler kılavuz düzenlenebilir ve bazı iş akışı Tasarımcısı yüzeyine düzenlenebilir.


| Özellik adı | Gerekli | Kullanım |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | İsteğe bağlı kolay adı <xref:System.ServiceModel.Activities.SendReply> etkinlik. SendReplyToReceive varsayılandır.<br /><br /> Ancak varsayılan olmayan bir değeri kullanımı kolay için <xref:System.Activities.Activity.DisplayName%2A> kesinlikle gerekli değildir, bu tür bir değer kullanmak en iyisidir. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | Doğru | Başvuru <xref:System.ServiceModel.Activities.Receive> etkinlik ile eşleştirilmiş <xref:System.ServiceModel.Activities.SendReply> etkinlik. Bu özellik olmamalıdır **null**. <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler birlikte sunucu üzerinde bir istek/yanıt Mesajlaşma modeli model için kullanılır. Bu özellik belirten <xref:System.ServiceModel.Activities.Send> etkinlik eşleştirilmiştir. Tasarımcıda için otomatik olarak bağlı olduğundan bu özellik düzenlenemiyor <xref:System.ServiceModel.Activities.Send> oluşturduğunuz etkinlik <xref:System.ServiceModel.Activities.SendReply> etkinlik. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | İleti veya parametre içeriği almak için belirtir. Ya da olabilir bir <xref:System.ServiceModel.Activities.ReceiveMessageContent> etkinlik veya <xref:System.ServiceModel.Activities.ReceiveParametersContent> etkinlik. Yanındaki üç nokta düğmesine tıklayarak bu özellik düzenleme **içerik** özellik kılavuzunda veya tıklayarak alan **tanımla** düğmesinin yanındaki **içerik** etiketi **Alma** etkinlik Tasarımcı yüzeyine bırakın. Her ikisini de görüntüle **içerik tanımı** iletişim. Bu kutuyu kullanma hakkında daha fazla bilgi için bkz. [içerik tanımı iletişim kutusunun](../workflow-designer/content-definition-dialog-box.md) konu. |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Koleksiyonunu belirtir <xref:System.ServiceModel.Activities.CorrelationInitializer> birden çok başlatmak nesneleri <xref:System.ServiceModel.Activities.CorrelationHandle> bu yapılandırma nesneleri <xref:System.ServiceModel.Activities.Receive> etkinlik iş akışı içinde. Yanındaki üç nokta düğmesini tıklayın <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> özelliği açmak için özellikler kılavuzundaki **bağıntı başlatıcılar Ekle** iletişim kutusu. Bu kutuyu kullanma hakkında daha fazla bilgi için bkz. [Correlationınitializer iletişim kutusunu](../workflow-designer/add-correlationinitializers-dialog-box.md) konu. |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | İletinin eylem üstbilgisini belirtir. Açıkça ayarlanmış ise, değeri varsayılan olarak:<br /><br /> <strong>https://tempuri.org/{service ad alanı sözleşme} / {hizmet sözleşmesi adı} / {işlem adı}</strong> |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Yanıt iletisi gönderilmeden önce iş akışı örneği kalıcı olup olmadığını belirtir. Varsayılan değer **false**. |

## <a name="see-also"></a>Ayrıca bkz.

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)