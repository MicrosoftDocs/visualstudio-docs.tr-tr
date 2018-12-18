---
title: 'Nasıl yapılır: Şeritteki sekmenin konumunu değiştirme'
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 08bbdf81023be466d30e49215fc0dbe1d3812f20
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255395"
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Nasıl yapılır: Şeritteki sekmenin konumunu değiştirme
  Kullanarak bir Şerit üzerindeki özel sekme sırasını değiştirebilirsiniz **Sekme Koleksiyonu Düzenleyicisi**. Özel sekmeler önce veya sonra Şerit'te yerleşik sekmesine yerleştirebilirsiniz. Yerleşik bir sekmeyi zaten bir Microsoft Office uygulamasından Şerit'te olan sekme olarak kullanılır. Örneğin, **veri** sekme, yerleşik bir sekmeyi Excel'de kullanılabilir.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>Şeritteki sekmelerin sırasını değiştirmek için  
  
1.  Şerit kod dosyasını seçin (*.vb* veya *.cs* dosyası) içinde **Çözüm Gezgini**.  
  
2.  Üzerinde **Görünüm** menüsünde tıklatın **Tasarımcısı**.  
  
3.  Şerit Tasarımcısı sağ tıklayın ve ardından **özellikleri**.  
  
4.  İçinde **özellikleri** penceresinde, seçin **sekmeleri** özelliği ve ardından üç nokta düğmesini (![ASP.NET Mobil Tasarımcı elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcı elips")).  
  
     **Sekme Koleksiyonu Düzenleyicisi** görüntülenir.  
  
5.  İçinde **Sekme Koleksiyonu Düzenleyicisi**, **üyeleri** listesinde, istediğiniz taşıyabilir ve yukarı veya aşağı sekme sırasını değiştirmek için okları sekmesini seçin.  
  
### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Önce veya sonra Şerit üzerindeki yerleşik bir sekmeyi sekme konumlandırmak için  
  
1.  Şerit Tasarımcısı'nda bir özel sekmesini seçin.  
  
2.  İçinde **özellikleri** penceresinde genişletin **ControlId** özelliği ve ardından olduğundan emin olun değerini **ControlIdType** özelliği ayarlanmış **özel**.  
  
3.  İçinde **özellikleri** penceresinde genişletin **konumu** özelliği.  
  
4.  Ayarlama **PositionType** özelliğini uygun değere:  
  
    -   **BeforeOfficeId** grubu belirtilen yerleşik bir sekmeyi önce konumlandırır.  
  
    -   **AfterOfficeId** sonra belirtilen yerleşik bir sekmeyi Grup yerleştirir.  
  
5.  Ayarlama **OfficeId** yerleşik bir sekmeyi denetim kimliği özelliği.  
  
     Denetim kimliklerinin bir listesi için bkz: [Office 2010 Yardım dosyalarını: Office fluent kullanıcı arabirimi denetim tanımlayıcıları](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Şerite Genel Bakış](../vsto/ribbon-overview.md)   
 [Şerit Tasarımcısı](../vsto/ribbon-designer.md)   
 [Şerit XML](../vsto/ribbon-xml.md)   
 [İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [İzlenecek yol: Şerit XML kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  