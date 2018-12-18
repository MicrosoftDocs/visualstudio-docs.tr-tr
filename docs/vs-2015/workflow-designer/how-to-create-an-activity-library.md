---
title: 'Nasıl yapılır: etkinlik kitaplığı oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 341e87459cbaae204baba66108a5944eb1f7f97f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49271838"
---
# <a name="how-to-create-an-activity-library"></a>Nasıl yapılır: etkinlik kitaplığı oluşturma
Özel etkinlikler, bir iş akışındaki belirli İş süreçlerinizi modelleyin için kullanılır. Etkinlik kitaplığı şablonu [!INCLUDE[vs2010](../includes/vs2010-md.md)] sağlamak görsel olarak kullanarak bu tür özel etkinlikler oluşturmak sağlanan [!INCLUDE[wfd1](../includes/wfd1-md.md)].  
  
### <a name="to-create-a-workflow-activity-library"></a>Bir iş akışı etkinlik kitaplığı oluşturma  
  
1.  Başlangıç [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje...** .  
  
     **Yeni proje** iletişim kutusu açılır.  
  
3.  İçinde **proje türleri** bölmesinde **iş akışı** da **Visual C#** projeleri veya **Visual Basic** gruplandırmaları bağlı olarak, dil tercihi.  
  
4.  İçinde **şablonları** bölmesinde **etkinlik Kitaplığı**.  
  
5.  İçinde **adı** kutusuna tanımlamak kolay hale getirmek için projeniz için açıklayıcı bir ad yazın.  
  
6.  İçinde **konumu** kutusuna yazın veya projenizi kaydetmek istediğiniz dizine **Gözat** gitmek için.  
  
7.  İçinde **çözüm** kutusunda, çözümünüz için açıklayıcı bir ad yazın ve ardından tıklayın **Tamam**.  
  
    > [!NOTE]
    >  Varolan bir çözüm için bir iş akışı konsol uygulaması eklemek istiyorsanız, bu çözümde açık [!INCLUDE[vs2010](../includes/vs2010-md.md)], çözüme sağ tıklayın **Çözüm Gezgini**seçip **Ekle**, ardından  **Yeni proje...** açmak için **yeni proje** iletişim kutusu. Bu yordamda yukarıda açıklanan şekilde devam edin.  
  
8.  Proje şablonu, XAML içinde bir etkinlik tanımı oluşturur. [!INCLUDE[wfd1](../includes/wfd1-md.md)] açılır ve özel etkinliğinizin tuval görüntüler.  
  
9. Etkinliği sürükleyin **araç kutusu** özel etkinliklerinizi içerecek şekilde tasarım yüzeyine bırakın.  
  
    > [!CAUTION]
    >  Yalnızca bir alt etkinlik özel etkinliğinizin gövdesinde izin verilir; Ancak, bu alt etkinlik bileşik bir etkinlik gibi olabilir bir <xref:System.Activities.Statements.Sequence> etkinlik veya <xref:System.Activities.Statements.Flowchart> etkinlik.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: bir etkinliği oluşturma](http://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436)   
 [İş Akışı Projesi Oluşturma](../workflow-designer/creating-a-workflow-project.md)