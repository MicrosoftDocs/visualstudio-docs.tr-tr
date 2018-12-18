---
title: 'Nasıl yapılır: Varolan türleri görüntüleme (Sınıf Tasarımcısı) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 630902cd789fb3eec0f51ed1cfede3ae54e1ac83
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846987"
---
# <a name="how-to-view-existing-types-class-designer"></a>Nasıl Yapılır: Varolan Türleri Görüntüleme (Sınıf Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Varolan bir türünü ve üyelerini görmek için bir sınıf diyagramına şeklini ekleyin.  
  
 Yerel ve başvurulan türleri görebilirsiniz. Yerel bir tür o anda açık olan projede mevcuttur ve okunur/yazılır. Başvurulan tür başka bir projede ya da başvurulan bir derlemede bulunur ve salt okunur özelliktedir.  
  
 Sınıf diyagramları üzerinde yeni türleri tasarımı için bkz: [nasıl yapılır: Sınıf Tasarımcısı kullanarak tür oluşturma](../ide/how-to-create-types-by-using-class-designer.md).  
  
### <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Projedeki türleri bir sınıf diyagramı üzerinde görmek için  
  
1. Çözüm Gezgini'ndeki bir projeden varolan bir sınıf diyagramı (.cd) dosyası açın. Ya da hiçbir sınıf diyagramı yoksa, projeye yeni bir sınıf diyagramı ekleyin. Bkz: [nasıl yapılır: sınıf diyagramları ekleme (Sınıf Tasarımcısı) projelerine](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).  
  
2. Çözüm Gezgini'ndeki projeden bir kaynak kodu dosyasını sınıf diyagramına sürükleyin.  
  
   > [!WARNING]
   >  Çözümünüz birden fazla uygulama kod paylaşan bir proje varsa, bir sınıf diyagramına dosyaları veya kodu yalnızca şu kaynaklardan sürükleyebilirsiniz:  
   > 
   > - Diyagramı içeren uygulama projesi  
   >   -   Uygulama projesi tarafından içeri aktarılan bir paylaşılan proje  
   >   -   Başvurulan bir proje  
   >   -   Bir derleme  
  
    Kaynak kodu dosyasında tanımlı türleri temsil eden şekiller, diyagram üzerinde dosyayı sürüklediğiniz konumda görünür.  
  
   Sınıf Görünümü'ndeki proje düğümünden bir veya daha fazla türü sınıf diyagramına sürükleyerek projedeki türleri de görüntüleyebilirsiniz.  
  
> [!TIP]
>  Sınıf Görünümü açık değilse, sınıf görünümünden açın **görünümü** menüsü. Sınıf Görünümü hakkında daha fazla bilgi için bkz: [Viewing Classes and Their Members](http://msdn.microsoft.com/en-us/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).  
  
 Türleri diyagram üzerinde varsayılan konumlarda görüntülemek için Sınıf Görünümü'nde bir veya daha fazla tür seçin, seçili türlere sağ tıklayın ve seçin **sınıf diyagramını görüntüle**.  
  
> [!NOTE]
>  Türü içeren bir kapalı sınıf diyagramı projede zaten varsa, sınıf diyagramı açılarak tür şeklini görüntüler. Ancak, proje içinde bu türü içeren hiçbir sınıf diyagramı yoksa, Sınıf Tasarımcısı proje içinde yeni bir sınıf diyagramı oluşturur ve bu diyagramı açarak türü görüntüler.  
  
 Bir türü diyagram üzerinde ilk kez görüntülediğinizde, bu türe ait şekil varsayılan olarak daraltılmış görünür. Şekli genişleterek içeriğini görüntüleyebilirsiniz.  
  
### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>Bir sınıf diyagramında bir projeyi içeriğini görüntülemek için  
  
1.  Çözüm Gezgini veya sınıf görünümü, projeye sağ tıklayıp seçin **görünümü**, ardından **sınıf diyagramını görüntüle**.  
  
     Otomatik olarak doldurulan bir Sınıf Diyagramı oluşturulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: (Sınıf Tasarımcısı) türler arasında devralmayı görüntüleme](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Nasıl yapılır: sınıf diyagramlarını özelleştirme (Sınıf Tasarımcısı)](../ide/how-to-customize-class-diagrams-class-designer.md)   
 [Türleri ve İlişkilendirmeleri Görüntüleme (Sınıf Tasarımcısı)](../ide/viewing-types-and-relationships-class-designer.md)



