---
title: 'Nasıl yapılır: WCF iş akışı hizmeti uygulaması oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 8632d8cf942fe4a06f12d324fea1f6f567080981
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228442"
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Nasıl yapılır: WCF iş akışı hizmeti uygulaması oluşturma
[!INCLUDE[indigo1](../includes/indigo1-md.md)] İş akışı hizmeti uygulamaları iletileri istemcileri ile kendisi arasında işlem sınırları arasında geçen dağıtılmış iletişimleri hizmetleridir. Hizmet tarafında hizmet sözleşmesinin uygulamasını bildirimli olarak iş akışı etkinliklerinde aracılığıyla gerçekleştirilir [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] .NET Framework 3.5 eski iş akışı hizmetlerine benzer şekilde.  
  
### <a name="to-create-a-wcf-workflow-service-application"></a>WCF iş akışı hizmeti uygulaması oluşturmak için  
  
1.  Başlangıç [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2.  Üzerinde **dosya** menüsünde **yeni**ve ardından **proje...** .  
  
     **Yeni proje** iletişim kutusu açılır.  
  
3.  İçinde **yüklü şablonlar** bölmesinde **WCF** veya **iş akışı** da **Visual C#** veya **VisualBasic** gruplandırmaları tercih ettiğiniz dilde bağlı olarak.  
  
4.  Orta bölmede seçin **WCF iş akışı hizmeti uygulaması**.  
  
5.  İçinde **adı** kutusunda, tanımlamakta kolaylaştırmak, projeniz için açıklayıcı bir ad girin.  
  
6.  İçinde **konumu** kutusunda, projeyi kaydedin veya istediğiniz dizin girin **Gözat** gitmek için.  
  
7.  İçinde **çözüm** kutusunda, yeni bir çözüm oluşturup ardından seçin **Tamam**.  
  
    > [!NOTE]
    >  Varolan bir çözüm için bir iş akışı konsol uygulaması eklemek istiyorsanız, bu çözümde açık [!INCLUDE[vs2010](../includes/vs2010-md.md)], çözüme sağ tıklayın **Çözüm Gezgini**seçip **Ekle**, ardından  **Yeni proje...** açmak için **yeni proje** iletişim kutusu. Bu yordamda yukarıda açıklanan şekilde devam edin.  
  
8.  Proje şablonunu bir hizmet tanımı XAML olarak oluşturur. [!INCLUDE[wfd1](../includes/wfd1-md.md)] Tasarım görünümü ile açılır bir <xref:System.Activities.Statements.Sequence> içeren bir dizi etkinlik <xref:System.ServiceModel.Activities.Receive> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: bir etkinliği oluşturma](http://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436)   
 [İş Akışı Projesi Oluşturma](../workflow-designer/creating-a-workflow-project.md)