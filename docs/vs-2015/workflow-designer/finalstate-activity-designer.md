---
title: FinalState etkinlik Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
caps.latest.revision: 5
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 48c44dc585ce1c9cf4e7b29970b4014f128b873d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209176"
---
# <a name="finalstate-activity-designer"></a>FinalState Etkinlik Tasarımcısı
<xref:System.Activities.Core.Presentation.FinalState> Tasarımcısı oluşturmak için kullanılan bir <xref:System.Activities.Statements.State> , durum makine örneği sonlandırır.  
  
## <a name="using-the-finalstate-activity-designer"></a>FinalState etkinlik Tasarımcısı kullanma  
 **FinalState** Tasarımcısı oluşturmak için kullanılan bir <xref:System.Activities.Statements.State> bir durum makinesindeki bir sonlandırıcı durumu olarak yapılandırılmış. A <xref:System.Activities.Statements.State> kullanılarak oluşturulan <xref:System.Activities.Core.Presentation.FinalState> etkinlik Tasarımcısı sahip kendi <xref:System.Activities.Statements.State.IsFinal%2A> özelliğini **true**, hiçbir <xref:System.Activities.Statements.State.Exit%2A> etkinlik ve bundan kaynaklanan hiçbir geçişler. Kullanılacak <xref:System.Activities.Core.Presentation.FinalState> eklemek için etkinlik Tasarımcısı bir <xref:System.Activities.Statements.State> önceden yapılandırılmış bir durum makinesindeki bir sonlandırıcı durumu etkinliğini sürükleyin **FinalState** etkinlik Tasarımcısı'ndan **Durum makinesi**bölümünü **araç kutusu** ve iş akışı Tasarımcısı bırakın. <xref:System.Activities.Core.Presentation.FinalState> Etkinlik Tasarımcısı bırakılan üzerine bir <xref:System.Activities.Statements.StateMachine> ve geçişleri eklenen daha sonra; veya bir geçiş olarak oluşturulabilir <xref:System.Activities.Core.Presentation.FinalState> etkinlik Tasarımcısı bırakıldı. Geçiş oluşturma hakkında daha fazla bilgi için bkz. [geçiş](../workflow-designer/transition-activity-designer.md).  
  
### <a name="state-activity-properties-in-the-workflow-designer"></a>İş akışı tasarımcısında State etkinlik özellikleri  
 Aşağıdaki tabloda kullanılarak ayarlanabilen özelliklerini gösterir <xref:System.Activities.Core.Presentation.FinalState> Tasarımcısı ve Tasarımcısı'nda nasıl kullanıldığını açıklar. Bu özelliklerin bazıları özellik kılavuzunda düzenlenebilir ve bazı Tasarımcı yüzeyinde düzenlenebilir.  
  
|Özellik adı|Gerekli|Kullanım|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Kolay adı belirtir <xref:System.Activities.Statements.State> üst bilgisindeki etkinlik Tasarımcısı. Varsayılan değer **durumu**. Değer özellik kılavuzunda veya etkinlik Tasarımcısı başlığındaki doğrudan düzenleyebilirsiniz. <xref:System.Activities.Statements.State.DisplayName%2A> İş akışı Tasarımcısı üst kısmında görüntülenen içerik haritalı gezinme kullanılır.<br /><br /> Ancak <xref:System.Activities.Statements.State.DisplayName%2A> kati şekilde gerekli değil kullanmak için en iyi bir uygulamadır.|  
|<xref:System.Activities.Statements.State.Entry%2A>|False|Bu durum için geçirildiğinde basıldığında uygulanacak eylemi belirtir. Bu değer, bir etkinlikten sürükleyerek ayarlanabilir **araç kutusu** üzerine sürükleyip bırakarak <xref:System.Activities.Statements.State.Entry%2A> durumu bölümü.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Durum makinesi](../workflow-designer/statemachine-activity-designer.md)   
 [durumu](../workflow-designer/state-activity-designer.md)   
 [Transition](../workflow-designer/transition-activity-designer.md)