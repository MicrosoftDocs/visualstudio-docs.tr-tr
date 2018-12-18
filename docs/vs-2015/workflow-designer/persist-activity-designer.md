---
title: Persist etkinlik Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 628082fc5130a17a14b273b4d1e35e962cc5e394
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209306"
---
# <a name="persist-activity-designer"></a>Persist Etkinlik Tasarımcısı
**Kalan** etkinlik Tasarımcısı oluşturmak ve yapılandırmak için kullanılan bir <xref:System.Activities.Statements.Persist> etkinlik.  
  
## <a name="the-persist-activity"></a>Persist etkinlik  
 <xref:System.Activities.Statements.Persist> Etkinliğini bir iş akışı mümkünse diske kaydeder. <xref:System.Activities.Statements.Persist> Etkinlik yürütülemiyor alanında bir Kalıcılık olmayan, örneğin, içinde bir <xref:System.Activities.Statements.TransactionScope> etkinlik. Kullanıyorsanız bir <xref:System.Activities.Statements.Persist> etkinlik kalıcı olmayan bir kapsam içinde bir özel durumu çalışma zamanında oluşturulur.  
  
### <a name="using-the-persist-activity-designer"></a>Kullanarak Persist etkinlik Tasarımcısı  
 **Kalan** etkinlik Tasarımcısı bulunabilir **çalışma zamanı** kategorisi **araç kutusu**, hangi erişilen tıklayarak **araç kutusu** sekme (Alternatif olarak, seçin **araç kutusu** gelen **görünümü** menüsünden veya CTRL + ALT + X.)  
  
 **Kalan** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve oturum bırakılan [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzey yerde etkinlikleri genellikle yerleştirilir, örneğin olarak içinde bir <xref:System.Activities.Statements.Sequence>. Bu, oluşturur bir <xref:System.Activities.Statements.Persist> etkinliği ile bir varsayılan **DisplayName** kalan. <xref:System.Activities.Activity.DisplayName%2A> Üst bilgisinde düzenlenebilir **kalan** etkinlik Tasarımcısı veya **DisplayName** özellik kılavuzunda kutusu.  
  
### <a name="the-persist-properties"></a>Kalıcı özellikleri  
 Aşağıdaki tabloda <xref:System.Activities.Statements.Persist> özellikleri Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda düzenlenebilir ve bunlardan bazıları üzerinde düzenlenebilir [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyi.  
  
|Özellik adı|Gerekli|Kullanım|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Kolay adı <xref:System.Activities.Statements.Persist> etkinlik. Kalan varsayılandır. Görünen ad kesinlikle gerekli olmamakla birlikte, bir görünen ad kullanmak için en iyi bir uygulamadır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma zamanı](../workflow-designer/runtime-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)