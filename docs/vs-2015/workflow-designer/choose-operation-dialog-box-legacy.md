---
title: İşlem iletişim kutusu (eski) seçin. | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 75b553bd79936db7b6d8aa2f8fe361650d4ef03e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189638"
---
# <a name="choose-operation-dialog-box-legacy"></a>İşlem Seç İletişim Kutusu (Eski)
Bu konu açıklar nasıl **işlemi seçin** eski iletişim kutusunda [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Eski kullanın [!INCLUDE[wfd2](../includes/wfd2-md.md)] hedeflemek gerektiğinde [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 **Seçin işlemi** iletişim kutusu ile ilişkilendirmek için bir işlem seçmek amacıyla kullanılan bir <xref:System.Workflow.Activities.ReceiveActivity> etkinlik veya <xref:System.Workflow.Activities.SendActivity> etkinlik. Bu iletişim kutusunda, bu etkinlikler ile kullanma hakkında daha fazla bilgi için bkz [nasıl yapılır: bir WCF sözleşmesi işlemi (eski) uygulama](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) ve [nasıl yapılır: bir WCF sözleşmesi işlemini (eski) çağırmak](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).  
  
 Aşağıdaki tabloda kullanıcı arabirimi (UI) öğelerini açıklar **seçin işlemi** iletişim kutusu.  
  
|Arabirim Öğesi|Açıklama|  
|----------------|-----------------|  
|**Anlaşma Ekle**|Yeni bir sözleşme sizin için oluşturur. Bu sözleşmede yeni işlemleri tanımlayabilirsiniz. (Bu ile kullanılan <xref:System.Workflow.Activities.ReceiveActivity> yalnızca.)|  
|**İşlem ekleme**|Oluşturduğunuz yeni bir sözleşme için yeni işlemleri ekler **seçin işlemi** iletişim kutusu. **Not:** yeni işlemleri aracılığıyla oluşturduğunuz sözleşmeleri ekleyebileceğiniz **seçin işlemi** iletişim kutusu. <br /><br /> (Bu ile kullanılan <xref:System.Workflow.Activities.ReceiveActivity> yalnızca.)|  
|**İçeri Aktar...**|Önceden tanımlanmış bir sözleşme alır ve bir işlem bu sözleşme seçmenizi sağlar.|  
|**İşlem adı**|Şu anda seçili olan işlemin adı. Bu metin kutusunda, yalnızca bir işlem aracılığıyla oluşturduysanız düzenlemek için kullanılabilir **seçin işlemi** iletişim kutusu.|  
|**Parametreler**|Şu anda seçili işlem parametresi tanımlarını içeren sekmesi. **Not:** parametre tanımlarıyla değiştirilebilir, yalnızca bir işlem aracılığıyla oluşturduysanız **seçin işlemi** iletişim kutusu.|  
|**Özellikler**|Sekmesini içeren <xref:System.Net.Security.ProtectionLevel> hizmet ve istemci arasında gönderilen iletiler için ayarlar. **Not:** yalnızca bir işlem aracılığıyla oluşturduysanız Bu sekme etkin **seçin işlemi** iletişim kutusu.|  
|**İzinler**|Sekmesini içeren <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> ve <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> bu işlemi çağırmak için izin verilen kullanıcıların özellikleri. Yalnızca Yöneticiler grubundaki kullanıcılar bu işlemi çağırmak için izni olan, örneğin, daha sonra "Yöneticiler" yazmalısınız **rol** metin kutusu.<br /><br /> Bu sekme aracılığıyla oluşturulan iki işlem için etkin **ChooseOperation** iletişim kutusu ve aracılığıyla alınan işlemler **alma** düğmesi.|  
  
> [!NOTE]
>  **Seçin işlemi** iletişim kutusu, yalnızca sözleşmeleri veya diğer tarafından kullanılan işlemleri gösterir <xref:System.Workflow.Activities.SendActivity> iş akışındaki etkinlikler. Benzer şekilde, **seçin işlemi** iletişim kutusu için <xref:System.Workflow.Activities.ReceiveActivity> etkinlikleri yalnızca sözleşmeleri veya diğer tarafından kullanılan işlemleri gösterir **ReceiveActivity** iş akışındaki etkinlikler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: bir WCF sözleşmesi işlemi (eski) uygulama](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Nasıl yapılır: bir WCF sözleşmesi işlemi (eski) Çağır](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Windows Workflow Foundation Kullanıcı Arabirimi Yardımı için Eski Tasarımcı](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)