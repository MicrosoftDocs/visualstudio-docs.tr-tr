---
title: İş Akışı Tasarımcısı - Parallel etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 76e0d7646645c7d86859de7f79ff22a46131c4a5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863769"
---
# <a name="parallel-activity-designer"></a>Parallel Etkinlik Tasarımcısı

<xref:System.Activities.Statements.Parallel> Etkinliği çocuk etkinliklerinin bir koleksiyonu aynı anda yürütür.

## <a name="the-parallel-activity"></a>Paralel etkinlik

<xref:System.Activities.Statements.Parallel> Etkinlik alt etkinlikleriyle depolayan bir <xref:System.Activities.Statements.Parallel.Branches%2A> koleksiyonu. Kullanım <xref:System.Activities.Statements.Parallel> yerine etkinlik <xref:System.Activities.Statements.Sequence> çocuk etkinliklerinin bazıları boş giderseniz etkinlik.

<xref:System.Activities.Statements.Parallel> Etkinliğinde bir <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> içeren bir kullanıcı özelliği belirtilen Visual Basic ifade. <xref:System.Activities.Statements.Parallel> Her dal tamamlandıktan sonra bu özellik etkinlik değerlendirir. Değerlendirilirse **True**, ardından <xref:System.Activities.Statements.Parallel> etkinliği tamamlandıktan diğer dalları çalıştırmadan. Varsa <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> için değerlendirilmiyor **True**, ardından <xref:System.Activities.Statements.Parallel> etkinliği tamamlandıktan tüm alt etkinliklerinin tamamladıktan sonra.

### <a name="using-the-parallel-activity-designer"></a>Paralel etkinlik Tasarımcısını kullanma

Erişim **paralel** etkinlik Tasarımcısı'nda **akış denetimi** kategorisi **araç kutusu**.

**Paralel** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve etkinlik tasarımcıları normalde, örneğin, bir içineyerleştirilenheryerdeişakışıTasarımcısıyüzeyineaçınbırakılan**Dizisi** etkinlik Tasarımcısı. İş akışı tasarımcıya bırakılırken sonra oluşturduğu bir <xref:System.Activities.Statements.Parallel> içeren varsayılan olarak, etkinlik bir <xref:System.Activities.Activity.DisplayName%2A> , **paralel**

Bir etkinlik eklemek için <xref:System.Activities.Statements.Parallel.Branches%2A> paralel etkinlik koleksiyonunu sürükleyin bazı diğer etkinlik Tasarımcısı'ndan **araç kutusu** ve bu üçgen bırak **paralel** etkinlik Tasarımcısı. Bu üçgen dalları etkinlikleri flank. Bu yordamı tekrarlayarak ek etkinlikler eklenebilir. Etkinlikler, bunların içinde sürükleyip bırakarak sıralanabilir **paralel** etkinlik Tasarımcısı.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>İş akışı tasarımcısında paralel etkinlik özellikleri

Aşağıdaki tabloda, paralel etkinlik özelliklerini gösterir ve Tasarımcısı'nda nasıl kullanıldığını açıklar.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Üst bilgide etkinlik Tasarımcısı kolay görünen adını belirtir. Varsayılan değer **paralel**. Değer, isteğe bağlı olarak düzenlenebilir **özellikleri** kılavuz veya doğrudan etkinlik Tasarımcısı başlığı.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Doğru|Yürütülecek çocuk etkinliklerinin koleksiyonunu içerir.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Bir dal tamamlandıktan sonra değerlendirilir. Değerlendirilirse **True**, ardından zamanlanmış dalları iptal edilir. Bu özelliği ayarlı değil veya değerlendiren **False**, tüm alt etkinliklerinin tamamladığında etkinliği tamamlar. Varsayılan değer **null**.|

## <a name="see-also"></a>Ayrıca bkz.

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Denetim Akışı](../workflow-designer/control-flow-activity-designers.md)