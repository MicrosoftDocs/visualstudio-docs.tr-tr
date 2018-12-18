---
title: 'Nasıl yapılır: bir iş akışı projesine yeni öğe ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f9dd186c4f9b319b5c4c60fa48d3a32e16c673f3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210946"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Nasıl yapılır: bir iş akışı projesine yeni öğe ekleme
Bir iş akışı projesi oluşturduktan sonra iş akışı etkinlikleri, tasarımcılar ve diğer tanıdık ekleyebilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projenize öğeleri.  
  
 Aşağıdaki tabloda [!INCLUDE[wf](../includes/wf-md.md)] öğeleri bir iş akışı projesine ekleyebilirsiniz.  
  
|Ad|Açıklama|  
|----------|-----------------|  
|Etkinlik|Diğer etkinliklerini oluşmasına bir etkinlik. Bu öğeyi seçerseniz ekler aynı XAML dosyasını projeye seçerken elde edebilirsiniz gibi **etkinlik Kitaplığı** için yeni bir proje şablonu. [!INCLUDE[crabout](../includes/crabout-md.md)] Bu yordama bakın [nasıl yapılır: etkinlik kitaplığı oluşturma](../workflow-designer/how-to-create-an-activity-library.md).|  
|Etkinlik Tasarımcısı|Bir etkinliğin tasarım zamanı deneyimi özelleştirmek için bir tasarımcı. Bu öğeyi seçerseniz ekler aynı dosyaları projeye seçerken elde edebilirsiniz gibi **etkinlik Tasarımcısı Kitaplığı** için yeni bir proje şablonu. [!INCLUDE[crabout](../includes/crabout-md.md)] Bu yordama bakın [nasıl yapılır: etkinlik Tasarımcısı kitaplığı oluşturma](../workflow-designer/how-to-create-an-activity-designer-library.md).|  
|Kod etkinliği|Yürütme mantığı kod olarak yazılmış bir etkinlik. Bir kaynak kodu dosyası geçersiz kılma ile <xref:System.Activities.CodeActivity.Execute%2A> yöntemi zaten oluşturulan sizin için.|  
|WCF iş akışı hizmeti|A [!INCLUDE[indigo2](../includes/indigo2-md.md)] iş akışı etkinlikleri kullanılarak yapılmış bir hizmet. Bu öğeyi seçerseniz ekler aynı dosyaları projeye seçerken elde edebilirsiniz gibi **WCF iş akışı hizmeti uygulaması** için yeni bir proje şablonu. [!INCLUDE[crabout](../includes/crabout-md.md)] Bu yordama bakın [nasıl yapılır: WCF iş akışı hizmeti uygulaması oluşturma](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|  
  
### <a name="to-add-a-new-item-to-a-workflow-project"></a>Bir iş akışı projesine yeni bir öğe eklemek için  
  
1.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle...** .  
  
     **Yeni bir öğe eklemek** iletişim kutusu açılır.  
  
2.  İçinde **yüklü şablonlar** bölmesinde **iş akışı** grubu.  
  
3.  Dört öğelerden birini seçin. Önceki tabloda kullanılabilir seçenekler listelenmiştir.  
  
4.  Öğesi için uygun bir ad yazın **adı** iletişim kutusunun alt kısmındaki kutusu.  
  
5.  Tıklayın **Ekle** geçerli iş akışı projesine öğe eklemek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı Projesi Oluşturma](../workflow-designer/creating-a-workflow-project.md)