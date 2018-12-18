---
title: 'Nasıl yapılır: özel bir derlemeyi bir BDC özelliğine dahil etme | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e685c3003fa77814217716fc886589e4a2633429
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294675"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Nasıl yapılır: özel bir derlemeyi bir BDC özelliğine dahil etme
  Projenizi derlemeleri aynı çözümdeki diğer projelerden başvuruda bulunabilir. Projenin özellik dosyasına kullanarak bu derlemeleri ancak eklemelisiniz **Ata başvurulan bütünleştirilmiş kodları LobSystem için** iletişim kutusu.  
  
### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Bir iş verileri bağlantısı (BDC) özelliği bir özel bütünleştirilmiş kod eklemek için
  
1.  İçinde **Çözüm Gezgini**, İVB Modeli içeren klasörü seçin.  
  
2.  Üzerinde **görünümü** menüsünde tıklatın **Özellikler penceresi**.  
  
3.  İçinde **özellikleri** penceresinde seçin **derlemeleri** özelliği ve üç nokta düğmesini (![ASP.NET Mobil Tasarımcısı elips](../sharepoint/media/mwellipsis.gif "ASP.NET Mobil Tasarımcı elips")).  
  
     **Ata başvurulan bütünleştirilmiş kodları LobSystem için** iletişim kutusu görüntülenir.  
  
4.  İçinde **bir derleme seçin** listesinde, özel bir derlemeyi seçin.  
  
    > [!NOTE]  
    >  Derlemeleri yalnızca görünür **Ata başvurulan bütünleştirilmiş kodları LobSystem için** derlemeyi içeren projeye başvuru eklediyseniz iletişim kutusu. Daha fazla bilgi için [nasıl yapılır: başvurular ekleme veya kaldırma Başvurusu Ekle iletişim kutusunu kullanarak](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
5.  İçinde **başvurusu özellikleri** için açılan listeyi açın, grup **LobSystem kapsamı** özelliği, özel bir derlemeyi kullanın ve ardından yöntemleri LOB sistemine seçin **Tamam**  düğmesi.  
  
    > [!NOTE]  
    >  Özel derleme kodunda hata ayıklamak için derleme çözüm paketine eklemeniz gerekir. Daha fazla bilgi için [nasıl yapılır: ek derlemeler ekleyip](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Nasıl yapılır: yerelleştirilmiş adlar, özellikler ve izinleri belirtmek için bir kaynak dosyası kullanma](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Nasıl yapılır: bir SharePoint projesine mevcut bir BDC modeli dosyası ekleme](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Nasıl yapılır: BDC modeli oluşturma](../sharepoint/how-to-create-a-bdc-model.md)   
 [SharePoint iş verileri Integragte](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
