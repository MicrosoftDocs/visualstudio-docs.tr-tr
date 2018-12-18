---
title: 'Nasıl yapılır: kendini barındıran WCF hizmetinde hata ayıklama | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 255ca0f7d472060d110135536d76de99dc46a18e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872128"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Nasıl Yapılır: Kendini Barındıran WCF Hizmetinde Hata Ayıklama
A *kendi kendini barındıran hizmete* WCF hizmet konağı IIS içinde çalışmaz bir WCF hizmeti veya [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] geliştirme sunucusu. Şirket içinde barındırılan bir WCF hata ayıklamak için en kolay yolu yapılandırmaktır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] seçtiğinizde, istemci ve sunucu başlatmak için **hata ayıklamayı Başlat** üzerinde **hata ayıklama** menüsü.  
  
 WCF hizmeti içinde veya NT hizmeti gibi bu yolla başlatılamıyor işlem kendi kendine barındırma olduğundan, bu yöntemi kullanamazsınız. Bunun yerine, aşağıdakilerden birini yapabilirsiniz:  
  
-   El ile barındırma işleme hata ayıklayıcı ekleyin. Daha fazla bilgi için [çalışan işlemlere ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     — veya —  
  
-   İstemci hata ayıklamayı başlatmak ve hizmeti çağrısı Adımlama. Bu, app.config dosyasında hata ayıklama etkinleştirmenizi gerektirir. Daha fazla bilgi için [WCE hata ayıklama sınırlamaları](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>Hem istemci hem de konak Visual Studio'dan başlatmak için  
  
1. Oluşturma bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hem istemci hem de sunucu projeleri içeren çözüm.  
  
2. Seçtiğinizde, istemci ve sunucu işlemleri başlatmak için çözüm yapılandırma **Başlat** üzerinde **hata ayıklama** menüsü.  
  
   1.  İçinde **Çözüm Gezgini**, çözüm adına sağ tıklayın.  
  
   2.  Tıklayın **başlangıç projelerini ayarlama**.  
  
   3.  İçinde **çözüm \<adı > Özellikleri** iletişim kutusunda **birden fazla başlangıç projesi**.  
  
   4.  İçinde **birden fazla başlangıç projesi** sunucu projesi için karşılık gelen satırda kılavuz **eylem** ve **Başlat**.  
  
   5.  İstemci projesine karşılık gelen satırda tıklatın **eylem** ve **Başlat**.  
  
   6.  **Tamam**'ı tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF hizmetlerinde hata ayıklama](../debugger/debugging-wcf-services.md)   
 [WCE hata ayıklamasında sınırlamalar](../debugger/limitations-on-wcf-debugging.md)   
 [Nasıl Yapılır: WCF Hizmetleri İçine Adımlama](../debugger/how-to-step-into-wcf-services.md)