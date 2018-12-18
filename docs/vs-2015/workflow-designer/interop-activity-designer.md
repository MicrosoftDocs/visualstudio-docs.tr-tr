---
title: Interop etkinlik Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 587f9017e7f2c76018fbb5eb98645f5e4c19216c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49283041"
---
# <a name="interop-activity-designer"></a>Interop Etkinlik Tasarımcısı
**Interop** etkinlik Tasarımcısı oluşturmak ve yapılandırmak için kullanılan bir <xref:System.Activities.Statements.Interop> etkinlik.  
  
## <a name="the-interop-activity"></a>Birlikte çalışma etkinliği  
 <xref:System.Activities.Statements.Interop> Etkinlik öğesinden türetilen türler yürütülmesini yönetir <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> bir iş akışındaki.  
  
### <a name="using-the-interop-activity-designer"></a>Interop etkinlik Tasarımcısı kullanma  
 **Interop** etkinlik Tasarımcısı bulunabilir **geçiş** kategorisi **araç kutusu**, hangi erişilen tıklayarak **araç kutusu**sekme (Alternatif olarak, seçin **araç kutusu** gelen **görünümü** menüsünden veya CTRL + ALT + X.)  
  
 [Geçiş](../workflow-designer/migration-activity-designers.md) içeren kategori <xref:System.Activities.Statements.Interop> etkinliği yalnızca gösterilir **araç kutusu** tam projenizin hedeflediği varsa [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)].  
  
 C# projeleri için projeyi tam kullanacak şekilde yeniden hedefleyebilirsiniz [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] projeye sağ tıklayarak **Çözüm Gezgini** seçerek **özellikleri**. Üzerinde **uygulama** sekmesinde **NET Framework 4** seçeneğini **hedef Framework'ü**. Seçin **Evet** düğmesine **hedef Framework'ü değiştirmek** görüntüler bu değişikliği onaylamanızı isteyen bir iletişim kutusu.  
  
 VB projeleri için projeyi tam kullanacak şekilde yeniden hedefleyebilirsiniz [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] bölümünde projeye sağ tıklayarak **Çözüm Gezgini** seçerek **özellikleri**. Üzerinde **derleme** sekmesinde **Gelişmiş derleme seçenekleri** düğmesi. Seçin **.Net Framework 4** gelen **hedef çerçeve listesi** ve ardından **Tamam**. Tıklayın **Evet** düğmesine **hedef Framework'ü değiştirmek** görüntüler bu değişikliği onaylamanızı isteyen bir iletişim kutusu.  
  
 **Interop** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve oturum bırakılan [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzey yerde etkinlikleri genellikle yerleştirilir, örneğin olarak içinde bir <xref:System.Activities.Statements.Sequence>. Bu, oluşturur bir <xref:System.Activities.Statements.Interop> etkinliği ile bir varsayılan **DisplayName** , birlikte çalışabilirlik. <xref:System.Activities.Activity.DisplayName%2A> Üst bilgisinde düzenlenebilir **Interop** etkinlik Tasarımcısı veya **DisplayName** özellik kılavuzunda kutusu.  
  
 Tıklayın **göz atmak için tıklatın...** metinde **ActivityType** üzerinde kutusu **birlikte çalışabilirliği** etkinlik Tasarımcısı veya ortaya çıkarmak için özellik kılavuzunda **Gözat ve Seç bir .net türü** iletişim kutusu. İş akışı 3.0 veya 3.5 iş akışı etkinlikleri için türleri yalnızca gösterilir (diğer bir deyişle, yalnızca öğesinden türetilmiş <xref:System.Workflow.ComponentModel.Activity>). [!INCLUDE[crabout](../includes/crabout-md.md)] bir tür belirtmek için bu kutuyu kullanma [göz atın ve bir .NET türünü seç iletişim kutusu](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) konu.  
  
### <a name="the-interop-properties"></a>Birlikte çalışma özellikleri  
 Aşağıdaki tabloda <xref:System.Activities.Statements.Interop> özellikleri Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. Bu özellikler düzenlenebilir, özellik kılavuzu veya Cihazınızda [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyi.  
  
|Özellik adı|Gerekli|Kullanım|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Kolay adı <xref:System.Activities.Statements.Interop> etkinlik. Birlikte çalışma varsayılandır. Görünen ad kesinlikle gerekli olmamakla birlikte, bir görünen ad kullanmak için en iyi bir uygulamadır.|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Doğru|Tarafından bulunan bir etkinlik türünü belirten <xref:System.Activities.Statements.Interop> etkinlik. Bu tür belirtilen öğesinden türetilmelidir <xref:System.Workflow.ComponentModel.Activity>.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Geçiş](../workflow-designer/migration-activity-designers.md)