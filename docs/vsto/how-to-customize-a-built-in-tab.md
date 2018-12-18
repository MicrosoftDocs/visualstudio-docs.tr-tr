---
title: 'Nasıl yapılır: yerleşik bir sekmeyi özelleştirme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- built-in tabs [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 30b4af116df218f3f778b9efa1e295fbadbad86a
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257273"
---
# <a name="how-to-customize-a-built-in-tab"></a>Nasıl yapılır: yerleşik bir sekmeyi özelleştirme
  Gruplar ve denetimler için yerleşik bir sekmeyi ekleyebilirsiniz. Yerleşik bir sekmeyi zaten bir Microsoft Office uygulamasından Şerit'te olan sekme olarak kullanılır. Örneğin, **veri** sekme, yerleşik bir sekmeyi Excel'de kullanılabilir. Özel bir grup oluşturduğunuzda, sekmesinde son görünür, ancak grubunuz sekmesinde herhangi bir yere taşıyabilirsiniz.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Yerleşik bir sekmeyi grupları ekleyebilirsiniz, ancak yerleşik sekmesinden yerleşik grupları kaldırılamıyor.  
  
### <a name="to-add-groups-to-a-built-in-tab"></a>Yerleşik bir sekmeyi grupları eklemek için  
  
1.  Şerit kod dosyasını sağ tıklatın **Çözüm Gezgini**ve ardından **Görünüm Tasarımcısı**.  
  
    > [!NOTE]  
    >  Şerit kod dosyası görünmüyorsa **Çözüm Gezgini**, eklemelisiniz bir **Şerit öğesi** projenize. Bkz: [nasıl yapılır: Şerit özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Şerit Tasarımcısı'nda herhangi bir sekmesini sağ tıklatın ve ardından **özellikleri**.  
  
3.  İçinde **özellikleri** penceresinde genişletin **ControlId** özelliğini ayarlayın ve ardından **ControlIdType** özelliğine **Office**.  
  
4.  Ayarlama **OfficeId** özelliğine *kimliği kontrol* özelleştirmek istediğiniz yerleşik sekmenin.  
  
     Denetim Kimliği sekmeler, gruplar ve Microsoft Office uygulamalarında yerleşik denetimler benzersiz olarak tanımlayan bir addır.  
  
     Denetim kimliklerinin bir listesi için bkz: [Office 2010 Yardım dosyalarını: Office fluent kullanıcı arabirimi denetim tanımlayıcıları](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
5.  Gelen **Office Şerit denetimleri** sekmesinde **araç**, grupları sekmesinde sürükleyin.  
  
    > [!NOTE]  
    >  Yerleşik gruplar Tasarımcısı'nda görünmez. Bu nedenle, yerleşik bir sekmeyle çalışıp çalışmadığını belirlemek için tek yolu incelemektir **ControlId** sekmenin özelliği.  
  
### <a name="to-position-groups-on-a-built-in-tab"></a>Yerleşik bir sekmede grupları konumlandırmak için  
  
1.  Şerit Tasarımcısı'nda bir özel grubu seçin.  
  
2.  İçinde **özellikleri** penceresinde genişletin **konumu** özelliği.  
  
3.  Ayarlama **PositionType** özelliğini uygun değere:  
  
    -   **BeforeOfficeId** grubu belirlenen yerleşik bir gruptan önce konumlandırır.  
  
    -   **AfterOfficeId** belirtilen yerleşik bir gruptan sonra Grup yerleştirir.  
  
4.  Ayarlama **OfficeId** yerleşik bir gruptan denetim kimliği özelliği.  
  
     Denetim kimliklerinin bir listesi için bkz: [Office 2010 Yardım dosyalarını: Office fluent kullanıcı arabirimi denetim tanımlayıcıları](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Şerite Genel Bakış](../vsto/ribbon-overview.md)   
 [Şerit Tasarımcısı](../vsto/ribbon-designer.md)   
 [Şerit XML](../vsto/ribbon-xml.md)   
 [İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [İzlenecek yol: Şerit XML kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Nasıl yapılır: Şerit özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Nasıl yapılır: Şeritteki sekmenin konumunu değiştirme](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Nasıl yapılır: Backstage görünümüne denetimler ekleme](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Nasıl yapılır: kullanıcı arayüzü hatalarını gösterme eklentisi](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  