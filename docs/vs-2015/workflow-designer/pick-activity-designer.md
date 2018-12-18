---
title: Pick etkinlik Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f0a3d5487d60a796f8bf9727c07df1afc959de5c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49221526"
---
# <a name="pick-activity-designer"></a>Pick Etkinlik Tasarımcısı
<xref:System.Activities.Statements.Pick> Olay tabanlı denetim akış etkinliği sağlar. Etkinlik birden fazla dalları birini bir tetikleyici olaya yanıt olarak yürütür.  
  
## <a name="the-pick-activity"></a>Pick etkinliği  
 A <xref:System.Activities.Statements.Pick> etkinliği içeren bir koleksiyonu <xref:System.Activities.Statements.PickBranch> nesneler, biri <xref:System.Activities.Statements.Pick> etkinlik, bir tetikleyici olarak hizmet veren bazı gelen bir olay nedeniyle yürütebilir. Bu şekilde [!INCLUDE[wfd1](../includes/wfd1-md.md)] olay tabanlı denetim akış modelleme sağlar. Her <xref:System.Activities.Statements.PickBranch> içeren bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> ve <xref:System.Activities.Statements.PickBranch.Action%2A>. Başında bir <xref:System.Activities.Statements.Pick> etkinliğin yürütme, tüm tetikleyici etkinliklerini <xref:System.Activities.Statements.PickBranch> öğeleri zamanlanır. İlk etkinlik tamamlandıktan sonra karşılık gelen eylem etkinliği zamanlandı ve diğer tetikleyici etkinlikleri iptal edilir.  
  
### <a name="how-to-use-the-pick-activity-designer"></a>Çekme Etkinlik Tasarımcısı kullanma  
 **Çekme** etkinlik Tasarımcısı bulunabilir **akış denetimi** kategorisi **araç kutusu**, hangi erişilen tıklayarak **araç kutusu**sekmesinde [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatif olarak, seçin **araç** gelen **görünümü** menüsünden veya CTRL + ALT + X.)  
  
 **Çekme** etkinlik Tasarımcısı, gelen sürüklenebilir **araç kutusu** ve oturum bırakılan [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzey yerde etkinlik tasarımcıları normalde yerleştirilir, örneğin içine bir  **Dizisi** etkinlik Tasarımcısı. İçine bırakmadan sonra [!INCLUDE[wfd2](../includes/wfd2-md.md)], oluşturduğu bir <xref:System.Activities.Statements.Pick> içeren varsayılan olarak iki boş etkinlik <xref:System.Activities.Statements.PickBranch> etkinlikleri öğelerle olarak görünen adlar Branch1 ve Branch2. Bu ilgili <xref:System.Activities.Statements.PickBranch.DisplayName%2A> özellik değerlerini düzenlenebilir **PickBranch** etkinlik Tasarımcısı üst bilgi veya içinde **özellikleri** her dal için penceresi.  
  
 Eklemek için iki yolu vardır <xref:System.Activities.Statements.PickBranch> etkinlikleri koleksiyonuna bir <xref:System.Activities.Statements.Pick> nesne: sürükleme ve bırakma **PickBranch** nden Tasarımcı **araç kutusu** veya bağlam menüsünden kullanarak içinde **çekme** tasarım yüzeyi. Ayrıntılar için bkz [PickBranch](../workflow-designer/pickbranch-activity-designer.md) konu. Yalnızca öğesini dikkat edin, içine yerleştirilebilir bir **çekme** etkinlik Tasarımcısı bir **PickBranch** etkinlik Tasarımcısı.  
  
### <a name="pick-activity-properties-in-the-workflow-designer"></a>İş akışı tasarımcısında etkinlik özellikleri seçin  
 Aşağıdaki tabloda <xref:System.Activities.Statements.Pick> özellikleri Tasarımcısı'nda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzu veya tasarımcı yüzeyine düzenlenebilir.  
  
|Özellik adı|Gerekli|Kullanım|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Kolay adı belirtir <xref:System.Activities.Statements.Pick> üst bilgisindeki etkinlik Tasarımcısı. Seçim varsayılan değerdir. Değer özellik kılavuzunda veya etkinlik Tasarımcısı başlığındaki doğrudan düzenleyebilirsiniz.<br /><br /> Ancak <xref:System.Activities.Activity.DisplayName%2A> kati şekilde gerekli değil kullanmak için en iyi bir uygulamadır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)   
 [Pick etkinliği](http://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e)   
 [Pick Etkinliği Kullanma](http://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)