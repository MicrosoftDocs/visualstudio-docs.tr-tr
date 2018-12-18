---
title: 'Nasıl yapılır: program aracılığıyla e-posta gönderme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 32977852ffbc4bb1411ed699cc97bb54035fada4
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677854"
---
# <a name="how-to-programmatically-send-email"></a>Nasıl yapılır: program aracılığıyla e-posta gönderme  
  Bu örnekte, etki alanı adına sahip kişilere bir e-posta iletisi gönderilir **example.com** kendi e-posta adresleri.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>Kod derleme  
 Bu örnek gerektirir:  
  
-   Etki alanı adına sahip kişiler **example.com** kendi e-posta adresleri.  
  
## <a name="robust-programming"></a>Güçlü programlama  
 Etki alanı adını arar filtreleme kodunu kaldırmayın **example.com**. Filtreyi kaldırmanız durumunda, çözümünüzün, tüm kişilere e-posta iletilerini gönderir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Posta öğeleriyle çalışma](../vsto/working-with-mail-items.md)   
 [Nasıl yapılır: program aracılığıyla bir e-posta öğesi oluşturma](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [Nasıl yapılır: program aracılığıyla Outlook Kişilerine erişme](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Nasıl yapılır: bir e-posta iletisi alındığında program aracılığıyla işlem gerçekleştirme](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  