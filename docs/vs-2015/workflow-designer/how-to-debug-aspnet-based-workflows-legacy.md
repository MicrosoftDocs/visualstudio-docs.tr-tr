---
title: 'Nasıl yapılır: ASP.NET tabanlı iş akışları (eski) hata ayıklama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: b9da40b0b40216fc36ea45b199ecde9c6dc4a89d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236892"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Nasıl yapılır: hata ayıklama ASP.NET tabanlı iş akışları (eski)
Bu konu, hata ayıklamak açıklar [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-tabanlı [!INCLUDE[wf](../includes/wf-md.md)] ya da hedefleyen uygulamalar [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] eski içinde [!INCLUDE[wfd1](../includes/wfd1-md.md)].  
  
 ASP.NET'te başlatılan eski iş akışı veya iş akışı barındıran işleme ekleyerek bir Web hizmeti olarak yayımlanır eski iş akışı hata ayıklaması yapabilirsiniz.  
  
### <a name="to-debug-an-aspnet-based-workflow"></a>Bir ASP.NET tabanlı iş akışı hata ayıklama  
  
1.  Ayarlayarak ASP.NET uygulaması için hata ayıklamayı etkinleştir **debug = true** web.config dosyasında.  
  
2.  İş akışı kitaplığı başlangıç projesi olarak ayarlayın ve iş akışını kesme noktaları ayarlayın.  
  
3.  İş akışı Proje özelliklerinde varsayılan Web sayfasının URL'sini girin **hata ayıklama** seçeneği **dış URL ile başlangıç tarayıcı** metin kutusu.  
  
4.  Seçin **iliştirme** üzerinde **hata ayıklama** menüsü.  
  
5.  İşlem iliştirmek **kullanılabilir işlemler** listesi.  
  
     İş akışı barındıran w3wp.exe, webdev.webserver veya aspnet_wp işlemine iliştirin.  
  
6.  Tıklayın **seçin** yanındaki **eklemek için** metin kutusu.  
  
     **Kod türünü seç** iletişim kutusu görüntülenir.  
  
7.  Seçin **bu tür kodlarda hata ayıklama** seçip **iş akışı**.  
  
8.  **Tamam**'ı tıklatın.  
  
9. Tıklayın **ekleme**.  
  
10. Varsayılan Web sayfasını bir tarayıcıda açın ve iş akışı başlatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Workflow Foundation (eski) için Visual Studio hata ayıklayıcısını çağırma](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Nasıl yapılır: (eski) akışlarında kesme noktası ayarlama](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [Eski İş Akışlarında Hata Ayıklama](../workflow-designer/debugging-legacy-workflows.md)