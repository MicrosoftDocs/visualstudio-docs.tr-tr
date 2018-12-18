---
title: 'Nasıl yapılır: bir SharePoint Web Bölümü oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6437620b4215726ba48ea3234e37c76e77d21ebe
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120581"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Nasıl yapılır: bir SharePoint web bölümü oluşturma
  Oluşturabilir ve web bölümünü ekleyerek özelleştirme bir **Web Bölümü** öğesi herhangi bir SharePoint projesine ve kod dosyası web bölümü için veya bir tasarımcı kullanarak düzenleme. Daha fazla bilgi için bkz: [nasıl yapılır: Tasarımcı kullanarak bir SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
### <a name="to-create-a-sharepoint-web-part"></a>Bir SharePoint web bölümü oluşturmak için
  
1.  Oluşturun veya bir SharePoint proje açın.  
  
     Daha fazla bilgi için bkz: [SharePoint projesi ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  SharePoint proje düğümünde seçin **Çözüm Gezgini** ve ardından **proje** > **Yeni Öğe Ekle**.  
  
3.  İçinde **Yeni Öğe Ekle** iletişim kutusunda, genişletin **SharePoint** düğümünü ve ardından **2010** düğümü.  
  
4.  SharePoint şablonları listesinden seçip **Web Bölümü**.  
  
5.  İçinde **adı** kutusunda web bölümü için bir ad belirtin ve ardından **Ekle** düğmesi.  
  
     Web bölümü görünür **Çözüm Gezgini**. Bir web bölümü içeren dosyaları hakkında daha fazla bilgi için bkz: [için SharePoint web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
6.  İçinde **Çözüm Gezgini**, az önce oluşturduğunuz web bölümü için kod dosyasını açın.  
  
     Örneğin, web bölümünün adı ise *WebPart1*, açık *WebPart1.vb* (Visual Basic'te) veya *WebPart1.cs* (C# ' ta).  
  
7.  Kod dosyasında denetimlerine ekleme <xref:System.Web.UI.Control.CreateChildControls%2A> yöntemi.  
  
     Bir örnek için bkz: [izlenecek yol: SharePoint için bir web bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Nasıl yapılır: Tasarımcı kullanarak bir SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [İzlenecek yol: SharePoint için bir web bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [İzlenecek yol: Tasarımcı kullanarak bir web bölümü SharePoint için oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  
