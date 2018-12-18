---
title: System.Deployment.Application kullanan ClickOnce uygulamalarında hata ayıklama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 4a97fb2db4c252efcb2f980915062861933a242e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890315"
---
# <a name="debugging-clickonce-applications-that-use-systemdeploymentapplication"></a>System.Deployment.Application Kullanan ClickOnce Uygulamalarında Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçinde [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım bir uygulamanın nasıl güncelleştirileceğini yapılandırmanıza olanak tanır. Ancak, özelleştirmek ve kullanmak gerekiyorsa Gelişmiş [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım özellikleri tarafından sağlanan dağıtımı nesne modeline erişme gerekecek <xref:System.Deployment.Application>. Kullanabileceğiniz <xref:System.Deployment.Application> API'leri için Gelişmiş görevler gibi:  
  
- "Şimdi güncelleştir" seçeneğini oluşturma  
  
- Koşullu, isteğe bağlı çeşitli uygulama bileşenleri yükler  
  
- Güncelleştirmeleri doğrudan uygulamanın içinde tümleşik  
  
- İstemci uygulama her zaman güncel olmasını güvence altına alır  
  
  Çünkü <xref:System.Deployment.Application> API'leri iş yalnızca bir uygulama ile dağıtıldığında [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] teknolojisine sahip tek yolu bunların hatalarını ayıklayın kullanarak uygulama dağıtmak için [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]ekleyebilir ve ardından, hata ayıklama. Hata ayıklayıcının zor olabilir erken yeterince, uygulama başlatıldığında ve debugger iliştirebilmek için önce yürütülür, bu kod genellikle çalıştığı için. Sonu (veya durdurur, Visual Basic projeleri için), güncelleştirme onay kodu veya isteğe bağlı kod önce yerleştirmek için kullanılan bir çözümdür.  
  
  Hata ayıklama önerilen tekniği aşağıdaki gibidir:  
  
1. Başlamadan önce sembol (.pdb) ve kaynak dosyaları arşivlenmiş emin olun.  
  
2. Sürüm 1 uygulama dağıtın.  
  
3. Yeni bir boş çözüm oluşturun. Gelen **dosya** menüsünde tıklatın **yeni**, ardından **proje**. İçinde **yeni proje** açık iletişim kutusunu **diğer proje türleri** düğümünü seçip **Visual Studio çözümleri** klasör. İçinde **şablonları** bölmesinde **boş çözüm**.  
  
4. Arşivlenen kaynak konumu için bu yeni çözüm özellikleri ekleyin. İçinde **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın ve ardından tıklayın **özellikleri**. İçinde **özellik sayfaları** iletişim kutusunda **kaynak dosyalarında Hata Ayıkla**, arşivlenen kaynak koduna dizininin eklersiniz. Aksi takdirde, kaynak dosya yollarını .pdb dosyasına kaydedilir. bu yana hata ayıklayıcı güncel olmayan kaynak dosyalarını bulun. Hata ayıklayıcı güncel olmayan kaynak dosyaları kullanıyorsa, kaynak eşleşmeyen bildiren bir ileti görürsünüz.  
  
5. Hata ayıklayıcı .pdb dosyalarını bulabildiğinden emin olun. Hata ayıklayıcının bunları uygulamanız ile dağıttıysanız, bunları otomatik olarak bulur. Her zaman derlemenin yanındaki önce söz konusu görünüyor. Aksi takdirde, arşiv yolu eklemeniz gerekecektir **sembol dosyası (.pdb) konumlar** (Bu seçenek, erişmek için **Araçları** menüsünde, tıklayın **seçenekleri**, ardından açın **Hata ayıklama** düğüm seçeneğine tıklayıp **sembolleri**).  
  
6. Hata ayıklama arasında ne `CheckForUpdate` ve `Download` / `Update` yöntemi çağırır.  
  
    Örneğin, bir güncelleştirme kod aşağıdaki gibi olabilir:  
  
   ```  
       Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
           If My.Application.Deployment.IsNetworkDeployed Then  
  
               If (My.Application.Deployment.CheckForUpdate()) Then  
  
                   My.Application.Deployment.Update()  
                   Application.Restart()  
  
               End If  
  
           End If  
       End Sub  
   ```  
  
7. Sürüm 2 dağıtın.  
  
8. Sürüm 2 güncelleştirmesi indirilirken hata ayıklayıcı sürüm 1 uygulamaya iliştirin. Alternatif olarak `System.Diagnostics.Debugger.Break` yöntemi ya da yalnızca `Stop` Visual Basic'te. Elbette, üretim kodunda bu yöntem çağrılarının bırakmamalısınız.  
  
    Örneğin, bir Windows Forms uygulaması geliştiriyorsanız ve güncelleştirme mantığı ile bu yöntemin bir olay işleyicisi içinde sahip olduğunuz varsayılır. Düğmeye basıldığında, sonra bir kesme noktası ayarlamak için önce bu hata ayıklamak için yalnızca ekleme (uygun arşivlenmiş dosyayı açın ve orada kesme noktasını ayarlamanız emin olun).  
  
   Kullanım <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> çağrılacak özelliği <xref:System.Deployment.Application> yalnızca uygulama dağıtıldığında API'leri; API'leri, hata ayıklama sırasında çağrılmamalıdır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Deployment.Application>



