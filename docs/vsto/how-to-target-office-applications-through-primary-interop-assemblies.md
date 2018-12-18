---
title: 'Nasıl yapılır: birincil birlikte çalışma derlemeleriyle hedef Office uygulamaları'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- assemblies [Office development in Visual Studio], PIA references
- primary interop assemblies [Office development in Visual Studio], adding references to
- Office primary interop assemblies in Visual Studio, adding references to
- Office applications [Office development in Visual Studio], automating
- application development [Office development in Visual Studio], automating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 576d26f039005dac3d494652f1e5127c39092a00
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863756"
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Nasıl yapılır: birincil birlikte çalışma derlemeleriyle hedef Office uygulamaları
  Yeni bir Office projesi oluşturduğunuzda, Visual Studio, projenizi yaratmanız için gerekli olan Microsoft Office birincil birlikte çalışma derlemeleri (PIA) başvurular otomatik olarak ekler. Aşağıdaki senaryolarda diğer pıa'lara başvuru eklemeniz gerekir:  
  
- Projenizde diğer Microsoft Office uygulamasının özelliklerini kullanmak istiyorsunuz. Örneğin, Microsoft Office Word için Microsoft Office Excel özelliklerinin bir projede kullanmak isteyebilirsiniz.  
  
- Adanmış projeleri gibi Microsoft Office Access, Visual Studio yüklü olmayan bir Microsoft Office uygulamalarını otomatikleştirmek istiyorsunuz.  
  
  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>Bir birincil birlikte çalışma derlemesine bir başvuru eklemek için  
  
1.  Office projenizi açın ve proje adlarında seçin **Çözüm Gezgini**.  
  
2.  Üzerinde **proje** menüsünü tıklatın **Başvuru Ekle**.  
  
3.  Üzerinde **Framework** sekmesinde, istediğiniz PIA'yı seçerek **bileşen adı** listesi. Kullanılabilir Microsoft Office birincil birlikte çalışma derlemeleri hakkında daha fazla bilgi için bkz: [Office birincil birlikte çalışma derlemelerini](../vsto/office-primary-interop-assemblies.md).  
  
     Projenizin hedeflediği [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ya da sonraki **birlikte çalışma türlerini katıştır** özelliği için bütünleştirilmiş kod başvurusu **True** varsayılan olarak. Bu ayarı kullanarak, son kullanıcı bilgisayarlarında PIA çözümünüzü gerektirmez. Daha fazla bilgi için [tasarım ve Office çözümleri oluşturma](../vsto/designing-and-creating-office-solutions.md).  
  
    > [!NOTE]  
    >  Her zaman Office projelerinde kullanarak Office PIA başvuruları eklemek **.NET** sekmesinde **Başvuru Ekle** iletişim yerine **COM** sekmesi. Daha fazla bilgi için [Office birincil birlikte çalışma derlemelerini](../vsto/office-primary-interop-assemblies.md).  
  
4.  **Tamam**'ı tıklatın.  
  
     Derleme adı görünür **başvuruları** klasörü **Çözüm Gezgini**.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office birincil birlikte çalışma derlemeleri](../vsto/office-primary-interop-assemblies.md)   
 [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)   
 [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)   
 [Nasıl yapılır: yükleme Office birincil birlikte çalışma derlemeleri](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  