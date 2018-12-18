---
title: Paralel etkinlik Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f557eb013cb313321b336fb22fd1299e51faaa82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49221597"
---
# <a name="parallel-activity-designer"></a>Parallel Etkinlik Tasarımcısı
<xref:System.Activities.Statements.Parallel> Etkinliği çocuk etkinliklerinin bir koleksiyonu aynı anda yürütür.  
  
## <a name="the-parallel-activity"></a>Paralel etkinlik  
 <xref:System.Activities.Statements.Parallel> Etkinlik alt etkinlikleriyle depolayan bir <xref:System.Activities.Statements.Parallel.Branches%2A> koleksiyonu. Kullanım <xref:System.Activities.Statements.Parallel> yerine etkinlik <xref:System.Activities.Statements.Sequence> çocuk etkinliklerinin bazıları boş giderseniz etkinlik.  
  
 <xref:System.Activities.Statements.Parallel> Etkinliğinde bir <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> içeren bir kullanıcı tarafından belirtilen özelliğe [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ifade. <xref:System.Activities.Statements.Parallel> Her dal tamamlandıktan sonra bu özellik etkinlik değerlendirir. Değerlendirilirse **True**, ardından <xref:System.Activities.Statements.Parallel> etkinliği tamamlandıktan diğer dalları çalıştırmadan. Varsa <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> için değerlendirilmiyor **True**, ardından <xref:System.Activities.Statements.Parallel> etkinliği tamamlandıktan tüm alt etkinliklerinin tamamladıktan sonra.  
  
### <a name="using-the-parallel-activity-designer"></a>Paralel etkinlik Tasarımcısını kullanma  
 **Paralel** etkinlik Tasarımcısı bulunabilir **akış denetimi** kategorisi **araç kutusu**, hangi erişilen tıklayarak **araç kutusu**sol tarafındaki sekmesinde [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatif olarak, seçin **araç** gelen **görünümü** menüsünü veya CTRL + ALT + X.)  
  
 **Paralel** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve oturum bırakılan [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzey yerde etkinlik tasarımcıları normalde yerleştirilir, örneğin, bir içinde**Dizisi** etkinlik Tasarımcısı. İçine bırakmadan sonra [!INCLUDE[wfd2](../includes/wfd2-md.md)], oluşturduğu bir <xref:System.Activities.Statements.Parallel> içeren varsayılan olarak, etkinlik bir <xref:System.Activities.Activity.DisplayName%2A> , **paralel**  
  
 Bir etkinlik eklemek için <xref:System.Activities.Statements.Parallel.Branches%2A> paralel etkinlik koleksiyonunu sürükleyin bazı diğer etkinlik Tasarımcısı'ndan **araç kutusu** ve bu üçgen bırak **paralel** etkinlik Tasarımcısı. Bu üçgen dalları etkinlikleri flank. Bu yordamı tekrarlayarak ek etkinlikler eklenebilir. Etkinlikler, bunların içinde sürükleyip bırakarak sıralanabilir **paralel** etkinlik Tasarımcısı.  
  
### <a name="parallel-activity-properties-in-the-workflow-designer"></a>İş akışı tasarımcısında paralel etkinlik özellikleri  
 Aşağıdaki tabloda, paralel etkinlik özelliklerini gösterir ve Tasarımcısı'nda nasıl kullanıldığını açıklar.  
  
|Özellik adı|Gerekli|Kullanım|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Üst bilgide etkinlik Tasarımcısı kolay görünen adını belirtir. Varsayılan değer **paralel**. Değer, isteğe bağlı olarak düzenlenebilir **özellikleri** kılavuz veya doğrudan etkinlik Tasarımcısı başlığı.|  
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Doğru|Yürütülecek çocuk etkinliklerinin koleksiyonunu içerir.|  
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Bir dal tamamlandıktan sonra değerlendirilir. Değerlendirilirse **True**, ardından zamanlanmış dalları iptal edilir. Bu özelliği ayarlı değil veya değerlendiren **False**, tüm alt etkinliklerinin tamamladığında etkinliği tamamlar. Varsayılan değer **null**.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dizisi](../workflow-designer/sequence-activity-designer.md)   
 [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Denetim Akışı](../workflow-designer/control-flow-activity-designers.md)