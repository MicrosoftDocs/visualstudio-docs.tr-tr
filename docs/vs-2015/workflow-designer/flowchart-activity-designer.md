---
title: Flowchart etkinlik Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 67bebeec9c2d88ba1912bc50b27e38f8278e7e3f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49226245"
---
# <a name="flowchart-activity-designer"></a>Flowchart Etkinlik Tasarımcısı
<xref:System.Activities.Statements.Flowchart> Etkinliği iş akışlarını tanımlamak ve yönetmek karmaşık akış denetimleri oluşturmak için kullanılır. A <xref:System.Activities.Statements.Flowchart> veya kod kullanarak yazılabilir [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Bu konu belgeleri [!INCLUDE[wfd2](../includes/wfd2-md.md)] karşılaşırsınız. [!INCLUDE[wfd1](../includes/wfd1-md.md)] İş akışı etkinlik Tasarımcısı, doğal bir şekilde iş akışları yazabilirsiniz geliştiricilerin sağlar.  
  
## <a name="the-flowchart-activity"></a>Akış etkinliği  
 <xref:System.Activities.Statements.Flowchart> Benzersiz bir belirtir <xref:System.Activities.Statements.Flowchart.StartNode%2A> kullanır ve iş akışı başlatır, ağ bağlantılı yürütülen <xref:System.Activities.Statements.Flowchart.Nodes%2A> rastgele döngüler oluşturmak için veya belirli herhangi bir zamanda iş akışı içinde başka bir yerde yürütmeyi akışını yöneltmektir.  
  
### <a name="using-the-flowchart-activity-designer"></a>Flowchart etkinlik Tasarımcısı kullanma  
 **Akış** etkinlik Tasarımcısı bulunabilir **akış** kategorisi **araç kutusu**, hangi erişilen tıklayarak **araç kutusu**sekmesinde [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatif olarak, seçin **araç** gelen **görünümü** menüsünden veya CTRL + ALT + X.)  
  
 **Akış** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve oturum bırakılan [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzey yerde etkinlik tasarımcıları normalde yerleştirilir, kök etkinlik veya alt olarak başka bir denetim akışı etkinliği. Varsa **akış** etkinlik Tasarımcısı boş bırakılan [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzey, oluşturur bir <xref:System.Activities.Statements.Flowchart> kendisini yürütme başlatan başlangıç düğümü olduğu bir Genişletilmiş görünümde sunar, varsayılan olarak, etkinlik Yeşil bir TOP temsil edilir. Varsa **akış** tıklanarak genişletilebilir bir simge durumuna küçültülmüş görünümünde kendisi sunar, etkinlik Tasarımcısı içinde başka bir denetim akışı etkinliği bırakılan **akış** etkinlik Tasarımcısı. Herhangi bir etkinliği **araç kutusu** doğrudan üzerine sürüklenebilen **akış** diğer denetim akışı etkinlikleri de dahil olmak üzere, etkinlik Tasarımcısı.  
  
 Çeşitli etkinlik tasarımcıları üzerine sürükleyerek sonra [!INCLUDE[wfd2](../includes/wfd2-md.md)] tuval, <xref:System.Activities.Activity> nesneleri temsil ettikleri bağlanabileceği birlikte yürütme sırası belirtmek için. Fareyle üzerine kare tanıtıcıları ve kaynak etkinlik Tasarımcısı kaynak etkinliği ve bir hedef etkinliği arasında bir bağlantı oluşturmak için bunu her bir tarafta görünür. Kare tutamaçları birine tıklayın ve fare ile üzerine geldiğinizde, hedef etkinlik etrafında benzer şekilde görünen tutamaçlarından birinin için fare düğmesini basılı tutarak sürükleyin. Fare düğmesini bırakın ve hedef tasarımcıya kaynağı Tasarımcısı'ndan bir ok olarak temsil edilen bu iki etkinliği arasında bir bağlantı oluşturulur.  
  
### <a name="flowchart-activity-properties"></a>Akış Çizelgesi etkinlik özellikleri  
 Aşağıdaki tabloda <xref:System.Activities.Statements.Flowchart> özellikleri Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzu veya tasarımcı yüzeyine düzenlenebilir.  
  
|Özellik adı|Gerekli|Kullanım|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Üst bilgide etkinlik Tasarımcısı görünen adını belirtir. Akış varsayılan değerdir. Değer içinde düzenlenebilir **özellikleri** penceresi veya doğrudan etkinlik Tasarımcısı başlığı.<br /><br /> Ancak <xref:System.Activities.Activity.DisplayName%2A> kati şekilde gerekli değil kullanmak için en iyi bir uygulamadır.|  
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|False|İçinde bu kapsamlı değişkenlerinin koleksiyonunu <xref:System.Activities.Statements.Flowchart> alt etkinlikleriyle arasında durum paylaşma için.|  
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|False|<xref:System.Activities.Statements.FlowNode> Diğer bir deyişle yürütülmesi <xref:System.Activities.Statements.Flowchart> başlatır.|  
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|False|Koleksiyonu içeren <xref:System.Activities.Statements.FlowNode> nesneler <xref:System.Activities.Statements.Flowchart>.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Akış Çizelgesi](../workflow-designer/flowchart-activity-designers.md)   
 [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)   
 [FlowSwitch\<T >](../workflow-designer/flowswitch-t-activity-designer.md)