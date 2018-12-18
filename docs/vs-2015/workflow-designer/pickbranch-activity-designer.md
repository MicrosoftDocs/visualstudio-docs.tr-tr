---
title: PickBranch etkinlik Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f39479c9421ab87caf7c918e05be89272f0fb4de
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887317"
---
# <a name="pickbranch-activity-designer"></a>PickBranch Etkinlik Tasarımcısı
<xref:System.Activities.Statements.PickBranch> Yürütme içinde olay-tabanlı bir yolunu sağlayan bir <xref:System.Activities.Statements.Pick> , gelen bir olay tarafından tetiklenebilecek bir etkinlik.  
  
## <a name="pickbranch"></a>PickBranch  
 <xref:System.Activities.Statements.PickBranch> içinde kapsanan nesneleri <xref:System.Activities.Statements.Pick.Branches%2A> koleksiyonunu bir <xref:System.Activities.Statements.Pick> etkinlik. Her <xref:System.Activities.Statements.PickBranch> bir dalda bulunan <xref:System.Activities.Statements.Pick> etkinliği ve bir tetikleyici olarak hizmet veren bazı gelen bir olay nedeniyle yürütülür. Bu şekilde [!INCLUDE[wfd1](../includes/wfd1-md.md)] olay tabanlı denetim akış modelleme sağlar. Her <xref:System.Activities.Statements.PickBranch> içeren bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> ve <xref:System.Activities.Statements.PickBranch.Action%2A>.  
  
### <a name="how-to-use-the-pick-activity-designer"></a>Çekme Etkinlik Tasarımcısı kullanma  
 **PickBranch** Tasarımcısı bulunabilir **akış denetimi** kategorisi **araç kutusu**, hangi erişilen tıklayarak **araç kutusu** sekmesindeki [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatif olarak, seçin **araç** gelen **görünümü** menüsünü veya CTRL + ALT + X).  
  
 İki boş <xref:System.Activities.Statements.PickBranch> nesneleriyle adlarını görüntülemek **Branch1** ve **Branch2** öğeleri olarak varsayılan olarak oluşturulan bir <xref:System.Activities.Statements.Pick> etkinlik zaman **çekme** Etkinlik Tasarımcısı için bırakılan başlangıçta [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Bu ilgili <xref:System.Activities.Statements.PickBranch.DisplayName%2A> özellik değerlerini düzenlenebilir **PickBranch** Tasarımcı üst bilgi veya içinde **özellikleri** her dal için penceresi.  
  
 Eklemek için iki yolu vardır <xref:System.Activities.Statements.PickBranch> nesneler koleksiyonuna bir <xref:System.Activities.Statements.Pick> nesne: sürükleme ve bırakma **PickBranch** nden Tasarımcı **araç kutusu** veya bağlam menüsünden kullanarak içinde **çekme** tasarım yüzeyine:  
  
1. **PickBranch** Tasarımcısı oluşturur bir <xref:System.Activities.Statements.PickBranch> zaman bunu sürüklediğiniz gelen **araç kutusu** ve dalları birine bırakılan bir **çekme** üzerindeetkinlikTasarımcısı[!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyi. Yeni <xref:System.Activities.Statements.PickBranch> nesneleri, içine yerleştirilebilir <xref:System.Activities.Statements.Pick> sola veya sağa var olan herhangi biri Tasarımcı <xref:System.Activities.Statements.PickBranch> zaten koleksiyonda yer alan öğeleri. Sürüklendiğinde bir **PickBranch** üzerine Tasarımcı **çekme** fareyle, tasarımcı **çekme** Tasarımcısı yeri belirtmek üzere bir dikey gri mavi bandı kullanır <xref:System.Activities.Statements.PickBranch> verilen fare yerleştirme için eklenir.  
  
2. Sağ tıklayın **çekme** etkinlik Tasarımcısı (ancak değil iç **PickBranch** Tasarımcısı) seçin ve bağlam menüsü elde **dal oluşturma** yeni bir <xref:System.Activities.Statements.PickBranch>. Dikkat yeni <xref:System.Activities.Statements.PickBranch> varolan sağa eklenen <xref:System.Activities.Statements.PickBranch> nesneler **çekme** Tasarımcısı.  
  
   **PickBranch** Tasarımcısı açığa çıkarmak için Genişletilebilir **tetikleyici** ve **eylem** kutuları veya kendi üst sağ tarafında çift düzeltme işaretleri tıklayarak daraltılmış. Düzenleme <xref:System.Activities.Statements.PickBranch.Trigger%2A> ve <xref:System.Activities.Statements.PickBranch.Action%2A> her <xref:System.Activities.Statements.PickBranch> etkinliklerine bırakarak tarafından **tetikleyici** ve **eylem** kutularını kendi tasarımcıları.  
  
   <xref:System.Activities.Statements.PickBranch> Nesneler <xref:System.Activities.Statements.Pick.Branches%2A> koleksiyonunu bir <xref:System.Activities.Statements.Pick> nesne, bunları içinde yeni bir konuma sürükleyip bırakarak sıralanabilir **çekme** Tasarımcısı. **Çekme** Tasarımcısı yeri belirtmek üzere bir dikey gri mavi bandı kullanır <xref:System.Activities.Statements.PickBranch> verilen fare yerleştirme için eklenir.  
  
   Silmek için iki yolla bir <xref:System.Activities.Statements.PickBranch>:  
  
3. Seçin **PickBranch** Tasarımcısı ve silin.  
  
4. Seçin **PickBranch** seçin ve bağlam menüsünü elde etmek için tasarımcı, sağ tıklama **Sil**.  
  
   Seçtiğinizden emin olun **PickBranch** Tasarımcı içinde etkinliklerden birini seçerek olarak kendi **tetikleyici** veya **eylem** kutuları yanlışlıkla siler Bu etkinliklerden birini değil <xref:System.Activities.Statements.PickBranch> nesne.  
  
### <a name="pickbranch-properties-in-the-workflow-designer"></a>İş akışı tasarımcısında PickBranch özellikleri  
 Aşağıdaki tabloda en kullanışlı gösterilmektedir <xref:System.Activities.Statements.PickBranch> özellikleri ve bunları kullanmayı açıklar [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Özellik adı|Gerekli|Kullanım|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Başlığında görüntülenen kolay ad **PickBranch** Tasarımcısı. Varsayılan değer daldır.<br /><br /> Ancak <xref:System.Activities.Activity.DisplayName%2A> kati şekilde gerekli değil kullanmak için en iyi bir uygulamadır.|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|Doğru|Her <xref:System.Activities.Statements.PickBranch> içeren bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> çağırabilirsiniz eylem <xref:System.Activities.Statements.PickBranch.Action%2A>.|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Her <xref:System.Activities.Statements.PickBranch> içeren bir <xref:System.Activities.Statements.PickBranch.Action%2A> tetiklenen ise yürütülür.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)   
 [Pick etkinliği](http://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e)   
 [Pick Etkinliği Kullanma](http://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)