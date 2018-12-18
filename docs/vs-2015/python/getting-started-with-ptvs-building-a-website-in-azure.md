---
title: "PTVS kullanmaya Başlarken: azure'da bir Web sitesi oluşturma | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bdbda36-14d2-4fde-ba42-d91042777ff6
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 1c4f0d0a1bf963857cde5dc0c6aa36e2aa04ca7f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282756"
---
# <a name="getting-started-with-ptvs-building-a-website-in-azure"></a>PTVS Kullanmaya Başlarken: Azure’da Web Sitesi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Azure'da bir Python web sitesi hızlı bir şekilde oluşturmaya başlayabilirsiniz.  
  
 Bu çok kısa yönergeleri izleyebilirsiniz [youtube video](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6).  
  
 Yeni Proje ile Başlat... iletişim ve altında Python Bottle Web projesi projeleri seçin.  Bu [Bottle](http://bottlepy.org/docs/dev/index.html) dayalı bir başlangıç sitesi şablonu, [önyükleme framework](http://getbootstrap.com/).  Proje oluşturduğunuzda, Visual Studio sanal bir ortama bağımlılıkları (Bu durumda Bottle) yüklemenizi ister.  Bir Azure Web sitesine dağıttığınız için sitenizin işlemi için gerekli bitleri dağıtmak için sanal bir ortama bağımlılıkları eklemeniz gerekir.  Python 2.7 veya 3.4 32 bit ortamınızı temel gerekir.  Projeyi oluşturduktan sonra sitenizin yerel olarak çalıştırma başlatmak için F5 tuşuna basın.  
  
 Azure'da site denemek kolay bir işlemdir.  Azure aboneliğiniz yoksa, kullanabileceğiniz [try.azurewebsites.net](https://trywebsites.azurewebsites.net/).  Bu site, yalnızca sosyal oturum açma ile bir kerede bir saat için Azure Web siteleri denemek için basit bir yol sunar.  Kredi kartı gerekmez.  Dil Değiştir açılan listesi boş Site şablonunu seçin ve oluştur.  "Web uygulamanızı ile çalışma" altında yayımlama profilini indir'i seçin ve Visual Studio ile kullanım için dosya kaydedin.  Ayrıca, herhangi bir işletim sisteminden git kullanarak dağıtabilirsiniz.  
  
 Visual Studio dönün ve proje oluşturduğunuz.  Çözüm Gezgini'nde, proje düğümünü seçin, sağ işaretçi düğmesini seçin ve Yayımla'ı seçin.  Bir Azure aboneliğiniz varsa, Microsoft Azure Web Siteleri'nde buradan sitelerinizi yönetmek için iletişim kutusunda tıklayabilirsiniz.  Bu kılavuzda, az önce indirdiğiniz yayımlama profilini içeri aktarmak için Al'ı seçin.  Yayımlama profili, gerekli tüm bilgileri olduğundan, yayımlama seçebilirsiniz.  Birkaç saniye içinde yeni bir tarayıcı penceresi açılır ve Azure Bulutu üzerinde barındırılan sitenizin Canlı.  
  
 Basit Web siteleri kolaydır, ancak azure'da daha önemli web uygulamaları hakkında daha fazla bilgi için bkz: [yakından](https://www.youtube.com/watch?v=WG3pGmoo8nE&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=10) video diğerlerinin yanı sıra bu kanal (bağlantı alma başlatıldı veya derin Dalış video sayfasının yanı sıra aşağıda sağ üst .  
  
 Bu çok kısa yönergeleri izleyebilirsiniz [youtube video](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Wiki belgeleri](https://github.com/Microsoft/PTVS/wiki/Web-Project)   
 [PTVS kullanmaya başlama ve kapsamlı videolar alma](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

