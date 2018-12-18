---
title: FlowDecision etkinlik Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 7109b779cf33d226f44853e3f67c8609bd42fc1b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49212894"
---
# <a name="flowdecision-activity-designer"></a>FlowDecision Etkinlik Tasarımcısı
<xref:System.Activities.Statements.FlowDecision> Sağlayan bir dal denetim akışı için belirtilen bir koşulu gerçekleşmiş demektir göre iki alternatifleri birine koşullu bir düğümü düğümüdür. Akış ikiden fazla dalları gerektiriyorsa, kullanın <xref:System.Activities.Statements.FlowSwitch%601> yerine.  
  
## <a name="the-flowdecision-node"></a>FlowDecision düğümü  
 Kullanım <xref:System.Activities.Statements.FlowDecision> zaman akışı dallandırılmış iki yola. A <xref:System.Activities.Statements.FlowDecision> düğüme sahip bir <xref:System.Activities.Statements.FlowDecision.Condition%2A> ve <xref:System.Activities.Statements.FlowNode> her iki sonuçtan ile ilişkilendirilmiş: <xref:System.Activities.Statements.FlowDecision.True%2A> veya <xref:System.Activities.Statements.FlowDecision.False%2A>. <xref:System.Activities.Statements.FlowDecision.Condition%2A> Değerlendirilir ve sonraki Bu değerlendirme değeri belirler <xref:System.Activities.Statements.FlowNode> içinde işlenecek <xref:System.Activities.Statements.Flowchart>.  
  
### <a name="using-the-flowdecision-designer"></a>FlowDecision Tasarımcısı'nı kullanarak  
 **FlowDecision** Tasarımcısı bulunabilir **akış** kategorisi **araç kutusu**, hangi erişilen tıklayarak **araç kutusu** sekmesindeki [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatif olarak, seçin **araç** gelen **görünümü** menüsünü veya CTRL + ALT + X.)  
  
 **FlowDecision** Tasarımcısı'ndan sürüklenebilir **araç kutusu** ve oturum bırakılan [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzey içinde bir **akış** etkinlik Tasarımcısı. Bu, oluşturur bir <xref:System.Activities.Statements.FlowDecision> etiketli **karar** içinde <xref:System.Activities.Statements.Flowchart> etkinlik. Tasarımcı üzerinde fare ve **True** ve **False** kare tanıtıcıları için iki dal görüntülenir.  
  
 Sürükleme sonra **FlowDecision** Tasarımcısı ve diğer tasarımcılar üzerine **akış**, düğümleri bağlı birlikte yürütme sırası belirtmek için. Kaynak düğüm arasında bir bağlantı oluşturmak için (dahil olmak üzere **True** ve **False** , dallar **FlowDecision**) ve bir hedef düğümü kaynak düğüm tasarımcının üzerine fare ve bunu her bir tarafta kare tutamaçları görünür. Kare tutamaçlarından birinin tıklayıp üzerine fare yükleyen hedef düğüme etrafında benzer şekilde görünür tutamaçlarından birinin için fare düğmesini basılı tutarak sürükleyin. Fare düğmesini bırakın ve bağlantı hedef tasarımcıya kaynağı Tasarımcısı'ndan bir ok olarak temsil edilen bu iki düğüm arasında oluşturulur.  
  
 Durumları ifade <xref:System.Activities.Statements.FlowDecision.Condition%2A> yazılabilir **koşul** kutusunun **özellikleri** tıklayarak penceresi ipucu metnini burada Yazan "VB ifadesi girin".  
  
### <a name="the-flowdecision-properties"></a>FlowDecision özellikleri  
 Aşağıdaki tabloda <xref:System.Activities.Statements.FlowDecision> özellikleri Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.  
  
|Özellik adı|Gerekli|Kullanım|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|Doğru|Hangi yolu belirleyen koşul akış denetimi gerçekleştirir.|  
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|Yolun, akış denetimi tarafından gerçekleştirilen <xref:System.Activities.Statements.FlowDecision.Condition%2A> karşılanmadı.|  
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|Yolun, akış denetimi tarafından gerçekleştirilen <xref:System.Activities.Statements.FlowDecision.Condition%2A> karşılanmadı.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Akış Çizelgesi](../workflow-designer/flowchart-activity-designers.md)   
 [Akış Çizelgesi](../workflow-designer/flowchart-activity-designer.md)   
 [FlowSwitch\<T >](../workflow-designer/flowswitch-t-activity-designer.md)