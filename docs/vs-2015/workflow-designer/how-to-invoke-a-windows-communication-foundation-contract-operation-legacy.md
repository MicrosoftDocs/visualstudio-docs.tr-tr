---
title: 'Nasıl yapılır: bir Windows Communication Foundation sözleşme işlemi (eski) çağırma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 5e59d5ed9617d4be71a0542e35dd509d9035ae33
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181850"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Nasıl yapılır: bir Windows Communication Foundation sözleşme işlemi (eski) Çağır
Bu konu nasıl çağrılacağını açıklar bir [!INCLUDE[indigo1](../includes/indigo1-md.md)] sözleşme işlemi kullanılarak [!INCLUDE[wfd1](../includes/wfd1-md.md)] hedefleyen [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Sürükleme sonra bir **SendActivity** etkinlik iş akışı tasarım yüzeyine araç kutusundan, var olan bir sözleşmeyi içeri aktarabilir ve hangi işlemi, çağrılacak belirlemek **SendActivity** Etkinlik. Sözleşmeniz ve aracılığıyla işlemlerini belirleyin [seçin işlemi iletişim kutusu (eski)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
 Ayrıca, hizmetiniz ile bir yapılandırma dosyası kullanıyorsanız, belirtmeniz gerekecektir bir <xref:System.Workflow.Activities.ChannelToken>. <xref:System.Workflow.Activities.ChannelToken> Gönderme etkinlik giderek iş akışı hizmetine bağlanmak için kullanılacak uç nokta yapılandırması tanımlar.  
  
### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Bir WCF sözleşmesi işlemini SendActivity etkinliğinden çağırmak için  
  
1.  Çift **SendActivity** etkinlik Tasarımcısı'nda veya yanındaki üç noktaya tıklayın **ServiceOperationInfo** özelliğinde **özellikleri** bölmesi.  
  
2.  Zaman **seçin işlemi** iletişim kutusu açılır, tıklayın **içeri aktarma** iletişim kutusunun sağ alt köşesindeki.  
  
     [Göz atın ve bir .NET türünü seç iletişim kutusu (eski)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) açılır.  
  
3.  Bir derleme veya istediğiniz sözleşme içeren proje arayın.  
  
4.  Sözleşme seçin ve tıklayın **Tamam**.  
  
5.  Altında **kullanılabilir işlemleri**,'a tıklayın ve çağırmak istediğiniz işlemi seçin **Tamam**.  
  
### <a name="to-specify-a-channel-token"></a>Bir kanal belirteci belirtmek için  
  
1.  Seçin <xref:System.Workflow.Activities.SendActivity> etkinlik Tasarımcısı'nda.  
  
2.  İçinde **özellikleri** bölmesi için bir ad belirtin <xref:System.Workflow.Activities.ChannelToken>. Bu ad, kanal belirteç benzersiz şekilde tanımlar.  
  
3.  Kanal belirteç düğümünü genişletin ve kullanmak için seçeceğiz istemci uç noktası için bir ad belirtin <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A> alan. Yapılandırma dosyası aynı adlı uç nokta yapılandırması kanalı yapılandırmak için kullanılır.  
  
4.  Zaten yoksa, yapılandırma dosyasında uç nokta yapılandırması oluşturun. İstemci yapılandırma hakkında daha fazla bilgi için bkz. [WCF istemcisi genel bakış](http://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşlem iletişim kutusu (eski) seçin](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Nasıl yapılır: bir WCF sözleşmesi işlemi (eski) uygulama](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Eski İş Akışı Etkinlikleri ](../workflow-designer/legacy-workflow-activities.md)