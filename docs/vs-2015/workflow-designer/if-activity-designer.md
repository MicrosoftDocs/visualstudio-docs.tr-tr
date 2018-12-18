---
title: Etkinlik Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: fee98f4b95d626e429662d20501541c3241a9b2e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244237"
---
# <a name="if-activity-designer"></a>If Etkinlik Tasarımcısı
<xref:System.Activities.Statements.If> Etkinliği bir koşulu değerlendirir ve bu değerlendirme sonuçlarına bağlı olarak bir etkinliği yürütür. Bu etkinlik, bir yordamsal programlama stilini modelleme kullanırken en yararlı olur. Bir <xref:System.Activities.Statements.If> etkinlik iç içe geçirilemez içinde bir <xref:System.Activities.Statements.Sequence> etkinlik veya <xref:System.Activities.Statements.Parallel> örneğin bir etkinlik. Kullanıyorsanız bir <xref:System.Activities.Statements.Flowchart> etkinliği kullanmayı bir <xref:System.Activities.Statements.FlowDecision> etkinliği bunun yerine.  
  
## <a name="if-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı özellikleri  
 Aşağıdaki tabloda en kullanışlı gösterilmektedir <xref:System.Activities.Statements.If> etkinlik özellikleri ve tasarımcıda kullanmayı açıklar.  
  
|Özellik adı|Gerekli|Kullanım|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.If.Condition%2A>|Doğru|Yürütmek için hangi alt etkinlik belirleyen koşul. Ayarlanacak <xref:System.Activities.Statements.If.Condition%2A>, tür a [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ifadesinde **koşul** kutusuna **varsa** etkinlik Tasarımcısı veya özellik kılavuzunda.|  
|<xref:System.Activities.Statements.If.Else%2A>|False|Etkinlik, yürütülecek <xref:System.Activities.Statements.If.Condition%2A> olduğu **false**. Tarafından yürütülen bir etkinlik eklemek için <xref:System.Activities.Statements.If.Else%2A> dal, etkinliği bırak **araç kutusu** içine **Else** kutusuna **varsa** ipucu metnini ile etkinlik Tasarımcısı " Etkinliği buraya bırakın".|  
|<xref:System.Activities.Statements.If.Then%2A>|False|Etkinlik, yürütülecek <xref:System.Activities.Statements.If.Condition%2A> olduğu **true**. Tarafından yürütülen bir etkinlik eklemek için <xref:System.Activities.Statements.If.Then%2A> dal, etkinliği bırak **araç kutusu** içine **ardından** kutusuna **varsa** ipucu metnini ile etkinlik Tasarımcısı " Etkinliği buraya bırakın".|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dizisi](../workflow-designer/sequence-activity-designer.md)   
 [Paralel](../workflow-designer/parallel-activity-designer.md)   
 [Denetim Akışı](../workflow-designer/control-flow-activity-designers.md)