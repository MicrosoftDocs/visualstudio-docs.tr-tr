---
title: FlowSwitch&lt;T&gt; etkinlik Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: ed39806fdca8eec3deccf5383c2386d07f0af929
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254765"
---
# <a name="flowswitchlttgt-activity-designer"></a>FlowSwitch&lt;T&gt; etkinlik Tasarımcısı
<xref:System.Activities.Statements.FlowSwitch%601> Dallanma ikiden fazla alternatif dalları gerekli olduğunda eşleştirme ölçütü temel alan denetim akışı için sağlayan bir koşullu düğüm bir etkinliktir. Akış dallanma yalnızca iki yolu gerektiriyorsa, kullanın <xref:System.Activities.Statements.FlowDecision> etkinliği bunun yerine.  
  
## <a name="the-flowswitcht-activity"></a>FlowSwitch\<T > etkinliği  
 <xref:System.Activities.Statements.FlowSwitch%601> Etkinliği içeren bir <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> türünde bir değer döndüren *T* (genel parametre tarafından belirtilen) değerlendirildiğinde. Etkinliği de bir dizi içeren <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, bir dizi benzersiz bir eşleme bu değerlendirmeyi mümkün sonuçlarından belirtir <xref:System.Activities.Statements.FlowNode> nesneleri. <xref:System.Activities.Statements.FlowNode> Yürütülen bir olan nesnenin türü olan *T* değerlendirilen değeri ile eşleşen <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. A <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> çalışması eşleşme alınır durum (isteğe bağlı olarak) sağlanabilir.  
  
### <a name="using-the-flowswitcht-activity-designer"></a>FlowSwitch kullanarak\<T > etkinlik Tasarımcısı  
 **FlowSwitch\<T >** etkinlik Tasarımcısı bulunabilir **akış** kategorisi **araç kutusu**, hangi erişilen tıklayarak**Araç kutusu** sol tarafındaki sekmesinde [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatif olarak, seçin **araç** gelen **görünümü** menüsünü veya CTRL + ALT + X.)  
  
 **FlowSwitch\<T >** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve oturum bırakılan [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzey içinde bir **akış** Etkinlik Tasarımcısı. Kullanım **türleri seçin** türü belirtmek için görüntüleyen pencere (kod ile ilişkili <xref:System.Activities.Statements.FlowSwitch%601> genel parametresi tarafından) hesaplanmasının elde <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Bu yordam oluşturur bir <xref:System.Activities.Statements.FlowSwitch%601> etiketli etkinlik **anahtar** içinde <xref:System.Activities.Statements.Flowchart> etkinlik. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> Yazılabilir **ifade** kutusunun **özellikleri** tıklayarak penceresi ipucu metnini burada Yazan "VB ifadesi girin".  
  
 Fare üzerindeyken **FlowSwitch\<T >** bağlantı için kullanılan kare tutamaçları neden etkinlik Tasarımcısı <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> kenarlarını geçici bir çözüm bulmak görüntülenmesini. Sürükleme sonra **FlowSwitch < T\>**  etkinlik Tasarımcısı ve diğer etkinlik tasarımcıları üzerine **akış**, <xref:System.Activities.Activity> temsil ettikleri nesneler birbirine bağlı hazır Yürütme sırası belirtmek için. Birini <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> ilişkili <xref:System.Activities.Statements.FlowSwitch%601>, çevre kare büyük/küçük harf tutamaçlardan birini tıklatın **FlowSwitch\<T >** ve (fare düğmesini basılı tutarak) tutamaçlarından birinin sürükleyin İş Tasarımcısı fare geldiğinde hedef etkinlik etrafında benzer şekilde görünür. Sürüm fare düğmesini ve bir ok **FlowSwitch\<T >** bu durumda temsil eden hedef tasarımcıya görünür. Varsayılan değer, bu durumda bulunan oka görüntüler ve içinde düzenlenebilir **çalışması** kutusunun **özellikleri** penceresi.  
  
### <a name="the-flowswitcht-properties"></a>FlowSwitch\<T > Özellikleri  
 Aşağıdaki tabloda <xref:System.Activities.Statements.FlowSwitch%601> özellikleri Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.  
  
|Özellik adı|Gerekli|Kullanım|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|Doğru|Hangi belirlemek için değerlendirilen bir ifade belirtir <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> yolu yürütme penceresine geçin.|  
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Hesaplanmasının elde edilen olası sonuçları benzersiz bir eşlemeyi belirtir <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> bir dizi <xref:System.Activities.Statements.FlowNode> nesneleri.|  
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|Doğru|Eşleme belirtir, değerlendirmesi <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> yer alan değerlerden eşleşmiyor <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> nesne.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Akış Çizelgesi](../workflow-designer/flowchart-activity-designers.md)   
 [Akış Çizelgesi](../workflow-designer/flowchart-activity-designer.md)   
 [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)