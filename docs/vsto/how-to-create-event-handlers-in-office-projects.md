---
title: 'Nasıl yapılır: Office projelerinde olay işleyicileri oluşturma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8b7e55ee7f094ad104d9c8eb6ef3057621bcccee
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254250"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Nasıl yapılır: Office projelerinde olay işleyicileri oluşturma
  Visual Basic ve C# ' olay işleyicileri oluşturmanın birkaç yolu vardır. Tasarım görünümünde, varsayılan denetimleri için olay işleyicileri denetimi çift tıklatarak oluşturabilir, veya olayları bölmesini kullanarak **özellikleri** herhangi bir olay işleyicileri denetimi oluşturmak için pencere. Bununla birlikte, kod görünümünde varsa, olay işleyici oluşturmak için Tasarım görünümüne geçiş istemeyebilirsiniz.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-an-event-handler-in-visual-basic"></a>Visual Basic'te bir olay işleyicisi oluşturmak için  
  
1.  Gelen **sınıf adı** aşağı açılan liste Kod Düzenleyicisi'nin üstünde seçin, istediğiniz nesne oluşturmak için bir olay işleyicisi.  
  
    > [!NOTE]  
    >  Olay işleyicileri oluşturmak istiyorsanız `ThisDocument` veya `ThisWorkbook`, seçmelisiniz **(ThisDocument olayları)** veya **(ThisWorkbook olayları)** içinde **sınıf adı**aşağı açılan liste  
  
2.  Gelen **yöntem adı** aşağı açılan liste Kod Düzenleyicisi'nin en üstünde, olayı seçin.  
  
     Visual Studio, olay işleyicisi oluşturur ve yeni oluşturulan olay işleyicisi ekleme noktasını taşır. Olay işleyicisi zaten varsa, mevcut olay işleyicisi ekleme noktasını taşır.  
  
### <a name="to-create-an-event-handler-in-c"></a>Olay işleyici C# ' ta oluşturmak için  
  
1.  Olay temsilcisini oluşturmak **başlangıç** bir boşluk bırakarak tam olay adını yazarak ve ardından yazarak sınıfının olayını **+=** boşluk daha sonra. Örneğin:  
  
     `this.<object name>.<event name> +=`  
  
2.  Kod satırının sonunda, iki kez SEKME tuşuna basın.  
  
     Visual Studio otomatik olarak kod satırını tamamlar, olay işleyicisi oluşturur ve yeni oluşturulan olay işleyicisi ekleme noktasını taşır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)   
 [İzlenecek yol: Program NamedRange denetimi olaylarına karşı](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Office çözümleri oluşturma](../vsto/building-office-solutions.md)  
  
  