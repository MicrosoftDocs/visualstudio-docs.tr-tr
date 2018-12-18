---
title: Eski iş akışlarında hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 5d835ddc84fae24130035f0664d446a73b7ac3f4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897714"
---
# <a name="debugging-legacy-workflows"></a>Eski İş Akışlarında Hata Ayıklama
Eski kullanıyorsanız [!INCLUDE[wfd1](../includes/wfd1-md.md)] içinde [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] oluşturmak için [!INCLUDE[wf](../includes/wf-md.md)] target.NET Framework 3.0 veya 3.5, başka bir programı gibi iş akışlarınızı kesme noktaları ayarlama işlemlere ekleme ve iş parçacığı İnceleme ayıklanabilmesi, uygulamaları ve çağrı yığını. Uzaktan hata ayıklama seçeneğiniz de vardır.  
  
> [!NOTE]
>  Visual Studio'nun birden çok sürümünü yüklediyseniz ve makinenizde kaldırılması WF3 hata ayıklama iki aşağıdaki olasılıkları biriyle başarısız olabilir:  
> 
> - Kesme noktalarınız ulaşılmıyor.  
>   -   Aşağıdaki ileti görüntülenir:  
> 
>   **Web sunucusunda hata ayıklama başlatılamadı. Hata ayıklayıcı düzgün yüklenmemiş.  İstenen türde kod hata ayıklaması yapılamıyor.  Yüklemek veya hata ayıklayıcı onarmak için Kurulumu çalıştırın.**  
> 
>   .NET Framework 3.0 veya 3.5 iş akışı hata ayıklama sırasında ya da bu senaryo ortaya çıkarsa sürümünü Visual Studio yüklemesi onarıp gerçekleştirin.  
  
 [!INCLUDE[wf2](../includes/wf2-md.md)] Aşağıdaki standart ile tümleştirilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] windows hata ayıklama:  
  
- **Kesme noktası**: beklendiği gibi çalışır, ancak bir etkinlik için işlev adı belirtin.  
  
- **Çağrı yığını**: değiştirilmiş bir iş akışı örneğinde yürüttünüz etkinliklerinin bir özetini sağlamak için. Girdileri **çağrı yığını** etkinlikleri yürütmenin bir Derinlik ilk arama penceresi açılır. Seçili etkinlik odak moduna giriş dosyasına çift tıklayabilirsiniz.  
  
- **İş parçacığı**: örnek kimliği ayıklanmakta olan iş akışı örneği sağlar.  
  
  Visual Studio için Windows Workflow Foundation, aşağıdaki hata ayıklama özellikleri desteklemez:  
  
- Koşullu kesme noktalarını Tasarımcı yüzeyinde.  
  
- QuickWatch.  
  
- Sonraki deyimi ayarlayın.  
  
- İmlece kadar Çalıştır.  
  
- Düzenle ve devam et.  
  
- Just-ın-time hata ayıklama.  
  
- Karışık mod hata ayıklama.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Windows Workflow Foundation için Visual Studio Hata Ayıklayıcısını Çağırma (Eski)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Windows Workflow Foundation için Visual Studio Hata Ayıklayıcısını Devre Dışı Bırakma (Eski)](../workflow-designer/disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Nasıl Yapılır: ASP.NET Tabanlı İş Akışlarında Hata Ayıklama (Eski)](../workflow-designer/how-to-debug-aspnet-based-workflows-legacy.md)  
  
 [Nasıl Yapılır: İş Akışlarında Kesme Noktası Ayarlama (Eski)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)  
  
 [Uzak Bir Bilgisayardan İş Akışlarında Hata Ayıklama (Eski)](../workflow-designer/debugging-workflows-from-a-remote-computer-legacy.md)  
  
 [Hata Ayıklama Adımlama Seçenekleri (Eski)](../workflow-designer/debug-stepping-options-legacy.md)  
  
 [Nasıl Yapılır: Hata Ayıklama Adımlama Seçeneğini Değiştirme (Eski)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)