---
title: İş Akışı Tasarımcısı - Ata etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 600f38d7bcd387915ba61fc148805705e8609431
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905264"
---
# <a name="assign-activity-designer"></a>Assign Etkinlik Tasarımcısı

**Atama** etkinlik Tasarımcısı oluşturmak ve yapılandırmak için kullanılan bir <xref:System.Activities.Statements.Assign> etkinlik.

## <a name="the-assign-activity"></a>Ata etkinliği

<xref:System.Activities.Statements.Assign> Etkinliği, bir değişken veya bağımsız değişken bir değer atar.

### <a name="using-the-assign-activity-designer"></a>Ata etkinlik Tasarımcısını kullanma

**Atama** etkinlik Tasarımcısı bulunabilir **Temelleri** kategorisi **araç kutusu**, hangi erişilen tıklayarak **araç kutusu**sekme (Alternatif olarak, seçin **araç kutusu** gelen **görünümü** menüsünden veya CTRL + ALT + X.)

**Atama** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve etkinlikleri yerleştirilir burada ever, örneğin olarak içinde iş akışı Tasarımcısı yüzeyine açın bırakılan bir <xref:System.Activities.Statements.Sequence>. Bırakarak **atama** etkinlik Tasarımcısı oluşturur bir <xref:System.Activities.Statements.Assign> etkinliği ile bir varsayılan **DisplayName** Ata'nın. <xref:System.Activities.Activity.DisplayName%2A> Üst bilgisinde düzenlenebilir **atama** etkinlik Tasarımcısı veya **DisplayName** özellik kılavuzunda kutusu.

### <a name="the-assign-properties"></a>Ata özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.Assign> özellikleri Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda düzenlenebilir ve bunlardan bazıları iş akışı Tasarımcısı yüzeyine düzenlenebilir.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Kolay adı <xref:System.Activities.Statements.Assign> etkinlik. Ata varsayılandır. Ancak <xref:System.Activities.Activity.DisplayName%2A> değeri kesinlikle gerekli değil, kullanmak için en iyi bir uygulamadır.|
|<xref:System.Activities.Statements.Assign.To%2A>|Doğru|Değişken veya bağımsız değişken olarak <xref:System.Activities.Statements.Assign.Value%2A> atanır. Değerin geçerli bir Visual Basic tanımlayıcısı olması gerekir. Özellik ayarlamak için bir Visual Basic ifadesinin türü **için** kutusuna **atama** etkinlik Tasarımcısı veya özellik kılavuzunda.|
|<xref:System.Activities.Statements.Assign.Value%2A>|Doğru|Değişkene atanan değer. Ayarlanacak <xref:System.Activities.Statements.Assign.Value%2A>, Visual Basic ifadesindeki türü **değer** kutusuna **atama** etkinlik Tasarımcısı veya özellik kılavuzunda.|

## <a name="see-also"></a>Ayrıca bkz.

- [Temel Türler](../workflow-designer/primitives-activity-designers.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)