---
title: İş Akışı Tasarımcısı - varsa etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 716f2b13758864d5eda449967990f9e5be399a9d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822851"
---
# <a name="if-activity-designer"></a>If Etkinlik Tasarımcısı

<xref:System.Activities.Statements.If> Etkinliği bir koşulu değerlendirir ve bu değerlendirme sonuçlarına bağlı olarak bir etkinliği yürütür. Bu etkinlik, bir yordamsal programlama stilini modelleme kullanırken en yararlı olur. Bir <xref:System.Activities.Statements.If> etkinlik iç içe geçirilemez içinde bir <xref:System.Activities.Statements.Sequence> etkinlik veya <xref:System.Activities.Statements.Parallel> örneğin bir etkinlik. Kullanıyorsanız bir <xref:System.Activities.Statements.Flowchart> etkinliği kullanmayı bir <xref:System.Activities.Statements.FlowDecision> etkinliği bunun yerine.

## <a name="if-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı özellikleri

Aşağıdaki tabloda en kullanışlı gösterilmektedir <xref:System.Activities.Statements.If> etkinlik özellikleri ve tasarımcıda kullanmayı açıklar.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|Doğru|Yürütmek için hangi alt etkinlik belirleyen koşul. Ayarlanacak <xref:System.Activities.Statements.If.Condition%2A>, Visual Basic ifadesindeki türü **koşul** kutusuna **varsa** etkinlik Tasarımcısı veya özellik kılavuzunda.|
|<xref:System.Activities.Statements.If.Else%2A>|False|Etkinlik, yürütülecek <xref:System.Activities.Statements.If.Condition%2A> olduğu **false**. Tarafından yürütülen bir etkinlik eklemek için <xref:System.Activities.Statements.If.Else%2A> dal, etkinliği bırak **araç kutusu** içine **Else** kutusuna **varsa** ipucu metnini ile etkinlik Tasarımcısı " Etkinliği buraya bırakın".|
|<xref:System.Activities.Statements.If.Then%2A>|False|Etkinlik, yürütülecek <xref:System.Activities.Statements.If.Condition%2A> olduğu **true**. Tarafından yürütülen bir etkinlik eklemek için <xref:System.Activities.Statements.If.Then%2A> dal, etkinliği bırak **araç kutusu** içine **ardından** kutusuna **varsa** ipucu metnini ile etkinlik Tasarımcısı " Etkinliği buraya bırakın".|

## <a name="see-also"></a>Ayrıca bkz.

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Denetim Akışı](../workflow-designer/control-flow-activity-designers.md)