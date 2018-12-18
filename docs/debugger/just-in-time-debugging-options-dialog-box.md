---
title: Yalnızca hata ayıklama, zamanında, iletişim kutusu seçenekleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6736e0646193754dbd932e5501a6473ee18c7e6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49936335"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Tam Zamanında, Hata Ayıklama, Seçenekler İletişim Kutusu
Erişim için **Just-ın-Time** sayfasında, Git **Araçları** menüsüne ve ardından **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda **hata ayıklama** düğümünü seçip alt **Just-ın-Time**. Bu sayfa, Just-ın-yönetilen kod, yerel kod ve betik hata ayıklama Time etkinleştirmenize izin verir. Daha fazla bilgi için [tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Tam zamanında hata ayıklama Bu program türleri için etkinleştirebilirsiniz:  
  
- Yönetilen  
  
- Yerel  
  
- Komut Dosyası  
  
  Just-In-Time hata ayıklama dışında başlatılan bir program hata ayıklama için bir yöntem olan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Oluşturulan bir programı çalıştırdığınız [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dışında [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ortam. Tam zamanında hata ayıklama etkinleştirilirse, bir kilitlenme hatalarını ayıklama isteyip istemediğinizi soran bir iletişim kutusu görüntülenir.  
  
## <a name="associated-warnings"></a>İlişkili uyarıları  
 Bu sayfa, ziyaret ettiğinizde **seçenekleri** iletişim kutusu, şöyle bir uyarı iletisi görebilirsiniz:  
  
 **Başka bir hata ayıklayıcı kendisini Just-ın-Time kaydettiği hata ayıklayıcı. Onarmak için Just-ın-hata ayıklama veya Visual Studio onarmayı çalıştırın Time etkinleştirin.**  
  
 Başka bir hata ayıklayıcı, büyük olasılıkla eski bir sürümü varsa, bu ileti oluşur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Just-ın-Time ayarlanmış bir hata ayıklayıcı, hata ayıklayıcı.  
  
 Görebileceğiniz başka bir ileti aşağıdaki gibidir:  
  
 **Just-In-Time hata ayıklama kaydı hataları algılandı. Onarmak için Just-ın-hata ayıklama veya Visual Studio onarmayı çalıştırın Time etkinleştirin.**  
  
 Bu uyarı, biri tam zamanında hata ayıklama görürseniz [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] sorunu düzelttik kadar yönetici ayrıcalıkları gerektirir. Hemen etkinleştirmeye çalışırsanız-yönetici olmayan bu koşullar altında aşağıdaki hata iletisini görürsünüz:  
  
 **Erişim reddedildi. Sahip bir yönetici Just-ın-Time hata ayıklamasını etkinleştirmek veya Visual Studio yüklemenizi onarın.**  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama, Seçenekler iletişim kutusu](../debugger/debugging-options-dialog-box.md)   
 [Nasıl Yapılır: Hata Ayıklayıcısı Ayarlarını Belirtme](../debugger/how-to-specify-debugger-settings.md)